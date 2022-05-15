# Secure .NET Clients

`Confluent.Kafka` supports flexibile SSL configuration for client certificates. We can either,

1. Configure the `SslCertificate`, `SslKey`, and `SslPassword` individually

2. Or configure the `SslKeystore` and `SslKeystorePassword` using the `.p12` keystore that we created previously that contains our certificate and key

## Configuration
=== "p12 Keystore file"
    ``` json title="appsettings.json"
    "Kafka": {
            "Consumer": {
                // CA Root public certificate file
                "SslCaCertificateLocation": "root.crt",

                // Client's p12 keystore
                "SslKeystoreLocation": "myconsumer.p12",

                // Password used to lock the keystore
                "SslKeystorePassword": "abcde"
            }
        }
    }
    ```

=== "PEM string"
    Useful if SSL configs need to be injected as a string from ACDC

    ``` json title="appsettings.json"
    {
        "Kafka": {
            "Consumer": {
                // Contents of CA public certificate `root.crt` as string
                "SslCaCertificatePem": "-----BEGIN CERTIFICATE-----\nMIIDgzCCAmug ...Contents... nagStwOuWl4MHDC\n-----END CERTIFICATE-----",

                // Contents of CA public certificate `root.crt` as string
                "SslCertificatePem": "-----BEGIN CERTIFICATE-----\nMIIDPjCCAiYC ...Contents... ss8DiMWQPUNNAo4\n-----END CERTIFICATE-----",

                // Contents of Client private key `myconsumer.key` as string
                "SslKeyPem": "-----BEGIN ENCRYPTED PRIVATE KEY-----\n ...Contents... \n-----END ENCRYPTED PRIVATE KEY-----",

                // Password used to encrypt the client private key
                "SslKeyPassword": "abcde"
            }
        }
    }
    ```

=== ".crt & .key files"
    ``` json title="appsettings.json"
    "Kafka": {
            "Consumer": {
                // CA Root public certificate file
                "SslCaCertificateLocation": "root.crt",

                // Client's public certificate file
                "SslCertificateLocation": "myconsumer.crt",

                // Client's private key file
                "SslKeyPem": "myconsumer.key",

                // Password used to encrypt the client private key
                "SslKeyPassword": "abcde"
            }
        }
    }
    ```
