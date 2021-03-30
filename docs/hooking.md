# Hooking

## Create a hook
*A hook is done using `RegisterHook`, the first argument is what you want to hook, and the second the name of the lua func you want the hook to run*

Example:
```lua
function onDraw()
	-- This will run at draw, here you can use the draw funcs to draw primitives and text
end

function onFSN(frame)
	if frame == 3 then
		-- This will run in the NET_UPDATE_POSTDATAUPDATE_END frame in FrameStageNotify
	end
end

RegisterHook("Draw", "onDraw")
RegisterHook("FrameStageNotify", "onFSN")
```

## Hooks
*List of what you can currently hook in lua*

### Draw
*Is ran when drawing to screen, you can draw things to screen here as shown in Utils->Draw*

### FrameStageNotify
*Passes an int specifying the current frame*

| Frame | Name                            |
|-------|---------------------------------|
| -1    | UNDEFINED                       |
| 0     | START                           |
| 1     | NET_UPDATE_START                |
| 2     | NET_UPDATE_POSTDATAUPDATE_START |
| 3     | NET_UPDATE_POSTDATAUPDATE_END   |
| 4     | NET_UPDATE_END                  |
| 5     | RENDER_START                    |
| 6     | RENDER_END                      |
