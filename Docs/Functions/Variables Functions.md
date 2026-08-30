# Variables Functions

---

## `setServerVar`

### Description
Dynamically sets a server variable (SVar) to an integer, float, or string depending on the passed value type.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | The variable identifier name. |
| value | integer, number, or string | The value to store. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
setServerVar("motd", "Welcome to Legacy Server!")
setServerVar("max_speed", 120.5)
setServerVar("round_number", 5)
```

---

## `setSVarInt`

### Description
Stores an integer variable in the server's global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |
| value | integer | Integer value to assign. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
setSVarInt("matchScore", 100)
```

---

## `setSVarString`

### Description
Stores a string variable in the server's global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |
| value | string | String value to assign. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
setSVarString("serverTag", "[RP]")
```

---

## `setSVarFloat`

### Description
Stores a floating-point number in the server's global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |
| value | number | Floating-point value to assign. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
setSVarFloat("multiplier", 1.75)
```

---

## `getSVarInt`

### Description
Retrieves an integer value from the global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |

### Return Type
```text
integer
```

### Return Value
Returns the stored integer value, or `0` if the variable does not exist.

### Example
```lua
local score = getSVarInt("matchScore")
```

---

## `getSVarString`

### Description
Retrieves a string value from the global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |

### Return Type
```text
string (or nil)
```

### Return Value
Returns the string value, or `nil` if the variable does not exist.

### Example
```lua
local tag = getSVarString("serverTag")
```

---

## `getSVarFloat`

### Description
Retrieves a floating-point number from the global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |

### Return Type
```text
number
```

### Return Value
Returns the stored float value, or `0.0` if the variable does not exist.

### Example
```lua
local mult = getSVarFloat("multiplier")
```

---

## `deleteSVar`

### Description
Deletes an existing variable from the global SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name to remove. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if removed, or `false` on failure.

### Example
```lua
deleteSVar("matchScore")
```

---

## `getSVarType`

### Description
Retrieves the data type identifier of a stored SVar.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| name | string | Variable name. |

### Return Type
```text
integer
```

### Return Value
Returns one of: `SERVER_VARTYPE_NONE` (`0`), `SERVER_VARTYPE_INT` (`1`), `SERVER_VARTYPE_STRING` (`2`), `SERVER_VARTYPE_FLOAT` (`3`).

### Example
```lua
local varType = getSVarType("matchScore")
if varType == SERVER_VARTYPE_INT then
    print("Variable is an integer")
end
```

---

## `getSVarNameAtIndex`

### Description
Retrieves the variable name stored at a given numeric index in the SVar pool.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| index | integer | SVar pool index. |

### Return Type
```text
string (or nil)
```

### Return Value
Returns variable name string, or `nil` if empty.

### Example
```lua
local name = getSVarNameAtIndex(0)
```

---

## `getSVarsUpperIndex`

### Description
Retrieves the upper bound / capacity size of the global SVar pool for iteration.

### Parameters
None

### Return Type
```text
integer
```

### Return Value
Returns total SVar pool size integer.

### Example
```lua
local maxIndex = getSVarsUpperIndex()
for i = 0, maxIndex - 1 do
    local name = getSVarNameAtIndex(i)
    if name then
        print(i, name)
    end
end
```
