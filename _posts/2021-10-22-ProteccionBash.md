---
title: 'Caracteres de protección en Bash'
permalink: '/20211022/ProteccionEnBash/'
author: 'LLamasDev'
date: 2021-10-22 8:00:00 +0800
last_modified_at: 2021-10-22 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Bash]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}/assets/img/BashLogo.png){: .align-center}

## Comillas dobles "

La protección es simple, eliminan el significado de todos los caracteres especiales del shell excepto `$`, `$()`, `\\` y a sí mismas.
```bash
echo "Hola, estoy en $(pwd)"
Hola, estoy en /
```

## Comillas simples '

Las comillas simples eliminan el significado a todos los caracteres especiales del shell.
```bash
echo 'Hola, estoy en $(pwd)'
Hola, estoy en $(pwd)
```

## El carácter \

La contrabarra elimina el significado especial del carácter que le sigue.
```bash
echo "Hola, estoy en $(pwd)"
Hola, estoy en /

echo "Hola, estoy en \$(pwd)"
Hola, estoy en $(pwd)


echo '$HOME \$HOME \\\\'
$HOME \$HOME \\\\

echo "$HOME \$HOME \\\\"
/root $HOME \\
```