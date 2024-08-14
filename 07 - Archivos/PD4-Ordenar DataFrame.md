## Agrupacion de un DataFrame
![[Pasted image 20240312035918.png]]

### Dividir un DataFrame en grupos
#### Creacion de grupos

El metodo `df.groupby()` se refiere al proceso de uno o mas de los siguientes pasos:

- **Divivir** los datos en grupos basados en un criterio
- **Aplicar** una función a cada grupo de manera independiente
- **Combinar** los resultados en una estructura de datos (*Series* o *DataFrame*)

|    |   A   |   B   |    C     |    D     |
|----|-------|-------|---------|---------|
|  0 |  foo  |  one  | 1.346061| -1.577585|
|  1 |  bar  |  one  | 1.511763|  0.396823|
|  2 |  foo  |  two  | 1.627081| -0.105381|
|  3 |  bar  | three | -0.990582|-0.532532|
|  4 |  foo  |  two  | -0.441652| 1.453749|
|  5 |  bar  |  two  | 1.211526|  1.208843|
|  6 |  foo  |  one  | 0.268520| -0.080952|
|  7 |  foo  | three | 0.024580| -0.264610|

```python
df.groupby("A")[["C", "D"]].sum()
```

> [!info]
> ![[Pasted image 20240320025726.png]]
> 


|    A   |     C     |     D     |
|--------|-----------|-----------|
|  bar   |  1.732707 |  1.073134 |
|  foo   |  2.824590 | -0.574779 |

#### Para dividir en grupos
- `df.groupby(columns).groups`: Devuelve un **diccionario** con cuyas claves son las **tuplas** que resultan de todas las combinaciones de los valores de las columnas con los nombres en la lista `columnns`, y valores las listas de los nombres de las filas que contienen esos valores en las correspondientes columnas del **DataFrame** `df`.
> [!example]- DataFrame
> 
> |    | nombre                        | edad | sexo | peso | altura | colesterol |
> |---:|-------------------------------|------|------|------|--------|------------|
> |  0 | José Luis Martínez Izquierdo | 18   | H    | 85.0 | 1.79   | 182.0      |
> |  1 | Rosa Díaz Díaz                | 32   | M    | 65.0 | 1.73   | 232.0      |
> |  2 | Javier García Sánchez         | 24   | H    |      | 1.81   | 191.0      |
> |  3 | Carmen López Pinzón           | 35   | M    | 65.0 | 1.7    | 200.0      |
> |  4 | Marisa López Collado          | 46   | M    | 51.0 | 1.58   | 148.0      |
> |  5 | Antonio Ruiz Cruz             | 68   | H    | 66.0 | 1.74   | 249.0      |
> |  6 | Antonio Fernández Ocaña       | 51   | H    | 62.0 | 1.72   | 276.0      |
> |  7 | Pilar Martín González         | 22   | M    | 60.0 | 1.66   |            |
> |  8 | Pedro Gálvez Tenorio          | 35   | H    | 90.0 | 1.94   | 241.0      |
> |  9 | Santiago Reillo Manzano       | 46   | H    | 75.0 | 1.85   | 280.0      |
> | 10 | Macarena Álvarez Luna         | 53   | M    | 55.0 | 1.62   | 262.0      |
> | 11 | José María de la Guía Sanz    | 58   | H    | 78.0 | 1.87   | 198.0      |
> | 12 | Miguel Angel Cuadrado Gutiérrez | 27 | H  | 109.0| 1.98   | 210.0      |
> | 13 | Carolina Rubio Moreno         | 20   | M    | 61.0 | 1.77   | 194.0      |
> 
> 

```python
>>> print(df.groupby("sexo").groups)

{
    "H": Int64Index([0, 2, 5, 6, 8, 9, 11, 12], dtype="int64"),
    "M": Int64Index([1, 3, 4, 7, 10, 13], dtype="int64"),
}

>>> print(df.groupby(["sexo", "edad"]).groups)

{
    ("H", 18): Int64Index([0], dtype="int64"),
    ("H", 24): Int64Index([2], dtype="int64"),
    ("H", 27): Int64Index([12], dtype="int64"),
    ("H", 35): Int64Index([8], dtype="int64"),
    ("H", 46): Int64Index([9], dtype="int64"),
    ("H", 51): Int64Index([6], dtype="int64"),
    ("H", 58): Int64Index([11], dtype="int64"),
    ("H", 68): Int64Index([5], dtype="int64"),
    ("M", 20): Int64Index([13], dtype="int64"),
    ("M", 22): Int64Index([7], dtype="int64"),
    ("M", 32): Int64Index([1], dtype="int64"),
    ("M", 35): Int64Index([3], dtype="int64"),
    ("M", 46): Int64Index([4], dtype="int64"),
    ("M", 53): Int64Index([10], dtype="int64"),
}

```

