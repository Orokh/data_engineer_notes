---
creation date: 2022-05-04 17:01

tags: gcp
---

1. Which of the following are the jobs of a data engineer? (choose all that apply) #dataengineer

	- ✅Manage the data
	- ✅Get the data into a usable condition
	- ✅Add new value to the data
	- ✅Get the data to where it can be useful
	- ✅Productionize data processes

1. Which of the following statements are true? (choose two)

	- [[cloudsql]] is optimized for high-read data
	- ✅[[bigquery]] is optimized for high-read data
	- [[bigquery]] is a row-based storage
	- ✅[[cloudsql]] is optimized for high-throughput writes

1. Which of the following statements on [[gcs]] are true?

	- Data in Cloud Storage is not encrypted
	- ✅Cloud Storage allows you to set retention policies on all objects in a bucket
	- ✅Cloud Storage implements both IAM policy and Access Control Lists
	- ✅Cloud Storage simulates a file system

1. Which statement best describes a data lake? #datalake

	- Storage for current/historical data intended for reporting.
	- Data storage intended for analytics.
	- Storage optimized for high-throughput writes.
	- ✅ The place where you capture every aspect of your business operations. Data is stored in its natural, raw format.

1. Which of the following statements on [[bigquery]] are correct?

	- ✅Data is run length-encoded and dictionary-encoded
	- ✅Data on BigQuery is physically stored in a redundant way separate from the compute cluster
	- The number of slots allotted to a query is independent of query complexity
	- ✅A BigQuery slot is a combination of CPU, memory, and networking resources

