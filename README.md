# 🧊 Cold Chain Breach Alert & Insurance Claim Assistant

> An AI-powered Streamlit application for real-time cold-chain breach detection, severity classification, and automated generation of FDA compliance reports and insurance claim documents.

---

## Overview

Cold-chain logistics in healthcare demands strict temperature and humidity control throughout the shipment lifecycle. A single excursion can compromise product integrity, trigger regulatory action, and result in significant financial loss.

This tool ingests IoT sensor data from healthcare shipments, automatically detects temperature and humidity breaches, classifies their severity, visualizes trends across routes and products, and generates ready-to-submit FDA compliance reports and insurance claim documents — all within a single Streamlit interface.

---

## Features

- **Automated Breach Detection** — Identifies temperature excursions from IoT sensor CSV data with configurable thresholds
- **Severity Classification** — Classifies each breach as Low, Medium, High, or Critical based on duration and deviation
- **Interactive Dashboard** — Visual summary of breach events, health index trends, route-level and product-level analysis
- **FDA Report Generation** — Produces structured, FDA-style compliance reports as `.docx` files
- **Insurance Claim Generation** — Auto-fills insurance claim documents with breach metadata and impact summary
- **Data Cleaning & Feature Engineering** — Handles missing values, timestamp parsing, and derived feature creation out of the box

---

## Project Structure

```
cold-chain-assistant/
│
├── app.py                          # Streamlit frontend — main entry point
│
├── utils/
│   ├── config.py                   # Constants, thresholds, and settings
│   ├── data_loader.py              # CSV ingestion and timestamp parsing
│   ├── data_cleaner.py             # Data cleaning, feature creation, summary stats
│   ├── breach_detector.py          # Excursion detection and breach statistics
│   ├── severity_classifier.py      # Breach severity classification logic
│   ├── report_generator.py         # FDA-style report text builder
│   ├── insurance_generator.py      # Insurance claim text builder
│   ├── docx_generator.py           # Exports reports as Word (.docx) documents
│   └── visualizer.py               # Charts for temperature, humidity, health index, route/product
│
├── data/
│   └── healthcare_iot_target_dataset.csv   # Sample IoT shipment dataset
│
├── FDA_Report.docx                 # Example generated FDA report
├── Insurance_Claim.docx            # Example generated insurance claim
│
├── test_breach_detector.py         # Unit tests — breach detection
├── test_severity.py                # Unit tests — severity classification
├── test_member.py                  # Unit tests — member-level logic
│
└── requirements.txt                # Python dependencies
```

---

## Getting Started

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
git clone https://github.com/your-username/cold-chain-breach-assistant.git
cd cold-chain-breach-assistant
pip install -r requirements.txt
```

### Run the App

```bash
streamlit run app.py
```

Then open your browser at `http://localhost:8501`.

---

## Usage

1. Upload a CSV file containing IoT shipment sensor data (temperature, humidity, timestamps, route, product ID)
2. The app automatically detects breaches, classifies severity, and displays a breach dashboard
3. Review interactive charts — temperature timeline, humidity trends, health index, and route/product-level analysis
4. Download the auto-generated **FDA Report** or **Insurance Claim** as a `.docx` file directly from the UI

A sample dataset is included at `data/healthcare_iot_target_dataset.csv` to test the workflow end-to-end.

---

## Expected CSV Format

Your input CSV should contain columns similar to:

| Column | Description |
|---|---|
| `timestamp` | ISO 8601 datetime of the sensor reading |
| `temperature` | Recorded temperature (°C) |
| `humidity` | Recorded humidity (%) |
| `product_id` | Product or shipment identifier |
| `route` | Shipment route or location tag |
| `device_id` | IoT sensor device ID |

Exact column names may be configurable via `utils/config.py`.

---

## Running Tests

```bash
python -m pytest test_breach_detector.py test_severity.py test_member.py -v
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Streamlit |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib / Plotly |
| Document Generation | python-docx |
| ML / Classification | Rule-based severity classifier |

---

## Use Cases

- **Pharmaceutical logistics** — Monitor vaccine and biologics cold-chain compliance
- **Medical device shipments** — Track temperature-sensitive hardware in transit
- **Insurance teams** — Rapidly generate claim documentation after a breach event
- **Regulatory compliance** — Produce FDA-ready excursion reports without manual effort

---

## Contributing

Pull requests are welcome. For major changes, open an issue first to discuss what you'd like to change. Please ensure unit tests pass before submitting a PR.

---


