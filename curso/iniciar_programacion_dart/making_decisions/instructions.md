# Tomando Decisiones

Todos los días, haces evaluaciones y comparaciones, y basándote en tus hallazgos, tomas decisiones. ¿Hace frío afuera? Sí, tal vez necesite vestirme abrigado. Pero, ¿está _realmente_ frío? Si es así, tal vez deba sacar mi abrigo de invierno en lugar de depender de esta chaqueta endeble.

Los programas también necesitan tomar decisiones. ¿Hay un usuario válido conectado? Si es así, permite que el usuario interactúe con la interfaz de usuario. ¿Existe el archivo que necesitamos cargar? Si es así, cárgalo, pero si no, créalo.

## Si Solo
Tomar decisiones es una parte esencial de todos los programas informáticos excepto los más simples. Podrías modelar parte de tu diálogo interno sobre qué ponerse afuera con código como este:

```dart
void main() {
  int frío = 60;
  int temperatura = 57;

  print("¿Hace frío afuera?");
  
  if (temperatura < frío) {
    print("Sí, un poco.");
  }
}
```

Si ejecutas este código en el editor, por supuesto que verás dos cadenas impresas, porque 57 es, de hecho, menor que 60. Observa que aquí tipificamos las variables como `int`, lo que significa que esperamos que los valores de temperatura sean enteros (números enteros). Los números mismos están en la escala Fahrenheit, la más comúnmente utilizada en los Estados Unidos, en caso de que 60&deg; no te parezca frío.

Una de las formas en que Dart toma decisiones es usando la palabra clave `if`, una de varias estructuras de control disponibles en el lenguaje. Entre los paréntesis que siguen a `if`, debes colocar una expresión que se resuelva a un valor booleano, ya sea `true` o `false`. En la siguiente lección, aprenderás más sobre la lógica booleana y los operadores de comparación de Dart, pero por ahora, concentrémonos en `if`.

Después de la expresión booleana entre paréntesis viene la llave de apertura que define el comienzo del bloque de código a ejecutar en caso de que la expresión sea `true`. Si la expresión es `false`, todo dentro del bloque de código `if` se omitirá. Naturalmente, el bloque de código se finaliza con una llave de cierre.

### Calentándose
Intenta cambiar el valor de `temperatura`:

```dart
int temperatura = 71;
```

Al ejecutar el código esta vez, se imprimirá la pregunta, pero no habrá respuesta, dejando a todos confundidos y angustiados. Como 71 no es menor que 60, la segunda llamada a `print()` nunca se ejecuta.

### ¿Qué Más?
Simplemente no es suficiente dejar la pregunta sin respuesta, así que agrega una cláusula `else` a tu declaración `if` para manejar una expresión `false`:

```dart
if (temperatura < frío) {
  print("Sí, un poco.");
} else {
  print("No, está bastante cálido.");
}
```

Ahora, con `temperatura` a 71&deg; y la definición de `frío` aún establecida en 60&deg;, la expresión de comparación se resolverá a `false`, porque 71 no es _menor_ que 60. El bloque de código `else` se ejecutará en este caso.

> **Nota:** Técnicamente se permite omitir las llaves de apertura y cierre para los bloques de código `if` o `else` que contienen solo una única declaración a ejecutar, pero no se recomienda.

## ¿Chaqueta o Abrigo?
Con `if` y `else`, puedes tomar decisiones simples, pero en la introducción de esta lección, luchaste con una pregunta más complicada. ¿Cómo se puede representar eso en código?

```dart
void main() {
  int frío = 60;
  int congelación = 40;
  int temperatura = 57;

  print("¿Hace frío afuera?");
  
  if (temperatura > frío) {
    print("No, bastante acogedor, en realidad.");
  } else if (temperatura > congelación) {
    print("Hace un poco de frío. Quizás una chaqueta.");
  } else {
    print("¡Está helado! ¿Dónde está mi abrigo?");
  }
}
```

Usando la declaración `else if`, puedes manejar más ramas de decisión. El código anterior imprimirá "Hace un poco de frío. Quizás una chaqueta." Dart examina cada expresión booleana en orden. La temperatura, en 57, no es mayor que 60, por lo que se omite el primer bloque de código. Luego, se examina la porción `else if`. Dado que 57 _es_ mayor que 40, esa expresión es `true`, y se ejecuta el segundo bloque de código. El bloque `else` final solo se ejecutará en caso de que todas las expresiones anteriores de `if` y `else if` se encontraran `false`.

Puedes usar tantas declaraciones `else if` como desees, pero si tienes demasiadas, es posible que quieras reestructurar tu código para hacer las cosas más simples, o tal vez usar otra estructura de control, como `switch`. Más sobre eso después.

## Siempre Jugando

Juega con diferentes valores para `temperatura`, `frío` y `congelación` para hacer que cada una de las llamadas a `print()` se ejecute.