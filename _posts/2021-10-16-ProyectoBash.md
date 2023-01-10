---
title: 'Arrancar, parar y ver estado de procesos en GNU/Linux'
permalink: '/20211016/ProcesosLinux/'
author: 'LLamasDev'
date: 2021-10-16 8:00:00 +0800
last_modified_at: 2021-10-16 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [Bash]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/BashLogo.png){: .align-center}

## Posibles errores al ejecutar el script

Convierte los saltos de línea de formato DOS a UNIX.  
`sed` es un potente editor de flujo de texto. Podemos hacer insertar, borrar, buscar y reemplazar.  
`-i` para editar archivos en el lugar en lugar de mostar el resultado.  
`-e` usa los comandos de edición pasados al sed.
```bash
sed -ie 's/\r$//' ALGO.sh
```

## Ver si esta corriendo el proceso

```bash
#!/bin/bash

primer_ag=$1 # Primer argumento

function funcion() {
  { # try
    proceso=$(ps -ef | grep -i $primer_ag.py | grep -iv "screen\|grep\|networkd" | wc -l)

    if [ $proceso -eq 1 ]; then # Si el contador del proceso es 1 significa que esta corriendo
      echo 'El proceso esta corriendo'
    else # El proceso no es 1 significa que no esta corriendo, ya que solo puede estar arrancado una vez
      echo 'El proceso no esta corriendo'
    fi
  } || { # catch
    echo 'El proceso esta en estado anomalo'
  }
}

funcion
```

Para tomar el primer argumento que se le pase al script usamos:
```bash
primer_ag=$1
```

Para ver si el proceso está corriendo:
```bash
ps -ef | grep -i $primer_ag.py | grep -iv "screen\|grep\|networkd" | wc -l
```

Con el `ps` vemos los procesos corriendo:
```bash
ps -ef
```

Con el `grep` filtramos por la palabra pasada, lo que buscamos es un archivo Python que se está ejecutando por lo que añadimos .py:  
`-i` no hace caso de si las letras son mayúsculas o minúsculas ni en el patrón ni en los ficheros de entrada.
```bash
grep -i $primer_ag.py
```

La idea es contar cuantos hay y si hacemos un grep aparecerán en el `ps`, ejemplo:
```bash
ps -ef | grep -i python
grep --color=auto -i python
```

Por lo cual en el filtro mostraremos todo menos lo que queremos, en nuestro caso no queremos ver nada de ventanas (`screen`) ni el `grep` y lo añadimos separándolos con `\\|`, también se puede usar `|`, pero si se añade `-E` al `grep`:  
`-v` filtra por todo menos por lo indicado a continuación.  
`-i` no hace caso de si las letras son mayúsculas o minúsculas ni en el patrón ni en los ficheros de entrada.
```bash
grep -iv "screen\|grep\|networkd"
```

Y para contarlos usaremos `wc`:  
`-l` cuenta cuantas líneas aparecerán.
```bash
wc -l
```

