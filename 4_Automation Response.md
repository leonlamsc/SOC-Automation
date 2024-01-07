# Shuffle
- Copy the "webhook URI" 
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/d636ca07-4eb5-45ae-b201-ee2b669b3947)




# Wazuh
`nano /var/ossec/etc/ossec.conf`
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


-Restart the wazuh

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0967db9a-e7c4-49c3-aeec-1b4afdde7d03)

1 Mimikatz Alert Sent to Shuffle
2 Shuffle Receives Mimikatz Alert
Extract SHA256 Hash From File
3. Check Reputation Score w/VirusTotal
4. Send Details To TheHive To Create Alert

-extract the hash value from the argument by regex pattern
`SHA256=([A-Fa-f0-9]{64})` 

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/afdd5fcc-2769-4d22-a19f-d8253c0a1277)

VirusTotal API key and configure virustotal in Shuffle

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/3058d738-20b3-498e-8ed6-157f65beaec4)

We need to change the request URL of virustotal to the following
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/b65f6064-e48f-4f7b-a971-5100593277a2)



# thehive
