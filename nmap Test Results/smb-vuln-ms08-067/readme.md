Commands:

1,Check what Devices is online using "nmap -sn 192.168.43.0/24"

Output: 

Starting Nmap 7.80 ( https://nmap.org ) at 2020-10-19 08:49 EDT

Nmap scan report for Lunarstar-Tablet (192.168.43.11)

Host is up (0.0082s latency).

MAC Address: 00:15:00:F0:00:5A (Intel Corporate)

Nmap scan report for lunarsta-hypod2 (192.168.43.20)

Host is up (0.00037s latency).

MAC Address: 00:0C:29:84:00:0B (VMware)

Nmap scan report for xp-pc (192.168.43.49)

Host is up (0.00053s latency).

MAC Address: 00:0C:29:6A:63:39 (VMware)

Nmap scan report for Lunarstar-LT (192.168.43.52)

Host is up (0.00040s latency).

MAC Address: 54:8D:5A:A5:82:4B (Unknown)

Nmap scan report for 192.168.43.75

Host is up (0.057s latency).

MAC Address: 00:15:00:F0:00:5A (Intel Corporate)

Nmap scan report for 192.168.43.125

Host is up (0.0066s latency).

MAC Address: 40:B0:76:E0:51:64 (Asustek Computer)

Nmap scan report for LunarKali (192.168.43.183)

Host is up (0.015s latency).

MAC Address: 00:15:00:F0:00:5A (Intel Corporate)

Nmap scan report for Lunarstar-Kali (192.168.43.153)

Host is up.

Nmap done: 256 IP addresses (8 hosts up) scanned in 1.48 seconds

2, Target found 

Nmap scan report for xp-pc (192.168.43.49)
Host is up (0.00053s latency).

MAC Address: 00:0C:29:6A:63:39 (VMware)

3,Check if smb-vuln-ms08-067 is working using "nmap --script smb-vuln-ms08-067.nse -p445 192.168.43.49"

Output Results: 

Starting Nmap 7.80 ( https://nmap.org ) at 2020-10-19 08:38 EDT                                                                                                                                                                            
Nmap scan report for xp-pc (192.168.43.49)                                                                                                                                                                                                 
Host is up (0.00028s latency).                                                                                                                                                                                                             

PORT    STATE SERVICE

445/tcp open  microsoft-ds

MAC Address: 00:0C:29:6A:63:39 (VMware)


Host script results:

| smb-vuln-ms08-067: 

|   VULNERABLE:

|   Microsoft Windows system vulnerable to remote code execution (MS08-067)

|     State: VULNERABLE

|     IDs:  CVE:CVE-2008-4250

|           The Server service in Microsoft Windows 2000 SP4, XP SP2 and SP3, Server 2003 SP1 and SP2,

|           Vista Gold and SP1, Server 2008, and 7 Pre-Beta allows remote attackers to execute arbitrary

|           code via a crafted RPC request that triggers the overflow during path canonicalization.

|           
|     Disclosure date: 2008-10-23

|     References:

|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-4250

|_      https://technet.microsoft.com/en-us/library/security/ms08-067.aspx

Nmap done: 1 IP address (1 host up) scanned in 0.56 seconds
