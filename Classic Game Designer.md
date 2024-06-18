# Classic Game Designer

## (C.G.D) instructions.

Dave Hughes, updated to version 1.3 on 15/10/13
CGD is a utility that runs on the 48k Spectrum and above to create games with that ‘old school’ early
1980’s feel.
Hopefully most of the instructions are within the utility, unless otherwise told key ‘E’ exits. Apologies
in advance for liberal use of the term ‘baddy’.

## 1 Design sprites.

Here you create the moving objects in the game. UDGS 0,1,2,3 are the player sprite right, left, up
and down graphics respectively. UDGS 4 – 15 are the ‘baddy’ sprites, they have only one UDG each
so no directional graphics for them.

To edit the player properties (speed, control type) use while editing block 0.

The main keys are;

QAOP-Space – to create your graphic. Keys 1 & 2 to scroll through your sprites.
Key 4 scrolls through the desired effect when the sprite collides with the player. So for this reason
you cannot select it for UDGs 0-3 (the player sprite). There are 4 types of effects:

- Do nothing -does nowt
- Kill player – player loses a life on collision
- Kill guardian – the baddy sprite is switched off & counter 2 is decreased.
- Dec counter 1 – counter 1 is decreased.

Key 5 – scrolls through the sprite speed, 9 is the fastest, 1 is very, very slow.

Key 6 – scrolls through the control mechanism. For the player it is the type of key read, for the
baddies it is the AI. It is best to change the player conditions on UDG 0.

### Control types

- Multiple key press
- Pacman style keys 
- Single key press  
- Turn based keys   

### AI movement types

- vertical_patrol       
- horizontal_patrol     
- diagonal_patrol       
- horizontal_snake      
- vertical_snake        
- diagonal_chaser       
- unidirectional wander 
- unidirectional chaser 
- vibrating baddy       
- runs away from you    
- runs away and wanders 
- moves in fits & starts
- up/left/right/down only             
- do nothing      

Key ‘G’ generates a random mirrored UDG, it may on occasion look like a space invader. It overwrites
the current UDG.

The others keys are hopefully self-explanatory, not mentioned is key ‘R’ which can be used to rotate
the sprite.

## 2 Design blocks

You have 32 (0-31) blocks to make you game. QAOP-Spc to make you graphics, keys 1 & 2 to scroll
through the blocks.Block 31 is enlarged and used on the game intro screen. It can also be used as an in game block.

Keys 5 & 6 scroll through the effect the block will have on the player. Keys T & Y scroll through the
effect the block with have on the baddy.

There are quite a few block effects:

- Do nothing: passive block you can move through with no effect
- Solid block: sprite cannot move through block
- Change baddy types: changes baddy AI on collision with this block type. Does not affect
- player even when selected.
- Make sprite down/up/left/right . Affects baddys only, makes a unidirection sprite. 
- Make sprite random. Baddy only, makes unidirectional in a random direction
- Dec counter 1-3: counter is a 16 bit counter (0-65535). Collision with this block decreases it
- by 1 and deletes the block with block with the same counter number.
- Inc counter 1-3: counter is a 16 bit counter. Collision with this block increases it by 1 and
- deletes the block with block with the same counter number.
- Zero counter 1-3: zeroes counter and deletes with block # 1
- Force down/up/left/right: forces player down one square, unable to return
- Counter 1-3 =0, locked: if counter  is zero it cannot be moved through
- Counter1-3<>0, locked: if counter  is not zero it cannot be moved through
- Counter2<>0, locked: if counter 1 
- Counters123nzlocked: counters 1,2 & 3 must be zero to allow passage
- Setflag1-3 ON: sets flag ON, deletes with block with same number
- Setflag1-3 OFF: sets flag1 OFF, deletes with block with same number
- Set all flags ON: sets flags 1,2,3 ON, deletes with block 0
- Set all flags OFF: sets flags 1,2,3 OFF, deletes with block 0
- Toggle ALL flags: if a flag is ON it is turned OFF, and vice versa, for all 3 flags. Deletes with block 0
- Flag 1-3 ON = locked: if flag is ON this block cannot be moved through
- Flag 1-3 OFF = locked: if flag is OFF this block cannot be moved through
- Open if timer = 0: only if the timer is zero this block can be moved through
- Open if timer<>0: if timer is zero this block cannot be moved through
- Decrease timer: decreases timer by 1, block is not deleted
- Increase timer: increases timer by 1, block is not deleted
- Next level up: completes the current level and jumps to the next one.
- Next level down: takes the player down one level.
- Goto level 1-9: these levels can also be used as e.g. teleporters or screen edges to give you any map shape you want in a multiscreen game.
- Complete game: whichever level the player is on, this successfully finishes the whole game.
- Kill sprite: turns the sprite off, this does not work well if applied to the player but works better when applied to the baddies. Counter 2 is decreased.
- Kill all baddies: turns off all baddies on the current screen. They are active on return to the screen.
- Kill player: player loses a life
- Extra life: increases lives by one, makes zap noise but does not interrupt game
- Gravity ON: set gravity on, pulls the player down slowly, the speed can be changed (see POKES). Rem if gravity is mixed with ‘force’ blocks you can get ghost graphics.
- Gravity OFF: turns gravity off, whatever the current condition.
- Toggle gravity: if gravity currently on it turns off, and vice versa
- Pacman tablet: gives player immunity, sets the baddies to run away mode, temporary effect, border flash and tick noise
- Immunity: gives player temporary immunity, border flash and tick noise
- Slow block: sprite movement is slowed while passing through
- Next block down: when sprite passes over it changes to the next block number down
- Next block up: when sprite passes over it changes to the next block number up
- Push block: can be pushed through block 0 only. Push blocks automatically screen wrap so if you do not want this you will need to create your own solid block border.
- Push ‘n’ squash: can be pushed freely through block 0, but squashes & disappears from the map on contact with any other. Push blocks automatically screen wrap so if you do not want this you will need to create your own solid block border.
- Push ‘n’ lock: a specialist block, a bit like a Sokoban block. The push block can only be pushed through block 0, and when it comes into contact with block 4 it becomes block5 and
- counter 3 is decreased. For this reason if using be sure to keep blocks 4 & 5 free. Push blocks automatically screen wrap so if you do not want this you will need to create your own solid block border.
- Print message 1-3: prints a 32 character message on the screen. This message is set in option 8 ‘Edit game text’. 
  
