# praxis-gateway

![Version: 0.1.4](https://img.shields.io/badge/Version-0.1.4-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.4.0](https://img.shields.io/badge/AppVersion-0.4.0-informational?style=flat-square)

Temporary Praxis gateway workload chart for Grid integration testing. Deploys the Praxis process directly — not an operator. Long-term ownership moves to the future Praxis/Gateway Operator repository.

**Homepage:** <https://github.com/praxis-proxy/grid>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Praxis Proxy |  | <https://github.com/praxis-proxy> |

## Source Code

* <https://github.com/praxis-proxy/grid>
* <https://github.com/praxis-proxy/ai>

## Requirements

Kubernetes: `>=1.26.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Pod affinity rules. |
| args | list | `["--config","/etc/praxis/praxis.yaml"]` | Container arguments. Defaults to the config file path. |
| commonLabels | object | `{}` | Labels added to all chart-managed resources. |
| config | object | `{"existingConfigMap":"","key":"praxis.yaml"}` | Required Praxis configuration. |
| config.existingConfigMap | string | `""` | Name of an existing ConfigMap containing the Praxis configuration. The chart does not create or manage this ConfigMap. |
| config.key | string | `"praxis.yaml"` | Key within the ConfigMap that holds praxis.yaml. |
| credentials | list | `[]` | Credential Secret mounts for provider gateways. Each entry mounts an existing Secret at the specified path. |
| env | list | `[]` | credentials and other deployment-managed secrets. |
| fullnameOverride | string | `""` | Override the fully qualified app name. |
| health | object | `{"liveness":{"initialDelaySeconds":5,"periodSeconds":10,"tcpSocket":{"port":"http"}},"readiness":{"initialDelaySeconds":3,"periodSeconds":5,"tcpSocket":{"port":"http"}}}` | Probe configuration. |
| health.liveness | object | `{"initialDelaySeconds":5,"periodSeconds":10,"tcpSocket":{"port":"http"}}` | Liveness probe settings. Set to null to disable. |
| health.readiness | object | `{"initialDelaySeconds":3,"periodSeconds":5,"tcpSocket":{"port":"http"}}` | Readiness probe settings. Set to null to disable. |
| image | object | `{"digest":"","pullPolicy":"IfNotPresent","repository":"ghcr.io/praxis-proxy/ai","tag":"0.4.0"}` | Gateway container image settings. |
| image.digest | string | `""` | Immutable image digest (sha256:<64 hex>). When set, tag is ignored. |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy. |
| image.repository | string | `"ghcr.io/praxis-proxy/ai"` | Image repository. |
| image.tag | string | `"0.4.0"` | Image tag. Used when digest is empty. |
| imagePullSecrets | list | `[]` | Pull secrets for private registries. |
| nameOverride | string | `""` | Override the chart name used in resource names. |
| nodeSelector | object | `{}` | Node selector for pod scheduling. |
| overlay | object | `{"enabled":false,"existingConfigMap":"","items":[{"key":"routing-config.json","path":"routing-config.json"},{"key":"routing-overlay.json","path":"routing-overlay.json"}],"mountPath":"/etc/praxis/routing","sidecar":{"dataKey":"routing-overlay.json","enabled":false,"expectedLocalSite":"","expectedNetwork":"","image":{"pullPolicy":"IfNotPresent","repository":"ghcr.io/praxis-proxy/grid-overlay-sync","tag":""},"resources":{"limits":{"cpu":"50m","memory":"32Mi"},"requests":{"cpu":"10m","memory":"16Mi"}}}}` | Optional operator-produced overlay ConfigMap mount (edge gateways). |
| overlay.enabled | bool | `false` | Enable overlay ConfigMap mount. |
| overlay.existingConfigMap | string | `""` | Name of the existing overlay ConfigMap. |
| overlay.items | list | `[{"key":"routing-config.json","path":"routing-config.json"},{"key":"routing-overlay.json","path":"routing-overlay.json"}]` | Items to project from the ConfigMap (used when sidecar is disabled). |
| overlay.mountPath | string | `"/etc/praxis/routing"` | Mount path for overlay files. |
| overlay.sidecar | object | `{"dataKey":"routing-overlay.json","enabled":false,"expectedLocalSite":"","expectedNetwork":"","image":{"pullPolicy":"IfNotPresent","repository":"ghcr.io/praxis-proxy/grid-overlay-sync","tag":""},"resources":{"limits":{"cpu":"50m","memory":"32Mi"},"requests":{"cpu":"10m","memory":"16Mi"}}}` | Overlay sync sidecar settings. When enabled, the sidecar watches the ConfigMap via the Kubernetes API and writes validated overlays to a shared emptyDir, replacing the kubelet volume sync. |
| overlay.sidecar.dataKey | string | `"routing-overlay.json"` | ConfigMap data key containing the overlay envelope. |
| overlay.sidecar.enabled | bool | `false` | Enable the overlay-sync sidecar. |
| overlay.sidecar.expectedLocalSite | string | `""` | Expected local site name for scope validation. |
| overlay.sidecar.expectedNetwork | string | `""` | Expected GridNetwork name for scope validation. |
| overlay.sidecar.image | object | `{"pullPolicy":"IfNotPresent","repository":"ghcr.io/praxis-proxy/grid-overlay-sync","tag":""}` | Sidecar container image. |
| overlay.sidecar.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy. |
| overlay.sidecar.image.repository | string | `"ghcr.io/praxis-proxy/grid-overlay-sync"` | Image repository. |
| overlay.sidecar.image.tag | string | `""` | Image tag. Defaults to the chart appVersion when empty. |
| overlay.sidecar.resources | object | `{"limits":{"cpu":"50m","memory":"32Mi"},"requests":{"cpu":"10m","memory":"16Mi"}}` | Sidecar resource requests and limits. |
| podAnnotations | object | `{}` | Annotations on the gateway pod template. |
| podLabels | object | `{}` | Additional labels on the gateway pod template. Selector labels cannot be overridden. |
| podSecurityContext | object | `{}` | Extra pod-level securityContext fields (e.g. runAsUser, runAsGroup). runAsNonRoot and seccompProfile are always set by the chart. |
| port | object | `{"containerPort":8080,"name":"http","protocol":"TCP"}` | Primary listener port configuration. |
| port.containerPort | int | `8080` | Container port number. |
| port.name | string | `"http"` | Port name. |
| port.protocol | string | `"TCP"` | Port protocol. |
| priorityClassName | string | `""` | Priority class for the gateway pod. |
| replicaCount | int | `1` | Number of gateway replicas. |
| resources | object | `{}` | Container resource requests and limits. |
| service | object | `{"annotations":{},"enabled":true,"loadBalancerIP":"","port":8080,"type":"ClusterIP"}` | Gateway Service configuration. |
| service.annotations | object | `{}` | Service annotations. |
| service.enabled | bool | `true` | Create a Service for the gateway. |
| service.loadBalancerIP | string | `""` | Static IP for LoadBalancer type. |
| service.port | int | `8080` | Service port number. |
| service.type | string | `"ClusterIP"` | Service type. |
| tls | object | `{"enabled":false,"existingSecret":"","mountPath":"/etc/praxis/tls"}` | TLS Secret mount. |
| tls.enabled | bool | `false` | Enable TLS Secret mount. |
| tls.existingSecret | string | `""` | Name of the existing TLS Secret. |
| tls.mountPath | string | `"/etc/praxis/tls"` | Mount path for TLS files. |
| tolerations | list | `[]` | Pod tolerations. |
| topologySpreadConstraints | list | `[]` | Topology spread constraints. |

