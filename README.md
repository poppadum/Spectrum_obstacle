# Obstacle Course Game
- Platform: Sinclair ZX Spectrum 16K/48K/128K
- Category: PUR-80
- Suggested emulators: [ZEsarUX](https://github.com/chernandezba/zesarux) or [fuse](https://sourceforge.net/projects/fuse-emulator/)
- Author: ChrisL


## Description
This is a Spectrum version of a game I remember on the SAM Coupé which was originally written in one line of SAM BASIC. Unfortunately I can't remember the original author's name.

## Instructions
Steer your line across the screen from left to right avoiding the obstacles in your way. The aim is to reach the "goal" (the blank space) on the right side of the screen.

Your line starts at the > marker at the left side of the screen. It grows upwards and to the right. If you hold the SPACE key, it grows downwards and to the right; release the SPACE key and it grows up and right again.

## Running
Load the [obstacle.tzx] tape image into your emulator. If it does not automatically load the tape, in Spectrum BASIC type `LOAD ""` and press enter.

The game exits after each play. To try again, type `RUN` and press enter.


## Difficulty
To make the game slower, increase the length of the `PAUSE` command on line 100. To make the game faster, remove the `PAUSE` command.

Increase or decrease the number of obstacles by adjusting the value `50` in the `FOR` loop on line 50.


