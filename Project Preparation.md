# Table of Content
1. [Cloud Platform for the environment](#cloud-platform-for-the-environment)
2. [Wazuh Server Installation](#wazuh-server-installation)
3. [TheHive Installation](#thehive-installation)
4. [Wazuh Agents Configuration](#wazuh-agents-configuration)
5. [Sysmon Installation on Windows](#sysmon-installation-on-windows)
6. [Acknowledgment Credit to](#acknowledgment-credit-to)

## Cloud Platform for the environment
Digital Ocean

## SOC Automation design
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d697386e-994f-4aa2-9ea5-81a7376d2dc5)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/fce1b9f1-f5f4-4cf1-8cb6-fb40a81bd9dc)

## Wazuh Server Installation
- Install Wazuh package
  - `curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a`

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/f51d93f2-b504-4b24-9374-f7f03c364db5)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/03bfedf5-b2aa-4667-9646-0f6062121f86)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/31e54afc-2a5c-45fb-9544-b2b5145992a5)


- Extract Wazuh Credentials
- `sudo tar -xvf wazuh-install-files.tar`

## TheHive Installation

- Install Java
  - `wget -qO- https://apt.corretto.aws/corretto.key | sudo gpg --dearmor  -o /usr/share/keyrings/corretto.gpg`
  - `echo "deb [signed-by=/usr/share/keyrings/corretto.gpg] https://apt.corretto.aws stable main" |  sudo tee -a /etc/apt/sources.list.d/corretto.sources.list`
  - `sudo apt update`
  - `sudo apt install java-common java-11-amazon-corretto-jdk`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/99be0044-8b6d-497d-887e-facbe56586e1)

  - `echo JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto" | sudo tee -a /etc/environment`
  - `export JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto"`

- Install Cassandra
  - `wget -qO- https://downloads.apache.org/cassandra/KEYS | sudo gpg --dearmor -o /usr/share/keyrings/cassandra-archive.gpg`
  - `echo "deb [signed-by=/usr/share/keyrings/cassandra-archive.gpg] https://debian.cassandra.apache.org 40x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list`
  - `sudo apt update`
  - `sudo apt install cassandra`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/3af6af51-52dc-4f87-af88-2d4caf0b08f9)


- Install ElasticSearch
  - `wget -qO- https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg`
  - `sudo apt-get install apt-transport-https`
  - `echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0df94104-e647-44f3-ad70-a0ecbd0245ae)

  - `sudo apt update`
  - `sudo apt install elasticsearch`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/a1072c62-9118-4a8c-bf2a-e2f6f061ec0a)

- Install TheHive
  - `wget -O- https://archives.strangebee.com/keys/strangebee.gpg | sudo gpg --dearmor -o /usr/share/keyrings/strangebee-archive-keyring.gpg`
  - `echo 'deb [signed-by=/usr/share/keyrings/strangebee-archive-keyring.gpg] https://deb.strangebee.com thehive-5.2 main' | sudo tee -a /etc/apt/sources.list.d/strangebee.list`
  - `sudo apt-get update`
  - `sudo apt-get install -y thehive`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/7a3c955a-7216-4acc-8e46-ac1c8eb369e8)

Default Credentials on port 9000
credentials are 'admin@thehive.local' with a password of 'secret'
## Wazuh Agents Configuration
## Sysmon Installation on windows 
- Sysmon Download link:
  - 'https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon'
- sysmonconfig file Download:
  - [olafhartong/sysmon-modular](https://github.com/olafhartong/sysmon-modular.git)
  
- Command used in Powershell.exe with Admin right:
  - `Sysmon64.exe -i .\sysmonconfig.xml` 
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/3fac0286-d0aa-43b5-a82b-cd34f6501115)
