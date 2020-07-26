# Readiness Probes

Kubernetes Docs:

"Sometimes, applications are temporarily unable to serve traffic. For example, an application might need to load large data or configuration files during startup, or depend on external services after startup. In such cases, you don't want to kill the application, but you don’t want to send it requests either. Kubernetes provides readiness probes to detect and mitigate these situations. A pod with containers reporting that they are not ready does not receive traffic through Kubernetes Services."

```diff
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
        
+ readinessProbe:
+   httpGet:
+     path: /api/ready
+     port: 8080
      
  volumes:
    - name: mypd
      persistentVolumeClaim:
        claimName: myclaim
        
```
Kubernetes Docs:

"Readiness probes are configured similarly to liveness probes. The only difference is that you use the readinessProbe 
field instead of the livenessProbe field."

```
readinessProbe:
  exec:
    command:
    - cat
    - /tmp/healthy
  initialDelaySeconds: 5
  periodSeconds: 5
```
