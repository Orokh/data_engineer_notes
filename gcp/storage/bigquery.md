---
creation date: 2022-05-04 17:01

tags: gcp datastorage
---

![BigQuery Logo](https://seeklogo.com/images/G/google-big-query-logo-AC63E7C329-seeklogo.com.png)

- Analytical database
- Storage service + analysis service
- Schema #design best practices:

![[Pasted image 20220504171528.png|500]]

FlexSlots for shorter spikes in demands (specific to BQ reservation mode)

# Best practices

- Avoid unnecessary columns (~~`select *`~~)
- Consider approximate aggregate functions (`approx_count_distinct` instead of `count(distinct)`). Avoid JS UDFs if possible
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