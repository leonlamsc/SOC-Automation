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
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/4a8c957c-50fc-4426-9c98-ba5cd7a57ace)

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

There you goooo!!!!

## Wazuh Agent Configuration



## Wazuh Server Installation
- Install Wazuh package
  - `curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a`

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/f51d93f2-b504-4b24-9374-f7f03c364db5)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/03bfedf5-b2aa-4667-9646-0f6062121f86)

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/31e54afc-2a5c-45fb-9544-b2b5145992a5)

