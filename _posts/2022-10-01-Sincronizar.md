---
title: 'Rsync'
permalink: '/20221001/Rsync/'
author: 'LLamasDev'
date: 2022-10-01 8:00:00 +0800
last_modified_at: 2022-10-01 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Comandos]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

## Sincronizar archivos o carpetas

`-a`: copia los archivos y directorios recursivamente, preserva enlaces, permisos de archivos, usuario y grupo del archivo, y estampas de tiempo.  
`-v`: Información extra de los archivos copiados.  
`-z`: Comprime la información antes de enviarla.  
`-h`: Información de los datos de la transferencia en modo legible para los humanos.  
`-P`: para que nos muestre el progreso de la copia.
```bash
rsync -a -P ORIGEN DESTINO
```