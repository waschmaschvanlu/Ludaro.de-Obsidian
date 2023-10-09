# Sprites in NativeUI: Enhancing Visual Elements 🎨

Sprites are fundamental elements within NativeUI that bring graphical textures to your PC screen. These graphics can represent various objects or visual components, and the entire menu itself can be considered a textured sprite.

## Creating Sprites: The Process

To create a sprite in NativeUI, you use a specific function that requires multiple parameters to define its appearance. Here's an example of how to create a sprite:

```lua
local TxtDictionary = "Your Texture Directory"
local TxtName = "Your Texture Name"
local X = 0
local Y = 0
local Width = 0
local Height = 0
local Heading = 0
local R = 0
local G = 0
local B = 0
local A = 255

local Sprite = Sprite.New(TxtDictionary, TxtName, X, Y, Width, Height, Heading, R, G, B, A)
```
In this example, you set the necessary parameters such as the texture directory, texture name, position (X and Y coordinates), width, height, orientation (rotation angle), and tint color (R, G, B, and A for Alpha). Once the sprite is created, you can use it to enhance the visual aspects of your projects.

## Resource Usage Considerations

Creating sprites can be resource-intensive, and it's recommended to use them only when necessary. Excessive use of sprites can impact the performance of your application. Therefore, it's essential to strike a balance between aesthetics and efficiency.

## Essential for NativeUI Functionality

Sprites play a central role in the mechanics of NativeUI and are closely related to other files within the framework. They form the backbone of the visual appeal of the menu system. Understanding how to create and use sprites effectively is a relatively demanding task and may not be necessary if you're only interested in creating menus.

[Source](https://github.com/MrMathias154/NativeUILua-Reloaded/blob/master/elements/Sprite.lua)
# File Contents
```lua
Sprite = setmetatable({}, Sprite)
Sprite.__index = Sprite
Sprite.__call = function() return "Sprite" end

---New
---@param TxtDictionary string
---@param TxtName string
---@param X number
---@param Y number
---@param Width number
---@param Height number
---@param Heading number
---@param R number
---@param G number
---@param B number
---@param A number
function Sprite.New(TxtDictionary, TxtName, X, Y, Width, Height, Heading, R, G, B, A)
	local _Sprite = {
		TxtDictionary = tostring(TxtDictionary),
		TxtName = tostring(TxtName),
		X = tonumber(X) or 0,
		Y = tonumber(Y) or 0,
		Width = tonumber(Width) or 0, 
		Height = tonumber(Height) or 0,
		Heading = tonumber(Heading) or 0,
		_Colour = {R = tonumber(R) or 255, G = tonumber(G) or 255, B = tonumber(B) or 255, A = tonumber(A) or 255},
	}
	return setmetatable(_Sprite, Sprite)
end

---Position
---@param X number
---@param Y number
function Sprite:Position(X, Y)
	if tonumber(X) and tonumber(Y) then
		self.X = tonumber(X)
		self.Y = tonumber(Y)
	else
		return {X = self.X, Y = self.Y}
	end
end

---Size
---@param Width number
---@param Height number
function Sprite:Size(Width, Height)
	if tonumber(Width) and tonumber(Width) then
		self.Width = tonumber(Width)
		self.Height = tonumber(Height)
	else
		return {Width = self.Width, Height = self.Height}
	end
end

---Colour
---@param R number
---@param G number
---@param B number
---@param A number
function Sprite:Colour(R, G, B, A)
    if tonumber(R) or tonumber(G) or tonumber(B) or tonumber(A) then
        self._Colour.R = tonumber(R) or 255
        self._Colour.B = tonumber(B) or 255
        self._Colour.G = tonumber(G) or 255
        self._Colour.A = tonumber(A) or 255
    else
    	return self._Colour
    end
end

---Draw
function Sprite:Draw()
	if not HasStreamedTextureDictLoaded(self.TxtDictionary) then
		RequestStreamedTextureDict(self.TxtDictionary, true)
	end
	local Position = self:Position()
	local Size = self:Size()
	Size.Width, Size.Height = FormatXWYH(Size.Width, Size.Height)
    Position.X, Position.Y = FormatXWYH(Position.X, Position.Y)
	DrawSprite(self.TxtDictionary, self.TxtName, Position.X + Size.Width * 0.5, Position.Y + Size.Height * 0.5, Size.Width, Size.Height, self.Heading, self._Colour.R, self._Colour.G, self._Colour.B, self._Colour.A)
end
```