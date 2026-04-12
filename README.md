-- Replacement for cloneref (Solara doesn't support it)
local function safe_cloneref(service)
    return service
end

repeat task.wait() until game:IsLoaded()

local wait = task.wait
local spawn = task.spawn

local Players = safe_cloneref(game:GetService("Players"))
local TweenService = safe_cloneref(game:GetService("TweenService"))
local Lighting = safe_cloneref(game:GetService("Lighting"))
-- Solara doesn't usually have gethui, default to CoreGui
local CoreGui = game:GetService("CoreGui") 
local LocalPlayer = Players.LocalPlayer

-- Fix for getexecutorname error in Solara
local executor_name = "Solara"
if getexecutorname then
    executor_name = getexecutorname():match("^%s*(.-)%s*$") or "Solara"
end

local title = "nah hub"
local labels = {}
local spacing = 48

-- UI LOADING SECTION (Kept your original logic)
local blur = Instance.new("BlurEffect")
blur.Size = 0
blur.Parent = Lighting
TweenService:Create(blur, TweenInfo.new(0.25, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), { Size = 35 }):Play()

local gui = Instance.new("ScreenGui")
gui.Name = "nah hub"
gui.IgnoreGuiInset = true
gui.ResetOnSpawn = false
gui.Parent = CoreGui

local root = Instance.new("Frame")
root.Size = UDim2.new(1, 0, 1, 0)
root.BackgroundTransparency = 1
root.Parent = gui

local background = Instance.new("Frame")
background.Size = UDim2.new(1, 0, 1, 0)
background.BackgroundColor3 = Color3.fromRGB(15, 0, 25)
background.BackgroundTransparency = 1
background.ZIndex = 0
background.Parent = root
TweenService:Create(background, TweenInfo.new(0.25, Enum.EasingStyle.Sine), { BackgroundTransparency = 0.18 }):Play()

-- LOGO FIX: Standard ImageLabel for Solara
local image = Instance.new("ImageLabel")
image.AnchorPoint = Vector2.new(0.5, 0.5)
image.Position = UDim2.new(0.5, 0, 0.4, 0)
image.Size = UDim2.new(0, 0, 0, 0)
image.BackgroundTransparency = 1
image.Image = "rbxassetid://128862750268311"
image.ImageTransparency = 1
image.ScaleType = Enum.ScaleType.Fit
image.Parent = gui

TweenService:Create(image, TweenInfo.new(0.4, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
	Size = UDim2.new(0, 200, 0, 200),
	ImageTransparency = 0
}):Play()

local function FadeOut()
	TweenService:Create(image, TweenInfo.new(0.2, Enum.EasingStyle.Sine), {
		ImageTransparency = 1,
		Size = UDim2.new(0, 180, 0, 180)
	}):Play()

	for _, lbl in ipairs(labels) do
		TweenService:Create(lbl, TweenInfo.new(0.2, Enum.EasingStyle.Sine), {
			TextTransparency = 1,
			TextStrokeTransparency = 1,
			TextSize = 22
		}):Play()
	end
	TweenService:Create(background, TweenInfo.new(0.2), { BackgroundTransparency = 1 }):Play()
	TweenService:Create(blur, TweenInfo.new(0.2), { Size = 0 }):Play()
	task.wait(0.25)
	gui:Destroy()
	blur:Destroy()
end

-- TEXT ANIMATION
for i = 1, #title do
	local char = title:sub(i, i)
	local lbl = Instance.new("TextLabel")
	lbl.Text = char
	lbl.Font = Enum.Font.GothamBlack
	lbl.TextColor3 = Color3.fromRGB(255, 255, 255)
	lbl
