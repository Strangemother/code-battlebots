# Simple Battlebots

A player codes a 'turtle' style reactive command module to run a 'bot' in a 3D
scene. The player bot will be created and coded given components and code to
build upon.

1. Bot development
2. Battle room
3. Score boards
4. Levels

Each level will extend the complexity of the bot, allowing more complex action
and code.

1. Simple drive and shoot and square rooms
2. tanks, flying vehicles
3. build-upon components.
4. joints, projectiles.

A user code may react to simulated signals in a websocket bot. This allows
bots of different languages. An autobot is coded without user interaction - and
state-like commands run the bot in single one-shot calls, allowing easy loadout
to the db.


# Interaction

A user may load a bot and run a room to play against other bots. They extend the
bot using signals supplied through the game engine. A developer extends the
bot for more complex interaction; such as joints and aiming.


## Building

Early bots are simple vehicles and a turret, a user emits steering and firing commands
until an opponent is dead. The commands are managed by user-developed code.


## Playing

The player will run the bot in the tornament, to win points by shooting the other
opponent, and avoiding damage. A round will timeout or a max win score.

The user may play the dev environment for dev and fun within the installable game
The game may run on a webgl environment however shoadow machines may struggle
( autobots may help )


# System

The game components emit simple events the user may react to; The game engine
runs the user bot through calls to the bot machine. Alternatively as standard
method calls on an executing API.


## Game State

Editing engine machinery can manipulate general FPS target and physics methods,
including the engine scale speed.

+ FPS general target
+ Game tree pausing
+ physics enabled delta scale


## Setup

A few options to select, depending upon requirement.

1. Each user creates their own client, connected via WS
    + A Developers vehicle must be 'alive'
2. A User uploads a bot
    + The system must run the bot


## Vehicle Build

Components should be a tree of connected nodes. Each node is pre-built to connect
such as Joints and ligatures.


### Pieces

Components to build a vehicle should be preprepared.

1. a car base, complete with wheels and chassis
2. sensors
3. weapons; e.g a turret, laser beams
4. Joints and motions.


### Joints

Actuations to translate the position of in-game elements.

1. a turn-plate
2. hinge
3. a l-joint rotation

Each joint may be defined as passive or active.


## Example code.

In this example a vehicle with a bump bonnet.

```py
class MyCar(Vehicle):
    # car structure.
    model = MyCarModel

    def on_start(self):
        # on game engine start
        self.power = .1 # 10%

    @signal('front_bumper.hit')
    def bump(self, event):
        # front bumper
        self.power = 0
```
