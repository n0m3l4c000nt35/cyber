# Recon

[Repo subfinder](https://github.com/projectdiscovery/subfinder)

```bash
subfinder -d hackerone.com -o subdomains.txt -rl 5 -t 5
```

[Repo httpx](https://github.com/projectdiscovery/httpx)

```bash
httpx -l subdomains.txt -o alive.txt
```

[Repo nuclei](https://github.com/projectdiscovery/nuclei)

```bash
nuclei -l alive.txt -o nuclei.txt
```