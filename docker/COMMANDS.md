```
Reference: 
https://hub.docker.com/r/bitnami/kafka
https://hub.docker.com/r/bitnami/zookeeper


docker-compose up -d



docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-topics.sh --bootstrap-server kafka-1:9092 --list
(Alternate Command: docker exec -it kafka-1 kafka-topics.sh --bootstrap-server kafka-1:9092 --list)

docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-topics.sh --bootstrap-server kafka-2:9092 --list






docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-topics.sh --bootstrap-server kafka-1:9092 --create --topic test_topic

docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-topics.sh --bootstrap-server kafka-1:9092 --describe --topic test_topic

docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-topics.sh --bootstrap-server kafka-1:9092 --delete --topic test_topic





docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-console-producer.sh --bootstrap-server kafka-1:9092 --topic test_topic

docker run -it --rm --network docker_kafka_net bitnami/kafka:latest kafka-console-consumer.sh --bootstrap-server kafka-2:9092 --from-beginning --topic test_topic





docker-compose down
```