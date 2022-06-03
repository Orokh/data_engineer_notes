---
creation date: 2022-05-04 17:01

tags: gcp datastorage
---

![GCS Logo|110](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.odrive.com%2Fimages%2Flinks%2Flogos%2Fgooglecloud.png&f=1&nofb=1)

# Description

- Object Storage
- #elastic
- Multi-regional storage
- Nearline (< 1/month) / Coldine (< 1/year)
- Hadoop compatible (faster than HDFS in most cases)
	- Drop-in replacement for HDFS systems
- Optimized for bulk/parallel operations, but has significant latency:
	- avoid small reads
	- avoid iterating sequentially over many nested directories
- Directories are **simulated**, so _moving_ is actually _renaming_ => can be costly


# Transfer Appliance

Transfer Appliance is a good fit for your data transfer needs if:

-   You are an existing Google Cloud Platform (GCP) customer.
-   Your data size is greater than or equal to 10TB.
-   Your data resides in locations that Transfer Appliance is available.
-   It would take more than one week to upload your data over the network.


# Storage Transfer

| Transfer scenario | Recommendation |
|---|---|
|Transferring from another cloud storage provider|Use Storage Transfer Service.|
|Transferring less than 1 TB from on-premises|Use gsutil.|
|Transferring more than 1 TB from on-premises|Use Transfer service for on-premises data.|
|Transferring less than 1 TB from another Cloud Storage region|Use gsutil.|
|Transferring more than 1 TB from another Cloud Storage region|Use Storage Transfer Service.|