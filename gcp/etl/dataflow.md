---
creation date: 2022-05-04 17:01

tags: gcp etl
---

![Logo|110](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcdn-images-1.medium.com%2Fmax%2F1200%2F1*AwcIAHRqAViaGAcN3ZZt_w.png&f=1&nofb=1)

# Presentation

- Serverless
- Use same code for batch & stream
- Recommended for creating pipelines
- Scalability + Low latency

- [BigQuery and Cloud Dataflow Ingestion Optimization Guide](https://docs.google.com/document/d/1T-FA0kGb5uwUgC5iqpC_tqpjxxsQ4C8YdSb_NvSg5kw/edit#heading=h.7wh80wwmajh5)

- Combine operation is much faster than GroupByKey.
	- GroupByKey: 1 worker / key (even if keys don't have the same cardinality)
	- Combine: can be parallelized on different workers for single key
		- Combine must be comutative and associative

[Code examples](https://github.com/GoogleCloudPlatform/training-data-analyst/blob/master/courses/data_analysis/lab2/python)

## Concepts

4 main concepts:
1. Pipeline: Data to be processed + actions to be taken on it
2. PCollection: *Immutable* data holder
3. PTransform: handles input, transformation and output of the data.
4. Pipeline runners: responsible for the processing

In a Pipeline, Data is passed as a PCollection from one PTransform to another.

### Ptransform

1. ParDo: apply a function to each elements of a PCollection
2. GroupByKey: join two P collections by a common key. Put all the elements with the same key together in the same worker
3. Combine: will make the transformation in a hierarchy of several steps
4. Flatten: join two P collections by a common key (= UNION)
5. Partition: divides the PCollection into several by applying a function that assigns a groupID to each element
6. CoGroupByKey: Aggregates all input elements by their key and allows downstream processing to consume all values associated with the key. While `GroupByKey` performs this operation over a single input collection and thus a single type of input values, `CoGroupByKey` operates over multiple input collections

#### Pardo

Very general transform, that can be specialized:

| PTransform | Input | Output | Side inputs/outputs | Details |
| --- | --- | --- | --- | --- |
| Pardo | 1 | 0 .. n | Y |
| Filter | 1 | 0 .. 1 | N |
| MapElements | 1 | 1 | N |
| FlatMapElements | 1 | 0 .. n | N |
| WithKeys | value | (f(value), value) | N |
| Keys | (key, value) | key | N |
| Values | (key, value) | value | N |

#### Lifecycle

# Streaming

Event time: time of reception of the event (insertion in the queue)

Processing time: time of process start of the event

Ideally, they're as close as possible together. In reality, they can spread over seconds or minutes.

## Windowing

![[Pasted image 20220512105517.png]]

3 windowing concepts in dataflow and each can be used for below use case
1. _Fixed window_: any aggregation use cases, any batch analysis of data, relatively simple use cases.
2. _Sliding window_: Moving averages of data
3. _Session window_: user session data, click data and real time gaming analysis. Based on a key in the data

### Lag management

Dataflow computes a watermark, which is : `|oldest non-processed pubsub message - latest message processed in dataflow|` (lagtime). Windows are closed after this delay, to ensure the session is complete.

For late message (like 1min late), behavior can be:

- Discard the message (default)
- Reprocess the whole window

### Triggers

With Triggers, you don't have to wait for a window to close to get the results.

3 types of triggers:
- event time
- processing time
- data-driven

Triggers can be a combination of the 3 types.

Custom triggers: AfterWatermark (event time), AfterProcessingTime (processing time), AfterCount(data-driven).

When the trigger is triggered multiple times during a window, you can chose what to do with the messages already sent:

1. Accumulate: send the new processed messages, as well a the older ones
2. Discard: send only the new processed messages in a new batch

## Deduplication

By default, Dataflow stores the message IDs processed in the last 10 minutes. if the same Id is found again, the message is considered #duplicate and discarded

# Compute/storage separation

Goal: Offload the window state storage from the persistent disks attached to worker VMs to a back-end service

![[Pasted image 20220518115052.png]]

## Shuffle service

Shuffle is a dataflow operation behind transforms such as groupbykey, combine, CoGroupByKey

Only available for batch pipelines

Benefits:

- Faster execution times (in most cases)
- reduced consumption of resources (cpu, mem, storage)
- better autoscale
- better fault tolerance

## Streaming engine

Same a shuffle service, but for streaming

## Flexible resource scheduling (flex****rs)

Reduced batch processing costs because of :

- advanced scheduling
- dataflow shuffle service
- mix of preemptible & standard VMs

Execution within 6 hours from job creation ==> suitable for jobs not time-critical. Validation at job submission

#  #iam

Multiple permissions required to run dataflow

3 different permissions:
- User roles => can you submit a dataflow job?
- Dataflow service account => interaction between the project and dataflow (worker creation & monitoring)
	- Automatically created when activating the Dataflow API
- Controller service account => assigned to the compute VMs to access the data
	- Defaults to default compute service account (automatcally created) => has super large access, not recommended for prod
	- Should have the Dataflow Worker role as a minimum

# Quotas

Consumed global quotas:

- global CPU
- number of in-use IP addresses (possible to launch VMs with internal IPs only)
- persistent disks
	- batch: 1 drive / VM (default disk size = 250GB for on worker jobs, 25GB for dataflow backend (shuffle service) - can be overridden)
	- streaming; fixed number of drive for the job (= max number of workers) (default disk size = 400GB for on worker jobs, 30Gb for streaming service - can be overridden)

# Security

Data locality: have workers in the same region/zone as your data

Shared VPC: have workers run in closed managed VPC

Use private IPs on the workers. This blocks the worker internet access, so data can be only from:

	- another instance in the same VPC
	- a shared VPC network
	- network with VPC network peering

For data within other Google services, Private Google Access (PGA) must be enabled for the subnetwork

CMEK: Customer Managed Encryption Keys to encrypt data (in persistent disks, storage buckets, df backends)

# Best practices

- Filter data early
- Move any step that reduce data volume up in the pipeline
- Apply data transformations serially to let Dataflow optimize DAG
- While working with external systems, look out for back pressure
	- Enable autoscaling to downscale if workers are underutilized

# Troubleshooting

Worklow:
1. Checking for errors in the jobs
	1. Dataflow logs
	2. GCP Logging
2.  Looking for anomalies in the job metrics tab
	1. Data freshness and system latency are good indicators of the health of the pipeline
		1. Data freshness: are the workers able to keep up with the data ingested?
		2. System latency: a work item is taking a long time to get processed

Types of troubles:
	- Failure building the pipeline
		- can be reproduced with direct runner, and tested with unit tests
	- Failure starting the pipeline
		- Make sure the service can access your jobs associated cloud storage buckets for file staging and temporary output
		- Check the required permissions in your Google Cloud project
		- Make sure the service can access input and output sources such as files.
	- Failure during pipeline execution
		- DoFn have generated unhandled exceptions. They are reported in the Dataflow monitoring interface.
		- Batch and streaming jobs handle failures differently:
			- batch: the Dataflow service retries failed tasks up to four times.
			- streaming: failed job may stall indefinitely
	- Performance problems