# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

# Listas

Para resolver problemas más complejos de manera eficiente, necesitaremos estructuras de datos más avanzadas. Esta lección introducirá un nuevo tipo de Dart, la Lista. Una lista es exactamente lo que suena: Es un montón de elementos almacenados secuencialmente. En la vida cotidiana, haces listas todo el tiempo. Listas de compras para recoger, listas de personas a llamar, listas de tareas por hacer, y así sucesivamente. A veces tus listas están numeradas, lo que facilita referirse directamente a cualquier elemento en la lista usando su posición en la lista ("¡He completado el elemento nº 7!"). Incluso podrías pensar en el tipo String de Dart como una forma especializada de lista, una que trata estrictamente con secuencias de caracteres individuales.

¿Qué tipo de información podrías recopilar en una lista dentro de un programa de computadora? En una aplicación de juego, el inventario de un personaje podría almacenarse como una lista. Para el comercio electrónico, el contenido del carrito de compras podría ser una lista. Un mazo de cartas podría ser modelado como una lista, con cada carta siendo un elemento de la lista. Incluso puede ser útil convertir un String en una Lista de caracteres para resolver ciertos tipos de problemas relacionados con cadenas.

**Manténlo Juntos**

Una lista puede tener cualquier longitud, y los elementos pueden agregarse y eliminarse según sea necesario. Esto hace que las listas sean mucho más flexibles que tratar de usar una colección de variables individuales:

```dart
void main() {
  int number1 = 5;
  int number2 = 7;
  int number3 = 10;

  // añadir 3 números
  int total = number1 + number2 + number3;

  print("Total: $total");
}
```

Este código funciona bien siempre y cuando quieras agregar exactamente tres números, pero no es muy flexible. Podrías estar escribiendo una aplicación de calculadora, y el usuario podría ingresar prácticamente cualquier cantidad de valores para sumar. Para esto, una lista funcionaría mejor:

```dart
void main() {
  List<int> numbers = [5, 7, 10];

  // añadir 3 números
  int total = numbers[0] + numbers[1] + numbers[2];

  print("Total: $total");
}
```

Esta vez, creamos una variable Lista llamada `numbers`. Puedes usar corchetes angulares junto con `List` para especificar un tipo para los elementos individuales de la lista, en este caso `<int>`. Una lista de Dart se denota por una secuencia delimitada por comas de valores encerrados dentro de corchetes. Al igual que con las cadenas, cada elemento de la lista puede ser accedido por índice, y el primer índice es 0. El valor en `numbers[0]` es 5, porque 5 es el primer elemento en esa lista.

Ahora que tienes una lista en lugar de variables individuales, es posible almacenar cualquier cantidad de valores para ser sumados allí. Sin embargo, el código de adición todavía está manejando exactamente tres valores. El verdadero poder de las listas se hace evidente cuando las combinas con bucles:

```dart
void main() {
  List<int> numbers = [5, 7, 10];

  // añadir todos los números
  int total = 0;
  for (int i = 0; i < numbers.length; i++) {
    total += numbers[i];
  }

  print("Total: $total");
}
```

En esta versión, usamos un bucle for para iterar sobre cada elemento en la lista. La primera vez que se ejecuta el bucle, agregaremos el valor en `numbers[0]` a `total`, porque `i` será 0. En la siguiente iteración, se accederá a `numbers[1]` y su valor, 7, se sumará al total en ejecución. Las listas tienen una propiedad de longitud que puedes usar para determinar cuántos elementos se almacenan actualmente dentro. Usando eso, puedes asegurarte de que tu bucle se ejecute el número correcto de veces. Tan pronto como `i` coincida con la longitud de la lista (3), el bucle dejará de ejecutarse.

Lancemos unos cuantos valores más en la lista para probar la flexibilidad, luego ejecuta el código nuevamente:

```dart
List<int> numbers = [5, 7, 10, 3, 19];
```

¡Como puedes ver, el bucle combinado con una lista puede sumar cualquier cantidad de valores juntos! Además, mantener todos los valores en una sola variable, `numbers`, es mucho más fácil de manejar que una tonelada de variables separadas. ¿Qué pasaría si tuvieras que almacenar 100 valores o más? ¿Puedes imaginar crear tantas variables individuales? Si ves a alguien hacer esto, ¡tírale la silla de inmediato y demuéstrale a todos que eso no se hace!

