# 🔐 Centralized Logging System using Syslog (rsyslog)

## 📌 Overview
This project demonstrates the implementation of a centralized logging system using **rsyslog** on Linux.  
It simulates how Security Operations Centers (SOC) collect, monitor, and analyze logs from multiple systems in real time.

---

## 🎯 Objective
- To set up a syslog server for centralized log collection  
- To enable TCP and UDP-based log transmission  
- To organize logs dynamically for better analysis  
- To validate and secure log flow across the network  

---

## 🛠️ Technologies Used
- Linux (Ubuntu)
- rsyslog
- systemctl (service management)
- UFW (firewall)
- Networking (TCP/UDP ports)

---

## ⚙️ Implementation Steps

### 1. Install and Enable rsyslog
```bash
sudo apt-get update
sudo apt-get install rsyslog
sudo systemctl start rsyslog
sudo systemctl enable rsyslog
```

### 2. Configure rsyslog Server
Edit configuration file:
```bash
sudo nano /etc/rsyslog.conf
```

Enable TCP & UDP:
```bash
module(load="imudp")
input(type="imudp" port="514")

module(load="imtcp")
input(type="imtcp" port="514")
```

### 3. Log Template Configuration
```bash
$template remote-incoming-logs,"/var/log/%HOSTNAME%/%PROGRAMNAME%.log"
*.* ?remote-incoming-logs
```

### 4. Restart Service
```bash
sudo systemctl restart rsyslog
```

### 5. Verify Configuration
```bash
sudo systemctl status rsyslog
ss -tunel | grep 514
```

### 6. Configure Firewall
```bash
sudo ufw allow 514/tcp
sudo ufw allow 514/udp
```

---

## 📊 Results
- Syslog service successfully running  
- Server listening on TCP & UDP port 514  
- Logs are structured and stored dynamically  

---

## 🔍 Key Learnings
- Importance of centralized logging in cybersecurity  
- Role of syslog in SOC environments  
- Network-level log transmission (TCP vs UDP)  
- Log organization and monitoring techniques  

---

## 🚀 Future Scope
- Integration with SIEM tools (Splunk, ELK Stack)  
- Real-time alerting and log correlation  
- Threat detection automation  

---

## 📷 Screenshots
(Add your screenshots here: service status + port listening)

---

## 🧠 Author
Harsh Yadav  
