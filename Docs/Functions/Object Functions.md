# Object Functions

---

## Global World Objects

### `createObject`

#### Description
Creates a global dynamic object visible to all connected players.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| model | integer | GTA object model ID. |
| x | number | World X coordinate. |
| y | number | World Y coordinate. |
| z | number | World Z coordinate. |
| rx | number | X rotation angle in degrees. |
| ry | number | Y rotation angle in degrees. |
| rz | number | Z rotation angle in degrees. |
| drawDistance | number | Maximum rendering draw distance. |

#### Return Type
```text
integer
```

#### Return Value
Returns the newly created object ID on success, or `INVALID_OBJECT_ID` (`65535`) on failure.

#### Example
```lua
local objId = createObject(1337, 1500.0, -1600.0, 13.5, 0.0, 0.0, 90.0, 300.0)
```

---

### `destroyObject`

#### Description
Destroys an existing global world object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID to destroy. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if destroyed, or `false` on failure.

#### Example
```lua
destroyObject(objId)
```

---

### `isValidObject`

#### Description
Checks whether a global object ID is valid and currently allocated.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID to check. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if the object exists, otherwise `false`.

#### Example
```lua
if isValidObject(objId) then
    print("Object is active")
end
```

---

### `getObjectModel`

#### Description
Retrieves the model ID of a global object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |

#### Return Type
```text
integer
```

#### Return Value
Returns the model ID, or `-1` if the object does not exist.

#### Example
```lua
local model = getObjectModel(objId)
```

---

### `getObjectPosition` / `getObjectPos`

#### Description
Retrieves the world position coordinates of a global object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |

#### Return Type
```text
number, number, number (or nil)
```

#### Return Value
Returns three `number` values (`x, y, z`), or `nil` if the object does not exist.

#### Example
```lua
local x, y, z = getObjectPosition(objId)
```

---

### `setObjectPosition` / `setObjectPos`

#### Description
Sets the world position coordinates of a global object and synchronizes with all players.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |
| x | number | New X coordinate. |
| y | number | New Y coordinate. |
| z | number | New Z coordinate. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
setObjectPosition(objId, 1500.0, -1600.0, 20.0)
```

---

### `getObjectRotation` / `getObjectRot`

#### Description
Retrieves the rotation angles of a global object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |

#### Return Type
```text
number, number, number (or nil)
```

#### Return Value
Returns three `number` values (`rx, ry, rz`) in degrees, or `nil` on error.

#### Example
```lua
local rx, ry, rz = getObjectRotation(objId)
```

---

### `setObjectRotation` / `setObjectRot`

#### Description
Sets the rotation angles of a global object and synchronizes with all players.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |
| rx | number | New X rotation. |
| ry | number | New Y rotation. |
| rz | number | New Z rotation. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
setObjectRotation(objId, 0.0, 0.0, 180.0)
```

---

### `moveObject`

#### Description
Smoothly moves a global object toward target coordinates at a given movement speed.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |
| x | number | Target X coordinate. |
| y | number | Target Y coordinate. |
| z | number | Target Z coordinate. |
| speed | number | Movement speed in units per second. |

#### Return Type
```text
number
```

#### Return Value
Returns the estimated travel time in milliseconds, or `0.0` on failure.

#### Example
```lua
local moveTime = moveObject(objId, 1500.0, -1600.0, 50.0, 5.0)
```

---

### `stopObject`

#### Description
Stops any ongoing movement interpolation for a global object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if stopped, or `false` on failure.

#### Example
```lua
stopObject(objId)
```

---

### `isObjectMoving`

#### Description
Checks whether a global object is currently in motion.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if moving, otherwise `false`.

#### Example
```lua
if isObjectMoving(objId) then
    print("Object is still moving")
end
```

---

### `setObjectScale`

#### Description
Sets the rendering scale factor of a global object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |
| scale | number | Scale multiplier (e.g. `1.0` for default, `2.0` for double size). |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
setObjectScale(objId, 1.5)
```

---

### `attachObjectToPlayer`

#### Description
Attaches a global object to a player with a relative offset and rotation.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectId | integer | The object ID. |
| playerId | integer | The player ID to attach to. |
| x | number | Relative X offset. |
| y | number | Relative Y offset. |
| z | number | Relative Z offset. |
| rx | number | Relative X rotation. |
| ry | number | Relative Y rotation. |
| rz | number | Relative Z rotation. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
attachObjectToPlayer(objId, playerid, 0.0, 0.0, 0.5, 0.0, 0.0, 0.0)
```

