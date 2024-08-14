---
created: 2024-08-07
tags:
  - Data-science/Data-analysis/Spreadsheets
aliases:
  - spreadsheets cheat sheet
---
# Spreadsheets cheat sheet
¡Claro! Aquí tienes un cheat sheet enfocado en funciones y comandos más útiles para el análisis de datos en Google Sheets:

### Funciones de Búsqueda y Referencia

- **VLOOKUP**: `=VLOOKUP(search_key, range, index, [is_sorted])`
  - Busca un valor en la primera columna de un rango y devuelve un valor en la misma fila desde una columna especificada.
  
- **HLOOKUP**: `=HLOOKUP(search_key, range, index, [is_sorted])`
  - Busca un valor en la primera fila de un rango y devuelve un valor en la misma columna desde una fila especificada.

- **INDEX**: `=INDEX(range, row_number, [column_number])`
  - Devuelve el valor de una celda en un rango especificado por el número de fila y columna.

- **MATCH**: `=MATCH(search_key, range, [search_type])`
  - Devuelve la posición relativa de un elemento dentro de un rango.

### Funciones de Manipulación de Texto

- **SPLIT**: `=SPLIT(text, delimiter)`
  - Divide el texto en fragmentos utilizando un delimitador específico.

- **CONCATENATE**: `=CONCATENATE(string1, [string2, ...])`
  - Une varios textos en una sola cadena.

- **LEFT, MID, RIGHT**: 
  - `=LEFT(text, [number_of_characters])`
  - `=MID(text, start, number_of_characters)`
  - `=RIGHT(text, [number_of_characters])`
  - Extraen una cantidad específica de caracteres desde el inicio, medio o final del texto.

### Funciones de Fecha y Hora

- **TODAY**: `=TODAY()`
  - Devuelve la fecha actual.

- **NOW**: `=NOW()`
  - Devuelve la fecha y hora actual.

- **DATEDIF**: `=DATEDIF(start_date, end_date, unit)`
  - Calcula la diferencia entre dos fechas en días, meses o años.

- **NETWORKDAYS**: `=NETWORKDAYS(start_date, end_date, [holidays])`
  - Calcula la cantidad de días laborales entre dos fechas, excluyendo fines de semana y días festivos opcionales.

### Funciones de Estadística y Matemáticas

- **SUM, AVERAGE, MIN, MAX**: 
  - `=SUM(range)`, `=AVERAGE(range)`, `=MIN(range)`, `=MAX(range)`
  - Suman, promedian, encuentran el mínimo y el máximo de un rango de celdas.

- **COUNT, COUNTA**: 
  - `=COUNT(range)`, `=COUNTA(range)`
  - Cuenta celdas con números y cuenta celdas no vacías, respectivamente.

- **SUMIF, SUMIFS**: 
  - `=SUMIF(range, criterion, [sum_range])`
  - `=SUMIFS(sum_range, criteria_range1, criterion1, [criteria_range2, criterion2, ...])`
  - Suman celdas que cumplen con un criterio (o múltiples criterios).

- **AVERAGEIF, AVERAGEIFS**: 
  - `=AVERAGEIF(range, criterion, [average_range])`
  - `=AVERAGEIFS(average_range, criteria_range1, criterion1, [criteria_range2, criterion2, ...])`
  - Promedian celdas que cumplen con un criterio (o múltiples criterios).

### Funciones de Filtrado y Ordenamiento

- **FILTER**: `=FILTER(range, condition1, [condition2, ...])`
  - Filtra un rango de datos según una condición.

- **SORT**: `=SORT(range, sort_column, is_ascending, [sort_column2, is_ascending2, ...])`
  - Ordena un rango de datos según una o más columnas.

- **QUERY**: `=QUERY(data, query, [headers])`
  - Usa consultas tipo SQL para manipular y extraer datos.

### Funciones de Manipulación de Datos

- **IMPORTRANGE**: `=IMPORTRANGE(spreadsheet_url, range_string)`
  - Importa un rango de celdas desde otra hoja de cálculo.

- **ARRAYFORMULA**: `=ARRAYFORMULA(array_formula)`
  - Permite aplicar una fórmula a un rango de celdas.

- **UNIQUE**: `=UNIQUE(range)`
  - Devuelve un rango de valores únicos de un conjunto de datos.

- **TRANSPOSE**: `=TRANSPOSE(range)`
  - Cambia la orientación de un rango de celdas de filas a columnas y viceversa.

### Formato y Visualización

- **Formato Condicional**: 
  - Aplica formato basado en reglas para resaltar datos importantes (Formato > Formato condicional).

- **Gráficos**: 
  - Inserta gráficos para visualizar datos (Insertar > Gráfico).

### Comandos y Atajos de Teclado

- **Ctrl + /**: 
  - Abre el menú de atajos de teclado.

- **Ctrl + Shift + V**: 
  - Pega sin formato.

- **Ctrl + \[** y **Ctrl + \]**: 
  - Expande y contrae filas/columnas seleccionadas.

Este cheat sheet te ayudará a aprovechar al máximo las capacidades de Google Sheets para el análisis de datos.