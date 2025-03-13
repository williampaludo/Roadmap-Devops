# CI/CD - Integração Contínua e Entrega Contínua

## 📌 Conceitos Fundamentais

### 🔹 O que é CI/CD?
- **Integração Contínua (CI)**: Processo de automação de builds e testes ao integrar código.
- **Entrega Contínua (CD)**: Automatiza a entrega do código testado para produção.
- **Desdobramento Contínuo (CD - Continuous Deployment)**: Deploys automáticos sem intervenção humana.

### 🔹 Benefícios do CI/CD
- Detecção precoce de erros.
- Redução do tempo de entrega de software.
- Processos automatizados e confiáveis.

### 🔹 Ferramentas de CI/CD
- **Jenkins**: Servidor de automação open-source.
- **GitHub Actions**: Pipelines diretamente no GitHub.
- **GitLab CI/CD**: Pipelines nativos do GitLab para automação.

---
## 🛠️ Exercícios Práticos

### 1️⃣ Criar um Pipeline Simples no GitHub Actions
Criar um arquivo `.github/workflows/ci.yml` no repositório:
```yaml
name: CI Pipeline

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout código
        uses: actions/checkout@v3
      
      - name: Configurar Python
        uses: actions/setup-python@v3
        with:
          python-version: '3.9'
      
      - name: Instalar dependências
        run: |
          pip install -r requirements.txt
      
      - name: Executar testes
        run: pytest
```

Executar o pipeline ao fazer push no repositório.

### 2️⃣ Configurar um Pipeline no GitLab CI/CD
Criar um arquivo `.gitlab-ci.yml`:
```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - echo "Compilando aplicação..."

test:
  stage: test
  script:
    - echo "Executando testes..."

deploy:
  stage: deploy
  script:
    - echo "Fazendo deploy para produção..."
  only:
    - main
```

### 3️⃣ Criar um Pipeline no Jenkins
1. Instalar o Jenkins e configurar um job freestyle.
2. Criar um `Jenkinsfile` para pipeline declarativo:
```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/seu-usuario/seu-repo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo Compilando aplicação...'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Executando testes...'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Fazendo deploy para produção...'
            }
        }
    }
}
```
3. Configurar o webhook do GitHub para acionar builds automáticos.

---
## 🚀 Conclusão
Este guia fornece uma introdução prática à CI/CD, ajudando a criar pipelines automatizados para integração e entrega contínua. Continue explorando para aprimorar seus fluxos de trabalho!

