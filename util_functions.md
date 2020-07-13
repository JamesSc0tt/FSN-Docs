## Client
To be able to call these in your script, ensure that it is included in the `__resource.lua` or `fxmanifest.lua`.
```lua
--[[/	:FSN:	\]]--
resource_manifest_version '44febabe-d386-4d18-afbe-5e627f4af937'
client_script '@fsn_main/cl_utils.lua'
--[[/	:FSN:	\]]--
```
### Util.Tick
*A simple wrapper for CreateThread + while do*

Argument | Type | Description
--- | --- | ---
`f` | function | The function you wish to run
`ms` | number | Number of milliseconds to wait at beginning. Defaults to `0`.
#### Example
```lua
--[[
	This example will display 'Example Text' on the player every tick.
]]--

Util.Tick(function()
	local loc = GetEntityCoords(GetPlayerPed(-1))
	Util.DrawText3D(loc.x, loc.y, loc.z, 'Example text')
end) 
``` 
```javascript
	// This function is not available in javascript.
```
### Util.Repeat
*Easy way to repeat something for x amount of seconds, good for locking animations*

Argument | Type | Description
--- | --- | ---
`f` | function | The function you wish to run
`s` | number | Number of seconds to repeat the function for.
#### Example
```lua
--[[
	This example will put the player in a drinking animation for 10 seconds.
]]--

Util.Repeat(function() 
	Util.LoadAnimDict('amb@code_human_in_car_mp_actions@drink@std@rps@base')

	if not IsEntityPlayingAnim(GetPlayerPed(-1), 'amb@code_human_in_car_mp_actions@drink@std@rps@base', 'idle_a', 3) then
		TaskPlayAnim(GetPlayerPed(-1), 'amb@code_human_in_car_mp_actions@drink@std@rps@base', 'idle_a', 8.0, 1.0, -1, 16, 0, 0, 0, 0)
	end
end, 10)
``` 
```javascript
	// This function is not available in javascript.
```
### Util.CreateBlip
*Easy way for creating a blip with 1 line*

Argument | Type | Description
--- | --- | ---
`name` | string | The name of the blip in the GTA map.
`sprite` | number | Sprite for the blip, list: https://docs.fivem.net/docs/game-references/blips/
`color` | number | The colour the blip should be, list: https://gtaforums.com/topic/864881-all-blip-color-ids-pictured/
`range` | boolean | True/false to set the blip as short range.
#### Example
```lua
--[[
	This example will put a blip on the map.
]]--

Citizen.CreateThread(function()
	local loc = {x = 183.01249694824, y = -1319.4348144531, z = 29.317804336548}
	local blip = Util.CreateBlip("Pawn Store", 277, 1, loc, true)
end)
```
```javascript
	// This function is not available in javascript.
```
### Util.SpawnVehicle
*Spawns a vehicle where specified.*

Argument | Type | Description
--- | --- | ---
`hash` | string | GTA Hash of the vehicle you wish to spawn.
`xyzh` | table | Coordinates to spawn vehicle at.
#### Example
```lua
--[[
	This example will spawn an FMJ at the pawn store.
]]--

Citizen.CreateThread(function()
	local loc = {183.01249694824, -1319.4348144531, 29.317804336548, 1.01}
	local vehicle = Util.SpawnVehicle(GetHashKey('fmj'), loc)
end)
```
```javascript
	// This function is not available in javascript.
```
### Util.DrawText
*Displays text on screen.*

Argument | Type | Description
--- | --- | ---
`text` | string | The text to display.
`font` | number | Font to use, list: https://gtaforums.com/topic/794014-fonts-list/
`center` | boolean | True/false align text center.
`x` | number | Padding to left of screen.
`y` | number | Padding to top of screen. 
`scale` | number | Font size.
`col` | Color of text.
#### Example
```lua
--[[
	This example will display text on screen.
]]--

Util.Tick(function()
	Util.DrawText('Hello Barn Finder', 4, false, 20, 20, 0.6, Color(255,255,255))
end) 
```
```javascript
	// This function is not available in javascript.
```
### Util.DrawText3D
*Displays text at a point in the world.*

