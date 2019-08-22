# Installation, Configuration & Validation – 12%

## Design a Kubernetes Cluster

- Official Documentation
  - [Cluster Administration Overview](https://kubernetes.io/docs/concepts/cluster-administration/cluster-administration-overview/)

## Install Kubernetes Masters and Nodes

- Official Documentation
  -[Creating a single control-plane cluster with kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)
- 3rd Party Hands-On
  - [Kubernetes Installation](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/01-k8s-installation.html)

## Configure secure cluster communications

**NOTE:** "If you install Kubernetes with kubeadm, the certificates that your cluster requires are automatically generated." - from the official documentation -> PKI Certificates and requirements

- Official Documentation
  - [PKI certificates and requirements](https://kubernetes.io/docs/setup/best-practices/certificates/)

## Configure a highly-available Kubernetes cluster

- Official Documentation
  - [Options fo Highly Available topology](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/ha-topology/)
  - [Creating HIghly Available clusters with kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/)

## Know where to get the Kubernetes release binaries

- Official Documentation
  - [ Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Provision underlying infrastructure to deploy a Kubernetes cluster

There are many options here including, but not limited to:

- Physical hosts
- VMs
- SaaS offerings such as GKE, AKE, Cloud PKS, etc...

 In any case, you'll need a [Container Runtime](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) installed before installing Kubernetes.

## Choose a network solution

- Official Documentation
  - [Cluster Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
  - [Getting Started: Creating a single control-plane cluster with kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/) - has CNI urls

## Choose your Kubernetes infrastructure configuration

- Official Documentation
  - [Getting started](https://kubernetes.io/docs/setup/)

## Run end-to-end tests on your cluster

### Use e2e from kubernetes

```bash
# Remove go 1.6.x and Install current go if not already installed
# Version 1.6 (default installed by apt-get install golang-go from default repo) has issue:
# package context: unrecognized import path "context" (import path does not begin with hostname)
sudo su -
# Repo instructions from: https://github.com/golang/go/wiki/Ubuntu
add-apt-repository -y ppa:longsleep/golang-backports
apt-get update
apt-get install -y golang-go
mkdir -p ~/go; echo "export GOPATH=$HOME/go" >> ~/.bashrc
echo "export PATH=$PATH:$HOME/go/bin:/usr/lib/go/bin" >> ~/.bashrc
echo "export GOROOT=/usr/lib/go" >> ~/.bashrc

source ~/.bashrc
# The following are steps are from:
# https://events.linuxfoundation.org/wp-content/uploads/2017/11/Verify-Your-Kubernetes-Clusters-with-Upstream-e2e-Tests-Kenichi-Omichi-NEC.pdf
# Now get the server version of your cluster:
kubectl version
# Download the k8s source code and checkout the same version as your cluster
go get k8s.io/kubernetes
cd $GOPATH/src/k8s.io/kubernetes
git checkout refs/tags/v1.15.2
# Build the e2e test binary
go run hack/e2e.go -- --build
# Now choose provider type: skeleton, local, gce, gke, aws
# Skeleton - export KUBE_MASTER_IP and KUBE_MASSTER
export KUBE_MASTER_IP="192.168.1.60:6443"
export KUBE_MASTER=k8m1
export KUBECONFIG=$HOME/admin.conf
# Run ALL e2e tests
go run hack/e2e.go -- --provider=skeleton --test
# Run ONLY CONFORMANCE Tests
export KUBERNETES_CONFORMANCE_TEST=true
go run hack/e2e.go -- --provider=skeleton --test --test_args="--ginkgo.focus=\[Conformance\]"
```

Alternate method:

```bash
go get -u k8s.io/test-infra/kubetest
kubetest --extract=v1.15.2
export KUBE_MASTER_IP="192.168.1.60:6443"
export KUBE_MASTER=k8m1
export KUBECONFIG=$HOME/admin.conf
cd kubernetes
kubetest --test --provider=skeleton > output.txt

#For Conformance Test run this:
kubetest --test --provider=skeleton --test_args="--ginkgo.focus=\[Conformance\]" > output.txt
```

### Manual

Verify that you can run these checked items

1. Deployments can run
2. Pods can run
3. Pods can be directly accessed
4. Logs can be collected
5. Commands run from Pod
6. Services can provide access
7. Nodes are healthy
8. Pods are healthy

```bash
kubectl get componentstatuses
kubectl get cluster-info
kubectl run nginx --image=nginx
kubectl get deployments
kubectl get pods
kubctl get pods -n kube-system
kubectl port-forward nginx 8081:80
curl --head http://127.0.0.1:8081
kubectl logs nginx
kubectl exec -it nginx --nginx -v
kubectl expose deployment nginx --port 80 --type NodePort
kubectl get services
curl -I localhost:<node port>
kubectl get nodes
kubectl describe nodes
kubectl describe pods
```

## Analyze end-to-end test results

## Run Node end-to-end Tests

- Official Documentation
  - [Validate node setup](https://kubernetes.io/docs/setup/best-practices/node-conformance/)

## Install and use kubeadm to install, configure, and manage Kubernetes clusters

- Official Documentation
  - [Installing Kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)

- 3rd Party Hands-On
  - [Kuberentes Installation](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/01-k8s-installation.html)
