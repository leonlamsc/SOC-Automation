# Wazuh-with-SOAR
## Table of Contents

1. [Introduction](#introduction)
2. [Wazuh Server Installation](#wazuh-server-installation)
3. [TheHive Installation](#thehive-installation)
4. [Wazuh Agents Configuration](#wazuh-agents-configuration)
5. [Sysmon Installation on Windows](#sysmon-installation-on-windows)
6. [Acknowledgment/Credit to](#acknowledgment-credit-to)

## Introduction 
This repository serves as a comprehensive guide for the implementation of Security Operations Center (SOC) automation using Wazuh and Security Orchestration, Automation, and Response (SOAR) frameworks within a controlled laboratory environment. The content herein outlines the procedural steps and practices essential for establishing a practical laboratory experience in SOC automation.

## SOC Automation design
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d697386e-994f-4aa2-9ea5-81a7376d2dc5)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/fce1b9f1-f5f4-4cf1-8cb6-fb40a81bd9dc)

## Wazuh Server Installation
- Install Wazuh package

- `curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a`

- Extract Wazuh Credentials

- `sudo tar -xvf wazuh-install-files.tar`

- 
## TheHive Installation

- Install Java
- `wget -qO- https://apt.corretto.aws/corretto.key | sudo gpg --dearmor  -o /usr/share/keyrings/corretto.gpg`
- `echo "deb [signed-by=/usr/share/keyrings/corretto.gpg] https://apt.corretto.aws stable main" |  sudo tee -a /etc/apt/sources.list.d/corretto.sources.list`
- `sudo apt update`
- `sudo apt install java-common java-11-amazon-corretto-jdk`
- `echo JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto" | sudo tee -a /etc/environment`
- `export JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto"`

- Install Cassandra
- `wget -qO- https://downloads.apache.org/cassandra/KEYS | sudo gpg --dearmor -o /usr/share/keyrings/cassandra-archive.gpg`
- `echo "deb [signed-by=/usr/share/keyrings/cassandra-archive.gpg] https://debian.cassandra.apache.org 40x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list`
- `sudo apt update`
- `sudo apt install cassandra`

- Install ElasticSearch
- `wget -qO- https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg`
- `sudo apt-get install apt-transport-https`
- `echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list`
- `sudo apt update`
- `sudo apt install elasticsearch`


- Install TheHive
`wget -O- https://archives.strangebee.com/keys/strangebee.gpg | sudo gpg --dearmor -o /usr/share/keyrings/strangebee-archive-keyring.gpg`
`echo 'deb [signed-by=/usr/share/keyrings/strangebee-archive-keyring.gpg] https://deb.strangebee.com thehive-5.2 main' | sudo tee -a /etc/apt/sources.list.d/strangebee.list`
`sudo apt-get update`
`sudo apt-get install -y thehive`

Default Credentials on port 9000
credentials are 'admin@thehive.local' with a password of 'secret'
## Wazuh Agents Configuration
## Sysmon Installation on windows 
## Acknowledgement/Credit to
