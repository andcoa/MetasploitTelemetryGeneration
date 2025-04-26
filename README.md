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
