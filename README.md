# Information Security Better Practises Guide for smaller businesses.

## What is in here?

1. Introduction
2. Why?
3. Principles for better control
4. Internet access
5. Updates
6. Email
7. Local Network
8. File Sharing
9. Backups
10. Antivirus
11. Disaster Recovery
12. Disclosure
13. Auditing  
Appendix:
* Further reading

## Introduction
Welcome to the better practices guide to IT / Information security.  This document exists as a personal reference and because walking in to a small business to do a disaster recovery exercise and realising that the entire problem could have been avoided is very frustrating.  The steps defined here are not the only way to achieve a good information security strategy, but they are a reasonable collection of steps and simple things that can be done to make your business more resilient and prevent catastrophic information loss.  I don't know everything, but we have to start somewhere and I hope that by sharing this as a resource, I can help more than just the companies that I work with.

Smaller businesses, in some ways, have the most to lose and are affected the most by viruses and hackers, but for the most part are the least protected, because of the constraints on resources.  There are lots of good practices that can protect a business without requiring a large investment in infrastructure.  Just by configuring your existing systems well, you can, for the most part, limit the risk of a virus / malware getting into your system and causing problems.

## Why?
This guide exists because looking after small IT systems can often be much harder than looking after large ones.  At scale, there are more resources available to implement, monitor and control good IT practices, but for small systems, the IT guy is not necessarily employed full time, there isn't a big budget to spend on fancy tools and IT is something that is just expected to work.

This is not a best practices guide.  Best practices would invite a whole lot of debate about which is the right way to go.  This is a better practices guide because it contains very easy to implement solutions that shouldn't break the budget, but will give you some level of protection.

Finally, everyone is vulnerable.  You don't have to attract unwanted attention, you don't have to visit unsavoury websites, there is nothing specific that makes you a target, everyone is being targeted.

## Principles for better control
Regardless of the system you are putting in place.  These are the principles that need to be considered:
1. Limit the access to the least number of people that need it.
2. Expect that the system / device will fail and you will need to recover somehow.
3. Test the recovery plan.
4. Assume that someone wants the information stored in your system, or at the very least, doesn't want you to have it.
5. Work out how valuable the information is and what your competitor could do with it.  Use that as a guide to how well you need to protect the system.

The rest of this guide contains practical steps that implement these principles.

## Internet access
The internet is an incredibly useful resource for businesses, but the inherent risk is that in most companies, the internet is always on, meaning that malicious individuals can constantly try and attack your network.

* Have a secure router / firewall.  
  * Ensure that between your business and the internet, there is a secure firewall.
  * Don't leave the default password in place
  * Don't open extra ports for convenience
  * Check if your router is vulnerable
  * Don't enable remote administration
  * Log access attempts
  * Update the firmware
  * Scan your public IP address from outside your network

* Use a secure VPN if you need to get back into the network, don't open RDP. [LockCrypt spreading via RDP](https://www.alienvault.com/blogs/labs-research/lockcrypt-ransomware-spreading-via-rdp-brute-force-attacks)
While there are many VPN options out there, choose one that does the following:
  * Has certificate based authentication - passwords are easy, certificates are infinitely harder.
  * Has a good reputation
  * Lets you grant access and revoke access to individuals
  * Doesn't automatically give the user access to everything in your network.

