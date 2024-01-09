# Detection of Brute Force and Active Response 
`curl -u USER:PASSWORD -k -X GET "https:/WAZUH-IP:55000/Security/user/authenticate?raw=true"`
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0a91f713-095a-4aaf-8e5d-31604e34f45d)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/196c3218-b664-4967-b66e-8f128132ab4a)

API configuration
- Modify `/usr/share/wazuh-dashboard/data/wazuh/config/wazuh.yml` to set the connection information.
-` curl -u <wazuh>:<password> -k -X GET "https://<wazuh IP>/security/user/authenticate?raw=true"`
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/940a4b54-6931-4ffa-b1e3-50b49d33fde3)

- Put the above command to the "Statement" of "Get-API"
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/c285f345-8815-44d6-99aa-f8d010c82314)

Configure Wazuh in Shuffle

-`nano /var/ossec/etc/ossec.conf`
- ```
  <active-response>
    <command>firewall-drop</command>
    <location>local</location>
    <level>5</level>
    <timeout>no</timeout>
  </active-response>

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/15764781-ac2e-4110-a585-a32adfce1a9f)

- Testing the active reponsive command `./agent_control -b 8.8.8.8 -f firewall-drop0 -u 004 `
  -my linux machine drops all 8.8.8.8(dns.google) after the "firewall-drop0"
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/54c23395-f338-4ca5-8c85-8d93ee5783bf)
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/cf465582-9980-4465-9fd0-f9b6e3da494d)

- Fill in the command and Alert as the following
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/262e941e-a72b-4b76-9183-463f88dab182)

Add Forward Email to user to ask for a response.

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/16e3aab0-f814-48ce-b834-e7bd1cad9469)

