![Uploading image.png…]()


# AI-Assisted Network Traffic Forensics for Intrusion Detection  
*Developed by Ahmed Mahmoud*

This project implements a real-time Intrusion Detection System (IDS) powered by Machine Learning to analyze network traffic, detect anomalies, and identify cyber threats in real-time.

---

## 🚀 Overview

The system captures and processes network traffic using **Suricata** and **Zeek**, then applies a trained **Random Forest model** to classify network flows as *normal* or *malicious*.  
It includes automated monitoring, visualization dashboards, and post-incident forensic tools.

---

## 🧠 Features

- **Real-time Network Monitoring** – Continuous capture and classification of live traffic  
- **Machine Learning Detection** – Random Forest classifier for anomaly detection  
- **Traffic Visualization** – Streamlit-based dashboard with graphs and alerts  
- **Forensic Analysis** – CSV logs and visual reports for post-event analysis  
- **Simulation Mode** – Supports simulated network data for offline testing  
- **Cross-Tool Integration** – Works with Suricata, Zeek, and Wireshark  

---

## 🧩 Project Structure
```
AI-Assisted Network Traffic Forensics/
├── models/
│ ├── scaler.joblib # Data scaler for preprocessing
│ └── target_column.txt # Target column used for training
│
├── p/
│ ├── confusion_matrix.png # Model performance visualization
│ └── feature_importance.png # Top features used by the ML model
│
├── suricata_logs/
│ ├── traffc.pcap # Raw network traffic capture
│ └── csv/
│ ├── suricata_flows.csv # Raw flow data
│ ├── suricata_flows_with_label.csv # Labeled training data
│ ├── suricata_flows_with_predictions.csv # Model predictions
│ ├── prediction_errors.csv # Misclassified samples
│ └── traffic_analysis_20250419_150051.csv # Analysis summary
│
├── dashboard.py # Streamlit dashboard for visualization
├── EDA Script.py # Exploratory Data Analysis
├── ml_gui.py # GUI version of the ML system
├── run_ml_gui.bat # Batch file to launch the GUI (Windows)
├── predict.py # Predicts new traffic samples
├── realtime_detection.py # Real-time IDS monitoring
├── README.md # Project documentation
└── ml_gui_README.md # GUI-specific documentation
```
---

## ⚙️ Requirements

- **Python** ≥ 3.8  
- **Suricata IDS**  
- **Zeek (Bro)**  
- **Wireshark**  
- **Python Libraries**  


  ```bash
  pip install pandas scikit-learn joblib matplotlib seaborn streamlit
🛠️ Installation
Install Suricata, Wireshark, and Zeek following their official documentation.
Core Standard Libraries Used:
os, sys, time, json, argparse, logging, datetime, threading, subprocess, signal

These handle system interaction, logging, real-time execution, and thread control.Clone the repository:

bash
نسخ الكود
git clone https://github.com/ahme-mahmoud/network-traffic-forensics.git
cd network-traffic-forensics
Install required dependencies:

bash
نسخ الكود
pip install -r requirements.txt
🧪 Usage
1️⃣ Data Collection
Capture live traffic using Suricata:

bash
sudo suricata -c /etc/suricata/suricata.yaml -i eth0 --set outputs.eve-log.filename=eve.json
2️⃣ Train the Model
bash
python ML.py
This trains the Random Forest model and saves it under models/.

3️⃣ Real-time Detection
bash
python realtime_detection.py --interface eth0
For simulated data:

bash
python realtime_detection.py --simulate
4️⃣ Visualization Dashboard
bash
streamlit run dashboard.py
Then open http://localhost:8501.

🖥️ Running the GUI (run_ml_gui.bat)
For Windows users, you can start the complete GUI-based system by simply double-clicking:

نسخ الكود
run_ml_gui.bat
The GUI will launch automatically, allowing you to train models, visualize traffic, and detect anomalies.

⚠️ Important Note:
Make sure all Python libraries are installed before running the .bat file.
You can install them using:

bash
pip install -r requirements.txt
Once installed, the .bat file will work from the first run with no extra setup.

🤖 Machine Learning Approach
The system uses a Random Forest Classifier trained on extracted flow-based features, such as:

Packet counts (to/from client and server)

Byte counts

TCP flags (SYN, ACK, RST)

Flow duration

Source and destination ports

Each flow is labeled as normal or malicious to train the model effectively.

🔮 Future Enhancements
Integration with Threat Intelligence APIs

Support for LSTM and Isolation Forest models

Enhanced analytics with heatmaps and timelines

Automated threat response actions

Distributed detection for large-scale networks

📜 License
MIT License

👨‍💻 Contributor
Ahmed Mahmoud
Junior Penetration Tester | Cybersecurity Student @ SUT | Offensive Security | Building AI-powered Security Tools
🔗 LinkedIn
📝 Medium

🙌 Acknowledgments
Suricata Project

Wireshark

Zeek Project

scikit-learn