Y con el `if` comparo que sea igual que 1, lo cual significa que el proceso estaría corriendo, y si no es 1 no está corriendo, ya que solo puede estar corriendo o no, [todo esto lo explico aquí](https://llamasdev.github.io/Blog/posts/Bash-comparaciones/).

## Arrancar proceso

```bash
#!/bin/bash

primer_ag=$1 # Primer argumento

function funcion() {
  { # try
    proceso=$(ps -ef | grep -i $primer_ag.py | grep -iv "screen\|grep\|networkd" | wc -l)

    if [ $proceso -eq 1 ]; then # Si el contador del proceso es 1 significa que esta corriendo
      echo 'Proceso ya estaba arrancado, saliendo del arranque'
    else # El proceso no es 1 significa que no esta corriendo, ya que solo puede estar arrancado una vez
      ruta=$(find /bot/ -type f -iname "$primer_ag*" 2>/dev/null) # Saco la ruta del archivo que siempre estan en bot
      screen_proceso=$(screen -S $primer_ag -d -m bash -c "python3 $ruta") # Ejecuto el archivo Python en una screen

      echo 'Proceso arrancado'
    fi
  } || { # catch
    echo 'Error al arrancar el proceso'
  }
}

funcion
```

En este caso vemos que esté arrancado, si lo está no hacemos nada, si no está arrancado lo tenemos que arrancar, primero buscamos la ruta donde está, en nuestro caso:
```bash
find /bot/ -type f -iname "$primer_ag*" 2>/dev/null
```

Usaremos `find` y lo tenemos alojado en la ruta `/bot/`.  
`-type f` para buscar solo ficheros y no directorios por si tienen el mismo nombre.  
`-iname "$primer_ag\*"` buscamos con el nombre del primer argumento pasado y el `\`* para indicar que detrás puede tener cualquier cosa.  
`2>/dev/null` esto redirecciona la salida estándar de errores (stderr), al dispositivo nulo (/dev/null).  

Con esto ya tendríamos la ruta del archivo deseado, ya solo falta arrancadlo con `screen` por si luego queremos volver a esa ventana:
```bash
screen -S $primer_ag -d -m bash -c "python3 $ruta"
```

`screen -S $primer_ag` Creamos la ventana con el nombre del argumento dado.  
`-d -m bash -c "python3 $ruta"` Despues de la ventana ejecutamos en Python 3 el archivo deseado obtenido en la ruta.  

## Parar proceso

```bash
#!/bin/bash

primer_ag=$1 # Primer argumento

function funcion() {
  { # try
    proceso=$(ps -ef | grep -i $primer_ag.py | grep -iv "screen\|grep\|networkd" | wc -l)

    if [ $proceso -eq 1 ]; then # Si el contador del proceso es 1 significa que esta corriendo
      pid=$(ps -ef | grep -i $primer_ag.py | grep -iv "screen\|grep\|networkd" | awk '{print $2}') # Saco el pid del proceso
      matar_pid=$(kill -9 $pid) # Mato el pid
      screen_id=$(screen -ls | grep -i $primer_ag | cut -d'.' -f1) # Saco el id del screen
      matar_screen=$(screen -XS $screen_id quit) # Mato el screen del proceso

      echo 'Proceso matado'
    else # El proceso no es 1 significa que no esta corriendo, ya que solo puede estar arrancado una vez
      echo 'El proceso no esta corriendo, saliendo de la parada'
    fi
  } || { # catch
    echo 'Error al matar el proceso'
  }
}

funcion
```

Miramos que esté arrancado, si lo está tenemos que sacar el `PID` del proceso:
```bash
ps -ef | grep -i $primer_ag.py | grep -iv "screen\|grep\|networkd" | awk '{print $2}'
```

Lo nuevo en este caso sería:  
`awk '{print $2}'` con lo que sacamos la segunda columna que es el PID.

Ahora tenemos que matar el proceso:
```bash
kill -9 $pid
```

Ahora sacamos el `ID` del `screen`:
```bash
screen -ls | grep -i $primer_ag | cut -d'.' -f1
```

Lo nuevo sería:  
`cut -d'.' -f1` sacar el ID que sale en pantalla `ID.NOMBRE` por lo cual separamos el ID por el punto tomando el primer campo.

Ya solo queda cerrar el `screen` de la siguiente manera:
```bash
screen -XS $screen_id quit
```

## ¿Posibles mejoras?

Controlar si el fichero no existe, pero siempre indicaremos los ficheros sabiendo que ya existen.  
Si quieres controlar que algo siempre esté arrancado y controlar por si se reinicia el servidor (ya que lo tenemos todo localmente y no por VPS), lo haríamos de la siguiente forma:  
En el crontab ponemos el arranque en el reinicio, en caso de bash:
```bash
@reboot         llamas  /bin/bash /bot/admin/start.sh ALGO
```

En caso de Python:
```bash
@reboot         llamas  /usr/bin/python3 /bot/ALGO.py
```