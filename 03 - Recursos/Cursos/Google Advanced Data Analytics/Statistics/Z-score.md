---
created: 2024-08-29
tags:
  - Matematicas/estadistica
aliases:
  - z-score
  - numero z
  - valor z
---
# Z-score
El **Z-score** es la distancia (+/-) entre un valor y su media en una [[Distribucion normal|distribucion normal]].

## Medida
$$
Z = \frac{\bar{x}-\mu}{\dfrac{\sigma}{\sqrt{ n }}}
$$
- $\bar{x}$: sample mean
- $\mu$: 
- $\sigma$: population std / $S$: sample std
- $n$: sample size

## Proporcion
### Dos muestras
$$
Z = \frac{\hat{p}_{1}-\hat{p}_{2}}{\sqrt{ \hat{p}_{0}(1-\hat{p}_{0})\left( \dfrac{1}{n_{1}}+\dfrac{1}{n_{2}} \right) }}
$$
- $\hat{p}_{i}$: sample proportion
- $n_{i}$: sample size

Por lo general no se suele tener la desviacion estandar de la poblacion ($\sigma$), por lo que se usa la desviacion estandar de la muestra ($S$)