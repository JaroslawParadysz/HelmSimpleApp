# SimpleAPI Helm Chart

This Helm chart deploys the SimpleAPI application to Kubernetes.

## Installation

```bash
# Install the chart
helm install simpleapi ./helm-chart

# Install with custom values
helm install simpleapi ./helm-chart -f custom-values.yaml

# Install in a specific namespace
helm install simpleapi ./helm-chart --namespace my-namespace --create-namespace
```

## Upgrading

```bash
# Upgrade the release
helm upgrade simpleapi ./helm-chart

# Upgrade with new values
helm upgrade simpleapi ./helm-chart --set image.tag=new-tag
```

## Uninstallation

```bash
helm uninstall simpleapi
```

## Configuration

The following table lists the configurable parameters:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `ghcr.io/jaroslawparadysz/simpleapp` |
| `image.tag` | Image tag | `main-2d77828` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Service type | `NodePort` |
| `service.port` | Service port | `8080` |
| `service.nodePort` | NodePort number | `31012` |
| `namespace` | Kubernetes namespace | `default` |
| `resources.requests.memory` | Memory request | `128Mi` |
| `resources.requests.cpu` | CPU request | `100m` |
| `resources.limits.memory` | Memory limit | `256Mi` |
| `resources.limits.cpu` | CPU limit | `500m` |

## Examples

### Change image tag
```bash
helm upgrade simpleapi ./helm-chart --set image.tag=latest
```

### Scale replicas
```bash
helm upgrade simpleapi ./helm-chart --set replicaCount=3
```

### Change service type to LoadBalancer
```bash
helm upgrade simpleapi ./helm-chart --set service.type=LoadBalancer
```
