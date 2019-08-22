# Scheduling – 5%

## Use label selectors to schedule Pods

- Official Documentation
  - [**Concept:** Labels and Selectors](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)

## Understand the role of DaemonSets

DaemonSets run a pod on each and ever node in the cluster. If a new node is added, the DaemonSet deploys the pod there too. Pods managed by DaemonSets bypass the scheduler

- Official Documentation
  - [**Concept:** DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)

## Understand how resource limits can affect Pod scheduling

- Official Documentation
  - [**Concept:** Managing Compute Resources for Containers](https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/)
  - [**Task:** Configure Default Memory Requests and Limits for a Namespace](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/memory-default-namespace/)


## Understand how to run multiple schedulers and how to configure Pods to use them

- Official Documentation
  - [**Task:** Configure Multiple Schedulers](https://kubernetes.io/docs/tasks/administer-cluster/configure-multiple-schedulers/)

## Manually schedule a pod without a scheduler

- Official Documentation
  - [**Task:** Create static pods](https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/)

## Display scheduler events

```bash
kubectl get events
kubectl get events --watch
kubectl logs kube-scheduler-bk8s-node0 -n kube-system

/var/log/kube-scheduler.log on the control/master node (if schedule is standalone service)
```
