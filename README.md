# Bentcher

```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+       ______     ________    __     __   ________     _____   __   __  ______   ____       +
+On    / ___  \   |   _____|  |  \   | |  |___  ___|   /  ___\  | | | |  | ____|  | _ \      +
+Calc | |___|  |  |  |_____   |   \  | |      | |     |  |      | |_| |  | |___   ||_| |     +
+     |_______/   |        |  |    \ | |      | |     |  |      | __  |  |  ___|  |   _/     +
+     |  ___  \   |  ______|  |  |\ \| |      | |     |  |      | | | |  | |      |   \      +
+     | |___|  |  |  |_____   |  | \   |      | |     |  \____  | | | |  | |___   | |\ \     +
+     |_______/   |________|  |__|  \__|      |_|      \_____/  |_| |_|  |_____|  |_| \_\    +
+                                                                                  By ibid   +
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
```

This is a Hebrew ebook reader with a built-in bentcher for the Texas Instruments ti83+/ti84+ graphing calculators (a series of 6-15MHz calcultors with z80 processors, and 96x64 monochrome displays). It was programmed in Axe Parser and compiled to z80 assembly. This featured a custom adjustable size variable-width right-to-left font with word wraping as well as a system to parse on-calc editable files into hebrew. It was worked on from about 2011 to 2012, and has been [hosted on ticalc.org since then](https://www.ticalc.org/archives/files/fileinfo/447/44723.html).

This should be runnable on the ti83+/ti83+SE/ti84+/ti84+SE calculators as well as the nspire calculators that have the ti84 emulator.

This game is not compatible with the ti83, ti84+CSE, or ti84+CE calculators.

If you do not have a calculator, there are several PC, javascript, and android based calculator emulators available that should run this fine. Wabbitemu, jsTIfied, and TilEm are all good options.

# Installation

Send the app Bentcher.8xk (app) or the program BENTCHER.8xp (mirage os) to your calculator using TI-Connect or TiLP.

# Controls

In menu:
up /down	change selection
2nd/Enter	chose selection
Clear		quit or back

In text:
Enter		Next page
left/right	Change paragraph
Up/down		Change section
+/-		Change contrast
^		invert screen
//*		Change font size

# Source Code

This program was compiled with Axe Parser 1.1.2, but should probably still be compatible with newer versions of the language. 

I've included the source.

- BENTSRC		the main program outputs the hebrew to the screen
- BENCMENU	the menu and external variable reader
- BENTCFNT	the sprites for the fonts
- BENTCDAT	the text

The source files are binary files, and cannot be viewed in a regular text editor. They're designed to be edited on a calculator with Axe installed, but they can also be opened with programs like [SourceCoder3](https://www.cemetech.net/sc/).

You can pretty much do whatever you want with the source code, but if you find yourself using it some credit would be appreciated.

# Syntax for new ebooks

To create a new Hebrew eBook that can be displayed by the reader,

1. Create an appvar or program that begins with `HEBR` as the first 4 bytes
2. Follow the following syntax for the rest of the file

- `A`-`V`		Aleph to Taf
- `W`-`Z`,`Theta`	end letters
- `n`		new line
- `o`		new paragraph
- `po`		new section
- `a`-`f`	),(,],[,/,-

The lowercase letters are the characters not the tokens. If you are programming in TI-BASIC you can use `=`,`?`,`+` for `n`,`o`,`p`.

TI-BASIC example:

```
PROGRAM:HELLO
:HEBR+?ULFX=ULFX=ULFX
```

AXE example (this is an Axe program that creates a new appvar and copies a string of characters into it.)

```
PROGRAM:ASRC
.A
:"HEBRpoULFXnULFXMnULFXM"->Str1
:Delvar appvHELLO
:legnth(Str1)->L
:Getcalc("appvHello",L)->A
:If A
:copy(Str1,A,L)
:Archive "appvHello"
:End
```
