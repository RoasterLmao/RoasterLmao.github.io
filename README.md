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
Enabled = true -- set by default to true
YLevelDetections = true -- set by default to true
ClientAnticheat = true -- set by default to true
Delay = 1 -- set by default to 1
MaxYLevel = 200 -- set by default to 200, if your player gets punished for no reason try changing the MaxYLevel, or disable YLevelDetections.
```
Self explainable (Antiflight).
Prevents exploiters from flying.
```lua
local aps = shared.RubyAnticheatAPI.Configurations.AntiPlatformStand
apsEnabled = true
```
↑ Sometimes prevents people from fly.
```lua
local Antigod = shared.RubyAnticheatAPI.Configurations.AntiGod
Antigod = true
```
↑ Prevents players from having GodMode. (Removing their Humanoid)
Full AntiCheat Code (Reccomended) that you can edit:
```lua
local RubyAnticheat = shared.RubyAnticheatAPI
local AntiSpeedhack = RubyAnticheat.Configurations.MagnitudeAntiSpeedhack
local AntiFlight = RubyAnticheat.Configurations.AntiFlight
local AntiPlatformstand = RubyAnticheat.Configurations.AntiPlatformStand
local AntiGodmode = RubyAnticheat.Configurations.AntiGod
AntiSpeedhack.Enabled = true -- set by default to true
AntiSpeedhack.Delay = 1 -- set by default to 1
AntiSpeedhack.MaxDistance = 30 -- set by default to 30
AntiSpeedhack.Punish = true -- set by default to true
AntiGodmode.Enabled = true -- set by default to true
AntiPlatformstand.Enabled = true -- set by default by true
Enabled = true -- set by default to true
YLevelDetections = true -- set by default to true
ClientAnticheat = true -- set by default to true
Delay = 1 -- set by default to 1
MaxYLevel = 200 -- set by default to 200, if your player gets punished for no reason try changing the MaxYLevel, or disable YLevelDetections.
```
## Functions
```lua
local RubyAnticheat = shared.RubyAnticheatAPI
RubyAnticheat.onWarned(function(plr)
    -- ...
end)
```
↑ onWarned - BETA! (Might not work)

plr: Player that got warned. (plr.UserId, plr.Name, plr.DisplayName, and other stuff inherited by Instance Properties/Functions)
```lua
local RubyAnticheat = shared.RubyAnticheatAPI
RubyAnticheat.Punish(plr,kickreason,fakelagcharacterseconds)
```
↑ Punishes player in any way selected in shared.RubyAnticheatAPI.Configurations.Punishment
## How to make your own AntiCheat?
Remember, use the Client AntiCheat for any purposes you want, but i highly reccomend you some checks and use the server anticheat.
Exploiters can spoof your walkspeed by using this script (roblox studio cannot access it):
```lua
local meta = getrawmetatable(game) -- gets the game metatable.
local old = meta.__newindex -- gets the newindex from the metatable.
setreadonly(meta, false) -- allows exploiters to edit the metatable.
meta.__newindex = newcclosure(function(self,property,value) -- get all indexed values.
if self:IsA("Humanoid") and property == "WalkSpeed" and value <= 16 then
-- ↑ Check if the indexed instance is humanoid, after it is checks if the property is "WalkSpeed" and then checks if the value is lower than 16, and if it is then returns to the instance the property and then the value. (Simply self.WalkSpeed = 16)
return old(self,property,16)
end
return old(self,property,value)
end)
```
↑ This script spoofs the exploiter's WalkSpeed if it changes.
Learn about exploiters here: [Exploiters and how they spoof stuff in your game](https://devforum.roblox.com/t/exploiters-and-how-they-spoof-stuff-in-your-own-game/695958)

Learn about making anticheats here: [How to make an strong anticheat and antihack](https://devforum.roblox.com/t/making-an-strong-anti-cheat-and-anti-hack-code/1884582/3)

What you must know about client and server: [Client And Server](https://developer.roblox.com/en-us/articles/Roblox-Client-Server-Model)

One free AntiCheat i found: [Robot's Anticheat (RELEASE)](https://devforum.roblox.com/t/robos-anti-cheat/1912416)

How exploiters bypass client sided anticheats: [Hooking metatables and other stuff](https://www.youtube.com/watch?v=cOzWLv_2iWs)

How to make a perfect anticheat for your game like this one:

Simple Anticheats (for begginers and starters): [Simple anticheat](https://www.youtube.com/watch?v=K2T6UNKq_E8)

Advanced Anticheats (for people that know already scripting): [Advanced Anticheat](https://www.youtube.com/watch?v=yMHN08m_56k)

What you should know about remotes and how you should protect them: [Remote Functions and Events](https://developer.roblox.com/en-us/articles/Remote-Functions-and-Events)
## Okay, if we learned about stuff how to make an anticheat and how exploiters spoof stuff in your game, how do we make an AntiCheat?
Well, try making a script (Script that's blue called ServerScript but shows as Script) in ServerScriptService.
After you made it, open the script and write or paste this script in there:
```lua
local maxDistance = 20 -- set this to anything you want, the higher the more distance required to find an exploiter, do not set it under 16 or else every time you move you will get lagbacked.
function vec1_vec2_to_magnitude(v1,v2) -- convert 2 vector3s into a magnitude
    return (v1 - v2).Magnitude -- 2 vector3s into magnitude
end -- end function
function get_plr_chr(plr) -- get players character
    if plr["Character"] ~= nil and plr["Character"]["PrimaryPart"] ~= nil then
        return plr.Character
    end
end
game.Players.PlayerAdded:Connect(function(plr) -- run a script everytime a player joins
    while wait() do -- loop
        local first = get_plr_chr(plr).PrimaryPart.Position -- get first position
        wait(1) -- wait 1 second
        local second = get_plr_chr(plr).PrimaryPart.Position -- get second position
        local dist = vec1_vec2_to_magnitude(second) -- get players distance
        if dist > maxDistance then -- check if the distance is greater than the maxDistance (20 by default)
            get_plr_chr(plr).PrimaryPart.CFrame = CFrame.new(first) -- teleport player back to place where it flagged
       end
    end
end
```
You also can add this as a localscript into StarterPlayer => StarterCharacterScripts (NOT RECCOMENDED AS ITS BYPASSABLE)
```lua
function gethummy()
    return script.Parent:FindFirstChildWhichIsA("Humanoid")
end
while wait() do
    if gethummy() ~= nil then
        local hummy = gethummy()
        if hummy.WalkSpeed <= 16 and hummy.Walkspeed >= 16 then
            game.Players.LocalPlayer:Kick("You have been kicked for having your walkspeed better or lower than 16")
        end
        if hummy.JumpPower <= 50 and hummy.JumpPower >= 50 then
            game.Players.LocalPlayer:Kick("You have been kicked for having your jumppower better or lower than 50")
        end
    end
end
```
