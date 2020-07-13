## Client
### Util.Tick(f, ms)
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
  Util.DrawText3D(GetEntityCoords(GetPlayerPed(-1)).x, GetEntityCoords(GetPlayerPed(-1)).y, GetEntityCoords(GetPlayerPed(-1)).z, 'Example text')
end) 
``` 
```javascript
	// This function is not available in javascript.
```
### Util.Repeat(f, s)
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
	RequestAnimDict('amb@code_human_in_car_mp_actions@drink@std@rps@base')
	while not HasAnimDictLoaded( "amb@code_human_in_car_mp_actions@drink@std@rps@base" ) do
		Citizen.Wait(1)
	end
	if not IsEntityPlayingAnim(GetPlayerPed(-1), 'amb@code_human_in_car_mp_actions@drink@std@rps@base', 'idle_a', 3) then
		TaskPlayAnim(GetPlayerPed(-1), 'amb@code_human_in_car_mp_actions@drink@std@rps@base', 'idle_a', 8.0, 1.0, -1, 16, 0, 0, 0, 0)
	end
end, 10)
``` 
```javascript
	// This function is not available in javascript.
```
### Util.CreateBlip(name, sprite, color, xyz, range)
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
### Util.SpawnVehicle(hash, xyzh)
*Spawns a vehicle where specified.*

Argument | Type | Description
--- | --- | ---
hash | string | GTA Hash of the vehicle you wish to spawn.
xyzh | table | Coordinates to spawn vehicle at.
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
## Server