#### Para obtener un grupo concreto
- `df.groupby(columns).get_group(values)`: Devuelve un **DataFrame** con las filas del **DataFrame** `df` que cumplen de la lista `columnas` presentanlos valores de la **tupla** `values`. La lista `columns` y la tupla `values` deben tener el mismo tamano.
```python
>>> print(df.groupby('sexo').get_group('M'))
                    nombre  edad sexo    peso   altura    colesterol
1           Rosa Díaz Díaz    32    M    65.0     1.73         232.0
3      Carmen López Pinzón    35    M    65.0     1.70         200.0
4     Marisa López Collado    46    M    51.0     1.58         148.0
7    Pilar Martín González    22    M    60.0     1.66           NaN
10   Macarena Álvarez Luna    53    M    55.0     1.62         262.0
13   Carolina Rubio Moreno    20    M    61.0     1.77         194.0
```

### Aplicar una agregacion por grupos
- `df.groupby(columns).agg(function)`: Devuelve un **DataFrame** con el resultado de aplicar las funciones de agregacion de la lista `functions` a cada uno de los **DataFrames** que resultan de dividir el DataFrame segun las columnas de la lista
> [!info]- Functions
> - `np.min` : Devuelve el mínimo de una lista de valores.
> - `np.max` : Devuelve el máximo de una lista de valores.
> - `np.count_nonzero` : Devuelve el número de valores no nulos de una lista de valores.
> - `np.sum` : Devuelve la suma de una lista de valores.
> - `np.mean` : Devuelve la media de una lista de valores.
> - `np.std` : Devuelve la desviación típica de una lista de valores.
> 
```python
>>> print(df.groupby('sexo').agg(np.mean))
           edad       peso    altura  colesterol
sexo                                            
H     40.875000  80.714286  1.837500     228.375
M     34.666667  59.500000  1.676667     207.200
```

```python
>>> print(df.groupby(['edad', 'sexo'])[['altura']].agg(np.mean))
```

### Quitar indice anterior
- `df.reset_index(Level=None)`: Reinicia el indice del **DataFrame**, y usa el por defecto en su lugar (1, 2, 3...). Si el DataFrame tiene multindice este metodo remove uno o mas niveles.

```python
import pandas as pd

# Crear un DataFrame de ejemplo
data = {'Nombre': ['Juan', 'María', 'Pedro'],
        'Edad': [25, 30, 35]}
df = pd.DataFrame(data)
# Configurar el índice a una nueva columna llamada 'ID'
df['ID'] = ['A', 'B', 'C']
df.set_index('ID', inplace=True)

print(df)
```

| ID  | Nombre | Edad |
| --- | ------ | ---- |
| A   | Juan   | 25   |
| B   | María  | 30   |
| C   | Pedro  | 35   |

```python
# Restablecer el índice
df_reset = df.reset_index()

# Mostrar el DataFrame después de restablecer el índice
print(df_reset)
```


|     | ID  | Nombre | Edad |
| --- | --- | ------ | ---- |
| 0   | A   | Juan   | 25   |
| 1   | B   | María  | 30   |
| 2   | C   | Pedro  | 35   |


> [!important]
> Al usar `df.groupby()` se se considerara como indice los valores agrupados, pero si se usa `df.groupby().reset_index()` se incluiran los las columnas
> 

### Contar valores unicos segun grupo
- `df.groupby(columns).nunique(dropna=True)`: Devuelve un **DataFrame** con la cantidad de valores unicos de `columns`, tomando `columns` como nuevo indice.

|     | id   | value1 | value2 |
| --- | ---- | ------ | ------ |
| 0   | spam | 1      | a      |
| 1   | egg  | 5      | b      |
| 2   | egg  | 5      | b      |
| 3   | spam | 2      | a      |
| 4   | ham  | 5      | x      |
| 5   | ham  | 5      | y      |

```python
df.groupby('id').nunique()
```

| id   | value1 | value2 |
| ---- | ------ | ------ |
| egg  | 1      | 1      |
| ham  | 1      | 2      |
| spam | 2      | 1      |

## Restructurar un DataFrame
![[Pasted image 20240312042309.png]]

