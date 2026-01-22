# Distributed Log Processing System
A Python-based distributed log processing system built using PySpark and Streamlit.
This system processes large-scale log files, performs advanced analytics, generates automated reports, and provides an interactive dashboard for real-time visualization.

🎯 Features

Distributed Processing – Scalable log processing using PySpark

Comprehensive Analytics – Error trends, severity analysis, IP & service breakdown

Alert System – Configurable threshold-based alerts

Interactive Dashboard – Streamlit-based real-time visualization

Automated Reporting – CSV & JSON report generation

Production Ready – Modular, clean, and scalable architecture

📂 Project Structure
distributed-log-system/
│
├── data/
│   └── raw_logs/                 # Input CSV log files
│
├── reports/
│   ├── csv/                      # CSV reports
│   ├── json/                     # JSON reports
│   └── alerts.log                # Alert history
│
├── src/
│   ├── spark/
│   │   ├── spark_session.py      # Spark session management
│   │   ├── ingest_logs.py        # Log ingestion
│   │   ├── parse_logs.py         # Log parsing & normalization
│   │   ├── analytics.py          # Core analytics
│   │   ├── alerts.py             # Alert system
│   │   └── export_reports.py     # Report generation
│   │
│   ├── dashboard/
│   │   └── app.py                # Streamlit dashboard
│   │
│   └── main.py                   # Main processing pipeline
│
├── config/
│   └── config.yaml               # Configuration file
│
├── requirements.txt
└── README.md

🚀 Setup
Prerequisites

Python 3.8+

Java 8+ (Required for PySpark)

Installation

Clone the repository:

git clone <repository-url>
cd distributed-log-system


Create and activate a virtual environment:

python -m venv venv
source venv/bin/activate     # Windows: venv\Scripts\activate


Install dependencies:

pip install -r requirements.txt


Verify Java installation:

java -version

📊 Input Data Format

Place CSV log files inside:

data/raw_logs/

Required Columns

timestamp – Log timestamp (multiple formats supported)

log_level – INFO, WARN, ERROR, DEBUG

message – Log message

Optional Columns

ip or IP – IP address

service – Service name

endpoint – API endpoint

Example CSV
timestamp,log_level,message,ip,service
2024-01-15 10:30:00,INFO,Request processed successfully,192.168.1.100,api-service
2024-01-15 10:31:00,ERROR,Connection timeout exception,192.168.1.101,api-service
2024-01-15 10:32:00,WARN,High response time detected,192.168.1.102,web-service

🔧 Configuration

Edit config/config.yaml to customize:

Spark Settings – Memory, executors, master

Input/Output Paths

Alert Thresholds

Analytics Parameters

Dashboard Auto-refresh Settings

🏃 Running the System
1️⃣ Run Full Pipeline
python src/main.py

2️⃣ Run Individual Modules (Optional)
python src/spark/ingest_logs.py
python src/spark/parse_logs.py
python src/spark/analytics.py
python src/spark/alerts.py
python src/spark/export_reports.py

📊 Launch Dashboard

Start the Streamlit dashboard:

streamlit run src/dashboard/app.py


Access at:
👉 http://localhost:8501

📈 Dashboard Features

Key Metrics

Total logs

Total errors

Error rate

Active alerts

Visualizations

Errors over time (line chart)

Top error types (bar chart)

Errors by IP

Errors by service

Filters

Date range

Log level selection

Alert Panel

Recent alerts with timestamps

Auto Refresh

Live dashboard updates

📋 Generated Reports
CSV Reports (reports/csv/)

errors_by_type.csv

errors_by_hour.csv

top_errors.csv

errors_per_ip.csv

errors_per_service.csv

JSON Reports (reports/json/)

error_trends.json

errors_by_day.json

errors_by_severity.json

Alert Log

reports/alerts.log

🔔 Alert System

Alerts are triggered for:

High Error Rate (default: >10%)

High Error Count (default: >100)

Critical Errors (default: >5)

Alerts are:

Logged to file

Printed to console

Displayed in dashboard

🛠️ Development Guidelines

No Pandas for Processing – All transformations use PySpark

Modular Codebase – Easy to extend analytics & alerts

Config-Driven – YAML-based configuration

Caching & Optimization – Spark caching enabled

Adding New Analytics

Add logic in analytics.py

Call function in run_all_analytics()

Export results via export_reports.py

Visualize in dashboard/app.py

🚀 Deployment
Local

Uses local[*] Spark master by default

Cluster Deployment

Update config.yaml:

spark:
  master: spark://your-cluster:7077


Supports:

AWS EMR

Databricks

On-prem Spark clusters

🐛 Troubleshooting
Java Not Found

Install Java 8+

Set JAVA_HOME

Spark Errors

Verify Java installation

Check Spark configs

Dashboard Not Updating

Ensure pipeline ran successfully

Verify report paths

📄 License

This project is provided as-is for educational and development purposes.

👥 Contributing

Contributions are welcome!

You can enhance this project by adding:

Advanced analytics

New visualizations

Enhanced alerting logic

Performance optimizations

🚀 Built with PySpark & Streamlit
