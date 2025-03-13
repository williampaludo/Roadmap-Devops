# Fase 1.2 - Redes e Segurança

## Revisão de Conceitos Fundamentais
Nesta fase, abordamos os principais conceitos de redes e segurança essenciais para administração de sistemas e infraestrutura:

### **1. Conceitos de TCP/IP**
- **Camadas do modelo OSI:** Física, Enlace, Rede, Transporte, Sessão, Apresentação e Aplicação.
- **Endereçamento IPv4 e IPv6:** Endereços públicos e privados, sub-redes e CIDR.
- **Protocolos importantes:** TCP (confiável), UDP (rápido, mas sem verificação de entrega), ICMP (diagnóstico, como ping).
- **Portas e serviços:** Associar serviços comuns às suas respectivas portas (exemplo: HTTP - 80, HTTPS - 443, SSH - 22).

### **2. DNS (Domain Name System)**
- Resolve nomes de domínio para endereços IP.
- Tipos de registros: A, AAAA, CNAME, MX, TXT.
- Ferramentas para consulta DNS: `nslookup`, `dig`, `host`.

### **3. VPNs (Virtual Private Networks)**
- Criam conexões seguras entre redes privadas e públicas.
- Tipos: Site-to-Site (conecta redes inteiras), Client VPN (conecta usuários remotos).
- Configuração básica de OpenVPN e WireGuard.

### **4. Firewalls e Proxies**
- **Firewalls:** Controlam tráfego de rede com base em regras (iptables, firewalld, UFW).
- **Proxies:** Intermediários entre clientes e servidores para controle e segurança (Squid, HAProxy).
- **Filtros e bloqueios:** Controle de acesso baseado em endereços IP, portas e domínios.

### **5. TLS/SSL (Transport Layer Security / Secure Sockets Layer)**
- Protegem a comunicação entre clientes e servidores.
- Geração e uso de certificados SSL/TLS com OpenSSL.
- Como configurar HTTPS em servidores web.

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
A segurança em ambientes de nuvem exige controles de acesso adequados e monitoramento constante. Algumas práticas recomendadas:

### **1. Princípio do Menor Privilégio**
- Criar usuários e grupos com permissões mínimas necessárias.
- Evitar o uso da conta root para operações diárias.

### **2. Uso de Autenticação Multifator (MFA)**
- Configurar autenticação em dois fatores para acessos administrativos.

### **3. Monitoramento e Auditoria**
- Habilitar logs de segurança e monitorar atividades suspeitas.
- Ferramentas como auditd, fail2ban e logs do sistema para detectar acessos indevidos.

### **4. Proteção contra ataques comuns**
- Configuração de regras no firewall para bloquear IPs suspeitos.
- Uso de IDS/IPS (Intrusion Detection/Prevention Systems) como Snort e Suricata.

---
## **Conclusão**
Esta fase abordou os conceitos essenciais de redes e segurança, incluindo fundamentos de TCP/IP, VPNs, firewalls e práticas de segurança. O próximo passo é aprofundar os conhecimentos em automação e programação, que será tratado na fase **1.3**.

