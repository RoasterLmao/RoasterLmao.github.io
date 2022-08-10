# Ruby Anticheat
Hello! This anticheat is fully free, and is only for ROBLOX.
Keep in mind, **Ruby Anticheat** is still not in **release**. After it is in release, it is gonna be in version **indev 1.0.0**.
Inspired by:
- Crystal Anticheat
- WatchCat (roblox bedwars)
- WatchDog (minecraft bedwars)
## Punishments available for now
Current punishments:
`` Crash, Kick, Respawn, fakelagcharacter``
Respawn is HIGHLY NOT RECCOMENDED.
Punishment Descriptions:
crash: Makes the screen blurry for the crashed player, and then makes the game completely unplayable (makes the client super laggy)
kick: Kicks the player out of the game for any reason you want.
respawn: Respawns the player's character.
fakelagcharacter: Makes the player's character heavy and adds in an delayed walk just like in bedwars anticheat
## Features
- No illegal guis (gui must be placed in **LocalPlayer.PlayerGui** to work): Description - prevents exploiters from putting a GUI in their playergui. **(Whitelist will be in V1.0.1)**
- Anti Platform Stand : Description - prevents exploiters from using some fly with platform stand, and prevents exploiters from standing in floor and not on floor.
- Anti Jackets : Description - Prevents players from using multiplied clothing (e.g. Jackets, Roblox multiplied clothing shirts, etc)
- Custom Settings in API (shared.RubyAnticheatAPI)
- Strong clientsided Anticheat (self explainable)
- Discord Webhook Sender API (It is in configs, down below)
- Unremovable scripts from character (Not toggable, always enabled)
and **more**!
## Documentation
```lua
shared.RubyAnticheatAPI
_G.RubyAnticheatAPI
```
↑ CAUTION: _G.RUBYANTICHEATAPI DOES NOT WORK FOR NOW. PLEASE USE SHARED.RUBYANTICHEATAPI
### you can use shared.RubyAnticheatAPI or _G.RubyAnticheatAPI, reccomended shared because _G is slower.
Allows you to change settings, and detections level, and stuff.
```lua
shared.RubyAnticheatAPI.Configurations.Punishment = "Crash";
```
If the player gets flagged, the player will get crashed by the AntiCheat.
```lua
local AntiSpeedhack = shared.RubyAnticheatAPI.Configurations.MagnitudeAntiSpeedhack
AntiSpeedhack.Enabled = true -- set by default to true
AntiSpeedhack.Delay = 1 -- set by default to 1
AntiSpeedhack.MaxDistance = 30 -- set by default to 30
AntiSpeedhack.Punish = true -- set by default to true
```
Enabled: Enables the anticheat module
Delay (SpeedHack): grabs the first position, after that it grabs the second position and then converts it to a **magnitude** (which is a length of the vector3 position), and then checks if it is greater to MaxDistance. If it is, it will flag the player. To punish the player, make sure the Punish on Speedhack is set to true.
```lua
local Antiflight = shared.RubyAnticheatAPI.Configurations.AntiFlight
Enabled = true, -- set by default to true
YLevelDetections = true, -- set by default to true
ClientAnticheat = true, -- set by default to true
Delay = 1 -- set by default to 1
MaxYLevel = 200, -- set by default to 200, if your player gets punised for no reason try changing the MaxYLevel, or disable YLevelDetections.
```
Self explainable (Antiflight).
Prevents exploiters from flying.
```lua
local aps = shared.RubyAnticheatAPI.Configurations.AntiPlatformStand
apsEnabled = true,
```
↑ Sometimes prevents people from fly.
```lua
local Antigod = shared.RubyAnticheatAPI.Configurations.AntiGod
Antigod = true,
```
↑ Prevents players from having GodMode. (Removing their Humanoid)
More Documentations coming soon!
