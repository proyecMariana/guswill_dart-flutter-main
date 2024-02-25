# Tipos

Las variables en Dart vienen en muchos tipos diferentes. Algunas variables están destinadas a contener números, algunas caracteres, y algunas apuntan a valores más complejos. Al declarar variables, puedes permitir que Dart intente inferir el tipo previsto de tu variable o puedes ser explícito.

## Tipos inferidos
En la última lección, declaraste tus variables usando la palabra clave `var` (abreviatura de "variable"), así:

```dart
var x;
```

Cuando declaras una variable usando `var`, Dart intenta inferir el tipo de la variable. Si no inicializas la nueva variable con un valor en la misma declaración, Dart no tiene nada en qué basarse para hacer una inferencia, por lo que la variable se considera de tipo `dynamic`. Como una variable dinámica, `x` puede aceptar valores de cualquier tipo válido. Si no inicializas una variable dinámica con un valor, se inicializa automáticamente con el valor especial de `null`.

## Mezclándolo
En este ejemplo, se declara una variable llamada `x`, pero no se inicializa con un valor, por lo que comienza con un valor de `null`. El tipo de variable en esta instancia es `dynamic`, lo que significa que puede contener valores de cualquier tipo, por lo que el código como este no sería un problema:

```dart
var x;
x = 5;
x = "Dart es genial.";
```

El código declara `x`, luego instruye a Dart a almacenar un valor de `5` en la ubicación de memoria llamada `x`. Ese valor es un _entero_, un número entero sin parte fraccionaria. La siguiente línea asigna el valor `"Dart es genial."`, una cadena de caracteres, a `x`. Esa es una variable versátil.

## Truco de desaparición numérica
Prueba este código:

```dart
void main() {
  var x;
  x = 5;
  x = "Dart es genial.";
  print(x);
}
```

¿Puedes predecir qué se imprimirá? Si ejecutas el código, verás que "Dart es genial." aparece en la consola. ¿Qué pasó con el `5`? Después de que se declaró `x`, se le asignó el valor `5`. El `5` reemplazó al valor `null` inicial. La siguiente instrucción asigna una cadena de caracteres a `x`, borrando el valor numérico. Dado que `x` es de tipo `dynamic`, el analizador de código no señala el problema potencial.

Modifica el código para imprimir el valor de la variable después de cada asignación para ver la acción paso a paso:

```dart
void main() {
  var x;
  print(x);
  x = 5;
  print(x);
  x = "Dart es genial.";
  print(x);
  x = null;
  print(x);
}
```

La mayoría de las veces cuando creamos variables, tenemos un tipo particular de valor en mente para ella, lo que significa que asignar valores de diferentes tipos a esa variable probablemente sea accidental, y puede producir resultados no deseados. Por ejemplo, si creas una variable destinada a almacenar el costo de un artículo (un número), probablemente no quieras almacenar el nombre de alguien más tarde, y si lo hiciste accidentalmente, puede producir un error. Ten en cuenta que siempre puedes restablecer una variable dinámica a `null` asignándole la palabra clave especial `null`, como se demuestra en el código de ejemplo.

Más adelante, verás cómo el analizador de Dart puede ayudarnos a evitar este tipo de problema.

## No puedes hacer eso
Modifica el código para que se vea así:

```dart
void main() {
  var x = 5;
  x = "Dart es genial.";
  print(x);
}
```

Este código hace que DartPad muestre un error, diciendo que estás mezclando tipos. Debido a que has inicializado `x` con un valor numérico entero al mismo tiempo que lo declaraste, Dart infiere que `x` debe contener enteros a partir de ese momento. Ahora `x` es de tipo `int` en lugar de `dynamic`, aunque fue declarado con la palabra clave genérica `var`.

Puedes anular la inferencia de Dart especificando que quieres que tu variable sea dinámica. Intenta cambiar la declaración para usar `dynamic` en lugar de `var` y observa cómo desaparece el error:

```dart
dynamic x = 5;
```

O podrías declarar e inicializar explícitamente `x` como un `int`, que probablemente sea la mejor opción en la mayoría de los casos:

```dart
int x = 5;
```

Al usar la palabra clave `int`, has creado una variable destinada explícitamente a contener enteros, por lo que si intentas más tarde asignar una cadena de caracteres a ella (un tipo `String`), Dart se queja. El error está de vuelta. El analizador simplemente está tratando de evitar que te hagas daño.

### Los errores detienen la ejecución
Ten en cuenta que si ejecutas el código con tipos de datos incompatibles, la ejecución fallará. Siempre debes eliminar todos los errores reportados antes de intentar ejecutar tu código.

## ¿Por qué usar tipos explícitos?
Dart estaba perfectamente feliz de permitirte asignar cualquier valor a tu variable sin errores cuando declaraste `x` como de tipo `dynamic`, entonces, ¿por qué te restringirías con tipos más específicos? El lenguaje tiene un sistema de tipos sólido diseñado para ayudarte a encontrar problemas antes de ejecutar tu código. Si pretendes usar `x` para contener valores enteros, como coordenadas de cuadrícula quizás, entonces probablemente sea un error asignarle una cadena de caracteres. Cuando usas anotaciones de tipo explícitas como `int`, Dart puede ayudarte a detectar este tipo de problemas antes de que se conviertan en errores de tiempo de ejecución&mdash;errores.

