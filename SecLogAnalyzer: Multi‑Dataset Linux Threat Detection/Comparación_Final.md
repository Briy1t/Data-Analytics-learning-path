# Comparación Final entre los Datasets 1, 2 y 3
La comparación global de los tres datasets permite entender cómo se comportan distintos sistemas expuestos a Internet y
qué señales permiten diferenciar entre tráfico normal, automatizado y malicioso. Cada dataset aporta una perspectiva distinta del ciclo de actividad y riesgo en infraestructuras modernas.

## 1. Naturaleza del sistema analizado
- **Dataset 1**: Servidor web expuesto a Internet.
- **Dataset 2**: Red IoT con dispositivos conectados.
- **Dataset 3**: Servidor Linux analizado a través de logs de autenticación.


Cada entorno tiene patrones propios, pero todos comparten exposición constante a tráfico automatizado y potencialmente malicioso.

## 2. Actividad normal
- **Dataset 1**: Muy poca actividad humana; casi todo es ruido de Internet.
- **Dataset 2**: Tráfico legítimo claro (MQTT, DNS, HTTP/HTTPS).
- **Dataset 3**: Actividad interna del sistema (cron, login) y accesos legítimos.


**El Dataset 2** es el único donde la actividad normal es dominante y claramente distinguible.

## 3. Actividad automatizada
- **Dataset 1**: Extremadamente alta (bots, escáneres, TOR, VPS).
- **Dataset 2**: Media (flujos IoT automáticos + escaneos).
- **Dataset 3**: Muy alta (fuerza bruta distribuida, diccionarios, procesos repetitivos).


**Dataset 1** y **Dataset 3** son los más afectados por automatización maliciosa.

## 4. Actividad maliciosa
- **Dataset 1**: Escaneos globales, bots persistentes, tráfico internacional no solicitado.
- **Dataset 2**: Ataques etiquetados (SYN Flood, ARP poisoning, NMAP, Slowloris, SSH brute force).
- **Dataset 3**: Fuerza bruta distribuida, escalada de privilegios, uso de protocolos inseguros.


Dataset 2 es el más explícito en ataques; Dataset 3 es el más útil para detección temprana.

## 5. Indicadores clave de ataque
- **Dataset 1**:
  - Hostnames repetidos
  - Rango 5.x.x.x
  - Escáneres (ZMap)
  - Nodos TOR

- **Dataset 2**:
  - attack_type
  - Puertos destino
  - Duración de flujos
  - Técnicas de escaneo

- **Dataset 3**:
  - Intentos fallidos repetitivos
  - Usuarios atacados
  - Servicios críticos (ssh, sudo, su)
  - Protocolos inseguros (TELNET, RDP)


Cada dataset aporta señales distintas que, combinadas, permiten una visión completa del comportamiento malicioso.

## 6. Qué aporta cada dataset al objetivo del estudio
**Dataset 1**  
- Enseña el “ruido” constante de Internet: bots, escaneos, tráfico automatizado.


**Dataset 2** 
- Muestra cómo distinguir tráfico IoT normal de ataques reales y variados.

**Dataset 3**  
- Permite entender cómo se manifiestan ataques en logs de autenticación Linux.

## 7. Conclusión comparativa final
Los tres datasets, analizados en conjunto, muestran que:

- Todo sistema expuesto a Internet recibe tráfico automatizado constante.
- Los ataques pueden ser masivos (Dataset 2), persistentes (Dataset 1) o silenciosos y repetitivos (Dataset 3).
- La actividad normal existe, pero queda oculta entre ruido y tráfico sospechoso.
- El análisis de logs —con limpieza, SQL y visualizaciones— permite diferenciar entre actividad legítima, automatizada y maliciosa.
- Cada dataset aporta una pieza distinta del rompecabezas:
- Reconocimiento externo (Dataset 1)
- Ataques activos (Dataset 2)
- Intentos de acceso y escalada (Dataset 3)

### En conjunto, ofrecen una visión completa del ciclo de ataque:
**reconocimiento → explotación → acceso → persistencia.**
