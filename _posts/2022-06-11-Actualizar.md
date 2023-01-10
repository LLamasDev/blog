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