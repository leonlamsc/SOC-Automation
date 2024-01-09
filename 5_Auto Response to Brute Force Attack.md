# Detection of Brute Force and Active Response 

## Use the Http app to get the API key from Wazuh by the following command
- `curl -u USER:PASSWORD -k -X GET "https:/WAZUH-IP:55000/Security/user/authenticate?raw=true"`

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/0a91f713-095a-4aaf-8e5d-31604e34f45d)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/196c3218-b664-4967-b66e-8f128132ab4a)

## API configuration
- Modify `/usr/share/wazuh-dashboard/data/wazuh/config/wazuh.yml` to set the connection information.

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/940a4b54-6931-4ffa-b1e3-50b49d33fde3)

## Configure Wazuh in Shuffle

-`nano /var/ossec/etc/ossec.conf` to add the below command to the file
- ```
  <active-response>
    <command>firewall-drop</command>
    <location>local</location>
    <level>5</level>
    <timeout>no</timeout>
  </active-response>
  ```
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/15764781-ac2e-4110-a585-a32adfce1a9f)

## Testing the active reponsive command `./agent_control -b 8.8.8.8 -f firewall-drop0 -u 004 `
  - my linux machine drops all 8.8.8.8(dns.google) after the "firewall-drop0"
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/54c23395-f338-4ca5-8c85-8d93ee5783bf)
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/cf465582-9980-4465-9fd0-f9b6e3da494d)

- Fill in the command and Alert as the following
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/262e941e-a72b-4b76-9183-463f88dab182)

## Add Forward Email to "User Input" to ask for a response.
- Fill in ` Brute Force Event Detected: Would you like to block this source IP:  $exec.all_fields.data.srcip` and your email to the fields

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/16e3aab0-f814-48ce-b834-e7bd1cad9469)

## Automation Response  
- Final Workflow
  
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/ae4bb08a-e32d-43f0-8e2f-063dcd162d67)

- Event in Wazuh captured

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/a9ec1200-6021-4157-b2e2-19805f47f1c8)

- Email Alert for Brute Force Event and ask for the response "Block the ip or not"
  
  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/e35b6ce2-033b-4345-8714-257bb08673a7)

- Alert created in thehive

  ![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/6601f4a0-f7df-45b4-877c-b080260ef5a6)

- All IP addresses of Brute Force are blocked  
![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/20d8598c-4b7a-4010-98e3-454c841e4ea2)

![image](https://github.com/leonlamsc/Wazuh-with-SOAR/assets/140391766/877046db-c66a-4da8-9dc6-a49b2c5cfc0b)

