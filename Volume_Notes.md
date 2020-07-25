```
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
```      
 ```diff       
  volumes:
  - name: data-volume
+   hostPath:
+       path: /data
+       type: Directory
 ```


 
 
 
```diff
{
  "some_param": true,
+ "another_param": true,
  "head_sha": "f83a356604ae3c5d0"
}
```
 
 
 