* Check for known vulnerabilities for your router
  * [https://cve.mitre.org](https://cve.mitre.org/)
  * [https://www.cvedetails.com/](https://www.cvedetails.com/)

## Updates
Windows updates are a pain.  They do break things and they can slow down work.  They are particularly frustrating when you turn your computer on to quickly do something and realise that you are going to wait a half hour while it thinks about life.  The frustration of waiting for updates to complete before being able to use your computer pales into significance though when you have started your computer and been greeted with a virus / ransomware notice.

* Don't turn automatic updates off.
* Regularly check that they are being applied
* If automatic updates are turned off, create a checklist and a recurring diary entry to perform the updates manually.  
* Keep a record of when they were done and have a person dedicated to the task and a second person to check up on them.  

### Patch software products.
* Any software that runs continuously needs to be kept up to date.  But not all software checks for updates on it's own.  
* Setup a schedule and a checklist and make sure that the software is kept patched and up to date.  
* Keep an inventory of what software is installed in your organisation and update it regularly.

### Patch hardware
* Update the firmware on device such as routers, Wifi access points, etc...  

## Email
For smaller organisations, running your own mail server can be a very challenging task.

Mail servers are always on, always facing the internet and plagued by vulnerabilities.  If the number of users isn't too large, consider using a hosted service, where someone else can manage the risks at scale.  

* Have a spam filter and configure it.
* Have DKIM & SPF records setup.
* Have strong passwords
* Do not re-use passwords
* Do not use passwords that are combinations of the company / user name.
* If you use a hosted service, consider turning on 2 factor authentication and keep the admin passwords safe.
* Backup your email inbox regularly.  Losing all of your emails is a huge risk to a company.  Consider storing the emails in another format.  Printing to pdf or at the least, copying them to an archive.
The advantage that [Office365](https://www.office.com) and [Google Mail](https://www.gmail.com) provide, is that they can deal with spam, viruses, targeted attacks on a much larger scale.  Doing the same internally for your business is expensive.

## Local network
All companies have some form of network.  It might be a single ethernet cable from your router to your computer, a Wifi access point, or a big network.  Regardless of the size, some of the same good practices apply.

### Ensure firewalls are turned on.
Either manage firewalls through active directory, manually, or via your anti-virus software, but ensure that they are always turned on.  Turning a firewall off may make it easier to configure a system and get it working, but it removes a barrier for anyone trying to break in.  It is also one of the easiest steps to forget when setting a new system up.  Consider having a group policy rule that automatically re-enables the firewall after a predetermined period of time.

### Don't share the Wifi password with everyone
The temptation is to share the Wifi password with customers, vendors and suppliers who visit the office.  Unfortunately, this means that the computer for that person will now always be able to connect to your network.  

For most offices, the Wifi signal is strong enough that you can sit outside in your car and access the Wifi.  This means that after hours, anyone with the Wifi password can sit outside your building and play with your network.

If you  do have lots of visitors coming into the building, setup a guest Wifi that only provides internet access and doesn't provide any internal network access.


### Scan your network.
Zenmap is a great, easy to use tool that will help to quickly diagnose what services are running.  It is not a fool proof solution, but a quick scan with Zenmap can expose ports that have been in-advertently left open and misconfigurations that make the system vulnerable.

[Zenmap](https://nmap.org/zenmap/)
[Useful commands](https://www.cyberciti.biz/networking/nmap-command-examples-tutorials/)

### Turn off RDP.
Remote desktop is very useful, but is another way into a system from the network.  If a single computer is compromised, any other devices on the network with RDP open, are now a target.  For most users, RDP isn't required and should be left off.

[LockCrypt spreading via RDP](https://www.alienvault.com/blogs/labs-research/lockcrypt-ransomware-spreading-via-rdp-brute-force-attacks)

### Don't use admin accounts for general use.
The temptation to grant users administrative rights in an active directory environment is great.  If a user is often making software changes, or as an IT administrator, you are often making changes, the temptation is to grant yourself admin rights.  

Working in an unprivileged account provides an additional level of protection if and when a machine is compromised.  Clicking on a bad link as an administrator is infinitely worse than clicking on the same link as a normal user.

### Don't allow antivirus software to turn your firewall off.
Some antivirus software provides the option for the software to manage the firewall configuration for all connected devices.  This is great, but must be treated with care as it can be configured to turn the firewall off just as easily as it can be configured to turn it back on.

### Segregate shared offices.
If the IT department doesn't have full control over the devices in the network, segregate the network.   For example, if an office building has a single incoming fibre line that is shared by all the tenants, place a separate firewall between each separate tenant.  This means that any misconfiguration in the other tenants networks won't affect your computers / devices.

## File sharing
Sharing access to files is critical for most businesses.  However, the more that is shared, the more that can be damaged by malware.

* Turn of SMB V1.  SMB is the protocol that windows uses to share files.  Version 1 of the protocol has some serious problems and needs to be turned off to protect your business.
* Only share the files that need to be shared.  While you may trust everyone in the business, if the engineering team doesn't need access to the accounting files, don't share them.
* Don't re-use passwords.
* Don't have generic accounts that anyone can access.

## Backups
The most important part of setting up a reliable computer system for a company is having a good backup program.  By program, I don't mean a specific piece of software (although that helps), but a documented, tested system of backing up your data.

* Test the backup regularly!
* Have multiple forms of backup.  Automated, manual, online, offline, on-site, off-site.
* Expect to recover from:
  * Hardware failure (e.g. a power surge destroying the file server).
  * Virus / malware (e.g. Wannacry encrypting all online documents).
  * Corruption (e.g. a word file that can't be opened).
  * The building catching fire (Keep a copy offsite)

### Suggested system

* Backup every few hours to a network attached storage device.
* Backup every few hours to the cloud.
* Backup full system images weekly for critical systems.
* Backup full system images to a USB hard drive and keep offsite.
* Password protect your backups.
* Test your recovery.  Know how to do it and know that it works.  
* Test that the backup covers all the files you need.  It is a horrible feeling to open a backup and not be able to find the one file you need.
* Explain to everyone in the organisation, what is backed up, how and what is not.  
* Don't leave your backups to run blind.  Have automated emails that let you know when the backup fails.

### Create system images.
Buying new computers and setting them up is probably one of the nicer IT tasks.  The user is generally happy and it doesn't generally involve fixing some obscure problem that is stopping the user from working.  However, an often missed step is creating a system image once the new hardware is setup and configured.  Having a complete system image (however old), reduces the time required to restore the system in the event of hardware failure or a virus/malware attack.  

* Don't store the images on a generally accessible device.
* Scan for viruses before creating an images
* Keep offline copies
* Update the image when you make significant changes (e.g. upgrading the operating system)

### Configure a NAS carefully.
A network attached storage device (NAS) is a great way to implement a backup for the information in your organisation.  However, the configuration of the NAS and the backup utility needs to be done carefully.

With Wannacry, any device presenting SMB (file shares) was potentially vulnerable.  

SFTP is a safer option, as is having the NAS run the backup software instead of the computers themselves.

Change the default admin password and make sure extra services are turned off if not required. (telnet, ssh, smb, webdav).

### Monitor your backups.
Don't setup a backup utility and blindly expect it to always run successfully.  Most backup utilities provide the option for notification emails.  Make use of this and monitor both success and failures.  

Backup to more than one location.  Have a non network connected backup, a NAS (to allow for quick recoveries) and a cloud solution if possible.  This gives you the greatest coverage and ability to recover.

* Cloud backups take your data offsite.
* A NAS provides quick on-site access to the data and can run automatically.
* The non-network connected backup (e.g. USB drive) provides a recovery method in the case of a virus taking everything down.

## Antivirus

* Do use anti-virus software on all your computers.
* Consider using an anti-virus application that doesn't just check for virus signatures, but also watches for suspicious behaviour.
* Avoid the free anti-virus software packages, unless you can work out why it is free.
* Do update the anti-virus signatures regularly.

## Disaster Recovery
Run a disaster recovery exercise.  Don't run it against your live system.  Beg, buy, borrow a separate server and attempt to recover from a disaster.  The exercise has 2 purposes, the first is to confirm that you have everything you need to recover, the second is to know how to do it.  When you eventually need to recover from a disaster, you will need to do it quickly.

Work out what systems you can't live without for the business and know how you can keep the business running while you fix the problem.

## Disclosure
If you store confidential information, have a plan for how you will disclose any leaked information to your customers.  Consider if you really need to store the information, and if not, get rid of it.


# Auditing  
Both internal and external audits can be a real benefit in ensuring that your IT systems are configured well.
