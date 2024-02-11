# Operadores

El término "operador" proviene de las matemáticas, pero en un lenguaje de programación, su significado es ligeramente diferente. En matemáticas, un operador es simbólico y abstracto. En Dart, los operadores instruyen a la computadora a realizar operaciones sobre operandos. Un operando es cualquier valor sobre el cual se realizará una operación.

## Tu asignación
Si has completado las lecciones anteriores , ya has estado utilizando uno de los operadores de Dart: el operador de asignación, o `=`. Como ya se discutió, ese símbolo significa equivalencia en matemáticas, pero Dart lo usa para asignar valores a una ubicación en la memoria de la computadora.

```dart
x = 5;
```

La expresión anterior instruye a Dart a tomar el valor `5` y almacenarlo en la ubicación `x`. Cuando se ejecuta esa línea de código, eso es exactamente lo que hace Dart.

## Sumémoslo

```dart
5 + 5;
```

Esa línea instruye a la computadora a sumar los dos operandos, produciendo la respuesta, `10`.

Pruébalo:

```dart
void main() {
  5 + 5;
}
```

Este es un programa válido, y si se ejecuta, se generará una respuesta, pero como no has instruido a la computadora a imprimir nada en la consola, nunca ves el resultado.

```dart
void main() {
  print(5 + 5);
}
```

¡Mejor! Ahora ves que se hizo la operación matemática y se muestra la respuesta. Utilizado en este contexto, `+` es un operador aritmético. Es importante tener en cuenta, sin embargo, que el contexto es clave. Combinar `+` con operandos numéricos le indica a Dart que realice la operación de suma familiar. Con operandos de otro tipo, el operador puede funcionar de manera diferente.

### ¿Qué hay de las cadenas?

```dart
void main() {
  print("Juan" + "Pérez");
}
```

Este código puede parecerte un poco extraño si esperas que `+` signifique adición, pero recuerda que incluso en inglés escrito, este tipo de símbolos pueden adquirir diferentes significados en nuevos contextos:

![Ned + Trudy](https://i.imgur.com/kkPKfpe.png)

En el árbol, el símbolo pretende representar la palabra "y", o posiblemente un concepto más abstracto, como sugerir que las vidas de Ned y Trudy están unidas. El punto es que "Juan + Pérez" no te invita a sumar el valor de "Juan" al valor de "Pérez" en un sentido matemático. Sabes por el contexto que el significado es diferente aquí.

Ejecutar el último fragmento de código producirá la siguiente salida:

```
JuanPérez
```

## Mejor con Espacios
¿Qué ha sucedido aquí? Con operandos `String`, el operador `+` _concatena_ los valores, produciendo una nueva cadena que contiene todos los caracteres. La segunda cadena se añade a la primera. Por supuesto, es un poco incómodo que los nombres y apellidos de este hombre se hayan concatenado sin un espacio, así que adelante y arreglalo:

```dart
void main() {
  print("Juan " + "Pérez");
  print("Juan" + " Pérez");
  print("Juan" + " " + "Pérez");
}
```

Se muestran aquí tres de las muchas soluciones posibles al problema. Podrías añadir el espacio solo en la primera o segunda cadena, o podrías usar dos operadores `+` para concatenar tres operandos `String`, uno de los cuales contiene solo un espacio.

Hay varias otras formas de hacerlo, pero quería señalar aquí que las soluciones de programación son muchas y variadas. Cualquier solución que produzca la salida deseada es "correcta", pero recuerda que cada solución cae en algún lugar en un espectro subjetivo de elegancia.

## Haz un Comentario
Antes de pasar a más operadores, quiero interrumpir con un concepto que nos ayudará a avanzar. Pruébalo con el siguiente código:

```dart
void main() {
  print("Juan" + " " + "Pérez");  // concatenación
}
```

Al ejecutar este código, se imprimirá `Juan Pérez`, como se esperaba. Cuando Dart encuentra la sintaxis de doble barra (`//`), ignora todo desde allí hasta el próximo salto de línea. Esto se conoce como un _comentario_. Los comentarios son útiles para documentar secciones de código para humanos. Se eliminan del código antes de la ejecución.

## Aritmética
Ahora, algunos operadores aritméticos más:

```dart
void main() {
  print(5 + 7);          // adición
  print(10 - 8);         // sustracción
  print(8 * 8);          // multiplicación
  print(10 / 5);         // división
}
```

Estos operadores hacen exactamente lo que esperarías. Comprueba las respuestas. Adelante. Resulta que las computadoras son bastante buenas en matemáticas.

## Orden de Operaciones
Afortunadamente, las reglas de precedencia de los operadores de Dart casi coinciden con lo que aprendiste en la clase de matemáticas. Todo lo que esté entre paréntesis se evalúa primero, y dentro o fuera de los paréntesis, las operaciones multiplicativas (`*`, `/`) se resuelven, seguidas de las operaciones aditivas (`+`, `-`). Cuando dos operadores tienen la misma precedencia, se evalúan en orden de izquierda a derecha.

```dart
void main() {
  print((5 * 5) + 5);    // 30
  print(5 * (5 + 5));    // 50
  print(7 - 4 / 2);      // 5
  print(6 * 2 + 4);      // 16
}
```

## Usa las Variables
Si bien ocasionalmente puedes hacer algunos cálculos con literales numéricos, como los del fragmento de código anterior, es mucho más común hacerlo con variables:

```dart
void main() {
  int x = 7;
  int y = 5;
  int producto = x * y;
  
  print(producto);
}
```

Aquí, los valores almacenados en las ubicaciones `x` e `y` se multiplican, y la respuesta se almacena en `producto`. Verificas el valor de `producto` con la función `print()`.

## Uno Más o Menos
Ahora que las variables están de vuelta en escena, puedes ser presentado a un par de operadores que son comunes en los lenguajes de programación, pero que nunca viste en tu libro de matemáticas. Otra cosa en la que las computadoras son excelentes es contando, y esto es algo que les pedirás que hagan tan a menudo que hay operadores dedicados para la tarea.

```dart
void main() {
  int x = 0;
  print(x);
  
  x++;
  print(x);
  
  x--;
  print(x);
}
```

Este código declarará una nueva variable entera llamada `x`, la inicializará en `0`, luego imprimirá el valor en la consola. Después, usarás el operador de incremento (`++`) para sumar 1 a `x`, luego imprimirás el valor nuevamente. Por último, usarás el operador de decremento (`--`) para restar 1 de `x`, lo que llevará su valor de vuelta a `0`.

### Comprensión Incremental
Las siguientes dos líneas de código son equivalentes:

```dart
x++;

x = x + 1;
```

La segunda declaración de código podría verse un poco extraña para alguien con formación en matemáticas pero ninguna en programación. ¿Cómo puede `x` ser igual a `x + 1`? Si `x` tiene el valor `5`, ¿esta cosa está tratando de decir que `5 = 5 + 1`?

Por supuesto, no está diciendo eso en absoluto. Debes recordar que `=` no se utiliza para la igualdad. Es el operador de asignación, solo otro operador que actúa sobre operandos, pero esta vez con una precedencia muy baja. Cuando Dart comienza a ejecutar esa declaración, primero toma el valor de `x` y lo suma en 1, luego asigna el resultado de la suma a `x`, sobrescribiendo cualquier valor que estuviera allí antes. Sucede de esta manera porque los operadores aditivos tienen precedencia sobre los operadores de asignación. La expresión `x++` es una abreviatura sintáctica de `x = x + 1`.

## Los Operadores
Aquí están los operadores discutidos hasta ahora, en orden de precedencia:

<table>
  <tr>
    <th>Operadores</th>
    <th>Descripción</th>
  </tr>
  <tr>
    <td>++ &nbsp;&nbsp;&dash;&dash;</td>
    <td>

Incrementa o decrementa el valor en 1</td>
  </tr>
  <tr>
    <td>* &nbsp;&nbsp;/</td>
    <td>Multiplicativo (multiplicar o dividir)</td>
  </tr>
  <tr>
    <td>+ &nbsp;&nbsp;-</td>
    <td>Aditivo (sumar o restar)</td>
  </tr>
  <tr>
    <td>=</td>
    <td>Asignación</td>
  </tr>
</table>
