# Application Lifecycle Management – 8%

## Understand deployments and how to perform rolling update and rollbacks

- Official Documentation
  - [Concepts: Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
  - [**Task:** Run a Stateless Aplication Using a Deployment](https://kubernetes.io/docs/tasks/run-application/run-stateless-application-deployment/)
  - [**Task:** Perform Rolling Update Using a Replication Controller](https://kubernetes.io/docs/tasks/run-application/rolling-update-replication-controller/)
  - [**Task:** Perform a Rolling Update on a Daemonset](https://kubernetes.io/docs/tasks/manage-daemon/update-daemon-set/)
  - [**Task:** Perform a Rollback on a DaemonSet](https://kubernetes.io/docs/tasks/manage-daemon/rollback-daemon-set/)
  - [**Tutorial:** Performing Rolling Update](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/)

<details>
<summary>Kubectl command Example</summary>
<p>

```bash
# Sample to create NGINX Pod YAML
# Note that including the --restart results in pod:
kubectl run mypod --dry-run --restart=Never -o yaml --image=nginx > example-pod.yaml
# Sample to create NGINX Deployment YAML
kubectl run mydeployment --dry-run -o yaml --image=nginx > example-deployment.yaml
```

</p>
</details>

## Know various ways to configure applications

- Official Documentation
  - [**Concept:** Configuration -> Secrets](https://kubernetes.io/docs/concepts/configuration/secret/)
  - Review/Perform all tasks in "Configure Pods and Containers"
    - [**Task:** Assign Memory Resources to Containers and Pods](https://kubernetes.io/docs/tasks/configure-pod-container/assign-memory-resource/)
  - Review/Perform all tasks in "Inject Data Into Applications"
    - [**Task:** Define a Command and Arguments for a Container](https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/)
- 3rd Party Hands-On
  - [Labels, annotations, selectors](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/06-k8s-labels_anotations_selectors.html)
  - [ConfigMaps](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/10-k8s-configmaps.html)
  - [Secrets](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/11-k8s-secrets.html)

## Know how to scale applications

- Official Documentation
  - [Concepts: Scaling your application](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/#scaling-your-application)
  - [**Tutorial:** Running Multiple Instances of Your App](https://kubernetes.io/docs/tutorials/kubernetes-basics/scale/scale-intro/)
  - [**Tutorial:** Interactive Tutorial - Scaling Your App](https://kubernetes.io/docs/tutorials/kubernetes-basics/scale/scale-interactive/)

## Understand the primitives necessary to create a self-healing application

The primitives necessary to create self-healing applications are [ReplicationControllers](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/), [ReplicationSets](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/), and [DaemonSets](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/). ReplicationControllers are no longer the preferred method of providing this functionality. Instead, Deployments should be used as they provide updated functionality for ReplicaSets. They provide for rolling update functionality and are declaritive, server-side, and have additional features. 

- 3rd Party Hands-On
  - [DaemonSets and NodeSelector](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/08-k8s-daemonsets.html)
  - [ReplicaSet](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/07-k8s-replicasets.html)
  - [Deployment](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/12-k8s-deployments.html) - Includes Rolling Upgrade and Rollback
  - [Self-Healing](https://multinode-kubernetes-cluster.readthedocs.io/en/latest/14-k8s-selfhealing.html)
