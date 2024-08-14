---
created: 2024-06-18
tags:
  - Programacion
  - python
aliases:
  - plt0-utilidades
---
# PLT0-Utilidades

## Aplicar estilos

Es posible declarar variables con un diccionario para los estilos y llamarlos luego con un `**kwarg` como parametro en el grafico.

```python
sin_style = dict(linewidth=3, color='darkorange')
cos_style = dict(marker='o', markerfacecolor='limegreen', color='darkgreen')

ax.plot(x, sin, **sin_style)
ax.plot(x, cos, **cos_style)
```

Esto ayuda a poder aplicar el mismo *estilo* a mas graficos.