# Storage – 7%

## Understand persistent volumes and know how to create them

- Official Documentation
  - [**Concept:** Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)

## Understand access modes for volumes

- Official Documentation
  - [**Concept:** Persistent Volumes -> Persistent Volumes -> Access Modes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)
  ```bash
  The access modes are:

  ReadWriteOnce – the volume can be mounted as read-write by a single node
  ReadOnlyMany – the volume can be mounted read-only by many nodes
  ReadWriteMany – the volume can be mounted as read-write by many nodes
  In the CLI, the access modes are abbreviated to:

  RWO - ReadWriteOnce
  ROX - ReadOnlyMany
  RWX - ReadWriteMany
  ```

## Understand persistent volume claims primitive

- Official Documentation
  - [**Concept:** Persistent Volumes -> PersistentVolumeClaims](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)

## Understand Kubernetes storage objects

- Official Documentation
  - [**Concept:** Volumes](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes)
  ```bash
  Kubernetes supports several types of Volumes:

  awsElasticBlockStore
  azureDisk
  azureFile
  cephfs
  cinder
  configMap
  csi
  downwardAPI
  emptyDir
  fc (fibre channel)
  flexVolume
  flocker
  gcePersistentDisk
  gitRepo (deprecated)
  glusterfs
  hostPath
  iscsi
  local
  nfs
  persistentVolumeClaim
  projected
  portworxVolume
  quobyte
  rbd
  scaleIO
  secret
  storageos
  vsphereVolume
  We welcome additional contributions.


  ```

## Know how to configure applications with persistent storage

- Official Documentation
  - [**Concept:** Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
  - [**Task:** Configure a Pod to Use a PersistentVolume for Storage](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/)
