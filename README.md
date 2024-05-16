# Lab10-Torrico
LABORATORIO 10 DEL CURSO DE PROGRAMACIÓN EN MOVILES MULTIPLATAFORMA

Ejercicio 2:

    //ignore_for_file: prefer_const_constructors
    
    import 'package:flutter/material.dart';
    
    void main() {
      runApp(MyApp());
    }
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          home: Producto(),
        );
      }
    }
    
    class Producto extends StatelessWidget {
    
      @override
      Widget build(BuildContext context) {
        return Scaffold(
           appBar: AppBar(
            title: Text('Detalles del Producto'),
          ),
          body: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              crossAxisAlignment: CrossAxisAlignment.center,
              children: [
                Image.asset('assets/images/zapatillas.PNG'),
                SizedBox(height: 20),
                Text(
                  'Nombre del Producto',
                  style: TextStyle(
                    fontFamily: 'Montserrats',
                    fontSize: 24,
                    fontWeight: FontWeight.bold,
                  ),
                ),
                SizedBox(height: 10),
                Text(
                  '\$109.99',
                  style: TextStyle(
                    fontFamily: 'Roboto',
                    fontSize: 18,
                  ),
                ),
                SizedBox(height: 10),
                Text(
                  'Una breve descripción del producto.',
                  style: TextStyle(
                    fontFamily: 'Nunito',
                    fontSize: 16,
                  ),
                ),
              ],
            ),
          ),
        );
      }
}
