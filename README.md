# BasiCUs 

Basic use cases that I consider that should be enabled/deployed, we will consider the use cases based on the log sources too taking into account the volume of the logs generated by the technology and the easiness of deploying the use case. We will split the UCs based on the system. 

All these detection rules will try to look for common TTPs used by APTs. All the rules will have a link to check it's logic. 

Checked most used TTPs to create the BasiCUs

https://resource.redcanary.com/rs/003-YRU-314/images/2020-Threat-Detection-Report.pdf

https://redcanary.com/threat-detection-report/techniques/windows-management-instrumentation/

### Core
- AV detection hacktool (cleaned or not) [AV cheatsheet @FlorianRoth](https://www.nextron-systems.com/wp-content/uploads/2021/03/Antivirus_Event_Analysis_CheatSheet_1.8.1.pdf)
-  

### Servers
- Webshell spawn
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_webshell_spawn.yml
- webshell recon commands
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_webshell_detection.yml
- whoami as SYSTEM
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_whoami_as_system.yml
- Enumerate local groups 

### Endpoints
- Multiple domain discovery commands
- Scheduled tasks
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_rare_schtasks_creations.yml
- Office launching command
  - https://github.com/SigmaHQ/sigma/blob/1f8e37351e7c5d89ce7808391edaef34bd8db6c0/rules/windows/process_creation/proc_creation_win_office_shell.yml
- Brute force login
- Clear command history
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_event_log_cleared.yml
- User added to admin groups


### DCs/AD
- Brute force
- User added to admin groups
- Login outside jump servers
- Kerberoasting
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_susp_rc4_kerberos.yml


### ATMs
- Enumerate local groups
  - Crear sigma
- whoami executed
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_susp_whoami.yml
