# Code Server Helm Chart

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.8.0](https://img.shields.io/badge/AppVersion-3.8.0-informational?style=flat-square)

[code-server](https://github.com/cdr/code-server) code-server is VS Code running
on a remote server, accessible through the browser.

This chart is a personal fork to address some deficiencies and additions I needed in my lab environment.

## My Helm Command

```console
$ helm install code-server --set serviceAccount.name=coder --set image.repository=registry.home.local:8443/test/code-server --set ingress.enabled=true --set password=mypassword ../Code-Server-Helm/ -n cicd
```

## TL;DR;

```console
$ git clone https://github.com/brandtkeller/Code-Server-Helm.git
$ helm install code-server ./Code-Server-Helm -n namespace
```

## Introduction

This chart bootstraps a code-server deployment on a
[Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh)
package manager.

## Prerequisites

  - Kubernetes 1.6+

## Installing the Chart

To install the chart with the release name `code-server`:

```console
$ git clone https://github.com/brandtkeller/Code-Server-Helm.git
$ helm install code-server ./Code-Server-Helm -n namespace
```

The command deploys code-server on the Kubernetes cluster in the default
configuration. The [configuration](#configuration) section lists the parameters
that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `code-server` deployment:

```console
$ helm delete code-server
```

The command removes all the Kubernetes components associated with the chart and
deletes the release.

## Configuration

The following table lists the configurable parameters of the code-server chart
and their default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| extraArgs | list | `[]` |  |
| extraConfigmapMounts | list | `[]` |  |
| extraContainers | string | `""` |  |
| extraSecretMounts | list | `[]` |  |
| extraVars | list | `[]` |  |
| extraVolumeMounts | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| hostnameOverride | string | `""` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"codercom/code-server"` |  |
| image.tag | string | `"3.8.0"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.enabled | bool | `false` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.annotations | object | `{}` |  |
| persistence.enabled | bool | `true` |  |
| persistence.size | string | `"1Gi"` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext.enabled | bool | `true` |  |
| securityContext.fsGroup | int | `1000` |  |
| securityContext.runAsUser | int | `1000` |  |
| service.port | int | `8443` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `nil` |  |
| tolerations | list | `[]` |  |
| volumePermissions.enabled | bool | `true` |  |
| volumePermissions.securityContext.runAsUser | int | `0` |  |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm
install`. For example,

```console
$ helm upgrade --install code-server \
    ci/helm-chart \
    --set persistence.enabled=false
```

The above command sets the the persistence storage to false.

Alternatively, a YAML file that specifies the values for the above parameters
can be provided while installing the chart. For example,

```console
$ helm upgrade --install code-server ci/helm-chart -f values.yaml
```

> **Tip**: You can use the default [values.yaml](values.yaml)

### TODO:
* Add a settings field for app customizations