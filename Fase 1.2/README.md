# Fase 1.2 - Redes e Segurança na AWS

## Revisão de Conceitos Fundamentais
Nesta fase, abordamos os principais conceitos de redes e segurança essenciais para a AWS, incluindo:

### **1. Conceitos de TCP/IP**
- **Camadas do modelo OSI:** Física, Enlace, Rede, Transporte, Sessão, Apresentação e Aplicação.
- **Endereçamento IPv4 e IPv6:** Endereços públicos e privados, sub-redes e CIDR.
- **Protocolos importantes:** TCP (confiável), UDP (rápido, mas sem verificação de entrega), ICMP (diagnóstico, como ping).

### **2. DNS (Domain Name System)**
- Resolve nomes de domínio para endereços IP.
- Tipos de registros: A, AAAA, CNAME, MX, TXT.
- AWS Route 53 para gerenciamento de domínios.

### **3. VPNs (Virtual Private Networks)**
- Criam conexões seguras entre redes privadas e públicas.
- Tipos: Site-to-Site (conecta redes inteiras), Client VPN (conecta usuários remotos).
- AWS Site-to-Site VPN permite conexão segura com redes locais.

### **4. Firewalls e Proxies**
- **Firewalls:** Controlam tráfego de rede com base em regras.
- **Proxies:** Intermediários entre clientes e servidores para controle e segurança.
- AWS WAF (Web Application Firewall) protege aplicações Web contra ameaças comuns.

### **5. TLS/SSL (Transport Layer Security / Secure Sockets Layer)**
- Protegem a comunicação entre clientes e servidores.
- Certificados SSL/TLS são usados para criptografia de tráfego HTTPS.
- AWS Certificate Manager (ACM) gerencia certificados SSL/TLS.

---
## Configuração de Firewalls e Regras de Segurança em Linux
Aqui estão alguns comandos para configurar firewalls no Linux:

### **1. Configuração com UFW (Uncomplicated Firewall)**
```sh
# Instalar o UFW (caso não esteja instalado)
sudo apt install ufw -y

# Ativar o firewall
sudo ufw enable

# Permitir conexão SSH (porta 22)
sudo ufw allow 22/tcp

# Permitir conexão HTTP e HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Bloquear todas as conexões de entrada
sudo ufw default deny incoming

# Permitir todas as conexões de saída
sudo ufw default allow outgoing

# Verificar regras ativas
sudo ufw status verbose
```

### **2. Configuração com IPTables**
```sh
# Bloquear todo tráfego de entrada por padrão
sudo iptables -P INPUT DROP

# Permitir conexões de entrada apenas na porta 22 (SSH)
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Permitir conexões HTTP e HTTPS
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Permitir tráfego de loopback
sudo iptables -A INPUT -i lo -j ACCEPT

# Verificar regras
sudo iptables -L -v
```

---
## Implementação de Boas Práticas de IAM e Segurança na Nuvem
A segurança na AWS é baseada no princípio de **Least Privilege (Menos Privilégios Possíveis)**. Algumas práticas recomendadas:

### **1. Criar um Usuário IAM e Evitar o Uso da Conta Root**
```sh
aws iam create-user --user-name MeuUsuario
```

### **2. Criar uma Política de Permissão Restrita**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["s3:ListBucket", "s3:GetObject"],
            "Resource": "arn:aws:s3:::meu-bucket/*"
        }
    ]
}
```

### **3. Criar um Grupo IAM e Atribuir a Política**
```sh
aws iam create-group --group-name GrupoRestrito
aws iam attach-group-policy --group-name GrupoRestrito --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

### **4. Habilitar Autenticação Multifator (MFA)**
```sh
aws iam enable-mfa-device --user-name MeuUsuario --serial-number arn:aws:iam::123456789012:mfa/MeuUsuario --authentication-code-1 123456 --authentication-code-2 654321
```

### **5. Monitoramento e Auditoria com AWS CloudTrail**
```sh
aws cloudtrail create-trail --name MeuTrail --s3-bucket-name meu-log-bucket
```

Com essas configurações, garantimos que apenas usuários autorizados tenham acesso aos recursos e podemos monitorar atividades suspeitas.

---
## **Conclusão**
Esta fase abordou os conceitos essenciais de redes e segurança na AWS, desde fundamentos de TCP/IP e VPNs até práticas avançadas de firewall e IAM. O próximo passo é aprofundar os conhecimentos em automação e programação na AWS, que será tratado na fase **1.3**.

