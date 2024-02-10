# Operadores de Asignación Compuesta

Además de los operadores ya discutidos, Dart admite una serie de operadores de conveniencia que combinan múltiples operaciones. Por lo general, estos operadores combinan operaciones matemáticas y de asignación, y utilizarlos puede ahorrarte algo de escritura.

## Sumar y Asignar

Supongamos que deseas realizar una suma simple, así:

```dart
int x = 5;
x = x + 5;
```

Esa es una forma perfectamente válida de sumar 5 a `x`, y después de que este código se ejecute, `x` contendrá el valor `10`. ¿Pero qué tal si pudiera ser aún más fácil?

```dart
int x = 5;
x += 5;
```

Este código utiliza uno de los operadores de asignación compuesta, `+=`, para obtener el mismo resultado con menos escritura. Los dos ejemplos de código son exactamente equivalentes. En cada caso, el valor inicial de `x` se suma a 5, y `x` termina siendo `10`.

### Pruébalo

Intenta ejecutar este código en el editor de código:

```dart
void main() {
  int x = 5;
  
  print(x += 5);
  print(x);
}
```

Como podrías haber predicho, la primera llamada a `print()` coloca un `10` en la consola, pero lo importante aquí es notar que `x` ha sido actualizado con el nuevo valor, por lo que la segunda llamada a `print()` también te da `10`.

Para comparación:

```dart
void main() {
  int x = 5;
  
  print(x + 5);
  print(x);
}
```

En esta versión, la suma ocurre y el resultado se imprime, pero la suma luego se desecha. Sin el `=`, `x` no se modifica. Permanece `5`.

## Restar

También puedes restar mientras asignas:

```dart
int x = 5;
x -= 5;
```

Después de que este código se ejecute, `x` será `0`.

## Multiplicar

¡Es cierto! También puedes hacer esto:

```dart
int x = 5;
x *= 2;
```

En este fragmento, `x` se multiplica por 2, y el resultado se guarda de nuevo en `x`, lo que significa que `x` se convierte en `10`.

## ¡Ten Cuidado con la División!

Los matemáticos entre ustedes pueden haber empezado a preguntarse si la división, que puede dar como resultado cocientes fraccionarios, podría causar problemas:

```dart
void main() {
  int x = 5;
  x /= 2;
}
```

Este código crea un error, porque el resultado de una operación de división siempre es de tipo `double`, y `x` fue declarado como un `int`. Arreglemos eso:

```dart
void main() {
  double x = 5;
  x /= 2;
}
```

¿Qué...? ¡Otro error! ¿Nada satisfará a Dart? El problema ahora es que estamos inicializando un `double` con un entero, el valor `5`. Otro ajuste:

```dart
void main() {
  double x = 5.0;
  x /= 2;
}
```

Ahora funciona, ya que `5.0` es un literal `double` con su componente fraccionario incluido explícitamente. Un poco molesto así, sin embargo, ya que `.0` es técnicamente innecesario. Hagamos un cambio más:

```dart
void main() {
  num x = 5;

  x /= 2;
  print(x);
}
```

¡Ahí lo tienes! Dado que una variable de tipo `num` puede contener valores `int` o `double`, esta versión de `x` funciona tal como esperarías. Cuando imprimes `x`, ves que ahora es el valor `double` `2.5`.

## División Entera

Dart incluye un operador matemático más interesante que aún no has visto: el operador de división entera. Usándolo, podríamos abordar los problemas de tipo de la división de otra manera. Este operador realiza una división como de costumbre, pero siempre devuelve un resultado entero en lugar de un `double`. Cualquier parte fraccionaria simplemente se desecha:

```dart
void main() {
  int x = 5;

  x ~/= 2;
  print(x);
}
```

Aquí, volvemos a declarar `x` como un `int`, lo que funciona porque la división entera siempre devolverá un `int`.

La versión no compuesta de este operador, sin hacer una asignación, se ve así:

```dart
6 ~/ 2;     // resultado: 3 (no 3.0)
```

Si no estás seguro de qué es la pequeña línea ondulada, es el carácter de tilde (`~`), que a menudo se encuentra en la parte superior izquierda de tu teclado. En algunos contextos, se usa para representar el concepto de aproximación, y por eso es perfecto para la división entera.