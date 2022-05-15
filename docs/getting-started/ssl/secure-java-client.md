# Secure Java Clients

Java clients require certificates and keys to be packed as a `.jks` file

## Configuration
Using the jks files generated previously,

``` py title="application.properties"
keystore.location="myconsumer.jks",
truststore.location="truststore.jks"
```
