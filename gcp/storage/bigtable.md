---
creation date: 2022-05-04 17:01

tags: gcp datastorage
---

![BigTable Logo|110](https://www.logiciels.pro/wp-content/uploads/2021/05/google-cloud-bigtable-avis-prix-alternatives-logiciel.webp)

- NoSQL database
- Structure: single index by table: RowKey

# Keys

👍 Dos:

- Keep the key short (<4KB)
- Store multiple delimited values in each row key
- Create a key that makes it possible to retrieve a well-defined range of rows
- Use human readable values
- In many cases, design row keys that start with a common value and end with a granular value

👎 Donts:

- Rowkey that start with timestamp (causes hotspotting on the nodes)
- Rowkey that separates related data
- Keys that will need frequent updates (ex: for a captor, store `<deviceID>#<captorID>#<timestamp>` for each reading, instead of updating `<deviceID>#<captorID>`)
- hashed values => nullifies bigtable sorting order

# Optimization

> If the **Read pressure index** metric for a key bucket is 100 or greater for a long period of time, you can take the following actions to lower the index:
>
> -   Use [filters](https://cloud.google.com/bigtable/docs/filters) to reduce the amount of data that you read.
> -   Change your [schema design](https://cloud.google.com/bigtable/docs/schema-design) or your application so that the data in a heavily used row, or in an excessively large row, is spread across multiple rows.
> -   Update your application to cache the results of reads from Bigtable.
>
> If the **Write pressure index** metric for a key bucket is 100 or greater for a long period of time, you can take the following actions to lower the index:
>
> -   Change your [schema design](https://cloud.google.com/bigtable/docs/schema-design) or your application so that the data in a heavily used row, or in an excessively large row, is spread across multiple rows.
> -   Update your application to batch and deduplicate writes to Bigtable.
>
> If the **Large rows** metric is present for a key bucket, examine the rows in the highlighted key bucket, then change your [schema design](https://cloud.google.com/bigtable/docs/schema-design) or your application so that less data is stored in those rows.

[Source](https://cloud.google.com/bigtable/docs/keyvis-getting-started)

In general, do not use more than 70% of the hard limit on total storage, so you have room to add more data. If you do not plan to add significant amounts of data to your instance, you can use up to 100% of the hard limit.

Clusters can be configured with either HDD (price --, speed --) or SSD (price ++, speed ++)
