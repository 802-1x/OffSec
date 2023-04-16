# RDP
General Notes
* RDP is typically not the first vector to target. Enumeration is easy, but exploitation can be more effective if targeting SMB et al.

## RDP Reconnaissance

Retrieve NETBIOS, FQDN, hostname, remote system time, certificate details, product version (tends to lag even on updates sytems, but can be indicative of patching problems), can find self-signed certificate finding
```
nmap -A -Pn -p3389 <IP>
```

Is NLA enabled?
```
nmap -p 3389 --script rdp-enum-encryption <ip>
```

Let's enumerate cryptographic protocol support. openssl no longer supports legacy protocols, but gives additional information above nmap for what it can detect.
```
openssl s_client -connect <host>:443 -tls1
openssl s_client -connect <host>:443 -tls2
openssl s_client -connect <host>:443
```
```
sudo nmap --script ssl-enum-ciphers -p 443 <ip>
```

Credential bruteforce
```
ncrack -vv -u <username> -P <password file.txt> rdp://<IP>
ncrack -vv -u <users.txt> -P <password file.txt> rdp://<IP>
```

## Defensive Engineering

1) Monitor successful RDP attempts through EDR reporting
2) Monitor logs for RDP threshold alerting
