---
creation date: 2022-05-04 17:01

tags: gcp datastorage
---

![GCS Logo|110](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.odrive.com%2Fimages%2Flinks%2Flogos%2Fgooglecloud.png&f=1&nofb=1)

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
