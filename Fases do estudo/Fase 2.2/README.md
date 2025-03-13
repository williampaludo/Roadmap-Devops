# Containers e Orquestração

## 📌 Conceitos Fundamentais

### 🔹 Docker
- **Imagens e Contêineres**: Criar, otimizar e gerenciar contêineres.
- **Volumes e Redes**: Compartilhar dados e configurar comunicação entre contêineres.
- **Docker Compose**: Orquestrar múltiplos serviços com um único arquivo.

### 🔹 Kubernetes
- **Pods**: Unidade básica de execução no Kubernetes.
- **Deployments**: Gerenciar a replicação e atualização dos pods.
- **Services**: Expor aplicações dentro e fora do cluster.
- **Ingress**: Configurar roteamento de tráfego externo.
- **Namespaces**: Isolar e organizar recursos dentro do cluster.

### 🔹 Ferramentas de Cluster Local
- **Minikube**: Criar um cluster Kubernetes local para testes.
- **Kind**: Criar clusters Kubernetes usando contêineres Docker.

---
## 🛠️ Exercícios Práticos

### 1️⃣ Criar e Gerenciar Contêineres com Docker
```sh
# Baixar e rodar um contêiner Nginx
docker run -d --name meu-nginx -p 8080:80 nginx

# Listar contêineres em execução
docker ps

# Parar e remover o contêiner
docker stop meu-nginx
docker rm meu-nginx
```

### 2️⃣ Criar um Dockerfile e Otimizar a Imagem
Crie um arquivo `Dockerfile` para uma aplicação Python:
```dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

Agora, crie e rode a imagem:
```sh
# Construir a imagem
docker build -t minha-app .

# Rodar o contêiner
docker run -d --name app-container minha-app
```

### 3️⃣ Utilizar Docker Compose
Crie um arquivo `docker-compose.yml`:
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  app:
    build: .
    depends_on:
      - db
  db:
    image: postgres
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```
Execute o ambiente com:
```sh
docker-compose up -d
```

### 4️⃣ Configurar um Cluster Local com Minikube
```sh
# Instalar e iniciar Minikube
minikube start

# Criar um deployment no Kubernetes
kubectl create deployment hello-world --image=nginx

# Expor o deployment
kubectl expose deployment hello-world --type=NodePort --port=80

# Acessar o serviço
minikube service hello-world
```

### 5️⃣ Criar um Cluster com Kind
```sh
# Instalar e iniciar Kind
kind create cluster --name meu-cluster

# Verificar os nodes
kubectl get nodes
```

---
## 🚀 Conclusão
Este guia fornece uma base sólida para começar a trabalhar com containers e Kubernetes. Continue praticando para aprofundar seus conhecimentos!

