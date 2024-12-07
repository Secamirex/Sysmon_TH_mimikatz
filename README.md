# Sysmon_TH_mimikatz

Mimikatz is an open-source application that allows attackers to view and save authentication credentials such as Kerberos ticket.

In this lab, I have demonstrated three ways to identify the Mimikatz exploit using Sysmon from Sysinternals Suite. 

# Monitoring the files named 'mimikatz' 

Checking a mimikatz file created in the system is an option for detection. However, the file name can be changed easily, so it is easy to bypass.

On Sysmon, <strong>EventID 11 - File created </strong> will be generated upon unpacking the mimikatz file. 

![image](https://github.com/user-attachments/assets/93a5a970-7ab8-4fae-a672-c0babc1e886f)


 # Monitoring the 'mimikatz' executable hash

 When a process with hash values belonging to Mimikatz.exe is started, Sysmon generates an alert - <strong> Event ID 1 - Process Create </strong> as shown below.
 Note since the hash value will be changed with a small modification in the file, this method is not a reliable way to trace it. 



 # Tracking the 'lsass.exe" process 
 Mimikatz uses lsass.exe to capture passwords. With the monitoring of "lsass.exe", the processes that use it are also recorded. This way, not only mimikatz but all suspicious processes that use lsass.exe are recorded.