Argument | Type | Description
--- | --- | ---
`x` | number | X position in the world.
`y` | number | Y position in the world. 
`z` | number | Z position in the world. 
`text` | string | The text to display.

#### Example
```lua
--[[
	This example will display 'Example Text' on the player every tick.
]]--

Util.Tick(function()
	local loc = GetEntityCoords(GetPlayerPed(-1))
	Util.DrawText3D(loc.x, loc.y, loc.z, 'Example text')
end) 
``` 
```javascript
	// This function is not available in javascript.
```
### Util.FormatMoneyString
*Will return a formatted red or green string if the player can afford it.*

Argument | Type | Description
--- | --- | ---
`amt` | number | Money amount.

#### Example
```lua
--[[
	This example will display text on the player prompting them to enter the clothing store.
]]--

Util.Tick(function()
	local loc = GetEntityCoords(GetPlayerPed(-1))
	Util.DrawText3D(loc.x, loc.y, loc.z, '[E] Clothing Store ('..Util.FormatMoneyString(500)..')')
	if IsControlJustPressed(0, Util.GetKeyNumber('E')) then
		-- enter clothes store
	end
end) 
``` 
```javascript
	// This function is not available in javascript.
```
### Util.GetPlayers
*Returns a table of all the currently connected players.* 


 **NOTICE:** FiveM released a real version of this, list: https://docs.fivem.net/docs/scripting-reference/runtimes/lua/functions/GetPlayers/

Argument | Type | Description
--- | --- | ---

#### Example
```lua
--[[
	This will check if any players are nearby.
]]--

Util.Tick(function()
	for _, player in pairs(Util.GetPlayers()) do
		if Util.GetVecDist(GetEntityCoords(GetPlayerPed(player)),GetEntityCoords(GetPlayerPed(-1))) < 5 then
			-- player is close
		end
	end
end) 
``` 
```javascript
	// This function is not available in javascript.
```
### Util.PrependTable
*Add the value to position one of the original table and return it.* 

Argument | Type | Description
--- | --- | ---
`t` | table | Table to add the value to.
`v` | * | The value to put into the table.

#### Example
```lua
local table = {1='one',2='two',3='three'}
table = Util.PrependTable(table, 'value')

orint(Util.PrintTable(table))
``` 
```lua
{1='value',2='one',3='two',4='three'}
```
```javascript
	// This function is not available in javascript.
```
### Util.PrintTable
*Return a formatted string of the table.* 

Argument | Type | Description
--- | --- | ---
`t` | table | Table to format into string.

#### Example
```lua
local table = {1='value',2='one',3='two',4='three'}
print(Util.PrintTable(table))
``` 
```javascript
	// This function is not available in javascript.
```
### Util.TableHasValue
*Returns true if the table includes any value matching element.* 

Argument | Type | Description
--- | --- | ---
`table` | table | Table to search.
`element` | * | The vale to search for.
#### Example
```lua
local t = {1='one',2='two',3='three'}
if Util.TableHasValue(t, 'pear') then
	print('has value')
else
	print('nothing')
end
``` 
```lua
nothing
```
```javascript
	// This function is not available in javascript.
```
### Util.GetVecDist
*Gets the vector distance between two entities.* 

Argument | Type | Description
--- | --- | ---
`v1` | vector3 | Vector to compare against.
`v2` | vector3 | Vector to compare against.
#### Example
```lua
if Util.GetVecDist(GetEntityCoords(GetPlayerPed(-1)), GetEntityCoords(vehicle)) then
	print('is nearby')
end
``` 
```lua
is nearby
```
```javascript
	// This function is not available in javascript.
```
### Util.PositionCheck
*Not really sure what this does...* 

Argument | Type | Description
--- | --- | ---
`playerPos` | vector3 | GetEntityCoords(GetPlayerPed(-1)).
`xyz` | vector3 | Vector to compare against.
#### Example
```lua
	-- not sure how to use this
``` 
```javascript
	// This function is not available in javascript.
```
### Util.GetClosestPlayer
*Stolen from Frazzle in #scripting-gated, returns the closest player + how far away they are.* 

