This report is about a local network scan I performed using Nmap inside Kali Linux, running on a UTM virtual machine on my Mac.

First, I checked that Nmap was installed using:
```nmap --version```

Then I found my local IP address using:
```ip a```
My IP was `192.168.64.1`, and the subnet was `192.168.64.0/24`.

To scan the whole subnet, I ran:
```sudo nmap -sS 192.168.64.0/24 -oN scan.txt -oX scan.xml```

This scan gave me a list of devices connected to my network and what ports were open. For example:
- `192.168.64.1` had port 80 open (a web server)
- `192.168.64.10` had port 22 (SSH) and 445 (SMB) open

The output showed that some services could be vulnerable if not properly configured or updated. SSH and SMB especially can be dangerous if they're exposed without proper protection.

I also opened Wireshark, started capturing traffic on the eth0 interface, and ran the same Nmap scan again. I could see SYN, SYN-ACK, and RST packets in Wireshark which confirmed the scan was working.

Files I have saved:
- scan.txt: the main Nmap scan output
- scan.xml: same scan in XML
- scan.html: converted from XML using xsltproc
- capture.pcapng: Wireshark packet capture
- a few screenshots of the terminal and Wireshark

In conclusion, Doing this task gave me a better understanding of how Nmap works and how to use it to scan local networks. I learned what kind of services are usually running on different devices and how open ports can lead to potential security issues, like exposed SSH or SMB. I also got hands-on experience analyzing scan results and identifying which services might be risky if not properly secured.

## 🧑‍💻 Environment Details
- **Operating System**: Kali Linux (running in UTM VM on macOS)
- **Nmap Version**: 7.95
- **Virtualization Platform**: UTM
- **Local IP**: (e.g., 192.168.64.1)
- **Target Subnet**: 192.168.64.0/24
