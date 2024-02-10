
![Conversión Temperaturas](https://0grados.com/admin/wp-content/uploads/2018/02/FoRMULAS-DE-CONVERSIoN-DE-TEMPERATURA.jpg)

# Conversión de Temperaturas

¿Estás listo para poner en práctica algunas de estas herramientas que has aprendido? Hasta ahora, has aprendido mucho sobre variables y operadores. Ahora es el momento de ver qué se puede hacer con todo eso.

## Conversión de Temperatura
Hemos hablado sobre las computadoras y su competencia matemática, y ahora veremos parte de eso en acción. Estados Unidos es avanzado en tantos aspectos, pero cuando se trata de sistemas de medición, la nación inexplicablemente vive en el pasado. Los países más sabios del mundo han abandonado las unidades imperiales y han pasado al sistema métrico. De manera similar, Estados Unidos sigue utilizando desafiante la escala Fahrenheit para la medición de la temperatura.

> **Nota:** La comunidad científica estadounidense ha dejado atrás a los profanos en este sentido. Solo es el público en general quien hace uso regular de estos sistemas arcaicos.

Debido a que hay tantas escalas diferentes para representar las mismas cosas, a menudo es necesario convertir valores entre ellas. Para convertir temperaturas de Fahrenheit a Celsius y viceversa, se pueden usar estas fórmulas complementarias:

```dart
F = 1.8C + 32
C = (F – 32) / 1.8
```

Deberás convertir estas fórmulas matemáticas a sintaxis de Dart antes de que la computadora pueda realizar los cálculos. (`1.8C` implica multiplicación en matemáticas, pero Dart no lo ve así).

```dart
void main() {
  // valores de entrada
  double f = 32;
  double c = 100;
  
  // convertir
  double convertedC = (f - 32) / 1.8;
  double convertedF = 1.8 * c + 32;
  
  // salida
  print("$f grados Fahrenheit son $convertedC grados Celsius.");
  print("$c grados Celsius son $convertedF grados Fahrenheit.");
}
```

### Análisis
En este caso, es mejor declarar las variables como tipo `double` ya que los valores de entrada y convertidos pueden contener decimales.

El programa sería algo más útil si los valores de `f` y `c` vinieran del usuario, pero aceptar la entrada del usuario se abordará en una lección posterior.

Observa que en la primera expresión de conversión, `(f - 32) / 1.8`, se utilizan paréntesis para asegurar que los cálculos se realicen en el orden correcto. Las operaciones multiplicativas, como la división, normalmente tienen precedencia sobre las operaciones aditivas, como la resta. Esto no es necesario en la otra conversión.

## Puntos Extra
Juega con diferentes valores de entrada para obtener diferentes resultados. Para práctica adicional, intenta agregar otro tipo de conversión, quizás a la escala Kelvin.