---
title: "How to create a chess app in flutter"
date: 2022-02-02
draft: false
tags: ["Flutter", "App", "Chess", "Programming"]
author: "Misael Armando"
---

# How to create a chess app in flutter

In this post, I'm going to explain how to create a basic chess app with Flutter. For this app I used the **RiverPod** state manager, you probably already know what it is, if not, just click on this [link](https://riverpod.dev/) to learn more about it. 


## Creating the project 

To create a Flutter project we simply write:
``` bash
flutter create chess_app
```

## How to create a chess board app in flutter 
First of all to create a chess we need the chessboard, for that, fortunately [Deven Joshi](https://pub.dev/publishers/joshi.dev/packages) created a package/widget that allows us to create and play in a chessboard, that is called  [flutter_chess_board](https://pub.dev/packages/flutter_chess_board) package.

### 1. Installing the package
To install the package to your flutter app, just run: 
``` shell
flutter pub add flutter_chess_board
```


### 2. Creating the chessboard
With this package it's really easy to create a chessboard.

* First of all, in the _main.dart_ file add the installed package using: 
```dart
import 'package:flutter_chess_board/flutter_chess_board.dart';
```


* Then (after adding the _material.dart_ package), I created a new statelessWidget called **ChessApp**, and added the **ChessBoard** Widget, in the end the file was like this: 

**main.dart**
``` dart
import 'package:flutter/material.dart';
import 'package:flutter_chess_board/flutter_chess_board.dart';

class ChessApp extends StatelessWidget {
  const ChessApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      themeMode: ThemeMode.system,
      debugShowCheckedModeBanner: false,
      title: 'Chess App',
      theme: ThemeData(
        brightness: Brightness.dark,
        primaryColorDark: primaryColor,
      ),
      home: const ChessBoard(title: 'Chess App'),
    );
  }
}

class ChessBoard extends StatefulWidget {
  const ChessBoard({super.key, required this.title});

  final String title;

  @override
  ChessBoardState createState() => ChessBoardState();
}

class MyHomePageState extends State<ChessBoard>{
  // Color theme variables
  const Color labelText = Color.fromRGBO(180, 180, 180, 1);
  const Color primaryColor = Color.fromRGBO(24, 24, 24, 1);
  const Color appBarBg = Color.fromRGBO(48, 48, 48, 1);
  
  ChessBoardController chessBoardController = ChessBoardController();
  List<String?> sanList = [''];


  @override
  void initState() {
	super.initState();
    chessBoardController.addListener(() {
      setState(() {
        sanList = chessBoardController.getSan();
      });
    });
  }

  @override
  void dispose() {
    super.dispose();
    chessBoardController.dispose();
  }

return Scaffold(
    backgroundColor: Theme.of(context).primaryColorDark,
    appBar: AppBar(
		title: Text(
          widget.title,
          style: const TextStyle(color: labelText, fontWeight: FontWeight.bold),
        ),
        backgroundColor: appBarBg,
    ),
    body: SafeArea(
	    child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: <Widget>[
            Container(
              margin: const EdgeInsets.only(top: 10, left: 4, right: 4),
              // Creates a scrollable horizontal list
              child: SingleChildScrollView(
                // Scrolls automatically when a new item is added
                reverse: true,
                scrollDirection: Axis.horizontal,
                // Shows a text of moves that were made
                child: RichText(
                  text: sanList.isNotEmpty
                      ? TextSpan(children: <TextSpan>[
                          TextSpan(
                              text: sanList.take(sanList.length - 1).join(" "),
                              style: const TextStyle(color: labelText)),
                          TextSpan(
                              text: '  ${sanList.last}',
                              style:
                                  const TextStyle(fontWeight: FontWeight.bold)),
                        ])
                      : const TextSpan(text: ""),
                ),
              ),
            ),
            _buildChessBoard(),
          ],
        ),
      ),
    );what is a san in chess
}

```

**\_buildChessBoard()**
``` dart 
Widget _buildChessBoard() {
    return Column(
      children: [
        ChessBoard(
          size: MediaQuery.of(context).size.width,
          controller: chessBoardController,
		  boadOrientation: PlayerColor.white,
		  boadColor: BoardColor.darkBrown,
        ),
      ],
    );
}

```

Let's break it down:
* `chessBoard` has a`ChessBoardController` widget, which is responsible for manipulating the chessboard programmatically.
* `ChessBoard` widget, creates the chessboard.
* `boardOrientation:` defines the orientation of the chessboard, meaning it can be chance the white pieces to show at the bottom and the black ones at the top, and vise-versa.
* `boardColor:` defines the color of the chessboard.

That's all we need to create a playable chessboard. But I also thought it would be nice to add the ability to see the chess moves. For that, we want to access the chessboard SAN.

What's a SAN? Well a SAN stands for Standard Algebraic Notation. It's basically a notation that allows you to know what moves were made during a chess game. Fortunately the **chessBoardController** has SAN list that we can use in our code. To get it we used the `getSan()` function.

The **chessBoardController** also has a function that always listens to game changes, which we used, in the code, to update the `sanList` list variable, every time a change is detected.

The _flutter_chess_board_ package allows you to do many others things. If you want you can add a timer, a back e forth button, a pause button, and many more things to make it look like Chess.com or lichess.

I hope you like this article, see you next time!
