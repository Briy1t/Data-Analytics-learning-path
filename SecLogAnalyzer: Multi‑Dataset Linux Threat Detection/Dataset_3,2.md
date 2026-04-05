# DATASET 3.2
linux_auth_logs_labeled (dataset etiquetado con anomalías)

## 1. Estructura del dataset
El archivo contiene registros de autenticación en servidores Linux, con información detallada sobre:
- timestamp
- source_ip
- server
- username
- service
- attempts
- status
- port
- protocol
- comment
- anomaly_label

---
Antes del análisis, el dataset fue limpiado y normalizado en Python, y posteriormente importado en DBeaver como:
- ![](imagenes/i15.png)
- ![](imagenes/i16.png)
---
linux_auth_logs_labeled_clean
- ![](imagenes/i17.png)

## 2. Consultas SQL utilizadas

### 2.1 Conteo de anomalías por tipo
```sql
SELECT anomaly_label, COUNT(*) AS total
FROM linux_auth_logs_labeled
GROUP BY anomaly_label
ORDER BY total DESC;
```
- ![](imagenes/i18.png)

#### 3.1 Anomalías detectadas
- **Normal**: La mayoría de eventos son benignos, lo cual es esperable en logs de autenticación.
- **Brute force**: Intentos repetidos de acceso fallido, típicos de ataques automatizados contra SSH.
- **Privilege escalation**: Uso de sudo o su para intentar elevar privilegios. Es un indicador crítico de actividad maliciosa.
- **Geo anomaly**: Accesos desde ubicaciones inesperadas o inconsistentes con el patrón habitual del servidor.
- **Port scan**:Escaneos de puertos desde múltiples IPs, característicos de bots que buscan servicios vulnerables.
### 2.2 Usuarios con más intentos fallidos
```sql
SELECT username, COUNT(*) AS failed_attempts
FROM linux_auth_logs_labeled_clean
WHERE status = 'Failed'
GROUP BY username
ORDER BY failed_attempts DESC
LIMIT 10;
```
- ![](imagenes/i19.png)
#### Analisis
- **root**: siempre es el usuario más atacado.
- **ubuntu**: usuario por defecto en servidores cloud.
- **www-data y nginx**: usuarios de servicios web; no deberían tener intentos de login manual.
- **admin**: usuario administrativo típico.
- **ec2-user**: usuario de AWS; si aparece en servidores no cloud, es sospechoso.
- **jsmith, rsmith, lsmith, csmith**: parecen usuarios generados automáticamente o usados para pruebas.
  
### 2.3 IPs con más actividad
```sql
SELECT source_ip, COUNT(*) AS total_events
FROM linux_auth_logs_labeled_clean
GROUP BY source_ip
ORDER BY total_events DESC
LIMIT 10;
```
- ![](imagenes/i20.png)

#### IPs con más actividad
- Todas las IPs tienen solo 2 eventos.
- No hay una IP dominante
- No hay un atacante único
- El patrón es consistente con ataques distribuidos o datos balanceados

### 2.4 Protocolos más usados
```sql
SELECT protocol, COUNT(*) AS total_events
FROM linux_auth_logs_labeled_clean
GROUP BY protocol
ORDER BY total_events DESC;
```
- ![](imagenes/i21.png)
#### Protocolos más usados
- **SSH2**: normal en Linux.
- **RDP**: muy inusual en Linux; indica entorno simulado o honeypot.
- **TELNET**: inseguro y obsoleto; su presencia indica mala configuración o entorno de pruebas.
- **nan**: valores faltantes.

### 2.5 Servicios más usados
```sql
SELECT service, COUNT(*) AS total_events
FROM linux_auth_logs_labeled_clean
GROUP BY service
ORDER BY total_events DESC;
```
- ![](imagenes/i22.png)
#### Servicios más usados
- **sudo / su**: intentos de escalada de privilegios.
- **ssh**: accesos remotos, vector principal de fuerza bruta.
- **login**: accesos locales o internos.
- **cron**: tareas automáticas del sistema.

### 2.6 Servidores con más actividad
```sql
SELECT server, COUNT(*) AS total_events
FROM linux_auth_logs_labeled_clean
GROUP BY server
ORDER BY total_events DESC;
```
- ![](imagenes/i23.png)
#### Servidores con más actividad
- **proxy**: expuesto a internet
- **monitor**: servidor de monitoreo
- **backup**: objetivo crítico
- **vpn**: acceso remoto
- **web**: servidor web
- **db**: base de datos
- **srv-nyc / tok / ldn**: infraestructura global
- 
### 2.7 Actividad por hora
```sql
SELECT strftime('%H', timestamp) AS hour, COUNT(*) AS total_events
FROM linux_auth_logs_labeled_clean
GROUP BY hour
ORDER BY hour;
```
- ![](imagenes/i24.png)
#### Actividad por hora
- Actividad constante
- Ataques automatizados
- Dataset sintético o honeypot
- 
### 2.8 Privilege escalation
```sql
SELECT *
FROM linux_auth_logs_labeled_clean
WHERE anomaly_label = 'privilege_escalation';
```
- ![](imagenes/i25.png)
### 2.9 Port scan
```sql
SELECT *
FROM linux_auth_logs_labeled_clean
WHERE anomaly_label = 'port_scan';
```
-![](imagenes/i26.png)

### 2.10 Geo anomaly
```sql
SELECT *
FROM linux_auth_logs_labeled_clean
WHERE anomaly_label = 'geo_anomaly';
```
- ![](imagenes/i27.png)
## Graficos
1. Tipos de anomalías 
- ![](imagenes/i28.png)
2. Actividad por hora
- ![](imagenes/i29.png)
3. Usuarios con más intentos fallidos 
- ![](imagenes/i30.png)
## 4. Conclusiones 
### Privilege Escalation  
Se observan múltiples ejecuciones de sudo desde usuarios de servicio, lo cual es anómalo y sugiere actividad simulada o automatizada.

### Port Scan  
Los registros muestran escaneos distribuidos desde múltiples IPs, típicos de bots que buscan vulnerabilidades.

### Geo Anomaly  
Los accesos provienen de ubicaciones inesperadas, lo que indica actividad sospechosa o un entorno de pruebas.

### Síntesis general  
El dataset combina actividad normal con anomalías simuladas. Los patrones son consistentes con un honeypot o laboratorio de detección de intrusiones. El análisis demuestra dominio en:
- manejo de datos estructurados
- consultas SQL
- análisis descriptivo
- interpretación contextual
