# Persistant Volumes

OpenShift docs:

"The Kubernetes persistent volume framework allows administrators to provision a cluster with persistent storage and gives users a way to request those resources without having any knowledge of the underlying infrastructure."


```diff
apiVersion: v1
kind: PersistentVolume
metadata:
  name: log-volume
spec:
  capacity:
+   storage: 10Gi
  accessModes:
+   - ReadWriteOnce

+ awsElasticBlockStore:
+     volumeID: <volume-id>
+     fsType: ext4
```
