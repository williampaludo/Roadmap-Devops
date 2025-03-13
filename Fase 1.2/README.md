# 🖥️ Fase 1.2 - Programação e Scripting

Nesta fase, você aprenderá os fundamentos de **Bash Scripting** e **Python**, essenciais para automação e gerenciamento de servidores em um ambiente DevOps.

## 📌 Tópicos Principais

### **1️⃣ Bash Scripting**
🔹 Conceitos essenciais:
- Estrutura básica de um script (`#!/bin/bash`)
- Variáveis e argumentos
- Estruturas condicionais (`if`, `case`)
- Laços (`for`, `while`)
- Manipulação de arquivos e logs

🔹 Comandos básicos:
```bash
echo "Olá, DevOps!"  # Exibe uma mensagem
VAR="Teste"           # Declaração de variável
echo $VAR             # Exibe variável
if [ -f arquivo.txt ]; then echo "Existe!"; fi  # Verifica se o arquivo existe
for i in {1..5}; do echo "Iteração $i"; done   # Loop de 1 a 5
```

**🔧 Prática:**
- Criar um script que automatiza a criação de usuários
- Criar um script para backup de diretórios

### **2️⃣ Python para DevOps**
🔹 Conceitos essenciais:
- Estrutura de um script Python
- Manipulação de arquivos e diretórios
- Bibliotecas úteis (`os`, `sys`, `subprocess`)
- Requisições HTTP (`requests`)

🔹 Exemplo básico:
```python
import os
print("Diretório atual:", os.getcwd())
```

**🔧 Prática:**
- Criar um script que lista processos ativos
- Criar um script que verifica status de um site

---
📌 **Desafio:**
1. Criar um script Bash que automatiza a instalação de pacotes no Linux.
2. Criar um script Python que verifica se um serviço (ex: Apache) está rodando.

🚀 **Registre suas práticas no GitHub!**
