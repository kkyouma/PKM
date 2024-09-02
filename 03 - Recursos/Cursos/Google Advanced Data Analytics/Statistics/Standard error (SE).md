---
created: 2024-08-27
tags:
  - Matematicas/estadistica
aliases:
  - standard error
  - error estandar
  - error standard
  - SE
---
# Standard error (SE)
El **error estándar** mide la variabilidad o dispersión de una muestra respecto a la media de la población. Es una estimación de cuanto difiere la media de la muestra de la media de la verdadera población.

$$\text{SE}=\frac{S}{\sqrt{n}}$$
- $S$ std de muestra
- $n$ tamaño de muestra

## Python
```python
df_sample = df.sample(n=10, replace=True, random_see)
estimate_1 = df_sample.mean()
```

- Population mean
- Sample estimate 1
- Sample estimate 2

Para hacer este proceso se puede automatizar

```python
estimations = 1000 # Number of estiamtes mean
estimate_list = []
for i in range(estimations):
	estimate_list.append(df.sample(n=50, replace=True).mean())
estimate_df = pd.DataFrame(data={"estimate": estimate_list})
```