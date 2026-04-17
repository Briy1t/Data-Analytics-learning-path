# Primer análisis: Dataset 1 — Web Server Access Logs
## 1. Revisión inicial del dataset
Antes de iniciar el análisis, se revisó el archivo en WordPad/VSCode y se observó que:
- ![](imagenes/1.png)
- No es un log crudo del sistema
- Es un archivo generado por un script que intentó resolver hostnames
- Muchos hostnames no se resolvieron
- Aun así, es válido para análisis de tráfico y comportamiento

## 2. Python (panda)
Se uso Python para limpiar el dataset y extraer la información que sera util es decir direcciones ip y hostname 
- ![](imagenes/2.png)
- guardamos el cvs limpio y lo proyecte en Excel
- ![](imagenes/3.png)

## 3. Consultas SQL iniciales
- ![](imagenes/4.png)
Se realizaron consultas para identificar:
- Repetición de IPs
- Hostnames reales vs no resueltos
- Proveedores frecuentes
- Rangos de IP
- Distribución del tráfico

- ![](imagenes/5.png)
- ![](imagenes/6.png)
- ![](imagenes/7.png)
- ![](imagenes/8.png)
- ![](imagenes/9.png)
- ![](imagenes/10.png)
- ![](imagenes/11.png)

## 4. Resultados preliminares
**Hostnames**
  - El 68% de las IP no tienen hostname real ( 1183 hostnames reales )
  - 2526 hostnames iguales a la IP (sin resolución DNS)
--- 
**Proveedores repetidos**
- puregig.net: 31 apariciones
- AS51430: 5
- getmyip.co: 5
- zmap.sorengard.com: 4
---
**Rango dominante**
- El rango 5.x.x.x es el más frecuente
- Este rango pertenece principalmente a proveedores iraníes

## 4. Patrones sospechosos detectados
- IPs asociadas a escaneo masivo `Ejemplo: zmap.sorengard.com`
- ZMap se utiliza para escaneo de puertos, mapeo de servicios y reconocimiento previo a un ataque.
---
- **Nodos TOR**
Ejemplos: `tor-exit.local, tor-exit-node.heteigenwijsje.nl`
- TOR se utiliza para anonimato extremo y ocultación de origen.

- VPS baratos usados frecuentemente en ataques
Ejemplos:`contaboserver.net, m247.com, hostry.com`
- Suelen utilizarse para bots, fuerza bruta, scrapers y escaneo automatizado.

- Hostnames repetidos desde un mismo proveedor
- `unknown.puregig.net`  aparece 31 veces, lo que sugiere un bot persistente o un proceso automatizado.

- IPs sin hostname pero con comportamiento repetitivo - Suelen corresponder a bots mal configurados, malware o dispositivos comprometidos.

- Tráfico masivo desde rangos específicos
- El rango 5.x.x.x domina el dataset.
- Este rango pertenece a proveedores iraníes con alto volumen de tráfico automatizado.

## 5. IPs que generan más tráfico
- Los hostnames más repetidos son:

- unknown.puregig.net  (31)
- swe-net-ip.as51430.net  (5)
- server2us.getmyip.co  (5)
- zmap.sorengard.com  (4)
- host.coloup.com  (4)
- Todos corresponden a servidores, VPS o escáneres, no a usuarios reales.

## 6. Rutas que suelen generar más errores (estimación)
Sin los logs de rutas aún, se documentan las rutas típicamente atacadas:
- /wp-login.php
- /admin
- /phpmyadmin
- /login
- /xmlrpc.php
- /api/*
- /cgi-bin/*
- Estas rutas suelen ser objetivo de fuerza bruta, escaneo de paneles de administración y explotación de scripts vulnerables.

### Resultado preliminar del Dataset 1
El Dataset 1 representa tráfico:
- Automatizado
- Distribuido
- Internacional
- Con fuerte presencia de bots, escáneres y servidores remotos
- Con muy poca actividad atribuible a usuarios reales

## Conclusión Dataset 1

El análisis del Dataset 1 muestra que el tráfico recibido por el servidor no corresponde al comportamiento típico de usuarios reales, sino a un entorno expuesto a Internet donde predominan procesos automatizados, escáneres y bots distribuidos. La revisión inicial del archivo revela que los hostnames fueron generados por un script de resolución DNS, lo que permite identificar patrones de origen, repetición y comportamiento sin necesidad de disponer del log crudo original.

Los resultados indican que más del 68% de las direcciones IP no tienen hostname resoluble, lo que es característico de tráfico automatizado, dispositivos comprometidos o bots mal configurados. Entre los hostnames que sí se resolvieron, destacan proveedores asociados a escaneo masivo, redes de anonimato y VPS de bajo coste, como puregig.net, AS51430, getmyip.co y zmap.sorengard.com. La presencia de ZMap es especialmente relevante, ya que se trata de una herramienta utilizada para reconocimiento a gran escala, lo que confirma actividad de escaneo sistemático.

El rango 5.x.x.x, dominante en el dataset, pertenece a proveedores internacionales con alta actividad automatizada, lo que refuerza la hipótesis de que el tráfico proviene de bots distribuidos globalmente. Asimismo, la repetición de hostnames como unknown.puregig.net sugiere procesos persistentes o nodos que ejecutan tareas de reconocimiento de forma continua.

Aunque el dataset no incluye rutas HTTP completas, se identificaron las rutas típicamente atacadas en este tipo de escenarios (/wp-login.php, /admin, /phpmyadmin, /xmlrpc.php), lo que permite contextualizar el tipo de actividad que probablemente estaba recibiendo el servidor: intentos de fuerza bruta, escaneo de paneles de administración y búsqueda de scripts vulnerables.

En conjunto, el Dataset 1 representa un entorno donde el tráfico es mayoritariamente automatizado, distribuido e internacional, con una presencia significativa de bots, escáneres y servidores remotos. La actividad humana es prácticamente inexistente. Este comportamiento es coherente con lo que experimenta cualquier servidor expuesto a Internet: un flujo constante de reconocimiento, escaneo y tráfico no solicitado que constituye la base del “ruido” habitual de la red.
