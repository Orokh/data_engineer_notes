---
creation date: 2022-05-04 17:01

tags: gcp scheduler
---

![Logo|110](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.mydraw.com%2FNIMG.axd%3Fi%3DShape-Libraries%2FCloud%2FGoogle-Cloud%2FGCP-Icons%2FData-Analytics%2FCloud-Dataflow.png&f=1&nofb=1)

# Core concepts

[DAG](https://airflow.apache.org/docs/apache-airflow/stable/concepts/dags.html)

A Directed Acyclic Graph is a collection of all the tasks you want to run, organized in a way that reflects their relationships and dependencies.

[Operator](https://airflow.apache.org/docs/apache-airflow/stable/concepts/operators.html)

The description of a single task, it is usually atomic. For example, the _BashOperator_ is used to execute bash command.

[Task](https://airflow.apache.org/docs/apache-airflow/stable/concepts/tasks.html)

A parameterised instance of an Operator; a node in the DAG.

[Task Instance](https://airflow.apache.org/docs/apache-airflow/stable/concepts/tasks.html#task-instances)

A specific run of a task; characterized as: a DAG, a Task, and a point in time. It has an indicative state: _running_, _success_, _failed_, _skipped_, ...

You can read more about the concepts [here](https://airflow.apache.org/concepts.html#).