Argument | Type | Description
--- | --- | ---
#### Example
```lua
Util.Tick(function()
	local ply,dist = Util.GetClosestPlayer()
	if dist < 5 then 
		local pos = GetEntityCoords(GetPlayerPed(ply))
		Util.DrawText3D(pos.x, pos.y, pos.z 'Player')
	end
end)
``` 
```javascript
	// This function is not available in javascript.
```
### Util.LoadAnimDict
*Simple one liner to load an anim dictionary.* 

Argument | Type | Description
--- | --- | ---
`dict` | string | The anim dictionary to load.
#### Example
```lua
--[[
	This example will put the player in a drinking animation for 10 seconds.
]]--

Util.Repeat(function() 
	Util.LoadAnimDict('amb@code_human_in_car_mp_actions@drink@std@rps@base')

	if not IsEntityPlayingAnim(GetPlayerPed(-1), 'amb@code_human_in_car_mp_actions@drink@std@rps@base', 'idle_a', 3) then
		TaskPlayAnim(GetPlayerPed(-1), 'amb@code_human_in_car_mp_actions@drink@std@rps@base', 'idle_a', 8.0, 1.0, -1, 16, 0, 0, 0, 0)
	end
end, 10)
``` 
```javascript
	// This function is not available in javascript.
```
### Util.MakeString
*Make a randomly generated string* 

Argument | Type | Description
--- | --- | ---
`length` | number | Number of characters to create string.
#### Example
```lua
['WEAPON_STUNGUN'] = {
    index = "WEAPON_STUNGUN",
    name = "Stun Gun",
    amt = 1,
    customData = {
        weapon = 'true',
        ammo = 0,
        ammotype = 'none',
        quality = 'normal',
        PDIssued = Util.MakeString(6)
    }
},
``` 
```javascript
	// This function is not available in javascript.
```
### Util.GetKeyNumber
*Stop the horrendous replication of the massive KEYS table, this just does that but better.* 

Argument | Type | Description
--- | --- | ---
`key` | string | Which key to retur the number of.
#### Example
```lua
--[[
	This example will display text on the player prompting them to enter the clothing store.
]]--

Util.Tick(function()
	local loc = GetEntityCoords(GetPlayerPed(-1))
	Util.DrawText3D(loc.x, loc.y, loc.z, '[E] Clothing Store ('..Util.FormatMoneyString(500)..')')
	if IsControlJustPressed(0, Util.GetKeyNumber('E')) then
		-- enter clothes store
	end
end) 
``` 
```javascript
	// This function is not available in javascript.
```

## Server
### Util.SplitString
*Split the string into table by seperator.* 

Argument | Type | Description
--- | --- | ---
`inputstr` | string | String to split up.
`sep` | string | Numerator to seperate the string by.
#### Example
```lua
AddEventHandler('chatMessage', function(source, auth, msg)
	local split = Util.SplitString(msg, ' ')
end)
``` 
```javascript
	// This function is not available in javascript.
```
### Util.GetSteamID
*Get the SteamID of the player, will drop the player if they don't have one.* 

Argument | Type | Description
--- | --- | ---
`src` | playerID | Player to get the SteamID of.
#### Example
```lua
AddEventHandler('chatMessage', function(source, auth, msg)
	print(source..' ('..Util.GetSteamID(source)..') said: '..msg)
end)
``` 
```lua
1 (steam:11000010e0828a9) said: Yo wassup
```
```javascript
	// This function is not available in javascript.
```
### Util.MakeString
*Make a randomly generated string* 

Argument | Type | Description
--- | --- | ---
`length` | number | Number of characters to create string.
#### Example
```lua
['WEAPON_STUNGUN'] = {
    index = "WEAPON_STUNGUN",
    name = "Stun Gun",
    amt = 1,
    customData = {
        weapon = 'true',
        ammo = 0,
        ammotype = 'none',
        quality = 'normal',
        PDIssued = Util.MakeString(6)
    }
},
``` 
```javascript
	// This function is not available in javascript.
```
