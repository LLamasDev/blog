---
title: 'Actualizar'
permalink: '/20220611/Actualizar/'
author: 'LLamasDev'
date: 2022-06-11 8:00:00 +0800
last_modified_at: 2022-06-11 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Comandos]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

## Actualizar en GNU/Linux

Actualiza la lista de paquetes disponibles y sus versiones, pero no instala o actualiza ningún paquete. Esta lista la coge de los servidores con repositorios que tenemos definidos en el `sources.list`.
```bash
apt-get update
```

Una vez el comando anterior ha descargado la lista de software disponible y la versión en la que se encuentra, podemos actualizar dichos paquetes usando este comando. Instalará las nuevas versiones respetando la configuración del software cuando sea posible.
```bash
apt-get upgrade
```

## Podemos usar ambos a la vez

```bash
apt-get update && apt-get upgrade
```

## Error

[Wiki Debian](https://wiki.debian.org/SourcesList)  
Modificar el `sources.list`:
```bash
/etc/apt/sources.list
```

Ejemplo Debian:
```bash
# Repositorios oficiales de Debian en español
deb http://ftp.es.debian.org/debian/ buster main contrib non-free
deb-src http://ftp.es.debian.org/debian/ buster main contrib non-free

deb http://ftp.es.debian.org/debian/ buster-updates main contrib non-free
deb-src http://ftp.es.debian.org/debian/ buster-updates main contrib non-free

deb http://security.debian.org/debian-security/ buster/updates main contrib non-free
deb-src http://security.debian.org/debian-security/ buster/updates main contrib non-free


# Repositorios oficiales de Debian
deb http://deb.debian.org/debian/ buster main
deb-src http://deb.debian.org/debian/ buster main

deb http://deb.debian.org/debian-security/ buster/updates main
deb-src http://deb.debian.org/debian-security/ buster/updates main

deb http://deb.debian.org/debian/ buster-updates main
deb-src http://deb.debian.org/debian/ buster-updates main


#MySQL
# Repositorio oficial de MySQL APT para Debian
deb http://repo.mysql.com/apt/debian/ buster mysql-8.0

# También puedes habilitar el repositorio de actualizaciones de MySQL
deb http://repo.mysql.com/apt/debian/ buster mysql-tools

# Para activar el soporte de origen (fuentes) de MySQL, descomenta la siguiente línea
deb-src http://repo.mysql.com/apt/debian/ buster mysql-8.0
```

Ejemplo Ubuntu:
```bash
deb http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu focal partner
deb-src http://archive.canonical.com/ubuntu focal partner
```

Una vez modificado `sources.list`:
```bash
apt update
```


Otro posible error es si te da lo siguiente:
```text
W: GPG error: http://repo.mysql.com/apt/debian buster InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 467B942D3A79BD29
```

Solución:
```bash
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 467B942D3A79BD29

apt update
```

En caso de que no encuentres el paquete haz la [instalación localmente]({{ site.url }}{{ site.baseurl }}./20230204/InstalarL/)