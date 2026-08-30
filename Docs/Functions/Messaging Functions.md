# Messaging Functions

---

## `sendClientMessage`

### Description
Sends a colored chat message to a specific connected player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID to receive the message. |
| color | integer | Hexadecimal RGBA/ARGB color code. |
| message | string | The message text to display in chat. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if sent, or `false` if the player is not connected or network is inactive.

### Example
```lua
sendClientMessage(playerid, 0xFFFFFFFF, "Welcome to the server!")
```

---

## `sendClientMessageToAll`

### Description
Sends a colored chat message to all connected players on the server.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| color | integer | Hexadecimal RGBA/ARGB color code. |
| message | string | The message text. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if sent, or `false` on failure.

### Example
```lua
sendClientMessageToAll(0xFFFF00FF, "[SERVER] Global announcement.")
```

---

## `gameTextForPlayer`

### Description
Displays formatted on-screen GameText to a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |
| text | string | The GameText string (supports GTA formatting codes like `~r~`, `~w~`, `~n~`). |
| time | integer | Display duration in milliseconds. |
| style | integer | GameText display style (0 - 6). |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if sent, or `false` on failure.

### Example
```lua
gameTextForPlayer(playerid, "~g~MISSION PASSED!", 5000, 1)
```

---

## `gameTextForAll`

### Description
Displays GameText on screen to all connected players.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| text | string | The GameText string. |
| time | integer | Display duration in milliseconds. |
| style | integer | GameText style (0 - 6). |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if sent, or `false` on failure.

### Example
```lua
gameTextForAll("~r~PAYDAY!", 4000, 3)
```

---

## `sendPlayerMessageToPlayer`

### Description
Sends a fake/simulated player chat message to a specific player (displays as `<SenderName>: message`).

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The recipient player ID. |
| senderId | integer | The sender player ID whose name will appear. |
| message | string | The chat message. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` if either player is disconnected.

### Example
```lua
sendPlayerMessageToPlayer(targetid, senderid, "Private message")
```

---

## `sendPlayerMessageToAll`

### Description
Sends a simulated player chat message to all players on the server.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| senderId | integer | The sender player ID. |
| message | string | The chat message. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` if the sender is not connected.

### Example
```lua
sendPlayerMessageToAll(playerid, "Hello everyone!")
```

---

## `sendDeathMessage`

### Description
Broadcasts a killfeed / death message to all connected players.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| killerId | integer | Killer player ID (`INVALID_PLAYER_ID` / `65535` for environment/suicide). |
| killeeId | integer | Victim player ID. |
| weaponId | integer | Weapon / reason ID (`WEAPON.*`). |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if broadcasted, or `false` on network failure.

### Example
```lua
sendDeathMessage(killerid, playerid, WEAPON.DEAGLE)
```

---

## `sendDeathMessageToPlayer`

### Description
Sends a killfeed death message entry to a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | Recipient player ID. |
| killerId | integer | Killer player ID. |
| killeeId | integer | Victim player ID. |
| weaponId | integer | Weapon ID. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if sent, or `false` if the player is not connected.

### Example
```lua
sendDeathMessageToPlayer(playerid, killerid, victimId, 24)
```

---

## `print` / `printServer`

### Description
Prints one or more values to the server console, UI log, and `server.log` file. Automatically joins multiple arguments with tab characters.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| ... | any | Comma-separated list of values to print. |

### Return Type
```text
nil
```

### Return Value
This function does not return a value.

### Example
```lua
print("Server initialized successfully", 123, true)
```

---

## `printf`

### Description
Formats a string and prints it to the console, UI log, and `server.log` file (using standard `string.format` formatting).

### Parameters
| Parameter | Type | Description |
|---|---|---|
| format | string | Format string (e.g. `"Player %s joined at %d"`). |
| ... | any | Variable format arguments. |

### Return Type
```text
nil
```

### Return Value
This function does not return a value.

### Example
```lua
printf("Player ID %d scored %d points", playerid, 500)
```
