<h1 align="center"> XRayGen

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![Telegram][telegram-shield]][telegram-url]

</h1>

<h3><strong>V2RayGen/XRayGen</strong>: A Fast and Automated Script for XRay/V2Ray Server Setup</h3>

[**Usage**](#usage)

[**Quick Setup**](#quicksetup)

[**Examples**](#examples)

[**Options**](#options)

[**Block List**](#blocklist)

[**License**](#license)

[**Donate Me**](#donateme)

## **Prerequisites & Dependencies**

- `Python3`
- `Docker`
- `Docker Compose`
<p>If your server lacks Docker and Docker-Compose, the script will install them and launch XRay-Core automatically.</p>

use **sudo** if your current user is not in the docker group or you don't have docker installed

## **How Does XRayGen Work?**

<p>XRayGen uses Docker to retrieve the xray-core image from the Docker registry. It then generates a configuration file to launch the XRay container.

A client-side configuration file is also created for use with XRay-core or V2Ray-core.

The XRayAgent provides user management for XRay configuration, offering CRUD operations.</p>

## **Usage**

`curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | python3 - -h`

![Sample](contents/content1.png)

<br>

## **QuickSetup**

You can use one of the following protocols for installation and change its settings according to your needs.

| Protoctol           | Argument             |
| ------------------- | -------------------- |
| VMESS WS            | --vmess              |
| VMESS WS TLS        | --vmess --tls        |
| VMESS TCP           | --vmess --tcp        |
| VMESS TCP TLS       | --vmess --tcp --tls  |
| VLESS WS TLS        | --vless              |
| VLESS TCP TLS       | --vless --tcp        |
| VLESS TCP XTLS      | --vless --tcp --xtls |
| TROJAN WS TLS       | --trojan             |
| TROJAN TCP TLS      | --trojan --tcp       |
| TROJAN TCP XTLS     | --trojan --xtls      |
| ShadowSocks TCP     | --shadowsocks        |
| ShadowSocks TCP TLS | --shadowsocks --tls  |

### **Quick `Xray` Setup with Default Setting** :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vmess
```

OR

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py --output V2RayGen.py
sudo python3 V2RayGen.py --vmess
```

![Sample](contents/content3.png)

<p>Use the provided link for your client, or use the client-side JSON configuration with XRay-Core or V2Ray-Core. If your server is on a domain, simply change the IP to your domain or subdomain after importing the link to your V2Ray client.</p>

# **Examples**

**Setup XRAY / ShadowSocks :**

VLESS :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vless
```

VMESS + TLS with blocking option :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vmess --tls --block
```

VMESS + TLS with blocking iranian domains and IPs option :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vmess --tls --blockir
```

VMESS + Changing client-side HTTP and SOCKS port :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vmess --chttp 4020 --csocks 8080
```

VMESS + TCP Network Stream :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vmess --tcp
```

VMESS + TCP Network Stream + TLS and QRCode :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vmess --tcp --tls --qrcode
```

VLESS + Using Google DNS :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vless --dns google
```

VLESS + TCP + XTLS :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --vless --tcp --xtls
```

ShadowSocks + adding shadowsocks port to server :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | sudo python3 - --shadowsocks --firewall
```

**Parsing Configuration :**

Parse & reading Configuration file :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | python3 - --parseconfig config.json
```

Parse URL and read information :

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py | python3 -  --parse vmess://eyJhZGQiOiIxMjcuMC4wLjEiLCJhaWQiOiIwIiwiaG9zdCI6IiIsImlkIjoiM2JlNjE2NzktOGQzOC00ZWJiLWJjOGItMTQ4ZjE0ZWY5ZTc3IiwibmV0Ijoid3MiLCJwYXRoIjoiL2dyYXBocWwiLCJwb3J0IjoiNDQzIiwicHMiOiJ4cmF5IiwidGxzIjoidGxzIiwidHlwZSI6Im5vbmUiLCJ2IjoiMiIgfQ==
```

---

# **XRayAgent**

XRayAgent is a Simple User Management for XRay Configuration

### Download Script & Run With Python3:

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/V2RayGen.py --output /tmp/v.py && python3 /tmp/v.py --agent
```

OR

```bash
curl https://raw.githubusercontent.com/SonyaCore/V2RayGen/main/XRayAgent.py --output XRayAgent.py
python3 XRayAgent.py
```

> By default it loads `config.json` for loading configuration

> For loading other configuration simply enter the name of the configuration after XRayAgent.py :

```bash
python3 XRayAgent.py config.json
```

## XRayAgent Commands :

```python3
  add, adduser                      Adding user
  update, updateuser                Update existing user with their index ID
  del, deluser                      Delete existing user with ther index ID
  users, listusers                  List of users

  deliptables, deleteiptables       Delete rules on server-side port
  climit , conlimit                 Add IP limitations on server-side port

  p, port                           Change server side port
  h, help                           Get help
  v, version                        Get version of program
  q, quit                           Exit program
```

after adding an user a index will be created for that user for example :

```bash
Index : 0 {'id': '25ad6df8-9a54-4f6e-8c44-d5685359a7ce', 'level': 0, 'email': 'example@example.com'}
Index : 1 {'id': '62bf2d5d-766b-4281-963a-544449a26b4f', 'level': 0, 'email': 'cLkx4WC0@protonmail.com'}
```

and now you can update that user with ther index ID :

```python3
cmd > : update 1
Index 1 Selected
Leave the section empty if you don't want to modify that section
New Email : test@gmail.com
New ID : 62bf2d5d-766b-4281-963a-544449a26b4f
Index 1 Updated
vless://62bf2d5d-766b-4281-963a-544449a26b4f@127.0.0.1:443?path=/graphql&security=tls&encryption=none&type=ws#xray
```

> Use Index ID for `update` , `del`

> For Showing list of Users and their Indexs use `users` or `listusers` command

<br>

### IPTABLES Section :

using `climit` or `conlimit` limits the total connection ips on server side port

for deleting the all rules on server side port use `deliptables` or `deleteiptables`

---

# **Options**

you can change server-side configuration with this options

## Server Side

### Protocols

`vmess` Creating vmess with default options.

`vless` Creating VLess with default options.

`shadowsocks` Creating ShadowSocks with default options.

> you can combine arguments with default options to change the behavior of your configuration for example :
>
> --vmess --port 8080 --tls --tcp --linkname TESTSERVER
>
> this will create a vmess with port 8080 and self-signed tls , then gives a link with TESTSERVER name

### Log & DNS Settings:

`dns` for using custom dns instead system's default dns configuration.

List of loglevels :

```
debug : Information for developers. All "Info" included.

info : Running stats of XRay，no effect for the functions. All "Warning"
included.

warning : usually some external problem that does not affect V2Ray but possibly the user experience.

error : XRay encountered a problem that needs to be resolved immediately.

none : Nothing will be printed.
```

> ex :
>
> --loglevel debug will set your logging level to debug mode
>
> logs will be printed on your container docker. you can view the logs with `docker logs <containerid>`

**Supported DNS providers:**

> list of avaliable dns's.
>
> ex : --dns google will set your server side configuration dns to google

| DNS        |
| ---------- |
| google     |
| cloudflare |
| opendns    |
| quad9      |
| adguard    |

> https://www.v2ray.com/en/configuration/dns.html

### Routing Options

`block` for adding blocking Bittorrent and Ads.

`blockir` for Blocking Bittorrent, Ads and Iranian IPs in routing configuration.

> The routing function module can send inbound data through different outbound connections according to different rules, so as to achieve the purpose of on-demand proxy.

> For example, the common usage is to divert domestic and foreign traffic, Xray can judge the traffic in different regions through the internal mechanism, and then send them to different outbound proxies.

> https://xtls.github.io/config/routing.html#routingobject

### Inbounds

`tls` Using TLS in specified protocol

> tls option can be used for any v2ray protocol for example :
>
> --vmess --tls will create a vmess with self-signed tls
>
> `it's important to enable allow insecure tls on your client`

`xtls` Using XTLS in specified protocol

> XTLS only supports (TCP, mKCP) so by default when you use --xtls argument tcp mode is being used for vless
>
> also xtls doesn't support vmess protocol

`port` for changing configuration port.

> if you want your v2ray to be listening on a different port use this option

`uuid` for using custom uuid configuration.

> by default random uuid will be generated. use this option if you want to have a custom uuid or existing uuid configuration
>
> ex : --uuid ca33b7a2-26d6-47b1-a3c4-471425d868b9

`id` custom alterID.

`insecure`, Disable Insecure Encryption. [deprecated]

### Stream Settings:

stream settings is the network type of the stream transport. and by default this script will use websocket for using it with nginx and cdn

`tcp` Using TCP network stream.

`wspath` Changing default WebSocket path configuration.

> default web socket path is /graphql change it with this option.
>
> ex :
>
> --wspath /myservice

`header` Using custom header obfuscation configuration.

> `Make sure your header file look like the below JSON` :

```
{
  "header": {
    "type": "http",
    "response": {
      "version": "1.1",
      "status": "200",
      "reason": "OK",
      "headers": {
        "Content-Type": [
          "application/octet-stream",
          "application/x-msdownload",
          "text/html",
          "application/x-shockwave-flash"
        ],
        "Transfer-Encoding": ["chunked"],
        "Connection": ["keep-alive"],
        "Pragma": "no-cache"
      }
    }
  }
}
```

> header argument is useful when needing another http request configuration you can pass your http request configuration with this option.
>
> --header request.json

> Visit below site for HTTPRequest Object :
> https://www.v2ray.com/en/configuration/transport/tcp.html#httprequestobject

`linkname` for changing linkname after generating configuration.

#### Link formats :

##### `VMess` :

```json
vmess://{"add":"ip / domain ","aid":"alterid","host":"","id":"random-uuid","net":"ws","path":"websocket-path","port":"80","ps":"linkname","tls":"","type":"none","v":"2" }
```

##### `VLess` :

```json
vless://random-uuid@ip:port?path=websocketpath&security=type&encryption=none&type=ws#linkname
```

##### `Trojan` :

```json
trojan://password@ip:port?allowInsecure=insecure&security=&type=networkstream#linkname
```

##### `ShadowSocks` :

```json
ss://shadowsocks-security-method:random-uuid@domain/ip :port
```

## Client Side

after generating the configuration with desired protocol client-side configuration is also generated as well

you can use client-side configuration directly with xray-core or v2ray-core

`security` security method for client-side configuration.

List of security methods :

- `aes-128-gcm`
- `chacha20-poly1305`
- `auto`
- `none`
- `zero`

`csocks` client-side SOCKS port . default: [10808]

`chttp` client-side HTTP port . default: [10809]

`qrcode` Generate QRCode for generated link.

> if you want to import your configuration with qrcode use this argument.

## ShadowSocks

shadowsocks are loaded with xray docker container and it uses tcp stream for passing traffic

`sspass` set password for shadowsocks configuration file. by default, it uses a random password

`ssmethod` Set cipher method for ShadowSocks . default cipher method is `2022-blake3-chacha20-poly1305` to provide better security hence it's only usable in xray-core. for using shadowsocks with v2ray core use one of the below cipher methods :

V2Ray Cipher methods :

- `2022-blake3-chacha20-poly1305`
- `2022-blake3-aes-256-gcm`
- `2022-blake3-aes-128-gcm`

XRay Cipher methods :

- `2022-blake3-chacha20-poly1305`
- `2022-blake3-aes-256-gcm`
- `2022-blake3-aes-128-gcm`
- `xchacha20-ietf-poly1305`

---

## Parsing Configuration

for parsing existed configuration or decoding vmess url use below options :

`parse` for parsing encoded link. supported formats are [vmess://,ss://]

`parseconfig` for reading the configuration file and parsing information

> `--parseconfig config.json` will show the information of the configuration and generate a QR code for that

---

## **Block List**

Block lists are files that can be used in V2Ray clients that allow users to block or direct individual connections. These lists can be used to blacklist specific IP addresses or domains, or to whitelist trusted ones.

In some countries, such as Iran, authorities actively try to block access to VPN services by monitoring requests sent from foreign IP addresses to local servers. When such requests are detected, the associated IP addresses are added to a blacklist, effectively blocking access to VPNs. As a result, users in these countries may need to disable their VPN connection in order to access local websites without issue. Block lists can help circumvent these restrictions by allowing users to selectively block or redirect certain connections, thereby avoiding detection by authorities.

This files are avaliable under [geodata][geodata] directory

### Block List Sources

The ads list is provided by the [PersianBlocker](https://github.com/MasterKia/PersianBlocker) list.

The iraninan CIDR is provided by the [IP2Location](<https://lite.ip2location.com/iran-(islamic-republic-of)-ip-address-ranges?lang=en_US>) site.

---

## DonateMe

If this Project helped you, you can also help me by donation

### ![tron-button] &nbsp; TTTo7aasobgqH5pKouCJfmPYn2KLed2RA3

### ![bitcoin-button] &nbsp; bc1qgdav05s04qx99mdveuvdt76jauttcwdq687pc8

### ![ethereum-button] &nbsp; 0xD17dF52790f5D6Bf0b29151c7ABC4FFC4056f937

### ![tether-button] &nbsp; 0xD17dF52790f5D6Bf0b29151c7ABC4FFC4056f937

## License

Licensed under the [GPL-3][license] license.

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[tron-button]: https://img.shields.io/badge/TRX-Tron-ff69b4
[tether-button]: https://img.shields.io/badge/ERC20-Tether-purple
[bitcoin-button]: https://img.shields.io/badge/BTC-Bitcoin-orange
[ethereum-button]: https://img.shields.io/badge/ETH-Ethereum-blue
[contributors-shield]: https://img.shields.io/github/contributors/SonyaCore/V2RayGen?style=flat
[contributors-url]: https://github.com/SonyaCore/V2RayGen/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/SonyaCore/V2RayGen?style=flat
[forks-url]: https://github.com/SonyaCore/V2RayGen/network/members
[stars-shield]: https://img.shields.io/github/stars/SonyaCore/V2RayGen?style=flat
[stars-url]: https://github.com/SonyaCore/V2RayGen/stargazers
[issues-shield]: https://img.shields.io/github/issues/SonyaCore/V2RayGen?style=flat
[issues-url]: https://github.com/SonyaCore/V2RayGen/issues
[telegram-shield]: https://img.shields.io/badge/Telegram-blue.svg?style=flat&logo=telegram
[telegram-url]: https://t.me/ReiNotes
[license]: LICENCE
[geodata]: geodata
