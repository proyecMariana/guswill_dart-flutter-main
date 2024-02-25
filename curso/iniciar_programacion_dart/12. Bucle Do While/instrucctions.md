# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

# Bucles Do-While

Un bucle do-while prueba la condición en el punto de salida del bucle. Esto significa que, a diferencia del bucle while, el cuerpo de un bucle do-while siempre se ejecutará al menos una vez.

## Un Caso de Uso Típico

Uno de los usos más comunes de un bucle do-while es verificar la entrada válida de un usuario en una aplicación de consola. En realidad, no puedes obtener entrada de consola con el editor de DartPad, así que demostraré la idea aquí con pseudo-código, que transmite la idea sin usar código real:

```dart
do {
  print("Ingrese su respuesta:");
  respuesta = <obtener respuesta de la consola>
} while (<respuesta es inválida>);
```

Si el usuario ingresa algo inválido, el programa seguirá preguntando hasta que le guste lo que obtenga.

## Un Poco Más de Pseudo-Código

Otro lugar donde verás que el bucle do-while aparece a menudo es al construir un bucle de juego. En muchos juegos, necesitas configurar un bucle principal que repita el código del juego una y otra vez hasta que se cumpla algún tipo de condición de salida:

```dart
do {
  // mover jugador y enemigos
  // dibujar gráficos del juego
  // obtener entrada del juego
} while (estado != "salir");
```

Algo así.

## Pruébalo

Suficiente con la teoría. Adelante, ingresa este código en el editor:

```dart
void main() {
  int cervezas = 99;
  
  do {
    print("$cervezas botellas de cerveza en la pared, $cervezas botellas de cerveza.");
    print("Toma una, pásala... ");
    print("${cervezas - 1} botellas de cerveza en la pared.\n");
    cervezas--;
  } while (cervezas > 0);
}
```

¡Mira eso! Has emborrachado a Dart, y ahora está cantando. La variable "cervezas" se inicializa en 99, luego, con cada iteración del cuerpo del bucle, "cervezas" se decrementa en 1. Mientras "cervezas" sea mayor que 0, volvemos al inicio y seguimos cantando. Una vez que llega a 0, la cerveza se acabó, la fiesta terminó y el bucle ha terminado.

## Queda Algo Incómodo

Para aquellos de ustedes con una atención al detalle, habrán notado que hay algo incómodo en este bucle. Cuando "cervezas" es 1, Dart canta "1 botellas de cerveza en la pared..." La palabra "botellas" permanece en plural aunque solo quede una botella!

¿Qué puedes hacer para evitar que Dart parezca estúpido en la gran fiesta? Ve si puedes usar algún tipo de declaración de control para arreglar esto, tal vez un if.

# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)