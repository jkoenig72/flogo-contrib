# tibco-kafkapub
This activity provides your flogo application the ability to send a Kafka message


## Installation

```bash
flogo install github.com/TIBCOSoftware/flogo-contrib/activity/kafkapub
```

## Schema
Inputs and Outputs:

```json
{
 "inputs":[
    {
      "name": "BrokerUrls",
      "type": "string"
    },
    {
      "name": "Topic",
      "type": "string"
    },
    {
      "name": "Message",
      "type": "string"
    },
    {
      "name": "user",
      "type": "string"
    },
    {
      "name": "password",
      "type": "string"
    },
    {
      "name": "truststore",
      "type": "string"
    }
  ],
  "outputs": [
    {
      "name": "partition",
      "type": "int"
    },
    {
      "name": "offset",
      "type": "long"
    }
  ]
}
```
## Settings
| Setting    | Description                                                                                                                                                                                             | Cardinality |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| BrokerUrls | The Kafka cluster to connect to                                                                                                                                                                         | Required    |
| Token      | The Kafka topic on which to place the message                                                                                                                                                           | Required    |
| Message    | The text message to send                                                                                                                                                                                | Required    |
| user       | If connectiong to a SASL enabled port, the userid to use for authentication                                                                                                                             | Optional    |
| password   | If connectiong to a SASL enabled port, the password to use for authentication                                                                                                                           | Optional    |
| truststore | If connectiong to a TLS secured port, the directory containing the certificates representing the trust chain for the connection.  This is usually just the CACert used to sign the server's certificate | Optional    |

## Outputs
| Value     | Description                                            |
|-----------|--------------------------------------------------------|
| partition | Documents the partition that the message was placed on |
| offset    | Documents the offset for the message                   |

## Configuration Examples
### Simple
Configure a task to send a message to the 'syslog' topic.


```json
{
      "id": 2,
      "name": "tibco-kafkapub",
      "description": "Publish a message to a kafka topic",
      "type": 1,
      "activityType": "tibco-kafkapub",
      "activityRef": "github.com/TIBCOSoftware/flogo-contrib/activity/kafkapub",
      "attributes": [
        {
          "name": "BrokerUrls",
          "value": "bilbo:9092",
          "required": false,
          "type": "string"
        },
        {
          "name": "Topic",
          "value": "syslog",
          "required": false,
          "type": "string"
        },
        {
          "name": "Message",
          "value": "mary had a little lamb",
          "required": false,
          "type": "string"
        }
      ]
}
```