1. Which of the following is the ideal use case for extract and load ( #el )

	- When you want to integrate with continuous integration / continuous delivery (CI/CD) systems and perform unit testing on all components.
	- ✅Scheduled periodic loads of log files (e.g. once a day)
	- When the data loading has to happen continuously
	- When the raw data needs to be quality-controlled, transformed, or enriched before being loaded into BigQuery

1. [[cloudsql]] and [[dataproc]] offer familiar tools (mysql and hadoop/pig/hive/spark). What is the value-add provided by google cloud platform? (select the 2 correct options below )

	- ✅Running it on Google infrastructure offers reliability and cost savings
	- ✅Fully-managed versions of the software offer no-ops
	- It’s the same API, but Google implements it better
	- Google-proprietary extensions and bug fixes to MySQL, Hadoop, and so on

1. #rdbms are a good choice when you need  :

	- ✅Transactional updates on relatively small datasets
	- Aggregations on unstructured data
	- Streaming, high-throughput writes
	- Fast queries on terabytes of data

 1. True or False: [[cloudsql]] is a big data analytics warehouse

	- ✅False

1. True or False: if you are migrating your #hadoop workload to the cloud, you must first rewrite all your #spark jobs to be compliant with the cloud.

	- ✅False (You can run your same Spark job code running on the same Hadoop software but running on cloud hardware with [[dataproc]].)

1. You are thinking about migrating your #hadoop workloads to the cloud and you have a few workloads that are fault-tolerant (they can handle interruptions of individual vms gracefully). What are some architecture considerations you should explore in the cloud? choose all that apply

	- ✅Consider having multiple [[dataproc]] instances for each priority workload and then turning them down when not in use
	- ✅Use PVMs or Preemptible Virtual Machines
	- ✅Migrate your storage from on-cluster HDFS to off-cluster [[gcs]]

1. [[gcs]] is a good option for storing data that: (select the 2 correct options below).

	- ✅May be imported from a bucket into a #hadoop cluster for analysis
	- ✅May be required to be read at some later time (i.e. load a CSV file into [[bigquery]])
	- Is ingested in #real-time from sensors and other devices and supports SQL-based queries
	- Will be accessed frequently and updated constantly with new transactions from a front-end and needs to be stored in a relational database

1. Which of the below are the core services that make up [[bigquery]]? (Choose the correct 2)

	- ✅Storage service
	- ✅Query service
	- Data Optimization service
	- Machine Learning service

1. True or False: You can query a google spreadsheet directly from [[bigquery]] without loading it in first.

	- ✅True (This is a federated query)

1. You have a taxi service data schema that has three columns: ride_id ride_timestamp ride_status you want to use [[bigquery]] for reporting but you don't want to split your table into multiple sub-tables. what native features of [[bigquery]] data types should you explore? (check all that apply)

	- ✅Consider adding lat / long geographic data points as new columns and using GIS Functions to quickly plot the distances your fleet has travelled.
	- ✅Consider making ride_timestamp an ARRAY of timestamp values so each ride_id row in your table could still be unique and easy to report off of.
	- Consider renaming the ride_id column to 'label' so you can use it in a [[bqml]] model to predict the ride_id of the next ride.

1. Complete the following: In [[machine learning]], a row of data is called a(n) ...... and a column of data is called a(n) ...... . we mark one or more columns as ...... which we know for historical data and are trying to predict for future data

	- ✅1.instance or observation 2.feature 3. labels

1. If you have an image classification task for identifying whether a car is present in a photo or not, which solution should you try first?

	- Try a custom model in #tensorflow first
	- Try [[automl]] Vision first
	- ✅Try the #cloudvision API first
	- Try a custom model in [[bqml]] first

1. Match each of the terms with what they do when setting up clusters in [[dataproc]]:

	| Term | Definition |
	| ---| --- |
	| Zone |Determines the Google data center where compute nodes will be |
	| Standard Cluster mode | Provides 1 primary and N workers |
	| Preemptible | Costs less but may not be available always |

1. [[dataproc]] provides the ability for #spark programs to separate compute and storage by:

	- Setting individual zones for compute and storage
	- Pre-copying data from Cloud Storage to persistent disk on cluster startup
	- Mirroring data on both Cloud Storage and HDFS
	- ✅Reading and writing data directly from/to Cloud Storage

1. Which of the following statements are true about [[dataproc]]? (select all 2 correct answers)

	- Streamlined API for #spark and #hadoop programming
	- ✅Helps you create job-specific clusters without HDFS
	- ✅Lets you run #spark and #hadoop clusters with minimal administration

1. Which of the following statements are true? (select all 2 correct responses) [[dataflow]]

	- ✅Dataflow executes Apache Beam pipelines
	- Map operations in a MapReduce can be performed by Combine transforms in Dataflow
	- Side-inputs in Dataflow are a way to export data from one pipeline to share with another pipeline
	- ✅Dataflow transforms support both batch and streaming pipelines

1. Match each of the [[dataflow]] terms with what they do in the life of a dataflow job:

	| Term | Definition |
	| --- | --- |
	| Transform | A data processing operation or step in your pipeline  |
	| PCollection | A set of data in your pipeline |
	| Sink | Output endpoint for your pipeline |

1. Match the google cloud product with its role when designing #streaming systems

	| Product | Role |
	| --- | --- |
	| [[pubsub]] | Global message queue |
	| [[dataflow]] | Controls to handle late-arriving and out-of-order data  |
	| [[bigquery]] | Query data as it arrives from streaming pipelines |
	| [[bigtable]] | Latency in the order of milliseconds when querying against overwhelming volume |

1. [[dataflow]] offers the following that makes it easy to create resilient streaming pipelines when working with unbounded data: (select all 2 correct responses)

	- Global message bus to buffer messages
	- ✅Ability to flexibly reason about time
	- ✅Controls to ensure correctness
	- SQL support to query in-process results

1. True or False? [[pubsub]] guarantees that messages delivered are in the order they were received

	- ✅False

1. Which of the following delivery methods is ideal for subscribers needing close to real time performance? [[pubsub]]

	- ✅Push Delivery
	- Pull Delivery

1. Which of the following about [[pubsub]] topics and subscriptions are true? (select all 2 correct responses)

	- Each topic MUST have at least 1 subscription
	- ✅1 or more publisher(s) can write to the same topic
	- Each topic will deliver ALL messages for a topic for each subscriber
	- ✅1 or more subscriber(s) can request from the same subscription

1. The [[dataflow]] models provides constructs that map to the four questions that are relevant in any out-of-order data processing pipeline:

	| Questions | Constructs |
	| --- | --- |
	| What results are calculated? | Answered via transformationsA.  |
	| Where in event time are results calculated? | Answered via Event-time windowing  |
	| When in processing time are results materialized? | Answered via Watermarks, triggers, and allowed lateness.  |
	| How do refinements of results relate? | Answered via Accumulation modes  |

1. Which of the following is true for #datastudio?

	- ✅Data Studio supports data ingest through multiple connectors.
	- Data Studio is part of BigQuery and requires data to already exist in tables.
	- Data Studio is part of Dataflow and requires a streaming pipeline for data ingest.
	- Data Studio can only ingest files stored in Cloud Storage buckets.

1. True or False? #datastudio can issue queries to [[bigquery]]

	- ✅True

1. Which of the following are true about [[bigtable]]? (mark all 3 correct responses)

	- Support for SQL
	- ✅Ideal for >1TB data
	- ✅Offers very low-latency in the order of milliseconds
	- ✅Great for time-series data

1. True or False? [[bigtable]] learns access patterns and attempts to distribute reads and storage across nodes evenly

	- ✅True

1. Which of the following can help improve performance of [[bigtable]]? (select all 3 correct responses)

	- ✅Add more nodes
	- ✅Clients and Bigtable are in same zone
	- ✅Change schema to minimize data skew
	- Use HDD instead of SDD

1. Which technology was developed to attack #devops challenges in [[machine learning]] using #kubernetes and containers?

	- [[vertexai]]
	- ✅[[kubeflow]]
	- Cloud Orchestrator
	- Composer

1. [[aihub]] has templates for which of the following?

	- ✅All other answers are correct
	- Kubeflow pipelines and components
	- Trained models
	- Jupyter notebooks

1. [[bqml]] has support for which of the following modeling tasks:

	- ✅Clustering
	- Computer vision
	- ✅Regression
	- ✅Classification

1. True or false? You can train and evaluate machine learning models directly in [[bigquery]]

	- ✅True

1. [[automl]] makes use of which of the following:

	- ✅Google's models and your data

1. Which of the following are valid techniques for improving [[automl]] vision and natural language models?

	- ✅Increase the diversity and complexity of data
	- ✅Ensure consistent labeling
	- Increase the number of labels
	- ✅Increase the amount of training data

1. What is the #beam portability framework? [[dataflow]]

	- ✅A set of protocols for executing pipelines
	- A hermetic worker environment
	- ✅A language-agnostic way to represent pipelines
	- A set of cross-language transforms

1. Which of the following are benefits of #beam portability (select all that apply) ? [[dataflow]]

	- ✅Implement new Beam transforms using a language of choice and utilize these transforms from other languages
	- ✅Cross-language transforms
	- ✅Running pipelines authored in any SDK on any runner

1. Which of the following are true about #flexrs (select all that apply): [[dataflow]]

	- ✅FlexRS helps to reduce batch processing costs by using advanced scheduling techniques
	- ✅FlexRS leverages a mix of preemptible and normal VMs
	- ✅When you submit a FlexRS job, the Dataflow service places the job into a queue and submits it for execution within 6 hours from job creation.
	- FlexRS is most suitable for workloads that are time-critical

1. What are the benefits of [[dataflow]] streaming engine? select all that apply:

	- ✅Reduced consumption of worker CPU, memory, and storage
	- ✅More responsive autoscaling for incoming data variations
	- ✅Lower resource and quota consumption

1. True or false? The [[dataflow]] shuffle service is available only for batch jobs.

	- ✅True

1. You want to run the following [[dataflow]] command: which of these roles can be assigned to you for the command to work?

	`gcloud dataflow jobs cancel 2021-01-31_14_30_00-9098096469011826084--region=$region`

	- Dataflow Viewer
	- ✅Dataflow Developer
	- ✅Dataflow Admin
	- Composer Worker

1. Your project’s current ssd usage is 100TB. You want to launch a streaming pipeline in [[dataflow]] with shuffle done on the vm. You set the initial number of workers to 5 and the maximum number of workers to 100. What will be your project’s ssd usage when the job launches?

	- ✅140TB (Recall that the number of disks allocated equals the maximum number of workers in streaming pipelines. When shuffle is done on the VM, the default PD size is 400 GB. Doing 100 + (0.4 TB * 100 workers) gives you 140 TB.)

1. Your project’s current in-use ip address usage is 500/575. You run the following command. What will be the in-use ip address usage after the job starts? [[dataflow]]

	```shell
	python3 -m apache_beam.examples.wordcount \
	    --input gs://dataflow-samples/shakespeare/kinglear.txt \
	    --output gs://$BUCKET/results/outputs \
	    --runner DataflowRunner \
	    --project $PROJECT \
	    --temp_location gs://$BUCKET/tmp/ \
	    --region $REGION \
	    --subnetwork regions/$REGION/subnetworks/$SUBNETWORK \
	    --num_workers 20 \
	    --machine_type n1-standard-4 \
	    --no_use_public_ips
	```

	- 520/575
	- ✅500/575 (Because you are launching a private IP Dataflow job with `--no_use_public_ips`, no in-use IP address quota will be taken up.)
	- The job will fail to launch.

1. You are a beam developer for a university in googleville. Googleville law mandates that all student data is kept within googleville. Compute engine resources can be launched in googleville; the region name is google-world1. [[dataflow]], however, does not currently have a regional endpoint set up in google-world1. Which flags are needed in the following command to allow you to launch a dataflow job and to conform with googleville’s law?

	```shell
	python3 -m apache_beam.examples.wordcount \
	    --input gs://dataflow-samples/shakespeare/kinglear.txt \
	    --output gs://$BUCKET/results/outputs --runner DataflowRunner \
	    --project $PROJECT \
		--temp_location gs://$BUCKET/tmp/
	```

	- ✅`--region northamerica-northeast1 --worker_region google-world1` (Use `--region` to specify a supported regional endpoint, and use `--worker_region` to specify the region where worker processing must occur.)
	- `--region northamerica-northeast1`
	- `--region google-world1 --worker_zone google-world1`

1. What is cogroupbykey used for? [[dataflow]]

	- ✅To join data in different PCollections that share a common key.
	- To join data in different PCollections that share a common key and a common value type.
	- To group by a key when there are more than two key groups (with 2 key groups, you use GroupByKey)

1. How many times will be the process/processelement method of a dofn called? [[dataflow]]

	- ✅As many times as elements are in the PCollection.
	- As many times as data bundles are in the PCollection.
	- This is a runner specific value. It depends on the runner.

1. If two messages arrive at your pipeline out of order... [[dataflow]]

	- ✅ you can recover the order of the messages with a window using event time. (This is the main use case of windows with event time.)
	- you cannot do anything to recover the order of the messages.
	- you can recover the order of the messages with a window using processing time.

1. How does Apache #beam decide that a message is late? [[dataflow]]

	- ✅A message is late if its timestamp is before the watermark. (This is one of the main advantages of using a watermark.)
	- This is a runner specific value. It depends on the runner.
	- If the timestamp of the message is before the clock of the worker where it is processed.

1. What are the types of windows that you can use with #beam? [[dataflow]]

	- ✅Fixed, sliding and session windows.
	- Open and closed windows.
	- It depends on the runner, each runner has different types of windows.

1. How many triggers can a window have? [[dataflow]]

	- ✅As many as we set.
	- Exactly one.
	- One or none.

1. A sink in its simplest form is a ... ? [[dataflow]]
	- PSink
	- ✅PTransform (A sink is a prebuilt PTransform.)
	- Built-in primitive function
	- PCollection

1. You can only use the sources and sinks provided in Apache #beam for inputs and outputs. [[dataflow]]

	- ✅False (You can build your own custom sources and sinks using the various components such as a Splittable DoFn or customer PTransforms.)

1. A bounded and unbounded source are commonly associated with which of the following respectively? [[dataflow]]

	- Time-series data and graph data.
	- Small data and Big Data.
	- ✅Batch data and streaming data.
	- Structured data and unstructured data.

1. Which of the following element types can be encoded as a Schema from a PCollection (Select ALL that apply)? [[dataflow]]

	- ✅Protobuf objects
	- ✅Avro objects
	- ✅Single list of JSON objects (The list can be converted to an ARRAY as a nested structure)
	- ✅Byte String objects

1. Is it possible to mix elements in Schema PCollections inside a single Beam pipeline (Select ALL that apply)? [[dataflow]]

	- ✅Yes, but only across different PCollections
	- ✅Not possible within the same PCollection
	- Yes in all scenarios
	- Not at all

1. With ParDo, you... [[dataflow]]

	- ✅can do aggregations using state variables in a DoFn. (this is the main use case for state variables.)
	- cannot do any type of aggregations.

1. What is the use case of timers in the State & Timers API of Beam? [[dataflow]]

	- ✅Timers are used in combination with state variables, to ensure that the state is cleared at regular intervals of time. (this the main use case for timers.)
	- You can use timers instead of state variables to do timely aggregations.

1. What is the recommended way to convert JSON objects to POJOs? [[dataflow]]

	- Use JsonToPOJO
	- ✅Use JsonToRow (JsonToRow is a helper class used to convert JSON strings into Java POJOs in Dataflow.)

1. Choose all the applicable options: If your pipelines interact with external systems, [[dataflow]]

	- External System doesn't impact performance of a Dataflow pipeline as they are run outside the Dataflow environment.
	- ✅It is important to provision those external systems appropriately (i.e., to handle peak volumes).
	- Testing external systems against peak volume is not important.
	- ✅Not provisioning external systems appropriately may impact the performance of your pipeline due to back pressure.

1. Which functions of the DoFn lifecycle are recommended to be used for micro-batching? [[dataflow]]

	- setup and teardown
	- init and destroy
	- ✅startBundle and finishBundle (It is recommended to utilize startBundle and finishBundle functions of the DoFn object for micro-batching. Based on runner implementation a DoFn object may be used to process more than one bundle, so it is important to appropriately reset the state of the variables used within DoFn.)

1. Which of the following interfaces support Calcite SQL (Select ALL that apply) ? [[dataflow]]

	- ✅Beam SQL client
	- ✅Dataflow template (A Dataflow Template can be implemented using either Calcite SQL or ZetaSQL dialects.)
	- Dataflow SQL

1. What operations can you do in standard Pandas DataFrames that are not possible in Beam DataFrames? [[dataflow]]

	- Write the DataFrame columns as rows?
	- ✅Compute two different aggregates based on the input data (It is possible by using different filters from the same source Dataframe and aggregating individually.)
	- Shift the DataFrame

1. When using the interactive runner which of the following are true? [[dataflow]]

	- ✅You can limit the amount of time the InteractiveRunner records data from an unbounded source by using recording_duration option. (make use of this value when you are not dealing with sources that have large volumes.)
	- ✅You can limit the amount of data the interactive runner records from an unbounded source by setting recording_size_limit (make use of this value when you are not dealing with sources that have large volumes to ensure your notebook does not read too much data.)
	- You can limit the number of elements the interactive runner records from an unbounded source by setting recording_element_count option.

1. Which of these statements is true? [[dataflow]]

	- When using the Interactive Runner, you have to create a logging DoFn to see the values of an intermittent PCollection.
	- When using the Interactive Runner, if you want to play with the values from a PCollection within a dataframe, you must access them from within a DoFn.
	- ✅You can use the option include_window_info from ib.show to get extra metadata about each element in a Pcollection. (ib.show(windowed_word_counts, include_window_info=True) can be used.)

