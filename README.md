# ☁️ AWS FinOps Intelligence Platform

Production-grade AWS resource reconciliation and cost analysis tool.
**100% offline — no external API calls — safe for air-gapped environments.**

---

## 🚀 Run with Docker (recommended for team sharing)

```bash
docker-compose up -d
# Open: http://localhost:8080
```

## 💻 Run without Docker

Just open `index.html` in Chrome, Edge, or Firefox. Zero setup.

---

## 📦 Git Push (what goes to Git)

```
finops-platform/
├── index.html        ← Entire app (~90KB)
├── Dockerfile        ← ~200 bytes
├── docker-compose.yml
├── nginx.conf
├── .gitignore
└── README.md
```

**The Docker IMAGE (~25MB) never goes to Git. Only source code does.**
Teammates clone the repo and run `docker-compose up -d` — Docker builds locally.

---

## 🔄 4 Modes

| Mode | What it does |
|------|-------------|
| **Reconcile** | Cross-file matching — find retired/decommissioned/new resources between 2 files. Auto-detects primary key (e.g. Application Code, Resource ID). 5-tier matching: exact → normalized → contains → token-set → fuzzy |
| **Smart Query** | Single-file filter builder. Multi-condition AND filters. Group by, sort by. Cost > $X, contains EC2, region = us-east-1, etc. |
| **Cost Compare** | Two billing periods → cost delta. Spikes, drops, new resources, removed resources. $ and % delta per resource. |
| **FinOps Templates** | One-click queries: Idle resources, Top 10 spenders, EC2/S3/RDS only, Cost > $50/$100, Untagged, Zombie EC2, By Region, By Service, Custom budget |

---

## 🔑 Key Features

- **Smart primary key detection** — auto-detects Application Code, Resource ID, or any identifier column
- **All extra columns included in export** — not just the key column, full row data
- **Data Quality Report** — per-file health score, blank % detection, duplicate warnings
- **Multi-sheet XLSX support** — pick which sheet to use per file
- **Dirty data handling** — skips junk header rows, handles merged cells, BOM chars, multiple CSV delimiters
- **Export** — CSV per tab, full XLSX report with summary sheet
- **Zero external dependencies** — runs fully offline, passes Airbus security audit

---

## ⚙️ Change Port

Edit `docker-compose.yml`:
```yaml
ports:
  - "3000:8080"  # now at http://localhost:3000
```
