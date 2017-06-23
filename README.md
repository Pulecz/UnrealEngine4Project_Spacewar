# Project Spacewar Evolved

This is a attempt to replicate [Spacewar!@wikipedia.org](https://en.wikipedia.org/wiki/Spacewar!) game released at 1962.

The original game in its original source running on [PDP-1@wikipedia.org](https://en.wikipedia.org/wiki/PDP-1) emulator in PERL can be found here: [Spacewar!@oversigma.com](http://spacewar.oversigma.com/)

Goal of the game is to shoot down the other flying craft using torpedos(currently spheres) while not crash to the star with strong gravity field.

This just a showcase with single player, without AI.

Playing on one PC with one or more controllers is not supported yet.

However LAN multiplayer is in progress...

No proper polishing or testing was done yet.

## Prerequisities
* Windows 7+ 64bit
* DirectX
* ...?

## Finished things so far
* Pawn with "space like" controls with option to attract to every object of another specific class
* Shooting projectiles without them being affected by any force, with editable speed
* Rectangular wraparround effect based on users screen resolution settings
* Hyperspace panic button teleporting pawn to random location in playable area
* Camera actor called cam, which in is used as central object and camera for both players in TwinStickExampleMap

## Not implemented yet
* No fuel gauge
* Finished logic determining Win/Lose
* Multiplayer
* Menus
* HUD
* Visual part, particle system
* Audio effects for hyperspace

## Knwon issues
* Wraparround using screen resolution is tricky and should be replaced perhaps with limits of the playable area and use the same logic to teleport based on being in or out (overlapping) the playable area.
  That will fix the issue of projectiles not wrapping and going around the level outside "playable area"
* not a playable prototype, just proof of concepts

## Usage
Find win64 binary in releases, download, unpack and launch it.
...

#### Controls

###### Keyboard
* W - shoot torpedo
* S - engine thrust
* A - rotate left
* D - rotate right
* A + D - hyperspace panic button (hold buttons together)

###### Gamepad
* Right thumbstick X Axis/left and right buttons - rotate left/right
* Left Trigger - shoot torpedo
* Right trigger - engine axis thrust
* A(Xbox controller) X(Dualshock) - hyperspace panic button (hold) (not implemented yet, just use keyboard, its cooler!)

# Development and blueprints description
Game is made using Blueprints:
* Center Camera with Destroying and Respawning Actor logic and editable parameter:
	* Starting Position Player 1 - X,Y,Z vector of start position for player 1 which is used after respawn (Default -800, -800, 100)
	* Starting Position Player 2 - X,Y,Z vector of start position for player 2 which is used after respawn (Default 800, 800, 100)
	* **NOTE**: currently you have to edit starting positions also in the map
* PlayableArea Actor with Light in 0,0,100 and scalable cylinder play area
* Torpedo Projectile taken from TwinStickShooter and added editable initial speed
* Warmonger Pawn having the controlls and following editable parameters:
	* Environment > Gravity Attraction - Amount of force applied to a ship to move it to the Center Camera (Default 9.6)
	* Ship > EngineSpeed - Multiply the amount of force added to the ship when thrusting (Default 35)
	* Ship > TurnSpeed - How quickly the ship can turn/rotate left or right (Default 2)
	* Ship > FireDelay - Seconds between shots, the lower the faster the shooting (Default 0.7)
	* Ship > ProjectileSpeed - Velocity of the ship + ProjectileSpeed = the velocity of the projectile (Default 400)
	* Ship > JumpChargingTime - Time in seconds before entering hyperspace (teleporting to very high Z) (Default 0.1)
	* Ship > JumpTime -  Amount of time in seconds spent in hyperspace, before teleporting back to play area(Default 3)
	* Ship > JumpRechardeDelay - Time in seconds until the Jump is avaliable again (Default 5)



When you load it Blueprint Editor you will see its derived from Pawn (top right corner).
In left in Assets, there is a Ship mesh, SpringArm with Camera, which is not used in this case and SpotLight which can be useful for real space levels.
Then all of the ship behaviour is defined in EventGraph - the blueprint part with Specific Functions.

## TODO
* See if Center Camera and PlayableArea Actor can be merged for simplicity
* Spawn characters, so starting position does not have to be set on 2 places