### Convertir un DataFrame a formato largo
- `df.melt(id_vars=id-columns, value_vars=columns, var_name=nombre-columns, var_value=nombre-values)`: Devuelve un **DataFrame** que resulta de convertir el DataFrame `df` de formato *ancho* a formato *largo*. Todas las columnas de la lista `columns` se reestructuran en dos nuevas columnas con nombres `nombre-columns` y `nombre-values` que contienen los nombres de las columnas originales y sus valores, respectivamente. Las columnas en la lista `id-columns` se mantienen sin reestructurar. Si no se pasa la lista `columns` entonces todas las columnas excepto las columnas de la columnas de la lista `id-columns`

```python
>>> datos = {'nombre':['María', 'Luis', 'Carmen'],
... 'edad':[18, 22, 20],
... 'Matemáticas':[8.5, 7, 3.5],
... 'Economía':[8, 6.5, 5],
... 'Programación':[6.5, 4, 9]}
>>> df = pd.DataFrame(datos)

>>> df1 = df.melt(id_vars=['nombre', 'edad'], var_name='asignatura', value_name='nota')
>>> print(df1)
```

|    | nombre | edad | asignatura   | nota |
|---:|:-------|-----:|:-------------|-----:|
|  0 | María  |   18 | Matemáticas |  8.5 |
|  1 | Luis   |   22 | Matemáticas |  7.0 |
|  2 | Carmen |   20 | Matemáticas |  3.5 |
|  3 | María  |   18 | Economía     |  8.0 |
|  4 | Luis   |   22 | Economía     |  6.5 |
|  5 | Carmen |   20 | Economía     |  5.0 |
|  6 | María  |   18 | Programación |  6.5 |
|  7 | Luis   |   22 | Programación |  4.0 |
|  8 | Carmen |   20 | Programación |  9.0 |

### Convertir un DataFrame a formato ancho
- `df.pivot(index=rows, columns=column, values=values)`: Devuelve el **DataFrame** que resulta de convertir el DataFrame `df` de formato largo a formato ancho. Se crean tantas columnas nuevas como valores distintos haya en la columna `column`. Los nombres de estas nuevas columnas son los valores de la columna `column` mientras que sus valores se toman de la columna `values`. Los nombres del indice del nuevo DataFrame se toman de los valores de la columna `rows`.
```python
>>> print(df1.pivot(index='nombre', columns='asignatura', values='nota'))
```

| nombre | Economía | Matemáticas | Programación |
|--------|----------|-------------|--------------|
| Carmen | 5.0      | 3.5         | 9.0          |
| Luis   | 6.5      | 7.0         | 4.0          |
| María  | 8.0      | 8.5         | 6.5          |
## Combinar varios DataFrames
Dos o mas DataFrames puede combinarse en tro DataFrame. La combinacion puede set de varias formas:
- **Concatenacion**: Combinacion de varios DataFrames concatenando sus filas o clumnas
- **Mezcla**: Combinacion de varios DataFrames usando columnas o indices comunes.

### Concatenación de DataFrames

- `df.concat([df1, df2], axis=0)`: Devuelve el DataFrame que resulta de concatenar los DataFrames de la lista `dataframes`. Si `eje` es 0 (valor por defecto) la concatenación se realiza por filas, y si `eje` es 1 se realiza por columnas.
> [!caution]-
> Si los DataFrame que **se concatenan por filas** no tienen el mismo indice de columnas, el DataFrame incluira todas las columnas existentes en los DataFrames y rellenara con `NaN` los datos no disponibles. 
> 
> Si los DataFrames que **se concatenan por columnas** no tienen el mismo indice de filas, el DataFrame resultante incluira todas las filas existentes de los DataFrames y rellenara los valores con `NaN` los datos no disponibles.
> 



#### Concatenacion de filas
- `df.concat([df1, df2])`

![[Pasted image 20240321010655.png]]

```python
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis"], 
... "Sexo":["Mujer", "Hombre"], "Edad":[22, 18]}).set_index("Nombre")

>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro"], 
... "Sexo":["Mujer", "Hombre"], "Edad":[25, 30]}).set_index("Nombre")
```

- df1:

| Nombre (index) | Sexo   | Edad |
| -------------- | ------ | ---- |
| Carmen         | Mujer  | 22   |
| Luis           | Hombre | 18   |

- df2: 

| Nombre (index) | Sexo   | Edad |
| -------------- | ------ | ---- |
| María          | Mujer  | 25   |
| Pedro          | Hombre | 30   |

```python
>>> df = pd.concat([df1, df2])
```

|Nombre (index)|Sexo|Edad|
|---|---|---|
|Carmen|Mujer|22|
|Luis|Hombre|18|
|María|Mujer|25|
|Pedro|Hombre|30|


