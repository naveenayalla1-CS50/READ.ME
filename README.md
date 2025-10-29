<!-- Banner -->
<p align="center">
  <img src="banner.png" width="100%" alt="Naveen Ayalla — Senior Data Engineer (GenAI & Databricks)">
</p>

<h1 align="center">Hi, I'm Naveen 👋</h1>
<h3 align="center">Senior Data Engineer — Building AI-powered data platforms for enterprise scale.</h3>

<p align="center">
  <a href="https://komarev.com/ghpvc/?username=naveenayalla1-CS50">
    <img src="https://komarev.com/ghpvc/?username=naveenayalla1-CS50&label=Profile%20Views&color=blue&style=flat" alt="views"/>
  </a>
</p>

---

## 🔧 Toolbelt (local icons — put these images in /assets)
<p align="center">
  <img src="Adobe.png" height="42"/> 
  <img src="Databricks.png" height="42"/> 
  <img src="AWS.png" height="42"/> 
  <img src="Azure.png" height="42"/> 
  <img src="Delta.png" height="42"/> 
  <img src="PySpark.png" height="42"/> 
  <img src="Kafka.png" height="42"/> 
  <img src="Kinesis.png" height="42"/> 
  <img src="Neptune.png" height="42"/> 
  <img src="MLflow.png" height="42"/> 
  <img src="dbt.png" height="42"/> 
  <img src="SnapLogic.png" height="42"/> 
  <img src="Salesforce.png" height="42"/> 
  <img src="D365.png" height="42"/> 
  <img src="Eloqua.png" height="42"/> 
  <img src="Powerbi.png" height="42"/> 
  <img src="Tableau.png" height="42"/> 
  <img src="SQL.png" height="42"/> 
  <img src="Python.png" height="42"/>
</p>

---

