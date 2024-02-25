# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

# Parámetros de Funciones

A veces, una función necesita entrada para hacer su trabajo. En lecciones anteriores, examinamos una función llamada greet() que lucía así:

```dart
void saludar() {
  print("¡Hola!");
}
```

La función saludar() siempre imprime "¡Hola!" en la consola, y no requiere ninguna información especial para hacerlo. Por eso, los paréntesis de la función están vacíos. No está preparada para aceptar ningún tipo de entrada. Muchas funciones pueden ser más útiles al permitir algún tipo de entrada. Como ejemplo, observa la llamada a print(); si no pudieras proporcionarle a esa llamada una cadena, ¿qué imprimiría en la pantalla? La función print() es útil para ti, una y otra vez, porque puedes decirle qué imprimir cada vez que la uses. Cuando quieres que tus propias funciones acepten entrada, utilizarás parámetros de función.

## ¿Cómo Utilizo los Parámetros de Funciones?

¡Me alegra que hayas preguntado! Como se mencionó anteriormente, la función saludar() no tiene parámetros porque no espera ninguna entrada. Mejoremos esa función para saludar a alguien (o algo) diferente cada vez que se ejecute:

```dart
void saludar(String destinatario) {
  print("¡Hola, $destinatario!");
}
```

Ahora es posible enviar un valor a saludar() cuando se llama. De hecho, si lo haces, se verá muy parecido a llamar a print(), porque ahora tu función espera exactamente un valor de tipo cadena, al igual que print():

```dart
saludar("Joe");
```

Llamar a saludar() de esa manera hará que la variable destinatario contenga el valor "Joe". "Joe" es un argumento que se pasa a saludar(). Dentro del cuerpo de saludar(), es posible usar ese valor para personalizar el saludo. Ingresa el siguiente código en el editor para probarlo:

```dart
void main() {
  saludar("Joe");
  saludar("Fred");
}

void saludar(String destinatario) {
  print("¡Hola, $destinatario!");
}
```

En este ejemplo, destinatario es el parámetro. Se convierte en una variable local, accesible solo dentro del cuerpo de la función saludar(), y se le asigna cualquier argumento proporcionado en la llamada de la función.

En su nueva forma, el cuerpo de la función saludar() utiliza interpolación de cadenas para saludar a "Joe", o a quien/qué desees.

## Firmando

Cuando defines una función, el tipo de retorno, el nombre y la lista de parámetros conforman la firma de esa función. La firma de una función es como un contrato, especificando qué se espera cuando se utiliza esa función. La lista de parámetros le dice al usuario cuántos valores se esperan, incluidos sus tipos y el orden en que deben proporcionarse. Si invocas la función con un grupo de argumentos que no coinciden, estás violando el contrato.

Ahora que la definición de saludar() incluye ese parámetro, el analizador de Dart se enojará si intentas llamar a la función sin proporcionar los argumentos esperados, en este caso precisamente un valor de tipo String. Adelante, intenta llamarlo de la manera antigua, con paréntesis vacíos, y verás aparecer un error.

## Más Parámetros

Las funciones también pueden aceptar más de un valor como entrada:

```dart
void main() {
  sumar(5, 10);
}

void sumar(int a, int b) {
  print(a + b);
}
```

Aquí, la firma de la función sumar() incluye dos parámetros enteros, separados por comas. Cuando llamas a la función, proporcionas todos los argumentos necesarios dentro de los paréntesis, también separados por comas. Al igual que en inglés, la convención es insertar un espacio después de cada coma, aunque a Dart no le importa si lo omites.

Dentro de sumar(), puedes acceder a los valores proporcionados como variables a y b. La función suma los dos juntos e imprime el resultado. ¡Pruébalo!

## Revisión de Parámetros vs. Argumentos

En el ejemplo de sumar(), a y b son los parámetros de la función. Los argumentos son los valores proporcionados cuando se invoca la función (sumar(5, 10);). Entonces 5 y 10 son los argumentos en este ejemplo. Puede que ocasionalmente escuches los términos usados indistintamente, porque el contexto generalmente deja claro cuál es el significado pretendido, pero si quieres ser técnico (y como programador, lo eres), los términos son distintos.

## Tipos Mixtos

Una función puede tomar cualquier cantidad de argumentos de cualquier tipo válido. Intenta un ejemplo más complicado:

```dart
void main() {
  imprimirRepetido("¡Hola!", 10);
}

void imprimirRepetido(String str, int repeticiones) {
  for (int i = 0; i < repeticiones; i++) {
    print(str);
  }
}
```

La función imprimirRepetido() espera una cadena para imprimir y un número que representa cuántas veces imprimirlo. El bucle for imprimirá el valor de str tantas veces como indique el argumento repeticiones. Pasar "¡Hola!" y 10 como argumentos resultará en una torre de saludos en tu consola.

¡Es tu turno!

Tómate un tiempo para experimentar con tus propias funciones. Varía el número y los tipos de parámetros. Echa un vistazo a las lecciones anteriores para ver si alguno de esos ejemplos podría haber hecho uso de funciones personalizadas para ser más limpio y mejor compartimentado.


# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)