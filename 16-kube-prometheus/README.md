# 16. kube-prometheus

## Already prepared

## Done by the speaker


* Install until there are no errors
```
helm install --namespace monitoring -f values.yaml --name prom stable/prometheus-operator --version 5.7.0
kubectl apply -f dashboards/
# restart grafana
kubectl delete pod -l app=grafana -n monitoring
kubectl apply -f exporters/
```

## Install exporter

```
helm upgrade --install mysql-exporter stable/prometheus-mysql-exporter -f mysql-exporter.yaml --namespace <YOURNAME>
kubectl apply -f mysql-service-monitor.yaml
```
