---
title: 'OpenShift'
permalink: '/20220507/OpenShift/'
author: 'LLamasDev'
date: 2022-05-07 8:00:00 +0800
last_modified_at: 2022-05-07 8:00:00 +0800
show_date: true
categories: [GNU/Linux]
tags: [OpenShift]
math: true
mermaid: true
toc: true
---

![image-center]({{ site.url }}{{ site.baseurl }}./assets/img/OpenShift.png){: .align-center}

## Cambiar de proyecto

```bash
oc project ALGO
```

## Nodos

```bash
oc get nodes
```

## Pods

Listado simple:
```bash
oc get pods
```

Listado completo de todos y con los ocultos:
```bash
oc get pods --all-namespaces -o wide
```

## Events

```bash
oc get events
```

Ordenar por fecha los eventos activos:
```bash
oc get events --sort-by='{.lastTimestamp}'
```

Para ver si se ha reiniciado un nodo en OCP:
```bash
who -b -r

oc get event --all-namespaces | grep -i notready | grep -v 'pod'
```