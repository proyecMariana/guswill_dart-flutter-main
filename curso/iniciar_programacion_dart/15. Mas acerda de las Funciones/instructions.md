# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

## Más sobre Parámetros de Funciones

A menudo es útil hacer que algunos parámetros de función sean opcionales, o requerir que el llamante de la función se refiera a un parámetro por su nombre para obtener claridad adicional. En esta lección, exploraremos tus opciones con respecto a los parámetros de función con más detalle.

Hay dos tipos de parámetros opcionales en las funciones de Dart. Hay parámetros opcionales posicionales y parámetros opcionales nombrados.

### Parámetros Opcionales Posicionales

Los parámetros posicionales (opcionales o no) se diferencian por su orden en la lista de parámetros, de la siguiente manera:

```dart
void miFuncion(String param1, int param2, bool param3)
```

Una llamada a una función con una firma como esa podría verse así:

```dart
miFuncion("Bob", 54, true);
```

Dart espera que la función reciba una cadena, un entero y un valor booleano, en ese orden. Si tu llamada a la función mezcla el orden o deja alguno de ellos fuera, el analizador de Dart se quejará.

Hazlo Opcional

Para hacer que este tipo de parámetros sean opcionales, usas corchetes:

```dart
void miFuncion([String? param1, int? param2, bool? param3])
```

Todos los parámetros entre corchetes se consideran opcionales. Ten en cuenta que necesitamos hacer que los tipos de parámetros sean anulables con un ? para que esto funcione correctamente. Ahora, todas estas serían formas válidas de llamar a esta función:

```dart
miFuncion("Bob", 54, true);
miFuncion("Bob", 54);
miFuncion("Bob");
miFuncion();
```

Los argumentos no proporcionados serán nulos, como cualquier otra variable no inicializada y anulable. Dado que estos son parámetros posicionales, el orden aún importa. No puedes llamar a la función y pasar solo el entero, por ejemplo. Aunque si fuera necesario, podrías mantener el orden pasando valores nulos de esta manera:

```dart
miFuncion(null, null, true);
```

Por lo general, este tipo de cosas debería evitarse, ya que hace que la llamada a la función sea críptica. Si regularmente necesitas llamar a una función de esta manera, considera usar parámetros nombrados en su lugar (discutidos a continuación).

Mejores Valores por Defecto

Si nulo no funciona bien como un valor predeterminado para un parámetro opcional posicional, puedes agregar valores predeterminados más sensatos a la declaración de la función:

```dart
void miFuncion([String name = "Jim", int age = 30, bool retired = false])
```

Ahora, miFuncion() usará estos valores predeterminados para cualquier argumento faltante. Ten en cuenta que esta versión tiene nombres de parámetros más descriptivos, lo cual es un hábito muy bueno.

### Ejemplo

¡Inténtalo!

```dart
void main() {
  print("Primera ejecución:");
  miFuncion();
  print("\nSegunda ejecución:");
  miFuncion("Bob", 54);
}

void miFuncion([String name = "Jim", int age = 30, bool retired = false]) {
  print(name);
  print(age);
  print(retired);
}
```

### Mezcla de Parámetros Opcionales y Requeridos

Con los parámetros posicionales, es posible que algunos sean opcionales y otros obligatorios, pero los opcionales deben estar al final de la lista:

```dart
void miFuncion(String name, int age, [bool retired = false])
```

En esta versión de la función, el llamante debe proporcionar argumentos para name y age, pero si no se proporciona ningún valor para retired, se establecerá en falso por defecto.

### Parámetros Opcionales Nombrados

Los parámetros opcionales nombrados permiten que los argumentos se pasen en cualquier orden. Se designan con llaves en lugar de corchetes:

```dart
void setFlags({bool? bold, bool? hidden})
```

Los nombres de los parámetros nombrados deben incluirse en la llamada de la función, pero los argumentos pueden pasarse en cualquier orden ya que el nombre servirá como diferenciador. La función setFlags() se puede llamar de estas formas:

```dart
setFlags(bold: true, hidden: true);
setFlags(hidden: true, bold: true);
setFlags(bold: true);
setFlags(hidden: true);
setFlags();
```

Al igual que con la variedad posicional, los argumentos faltantes son simplemente nulos a menos que tengas otros valores predeterminados en su lugar. Si no se proporcionan valores predeterminados, los tipos de parámetros deben ser anulables. Aquí tienes un ejemplo con valores predeterminados:

```dart
void setFlags({bool bold = false, bool hidden = false})
```

Con esa firma, llamar a setFlags() sin argumentos establecerá ambos indicadores en falso.

Puedes especificar que los parámetros nombrados sean requeridos usando la palabra clave required:

```dart
void setFlags({required bool bold, required bool hidden})
```

De esta manera, puedes mantener tus tipos de parámetros no anulables y se requerirá que el llamante pase un valor válido. Puedes hacer que cualquier número de parámetros nombrados sea requerido.

### Ejemplo

¡Inténtalo!

```dart
void main() {
  print("Primera ejecución:");
  setFlags();
  print("\nSegunda ejecución:");
  setFlags(hidden: true);
}

void setFlags({bool bold = false, bool hidden = false}) {
  print(bold);
  print(hidden);
}
```

### Mezcla de Parámetros Opcionales y Requeridos (Revisitado)

Los parámetros opcionales, incluso los nombrados, deben estar al final de la lista si también hay parámetros regulares y requeridos en la firma de una función:

```dart
void miFuncion(String name, int age, {bool retired = false})
```

Llamar a esta función con los tres argumentos se vería así:

```dart
miFuncion("Bob", 54, retired: true);
```

Los parámetros booleanos son excelentes candidatos para ser nombrados, ya que hacen que la llamada a la función sea mucho más clara para cualquier persona que lea el código. Solo recuerda que si no hay un valor predeterminado en la declaración de la función y el tipo del parámetro es anulable, se establecerá en nulo por defecto, lo cual no es un valor booleano válido.

### Mezcla de Parámetros Opcionales Posicionales y Nombrados

Dart no te permitirá hacer esto, así que no lo intentes. Una función puede tener parámetros requeridos y opcionales, pero los parámetros opcionales deben ser todos nombrados o todos posicionales.

# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)