# Persistent Volume Claims

Kubernetes docs:
"A persistentVolumeClaim volume is used to mount a PersistentVolume into a Pod. 
PersistentVolumes are a way for users to "claim" durable storage (such as a GCE PersistentDisk or an iSCSI volume) 
without knowing the details of the particular cloud environment."


```diff
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: log-claim
spec:
  accessModes:
+   - ReadWriteOnce
  resources:
    requests:
+     storage: 200Mi
```
