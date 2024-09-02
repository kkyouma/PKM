---
created: 2024-08-31
tags:
  - Matematicas/estadistica
aliases:
  - diseno experimental
---
# Diseno experimental

## Pasos clave
1. Definir las variables
	1. Variables independientes: El investigaror cambia variables independientes para determinar como afecta a la variable dependiente
	2. Variables dependientes: 
2. Formular la hipotesis
3. Asignar los sujetos de la prueba a los grupos de tratamiento y control

### Definir variables
#### Variable independiente
- Su variable independiente es el medicamento, la causa que desea investigar.

#### Variable dependiente
- Su variable dependiente es el tiempo de recuperación, el efecto que desea medir.

### Formular hipotesis
- Su hipótesis nula (H0) es que el medicamento no tiene ningún efecto.
- La hipótesis alternativa (Ha) es que el medicamento es eficaz.

### Asignacion de los sujetos de ensayo
#### Grupos de tratamiento y de control

Los experimentos como los ensayos clínicos y las Pruebas A/B son experimentos controlados. En un **experimento** controlado, los sujetos de ensayo se asignan a un grupo de tratamiento y a un grupo de control. El **tratamiento** es el nuevo cambio que se prueba en el experimento. El grupo de **tratamiento** está expuesto al tratamiento. El grupo de **control** no está expuesto al tratamiento. La diferencia en los valores métricos entre los dos grupos mide el efecto del tratamiento en los sujetos de ensayo.

En el ensayo clínico, el tratamiento es el medicamento que se administra a los sujetos del grupo de tratamiento. Los sujetos del grupo de control no reciben el medicamento. Imagine que sus resultados muestran que el tiempo medio de recuperación es menor en el grupo de tratamiento (6,2 días) que en el grupo de control (7,5 días). La diferencia entre los dos grupos, 7,5 - 6,2 = 1,3 días, mide el impacto del tratamiento. En otras palabras, el medicamento disminuye el tiempo medio de recuperación en 1,3 días.

**Nota**: Después de que un profesional de los datos diseñe y ejecute su experimento, utiliza pruebas estadísticas para analizar los resultados. Como siguiente paso, podría realizar una prueba t de dos muestras para determinar si la diferencia observada en el tiempo de recuperación es estadísticamente significativa o se debe al azar.

Lo ideal es que la exposición al tratamiento sea la única diferencia significativa entre los dos grupos. Este diseño permite a los investigadores controlar otros factores que podrían influir en los resultados de la prueba y extraer conclusiones causales sobre el efecto del tratamiento.

Por ejemplo, imagine que los sujetos del grupo de tratamiento tienen una dieta mucho más sana que los sujetos del grupo de control. Cualquier disminución observada en el tiempo de recuperación del grupo de tratamiento podría deberse a su dieta más sana, y no al medicamento. En este caso, no se puede afirmar con seguridad que el medicamento por sí solo sea la _causa_ de un tiempo de recuperación más rápido.

#### Aleatorización

Normalmente, los profesionales de datos asignan aleatoriamente los sujetos de prueba a los grupos de tratamiento y control. La aleatorización ayuda a controlar el efecto de otros factores en el resultado de un experimento. Dos métodos habituales para asignar sujetos a los grupos de tratamiento y control son el diseño completamente aleatorizado y el diseño de bloques aleatorizados.

En un diseño completamente **aleatorizado**, los sujetos de ensayo se asignan a los grupos de tratamiento y control mediante un proceso aleatorio. Por ejemplo, en un ensayo clínico, se puede utilizar un programa informático para etiquetar a cada sujeto con un número y, a continuación, seleccionar aleatoriamente números para cada grupo.

A veces, sin embargo, un diseño completamente aleatorizado puede no ser el enfoque más eficaz. Al diseñar un experimento, los profesionales de los datos deben tener en cuenta los **factores perturbadores**. Se trata de factores que pueden afectar al resultado de un experimento, pero que no son de interés primordial para el investigador.

Los investigadores pueden utilizar un **diseño de bloques aleatorizados** para minimizar el impacto de los factores perturbadores conocidos. El **bloqueo** consiste en organizar a los sujetos de la prueba en grupos, o bloques, similares entre sí. En un diseño de bloques, primero se dividen los sujetos en bloques y luego se asignan aleatoriamente los sujetos de cada bloque a los grupos de tratamiento y control.

Por ejemplo, supongamos que sabemos que la edad es un factor importante en el tiempo de recuperación de un resfriado común. En concreto, sabe que las personas menores de 35 años tienden a recuperarse antes que las mayores. En este escenario, la edad es un factor molesto porque podría afectar a los resultados de su experimento. Por ejemplo, en un ensayo clínico con un diseño completamente aleatorizado y un tamaño de muestra más pequeño, podría obtener al azar una gran proporción de jóvenes en el grupo de tratamiento. Esto hará más difícil determinar si cualquier disminución observada en el tiempo de recuperación se debe al tratamiento (medicamento) o al factor perturbador (edad).

En este caso, bloquear el factor edad es una forma más eficaz de diseñar el experimento. En primer lugar, se dividen los sujetos de la prueba en bloques en función de la edad, como 21-35, 36-50 y 51-65. A continuación, se asignan aleatoriamente los sujetos de la prueba a los grupos de edad de 21-35, 36-50 y 51-65. A continuación, asigne aleatoriamente los sujetos de cada bloque a los grupos de tratamiento y control. De este modo, si hay una diferencia significativa en el tiempo de recuperación dentro de un bloque específico, puede estar más seguro de que este resultado se debe al tratamiento (medicamento) y no al factor perturbador (edad).