---
title: 'Servicios o demonios'
permalink: '/20220806/Servicios/'
author: 'LLamasDev'
date: 2022-08-06 8:00:00 +0800
last_modified_at: 2022-08-06 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Comandos]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

# Ver el estado actual

```bash
service --status-all
```

# Servicios

## Estado

```bash
service ALGO status
```

## Arrancar

```bash
service ALGO start
```

## Parar

```bash
service ALGO stop
```

# Rutas

## Estado

```bash
/etc/init.d/ALGO status
```

## Arrancar

```bash
/etc/init.d/ALGO start
```

## Parar

```bash
/etc/init.d/ALGO stop
```