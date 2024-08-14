---
created: 2024-04-26
tags: 
aliases:
  - py4-string formating
---
# PY4-String formating

## Operador %

```python
>>> name = 'Pete'
>>> 'Hello %s' % name
# "Hello Pete"
```

## str.format

```python
>>> name = 'John'
>>> age = 20

>>> "Hello I'm {}, my age is {}".format(name, age)
# "Hello I'm John, my age is 20"

>>> "Hello I'm {0}, my age is {1}".format(name, age)
# "Hello I'm John, my age is 20"
```

## f-Strings

Una cadena literal formateada o cadena f es una cadena literal que lleva como prefijo `f` o `F`. Estas cadenas pueden contener campos de sustitución, que son expresiones delimitadas por llaves {}. Mientras que otros literales de cadena tienen siempre un valor constante, las cadenas formateadas son en realidad expresiones evaluadas en tiempo de ejecución.

```python
>>> name = 'Elizabeth'
>>> f'Hello {name}!'
# 'Hello Elizabeth!'
```

### f-Strings multilinea

```python
>>> name = 'Robert'
>>> messages = 12
>>> (
... f'Hi, {name}. '
... f'You have {messages} unread messages'
... )
# 'Hi, Robert. You have 12 unread messages'
```

### El especificado =

Esto imprimira la expresion y su valor

```python
>>> from datetime import datetime
>>> now = datetime.now().strftime("%b/%d/%Y - %H:%M:%S")
>>> f'date and time: {now=}'
# "date and time: now='Nov/14/2022 - 20:50:01'"
```

### Agregar espacios o caracteres

```python
>>> f"{name.upper() = :-^20}"
# 'name.upper() = -------ROBERT-------'
>>>
>>> f"{name.upper() = :^20}"
# 'name.upper() =        ROBERT       '
>>>
>>> f"{name.upper() = :20}"
# 'name.upper() = ROBERT              '
```

### Formatear digitos

Anadiendo separador de miles
```python
>>> a = 10000000
>>> f"{a:,}"
# '10,000,000'
```

redondeo

```python
>>> a = 3.1415926
>>> f"{a:.2f}"
# '3.14'
```

mostrar como porcentaje
```python
>>> a = 0.816562
>>> f"{a:.2%}"
# '81.66%'
```

### Tabla de formateo de numeros

| Número     | Formato   | Output    | descripción                                              |
| ---------- | --------- | --------- | -------------------------------------------------------- |
| 3.1415926  | `{:.2f}`  | 3.14      | Formato flotante 2 decimales                             |
| 3.1415926  | `{:+.2f}` | +3.14     | Formato flotante 2 decimales con signo                   |
| -1         | `{:+.2f}` | -1.00     | Formato flotante 2 decimales con signo                   |
| 2.71828    | `{:.0f}`  | 3         | Formato flotante sin decimales                           |
| 4          | `{:0>2d}` | 04        | Número de relleno con ceros (relleno izquierdo, ancho 2) |
| 4          | `{:x<4d}` | 4xxx      | Número de relleno con x (relleno derecho, ancho 4)       |
| 10         | `{:x<4d}` | 10xx      | Número de relleno con x (relleno derecho, ancho 4)       |
| 1000000    | `{:,}`    | 1.000.000 | Formato de número con separador de coma                  |
| 0,35       | `{:.2%}`  | 35,00%    | Porcentaje de formato                                    |
| 1000000000 | `{:.2e}`  | 1.00e+09  | Notación de exponente                                    |
| 11         | `{:11d}`  | 11        | Alineado a la derecha (predeterminado, ancho 10)         |
| 11         | `{:<11d}` | 11        | Alineado a la izquierda (ancho 10)                       |
| 11         | `{:^11d}` | 11        | Alineado al centro (ancho 10)                            |
## Template Strings

Un mecanismo mas simple y menos potente, pero recomendado cuando se manejan cadenas generadas por los usuarios. Debido a su reducida complejidad, las *template strings* son una opcion mas segura.                

```python
>>> from string import Template
>>> name = 'Elizabeth'
>>> t = Template('Hey $name!')
>>> t.substitute(name=name)
# 'Hey Elizabeth!'
```

