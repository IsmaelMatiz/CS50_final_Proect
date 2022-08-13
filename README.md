# Bizarre Adventure

#### Video Demo: [Bizarre adventure Youtube]()

## Members
- Juan Rodriguez
- Ismael Matiz
---

##What is Bizarre adventure?
This is a simple Videogame that we develop to practice and show a couple of things that
we learned in CS50x, it's SO simple but we think that it's funny, basically, you are a ninja
and you will need to jump in a platform world and fight against wizards who shot fire
___
## How was developed?
#### Enviorment and Design
First we decide to Use Unity and C# to develop the game because Unity offers a lot of useful
features to develop a game and we use C# because it's like a strong version of C/C++ also, 
is the default language from Unity XD, Juan draw most of the sprites and the 2 backgrounds, 
to be honest, I only made the second type of ground and the torches, Juan takes inspiration from
[Truth Sasuke's creator]() to redesign the character, he creates the rest of the idea, also
he use a lot the tutorials from [Deekman]() to redesign the character, he creates the rest of the idea, also.


The first thing that we have to do was create the design of the game, that's why we use as 
inspiration pixel art, we start a design with two sprites in a program call it Aseprite, the 
first one being some kind of Sasuke of the naruto series, this sprite and animations were 
created by a user call it Deekman in Pinterest we made a few changes in the sprite painting with 
red and gray in the palet color, the next one was a fire wizard,(from now on the designs are 
from us) this design is completely from our minds we didn't use any other sprite from the 
internet, we inspiring us of Walter white of the Breaking Bad series.
After that, we made animations, backgrounds, trees, torches, and some platforms made in the
Aseprite program (you can see each one in the youtube video of the cs50 final project) the next 
part was the level design which means organizing everything that we made earlier to create 
challenging levels for the players were they have to jump, attack, run, protect and die, the 
same to our fire wizard when we finished everything, and that's how we made our game personality 
and my first-pixel art design and animations excepting the original Sasuke from Deekman.


#### Project Structure

This folders
- Library //This folder has been deleted because is too large
- Logs
- Packages
- ProjectSettings
- UserSettings

are default packages I mean the Unity system automatically creates and add these packages to the
project, maybe Packages was the only of these folders that we made a little change download
shaders asset however the folder where all that we developed is saved, is Assets here you will found

- Animations
- Change Scence Scripts
- Ilumination 
- Materials 
- Melodious shooter Music
- prefabs
- Scenes
- Scripts
- Sound Effects
- Sprites
- Streaming Assets
- TextMesh Pro
- several config files required for some assets .meta
##### Lets check one by one
---
##### Animations
Here you will find several .anim and .anim.meta files, these files contain info about the animation
i mean it's a special file created for Unity that has info about every frame on the animation
and also if the animation will have an infinite loop or the animation speed.

Also you will find some .controller files. this file's type has info about what animation execute
in what moment, for example if the player die change the animation to player_die.anim or 
if the player is running change the animation to player_run.anim...

##### Change Scence Scripts
This folder has information about some simple scripts that Juan creates to handle change from 
the menu to the next levels or from one level to another and the final message thats the only 
info that this files contain, is possible to resume these files just to one file? yes, we can
create a better algorithm but we create these files in a quick time without taking in count that

##### ilumination
This has info metadata and info required for the correct function of the plugin that we use
to create the lights in the game

##### Melodious Shooter Music
This folder contain several tracks and info from the music that we use in the game

##### prefabs
Every game object(player, enemy, ground, torches...) it's composed of several things, I mean, 
sprites, animationAnimator enemyAnimator;
bool isLookingRight;
bool startMovement;, position/scale, scripts, collisions... these kinds of objects that already
have all the necessary components are called prefabs, the information that will see here is
handled and created from Unity, here you will see the different grounds, the torch, the
player and other kinds of recurrent game objects

##### Scenes
Here you will find different Unity objects, these are the main menu, the levels and the final message
this objects contains info with all the game objects that compose each scene, this is created
and handled through Unity

##### Scripts 
###### background_Controller
Here we have 3 variables (Material material, Gameobject target, int currentScene), basically, 
material is required to make the parallax effect and target is to specify what object should the 
background follow and currenScene is required because the first background is bigger than the other two
to handle it better we create 2 conditionals where the only change in the code is how high is the background

###### CameraController
On this file we got

GameObject target; >> specify what game object follow
Vector3 camAdjust; >> to indicate the next camera position
float ahead; >> to show better the environment it's more easy show a little more ahead the camera
float smooth; >> like the name says, is for smoothie the camera movement.

First, we check if the player is looking to the right or to the left (checking the scale)
based on that we set the new camera's position into camAdjust. Then we change the position
using the transform and lerp functions to change position, with lerp we specify how many time should pass during this update

###### Enemy Controller
On this file we got these vars

public GameObject fireball; >> this is to specify what is the object that the wizard will shoot
public float speedEnemy; >> the name say all
public LayerMask border; >> this to specify what object will mark the border of the ground
Animator enemyAnimator; >> this is to handle the wizard animations
bool isLookingRight; >> the name say all
bool startMovement; >> its to indicate when activate the function to move the enemy
and 2 STATE vars >> this is to conect with the animation conditions

First, whe set the value in the variables, and start a coroutine, that coroutine is for coordinate, when execute what animation and when shoot a fire ball and when activate the movement

Then in the Update func, you will see the code to move the enemy and when the enemy touch the border flip it

###### Enemy Controller
On this file you will see
Rigidbody2D fire; >> this is to add physics to the object
public float speedFireBall; >> velocity of the ball

The fireball is programmed to go ahead with a constant velocity and destroy itself after 5 seconds from its creation

###### PlayerController
On this file you will see

Several STATE variables >> like the wizard this is to connect with the animation conditions

Animator playerAnimator; >> this is also requireed to connect with the animations
Rigidbody2D rigidBody; >> this is to handle the physics of the player
public float jumpForce; >> how high the player is able to jump
public float speed; >> the player velocity
public float speedPrev; >> this is required to stop the plaer run and then star it again
public PlayerStatus status; >> is the player attacking the enemies, or is vulnerable to attacks 
public LayerMask groundMask; >> this to specify what sprit should be recognize as ground
public GameObject restartPlay; >> this to hide the die screen and show it again if the player is alive or not
public GameObject mainMenu; >> this to hide the die screen and show it again if the player is alive or not
public Image GameOver; >> this to hide the die screen and show it again if the player is alive or not
private float lastYPosition; >> this is for help me to know if the player is jumping or falling

First, I set up the inital values from several of the last variables

Second, I program the player movement using the Input.GetAxis that return 1 if the player go to the right
or -1 if the player go to the left and multiplying that with the speed and the real time to avoid
trouble with falling frames 

Third if the player press the up arrow and is touching the ground we add force to player to go up

Fourth the attack if the player press Z or X we stop any previous attack(just in case), we set animation
change the player status and after the animation is completed go back at the first position and vulnerable
also if the player press Q we stop the player movement, the player is now invulnerable to the fireballs and 
we lock the animation to the animation to block animation

Fifth handle the animation movement of the player depending on what key is he pressing or letting press, 
also flip the player if is required

Sixth the maps are designed to avoid the -11.5 so if the player reaches that Y position that means death for falling

Seventh you will see several funcitions that help to handle the last behaviors, but the only func
that i didn't explain is OnCollisionEnter2D(Collision2D collision), basically, depending on the player status if the player crash against a 
wizard in the attacking status the wizard will be killed otherwise the player, if the player is invencible he will destroy the fireball 
otherwise the player


###### ScenesManager
On this file you will see only one var int currentScene, this is to save the index of the current
scence(menu=0,level1=1,level2=2...) and then the several funtions to handle the change betwen scenes

Start() >> here we set the value of the current scene and if we are in the last scene the system wait
for 40 seconds and then go back to the nmain menu

OnCollisionEnter2D() >> if the player crash against the object with this code this will change the level
to the next one

GoToMenu() >> the name say all

Restart() >> the name say all

CloseGame() >> this function is only available in the main menu and try to guess, what this function do?

##### Sprites
Here you will find all the pictures that we use in the game, i mean the backgrounds, the sprite
atlas, the ground... also you will see several .meta files, this files are important because it has
info about some edit that we made in the pictures in Unity for example divide the sprite atlas in
individual sprites into the Unity engine this in order to save memory

##### TextMesh Pro
this has info and meta date about the text plugin that Unity has for default also we add an special
font that we download from [dafont](https://www.dafont.com/es/kerox.font).

---

## The Process
This was a really cooperative work so it's a little hard explain who made what, because i fix some
lines of code from Juan he give the idea about how to improve another, also he made a lot of the
sprites but i help to draw some of them and also i created some of them and Juan Fix them a little
bit, so i prefer to explain how we did it, we live in the same City but in different locations, so
we share the work from the other using pictures, videos, zoom, liveshare from VS code, my laptop
has a little more resources than the Juan's laptop so i join everything with Unity in my end and then
i share it with Juan, we started the project with

#### first
We create the sprites and the animations, Juan sent me the pictures via Whatsapp and 
i add it to the project we use -pixel art editor- how i said Juan made 
most of the sprites and i join all in  my end

#### second
we develop the fundamental scripts, you know, the character movement, the enemys behavior, 
the camera movement, the background movement... we work together to develop this using live share
from VS code to edit the code in real-time, Juan give me some ideas and I fix some of his bugs.
In that moment the game start to get life

#### Third

Add the audio, lights and polish some details to give more life to the game.

this was not an strict order i mean, sometime we did all of this steps only for create the player,
to make the trees or add the audio could be only the first and third step, also take in count
that when we add something new that could affect the existing object so we should fixed the bugs
fix the collision, the animation logic... so it was a little different the process but basically this how we develop the game

### References and Inspiration
In some parts of the code you will found also comments with the link but also we want to add them
here and give special thanks, to the Unity Manuals, the Youtube tutorials and Stack Overflow to give
some content, teach and help us to create, improve and fixed the game



#### Design inspiration and Tutorials
https://www.youtube.com/watch?v=vs-ierVdE7I
https://www.youtube.com/watch?v=sg3EffpU6uo
https://www.youtube.com/watch?v=pTqPZutyQKQ
https://www.youtube.com/watch?v=btnH0x7_1g8&t=468s
https://www.youtube.com/watch?v=tnKC9Asr7p4
https://www.youtube.com/watch?v=cLESnHw2dPE&t=530s&pp=ugMICgJlcxABGAE%3D
http://deekman.cbj.net/
https://www.spriters-resource.com/game_boy_advance/narutonc2/sheet/14405/

