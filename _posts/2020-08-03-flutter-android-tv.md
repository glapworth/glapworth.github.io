---
title: "Flutter and Android on the TV"
categories:
  - Programming
tags:
  - flutter
  - androidtv
  - firetv
  - amazon
---

I wrote recently about installing TV HeadEnd on a Raspberry PI and I was wondering what sort of things I could do with it
for fun.  One of the problems we have in the house is that we use Amazon Fire TV Sticks or ChromeCast dongles and in order to watch
normal broadcast TV, we have to either download an App for the station - such as BBC IPlayer, or Channel 4, then search for the 
program before being able to watch it.  Even with IPlayer, watching live TV is at least 5 clicks away, each with a submenu - it's a 
painful experience.  The alternative is to switch TV inputs and watch the TV through my new fancy aerial (admittedly this is 
the simpler approach, but I wasn't after simple, I wanted utility and function).

What I wanted was a an App that could live on the Fire TV stick which when launched simply showed me a list of channels and allowed me to click on
channel to fire up a stream.  A very simple UI would work, and it'd mean that I don't have to change TV inputs at all. 

I've been interested in Flutter and Dart for a while, and I've been itching to try writing up something useful, so this would be a 
perfect project to try it in.  The TV HeadEnd server has an API, albeit lacking in documentation, but what is available is workable.
I know there is already an app for the Fire TV stick that allows you watch TV from the TVHeadEnd server, and it's actually quite good
but it still requires far too many clicks to get what you want. 

I managed to develop the app in two afternoons, and using the ADK I could test it quite happily with and Android TV emulator.  It turns
out though that Flutter doesn't yet work with a D-PAD interface, and in order to use a remote control you have set up a `RawKeyboardListener` 
and really fight with the `FocusNode`.  This was sometimes painful, especially when using a GridView of `n` elements and having no
`onTap` methods available since the raw widgets didn't realised they were being tapped.  To resolve this, I ended up with large 
switch statements inside the `RawKeyboardListner` to work out which widget is selected and then calling the right method 
when the user clicks the centre button.  This might not have been the best solution, but it was the one that I managed to get to work.

After much fumbling and reverting to many mailing list posts, and issues on Github, I got the thing up and running, only to be 
rejected by the Amazon App store - they claim it crashes on startup, but don't provide any logs.  I've debugged and debugged on two
of my FireTV sticks, and I can't seem to get it to fail. I'm putting the project to one side for now until flutter gets better
support for Android TV and other remote control interfaces, and maybe I'll try again soon.

For what it's worth, Flutter is Awesome!  I can wholeheartedly say that I'd happily try writing my next app project in it.  
Development was a breeze, the documentation was fantastic and there are lots of developers writing about it and publishing
interesting tips.  

I don't blame Flutter and the team for the app not working out the of the box with remote control based interfaces.  I expect
support will come soon.

In the mean time, I might build a standard Android mobile app with Chromecast support in order to solve my use-case. I can however run
the app quite nicely when I publish it directly to my FireTV stick, so theres that.

**Edit**: I recently found [https://pub.dev/packages/focusnode_widgets](https://pub.dev/packages/focusnode_widgets) and hope to try re-implementing the UI with that to see if it makes a 
difference.  