# Actor Functions

---

## `createActor`

### Description
Creates a new static actor (pedestrian) at the specified world position and facing angle.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| modelId | integer | The ped skin/model ID. |
| x | number | The X world position coordinate. |
| y | number | The Y world position coordinate. |
| z | number | The Z world position coordinate. |
| rotation | number | The facing angle rotation in degrees. |

### Return Type
```text
integer
```

### Return Value
Returns the newly created actor ID on success, or `INVALID_ACTOR_ID` (`65535`) on failure.

### Example
```lua
local actorId = createActor(294, 1782.1, -1299.4, 13.5, 90.0)
```

---

## `destroyActor`

### Description
Destroys an existing actor from the server.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The ID of the actor to destroy. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the actor was successfully destroyed, or `false` if the actor does not exist.

### Example
```lua
destroyActor(actorId)
```

---

## `isValidActor`

### Description
Checks whether an actor with the given ID exists and is currently active.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID to check. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the actor exists and is active, otherwise `false`.

### Example
```lua
if isValidActor(actorId) then
    print("Actor exists!")
end
```

---

## `setActorPosition` / `setActorPos`

### Description
Sets the world position coordinates of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID to move. |
| x | number | The new X world position coordinate. |
| y | number | The new Y world position coordinate. |
| z | number | The new Z world position coordinate. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the position was set, or `false` if the actor was not found.

### Example
```lua
setActorPosition(actorId, 1782.1, -1299.4, 15.0)
```

---

## `getActorPosition` / `getActorPos`

### Description
Retrieves the current world position coordinates of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID to query. |

### Return Type
```text
number, number, number (or nil)
```

### Return Value
Returns three `number` values (`x, y, z`) representing world coordinates, or `nil` if the actor does not exist.

### Example
```lua
local x, y, z = getActorPosition(actorId)
if x then
    print(string.format("Actor position: %.2f, %.2f, %.2f", x, y, z))
end
```

---

## `setActorFacingAngle`

### Description
Sets the facing angle (rotation) of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |
| angle | number | The new facing angle in degrees (0.0 - 360.0). |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the angle was updated, or `false` if the actor does not exist.

### Example
```lua
setActorFacingAngle(actorId, 180.0)
```

---

## `getActorFacingAngle`

### Description
Retrieves the current facing angle of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID to query. |

### Return Type
```text
number (or nil)
```

### Return Value
Returns the facing angle in degrees, or `nil` if the actor does not exist.

### Example
```lua
local angle = getActorFacingAngle(actorId)
```

---

## `setActorHealth`

### Description
Sets the health value of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |
| health | number | The health amount to assign. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the health was updated, or `false` if the actor does not exist.

### Example
```lua
setActorHealth(actorId, 100.0)
```

---

## `getActorHealth`

### Description
Retrieves the current health value of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |

### Return Type
```text
number (or nil)
```

### Return Value
Returns the current health amount as a `number`, or `nil` if the actor does not exist.

### Example
```lua
local health = getActorHealth(actorId)
```

---

## `setActorInvulnerable`

### Description
Toggles whether an actor is invulnerable to damage.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |
| invulnerable | boolean | `true` to make invulnerable, `false` to make vulnerable. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the state was updated, or `false` if the actor does not exist.

### Example
```lua
setActorInvulnerable(actorId, true)
```

---

## `isActorInvulnerable`

### Description
Checks whether an actor is currently invulnerable.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the actor exists and is invulnerable, otherwise `false`.

### Example
```lua
if isActorInvulnerable(actorId) then
    print("Actor cannot be damaged")
end
```

---

## `setActorVirtualWorld`

### Description
Assigns an actor to a specific virtual world.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |
| world | integer | The virtual world ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the virtual world was set, or `false` if the actor does not exist.

### Example
```lua
setActorVirtualWorld(actorId, 1)
```

---

## `getActorVirtualWorld`

### Description
Retrieves the virtual world ID of an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |

### Return Type
```text
integer
```

### Return Value
Returns the virtual world ID, or `0` if the actor does not exist.

### Example
```lua
local vw = getActorVirtualWorld(actorId)
```

---

## `applyActorAnimation`

### Description
Plays an animation on an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |
| lib | string | The animation library / dictionary name. |
| name | string | The animation name. |
| delta | number | Speed / delta multiplier for the animation. |
| loop | boolean | Whether the animation should loop continuously. |
| lockX | boolean | Lock X position displacement. |
| lockY | boolean | Lock Y position displacement. |
| freeze | boolean | Freeze the actor when the animation finishes. |
| time | integer | Animation duration in milliseconds (`0` for indefinite). |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the animation was applied, or `false` if the actor does not exist.

### Example
```lua
applyActorAnimation(actorId, "DEALER", "DEALER_IDLE", 4.1, true, false, false, false, 0)
```

---

## `clearActorAnimations`

### Description
Stops and clears any currently playing animation on an actor.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| actorId | integer | The actor ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if cleared, or `false` if the actor does not exist.

### Example
```lua
clearActorAnimations(actorId)
```
