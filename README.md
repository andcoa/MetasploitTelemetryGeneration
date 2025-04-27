# Metasploit Telemetry Generation

## Objective

To simulate a reverse shell attack using msfvenom and Metasploit from Kali Linux to a Windows Virtual Machine and to generate malicious telemetry data. Capture and verify the logs using Sysmon and Splunk, helping validate the detection pipeline in a home lab SIEM setup.

## Skills Learned

- Payload Creation with msfvenom: Generated custom Windows executables to simulate real-world malware attacks.
- Attack Execution: Conducted controlled payload execution between Kali Linux and Windows VMs.
- Sysmon Event Logging: Captured detailed process creation, network connections, and file events on Windows.
- Splunk Data Analysis: Indexed and visualized malicious activity using Splunk queries and dashboards.
- Threat Behavior Understanding: Analyzed attacker techniques, payload behaviors, and detection signatures.

## Tools Used

- Metasploit Framework (msfvenom): For creating and delivering payloads.
- Windows 10/11 VM: Target endpoint for attack execution.
- Sysmon: To capture detailed security-relevant events.
- Splunk: To aggregate, index, and search telemetry data.
- Kali Linux: Host for launching payloads and attacks.

## Steps

Enabled Remote Desktop Protoecol (RDP) on the Windows VM.

![image](https://github.com/user-attachments/assets/97fb841c-4e35-4c95-ae7c-abdb1699edd7)

Executed the following Nmap command in Kali to aggressively scan (nmap -A) the Windows VM without first checking if the host responds to the ping (-Pn). The scan reports that port 3389 (RDP) is open on the Windows VM.

![image](https://github.com/user-attachments/assets/42a65f0e-5b7d-4481-8bb0-25367ddbc761)

Used the following command to see available Metasploit exploits that can be used against the Windows VM.

![image](https://github.com/user-attachments/assets/be62d66f-eb83-4b86-9826-8fa39c0a978e)
![image](https://github.com/user-attachments/assets/d746e137-3f71-4dcf-8cca-53f7dcd58f0b)

Ran the following command to generate malware using Meterpeter's reverse TCP payload which is instructed to connect back to the host Kali VM using "lhost" and "lport". The payload is then delivered in the .exe format under a file named Resume.pdf.exe.

![image](https://github.com/user-attachments/assets/8263f92b-0083-439c-8d69-c77b1b43571f)

Opened Metasploit to listen in on the port configured in the malware.

![image](https://github.com/user-attachments/assets/e31a0770-e081-410d-bcb8-049a5d163e8d)

Changed the generic settings of the payload to match the malware configured with msfvenom in the earlier steps.

![image](https://github.com/user-attachments/assets/e579efef-7839-4847-ad7e-d3ce482b756c)

New payload settings.

![image](https://github.com/user-attachments/assets/8ce349f0-d748-4228-96a8-66a0350f9ea9)

Changed lhost to match the IP of the attacking machine (Kali VM).

![image](https://github.com/user-attachments/assets/97a28ed3-a82e-4c5d-846f-d953638ced08)

Started the handler to listen in and wait for the Windows VM to execute the payload.

![image](https://github.com/user-attachments/assets/f7a72ddc-612c-42b3-ade9-aac430ad6c35)

Set up a HTTP server on the attacking Kali VM using Python so the target Windows VM can download the malware.

![image](https://github.com/user-attachments/assets/767f7a83-2d81-42b1-ae30-4ad334ea5e98)

Disabled Windows Defender.

![image](https://github.com/user-attachments/assets/b74b93a6-d7a2-490e-9092-b8b76240ae06)

Downloaded the file on the Windows VM through by inputting the IP of the Kali VM in Google Chrome.

![image](https://github.com/user-attachments/assets/3063b5d3-3385-4ea6-8316-30c7f48ee60f)
![image](https://github.com/user-attachments/assets/e332311d-fab2-46a0-8c03-16f98029269a)

Successfully established a connection with the Kali VM. This information can be seen in Command Prompt by running the command "netstat -anob".

![image](https://github.com/user-attachments/assets/6083f40e-9891-4af0-a35e-1319b17b2cf7)

![image](https://github.com/user-attachments/assets/db18c7ab-e43d-4754-9a0c-b4fa9db725ee)

The handler in the Kali VM confirms the connection was successful and then established a shell on the Windows VM.

![image](https://github.com/user-attachments/assets/3320dd0d-4bcb-4a1b-a37c-26ad12f469fd)
![image](https://github.com/user-attachments/assets/254df570-b14a-44c9-bef3-a1fbeb4f5ae5)

Ran the commands net user, net localgroup and ipconfig to retrieve information about the target Windows VM.

![image](https://github.com/user-attachments/assets/388b71ab-a869-4d21-8b6a-d3828549faa8)

Configured Splunk to ingest Sysmon logs by copying the input file from the "default" directory in Splunk to the "local" directory" and editing it with the Sysmon information.

![image](https://github.com/user-attachments/assets/652adf07-dbac-4788-ae65-42e7f503bb5b)

![image](https://github.com/user-attachments/assets/b86b61d6-69f2-4c53-bc6c-968e04365989)






