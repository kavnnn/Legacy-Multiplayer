# Constants

---

## Limits and Pool Maxima

| Constant Name | Description |
|---|---|
| `MAX_PLAYERS` | Maximum supported player slots. |
| `MAX_VEHICLES` | Maximum supported vehicle instances. |
| `MAX_OBJECTS` | Maximum supported world objects. |
| `MAX_PICKUPS` | Maximum supported world pickups. |
| `MAX_ACTORS` | Maximum supported static actors. |
| `MAX_GANG_ZONES` | Maximum supported gang zones. |
| `MAX_TEXT_DRAWS` | Maximum supported global text draws. |
| `MAX_PLAYER_TEXT_DRAWS` | Maximum supported per-player text draws. |
| `MAX_MENUS` | Maximum supported server menus. |
| `MAX_PLAYER_NAME` | Maximum character length for a player name. |
| `MAX_3DTEXT_GLOBAL` | Maximum supported global 3D text labels. |
| `MAX_3DTEXT_PLAYER` | Maximum supported per-player 3D text labels. |

---

## Sentinel & Invalid IDs

| Constant Name | Value | Description |
|---|---|---|
| `INVALID_PLAYER_ID` | `65535` | Sentinel value indicating an invalid player ID. |
| `INVALID_VEHICLE_ID` | `65535` | Sentinel value indicating an invalid vehicle ID. |
| `INVALID_OBJECT_ID` | `65535` | Sentinel value indicating an invalid object ID. |
| `INVALID_ACTOR_ID` | `65535` | Sentinel value indicating an invalid actor ID. |
| `INVALID_GANG_ZONE` | `-1` | Sentinel value indicating an invalid gang zone ID. |
| `INVALID_TEXT_DRAW` | `65535` | Sentinel value indicating an invalid text draw ID. |
| `INVALID_MENU` | `255` | Sentinel value indicating an invalid menu ID. |
| `INVALID_3DTEXT_ID` | `65535` | Sentinel value indicating an invalid 3D text label ID. |
| `NO_TEAM` | `255` | Sentinel value indicating no team assigned. |

---

## Disconnect Reasons

| Constant Name | Value | Description |
|---|---|---|
| `DISCONNECT_REASON_LOST_CONNECTION` | `0` | Player timed out or lost network connection. |
| `DISCONNECT_REASON_DISCONNECTED` | `1` | Player cleanly quit or left the game. |
| `DISCONNECT_REASON_KICKED` | `2` | Player was kicked or banned by server. |

---

## `PLAYER_STATE` Table

Accessed via `PLAYER_STATE.<KEY>`:

| Key | Description |
|---|---|
| `NONE` | Player state is undefined / inactive. |
| `ONFOOT` | Player is on foot. |
| `DRIVER` | Player is driving a vehicle. |
| `PASSENGER` | Player is a passenger in a vehicle. |
| `EXIT_VEHICLE` | Player is exiting a vehicle. |
| `ENTER_VEHICLE_DRIVER` | Player is entering a vehicle as the driver. |
| `ENTER_VEHICLE_PASSENGER` | Player is entering a vehicle as a passenger. |
| `WASTED` | Player is dead / wasted. |
| `SPAWNED` | Player has spawned. |
| `SPECTATING` | Player is in spectator mode. |

---

## `SPECIAL_ACTION` Table

Accessed via `SPECIAL_ACTION.<KEY>`:

| Key | Description |
|---|---|
| `NONE` | No special action. |
| `DUCK` | Ducking / crouching. |
| `USEJETPACK` | Wearing and flying with a jetpack. |
| `ENTER_VEHICLE` | Entering a vehicle. |
| `EXIT_VEHICLE` | Exiting a vehicle. |
| `DANCE1` | Dance style 1. |
| `DANCE2` | Dance style 2. |
| `DANCE3` | Dance style 3. |
| `DANCE4` | Dance style 4. |
| `HANDSUP` | Hands raised up. |
| `USECELLPHONE` | Holding cellphone to ear. |
| `SITTING` | Sitting posture. |
| `STOPUSECELLPHONE` | Stop holding cellphone. |
| `DRINK_BEER` | Drinking beer bottle. |
| `SMOKE_CIGGY` | Smoking cigarette. |
| `DRINK_WINE` | Drinking wine bottle. |
| `DRINK_SPRUNK` | Drinking sprunk can. |
| `URINATE` | Urinating animation action. |

---

## `WEAPON` Table

Accessed via `WEAPON.<KEY>`:

| Key | Description |
|---|---|
| `FIST` | Unarmed fists. |
| `BRASSKNUCKLE` | Brass knuckles. |
| `GOLFCLUB` | Golf club. |
| `NITESTICK` | Nightstick. |
| `KNIFE` | Knife. |
| `BAT` | Baseball bat. |
| `SHOVEL` | Shovel. |
| `POOLSTICK` | Pool cue stick. |
| `KATANA` | Katana sword. |
| `CHAINSAW` | Chainsaw. |
| `DILDO`, `DILDO2` | Dildo melee weapons. |
| `VIBRATOR`, `VIBRATOR2` | Vibrator melee weapons. |
| `FLOWER` | Bouquet of flowers. |
| `CANE` | Walking cane. |
| `GRENADE` | Hand grenade. |
| `TEARGAS` | Tear gas grenade. |
| `MOLTOV` | Molotov cocktail. |
| `COLT45` | 9mm pistol (Colt .45). |
| `SILENCED` | Silenced 9mm pistol. |
| `DEAGLE` | Desert Eagle (.50). |
| `SHOTGUN` | Pump shotgun. |
| `SAWEDOFF` | Sawn-off shotgun. |
| `SHOTGSPA` | Combat shotgun (SPAS-12). |
| `UZI` | Micro Uzi. |
| `MP5` | MP5 submachine gun. |
| `AK47` | AK-47 assault rifle. |
| `M4` | M4 assault rifle. |
| `TEC9` | Tec-9. |
| `RIFLE` | Country hunting rifle. |
| `SNIPER` | Sniper rifle. |
| `ROCKETLAUNCHER` | RPG / Rocket launcher. |
| `HEATSEEKER` | Heat-seeking rocket launcher (Stinger). |
| `FLAMETHROWER` | Flamethrower. |
| `MINIGUN` | Vulcan Minigun. |
| `SATCHEL` | Remote satchel explosive charge. |
| `BOMB` | Detonator bomb. |
| `SPRAYCAN` | Spray paint can. |
| `FIREEXTINGUISHER` | Fire extinguisher. |
| `CAMERA` | Camera. |
| `NIGHTVISION` | Night vision goggles. |
| `INFRARED` | Thermal infrared goggles. |
| `PARACHUTE` | Parachute. |
| `VEHICLE` | Damage caused by vehicle impact. |
| `DROWN` | Death caused by drowning. |
| `COLLISION` | Death caused by collision/impact. |
| `CONNECT` | System connection event ID. |
| `DISCONNECT` | System disconnection event ID. |
| `SUICIDE` | Player death via suicide. |

---

## `KEYS` Table

Accessed via `KEYS.<KEY>` (bitmask values for `onPlayerKeyStateChange` / `getPlayerKeys`):

| Key | Bitmask Value | Description |
|---|---|---|
| `ACTION` | `1` | Action button (default: Tab). |
| `CROUCH` | `2` | Crouch key (default: C). |
| `FIRE` | `4` | Fire weapon key (default: Left Mouse Button). |
| `SPRINT` | `8` | Sprint key (default: Spacebar). |
| `SECONDARY_ATTACK` | `16` | Secondary attack / enter car (default: Enter / F). |
| `JUMP` | `32` | Jump key (default: Left Shift). |
| `LOOK_RIGHT` | `64` | Look right in vehicle (default: E). |
| `HANDBRAKE` | `128` | Handbrake in vehicle / aim weapon (default: Right Mouse Button / Space). |
| `LOOK_LEFT` | `256` | Look left in vehicle (default: Q). |
| `SUBMISSION` | `512` | Horn / submission key (default: Caps Lock / 2). |
| `WALK` | `1024` | Walk key (default: Left Alt). |
| `ANALOG_UP` | `2048` | Analog up key (default: Numpad 8). |
| `ANALOG_DOWN` | `4096` | Analog down key (default: Numpad 2). |
| `ANALOG_LEFT` | `8192` | Analog left key (default: Numpad 4). |
| `ANALOG_RIGHT` | `16384` | Analog right key (default: Numpad 6). |
| `YES` | `32768` | Yes response key (default: Y). |
| `NO` | `65536` | No response key (default: N). |
| `CTRL_BACK` | `131072` | Control back key (default: H). |
| `CTRL_FORWARD` | `262144` | Control forward key (default: G). |

---

## Spectate & Camera Constants

| Constant Name | Value | Description |
|---|---|---|
| `SPECTATE_MODE_NORMAL` | `1` | Standard spectate mode. |
| `SPECTATE_MODE_FIXED` | `2` | Fixed position spectate mode. |
| `SPECTATE_MODE_SIDE` | `3` | Side view spectate mode. |
| `SPECTATE_TYPE_NONE` | `0` | No spectator target. |
| `SPECTATE_TYPE_PLAYER` | `1` | Spectating a player. |
| `SPECTATE_TYPE_VEHICLE` | `2` | Spectating a vehicle. |
| `CAMERA_MOVE` | `1` | Smooth camera interpolation movement. |
| `CAMERA_CUT` | `2` | Instant camera cut. |
| `CLICK_SOURCE_SCOREBOARD` | `0` | Player clicked from scoreboard GUI. |

---

## Fighting Styles

| Constant Name | Value | Description |
|---|---|---|
| `FIGHT_STYLE_NORMAL` | `4` | Standard GTA street fight style. |
| `FIGHT_STYLE_BOXING` | `5` | Boxing style. |
| `FIGHT_STYLE_KUNGFU` | `6` | Kung Fu martial arts style. |
| `FIGHT_STYLE_KNEEHEAD` | `7` | Kneehead Muay Thai style. |
| `FIGHT_STYLE_GRABKICK` | `15` | Grab kick style. |
| `FIGHT_STYLE_ELBOW` | `16` | Elbow fighting style. |

---

## Server & Player Variable Types

| Constant Name | Description |
|---|---|
| `SERVER_VARTYPE_NONE` | Variable does not exist. |
| `SERVER_VARTYPE_INT` | Server integer variable. |
| `SERVER_VARTYPE_STRING` | Server string variable. |
| `SERVER_VARTYPE_FLOAT` | Server float variable. |
| `PLAYER_VARTYPE_NONE` | Player variable does not exist. |
| `PLAYER_VARTYPE_INT` | Player integer variable. |
| `PLAYER_VARTYPE_STRING` | Player string variable. |
| `PLAYER_VARTYPE_FLOAT` | Player float variable. |
