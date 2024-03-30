# wazuh-Lab
1. Installed and configured wazuh manager in Ubuntu virtual machine
2. Add a linux and windows virual machine as a agents

# File integrity monitoring
![wa-3](https://github.com/George-1100/wazuh-Lab/assets/76154087/bf843e29-9456-4211-a993-8cb46320d034)
Go to # /var/ossec/etc/ossec.conf file and specify the path(under FIM syscheck block) for which folder can be monitoried

![wa-2](https://github.com/George-1100/wazuh-Lab/assets/76154087/b0297a0a-ed3e-4f25-9f53-e1677ade6a5f)
crating text file in agent

![wa-1](https://github.com/George-1100/wazuh-Lab/assets/76154087/f65532d3-3423-4d96-8d13-092b59a7bd23)
I can able to see the integrity monitoring logs

# Active response

![image](https://github.com/George-1100/wazuh-Lab/assets/76154087/50fc7319-100c-4b48-8c61-02b8033a6c55)
Add path to monitor under the FIM syscheck block

Install jq, a utility that processes JSON input from the active response script.
sudo apt update
sudo apt -y install jq

![image](https://github.com/George-1100/wazuh-Lab/assets/76154087/ed7e73ef-dc63-4728-8c31-b03df7c3a6e3)
Create the /var/ossec/active-response/bin/remove-threat.sh active response script to remove malicious files from the endpoint

Change the /var/ossec/active-response/bin/remove-threat.sh file ownership, and permissions:
sudo chmod 750 /var/ossec/active-response/bin/remove-threat.sh
sudo chown root:wazuh /var/ossec/active-response/bin/remove-threat.sh

Restart the Wazuh agent to apply the changes:
sudo systemctl restart wazuh-agent

#wazu server
Add the following rules to the /var/ossec/etc/rules/local_rules.xml file on the Wazuh server. These rules alert about changes in the /home/wazu-linuc-agent directory that are detected by FIM scans.
![image](https://github.com/George-1100/wazuh-Lab/assets/76154087/46449576-fb47-4965-825e-f557fd451a71)

Add the virus total configuration to the Wazuh server /var/ossec/etc/ossec.conf
Append the remove-threat.sh blocks to the Wazuh server /var/ossec/etc/ossec.conf
![image](https://github.com/George-1100/wazuh-Lab/assets/76154087/ae90f84d-dc0c-408d-a051-15f30ff30e06)

sudo systemctl restart wazuh-manager
![image](https://github.com/George-1100/wazuh-Lab/assets/76154087/60dca628-cc27-4c4f-9112-e72badfd699c)


