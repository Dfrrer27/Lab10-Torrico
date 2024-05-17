# Lab10-Torrico
LABORATORIO 10 DEL CURSO DE PROGRAMACIÓN EN MOVILES MULTIPLATAFORMA

Ejercicio 1:

    import 'package:flutter/material.dart';
    
    void main() {
      runApp(MyApp());
    }
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Flutter Demo',
          theme: ThemeData(
            primarySwatch: Colors.blue,
          ),
          home: MyHomePage(),
        );
      }
    }
    
    class MyHomePage extends StatelessWidget {
      final List<Map<String, String>> items = [
        // Alimentos
        {
          'category': 'Alimentos',
          'name': 'Manzana',
          'image': 'assets/images/apple.png',
        },
        {
          'category': 'Alimentos',
          'name': 'Banana',
          'image': 'assets/images/banana.png',
        },
        // Animales
        {
          'category': 'Animales',
          'name': 'Perro',
          'image': 'https://example.com/dog.png',
        },
        {
          'category': 'Animales',
          'name': 'Gato',
          'image': 'https://example.com/cat.png',
        },
        // Lugares
        {
          'category': 'Lugares',
          'name': 'París',
          'image': 'assets/images/paris.png',
        },
        {
          'category': 'Lugares',
          'name': 'Nueva York',
          'image': 'assets/images/nyc.png',
        },
      ];
    
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Lista de Categorías'),
          ),
          body: ListView.builder(
            itemCount: items.length,
            itemBuilder: (context, index) {
              return ListItem(
                category: items[index]['category']!,
                name: items[index]['name']!,
                image: items[index]['image']!,
              );
            },
          ),
        );
      }
    }
    
    class ListItem extends StatelessWidget {
      final String category;
      final String name;
      final String image;
    
      ListItem({
        required this.category,
        required this.name,
        required this.image,
      });
    
      @override
      Widget build(BuildContext context) {
        TextStyle textStyle;
    
    switch (category) {
      case 'Alimentos':
        textStyle = TextStyle(
          fontFamily: 'OpenSans',
          fontSize: 20,
          fontWeight: FontWeight.bold,
        );
        break;
      case 'Animales':
        textStyle = TextStyle(
          fontFamily: 'Lato',
          fontSize: 20,
          fontWeight: FontWeight.bold,
        );
        break;
      case 'Lugares':
        textStyle = TextStyle(
          fontFamily: 'Ubuntu',
          fontSize: 20,
          fontWeight: FontWeight.bold,
        );
        break;
      default:
        textStyle = TextStyle(
          fontSize: 20,
          fontWeight: FontWeight.bold,
        );
    }
    
    return ListTile(
      leading: image.startsWith('http')
          ? Image.network(image)
          : Image.asset(image),
      title: Text(name, style: textStyle),
    );
      }
    }

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

Ejercicio 3:

    import 'package:flutter/material.dart';
    import 'package:flutter_svg/flutter_svg.dart';
    import 'package:google_fonts/google_fonts.dart';
    
    void main() {
      runApp(GalleryApp());
    }
    
    class GalleryApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Image Gallery',
          theme: ThemeData(
            primarySwatch: Colors.blue,
          ),
          home: GalleryScreen(),
        );
      }
    }
    
    class GalleryScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Image Gallery'),
          ),
          body: ListView(
            padding: EdgeInsets.all(8.0),
            children: [
              _buildImageCard('assets/images/pan.jpeg', 'ochito.jpeg', GoogleFonts.merriweather(fontSize: 18)),
              _buildImageCard('assets/images/josua.png', 'benja.png', GoogleFonts.lato(fontSize: 18)),
              _buildImageCard('assets/images/amigo.svg', 'max.svg', GoogleFonts.roboto(fontSize: 18)),
            ],
          ),
        );
      }
    
      Widget _buildImageCard(String imagePath, String imageName, TextStyle textStyle) {
        Widget imageWidget;

        if (imagePath.endsWith('.svg')) {
          imageWidget = SvgPicture.asset(imagePath, width: 200, height: 200);
        } else {
          imageWidget = Image.asset(imagePath, width: 200, height: 200);
        }
    
        return Card(
          margin: EdgeInsets.symmetric(vertical: 10),
          child: Padding(
            padding: EdgeInsets.all(8.0),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                imageWidget,
                SizedBox(height: 8),
                Text(imageName, style: textStyle),
              ],
            ),
          ),
        );
      }
    }
