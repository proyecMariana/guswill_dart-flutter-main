# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

## Valores de Retorno de Funciones

En este punto, tienes funciones que pueden tomar entrada, pero tu viaje a través del mundo mágico de las funciones de Dart no estará completo hasta que también puedas producir salida con ellas. Cuando colocas la palabra clave `void` al principio de la definición de una función, estás diciendo que la función no producirá ninguna salida útil; no devolverá un valor de consecuencia. Es posible declarar un tipo distinto de `void` como el tipo de retorno de tu función. Compara estas dos versiones de una función `sum()`:

```dart
void sum(int a, int b) {
  int total = a + b;
  print(total);
}

int sum(int a, int b) {
  int total = a + b;
  return total;
}
```

En ambas versiones, primero declaras una variable entera llamada `total` y le asignas el resultado de sumar los valores de `a` y `b`. Después, la primera versión imprime `total`, pero la segunda utiliza la palabra clave `return` para indicar que te gustaría enviar el valor de `total` al llamante de la función `sum()`. La nueva firma de la función incluye `int` en lugar del habitual `void`, lo que indica que se espera que `sum()` devuelva un valor entero como su acto final.

¿Por qué molestarse con la nueva versión? ¿No hacen lo mismo? Las funciones que devuelven valores son mucho más flexibles, y eso amplía su atractivo. El usuario de la primera función `sum()` obtiene una respuesta impresa en la consola cada vez. No se puede detener. Usar la segunda versión permite opciones. El resultado se puede imprimir, descartar, guardar para formar parte de un cálculo más grande o cualquier otra cosa que se desee.

Uso del Valor de Retorno de una Función
Dado que `sum()` no está imprimiendo el resultado del cálculo, ¿cómo hará tu programa uso de él? Así:

```dart
void main() {
  int respuesta = sum(5, 10);
  print(respuesta);
}

int sum(int a, int b) {
  int total = a + b;
  return total;
}
```

La primera línea de la función `main()` crea una variable entera llamada `respuesta` y le asigna el resultado de llamar a `sum(5, 10)`. La función `sum()` acepta los argumentos 5 y 10, los suma y luego devuelve la suma al llamante. Esencialmente, el código `sum(5, 10)` se resuelve al valor de retorno de `sum()`, y 15 se coloca en `respuesta`. Luego, el valor de `respuesta` se imprime en la consola.

La Brevedad es el Alma del Ingenio
Para ayudar a ilustrar los pasos de manera más clara, los ejemplos hasta ahora han creado algunas variables que no son estrictamente necesarias. El código podría escribirse de manera más concisa:

```dart
void main() {
  print(sum(5, 10));
}

int sum(int a, int b) {
  return a + b;
}
```

Este código produce exactamente la misma salida que antes, pero con menos líneas. Ya no estamos creando las variables `respuesta` o `total`, ya que no hay necesidad de guardar sus valores para futuras operaciones. La expresión `sum(5, 10)`, cuando se evalúa, aún se resuelve al entero 15, que se envía a la función `print()`. Si esa llamada a `print()` te parece un lío confuso de paréntesis, confía en mí, te acostumbrarás a medida que avance tu carrera como programador. Dicho esto, si prefieres mantener la forma larga para preservar la claridad, ciertamente no hay nada malo en eso.

La Increíble Función Reducida
A veces, usar más código es más claro, pero a veces es simplemente largo. Con funciones muy simples como `sum()`, Dart te permite reducir aún más la verbosidad:

```dart
int sum(int a, int b) => a + b;
```

Esto puede parecer un poco esotérico a primera vista, pero aguanta y lo desglosaremos pieza por pieza. Primero, tienes una firma de función típica: `int sum(int a, int b)`. Directamente después de la firma está la sintaxis de la flecha gruesa: `=>`. Después de la flecha, se te permite solo una expresión, en este caso `a + b`. El resultado de esa expresión será devuelto por la función de flecha gruesa. La palabra clave `return` está ausente pero implícita, y no hay necesidad de un corchete de apertura o cierre para delimitar el cuerpo de la función.

A medida que tu código se vuelva más complejo, la concisión puede convertirse en un activo. En este ejemplo, la ventaja puede no ser completamente obvia, pero a medida que abordes lecciones más avanzadas, verás que los diseñadores del lenguaje Dart incluyeron esta sintaxis por una buena razón.

Si pruebas el código en su última encarnación,

 deberías encontrar que funciona de manera idéntica a las formas anteriores:

```dart
void main() {
  print(sum(5, 10));
}

int sum(int a, int b) => a + b;
```

Revisando Calificaciones
En una lección anterior, usaste `if` y `else if` para determinar la calificación de un estudiante según una puntuación dada. Este es un excelente ejemplo de una característica que podría encapsularse fácilmente en una función:

```dart
void main() {
  print("Mi calificación: ${getGrade(81.5)}");
}

String getGrade(double score) {
  String calificacion;
  
  if (score >= 90) {
    calificacion = "A";
  } else if (score >= 80) {
    calificacion = "B";
  } else if (score >= 70) {
    calificacion = "C";
  } else if (score >= 60) {
    calificacion = "D";
  } else {
    calificacion = "F";
  }
  
  return calificacion;
}
```

Las funciones pueden devolver tipos distintos de `int`, y esta devuelve un `String`. Con tu calculadora de calificaciones siendo una función, puedes obtener fácilmente una letra de calificación para una puntuación repetidamente en todo un programa. Sin funciones, tendrías que escribir o copiar todo ese código cada vez que quisieras otra calificación. Dado que cualquier expresión Dart válida se puede interpolar en una cadena, es posible llamar a `getGrade()` convenientemente dentro del argumento de cadena de la función `print()`.

¡Refactorización FTW!
Los programadores pasan mucho tiempo refactorizando su (o el de otra persona) código. ¿Qué significa eso? A veces te das cuenta de que el código existente podría hacerse mejor. Tal vez aprendiste nuevas técnicas de codificación, o tal vez te familiarizaste más con tu dominio de problema. Es un buen hábito revisar regularmente el código antiguo y refactorizarlo. Esto podría ser tan simple como cambiar el nombre de una variable o función para representar mejor su papel, o tan involucrado como reorganizar o reescribir segmentos enteros para leer mejor o ejecutarse de manera más eficiente.

Ahora que tienes todos los conceptos básicos para escribir tus propias funciones, retrocede sobre lecciones anteriores para ver si algún código podría beneficiarse de una refactorización.


# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)