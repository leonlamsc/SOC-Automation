# Wazuh-with-SOAR
## Table of Contents

1. [Introduction](#introduction)
2. [Wazuh Server Installation](#wazuh-server-installation)
3. [TheHive Installation](#thehive-installation)
4. [Wazuh Agents Configuration](#wazuh-agents-configuration)
5. [Sysmon Installation on Windows](#sysmon-installation-on-windows)
6. [Acknowledgment Credit to](#acknowledgment-credit-to)

## Introduction 
This repository serves as a comprehensive guide for the implementation of Security Operations Center (SOC) automation using Wazuh and Security Orchestration, Automation, and Response (SOAR) frameworks within a controlled laboratory environment. The content herein outlines the procedural steps and practices essential for establishing a practical laboratory experience in SOC automation.

## SOC Automation design
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d697386e-994f-4aa2-9ea5-81a7376d2dc5)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/fce1b9f1-f5f4-4cf1-8cb6-fb40a81bd9dc)

## Wazuh Server Event Logs
- Install Wazuh package
  - `curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a`

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/f51d93f2-b504-4b24-9374-f7f03c364db5)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/03bfedf5-b2aa-4667-9646-0f6062121f86)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/31e54afc-2a5c-45fb-9544-b2b5145992a5)


- Extract Wazuh Credentials
- `sudo tar -xvf wazuh-install-files.tar`

## TheHive Alert 


## Acknowledgement Credit to
- [olafhartong/sysmon-modular](https://github.com/olafhartong/sysmon-modular.git)
- [MyDFIR](https://www.youtube.com/@MyDFIR)
