# Table of Content
1. [TheHive Configuration](#thehive-installation)
2. [Wazuh Agent Configuration](#wazuh-agent-configuration) 


## TheHive Configuration
Configure the cassandra.yaml for the listen address or port, and name
- `sudo nano /etc/cassandra/cassandra.yaml`
- Change the "listen_address" to our thehive ip address
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/a478b94e-8007-422a-8146-d980c60546d6)

- Change the "rpc_address" to our thehive ip address
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d59cdcce-d605-46ec-b495-99c7262c62ea)

- Change the "seeds" of "seed_provider" to our thehive ip address:7000
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0fc7cffd-7a32-409a-88cd-d14209bb7005)


Afterwards, restart the cassandra.service
- `systemctl stop cassandra.service`
- `rm -rf /var/lib/cassandra/*`
- `systemctl start cassandra`

Configure the elasticsearch
- `sudo nano /etc/elasticsearch/elasticsearch.yml`
- enbale the "network.host" and type the IP address in there
   ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/30d91351-09d9-4b1d-b446-ab1df904b7c2)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/cc7d7606-6bd9-4560-8464-f866e604df7e)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/6ed8778e-98e1-4369-96ed-10c100a78df1)

Afterwards, start the elasticsearch
- `systemctl start elasticsearch`
- `systemctl enable elasticsearch`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/846e6f59-5c3d-4d04-ad9b-ec14f87538f3)


Change ownership of the "/opt/thp" directory from root to thehive:thehive
-`chown -R thehive:thehive /opt/thp`
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/1338cc95-d154-4ccd-85f8-b93df1f159b1)

COnfigure the "thehive application.conf" file.

-`sudo nano /etc/thehive/application.config`

- change hostname and application.basedUrl to our ip address

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/5ab3a77c-82af-422d-9360-b8428a543927)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/391a2563-4e54-4b8c-8126-fc434100299d)


Afterwards, start the thehive
- `systemctl start thehive`
- `systemctl enable thehive`

-`nano /etc/elasticsearch/jvm.options.d/jvm.options`

Configure the elasticsearch for less usage on memory allocated to the Java Virtual Machine to prevent the crush of elasticsearch
-`sudo nano /etc/elasticsearch/jvm.options.d/jvm.options`
  - Dlog4j2.formatMsgNoLookups=true
  - Xms2g
  - Xmx2g



There you goooo!!!!
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/3012a93a-c293-430c-ba73-2025536305d7)

## Wazuh Agent Configuration
- Choose "Deploy new agent"
- Follow the steps from GUI
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/f46cb67a-2bf7-4645-9ebf-0f0777bdad40)

- Wazuh will give you the following commands for you to run on your client device (Windows/Linux)
- `Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.7.1-1.msi -OutFile ${env.tmp}\wazuh-agent; msiexec.exe /i ${env.tmp}\wazuh-agent /q WAZUH_MANAGER='Your Wazuh Server IP address' WAZUH_AGENT_GROUP='default' WAZUH_AGENT_NAME='Client' WAZUH_REGISTRATION_SERVER='Your Wazuh Server IP address'`
- `NET START WazuhSvc`

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/422c3e43-d249-4b84-96e8-4be124adae49)
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/518e1ed0-2839-4a9d-86e0-46d045e8845a)



