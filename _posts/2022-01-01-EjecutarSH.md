---
title: 'Script'
permalink: '/20220101/Script/'
author: 'LLamasDev'
date: 2022-01-01 8:00:00 +0800
last_modified_at: 2022-01-01 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Bash]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/BashLogo.png){: .align-center}

## Problemas al ejecutar un script

Convierte los saltos de línea de formato DOS a UNIX.  
`sed`: Es un potente editor de flujo de texto. Podemos hacer insertar, borrar, buscar y reemplazar.  
`-i`: Para editar archivos en el lugar en lugar de mostrar el resultado.  
`-e`: Usa los comandos de edición pasados al sed.
```bash
sed -ie 's/\r$//' NOMBRESCRIPT.sh
```

Si no funciona podemos usar:
```bash
apt-get install dos2unix

dos2unix NOMBRESCRIPT.sh
```