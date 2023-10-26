# Sprawozdanie nieobowiązkowe z laboratorium numer 4

Kacper Adamiak

https://github.com/Kacper-adamiak/full_stack_laboratory/tree/master/lab_4

### Zawartość pliku lab_4.yaml

```yaml
apiVersion: v1
kind: List
items:
- 
  apiVersion: v1
  kind: Namespace
  metadata:
    name: lab4
- 
  apiVersion: v1
  kind: ResourceQuota
  metadata:
    name: lab4-quota
    namespace: lab4
  spec:
    hard:
      cpu: "1000m"
      memory: "1Gi"
      pods: "5"
- 
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: restrictednginx
    namespace: lab4
  spec:
    replicas: 3
    selector:
      matchLabels:
        app: restrictednginx
    template:
      metadata:
        labels:
          app: restrictednginx
      spec:
        containers:
        - name: nginx
          image: nginx
          resources:
            requests:
              memory: "64Mi"
              cpu: "125m"
            limits:
              memory: "256Mi"
              cpu: "250m"
```

### Wykonanie pliku lab4.yaml

![](assets/uruchomienie_pliku_lab4)

### Sprawdzenie utworzenia przestrzeni nazw lab4

![](assets/sprawdzenie_przestrzeni_nazw_lab4)

### Sprawdzenie zawartości przestrzeni nazw lab4

![](assets/sprawdzenie_przestrzeni_nazw_lab4)

### Sprawdzenie zasad w przestrzeni nazw lab4

![](assets/sprawdzenie_ustawionych_zasad_dla_przestrzeni_nazw_lab4)

### Sprawdzenie zasad tworzenia restrictednginx

![](assets/sprawdzenie_deployment)