## La solución está en
Para arreglar las cosas, intenta esto:

```dart
void main() {
  String x = "Dart es genial.";
  print(x);
}
```

Ahora que

 `x` se declara explícitamente como de tipo `String`, DartPad está contento, seguro de que sabes lo que estás haciendo. En este ejemplo, también podrías haber usado `var` y permitido que Dart infiera el tipo `String` a partir del valor de inicialización.

> **¡Oye! ¿Por qué `int` está en minúscula, pero `String` está en mayúscula?** Esto puede parecer un intento de hacer las cosas más confusas de lo necesario, pero realmente la razón radica en la forma en que han evolucionado los lenguajes de programación con el tiempo. Dart fue construido para ser familiar para aquellos que vienen de otros lenguajes, como Java o C++. A diferencia de Dart, esos lenguajes tienen el concepto de tipos _primitivos_, tipos especiales que son fundamentalmente compatibles. Los primitivos suelen estar denotados por palabras clave en minúsculas del lenguaje, mientras que los tipos complejos o definidos por el usuario se capitalizan. Aunque todos los tipos de Dart son simplemente _objetos_, y Dart no tiene primitivos, los diseñadores del lenguaje optaron por la familiaridad en este caso. No te preocupes por lo que son los objetos por ahora&mdash;entraremos en eso más adelante.

## Tipos fundamentales
No hay límite en el número de tipos que puede tener un programa, pero hay algunos tipos que son fundamentales para Dart:

| Tipo    | Descripción                           | Ejemplos                   |
|---------|---------------------------------------|----------------------------|
| int     | Número entero (número entero)         | 5, -13, 0                  |
| double  | Número de punto flotante (decimales)  | 3.14, 18.0, -33.999        |
| num     | Número entero o de punto flotante     | 5, 3.14, -13, 999.666      |
| bool    | Booleano                              | true, false                |
| String  | Cadena de cero o más caracteres      | "hola", "Juan Pérez", "X", "" |
| List    | Lista de valores en serie             | [1, 2, 3], ["uno", "dos", "tres"] |
| Map     | Mapa de valores por clave             | {"x": 8, "y": 16}          |
| dynamic | Cualquier tipo                        |                            |

## Recapitulación de `var`
Recuerda, la palabra clave `var` funciona de manera diferente según el contexto. Si declaras una variable con `var`, pero no le asignas un valor en la misma declaración, Dart asumirá que debe ser `dynamic` y le asignará un valor de `null` para empezar. Si inicializas el valor al declarar la variable, Dart inferirá el tipo en función del tipo de ese valor, y esa variable se tratará como si hubieras usado un tipo explícito. Por lo tanto, las siguientes dos líneas son equivalentes:

```dart
var z;

dynamic z;
```

Y estas son equivalentes:

```dart
var y = 99;

int y = 99;
```

## Más sobre `null`

En Dart, la mayoría de las variables no pueden asignarse el valor especial de `null`. Esto es para ayudarte a evitar errores en tu código. Intentar realizar operaciones en `null`, naturalmente, no funciona bien. No puedes sumar `null` a `5`, por ejemplo, porque `null` no es `0`—no es nada en absoluto. Por esta razón, Dart te ayuda a garantizar que tus variables nunca contendrán `null`, sino que siempre tendrán un valor "válido" para el tipo de esa variable.

Una variable con tipo `dynamic` (ya sea explícita o a través de la inferencia) puede tener *cualquier* valor, incluido `null`, pero sin tratamiento especial, no se permite que otras variables tipadas contengan `null`:

```dart
void main() {
  var myVar;          // se inicializa automáticamente a null y se infiere como dynamic
  dynamic myDyn;      // se inicializa automáticamente a null
  int myInt;          // advertencia: las variables enteras deben asignarse antes de usarlas

  print(myVar);       // null
  print(myDyn);       // null
  print(myInt);       // error: myInt no tiene ningún valor (ni siquiera null)
}
```

Debes darle a una variable tipada un valor antes de intentar usarla:

```dart
void main() {
  int myInt1 = 0;
  print(myInt1);       // 0
    
  int myInt2;
  myInt2 = 0;
  print(myInt2);       // 0
    
  myInt1 = null;       // error: una variable int no puede ser null
}
```

### Haciendo que las variables tipadas sean nulas

Si realmente quieres que una variable tipada pueda almacenar un valor `null`, debes declararlo explícitamente usando el carácter `?` con el tipo:

```dart
void main() {
  int? myInt;          // se inicializa automáticamente a null
  print(myInt);        // null
  myInt = 4;
  print(myInt);        // 4
  myInt = null;
  print(myInt);       // null
}
```

Es mejor pensar en `int` y `int?` como tipos similares pero a veces incompatibles.

## Hora de Jugar
> **Reto:** Escribe un script en Dart en el cual puedas definir variables de diferentes tipos de datos como int, double, num, bool y String. Luego, asigna valores adecuados a cada tipo de dato y muestra estos valores en pantalla.
