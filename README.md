<h2>SOC Automation Project Part 5</h2>

<h3>Objectives</h3>
- Connect Shuffle (SOAR)
<br />
- Send details to TheHive
<br />
<br />

Starting off in Shuffle, I create a new account and project to begin. Firstly, I grab the "webhook" workflow starter and name it "Wazuh-Alerts," then copy the URI provided. This allows me to add the URI to the ossec configuration hosted on the Wazuh manager. In the ossec file, I create a new "integration" command and insert the URI from Shuffle, then restart the Wazuh manager service.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/ad045a4d-8151-4ab5-b1cb-6dafa5129bc8" height="30%" width="70%" alt="Disk Sanitization Steps"/>

Now, let's generate another Mimikatz instance in PowerShell and check Shuffle to see if we received anything. And there it is! We have all the information generated from Wazuh. Pretty neat, right?
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/2146bfeb-f419-4d12-8e4f-4c5e7d54ee62" height="30%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/0c55a7e2-99e3-487a-969a-05ae0b425263" height="30%" width="70%" alt="Disk Sanitization Steps"/>


