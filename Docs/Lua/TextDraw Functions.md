# TextDraw Functions

---

## Global TextDraws

### `textDrawCreate`
- **Description**: Creates a global 2D on-screen text draw.
- **Parameters**:
  | Parameter | Type | Description |
  |---|---|---|
  | x | number | Screen X position coordinate (0.0 - 640.0). |
  | y | number | Screen Y position coordinate (0.0 - 480.0). |
  | text | string | Text content to display. |
- **Return Type**: `integer`
- **Return Value**: Newly created text draw ID, or `INVALID_TEXT_DRAW` (`65535`) on failure.
- **Example**: `local td = textDrawCreate(320.0, 240.0, "Welcome!")`

### `textDrawDestroy`
- **Description**: Destroys an existing global text draw.
- **Parameters**: `id: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if destroyed, `false` on failure.
- **Example**: `textDrawDestroy(td)`

### `isValidTextDraw`
- **Description**: Checks whether a global text draw ID is valid.
- **Parameters**: `id: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` if valid, `false` otherwise.
- **Example**: `if isValidTextDraw(td) then ... end`

### `textDrawLetterSize`
- **Description**: Sets the width and height scaling of text characters.
- **Parameters**: `id: integer`, `x: number`, `y: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawLetterSize(td, 0.5, 2.0)`

### `textDrawTextSize`
- **Description**: Sets the bounding box width and height for text alignment, wrapping, or box backgrounds.
- **Parameters**: `id: integer`, `x: number`, `y: number`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawTextSize(td, 200.0, 50.0)`

### `textDrawAlignment`
- **Description**: Sets the text alignment (`1`=Left, `2`=Center, `3`=Right).
- **Parameters**: `id: integer`, `alignment: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawAlignment(td, 2)`

### `textDrawColor`
- **Description**: Sets the text color.
- **Parameters**: `id: integer`, `color: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawColor(td, 0xFFFFFFFF)`

### `textDrawUseBox`
- **Description**: Toggles whether a background box is rendered behind the text draw.
- **Parameters**: `id: integer`, `use: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawUseBox(td, true)`

### `textDrawBoxColor`
- **Description**: Sets the background box color.
- **Parameters**: `id: integer`, `color: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawBoxColor(td, 0x00000088)`

### `textDrawSetShadow`
- **Description**: Sets shadow offset size in pixels.
- **Parameters**: `id: integer`, `size: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawSetShadow(td, 2)`

### `textDrawSetOutline`
- **Description**: Sets outline thickness in pixels.
- **Parameters**: `id: integer`, `size: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawSetOutline(td, 1)`

### `textDrawBackgroundColor`
- **Description**: Sets the color of the outline or shadow.
- **Parameters**: `id: integer`, `color: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawBackgroundColor(td, 0x000000FF)`

### `textDrawFont`
- **Description**: Sets the font style (0 - 3).
- **Parameters**: `id: integer`, `font: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawFont(td, 1)`

### `textDrawSetProportional`
- **Description**: Toggles proportional font spacing.
- **Parameters**: `id: integer`, `set: boolean`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawSetProportional(td, true)`

### `textDrawSetString`
- **Description**: Updates the text string of a global text draw for all players currently viewing it.
- **Parameters**: `id: integer`, `text: string`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawSetString(td, "New Score: 100")`

### `textDrawShowForPlayer`
- **Description**: Displays a global text draw to a specific player.
- **Parameters**: `playerId: integer`, `id: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawShowForPlayer(playerid, td)`

### `textDrawHideForPlayer`
- **Description**: Hides a global text draw from a player.
- **Parameters**: `playerId: integer`, `id: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawHideForPlayer(playerid, td)`

### `textDrawShowForAll`
- **Description**: Displays a global text draw to all connected players.
- **Parameters**: `id: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawShowForAll(td)`

### `textDrawHideForAll`
- **Description**: Hides a global text draw from all players.
- **Parameters**: `id: integer`
- **Return Type**: `boolean`
- **Return Value**: `true` on success, `false` on failure.
- **Example**: `textDrawHideForAll(td)`

---

## Per-Player TextDraws

| Function | Parameters | Return Type | Description |
|---|---|---|---|
| `createPlayerTextDraw` | `playerId: integer, x: number, y: number, text: string` | `integer` | Creates a text draw unique to a player. Returns ID or `-1`. |
| `playerTextDrawDestroy` | `playerId: integer, id: integer` | `boolean` | Destroys a per-player text draw. |
| `playerTextDrawShow` | `playerId: integer, id: integer` | `boolean` | Shows the text draw to its owner player. |
| `playerTextDrawHide` | `playerId: integer, id: integer` | `boolean` | Hides the text draw from its owner player. |
| `playerTextDrawSetString` | `playerId: integer, id: integer, text: string` | `boolean` | Updates text content. |
| `playerTextDrawLetterSize` | `playerId: integer, id: integer, x: number, y: number` | `boolean` | Sets font character dimensions. |
| `playerTextDrawTextSize` | `playerId: integer, id: integer, x: number, y: number` | `boolean` | Sets box / alignment area dimensions. |
| `playerTextDrawAlignment` | `playerId: integer, id: integer, alignment: integer` | `boolean` | Sets alignment (`1`=Left, `2`=Center, `3`=Right). |
| `playerTextDrawColor` | `playerId: integer, id: integer, color: integer` | `boolean` | Sets text color. |
| `playerTextDrawBoxColor` | `playerId: integer, id: integer, color: integer` | `boolean` | Sets background box color. |
| `playerTextDrawBackgroundColor` | `playerId: integer, id: integer, color: integer` | `boolean` | Sets shadow/outline color. |
| `playerTextDrawUseBox` | `playerId: integer, id: integer, use: boolean` | `boolean` | Enables/disables box background. |
| `playerTextDrawSetShadow` | `playerId: integer, id: integer, size: integer` | `boolean` | Sets shadow size. |
| `playerTextDrawSetOutline` | `playerId: integer, id: integer, size: integer` | `boolean` | Sets outline size. |
| `playerTextDrawFont` | `playerId: integer, id: integer, font: integer` | `boolean` | Sets font style (`0` - `3`). |
| `playerTextDrawSetProportional` | `playerId: integer, id: integer, set: boolean` | `boolean` | Toggles proportional spacing. |
