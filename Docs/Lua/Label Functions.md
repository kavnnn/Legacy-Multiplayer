# Label Functions

---

## Global 3D Text Labels

### `create3DTextLabel`

#### Description
Creates a global 3D text label visible in the 3D game world.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| text | string | The text content to display. |
| color | integer | Hexadecimal color code (e.g. `0xFFFFFFFF`). |
| x | number | The X world position. |
| y | number | The Y world position. |
| z | number | The Z world position. |
| drawDistance | number | Maximum distance from which the label is rendered. |
| virtualWorld | integer | The virtual world ID in which the label appears. |
| testLOS | boolean | Whether line-of-sight is required to see through walls. |

#### Return Type
```text
integer
```

#### Return Value
Returns the newly created label ID on success, or `INVALID_3DTEXT_ID` (`65535`) on failure.

#### Example
```lua
local label = create3DTextLabel("Bank Entrance", 0x00FF00FF, 1481.0, -1770.0, 15.0, 40.0, 0, false)
```

---

### `delete3DTextLabel`

#### Description
Deletes a global 3D text label.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| labelId | integer | The 3D text label ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if deleted, or `false` if invalid.

#### Example
```lua
delete3DTextLabel(label)
```

---

### `attach3DTextLabelToPlayer`

#### Description
Attaches a global 3D text label to a specific player with a relative offset.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| labelId | integer | The 3D text label ID. |
| playerId | integer | The player ID to attach to. |
| x | number | Relative X offset. |
| y | number | Relative Y offset. |
| z | number | Relative Z offset. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
attach3DTextLabelToPlayer(label, playerid, 0.0, 0.0, 0.7)
```

---

### `attach3DTextLabelToVehicle`

#### Description
Attaches a global 3D text label to a vehicle with a relative offset.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| labelId | integer | The 3D text label ID. |
| vehicleId | integer | The vehicle ID to attach to. |
| x | number | Relative X offset. |
| y | number | Relative Y offset. |
| z | number | Relative Z offset. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
attach3DTextLabelToVehicle(label, vehicleid, 0.0, 0.0, 1.2)
```

---

### `update3DTextLabelText`

#### Description
Updates the text and color of an existing global 3D text label.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| labelId | integer | The 3D text label ID. |
| color | integer | New hexadecimal color. |
| text | string | New text content. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
update3DTextLabelText(label, 0xFF0000FF, "Updated Text")
```

---

### `isValid3DTextLabel`

#### Description
Checks whether a global 3D text label ID is valid and active.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| labelId | integer | The label ID to check. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if valid, otherwise `false`.

#### Example
```lua
if isValid3DTextLabel(label) then
    print("Label is active")
end
```

---

## Per-Player 3D Text Labels

### `createPlayer3DTextLabel`

#### Description
Creates a 3D text label visible exclusively to a single player.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID who will see this label. |
| text | string | The text content to display. |
| color | integer | Hexadecimal color code. |
| x | number | The X world position. |
| y | number | The Y world position. |
| z | number | The Z world position. |
| drawDistance | number | Maximum rendering distance. |
| attachedPlayer | integer | Player ID to attach to (`INVALID_PLAYER_ID` / `65535` for none). |
| attachedVehicle | integer | Vehicle ID to attach to (`INVALID_VEHICLE_ID` / `65535` for none). |
| testLOS | boolean | Whether line-of-sight is required. |

#### Return Type
```text
integer
```

#### Return Value
Returns the created player 3D text label ID, or `INVALID_3DTEXT_ID` (`65535`) on failure.

#### Example
```lua
local pLabel = createPlayer3DTextLabel(playerid, "Your Target", 0xFFFF00FF, 1500.0, -1600.0, 14.0, 50.0, 65535, 65535, false)
```

---

### `deletePlayer3DTextLabel`

#### Description
Deletes a per-player 3D text label.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| labelId | integer | The player 3D text label ID. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` if deleted, or `false` on failure.

#### Example
```lua
deletePlayer3DTextLabel(playerid, pLabel)
```

---

### `updatePlayer3DTextLabelText`

#### Description
Updates the text and color of a per-player 3D text label.

#### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| labelId | integer | The player 3D text label ID. |
| color | integer | New hexadecimal color. |
| text | string | New text content. |

#### Return Type
```text
boolean
```

#### Return Value
Returns `true` on success, or `false` on failure.

#### Example
```lua
updatePlayer3DTextLabelText(playerid, pLabel, 0x00FFFFFF, "Objective Complete")
```
