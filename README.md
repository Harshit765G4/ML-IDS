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

