# Player Functions

---

## Connection & Information

### `isPlayerConnected`
- **Description**: Checks whether a player is connected to the server.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if connected, `false` otherwise.
- **Example**: `if isPlayerConnected(playerid) then ... end`

### `getPlayerName`
- **Description**: Retrieves a player's nickname.
- **Parameters**: `playerId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: Nickname string on success, or `nil` if player is not connected.
- **Example**: `local name = getPlayerName(playerid)`

### `setPlayerName`
- **Description**: Changes a player's nickname.
- **Parameters**: `playerId: integer`, `name: string`
- **Return Type**: `integer`
- **Return Value**: `1` on success, `0` if name is in use, `-1` on validation/character error.
- **Example**: `local result = setPlayerName(playerid, "NewName")`

### `getPlayerIp`
- **Description**: Retrieves a player's IP address.
- **Parameters**: `playerId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: IP address string (e.g. `"127.0.0.1"`), or `nil` if disconnected.
- **Example**: `local ip = getPlayerIp(playerid)`

### `getPlayerPing`
- **Description**: Retrieves a player's current network latency/ping.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Ping in milliseconds, or `0` if disconnected.
- **Example**: `local ping = getPlayerPing(playerid)`

### `getPlayerVersion`
- **Description**: Retrieves the client version string reported by the player.
- **Parameters**: `playerId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: Client version string (e.g. `"0.3.7"`), or `nil`.
- **Example**: `local ver = getPlayerVersion(playerid)`

### `gpci`
- **Description**: Retrieves the client hardware serial hash (GPCI) of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: Serial hash string, or `nil` if unavailable.
- **Example**: `local serial = gpci(playerid)`

### `getPlayerCount`
- **Description**: Retrieves the total number of connected players.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Connected player count.
- **Example**: `local online = getPlayerCount()`

### `getPlayerPoolSize`
- **Description**: Retrieves the highest active player slot ID.
- **Parameters**: None
- **Return Type**: `integer`
- **Return Value**: Highest player ID on server.
- **Example**: `local maxId = getPlayerPoolSize()`

### `getPlayerIdFromName`
- **Description**: Finds a player ID by matching part or all of their nickname (case-insensitive).
- **Parameters**: `name: string`
- **Return Type**: `integer`
- **Return Value**: Player ID if found, or `-1` if not found.
- **Example**: `local targetId = getPlayerIdFromName("Carl")`

---

## Position, Velocity & Movement

### `getPlayerPosition` / `getPlayerPos`
- **Description**: Retrieves the world position coordinates of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `number, number, number (or nil)`
- **Return Value**: Three numbers (`x, y, z`), or `nil` if disconnected.
- **Example**: `local x, y, z = getPlayerPosition(playerid)`

### `setPlayerPosition` / `setPlayerPos`
- **Description**: Sets the world position coordinates of a player.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerPosition(playerid, 1500.0, -1600.0, 13.5)`

### `setPlayerPosFindZ`
- **Description**: Sets the position coordinates of a player and automatically adjusts Z coordinate to ground level.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerPosFindZ(playerid, 1500.0, -1600.0, 13.5)`

### `getPlayerVelocity`
- **Description**: Retrieves the velocity / move vector of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `number, number, number (or nil)`
- **Return Value**: Velocity vector components (`vx, vy, vz`).
- **Example**: `local vx, vy, vz = getPlayerVelocity(playerid)`

### `setPlayerVelocity`
- **Description**: Sets the velocity vector of a player.
- **Parameters**: `playerId: integer`, `vx: number`, `vy: number`, `vz: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerVelocity(playerid, 0.0, 0.0, 0.5)` -- Jump boost

### `getPlayerFacingAngle`
- **Description**: Retrieves the facing angle (rotation in degrees) of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `number (or nil)`
- **Return Value**: Angle in degrees (0.0 - 360.0), or `nil`.
- **Example**: `local angle = getPlayerFacingAngle(playerid)`

### `setPlayerFacingAngle`
- **Description**: Sets the facing angle of a player.
- **Parameters**: `playerId: integer`, `angle: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerFacingAngle(playerid, 180.0)`

### `isPlayerInRangeOfPoint`
- **Description**: Checks whether a player is within a spherical radius of a point.
- **Parameters**: `playerId: integer`, `range: number`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` if within range, otherwise `false`.
- **Example**: `if isPlayerInRangeOfPoint(playerid, 5.0, 1500.0, -1600.0, 13.5) then ... end`

