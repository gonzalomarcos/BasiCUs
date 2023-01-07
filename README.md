# BasiCUs 

## Idea
The main idea of this project is deploying basic use cases that I consider that should be enabled/deployed in every SIEM. The rules have been considered based on the log sources, taking into account the volume of the logs generated by the source and the easiness of deploying the use case. We will split the UCs based on the system source. 

I have splited the UCs in the following environments:
- Core
  - Should be present across all systems
- Servers
  - Internet facing servers and internal servers
- Endpoints
  - Users endpoints
- DCs/AD
  - Uses cases based on domain controllers or common attacks to active directory
- ATMs
  - ATMs use cases

All these detection rules will try to look for common TTPs used by APTs. All the use cases will have a sigma link to check it's logic. 
Checked most used TTPs to create the BasiCUs

## Prioritization

| ![alt text](https://www.picussecurity.com/hubfs/logo-original.svg "Picus")  | ![alt text](https://www.crowdstrike.com/wp-content/themes/main-theme/images/logos/crowdstrike/RedLogoCS.svg "CrowdStrike")  | ![alt text](https://cms.recordedfuture.com/uploads/brand_logo_long_black_f2ead5b5c6.svg?w=1920 "Recorded Future") | ![alt text](https://avatars.githubusercontent.com/u/6877001?s=200&v=4 "Red Canary") | 
| ------------- | ------------- | ------------- | ------------- |
|Process Injection | Masquerading | Security Software Discovery | Process Injection| 
|PowerShell | Command-line Interface | Obfuscated Files or Information | Scheduled Task| 
|Credential Dumping | Credential Dumping | Process Injection | Windows Admin Shares| 
|Masquerading | PowerShell | System Information Discovery | PowerShell| 
|Command-line Interface | Hidden Files and Directories | Process Discovery | Remote File Copy| 
|Scripting | Process Injection | Software Packing | Masquerading| 
|Scheduled Task | Registry Run Keys / Startup Folder | DLL Side-Loading | Scripting| 
|Registry Run Keys / Startup Folder | System Owner/User Discovery | Data Encrypted | DLL Search Order Hijacking| 
|System Information Discovery | Account Discovery | Execution Through API | Domain Trust Recovery| 
|Disabling Security Tools | Scripting | Standard Cryptographic Protocol | Disabling Security Tools | 

[For more information about the Top 10 TTPs][1]

## Use Cases

### Core
- AV detection hacktool (cleaned or not) [AV cheatsheet @FlorianRoth](https://www.nextron-systems.com/wp-content/uploads/2021/03/Antivirus_Event_Analysis_CheatSheet_1.8.1.pdf) 
- User added to local admin
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_user_added_to_local_administrators.yml
 

### Servers
- Webshell spawn
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_webshell_spawn.yml
- webshell recon commands
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_webshell_detection.yml
- whoami as SYSTEM
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_whoami_as_system.yml
- Enumerate local groups 
  - https://github.com/gonzalomarcos/BasiCUs/blob/main/rules/win_security_local_groups_enumeration.yml

### Endpoints
- Scheduled tasks
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_rare_schtasks_creations.yml
- Office launching command
  - https://github.com/SigmaHQ/sigma/blob/1f8e37351e7c5d89ce7808391edaef34bd8db6c0/rules/windows/process_creation/proc_creation_win_office_shell.yml
- Clear command history
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_event_log_cleared.yml



### DCs/AD
- Special user logon
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_admin_logon.yml
- User added to admin groups
- Login outside jumpservers
  - https://github.com/gonzalomarcos/BasiCUs/blob/main/rules/win_security_ad_logon_outside_jumpservers.yml
- Kerberoasting
  - https://github.com/SigmaHQ/sigma/blob/8b749fb1260b92b9170e4e69fa1bd2f34e94d766/rules/windows/builtin/security/win_security_susp_rc4_kerberos.yml


### ATMs
- Enumerate local groups
  - https://github.com/gonzalomarcos/BasiCUs/blob/main/rules/win_security_local_groups_enumeration.yml
- whoami executed
  - https://github.com/SigmaHQ/sigma/blob/master/rules/windows/process_creation/proc_creation_win_susp_whoami.yml






[1]: https://www.picussecurity.com/resource/the-top-ten-mitre-attck-techniques
