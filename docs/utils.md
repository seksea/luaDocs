# Utils

## Utils

### GetEntitiesByClassID()
*Gets all entities that match a classid, much more efficient than a crude loop over all ents*

Example:
```lua
-- Simple ChickenESP using GetEntitiesByClassID
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

## Math

### WorldToScreen()
*Takes a Vec3, returns a Vec2 of where it exists on-screen*

Example:
```lua
-- Simple ChickenESP using WorldToScreen
function onDraw()
        if Interfaces.Engine.IsInGame() then
                for k, chickenEntity in pairs(Utils.GetEntitiesByClassID(36)) do
                        if chickenEntity:Exists() then
                                local origin = chickenEntity:Origin()
				local originOnScreen = Math.WorldToScreen(origin)
                                Draw.CenteredOutlinedText(Vec2(originOnScreen.x, originOnScreen.y), Color(255, 255, 255, 255), Color(0, 0, 0, 255), "Chicken")
                        end
                end
        end
end

RegisterHook("Draw", "onDraw")
```

## Draw
*Everything in this section should be done in a draw hook*

* `Draw.Rect(Vec2 min, Vec2 max, Color col, int thickness)`
* `Draw.RoundedRect(Vec2 min, Vec2 max, Color col, int thickness, int rounding)`
* `Draw.OutlinedRect(Vec2 min, Vec2 max, Color col, Color outlineColor, int thickness)`
* `Draw.OutlinedRoundedRect(Vec2 min, Vec2 max, Color col, Color outlineColor, int thickness, int rounding)`

* `Draw.FilledRect(Vec2 min, Vec2 max, Color col, int thickness)`
* `Draw.FilledRoundedRect(Vec2 min, Vec2 max, Color col, int thickness, int rounding)`
* `Draw.FilledOutlinedRect(Vec2 min, Vec2 max, Color col, Color outlineColor, int thickness)`
* `Draw.FilledOutlinedRoundedRect(Vec2 min, Vec2 max, Color col, Color outlineColor, int thickness, int rounding)`

* `Draw.Circle(Vec2 pos, int r, Color col)`
* `Draw.OutlinedCircle(Vec2 pos, int r, Color col, Color outlineColor)`
* `Draw.FilledCircle(Vec2 pos, int r, Color col)`
* `Draw.FilledOutlinedCircle(Vec2 pos, int r, Color col, Color outlineColor)`

* `Draw.Text(Vec2 pos, Color col, string text)`
* `Draw.OutlinedText(Vec2 pos, Color col, Color outlineColor, string text)`
* `Draw.CenteredText(Vec2 pos, Color col, string text)`
* `Draw.CenteredOutlinedText(Vec2 pos, Color col, Color outlineColor, string text)`
