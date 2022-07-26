---
creation date: 2022-05-31 18:20

tags: hadoop
---

# Hive

- Use SQL to run queries on large datasets
- Developed at Facebook
- Similar to Pig, Hive runs on client computer that submit jobs (no need to install on Hadoop cluster)
- You write HiveQL (Hive’s query language), which gets converted into MapReduce jobs

# Pig

- Pig is procedural (SQL is declarative)
- Checkpointing data in the pipeline
- Use specific operator implementations vs. relying on optimizer
- Splitting pipeline e.g., do multiple things to intermediate data
- Use developer’s own code e.g., different ways of loading data