---

## Per-Player Objects

### `createPlayerObject`

#### Description
Creates an object visible only to a specific player.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID who will see this object. |
| model | integer | GTA object model ID. |
| x | number | World X coordinate. |
| y | number | World Y coordinate. |
| z | number | World Z coordinate. |
| rx | number | X rotation. |
| ry | number | Y rotation. |
| rz | number | Z rotation. |
| drawDistance | number | Maximum draw distance. |

#### Return Type
```text
integer
```

#### Return Value
Returns the player object ID on success, or `INVALID_OBJECT_ID` (`65535`) on failure.

#### Example
```lua
local pObj = createPlayerObject(playerid, 1225, 1400.0, -1700.0, 13.0, 0.0, 0.0, 0.0, 200.0)
```

---

### `destroyPlayerObject`

#### Description
Destroys a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if destroyed, or `false` on failure.

#### Example
```lua
destroyPlayerObject(playerid, pObj)
```

---

### `isValidPlayerObject`

#### Description
Checks whether a per-player object exists.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if valid, otherwise `false`.

#### Example
```lua
if isValidPlayerObject(playerid, pObj) then
    print("Player object is valid")
end
```

---

### `getPlayerObjectPosition` / `getPlayerObjectPos`

#### Description
Retrieves the position of a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
number, number, number (or nil)
```

#### Return Value
Returns three `number` values (`x, y, z`), or `nil` on error.

#### Example
```lua
local x, y, z = getPlayerObjectPosition(playerid, pObj)
```

---

### `setPlayerObjectPosition` / `setPlayerObjectPos`

#### Description
Sets the position coordinates of a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |
| x | number | New X coordinate. |
| y | number | New Y coordinate. |
| z | number | New Z coordinate. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
setPlayerObjectPosition(playerid, pObj, 1400.0, -1700.0, 15.0)
```

---

### `getPlayerObjectRotation` / `getPlayerObjectRot`

#### Description
Retrieves the rotation angles of a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
number, number, number (or nil)
```

#### Return Value
Returns three `number` values (`rx, ry, rz`), or `nil` on error.

#### Example
```lua
local rx, ry, rz = getPlayerObjectRotation(playerid, pObj)
```

---

### `setPlayerObjectRotation` / `setPlayerObjectRot`

#### Description
Sets the rotation angles of a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |
| rx | number | New X rotation. |
| ry | number | New Y rotation. |
| rz | number | New Z rotation. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
setPlayerObjectRotation(playerid, pObj, 0.0, 0.0, 90.0)
```

---

### `getPlayerObjectModel`

#### Description
Retrieves the model ID of a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
integer
```

#### Return Value
Returns the model ID, or `-1` if not found.

#### Example
```lua
local model = getPlayerObjectModel(playerid, pObj)
```

---

### `movePlayerObject`

#### Description
Smoothly moves a per-player object toward target coordinates at a given speed.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |
| x | number | Target X coordinate. |
| y | number | Target Y coordinate. |
| z | number | Target Z coordinate. |
| speed | number | Movement speed. |

#### Return Type
```text
number
```

#### Return Value
Returns the movement duration in milliseconds, or `0.0` on failure.

#### Example
```lua
local duration = movePlayerObject(playerid, pObj, 1400.0, -1700.0, 25.0, 3.5)
```

---

### `stopPlayerObject`

#### Description
Stops any ongoing movement on a per-player object.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
stopPlayerObject(playerid, pObj)
```

---

### `isPlayerObjectMoving`

#### Description
Checks whether a per-player object is currently moving.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| objectId | integer | The player object ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if moving, otherwise `false`.

#### Example
```lua
if isPlayerObjectMoving(playerid, pObj) then
    print("Moving...")
end
```

---

### `attachPlayerObjectToPlayer`

#### Description
Attaches a per-player object to a target player.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| objectPlayerId | integer | The player ID who owns/sees the object. |
| objectId | integer | The player object ID. |
| attachPlayerId | integer | The target player ID to attach the object to. |
| x | number | Relative X offset. |
| y | number | Relative Y offset. |
| z | number | Relative Z offset. |
| rx | number | Relative X rotation. |
| ry | number | Relative Y rotation. |
| rz | number | Relative Z rotation. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
attachPlayerObjectToPlayer(playerid, pObj, targetid, 0.0, 0.0, 0.3, 0.0, 0.0, 0.0)
```
