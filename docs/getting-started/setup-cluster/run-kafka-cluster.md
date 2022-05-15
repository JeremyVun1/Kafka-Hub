# Run Kafka Cluster

## Kafka Cluster
The Kafka Cluster supports the consumption and production of event messages and is comprised of the following services,

| Service | Description |
| :--- | :--- |
| Kafka Zookeeper | Manages the Kafka Brokers |
| Kafka Broker | Manages access to topics |
| Kafka Schema Registry | Manages topic schemas |

### Producer and Consumer flows

The below flows outline consumption and production from/to a topic on the broker

=== "Producer"
    ``` mermaid
    sequenceDiagram
        actor Producer
        Producer ->> Schema Registry: upsert schema
        Schema Registry ->> Producer: return schema id
        Producer ->> Broker: schema id + event
        Broker ->> Schema Registry: validate event using schema id
        Broker ->> Broker: add to topic
    ```

=== "Consumer"
    ``` mermaid
    sequenceDiagram
        actor Consumer
        Consumer ->> Broker: poll event
        Broker ->> Consumer: return event + schema id
        Consumer ->> Schema Registry: fetch schema
        Schema Registry ->> Consumer: cache schema
        Consumer ->> Consumer: deserialize event
    ```

## Run the Cluster

ABC uses kafka images maintained and published by Confluent IO. We will do the same.

1. Clone the Local Kafka Repo. It comes with a `docker-compose.yml` configuration which will spin up a Zookeeper, Broker, and Schema Registry.
    ``` powershell
    git clone x
    cd kafka-local
    ```

2. To start the cluster, run the following
    ``` powershell
    docker-compose up -d
    ```

3. You should now see the Kafka Cluster services running
    ``` powershell
    docker ps
    ```
