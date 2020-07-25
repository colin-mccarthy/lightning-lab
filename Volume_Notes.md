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
    - mountPath: /opt
      name: data-volume     
       
  volumes:
  - name: data-volume
+   hostPath:
+       path: /data
+       type: Directory
 ```


 
 
 

 
 
 
