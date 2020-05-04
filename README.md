# paparazzi

A Flutter package to convert widget to an image.

## Example

```dart
import 'package:flutter/material.dart';
import 'package:paparazzi/paparazzi.dart';

// ...


void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Paparazzi',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Demo Paparazzi Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;


  @override
  Widget build(BuildContext context) {
      var container = Container(
          width:200,
          height:200,
          color:Colors.red
      );
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(children:[
            container,
        ])
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: ()async {
            Uint8List pngBytes =await Paparazzi.shot(container);
            // do what you want with that; with Image.memory for example
        },
        tooltip: 'Pint button',
        child: Icon(Icons.printer),
      ),
    );
  }
}

```
