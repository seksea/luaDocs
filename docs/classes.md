# Classes
## Entity

### GetNetvarInt()
*Returns value of a netvar int*

Example:
```lua
-- Get localPlayer
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
        print("localPlayer's health: " .. localPlayer:GetNetvarInt("DT_BasePlayer", "m_iHealth"))
end
```
Output: `localPlayer's health: 100`

### GetNetvarFloat()
*Same as GetNetvarInt(), just with a float*

### ClassID()
*Return's the entities' ClassID, e.g 35 for players*

Example:
```lua
-- Get localPlayer
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
        print("localPlayer's classid: " .. localPlayer:ClassID())
end
```
Output: `localPlayer's classid: 35`

### NetworkName()
*Return's the entities' network name e.g `TODO:add players' networkname` for players*

Example:
```lua
-- Get localPlayer
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
        print("localPlayer's network name: " .. localPlayer:NetworkName())
end
```
Output: `localPlayer's network name: TODO: get player's networkname`

### Exists()
*Checks the entity exists, checking for this should be done before doing anything else involving the ent*

Example:
```
-- Get localPlayer
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
        print("localPlayer's network name: " .. localPlayer:NetworkName())
end
```

### Enemy()
*Checks if the entity is an enemy, this should be used over team netvar as it accounts for dangerzone too*

Example:
```
-- Get localPlayer
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
        print("is localPlayer an enemy? (will obviously return false): " .. localPlayer:Enemy())
end
```
Output: `is localPlayer an enemy? (will obviously return false): false`

### Origin()
*Gets entities' position*

Example:
```lua
local localPlayer = Interfaces.EntityList.GetClientEntity(Interfaces.Engine.GetLocalPlayer())
if localPlayer:Exists() then
        -- Get the localPlayer's origin
        local origin = localPlayer:Origin()
        -- Print the origin
        print("localPlayer's origin = X:" .. origin.x .. " Y:" .. origin.y .. " Z:" .. origin.z)
end
```

Output: `localPlayer's origin = X:1853.345 Y:-242.234 Z:232.463`

### GetBox()
*Gets a box around the specified entity for ESP and returns each corner in a vec4*

Example:
```lua
-- Simple ChickenESP using GetBox
function onDraw()
	if Interfaces.Engine.IsInGame() then
		for k, chickenEntity in pairs(Utils.GetEntitiesByClassID(36)) do
			if chickenEntity:Exists() then
				local box = chickenEntity:GetBox()
				Draw.CenteredOutlinedText(Vec2(box.x + ((box.z-box.x)//2), box.y - 14), Color(255, 255, 255, 255), Color(0, 0, 0, 255), "Chicken")
				Draw.OutlinedRect(Vec2(box.x, box.y), Vec2(box.z, box.w), Color(255, 255, 255, 255), Color(0, 0, 0, 255), 1)
			end
		end
	end
end

RegisterHook("Draw", "onDraw")
```

## Color
*Basic color class*

Contains: r, g, b, a

## Vec2
*Basic Vec2 class*

Contains: x, y

## Vec3
*Basic Vec3 class*

Contains: x, y, z

## Vec4
*Basic Vec4 class*

Contains: x, y, z, w
