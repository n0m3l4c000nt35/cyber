## Password Manager

- [https://proton.me/pass](https://proton.me/pass)
- [https://bitwarden.com/](https://bitwarden.com/)

## Note Taking

### Processing

- [https://notion.so/](https://notion.so/)
- [https://www.xmind.net/](https://www.xmind.net/)
- [https://obsidian.md/](https://obsidian.md/)

### Results

- [Ghostwriter](https://github.com/GhostManager/Ghostwriter)
- [pwndoc](https://github.com/pwndoc/pwndoc)

### Logging

PS1

```bash
PS1="\[\033[1;32m\]\342\224\200\$([[ \$(/opt/vpnbash.sh) == *\"10.\"* ]] && echo \"[\[\033[1;34m\]\$(/opt/vpnserver.sh)\[\033[1;32m\]]\342\224\200[\[\033[1;37m\]\$(/opt/vpnbash.sh)\[\033[1;32m\]]\342\224\200\")[\[\033[1;37m\]\u\[\033[01;32m\]@\[\033[01;34m\]\h\[\033[1;32m\]]\342\224\200[\[\033[1;37m\]\w\[\033[1;32m\]]\n\[\033[1;32m\]\342\224\224\342\224\200\342\224\200\342\225\274 [\[\e[01;33m\]$(date +%D-%r)\[\e[01;32m\]]\\$ \[\e[0m\]"
```

### Screenshots

- [Flameshot](https://github.com/flameshot-org/flameshot)
- [Peek](https://github.com/phw/peek)

---

## Update OS

```bash
sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt autoclean -y
```

```powershell
Get-ExecutionPolicy -List
Set-ExecutionPolicy Unrestricted -Scope Process
Get-ExecutionPolicy -List
Install-Module PSWindowsUpdate
Import-Module PSWindowsUpdate
Install-WindowsUpdate -AcceptAll
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
choco upgrade chocolatey -y
choco info vscode
choco install wsl2 python git vscode openssh openvpn nmap wireshark burp-suite-free-edition heidisql sysinternals putty golang neo4j-community openjdk microsoft-windows-terminal
RefreshEnv

Add-MpPreference -ExclusionPath "C:\Users\$env:USERNAME\AppData\Local\Temp\chocolatey\"
Add-MpPreference -ExclusionPath "C:\Users\$env:USERNAME\Documents\git-repos\"
Add-MpPreference -ExclusionPath "C:\Users\$env:USERNAME\Documents\scripts\"
```

##  Active Directory Enumeration & Attacks

### Obtener y visualizar información de un AD

| Tool | Description | OS | Lenguaje |
| - | - | - | - |
| [PowerView](https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1) | Obtiene información de un AD | Windows | PowerShell |
| [SharpView](https://github.com/dmchell/SharpView) | Obtiene información de un AD | Windows | C# |
| [SharpHound](https://github.com/SpecterOps/BloodHound-Legacy/tree/master/Collectors) | Obtiene información de un AD para usar en BloodHound | Windows | C# |
| [BloodHound](https://github.com/SpecterOps/BloodHound) | Visualiza las relaciones en un AD | X | X |
| [BloodHound.py](https://github.com/fox-it/BloodHound.py) | Obtiene información de un AD | Linux | Python |
| [NetExec](https://www.netexec.wiki/ldap-protocol/bloodhound-ingestor) | Obtiene información de un AD | Linux | X |

```bash
nxc ldap 10.10.11.174 -d support.htb --dns-server 10.10.11.174 -u 'support' -p 'Ironside47pleasure40Watchful' --bloodhound -c All
```

### Enumerar usuarios

```bash
kerbrute userenum -d domain.tld --dc <ip-dc> /wordlist/path -o valid_ad_users
nxc smb <ip> -u '<user>' -p '<password>' --users
rpcclient -U '<user>' --password '<password>' <ip>
```

### Password Spraying

```bash
for u in $(cat <users-list>);do rpcclient -U "$u%" --password '<password>' -c "getusername;quit" <ip> | grep Authority; done
kerbrute passwordspray -d <domain> --dc <ip> <users-list>  '<password>'
nxc smb <ip> -u <users-list> -p '<password>'
```

## LDAP

[Apache Directory Studio](https://directory.apache.org/studio/)
> Apache Directory Studio is a complete directory tooling platform intended to be used with any LDAP server however it is particularly designed for use with ApacheDS.

```bash
ldapsearch -H ldap://support.htb -x -D "ldap@support.htb" -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' -b "dc=support,dc=htb" "(objectClass=*)"
ldapsearch -H ldap://support.htb -x -D "ldap@support.htb" -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' -b "dc=support,dc=htb" "Administrator"
```

## WinRM

```bash
evil-winrm -i 10.10.11.174 -u support -p 'Ironside47pleasure40Watchful'
```

## Decompilers

- [AvaloniaILSpy](https://github.com/icsharpcode/AvaloniaILSpy)

## Miscellaneous
[Wine](https://www.winehq.org/)
> Permite correr software de Windows en otros sistemas operativos.
