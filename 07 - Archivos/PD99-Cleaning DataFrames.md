## Eliminar valores nulos
 - `df.isna()` devuelve una serie en `boolean` de los valores que son nulos
```python
     0     1    2
0  ant   bee  cat
1  dog  None  fly

mask = df.isna()
       0      1      2
0  False  False  False
1  False   True  False

df[mask].sum()
0 0 
1 1 
2 0
```
- `df.dropna()` elimina filas y/o columnas con valores nulos
```python
df.dropna(how='any', axis='columns', thresh=3) 
# thresh indica la cantidad minima de valores no-null a mantener 
```

- `df.fillna()` rellena los valores nulos con un `value` especifico
```python
df.fillna(value)
# df.fillna(df.mean()) es una opcion
```
Si se quiere rellenar solo una columna especifica se puede usar un diccionario como valor:

```python
df.fillna({"column": 0})
```

```python
df.fillna(method='ffill') # para rellenar valores
```

- `.notnull()` tambien se puede usar para entregar un `boolean` de los valores validos (no `falsy`)

- `s.any()`, `s.all()` son metodos de python que verifican si es que algun (`any`) valor es nulo o si todos (`all`) los valores son validos
```python
pd.Series([True, False, False]).any()
True

pd.Series([True, False, False]).all()
False
```
## Detección y eliminación de duplicados
- `df.duplicated()` devuelve un `boolean` si la fila ya se encontraba previamente
```python
df.duplicated(subset=["column"], keep='first') #keep default 'first'
```

- `df.drop_duplicates()` elimina filas duplicadas
```python
df.drop_duplicates()
```

- `df.unique()` entrega un `array` con los valores unicos
```python
df['Sex'].unique()

array(['M', 'F', 'D', '?'], dtype=object) #output
```

- `df.value_counts()` similar a unique solo que entrega un `DataFrame` con cuantas veces se repite cada valor
```python
df['Sex'].value_counts()
F    2
D    1
?    1
M    1
Name: Sex, dtype: int64 #output
```
## Manejo de valores atípicos
- `df.clip()` recorta los valores que exceden un rango especifico
```python
df.clip(lower, upper)
```
- `.replace()` remplaza los valores declarados con otros
```python
df.replace({
    'Sex': {
        'D': 'F',
        'N': 'M'
    },
    'Age': {
        290: 29
    }
})
```

|Sex|Age|
|---|---|
|0|M|29|
|1|F|30|
|2|F|24|
|3|F|29|
|4|?|25|
- `.quantile(q)` calcula los cuantiles en busca de valores atípicos
## Formato

- `df.info()` entrega un dataframe con el dtype de cada valor
```python
 #   Column    Non-Null Count  Dtype  
---  ------    --------------  -----  
 0   Column A  2 non-null      float64
 1   Column B  3 non-null      float64
 2   Column C  3 non-null      float64
 3   Column D  4 non-null      int64
```

- `df.astype()` 
```python
df.astype({'col1': 'int32'})
col1    int32
```

```python
df["col1"] = df[["col1"]].astype("int32")
col1    int32
```

## Agregar filas
- `pd.concat()`
```python
pd.concat([df1, df2])
```
[pandas concat](https://pandas.pydata.org/docs/user_guide/10min.html#concat)

## Reshape
- `pd.pivot_table`
```python
pd.pivot_table(df, values="D", index=["A", "B"], columns=["C"])

C             bar       foo
A     B                    
one   A  2.395985 -1.202872
      B  1.395433 -1.814470
      C -0.392670 -0.055224
three A -0.595447       NaN
      B       NaN  1.928123
      C  0.166599       NaN
two   A       NaN  0.007207
      B  1.552825       NaN
      C       NaN  1.018601
```
> [!note]- methods
> `aggfunc=`
> 

[[pd.pivot_table]]
[pandas pivot](https://pandas.pydata.org/docs/user_guide/reshaping.html#reshaping-pivot)

- `.split()` divide un `DataFrame` segun el caracter seleccionado
```python
df['Data'].str.split('_', expand=True)
```

|0|1|2|3|
|---|---|---|---|
|0|1987|M|US|1|
|1|1990?|M|UK|1|
|2|1992|F|US|2|
|3|1970?|M|IT|1|
|4|1985|F|I T|2|