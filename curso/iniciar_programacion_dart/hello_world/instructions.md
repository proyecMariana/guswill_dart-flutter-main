# "Hello!"

Te doy la bienvenida al comienzo de tu aventura para aprender cómo hacer que las computadoras en tu vida hagan lo que tú quieras. Normalmente, esta aventura comienza con un saludo digital: "¡Hola, Mundo!" Saludar al mundo de esta manera es solo cuestión de escribir unas pocas líneas de código :

```dart
void main() {
  print("Hello, World!");
}
```
Ingresa el código de arriba, tal como se muestra, en tu editor de código Dart, luego ejecútalo. Deberías ver el texto "¡Hola, Mundo!" aparecer en la consola.

Si este fue tu primer programa, ¡felicidades! Ya estás demostrando quién manda aquí.

## El manejo de las funciones
Veamos si podemos desmitificar algunas de estas palabras y símbolos locos:

```dart
void main() {
```
Cada programa de Dart comienza con una _función_ llamada `main()`. Por ahora, no necesitas preocuparte demasiado por lo que significa eso, pero en resumen, una función define un bloque de declaraciones de código que la computadora ejecuta cuando es "llamada" por su nombre. Dado que `main()` es el punto de entrada estándar de Dart, se llama automáticamente cuando ejecutas el programa.

Las funciones pueden tomar _input_ (datos que entran) y pueden producir _output_ (datos que salen). Los paréntesis vacíos adjuntos al nombre de la función indican que no espera ninguna entrada, mientras que la palabra clave `void` le dice a Dart que `main()` no producirá ninguna salida.

Como una buena historia, cada función tiene un principio, un desarrollo y un final. Llaves de apertura y cierre denotan el inicio y el final de una función. Probablemente te hayas preguntado durante años por qué tu teclado de computadora incluso _tiene_ esas teclas. Bueno, ahora lo sabes. Entre las llaves, colocas las instrucciones que deseas que la computadora siga cuando se ejecute tu función.

## Poniendo Cosas en la Pantalla
La función `main()` tiene solo una declaración de instrucción en su _cuerpo_:

```dart
print("¡Hola, Mundo!");
```

Observa que esta línea está indentada dos espacios. Por convención, la indentación se utiliza en el código de Dart para hacer evidente la jerarquía. En su mayor parte, el espacio en blanco de todo tipo (espacios, saltos de línea, etc.) es ignorado por el intérprete de Dart, pero como humanos, lo usamos para hacer relaciones claras. La llamada a la función `print()` _pertenece_ a la función `main()`.

La función `print()` está definida en la biblioteca central de Dart, disponible para todos los programas de Dart. Al igual que tu función `main()`, no devuelve valores (no produce salida de código), pero espera entrada. La entrada debe tener la forma de una _cadena_. Una cadena es una serie de caracteres concatenados (una cadena de caracteres), delimitados por comillas. Por supuesto, en este caso, estás enviando los caracteres que componen la frase "¡Hola, Mundo!" a la función `print()`. La función `print()` acepta la entrada e imprime en la consola del sistema, normalmente una pantalla.

## Entonces _Eso_ Para Qué Sirve un Punto y Coma
Debido a que Dart ignora el espacio en blanco, necesitas usar un punto y coma para indicar al intérprete de código dónde termina tu declaración. Si olvidas el punto y coma, el intérprete se confundirá e incluso puede quejarse contigo. Intenta eliminar el punto y coma en tu editor de código. Deberías ver aparecer un error. Corrige el problema y el editor volverá a su estado de equilibrio.

## Hora de Jugar
Ahora, tómate un minuto para jugar con este código. Cambia la cadena de caracteres que estás enviando a `print()`. Incluso puedes hacer que diga cosas traviesas, si quieres. Sé que estás deseando intentarlo.

Aunque puede parecer prematuro utilizar un print en conjunto con un bucle `for`, considero que es importante abordarlo en esta etapa para explorar la interacción y la capacidad que ofrece cualquier lenguaje de programación mediante el uso de bucles, como es el caso del bucle `for`. Más adelante, profundizaremos con más ejercicios y pruebas sobre esta temática.

```dart
void main() {
  // Imprime un mensaje de bienvenida
  print("¡Bienvenido al ejercicio de Dart!");

  // Imprime una lista de números del 1 al 10
  for (int i = 1; i <= 10; i++) {
    print(i);
  }

  // Imprime un mensaje de despedida
  print("¡Eso es todo por ahora!");
}
```


