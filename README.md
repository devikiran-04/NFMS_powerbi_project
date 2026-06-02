# NFMS Power BI Dashboard — All Projects

A comprehensive Power BI report for monitoring **Advanced Metering Infrastructure (AMI)** across the **National Feeder Monitoring System (NFMS)** — covering all three data domains (DLP, BLP, and Events) for multiple utility circles.

> 📌 **This is the full multi-domain version** of the NFMS dashboard, combining Daily Load Profile, Billing Load Profile, and Event monitoring in a single report.

---

## 📊 Report Overview

| Property | Details |
|---|---|
| **File** | `NFMS_POWERBI_All_PROJECTS.pbix` |
| **Tool** | Microsoft Power BI Desktop |
| **Created From** | Power BI Cloud (2025.11) |
| **Report Theme** | NewExecutive |
| **Report Pages** | NFMS BLP, NFMS_DLP, NFMS_EVENTS, Page 1 |
| **Visual Types** | Line Charts |

---

## 🗂️ Data Model

The report connects to **12 data tables** across **4 utility circles** and **3 data domains**:

### Utility Circles
| Circle | Description |
|---|---|
| **AUR** | Aurangabad |
| **NASHIK** | Nashik |
| **APDCL** | Assam Power Distribution Company Ltd |
| **BIHAR** | Bihar |

### Data Domains (per circle)
| Suffix | Domain | Description |
|---|---|---|
| `_NFMS_DLP` | Daily Load Profile | Daily meter reading and audit data |
| `_NFMS_BLP` | Billing Load Profile | Billing cycle meter and transaction data |
| `_NFMS_EVENTS` | Meter Events | Tamper, outage, and alert event data |

**Full table list:**
```
AUR_NFMS_DLP       NASHIK_NFMS_DLP       APDCL_NFMS_DLP       BIHAR_NFMS_DLP
AUR_NFMS_BLP       NASHIK_NFMS_BLP       APDCL_NFMS_BLP       BIHAR_NFMS_BLP
AUR_NFMS_EVENTS    NASHIK_NFMS_EVENTS    APDCL_NFMS_EVENTS    BIHAR_NFMS_EVENTS
```

---

## 📈 Key Metrics Tracked

| Metric | Description |
|---|---|
| `audit_AUR / audit_NASHIK / audit_APDCL / audit_BIHAR` | Audit feeder count (`aud_fdr_cnt`) per circle |
| `nfms_AUR / nfms_NASHIK / nfms_APDCL / nfms_BIHAR` | NFMS meter count per circle |
| `trans_AUR / trans_NASHIK / trans_APDCL / trans_BIHAR` | Transaction meter count per circle |
| `Sum of trans_mtr_cnt` | Total transaction meter count across all circles |
| `DATE` | Billing date (`bill_date`) — X-axis for all trend charts |

---

## 📑 Report Pages

### 1. `NFMS BLP` — Billing Load Profile
Line chart trends comparing billing load profile metrics across all four utility circles. Tracks meter counts and audit data on a billing cycle basis.

### 2. `NFMS_DLP` — Daily Load Profile
Line charts comparing daily audit feeder counts (`aud_fdr_cnt`) across AUR, NASHIK, APDCL, and BIHAR over time. Useful for monitoring daily data collection coverage.

### 3. `NFMS_EVENTS` — Meter Events
Trend visualizations for meter event data (tamper alerts, outage events, etc.) across all circles, helping identify anomalies or spikes by date.

### 4. `Page 1`
Additional or summary visualizations — configurable in Power BI Desktop.

---

## 🚀 Getting Started

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (version 2025.11 or later recommended)
- Access to the NFMS backend database / data source

### Opening the Report
1. Clone or download this repository.
2. Open **Power BI Desktop**.
3. Go to **File → Open report** and select `NFMS_POWERBI_All_PROJECTS.pbix`.
4. If prompted, update data source credentials via **Home → Transform data → Data source settings**.
5. Click **Refresh** to load the latest data.

---

## 🔗 Data Source Configuration

This report is linked to a remote Power BI dataset:

| Property | Value |
|---|---|
| Dataset ID | `` |
| Report ID | `` |

> **Note:** To use this report in a local or different workspace, reconnect the data source under **Transform Data → Data Source Settings** and point it to your database or Power BI Service workspace.

---

## 📁 Repository Structure

```
├── NFMS_POWERBI_All_PROJECTS.pbix   # Main Power BI report file (all domains)
└── README.md                        # Project documentation
```

---


## 🛠️ Customization

- **Add a new circle:** Duplicate an existing table query (e.g., `AUR_NFMS_DLP`), point it to the new circle's source, and add the new series to the relevant page's line charts.
- **Filter by date range:** Use the **Filters** pane on the `DATE` field on any page.
- **Switch theme:** Go to **View → Themes** in Power BI Desktop to apply a different theme.

---

## 📝 Notes

- All date filtering is based on the `bill_date` column present across DLP, BLP, and Events tables.
- `aud_fdr_cnt` (audit feeder count) and `trans_mtr_cnt` (transaction meter count) are the primary KPIs.
- No auto-created relationships are defined — validate table relationships before publishing to Power BI Service.

---

## 📄 License

This project is intended for internal utility monitoring use. Please consult your organization's data governance policy before sharing externally.
