# Mentoria k8s

- Estudos de kubernetes
- Desenvolvimento de labs de estudo

```
mentoria-k8s/
├── k8s/
│ ├── deployment.yaml
│ └── service.yaml
├── dockerfile
├── main.py
├── README.md
└── requirements.txt
```

## Descrição

Este repositório contém:

- Arquivos de deploy no Kubernetes (`deployment.yaml` e `service.yaml`)
- Um Dockerfile para build da aplicação
- Código base da aplicação em `main.py`
- Dependências no `requirements.txt`

## Como usar

### 1. Build da imagem

Caso teste local e simples pode executar o comando:

```bash
docker build -t mentoria-k8s .
```

Criando instancia em muilti arquiteturas docker, caso quiser treinar

```bash
# Docker build
docker build -t mentoria-k8s .
docker buildx create --name mentoria-k8s --use'
docker build -t mentoria-k8s:v1 .
#Docker build/push no DockerHub
docker buildx build --platform linux/amd64,linux/arm64 -t okarinadantas/mentoria-k8s:v1 --push . 
```

### Kubernetes - Comandos usados 

```bash

# Criar namespace e aplicar manifestos
kubectl create ns mentoria-k8s
kubectl apply -f k8s/deployment.yaml -n mentoria-k8s
kubectl apply -f k8s/service.yaml -n mentoria-k8s

# Validar Deployment
kubectl get deployments -n mentoria-k8s
kubectl describe deployment hello-k8s -n mentoria-k8s

# Validar Pods
kubectl get pods -n mentoria-k8s

# Acessar aplicação
curl http://localhost:30080
# ou via navegador
kubectl port-forward pod/<nome-do-pod> 5000:5000 -n mentoria-k8s

# Scaling manual
kubectl scale deployment hello-k8s --replicas=3 -n mentoria-k8s
kubectl get pods -n mentoria-k8s -w   # watch em tempo real

# Auto Healing — deletar pod manualmente
kubectl delete pod <nome-do-pod> -n mentoria-k8s
kubectl get pods -n mentoria-k8s -w   # observar recriação automática
```
