---
created: 2024-08-30
tags:
  - Matematicas/estadistica
aliases:
  - errores en la toma de decisiones estadistica
---
# Errores en la toma de decisiones estadistica

Cuando se decide rechazar o no rechazar la [[Hipotesis nula|hipotesis nula]] hay cuatro resultados posibles:

1. Rechazar la hipotesis nula cuando en realidad es cierta ([[Falso positivo]])
2. Rechazar la hipotesis nula cuando realidad es falsa :LiCheck:
3. No rechazar la hipotesis nula cuando en realidad es verdadera :LiCheck:
4. No rechazar la hipotesis nula cuando en realidad es falsa ([[Falso negativo]])

![[Pasted image 20240830211237.png]]

## Reducir riesgos
### Tipo I
Para reducir el riesgo de un **falso positivo** se puede reducir el nivel de signifiancia $\alpha$. 

| Nivel de significación (α) | Probabilidad de cometer un error de tipo I |
| -------------------------- | ------------------------------------------ |
| 0.05                       | 5%                                         |
| 0.01                       | 1%                                         |
### Tipo II
Sin embargo, reducir el riesgo significa que es mas probable cometer un **falso negativo**. Dicha probabilidad esta relacionado con la potencia de una prueba de hipotesis $$\text{potencia} = 1-\beta$$
- [[Potencia]] es la probabilidad de que una prueba pueda detectar correctamente un efecto real cuando lo hay.

Para reducir el riesgo se puede asegurar que la prueba tiene suficiente potencia. 

```ad-note
En el trabajo de datos la potencia suele fijarse en $0.8$ u $80\%$

```

Para aumentar la potencia se puede aumentar el tamano de la muestra o el nivel de significacion.

## Riesgos potenciales
### Tipo I
Puede llevar a aplicar cambios que son innecesarios e ineficaces.

### Tipo II
Puede hacer que se pierdan oportunidades de cambio positivo e innovacion.