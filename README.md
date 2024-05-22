## What is this?
This is a fork of the [wirehole](https://github.com/IAmStoxe/wirehole) repository by Devin Stokes.
In this fork, Shadowsocks support has been added.
ShadWireHole is a combination of ShadowSocks, WireGuard, PiHole, and Unbound in a docker-compose project with the intent of enabling users to quickly and easily create and deploy a personally managed full or split-tunnel WireGuard VPN with ad blocking capabilities (via Pihole), and DNS caching with additional privacy options (via Unbound). 

### Quickstart
To get started all you need to do is clone the repository and spin up the containers.

```bash
git clone https://github.com/GubaidullinED/shadwirehole.git
cd shadwirehole
docker-compose up
```
### Full Setup
```bash
#!/bin/bash

# Prereqs and docker
sudo apt-get update &&
    sudo apt-get install -yqq \
        curl \
        git \
        apt-transport-https \
        ca-certificates \
        gnupg-agent \
        software-properties-common

# Install Docker repository and keys
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) \
        stable" &&
    sudo apt-get update &&
    sudo apt-get install docker-ce docker-ce-cli containerd.io -yqq

# docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose &&
    sudo chmod +x /usr/local/bin/docker-compose &&
    sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

# wirehole
git clone [https://github.com/IAmStoxe/wirehole.git](https://github.com/GubaidullinED/shadwirehole.git) &&
    cd wirehole &&
    docker-compose up

```


Within the output of the terminal will be QR codes you can (if you choose) to setup it WireGuard on your phone.

```bash
wireguard    | **** Internal subnet is set to 10.6.0.0 ****
wireguard    | **** Peer DNS servers will be set to 10.2.0.100 ****
wireguard    | **** No found wg0.conf found (maybe an initial install), generating 1 server and 1 peer/client confs ****
wireguard    | PEER 1 QR code:
wireguard    | █████████████████████████████████████████████████████████████████
wireguard    | █████████████████████████████████████████████████████████████████
wireguard    | ████ ▄▄▄▄▄ █▀▀▀▄ ▀▀▀▀▄█ ██   ▄▀ ██ ██▄▀█    █▄▄█▀ ▄ ██ ▄▄▄▄▄ ████
wireguard    | ████ █   █ █▀▄█▀█▄█▄██▀▄   ▀▀██▀▄█ ▀▄█  ▀ █▀▄█▄ ▄▄▄ ██ █   █ ████
wireguard    | ████ █▄▄▄█ █▀█   ▀▀▄                               ▄██ █▄▄▄█ ████
wireguard    | ████▄▄▄▄▄▄▄█   ▀ ▀   █                         █▄█▄▀ █▄▄▄▄▄▄▄████
wireguard    | ████ ▄▄  █▄▄▄  ▄▀█▀▀▄    ▀█ ▀█  ▄  █▀▀▄▄██▄▄▀▀█▄ ██▀▀ █ █▄█ ▀████
wireguard    | █████  ▄█ ▄  ▀▀█▄▄  █▀ ▀ ▀ ▄  ▄ ▀▄▀▀█ ██ ▀██▀   ▀ ▀▀   ▀  ▀▄ ████
wireguard    | ████▀▀██  ▄▄▄ ██▀▄▄██▀ ██▀▄  ▀▀ █▄█   ▄ ▄█▄██   ▀▄▄█  █▀▀█ ▄▀████
wireguard    | ████ ▄█▀█▀▄▄   ▄███ ▄█ ▀▀▀▀█ ▄█ ▀▀▀▀▀▄ █   █ ███▄ █ ▄▄▄▄▀▀▀ █████
wireguard    | ████▀▄ ▀▀ ▄▄ ▄▄  █▀██    ▀▀▀▀▀  ▄  █▀▀██  ██▀   ▀█▄█▄█  ▄▄▀ ▀████
wireguard    | ████   ▀█ ▄▄                                          █  ▀▀██████
wireguard    | ███████  ▄▄█ █                                        ▄█▀█▀▀▄████
wireguard    | ████ ▄  █▄▄▀  ▄   ▀▄ █ ▄██▀▀█▀   █▄▄█▀▄█▀█▄ █ ▀▄█ ▄█ ▀   █  █████
wireguard    | ████▄██▀█▄▄ ▀ ▄▀                       ▀▄  ▄█ ▀▄  █▀ ▀██▀▄███████
wireguard    | ████ ▀█  ▄▄▄ ██▀███▄█▄█ █▄█▀ ▀ ▄▄▄ ▀▀  ▀▄ ▀▀█   █ █  ▄▄▄   ▄▀████
wireguard    | ████▄██  █▄█  █                                          ▀▀ ▀████
wireguard    | █████▀█▄▄▄▄▄ █▄ ▀▄ ██  ██▀ ▄ █▄ ▄▄▄▀ ▀▄▀█  █▀ █▄ ▄ ▄▄▄  ▄ ▀▄█████
wireguard    | █████▀▄▀  ▄▄█▄▀ ██▄▄▄    █▀  ██    ██ █▄   ██▄ ▄▀█▄██▀▄█   █▀████
wireguard    | ████▄   ▀ ▄ ▀ ▀▀▀▀▀▀█▀██▀ █  █▀█▀███ ▀▄█  █▄ █     ▀▀█▀██▀ ▄█████
wireguard    | ████ ▀ ▄   ██▄ ▀▀▀▄▀█  ▀▀▄ ▄ ▄  █▀▀▄█ ▄█▄▀█▄█▀ ▄▀█▄▀ ▀▀▀ ▀▀ ▀████
wireguard    | ███████ ▄█▄  ▀█▄▄  ▀█ █▀ █▀▄ ▄ ▀▄█▄▄█▀▄█▄▄▄▄█▀ ▀█ █▀  ▄ ██▀▄█████
wireguard    | ████▀█ █▀ ▄                                             █ ▄▀█████
wireguard    | ████▀▄ ▄▄█▄▄  ▄ ▄██▄ ▀ █ ▀ ▄▄█▀▀ ▄ ▀▀▄█▀▄██▀▀ ▄   ▄▄▄▄▀▀▄▀▀▀ ████
wireguard    | ████ ▀▄▄▀▀▄▀▀▀▄ ▄ █▄▄▀ ██▀▄▀ █▄██▀▀▄█▄▄█ ████▄ ▀█▄█▀▄▀ ▀▄ ▀ █████
wireguard    | ████ ▀ ▀▀▄▄ ▄ █▄ ▄ ██ ▄▀█▄▄  ▄ ▄ █▄▀ ▄▄▀██▄▀▀██▀▀▄▄ ▄   ██ ▄▀████
wireguard    | ██████████▄█▀▀█ ▄█ █▄▄ ▀▄▀█▀▀  ▄▄▄ ▀█▀█ ▄▀█▀█▀▀ ██▄▀ ▄▄▄ ▄██▄████
wireguard    | ████ ▄▄▄▄▄ █▄▄▄█▀▄█▀██ ▄ ▀█ ▀  █▄█ ▀▀█▄ ██▄█ ▀▄ ▀█▄▄ █▄█    █████
wireguard    | ████ █   █ █  ▄▄ ▄█   ▄▄█ █▀   ▄ ▄  █ ▄█▄▄█ █▀ ▄████ ▄▄  ▀▀▄▄████
wireguard    | ████ █▄▄▄█ █ ▀ ▄▄█ ▄ ▀▀▄██▄▀█▀█ █▀█▀▀▀▄   ▄ █▀▀▄▀ ▄▀███▀██▀██████
wireguard    | ████▄▄▄▄▄▄▄█▄██▄▄█▄▄▄▄▄██▄█▄▄▄█▄█▄█▄▄▄▄█▄▄▄█████▄▄█▄█▄▄████▄█████
wireguard    | █████████████████████████████████████████████████████████████████
wireguard    | █████████████████████████████████████████████████████████████████
wireguard    | [cont-init.d] 30-config: exited 0.
wireguard    | [cont-init.d] 99-custom-scripts: executing...
wireguard    | [custom-init] no custom files found exiting...
wireguard    | [cont-init.d] 99-custom-scripts: exited 0.
wireguard    | [cont-init.d] done.
wireguard    | [services.d] starting services
```

---

## Recommended configuration / Split tunnel:

Modify your wireguard client `AllowedIps` to `10.2.0.0/24` to only tunnel the web panel and DNS traffic.

---

## Access PiHole

While connected to WireGuard, navigate to http://10.2.0.100/admin

*The password (unless you set it in `docker-compose.yml`) is blank.*

![](https://i.imgur.com/hlHL6VA.png)

---

## Configuring for Dynamic DNS (DDNS)
If you're using a dynamic DNS provider, you can edit `docker-compose.yml` under "wireguard". 
Here is an excerpt from the file. 

You need to uncomment `#- SERVERURL` so it reads `- SERVERURL` without the `#` and then change `my.ddns.net` to your DDNS URL.

```yaml
wireguard:
   # ...
    environment:
      # ...
      - SERVERURL=my.ddns.net #optional - For use with DDNS (Uncomment to use)
      # ...
 # ...
```

---
## Configuring / Parameters

Container images are configured using parameters passed at runtime (such as those above). These parameters are separated by a colon and indicate `<external>:<internal>` respectively. For example, `-p 8080:80` would expose port `80` from inside the container to be accessible from the host's IP on port `8080` outside the container.

| Parameter | Function |
| :----: | --- |
| `-p 51820/udp` | wireguard port |
| `-e PUID=1000` | for UserID - see below for explanation |
| `-e PGID=1000` | for GroupID - see below for explanation |
| `-e TZ=Europe/London` | Specify a timezone to use EG Europe/London |
| `-e SERVERURL=wireguard.domain.com` | External IP or domain name for docker host. Used in server mode. If set to `auto`, the container will try to determine and set the external IP automatically |
| `-e SERVERPORT=51820` | External port for docker host. Used in server mode. |
| `-e PEERS=1` | Number of peers to create confs for. Required for server mode. Can be a list of names too: myPC,myPhone,myTablet... |
| `-e PEERDNS=auto` | DNS server set in peer/client configs (can be set as `8.8.8.8`). Used in server mode. Defaults to `auto`, which uses wireguard docker host's DNS via included CoreDNS forward. |
| `-e INTERNAL_SUBNET=10.13.13.0` | Internal subnet for the wireguard and server and peers (only change if it clashes). Used in server mode. |
| `-e ALLOWEDIPS=0.0.0.0/0` | The IPs/Ranges that the peers will be able to reach using the VPN connection. If not specified the default value is: '0.0.0.0/0, ::0/0' This will cause ALL traffic to route through the VPN, if you want split tunneling, set this to only the IPs you would like to use the tunnel AND the ip of the server's WG ip, such as 10.13.13.1. |
| `-v /config` | Contains all relevant configuration files. |
| `-v /lib/modules` | Maps host's modules folder. |
| `--sysctl=` | Required for client mode. |

### Environment variables from files (Docker secrets)

You can set any environment variable from a file by using a special prepend `FILE__`.

As an example:

```bash
-e FILE__PASSWORD=/run/secrets/mysecretpassword
```

Will set the environment variable `PASSWORD` based on the contents of the `/run/secrets/mysecretpassword` file.

### Umask for running applications

There is the ability to override the default umask settings for services started within the containers using the optional `-e UMASK=022` setting.
Keep in mind umask is not chmod it subtracts from permissions based on it's value it does not add. Please read up [here](https://en.wikipedia.org/wiki/Umask) before asking for support.

### User / Group Identifiers

When using volumes (`-v` flags) permissions issues can arise between the host OS and the container, this is avoided by allowing you to specify the user `PUID` and group `PGID`.

Ensure any volume directories on the host are owned by the same user you specify and any permissions issues will vanish like magic.

In this instance `PUID=1000` and `PGID=1000`, to find yours use `id user` as below:

```bash
  $ id username
    uid=1000(dockeruser) gid=1000(dockergroup) groups=1000(dockergroup)
```

---

## Adding Clients
If the environment variable `PEERS` is set to a number or a list of strings separated by comma, the container will run in server mode and the necessary server and peer/client confs will be generated. The peer/client config qr codes will be output in the docker log. They will also be saved in text and png format under `/config/peerX` in case `PEERS` is a variable and an integer or `/config/peer_X` in case a list of names was provided instead of an integer.

Variables `SERVERURL`, `SERVERPORT`, `INTERNAL_SUBNET` and `PEERDNS` are optional variables used for server mode. Any changes to these environment variables will trigger regeneration of server and peer confs. Peer/client confs will be recreated with existing private/public keys. Delete the peer folders for the keys to be recreated along with the confs.

To add more peers/clients later on, you increment the `PEERS` environment variable or add more elements to the list and recreate the container.

To display the QR codes of active peers again, you can use the following command and list the peer numbers as arguments: `docker exec -it wireguard /app/show-peer 1 4 5` or `docker exec -it wireguard /app/show-peer myPC myPhone myTablet` (Keep in mind that the QR codes are also stored as PNGs in the config folder).

The templates used for server and peer confs are saved under `/config/templates`. Advanced users can modify these templates and force conf generation by deleting `/config/wg0.conf` and restarting the container.

*(This portion of documentation has been adapted from [docker-wireguard](https://github.com/linuxserver/docker-wireguard/blob/master/README.md))*

---

## Modifying the upstream DNS provider for Unbound
If you choose to not use Cloudflare any reason you are able to modify the upstream DNS provider in `unbound.conf`.

Search for `forward-zone` and modify the IP addresses for your chosen DNS provider.

>**NOTE:** The anything after `#` is a comment on the line. 
What this means is it is just there to tell you which DNS provider you put there. It is for you to be able to reference later. I recommend updating this if you change your DNS provider from the default values.


```yaml
forward-zone:
        name: "."
        forward-addr: 1.1.1.1@853#cloudflare-dns.com
        forward-addr: 1.0.0.1@853#cloudflare-dns.com
        forward-addr: 2606:4700:4700::1111@853#cloudflare-dns.com
        forward-addr: 2606:4700:4700::1001@853#cloudflare-dns.com
        forward-tls-upstream: yes
```

---

## Available DNS Providers

While you can actually use any upstream provider you want, the team over at pi-hole.net provide a fantastic break down along with all needed information of some of the more popular providers here:
https://docs.pi-hole.net/guides/upstream-dns-providers/

Providers they have the information for:

1. Google
2. OpenDNS
3. Level3
4. Comodo
5. DNS.WATCH
6. Quad9
7. CloudFlare DNS


---

## Setting a DNS record for pihole
1. Login to pihole admin
2. Navigate to "Local Records"
3. Fill out the form like the image below
![Image](https://i.imgur.com/PM1kwcf.png)

Provided your DNS is properly configured on the device you're using, and you're connected to WireGuard, you can now navigate to http://pi.hole/admin and it should take you right to the pihole admin interface.

---

## Shadowsocks
To set a password for Shadowsocks, specify it in the environment:
```
environment:
PASSWORD=$SS_PASSWORD
```
And then set the SS_PASSWORD environment variable with the actual password value.
or you can set a password in the Shadowsocks section:
```
- PASSWORD=Your_password
```
---

## FAQ

### How do you add client configurations?
If the environment variable `PEERS` is set to a number, the container will run in server mode and the necessary server and peer/client confs will be generated. The peer/client config qr codes will be output in the docker log. They will also be saved in text and png format under /config/peerX.

Variables `SERVERURL`, `SERVERPORT`, `INTERNAL_SUBNET` and `PEERDNS` are optional variables used for server mode. Any changes to these environment variables will trigger regeneration of server and peer confs. Peer/client confs will be recreated with existing private/public keys. Delete the peer folders for the keys to be recreated along with the confs.

To add more peers/clients later on, you increment the `PEERS` environment variable and recreate the container.

To display the QR codes of active peers again, you can use the following command and list the peer numbers as arguments: `docker-compose exec wireguard /app/show-peer 1 4 5` will show peers #1 #4 and #5 (Keep in mind that the QR codes are also stored as PNGs in the config folder).

The templates used for server and peer confs are saved under /config/templates. Advanced users can modify these templates and force conf generation by deleting /config/wg0.conf and restarting the container.

### Where can I get additional block lists?
* [The Big Blocklist Collection](https://firebog.net/)

### Commonly whitelisted domains
* [Pi-Hole Community List](https://discourse.pi-hole.net/t/commonly-whitelisted-domains/212)
* [anudeepND Whitelist](https://github.com/anudeepND/whitelist)

### Why do you use Unbound / What benefit is there to using Unbound?
* [PiHole Official Site: What does this guide provide?](https://docs.pi-hole.net/guides/unbound/#what-does-this-guide-provide)
