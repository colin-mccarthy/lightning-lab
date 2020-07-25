At its core, a volume is just a directory, possibly with some data in it, which is accessible to the Containers in a Pod. How that directory comes to be, the medium that backs it, and the contents of it are determined by the particular volume type used.

To use a volume, a Pod specifies what volumes to provide for the Pod (the .spec.volumes field) and where to mount those into Containers (the .spec.containers[*].volumeMounts field).


```diff
apiVersion: apps/v1
kind: Pod
metadata:
  name: command-test
  namespace: default
spec:
  containers:
  - image: alpine
    name: alpine
    command: ["bin/shell","-c"]
    args: ["shuff -i 0-100 -n >> /opt/number.out;"]
    volumeMounts:
+   - mountPath: /opt
+     name: data-volume 

  volumes:
  - name: data-volume
+   hostPath:
+       path: /data
+       type: Directory
```


    
       

# AWS Elastic Block Storage
 
```diff
  volumes:
  - name: data-volume
  
+   awsElasticBlockStore:
+       volumeID: <volume-id>
+       fsType: ext4
 ```
 
 
 

 
 
 
