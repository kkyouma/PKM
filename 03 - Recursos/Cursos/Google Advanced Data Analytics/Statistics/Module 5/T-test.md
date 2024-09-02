---
created: 2024-08-31
tags:
  - Matematicas/estadistica
aliases:
  - t-test
---
# T-test
Compara las medias de dos grupos cuando las muestras son pequeñas ($n < 30$) o la varianza es desconocida.

- Las dos muestras son independientes entre si
- Para cada muestra, los datos estan sacados aleatoriamente de poblacion con distribucion normal
- La desviacion estandar de la poblacion es desconocida
## Elementos
-  [[T-score]]
-  [[P-value]]
-  [[Pruebas de una cola|pruebas de una cola]] y [[Pruebas de dos colas]] 
## Programacion
### Python
#### Una muestra
- **Una cola**: `stats.ttest_1samp(a, popmean, alternative)`
	- `a`: sample `pd.Series`
	- `popmean`: media de la poblacion `int`
	- `alternative`: signo de la hipotesis alternativa "greater", "lower" `str`

```python
tstat, pvalue = stats.ttest_1samp(michigan['aqi'], 10, alternative='greater')

print(tstat)
print(pvalue)
```

- **Dos colas**: Lo mismo :LiArrowUp: pero `alternative="two-sided"`
#### Dos muestras
- **Dos colas**: `stats.ttest_ind(a,b,equal_var)` `a` y `b` son dos *Series* de muestra a comparar. Devuelve una tupla con `(statistic, pvalue)`

```python
from scipy import stats

stats.ttest_ind(sampled_1,sampled_2,equal_var=False)
```

- **Una cola**: `stats.ttest_`