### `getPlayerDistanceFromPoint`
- **Description**: Calculates the 3D distance between a player and a world point.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `number`
- **Return Value**: Distance in game units, or `0.0`.
- **Example**: `local dist = getPlayerDistanceFromPoint(playerid, 0.0, 0.0, 0.0)`

---

## Health, Armour & Stats

### `getPlayerHealth`
- **Description**: Retrieves a player's health.
- **Parameters**: `playerId: integer`
- **Return Type**: `number (or nil)`
- **Return Value**: Health value (`0.0` - `100.0`+), or `nil`.
- **Example**: `local hp = getPlayerHealth(playerid)`

### `setPlayerHealth`
- **Description**: Sets a player's health.
- **Parameters**: `playerId: integer`, `health: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerHealth(playerid, 100.0)`

### `setPlayerMaxHealth`
- **Description**: Sets maximum allowable health for a player.
- **Parameters**: `playerId: integer`, `maxHealth: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerMaxHealth(playerid, 150.0)`

### `getPlayerArmour` / `getPlayerArmor`
- **Description**: Retrieves a player's armour.
- **Parameters**: `playerId: integer`
- **Return Type**: `number (or nil)`
- **Return Value**: Armour value (`0.0` - `100.0`), or `nil`.
- **Example**: `local armour = getPlayerArmour(playerid)`

### `setPlayerArmour` / `setPlayerArmor`
- **Description**: Sets a player's armour.
- **Parameters**: `playerId: integer`, `armour: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerArmour(playerid, 100.0)`

### `getPlayerScore`
- **Description**: Retrieves a player's scoreboard score.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Score integer.
- **Example**: `local score = getPlayerScore(playerid)`

### `setPlayerScore`
- **Description**: Sets a player's score and synchronizes it to all clients.
- **Parameters**: `playerId: integer`, `score: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerScore(playerid, 10)`

### `getPlayerMoney`
- **Description**: Retrieves the player's money balance tracked by the server.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Amount of money.
- **Example**: `local cash = getPlayerMoney(playerid)`

### `setPlayerMoney`
- **Description**: Directly sets the server-side tracked money for a player.
- **Parameters**: `playerId: integer`, `money: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerMoney(playerid, 5000)`

### `givePlayerMoney`
- **Description**: Gives money to a player (updates client HUD and server balance).
- **Parameters**: `playerId: integer`, `money: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `givePlayerMoney(playerid, 500)`

### `resetPlayerMoney`
- **Description**: Resets a player's money to 0 on both client and server.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `resetPlayerMoney(playerid)`

---

## State, Skin & Spawning

### `getPlayerState`
- **Description**: Retrieves the player's current sync state (`PLAYER_STATE.*`).
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: State ID (`PLAYER_STATE.ONFOOT`, `DRIVER`, `PASSENGER`, `WASTED`, etc.).
- **Example**: `local state = getPlayerState(playerid)`

### `getPlayerSkin`
- **Description**: Retrieves the ped model skin ID of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Skin model ID, or `0`.
- **Example**: `local skin = getPlayerSkin(playerid)`

### `setPlayerSkin`
- **Description**: Sets the ped skin model of a player.
- **Parameters**: `playerId: integer`, `skin: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on invalid skin.
- **Example**: `setPlayerSkin(playerid, 294)`

### `getPlayerTeam`
- **Description**: Retrieves the team ID assigned to a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Team ID (`0` - `254`), or `NO_TEAM` (`255`).
- **Example**: `local team = getPlayerTeam(playerid)`

### `setPlayerTeam`
- **Description**: Assigns a player to a team.
- **Parameters**: `playerId: integer`, `team: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerTeam(playerid, 1)`

