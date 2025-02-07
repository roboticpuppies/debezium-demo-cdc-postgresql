# Strimzi Kafka Operator

This directory contains `values.yml` to install Strimzi Kafka Operator using Helm chart. [Documentation](https://strimzi.io/docs/operators/latest/deploying#deploying-cluster-operator-helm-chart-str).

```bash
helm install strimzi-cluster-operator oci://quay.io/strimzi-helm/strimzi-kafka-operator -f kafka-operator/values.yml
```