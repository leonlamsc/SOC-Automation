# Wazuh-with-SOAR
## Table of Contents

1. [Introduction](#introduction)
2. [SOC Automation design](#soc-automation-design)
3. [Shuffle Automation](#shuffle-automation)
4. [Wazuh Server Event Logs](#wazuh-server-event-logs)
5. [TheHive Alert](#thehive-alert)
6. [Active Response to the event ](#active-response-to-the-event)
7. [Credit to](#credit-to)


## Introduction 
This repository serves as a comprehensive guide for the implementation of Security Operations Center (SOC) automation using Wazuh, thehive, Shuffle and Security Orchestration, Automation, and Response (SOAR) frameworks within a controlled laboratory environment. The content herein outlines the procedural steps and practices essential for establishing a practical laboratory experience in SOC automation.

All of the lab procedures are documented in the .md files.
## SOC Automation design
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d697386e-994f-4aa2-9ea5-81a7376d2dc5)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/fce1b9f1-f5f4-4cf1-8cb6-fb40a81bd9dc)

## Shuffle Automation 
### Workflow for Detecting Mimikatz
  1. Mimikatz Alert Sent to Shuffle
  2. Shuffle Receives Mimikatz Alert
    - Extract SHA256 Hash From File
  3. Check Reputation Score w/VirusTotal(Optional)
  4. Send Details To TheHive To Create an Alert
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0aa52a7c-7de9-42c1-b076-f438d72a60b8)

### Workflow for Detecting Brute Force Attack
  1. Push All LEVEL S Alerts To Shuffle
  2. Send Details via Email To The User
     - Ask To Block Source IP
  3. Create An Alert In TheHive
  4. Automatically Block IP If User Confirms
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/ae4bb08a-e32d-43f0-8e2f-063dcd162d67)

## Wazuh Server Event Logs
### Mimikatz Detection Logs
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/cfc9b5d6-3c9f-4d42-9553-7812dd0dec50)

### Brute Force Detection Logs
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/f5f11993-f274-4559-ab7f-9d8580a284b5)

## TheHive Alert 
### Mimikatz Detection Alert 
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/25bf2b66-f9fb-4f66-846a-864427bd3adf)

### Brute Force Detection Alert
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/6601f4a0-f7df-45b4-877c-b080260ef5a6)

## Active Response to the event 
### Brute Force Active Response through Email Alert
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/e35b6ce2-033b-4345-8714-257bb08673a7)
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/37727c55-3bb3-415d-8c85-b8ce78fdffc6)

- All IP addresses of Brute Force are blocked  
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/20d8598c-4b7a-4010-98e3-454c841e4ea2)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/877046db-c66a-4da8-9dc6-a49b2c5cfc0b)

## Credit to
- [olafhartong/sysmon-modular](https://github.com/olafhartong/sysmon-modular.git)
- [Mimikatz](https://github.com/gentilkiwi/mimikatz/releases/tag/2.2.0-20220919)
- [MyDFIR](https://www.youtube.com/@MyDFIR)
