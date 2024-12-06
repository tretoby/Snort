# Snort Intrusion Prevention 

Explore how to detect and prevent malicious activity using Snort!, we’ll investigate traffic data and stop attacks under two different scenarios. The goal is to use Snort to analyze live and captured traffic while creating rules to thwart malicious behavior.

---

## Steps

### 1. The Machine is Under Attack!

First, we’ll use Snort in **logger mode** to capture network activity. Let it run for about a minute to capture a brute-force attack. Once stopped, a log file should be created.

![Logger mode command](https://github.com/user-attachments/assets/669234eb-8976-4610-8692-5c1b3f3eca67)

---

### 2. Viewing Captured Logs

To analyze the captured logs, we can read the log file. This will display detailed packet data. For example, in this capture, we detected **9,948 packets** in total.

![Viewing logs](https://github.com/user-attachments/assets/c8e777a1-ae38-4dc4-9b18-89d03aae04a3)

---

### 3. Identify Ports Under Attack

#### Find the IP Address of the Machine
We locate the machine's IP address by checking its network configuration.

![Finding the IP](https://github.com/user-attachments/assets/fc6df90d-35dd-49c0-b3da-ef5e940ee95a)

#### Analyze the Logs
Switching back to the logs, we observed attempts on **port 80 (HTTP)** and **port 22 (SSH)**.

![Port 80 attack attempts](https://github.com/user-attachments/assets/6a450fb4-dfc0-4d4a-8495-82eb73b3ecdf)  
![Port 22 attack attempts](https://github.com/user-attachments/assets/4e8aae0a-49c1-4bdc-9d62-ecd46beac892)

---

### 4. Filter Traffic by Ports

#### Filter Traffic for Port 22
To narrow down the traffic, we filtered packets for port 22.

![Filter for port 22](https://github.com/user-attachments/assets/68fb6772-c46c-419f-b9e8-bc8c98f0990b)  

We identified **2,872 packets** related to port 22.

![Packets for port 22](https://github.com/user-attachments/assets/c83bb803-2d4c-416c-966f-c9caaae5d174)

---

#### Filter Traffic for Port 80
Similarly, filtering traffic for port 80 revealed **7,049 packets**.

![Filter for port 80](https://github.com/user-attachments/assets/e9e545a7-05c5-4466-ac10-62cd03a20489)  
![Packets for port 80](https://github.com/user-attachments/assets/8f9d19ee-4afe-4875-a10e-2093f74c91af)

---

### 5. Investigate Port 22

After closely inspecting the first 10 packets for port 22, we noticed persistent communication patterns indicative of a brute-force attack.

![Filtering first 10 packets](https://github.com/user-attachments/assets/4e0505e1-e0e3-42ba-80cc-215d461729f7)  
![Analyzing packets](https://github.com/user-attachments/assets/aa19e988-e207-4d60-9783-e15472d1e014)

We ruled out port 80 traffic, as it seemed to be regular browsing activity. The constant communication on port 22 confirmed it as the target of the attack.

---

### 6. Stopping the Attack

#### Create Rules to Block Traffic
To stop the brute-force attack, we crafted a rule to drop all packets targeting port 22, regardless of the source or destination.

![Creating rules](https://github.com/user-attachments/assets/24b6b81d-f8cf-4245-b894-e03058fb1f45)

The rule added to the configuration blocks malicious traffic targeting port 22.

![Configuring rules](https://github.com/user-attachments/assets/d2985f32-9ac8-4970-b333-85a35a7f681d)

---

### 7. Run Snort in IPS Mode

We enabled **IPS mode** to actively block the malicious traffic, successfully stopping the attack.

![Running Snort in IPS mode](https://github.com/user-attachments/assets/3c7762e3-cdfd-40ba-b526-8b82c2838bfe)

---

## Success!

The brute-force attack on port 22 was successfully stopped. 🎉

![Attack stopped](https://github.com/user-attachments/assets/7a97585b-6e12-4c05-a36f-1fa85cd8f261)

---

## Conclusion

This project demonstrates how to use Snort for real-time intrusion prevention by analyzing network traffic, identifying threats, and deploying effective rules. Snort's versatility makes it a powerful tool for defending against network attacks. 🚀



























