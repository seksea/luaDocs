# Interfaces
## Engine

### GetWindowWidth()
*Returns window width:*

Example: 
```lua
print("Screen Resolution: " .. 
	tostring(Interfaces.Engine.GetScreenWidth()) .. "x" ..
	tostring(Interfaces.Engine.GetScreenHeight()))
```
Output: `Screen resolution: 1920x1080`

### GetWindowHeight()
*Returns window height:*

Example: 
```lua
print("Screen Resolution: " .. 
	tostring(Interfaces.Engine.GetScreenWidth()) .. "x" ..
	tostring(Interfaces.Engine.GetScreenHeight()))
```
Output: `Screen resolution: 1920x1080`

### GetLocalPlayer()
*Returns local player's index:*

Example: 
```lua
print("LocalPlayer: " .. tostring(Interfaces.Engine.GetLocalPlayer()))
```
Output: `LocalPlayer: 1`

### IsInGame()
*Returns true/false whether you are currently in-game:*

Example: 
```lua
print("InGame: " .. tostring(Interfaces.Engine.IsInGame()))
```
Output: `InGame: false` (would say true if in game)

### IsConnected()
*Returns true/false whether you are currently connected (in-game, or connected but in loading screen):*

Example: 
```lua
print("Connected: " .. tostring(Interfaces.Engine.IsConnected()))
```
Output: `Connected: false` (would say true if in game/end of loading screen)

### ExecuteClientCmd()
*Runs a command as if it were ran in console*

Example:
```lua
Interfaces.Engine.ExecuteClientCmd("clear;echo Hello World!")
```
Would clear the in-game console and print to it: "Hello World!"

## Input

### IsButtonDown()
*Returns true/false if button is pressed*

Example:
```lua
TODO: This example.
```

## EntityList

### GetClientEntity()
*Returns the [Entity](#Entity) of a specified index*

Example:
```lua
-- Get localPlayer
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
	-- Get the localPlayer's origin
	local origin = localPlayer:Origin()
	-- Print the origin
	print("localPlayer's origin = X:" .. origin.x .. " Y:" .. origin.y .. " Z:" .. origin.z)
end
```

Output: `localPlayer's origin = X:1853.345 Y:-242.234 Z:232.463`

### GetHighestEntityIndex
*Returns the index of the highest entity, (useful for doing a for loop over every ent in-game, although using GetEntitiesByClassID unless trying to loop through __every__ enity, as it is more efficient by a landslide)*

Example:
```lua
for entityIndex=0, Interfaces.EntityList.GetHighestEntityIndex() do
	local entity = Interfaces.EntityList.GetClientEntity(entityIndex)
	if entity:Exists() then
		local origin = entity:Origin()
		print("Entity " .. entityIndex .. "'s origin = X:" .. origin.x .. " Y:" .. origin.y .. " Z:" .. origin.z)
	end
end
```

Output: `Entity 0's origin = X:0 Y:0 Z:0` (Repeating for all entities)