## 3- Font designer

A not very sophisticated designer*. QAOP-Space to make the chars, 1 & 2 to scroll through them. 'B'
makes the entire font bold, 'I' makes the entire font italic. ‘R’ removes your work and replaces it with
the regular Sinclair font.

So be careful, it is very easy to spoil your font with one key press.

If you want to load you own font the 768 bytes should be inserted at memory address 52451

## 4- Map designer

Follow the instructions to edit the 9 screens available.

Not all the keys are listed in the utility:

Keys QAOP-Space to move around the map and insert blocks.

Keys 1 & 2 scroll through the block you want to insert. It moves through the entire 0-32 blocks plus
the sprites. So to insert the player or a baddy you need to find them in these blocks and insert it in
position.

Key X – clears the entire screen with block 0.

Key C – copies the entire screen to the clipboard

Key V – pastes the contents of the clipboard into the current screen edit

So be careful, keys X and V can ruin your work with one key press

## 5- Event manager

Sets some conditions for game events. It is possible to make a playable game using blocks only, so it
is safe to leave them all as ‘do nothing’ if you want.

Key 1: scrolls through the effect that leads to the level being successfully completed. E.g. a frogger
style game can be created with the ‘player at top’.Key 2: scrolls through the effect that leads to the level failing and the player losing a life.

Keys 3 & 4: scrolls through the effect when the player or baddy meet the screen edge.

- Screen wrap: on meeting the screen edge the sprite appears at the opposite edge
- Random wrap: on meeting the screen edge the sprite appears at a random position at the opposite edge
- Next screen: makes the game a flip screen game, the next screen along or vertically is moved to.

## 6- Item counters

Sets the game counters 1,2,3 to a given number at the start of a level. Useful for collectable objects
that manipulate the counters.

N – Set the counters to a fixed number at the start of each level

Use keys 1 & 2, Q & W and A & S to inc and dec counters 1,2,3 respectively.

B – sets the counters to a particular block abundance at the start of each level.

This function saves you having to count a particular block that is large in number.

At the start of a level the program counts the numbers of the selected block and sets the counter to
the same number. This saves laborious counting, and allows a different number per level (unlike the
fixed number choice).

For this reason you can only set all counters to a fixed number, or blocks, not a combination of the
two.

## 7 – Variables

Use the keys specified to inc and dec the variables on the screen.

If timer is set to zero it is not printed on the screen during a game.

If doing a flip-screen game it is best to set level to 1.

## 8-Game text

This is the text that appears at the bottom of each level/screen.
Press the level number you want to edit, or B, G, C for bottom line, (game over message, congrats
screen), then type the text. Press A, S, D to edit in game message 1,2,3 respectively. While typing
pressing ‘ENTER’ returns.

## 9-Effects

You have two effects to include when the game is completed or the game is over. Press the keys
specified to scroll through the (limited) number of effects, the on screen descriptions should be self-
explanatory.

I – Introscreen text
This is the paragraph that appears at the bottom of the game intro screen. You have 256 character
spaces for this. Press ‘ENTER’ to exit.

C – Game colours
Follow the on screen instructions to set the game paper and ink colours for the game introscreen,
game colours (border), game over screen and game completion screen. ‘E’ exits.

T – Test game
This enables you to play the game with your current settings. Key ‘Z’ skips through the levels until
completion. Be careful how you have set things up in case you get stuck, for although I have not
managed this in recent versions it may be possible. It still is a good idea to save a snapshot before
testing.

S – Save game
For when you have finished editing your game. A very good time to save an emulator snapshot in
case there are problems.

This exits to BASIC so you can save the code to a TAP file (or even real tape if you're hardcore). The
game code occupies memory addresses 32512 to 53662. On return to BASIC you need to type SAVE
32512,21150 & save to an inserted tape. The game entry address is 34051, so to start the game in
this code you type RANDOMIZE USR 34051.

If you want to return to the game editor from BASIC you type CLEAR 26999, then RANDOMIZE USR
27000.

## 10 Completion

The following test for level completion are possible

- counter1-3 zero   
- timer zero      
- baddies all_dead
- player at bottom/top/left/right
- baddy at bottom/top/left/right

## 11 Miscellany

### Game introscreen

The default game intro screen uses a combination of:

Game title, as entered in option 8 game text
An enlarged picture, which is block 31
256 characters of text, as entered in option ‘I’ - introscreen text.

### Introscreen music

There is a large amount of spare memory (~11k) above the game. Any music can be stored here.
To activate introscreen music (example uses music stored at 64000):

### Notes

Load your music starting at memory address 64000 (though you can go as low as 53662).
Poke memory address 34117 with the music start memory address.
For example if your music is at 64000 you poke 34117,0 and 34118,250 (250 x 256 + 0 =
64000)

