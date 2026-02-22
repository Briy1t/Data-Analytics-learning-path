# Modulo 1 

**Objetivo**: 
- Dominar los fundamentos básicos de Excel: navegación por la interfaz, entrada de datos y organización de hojas de cálculo.
- Comprender y aplicar funciones comunes para cálculos simples y funciones más avanzadas.
- Adquirir habilidades para trabajar con tablas dinámicas mediante ejemplos prácticos y casos reales del entorno empresarial.

**Nota:** Los objetivos de aprendizaje de este módulo están adaptados del curso de 
Excel del Programa Santander. He redactado esta versión para uso personal y documentación
dentro de mi repositorio.

**Tablas de datos: Excel vs LibreOffice Calc**
He querido realizar los ejercicios en diferentes medios como Excel web y LibreOffice en lugar de Excel
para analizar las facilidades que tiene tener una licencia de office y sus beneficios.

---
Las **tablas de datos** aparecieron en Excel a partir de la `versión 2007` y se convirtieron en una herramienta muy útil para manejar listas grandes.
Permiten mantener cálculos y operaciones actualizados sin necesidad de modificar manualmente el tamaño del rango cada vez que añadimos filas o columnas.

- En `LibreOffice Calc`, como no existe el concepto de “tabla inteligente”, el equivalente es definir un Rango de datos.
Diferencia entre un rango y una tabla.

## ¿Qué es un rango?
Un rango es simplemente un conjunto de celdas normales.
No tiene inteligencia, no se actualiza solo y no tiene herramientas especiales.

---
**Características del rango:**
- Son celdas “normales”.
- No se expanden automáticamente.
- No tienen filtros automáticos.
- No tienen estilos automáticos.
- No tienen fila de totales dinámica.
- Si agregas datos debajo, Excel no lo reconoce como parte del conjunto.
- En Calc, todo funciona como rangos (aunque existe tabla dinamica).
  
---
**Ejemplo:**
A1:D20 es un rango. Nada más.

--- 

## ¿Qué es una tabla?
Una tabla es un rango “convertido” en un objeto inteligente.
Excel la reconoce como un conjunto de datos estructurados.

---

**Características de la tabla:**
- Tiene estilo automático (colores, bordes, formato).
- Agrega filtros automáticamente en los encabezados.
- Se expande sola cuando agregas filas o columnas.
- Permite activar la fila de totales.
- Tiene su propia pestaña de herramientas: Diseño de tabla.
- Se puede nombrar (Tabla1, Ventas2024, etc.).
- Funciona mejor con tablas dinámicas.
- Permite segmentación de datos (solo disponible para tablas).

---

**Ejemplo:**  
Cuando presionas Ctrl + T en Excel, el rango se convierte en una tabla inteligente.
---

 **Resumen rápido**
 
| Característica |	Rango | Tabla |
|:--|:--|:--|
|Celdas normales	|✔️	|❌ |
|Estilo automático |❌|✔️ |
|Filtros automáticos |	❌|	✔️ |
|Expansión automática |	❌ |	✔️ |
|Fila de totales dinámica	|❌ |	✔️|
|Segmentación de datos |	❌|	✔️ |
|Ideal para grandes volúmenes|	❌|	✔️|
|Existe en LibreOffice Calc	|❌ (solo rangos)|❌(existe tabla dinamica mas no tabla inteligente )


### Filtrar datos 


- Cómo crear un rango estructurado en Calc:
  - Seleccionar las filas y columnas.
  - Ir al menú Datos.
  - Activar Filtro automático.

im_1

- En Excel Online aparece simplemente como Filtrar.
  - Esto le indica a Calc que ese bloque funcionará como una tabla estructurada.
im_2

--- 
**Requisitos importantes**

- Todas las tablas deben tener fila de encabezados, Excel nunca permite eliminar esa fila.
- Antes de convertir un rango en tabla, la primera fila debe contener los títulos.

### Qué ocurre al convertir un rango en tabla (Excel)
- Formato especial automático
- Colores, bordes y estilo.
- No es solo estética: mejora la lectura.
- Botones de filtro en los encabezados  
  - Permiten:
      - Ordenar
      - Filtrar por valores
      - Buscar dentro de la columna
      - Mostrar solo ciertos datos
      - La tabla se vuelve “inteligente”
      - Se expande automáticamente al añadir filas.
      - Aparece la ficha Diseño de tabla.
      - Permite cambiar estilo, agregar fila de totales, renombrar la tabla, etc.
      - La ficha desaparece cuando no estamos dentro de una tabla para no saturar la interfaz.

---

En conclusion las tablas nos facilitan el manejo de datos ya que nos ahorran tiempo y mejoran el rendimiento.

--- 
###  Comparativa Excel vs LibreOffice Calc

