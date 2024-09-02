---
created: 2024-08-31
tags:
  - Matematicas/estadistica
aliases:
  - a-b testing
  - two-sample
---
# A-B testing
Se comparan dos grupos independientes entre si.

## Componentes comunes
### Diseno de la prueba
- **Experimento controlado**: Asignar aleatoriamente sujetetos a los grupos A y B para minimizar el sesgo

- **Grupo de control**: Sirve como linea de base para comparacion y no recibe tratamiento
- **Grupo de tratamiento**: Recibe el tratamiento, que es el camio que se esta probando

### Muestreo
- **Selección aleatoria:** Asegura una muestra representativa de la población, lo que hace que los resultados sean generalizables.
- **Tamaño de la muestra:** Una muestra más grande proporciona resultados más precisos y significativos, pero requiere más recursos.
### Testeo de hipotesis
- **Formulación de hipótesis:** Se establece una hipótesis nula (sin diferencia entre los grupos) y una hipótesis alternativa (existe una diferencia).
- **Prueba t de dos muestras:** Se utiliza para determinar si la diferencia observada en la métrica clave entre los grupos A y B es estadísticamente significativa o se debe al azar.
- **Conclusión:** Con base en los resultados de la prueba, se rechaza o no se rechaza la hipótesis nula, lo que lleva a una decisión sobre la implementación del cambio probado.


- [>] [[Test estadistico]]
[[Pruebas de dos colas]]



## Ejemplos
### Media

|             | Version A | Version B |
| ----------- | --------- | --------- |
| Sample size | 40        | 38        |
| Sample mean | 300 seg   | 305 seg   |
| Sample std  | 18.5 seg  | 16.7 seg  |
#### Paso 1: Plantear las hipotesis
- $H_{0}: A = B$ (No hay una diferencia entre la version A y la version B)
- $H_{a}: A \neq B$ (Hay una diferencia entre la version A y la version B)
#### Paso 2: Elegir nivel de significacion
Por convencion se suele usar $\alpha = 0.05$. 
#### Paso 3: Encontrar el valor p
En este caso se esta haciendo un [[T-test]], por lo que:

$$
\begin{align}
& t = \dfrac{300-305}{\sqrt{ \dfrac{18.5^{2}}{38}+\dfrac{16.7^{2}}{40} }} \\ \\
& t = -1.2508
\end{align}
$$

Sobre la base estadistica de prueba, se calcula un P-value de:
$$
P = 0.2148 = 21.48\%
$$
#### Paso 4: Rechazar o no rechazar hipotesis nula
- Si [[P-value|p-value]] > [[Nivel de significancia|nivel de significancia]]: *no rechaza* la hipotesis nula

$$
\begin{align}
p > 0.05 \\
0.2148 > 0.05 \\
\end{align}
$$
El valor-p es de $21.48\%$, superior al $5\%$. La prueba indica que el nivel de significancia es menor y por tanto no se puede rechazar la hipotesis nula de que las diferencias entre A y B se deba a aleatoriedad.

### Proporciones

|                   | London office | Beijing office |
| ----------------- | ------------- | -------------- |
| sample size       | 50            | 50             |
| sample proportion | 67%           | 57%            |

#### Paso 1: Plantear las hipotesis
- **Null** : No existe diferencia en la *proporcion* de satisfaccion entre London y Beijing
	- $H_{0}: A = B$ (No hay una diferencia entre la version A y la version B)
- **Alternative** : Existe diferencia en la *proporcion* de satisfaccion entre London y Beijing
	- $H_{a}: A \neq B$ (Hay una diferencia entre la version A y la version B)
#### Paso 2: Elegir nivel de significacion
Por convencion se suele usar $\alpha = 0.05$. 
#### Paso 3: Encontrar el valor p
- [[Z-score|z-score]]: normal dist
- [[Pruebas de dos colas]]
$$
\begin{align}
& Z = \frac{0.67 - 0.57}{\sqrt{ 0.62 \cdot (1-0.62)\left( \dfrac{1}{50}+\dfrac{1}{50} \right) }} \\ \\
& Z = 1.03
\end{align}
$$
Se calcula un p-value:

$$
\text{p-value} = 0.303
$$
#### Paso 4: Rechazar o no rechazar hipotesis nula
- Si p-value > nivel de significancia: *no rechaza* la hipotesis nula

$$
\begin{align}
p > 0.05 \\
0.303 > 0.05 \\
\end{align}
$$

No se rechaza la hipotesis nula.
