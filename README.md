
# Comandos para crear los deployments en Kubernetes

## Abrir Kubernetes Dashboard
```bash
minikube dashboard
```

## Microservicio: mysql8

### Forma declarativa

### Comando para generar el deployment declarativo en un archivo sin crear el recurso en el Cluster de Kubernetes
```bash
kubectl create deployment mysql8 --image=mysql:8.0.42 --port=3306 --dry-run=client -o yaml > deployment-mysql.yaml
```
### Ejecutar el deployment de forma declarativa al llamar el archivo:
```bash
kubectl apply -f deployment-mysql.yaml
```

### Forma imperativa

### Crear deployment
```bash
kubectl create deployment mysql8 --image=mysql:8.0.42 --port=3306
```

### Crear service exponiendo su puerto
```bash
kubectl expose deployment mysql8 --port=3306 --type=ClusterIP
```

## Microservicio: msvc-k8-users

### Forma declarativa
```bash
kubectl create deployment msvc-k8-users --image=luisenriquesm/msvc-k8-users:v4 --port=8001 --dry-run=client -o yaml > deployment-users.yaml
```

### Ejecutar o actualizar el deployment de forma declarativa al llamar el archivo:
```bash
kubectl apply -f deployment-users.yaml
```

### Reiniciar el deployment
```bash
kubectl rollout restart deployment msvc-k8-users
```

## Forma imperativa

### Crear deployment
```bash
kubectl create deployment msvc-k8-users --image=luisenriquesm/msvc-k8-users:v4 --port=8001
```

### Crear service exponiendo su puerto
```bash
kubectl expose deployment msvc-k8-users --port=8001 --type=LoadBalancer
```

### Exponer service
```bash
minikube service msvc-k8-users --url
```

### Actualizar Imagen del contenedor msvc-k8-users
```bash
kubectl set image deployment msvc-k8-users msvc-k8-users=luisenriquesm/msvc-k8-users:v4
```

### Escalando instancias de pod con replicas
```bash
kubectl scale deployment msvc-k8-users --replicas=3
```

### Eliminar deployment
```bash
kubectl delete deployment msvc-k8-users
```

### Elinar deployment basado en archivo yaml
```bash
kubectl delete -f deployment-users.yaml
```

### Obtener el storage class
```bash
kubectl get sc
```

### Obtener PersistentVolume
```bash
kubectl get pv
```

### Obtener PersistentVolumeClaim
```bash
kubectl get pvc
```

### Obtener Secrets
```bash
kubectl get secret
```