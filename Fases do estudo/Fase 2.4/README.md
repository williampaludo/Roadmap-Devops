# Infraestrutura como Código (IaC) com Terraform

## 📌 Conceitos Fundamentais

### 🔹 O que é Infraestrutura como Código (IaC)?
- Automação e gerenciamento de infraestrutura por meio de código.
- Permite reprodutibilidade e versionamento da infraestrutura.
- Reduz erros manuais e melhora a escalabilidade.

### 🔹 Terraform
- Ferramenta declarativa para provisionamento de infraestrutura.
- Suporta múltiplos provedores (AWS, Azure, Google Cloud, etc.).
- Gerencia estado da infraestrutura através do **Terraform State**.

### 🔹 Conceitos Principais
- **Providers**: APIs de nuvem suportadas pelo Terraform.
- **Modules**: Blocos reutilizáveis de configuração.
- **State Management**: Rastreamento da infraestrutura existente.
- **Alternativas**: AWS CloudFormation, Pulumi.

---
## 🛠️ Exercícios Práticos

### 1️⃣ Instalar o Terraform
```sh
# Baixar e instalar Terraform
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install terraform

# Verificar instalação
terraform -v
```

### 2️⃣ Criar um Arquivo Terraform Básico
Crie um arquivo `main.tf` para provisionar uma instância EC2 na AWS:
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0" # ID da AMI do Ubuntu
  instance_type = "t2.micro"
}
```

### 3️⃣ Executar o Terraform
```sh
# Inicializar o Terraform
terraform init

# Validar a configuração
terraform validate

# Planejar mudanças antes da aplicação
terraform plan

# Aplicar mudanças
terraform apply -auto-approve
```

### 4️⃣ Criar um Módulo Terraform
Estruture um módulo reutilizável:
```
my-module/
├── main.tf
├── variables.tf
├── outputs.tf
```
Arquivo `main.tf` dentro do módulo:
```hcl
resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type
}
```

Arquivo `variables.tf`:
```hcl
variable "ami_id" {}
variable "instance_type" {}
```

Arquivo `outputs.tf`:
```hcl
output "instance_ip" {
  value = aws_instance.example.public_ip
}
```

### 5️⃣ Alternativas ao Terraform
- **AWS CloudFormation**: Serviço nativo AWS para provisionamento.
- **Pulumi**: Infraestrutura como código usando linguagens como Python e Go.

---
## 🚀 Conclusão
Este guia fornece uma introdução prática ao Terraform e suas alternativas. Continue explorando para aprofundar suas habilidades em IaC!

