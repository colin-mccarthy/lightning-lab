# Liveness Probes

Kubernetes Docs:

"Sometimes, you have to deal with legacy applications that might require an additional startup time on their first initialization. In such cases, it can be tricky to set up liveness probe parameters without compromising the fast response to deadlocks that motivated such a probe. The trick is to set up a startup probe with the same command, HTTP or TCP check, with a failureThreshold * periodSeconds long enough to cover the worse case startup time."

```
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: myfrontend
      image: nginx
      ports:
        - containerPort: 8080
      volumeMounts:
      - mountPath: "/var/www/html"
        name: mypd
        
+ livenessProbe:
+   httpGet:
+     path: /api/ready
+     port: 8080
+   failureThreshold: 1
+   periodSeconds: 10


+ startupProbe:
+   httpGet:
+     path: /api/ready
+     port: 8080
+   failureThreshold: 30
+   periodSeconds: 10
      
  volumes:
    - name: mypd
      persistentVolumeClaim:
        claimName: myclaim
        
```
        
