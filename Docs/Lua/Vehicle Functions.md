# Vehicle Functions

---

## Creation & Lifecycle

### `createVehicle`
- **Description**: Spawns a new dynamic vehicle at world coordinates.
- **Parameters**:
  | Parameter | Type | Description |
  |---|---|---|
  | modelId | integer | Vehicle model ID (400 - 611). |
  | x | number | World X coordinate. |
  | y | number | World Y coordinate. |
  | z | number | World Z coordinate. |
  | rotation | number | Z-facing angle (0.0 - 360.0). |
  | color1 | integer | Primary color index (`-1` for random). |
  | color2 | integer | Secondary color index (`-1` for random). |
  | respawnDelay | integer | Delay in seconds before vehicle respawns if unoccupied. |
  | addSiren | boolean | Whether to enable siren functionality. |
- **Return Type**: `integer`
- **Return Value**: Newly created vehicle ID, or `INVALID_VEHICLE_ID` (`65535`) on failure.
- **Example**: `local veh = createVehicle(411, 1500.0, -1600.0, 13.5, 90.0, 1, 1, 60, false)`

### `addStaticVehicle`
- **Description**: Adds a static vehicle that respawns automatically after 120 seconds.
- **Parameters**: `modelId: integer`, `x: number`, `y: number`, `z: number`, `rotation: number`, `color1: integer`, `color2: integer`
- **Return Type**: `integer`
- **Return Value**: Vehicle ID, or `INVALID_VEHICLE_ID`.
- **Example**: `local veh = addStaticVehicle(522, 1500.0, -1600.0, 13.5, 0.0, 3, 3)`

### `addStaticVehicleEx`
- **Description**: Adds a static vehicle with custom respawn delay and siren toggle.
- **Parameters**: `modelId: integer`, `x: number`, `y: number`, `z: number`, `rotation: number`, `color1: integer`, `color2: integer`, `respawnDelay: integer`, `addSiren: boolean`
- **Return Type**: `integer`
- **Return Value**: Vehicle ID, or `INVALID_VEHICLE_ID`.
- **Example**: `local veh = addStaticVehicleEx(416, 1500.0, -1600.0, 13.5, 0.0, 1, 3, 30, true)`

### `destroyVehicle`
- **Description**: Destroys an existing vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `destroyVehicle(veh)`

### `isValidVehicle`
- **Description**: Checks whether a vehicle ID is valid and active.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if valid, otherwise `false`.
- **Example**: `if isValidVehicle(veh) then ... end`

