
# Switch

La instrucción `if` es probablemente la estructura de control más común que usarás al programar con Dart, y puede manejar la mayoría de los trabajos, pero cuando necesitas tomar una decisión entre un gran número de posibilidades, `if` puede volverse engorroso.

## No es la Mejor Manera
Supongamos que estás escribiendo un programa para usuarios que juegan un juego de rol de fantasía. Tu programa sugiere armas apropiadas para un personaje según la raza de fantasía que el jugador ha elegido jugar.

```dart
void main() {
  String razaPersonaje = "elfo";

  if (razaPersonaje == "enano") {
    print("Hacha de Batalla");
  } else if (razaPersonaje == "elfo") {
    print("Arco Largo");
  } else if (razaPersonaje == "trasgo") {
    print("Espada Corta");
  } else if (razaPersonaje == "mediano") {
    print("Daga");
  } else if (razaPersonaje == "humano") {
    print("Espada Larga");
  } else if (razaPersonaje == "orco") {
    print("Maza");
  } else {
    print("Garrote");
  }
}
```

Esta gran cantidad de declaraciones `if`, `else if` y `else` hace una recomendación de arma para seis razas de personajes diferentes y ofrece un garrote en caso de que el jugador haya elegido algo más. El código funciona y hace bien su trabajo. Pero, ¿podemos hacerlo mejor?

## Una Mejor Manera
¡Introduciendo la instrucción `switch`! Sí, `switch` fue diseñado para manejar exactamente este tipo de situaciones, y con menos escritura:

```dart
void main() {
  String razaPersonaje = "elfo";
  
  switch (razaPersonaje) {
    case "enano":
      print("Hacha de Batalla");
      break;
    case "elfo":
      print("Arco Largo");
      break;
    case "trasgo":
      print("Espada Corta");
      break;
    case "mediano":
      print("Daga");
      break;
    case "humano":
      print("Espada Larga");
      break;
    case "orco":
      print("Maza");
      break;
    default:
      print("Garrote");
  }
}
```

Usar la instrucción `switch` es un poco más sucinto. No necesariamente usa menos líneas, pero es más fácil ver qué opciones se manejan con solo un vistazo.

En los paréntesis que siguen a la palabra clave `switch`, especificas la variable a examinar. Para cada valor que deseas admitir, incluyes una palabra clave `case`, seguida inmediatamente por un valor válido. Si el valor de la variable coincide con algún caso en particular, se ejecutan las instrucciones después de los dos puntos (`:`) de ese caso. Cuando se encuentra la palabra clave `break`, Dart sale de la instrucción `switch`, continuando la ejecución debajo de la llave de cierre.

El caso `default`, que no requiere un `break`, es opcional, pero actúa de manera similar a una declaración `else` en el sentido de que maneja el caso cuando todas las pruebas anteriores son `false`. Si `razaPersonaje` no coincide con ninguna de las razas especificadas, se ejecutarán las instrucciones `default`.

## ¿Poner o no poner Break?
Hay momentos en los que puedes omitir la instrucción `break` en un `case`. En nuestro juego de fantasía ficticio, tal vez quieras manejar el resultado de un lanzamiento de dados durante una batalla:

```dart
void main() {
  int tiradaAtaque = 5;
  
  switch (tiradaAtaque) {
    case 1:
    case 2:
    case 3:
      print("¡Fallaste!");
      break;
    case 4:
    case 5:
    case 6:
      print("¡Diste en el blanco!");
      break;
  }
}
```

Aquí, si `tiradaAtaque` es 1, Dart comienza ejecutando ese caso, pero no encuentra un `break`, así que _cae a través_ hasta el siguiente caso hasta que se encuentre un `break`. Un resultado de 1, 2 o 3 resultará en un fallo, mientras que un resultado de 4, 5 o 6 no. Esta vez no se proporciona una cláusula `default` porque un lanzamiento de ataque en este juego ficticio siempre debería estar entre 1 y 6.

