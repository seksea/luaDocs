# Examples

## Simple ESP

```lua
function onDraw()
        if Interfaces.Engine.IsInGame() then
                for k, index in pairs(Utils.GetEntitiesByClassID(40)) do
                        if not (index == Interfaces.Engine.GetLocalPlayer()) then
			                    local entity = Interfaces.EntityList.GetClientEntity(index)
                                if entity:Exists() and not entity:Dormant() and entity:GetNetvarInt("DT_BasePlayer", "m_iHealth") > 0 then
				                    local box = entity:GetBox()
                                    Draw.OutlinedRect(Vec2(box.x, box.y), Vec2(box.z, box.w), entity:Enemy() and UI.GetConfigColor("simpleESP.EnemyColor") or UI.GetConfigColor("simpleESP.TeamColor"), Color(0, 0, 0, 100), 1)
                                end
                        end
                end
        end
end

function onUI()
    UI.AddColorPicker("Enemy", "simpleESP.EnemyColor")
    UI.AddColorPicker("Team", "simpleESP.TeamColor")
end

RegisterHook("Draw", "onDraw")
RegisterHook("UI", "onUI")
```

## Chicken ESP

```lua
function onDraw()
	if Interfaces.Engine.IsInGame() then
													-- Chicken's classid is 36
		for k, chickenIndex in pairs(Utils.GetEntitiesByClassID(36)) do
			local chickenEntity = Interfaces.EntityList.GetClientEntity(chickenIndex)
			if chickenEntity:Exists() and not chickenEntity:Dormant() then
				local box = chickenEntity:GetBox()
				Draw.CenteredOutlinedText(Vec2(box.x + ((box.z-box.x)//2), box.y - 14), Color(255, 255, 255, 255), Color(0, 0, 0, 255), "Chicken")
				Draw.OutlinedRect(Vec2(box.x, box.y), Vec2(box.z, box.w),  UI.GetConfigColor("chickenESP.Color"), Color(0, 0, 0, 255), 1)
			end
		end
	end
end

function onUI()
    UI.AddColorPicker("Chicken Color", "chickenESP.Color")
end

RegisterHook("UI", "onUI")
RegisterHook("Draw", "onDraw")
```

## ESP Everything
*Useful for getting classid's / network names of entities*

```lua
function onDraw()
	if Interfaces.Engine.IsInGame() then
		for index=0, Interfaces.EntityList.GetHighestEntityIndex() do
			local entity = Interfaces.EntityList.GetClientEntity(index)
			if entity:Exists() then
				local box = entity:GetBox()
				Draw.Text(Vec2(box.x + ((box.z-box.x)//2), box.y - 14), Color(255, 255, 255, 255), entity:NetworkName() .. " (" .. entity:ClassID() .. ")")
				Draw.OutlinedRect(Vec2(box.x, box.y), Vec2(box.z, box.w), Color(255, 255, 255, 255), Color(0, 0, 0, 255), 1)
			end
		end
	end
end

RegisterHook("Draw", "onDraw")
```
