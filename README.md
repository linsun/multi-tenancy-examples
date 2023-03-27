# multi-tenancy-examples

## Hard Multi-tenancy

There are web-api, recommendation and purchase-history services.  web-api is owned by team A, and the other two services are owned by team B.

For team A (owning web-api-ns), the following resources are updated/added to enforce multi-tenancy:

hard-mt/web-api-vs-exportto.yaml
hard-mt/sidecar-team-a.yaml
hard-mt/web-api-authz.yaml

For team B (owning recommendation-ns & purchase-history-ns), the following resources are updated/added to enforce multi-tenancy:

hard-mt/recommendation-vs-exportto.yaml
hard-mt/purchase-history-service-exportto.yaml
hard-mt/sidecar-team-b.yaml
hard-mt/recommendation-authz.yaml
hard-mt/purchase-history-authz.yaml
