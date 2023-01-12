---
title: 'Comprimir'
permalink: '/20220826/Comprimir/'
author: 'LLamasDev'
date: 2022-08-26 8:00:00 +0800
last_modified_at: 2022-08-26 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Comandos]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

## TAR

Comprimir:
```bash
tar -cvf archivo.tar ficheros
```

Descomprimir:
```bash
tar -xvf archivo.tar
```

Para ver el contenido:
```bash
tar -tzf archivo.tar
```

## RAR

Comprimir:
```bash
rar -a archivo.rar ficheros
```

Descomprimir:
```bash
rar -x archivo.rar
```

Para ver el contenido:
```bash
rar -l archivo.rar
rar -v archivo.rar
```

## ZIP

Comprimir:
```bash
zip archivo.zip ficheros
```

Descomprimir:
```bash
unzip archivo.zip
```

Para ver el contenido:
```bash
unzip -v archivo.zip
```

## GZ

Comprimir:
```bash
gzip -9 fichero
```

Descomprimir:
```bash
gzip -d fichero.gz
```

Para buscar el contenido:  
`-c`: Contar cuantos hay.  
`-i`: Ignorar mayúsculas y minúsculas.  
`-n`: Muestra el número de la línea.  
`-v`: Que no contanga.  
`-l`: Nombre del fichero.
```bash
zgrep -ALGO ALGO.gz
```

## TAR.BZ2

Comprimir:
```bash
tar -c ficheros | bzip2 > archivo.tar.bz2
```

Descomprimir:
```bash
bzip2 -dc archivo.tar.bz2 | tar -xv
```

Para ver el contenido:
```bash
bzip2 -dc archivo.tar.bz2 | tar -t
```

## BZ2

Comprimir:
```bash
bzip fichero
```

Descomprimir:
```bash
bzip2 -d fichero.bz2
```