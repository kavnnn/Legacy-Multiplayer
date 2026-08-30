# NetStats Functions

---

## `netStatsGetConnectedTime`

### Description
Retrieves the total connected time timestamp for a specific player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID to query. |

### Return Type
```text
integer
```

### Return Value
Returns the connection start timestamp in milliseconds, or `0` if not available.

### Example
```lua
local connectedTime = netStatsGetConnectedTime(playerid)
```

---

## `netStatsMessagesReceived`

### Description
Retrieves the total number of network messages received from a player (including valid, invalid, and duplicate messages).

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns the total count of received messages, or `0` if not available.

### Example
```lua
local msgs = netStatsMessagesReceived(playerid)
```

---

## `netStatsBytesReceived`

### Description
Retrieves the total number of bytes received from a player across their current connection.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns total bytes received as an integer, or `0` on error.

### Example
```lua
local bytes = netStatsBytesReceived(playerid)
```

---

## `netStatsMessagesSent`

### Description
Retrieves the total number of network messages sent from the server to a player across all network priorities.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns total messages sent count, or `0`.

### Example
```lua
local sent = netStatsMessagesSent(playerid)
```

---

## `netStatsBytesSent`

### Description
Retrieves the total number of bytes sent by the server to a player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns total bytes sent as an integer, or `0`.

### Example
```lua
local bytesSent = netStatsBytesSent(playerid)
```

---

## `netStatsMessagesRecvPerSecond`

### Description
Retrieves the current rate of incoming messages received per second from a player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns messages received per second as an integer, or `0`.

### Example
```lua
local rate = netStatsMessagesRecvPerSecond(playerid)
if rate > 200 then
    print("Warning: High incoming message rate from player " .. playerid)
end
```

---

## `netStatsPacketLossPercent`

### Description
Calculates the packet loss percentage for a player's connection based on total resent bits vs sent bits.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
number
```

### Return Value
Returns the packet loss as a percentage `number` (e.g. `1.25`%), or `0.0` on error.

### Example
```lua
local loss = netStatsPacketLossPercent(playerid)
print(string.format("Player packet loss: %.2f%%", loss))
```

---

## `netStatsConnectionStatus`

### Description
Retrieves the low-level RakNet connection state code of a player.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
integer
```

### Return Value
Returns the connection mode integer, or `-1` if disconnected / invalid.

### Example
```lua
local status = netStatsConnectionStatus(playerid)
```

---

## `netStatsGetIpPort`

### Description
Retrieves the IP address and remote port combination for a player as a string.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
string (or nil)
```

### Return Value
Returns formatted string `"IP:PORT"` (e.g. `"127.0.0.1:7777"`), or `nil` if player is not connected.

### Example
```lua
local ipPort = netStatsGetIpPort(playerid)
print("Remote address: " .. tostring(ipPort))
```

---

## `getPlayerNetworkStats`

### Description
Retrieves the full diagnostic network statistics report for a specific player as formatted text.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| playerId | integer | The player ID. |

### Return Type
```text
string
```

### Return Value
Returns a multi-line string containing comprehensive network metrics (messages, ping, bytes, packet loss, bandwidth).

### Example
```lua
local report = getPlayerNetworkStats(playerid)
print(report)
```

---

## `getNetworkStats`

### Description
Retrieves the server-wide diagnostic network statistics and server tick rate.

### Parameters
None

### Return Type
```text
string
```

### Return Value
Returns a multi-line string report of overall server networking statistics and server ticks.

### Example
```lua
local serverStats = getNetworkStats()
print(serverStats)
```
