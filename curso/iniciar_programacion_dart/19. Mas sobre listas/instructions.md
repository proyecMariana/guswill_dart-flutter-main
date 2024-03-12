# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)

# Más sobre Listas

¡Bienvenido de nuevo! Y ahora, más sobre listas.

Agregar y Eliminar Elementos
A veces no tienes todos los elementos a mano en el momento en que creas tu lista. Tal vez un usuario te está dando elementos uno a uno, o tal vez estás generando cada elemento con código. En casos como estos, necesitas poder agregar elementos a una lista existente:

```dart
void main() {
  List<String> estudiantes = [];

  String entradaUsuario = "María";

  estudiantes.add(entradaUsuario);

  entradaUsuario = "Jon";

  estudiantes.add(entradaUsuario);

  print(estudiantes);
}
```

En este código, primero creamos una lista vacía, especificando que sus elementos serán cadenas. Luego simulamos la entrada del usuario usando una variable String, adecuadamente llamada `entradaUsuario`. Una vez que tiene un nombre, se agrega a la lista mediante el método `add()`. Reutilizamos `entradaUsuario` asignándole una nueva cadena, luego agregamos esa a `estudiantes`. Finalmente, imprimimos toda la lista en la consola para mostrarla.

Desafortunadamente, Jon es un estudiante terrible, así que decides expulsarlo de la clase. Veamos cómo podemos eliminarlo de la lista de estudiantes:

```dart
void main() {
  List<String> estudiantes = ["María", "Jon", "Sally", "Bob"];
  print(estudiantes);

  estudiantes.remove("Jon");
  print(estudiantes);
}
```

¡Y se ha ido! Adiós, Jon. No te extrañaremos.

Es importante notar que cuando eliminamos al estudiante en el índice 1, los otros nombres se reorganizaron para llenar ese espacio, por lo que el índice de Sally se convirtió en 1 y el de Bob en 2. Los espacios vacíos no son tolerados en una Lista de Dart. De hecho, mejoremos nuestra lógica de impresión para hacer esto más claro:

```dart
void main() {
  List<String> estudiantes = ["María", "Jon", "Sally", "Bob"];
  printLista(estudiantes);

  print('');

  estudiantes.remove("Jon");
  printLista(estudiantes);
}

void printLista(List<String> lista) {
  for (int i = 0; i < lista.length; i++) {
    print("$i: ${lista[i]}");
  }
}
```

Reemplazamos la llamada estándar a `print()` con nuestra propia función personalizada, `printLista()`. Esto imprimirá cualquier lista de cadenas junto con el índice de cada elemento, representado por `i`. Esto resaltará el efecto de la expulsión de Jon. Ten en cuenta que imprimimos una cadena vacía con `print('')` solo para crear un espacio en blanco vertical entre las dos versiones de la lista.

Ordénalo
Como has visto, la estructura de datos de Lista de Dart te ayuda a mantener las cosas organizadas cuando tienes una gran cantidad de datos para almacenar. También proporciona una serie de métodos destinados a ayudarte a modificar el contenido y el orden de los elementos. Uno de los más útiles es el método `sort()`:

```dart
void main() {
  List<String> estudiantes = ["María", "Jon", "Sally", "Bob"];
  print(estudiantes);

  estudiantes.sort();
  print(estudiantes);
}
```

Sí, Jon ha vuelto. Resulta que su padre fue un gran donante para la escuela, así que simplemente tendrás que lidiar con su basura.

Este código imprime la lista antes y después de una ordenación para ilustrar los cambios. El método `sort()` ordena las cadenas alfabéticamente y los números numéricamente. Es posible personalizar el comportamiento de la ordenación, e incluso es necesario hacerlo para tipos de elementos más complejos, pero aún no vamos a cubrir eso.

Del Principio al Fin
A veces necesitas recuperar solo el primer o el último elemento de una lista:

```dart
List<String> estudiantes = ["María", "Jon", "Sally", "Bob"];

// de la manera tonta
String primero = estudiantes[0];    // María
String último = estudiantes[3];      // Bob
```

Ciertamente puedes acceder al primer y al último elemento por índice, pero esta no es siempre la mejor manera. El primer elemento en una lista no vacía siempre estará en el índice 0, pero ¿qué hay del último? Es común no ser consciente de cuántos elementos tiene la lista al consultar el último. Podrías hacer que el índice sea relativo, así:

```dart
// de manera menos tonta
String último = estudiantes[estudiantes.length - 1];    // Bob
```

El índice del último elemento siempre será uno menos que la longitud completa de la lista (ya que los índices comienzan en 0), pero este método no es muy legible.

