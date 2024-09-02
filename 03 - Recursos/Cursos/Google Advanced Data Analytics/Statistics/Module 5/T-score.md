---
created: 2024-08-30
tags:
  - Matematicas/estadistica
aliases:
  - t-score
---
# T-score
El **T-score** es un valor que se utiliza en estadística para calcular la probabilidad de obtener un resultado específico cuando la desviación estándar de la población es desconocida y el tamaño de la muestra es pequeño (menos de $30$).

- Para [[A-B testing]]:
$$
t = \dfrac{\bar{x}_{1}-\bar{x}_{2}}{\sqrt{ \dfrac{s^{2}_{1}}{n_{1}}+\dfrac{s^{2}_{2}}{n_{2}} }}
$$
- $\bar{x}_{i}$: sample mean
- $s_{i}$: sample std
- $n_{i}$: sample size


En otras palabras, te ayuda a estimar la probabilidad de que una muestra provenga de una población con una media y una desviación estándar determinadas, especialmente cuando no tienes toda la información sobre la población.

![[Pasted image 20240830002457.png]]

- [>] [[Z-score]]