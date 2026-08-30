# Pickup Functions

---

## `createPickup`

### Description
Creates a dynamic world pickup with a specified model, spawn type, position, and virtual world.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| model | integer | GTA model ID for the pickup. |
| type | integer | Pickup spawn/respawn behavior type (e.g. `1` for static non-respawning, `2` for normal respawn). |
| x | number | World X coordinate. |
| y | number | World Y coordinate. |
| z | number | World Z coordinate. |
| virtualWorld | integer | Virtual world ID where the pickup exists. |

### Return Type
```text
integer
```

### Return Value
Returns the newly created pickup ID on success, or `-1` on failure.

### Example
```lua
local pickup = createPickup(1240, 2, 1500.0, -1600.0, 13.5, 0) -- Heart pickup
```

---

## `addStaticPickup`

### Description
Creates a static non-destroyable pickup in the world.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| model | integer | GTA model ID. |
| type | integer | Spawn behavior type. |
| x | number | World X coordinate. |
| y | number | World Y coordinate. |
| z | number | World Z coordinate. |
| virtualWorld | integer | Virtual world ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if added successfully, otherwise `false`.

### Example
```lua
addStaticPickup(1242, 2, 1505.0, -1600.0, 13.5, 0) -- Armour pickup
```

---

## `destroyPickup`

### Description
Destroys an existing dynamic pickup.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID to destroy. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if destroyed, or `false` on failure.

### Example
```lua
destroyPickup(pickup)
```

---

## `destroyAllPickups`

### Description
Destroys all active pickups currently in the world.

### Parameters
None

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
destroyAllPickups()
```

---

## `isValidPickup`

### Description
Checks whether a pickup ID is currently valid and active.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID to check. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if valid, otherwise `false`.

### Example
```lua
if isValidPickup(pickup) then
    print("Pickup is active")
end
```

---

## `isStaticPickup`

### Description
Checks whether a pickup was created as a static pickup.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if static, otherwise `false`.

### Example
```lua
local isStatic = isStaticPickup(pickup)
```

---

## `getPickupPosition` / `getPickupPos`

### Description
Retrieves the world position coordinates of a pickup.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID. |

### Return Type
```text
number, number, number (or nil)
```

### Return Value
Returns three `number` values (`x, y, z`), or `nil` if the pickup is invalid.

### Example
```lua
local x, y, z = getPickupPosition(pickup)
```

---

## `getPickupModel`

### Description
Retrieves the model ID of a pickup.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID. |

### Return Type
```text
integer
```

### Return Value
Returns the model ID, or `-1` if the pickup is invalid.

### Example
```lua
local model = getPickupModel(pickup)
```

---

## `getPickupType`

### Description
Retrieves the spawn type of a pickup.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID. |

### Return Type
```text
integer
```

### Return Value
Returns the pickup type integer, or `-1` if invalid.

### Example
```lua
local pType = getPickupType(pickup)
```

---

## `getPickupCount`

### Description
Retrieves the total number of currently active pickups on the server.

### Parameters
None

### Return Type
```text
integer
```

### Return Value
Returns the active pickup count.

### Example
```lua
local count = getPickupCount()
```

---

## `getPickupPoolSize`

### Description
Retrieves the highest active pickup slot index in the pickup pool.

### Parameters
None

### Return Type
```text
integer
```

### Return Value
Returns highest active pickup index.

### Example
```lua
local poolSize = getPickupPoolSize()
```

---

## `getPickupVirtualWorld`

### Description
Retrieves the virtual world ID in which a pickup exists.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| pickupId | integer | The pickup ID. |

### Return Type
```text
integer
```

### Return Value
Returns virtual world ID, or `0` if invalid.

### Example
```lua
local vw = getPickupVirtualWorld(pickup)
```
