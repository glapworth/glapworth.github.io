---
title: "Flutter and Android on the TV - An Update"
categories:
  - Programming
tags:
  - flutter
  - androidtv
  - firetv
  - amazon
---

If you read my previous post on developing an Android TV app using Flutter, you'd have noticed that I was a little frustrated
about having to rewrite large portions of the user interface by wrapping a `RawKeyboardListener` in order to support the remote control
D-PAD. 

I stumbled across a post [^1] by Mushthaq Mohammed discussing using Flutter on Android TV and in the article, I found this little 
snippet:

```dart
return Shortcuts(
      shortcuts: <LogicalKeySet, Intent>{
        LogicalKeySet(LogicalKeyboardKey.select): ActivateIntent(),
      },
      child: MaterialApp(
      ...
);
```

I quickly wrapped an older version of my app (pre RawKeyboardListener extensions) with this snippet, and lo-and-behold, it works 
perfectly with the D-PAD.  At least with the emulator.  I'm going to try this on a real device later this evening.  Fingers Crossed!

[^1]: [https://medium.com/@pcmushthaq/adding-android-tv-support-to-your-flutter-app-dcc5c1196231](https://medium.com/@pcmushthaq/adding-android-tv-support-to-your-flutter-app-dcc5c1196231)