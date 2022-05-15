# Create Topic

## Create Topic
Use the Control Center to create a topic called `POC-NET-Topic`

## Create Schemas
We use avro schemas to define the structure of events posted to Kafka topics. Each topic has it's own Key and Value Schema.

When an event gets produced to a topic that does not have a schema defined, the `Schema Registry` will try to auto create the schema. However, because the schema acts as a contract between producers and consumers, it is best practice to define and configure the schema ourselves directly on the topic.

### Key Schema
Key values are also used to determine which topic partition Kafka writes the event to. As we will be sending a random string as the key, simply define the key schema for our topic in control center as following

``` json
string
```

### Value Schema
For the most part we are mainly concerned with the Value Schema as this defines our data payload. Here is the Schema we will be using for our `POC` topic
``` json
{
    "Header": "x"
}
```

## ABC Schema Standards
At ABC, schemas include the Kafka Event Header element for audit and logging purposes. This header element contains Correlation Id, Process Path, and timestamps.
