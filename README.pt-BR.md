[English](README.md) · Português

### Oi, sou o Mateus

Engenheiro de Computação, especialista em **Inteligência Artificial para a Engenharia de Testes de Software** (IARTES · UFAM, 2026). Manaus, AM · INDT.

Trabalho com **engenharia de dados**, **automação de testes** e **backend**.

#### Engenharia de Dados
Projetei e construí uma **plataforma de dados lakehouse do zero** (abr/2025 – atual, 70+ releases), self-hosted on-prem e com deploy híbrido na AWS:

- **Ingestão:** Apache Airflow 3 (Celery) orquestrando jobs PySpark que extraem dados de negócio de uma API REST (empresas, unidades de negócio, centros de custo/lucro, colaboradores, fornecedores), além de upload de arquivos (XLSX/CSV/JSON/Parquet)
- **Armazenamento:** tabelas Apache Iceberg em object storage compatível com S3 (MinIO / AWS S3), organizadas em camadas **Bronze → Silver → Gold** (bruto → limpo, deduplicado e mesclado incrementalmente → agregados de negócio)
- **Catálogo:** Project Nessie para versionamento estilo Git. Cada execução de pipeline grava em sua própria branch e só faz merge na `main` quando termina com sucesso
- **Consumo:** Trino para SQL federado e Apache Superset para dashboards
- **Segurança:** SSO com Keycloak (OIDC) em todas as ferramentas, acesso a tabelas por grupo no Trino via Open Policy Agent, HashiCorp Vault para segredos, Nginx/APISIX como gateway
- **Alertas:** meu trabalho mais recente é um sistema de alertas para a plataforma

#### Automação de Testes (SDET)
- Criei ferramentas com agentes de IA para criação, análise e execução de casos de teste
- Automatizei a criação de tasks a partir de user stories, trabalho que virou o artigo *An Approach to Automating User Story Management for Testing Process Optimization in Large Distributed Teams*
- Automatizei processos do dia a dia do time e criei dashboards para acompanhá-los

Também cuido da infraestrutura de uma plataforma de ferramentas para desenvolvedores de testes manuais e automatizados:
- **SSO:** login único com OAuth 2.0 em todas as ferramentas da plataforma
- **Servidor:** gerencio o servidor que hospeda as ferramentas, com monitoramento no Grafana
- **Processamento assíncrono:** RabbitMQ como broker central das filas assíncronas, consumidas por workers Celery
- **Servidores de aplicação:** Gunicorn gerenciando workers Uvicorn, para que as aplicações usem todos os núcleos de CPU, workers travados ou com falha sejam substituídos automaticamente e os workers sejam reciclados periodicamente, mantendo o uso de memória estável
- **Nginx:** um gateway que atua como proxy reverso e load balancer, e um Nginx por aplicação servindo seus arquivos estáticos. O gateway continua no ar e roteando mesmo quando um dos serviços por trás dele cai

#### Publicações e apresentações
- *An Approach to Automating User Story Management for Testing Process Optimization in Large Distributed Teams*
- *Otimização da Geração de Casos de Teste em Aplicativos Móveis via Aprendizado por Reforço e Agentes de IA*. Trabalho da pós, apresentado no [SAST · CBSoft 2026](https://cbsoft.sbc.org.br/2026/en/symposiums/sast/event/)

#### Stack
**Linguagens:** Python · Java · JavaScript/TypeScript · SQL

**Backend:** Django · Django REST · FastAPI · Spring Boot · Celery · RabbitMQ

**Dados:** Apache Spark · Airflow · Iceberg · Nessie · Trino · Superset · MinIO/S3 · PostgreSQL

**Testes & IA:** Android · Aprendizado por reforço · Agentes de IA

**Infra & Segurança:** Docker · Nginx · APISIX · Gunicorn · Uvicorn · Grafana · OAuth 2.0 · Keycloak · HashiCorp Vault · OPA · Linux
