---
creation date: 2022-05-04 17:01

tags: gcp scheduler
---

# Comparison

## [[pubsub]]:

- Publishers do not need to know anything about their subscribers
- Publishers have no control over the delivery of the messages
- Referred to as **implicit** invocation

## [[tasks]]:

- Publisher retains full control of execution
- Publisher specifies an endpoint where each message is to be delivered
- Referred to as **explicit** invocation

https://cloud.google.com/tasks/docs/comp-pub-sub
