# Social-Engineering
Utilizing Kali Linux 2022.2 and Windows Server 2016(victim's system) to perform social engineering using SET
<h1>Scenario</h1>

A client is concerned about their susceptibility to soical engineering attacks and have given approval to test their personnel. I will perform a simulated social engineering attack a against a clien't employee using the Social Engineering Toolkit (SET). The goal is to trick a victim into running a malicious payload which will result in a reverse shell being established between the victim and the attacker systems.

**<p style="font-size: 15px;">Step 1: Create a Spear Phishing Message.</p>**

I first elevated the terminal to root privileges so that I could use the full suite of tools in the Social Engineering Toolkit(SET) and then launched SET by entering "setoolkit".

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/625997d5-43f3-4dbe-82d2-e03f22a0b118)

Here you can see the opening screen of SET. There are 6 options to choose from the initial menu, but I only needed the first option, Social-Engineering Attacks. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/9cebeacb-d061-444b-83ef-ddca58fd486e)

SET gives attackers 10 types of attacks to utilize. To create a spear phishing message I will use option 5 and option 4. Option 5, Mass Mailer Attack, can be used to send an email to one email or a group from an imported list. Option 4 is used to create the payload that will be sent in the email.

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/ec4aa23b-aa78-4b6d-a8f8-10ffb6b1629d)

Below I have used the Create a Payload and Listener option to create a Windows Reverse_TCP Meterpreter. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/ca7dd9ca-784a-4a76-b47f-e4747b36f35c)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/50204f4b-42d8-41ad-98e7-297b8263c63c)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/78abd8e4-b51f-4acd-b0f2-bda3c9f87a16)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/cf3cdefa-839e-47a9-be3b-2e880b07b4be)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/e601be86-0411-44af-8f19-68ffe71ffe12)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/39150620-b4b8-4541-99a1-608bdf6fe3b7)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/c1f2aeb7-b985-40fe-b25a-59d6814595e2)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/3ad3d8ec-34db-4858-a668-45436fcacd8d)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/5757f0b7-b293-49eb-9071-4b2d52b92d19)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/f76e43d3-1ba8-4a83-870a-e13c83874dbd)

**<p style="font-size: 15px;">Step 2: Be an email phishing victim.</p>**

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/fd19e601-ec5c-40f8-b62c-4ad7f3636010)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/1644ef0d-62fd-4d6c-b5d4-f9a23f777c1f)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/bf215076-64b0-4d0d-86d9-131a0e52aba6)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/6211cdee-8de4-430e-9462-4a398a0f1467)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/106d59d9-9d6d-4b2b-bcc5-ab06170cda6a)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/b400bc8f-27cd-466e-9369-dbd78afc615a)

**<p style="font-size: 15px;">Step 3: Exploit the victim through the established reverse shell.</p>**


![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/8609ea96-2803-4c3b-a8c8-56ebb50cac80)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/2bc88330-06b7-49ba-9da6-238e17309aae)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/820cd5d7-42c8-4d00-8b76-567811e7b096)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/446b7b5e-5850-4de6-bb11-29b87db9c47e)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/40cbf292-9331-45a8-a771-9b39d12571ba)

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/748d2725-a798-40a6-a4fa-c32ead80d01f)






