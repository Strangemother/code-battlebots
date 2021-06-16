# Base Units

The application framework includes a range of _builtin_ units such as basic shapes and physics objects.


## Structure

The developer interacts with the 3D scene as an "actor" or _puppet master_ of generated objects, given through the websocket API. A developer submits an action such as "create" and perform update statements with the given instance ID.

_configs/entity.json:_
```
{
    "name": "Example2",
    "position": [1, 11, -1],
    "nodes": [
        {
            "type": "cube",
            "position": [0, 0, 0],
            "color": "#ff2200"
        }
    ]
}
```

Loading scenes:


```json
[
    "res://configs/entity.json",
]
```

## Shapes

Fundamental 3D mesh shapes with minor syntax sugar to improve readability.

+ Cube, Sphere, Pyramid

## Physics

Scene objects and actor characters (all driven units) maintain a rigid structure, enabled through the API as `physics=true`.

+ Static Body: Scene locked elements such as a _floor_.
+ Rigid Body: _Standard_ physics units for a scene without user deterministic directions, such as a ball
+ Character Body: Actor based, developer driven physics units such as a 3D world avatar.

Other physics units exist to assist the developer with the boilerplate:

+ Vehicle: An actor driven wheeled vehicle, complete with steering an power
+ Joints: Hinges, Pins and other dynamic _motor_ units


## Pluggable

Base structures and developer created units may be loaded as _packs_ of extra content. The application may load plugins from a base directory, applying additional resources to a scene for a developer to build-upon.

```json
{
    "egg": "res://egg.pck",
    "pyramid": "res://pyramid3.zip"
}
```

The base structure for a plugin mimics the world scene. Packs pre-load before entity and scene construction.

```json
{
    "cube": "res://units/Cube.tscn",
    "egg": "res://units/Egg.tscn",
    "sphere": "res://units/Sphere.tscn",
    "pyramid": "res://units/Pyramid.tscn"
}
```
