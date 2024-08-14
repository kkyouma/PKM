---
created: 2024-07-24
tags: 
aliases:
  - python datetime
---
# Python DateTime
El modulo integrado `DateTime` de Python se usa para formatear datos al tipo de dato `datetime`.

- Pandas clase datetime: En pandas se puede usar `pd.to_datetime(df[column])` para convertir toda una columna. Y luego `dt.year`,`dt.month` y `dt.day` 

| **Code** | **Format**                                 | **Example**                                                           |
| -------- | ------------------------------------------ | --------------------------------------------------------------------- |
| **%a**   | Abbreviated workday                        | Sun                                                                   |
| **%A**   | Weekday                                    | Sunday                                                                |
| **%b**   | Abbreviated month                          | Jan                                                                   |
| **%B**   | Month name                                 | January                                                               |
| **%c**   | Date and time                              | Sun Jan 1 00:00:00 2021                                               |
| **%d**   | Day (leading zeros)                        | 01 to 31                                                              |
| **%H**   | 24 hours                                   | 00 to 23                                                              |
| **%I**   | 12 hours                                   | 01 to 12                                                              |
| **%j**   | Day of year                                | 001 to 366                                                            |
| **%m**   | Month                                      | 01 to 12                                                              |
| **%M**   | Minute                                     | 00 to 59                                                              |
| **%p**   | AM or PM                                   | AM/PM                                                                 |
| **%S**   | Seconds                                    | 00 to 61                                                              |
| **%U**   | Week number (Sun)                          | 00 to 53                                                              |
| **%W**   | Week number (Mon)                          | 00 to 53                                                              |
| **%w**   | Weekday                                    | 0 to 6                                                                |
| **%x**   | Locale’s appropriate date representation   | 08/16/88 (None);<br><br>08/16/1988 (en_US);<br><br>16.08.1988 (de_DE) |
| **%X**   | A locale’s appropriate time representation | 21:30:00 (en_US);<br><br>21:30:00 (de_DE)                             |
| **%y**   | Year without century                       | 00 to 99                                                              |
| **%Y**   | Year                                       | 2022                                                                  |
| **%z**   | Offset                                     | +0900                                                                 |
| **%Z**   | Time zone                                  | EDT/JST/WET etc (GMT)                                                 |
|          |                                            |                                                                       |

### Funciones Importantes de la Biblioteca `datetime`

1. **Convertir cadena a objeto `datetime`:**
   ```python
   datetime.strptime("25/11/2022", "%d/%m/%Y")
   ```
   Ejemplo:
   - Entrada: `"25/11/2022"`
   - Salida: `DateTime: 2022-11-25 00:00:00`

2. **Convertir objeto `datetime` a cadena:**
   ```python
   datetime.strftime(dt_object, "%d/%m/%Y")
   ```
   Ejemplo:
   - Entrada: `DateTime: 2022-11-25 00:00:00`
   - Salida: `"25/11/2022"`

3. **Obtener timestamp UTC desde cadena:**
   ```python
   datetime.strptime("25/11/2022", "%d/%m/%Y").timestamp()
   ```
   Ejemplo:
   - Entrada: `"25/11/2022"`
   - Salida: `Timestamp: 1671990000.0`

4. **Formatear objeto `datetime` a cadena específica:**
   ```python
   datetime.strptime("25/11/2022", "%d/%m/%Y").strftime("%Y-%m-%d")
   ```
   Ejemplo:
   - Entrada: `"25/11/2022"`
   - Salida: `"2022-11-25"`

5. **Convertir timestamp UTC a objeto `datetime`:**
   ```python
   datetime.fromtimestamp(1617836400.0)
   ```
   Ejemplo:
   - Entrada: `Timestamp: 1617836400.0`
   - Salida: `DateTime: 2021-04-07 23:00:00`

6. **Formatear timestamp UTC a cadena de fecha:**
   ```python
   datetime.fromtimestamp(1617836400.0).strftime("%d/%m/%Y")
   ```
   Ejemplo:
   - Entrada: `Timestamp: 1617836400.0`
   - Salida: `"07/04/2021"`

7. **Convertir y ajustar zona horaria:**
   ```python
   datetime.strptime("25-11-2022 09:34:00-0700", "%d-%m-%Y %H:%M:%S%z").astimezone(timezone('Asia/Tokyo'))
   ```
   Ejemplo:
   - Entrada: `"25-11-2022 09:34:00-0700"`
   - Salida: `DateTime: 2022-11-26 01:34:00 JST`

8. **Convertir hora en formato de 24 horas a 12 horas:**
   ```python
   datetime.strptime("20:00", "%H:%M").strftime("%I:%M %p")
   ```
   Ejemplo:
   - Entrada: `"20:00"`
   - Salida: `"08:00 PM"`

9. **Convertir hora en formato de 12 horas a 24 horas:**
   ```python
   datetime.strptime("08:00 PM", "%I:%M %p").strftime("%H:%M")
   ```
   Ejemplo:
   - Entrada: `"08:00 PM"`
   - Salida: `"20:00"`