### `getPlayerColor`
- **Description**: Retrieves a player's radar and nametag color.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Hexadecimal color code.
- **Example**: `local color = getPlayerColor(playerid)`

### `setPlayerColor`
- **Description**: Sets a player's nametag and radar marker color.
- **Parameters**: `playerId: integer`, `color: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerColor(playerid, 0xFF0000FF)`

### `setSpawnInfo`
- **Description**: Configures spawn parameters (team, skin, position, rotation, weapons) for a player's next spawn.
- **Parameters**: `playerId: integer`, `team: integer`, `skin: integer`, `x: number`, `y: number`, `z: number`, `rotation: number`, `weapon1: integer`, `ammo1: integer`, `weapon2: integer`, `ammo2: integer`, `weapon3: integer`, `ammo3: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setSpawnInfo(playerid, 0, 294, 1500.0, -1600.0, 13.5, 0.0, 24, 100, 29, 200, 0, 0)`

### `spawnPlayer`
- **Description**: Forces a player to spawn immediately.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `spawnPlayer(playerid)`

### `forceClassSelection`
- **Description**: Forces a player to return to the class selection screen on their next spawn.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `forceClassSelection(playerid)`

---

## Weapons & Combat

### `getPlayerWeapon`
- **Description**: Retrieves the weapon ID currently held by a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Weapon ID (`WEAPON.*`), or `0`.
- **Example**: `local weapon = getPlayerWeapon(playerid)`

### `getPlayerAmmo`
- **Description**: Retrieves the remaining ammo of the currently equipped weapon.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Ammo count, or `0`.
- **Example**: `local ammo = getPlayerAmmo(playerid)`

### `getPlayerWeaponData`
- **Description**: Retrieves weapon ID and total ammo for a specific weapon slot (0 - 12).
- **Parameters**: `playerId: integer`, `slot: integer`
- **Return Type**: `integer, integer (or nil)`
- **Return Value**: Two numbers (`weaponId, ammo`), or `nil` on error.
- **Example**: `local weapon, ammo = getPlayerWeaponData(playerid, 2)`

### `givePlayerWeapon`
- **Description**: Gives a weapon with specified ammo to a player.
- **Parameters**: `playerId: integer`, `weaponId: integer`, `ammo: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `givePlayerWeapon(playerid, WEAPON.DEAGLE, 150)`

### `setPlayerAmmo`
- **Description**: Sets the ammo amount in a player's weapon slot.
- **Parameters**: `playerId: integer`, `weaponSlot: integer`, `ammo: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerAmmo(playerid, 2, 50)`

### `resetPlayerWeapons`
- **Description**: Removes all weapons and ammo from a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `resetPlayerWeapons(playerid)`

### `setPlayerArmedWeapon`
- **Description**: Changes the player's equipped/held weapon.
- **Parameters**: `playerId: integer`, `weaponId: integer`
- **Return Type**: `integer`
- **Return Value**: `1` on success, `-1` if player does not have the weapon, `-2` on failure.
- **Example**: `setPlayerArmedWeapon(playerid, WEAPON.M4)`

### `setPlayerSkillLevel`
- **Description**: Sets weapon skill proficiency level (0 - 999) for a weapon type.
- **Parameters**: `playerId: integer`, `skill: integer`, `level: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerSkillLevel(playerid, 0, 999)` -- Hitman level pistols

### `getPlayerFightingStyle`
- **Description**: Retrieves the fighting style ID of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Fighting style ID (`FIGHT_STYLE.*`).
- **Example**: `local style = getPlayerFightingStyle(playerid)`

### `setPlayerFightingStyle`
- **Description**: Sets the melee fighting style for a player.
- **Parameters**: `playerId: integer`, `style: integer`, `moves: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerFightingStyle(playerid, FIGHT_STYLE_BOXING, 6)`

### `getPlayerTargetPlayer`
- **Description**: Retrieves the player ID that a player is currently aiming at.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Target player ID, or `INVALID_PLAYER_ID` (`65535`).
- **Example**: `local target = getPlayerTargetPlayer(playerid)`

### `getPlayerTargetActor`
- **Description**: Retrieves the actor ID that a player is currently aiming at.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Target actor ID, or `INVALID_ACTOR_ID` (`65535`).
- **Example**: `local targetActor = getPlayerTargetActor(playerid)`

---

## Vehicles & Driving

### `isPlayerInAnyVehicle`
- **Description**: Checks whether a player is in any vehicle (as driver or passenger).
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if in a vehicle, otherwise `false`.
- **Example**: `if isPlayerInAnyVehicle(playerid) then ... end`

### `isPlayerInVehicle`
- **Description**: Checks whether a player is inside a specific vehicle.
- **Parameters**: `playerId: integer`, `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if in the specified vehicle, otherwise `false`.
- **Example**: `if isPlayerInVehicle(playerid, vehicleid) then ... end`

