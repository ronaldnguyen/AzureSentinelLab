<h1><p align="center">
  Azure Sentinel Home Lab  <p align="left"><img src="https://user-images.githubusercontent.com/114441952/192993162-fc2167fe-9ed8-4a51-b142-65a005c726c0.png" width="200"></h1>

<h2>Description</h2>
In this project, I used Azure Sentinel (SIEM) to connect it to a live virtual machine and made this machine very vulnerable by turning off all firewalls, a basic honeypot. I then ran a Powershell script to inspect the Windows Event Log information for failed RDP attacks, which used ipgeolocation.io (a third-party API) to harvest the geographic information of attackers IP address, and plotted the attacker's geolocation information on an Azure Sentinel Map.

</br>

<h2>Languages and Utilities Used</h2>

- <b>PowerShell: Extracts the Windows Event Viewer Logon Logs
- ipgeolocation.io: Returns geographic information for a given IP
</b> 

<h2>Lab walk-through:</h2>

<p align="center">
Created an Azure VM, turned off firewall, created own inbound rule to make machine more vulnerable: <br>
<img src="https://user-images.githubusercontent.com/114441952/193006518-7db82ccf-fdb0-4f1b-ae45-b67c593e6b2c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Created Log Analytics Workspace to ingest custom logs from the VM: <br>
<img src="https://user-images.githubusercontent.com/114441952/193008992-a6955ef4-668a-4668-af55-5006af999919.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<p align="center">
Enabled gathering VM logs in Security Center: <br>
<img src="https://user-images.githubusercontent.com/114441952/193009090-4c001921-ad4b-42ea-9d19-daaa7f3f6c24.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<p align="center">
Setup Azure Sentinel and connect it to Log Analytics so we can visualize the attack data: <br>
<img src="https://user-images.githubusercontent.com/114441952/193010170-96502068-58b5-404f-8404-f02d0ce0ced3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Ran PowerShell script to obtain geographical data from the third-party API using the attackers' IP address and then sends info into a log file which will be used by Log Analytics : <br>
<img src="https://user-images.githubusercontent.com/114441952/193014618-f7aaa266-cb2c-4c57-9322-835b2b2e2277.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://user-images.githubusercontent.com/114441952/193018301-a392ac22-8f62-42d2-83b2-85c9587cf285.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Created a custom log in Log Analytics to bridge the VM logs and extracted the raw data to create fields so that we can use these fields in Azure Sentinel Map: <br>
<img src="https://user-images.githubusercontent.com/114441952/193010170-96502068-58b5-404f-8404-f02d0ce0ced3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Ran a Sentinel Map Query to return results from Log Analytics to plot the attacker geographical location on a Map: <br>
<img src="https://user-images.githubusercontent.com/114441952/193020658-a5ac6a61-3c6e-4588-81eb-393a0f60e336.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Live map one day later: <br>
<img src="" height="80%" width="80%" alt=""/>
</p>
