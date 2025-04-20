# 📊 Apache Logs – Análise SOC com ELK Stack

[![Status](https://img.shields.io/badge/status-concluído-brightgreen)]()
[![Nível](https://img.shields.io/badge/nível-iniciante-blue)]()
[![Ferramentas](https://img.shields.io/badge/stack-ELK%20Stack-orange)]()

## 📦 Estrutura do Projeto

```bash
log-analysis-elk-stack/
├── kibana_dashboard/                 <- Prints das visualizações e dashboard
├── logstash/                        <- Configuração de Logstash e logs
│   ├── apache_logs.log              <- Logs de exemplo
│   └── pipeline.conf                <- Configuração do pipeline do Logstash
└── docker-compose.yml               <- Arquivo para executar o projeto com Docker, configurando os containers necessários para rodar o ELK Stack de forma simplificada
```

## 🧠 Objetivo
Simular um cenário SOC utilizando a ELK Stack (Elasticsearch, Logstash e Kibana) para analisar logs de acesso Apache. O objetivo é identificar possíveis ataques, como tentativas de exploração automatizada, negação de serviço (DoS), e reconhecimento de rede.

## 📸 Evidências da Análise

### 🖼️ 1. Dashboard Geral
![Dashboard](./kibana_dashboard/dashboard.png)
- Visão macro do ambiente: IPs, requisições por minuto, status HTTP e tendências.  
- Ideal para uma análise rápida e para identificar anomalias visuais.

---

### 🖼️ 2. Top 10 IPs Suspeitos
![Top 10 IPs](./kibana_dashboard/top-10-ips.png)
- Alguns IPs fazem um número absurdo de requisições.  
- Padrão típico de bots ou scanners automáticos.  
- Pode indicar mapeamento de endpoints ou testes de vulnerabilidades.

---

### 🖼️ 3. Linha do Tempo dos IPs
![Top IPs Timeline](./kibana_dashboard/top-ips-timeline.png)
- Picos de acesso em horários específicos ⏰.  
- Indica scripts programados ou ciclos de execução automáticos.  
- 💣 Potencial ataque agendado ou reconhecimento sistemático.

---

### 🖼️ 4. Requisições por Minuto
![Requests per Minute](./kibana_dashboard/requests-per-minute.png)
-  Picos evidentes de tráfego.
-  Pode sugerir ataques leves de DoS ou fuzzing.
-  Sobrecarrega sistemas frágeis.

---

### 🖼️ 5. Códigos de Status HTTP
![HTTP Status Codes](./kibana_dashboard/http-status-codes.png)
-  404 excessivos → tentativa de descobrir URLs escondidas.
-  500 elevados → possíveis falhas causadas por requisições maliciosas.
-  Ideal para capturar comportamento de exploração automatizada.

---

## ✅ Conclusão
O uso do ELK Stack permitiu uma análise eficiente dos logs Apache, identificando padrões suspeitos e ajudando na detecção de possíveis atividades maliciosas. A visualização das informações no Kibana torna a análise SOC mais dinâmica, permitindo uma resposta rápida a incidentes.

## 🧰 Ferramentas Usadas
- **Kibana** – Visualizações e dashboard interativo
- **Elasticsearch** – Armazenamento e indexação dos logs
- **Logstash** – Ingestão e parsing dos logs Apache
- **Apache Access Logs** – Dados analisados
- **Docker** – Para facilitar a execução do projeto
