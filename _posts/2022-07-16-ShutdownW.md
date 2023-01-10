---
title: 'Shutdown para Windows'
permalink: '/20220716/ShutdownW/'
author: 'LLamasDev'
date: 2022-07-16 8:00:00 +0800
last_modified_at: 2022-07-16 8:00:00 +0800
show_date: true
categories: [Windows]
tags: [PowerShell]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/TuxW.png){: .align-center}

## Parámetros

`-i`: Muestra la interfaz gráfica.  
`-l`: Cerrar sesión (No puede se utilizado con la opción -m).  
`-s`: Apaga el ordenador.  
`-r`: Reinicia el ordenador.  
`-a`: Cancela la tarea apagar o reiniciar.  
`-m \computername`: Apaga / Reinicia / Cancela Apagado Remoto del ordenador.  
`-t xx`: Establece el tiempo de apagado a xx segundos.  
`-c comment`: Muestra comentarios en el cuadro de dialogo (máximo 127 caracteres).  
`-f`: Cierra a la fuerza las aplicaciones sin previo aviso.

## Apagar

Para apagar en menos de un minuto.
```console
shutdown -s
```

## Reiniciar

```console
shutdown -r
```

## Programar apagado

`XXX`: En segundo.
```console
shutdown -s -t XXX
```