### `getPlayerVehicleId`
- **Description**: Retrieves the vehicle ID the player is currently inside.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Vehicle ID, or `0` if not in a vehicle.
- **Example**: `local veh = getPlayerVehicleId(playerid)`

### `getPlayerVehicleSeat`
- **Description**: Retrieves the seat index (`0` for driver, `1`+ for passengers) occupied by the player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Seat index, or `-1` if not in a vehicle.
- **Example**: `local seat = getPlayerVehicleSeat(playerid)`

### `putPlayerInVehicle`
- **Description**: Teleports/places a player into a vehicle seat.
- **Parameters**: `playerId: integer`, `vehicleId: integer`, `seatId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `putPlayerInVehicle(playerid, vehicleid, 0)` -- Put as driver

### `removePlayerFromVehicle`
- **Description**: Ejects a player from their current vehicle.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `removePlayerFromVehicle(playerid)`

### `getPlayerSurfingVehicleId`
- **Description**: Retrieves the vehicle ID that the player is currently surfing / standing on top of.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Vehicle ID, or `INVALID_VEHICLE_ID` (`65535`).
- **Example**: `local surfVeh = getPlayerSurfingVehicleId(playerid)`

### `disableRemoteVehicleCollisions`
- **Description**: Disables vehicle-on-vehicle physical collisions for a player's client.
- **Parameters**: `playerId: integer`, `disable: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `disableRemoteVehicleCollisions(playerid, true)`

---

## Camera, Audio & Environment

### `setPlayerCameraPos`
- **Description**: Sets the player's camera to a fixed world position.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`, `rx?: number`, `ry?: number`, `rz?: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerCameraPos(playerid, 1500.0, -1600.0, 50.0)`

### `setPlayerCameraLookAt`
- **Description**: Points the player's camera toward a specific world point.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`, `cut?: integer` (`1`=Move, `2`=Cut)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerCameraLookAt(playerid, 1500.0, -1600.0, 13.5, 2)`

### `setCameraBehindPlayer`
- **Description**: Restores the player's camera to standard 3rd person behind the player.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setCameraBehindPlayer(playerid)`

### `interpolateCameraPos`
- **Description**: Smoothly interpolates the camera position from one point to another over a duration.
- **Parameters**: `playerId: integer`, `fromX: number`, `fromY: number`, `fromZ: number`, `toX: number`, `toY: number`, `toZ: number`, `time: integer`, `cut: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `interpolateCameraPos(playerid, 1000.0, -1500.0, 50.0, 1050.0, -1500.0, 30.0, 5000, 1)`

### `interpolateCameraLookAt`
- **Description**: Smoothly interpolates camera look-at focus point over a duration.
- **Parameters**: `playerId: integer`, `fromX: number`, `fromY: number`, `fromZ: number`, `toX: number`, `toY: number`, `toZ: number`, `time: integer`, `cut: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `interpolateCameraLookAt(playerid, 1500.0, -1600.0, 15.0, 1520.0, -1600.0, 15.0, 5000, 1)`

