-- [[ NAH HUB: SOLARA LITE LOADER ]] --
repeat task.wait() until game:IsLoaded()

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- Check for Rivals ID
local script_id = "3bb7969a9ecb9e317b0a24681327c2e2" 

if tostring(game.GameId) ~= "6035872082" then
    print("Not in Rivals. Running general check...")
end

-- [[ THE OVERLAY (Fixes Invisible Menu) ]] --
task.spawn(function()
    while task.wait(2) do
        local target = gethui and gethui() or game:GetService("CoreGui")
        for _, gui in pairs(target:GetChildren()) do
            -- This finds the Solix menu and FORCES it to be visible
            if gui:IsA("ScreenGui") and (gui.Name:find("Solix") or gui.Name:find("Hub")) then
                gui.Enabled = true
                gui.Name = "nah hub"
                for _, obj in pairs(gui:GetDescendants()) do
                    if obj:IsA("Frame") then
                        obj.BackgroundTransparency = 0 -- Makes the menu solid so you can see it
                    end
                    if obj:IsA("TextLabel") and obj.Text:find("Solix") then
                        obj.Text = "nah hub"
                        obj.TextColor3 = Color3.fromRGB(255, 110, 170)
                    end
                end
            end
        end
    end
end)

-- [[ BYPASS LOAD ]] --
print("Loading nah hub for Solara...")
local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = script_id
api.load_script()
