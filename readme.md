## permissive-mtls-ws

kind create cluster --config=cluster.yaml
consul-k8s install -config-file values.yaml
kubectl apply -f static-server.yaml -f static-client.yaml
kubectl apply -f mesh-config-entry.yaml -n consul --validate=false
kubectl apply -f service-defaults-static-server.yaml -n consul --validate=false

testing
curl localhost:9090
kubectl port-forward svc/static-client 9090:80

taken from:
https://github.com/hashicorp/consul-k8s/pull/2100