**Está Vacío**

Es completamente posible tener una lista con cero elementos, una lista vacía:

```dart
List<int> myList = [];
```

Si intentas ejecutar el código anterior con una lista vacía, encontrarás que el total impreso es 0, porque el bucle nunca se ejecuta, por lo que nunca se agrega nada a `total` después de inicializarlo. Esto se debe a que una lista vacía tiene una longitud de 0, y el iterador del bucle, `i`, comienza en 0. Dado que 0 no es menor que 0, la condición del bucle falla inmediatamente y el cuerpo del bucle no se ejecuta.

Las listas tienen dos propiedades especiales para verificar su estado, así como un método para vaciar una lista:

```dart
void main() {
  List<int> numbers = [5, 7, 10, 3, 19];

  print("¿Vacio? ${numbers.isEmpty}");
  print("¿No vacío? ${numbers.isNotEmpty}");
  print("Longitud: ${numbers.length}");

  // vaciar la lista
  numbers.clear();

  print("\n¿Vacio? ${numbers.isEmpty}");
  print("¿No vacío? ${numbers.isNotEmpty}");
  print("Longitud: ${numbers.length}");
}
```

Estas propiedades de conveniencia son geniales cuando se usan con instrucciones if, más concisas y legibles que verificar la longitud manualmente:

```dart
if (numbers.isEmpty) {
  // ¡No tenemos números! ¡Pánico!
}

if (numbers.length == 0) {
  // También funciona, pero no es tan genial.
}

if (numbers.isNotEmpty) {
  // Procesar los números, ya que tenemos algunos.
}
```

**Otros Tipos de Elementos**

Ya hemos

 visto que una Lista puede contener una secuencia de elementos enteros, ¿pero qué pasa con otros tipos?

```dart
void main() {
  List<String> names = ["Bob", "Jerry", "Tim"];

  // imprimir todos los nombres
  for (int i = 0; i < names.length; i++) {
    print(names[i]);
  }
}
```

Sí, las listas pueden contener cadenas, valores booleanos o cualquier otro tipo de datos Dart válido. De hecho, incluso podrías mezclar y combinar:

```dart
void main() {
  List stuff = ["Bob", "Jerry", "Tim", 15, 3.14, true];

  // imprimir todas las cosas
  for (int i = 0; i < stuff.length; i++) {
    print(stuff[i]);
  }
}
```

Esto funciona porque cuando declaras una variable de tipo List, estás diciendo implícitamente que quieres una lista que pueda almacenar cualquier tipo. La forma larga de declarar este tipo de lista sería:

```dart
List<dynamic> stuff = ["Bob", "Jerry", "Tim", 15, 3.14, true];
```

El tipo dynamic abarca todos los tipos, y es el valor predeterminado para los elementos de la lista. La mayor parte del tiempo que creas una lista, tendrás un tipo particular en mente para todos sus elementos, y debes incluir ese tipo en tu declaración para asegurarte de que nada no válido termine allí:

```dart
List<int> stuff = ["Bob", "Jerry", "Tim", 15, 3.14, true];
```

¡Ese ejemplo hará que el analizador de Dart se queje de que estás intentando poner tipos que no son enteros en una lista de enteros!

```dart
List<int> numbers = [5, 7, 10, 3, 19];
```

¡Eso es mejor! Ahora tu entorno de desarrollo puede ayudarte a asegurarte de que no haya entidades incompatibles flotando en tu lista de números. ¡Homogeneidad para la victoria!

**Una Función de Suma**

Podemos resaltar las ventajas de tipificar tus listas separando el código para realizar la suma en su propia función reutilizable:

```dart
void main() {
  List<int> numbers = [5, 7, 10, 3, 19];

  int total = sum(numbers);
  print("Total: $total");
}

int sum(List<int> values) {
  int total = 0;

  for (int i = 0; i < values.length; i++) {
    total += values[i];
  }

  return total;
}
```

Usar una lista tipada aquí asegura que la función `sum()` no se bloquee cuando intenta sumar cadenas, números y valores booleanos juntos. El parámetro `values` solo puede ser asignado a una lista de enteros, por lo que el código dentro de la función puede asumir de manera segura que cada elemento es un entero.

# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)