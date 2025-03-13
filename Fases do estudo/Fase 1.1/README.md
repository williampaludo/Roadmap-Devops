# 🐧 Fase 1.1 - Fundamentos de Linux

Nesta fase, você aprenderá os conceitos essenciais do Linux, incluindo manipulação de arquivos, gerenciamento de usuários, processos e redes. O objetivo é criar uma base sólida para o trabalho com DevOps.

## 📌 Tópicos Principais

### **1️⃣ Gerenciamento de Arquivos e Diretórios**
🔹 Comandos essenciais:
```bash
ls -la       # Lista arquivos e diretórios com detalhes
pwd          # Mostra o diretório atual
cd /caminho  # Navega entre diretórios
mkdir nome   # Cria um diretório
touch nome   # Cria um arquivo vazio
rm -r nome   # Remove arquivos/diretórios
```

**🔧 Prática:**
- Navegar pelo sistema de arquivos
- Criar, copiar, mover e excluir arquivos/diretórios

### **2️⃣ Gerenciamento de Usuários e Grupos**
🔹 Comandos essenciais:
```bash
sudo useradd -m -s /bin/bash usuario  # Criar usuário
sudo passwd usuario                   # Definir senha
sudo groupadd grupo                    # Criar grupo
sudo usermod -aG grupo usuario         # Adicionar usuário ao grupo
```

**🔧 Prática:**
- Criar usuários e grupos
- Modificar permissões de acesso

### **3️⃣ Gerenciamento de Processos**
🔹 Comandos essenciais:
```bash
ps aux      # Lista processos em execução
top         # Monitoramento em tempo real
kill -9 PID # Finaliza um processo pelo PID
```

**🔧 Prática:**
- Identificar processos ativos
- Finalizar processos de teste

### **4️⃣ Gerenciamento de Rede**
🔹 Comandos essenciais:
```bash
ip a           # Exibe interfaces de rede e IPs
ping 8.8.8.8   # Testa conectividade
ss -tulnp      # Lista conexões ativas
```

**🔧 Prática:**
- Identificar endereço IP da máquina
- Testar conexão com um site externo

---

# 🚀 Desafio Prático - Linux Básico

## **🎯 Cenário**
Você foi contratado para configurar um ambiente Linux e recebeu as seguintes tarefas:

### **1️⃣ Arquivos e Diretórios**
✅ Criar um diretório `/opt/devops` e os subdiretórios `scripts`, `configs` e `logs`  
✅ Criar um arquivo `server.conf` em `configs` com o seguinte conteúdo:
```bash
server_name=devops_server
ip_address=192.168.1.100
```
✅ Copiar `server.conf` para `logs` como `server_backup.conf`
✅ Remover `server.conf` original

### **2️⃣ Usuários e Grupos**
✅ Criar um usuário `devops_user` com home `/home/devops_user` e shell `/bin/bash`
✅ Criar um grupo `devops` e adicionar `devops_user`
✅ Modificar permissões do diretório `/opt/devops` (`chmod 750` e `chown` para `devops_user`)

### **3️⃣ Processos**
✅ Listar processos em execução e filtrar os do usuário `devops_user`
✅ Finalizar um processo do `devops_user`, se houver

### **4️⃣ Rede**
✅ Listar interfaces de rede e exibir o IP
✅ Testar conexão com `8.8.8.8`
✅ Verificar portas em escuta

---
📌 **Como Enviar as Respostas:** Execute os comandos e registre os resultados em um arquivo para revisão! 🚀
