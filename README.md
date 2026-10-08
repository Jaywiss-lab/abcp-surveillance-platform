# 🏦 Multi-Seller ABCP Conduit & Auto ABS Digital Twin

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Streamlit-red?logo=streamlit)](#) *(Click here to view the live dashboard: [INSERT YOUR STREAMLIT LINK HERE])*

## 📌 Executive Summary
This project is an **Institutional-Grade Structured Finance Surveillance Platform**. It acts as a "Digital Twin" for a public Auto Asset-Backed Securities (ABS) transaction, designed to bridge the gap between asset-level collateral performance and liability-level liquidity risk for ABCP conduit sponsors.

By programmatically ingesting regulatory filings from the **SEC EDGAR database**, the engine allows structurers, risk managers, and rating agency analysts to simulate macroeconomic shocks and forecast liquidity facility drawdowns.

## 🎯 Business Objective & Impact
In the structured credit market, an ABCP SPV funds long-term assets (like auto loans) with short-term liabilities (Commercial Paper). 
This platform answers the critical desk question: 
> *"At what level of collateral deterioration do structural covenants (triggers) breach, causing a CP issuance freeze and forcing the Sponsor Bank to draw on its backup Liquidity Facility?"*

## ⚙️ Core Features & Architecture

### 1. Automated SEC EDGAR Data Ingestion (ETL)
* **Source:** Direct API connection to the U.S. Securities and Exchange Commission (SEC).
* **Target Filings:** Extracts historical distribution metrics from Trustee Reports (`Form 10-D`) and processes loan-level XML metadata (`Form ABS-EE`).
* **Output:** Establishes the exact *Current Pool Balance* and *Overcollateralization (OC)* baseline without manual data entry.

### 2. Macro Stress-Testing Engine
Users can apply real-time credit shocks to the collateral pool via the web interface:
* **CDR (Constant Default Rate):** Annualized percentage of the loan pool expected to default.
* **CPR (Constant Prepayment Rate):** Speed of early principal repayments, impacting the portfolio's Excess Spread generation.
* **Recovery Rate:** The percentage of defaulted balances recovered through vehicle repossession and liquidation.

### 3. Dynamic Covenant & Trigger Monitoring
* **OC Target Tracking:** The engine continuously recalculates the Overcollateralization cushion against the structural target (e.g., 12.0%).
* **Early Amortization Alerts:** If projected net losses deplete the OC cushion below the target, the platform signals a structural breach, simulating a Sequential Pay environment where cash flows are trapped to protect senior CP noteholders.

## 🛠️ Technology Stack
* **Language:** Python 3.9+
* **Data Engineering:** `Requests` (REST API routing), `JSON`, `xml.etree.ElementTree` (Streaming parsing for heavy XML files to optimize RAM usage).
* **Data Analysis:** `Pandas`
* **Frontend / UI:** `Streamlit` (Interactive analytical dashboard)

## 🚀 How to Run Locally
If you wish to run the engine on your local machine rather than the cloud dashboard:

1. Clone the repository:
```bash
git clone [https://github.com/YourUsername/abcp-surveillance-platform.git](https://github.com/YourUsername/abcp-surveillance-platform.git)
cd abcp-surveillance-platform
Install dependencies:

Bash

pip install -r requirements.txt

Run the ETL pipeline to fetch the latest SEC data:

Bash

python etl_pipeline.py

Launch the Streamlit dashboard:

Bash

streamlit run dashboard.py

Developed by Jeremy Cassagne | Designed for quantitative risk assessment in Structured Credit & Securitization.
