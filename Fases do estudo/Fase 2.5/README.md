# Monitoramento e Observabilidade

## 📌 Conceitos Fundamentais

### 🔹 O que é Monitoramento e Observabilidade?
- **Monitoramento**: Coleta e análise de métricas para identificar falhas.
- **Observabilidade**: Capacidade de entender o estado interno de um sistema a partir de logs, métricas e traces.

### 🔹 Ferramentas Principais
- **Prometheus**: Coleta e armazena métricas de aplicações e infraestrutura.
- **Grafana**: Visualização de métricas em dashboards interativos.
- **Loki**: Solução para logs eficiente e escalável.
- **ELK Stack**: Elasticsearch, Logstash e Kibana para análise de logs.

---
## 🛠️ Exercícios Práticos

### 1️⃣ Instalar Prometheus e Grafana
```sh
# Baixar e iniciar Prometheus
wget https://github.com/prometheus/prometheus/releases/latest/download/prometheus-linux-amd64.tar.gz
mkdir prometheus && tar -xvf prometheus-linux-amd64.tar.gz -C prometheus --strip-components=1
cd prometheus && ./prometheus --config.file=prometheus.yml

# Instalar Grafana
sudo apt-get install -y adduser libfontconfig1
wget https://dl.grafana.com/oss/release/grafana_8.0.6_amd64.deb
sudo dpkg -i grafana_8.0.6_amd64.deb
sudo systemctl start grafana-server
```

### 2️⃣ Configurar um Exporter no Prometheus
Edite o arquivo `prometheus.yml` para coletar métricas de um Node Exporter:
```yaml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```
```sh
# Baixar e iniciar o Node Exporter
wget https://github.com/prometheus/node_exporter/releases/latest/download/node_exporter-linux-amd64.tar.gz
mkdir node_exporter && tar -xvf node_exporter-linux-amd64.tar.gz -C node_exporter --strip-components=1
cd node_exporter && ./node_exporter &
```

### 3️⃣ Criar um Dashboard no Grafana
1. Acesse `http://localhost:3000` e faça login.
2. Adicione o Prometheus como fonte de dados (`http://localhost:9090`).
3. Crie um dashboard e adicione um painel com a consulta:
   ```promQL
   node_cpu_seconds_total{mode="idle"}
   ```
4. Salve o dashboard.

### 4️⃣ Coletar Logs com Loki
```sh
# Baixar e rodar Loki
wget https://github.com/grafana/loki/releases/latest/download/loki-linux-amd64.zip
unzip loki-linux-amd64.zip && chmod +x loki-linux-amd64
./loki-linux-amd64 -config.file=loki-config.yml &

# Configurar Grafana para visualizar logs do Loki.
```

### 5️⃣ Criar Alertas no Prometheus
Adicione um alerta no `prometheus.yml`:
```yaml
rule_files:
  - "alerts.yml"
```
Crie `alerts.yml` com a seguinte regra:
```yaml
groups:
  - name: HighCPUUsage
    rules:
      - alert: HighCPU
        expr: node_cpu_seconds_total{mode="idle"} < 20
        for: 2m
        labels:
          severity: critical
        annotations:
          description: "Uso de CPU muito alto."
```
Reinicie o Prometheus para aplicar as configurações.

---
## 🚀 Conclusão
Este guia fornece uma introdução prática ao monitoramento e observabilidade com Prometheus, Grafana, Loki e ELK Stack. Continue explorando para aprimorar seus dashboards e alertas!

