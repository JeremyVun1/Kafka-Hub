# Introduction

Welcome to the Kafka Hub.

The following is a crash course designed to guide you through Kafka basics and how to use Kafka at the bank. At the end of this, you will understand,

- how to configure and secure Kafka Topics
- how to develop and test Kafka producers and consumers
- how to deploy and monitor your Kafka clients

Please also find reference guides for other content in the sections above

## Kafka
Kafka is a platform for robust, asynchronous event processing. The platform consists of,

- Kafka Topics that hold event messages

- Kafka Clients that produce and consume messages to/from topics

- A Kafka Cluster that hosts and manages topics

``` mermaid
graph LR
    p1[Producer] -->|Event| t([Kafka Topic]);
    subgraph Kafka Cluster
    t([Kafka Topic]);
    end
    t([Kafka Topic]) -->|Event| c1[Consumer1];
    t([Kafka Topic]) -->|Event| c2[Consumer2];
```

We will setup a Local Kafka Cluster using Docker, create a topic, and develop consumer and producer clients.

Then we will produce and consume from the Eventhub Kafka Cluster
