## permissive-mtls-ws

1. `kind create cluster --config=cluster.yaml`
1. `consul-k8s install -config-file values.yaml`
1. `kubectl apply -f static-server.yaml -f static-client.yaml`
1. `kubectl apply -f mesh-config-entry.yaml -n consul --validate=false`
1. `kubectl apply -f service-defaults-static-server.yaml -n consul --validate=false`

testing:
1. `curl localhost:9090`
1. `kubectl port-forward svc/static-client 9090:80`

taken from:
https://github.com/hashicorp/consul-k8s/pull/2100
