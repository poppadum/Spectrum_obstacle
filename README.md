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
Load the [obstacle.tzx](obstacle.tzx) tape image into your emulator. If it does not automatically load the tape, in Spectrum BASIC type `LOAD ""` and press enter.

The game exits after each play. To try again, type `RUN` and press enter.


## Difficulty
To make the game slower, increase the length of the `PAUSE` command on line 100. To make the game faster, remove the `PAUSE` command.

Increase or decrease the number of obstacles by adjusting the value `50` in the `FOR` loop on line 50.


## Program Listing
```
  10 RANDOMIZE : CLS : PAPER 7: INK 0: PRINT "■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■"
  20 FOR y=1 TO 20: PRINT "■";AT y,31;"■": NEXT y
  30 PRINT "■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■"
  40 PRINT AT 11,0; OVER 1;">": PRINT AT RND*18 +2,31;" "
  50 FOR o=1 TO 50: PRINT AT RND*19+1,RND*26+3;" ": NEXT o
  60 LET x=8: LET y=83: FOR o=1 TO 3: BEEP .2,3: NEXT o: BEEP .5,5
  70 PLOT INK 1;x,y: LET x=x+1: LET y=y+1-(INKEY$=" ")*2
  80 IF POINT (x,y)=1 THEN PRINT AT 11,12; INK 2;"Crash!": BEEP .5,10: BEEP .5,8: STOP
  90 IF x>=249 THEN PRINT AT 11,14; PAPER 6;"Win!": BEEP .25,10: BEEP .25,12: STOP
 100 PAUSE 1: GO TO 70
```

Lines 10-30: initialise the random number seed, clear the screen and set the colours to black ink on white background. Print a black box around the edge of the screen.
Line 40: print the start marker `>` at the middle of the left edge; mark the 'goal' by printing a space at a random place on the right edge of the screen.
Line 50: draw 50 obstacle blocks at random points on the screen.
Line 60: `x` and `y` hold the coordinates for the next point on the player's line; start just to the right of the start marker. Play a short sound to indicate to the player the game is about to start.
Line 70: draw a single pixel at the line's current coordinates. Increase `x` to move the next point to the right. Increase `y` by one to move the next point down; if SPACE is pressed, subtract 2 to cancel the move down and move the next point up.
Line 80: if the line's next point is already occupied, we've crashed: inform the player and stop the game.
Line 90: if the line has reached the right side of the screen, we've won: inform the player and stop the game.
Line 100: pause 1/50s (so the game runs at a playable speed); go back to line 70 to draw the next point on the line.
