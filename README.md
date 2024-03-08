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
