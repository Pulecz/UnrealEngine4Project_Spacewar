# Unreal_Spacewar!

This is a attempt to replicate [Spacewar!@wikipedia.org](https://en.wikipedia.org/wiki/Spacewar!) game released at 1962.
The original game in its original source running on [PDP-1@wikipedia.org](https://en.wikipedia.org/wiki/PDP-1) emulator in PERL can be found here: [Spacewar!@oversigma.com](http://spacewar.oversigma.com/)
Goal of the game is to shoot down the other flying craft using torpedos(currently spheres) while not crash to the star with strong gravity field.

Playing on one PC with one or more controllers is not supported yet.
However LAN multiplayer is supported.

## Prerequisities
Windows 7+ 64bit
DirectX
...?

## Usage
Find win64 binary in releases, download, unpack and launch it.
...

#### Controls

###### Keyboard
W - shoot torpedo
S - engine thrust
A - rotate left
D - rotate right
A+D - hyperspace panic button (hold buttons together)

###### Gamepad
Right thumbstick X Axis/left and right buttons - rotate left/right
Left Trigger - shoot torpedo
Right trigger - engine axis thrust
A(Xbox controller) X(Dualshock) - hyperspace panic button (hold)

# Development and blueprints description
Game is made using Unreal Engine blueprint system with Warmonger asset having the most logic and settings.

When you load it Blueprint Editor you will see its derived from Pawn (top right corner).
In left in Assets, the of a Ship mesh
....
