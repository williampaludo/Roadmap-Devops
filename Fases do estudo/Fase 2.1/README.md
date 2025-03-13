# Controle de Versão com Git

## 📌 Conceitos Fundamentais

### 🔹 Branches, Merges, Rebases e Conflitos
- **Branches**: Criar ramificações para desenvolvimento paralelo.
- **Merges**: Unir mudanças de diferentes branches.
- **Rebases**: Reaplicar commits para manter um histórico linear.
- **Conflitos**: Resolver manualmente conflitos ao mesclar código.

### 🔹 Hooks do Git e Automação de Fluxos de Trabalho
- **Hooks**: Scripts executados automaticamente em eventos específicos do Git.
- **Exemplos**: `pre-commit`, `pre-push`, `post-merge`.
- **Automação**: Padronizar commits, validar código antes de envio.

### 🔹 Estratégias de Versionamento
- **GitFlow**: Workflow estruturado com branches de `feature`, `develop`, `release` e `hotfix`.
- **Trunk-Based Development**: Desenvolvimento contínuo na branch principal com feature flags.

---
## 🛠️ Exercícios Práticos

### 1️⃣ Criar um repositório no GitHub/GitLab
```sh
# Inicializar um repositório
mkdir meu-repo && cd meu-repo
git init

git remote add origin https://github.com/seu-usuario/meu-repo.git
git push -u origin main
```

### 2️⃣ Criar branches para features e fazer merges
```sh
# Criar uma nova branch e alternar para ela
git checkout -b feature-login

# Adicionar arquivos, commitar e enviar alterações
git add .
git commit -m "Adiciona funcionalidade de login"
git push origin feature-login

# Mesclar com a branch principal
git checkout main
git merge feature-login
git push origin main
```

### 3️⃣ Simular um conflito e resolvê-lo manualmente
```sh
# Criar um conflito modificando a mesma linha de código em duas branches diferentes
# Ao tentar mesclar, o Git notificará sobre o conflito

git merge outra-branch
# Editar os arquivos manualmente para corrigir o conflito
# Após resolver, marcar como resolvido
git add .
git commit -m "Resolvendo conflito"
```

### 4️⃣ Implementar um hook de pre-commit para validar código
```sh
# Criar um hook de pre-commit para garantir que o código segue um padrão
mkdir -p .git/hooks
echo "#!/bin/sh
black . --check" > .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

### 5️⃣ Configurar um fluxo de GitFlow
```sh
# Instalar GitFlow
git flow init

# Criar uma nova feature
git flow feature start nova-feature

# Finalizar e mesclar com develop
git flow feature finish nova-feature
```

---
## 🚀 Conclusão
Este guia prático ajudará a consolidar o uso do Git, permitindo maior organização e eficiência no versionamento de código. Continue explorando para aprofundar suas habilidades!

