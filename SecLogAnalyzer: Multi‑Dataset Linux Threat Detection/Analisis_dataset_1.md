# Primer análisis: Dataset 1 — Web Server Access Logs
## 1. Revisión inicial del dataset
Antes de iniciar el análisis, se revisó el archivo en WordPad/VSCode y se observó que:
- 1
- No es un log crudo del sistema
- Es un archivo generado por un script que intentó resolver hostnames
- Muchos hostnames no se resolvieron
- Aun así, es válido para análisis de tráfico y comportamiento

## 2. Python (panda)
Se uso Python para limpiar el dataset y extraer la información que sera util es decir direcciones ip y hostname 
- 2
- guardamos el cvs limpio y lo proyecte en Excel
- 3 

## 3. Consultas SQL iniciales
- 4
Se realizaron consultas para identificar:
- Repetición de IPs
- Hostnames reales vs no resueltos
- Proveedores frecuentes
- Rangos de IP
- Distribución del tráfico

- 5 6 7 8 9 10 11 

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

- IPs sin hostname pero con comportamiento repetitivo ➡️Suelen corresponder a bots mal configurados, malware o dispositivos comprometidos.

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

en procesos--- 

