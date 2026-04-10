-- [[ NAH HUB: RIVALS FIXED ]] --
repeat task.wait() until game:IsLoaded()

print("Connection Check: Starting...")

local script_id = "3bb7969a9ecb9e317b0a24681327c2e2"

-- Loader
local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = script_id
api.load_script()

print("Nah Hub: Script Sent to Luarmor")

-- UI Visibility Fix
task.spawn(function()
    while task.wait(2) do
        local target = gethui and gethui() or game:GetService("CoreGui")
        for _, v in pairs(target:GetChildren()) do
            if v:A("ScreenGui") and (v.Name:find("Solix") or v.Name:find("Hub")) then
                v.Enabled = true
            end
        end
    end
end)
