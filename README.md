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
Create monitoring, dev-ns namespace in kubernetes

**Install kube-prometheus-stack**
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update


**Install prometheus on k8s**
helm install kube-prometheus prometheus-community/kube-prometheus-stack -n monitoring

**Upgrade kube-prometheus configuration**
helm upgrade -f values.yaml kube-prometheus prometheus-community/kube-prometheus-stack -n monitoring

prometheus:
  prometheusSpec:
    podMonitorSelectorNilUsesHelmValues: false
    serviceMonitorSelectorNilUsesHelmValues: false

alertmanager:

  alertmanagerSpec:
    alertmanagerConfigNamespaceSelector:
    alertmanagerConfigSelector:
    alertmanagerConfigMatcherStrategy:
      type: None

**Deploy Kubernetes resources**
kubectl create -f .

**Prometheus UI**
kubectl port-forward service/prometheus-operated -n monitoring 9090:9090

**Grafana**
kubectl port-forward service/monitoring-grafana -n monitoring 8080:80

**Alertmanager UI**
kubectl port-forward service/alertmanager-operated -n monitoring 9093:9093
