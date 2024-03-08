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

I configure the "Change Me" icon by setting the "Find Actions" to regex capture group, specifying the "Input Data" as the hashes execution argument. Then, I request ChatGPT to create a regex pattern to parse the SHA256 value of the hash. After completing these steps, I rerun the workflow, and as expected, it successfully parses out the SHA256 hash.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/816f1df0-cce4-4ba2-a38b-650c61c8962d" height="30%" width="70%" alt="Disk Sanitization Steps"/>

To leverage VirusTotal's API for automatic hash checking and retrieval of values, I first copy the API Key from my VirusTotal account. Then, I add VirusTotal into my Shuffle workflow along with the API Key. Upon rerunning the workflow and checking VirusTotal, I notice the status is 404, indicating that VirusTotal was unable to return any results. This likely occurred because the VirusTotal app in Shuffle is accessing an incorrect URL.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/2d317483-574a-4c62-9e58-77741507b37d" height="30%" width="70%" alt="Disk Sanitization Steps"/>

To resolve the issue, I navigate to the "Apps" page in Shuffle and modify the VirusTotal app. Specifically, I change the hash report from "report" to "id" and enclose it in curl brackets. Then, I create a new VirusTotal step in my workflow, add my API Key, and make the necessary adjustments. Upon rerunning the workflow, I observe a wealth of additional information. For instance, under "last_analysis_status," it indicates "malicious 62," signifying that 62 scanners detected the file as malicious.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/3aad2638-228e-4264-806d-f1bc5ec1a277" height="30%" width="70%" alt="Disk Sanitization Steps"/>

In Shuffle, I integrate TheHive into my workflow and proceed to TheHive's webpage. There, I create two new users: one "normal" user and one "service" user. I assign the "normal" user an "analyst" profile and generate a password. For the "service" user, although the principle of least privilege suggests setting it to "read-only," for testing purposes, I also assign it an "analyst" profile. After generating an API key for the "service" user, I log out of the webpage and log in again using the credentials of the "normal" user. Returning to Shuffle, I add the API Key and URL to TheHive into my workflow.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/9de7b3f4-a42c-42fc-b95e-611c324d8c47" height="30%" width="70%" alt="Disk Sanitization Steps"/>

In Shuffle, I include custom text on TheHive so that alerts are easily identifiable. To enhance security, I configure a firewall on DigitalOcean for port 9000, allowing access to the machines from any source via IPv4. This helps ensure that only authorized traffic can reach the machines on port 9000.
<br />
<br />
<img src="..." height="30%" width="70%" alt="Disk Sanitization Steps"/>

Returning to Shuffle, I incorporate commands into the custom text I created, then rerun the workflow. After making several custom additions, I verify the success of TheHive integration. Checking TheHive for any alerts, I confirm that we have received them. Awesome, mission accomplished!
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationProjectPart5/assets/145611184/512ae3a9-1bff-437c-b754-aa1b87518c06" height="30%" width="70%" alt="Disk Sanitization Steps"/>





