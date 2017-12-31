# Information Security Better Practises Guide for smaller businesses.

## What is in here?

1. Introduction
2. Why?
3. What is Information Security?
4. Principles for better control
5. Internet access
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
Welcome to the better practices guide to IT / Information security.  This document exists as a personal reference and because walking in to a small business do do a disaster recovery exercise is most frustrating.  The steps defined here are not the only way to achieve a good information security strategy, but they are a reasonable collection of steps and simple things that can be done to make your business more resilient and prevent catastrophic information loss.

Smaller businesses, in some ways, have the most to lose and are affected the most by viruses and hackers, but for the most part are the least protected.  Having good practices in place will help to limit the impact of a major incident.

## Why?
This guide exists because looking after small IT systems can often be much harder than looking after large ones.  At scale, there are more resources available to implement, monitor and control good IT practices, but for small systems, the IT guy is not necessarily employed full time, there isn't a big budget to spend on fancy tools and IT is a support service for the main business. Unfortunately, as many businesses have realised, while it is a support service, everything stops when it stops working.

This is not a best practices guide.  Best practices would invite a whole lot of debate about which is the right way to go.  This is a better practices guide because it contains very easy to implement solutions that shouldn't break the budget, but will give you some level of protection.

Finally, everyone is vulnerable.  You don't have to attract unwanted attention, you don't have to visit unsavoury websites, there is nothing specific that makes you a target, everyone is being targeted.

## What is information security?
Important documents used to be stored in a safe / locked cabinet.  This physical security meant that the key documents required to run your business were kept safe.  The size of the safe, how many documents were locked away, if there was a guard on the door, all depended on how important the information was.  Banks had bigger safes, the corner shop had a locked box.    

Today, the vast majority of business critical information is stored in some digital format.  This makes it easier to store, easier to share and easier to find.  However, it also poses a much larger threat to businesses.  No longer is corporate espionage, or miscreant thievery the biggest threat, but that posed by hackers and the authors of malicious viruses and malware.  The end goal may be to extract money (ransomware), or purely malicious destruction of property.

"Failing to plan, is planning to fail" (Alan Lakein) is a very appropriate description here.  Companies that blindly continue without stopping to plan a strategy around information security are the most at risk.

## Principles for better control
Regardless of the system you are putting in place.  These are the principles that need to be considered:
1. Limit the access to the people that need it.
2. Plan to have the system fail and have a recovery plan.
3. Test the recovery plan.
4. Assume that someone wants the information stored in your system, or at the very least, doesn't want you to have it.
5.  Work out how valuable the information is and what your competitor could do with it.


The rest of this guide contains practical steps that implement these principles.

## Internet access
The internet is an incredibly useful resource for businesses, but the inherent risk is that in most companies, the internet is always on, meaning that malicious individuals can constantly try and attack your network.

* Have a secure router / firewall.  
Ensure that between your business and the internet, there is a secure firewall.
** Don't leave the default password in place
** Don't open extra ports for convenience
** Check if your router is vulnerable
** Don't enable remote administration
** Log access attempts
** Update the firmware

* Use a secure VPN if you need to get back into the network.
While there are many VPN options out there, choose one that does the following:
** Has certificate based authentication - passwords are easy, certificates are infinitely harder.

* Check for known vulnerabilities
** [https://cve.mitre.org/]
** [https://www.cvedetails.com/]

## Windows updates
Windows updates are a pain.  They do break things and they can slow down work.  However, turning automatic updates off is something that should only be done if someone responsible is going to manually take over the process.  

From experience, the frustration of waiting for updates to complete before being able to use your computer pales into significance once the threat of viruses / malware is realised.

If automatic updates are turned off, create a checklist and a recurring diary entry to perform the updates manually.  Keep a record of when they were done and have a person dedicated to the task and a second person to check up on them.  

## Patch software products.
Any software that runs continuously needs to be kept up to date.  But not all software checks for updates on it's own.  Setup a schedule and a checklist and make sure that the software is kept patched and up to date.

## Ensure firewalls are turned on.
Either manage firewalls through active directory, or manually, but ensure that they are always turned on.  Turning a firewall off may make it easier to configure a system and get it working, but it removes a barrier for anyone trying to break in.  It is also one of the easiest steps to forget when setting a new system up.  Consider having a group policy rule that automatically re-enables the firewall after a predetermined period of time.

## Create system images.
Buying new computers and setting them up is probably one of the nicer IT tasks.  The user is generally happy and it doesn't generally involve finding obscure incompatibilities / bugs.  However, an often missed step is creating a system image once the new hardware is setup and configured.  Having a complete system image (however old), reduces the time required to restore the system in the event of hardware failure or a virus/malware attack.

If you store the system images on a network attached device, make sure to keep a copy that is not network attached just in case.  Some ransomware is capable of affecting the pc and any linked devices.

## Configure a NAS carefully.
A network attached storage device (NAS) is a great way to implement a backup for the information in your organisation.  However, the configuration of the NAS and the backup utility needs to be done carefully.

With Wannacry, any device presenting SMB (file shares) was potentially vulnerable.  

SFTP is a safer option, as is having the NAS run the backup software instead of the computers themselves.

Change the default admin password and make sure extra services are turned off if not required. (telnet, ssh, smb, webdav).

## Scan your network.
Zenmap is a great, easy to use tool that will help to quickly diagnose what services are running.  It is not a foolproof solution, but a quick scan with Zenmap can expose ports that have been in-advertently left open and misconfigurations that make the system vulnerable.

## Turn off RDP.
Remote desktop is very useful, but is another way into a system from the network.  If a single computer is compromised, any other devices on the network with RDP open, are now a target.  For most users, RDP isn't required and should be left off.

## Don't use admin accounts.
The temptation to grant users administrative rights in an active directory environment is great.  If a user is often making software changes, or as an IT administrator, you are often making changes, the tempation is to grant yourself admin rights.  

Working in an unprivileged account provides an additional level of protection if and when a machine is compromised.  Clicking on a bad link as an administrator is infitely worse than clicking on the same link as a normal user.

## Don't allow antivirus software to turn your firewall off.
Some antivirus software provides the option for the software to manage the firewall configuration for all connected devices.  This is great, but must be treated with care as it can be configured to turn the firewall off just as easily as it can be configured to turn it back on.

## Segregate shared offices.
If the IT department doesn't have full control over the devices in the network, segregate the network.   For example, if an office building has a single incoming fibre line that is shared by all the tennants, place a separate firewall between each separate tenant.  This means that any misconfiguration in the other tenants networks won't affect your computers / devices.

## Monitor your backups.
Don't setup a backup utility and blindly expect it to always run successfully.  Most backup utilities provide the option for notification emails.  Make use of this and monitor both success and failures.  

Backup to more than one location.  Have a non network connected backup, a nas (to allow for quick recoveries) and a cloud solution if possible.  This gives you the greatest coverage and ability to recover.

Cloud backups take your data offsite.
A NAS provides quick on-site access to the data and can run automatically.
The non-network connected backup (e.g. USB drive) provides a recovery method in the case of a virus taking everything down.
