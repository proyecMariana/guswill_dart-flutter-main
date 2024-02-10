# Variables

Las variables son un bloque básico de la mayoría de los programas modernos. En resumen, una variable es un alias de una ubicación de memoria de la computadora, en la que se almacenará algo de interés. Lo que se almacena allí se dice que es el valor de la variable. Si has estudiado los conceptos básicos del álgebra, es posible que recuerdes las variables principalmente como sustitutos de una sola letra para números que te ayudaron a conceptualizar y resolver ecuaciones complejas. Las variables de Dart son similares pero no exactamente iguales, ya que son capaces de sustituir todo tipo de valores: números, cadenas de caracteres o incluso estructuras más complejas que representan personas, transacciones económicas o ubicaciones geográficas.

## No Hay Nada Allí
Para empezar de manera simple, ingresa el siguiente programa en el editor y ejecútalo:

```dart
void main() {
  var x;
  print(x);
}
```

La primera línea de `main()` declara una variable llamada `x` usando la palabra clave `var` de Dart. Cuando se ejecuta esta línea, Dart reserva un lugar en la memoria para un valor, y más tarde puedes hacer uso de ese valor por su nombre, `x`. En este caso, envías el valor a la función `print()` para verlo impreso en la consola del sistema.

Las variables declaradas con la palabra clave `var` en Dart inicialmente reciben el valor especial de `null`. Esto significa que la variable no está inicializada. No tiene ningún valor. Incluso 0 (cero) sería un valor, pero `null` realmente es, en términos de programación, _nada_. Es por eso que ves `null` en la consola cuando imprimes el valor de `x`.

Puede que hayas notado que el analizador de código de Dart ha subrayado `x`, y hay un mensaje de advertencia adjunto: "Preferir tipificar variables y campos no inicializados". Abordaremos eso en la siguiente sección convirtiendo la variable no inicializada en una inicializada. La tipificación de variables se discutirá más adelante en la próxima lección.

## Inicializar
Como `null` no es un valor muy útil para tu variable, intenta inicializarlo con un valor numérico, así:

```dart
void main() {
  var x = 5;
  print(x);
}
```

A diferencia de la clase de álgebra, el operador `=` en Dart no representa estrictamente la equivalencia. Se conoce como el operador de asignación, por lo que `x = 5` es una expresión que instruye a la computadora a asignar el valor `5` a una ubicación de memoria llamada `x`. Entonces, cuando imprimes `x`, el resultado es `5`.

Ahora que estás inicializando la variable `x` con un valor, el analizador de Dart puede *inferir* el tipo de la variable a partir del tipo del valor, en este caso un *entero* (un número entero). Dart utiliza la información del tipo de variable para ayudarte a evitar errores en tu código. En lecciones posteriores, aprenderás a tipificar explícitamente tus variables para declarar mejor tus intenciones.

## Imprimir "x"
¿Qué pasa si en realidad estuvieras intentando imprimir la letra X en la pantalla? Podrías hacerlo de esta manera:

```dart
void main() {
  var x = 5;
  print("x");
}
```

Con comillas alrededor de la X, la computadora ahora la interpretará como el carácter X, en lugar de buscar una variable con el nombre `x`. Esto significa que ahora estás creando una variable y asignándole el valor `5` inútilmente. El analizador se molestará con este código, informándote que has declarado una variable que no estás utilizando.

## No Computa
Intenta eliminar las comillas una vez más, y también elimina la línea que declara e inicializa la variable `x`:

```dart
void main() {
  print(x);
}
```

Con las comillas eliminadas, Dart cree que estás haciendo referencia a una variable llamada `x`, y diligentemente la busca para intentar imprimir su valor. Rápidamente se da cuenta de que nunca has declarado tal variable, y te lo informa amablemente con un mensaje de error. No puedes ejecutar correctamente un código que tenga errores.

## Solo Imprimir el Número
Ahora podrías estar pensando: "Si quiero imprimir un 5, ¿no podría hacerlo así?"

```dart
void main() {
  print(5);
}
```

¡Sí! Esto también funcionaría, pero de una manera ligeramente diferente, que se discutirá más adelante:

```dart
void main() {
  print("5");
}
```

## ¿Qué Sigue?
En las próximas lecciones, verás el punto de utilizar variables en primer lugar. Por ahora, solo toma mi palabra de que el concepto es fundamental para hacer que una computadora haga casi cualquier cosa.

> **Nota:** Esto se complica más adelante, pero por ahora, debes asumir que Dart lee el código de la misma manera que tú: de arriba hacia abajo y de izquierda a derecha. Así que la primera línea de código se ejecuta primero, la segunda después, y así sucesivamente, y cada línea se lee y se ejecuta comenzando desde la izquierda y avanzando hacia la derecha. Obviamente, esto asume que provienes de una cultura occidental.