```
Reference: https://kafka.apache.org/quickstart

curl https://dlcdn.apache.org/kafka/3.3.1/kafka_2.13-3.3.1.tgz | tar -xz
cd kafka_2.13-3.3.1/

bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties

bin/kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
bin/kafka-topics.sh --describe --topic test-topic --bootstrap-server localhost:9092
bin/kafka-topics.sh --delete --topic test-topic --bootstrap-server localhost:9092

bin/kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092
bin/kafka-console-consumer.sh --topic test-topic --from-beginning --bootstrap-server localhost:9092

rm -rf /tmp/kafka-logs /tmp/zookeeper /tmp/kraft-combined-logs
```