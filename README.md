![Project Banner](image.png)

# AI-Assisted Network Traffic Forensics for Intrusion Detection
*Developed by Ahmed Mahmoud*

AI-assisted network forensics project that implements a real-time Intrusion Detection System (IDS) powered by Machine Learning to analyze network traffic, detect anomalies, and support post-incident investigation.

---

## 🚀 Overview
The system captures and processes network traffic using **Suricata** and **Zeek**, then applies a trained **Random Forest** model to classify flows as **Normal** or **Malicious**.

It includes monitoring, visualization dashboards, and forensic outputs to help with investigation and reporting.

---

## 🧠 Key Features
- **Real-time Monitoring**: Capture and classify live traffic continuously
- **Machine Learning Detection**: Random Forest-based anomaly/threat classification
- **Visualization Dashboard**: Streamlit dashboard with graphs and alerts
- **Forensics & Reporting**: CSV logs + visual reports for post-event analysis
- **Simulation Mode**: Offline testing using simulated/recorded datasets
- **Cross-Tool Integration**: Suricata, Zeek, Wireshark workflows supported

---

## 📂 Project Structure
```text
AI-Assisted Network Traffic Forensics/
├── models/
│   ├── scaler.joblib                 # Data scaler for preprocessing
│   └── target_column.txt             # Target column used for training
│
├── p/
│   ├── confusion_matrix.png          # Model performance visualization
│   └── feature_importance.png        # Feature importance chart
│
├── suricata_logs/
│   ├── traffic.pcap                  # Raw network traffic capture
│   └── csv/
│       ├── suricata_flows.csv
│       ├── suricata_flows_with_label.csv
│       ├── suricata_flows_with_predictions.csv
│       ├── prediction_errors.csv
│       └── traffic_analysis_YYYYMMDD_HHMMSS.csv
│
├── dashboard.py                      # Streamlit dashboard
├── EDA Script.py                     # Exploratory Data Analysis
├── ml_gui.py                         # GUI version
├── run_ml_gui.bat                    # Windows launcher for GUI
├── predict.py                        # Predict new traffic samples
├── realtime_detection.py             # Real-time IDS monitoring
├── ml_gui_README.md                  # GUI documentation
└── README.md                         # Project documentation
```
---
###Detection Workflow (ASCII)

```
┌───────────────────────────────┐
│     Traffic Source            │
│ (Live Interface / PCAP File)  │
└───────────────┬───────────────┘
                ▼
┌───────────────────────────────┐
│  Suricata / Zeek Processing   │
│  - Extract events & flows     │
│  - Generate structured logs   │
└───────────────┬───────────────┘
                ▼
┌───────────────────────────────┐
│ Feature Engineering & Parsing │
│ - Clean + scale features      │
│ - Build flow-based dataset    │
└───────────────┬───────────────┘
                ▼
┌───────────────────────────────┐
│  ML Classification (RF Model) │
│ - Normal vs Malicious         │
└───────────────┬───────────────┘
                ▼
┌───────────────────────────────┐
│ Alerts + Dashboard + Reports  │
│ - Streamlit visualization     │
│ - CSV outputs for forensics   │
└───────────────────────────────┘
```
---
⚙️ Requirements

Python ≥ 3.8

Suricata

Wireshark

Python packages:

pip install pandas scikit-learn joblib matplotlib seaborn streamlit
🛠 Installation

Clone the repository:

git clone https://github.com/ahme-mahmoud/network-traffic-forensics.git
cd network-traffic-forensics


Install dependencies:

pip install -r requirements.txt

🧪 Usage
1) Data Collection (Suricata)
sudo suricata -c /etc/suricata/suricata.yaml -i eth0 --set outputs.eve-log.filename=eve.json

2) Train the Model
python ML.py

3) Real-time Detection
python realtime_detection.py --interface eth0


Simulation mode:

python realtime_detection.py --simulate

4) Dashboard
streamlit run dashboard.py


Open: http://localhost:8501

🖥 GUI (Windows)

Run:

run_ml_gui.bat


Note: Make sure dependencies are installed first:

pip install -r requirements.txt

🤖 Machine Learning Approach

Random Forest trained on flow-based features such as:

Packet counts (client/server)

Byte counts

TCP flags (SYN/ACK/RST)

Flow duration

Source/Destination ports

🔮 Future Enhancements

Threat Intelligence API integration

Support LSTM / Isolation Forest

Better analytics (heatmaps, timelines)

Automated response actions

Distributed detection for large networks

