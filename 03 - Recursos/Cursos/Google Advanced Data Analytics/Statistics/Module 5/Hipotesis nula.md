---
created: 2024-08-30
tags:
  - Matematicas/estadistica
aliases:
  - null hypothesis
  - hipotesis nula
---
# Hipótesis nula
La **hipótesis nula** es una sentencia en la que se asume que sera verdadera hasta que haya evidencia convincente de lo contrario. La hipótesis nula suele suponer que no hay ningún efecto en la población y que los datos observados se producen por casualidad.

- Se simboliza con $$H_{0}$$
- Se suele incluir con símbolos de igualdad
- Se suelen escribir como "ningún efecto", "ninguna diferencia", "ninguna relacion" o "ningun cambio"
Normalmente la hipotesis nula representa el *status quo*, o el estado actual de las cosas. La hipotesis nula supone que el estatus quo no ha cambiado. La hipotesis alternativa sugiera una posibilidad o explicacion diferente.
## Decision
En algun punto se tendra que decidir si **rechazar** o **fallar al rechazar** la hipotesis nula.

- Si [[P-value|p-value]] < [[Nivel de significancia|nivel de significancia]]: *rechazar* la hipotesis nula
- Si [[P-value|p-value]] > [[Nivel de significancia|nivel de significancia]]: *no se rechaza* la hipotesis nula

- [>] [[Hipotesis alternativa]]

```ad-example
title: Ejemplo 1
Una empresa de alimentos ecológicos es famosa por su granola. La empresa afirma que cada bolsa que produce contiene 300 gramos de granola, ni más ni menos. Para comprobar esta afirmación, un experto en control de calidad mide el peso de una muestra aleatoria de 40 bolsas.

$H0: μ = 300$ (el peso medio de todas las bolsas de granola producidas es igual a 300 gramos)

$Ha: μ ≠ 300$ (el peso medio de todas las bolsas de granola producidas no es igual a 300 gramos)

```

```ad-example
title: Ejemplo 2

Una empresa afirma que al menos el 80% de sus empleados están satisfechos con su trabajo. Sin embargo, un investigador independiente cree que menos del 80% de los empleados están satisfechos con su trabajo. Para comprobar esta afirmación, el investigador encuesta a una muestra aleatoria de 100 empleados.

$H_{0}: p ≥ 0,80$ (la proporción de todos los empleados que están satisfechos con su trabajo es igual o superior al 80%)

$H_{a}: p < 0,80$ (la proporción de todos los empleados que están satisfechos con su trabajo es inferior al 80%)

```
