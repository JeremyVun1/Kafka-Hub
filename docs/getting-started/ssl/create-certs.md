# Create Certificates

Currently we are connecting to our Local Kafka Cluster over Plain text. To secure it we need to create the following,

- CA root certificate
- Signed certificates for our Cluster
- Signed certificates for our Clients

!!! Info
    ABC uses SSL Certificates to secure access to the brokers and topics

## Requirements
### OpenSSL
`openssl` is required for generating ssl certificates.

Run following to check,
``` powershell
openssl version
```

!!! Failure
    If you have git installed, `openssl` will be in your git installation bin folder i.e. `<git_dir>\usr\bin\openssl.exe`. Add the bin folder to your Environment paths.

### Keytool
Java applications such as our Broker, Schema Registry etc. require certificates packed into a Java Keystore `.jks` file. If you are developing a Java client, you will also to pack the keys and certificates into a Java Keystore `.jks` file. We need `keytool` to do this.

Run following to check,
``` powershell
keytool
```

!!! Failure
    `keytool` ishould be bundled with your JDK installation in the bin folder i.e. `<jdk_dir>\bin\keytool.exe`. Add the bin folder to your Environment paths.

## Generate the Certificates
In the `secrets` folder you will find several powershell scripts for setting up certificates

1. Generate the Root CA certificate and the signed certificates for our Kafka Cluster
``` powershell
./gen-kafka-certs.ps1
```

2. Generate certs for our clients and pack them into a pkcs12 keystore
``` powershell
./gen-client-cert.ps1 myproducer
./gen-client-cert.ps1 myconsumer
```

3. View details of our generated certificates if you want using
``` powershell
openssl x509 -in <cert_name>.crt -text
```
