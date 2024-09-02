---
created: 2024-08-29
tags:
  - Matematicas/estadistica
aliases:
  - intervalo de confianza
  - Confidence interval
  - CI
  - iC
---
# Intervalo de confianza
El **Intervalo de confianza** es un rango que estimamos a partir de datos muestrales y dentro del cual esperamos que se encuentre el parámetro real de la población en un cierto porcentaje de las muestras repetidas.

Se puede esperar que el $95\%$ de los intervalos aleatores que se generan capturen el parametro de la poblacion (*Population mean*).

![[Pasted image 20240829224949.png]]

```ad-example
collapse:true
Imagina que quieres estimar el peso medio de una población de 10.000 pingüinos. En lugar de pesar todos y cada uno de los pingüinos, seleccionas una muestra de 100 pingüinos. El peso medio de la muestra es de $30$ libras. Basándote en los datos de tu muestra, construyes un intervalo de confianza del $95\%$ entre $28$ libras y $32$ libras.

$$
\begin{align}
30+2=32 \\
30-2=28 \\ \\

\text{CI}: [20, 32]
\end{align}
$$

Considerando un margen de error de $2$
```

```ad-missing
collapse:true
Algunas mal interpretaciones del intervalod de confianza:

1. El $95\%$ se refiere a la probabilidad de que la media de la población se encuentre dentro del intervalo construido.
2. El $95\%$ se refiere al porcentaje de valores de los datos que caen dentro del intervalo
3.  El $95\%$ se refiere al porcentaje de medias muestrales que caen dentro del intervalo.

```

## Pasos para construir un intervalo de confianza
1. Identificar una [[Estadistica muestral]] (proporcion o valor)
2. Escoger un [[Nivel de confianza|nivel de confianza]]
3. Encontrar el [[Margen de error|margen de error]]
4. Calcular el intervalo

```ad-example
1. Identificar una estadistica muestral: Proporcion ($0.55$)
2. Escoger un nivel de confianza: $95\%$
3. Encontrar el margen de error:
	1. Z-score para un nivel de confianza $95\%$
	   $$\text{z-score}(0.95) = 1.96  $$
	2. Error estandar de la proporcion:
		$$SE(\hat{p}) = \sqrt{ \frac{\hat{p}(1-\hat{p})}{n} } = \sqrt{ \frac{0.55(1-0.55)}{100} } = 0.05, \\[10pt]$$
	3. Margen de error:
	   $$\text{Margin of error} = \text{z-score} \cdot SE = 1.96 \cdot 0.05 = 0.098$$
4. Calcular el intervalo
	1. Lower limit: $0.55 - 0.098 = 0.452 \rightarrow 45.2\%$
	2. Upper limit: $0.55 + 0.098 = 0.648 \rightarrow 64.8\%$

```

```ad-note
Para muestras *grandes* se usa [[Z-score]], pero para muestras *pequenas* se usa [[T-score]]

```



## Python
Para calcular el intervalo de confianza se usa modulo `stats` de `scipy`

- `stats.norm.interval(alpha=confidence_level, loc=sample_mean, scale=standard_error)`

```python
stats.norm.interval(confidence=0.95, loc=12, scale=0.898)

(10.359751399400034, 13.882672843024208)
```



