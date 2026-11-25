[🇺🇸 English](README.md) · 🇧🇷 Português

### Oi, sou o Mateus 👋

Engenheiro de Computação, especialista em **Inteligência Artificial para a Engenharia de Testes de Software** (IARTES · UFAM, 2026). Manaus, AM · INDT.

Trabalho com **engenharia de dados** e **backend**.

#### 🗄️ Engenharia de Dados
Projetei e construí uma **plataforma de dados lakehouse do zero** (abr/2025 – atual, 70+ releases), self-hosted on-prem e com deploy híbrido na AWS:

- **Ingestão:** Apache Airflow 3 (Celery) orquestrando jobs PySpark que extraem dados de negócio de uma API REST (empresas, unidades de negócio, centros de custo/lucro, colaboradores, fornecedores), além de upload de arquivos (XLSX/CSV/JSON/Parquet)
- **Armazenamento:** tabelas Apache Iceberg em object storage compatível com S3 (MinIO / AWS S3), organizadas em camadas **Bronze → Silver → Gold** (bruto → limpo, deduplicado e mesclado incrementalmente → agregados de negócio)
- **Catálogo:** Project Nessie para versionamento estilo Git. Cada execução de pipeline grava em sua própria branch e só faz merge na `main` quando termina com sucesso
- **Consumo:** Trino para SQL federado e Apache Superset para dashboards
- **Segurança:** SSO com Keycloak (OIDC) em todas as ferramentas, acesso a tabelas por grupo no Trino via Open Policy Agent, HashiCorp Vault para segredos, Nginx/APISIX como gateway

**Desafios que resolvi**
- **Cargas isoladas e atômicas:** uma execução com falha nunca deixa a `main` pela metade, porque cada execução tem sua própria branch no Nessie
- **Camada Silver incremental:** upserts com MERGE e controle de soft delete (`is_deleted`) em vez de recargas completas
- **Uma identidade, quatro papéis:** os papéis admin / engineer / analyst / viewer valem de forma consistente no Trino, no object storage, no Superset e no Airflow. Mudanças de grupo no Keycloak chegam ao motor de consulta por webhook, sem precisar reiniciar nada
- **Gestão de segredos:** migrei as credenciais de arquivos env para o Vault (AppRole por serviço), permitindo rotacioná-las sem novo deploy
- **Operação:** backups criptografados (AES-256) no object storage e no Google Drive com retenção, pipeline de restore e relatório mensal de auditoria de acesso (logins e histórico de queries) enviado por e-mail
- **Portabilidade:** o mesmo código faz deploy em 6 topologias (dev, staging, on-prem, AWS híbrido…) com Docker Compose

#### 🛠️ Stack
**Linguagens:** Python · Java · JavaScript/TypeScript · SQL
**Backend:** Django · Django REST · FastAPI · Flask · Spring Boot
**Dados:** Apache Spark · Airflow · Iceberg · Nessie · Trino · Superset · MinIO/S3 · PostgreSQL
**Infra & Segurança:** Docker · Nginx · APISIX · Keycloak · HashiCorp Vault · OPA · Linux
