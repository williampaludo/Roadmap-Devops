# Fase 1.3 - Programação e Automação

## Introdução
Nesta fase, o foco está no uso de Python ou Go para automação de tarefas, manipulação de arquivos, logs e serviços, além da introdução ao uso de APIs REST.

---
## 1. Escolhendo a Linguagem
As linguagens sugeridas para automação são:
- **Python**: Simples, com grande suporte para automação e muitas bibliotecas disponíveis.
- **Go**: Rápido e eficiente, ótimo para automação em infraestrutura e desenvolvimento de ferramentas CLI.

Para seguir com Python, certifique-se de ter o interpretador instalado:
```sh
python3 --version
```

Se for usar Go, verifique a versão instalada:
```sh
go version
```

---
## 2. Criando Scripts de Automação
A automação é fundamental para melhorar a eficiência no gerenciamento de sistemas e infraestrutura.

### **2.1 Manipulação de Arquivos com Python**

#### **Criando e lendo arquivos**
```python
# Criar um arquivo e escrever nele
with open("exemplo.txt", "w") as arquivo:
    arquivo.write("Olá, este é um teste de automação!")

# Ler o conteúdo do arquivo
with open("exemplo.txt", "r") as arquivo:
    conteudo = arquivo.read()
    print(conteudo)
```

#### **Manipulando Logs**
```python
import logging

# Configurando o logging
logging.basicConfig(filename='app.log', level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')

logging.info("Este é um log de informação")
logging.warning("Este é um log de aviso")
logging.error("Este é um log de erro")
```

---
## 3. Introdução a API REST com Python
Para interagir com APIs REST, a biblioteca `requests` do Python é amplamente utilizada.

### **3.1 Instalando a biblioteca requests**
```sh
pip install requests
```

### **3.2 Fazendo uma requisição GET**
```python
import requests

url = "https://jsonplaceholder.typicode.com/posts/1"
response = requests.get(url)

dados = response.json()
print(dados)
```

### **3.3 Enviando dados com POST**
```python
url = "https://jsonplaceholder.typicode.com/posts"
dados = {"title": "Teste", "body": "Este é um post de teste", "userId": 1}

response = requests.post(url, json=dados)
print(response.json())
```

---
## 4. Automação de Serviços no Linux
Podemos usar scripts para automatizar tarefas administrativas como reiniciar serviços e monitorar processos.

### **4.1 Verificar status de um serviço**
```python
import os

servico = "apache2"
os.system(f"systemctl status {servico}")
```

### **4.2 Criar um script para reiniciar um serviço automaticamente**
```python
import os

servico = "apache2"
os.system(f"systemctl restart {servico}")
print(f"O serviço {servico} foi reiniciado com sucesso!")
```

---
## **Conclusão**
Nesta fase, exploramos conceitos fundamentais de automação com Python e Go, abordamos a manipulação de arquivos e logs, interações com APIs REST e automação de serviços no Linux. Essas habilidades são essenciais para melhorar a eficiência no gerenciamento de infraestrutura e sistemas.

