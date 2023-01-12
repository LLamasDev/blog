---
title: 'Activación de Windows 10'
permalink: '/20220916/ActivacionW/'
author: 'LLamasDev'
date: 2022-09-16 8:00:00 +0800
last_modified_at: 2022-09-16 8:00:00 +0800
show_date: true
categories: [Windows]
tags: [Activacion]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/TuxW.png){: .align-center}

## ¿Cómo se hace?

Como administrador y si kms.digiboy.ir no funciona, otra opción es kms.msguides.com:
```console
slmgr /ipk XXXX-XXXX-XXXX-XXXX-XXXX
slmgr /skms kms.digiboy.ir
slmgr /ato
```

## Ejemplo

```console
slmgr /ipk TX9XD-98N7V-6WMQ6-BX7FG-H8Q99
slmgr /skms kms.digiboy.ir
slmgr /ato
```

- [x] Windows activado :)

## Otro método

```console
bcdedit -set TESTSIGNING OFF
```