---
created: 2024-07-22
tags:
  - data-analysis
  - data-science
aliases:
  - eda
  - exploring data analysis
  - analisis exploratorio de datos
  - analisis exploratorio
---
# EDA
El **Exploring Data Analysis (EDA)** es un proceso *iterativo* y *no estrictamente secuencial*. Mediante el que se exploraran los datos, se realizaran limpiezas y otros 

- Descubrir
- [[Estructurar datos Pandas|Estructurar]]
- [[PD99-Cleaning DataFrames|Limpiar]]
- Unir
- Validar
- Presentar

![[Pasted image 20240722223157.png]]

1. **Descubrir**: Comprueba la forma general, el tamaño y el contenido del conjunto de datos. Comprueba que los datos son escasos. 
2. **Unir**: Se añaden más datos.
3. **Validar**: Se comprueba rápidamente que los nuevos datos no contienen errores ni faltas de ortografía. 
4. **Estructuración**: Se estructuran los datos en diferentes periodos de tiempo y segmentos para comprender las tendencias. 
5. **Validación**: Realiza otra comprobación rápida para asegurarse de que las nuevas columnas que ha creado en la estructuración están correctamente diseñadas. 
6. **Limpieza**: Se comprueban los valores atípicos, los datos que faltan y las conversiones o transformaciones necesarias. 
7. **Validación**: Tras la limpieza, se comprueba que los cambios realizados son correctos y precisos. 
8. **Presentación**: Se comparte el conjunto de datos con un compañero. 
## Pasos
### Discovering
- **Carga de Datos:** Importar el dataset.
- **Vista Preliminar:** Revisar las primeras y últimas filas.
- **Descripción Estadística:** Obtener estadísticas descriptivas.
- **Revisión de Estructura:** Evaluar la forma, tamaño y tipos de datos

```python
import pandas as pd

# Cargar el dataset
df = pd.read_csv('ruta_a_tu_archivo.csv')

# Vista preliminar
print(df.head())
print(df.tail())

# Descripción estadística
print(df.describe())

# Revisión de estructura
print(df.shape)
print(df.info())

```

### Joining
- **Agregar Más Datos:** Combinar datasets adicionales.
- **Unión de Datos:** Unir datasets por una clave común.
```python
# Agregar más datos
df_nuevo = pd.read_csv('ruta_a_otro_archivo.csv')
df = pd.concat([df, df_nuevo], ignore_index=True)

# Unión de datos por clave común
df_merged = pd.merge(df1, df2, on='clave_comun', how='left')

```


### Validating
- **Revisión de Valores Nulos:** Identificar y manejar valores nulos.
- **Validación de Tipos de Datos:** Asegurar que los tipos de datos sean correctos.
- **Validación de Nuevos Datos:** Revisar datos nuevos agregados para errores.

```python
# Revisión de valores nulos
print(df.isnull().sum())

# Validación de tipos de datos
print(df.dtypes)
df['columna'] = df['columna'].astype(tipo_deseado)

# Validación de nuevos datos
print(df['columna'].unique())

```

### Structuring
- **Reestructuración Temporal:** Agrupar datos por períodos de tiempo.
- **Segmentación:** Agrupar datos por categorías o segmentos específicos.
```python
# Reestructuración temporal
df['fecha'] = pd.to_datetime(df['fecha'])
df.set_index('fecha', inplace=True)
df_resample = df.resample('M').sum()  # Ejemplo de reestructuración por mes

# Segmentación
segmentos = df.groupby('columna_segmento').sum()

```

### Cleaning
- **Eliminación de Valores Nulos:** Manejar valores nulos mediante eliminación o imputación.
- **Eliminación de Duplicados:** Remover filas duplicadas.
- **Detección de Outliers:** Identificar y manejar valores atípicos.
- **Conversión de Tipos:** Asegurar la coherencia en los tipos de datos.

```python
# Eliminación de valores nulos
df = df.dropna()  # o df.fillna(valor)

# Eliminación de duplicados
df = df.drop_duplicates()

# Detección de outliers
import seaborn as sns
sns.boxplot(x='variable', data=df)

# Conversión de tipos
df['columna'] = df['columna'].astype(tipo_deseado)

```

- [>] [[Como manejar valores nulos]] 
### Presenting
- **Documentación:** Documentar hallazgos y procesos.
- **Compartir Dataset:** Exportar y compartir el dataset limpio y estructurado.
- **Visualización:** Crear visualizaciones para comunicar insights.

```python
# Exportar dataset limpio
df.to_csv('dataset_limpio.csv')

# Visualización básica
import matplotlib.pyplot as plt
sns.histplot(df['columna'], kde=True)
plt.show()

```