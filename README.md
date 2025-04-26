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
![image](https://github.com/user-attachments/assets/b87de91b-2634-4727-bd32-3c9c6f2c80cb)



