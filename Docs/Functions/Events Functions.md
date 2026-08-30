# Events Functions

---

## `addEventHandler`

### Description
Registers a Lua function to be executed when a specific server event is triggered. Supports multiple event handlers per event.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| eventName | string | The name of the event to listen for (e.g., `"onPlayerConnect"`, `"onScriptInit"`). |
| handler | function | The callback function to invoke when the event is triggered. |

*Note: Also accepts an optional 2nd argument (such as `root` or `resourceRoot`) before the handler function for compatibility.*

### Return Type
```text
integer
```

### Return Value
Returns the total number of active handlers registered for this event on success, or `0` on invalid arguments.

### Example
```lua
addEventHandler("onPlayerConnect", function(playerid)
    print("Player " .. playerid .. " connected!")
end)
```

---

## `removeEventHandler`

### Description
Unregisters a previously registered event handler function from an event.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| eventName | string | The name of the event. |
| handler | function | The function instance previously passed to `addEventHandler`. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the handler was found and removed, otherwise `false`.

### Example
```lua
local function myHandler(playerid)
    -- handle event
end

addEventHandler("onPlayerSpawn", myHandler)
-- Later:
removeEventHandler("onPlayerSpawn", myHandler)
```

---

## `addEvent`

### Description
Registers a custom event name in the event system.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| eventName | string | Custom event name. |
| allowRemoteTrigger | boolean | *(Optional)* Remote triggering allowance flag. |

### Return Type
```text
boolean
```

### Return Value
Always returns `true`.

### Example
```lua
addEvent("onCustomEvent", true)
```

---

## `triggerEvent`

### Description
Triggers an event by name, invoking all registered handler functions with the supplied arguments.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| eventName | string | The name of the event to trigger. |
| ... | any | Variable arguments passed directly to the registered handler callbacks. |

### Return Type
```text
any (or nil)
```

### Return Value
Returns the return value of the last executed handler, or `nil` if no handlers exist or no value was returned.

### Example
```lua
triggerEvent("onCustomEvent", playerid, "test_data", 100)
```

---

## `eventNameFromCallback`

### Description
Helper function that converts a Pawn-style callback name (e.g. `"OnPlayerConnect"`) to the lowerCamelCase Lua event name (`"onPlayerConnect"`).

### Parameters
| Parameter | Type | Description |
|---|---|---|
| callbackName | string | The callback string to convert. |

### Return Type
```text
string
```

### Return Value
Returns the converted event name string.

### Example
```lua
local eventName = eventNameFromCallback("OnPlayerDeath") -- returns "onPlayerDeath"
```

---

## Built-in Server Events Reference

Below are the standard server events triggered by the Legacy Server engine:

| Event Name | Parameters | Description |
|---|---|---|
| `onMainScriptInit` | None | Triggered when the main gamemode script finishes loading. |
| `onMainScriptExit` | None | Triggered when the main gamemode script is unloaded/restarted. |
| `onScriptInit` | None | Triggered when a filterscript / sidescript initializes. |
| `onScriptExit` | None | Triggered when a filterscript / sidescript unloads. |
| `onPlayerConnect` | `playerid: integer` | Triggered when a player connects to the server. |
| `onPlayerDisconnect` | `playerid: integer, reason: integer` | Triggered when a player disconnects (`0`=Timeout, `1`=Quit, `2`=Kicked). |
| `onPlayerSpawn` | `playerid: integer` | Triggered when a player spawns into the game. |
| `onPlayerDeath` | `playerid: integer, killerid: integer, reason: integer` | Triggered when a player dies or is killed. |
| `onVehicleSpawn` | `vehicleid: integer` | Triggered when a vehicle spawns or respawns. |
| `onVehicleDeath` | `vehicleid: integer, killerid: integer` | Triggered when a vehicle is destroyed. |
| `onPlayerText` | `playerid: integer, text: string` | Triggered when a player sends a chat message. Returning `false` suppresses the message. |
| `onPlayerInfoChange` | `playerid: integer` | Triggered when a player's client information changes. |
| `onPlayerEnterVehicle` | `playerid: integer, vehicleid: integer, ispassenger: boolean` | Triggered when a player begins entering a vehicle. |
| `onPlayerExitVehicle` | `playerid: integer, vehicleid: integer` | Triggered when a player starts exiting a vehicle. |
| `onPlayerStateChange` | `playerid: integer, newstate: integer, oldstate: integer` | Triggered when a player's state changes (`PLAYER_STATE.*`). |
| `onPlayerEnterCheckpoint` | `playerid: integer` | Triggered when a player enters their active checkpoint. |
| `onPlayerLeaveCheckpoint` | `playerid: integer` | Triggered when a player leaves their active checkpoint. |
| `onPlayerEnterRaceCheckpoint` | `playerid: integer` | Triggered when a player enters their active race checkpoint. |
| `onPlayerLeaveRaceCheckpoint` | `playerid: integer` | Triggered when a player leaves their active race checkpoint. |
| `onPlayerKeyStateChange` | `playerid: integer, newkeys: integer, oldkeys: integer` | Triggered when a player presses or releases mapped keys. |
| `onObjectMoved` | `objectid: integer` | Triggered when a global object finishes moving. |
| `onPlayerObjectMoved` | `playerid: integer, objectid: integer` | Triggered when a player object finishes moving. |
| `onPlayerPickUpPickup` | `playerid: integer, pickupid: integer` | Triggered when a player walks over a pickup. |
| `onPlayerExitedMenu` | `playerid: integer` | Triggered when a player cancels/exits a menu. |
| `onPlayerSelectedMenuRow` | `playerid: integer, row: integer` | Triggered when a player selects a row in a menu. |
| `onEnterExitModShop` | `playerid: integer, enterexit: integer, interiorid: integer` | Triggered when a player enters (`1`) or exits (`0`) a vehicle mod shop. |
| `onPlayerInteriorChange` | `playerid: integer, newid: integer, oldid: integer` | Triggered when a player transitions to a new interior. |
| `onRconLoginAttempt` | `ip: string, password: string, success: boolean` | Triggered when an RCON login attempt occurs. |
| `onPlayerBeginTyping` | `playerid: integer` | Triggered when a player starts typing in chat. |
| `onPlayerEndTyping` | `playerid: integer` | Triggered when a player stops typing in chat. |
| `onPlayerStunt` | `playerid: integer, vehicleid: integer` | Triggered when a player performs a vehicle stunt. |
| `onClientCheckResponse` | `playerid: integer, type: integer, address: integer, checksum: integer` | Triggered in response to a client memory checksum query. |
| `onVehicleSirenStateChange` | `playerid: integer, vehicleid: integer, newstate: integer` | Triggered when vehicle sirens are toggled. |
| `onVehicleDamageStatusUpdate` | `vehicleid: integer, playerid: integer` | Triggered when vehicle damage status synchronizes. |
| `onActorStreamIn` | `actorid: integer, forplayerid: integer` | Triggered when an actor streams in for a player. |
| `onActorStreamOut` | `actorid: integer, forplayerid: integer` | Triggered when an actor streams out for a player. |
| `onPlayerGiveDamageActor` | `playerid: integer, actorid: integer, damage: number, weaponid: integer, bodypart: integer` | Triggered when a player damages an actor. |
| `onPlayerClickPlayer` | `playerid: integer, clickedplayerid: integer, source: integer` | Triggered when a player clicks on another player in the scoreboard. |
