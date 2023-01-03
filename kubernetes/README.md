```
TO DO
```

```
https://github.com/bitnami/charts/tree/main/bitnami/kafka
```

```

1. https://github.com/acehko/kubernetes-examples/tree/main/kafka 
2. https://jinnabalu.medium.com/kafka-cluster-on-amezon-eks-cluster-5850d67ae723
3. https://platform9.com/blog/how-to-set-up-and-run-kafka-on-kubernetes/
4. https://medium.com/@knoldus/set-up-kafka-cluster-using-kubernetes-statefulset-30d73d25864b

Commands:
kubectl apply -f kafka/ns.yaml
kubectl apply -f kafka/zookeeper.yaml -n kafka
kubectl apply -f kafka/kafka.yaml -n kafka
kubectl apply -f kafka/testclient.yaml -n kafka

kubectl -n kafka exec -ti testclient -- kafka-topics.sh --topic hello --create --partitions 1 --replication-factor 1 --bootstrap-server ae8c769a22fdf45a5bb288e837323005-573386060.us-west-2.elb.amazonaws.com:9092

Create the namespace 
- kubectl apply -f kafka/namespace-kafka.yaml

Deploy the cluster
- kubectl apply -f kafka/zookeeper-cluster.yaml  --namespace=kafka-cluster
- kubectl create -f kafka/kafka-cluster.yaml --namespace=kafka-cluster

Deploy the service
- kubectl create -f kafka/zookeeper-service.yaml --namespace=kafka-cluster
- kubectl create -f kafka/kafka-service.yaml --namespace=kafka-cluster (Get kafka host from this) 

create the topic
- kubectl -n kafka exec -ti testclient -- kafka-topics.sh --bootstrap-server ${BROKER_HOST}:${BROKER_PORT} --topic ${TOPIC_NAME} --create --partitions 1 --replication-factor 1
kubectl -n kafka-cluster exec -ti testclient -- kafka-topics.sh --bootstrap-server a017735f0f0424317aa09e822950f608-1168215179.us-west-2.elb.amazonaws.com:9092 --topic hello --create --partitions 1 --replication-factor 1

list the topics
- kubectl -n ${NAMESPACE} exec -ti testclient -- kafka-topics.sh --bootstrap-server ${BROKER_HOST}:${BROKER_PORT} --list

Create a producer and publish the message
- kubectl -n ${NAMESPACE} exec -i testclient -- kafka-console-producer.sh --bootstrap-server ${BROKER_HOST}:${BROKER_PORT} --topic ${TOPIC_NAME} < input.txt

Create a consumer
- kubectl -n ${NAMESPACE} exec -ti testclient -- kafka-console-consumer.sh --bootstrap-server ${BROKER_HOST}:${BROKER_PORT} --topic ${TOPIC_NAME} --from-beginning > consumer-output.txt --timeout-ms 2000

delete the topic
- kubectl -n ${NAMESPACE} exec -ti testclient -- kafka-topics.sh --bootstrap-server ${BROKER_HOST}:${BROKER_PORT} --topic ${TOPIC_NAME} --delete 

```
