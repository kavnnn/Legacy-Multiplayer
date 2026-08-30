# World Functions

---

## Environment & Server State

### `setWeather`
- **Description**: Sets the global weather ID for all players on the server.
- **Parameters**: `weatherId: integer` (0 - 45)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setWeather(10)` -- Clear sunny weather

### `getWeather`
- **Description**: Retrieves the current global weather ID.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Current weather ID integer.
- **Example**: `local weather = getWeather()`

### `setWorldTime`
- **Description**: Sets the global world clock hour (0 - 23).
- **Parameters**: `hour: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setWorldTime(12)` -- Noon

### `getWorldTime`
- **Description**: Retrieves the current global world clock hour.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: World hour integer (0 - 23).
- **Example**: `local hour = getWorldTime()`

### `setGravity`
- **Description**: Sets world gravity multiplier (default GTA SA gravity is `0.008`).
- **Parameters**: `gravity: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setGravity(0.008)`

### `getGravity`
- **Description**: Retrieves the current world gravity.
- **Parameters**: None
- **Return Type**: `number`
- **Return Value**: Gravity float value.
- **Example**: `local g = getGravity()`

### `setGameModeText`
- **Description**: Sets the gamemode text displayed in the server browser.
- **Parameters**: `text: string`
- **Return Type**: `boolean`
- **Return Value**: `true` on success.
- **Example**: `setGameModeText("Legacy RP v1.0")`

### `getMaxPlayers`
- **Description**: Retrieves maximum player capacity configured for the server.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Max players integer.
- **Example**: `local max = getMaxPlayers()`

### `getTickCount`
- **Description**: Retrieves the current system uptime timestamp in milliseconds.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Milliseconds count.
- **Example**: `local start = getTickCount()`

### `getServerTickCount`
- **Description**: Retrieves how many milliseconds have elapsed since the server started.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Server uptime milliseconds.
- **Example**: `local uptime = getServerTickCount()`

### `getServerTickRate`
- **Description**: Retrieves the measured server processing tick rate per second.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Server ticks per second.
- **Example**: `local tickrate = getServerTickRate()`

### `gameModeExit`
- **Description**: Restarts the server gamemode or triggers shutdown if no scripts remain.
- **Parameters**: None
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `gameModeExit()`

---

## Server Rules & Game Mechanics

| Function | Parameters | Return Type | Description |
|---|---|---|---|
| `showNameTags` | `show: boolean` | `boolean` | Toggles overhead nametag rendering for all players. |
| `showPlayerMarkers` | `show: boolean` | `boolean` | Toggles player radar markers on the minimap. |
| `allowInteriorWeapons` | `allow: boolean` | `boolean` | Allows or disallows firing weapons inside interior environments. |
| `allowAdminTeleport` | `allow: boolean` | `boolean` | Toggles right-click map teleportation for admins. |
| `enableZoneNames` | `enable: boolean` | `boolean` | Enables showing area/neighborhood names when entering new areas. |
| `enableTirePopping` | `enable: boolean` | `boolean` | Enables tire popping damage when shooting vehicle wheels. |
| `usePlayerPedAnims` | None | `boolean` | Enables standard CJ sprint and running animations for all skins. |
| `disableInteriorEnterExits` | None | `boolean` | Disables default yellow interior enter/exit entrance markers. |
| `disableVehicleMarkers` | None | `boolean` | Disables default vehicle minimap markers. |
| `disableNameTagLOS` | None | `boolean` | Allows player nametags to be seen through walls without LOS checks. |
| `setNameTagDrawDistance` | `distance: number` | `boolean` | Sets maximum viewing distance for player overhead nametags. |
| `limitGlobalChatRadius` | `radius: number` | `boolean` | Limits default local chat hearing distance in game units. |
| `limitPlayerMarkerRadius` | `radius: number` | `boolean` | Limits radar marker visibility distance. |
| `setDeathDropAmount` | `amount: integer` | `boolean` | Sets amount of cash dropped by players upon dying. |
| `setDisabledWeapons` | `...integer` | `boolean` | Disables synchronization for a list of weapon IDs. |

---

## Spawns & Classes

### `addPlayerClass`
- **Description**: Adds a spawn class available in the class selection screen.
- **Parameters**: `skinId: integer`, `x: number`, `y: number`, `z: number`, `a: number`, `weapon1: integer`, `ammo1: integer`, `weapon2: integer`, `ammo2: integer`, `weapon3: integer`, `ammo3: integer`
- **Return Type**: `integer`
- **Return Value**: Newly registered class ID.
- **Example**: `local classId = addPlayerClass(294, 1500.0, -1600.0, 13.5, 0.0, 24, 100, 29, 200, 0, 0)`

### `addPlayerClassEx`
- **Description**: Adds a team-restricted spawn class to the class selection screen.
- **Parameters**: `teamId: integer`, `skinId: integer`, `x: number`, `y: number`, `z: number`, `a: number`, `weapon1: integer`, `ammo1: integer`, `weapon2: integer`, `ammo2: integer`, `weapon3: integer`, `ammo3: integer`
- **Return Type**: `integer`
- **Return Value**: Newly registered class ID.
- **Example**: `addPlayerClassEx(1, 280, 1550.0, -1600.0, 13.5, 90.0, 3, 1, 24, 100, 0, 0)`

---

## Explosions & Stunts

### `createExplosion`
- **Description**: Creates a global explosion visible to all players.
- **Parameters**: `x: number`, `y: number`, `z: number`, `type: integer` (0 - 13), `radius: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `createExplosion(1500.0, -1600.0, 13.5, 2, 10.0)`

