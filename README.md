-- [[ NAH HUB: SOLARA VERSION ]] --
repeat task.wait() until game:IsLoaded()

print("--- Link Success: Loading nah hub ---")

local sid = "3bb7969a9ecb9e317b0a24681327c2e2" -- Rivals ID

local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = sid
api.load_script()
