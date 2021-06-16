# Building Components


## Create


```json
{
    "action": "create",
    "parent": "/root/World/",
    "owner": "user_id",

    "definition": {
        "name": "Example",
        "position": [1, 8, 1],
        "version": 1.0,
        "rotation": [0,0, 0.15],
        "nodes": [{
            "type": "cube",
            "position": [0, 0, 0],
            "size": [0.25, 2, 0.25],
        }]
    }
}
```


## Destroy

Entities generated within the scene may be deleted through the API.

```json
{
    "action": "delete",
    "node": "node_id_1234",
}
```

## Set

An _update_ will change the asset value noted within the `nodepath`. Given a complex
value (requiring pre-convert before applying) the `complex` string type presents the expected output input value for the `node` and `nodepath`

```json
{
    "action": "update",
    "node": "node_id_1234",
    "nodepath": "full:extent:",
    "value": [1,2,3],
    "complex": "Vector3",
}
```


## Get

Fetch the value from the given `node` and/or `nodepath`.

```json
{
    "action": "get",
    "node": "node_id_1234",
    "nodepath": "full:extent:"
}
```

