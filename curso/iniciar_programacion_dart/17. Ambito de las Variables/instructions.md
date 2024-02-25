# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

## Ámbito de las Variables

Ahora que estás compartimentando tu código en bloques separados, es hora de que discutamos cómo afectará a las variables que creas y utilizas. Cada variable que declares tiene un ámbito. El ámbito de una variable define qué partes de tu código pueden "verla". En la mayoría de las situaciones, puedes contar con que las llaves rizadas sean el borde del ámbito, lo que significa que si defines una variable entre llaves rizadas de apertura y cierre, su ámbito se limita a ese bloque de código y a cualquier bloque anidado dentro de él.

### Variables Locales

Un ejemplo o dos te ayudarán a visualizar el concepto:

```dart
void main() {
  String name = "Jack";
  print(name);
}
```

Aquí, la variable `name` está definida dentro de la función `main()`, entre las llaves rizadas de apertura y cierre de la función. Es una variable local para `main()`. La llamada a `print()` tiene acceso a `name` porque existe dentro de ese mismo ámbito.

Pero, ¿qué tal esto?

```dart
void main() {
  print(name);
}

void createName() {
  String name = "Jack";
}
```

Esta vez, `name` se crea en el cuerpo de `createName()`. Es local y solo se puede acceder dentro de esa función. Si intentas acceder a `name` en `main()`, o desde cualquier otra función excepto `createName()`, te resultará imposible. La variable tiene ámbito de función.

### ¿Qué Tan Local Puede Ser?

Las variables pueden tener un ámbito incluso más específico que a nivel de función. Echa un vistazo a este ejemplo:

```dart
void main() {
  bool adult = false;
  
  if (!adult) {
    int age = 15;
  }
  
  if (age >= 21) {
    adult = true;
  }
}
```

Este código no tiene mucho sentido, pero ilustra el punto que estamos haciendo. Si pones ese código en el editor de código, encontrarás un error en la segunda declaración `if`. Ese `if` no puede ver `age`, porque `age` se definió dentro del primer bloque de código `if` y es local a ese bloque. La variable `adult` tiene ámbito de función, por lo que se puede manipular en cualquier lugar de la función, incluidos los bloques `if`.

### El Gran Cuadro

También es posible que las variables tengan un ámbito más global. Una variable declarada fuera de cualquier bloque de código es una variable de nivel superior, accesible en cualquier lugar del archivo actual. Por supuesto, usando nuestro editor de código interactivo, solo tienes un archivo, por lo que las variables de nivel superior pueden ser accesibles por todo tu código.

```dart
int age = 15;

void main() {
  bool adult;
  
  if (age >= 21) {
    adult = true;
  } else {
    adult = false;
  }
  
  printAgeCategory(adult);
}

void printAgeCategory(bool adult) {
  if (adult) {
    print("Adulto, edad $age.");
  } else {
    print("Menor, edad $age.");
  }
}
```

Lo primero que hay que notar aquí es que `age` es accesible en todas partes. Se puede ver en `main()` y en `printAgeCategory()` porque es una variable de nivel superior.

La variable `adult` es un poco más interesante. Originalmente se definió dentro del ámbito de `main()`, entonces, ¿cómo se puede acceder en `printAgeCategory()`? La respuesta es que no se puede. La función `printAgeCategory()` toma un parámetro booleano que también se llama `adult`, pero podría haber tenido cualquier nombre. Cuando `main()` llama a `printAgeCategory()`, pasa el valor de la variable local `adult` de `main()`, que es `false`. Ese valor (el argumento) se asigna al parámetro `adult` de `printAgeCategory()`, que se convierte en una variable local dentro de `printAgeCategory()`. Por lo tanto, son dos variables separadas que tienen el mismo nombre.

Veámoslo con un cambio de nombre para ver si aclara las cosas:

```dart
int age = 15;

void main() {
  bool adult;
  
  if (age >= 21) {
    adult = true;
  } else {
    adult = false;
  }
  
  printAgeCategory(adult);
}

void printAgeCategory(bool isAdult) {
  if (isAdult) {
    print("Adulto, edad $age.");
  } else {
    print("Menor, edad $age.");
  }
}
```

Ahora, el parámetro de la función se llama `isAdult`, pero eso no cambia cómo funciona el código. Llamar a `printAgeCategory(adult)` aún pasa cualquiera que sea el valor actual de la variable local `adult` de `main()`, porque `adult` se resuelve a su valor antes de que se haga la llamada a `printAgeCategory()`. Se envía `true` o `false` a `printAgeCategory()` y se asigna a la variable local de esa función, ahora llamada `isAdult`. Observa que no fue un problema reutilizar el nombre `adult`, y de hecho sucede todo el tiempo en el código del mundo real, pero lo hemos desambiguado aquí por claridad instructiva.

### Siempre Verifica el Ámbito

Es muy importante que cuando leas código (tuyo o de otra persona), siempre que veas que se accede a una variable, tómate un momento para descubrir el ámbito de esa variable. Puede haber cualquier cantidad de variables con el mismo nombre en un programa, así que debes estar seguro de cuál estás mirando.

```dart
int age = 15;

void main() {
  int age = 30;
  
  print(age);
}
```

¿Qué imprime este código? Hay una variable `age` definida a nivel superior, y otra definida como variable local dentro de `main()`. En este caso, la salida será 30. Cuando Dart intenta resolver una variable, primero verifica el ámbito más local y luego se expande hacia arriba. De hecho, la variable local `age` oculta completamente la variable de nivel superior dentro de `main()`. No hay forma de referirse a la versión de nivel superior, porque Dart siempre asumirá que estás intentando acceder a la local. En una situación como esta, necesitarías cambiar el nombre de una de las variables para acceder a ambas.


# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)