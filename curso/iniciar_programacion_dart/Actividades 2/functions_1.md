import 'dart:convert';
import 'package:http/http.dart' as http;

void sortUsers(String sortBy) {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/users');

  http.get(url).then((response) {
    if (response.statusCode == 200) {
      List<dynamic> users = json.decode(response.body);

      // Ordenar usuarios por nombre o correo electrónico
      users.sort((a, b) {
        if (sortBy.toLowerCase() == 'name') {
          return a['name'].toLowerCase().compareTo(b['name'].toLowerCase());
        } else if (sortBy.toLowerCase() == 'email') {
          return a['email'].toLowerCase().compareTo(b['email'].toLowerCase());
        } else {
          throw ArgumentError('sortBy debe ser "name" o "email"');
        }
      });

      // Mostrar los usuarios ordenados
      print('Usuarios ordenados por $sortBy:');
      for (var user in users) {
        print('Nombre: ${user['name']}, Correo electrónico: ${user['email']}');
      }
    } else {
      print('Error al obtener datos: ${response.statusCode}');
    }
  }).catchError((error) {
    print('Error: $error');
  });
}

void main() {
  // Ordenar usuarios por nombre (Ejemplo)
  sortUsers('name');

  // Ordenar usuarios por correo electrónico (Ejemplo)
  sortUsers('email');
}


import 'dart:convert';
import 'package:http/http.dart' as http;

void filterUsersByCityOrCompany(String filterKey, String filterValue) {
  final url = Uri.parse('https://jsonplaceholder.typicode.com/users');

  http.get(url).then((response) {
    if (response.statusCode == 200) {
      List<dynamic> users = json.decode(response.body);

      // Filtrar usuarios por ciudad o compañía
      List<dynamic> filteredUsers = users.where((user) =>
          user['address']['city'].toLowerCase() == filterValue.toLowerCase() ||
          user['company']['name'].toLowerCase() == filterValue.toLowerCase())
          .toList();

      // Mostrar los usuarios filtrados
      print('Usuarios filtrados por $filterKey "$filterValue":');
      for (var user in filteredUsers) {
        print('Nombre: ${user['name']}, Ciudad: ${user['address']['city']}, Compañía: ${user['company']['name']}');
      }
    } else {
      print('Error al obtener datos: ${response.statusCode}');
    }
  }).catchError((error) {
    print('Error: $error');
  });
}

void main() {
  // Filtrar usuarios por ciudad (Ejemplo)
  filterUsersByCityOrCompany('ciudad', 'Gwenborough');

  // Filtrar usuarios por compañía (Ejemplo)
  filterUsersByCityOrCompany('compañía', 'Romaguera-Crona');
}


void buscarNombresExtremos(List<dynamic> usuarios) {
  if (usuarios.isEmpty) {
    print('No hay usuarios disponibles.');
    return;
  }

  String nombreMasLargo = usuarios.first['name'];
  String nombreMasCorto = usuarios.first['name'];

  for (var usuario in usuarios) {
    String nombre = usuario['name'];
    if (nombre.length > nombreMasLargo.length) {
      nombreMasLargo = nombre;
    }
    if (nombre.length < nombreMasCorto.length) {
      nombreMasCorto = nombre;
    }
  }

  print('Nombre más largo: $nombreMasLargo');
  print('Nombre más corto: $nombreMasCorto');
}
