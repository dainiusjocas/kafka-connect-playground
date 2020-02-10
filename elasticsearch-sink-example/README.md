# Simple Kafka Connect Elasticsearch example
In this example we will generating mock data using DataGen and streaming them to Elasticsearch (using Kafka Connect Elasticsearch).

# Setup

Makefile is with the following commands is also provided.

## Run docker containers

* `docker-compose up --build`

## Configure connectors

* `curl -s -X POST -H 'Content-Type: application/json' --data @datagen-config.json http://localhost:8088/connectors`

* `curl -s -X POST -H 'Content-Type: application/json' --data @elasticsearch-sink-config.json http://localhost:8088/connectors`

In case you want to change the Elasticsearch sink configuration and re-upload it, use this command to delete the connector.

* `curl -s -X DELETE -H 'Content-Type: application/json' http://localhost:8088/connectors/elasticsearch-sink`


# Check What is Happening

To monitor the overal setup in Confluent Control Center open `http://localhost:9021/`.

To check what documents are in Elasticsearch open: `http://localhost:9200/test-elasticsearch-sink/_search`.

# Relevant Resources:

- [Blog post on using the Kafka Elasticsearch Connector](https://rmoff.net/2019/10/07/kafka-connect-and-elasticsearch/)
- [Presentation on Kafka Connect](https://talks.rmoff.net/QZ5nsS/from-zero-to-hero-with-kafka-connect)
- [Kafka Connector REST API documentation](http://kafka.apache.org/documentation.html#connect_rest)
- [Another nice blog on the issue](https://sematext.com/blog/kafka-connect-elasticsearch-how-to/#toc-kafka-connect-rest-api-9)
