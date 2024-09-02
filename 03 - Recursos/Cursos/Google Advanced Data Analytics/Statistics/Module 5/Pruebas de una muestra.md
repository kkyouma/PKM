---
created: 2024-08-31
tags:
  - Matematicas/estadistica
aliases:
  - pruebas de una muestra
---
# Pruebas de una muestra
- [>] [[A-B testing]]
## Ejemplo
### Paso 1: Plantear las hipotesis
- $H_{0}: \mu = 8$ (la duración media de la batería de todos los portátiles rediseñados es *igual* a 8,5 horas)
- $H_{a}: \mu > 8,5$ (la duración media de la batería de todos los portátiles rediseñados es *superior* 8,5 horas)
### Paso 2: Elegir nivel de significacion
Por convencion se suele usar $\alpha = 0.05$. 

### Paso 3: Encontrar el valor p

[[Z-score]]: Para un Z-test
[[T-score]]: Para un T-test

En este caso se esta haciendo un Z-test, por lo que:

$$
Z = 2.53
$$
Sobre la base estadistica de prueba, se calcula un P-value de:
$$
P = 0.0057
$$
### Paso 4: Rechazar o no rechazar hipotesis nula
- Si [[P-value|p-value]] < [[Nivel de significancia|nivel de significancia]]: *rechazar* la hipotesis nula
- Si [[P-value|p-value]] > [[Nivel de significancia|nivel de significancia]]: *no rechaza* la hipotesis nula

$$
\begin{align}
p < 0.05 \\
0.0057 < 0.05 \\
\end{align}
$$
El valor-p es de $0.57\%$, inferior al $5\%$. Su prueba proporciona pruebas suficientes para concluir que la duracion media de todos los portatiles redisenados ha aumentado de $8,5$ horas. Rechazar la hipotesis nula. Determina que los resultados son estadisticamente significativos.