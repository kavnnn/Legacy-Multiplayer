# Menu Functions

---

## `createMenu`

### Description
Creates a new native server menu.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| title | string | Menu title header text. |
| columns | integer | Number of columns (1 or 2). |
| x | number | Screen X position coordinate. |
| y | number | Screen Y position coordinate. |
| col1Width | number | Width of the first column in screen units. |
| col2Width | number | Width of the second column in screen units. |

### Return Type
```text
integer
```

### Return Value
Returns the menu ID on success, or `INVALID_MENU` (`255`) on failure.

### Example
```lua
local menu = createMenu("Weapon Shop", 1, 200.0, 150.0, 150.0, 0.0)
```

---

## `destroyMenu`

### Description
Destroys an existing menu.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID to destroy. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if destroyed, or `false` on failure.

### Example
```lua
destroyMenu(menu)
```

---

## `isValidMenu`

### Description
Checks whether a menu ID is valid and exists.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID to check. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the menu exists, otherwise `false`.

### Example
```lua
if isValidMenu(menu) then
    print("Menu is active")
end
```

---

## `addMenuItem`

### Description
Adds an item / row to a column in a menu.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID. |
| column | integer | The column index (`0` or `1`). |
| text | string | The text for this menu row. |

### Return Type
```text
integer
```

### Return Value
Returns the row index where the item was added, or `-1` on failure.

### Example
```lua
addMenuItem(menu, 0, "Desert Eagle - $500")
addMenuItem(menu, 0, "Shotgun - $800")
```

---

## `setMenuColumnHeader`

### Description
Sets the column header text of a menu.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID. |
| column | integer | The column index (`0` or `1`). |
| text | string | The header text to display. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
setMenuColumnHeader(menu, 0, "Available Weapons")
```

---

## `showMenuForPlayer`

### Description
Displays a menu on the screen for a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID. |
| playerId | integer | The player ID to show the menu to. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
showMenuForPlayer(menu, playerid)
```

---

## `hideMenuForPlayer`

### Description
Hides the active menu for a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID. |
| playerId | integer | The player ID to hide the menu for. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
hideMenuForPlayer(menu, playerid)
```

---

## `disableMenu`

### Description
Disables interaction for an entire menu.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
disableMenu(menu)
```

---

## `disableMenuRow`

### Description
Disables interaction for a specific row in a menu.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| menuId | integer | The menu ID. |
| row | integer | The row index to disable. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
disableMenuRow(menu, 0)
```

---

## `getPlayerMenu`

### Description
Retrieves the menu ID of the menu currently displayed to a player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns the menu ID currently open for the player, or `INVALID_MENU` (`255`) if no menu is open.

### Example
```lua
local currentMenu = getPlayerMenu(playerid)
```