### `createExplosionForPlayer`
- **Description**: Creates an explosion visible only to a specific player.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`, `type: integer`, `radius: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `createExplosionForPlayer(playerid, 1500.0, -1600.0, 13.5, 1, 5.0)`

### `enableStuntBonusForAll`
- **Description**: Enables or disables money awards for performing vehicle stunts globally.
- **Parameters**: `enable: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success.
- **Example**: `enableStuntBonusForAll(false)`

### `enableStuntBonusForPlayer`
- **Description**: Enables or disables stunt bonus awards for a specific player.
- **Parameters**: `playerId: integer`, `enable: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success.
- **Example**: `enableStuntBonusForPlayer(playerid, true)`

---

## Administration & Banning

### `kick`
- **Description**: Disconnects a player from the server.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `kick(playerid)`

### `ban`
- **Description**: Permanently bans a player by IP and username.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `ban(playerid)`

### `banEx`
- **Description**: Permanently bans a player with a specified reason string.
- **Parameters**: `playerId: integer`, `reason: string`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `banEx(playerid, "Cheating / Speedhack")`

### `removeBan`
- **Description**: Unbans an IP address in `samp.ban`.
- **Parameters**: `ip: string`
- **Return Type**: `boolean`
- **Return Value**: `true` on success.
- **Example**: `removeBan("127.0.0.1")`

### `isBanned`
- **Description**: Checks whether an IP address is currently banned.
- **Parameters**: `ip: string`
- **Return Type**: `boolean`
- **Return Value**: `true` if banned, `false` otherwise.
- **Example**: `if isBanned("127.0.0.1") then ... end`

### `blockIpAddress`
- **Description**: Temporarily blocks an IP address at network firewall level for duration in milliseconds.
- **Parameters**: `ip: string`, `timeMs: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success.
- **Example**: `blockIpAddress("127.0.0.1", 60000)` -- Block for 60 seconds

### `unblockIpAddress`
- **Description**: Unblocks a temporarily blocked IP address.
- **Parameters**: `ip: string`
- **Return Type**: `boolean`
- **Return Value**: `true` on success.
- **Example**: `unblockIpAddress("127.0.0.1")`

---

## Utilities & Math

### `vectorSize`
- **Description**: Calculates Euclidean magnitude of a 3D vector $\sqrt{x^2 + y^2 + z^2}$.
- **Parameters**: `x: number`, `y: number`, `z: number`
- **Return Type**: `number`
- **Return Value**: Magnitude length.
- **Example**: `local len = vectorSize(3.0, 4.0, 0.0)` -- returns 5.0

### `asin`, `acos`, `atan`, `atan2`
- **Description**: Trigonometric functions returning results in degrees (0 - 360).
- **Parameters**: `value: number` (or `y: number, x: number` for `atan2`)
- **Return Type**: `number`
- **Return Value**: Angle in degrees.
- **Example**: `local deg = atan2(1.0, 1.0)` -- returns 45.0

### `sha256PassHash`
- **Description**: Computes a SHA-256 cryptographic hash of a password concatenated with a salt string.
- **Parameters**: `password: string`, `salt: string`
- **Return Type**: `string`
- **Return Value**: 64-character lowercase hexadecimal hash.
- **Example**: `local hash = sha256PassHash("secret123", "random_salt")`

### `getWeaponName`
- **Description**: Retrieves the weapon name string for a given weapon ID (0 - 46).
- **Parameters**: `weaponId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: Weapon name (e.g. `"Desert Eagle"`), or `nil`.
- **Example**: `local name = getWeaponName(24)`

### `findWeaponId`
- **Description**: Searches for a weapon ID by partial or full name match.
- **Parameters**: `name: string`
- **Return Type**: `integer`
- **Return Value**: Weapon ID, or `0` if not found.
- **Example**: `local id = findWeaponId("m4")`

### `getVehicleName`
- **Description**: Retrieves the vehicle name string for a vehicle model ID (400 - 611).
- **Parameters**: `modelId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: Vehicle name string (e.g. `"Infernus"`), or `nil`.
- **Example**: `local vehName = getVehicleName(411)`

### `findVehicleModel`
- **Description**: Searches for a vehicle model ID by partial or full name match.
- **Parameters**: `name: string`
- **Return Type**: `integer`
- **Return Value**: Vehicle model ID (400 - 611), or `0` if not found.
- **Example**: `local model = findVehicleModel("infernus")`
