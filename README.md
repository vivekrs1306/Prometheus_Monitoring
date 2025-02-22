# Prometheus_Monitoring

**Overview**

Implemented Kubernetes Monitoring and Alerting by using Prometheus.
Installed Prometheus on kubernetes cluster by using Helm (kube-prometheus-stack).
Created CRD for a service to monitor application.
Along with prometheus we installed alertmanager for alerting.
Integrated Slack with prometheus for alerting.

**Pre-requisite**
Kubernetes
Prometheus
Helm

**Install prometheus on k8s**
helm install kube-prometheus prometheus-community/kube-prometheus-stack -n monitoring

