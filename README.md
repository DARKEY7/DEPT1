# DEPTH1-VULNHUB

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


![2024-09-23_13-15](https://github.com/user-attachments/assets/344c81dd-1f25-4c32-b646-6feb898dbab9)



![2024-09-23_13-16](https://github.com/user-attachments/assets/15aac728-efab-4171-a4e3-a5c55ca0f10f)


 
 listing out for user name
 ![2024-09-23_13-18](https://github.com/user-attachments/assets/e861d113-8f3a-42b9-a3a4-9616fa4865a9)


![2024-09-23_13-18_1](https://github.com/user-attachments/assets/4d44a837-285e-456d-9d4a-c8cde7615465)

::::::::getting the shell:::Boooooyahhhhhhhhhh:""""::: 

![2024-09-23_13-19](https://github.com/user-attachments/assets/3201771e-e8c8-4ab3-818e-e05b9b1beb08)

  
 that's went quiet  easy DEPTH1---VULNHUB





  
















