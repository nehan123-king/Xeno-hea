-- [[ NAH HUB: SOLARA COMPATIBLE ]] --
if not game:IsLoaded() then
    game.Loaded:Wait()
end

local script_id = "3bb7969a9ecb9e317b0a24681327c2e2" -- RIVALS ID

-- Force UI Visibility for Solara
task.spawn(function()
    while task.wait(3) do
        local CoreGui = game:GetService("CoreGui")
        local target = gethui and gethui() or CoreGui
        for _, v in pairs(target:GetChildren()) do
            if v:IsA("ScreenGui") and (v.Name:find("Solix") or v.Name:find("Hub")) then
                v.Enabled = true
                v.Name = "nah hub"
            end
        end
    end
end)

print("Attempting to load nah hub...")
local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = script_id
api.load_script()