#### Concatenacion de columnas

- `pd.concat([df1, df2] axis=1)`

![[Pasted image 20240321010715.png]]

```python
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"], 
... "Sexo":["Mujer", "Hombre", "Mujer"]}).set_index("Nombre")

>>> df2 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"], 
... "Edad":[22, 18, 25]}).set_index("Nombre")
```

- df1:

| Nombre (index) | Sexo   |
| -------------- | ------ |
| Carmen         | Mujer  |
| Luis           | Hombre |
| María          | Mujer  |

- df2:

| Nombre (index) | Edad |
| -------------- | ---- |
| Carmen         | 22   |
| Luis           | 18   |
| María          | 25   |


```python
>>> df = pd.concat([df1, df2], axis = 1)
```

| Nombre (index) | Sexo   | Edad |
| -------------- | ------ | ---- |
| Carmen         | Mujer  | 22   |
| Luis           | Hombre | 18   |
| María          | Mujer  | 25   |




### Mezcla de DataFrames

La mezcla de DataFrames permite integrar filas de dos DataFrames que contienen information en comun en una o varias columnas o indices que se conocen como *key*.

Para eso se usa el metodo:
- `df.merge(df1, df2, on = [key], how = type)`: Devuelve un **DataFrame** que resulta de mezlar el DataFrame `df2` con el DataFrame `df1`, usando como claves las columnas de la lista `key` y siguiendo el metodo de mezcla indicado por `type`.

Usando los siguientes DataFrames:

`df1`:

|     | Nombre | Sexo   |
| --- | ------ | ------ |
| 0   | Carmen | Mujer  |
| 1   | Luis   | Hombre |
| 2   | María  | Mujer  |
 `df2`:

|   | Nombre |  Edad  |
|---|--------|--------|
| 0 | María  |   25   |
| 1 | Pedro  |   30   |
| 2 |  Luis  |   18   |
La mezcla puede set:
#### Interseccion
- `inner (default)`: El DataFrame resultante solo contiene las filas cuyos valores en la clave estan en los dos DataFrame. Es equivalente a la [[AMR1-Interseccion de conjuntos|interseccion de conjuntos]]:

```python
df = pd.merge(df1, df2, on="Nombre")
```

|     | Nombre | Sexo   | Edad |
| --- | ------ | ------ | ---- |
| 0   | Luis   | Hombre | 18   |
| 1   | María  | Mujer  | 25   |
#### Union
- `outer`: El DataFrame resultante contiene todas las filas de los dos DataFrame. Si una fila de un DataFrame no puede emparejarse con otra los mismos valores en clave en el otro DataFrame, la fila se anade igualmente al DataFrame resultante **rellenando las columnas del otro DataFrame con el valor** `NaN`. Es equivalente a la [[AMR2-Union de conjuntos|union de conjuntos]] 
```python
df = pd.merge(df1, df2, on="Nombre", how="outer")
```

|     | Nombre | Sexo   | Edad |
| --- | ------ | ------ | ---- |
| 0   | Carmen | Mujer  | NaN  |
| 1   | Luis   | Hombre | 18.0 |
| 2   | María  | Mujer  | 25.0 |
| 3   | Pedro  | NaN    | 30.0 |

#### Izquierda
- `left`: El **DataFrame** resultante contiene todas las filas del primer DataFrame y descarta las filas del segundo DataFrame que no pueden emparjarse con alguna fila del primer DataFrame a traves de la clave.
```python
pd.merge(df1, df2, on="Nombre", how="left")
```

|   | Nombre |  Sexo  |  Edad |
|---|--------|--------|-------|
| 0 | Carmen | Mujer  |  NaN  |
| 1 |  Luis  | Hombre | 18.0  |
| 2 | María  | Mujer  | 25.0  |
#### Derecha
- `right`: El **DataFrame** resultante contiene todas las filas del segundo DataFrame y descarta las filas del primer DataFrame `df1` que no pueden emparejarse con alguna fila del segundo DataFrame `df2` a traves de una clave.
```python
pd.merge(df1, df2, on="Nombre", how="right")
```

|   | Nombre |  Sexo  |  Edad |
|---|--------|--------|-------|
| 0 |  María | Mujer  |   25  |
| 1 |  Pedro |  NaN   |   30  |
| 2 |  Luis  | Hombre |   18  |
#### Cruzado
- `cross`

![Pandas >> Data Combination(1): merge() | by NextGenTechDawn | Medium](https://miro.medium.com/v2/resize:fit:1400/0*8Fsy94YE9M6stkT2.png)