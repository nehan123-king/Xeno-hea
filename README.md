-- [[ NAH HUB: SOLARA FIXED ]] --
repeat task.wait() until game:IsLoaded()

print("Checking for Rivals...")

-- Rivals ID
local script_id = "3bb7969a9ecb9e317b0a24681327c2e2"

-- Loader
local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = script_id
api.load_script()

-- Force UI Visibility
task.spawn(function()
    while task.wait(5) do
        local ui = gethui and gethui() or game:GetService("CoreGui")
        for _, v in pairs(ui:GetChildren()) do
            if v:IsA("ScreenGui") and (v.Name:find("Solix") or v.Name:find("Hub")) then
                v.Enabled = true
                v.Name = "nah hub"
            end
        end
    end
end)
