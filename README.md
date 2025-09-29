local Players = game:GetService("Players")
local player = Players.LocalPlayer

print("[Delta Script] Iniciado para:", player.Name)

local function rewardMultiplier(baseAmount, multiplier)
    local total = baseAmount * multiplier
    print(string.format("Recompensa: Base=%d, Multiplicador=%dx → Total=%d", baseAmount, multiplier, total))
    
    -- Mostrar mensaje en pantalla
    local billboard = Instance.new("BillboardGui")
    billboard.Size = UDim2.new(0, 200, 0, 50)
    billboard.Adornee = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
    billboard.AlwaysOnTop = true
    billboard.Parent = player.PlayerGui

    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, 0, 1, 0)
    label.BackgroundTransparency = 0.5
    label.Text = string.format("+%d (x%d)", baseAmount * multiplier, multiplier)
    label.TextColor3 = Color3.new(0, 1, 0)
    label.TextScaled = true
    label.Parent = billboard

    delay(2, function()
        billboard:Destroy()
    end)
end

-- Demo
rewardMultiplier(100, 10) -- base 100, x10
