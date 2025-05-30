# Deployments with YAML
## Step-01: Kubernetes YAML Top level Objects

```yml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp3-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp3
  template: 
    metadata: # Dictionary
      name: myapp3-pod
      labels: # Dictionary 
        app: myapp3         
    spec:
      containers: # List
        - name: myapp3-container
          image: stacksimplify/kubenginx:3.0.0
          ports:
            - containerPort: 80


---

apiVersion: v1
kind: Service
metadata:
  name: deployment-nodeport-service
spec:
  type: NodePort 
  selector: 
    app: myapp3
  ports: 
    - name: http
      port: 80
      targetPort: 80
      nodePort: 31233

```
    