### `playAudioStreamForPlayer`
- **Description**: Plays an internet audio stream (URL) for a player (optionally with 3D positional audio).
- **Parameters**: `playerId: integer`, `url: string`, `posX: number`, `posY: number`, `posZ: number`, `distance: number`, `usePos: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `playAudioStreamForPlayer(playerid, "http://example.com/radio.mp3", 0.0, 0.0, 0.0, 0.0, false)`

### `stopAudioStreamForPlayer`
- **Description**: Stops any playing audio stream for a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `stopAudioStreamForPlayer(playerid)`

### `playerPlaySound`
- **Description**: Plays a GTA sound effect ID for a player at specified coordinates.
- **Parameters**: `playerId: integer`, `soundId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `playerPlaySound(playerid, 1056, 0.0, 0.0, 0.0)`

### `setPlayerWeather`
- **Description**: Sets the individual weather ID for a player.
- **Parameters**: `playerId: integer`, `weatherId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerWeather(playerid, 10)`

### `setPlayerTime`
- **Description**: Sets the individual clock hour and minute for a player.
- **Parameters**: `playerId: integer`, `hour: integer`, `minute: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerTime(playerid, 12, 0)`

### `togglePlayerClock`
- **Description**: Toggles whether the in-game clock HUD element is shown.
- **Parameters**: `playerId: integer`, `toggle: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `togglePlayerClock(playerid, true)`

### `setPlayerInterior`
- **Description**: Sets the interior world ID of a player.
- **Parameters**: `playerId: integer`, `interior: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerInterior(playerid, 1)`

### `getPlayerInterior`
- **Description**: Retrieves the current interior ID of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Interior ID (`0` for outside world).
- **Example**: `local interior = getPlayerInterior(playerid)`

### `setPlayerVirtualWorld`
- **Description**: Sets the virtual world instance ID of a player.
- **Parameters**: `playerId: integer`, `world: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerVirtualWorld(playerid, 1)`

### `getPlayerVirtualWorld`
- **Description**: Retrieves the virtual world ID of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Virtual world ID.
- **Example**: `local vw = getPlayerVirtualWorld(playerid)`

---

## Checkpoints & Map Icons

### `setPlayerCheckpoint`
- **Description**: Creates a red ground checkpoint cylinder for a player.
- **Parameters**: `playerId: integer`, `x: number`, `y: number`, `z: number`, `size: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerCheckpoint(playerid, 1500.0, -1600.0, 13.5, 3.0)`

### `disablePlayerCheckpoint`
- **Description**: Removes the active checkpoint for a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `disablePlayerCheckpoint(playerid)`

### `isPlayerInCheckpoint`
- **Description**: Checks whether a player is currently inside their active checkpoint.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if inside, `false` otherwise.
- **Example**: `if isPlayerInCheckpoint(playerid) then ... end`

### `setPlayerRaceCheckpoint`
- **Description**: Creates a race checkpoint (with direction arrow pointing to next checkpoint) for a player.
- **Parameters**: `playerId: integer`, `type: integer`, `x: number`, `y: number`, `z: number`, `nextX: number`, `nextY: number`, `nextZ: number`, `size: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerRaceCheckpoint(playerid, 0, 1500.0, -1600.0, 13.5, 1550.0, -1600.0, 13.5, 5.0)`

### `disablePlayerRaceCheckpoint`
- **Description**: Removes the active race checkpoint for a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `disablePlayerRaceCheckpoint(playerid)`

### `isPlayerInRaceCheckpoint`
- **Description**: Checks whether a player is currently inside their race checkpoint.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if inside, `false` otherwise.
- **Example**: `if isPlayerInRaceCheckpoint(playerid) then ... end`

### `setPlayerMapIcon`
- **Description**: Creates a radar/map icon on a player's minimap.
- **Parameters**: `playerId: integer`, `iconId: integer` (0-99), `x: number`, `y: number`, `z: number`, `markerType: integer`, `color: integer`, `style: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerMapIcon(playerid, 0, 1500.0, -1600.0, 13.5, 55, 0, 0)`

### `removePlayerMapIcon`
- **Description**: Removes a map icon by ID for a player.
- **Parameters**: `playerId: integer`, `iconId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `removePlayerMapIcon(playerid, 0)`

---

## Controls, Animations & Actions

### `togglePlayerControllable`
- **Description**: Freezes or unfreezes a player's controls and movement.
- **Parameters**: `playerId: integer`, `toggle: boolean` (`true`=unfreeze, `false`=freeze)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `togglePlayerControllable(playerid, false)` -- Freeze player

