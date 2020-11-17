## Threat

##### Internet
  
    1, DDoS
    2, APT
    3, Spoofing
    
###### Safety Defense
    
    1, Firewall
    2, IDS/IPS
    3, Honeypot
    
##### Website(Database)(Web Application)

    1, OWASP TOP10
    
###### Safety Defense

    1, WAF(Web Application Firewall)
    
## Practice(Using Iptable to Defense SYN Flood Attack)

##### Platform

    Attack Computer: Distro: Kali GNU/Linux 2020.3  Kernel: 5.7.0-kali1-amd64 x86_64
    
    Defense Computer: Distro: Ubuntu 20.04.1 LTS  Kernel: 5.4.0-54-generic x86_64
    
##### Step

###### 1, find target by using command "ip addr" on target Computer or "nmap -sn {ip}" on Attack Computer
###### 2, In this case we just going to use ip addr on Target Computer

![alt text](https://github.com/LunarstarPony/iPAS-Probably-Would-Win/blob/main/Class_Files/11_17_2020/1.png?raw=true)

###### 3, Start the attack using "hping3 -c 15000 -d 120 -S -w 64 -p 80 --flood --rand-source 192.168.1.159" 
    
