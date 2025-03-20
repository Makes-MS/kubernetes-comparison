# Демонстрація "Hello World" на Kubernetes

Цей приклад демонструє, як розгорнути простий додаток "Hello World" на локальному Kubernetes кластері за допомогою minikube, kind та k3d.

## Мінімальні вимоги
- Інстальований Docker
- Інстальовані інструменти Kubernetes: minikube, kind, k3d

## Кроки для розгортання

### Для Minikube
```bash
minikube start
kubectl run hello-world --image=nginx --port=80
kubectl expose pod hello-world --port=8080
```

### Для Kind
```bash
kind create cluster
kubectl run hello-world --image=nginx --port=80
kubectl expose pod hello-world --port=8080
```

### Для k3d
```bash
k3d cluster create
kubectl run hello-world --image=nginx --port=80
kubectl expose pod hello-word --port=8080
```