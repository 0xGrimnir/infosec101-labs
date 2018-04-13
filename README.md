# Information Security 101: Practical Experience (Labs)

### Part of my Information Security 101 Series.
- [Information Security 101: The Reading List](https://github.com/MalwareJedi/infosec101-reading)
- [Information Security 101: The Community](https://github.com/MalwareJedi/infosec101-community)
- **[Information Security 101: Hands-On Experience with Information Security](https://github.com/MalwareJedi/infosec101-labs)**
- Information Security 101: Certifications and Degrees (Coming soon.)
- Information Security 101: Careers and Career Paths (Coming soon.)

#### Follow me on Twitter:
[![Twitter Follow](https://img.shields.io/twitter/follow/MalwareJedi.svg?style=social&label=Follow%20%40MalwareJedi)](https://twitter.com/MalwareJedi)

--- 

## Table of Contents
- [Overview]()
- [Lab I: Handling Malicious Software]()
- [Lab II: Web Application Security with OWASP]()
- [Lab III: Digital Forensics: The Order of Volatility]()
- [Additional Resources for Hands-On Experience]()

---

## Overview

I think we can all agree that practical, hands-on experience is one of the most fundamental necessities for breaking into the Information Security industry. It's important to understand that Information Security is not a "first tier" concept; you are likely, and probably should be, coming from some previous technical background. In order to be successful in Information Security, you will likely also want to have a firm grasp on the fundamental Information Technology/Computer Science concepts. With that in mind, let's take a look at some common tasks or concepts within the Information Security industry - some will be tasks you may perform on a daily basis, depending on your job description, whilst others look at popular vulnerable applications that you can use to hone your skills.

---

## Lab I: Handling Malicious Software

Malware. In the Information Security industry, malware is going to be something you frequently see. Depending on what kind of work you do within the industry, you may even deal with malware daily. But, even if you do not, it's still important to understand how to handle malicious samples.

Everyone wants to play around with malware - I mean, c'mon, it's extremely cool! Unfortunately, proper handling of malware samples is often overlooked, and can cause unintentional infections. For this lab, feel free to spin up any virtual machine you feel comfortable with as we will not be dealing with actual malware, but rather, discussing how to properly handle malicious samples. 

### Handling Procedures

To begin, create a new file within your VM. To simplify things, it can even just be a .txt file. We're going to pretend that this file is a suspected piece of malware, and we're going to treat it with caution.

When analyzing malware, it often needs to be done on a system that can actually be infected by the malware; especially for dynamic malware analysis. As such, we have to ensure that whilst handling that malware sample, we don't accidentally execute the sample and infect ourselves (until such time as we're ready to do so.) Follow along with these procedures in your VM where applicable:

- Append a new extension to the file - such as **.vir**. 
  - On Windows, you may have to enable file extensions in order to do this.
  - If your suspected malicious file is "**sample.exe**" it should now look like "**sample.exe.vir**".
  - The .vir extension is a pretty common extension to go with for this task, as it is not associated with any Windows program, and therefore cannot be accidentally executed.
- When working on samples outside of your analysis lab, antimalware solutions may gobble up your sample and send it to quarantine. White-list the .vir extension, to prevent the installed antimalware solution from interfering with your sample.
- Practice patience. Do not rush out and immediately submit the sample to VirusTotal. Malware can contain sensitive information, so submitting it to the public could put you at risk. Instead...
- Fingerprint the sample. We do this with hashing. Currently, VirusTotal accepts MD5, SHA1 and SHA256. I typically use SHA256.
  - On Windows systems, you can use PowerShell for this task.
    - ```Get-FileHash C:\Path\To\Sample\sample.exe.vir```
  - On Linux, you can use the sha256sum utility.
  - It may look something like this: ```1e55abb94951cedc548fd8d67bd1b50476808f1d0ae72f9842181761ff92f83f```
    - Go ahead, run that through VirusTotal. What does VirusTotal tell you about this checksum?
  - Hashing the suspected file allows you to search the VirusTotal database (and other similar sites), for a match. If one is found, you have more information about your malware. If not, you didn't run the risk of accidentally submitting a file that may contain sensitive information. This also can tell you that you may have targeted threats to deal with.
- Archive the file for transportation. Don't forget the password.
  - Typically, this is done with (.zip)ing the file. I also, occasionally, (.rar) it.
  - Only put one sample per archive, if at all possible.
  - When archiving your sample, make sure you password protect the archive. And if you're sending it via email, you may want to encrypt the file names.
    - Typically "infected" is the industry-standard password when archiving a malware sample.
    - Unfortunately, certain services (GMail included), know to look for zipped archives and automatically test "infected" as the password. Thus blocking the file as malicious.
    - GMail also forbids password protected files with encrypted file names.
    - I often use "inf3cted" in lieu of "infected."
  - Make sure to include the hash results in your archive, containing the SHA256 checksum generated for your sample. You can either include it as a file, or as an archive note with WinRAR.

Whew! Don't you feel a little bit safer already, knowing how to properly handle malicious samples? Here are a few additional things to consider when playing around with malware:

- If you're using virtual machines as part of your malware analysis toolkit - and why wouldn't you be, as they make excellent analysis environments - make sure you learn the fine art of "snapshotting." This will allow you to easily roll back to a non-infected state once you're finished with your analysis work.
- Also, you need to get in the habit of making sure that your analysis environment has file extensions enabled, and hidden system files are being shown. Make sure to look into editing the registry to enable visibility of ```super hidden``` folders and files, as well! (Shout out to [@SageFedora](https://twitter.com/sagefedora) for this tip.) If you snapshot your virtual analysis environments correctly, all of this will be ready to go each and every time.
- Most importantly: Research. Do not just spin up a virtual machine and drop some malware in it to start playing with. Research how to properly build a safe, sterile analysis environment to minimize the risk of damaging your host system. There are plenty of guides on how to develop a safe analysis environment, and I'll be creating one of my own eventually as well - to accompany this Information Security 101 series. (Albeit, that'll probably go along with a future series I have planned for Malware Analysis. So stay tuned!)

--- 

## Lab II: Web Application Security with OWASP

Moving away from malware a bit, let's take a look at web application security. 

In 2018, the world is web-centric. It's easy to understand, then, why web application security is important. No organization may possibly understand that more than OWASP. And they make that known with the release of their documentation, vulnerable applications (for testing), and lists! In this lab, I'm going to introduce you to several of the vulnerable web applications that OWASP has released, but it'll be up to you to pick one and go through it. So, let's dive right in...

| Application Name | OWASP Designation | More Information|
| :---: | :---: | :---: |
| Hackademic Challenges Project | Online | [More information.](http://hackademic1.teilar.gr) |
| Juice Shop | Online | [More information.](https://juice-shop.herokuapp.com/) |
| Broken Web Applications Project (BWA) | Virtual Machine | [More information.](http://code.google.com/p/owaspbwa/wiki/ProjectSummary) |
| Brick | Offline | [More information.](http://sechow.com/bricks/index.html) |
| .NET Goat | Offline | [More information.](https://github.com/jerryhoff/WebGoat.NET) |
| NodeGoat | Offline | [More information.](https://www.owasp.org/index.php/OWASP_Node_js_Goat_Project) |
| Rails Goat | Offline | [More information.](https://www.owasp.org/index.php/OWASP_Rails_Goat_Project) |
| Security Shepherd | Offline | [More information.](https://www.owasp.org/index.php/OWASP_Security_Shepherd) |
| WebGoat | Offline | [More information.](https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project)
| WebGoatPHP | Offline | [More information.](https://www.owasp.org/index.php/WebGoatPHP) |

As far as my personal pick goes: WebGoat is a favorite of mine. Security Shepherd comes highly recommended to me by long-term (13 years!) OWASP Indianapolis Founder and Leader Carl Sampson ([@chs](https://twitter.com/chs)). Whichever you pick, the most important part is to stick with it. Learn the underlying technology behind the vulnerable web application. Learn how the vulnerabilities work at a technical level. For additional reading in this area, pick up the [Web Application Hacker's Handbook](https://www.amazon.com/Web-Application-Hackers-Handbook-Exploiting/dp/1118026470) and the [Browser Hacker's Handbook](https://www.wiley.com/en-us/The+Browser+Hacker%27s+Handbook-p-9781118662090). More resources similar to this, just not authored by OWASP, can be found in the final section of this article.

--- 

### Lab III: Understanding the Order of Volatility