|Concepto|	Excel |	LibreOffice Calc |
|:--|:--|:--|
|Rango	|Celdas normales	|Celdas normales |
|Tabla	|Objeto inteligente con filtros, estilo y expansión	| No existe como objeto |
|Filtros |	Automáticos al crear tabla	Datos | Filtro selecionado manualmente |
|Tabla dinámica	|Sí |	Sí |
|Estilos automáticos	| Sí	|Manuales|
|Expansión automática	| Sí	|No |


- Congelar encabezados :“Dejar los rótulos estáticos arriba” = Congelar fila superior.
- Disponible en:Excel , Excel Online, LibreOffice Calc

### Formato rápido de encabezados
- (Calc)
  1. Ver
  2. Inmovilizar celdas
  3. Inmovilizar primera celda
im_3 
- Excel Online
  1. En la cinta de opciones debajo de insertar podemos ver la opcion
  2. Top Row
  3. la selecionamos
im_4
---.
### Tablas en Excel Online
- Excel Online sí permite crear diseño de tablas.
- En Diseño de tabla se puede activar la fila de totales.
  - Se encontro en la cinta de opciones
  - Table Design
  - selecionamos table
 im_6 y im_7 
imagen si hay table
---
- En LibreOffice Calc no existe esta opción automática.
- Aqui es un poco mas manual el diseño de tabla
- Configuración de la fila de totales
im_8


### Actividad 1
1. Configurar las siguientes columnas:
  - CURSO: Recuento
  - DURACIÓN: Suma
  - IMPORTE CLIENTE: Suma
  - IMPORTE PROFESOR: Promedio
  - FECHA CURSO: Mínimo
En la parte inferior asignamos la configuracion pertinente:imagen 8
configuracion 1
resultado final im_9 
---
- **La fila de totales se actualiza automáticamente cuando aplicamos filtros**.
- En los siguiente ejercicios practicos se hicieron en Excel web porque cal no tienen las herramientas requeridas , por eso se llega
a la conclusion que Excel es muy util y tiene muchas herramientas.

### Prácticas realizadas
2. **1.4 Filtrar datos I**
   
  En el archivo 02. BD CURSOS: Se deben aaplicar los siguiente filtros
  - CURSO: DISEÑO, PROGRAMACIÓN, WORD
  - JORNADA CURSO: MAÑANA, TARDE
  - PAGADO CLIENTE: NO
  - PAÍS: ITALIA
    im_10 
Luego consulté la fila de totales.
im_11
---
posterior mente procedi a mirar el video y comprobar el resultado final 
im_12



note que tenia el signo del dolar en lugar del euro , hago el cambio correspondientes
im_13

### Filtrar por terminación o palabras
También practiqué filtros avanzados como:
  - Filtrar por valores que terminan en cierto texto
  - Filtrar por palabras específicas
    im_14

3. **Actividad 3**
- En el archivo 03. BD CURSOS:
    - Filtros aplicados:
    - CURSO: WORD, EXCEL, ACCESS
    - IMPORTE CLIENTE: menor que 1000
    - JORNADA CURSO: MAÑANA, NOCHE
    - PAÍS: ITALIA

Luego revisé la fila de totales.
im_15

### 1.4 Filtrar datos II – Fechas
Los campos de fecha se agrupan automáticamente por: Año, Mes,Día .

--- 
**Importante:**
En una misma columna, no se puede filtrar por elemento y por tipo de dato al mismo tiempo.
El último filtro aplicado es el que prevalece.

4. **Actividad** 
- En el archivo 01. BD CURSOS:para practicar
- Filtros aplicados:
  - CLIENTE: CLIENTE-001, 003, 005, 008
  im_16
  - FECHA CURSO: primeros 6 meses de 2019 y 2021
  im_17
  - DURACIÓN: mayor que 20
  im_18
  - PAÍS: ESPAÑA e ITALIA
  im19
  - PAGADO CLIENTE: NO
  im_20
Luego consulté la fila de totales.
im  21
4.1 **Ejercicio**
- En el archivo 04. BD CURSOS:
- Filtros aplicados:
  - CLIENTE: CLIENTE-001, 003, 005, 008
  imagen 22
  - FECHA CURSO: primeros 6 meses de 2019 y 2021
  imagen 23
  - DURACIÓN: mayor que 20
    24
  - PAÍS: ESPAÑA e ITALIA
    25
  - PAGADO CLIENTE: NO
  26
Luego consulté la fila de totales.
27

### 1.5 Segmentación de datos
La segmentación es una herramienta visual para filtrar tablas.Solo está disponible para:
- Tablas
- Tablas dinámicas
- Cada segmentación es un objeto independiente con un botón por cada elemento del campo.

No encontre segmentacion el excel web procedemos ha realizar los ejercicios en Excel.
