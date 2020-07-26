# Persistant Volumes


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