### `setVehicleToRespawn`
- **Description**: Forces a vehicle to respawn at its designated spawn point.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleToRespawn(veh)`

---

## Position, Velocity & Orientation

### `getVehiclePosition` / `getVehiclePos`
- **Description**: Retrieves the world coordinates of a vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `number, number, number (or nil)`
- **Return Value**: Three numbers (`x, y, z`), or `nil` on failure.
- **Example**: `local x, y, z = getVehiclePosition(veh)`

### `setVehiclePosition` / `setVehiclePos`
- **Description**: Sets the world position of a vehicle.
- **Parameters**: `vehicleId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehiclePosition(veh, 1500.0, -1600.0, 14.0)`

### `getVehicleZAngle`
- **Description**: Retrieves the facing angle (rotation in degrees) of a vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `number (or nil)`
- **Return Value**: Angle in degrees (0.0 - 360.0), or `nil`.
- **Example**: `local angle = getVehicleZAngle(veh)`

### `setVehicleZAngle`
- **Description**: Sets the facing angle of a vehicle.
- **Parameters**: `vehicleId: integer`, `angle: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleZAngle(veh, 180.0)`

### `getVehicleVelocity`
- **Description**: Retrieves the linear velocity vector of a vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `number, number, number (or nil)`
- **Return Value**: Velocity vector components (`vx, vy, vz`).
- **Example**: `local vx, vy, vz = getVehicleVelocity(veh)`

### `setVehicleVelocity`
- **Description**: Sets the velocity vector of a vehicle.
- **Parameters**: `vehicleId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleVelocity(veh, 0.0, 0.5, 0.0)`

### `setVehicleAngularVelocity`
- **Description**: Sets angular velocity of a vehicle.
- **Parameters**: `vehicleId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleAngularVelocity(veh, 0.0, 0.0, 0.2)`

### `getVehicleRotationQuat`
- **Description**: Retrieves the full 3D rotation of a vehicle as a quaternion.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `number, number, number, number (or nil)`
- **Return Value**: Four numbers (`w, x, y, z`), or `nil`.
- **Example**: `local w, x, y, z = getVehicleRotationQuat(veh)`

### `getVehicleDistanceFromPoint`
- **Description**: Calculates 3D distance between a vehicle and a world point.
- **Parameters**: `vehicleId: integer`, `x: number`, `y: number`, `z: number`
- **Return Type**: `number`
- **Return Value**: Distance in game units.
- **Example**: `local dist = getVehicleDistanceFromPoint(veh, 0.0, 0.0, 0.0)`

---

## Health, Damage & State

### `getVehicleHealth`
- **Description**: Retrieves the current health of a vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `number (or nil)`
- **Return Value**: Health value (typically 0.0 - 1000.0), or `nil`.
- **Example**: `local hp = getVehicleHealth(veh)`

### `setVehicleHealth`
- **Description**: Sets the health of a vehicle.
- **Parameters**: `vehicleId: integer`, `health: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleHealth(veh, 1000.0)`

### `repairVehicle`
- **Description**: Instantly repairs all visual damage and restores vehicle health to 1000.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `repairVehicle(veh)`

### `explodeVehicle`
- **Description**: Causes a vehicle to violently explode immediately.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `explodeVehicle(veh)`

### `getVehicleDamageStatus`
- **Description**: Retrieves bitmask damage states for vehicle parts.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `integer, integer, integer, integer (or nil)`
- **Return Value**: Four integers (`panels, doors, lights, tires`), or `nil`.
- **Example**: `local panels, doors, lights, tires = getVehicleDamageStatus(veh)`

### `updateVehicleDamageStatus`
- **Description**: Sets damage status bitmasks for vehicle components.
- **Parameters**: `vehicleId: integer`, `panels: integer`, `doors: integer`, `lights: integer`, `tires: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `updateVehicleDamageStatus(veh, panels, doors, lights, tires)`

---

## Appearance & Components

### `getVehicleModel`
- **Description**: Retrieves the GTA vehicle model ID (400 - 611).
- **Parameters**: `vehicleId: integer`
- **Return Type**: `integer`
- **Return Value**: Model ID integer.
- **Example**: `local model = getVehicleModel(veh)`

### `changeVehicleColor`
- **Description**: Sets the primary and secondary colors of a vehicle.
- **Parameters**: `vehicleId: integer`, `color1: integer`, `color2: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `changeVehicleColor(veh, 3, 3)`

### `getVehicleColor`
- **Description**: Retrieves the color indices of a vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `integer, integer (or nil)`
- **Return Value**: Two integers (`color1, color2`), or `nil`.
- **Example**: `local col1, col2 = getVehicleColor(veh)`

### `changeVehiclePaintjob`
- **Description**: Applies a paintjob texture to a vehicle.
- **Parameters**: `vehicleId: integer`, `paintjob: integer` (0 - 2, or 3 for none)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `changeVehiclePaintjob(veh, 1)`

### `getVehiclePaintjob`
- **Description**: Retrieves the currently applied paintjob index.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `integer`
- **Return Value**: Paintjob index, or `-1`.
- **Example**: `local pj = getVehiclePaintjob(veh)`

### `setVehicleNumberPlate`
- **Description**: Sets the custom text displayed on a vehicle's license plate.
- **Parameters**: `vehicleId: integer`, `plate: string` (up to 8 characters)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleNumberPlate(veh, "LEGACY")`

### `getVehicleNumberPlate`
- **Description**: Retrieves the text on a vehicle's license plate.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `string (or nil)`
- **Return Value**: Plate string, or `nil`.
- **Example**: `local plate = getVehicleNumberPlate(veh)`

### `addVehicleComponent`
- **Description**: Adds a tuning component (spoiler, wheels, nitro, etc.) to a vehicle.
- **Parameters**: `vehicleId: integer`, `componentId: integer` (1000 - 1193)
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `addVehicleComponent(veh, 1010)` -- 10x Nitro

