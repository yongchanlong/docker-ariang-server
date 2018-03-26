Aria2 + AriaNg

- [Features](#features)
- [How to run](#how-to-run)
  - [Simple Usage](#simple-usage)
  - [Full Usage](#full-usage)
  - [Other Usage](#other-usage)
  - [Supported Environment Variables](#supported-environment-variables)
  - [Supported Volumes](#supported-volumes)

## Features
  * Aria2 (SSL support)
  * AriaNg
  * Auto HTTPS （Let's Encrypt）
  * Basic Auth

## How to run

### Simple Usage

```shell
  docker run -d --name ariang -p 80:80 -p 6800:6800 andrewai/docker-ariang-server
```

* Aria2: <http://yourip>

### Full Usage
```shell
  docker run -d --name ariang -p 80:80 -p 6800:6800 -p 443:443 \
  -e ENABLE_AUTH=true -e RPC_SECRET=Hello -e DOMAIN=example.com \
  -e ARIA2_USER=user -e ARIA2_PWD=pwd \
  -v /yourdata:/data \
  -v /yoursslkeys/:/root/conf/key andrewai/docker-ariang-server
```
### Other Usage
```
  docker run -d -it --name ariang -p 80:80 -p 6800:6800 -p 443:443 \
  -e ENABLE_AUTH=true -e RPC_SECRET=Hello \
  -e ARIA2_USER=user \
  -e ARIA2_PWD=pwd \
  -v ~/data:/data \
  -v ~/sslkeys/:/root/conf/key \
  andrewai/docker-ariang-server
```

### Supported Environment Variables

  * ENABLE_AUTH enable Basic auth
  * ARIA2_USER Basic Auth username
  * ARIA2_PWD Basic Auth
  * RPC_SECRET The Aria2 RPC secret token
  * DOMAIN The domain you'd like to bind


### Supported Volumes
  * `/data` The folder of all Aria2 downloaded files.
  * `/root/conf/key` The folder which stored Aria2 SSL `certificate` and `key` file. `Notice`: The certificate file should be named `aria2.crt` and the key file should be named `aria2.key`