¡Dart al rescate! Puedes acceder a estos elementos a través de propiedades en Lista:

```dart
// la mejor manera
String primero = estudiantes.first;    // María
String último = estudiantes.last;      // Bob
```

Ahora es fácil ver de un vistazo qué está sucediendo aquí. Así como usar `isEmpty` en lugar de verificar manualmente la longitud de una lista es una buena práctica, también lo es usar `first` y `last` en lugar de adivinar los índices.

Otra Forma de Iterar
Si alguna vez te

 cansas de iterar sobre listas con enteros e índices, puedes probar otra forma de bucle: el bucle `for...in`. Esta es una construcción de bucle más conveniente en algunos aspectos, pero a costa de cierta flexibilidad. El bucle `for...in` siempre recorre cada elemento de una lista, y no proporciona una forma fácil de saber en qué índice estás operando. A menudo, estas limitaciones no son un problema.

Reescribamos la función `printLista()` anterior, esta vez usando `for...in`:

```dart
void main() {
  printLista(["Dart", "JavaScript", "TypeScript", "C++"]);
}

void printLista(List<String> lista) {
  for (String elemento in lista) {
    print(elemento);
  }
}
```

Con esta versión, la variable `elemento` apunta a cada uno de los elementos de la lista en secuencia, uno por cada iteración. La primera vez que se ejecuta el cuerpo del bucle, `elemento` será "Dart", luego "JavaScript", y así sucesivamente. Si la lista no tiene elementos, el bucle no se ejecutará en absoluto, al igual que cuando estamos verificando manualmente la longitud de la lista. Este bucle es genial cuando quieres iterar sobre una lista completa y realizar alguna acción en cada elemento.

# Ejemplo práctico
```dart
import 'dart:convert';
import 'package:http/http.dart' as http;

void main() {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/albums'); // Reemplaza esto con tu URL real

  http.get(url).then((response) {
    if (response.statusCode == 200) {
      // Si la solicitud fue exitosa (código de estado 200)
      List<dynamic> data = json.decode(response.body);
      // Itera sobre cada registro
      for (var registro in data) {
        int userId = registro['userId'];
        int id = registro['id'];
        String title = registro['title'];
        print('userId: $userId, id: $id, title: $title');
      }
    } else {
      // Si la solicitud no fue exitosa
      print('Error al obtener datos: ${response.statusCode}');
    }
  }).catchError((error) {
    // Manejar errores de solicitud
    print('Error: $error');
  });
}
 
import 'dart:convert';
import 'package:http/http.dart' as http;

void main() {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/albums');

  http.get(url).then((response) {
    if (response.statusCode == 200) {
      List<dynamic> data = json.decode(response.body);
      mostrarMenu(data);
    } else {
      print('Error al obtener datos: ${response.statusCode}');
    }
  }).catchError((error) {
    print('Error: $error');
  });
}

void mostrarMenu(List<dynamic> data) {
  print('--- Menú ---');
  print('1. Listar todos los registros');
  print('2. Listar registros pares');
  print('3. Listar registros impares');
  print('4. Mostrar los 50 primeros registros');
  print('5. Salir');

  var opcion = '3'; // Asignamos directamente la opción 1

  switch (opcion) {
    case '1':
      listarRegistros(data);
      break;
    case '2':
      listarRegistrosPares(data);
      break;     
    case '3':
      listarRegistrosImpares(data);
      break;        
  }
}

void listarRegistros(List<dynamic> data) {
  print('----------------------');
  print('Existen ${data.length} registros disponibles');
  print('| userId | id | title');
  print('----------------------');
  for (var registro in data) {
    int userId = registro['userId'];
    int id = registro['id'];
    String title = registro['title'];
    print('| $userId | $id | $title');
  }
}

void listarRegistrosPares(List<dynamic> data) {
  print('----------------------');
  print('Existen ${data.length} registros disponibles');
  print('| userId | id | title');
  print('----------------------');
  for (var registro in data) {
    if (registro['id'] % 2 == 0) {
      int userId = registro['userId'];
      int id = registro['id'];
      String title = registro['title'];
      print('| $userId | $id | $title');
    }
  }
}

void listarRegistrosImpares(List<dynamic> data) {
  print('----------------------');
  print('Existen ${data.length} registros disponibles');
  print('| userId | id | title');
  print('----------------------');
  for (var registro in data) {
    if (registro['id'] % 2 != 0) {
      int userId = registro['userId'];
      int id = registro['id'];
      String title = registro['title'];
      print('| $userId | $id | $title');
    }
  }
}

```
# [Regresar al menú](https://github.com/proyecMariana/guswill_dart-flutter-main/tree/main)