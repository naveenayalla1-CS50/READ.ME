# Build an updated repo with richer Projects section and visible local logo badges
import os, zipfile, textwrap
from PIL import Image, ImageDraw, ImageFont

root = "/mnt/data/naveenayalla1-CS50_v3"
assets = os.path.join(root, "assets")
workflows = os.path.join(root, ".github", "workflows")
os.makedirs(assets, exist_ok=True)
os.makedirs(workflows, exist_ok=True)

# -------- helper to make local "logo badges" so nothing is hotlinked --------
def make_badge(text, filename, bg=(32,32,32), fg=(255,255,255), w=420, h=96, radius=20):
    img = Image.new("RGBA", (w, h), (0,0,0,0))
    d = ImageDraw.Draw(img)
    d.rounded_rectangle([0,0,w-1,h-1], radius=radius, fill=bg)
    try:
        font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 36)
    except:
        font = ImageFont.load_default()
    tw, th = d.textbbox((0,0), text, font=font)[2:]
    d.text(((w-tw)//2, (h-th)//2), text, font=font, fill=fg)
    img.save(os.path.join(assets, filename))

# Brand/tech badges (kept concise but broad)
badges = [
    ("Adobe", "adobe.png", (190,0,0)), ("Databricks", "databricks.png", (242,80,34)),
    ("AWS", "aws.png", (244,180,0), (32,32,32)), ("Azure", "azure.png", (0,120,215)),
    ("Kafka", "kafka.png", (25,25,25)), ("Kinesis", "kinesis.png", (255,140,0)),
    ("Glue", "glue.png", (149,91,165)), ("Lambda", "lambda.png", (255,102,0)),
    ("Redshift", "redshift.png", (0,88,155)), ("S3", "s3.png", (199,80,79)),
    ("Neptune", "neptune.png", (0,102,153)), ("Delta Lake", "delta.png", (0,150,136)),
    ("MLflow", "mlflow.png", (31,119,180)), ("SnapLogic", "snaplogic.png", (61,84,161)),
    ("Salesforce", "salesforce.png", (0,161,224)), ("D365", "d365.png", (0,122,122)),
    ("Eloqua", "eloqua.png", (207,17,43)), ("Power BI", "powerbi.png", (255,199,0), (32,32,32)),
    ("Tableau", "tableau.png", (48,86,166)), ("dbt", "dbt.png", (255,102,67)),
]
for b in badges:
    if len(b)==3:
        make_badge(b[0], b[1], bg=b[2])
    elif len(b)==4:
        make_badge(b[0], b[1], bg=b[2], fg=b[3])
    else:
        make_badge(b[0], b[1])

# Banner (red corporate)
W,H=3000,800
banner = Image.new("RGB",(W,H),(190,0,0))
d = ImageDraw.Draw(banner)
try:
    title_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 120)
    tag_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf", 56)
except:
    title_font = ImageFont.load_default(); tag_font = ImageFont.load_default()
title="NAVEEN AYALLA"
subtitle="Senior Data Engineer  |  GenAI • Databricks • Cloud Modernization"
tw, th = d.textbbox((0,0), title, font=title_font)[2:]
sw, sh = d.textbbox((0,0), subtitle, font=tag_font)[2:]
d.text(((W-tw)//2, H//2 - th - 20), title, font=title_font, fill="white")
d.text(((W-sw)//2, H//2 + 20), subtitle, font=tag_font, fill="white")
banner.save(os.path.join(assets, "banner.png"))

# -------- README with expanded "Projects" section w/ logo rows --------
projects_md = """
### 🚀 Complex, Real-World Projects (Selected)

#### 1) Databricks ETL Migration — Legacy SAP HANA ➜ PySpark (Adobe)
<p>
  <img src="assets/Adobe.png" height="28"/> 
  <img src="assets/Databricks.png" height="28"/> 
  <img src="assets/Delta.png" height="28"/> 
  <img src="assets/MLflow.png" height="28"/> 
  <img src="assets/SnapLogic.png" height="28"/> 
  <img src="assets/AWS.png" height="28"/>
</p>

- Replatformed dozens of SAP HANA stored procedures into **Databricks PySpark** with SCD2 history, auditability, and parity testing
- Built **DQ/metrics** layer (run logs, parity checks, incremental/full load hygiene)
- Introduced **GenAI “Mosaic” agent** to explain notebook logic, generate jobs, and accelerate troubleshooting
- **Outcome:** ~40% faster runtime, cleaner governance, lower maintenance

---

#### 2) Southwest Airlines — Kafka Streaming + AWS Neptune Design
<p>
  <img src="assets/Kafka.png" height="28"/> 
  <img src="assets/Kinesis.png" height="28"/> 
  <img src="assets/Neptune.png" height="28"/> 
  <img src="assets/Databricks.png" height="28"/> 
  <img src="assets/AWS.png" height="28"/> 
  <img src="assets/dbt.png" height="28"/>
</p>

- Designed streaming pipelines (**Kafka/Kinesis**) for passenger, gate, crew events (1M+/min)
- Modeled **graph relationships** in **AWS Neptune** for crew/route/asset connectivity
- Operationalized real-time transformations in **Databricks/dbt**, driving compliance and SLA (99.95%)
- **Outcome:** Cut tarmac/ops costs, improved real-time decisioning (–35% latency)

---

#### 3) Thermo Fisher Scientific — Life Sciences Email Marketing Analytics
<p>
  <img src="assets/Databricks.png" height="28"/> 
  <img src="assets/Delta.png" height="28"/> 
  <img src="assets/Powerbi.png" height="28"/> 
  <img src="assets/Tableau.png" height="28"/> 
  <img src="assets/dbt.png" height="28"/>
</p>

- Unified multi-channel email events (15M+/day) into Delta Lake; ran **statistical A/B tests**
- Attribution + cohort modeling; anomaly detection embedded into BI dashboards
- **Outcome:** Verified ~18% true lift, +40% insights velocity

---

#### 4) Eloqua ➜ Modern Stack Migration — End-to-End
<p>
  <img src="assets/Eloqua.png" height="28"/> 
  <img src="assets/Databricks.png" height="28"/> 
  <img src="assets/AWS.png" height="28"/> 
  <img src="assets/dbt.png" height="28"/>
</p>

- Ingested Eloqua campaign/email data; standardized into analytics-ready **dbt** models
- Built activation-ready tables and scheduled orchestration with CI/CD
- **Outcome:** Faster campaign analytics, strong data lineage & governance

---

#### 5) ADP — Revenue & Incentive Analytics
<p>
  <img src="assets/AWS.png" height="28"/> 
  <img src="assets/Powerbi.png" height="28"/> 
  <img src="assets/dbt.png" height="28"/>
</p>

- Automated payroll/revenue pipelines and incentive calculations with auditing
- Delivered finance-grade dashboards and anomaly alerts
- **Outcome:** Improved compliance visibility and reduced manual ops

---

#### 6) AAI in Adobe — Agentic Analytics & Insights
<p>
  <img src="assets/Adobe.png" height="28"/> 
  <img src="assets/Databricks.png" height="28"/> 
  <img src="assets/MLflow.png" height="28"/> 
  <img src="assets/SnapLogic.png" height="28"/>
</p>

- Built **Agentic AI** components (RAG + LLM tools) to summarize pipeline logic, surface metrics, and propose fixes
- Connected to MLflow/metadata for intelligent observability
- **Outcome:** Lower MTTR, faster onboarding, and self-documenting pipelines
""".strip()

readme = f"""
<!-- Banner -->
<p align="center">
  <img src="assets/banner.png" alt="Naveen Ayalla — Senior Data Engineer | GenAI + Databricks + Cloud Modernization" width="100%">
</p>

<h1 align="center">👋 Hi, I'm Naveen Ayalla</h1>
<h3 align="center">Senior Data Engineer | GenAI + Databricks + Cloud Modernization</h3>

<p align="center">
  <a href="https://komarev.com/ghpvc/?username=naveenayalla1-CS50">
    <img src="https://komarev.com/ghpvc/?username=naveenayalla1-CS50&label=Profile%20Views&color=blue&style=flat" alt="profile views"/>
  </a>
</p>

---

### 👨‍💻 About Me
- 🔭 **AI-powered ETL** and **cloud modernization** across Adobe, airlines, life sciences, and education
- 🚀 SAP HANA ➜ Databricks PySpark migration with SCD2 + DQ + metrics
- 🔌 Enterprise sync: **SnapLogic + D365 + Salesforce**
- 🧠 **RAG/LLM + MLflow** for agentic observability and automation
- ☁️ **AWS, Azure, Databricks, Delta Lake, Kafka/Kinesis, Neptune, dbt, BI**

---

### 🛠 Tech Stack (Local Logos — always visible)

<p>
  <img src="assets/Adobe.png" height="42"/>&nbsp;
  <img src="assets/Databricks.png" height="42"/>&nbsp;
  <img src="assets/AWS.png" height="42"/>&nbsp;
  <img src="assets/Azure.png" height="42"/>&nbsp;
  <img src="assets/Kafka.png" height="42"/>&nbsp;
  <img src="assets/Kinesis.png" height="42"/>&nbsp;
  <img src="assets/Glue.png" height="42"/>&nbsp;
  <img src="assets/Lambda.png" height="42"/>&nbsp;
  <img src="assets/Redshift.png" height="42"/>&nbsp;
  <img src="assets/S3.png" height="42"/>&nbsp;
  <img src="assets/Neptune.png" height="42"/>&nbsp;
  <img src="assets/Delta.png" height="42"/>&nbsp;
  <img src="assets/MLflow.png" height="42"/>&nbsp;
  <img src="assets/SnapLogic.png" height="42"/>&nbsp;
  <img src="assets/Salesforce.png" height="42"/>&nbsp;
  <img src="assets/D365.png" height="42"/>&nbsp;
  <img src="assets/Eloqua.png" height="42"/>&nbsp;
  <img src="assets/Powerbi.png" height="42"/>&nbsp;
  <img src="assets/Tableau.png" height="42"/>&nbsp;
  <img src="assets/dbt.png" height="42"/>
</p>

---

{projects_md}

---

### 📊 GitHub Analytics

<p align="center">
  <img height="160" src="https://github-readme-stats.vercel.app/api?username=naveenayalla1-CS50&show_icons=true&theme=radical" />
  <img height="160" src="https://github-readme-streak-stats.herokuapp.com/?user=naveenayalla1-CS50&theme=radical" />
</p>

<p align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=naveenayalla1-CS50&theme=darkhub&margin-w=10" />
</p>

---

### 🐍 Animated Contribution Snake

> Auto-generated daily via GitHub Actions

<p align="center">
  <img src="https://raw.githubusercontent.com/naveenayalla1-CS50/naveenayalla1-CS50/output/snake.svg" alt="snake animation">
</p>

---

### 🌐 Connect With Me
<p>
<a href="https://www.linkedin.com/in/naveen-ayalla-091464225/">
  <img src="https://img.shields.io/badge/LinkedIn-Naveen%20Ayalla-blue?style=for-the-badge&logo=linkedin" />
</a>
</p>

---

⭐ If you like my work, please ⭐ my repositories!
""".strip()

with open(os.path.join(root, "README.md"), "w", encoding="utf-8") as f:
    f.write(readme)

# workflow (snake)
snake = """
name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: write

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate snake.svg
        uses: Platane/snk@v3
        with:
          github_user_name: naveenayalla1-CS50
          outputs: |
            dist/snake.svg
            dist/snake-dark.svg?palette=github-dark

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
""".strip()

with open(os.path.join(workflows, "snake.yml"), "w", encoding="utf-8") as f:
    f.write(snake)

# Zip it
zip_path = "/mnt/data/naveenayalla1-CS50-expanded-projects.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for rootdir, _, files in os.walk(root):
        for file in files:
            full = os.path.join(rootdir, file)
            rel = os.path.relpath(full, os.path.dirname(root))
            z.write(full, rel)

zip_path
