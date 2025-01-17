# SOAR EDR PROJECT
# Objective
The SOAR EDR project was geared to design an environment for automatic detection and responses. The primary focus was to create a SOAR playbook using various automation tools, respond to security events as they happen automatically, and perform actions based on user responses to events. This project aimed to gain a deeper understanding of certain processes that could be automated in the real world, create rules and user prompts for detection, and obtain hands-on experience in setting up a SOAR environment.
# Skills Learned
Advanced understanding of SOAR concepts and practical application.
Learned how to create virtual hosts and configure automation software.
Gained an understanding of how certain components are connected for automation using application channels, sensors, outputs, and webhooks.
Ability to create detection and response rules for SOAR environment.
Created a SOAR environment using Tines.
Configure the process to isolate machines automatically after a security event is detected.
Ability to send detection and response alerts through emails or to a shared community channel automatically.
# Tools Used
- Endpoint detection and analysis software. // LimaCharlie
- Shared community channel for alerts and responses. // Slack
- Virtual environment for target endpoint machine. // VMWare
- SOAR environment software. // Tines
# Steps
![image](https://github.com/user-attachments/assets/00202317-b96a-478d-b87b-601eb1b1b954)
 1. Created a Windows 10 Pro Virtual Machine, and installed LimaCharlie (endpoint detection and analysis software) using the provided installer and installation key.
 2. Downloaded the Hack Tool Lazagne.exe from Github repository to start generating test security events on the Windows 10 Pro Machine.
 3. On LimaCharlie I navigated to the D&R rules and searched for a new process creation credential access rule. Modified the raw code by replacing the value with Lazagne.exe to start detecting all processes created by Lazagne.exe. I also included a command line rule for all instances mentioning Lazagne.exe in the comamnd line
![image](https://github.com/user-attachments/assets/fe800f40-280d-4379-903f-5bc1b6dfae0e)
4. Tested the detection on LimaCharlie by running the Lazagne.exe executable. Confirmed that the endpoint was able to detect security events to LimaCharlie.
![image](https://github.com/user-attachments/assets/0ae6f1bd-e49b-47e9-9507-a635957161a8)
5. Created a community channel on Slack, to correlate all alerts to one software.
6. On Tines, I created a new story starting with a webhook URL to our LimaCharlie software. By this process, I was able to connect Tines with detection events from LimaCharlie.
7. Using the above diagram, I imported the appropriate Slack and Email modules to send alerts once events were detected.
8. I connected the Slack module by copying the channel code to the Tines playbook, as well as providing my own personal email into the email module.
9. For the message, I included the same message that was provided in the above diagram to the Slack and email modules.
10. I imported a user prompt page, for the user to respond to the alert. Provided a "Do you want to isolate this machine?" message with a boolean input field (yes/no).
11. By using the event details in Tines. I was also able to include the host's details on the alert messages as well, that way the receiving user will also be notified of the specific system details the alert originated from.
![image](https://github.com/user-attachments/assets/26e5a4d4-d218-4d29-b89f-559369d7fc57)
12. I added a new credential of LimaCharlie to the Tines environment with the LimaCharlie API key.
13. Added triggers to the user prompt page, with actions to take when a user selects both "yes" or "no"
14. For "No" I sent a message to Slack confirming the machine was not isolated. For "yes" I connected a LimaCharlie module with the action "Isolate Sensor" and chose to connect it with the appropriate sensor ID.
15. I generated the test event on my Windows 10 Pro VM, confirmed the messages were sent to both Slack and my email, and selected "Yes" on the user prompt page. I then confirmed that the machine was isolated on
![image](https://github.com/user-attachments/assets/ab17a3d5-cc54-4031-b07c-7cbf5479253d)
![image](https://github.com/user-attachments/assets/d72c5da4-b501-4881-9f84-41282086bfa2)
![image](https://github.com/user-attachments/assets/b5f1d884-36fd-420d-8480-318e10b6c4ea)
![image](https://github.com/user-attachments/assets/0cf443ba-a9ae-4ba3-9abe-fc6b670a9a56)



