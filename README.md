# Mentoria k8s

- Estudos de kubernetes
- Desenvolvimento de labs de estudo


mentoria-k8s/
├── k8s/
│ ├── deployment.yaml
│ └── service.yaml
├── dockerfile
├── main.py
├── README.md
└── requirements.txt


## Descrição

Este repositório contém:

- Arquivos de deploy no Kubernetes (`deployment.yaml` e `service.yaml`)
- Um Dockerfile para build da aplicação
- Código base da aplicação em `main.py`
- Dependências no `requirements.txt`

## Como usar

### 1. Build da imagem (opcional)

Caso teste local e simples pode executar o comando:

```bash
docker build -t mentoria-k8s .
```

Criando instancia em muilti arquiteturas docker, caso quiser treinar

```bash
docker buildx create --name mentoria-k8s --use'
```

```bash
'docker build -t mentoria-k8s:v1 .'
```
Push image para o dockerhub, antes faça docker login

```bash
'docker buildx build --platform linux/amd64,linux/arm64 -t okarinadantas/mentoria-k8s:v1 --push . '
```

### Kubernetes - Comandos usados 

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### Verificar recrusos - Comandos usados

```bash
kubectl get pods
kubectl get services
```