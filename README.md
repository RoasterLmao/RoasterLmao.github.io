# Ruby Anticheat
**CURRENTLY REWRITING!**

![Logo](https://user-images.githubusercontent.com/110973471/183887863-a727dc59-ba41-40a0-982e-2df761c2b195.png)

Hello! This anticheat is fully free, and is only for ROBLOX.

Press [this](https://discord.gg/CWzpTJphxu) to join Ruby's AntiCheat Discord server.

Keep in mind, **Ruby Anticheat** is still not in **release**. After it is in release, it is gonna be in version **indev 1.0.0**.

Inspired by:

- Crystal Anticheat
- WatchCat (roblox bedwars)
- WatchDog (minecraft bedwars)

↑ Punishes player in any way selected in ~~shared.RubyAnticheatAPI.Configurations.Punishment~~
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
function get_plr_chr(plr): Model -- get players character
	if plr["Character"] ~= nil and plr["Character"]["PrimaryPart"] ~= nil then
		return plr.Character
	end
end
game.Players.PlayerAdded:Connect(function(plr) -- run a script everytime a player joins
	while wait() do -- loop
		if not plr:FindFirstChild("HumanoidRootPart") then
			repeat wait() until plr:FindFirstChild("HumanoidRootPart")
		end
		local first = get_plr_chr(plr):FindFirstChild("HumanoidRootPart").Position -- get first position
		wait(1) -- wait 1 second
		local second = get_plr_chr(plr):FindFirstChild("HumanoidRootPart").Position -- get second position
		local dist = vec1_vec2_to_magnitude(second) -- get players distance
		if dist > maxDistance then -- check if the distance is greater than the maxDistance (20 by default)
			get_plr_chr(plr).PrimaryPart.CFrame = CFrame.new(first) -- teleport player back to place where it flagged
		end
	end
end)
```
You also can add this as a localscript into StarterPlayer => StarterCharacterScripts (NOT RECCOMENDED AS ITS BYPASSABLE)

Keep in mind: ↓ this script doesn't work, so please use other one upper there ↑, or use Ruby AntiCheat as it is reccomended.
```lua
function gethummy()
	return script.Parent:FindFirstChildWhichIsA("Humanoid")
end
while wait() do
	if gethummy() ~= nil then
		local hummy = gethummy()
		if hummy.WalkSpeed <= 15 and hummy.WalkSpeed >= 17 then
			game.Players.LocalPlayer:Kick("You have been kicked for having your walkspeed better or lower than 16")
		end
		if hummy.JumpPower <= 49 and hummy.JumpPower >= 51 then
			game.Players.LocalPlayer:Kick("You have been kicked for having your jumppower better or lower than 50")
		end
	end
end
```
