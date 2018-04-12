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
- Practice paitence. Do not rush out and immediately submit the sample to VirusTotal. Malware can contain sensitive information, so submitting it to the public could put you at risk. Instead...
- Fingerprint the sample. We do this with hashes. Currently, VirusTotal accepts MD5, SHA1 and SHA256. I typically use SHA256.
  - On Windows systems, you can use PowerShell for this task.
    - ```Get-FileHash C:\Path\To\Sample\sample.exe.vir```
  - On Linux, you can use the sha256sum utility.
  - It may look something like this: ```1e55abb94951cedc548fd8d67bd1b50476808f1d0ae72f9842181761ff92f83f```
    - Go ahead, run that through VirusTotal. What does VirusTotal tell you about this hash?