### `removeVehicleComponent`
- **Description**: Removes a tuning component from a vehicle.
- **Parameters**: `vehicleId: integer`, `componentId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `removeVehicleComponent(veh, 1010)`

### `getVehicleComponentInSlot`
- **Description**: Retrieves the installed component ID in a specific vehicle modification slot (0 - 16).
- **Parameters**: `vehicleId: integer`, `slot: integer`
- **Return Type**: `integer`
- **Return Value**: Installed component ID, or `0` if empty.
- **Example**: `local comp = getVehicleComponentInSlot(veh, 8)` -- Nitro slot

### `getVehicleComponentType`
- **Description**: Determines the slot type index for a component ID.
- **Parameters**: `componentId: integer`
- **Return Type**: `integer`
- **Return Value**: Slot type index (0 - 16), or `-1` if invalid.
- **Example**: `local slot = getVehicleComponentType(1010)`

---

## Trailers & Doors

### `attachTrailerToVehicle`
- **Description**: Attaches a trailer vehicle behind a tractor/cab vehicle.
- **Parameters**: `trailerId: integer`, `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `attachTrailerToVehicle(trailer, truck)`

### `detachTrailerFromVehicle`
- **Description**: Detaches the connected trailer from a vehicle.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `detachTrailerFromVehicle(truck)`

### `isTrailerAttachedToVehicle`
- **Description**: Checks whether a vehicle currently has a trailer attached.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if attached, otherwise `false`.
- **Example**: `if isTrailerAttachedToVehicle(truck) then ... end`

### `getVehicleTrailer`
- **Description**: Retrieves the vehicle ID of the attached trailer.
- **Parameters**: `vehicleId: integer`
- **Return Type**: `integer`
- **Return Value**: Trailer vehicle ID, or `INVALID_VEHICLE_ID` (`65535`).
- **Example**: `local trailer = getVehicleTrailer(truck)`

### `setVehicleDoorState`
- **Description**: Controls open/closed state of individual vehicle doors.
- **Parameters**: `vehicleId: integer`, `doorId: integer` (1=Driver, 2=Passenger, 3=BackLeft, 4=BackRight), `state: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleDoorState(veh, 1, true)` -- Open driver door

### `setVehicleHoodState`
- **Description**: Controls open/closed state of the vehicle's bonnet/hood.
- **Parameters**: `vehicleId: integer`, `state: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleHoodState(veh, true)`

### `setVehicleTrunkState`
- **Description**: Controls open/closed state of the vehicle's boot/trunk.
- **Parameters**: `vehicleId: integer`, `state: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `setVehicleTrunkState(veh, true)`

---

## Features & Parameters

| Function | Parameters | Return Type | Description |
|---|---|---|---|
| `setVehicleEngineState` | `vehicleId: integer, engineState: boolean` | `boolean` | Toggles the engine on/off. |
| `setVehicleLightState` | `vehicleId: integer, lightState: boolean` | `boolean` | Toggles the vehicle lights. |
| `toggleTaxiLight` | `vehicleId: integer, toggle: boolean` | `boolean` | Toggles the taxi roof light. |
| `setVehicleParamsCarWindows` | `vehicleId: integer, driver: integer, passenger: integer, backLeft: integer, backRight: integer` | `boolean` | Sets window open (`1`) / closed (`0`) state. |
| `getVehicleParamsCarWindows` | `vehicleId: integer` | `integer, integer, integer, integer (or nil)` | Retrieves window states. |
| `setVehicleParamsCarDoors` | `vehicleId: integer, driver: integer, passenger: integer, backLeft: integer, backRight: integer` | `boolean` | Sets door open (`1`) / closed (`0`) state. |
| `getVehicleParamsCarDoors` | `vehicleId: integer` | `integer, integer, integer, integer (or nil)` | Retrieves door states. |
| `manualVehicleEngineAndLights` | None | `boolean` | Enables manual server-controlled engine and light switching. |
| `linkVehicleToInterior` | `vehicleId: integer, interior: integer` | `boolean` | Links vehicle to an interior ID. |
| `getVehicleInterior` | `vehicleId: integer` | `integer` | Retrieves vehicle interior ID. |
| `setVehicleVirtualWorld` | `vehicleId: integer, world: integer` | `boolean` | Sets vehicle virtual world. |
| `getVehicleVirtualWorld` | `vehicleId: integer` | `integer` | Retrieves vehicle virtual world. |
| `getVehiclePoolSize` | None | `integer` | Retrieves highest active vehicle ID. |
