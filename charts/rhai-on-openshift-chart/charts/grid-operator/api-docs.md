# grid-operator

![Version: 0.1.4](https://img.shields.io/badge/Version-0.1.4-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.1.4](https://img.shields.io/badge/AppVersion-v0.1.4-informational?style=flat-square)

Grid operator for multi-site AI inference routing with Praxis

**Homepage:** <https://github.com/praxis-proxy/grid>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Praxis Proxy |  | <https://github.com/praxis-proxy> |

## Source Code

* <https://github.com/praxis-proxy/grid>

## Requirements

Kubernetes: `>=1.26.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Pod affinity rules. |
| commonLabels | object | `{}` | Labels added to all chart-managed resources. |
| fullnameOverride | string | `""` | Override the fully qualified app name. |
| gateway | object | `{"address":"","port":"","serviceName":""}` | Advertised gateway address configuration. |
| gateway.address | string | `""` | Gateway address override. |
| gateway.port | string | `""` | Gateway port for operator-to-gateway discovery. Maps to GRID_GATEWAY_PORT. |
| gateway.serviceName | string | `""` | Gateway Kubernetes Service name for the operator to discover. Maps to GRID_GATEWAY_SERVICE_NAME. |
| health | object | `{"liveness":{"initialDelaySeconds":5,"periodSeconds":10},"readiness":{"initialDelaySeconds":5,"periodSeconds":10}}` | Probe timing configuration. |
| health.liveness | object | `{"initialDelaySeconds":5,"periodSeconds":10}` | Liveness probe settings. |
| health.liveness.initialDelaySeconds | int | `5` | Initial delay before the first liveness probe. |
| health.liveness.periodSeconds | int | `10` | Period between liveness probes. |
| health.readiness | object | `{"initialDelaySeconds":5,"periodSeconds":10}` | Readiness probe settings. |
| health.readiness.initialDelaySeconds | int | `5` | Initial delay before the first readiness probe. |
| health.readiness.periodSeconds | int | `10` | Period between readiness probes. |
| image | object | `{"digest":"","pullPolicy":"IfNotPresent","repository":"ghcr.io/praxis-proxy/grid-operator","tag":""}` | Operator container image settings. |
| image.digest | string | `""` | Immutable image digest (sha256:<64 hex>). When set, tag is ignored. |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy. |
| image.repository | string | `"ghcr.io/praxis-proxy/grid-operator"` | Image repository. |
| image.tag | string | `""` | Image tag. Defaults to the chart appVersion when empty. |
| imagePullSecrets | list | `[]` | Pull secrets for private registries. |
| log | object | `{"level":"info"}` | Logging configuration. |
| log.level | string | `"info"` | RUST_LOG filter directive. |
| metrics | object | `{"bindAddress":"0.0.0.0:9090","service":{"annotations":{},"enabled":true,"port":9090}}` | Metrics and health server configuration. |
| metrics.bindAddress | string | `"0.0.0.0:9090"` | Metrics server bind address (host:port). |
| metrics.service | object | `{"annotations":{},"enabled":true,"port":9090}` | Metrics ClusterIP Service. |
| metrics.service.annotations | object | `{}` | Service annotations. |
| metrics.service.enabled | bool | `true` | Create a ClusterIP Service for the metrics port. |
| metrics.service.port | int | `9090` | Service port number. |
| nameOverride | string | `""` | Override the chart name used in resource names. |
| nodeSelector | object | `{}` | Node selector for pod scheduling. |
| podAnnotations | object | `{}` | Annotations added to the operator pod template. |
| podLabels | object | `{}` | Labels added to the operator pod template. |
| priorityClassName | string | `""` | Priority class for the operator pod. |
| rbac | object | `{"create":true}` | RBAC configuration. |
| rbac.create | bool | `true` | Create ClusterRoles, ClusterRoleBindings, and RoleBindings. |
| replicaCount | int | `1` | Number of operator replicas. Must be 1 until multi-replica operation is qualified. |
| resourceNamespaces | list | `[]` | Additional namespaces where the operator needs Secret, ConfigMap, Event, and Service access. The release namespace is always included. |
| resources | object | `{}` | Container resource requests and limits. |
| serviceAccount | object | `{"annotations":{},"create":true,"name":""}` | ServiceAccount configuration. |
| serviceAccount.annotations | object | `{}` | Annotations on the ServiceAccount (e.g. for IAM role binding). |
| serviceAccount.create | bool | `true` | Create a ServiceAccount for the operator. |
| serviceAccount.name | string | `""` | ServiceAccount name. When create is true, defaults to the release fullname. When create is false, defaults to "default". |
| serviceMonitor | object | `{"enabled":false,"interval":"","labels":{},"namespace":"","scrapeTimeout":""}` | Prometheus ServiceMonitor (requires the Prometheus Operator CRD). |
| serviceMonitor.enabled | bool | `false` | Create a ServiceMonitor resource. |
| serviceMonitor.interval | string | `""` | Prometheus scrape interval. |
| serviceMonitor.labels | object | `{}` | Additional labels on the ServiceMonitor. |
| serviceMonitor.namespace | string | `""` | ServiceMonitor namespace override. |
| serviceMonitor.scrapeTimeout | string | `""` | Prometheus scrape timeout. |
| swim | object | `{"advertiseAddress":"","bindAddress":"0.0.0.0:7946","seeds":"","service":{"annotations":{},"enabled":false,"externalTrafficPolicy":"","loadBalancerIP":"","port":7946,"type":"ClusterIP"},"siteName":""}` | SWIM protocol configuration. |
| swim.advertiseAddress | string | `""` | Externally reachable SWIM advertise endpoint (ip:port, [ipv6]:port, or hostname:port). Defaults to Pod IP and bind port. Must be set when a LoadBalancer or NodePort Service fronts the SWIM port and remote peers connect through that address. |
| swim.bindAddress | string | `"0.0.0.0:7946"` | SWIM bind address (host:port). |
| swim.seeds | string | `""` | Bootstrap SWIM seed endpoints (comma-separated ip:port, [ipv6]:port, or hostname:port). |
| swim.service | object | `{"annotations":{},"enabled":false,"externalTrafficPolicy":"","loadBalancerIP":"","port":7946,"type":"ClusterIP"}` | SWIM Service (disabled by default). |
| swim.service.annotations | object | `{}` | Service annotations. |
| swim.service.enabled | bool | `false` | Create a Service for the SWIM port. |
| swim.service.externalTrafficPolicy | string | `""` | External traffic policy. Defaults to Local for LoadBalancer, omitted for ClusterIP and NodePort. |
| swim.service.loadBalancerIP | string | `""` | Static IP for LoadBalancer type. |
| swim.service.port | int | `7946` | Service port number. |
| swim.service.type | string | `"ClusterIP"` | Service type: ClusterIP, LoadBalancer, or NodePort. |
| swim.siteName | string | `""` | Bootstrap SWIM site name override. |
| tolerations | list | `[]` | Pod tolerations. |
| topologySpreadConstraints | list | `[]` | Topology spread constraints. |