### `applyAnimation`
- **Description**: Plays an animation on a player and broadcasts to nearby clients.
- **Parameters**: `playerId: integer`, `animLib: string`, `animName: string`, `speed: number`, `loop: boolean`, `lockX: boolean`, `lockY: boolean`, `lockF: boolean`, `time: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `applyAnimation(playerid, "PED", "WALK_DRUNK", 4.1, true, true, true, false, 0)`

### `clearAnimations`
- **Description**: Clears any currently playing animation on a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `clearAnimations(playerid)`

### `setPlayerSpecialAction`
- **Description**: Sets a player's special action (`SPECIAL_ACTION.*`).
- **Parameters**: `playerId: integer`, `actionId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerSpecialAction(playerid, SPECIAL_ACTION.USEJETPACK)`

### `getPlayerSpecialAction`
- **Description**: Retrieves the current special action of a player.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Special action ID (`SPECIAL_ACTION.*`).
- **Example**: `local action = getPlayerSpecialAction(playerid)`

### `setPlayerDrunkLevel`
- **Description**: Sets the drunken camera shake level of a player (0 - 50000).
- **Parameters**: `playerId: integer`, `level: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerDrunkLevel(playerid, 3000)`

### `getPlayerDrunkLevel`
- **Description**: Retrieves a player's drunk level.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Drunk level integer.
- **Example**: `local drunk = getPlayerDrunkLevel(playerid)`

### `setPlayerWantedLevel`
- **Description**: Sets a player's police wanted level (0 - 6 stars).
- **Parameters**: `playerId: integer`, `level: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setPlayerWantedLevel(playerid, 3)`

### `getPlayerWantedLevel`
- **Description**: Retrieves a player's wanted level.
- **Parameters**: `playerId: integer`
- **Return Type**: `integer`
- **Return Value**: Wanted stars (0 - 6).
- **Example**: `local stars = getPlayerWantedLevel(playerid)`

---

## Spectating

### `togglePlayerSpectating`
- **Description**: Enables or disables spectator mode for a player.
- **Parameters**: `playerId: integer`, `toggle: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `togglePlayerSpectating(playerid, true)`

### `playerSpectatePlayer`
- **Description**: Makes a spectating player spectate another player.
- **Parameters**: `playerId: integer`, `targetPlayerId: integer`, `mode: integer` (`SPECTATE_MODE_*`)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `playerSpectatePlayer(playerid, targetid, SPECTATE_MODE_NORMAL)`

### `playerSpectateVehicle`
- **Description**: Makes a spectating player spectate a vehicle.
- **Parameters**: `playerId: integer`, `vehicleId: integer`, `mode: integer` (`SPECTATE_MODE_*`)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `playerSpectateVehicle(playerid, vehicleid, SPECTATE_MODE_NORMAL)`

---

## Player Variables (PVars)

| Function | Parameters | Return Type | Description |
|---|---|---|---|
| `setPVarInt` | `playerId: integer, name: string, value: integer` | `boolean` | Sets an integer PVar. |
| `setPVarString` | `playerId: integer, name: string, value: string` | `boolean` | Sets a string PVar. |
| `setPVarFloat` | `playerId: integer, name: string, value: number` | `boolean` | Sets a float PVar. |
| `getPVarInt` | `playerId: integer, name: string` | `integer` | Retrieves an integer PVar (default `0`). |
| `getPVarString` | `playerId: integer, name: string` | `string (or nil)` | Retrieves a string PVar. |
| `getPVarFloat` | `playerId: integer, name: string` | `number` | Retrieves a float PVar (default `0.0`). |
| `deletePVar` | `playerId: integer, name: string` | `boolean` | Deletes a PVar. |
| `getPVarType` | `playerId: integer, name: string` | `integer` | Returns `PLAYER_VARTYPE_*`. |
| `getPVarNameAtIndex` | `playerId: integer, index: integer` | `string (or nil)` | Retrieves PVar name at index. |
| `getPVarsUpperIndex` | `playerId: integer` | `integer` | Retrieves highest PVar slot index. |
