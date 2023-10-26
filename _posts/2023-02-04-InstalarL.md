---
title: 'Instalación para Unix'
permalink: '/20230204/InstalarU/'
author: 'LLamasDev'
date: 2023-02-04 8:00:00 +0800
last_modified_at: 2023-02-04 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Comandos]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/GNULinux.png){: .align-center}

## Instalar localmente

```bash
tar -zxvf mysql-connector-python_8.0.15.orig.tar.gz

cd mysql-connector-python-8.0.15/

python3 setup.py install
```