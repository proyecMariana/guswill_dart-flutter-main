# Cadenas de Texto

En lecciones anteriores, ya has usado cadenas de texto varias veces, ¡pero te sorprenderá saber que hay más por conocer!

> **Pista:** Siempre hay más por conocer.

## Definición de Cadenas
Las cadenas de texto son cómo llevas un seguimiento del texto en tus programas. Puedes definir cadenas de texto de varias maneras. Puedes usar comillas simples o dobles para definir una `String`:

```dart
void main() {
  String mensaje1 = "Dart es genial.";
  String mensaje2 = 'JavaScript no es genial.';
  
  print(mensaje1);
  print(mensaje2);
}
```

## Vecinos
Las literales de cadena adyacentes se concatenan automáticamente:

```dart
void main() {
  print("¡Hola, " "Mundo!");
}
```

## Diálogo
¿Qué pasa si quieres comillas _dentro_ de tus cadenas? ¿No confundirá eso a Dart? Sí, en efecto. Intenta esto:

```dart
void main() {
  print(""¿Podría Dart salvar mi matrimonio?" preguntó.);
}
```

¡Errores! ¡Advertencias! La solución en este caso es definir la cadena con comillas simples:

```dart
void main() {
  print('"¿Podría Dart salvar mi matrimonio?" preguntó.');
}
```

## Contracciones
¿Qué pasa si también tienes un apóstrofe ahí? ¡Un apóstrofe es el mismo carácter que una comilla simple!

```dart
void main() {
  print('"Ella no vale la pena," respondió su amigo.');
}
```

Más problemas. También puedes arreglar eso. Puedes _escapar_ el apóstrofe usando una barra invertida (`\`):

```dart
void main() {
  print('"Ella no vale la pena," respondió su amigo.');
}
```

## La Necesidad de Escapar
La barra invertida que precede al apóstrofe le dice a Dart que es solo un apóstrofe y no debe interpretarse como un delimitador de cadena. De hecho, podrías definir la cadena con comillas dobles, y escaparlas dentro de la cadena en su lugar:

```dart
void main() {
  print("\"Ella no vale la pena,\" respondió su amigo.");
}
```

Una vez más, hay más de una manera de pelar un gato.

> **Nota:** No debes pelar gatos.

## Interpolación
El signo de dólar (`$`) es otro carácter especial en el contexto de las cadenas de texto de Dart. Se usa para hacer _interpolación de cadenas_. Aquí tienes un ejemplo:

```dart
void main() {
  String nombre = "Amber";
  print("$nombre es mi mejor amiga.");
}
```

Cuando Dart encuentra un `$` en la cadena, espera que lo que sigue sea una variable, luego toma el valor de esa variable e lo inserta en la cadena. Resulta que esto es mucho más agradable que usar el operador `+` para concatenar:

```dart
void main() {
  String nombre = "Amber";
  print(nombre + " es mi mejor amiga.");
}
```

En el código Dart, siempre debes preferir usar interpolación de cadenas cuando sea posible, ya que conduce a un código mucho más legible.

### Muestra el Dinero
¡Pero espera! ¿Ahora no puedo usar un signo de dólar en mis cadenas?

```dart
void main() {
  print("El tapete cuesta $4.99.");
}
```

Más errores. Aquí tienes algunas soluciones para ese problema:

```dart
void main() {
  print("El tapete cuesta \$4.99.");
  print(r"El tapete cuesta $4.99.");
}
```

Puedes escapar el signo de dólar con una barra invertida, o puedes preceder la cadena con una "r" en minúscula para decirle a Dart que la cadena debe considerarse _cruda_, lo que significa que no se realizará interpolación de cadenas dentro de ella.

### Rutas
Ahora que sabes que la barra invertida se usa para escapar caracteres especiales, debes estar preguntándote cómo puedes incluir una barra invertida en tu cadena. Eso no se presenta mucho bajo la mayoría de las circunstancias, pero ¿no puedes simplemente vivir el resto de tu vida sin imprimir barras invertidas, verdad? De hecho, puedes usar una barra invertida para escapar una barra invertida, así:

```dart
void main() {
  print("Ruta de Windows: C:\\Program Files\\Dart");
}
```

Ejecuta ese código y verás la barra invertida aparecer justo como esperabas.

### Más Interpolación
Hablemos un poco más sobre la interpolación de cadenas. Siempre que quieras insertar el valor de una variable simple, como `nombre`, en una cadena, el signo de dólar te sacará del apuro. Si quieres hacer algo más complejo, como una verdadera expresión de código, necesitas agregar un par de llaves:

```dart
void main() {
  print("16 + 4 = ${16 + 4}");
}
```

Esta vez, Dart imprimirá el problema matemático, luego, cuando encuentre la expresión interpolada, realizará el cálculo y devolverá el resultado, insertándolo en la cadena en lugar de la expresión. Ejecuta el código para verlo en acción.

### Expresiones Interpoladas
¿Qué otros tipos de expresiones son posibles allí? Casi cualquier expresión Dart válida. Mira este ejemplo:

```dart
void main() {
  String nombre = "Rachel";
  
  print("$nombre empieza con ${nombre[0]}.");
  print("Su nombre contiene ${nombre.length} letras.");
}
```

¡Bastante ingenioso, ¿eh? Puedes usar el operador de índice (`[]`), manifestado por corchetes, para acceder a caracteres individuales dentro de una variable de cadena. Para obtener la primera letra de `nombre`, usas la expresión `nombre[0]`. ¿Por qué no `nombre[1]`? En la mayoría de los lenguajes de programación, el conteo típicamente comienza desde 0. Esto hace que iterar sobre una serie de valores sea más conveniente, como descubrirás en una lección posterior sobre bucles. "R" está en la posición 0 en la cadena `nombre`.

La segunda llamada a `print()` interpola otro nuevo tipo de expresión: `nombre.length`. Las variables de cadena tienen _propiedades_ en ellas. Estas propiedades contienen información pertinente a las variables de cadena, como cuántos

 caracteres están conteniendo. Accedes a estas propiedades usando el operador de punto (`.`).

## Hora de Jugar
> **Reto:** Elabora un script en Dart donde definas cuatro variables de entrada. Luego, realiza operaciones matemáticas y manipulación de cadenas directamente con estas variables, utilizando la función print para mostrar los resultados.
```dart
void main() {
  // Definir cuatro variables de entrada
  int numero1 = 10;
  int numero2 = 5;
  double decimal = 3.5;
  String cadena = "Dart";

  // Realizar operaciones matemáticas y de manejo de cadena de forma directa
  int suma = numero1 + numero2;
  double multiplicacion = numero1 * decimal;
  String concatenacion = cadena + " es genial";

  // Mostrar los resultados utilizando la función print
  print("La suma de $numero1 y $numero2 es: $suma");
  print("El resultado de multiplicar $numero1 por $decimal es: $multiplicacion");
  print("Cadena concatenada: $concatenacion");
}

```
