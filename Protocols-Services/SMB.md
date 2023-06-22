# SMB Signing

sudo nmap -Pn -p137,139,445 --script smb2-security-mode 10.10.10.0/24 | egrep 'Nmap scan report for|Message signing' | egrep -B 1 'Message signing enabled but not required|Message signing not enabled'

sudo nmap -p137,139,445 --script smb-security-mode <target>

nmap --script smb-enum-*,smb-vuln-*,smb-ls.nse,smb-mbenum.nse,smb-os-discovery.nse,smb-print-text.nse,smb-psexec.nse,smb-security-mode.nse,smb-server-stats.nse,smb-system-info.nse,smb-protocols -p 139,445 10.11.1.111

nmap --script smb-enum-domains.nse,smb-enum-groups.nse,smb-enum-processes.nse,smb-enum-sessions.nse,smb-enum-shares.nse,smb-enum-users.nse,smb-ls.nse,smb-mbenum.nse,smb-os-discovery.nse,smb-print-text.nse,smb-psexec.nse,smb-security-mode.nse,smb-server-stats.nse,smb-system-info.nse,smb-vuln-conficker.nse,smb-vuln-cve2009-3103.nse,smb-vuln-ms06-025.nse,smb-vuln-ms07-029.nse,smb-vuln-ms08-067.nse,smb-vuln-ms10-054.nse,smb-vuln-ms10-061.nse,smb-vuln-regsvc-dos.nse -p 139,445 10.11.1.111

enum4linux -a 10.11.1.111

rpcclient -U "" 10.11.1.111
	srvinfo
	enumdomusers
	getdompwinfo
	querydominfo
	netshareenum
	netshareenumall

smbclient -L 10.11.1.111
smbclient //10.11.1.111/tmp
smbclient \\\\10.11.1.111\\ipc$ -U john
smbclient //10.11.1.111/ipc$ -U john  

winexe -U username //10.11.1.111 "cmd.exe" --system

smbtree 10.11.1.111

nmblookup -A target

smbmap -u victim -p s3cr3t -H 10.11.1.111
