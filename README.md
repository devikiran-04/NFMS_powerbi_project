# AMI NFMS Power BI Dashboard

A Power BI report for monitoring **Advanced Metering Infrastructure (AMI)** across the **National Feeder Monitoring System (NFMS)** — tracking audit, transaction, and event data across multiple utility circles.

---

## 📊 Report Overview

| Property | Details |
|---|---|
| **File** | `AMI_NFMS_POWERBI.pbix` |
| **Tool** | Microsoft Power BI Desktop |
| **Created From** | Power BI Cloud (2025.11) |
| **Report Pages** | NFMS_DLP, Page 1 |
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
| Suffix | Domain |
|---|---|
| `_NFMS_DLP` | Daily Load Profile data |
| `_NFMS_BLP` | Billing Load Profile data |
| `_NFMS_EVENTS` | Meter Events data |

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
| `Sum of trans_mtr_cnt` | Total transaction meter count |
| `DATE` | Billing date (`bill_date`) — used as X-axis across all trend charts |

---

## 📑 Report Pages

### 1. `NFMS_DLP` — Daily Load Profile
Line charts comparing audit feeder counts (`aud_fdr_cnt`) across all four circles over time. Each chart plots multi-series trends by billing date to visualize data coverage and gaps.

### 2. `Page 1`
Additional comparative visualizations (details configurable in Power BI Desktop).

---

## 🚀 Getting Started

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (version 2025.11 or later recommended)
- Access to the NFMS backend database / data source

### Opening the Report
1. Clone or download this repository.
2. Open **Power BI Desktop**.
3. Go to **File → Open report** and select `AMI_NFMS_POWERBI.pbix`.
4. If prompted, update the data source credentials under **Home → Transform data → Data source settings**.
5. Click **Refresh** to load the latest data.

---

## 🔗 Data Source Configuration

This report is connected to a remote Power BI dataset:

| Property | Value |
|---|---|
| Dataset ID | `` |
| Report ID | `` |

> **Note:** To use this report locally, you may need to reconnect the data source to your own database or Power BI service workspace. Update the connection string under **Transform Data → Data Source Settings**.

---

## 📁 Repository Structure

```
├── AMI_NFMS_POWERBI.pbix   # Main Power BI report file
└── README.md               # Project documentation
```

---

## 🛠️ Customization

- **Add a new circle:** Duplicate an existing table query (e.g., `AUR_NFMS_DLP`), point it to the new circle's data source, and add the new series to the line charts.
- **Change date range:** Use the **Filters** pane on the `DATE` field to limit the time window.
- **Theme:** The report uses the `Accessible_Tidal` theme for accessibility compliance.

---

## 📝 Notes

- All date filtering is based on the `bill_date` column present in every DLP table.
- The `aud_fdr_cnt` (audit feeder count) and `trans_mtr_cnt` (transaction meter count) are the primary KPIs.
- No auto-created relationships are defined — table relationships should be validated before publishing to Power BI Service.

---

## 📄 License

This project is intended for internal utility monitoring use. Please consult your organization's data governance policy before sharing externally.
