# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

# Funciones

Puedes recordar el concepto de funciones de tu clase de matemáticas. En matemáticas, una función es una construcción que relaciona una entrada con una salida. Lo que sale está relacionado con lo que entra. La forma clásica de escribir una función matemática es f(x). Cuando f(x) = 2x, lo que estás diciendo es que la función, llamada f, toma una entrada, x, y la duplica, produciendo una salida. Entonces, si x = 4, entonces tendrías f(4) = 8. El 4 entra, se multiplica por 2 y la salida es 8.

## ¿Qué son las Funciones en Dart?

Las funciones en Dart a veces se usan para producir una salida determinada dada una entrada particular, pero muchas de ellas son más simples que eso, actuando como nada más que bloques de código reutilizables o procedimientos. Son una de las unidades básicas para organizar el código en un programa. Cuando los programas se vuelven largos, las funciones te ayudan a mantener las cosas limpias y legibles, y te evitan repetirte todo el tiempo.

## ¿Cómo lucen?

Si has completado las lecciones anteriores, ya has visto y usado varias funciones. Todos los programas Dart comienzan la ejecución con la función main():

```dart
void main() {
  // código para la función main() va aquí
}
```

Para ahora, también has hecho un uso extensivo de la función print():

```dart
print("¡Imprímeme!");
```

La función print() toma una cadena como entrada y imprime los caracteres en la consola del sistema. (Técnicamente, la función print() toma un tipo Object como entrada, que luego se convierte en un String, pero profundizaremos en esos detalles más tarde). Colocar caracteres en la pantalla implica el uso de muchas instrucciones de nivel inferior, escritas para ti por las buenas personas de Google. Tu programa sería un desastre ilegible si tuvieras que escribir todas esas instrucciones cada vez que quisieras enviar un mensaje a la consola. Cuando llamas a la función print(), usas una línea de código para ejecutar muchas otras, y puedes hacerlo una y otra vez. Crearás tus propias funciones para un propósito muy similar.

Descubrirás que los empleados de Google y los miembros de la comunidad de Dart han escrito muchas funciones útiles y las han puesto a disposición de forma gratuita como código fuente abierto. Una gran parte de dominar un lenguaje de programación es familiarizarse con todas las herramientas y el código escrito por otros para tu uso.

## Un Ejemplo

Es posible que necesites imprimir un saludo en la consola con cierta regularidad. Tu programa es tanto charlatán como demasiado amigable, si no un poco promiscuo, así que creas una función que se ve así:

```dart
void saludar() {
  print("¡Hola!");
}
```

Ahora, cada vez que sea momento de emitir un saludo, puedes ejecutar esta función:

```dart
saludar();
```

En este caso simple, encapsular tu saludo en una función no te ha ahorrado mucho escribir, pero hay otros beneficios importantes. Por ejemplo, ¿qué pasa si luego te das cuenta de que el signo de exclamación en "¡Hola!" te hace sonar demasiado entusiasta, o quizás tu programa se encuentra en un entorno más formal? Si tienes 30 saludos dispersos por todo tu código, cambiar cada uno de esos para imprimir una nueva cadena sería laborioso, pero si todos esos saludos usan la función saludar(), cambiar la cadena en ese único lugar es todo lo que necesitarás hacer:

```dart
void saludar() {
  print("¡Hola.");
}
```

Ahora, cada llamada a saludar() producirá la cadena "¡Hola." en lugar de "¡Hola!"

## ¿Dónde Ubico Mis Funciones?

Por ahora, tus funciones personalizadas pueden vivir junto a la función main() requerida. Más adelante, cuando hayas avanzado más allá de nuestro entorno de codificación simple, a veces agruparás las funciones en diferentes archivos.

Prueba este código en el editor de código:

```dart
void main() {
  saludar();
}

void saludar() {
  print("¡Hola!");
}
```

Cuando lo ejecutes, deberías ver la cadena "¡Hola!" aparecer en la consola. El programa comienza ejecutando main(), y la única instrucción en main() llama a tu función personalizada saludar(), lo que hace que tu saludo aparezca en la pantalla.

## Anatomía de la Función

Anteriormente, dijimos que las funciones pueden tomar entrada y producir salida. Hablando estrictamente, la función saludar() no hace ninguna de las dos cosas. Es un procedimiento, que existe solo por conveniencia y para agrupar acciones comúnmente utilizadas.

###

 En el Vacío

Cuando colocas la palabra clave void antes del nombre de una función que estás definiendo, estás diciendo que no tienes la intención de que la función produzca ninguna salida, o en la jerga de programación, no tiene ningún valor de retorno.

### El Juego de los Nombres

La siguiente parte de la definición de tu función es el nombre de la función, saludar. Este nombre puede ser cualquier identificador válido, que es una palabra que comienza con una letra o un guión bajo (_), seguida de cualquier combinación de letras, números y guiones bajos. Por ahora, no comiences uno con un guión bajo, ya que eso significa algo especial en Dart, que se discutirá más adelante.

Por convención, los nombres de las funciones usan la notación camelCase. Esto significa que deberías capitalizar la primera letra de cada palabra en el identificador, excepto la primera, que siempre está en minúscula. Ejemplo: miFuncionFavorita().

### Entre Paréntesis

La función saludar() tiene un conjunto vacío de paréntesis porque no toma ninguna entrada. En lecciones posteriores, pasarás valores como entrada en forma de una lista de parámetros de función.

# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)