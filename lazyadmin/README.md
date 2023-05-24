# Lazy Admin
IP: 10.10.57.66

## Open Ports/Services
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 497cf741104373da2ce6389586f8e0f0 (RSA)
|   256 2fd7c44ce81b5a9044dfc0638c72ae55 (ECDSA)
|_  256 61846227c6c32917dd27459e29cb905e (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

## Directories
- /content -> CMS SweetRice
  - /inc
    - /mysql_backup/ -> found via searchsploit
  - /as - Login page

## Credentials
- `manager:Password123` -> found in mysql backup (hash cracked with CrackStation)

## Access
- exploit `php/webapps/40700.html`
- user.txt = `THM{63e5bce9271952aad1113b6f1ac28a07}`

## Privilege Escalation
- `sudo -l` > (ALL) NOPASSWD: /usr/bin/perl /home/itguy/backup.pl
- possible to modify copy.sh which backup.pl runs (rev shell)
- `root.txt` > THM{6637f41d0177b6f37cb20d775124699f}

SOLVED
