---
title: 'phpMyAdmin'
permalink: '/20220409/phpMyAdmin/'
author: 'LLamasDev'
date: 2022-04-09 8:00:00 +0800
last_modified_at: 2022-04-09 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [SQL]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/SQL.png){: .align-center}

## Instalar

`php-mbstring`: Módulo para administrar cadenas no-ASCII y convertir cadenas a diferentes codificaciones.  
`php-zip`: Esta extensión admite la carga de archivos .zip a phpMyAdmin.  
`php-gd`: Habilita la obtención de ayuda de la biblioteca GD Graphics.  
`php-json`: Proporciona PHP con compatibilidad para serialización JSON.  
`php-curl`: Permite que PHP interactúe con diferentes tipos de servidores utilizando diferentes protocolos.
```bash
sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
```

Después ejecutaremos:
```bash
phpenmod mbstring

systemctl restart apache2
```

## Problemas con phpMyAdmin

Si la web no carga, veamos si no esta añadida en `apache`:
```bash
vi /etc/apache2/apache2.conf

Include /etc/phpmyadmin/apache.conf

/etc/init.d/apache2 restart
```

## Servicios o Demonios

[Servicios o Demonios]({{ site.url }}{{ site.baseurl }}./20220805/Servicios/)