-- [[ NAH HUB: SOLARA + RIVALS SUPPORT ]] --
repeat task.wait() until game:IsLoaded()

local Players = game:GetService("Players")
local CoreGui = gethui and gethui() or game:GetService("CoreGui")
local LocalPlayer = Players.LocalPlayer

-- [[ GAME IDS ]] --
local GameList = {
    ["3808223175"] = { id = "4fe2dfc202115670b1813277df916ab2" }, -- Jujutsu Infinite
    ["994732206"]  = { id = "e2718ddebf562c5c4080dfce26b09398" }, -- Blox Fruits
    ["1511883870"] = { id = "fefdf5088c44beb34ef52ed6b520507c" }, -- Shindo Life
    ["6035872082"] = { id = "3bb7969a9ecb9e317b0a24681327c2e2" }, -- RIVALS
    ["245662005"]  = { id = "21ad7f491e4658e9dc9529a60c887c6e" }, -- Jailbreak
    ["3317771874"] = { id = "e95ef6f27596e636a7d706375c040de4" }  -- Pet Simulator 99
}

local game_id = tostring(game.GameId)
local config = GameList[game_id]

if not config then
    warn("Game not supported by nah hub.")
    return
end

-- [[ THE NAH HUB RESKINNER ]] --
task.spawn(function()
    while task.wait(1) do
        local target = gethui and gethui() or game:GetService("CoreGui")
        for _, gui in pairs(target:GetChildren()) do
            if gui:IsA("ScreenGui") and gui.Name ~= "nah hub" then
                for _, obj in pairs(gui:GetDescendants()) do
                    if obj:IsA("TextLabel") and (obj.Text:find("Solix") or obj.Text:find("Hub")) then
                        obj.Text = "nah hub"
                        obj.TextColor3 = Color3.fromRGB(255, 110, 170)
                    end
                    if obj:IsA("Frame") and obj.BackgroundColor3 == Color3.fromRGB(15, 12, 16) then
                        obj.BackgroundColor3 = Color3.fromRGB(15, 0, 25)
                    end
                end
            end
        end
    end
end)

-- [[ LUARMOR EXECUTION ]] --
local api = loadstring(game:HttpGet("https://sdkapi-public.luarmor.net/library.lua"))()
api.script_id = config.id
api.load_script()
