---
title: 'Reinicio de Spazio y GBI'
permalink: '/20220521/SpazioGBI/'
author: 'LLamasDev'
date: 2022-05-21 8:00:00 +0800
last_modified_at: 2022-05-21 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Spazio, GBI]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

## Reinicio controlado de Spazio y GBI

Parar GBI:
```bash
/spazio/GBI/GhibliBIServer/ServerKernel/stop.sh
```

Parar Spazio:  
`sp_shut`: Es una parada no forzada.  
`sp_stop`: Es una parada forzada.
```bash
sp_shut

sp_stop
```

Verificar la parada de Spazio:
```bash
checksp -v
```

Arrancar Spazio:
```bash
sp_start
```

Arrancar GBI:
```bash
/spazio/GBI/GhibliBIServer/ServerKernel/startup.sh
```