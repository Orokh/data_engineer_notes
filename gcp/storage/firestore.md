---
creation date: 2022-05-04 17:01

tags: gcp datastorage
---

![Firestore logo|110](https://www.zoomodsplus.com/templates/yootheme/cache/firebase_logo-84111921.png)

The rows of an index table are sorted first by ancestor and then by property values, in the order specified in the index definition. The perfect index for a query, which allows the query to be executed most efficiently, is defined on the following properties, in order:

- Property used in equality filters
- Property used in an inequality filter (of which there can be no more than one)
- Properties used in sort orders
- Properties used in projections (that are not already included in sort orders)
