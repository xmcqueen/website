---
title: 下载 Kubernetes
type: docs
---
<!-- 
title: Download Kubernetes
type: docs
-->

<!-- 
Kubernetes ships binaries for each component as well as a standard set of client
applications to bootstrap or interact with a cluster. Components like the
API server are capable of running within container images inside of a
cluster. Those components are also shipped in container images as part of the
official release process. All binaries as well as container images are available
for multiple operating systems as well as hardware architectures.
-->
Kubernetes 为每个组件提供二进制文件以及一组标准的客户端应用程序用来引导集群或与集群交互。
像 API 服务器这样的组件能够在集群内的容器镜像中运行。
作为官方发布过程的一部分，这些组件也以容器镜像的形式提供。
所有二进制文件和容器镜像都可用于多种操作系统和硬件架构。

<!-- 
## Container Images

All Kubernetes container images are deployed to the
`registry.k8s.io` container image registry.
-->
## 容器镜像  {#container-images}

所有 Kubernetes 容器镜像都被部署到 `registry.k8s.io` 容器镜像仓库。

{{< feature-state for_k8s_version="v1.24" state="alpha" >}}

<!-- 
For Kubernetes {{< param "version" >}}, the following
container images are signed using [cosign](https://github.com/sigstore/cosign)
signatures:
-->
对于 Kubernetes {{< param "version" >}}，以下容器镜像使用
[cosign](https://github.com/sigstore/cosign) 进行签名：

<!-- 
| Container Image                                                     | Supported Architectures                                                                  |
-->
| 容器镜像                                                             | 支持架构                                                                                  |
| ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| [registry.k8s.io/kube-apiserver:{{< param "fullversion" >}}][0]          | [amd64][0-amd64], [arm][0-arm], [arm64][0-arm64], [ppc64le][0-ppc64le], [s390x][0-s390x] |
| [registry.k8s.io/kube-controller-manager:{{< param "fullversion" >}}][1] | [amd64][1-amd64], [arm][1-arm], [arm64][1-arm64], [ppc64le][1-ppc64le], [s390x][1-s390x] |
| [registry.k8s.io/kube-proxy:{{< param "fullversion" >}}][2]              | [amd64][2-amd64], [arm][2-arm], [arm64][2-arm64], [ppc64le][2-ppc64le], [s390x][2-s390x] |
| [registry.k8s.io/kube-scheduler:{{< param "fullversion" >}}][3]          | [amd64][3-amd64], [arm][3-arm], [arm64][3-arm64], [ppc64le][3-ppc64le], [s390x][3-s390x] |
| [registry.k8s.io/conformance:{{< param "fullversion" >}}][4]             | [amd64][4-amd64], [arm][4-arm], [arm64][4-arm64], [ppc64le][4-ppc64le], [s390x][4-s390x] |

[0]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-apiserver
[0-amd64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-apiserver-amd64
[0-arm]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-apiserver-arm
[0-arm64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-apiserver-arm64
[0-ppc64le]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-apiserver-ppc64le
[0-s390x]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-apiserver-s390x
[1]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-controller-manager
[1-amd64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-controller-manager-amd64
[1-arm]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-controller-manager-arm
[1-arm64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-controller-manager-arm64
[1-ppc64le]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-controller-manager-ppc64le
[1-s390x]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-controller-manager-s390x
[2]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-proxy
[2-amd64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-proxy-amd64
[2-arm]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-proxy-arm
[2-arm64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-proxy-arm64
[2-ppc64le]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-proxy-ppc64le
[2-s390x]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-proxy-s390x
[3]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-scheduler
[3-amd64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-scheduler-amd64
[3-arm]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-scheduler-arm
[3-arm64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-scheduler-arm64
[3-ppc64le]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-scheduler-ppc64le
[3-s390x]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/kube-scheduler-s390x
[4]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/conformance
[4-amd64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/conformance-amd64
[4-arm]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/conformance-arm
[4-arm64]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/conformance-arm64
[4-ppc64le]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/conformance-ppc64le
[4-s390x]: https://console.cloud.google.com/gcr/images/k8s-artifacts-prod/us/conformance-s390x

<!-- 
All container images are available for multiple architectures, whereas the
container runtime should choose the correct one based on the underlying
platform. It is also possible to pull a dedicated architecture by suffixing the
container image name, for example
[`registry.k8s.io/kube-apiserver-arm64:{{< param "fullversion" >}}`][0-arm64]. All
those derivations are signed in the same way as the multi-architecture manifest lists.
-->
所有容器镜像都支持多架构，容器运行时应根据下层平台选择正确的镜像。
也可以通过给容器镜像名称加后缀来拉取适合特定架构的镜像，例如
[`registry.k8s.io/kube-apiserver-arm64:{{< param "fullversion" >}}`][0-arm64]。
所有这些派生镜像都以与多架构清单列表相同的方式签名。

<!-- 
The Kubernetes project publishes a list of signed Kubernetes container images
in [SPDX 2.2](https://spdx.dev/specifications/) format.
You can fetch that list using:
-->
Kubernetes 项目以 [SPDX 2.2](https://spdx.dev/specifications/) 格式发布已签名的 Kubernetes 容器镜像列表。
你可以使用以下方法获取该列表：

```shell
curl -Ls "https://sbom.k8s.io/$(curl -Ls https://dl.k8s.io/release/latest.txt)/release"  | awk '/Package: registry.k8s.io\// {print $3}'
```
<!-- 
For Kubernetes v{{< skew currentVersion >}}, the only kind of code artifact that
you can verify integrity for is a container image, using the experimental
signing support.

To manually verify signed container images of Kubernetes core components, refer to
[Verify Signed Container Images](/docs/tasks/administer-cluster/verify-signed-artifacts).
-->
对于 Kubernetes v{{< skew currentVersion >}}，唯一可以验证完整性的代码工件就是容器镜像，它使用实验性签名支持。

如需手动验证 Kubernetes 核心组件的签名容器镜像，
请参考[验证签名容器镜像](/zh-cn/docs/tasks/administer-cluster/verify-signed-artifacts)。

<!-- 
## Binaries

Find links to download Kubernetes components (and their checksums) in the [CHANGELOG](https://github.com/kubernetes/kubernetes/tree/master/CHANGELOG) files.

Alternately, use [downloadkubernetes.com](https://www.downloadkubernetes.com/) to filter by version and architecture.
-->
## 二进制  {#binaries}

在 [CHANGELOG](https://github.com/kubernetes/kubernetes/tree/master/CHANGELOG) 文件中找到下载 Kubernetes 组件（及其校验和）的链接。

或者，使用 [downloadkubernetes.com](https://www.downloadkubernetes.com/) 按版本和架构进行过滤。

### kubectl

<!-- overview -->

<!-- 
The Kubernetes command-line tool, [kubectl](/docs/reference/kubectl/kubectl/), allows
you to run commands against Kubernetes clusters.

You can use kubectl to deploy applications, inspect and manage cluster resources,
and view logs. For more information including a complete list of kubectl operations, see the
[`kubectl` reference documentation](/docs/reference/kubectl/).
-->
Kubernetes 命令行工具 [kubectl](/zh-cn/docs/reference/kubectl/kubectl/) 允许你对 Kubernetes 集群执行命令。

你可以使用 kubectl 部署应用程序、检查和管理集群资源以及查看日志。
有关更多信息，包括 kubectl 操作的完整列表，请参阅
[`kubectl` 参考文档](/zh-cn/docs/reference/kubectl/)。

<!-- 
kubectl is installable on a variety of Linux platforms, macOS and Windows.
Find your preferred operating system below.

- [Install kubectl on Linux](/docs/tasks/tools/install-kubectl-linux)
- [Install kubectl on macOS](/docs/tasks/tools/install-kubectl-macos)
- [Install kubectl on Windows](/docs/tasks/tools/install-kubectl-windows)
-->
kubectl 可安装在各种 Linux 平台、macOS 和 Windows 上。
在下方找到你首选的操作系统。

- [在 Linux 上安装 kubectl](/zh-cn/docs/tasks/tools/install-kubectl-linux)
- [在 macOS 上安装 kubectl](/zh-cn/docs/tasks/tools/install-kubectl-macos)
- [在 Windows 上安装 kubectl](/zh-cn/docs/tasks/tools/install-kubectl-windows)
