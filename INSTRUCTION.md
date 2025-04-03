Create Deployment
``` k apply -f deployment.yml ```  
Create Horizontal Pod Autoscaler
``` k apply -f hpa.yml  ```

Access the app
``` http://localhost:8080/ ```

apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 2             ### How many containers will be created as a default 
  selector:
    matchLabels:          ### deployment looking for labels to know what he's managing
      app: myapp
  template:               ### Template of our app pod Deployment using to scale 
    metadata:
      labels:
        app: myapp        ### label for deployment to look up
    spec:
      containers:
      - name: todoapp
        resources:          ### Resources we need to give this container limits so he have no more no less 
          requests:
            memory: "64Mi"
            cpu: "30m"
          limits:
            memory: "128Mi"
            cpu: "50m"