# Overview

This repository is intended as a place of learning flink utilizing CodeSpaces and DevContainers
_More details pending_

# Quickstart

## Stand-alone Cluster
```bash
flink*/bin/start-cluster.sh
flink*/bin/flink run flink*/examples/streaming/WordCount.jar
tail flink*/log/flink-*-taskexecutor-*.out

python ./src/basic_operations.py

python ./src/word_count.py --input ./data/livy.txt --output ./data/livy_word_count
cat ./data/livy_word_count/$(date)/prefix-*

flink*/./bin/stop-cluster.sh
```

## Kubernetes Cluster
```bash
kubectl create sa flink
kubectl create rolebinding flink-operator --clusterrole=flink-operator --serviceaccount=default:flink
kubectl create -f https://raw.githubusercontent.com/apache/flink-kubernetes-operator/release-1.1/examples/basic.yaml
kubectl get pods
kubectl port-forward svc/basic-example-rest 8081 &
kubectl logs -f deploy/basic-example
```