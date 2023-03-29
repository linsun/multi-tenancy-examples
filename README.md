# multi-tenancy-examples

There are web-api, recommendation and purchase-history services.  web-api is owned by team A, and the other two services are owned by team B.

For team A (owning web-api-ns), the following resources are updated/added to enforce multi-tenancy:

* mt/web-api-vs-exportto.yaml
* mt/sidecar-team-a.yaml
* mt/web-api-authz.yaml

For team B (owning recommendation-ns & purchase-history-ns), the following resources are updated/added to enforce multi-tenancy:

* mt/recommendation-vs-exportto.yaml
* mt/purchase-history-service-exportto.yaml
* mt/sidecar-team-b.yaml
* mt/recommendation-authz.yaml
* mt/purchase-history-authz.yaml
