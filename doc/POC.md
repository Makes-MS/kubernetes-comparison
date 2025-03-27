# Proof of Concept: Розгортання ArgoCD на Kubernetes (k3d)

## Вступ
Цей документ описує процес розгортання GitOps-системи ArgoCD на Kubernetes-кластері, створеному за допомогою `k3d`. 

## Вимоги
- Встановлені `k3d`, `kubectl`
- Доступ до терміналу (Linux/macOS/WSL)

## Кроки розгортання

### 1. Створення Kubernetes-кластера
```sh
k3d cluster create asciiartify-poc --servers 1 --agents 2
```

### 2. Встановлення ArgoCD
```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 3. Отримання облікових даних
```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

### 4. Доступ до ArgoCD UI
Запустити проксування порту:
```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Перейти в браузері: [https://localhost:8080](https://localhost:8080)  
Логін: `admin`  
Пароль: отриманий на попередньому кроці.

---

Після виконання цих кроків система ArgoCD готова до роботи!