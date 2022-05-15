# Develop Clients

The lowest level interface for producing and consuming to Kafka topics is via the `consumer` and `producer` API.

!!! info "Java clients"
    Java has additional support for higher level abstractions that build ontop of the `consumer` and `producer` primitives.

    - Kafka Streamer

    - Kafka Connect

    - KSql

!!! info ".NET clients"
    .NET currently only has support for `consumer` and `producer` primitives via the [Confluent.Kafka](https://www.nuget.org/packages/Confluent.Kafka/) library

We will be working with the Consumer and Producer API in this guide. For more information on the other client types, refer to [Kafka Client Guides](/clients/index.md)

## .NET
Refer to [.NET guide](/getting-started/develop-clients/dotnet/producer)

## Consumer & Producer
Refer to [Java guide](/getting-started/develop-clients/java/producer)
