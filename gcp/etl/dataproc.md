---
creation date: 2022-05-04 17:01

tags: gcp etl
---

![Logo|110](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmiro.medium.com%2Fmax%2F1024%2F1*7zT3ByyHCc1w2SdFS4TqSw.png&f=1&nofb=1)

# Presentation

- Apache #spark implementation
- Full [[hadoop]].
- Use case: Lift and shift de solutions on prem. Pas de nouveau jobs
- Cost effective (variable clusters)
	- Use of preemptible instances
- Fast and scalable (autoscaling)
- open source ecosystem
- managed hardware & configuration
- simplified versionning (multiple versions of Spark available)

# Cluster architecture

- All secondary workers are either preemptable or non-preemptable. It can't be a mix
- Clusters are not long-lived, they run only when required
- HDFS storage in the cluster is deleted when stopping the cluster ==> use [[gcs]]

# Usage

1. Setup
	Create a cluster. Can be done through console, gcloud, [[terraform]] config or cloud sdk
2. Configure
	Cluster options
		Region, zone (can be global)
		Architecture (single > 1:0, standard > 1:n, high availability > 3:n)
		Spark version
		Optional components
	Primary node options
		Number of vCPU, disk types (default to local SSD)
	Worker nodes
		Min number of non-preemptable workers, max number of preemptible workers
		VM options, init config, ...
3. Optimize
	Preemptible VM
	Custom machine types
	Custom images
	Persistent SSD boot, attached GPUs, ...
4. Utilize
	Job submitted through console, gcloud command, rest API, orchestration services
	Don't use hadoop direct interface
5. Monitor
	Done through native Cloud monitoring + logs

# Storage

#hdfs vs [[gcs]]

Issue with block size, locality & replication

# Optimization

- Have cluster close to data. Possible to use "auto-zone" setup in a region.
- Do not funnel the network between [[gcs]] and [[dataproc]]
- Do not deal with more than ~10k input files
	- If files are now bigger than hadoop partitions, use `fs.gs.block.size` option
- Is the size of the persistent disk enough?
- Are there enough VMs in the cluster?

Local HDFS can be necessary if:

- lots of metadata operations (many small files)
- data is modified frequently, or directories are renamed
- heavy use of _append_
- heavy IO operations
- IO workloads sensitive to latency

In general, GCS is source / target of job. Local storage is always used (shuffling, log files, ...).

# Workflow template

- YAML file, processed through a directed acyclic graph (DAG).
- Can: create/delete/select clusters, run job, wait for dependencies
- Only available via gcloud command or rest API (no console)

## Autoscaling

- Based on hadoop YARN metrics.
- Autoscaling events logged Cloud Logging
- Designed to work with off-cluster persistent data (no on-cluster hdfs/hbase)
- Does not support Spark structured streaming
- Not designed to scale to 0 (better to terminate/create clusters)
