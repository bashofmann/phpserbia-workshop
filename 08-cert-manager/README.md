# 8. cert-manager

## Done by the speaker

* Install cert-manager
```
kubectl apply -f https://raw.githubusercontent.com/jetstack/cert-manager/release-0.8/deploy/manifests/00-crds.yaml
kubectl create namespace cert-manager
kubectl label namespace cert-manager certmanager.k8s.io/disable-validation=true
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm upgrade --install --namespace cert-manager -f cert-manager.yaml cert-manager jetstack/cert-manager
```

* Add DigitalOcean API Token to `digitalocean-dns-secret.yaml`

* Create ClusterIssuer
```
kubectl apply -f digitalocean-dns-secret.yaml
kubectl apply -f clusterissuer-digitalocean.yaml
```

* Create wildcard certificate
```
kubectl apply -f certificate.yaml -n default
```
