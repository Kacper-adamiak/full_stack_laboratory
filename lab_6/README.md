# Sprawozdanie nieobowiązkowe z laboratorium numer 6

Kacper Adamiak

https://github.com/Kacper-adamiak/full_stack_laboratory/tree/master/lab_6

### Zawartość pliku lab_6.yaml

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
    type: proxy
  annotations:
    version: "1.9"
spec:
  replicas: 5
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx-container
        image: nginx:1.9
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 2
  revisionHistoryLimit: 3
  minReadySeconds: 5
```