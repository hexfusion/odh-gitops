# grid-enrollment

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.1.0](https://img.shields.io/badge/AppVersion-v0.1.0-informational?style=flat-square)

Grid enrollment service with self-provisioned Grid CA and Postgres

**Homepage:** <https://github.com/praxis-proxy/grid>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Praxis Proxy |  |  |

## Source Code

* <https://github.com/praxis-proxy/grid>

## Requirements

Kubernetes: `>=1.26.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| ca | object | `{"bootstrap":{"resources":{}},"bundleSecretName":"grid-ca-bundle","commonName":"grid-ca","forceRegenerate":false,"keySecretName":"grid-ca-key","method":"builtin","provided":{"keySecretRef":""}}` | ---------------------------------------------------------------------------- |
| commonLabels | object | `{}` |  |
| db | object | `{"builtin":{"auth":{"database":"enrollment","existingSecretRef":"","username":"enrollment"},"image":"quay.io/sclorg/postgresql-16-c9s","pullPolicy":"IfNotPresent","resources":{},"storage":"8Gi","tls":{"servingSecretName":"grid-db-serving-tls"}},"external":{"caConfigMapKey":"ca.crt","caConfigMapName":"","connectionUrlSecretKey":"DB_CONNECTION_URL","connectionUrlSecretRef":""},"type":"builtin"}` | ---------------------------------------------------------------------------- |
| enrollment | object | `{"affinity":{},"authz":"kube","certLifetimeSecs":"","gridAdminTokens":{"existingSecretRef":"","generate":true},"listenAddr":"0.0.0.0:8443","nodeSelector":{},"podSecurityContext":{"runAsNonRoot":true,"seccompProfile":{"type":"RuntimeDefault"}},"replicaCount":1,"resources":{},"securityContext":{"allowPrivilegeEscalation":false,"capabilities":{"drop":["ALL"]},"readOnlyRootFilesystem":true},"service":{"type":"ClusterIP"},"serviceAccount":{"create":true,"name":""},"tolerations":[]}` | ---------------------------------------------------------------------------- |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"quay.io/praxis-proxy/grid-enrollment"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| serving | object | `{"existingSecretRef":"","extraDnsNames":[],"secretName":"enrollment-serving-tls"}` | ---------------------------------------------------------------------------- |

