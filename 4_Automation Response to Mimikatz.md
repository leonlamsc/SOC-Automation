# Detection of Mimikatz
## Shuffle
- Copy the "webhook URI" 
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d636ca07-4eb5-45ae-b201-ee2b669b3947)




## Wazuh
- `nano /var/ossec/etc/ossec.conf`
- Alert the mimikatz event with rule -d 100002 only
```
  <integration>
    <name>shuffle</name>
    <hook_url>https://shuffler.io/api/v1/hooks/webhook_fe0cb4ff-b2a7-41f2-88a7-cde4f6caa294 </hook_url>
    <rule_id>100002</rule_id>
    <alert_format>json</alert_format>
  </integration>
```
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/1909f3ef-0784-43b5-8b1e-fab1fc039ab1)


- Restart the wazuh

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0967db9a-e7c4-49c3-aeec-1b4afdde7d03)

1. Mimikatz Alert Sent to Shuffle
2. Shuffle Receives Mimikatz Alert
    - Extract SHA256 Hash From File
4. Check Reputation Score w/VirusTotal
5. Send Details To TheHive To Create Alert

- extract the hash value from the argument by regex pattern
  `SHA256=([A-Fa-f0-9]{64})` 

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/afdd5fcc-2769-4d22-a19f-d8253c0a1277)

## VirusTotal API key and configure virustotal in Shuffle

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/3058d738-20b3-498e-8ed6-157f65beaec4)

- We need to change the request URL of virustotal to the following

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/b65f6064-e48f-4f7b-a971-5100593277a2)



## thehive
- Create a new organization 
- Create two users for the organization
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/4632221a-1f4e-4fcb-9301-252fbcfa117a) ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/b82ebe9d-9c41-4dc7-8c77-944308b5734b)

- Create an API key for the "SOAR"
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/731ca882-9dff-4c38-bb48-3c3a23a06805)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/14eaed6c-f473-4be7-9b58-3ef5ecf70ff8)

- Configure thehive in shuffle
- ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/860d08ab-0b0d-41dc-b4b7-8f3a79cee0c3)
- ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/ccfd3326-19a3-4c4a-9696-4ab58bbd2b9c)
- ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/4a6acbf0-12b7-47f6-855a-36508bc4a757)
- ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0b3f1068-4324-4fb1-8d34-e266cb83fd19)

- Allow the incoming traffic from any IPv4 port 9000 in the Digital Ocean
- ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/74419b43-e516-4bca-b4ff-90679a0884be)

## Alert Created
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/25bf2b66-f9fb-4f66-846a-864427bd3adf)


## Email Automation:

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/25321a8e-fcd2-49e3-9284-2b0c7d9e7b50)

- Email Alert created

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/b65b6101-3d00-4c15-9c03-93bf39ff7b39)



