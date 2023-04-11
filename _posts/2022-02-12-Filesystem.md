---
title: 'Filesystem'
permalink: '/20220212/Filesystem/'
author: 'LLamasDev'
date: 2022-02-12 8:00:00 +0800
last_modified_at: 2022-02-12 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Comandos]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

## Mostrar tamaño del FS

`-k`: Emplea unidades de 1024 bytes (1 kB) en lugar de las predeterminadas de 512 bytes.
```bash
df -k RUTA
```

`-h`: Añade una letra indicativa de tamaño, como M para megabytes binarios (mebibytes), a cada tamaño.
```bash
df -h RUTA
```

## Mostrar tamaño de un archivo en GB

```bash
ls -lrt --block-size=GB
```

## Mostrar tamaño de una carpeta

```bash
du -sh CARPETA
```

## Ordenar por tamaño

Mostrar el tamaño de los archivos que más ocupen y ordenados:  
`-h / --human-readable`: Imprime los datos como: 1K ó 234M ó 2G.  
`-s`: No muestra los subdirectorios.
```bash
du -hs * | sort -n
```

`-k / --block-size=1K`:
```bash
du -ks * | sort -n
```

## Borrar

Para buscar un archivo y borrar los de más de una semana:  
`-type f`: Fichero.  
`-type d`: Carpeta.  
`-iname`: Buscar algo y no distingue mayúsculas de minúsculas.  
`-mtime`: Tiempo a buscar o desde cuando.  
`-exec`: Ejecutar lo siguiente.
```bash
find RUTA(si no se pone, es la actual) -type f -iname 'ALGO*' -mtime +X -exec ls -lrt {} \;

find RUTA(si no se pone, es la actual) -type f -iname 'ALGO*' -mtime +X -exec rm -fv {} \;
```

## Vaciar

Vaciar un archivo:
```bash
> ALGO
```

## Comprimir

Comprimir sin estar pintando:
```bash
gzip -9f ALGO
```

Comprimir en caliente (pintando ahora mismo):
```bash
gzip -c ALGO >> ALGO.gz && > ALGO
```