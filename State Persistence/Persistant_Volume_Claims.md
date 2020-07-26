# Persistent Volume Claims

Kubernetes docs:
"A persistentVolumeClaim volume is used to mount a PersistentVolume into a Pod. 
PersistentVolumes are a way for users to "claim" durable storage (such as a GCE PersistentDisk or an iSCSI volume) 
without knowing the details of the particular cloud environment."


```diff
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: myclaim
spec:
  accessModes:
+   - ReadWriteOnce
  resources:
    requests:
+     storage: 200Mi
```

# Using a PVC in a Pod

KodeKloud DOcs:
"Once you create a PVC use it in a POD definition file by specifying the PVC Claim name under persistentVolumeClaim 
section in the volumes section like this:"

```diff
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: myfrontend
      image: nginx
      volumeMounts:
+     - mountPath: "/var/www/html"
+       name: mypd
  volumes:
    - name: mypd
+     persistentVolumeClaim:
+       claimName: myclaim
```
