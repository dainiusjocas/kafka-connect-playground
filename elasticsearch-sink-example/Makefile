start-example:
	docker-compose -p elasticsearch-sink-example up --build

create-datagen-connector:
	curl -s -X POST -H 'Content-Type: application/json' --data @datagen-config.json http://localhost:8088/connectors
	
create-elasticsearch-connector:
	curl -s -X POST -H 'Content-Type: application/json' --data @elasticsearch-sink-config.json http://localhost:8088/connectors

create-all-connectors: create-datagen-connector create-elasticsearch-connector
	
delete-elasticsearch-connector:
	curl -s -X DELETE -H 'Content-Type: application/json' http://localhost:8088/connectors/elasticsearch-sink
