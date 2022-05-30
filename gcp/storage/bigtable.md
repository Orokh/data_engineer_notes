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
- create a key that akes it possible to retrieve a well-defined range of rows
- Use human readable values
- In many cases, design row keys that start with a common value and end with a granular value

👎 Donts:

- Rowkey that start with timestamp (causes hotspotting on the nodes)
- Rowkey that separates related data
- Keys that will need frequent updates (ex: for a captor, store `<deviceID>#<captorID>#<timestamp>` for each reading, instead of updating `<deviceID>#<captorID>`)
- hashed values => nullifies bigtable sorting order
