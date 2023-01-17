---
title: 'Depurar en Bash'
permalink: '/20220903/DepurarBash/'
author: 'LLamasDev'
date: 2022-09-03 8:00:00 +0800
last_modified_at: 2022-09-03 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Bash]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/BashLogo.png){: .align-center}

## ¿Cómo depurar?

`-e`: Garantiza que si falla el script, se cancele el script.  
`-x`: Muestra por pantalla todo lo que se ejecuta.
```bash
#!/bin/bash -ex
```