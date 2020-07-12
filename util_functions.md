## Client
### Util.Tick()
A wrapper to simplify the following:
```lua
Citizen.CreateThread(function()
  while true do
    Citizen.Wait(0)
  end
end)
```
#### Examples
```lua
  Util.Tick(function()
    Util.DrawText3D(GetEntityCoords(GetPlayerPed(-1)).x, GetEntityCoords(GetPlayerPed(-1)).y, GetEntityCoords(GetPlayerPed(-1)).z, 'Example text')
  end) 
``` 
