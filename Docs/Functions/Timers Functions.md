# Timers Functions

---

## `setTimer`

### Description
Creates a one-shot or recurring timer that invokes a callback function after a specified interval in milliseconds. Supports passing a Lua closure function or a global function name string, along with arbitrary trailing arguments.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| callback | function or string | The Lua function (closure) or global function name string to invoke. |
| interval | integer | Time delay in milliseconds before timer fires. |
| repeating | boolean | `true` for a recurring interval, `false` for one-time execution. |
| ... | any | *(Optional)* Variable arguments to pass directly to the callback function when it fires. |

### Return Type
```text
integer
```

### Return Value
Returns the newly created timer ID integer on success, or `0` on invalid arguments.

### Example
```lua
-- Using an inline anonymous function:
local timerId = setTimer(function(message)
    print("Timer fired: " .. message)
end, 1000, true, "Hello World")

-- Using a global function:
function onTick(playerid)
    print("Tick for player " .. playerid)
end

setTimer("onTick", 5000, false, playerid)
```

---

## `killTimer`

### Description
Stops and cancels an active timer by its timer ID.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| timerId | integer | The timer ID returned by `setTimer`. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the timer was found and cancelled, or `false` if the timer does not exist.

### Example
```lua
killTimer(timerId)
```
