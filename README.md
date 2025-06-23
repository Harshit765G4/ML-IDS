# 🔐 Machine Learning-Based Intrusion Detection System (ML-IDS) 🚨

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Flask](https://img.shields.io/badge/Flask-Web%20Framework-lightgrey?logo=flask)
![Project Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![License](https://img.shields.io/badge/License-MIT-yellow)

A smart, real-time, flow-based Intrusion Detection System (IDS) that uses **Machine Learning** to detect and classify various network attacks like **SYN Flood**, **UDP Flood**, **ICMP Flood**, **Nmap Scans**, **Slowloris**, **Reverse Shells**, and more! 🌐🔍

---

## 📌 Project Objectives

- ✅ Build an intelligent IDS using **ML techniques**.
- ✅ Detect multiple types of **network attacks in real time**.
- ✅ Simulate attacks using **virtual machines**.
- ✅ Deploy a user-friendly **Flask-based web interface**.

---

## ⚙️ Project Architecture

[Attacker VM] ←🧠→ [Victim VM]  
       ↓ ↑  
[Traffic Capture via tcpdump / Wireshark]  
       ↓  
[CICFlowMeter → CSV Flows]  
       ↓  
[Preprocessing + ML Model Training]  
       ↓  
[Flask Web App for Prediction]


---

## 🖥️ Environment Setup

- **Host OS:** Linux (Ubuntu)
- **VMs:**  
  - Attacker: Kali Linux  
  - Victim: Ubuntu Server
- **Tools Installed:**
  - `Wireshark`, `tcpdump`, `Metasploit`, `Nmap`, `Scapy`, `CICFlowMeter`, `Python`, `Flask`, `joblib`

---

## 💣 Attack Types Simulated

> We selected attacks based on **protocol**, **port usage**, and **behavior patterns**.

| Attack Name | Command |
|-------------|---------|
| 🔥 SYN Flood | `sudo hping3 -S -p 80 --flood 192.168.100.4` |
| 🌊 UDP Flood | `sudo hping3 --udp -p 53 --flood 192.168.100.4` |
| 📶 ICMP Flood | `sudo hping3 -1 --flood 192.168.100.4` |
| 🧭 Nmap Scans | `nmap -sT`, `nmap -A -T4`, `nmap -sF`, `nmap -sN`, `nmap -sX` |
| 🐌 Slowloris | `python3 slowloris.py 192.168.100.4` |
| 🪠 Reverse Shell | `msfvenom` + `Metasploit handler` |
| 🌐 Normal Traffic | Browsing, Netcat file transfers, HTTP requests |

> Capturing done using:  
> `sudo tcpdump -i eth0 -w attack_name_capture.pcap`

---

## 📦 Dataset Generation Workflow

1. **Packet Capture:** `.pcap` files recorded using `tcpdump`/`Wireshark`
2. **Flow Conversion:** Used `CICFlowMeter` to convert to `.csv` format
3. **Labeling:** Each flow labeled by attack type
4. **Merging:** Combined 900K+ labeled flows into one dataset

---

## 🧹 Data Preprocessing

- Removed columns: `IP addresses`, `timestamps`
- Normalized numeric features
- Encoded categorical values
- Split into **Training/Test** sets (80:20)

---

## 🧠 Model Training

| Model Tried | Accuracy |
|-------------|----------|
| 🔁 Logistic Regression | 93% |
| 📊 SVM | 96% |
| 🌲 Random Forest (Selected) | ⭐ 98% |

> Final Model: **Random Forest Classifier**

✅ Evaluation Metrics:  
- Accuracy, Precision, Recall, F1-Score  
- Confusion Matrix, Classification Report

---

## 💾 Model Export

- Trained model exported as:  
  `best_ids_model.pkl`  
- Serialization via `joblib`

---

## 🌐 Flask Web Application

| Feature | Description |
|--------|-------------|
| 🧾 Input Form | Enter flow values manually |
| 🧠 Prediction | Uses trained model to classify |
| 🧩 /predict Route | Receives POST requests and returns prediction |
| 🎨 UI | Built using **Flask + Bootstrap** |

---

## 🔄 Real-Time Testing

- Simulated new attack flows live
- Captured → Converted → Entered into web form
- Validated real-time classification results

---

## 📸 Screenshots

![WhatsApp Image 2025-06-18 at 22 17 07_a61859ed](https://github.com/user-attachments/assets/99d651c6-7114-45dd-937b-ef2a7e381b5c)

![WhatsApp Image 2025-06-18 at 22 40 18_38918de5](https://github.com/user-attachments/assets/5dc0af3a-67ed-4923-9fb6-1204edb3e6d1)

---

## 🚀 How to Run the Project

```bash
# 1. Clone the repo
git clone https://github.com/Harshit765G4/ml-ids.git
cd ml-ids

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run Flask app
python app.py

# 4. Open in browser
http://127.0.0.1:5000

📚 Future Enhancements
🧠 Use Deep Learning (e.g., LSTM)

🌍 Live dashboard with real-time attack logs

📦 Auto packet capture → flow → classify pipeline

🧪 Adversarial attack resistance testing

🤝 Contributor
👨‍💻 Harshit Garg - Project Lead, Developer

🤖 Machine Learning, Dataset Generation, Flask Integration

🙌 Acknowledgements
CICFlowMeter

Metasploit Framework

Scapy

Flask

Contact Me If any Kind Of Assistance needed for the Project.