## 🧭 Table of Contents
- [About](#about)
- [Signature Projects](#-signature-projects)
- [Playbooks & Templates](#-playbooks--templates)
- [Dashboards & Analytics](#-dashboards--analytics)
- [GitHub Stats](#github-stats)
- [Contributions](#-contributions)
- [Contact](#contact)

---

## About
I build reliable, scalable **data platforms** and **AI-assisted ETL**. My work spans **cloud migrations**, **streaming**, **data quality/observability**, and **agentic analytics** that explain pipelines in natural language.

---

## 🚀 Signature Projects

### 🔴 1) Adobe — **GenAI ETL Migration (SAP HANA ➜ Databricks)**
<p>
  <img src="Adobe.png" height="28"/> <img src="Databricks.png" height="28"/> <img src="Delta.png" height="28"/> <img src="MLflow.png" height="28"/> <img src="SnapLogic.png" height="28"/> <img src="AWS.png" height="28"/> <img src="PySpark.png" height="28"/>
</p>

**Problem**: Legacy SPs in HANA were hard to maintain and slow to iterate.  
**Solution**: Replatformed dozens of SPs into **PySpark on Databricks**, implemented **SCD2 history**, **DQ metrics**, and **parity tests**. Built a **Mosaic LLM agent** to explain notebook logic, propose fixes, and auto-generate orchestration tasks.  
**Architecture**: SnapLogic ➜ Databricks Jobs ➜ Delta Lake (Main + History) ➜ MLflow metadata ➜ DQ dashboards.  
**Impact**: ~40% faster runtime, **self-documenting** pipelines, safer deployments.

---

### ✈️ 2) Southwest Airlines — **Real-Time Ops (Kafka/Kinesis + Neptune Graph)**
<p>
  <img src="Kafka.png" height="28"/> <img src="Kinesis.png" height="28"/> <img src="Neptune.png" height="28"/> <img src="Databricks.png" height="28"/> <img src="dbt.png" height="28"/> <img src="AWS.png" height="28"/>
</p>

**Problem**: Fragmented event data (crew, gates, tickets) limited operational response.  
**Solution**: Built **Kafka/Kinesis** pipelines (1M+/min), modeled **crew/route/asset** as a **Neptune** graph, and transformed streams in **Databricks + dbt**.  
**Architecture**: Producers ➜ Kafka/Kinesis ➜ Databricks Structured Streaming ➜ dbt models ➜ Neptune graph queries.  
**Impact**: **99.95%** SLA, −35% latency in decision loops, lower ops costs.

---

### 🧪 3) Thermo Fisher — **Life Sciences Email Analytics (A/B + Attribution)**
<p>
  <img src="Databricks.png" height="28"/> <img src="Delta.png" height="28"/> <img src="Tableau.png" height="28"/> <img src="Powerbi.png" height="28"/> <img src="dbt.png" height="28"/>
</p>

**Problem**: Multi-channel email events (15M+/day) with weak attribution.  
**Solution**: Centralized events into **Delta Lake**, standardized **dbt** models, added **statistical A/B**, anomaly detection, and attribution.  
**Impact**: Verified ~**18%** true lift, **+40%** insight velocity, cleaner campaign analytics.

---

### ✉️ 4) Eloqua ➜ Modern Stack **End-to-End Migration**
<p>
  <img src="Eloqua.png" height="28"/> <img src="Databricks.png" height="28"/> <img src="AWS.png" height="28"/> <img src="dbt.png" height="28"/> <img src="SQL.png" height="28"/>
</p>

- Ingest + normalize Eloqua data, **dbt** semantic layers, **CI/CD** orchestration  
- Activation-ready tables for BI and downstream CRM sync  
- Result: Lower time-to-insight, strong lineage & governance

---

### 💸 5) ADP — **Revenue & Incentive Analytics**
<p>
  <img src="AWS.png" height="28"/> <img src="Powerbi.png" height="28"/> <img src="dbt.png" height="28"/> <img src="SQL.png" height="28"/>
</p>

- Automated payroll/revenue pipelines with **auditing & controls**
- Built trusted **finance dashboards** and anomaly alerts 
- Result: Improved compliance visibility and reduced manual ops

---

### 🎓 6) ETS — **Student Journey Analytics (GRE/TOEFL)**
<p>
  <img src="AWS.png" height="28"/> <img src="Databricks.png" height="28"/> <img src="Tableau.png" height="28"/> <img src="dbt.png" height="28"/>
</p>

- Funnel + fallout analytics across registration and prep flows  
- Scalable infra via Terraform + dbt + Delta Lake  
- Result: **+14%** registration completion

---

## 📚 Playbooks & Templates
- **Delta Lake SCD2 Upserts**: main + history pattern, audit columns, soft deletes  
- **DQ Metrics Layer**: run logs, parity checks, thresholds, anomaly detection hooks  
- **Agentic Explainers**: RAG over notebooks + metadata; “why did my job fail?” in English  
- **ELT Migration Checklist**: from legacy SPs to PySpark/dbt with test harness

---

## 📊 Dashboards & Analytics
- **Ops KPIs**: latency, SLA, error budgets  
- **Marketing Performance**: causal lift, cohorts, channel mix  
- **Finance**: incentive accruals, variance analysis, audit readiness

---

## GitHub Stats
<p align="center">
  <img height="160" src="https://github-readme-stats.vercel.app/api?username=naveenayalla1-CS50&show_icons=true&theme=radical" />
  <img height="160" src="https://github-readme-streak-stats.herokuapp.com/?user=naveenayalla1-CS50&theme=radical" />
</p>

---

## 📈 Contributions
<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=naveenayalla1-CS50&theme=github-dark" alt="Activity Graph" />
</p>

## 🐍 Animated Contribution Snake
> Auto-generated daily by GitHub Actions
<p align="center">
  <img src="https://raw.githubusercontent.com/naveenayalla1-CS50/naveenayalla1-CS50/output/snake.svg" alt="snake animation">
</p>

---

## Contact
<p>
  <a href="mailto:ust12247@adobe.com">📧 Email</a> &nbsp;|&nbsp;
  <a href="https://www.linkedin.com/in/naveen-ayalla-091464225/">🔗 LinkedIn</a>
</p>
