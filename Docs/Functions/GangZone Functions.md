# GangZone Functions

---

## `gangZoneCreate`

### Description
Creates a 2D rectangular gang zone on the radar and map.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| minX | number | Minimum X coordinate (western border). |
| minY | number | Minimum Y coordinate (southern border). |
| maxX | number | Maximum X coordinate (eastern border). |
| maxY | number | Maximum Y coordinate (northern border). |

### Return Type
```text
integer
```

### Return Value
Returns the newly created gang zone ID, or `INVALID_GANG_ZONE` (`-1`) on failure.

### Example
```lua
local zoneId = gangZoneCreate(1000.0, -2000.0, 1500.0, -1500.0)
```

---

## `gangZoneDestroy`

### Description
Destroys an existing gang zone.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| zone | integer | The gang zone ID to destroy. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if destroyed, or `false` on failure.

### Example
```lua
gangZoneDestroy(zoneId)
```

---

## `isValidGangZone`

### Description
Checks whether a gang zone with the specified ID exists.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| zone | integer | The gang zone ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the gang zone exists, otherwise `false`.

### Example
```lua
if isValidGangZone(zoneId) then
    print("Gang zone exists")
end
```

---

## `gangZoneShowForPlayer`

### Description
Displays a gang zone on the radar/map for a specific player with a given RGBA color.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| zone | integer | The gang zone ID. |
| color | integer | Hexadecimal RGBA or ARGB color integer. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneShowForPlayer(playerid, zoneId, 0xFF000088) -- Semi-transparent red
```

---

## `gangZoneShowForAll`

### Description
Displays a gang zone for all connected players with a given color.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| zone | integer | The gang zone ID. |
| color | integer | Hexadecimal RGBA or ARGB color integer. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneShowForAll(zoneId, 0x00FF0088) -- Semi-transparent green
```

---

## `gangZoneHideForPlayer`

### Description
Hides a gang zone from a specific player's radar and map.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| zone | integer | The gang zone ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneHideForPlayer(playerid, zoneId)
```

---

## `gangZoneHideForAll`

### Description
Hides a gang zone from all connected players.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| zone | integer | The gang zone ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneHideForAll(zoneId)
```

---

## `gangZoneFlashForPlayer`

### Description
Causes a gang zone to continuously flash with a flashing color for a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| zone | integer | The gang zone ID. |
| color | integer | Hexadecimal RGBA flash color integer. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneFlashForPlayer(playerid, zoneId, 0xFFFFFFFF)
```

---

## `gangZoneFlashForAll`

### Description
Causes a gang zone to flash for all connected players.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| zone | integer | The gang zone ID. |
| color | integer | Hexadecimal RGBA flash color integer. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneFlashForAll(zoneId, 0xFF0000FF)
```

---

## `gangZoneStopFlashForPlayer`

### Description
Stops a flashing gang zone for a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| zone | integer | The gang zone ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneStopFlashForPlayer(playerid, zoneId)
```

---

## `gangZoneStopFlashForAll`

### Description
Stops a flashing gang zone for all connected players.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| zone | integer | The gang zone ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
gangZoneStopFlashForAll(zoneId)
```
