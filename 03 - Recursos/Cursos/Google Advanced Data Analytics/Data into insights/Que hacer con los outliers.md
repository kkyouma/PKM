---
created: 2024-08-14
tags: 
aliases:
  - que hacer con los outliers
---
# Que hacer con los outliers
1. [[#Eliminarlos]]
2. [[#Reasignarlos]]
3. [[#Dejarlos]]

## Eliminarlos
```python
box = sns.boxplot(x=df['number_of_strikes']) 
g = plt.gca() # Obtiene info del grafico actual
box.set_xticklabels(np.array([readable_numbers(x) for x in g.get_xticks()])) #Se obtienen las etiquetas del eje X, luego se aplica una funcion para formatear y luego se aplica a la figura
plt.xlabel('Number of strikes')
plt.title('Yearly number of lightning strikes');
```

Establecer criterios para los que se considerara que un valor es o no un Outlier

```python
# Calculate 25th percentile of annual strikes
percentile25 = df['number_of_strikes'].quantile(0.25)

# Calculate 75th percentile of annual strikes
percentile75 = df['number_of_strikes'].quantile(0.75)

# Calculate interquartile range
iqr = percentile75 - percentile25

# Calculate upper and lower thresholds for outliers
upper_limit = percentile75 + 1.5 * iqr
lower_limit = percentile25 - 1.5 * iqr

print('Lower limit is: ', upper_limit)
```

aplicar limites para eliminar outliers

```python
mask = (df['number_of_strikes'] >= lower_limit) & (df['number_of_strikes'] <=
upper_limit)

df = df[mask].copy()
```
## Reasignarlos

1. **Cree un suelo y un techo en un cuantil:** Por ejemplo, puede colocar paredes en los percentiles 90 y 10 de la distribución de los valores de los datos. Cualquier valor por encima de la marca del 90% o por debajo de la marca del 10% se modifica para ajustarse a las paredes que establezca. He aquí un ejemplo de cómo podría ser ese código:
```python
# Calculate 10th percentile
tenth_percentile = np.percentile(df['number_of_strikes'], 10)

# Calculate 90th percentile
ninetieth_percentile = np.percentile(df['number_of_strikes'], 90)

# Apply lambda function to replace outliers with thresholds defined above
df['number_of_strikes'] = df['number_of_strikes'].apply(lambda x: (
    tenth_percentile if x < tenth_percentile 
    else ninetieth_percentile if x > ninetieth_percentile 
    else x))
```

2. **Imputar la media:** En algunos casos, puede ser mejor reasignar todos los valores atípicos para que coincidan con la mediana o el valor medio. Esto garantizará que la mediana y la distribución se basen únicamente en los valores no atípicos, excluyendo los valores atípicos originales. La imputación real o la reasignación de valores puede ser bastante sencilla si ya ha encontrado los valores atípicos. El siguiente bloque de código calcula la mediana de los valores superiores al límite inferior. A continuación, imputa la mediana de los valores inferiores al límite inferior.

```python
# Calculate median of all NON-OUTLIER values
median = np.median(df['number_of_strikes'][df['number_of_strikes'] >= lower_limit])

# Impute the median for all values < lower_limit
df['number_of_strikes'] = np.where(df['number_of_strikes'] < lower_limit, median, df['number_of_strikes'] )
```