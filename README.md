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
```
