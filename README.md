# multi-tenancy-examples

There are web-api, recommendation and purchase-history services.  web-api is owned by team A, and the other two services are owned by team B.

```bash
kubectl create ns web-api-ns
kubectl create ns recommendation-ns
kubectl create ns purchase-history-ns
kubectl label namespace web-api-ns istio-injection=enabled
kubectl label namespace recommendation-ns istio-injection=enabled
kubectl label namespace purchase-history-ns istio-injection=enabled
kubectl apply -f mt/web-api.yaml
kubectl apply -f mt/recommendation.yaml
kubectl apply -f mt/purchase-history-v1.yaml
kubectl apply -f mt/web-api-vs.yaml
kubectl apply -f mt/web-api-gw-https.yaml
```

For team A (owning web-api-ns), the following resources are updated/added to enforce multi-tenancy:

* mt/web-api-vs-exportto.yaml
* mt/sidecar-team-a.yaml
* mt/web-api-authz.yaml

For team B (owning recommendation-ns & purchase-history-ns), the following resources are updated/added to enforce multi-tenancy:

* mt/purchase-history-service-exportto.yaml
* mt/sidecar-team-b.yaml
* mt/recommendation-authz.yaml
* mt/purchase-history-authz.yaml

Create the secret:

```bash
kubectl create -n istio-system secret tls istioinaction-cert --key mt/certs/istioinaction.io.key --cert mt/certs/istioinaction.io.crt
```

To access the `web-api` service:

```bash
curl --cacert mt/certs/ca/root-ca.crt -H "Host: istioinaction.io" https://istioinaction.io --resolve istioinaction.io:443:$GATEWAY_IP
```
