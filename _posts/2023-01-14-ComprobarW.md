---
title: 'Comprobador de archivos de sistema'
permalink: '/20230114/ComprobarW/'
author: 'LLamasDev'
date: 2023-01-14 8:00:00 +0800
last_modified_at: 2023-01-14 8:00:00 +0800
show_date: true
categories: [Windows]
tags: [PowerShell]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/TuxW.png){: .align-center}

## ¿Cómo hacerlo?

Como `administrador`:  
Al ejecutar este comando, DISM utiliza Windows Update para proporcionar los archivos necesarios para reparar los daños.
```console
DISM.exe /Online /Cleanup-image /Restorehealth
```

Examinará todos los archivos de sistema protegidos y remplaza los archivos dañados con una copia en caché ubicada en una carpeta comprimida en %WinDir%\System32\dllcache.  
El marcador de posición %WinDir% representa la carpeta del sistema operativo Windows. Por ejemplo, C:\Windows.
```console
sfc /scannow
```

## Salidas

- Protección de recursos de Windows no encontró ninguna infracción de integridad.

Esto quiere decir que no hay ningún archivo de sistema que esté dañado o que falte.

- Protección de recursos de Windows no pudo realizar la operación solicitada.

Para resolver este problema, vuelva a ejecutar el examen de Comprobador de archivos de sistema en modo seguro y compruebe que las carpetas PendingDeletes y PendingRenames existen dentro de %WinDir%\WinSxS\Temp.

- Protección de recursos de Windows encontró archivos dañados y los reparó correctamente. Los detalles están incluidos en CBS.Log %WinDir%\Logs\CBS\CBS.log.

Para obtener información detallada sobre el análisis de archivos de sistema y su restauración, diríjase a Cómo ver los detalles del proceso de Comprobador de archivos de sistema.

- Protección de recursos de Windows encontró archivos dañados pero no pudo corregir algunos de ellos. Los detalles están incluidos en CBS.Log %WinDir%\Logs\CBS\CBS.log.

Para reparar los archivos dañados de manera manual, consulta los detalles del proceso de Comprobador de archivos de sistema para encontrar el archivo dañado y luego remplace el archivo dañado con una copia del archivo que sepa que no esté dañada.