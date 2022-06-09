---
creation date: 2022-05-04 17:01

tags: gcp datastorage
---

![BigQuery Logo](https://seeklogo.com/images/G/google-big-query-logo-AC63E7C329-seeklogo.com.png)

- Analytical database
- Storage service + analysis service

FlexSlots for shorter spikes in demands (specific to BQ reservation mode)

# Best practices

- Avoid unnecessary columns (~~`select *`~~)
- Consider approximate aggregate functions (`approx_count_distinct` instead of `count(distinct)`)
- Avoid javascript UDFs if possible
- Instead of joins, prefer nested and repeated fields in denormalized tables
	- Keep a dimension table under 10GB normalized, unless the date is rarely updated
	- Denormalize table over 10GB, unless data manipulation or costs outweigh the benefits of optimal queries
- Filter early and often
- Only order if needed, and in the outermost query
- Pull the largest table on the left side of a `join`
- Use wildcards to query multiple tables
- `group by` low cardinality fields
- partition tables when possible
	- partition by ingestion time, date or timestamp column or integer
	- always include the partition fields in the query filters (on the left-hand side of the clause)
- clustering to accelerate sorts / grouping within a partition
- break big complex queries into intermediate tables

[Optimizing BigQuery | Technical | Google Cloud | Y20 (last updated May 2020)](https://docs.google.com/presentation/d/1_UEyo3jZv7mivybzEGRMJb91qDDQsWqL_m230IuDH0s/edit#slide=id.g76f269f17a_1_1868)

# Omni

Federated query engine to access data from other clouds (AWS, Azure, ...). BigQuery compute clusters installed in the target Cloud directly.

- Flexible, fully-managed, multi-cloud analytics solution that allows you to analyze data across clouds such as AWS and Azure
- Use standard SQL and BQ's interface
- Take compute to where the data resides
- Powered by [[anthos]]
