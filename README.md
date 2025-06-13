# ML-IDS


Steps :- 
1. Project Planning & Objective Definition

-> Identified the need for a smarter, ML-based IDS.

-> Defined project aim: Detect various attacks in real time using machine learning.

2. Environment Setup

-> Set up host machine and two virtual machines (Attacker: Kali, Victim: Ubuntu).

-> Installed tools: Wireshark, Metasploit, Nmap, Scapy, CICFlowMeter, Flask, Python, joblib.

3. Attack Type Selection

-> Selected multiple attacks: SYN flood, UDP flood, ICMP flood, Nmap scans, FIN/NULL/Xmas scans, protocol obfuscation, reverse shell, payload injection.

4. Packet Capture

-> Generated traffic using tools like Metasploit, Nmap, Scapy.

-> Captured packets using Wireshark and tcpdump into .pcap files.

5. Flow Conversion

-> Converted .pcap files to flow-based .csv using CICFlowMeter.

6. Labeling and Combining Dataset

-> Labeled each flow file with its corresponding attack or "normal".

-> Combined all labeled .csv files into a single dataset (~900,000+ rows).

7. Data Preprocessing

-> Dropped irrelevant columns (e.g., IPs, timestamps).

-> Normalized features.

-> Encoded categorical features if needed.

8. Model Selection and Training

-> Tried multiple models: Random Forest, SVM, Logistic Regression.

-> Finalized Random Forest Classifier based on best accuracy.

9. Model Evaluation

-> Split data into training and test sets.

-> Evaluated using accuracy, precision, recall, F1-score.

-> Achieved ~98% accuracy.

10. Model Saving

-> Exported the trained model as best_ids_model.pkl using joblib.

11. Flask Web Application Development

-> Built a simple web interface using Flask and Bootstrap.

-> Created input form to enter flow features manually.

12. Model Integration with Flask

-> Loaded the trained model in Flask backend.

-> Created /predict route to classify input and return prediction.

13. Testing the Web App

-> Ran the Flask server.

-> Entered sample flow inputs into the web form.

-> Validated predictions (Normal/Attack Type).

14. Real-Time Simulation

-> Simulated new attacks live.

-> Captured and converted flows.

-> Tested prediction by entering new flows in the web app.

