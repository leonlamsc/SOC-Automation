## In Windows agent:
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/1dd8093e-5e1c-47ae-bd59-9356d2ee2ae8)


![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/6d233a44-a9eb-4046-a682-0f2172edd671)
- Restart Wazuh in "Services"

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/f8923236-28e2-4798-903f-8ba5efb26ee1)

## In Wazuh Manager
-`cp /var/ossec/etc/ossec.conf ~/ossec-backup.conf`
-`sudo nano /var/ossec/etc/ossec.conf`
- change 'logall' and 'logall_json' from no to yes

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/9b649fa3-2720-45bb-a83d-f08ba608291d)

- Restart Wazuh manager

## Make the Wazuh to injest the logs in archives
- `nano /etc/filebeat/filebeat.yml`
- change the 'archives' to true
  
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/e0efaa88-4dfa-4f23-ab28-6f67380f7830)

- Restart filebeat

## Create index pattern for the archives
- Go to 'Stack Management', then 'Index Pattern'
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/b009d427-166f-466c-b30f-bc15aaac925a)
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/52770739-f782-4942-9a85-e9d07c76335e)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/97a22e91-dc4b-4373-b743-87648d42e70c)

- Run the mimikatz with Powershell

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/063c34a9-54c7-4abd-b146-3871dc39beb4)

- Search mimikatz in Wazuh manager
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/4e23434e-03b1-4903-b5a4-1e6f51f322c9)

## Configure the rule based on the original name of the file
- Locate 'Rules' in dashboard, and Select "Manage rules files"
- Click 'Custom rules' and edit the 'local_rules.xml'
- Add the following rule in the xml, Pay make sure the originalFileName is correct becasue it is case-sensitive
  - ```
    <rule id="100002" level="15">
      <if_group>sysmon_event1</if_group>
      <field name="win.eventdata.originalFileName" type="pcre2">(?i)\\mimikatz\.exe</field>
      <description>Mimikatz Usage Detected</description>
      <mitre>
        <id>T103</id>
      </mitre>
    </rule>
  
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/50a7b80d-65a7-4326-8f87-4f68dc54bda7)

- Save it and restart Wazuh

## Result:
- Run mimikatz with a new name "HeyHeyYo.exe" in windows
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/29819ef2-72ba-4aac-8b1a-9b248bfb4f66)
- Wazuh detected the execution
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/be763185-9fa1-4c9b-aecc-7a316b79e3a9)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/e19869af-081c-4338-b5f1-cbfc86ead7ba)

