# Troubleshooting – 10%

## Troubleshoot application failure

- Official Documentation
  - [**Task:** Troubleshoot Applications](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/)
  - [**Task:** Determine the Reason for Pod Failure](https://kubernetes.io/docs/tasks/debug-application-cluster/determine-reason-pod-failure/)
  - [**Task:** Application Introspection and Debugging](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application-introspection/)
  - [**Task:** Debug Services](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-service/)

### Helpful commands

```bash
kubectl logs mypod --previous
kubectl describe po/mypod
```

## Troubleshoot control plane failure

- Official Documentation
  - [**Task:** Troubleshoot Clusters](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)

### Helpful commands

```bash
kubectl get componentstatuses
kubectl get nodes
kubectl get pods
kubectl get pods -n kube-system
kubectl logs kube-apiserver-master -n kube-system
sudo journalctl -u kube-apiserver
```

## Troubleshoot worker node failure

- Official Documentation
  - [**Task:** Troubleshoot Clusters](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)

### Helpful commands

```bash
kubectl get componentstatuses
kubectl get nodes -o wide
top
df -h
service kubelet status
journalctl -u kubelet -f
```


## Troubleshoot networking

1. Make sure you’re connecting to the service’s cluster IP from within the cluster, not from the outside.
2. Don’t bother pinging the service IP to figure out if the service is accessible (remember, the service’s cluster IP is a virtual IP and pinging it will never work).
3. If you’ve defined a readiness probe, make sure it’s succeeding; otherwise the pod won’t be part of the service.
4. To confirm that a pod is part of the service, examine the corresponding Endpoints object with kubectl get endpoints.
5. If you’re trying to access the service through its FQDN or a part of it (for example, myservice.mynamespace.svc.cluster.local or myservice.mynamespace) and it doesn’t work, see if you can access it using its cluster IP instead of the FQDN.
6. Check whether you’re connecting to the port exposed by the service and not the target port.
7. Try connecting to the pod IP directly to confirm your pod is accepting connections on the correct port.
8. If you can’t even access your app through the pod’s IP, make sure your app isn’t only binding to localhost.

Source: http://www.kubernet.io/troubleshooting_cka_1.9.0.html