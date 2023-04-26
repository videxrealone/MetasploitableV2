
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

# Setting up Metasploit

To work, msf uses Postgres and also needs to have the **msfdb** initialized.

![image](https://user-images.githubusercontent.com/91763346/234705535-27106ac1-e966-4b0b-bb00-d3781c8e76c4.png)

![image](https://user-images.githubusercontent.com/91763346/234706013-d6bc067c-9666-441e-94aa-410a3794a993.png)

## Running msfconsole

To run metasploit, we just need to start **msfconsole**

```
$ sudo msfconsole
```
![image](https://user-images.githubusercontent.com/91763346/234706472-6a1dbaaa-7077-4050-9e40-3be077aaa5fd.png)

# Active & Passive Recon

As seen in the first part of the repo, the first phase is recon.
The most common tools used for this are:
* Shodan:

Shodan (Sentient Hyper-Optimised Data Access Network) is a search engine designed to map and gather information about internet-connected devices and systems. Shodan is sometimes referred to as a search engine for the internet of things (IoT).  Applications of the software include market research, vulnerability analysis and penetration testing, as well as hacking.

Shodan makes it possible to detect devices that are connected to the internet at any given time, the locations of those devices and their current users. Such devices could be in almost any type of system, including business networks, surveillance cameras, industrial control systems (ICS) and smart homes. Shodan attempts to grab the system’s banner directly, gathering the data by way of the associated server’s ports. Banner grabbing is a key step for penetration testing as it helps identify vulnerable systems. Shodan also searches corresponding exploits in the search platform’s exploit section.

* whois:

The whois system is a listing of records that contains details about both the ownership of domains and the owners. The Internet Corporation for Assigned Names and Numbers (ICANN) regulates domain name registration and ownership, but the list of records is held by many companies, known as registries.

* nslookup:

Name server lookup (nslookup) is a command-line tool that lets you find the internet protocol (IP) address or domain name system (DNS) record of a specific hostname. This command also allows reverse DNS lookup by inputting the IP addresses of the corresponding domains.

## Testing the whois command

The target site will be **hackthissite.org** which is a free, safe and legal training ground for hackers to test and expand their ethical hacking skills with challenges, CTFs, and more.

![5](https://user-images.githubusercontent.com/91763346/234708591-a475bf48-4de1-4dd4-9b87-d6f865c2c1dc.PNG)

## Testing the nslookup command

![image](https://user-images.githubusercontent.com/91763346/234708678-498b7816-0ead-45e5-b7e0-43cc56117b3b.png)

## Using Shodan to Gather Intel

![image](https://user-images.githubusercontent.com/91763346/234709012-c91c2b9e-f042-404c-9794-2c97ac081374.png)

## gathering intel from one of the DNS servers

![image](https://user-images.githubusercontent.com/91763346/234709265-bcc301ef-0e78-492b-9791-10268066865c.png)

We can see the following IP **116.203.6.3**. Let's try to gather more info from that ip.

![image](https://user-images.githubusercontent.com/91763346/234709411-abddf5b7-bde7-4430-8bcb-a33e7cc3a6fe.png)

## Digging intel from the DNS Records.

DNS records (aka zone files) are instructions that live in authoritative DNS servers and provide information about a domain including what IP address is associated with that domain and how to handle requests for that domain. These records consist of a series of text files written in what is known as DNS syntax.

![image](https://user-images.githubusercontent.com/91763346/234709801-500b2fd7-81c2-4d5a-81e2-09c67bf633a7.png)

# Vulnerability Scan & Assessment

Vulnerability assessment refers to the process of identifying risks and vulnerabilities in computer networks, systems, hardware, applications, and others...

## Checking for open ports

Metasploit comes with a number of scanners.
Let's use a simple **SYN** scanner.

![image](https://user-images.githubusercontent.com/91763346/234710403-dab44bf5-e7ff-4723-8ed0-ec10cb604eb8.png)

```
use auxiliary/scanner/portscan/syn
set rhosts 192.168.56.102 - 103
set threads 50 -- for better performance
run
```

![image](https://user-images.githubusercontent.com/91763346/234711211-35bb39d8-f5f4-4aa8-a290-83e9daba5a4b.png)

## Checking for SMB version

The Server Message Block (SMB) protocol is a network file sharing protocol that allows applications on a computer to read and write to files and to request services from server programs in a computer network. The SMB protocol can be used on top of its TCP/IP protocol or other network protocols.

![image](https://user-images.githubusercontent.com/91763346/234711743-4e96d781-d3e3-40d3-865f-d7efe37fae93.png)

## Checking for SSH version

The Secure Shell Protocol is a cryptographic network protocol for operating network services securely over an unsecured network. Its most notable applications are remote login and command-line execution. SSH applications are based on a client–server architecture, connecting an SSH client instance with an SSH server.

![image](https://user-images.githubusercontent.com/91763346/234712419-a0a25226-5325-45c7-a243-c1d09c0a236b.png)

## Checking for FTP version

The File Transfer Protocol is a standard communication protocol used for the transfer of computer files from a server to a client on a computer network. FTP is built on a client–server model architecture using separate control and data connections between the client and the server.

![image](https://user-images.githubusercontent.com/91763346/234712724-a1b843c3-893c-4c43-8baf-c36a35fd329f.png)

## Exploiting ftp with the vsftpd_backdoor exploit

![image](https://user-images.githubusercontent.com/91763346/234713228-63943673-efc5-4260-abbd-560e0851f960.png)

In 2011, attackers managed to place a code snippet with a backdoor to vsFTPd 2.3.4 version source code.

If you installed vsFTPd 2.3.4 version with changed source code in 2011, you might be impacted by this vulnerability. People with malicious intent who exploit this vulnerability can access to user rights with the highest authorisation in the target system.

![image](https://user-images.githubusercontent.com/91763346/234713120-1e01731b-5c11-4ea0-a887-76d7c9490456.png)

We can see that we successfully got access and have pwned the machine.

## Exploiting ssh with a user:pass Bruteforce

In this exploit, we will create 2 files that could work as a dictionary attack ( upon doing all the recon and intel gathering we can create possible passwords combos )

![image](https://user-images.githubusercontent.com/91763346/234714744-d0c319a6-4da6-4b3c-adf6-06912663d9e4.png)

![image](https://user-images.githubusercontent.com/91763346/234714791-b8363bd0-d9cc-4a8a-b10e-72fa00fc64a5.png)

We can see that we have a succesful login attempt, on session 2.

Let's switch to that session with the command:

```
$ sessions
$ sessions 2
```

![image](https://user-images.githubusercontent.com/91763346/234714987-fd5b4769-c579-4086-9d3f-7da0a486266f.png)
