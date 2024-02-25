
# Bucles For

Es hora de hablar de otra forma de hacer un bucle. ¿Por qué hay tantos tipos diferentes de bucles? Con un poco de ingenio, realmente podrías hacer la mayoría de los trabajos con solo un tipo de bucle, pero algunos tipos son más adecuados para ciertos problemas que otros. No te sientas mal si aún no puedes identificar cuál es el mejor en una situación determinada. Solo tres de nosotros nacimos con ese conocimiento innato, y al resto de ustedes les toca aprender.

## ¿Para qué sirve un Bucle For?
El bucle `for` está hecho a medida para situaciones en las que necesitas una variable de índice. Puede que recuerdes eso de algunas lecciones anteriores. Por convención, a menudo se les llama `i`, que podría significar _índice_. Cuando estás contando algo o necesitas saber dónde cae un valor en una secuencia ordinal, el bucle `for` es el bucle para ti.

Comencemos con el antiguo conocido, contando:

```dart
void main() {
  for (int i = 0; i < 10; i++) {
    print(i);
  }
}
```

Ese es el tipo de bucle `for` más típico que verás. Pueden volverse más complicados, pero esta es la estructura más común. Dentro de los paréntesis que siguen a la palabra clave `for`, colocas tres declaraciones, separadas por punto y coma.

En la primera declaración, tienes la oportunidad de inicializar una variable, o incluso declarar una, como hemos hecho aquí. Con otros tipos de bucles, tenías que declarar e inicializar una variable de índice fuera del contexto del bucle, pero el bucle `for` tiene un lugar especial reservado solo para este tipo de cosas. Además, la variable está _acotada_ al bucle, lo que significa que existe solo dentro del cuerpo del bucle y no es accesible en ningún otro lugar. Inténtalo y prueba `print(i);` después del cuerpo del bucle. No funcionará bien.

En la segunda declaración es donde colocas la expresión booleana que rige si el cuerpo del bucle se ejecutará. Como en otros bucles, si esto se evalúa como `true`, se ejecuta el código del bucle y, si no, la ejecución continúa después de la llave de cierre del bucle. En este ejemplo, puedes pensar en ello como "Si `i` es menor que 10, haz el bucle de nuevo". ¿Rima, verdad? Bonito.

Con la tercera declaración, se espera que proporciones una expresión que mute la variable de índice de alguna manera, siendo la más típica un incremento simple. Cada vez después de la primera vez, este bucle agregará 1 a `i`, y cuando `i` sea igual o supere 10, no habrá más bucles.

### ¿Cuándo Sucede Todo Esto?
Es importante entender la secuencia de operaciones cuando se trata de las tres declaraciones entre paréntesis. La primera vez que Dart encuentra el bucle, sucede la primera declaración, donde se crea `i` y se establece en `0`. Luego se evalúa la expresión booleana. Si es `false`, el cuerpo del bucle nunca se ejecuta. Si es `true`, el cuerpo se ejecuta, pero la tercera declaración no se ejecuta en este momento.

Piénsalo un momento. Si las tres declaraciones `for` sucedieran desde el principio, el primer número impreso sería `1`, pero en la salida, `0` se imprime primero. Esto se debe a que la última declaración se evalúa solo al final del bucle. Si la operación de incremento ocurriera de inmediato, la variable de índice tendría un valor de 1 antes de que `print()` se llamara por primera vez.

### La Salida
Al observar el bucle, uno podría esperar razonablemente que la salida comience con `0` y termine con `10`. Por supuesto, esto solo es razonable si tu comprensión del bucle `for` es superficial, ya que la tuya no lo será por mucho tiempo.

Como `i` comienza en 0 y la operación de incremento no ocurre hasta después de una iteración completa del bucle, `0` es el primer valor que aparece en la consola. Después de imprimir `0`, se evalúa la expresión mutadora y `i` es entonces 1. Luego se evalúa la expresión booleana para determinar si el cuerpo del bucle debe ejecutarse nuevamente. En este caso, como 1 es menor que 10, se ejecuta.

Esto continúa hasta que `i` se convierte en 9. Después de imprimir `9`, se sigue el procedimiento habitual. La variable de índice se incrementa a 10, pero esta vez cuando se evalúa `i < 10`, es `false`, y el bucle ha terminado. Por lo tanto, `9` es el último valor impreso.

## Imprimir de 1 a 10
El siguiente código de ejemplo muestra tres formas diferentes de lograr el noble objetivo de imprimir los valores `1` a `10`:

```dart
void main() {
  for (int i = 1; i < 11; i++) {
    print(i);
  }

  for (int i = 1; i <= 10; i++) {
    print(i);
  }

  for (int i = 0; i < 10; i++) {
    print(i + 1);
  }
}
```

Revisa cada solución y asegúrate de entender cómo producen la misma salida. Ten en cuenta que como `i` es _local_ a cada bucle individualmente, está bien reutilizar el nombre `i`. El primer bucle tiene su propia versión de `i`, que es igual a 10 cuando ese bucle termina, y luego el segundo bucle crea una variable de índice completamente separada que simplemente también se llama `i`.

## ¡Más Cerveza!
El bucle `for` también puede contar hacia atrás. 

```dart
void main() {
  for (int beers = 99; beers > 0; beers--) {
    print("$beers botellas de cerveza en la pared, $beers botellas de cerveza.");
    print("Tomas una, la pasas... ");
    print("${beers - 1} botellas de cerveza en la pared.\n");
  }
}
```

Comienzas la variable de índice, esta vez llamada `beers`, en 99, y en cada iteración del bucle, restas 1 de eso