-- [[ TOTAL RESET LOADER ]] --
if not game:IsLoaded() then game.Loaded:Wait() end

print("STAGES: 1 - Starting Load")

-- Rivals ID directly
local sid = "3bb7969a9ecb9e317b0a24681327c2e2"

-- Simple Load - No extra threads
local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = sid
api.load_script()

print("STAGES: 2 - Script Sent to Luarmor")
