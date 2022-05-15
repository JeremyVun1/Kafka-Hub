# Control Center UI

Confluent IO also provides a web app called **Control Center** for managing Kafka Clusters via a UI.

## Install Control Center
1. Add this service to our `docker-compose.yml`

    ``` yaml
    control-center:
    image: confluentinc/cp-enterprise-control-center:${CONFLUENT_VERSION}
    hostname: control-center
    container_name: control-center
    depends_on:
        - broker
        - schema-registry
    ports:
        - "${CC_PORT}:${CC_PORT}"
    environment:
        CONTROL_CENTER_BOOTSTRAP_SERVERS: 'broker:${BROKER_PORT_INTER_HOST}'
        CONTROL_CENTER_SCHEMA_REGISTRY_URL: "schema-registry:${SCHEMA_REGISTRY_PORT}"

        CONTROL_CENTER_REPLICATION_FACTOR: 1
        CONTROL_CENTER_INTERNAL_TOPICS_PARTITIONS: 1
        CONTROL_CENTER_MONITORING_INTERCEPTOR_TOPIC_REPLICATION: 1
        CONTROL_CENTER_MONITORING_INTERCEPTOR_TOPIC_PARTITIONS: 1
        CONTROL_CENTER_METRICS_TOPIC_REPLICATION: 1
        CONTROL_CENTER_METRICS_TOPIC_PARTITIONS: 1

        CONTROL_CENTER_STREAMS_SESSION_TIMEOUT_MS: 10000

        PORT: ${CC_PORT}
    ```

2. Define the **CC_PORT** variable in the `.env` file
    ``` py
    CC_PORT=9021
    ```

3. Run docker-compose again to start the Control Center
    ``` powershell
    docker-compose up -d
    ```

## Using Control Center
Once finished loading, it will become accessible at [http://localhost:9021](http://localhost:9021){target=_blank}. We'll be using this service to create our Topic & Schema.
