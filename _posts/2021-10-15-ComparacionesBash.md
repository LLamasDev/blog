---
title: Comparaciones en Bash
author: LLamasDev
date: 2021-10-15 12:00:00 +0800
categories: [GNU/Linux, Bash]
tags: [Bash]
math: true
mermaid: true
toc: true
---

![](./../assets/img/BashLogo.png)
![image-center]({{ site.url }}{{ site.baseurl }}/assets/img/BashLogo.png){: .align-center}

En bash hay diferentes comparadores según lo que queramos comparar:

## Comparación de enteros

```bash
#!/bin/bash

if [ "$a" -eq "$b" ]; then
  echo "\$a es IGUAL que \$b"
fi

if [ "$a" -ne "$b" ]; then
  echo "\$a NO ES IGUAL que \$b"
fi

if [ "$a" -gt "$b" ]; then
  echo "\$a es MAYOR que \$b"
fi

if [ "$a" -lt "$b" ]; then
  echo "\$a es MENOR que \$b"
fi

if [ "$a" -ge "$b" ]; then
  echo "\$a es MAYOR O IGUAL que \$b"
fi

if [ "$a" -le "$b" ]; then
  echo "\$a es MENOR O IGUAL que \$b"
fi
```

## Comparación de textos

```bash
#!/bin/bash

if [ "$a" = "$b" ]; then
  echo "\$a es IGUAL que \$b"
fi

if [ "$a" == "$b" ]; then
  echo "\$a es IGUAL que \$b"
fi

if [ "$a" != "$b" ]; then
  echo "\$a NO ES IGUAL que \$b"
fi

if [ "$a" \> "$b" ]; then
  echo "\$a es MAYOR que \$b"
fi

if [ "$a" \< "$b" ]; then
  echo "\$a es MENOR que \$b"
fi

if [ -z "$a" ]; then
  echo "\$a ES NULO"
fi

if [ -n "$a" ]; then
  echo "\$a NO ES NULO"
fi
```

## Comparaciones sobre Ficheros

```bash
#!/bin/bash
$fichero="~/pruebas.txt"

if [ -e "$fichero" ]; then
  echo "\$fichero EXISTE"
fi

if [ -f "$fichero" ]; then
  echo "\$fichero es un fichero REGULAR"
fi

if [ -s "$fichero" ]; then
  echo "\$fichero NO TIENE TAMAÑO CERO"
fi

if [ -d "$fichero" ]; then
  echo "\$fichero es un DIRECTORIO"
fi

if [ -b "$fichero" ]; then
  echo "\$fichero es un DISPOSITIVO DE BLOQUES"
fi
```