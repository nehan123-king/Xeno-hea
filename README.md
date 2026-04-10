-- [[ NAH HUB: UNIVERSAL SOLARA LOADER ]] --
repeat task.wait() until game:IsLoaded()

print("--- nah hub loading ---")

-- Rivals Script ID
local script_id = "3bb7969a9ecb9e317b0a24681327c2e2"

-- Loader Logic
local success, result = pcall(function()
    local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
    api.script_id = script_id
    api.load_script()
end)

if not success then
    warn("nah hub: Load failed. Check F9 console.")
    print("Error:", result)
end

-- Force UI Visibility
task.spawn(function()
    while task.wait(5) do
        local cg = game:GetService("CoreGui")
        local ui = gethui and gethui() or cg
        for _, v in pairs(ui:GetChildren()) do
            if v:IsA("ScreenGui") and (v.Name:find("Solix") or v.Name:find("Hub")) then
                v.Enabled = true
                v.Name = "nah hub"
            end
        end
    end
end)
