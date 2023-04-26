# MetasploitableV2
Running Metasploitable 2 as a Pentesting Lab



# Setting up the Environment

## Setting our environment
Our environment will be composed of several virtual machines. Our first task is making sure out host machine is capable of running multiple guest OSes.

## Hypervisor
There are several hypervisers available (VMWare, Virtualbox, Hyper-V, etc). I’m currently running Virtualbox but feel free to chose your own.

## Kali Linux
It’s possible to download and install Kali Linux from the project’s site. I advise to download a preconfigured ISO from Offensive Security (https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/).

## Update
Kali has lots of tools for pentesting. It’s paramount to keep them updated. Open the terminal and type:

```
$ apt-get update && apt-get upgrade -y && apt-get dist-upgrade -y && apt-get autoremove -y
```

# Metasploitable 2

![image](https://user-images.githubusercontent.com/91763346/234699595-45b637a6-0310-4cd2-b19c-615cba15a05a.png)

The metasploitable ISO is availble in Rapid 7’s site or on Sourceforge (http://sourceforge.net/projects/metasploitable/files/Metasploitable2/). The ISO is VMWare format.

Metasploitable is a testing environment that is very useful for beginner who wants to practice and test their penetration testing skills and security research. It is a target machine that is used to discover and penetrate vulnerabilities so that the user gets an idea of somewhat close to real-life targets and machines.

In other words, Metasploitable is a virtual machine intentionally vulnerable version of Ubuntu designed for testing security tools and demonstrating common vulnerabilities.

## Virtualbox
Unzip the file. Create a new VM. Choose Linux->Ubuntu (64bit), give it at least at least 1024MB RAM and do not create a HDD. Wait and add the disk *.vmdk:

![image](https://user-images.githubusercontent.com/91763346/234700718-922fc8a1-f10a-401d-895b-b4c2432f125d.png)

Change the network configuration:

![image](https://user-images.githubusercontent.com/91763346/234700764-ed6f56c5-6469-42cf-a9b1-c1ecdf3a4ca6.png)

## Network
Start the machine and determine its IP address:

```
$ ifconfig
```
![image](https://user-images.githubusercontent.com/91763346/234701951-b6eb0fba-bf58-43a1-90be-a907c6fa8123.PNG)


# Hacking Phases

Finding and fully exploiting system vulnerabilities takes great time and patience. A typical penetration testing requires the ethical hacker to bypass authorization & authentication mechanisms, then probe the network for potential data breaches and network security threats.

## 1. Reconnaissance

When it comes to penetration testing, the first natural question is – *What is the first hacking phase?*

Before performing any penetration tests, hackers footprint the system and gather as much information as possible. Reconnaissance is a preparatory phase where the hacker documents the organization’s request, finds the system’s valuable configuration and login information and probes the networks. This information is crucial to performing the attacks and includes:

* Naming conventions
* Services on the network
* Servers handling workloads in the network
* IP Addresses
* Names and Login credentials of users connected to the network
* The physical location of the target machine

## 2. Scanning
In this stage, a hacker begins testing the networks and machines to identify potential attack surfaces. This involves gathering information on all machines, users, and services within the network using automated scanning tools. Penetration testing typically undertakes three types of scans:

* Network Mapping
This involves discovering the network topology, including host information, servers, routers, and firewalls within the host network. Once mapped, white hat hackers can visualize and strategize the next steps of the ethical hacking process.

* Port Scanning
Ethical hackers use automated tools to identify any open ports on the network. This makes it an efficient mechanism to enumerate the services and live systems in a network and how to establish a connection with these components.

* Vulnerability Scanning
The use of automated tools to detect weaknesses that can be exploited to orchestrate attacks.

## 3. Gaining Access
Once ethical hackers expose vulnerabilities through the process’s first and second hacking phases, they now attempt to exploit them for administrative access. The third phase involves attempting to send a malicious payload to the application through the network, an adjacent subnetwork, or physically using a connected computer. Hackers typically use many hacking tools and techniques to simulate attempted unauthorized access, including:

* Buffer overflows
* Phishing
* Injection attacks
* XML External Entity processing
* Using components with known vulnerabilities

If the attacks are successful, the hacker has control of the whole or part of the system and may simulate further attacks such as data breaches and Distributed Denial of Service (DDoS).

## 4. Maintaining Access
The fourth phase of the ethical hacking process involves processes to ensure the hacker can access the application for future use. A hacker continuously exploits the system for further vulnerabilities and escalates privileges to understand how much control attackers can gain once they pass security clearance. Some attackers may also try to hide their identity by removing the evidence of an attack and installing a backdoor for future access.

## 5. Clearing Tracks
To avoid any evidence that leads back to their malicious activity, hackers perform tasks that erase all traces of their actions. These include:

Uninstalling scripts/applications used to carry out attacks
Modifying registry values
Clearing logs
Deleting folders created during the attack
For those hackers looking to maintain undetected access, they tend to hide their identity using techniques such as:

* Tunneling
* Stenography

Having successfully performed all the 5 steps of ethical hacking, the ethical hacker then concludes the steps of ethical hacking by documenting a report on the vulnerabilities and suggesting remediation advice. 
