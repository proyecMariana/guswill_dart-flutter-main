# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

# Bucles While

Es importante que realmente interiorices el concepto de expresiones booleanas, porque en el mundo de la programación, esas cosas surgen una y otra vez. Muchas de las estructuras de control de Dart las usan para decidir qué hacer. 

## ¿Qué es un Bucle?

Al escribir programas de computadora, a menudo surgen situaciones en las que quieres hacer lo mismo muchas, muchas veces, o necesitas realizar la misma acción básica en decenas, cientos, miles o incluso millones de piezas de datos. Obviamente, sería poco práctico escribir todo ese código a mano. De hecho, ¿cómo se vería algo así?

```dart
void main() {
  print(1);
  print(2);
  print(3);
  print(4);
  print(5);
  print(6);
  print(7);
  print(8);
  print(9);
  print(10);
}
```

Así es como podría verse tu código si necesitaras hacer lo mismo solo 10 veces, con solo la más mínima variación cada vez. Tiene que haber una mejor manera, ¿quizás usando variables, expresiones booleanas, y qué más...? ¡Bucles!

```dart
void main() {
  int i = 1;
  
  while (i <= 10) {
    print(i);
    i++;
  }
}
```

Si has ejecutado ambos ejemplos de código anteriores en el editor de DartPad, habrás visto que producen exactamente la misma salida. El bucle while, uno de varios tipos de bucles admitidos por Dart, evalúa la expresión booleana contenida entre paréntesis después de la palabra clave "while". Si esa expresión se evalúa como verdadera, se ejecuta el bloque de código definido entre las llaves de apertura y cierre del bucle. Incluso podrías decir que mientras la expresión permanezca verdadera, se ejecutará el cuerpo del bucle.

## Paso a Paso

Analicemos el ejemplo de código basado en bucles línea por línea.

Primero, creas una variable entera llamada "i" e inicializas su valor en 1, porque quieres contar de 1 a 10.

¿Por qué "i"? Ha sido una tradición de larga data nombrar las variables de control de bucle como "i". En la mayoría de los casos, un nombre de variable corto y poco descriptivo sería desaconsejable, pero las excepciones típicas son "i", abreviatura de "iterator" o posiblemente "index", y "x" e "y" para representar coordenadas cartesianas.

En el momento en que la computadora evalúa la expresión booleana que controla el bucle while, "i" tiene el valor de 1. Dado que 1 es menor o igual a 10 (verdadero), se ejecuta el cuerpo del bucle. La primera declaración dentro del bucle imprime "i" (1), luego "i" se incrementa (aumenta en 1) usando el operador de incremento.

Al infinito... Es extremadamente importante ajustar el valor de "i" durante la ejecución del bucle. Si el valor permaneciera en 1, el bucle continuaría ejecutando su cuerpo infinitamente (o al menos hasta que Dart decida que ha sido suficiente y intervenga para detenerlo por la fuerza).

Con el cuerpo del bucle terminado, el control del programa vuelve a evaluar la expresión booleana del bucle while.

En la segunda iteración, "i" es 2. Una vez más, la expresión se resuelve como verdadera, y se ejecuta el cuerpo del bucle, imprimiendo e incrementando "i". Esto continúa, repitiéndose una y otra vez, hasta que "i <= 10" se convierte en falso. Esto sucede cuando "i" llega a 11. Para entonces, los valores de 1 a 10 se han impreso en la consola.

## Incluso Más Corto

Debido a una peculiaridad del orden de las operaciones en Dart, es posible acortar aún más este código sin comprometer el resultado deseado. El nombre de una variable, por sí solo, es en realidad una expresión. Como todas las expresiones, se evalúa a un valor final, en este caso, el valor que contiene la variable.

```dart
int x = 1;
x;
```

La segunda línea de código anterior se evalúa como 1. No es muy útil ya que no imprimes ni usas el valor de ninguna manera, pero es importante entender que es una expresión perfectamente válida. El operador de incremento (++) tiene una precedencia tan baja que incluso la evaluación solitaria de una variable ocurre primero, por lo que si "i" es 1 y tienes una expresión

 "i++", cualquier expresión/declaración circundante que haga uso de "i" podrá hacerlo antes de que ocurra la operación de incremento.

```dart
void main() {
  int i = 1;
  
  while (i <= 10) {
    print(i++);
  }
}
```

La primera vez que se ejecuta el cuerpo del bucle, imprime 1, y luego incrementa "i" a 2. El valor de "i" se imprime antes de que se le agregue 1. Ahora, hay algunos que desaprueban este enfoque, argumentando que es menos claro, que necesitas entender una regla oscura para ver qué está pasando. Puedes decidir por ti mismo.

## Prefijarlo

Intenta poner el operador de incremento en el otro lado de "i", como un prefijo en lugar de un sufijo: print(++i). ¿Cómo cambia tu salida? Obtendrás los números del 2 al 11 impresos, porque en la primera iteración del bucle, el valor de 1 se incrementa a 2 antes de que ocurra la llamada a print().

```dart
void main() {
  int i = 0;
  
  while (i < 10) {
    print(++i);
  }
}
```

Arriba, puedes ver que para imprimir del 1 al 10 usando la versión prefija del operador de incremento, necesitas inicializar "i" en 0 y cambiar el operador de comparación de "<=" a "<". La variable "i" se incrementa antes de imprimir el valor en cada iteración del bucle, por lo que aunque entra en el bucle por primera vez con un valor de 0, se convierte en 1 antes de imprimirse. La última vez que "< 10" se evalúa como verdadero, "i" es 9, pero se aumenta a 10 antes de imprimirse en la consola.

## Fácil de Ajustar

Ahora tienes este programa asesino que puede contar hasta 10, pero tu jefe regresa y te dice que la función más solicitada por tus usuarios es contar hasta 50. ¡Te quedas sin aliento! ¿Qué? Pero 50 es mucho más que 10. ¡Al menos 5 veces más! ¿Puede un programador lograr tal cosa en una sola vida?

Bueno, sin bucles, sería bastante tedioso. Tendrías que apilar 50 llamadas a print(). Con el bucle, puedes lograr lo que parecía imposible cambiando solo un carácter:

```dart
void main() {
  int i = 1;
  
  while (i <= 50) {
    print(i++);
  }
}
```

# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)