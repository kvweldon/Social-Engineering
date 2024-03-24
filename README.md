# Social-Engineering
Utilizing Kali Linux 2022.2 and Windows Server 2016(victim's system) to perform social engineering using SET
<h1>Phase 2</h1>

Structureality is concerned about their susceptibility to soical engineering attacks and have given approval to test their personnel. I will perform a simulated social engineering attack against their employee using the Social Engineering Toolkit (SET). The goal is to trick a victim into running a malicious payload which will result in a reverse shell being established between the victim and the attacker systems.

**<p style="font-size: 15px;">Step 1: Create a Spear Phishing Message.</p>**

I first elevated the terminal to root privileges so that I could use the full suite of tools in the Social Engineering Toolkit(SET) and then launched SET by entering "setoolkit".

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/625997d5-43f3-4dbe-82d2-e03f22a0b118)

Here you can see the opening screen of SET. There are 6 options to choose from the initial menu, but I only needed the first option, Social-Engineering Attacks. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/9cebeacb-d061-444b-83ef-ddca58fd486e)

SET gives attackers 10 types of attacks to utilize. To create a spear phishing message I will use option 5 and option 4. Option 5, Mass Mailer Attack, can be used to send an email to one email or a group from an imported list. Option 4 is used to create the payload that will be sent in the email.

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/ec4aa23b-aa78-4b6d-a8f8-10ffb6b1629d)

Below I have used the Create a Payload and Listener option to create a Windows Reverse_TCP Meterpreter. This will create a reverse shell that will listen on port 443 of the IP address of 203.0.113.66, the "attacker" IP address on the Kali Linux VM. When the payload is generated it is saved as the file /root/.set/payload.exe. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/ca7dd9ca-784a-4a76-b47f-e4747b36f35c)

Once generated, SET will launch the MSFconsole and begin the listening session. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/50204f4b-42d8-41ad-98e7-297b8263c63c)

I then started a new Terminal window and elevated it to use root privileges using the "sudo su" command. This is necessary because SET locks into waiting for a connection once the listener was launched. I then moved to the .set directory of the root directory to zip the payload.exe into a file located in the rood directory of the Kali web server using the command "zip /var/www/html/acctupd.zip payload.exe". Performing zip operation while in the same directory as the executable ensures the zip file does not contain sub-directories. I then started the pre-installed Apached web server to so that I can a create the download link for the attack later on.  

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/cf3cdefa-839e-47a9-be3b-2e880b07b4be)

Once back in SET I utilized the Mass Mailer Attack to begin the email spoofing process. As mentioned earlier, Mass Mailer gives an attacker the ability to send multiple emails at once or to a single email address. For this lab I sent the payload to a single email address, jaime@structureality.com. This attack will not utilize Gmail, therefore option 2 is selected. The attack uses the spoofed email address of, support@structurealty.com, to mask as a the Support Department sending a high priority email about an Important Account Update. The HTML format is used, and the email instructs the recipient to download, extract and run the update file in the link which will have the reverse shell payload embedded in it.  

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/f76e43d3-1ba8-4a83-870a-e13c83874dbd)

**<p style="font-size: 15px;">Step 2: Be an email phishing victim.</p>**

This section is a proof of concept to show how the phishing attack would work. I assume the role of Jaime receiving the spoofed email, believing it is a legitimate email from Structureality Support Department. Below I have opened the Microsoft Virtual Machine to display the desktop of Jaime's computer.

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/fd19e601-ec5c-40f8-b62c-4ad7f3636010)

Below shows the email sent from the spoofed email.   

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/1644ef0d-62fd-4d6c-b5d4-f9a23f777c1f)

I seleceted the email to open the email and an alert warning that the email is a scan pops up. As I am assuming the role of Jaime who believes this is a legitimate email, I select yes.

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/bf215076-64b0-4d0d-86d9-131a0e52aba6)

The link opens Firefox and the file is downloaded as shown in the picture below. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/6211cdee-8de4-430e-9462-4a398a0f1467)

I select Run on the security warning. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/106d59d9-9d6d-4b2b-bcc5-ab06170cda6a)

From the victim's perspective, nothing will seem to have happened when the payload.exe is executed. However, the reverse shell has been created from the victim's system to the attacker's system. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/b400bc8f-27cd-466e-9369-dbd78afc615a)

**<p style="font-size: 15px;">Step 3: Exploit the victim through the established reverse shell.</p>**

In the final step, I have returned back as the attacker on the Linux system. The MSF6 prompt now shows a Meterpreter session opened from 203.0.113.66, the attacker's system, on port 443 to 203.0.113.1, the "public" IP address of Structureality's network, on port 55419. Since the victim is inside the private network of Structureality, the first "public" IP address is displayed as the connect remote host. This session is being relayed by the edge device, usually a firewall which is true in this case, to "Jaime's" internal system. Most firewalls block inbound connection attempts to internal systems which is why tricking a user to into initiating a reverse shell, which causes the internal system to initiate an outbound connection to the attacker, is often necessary.  

I entered "sessions" to view the list of current sessions on MSF6 and then entered "-i 1" to connect to the established session. "sysinfo" is entered to view information about Jaime's compromised system which the attacker is now connected to. 


![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/40cbf292-9331-45a8-a771-9b39d12571ba)

I entered "help" to show a list of other commands that can now be used through meterpreter against the victim systems. 

![image](https://github.com/kvweldon/Social-Engineering/assets/141193154/748d2725-a798-40a6-a4fa-c32ead80d01f)






