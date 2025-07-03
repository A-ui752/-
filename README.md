# -
شلك دخل سكربت خاص بيه 
-- سكربت Brookhaven GUI | تصميم جني 📿
local player = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", player.PlayerGui)
gui.Name = "BrookhavenScriptByJinni"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 300, 0, 350)
frame.Position = UDim2.new(0.5, -150, 0.5, -175)
frame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
frame.BorderSizePixel = 0

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1, 0, 0, 50)
title.Text = "سكربت بروكهافن | جني 📿"
title.BackgroundColor3 = Color3.fromRGB(80, 0, 100)
title.TextColor3 = Color3.new(1, 1, 1)
title.Font = Enum.Font.GothamBold
title.TextSize = 20

-- زر: قتل الجميع
local killBtn = Instance.new("TextButton", frame)
killBtn.Size = UDim2.new(1, -20, 0, 40)
killBtn.Position = UDim2.new(0, 10, 0, 60)
killBtn.Text = "🔪 قتل الجميع"
killBtn.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
killBtn.TextColor3 = Color3.new(1,1,1)
killBtn.Font = Enum.Font.GothamBold
killBtn.TextSize = 18
killBtn.MouseButton1Click:Connect(function()
    for _, plr in pairs(game.Players:GetPlayers()) do
        if plr ~= player and plr.Character and plr.Character:FindFirstChild("Humanoid") then
            local success, remote = pcall(function()
                return game:GetService("ReplicatedStorage"):FindFirstChild("RE"):FindFirstChild("Damage")
            end)
            if success and remote then
                remote:FireServer(plr.Character.Humanoid, 9999999)
            end
        end
    end
end)

-- زر: سحب الجميع
local bringBtn = Instance.new("TextButton", frame)
bringBtn.Size = UDim2.new(1, -20, 0, 40)
bringBtn.Position = UDim2.new(0, 10, 0, 110)
bringBtn.Text = "🧲 سحب الجميع"
bringBtn.BackgroundColor3 = Color3.fromRGB(0, 150, 255)
bringBtn.TextColor3 = Color3.new(1,1,1)
bringBtn.Font = Enum.Font.GothamBold
bringBtn.TextSize = 18
bringBtn.MouseButton1Click:Connect(function()
    for _, plr in pairs(game.Players:GetPlayers()) do
        if plr ~= player and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
            plr.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame + Vector3.new(math.random(-5,5),0,math.random(-5,5))
        end
    end
end)

-- زر: تدوير اللاعبين
local spinBtn = Instance.new("TextButton", frame)
spinBtn.Size = UDim2.new(1, -20, 0, 40)
spinBtn.Position = UDim2.new(0, 10, 0, 160)
spinBtn.Text = "🌀 تدويرهم"
spinBtn.BackgroundColor3 = Color3.fromRGB(200, 100, 0)
spinBtn.TextColor3 = Color3.new(1,1,1)
spinBtn.Font = Enum.Font.GothamBold
spinBtn.TextSize = 18
spinBtn.MouseButton1Click:Connect(function()
    for _, plr in pairs(game.Players:GetPlayers()) do
        if plr ~= player and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
            for i = 1, 10 do
                plr.Character.HumanoidRootPart.CFrame *= CFrame.Angles(0, math.rad(45), 0)
                wait(0.05)
            end
        end
    end
end)

-- زر: تخريب الشاشة
local screenBtn = Instance.new("TextButton", frame)
screenBtn.Size = UDim2.new(1, -20, 0, 40)
screenBtn.Position = UDim2.new(0, 10, 0, 210)
screenBtn.Text = "📺 تخريب الشاشة"
screenBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 255)
screenBtn.TextColor3 = Color3.new(1,1,1)
screenBtn.Font = Enum.Font.GothamBold
screenBtn.TextSize = 18
screenBtn.MouseButton1Click:Connect(function()
    local blur = Instance.new("BlurEffect", game.Lighting)
    blur.Size = 56
    wait(2)
    blur:Destroy()
end)

-- زر: إغلاق
local closeBtn = Instance.new("TextButton", frame)
closeBtn.Size = UDim2.new(1, -20, 0, 40)
closeBtn.Position = UDim2.new(0, 10, 0, 270)
closeBtn.Text = "❌ إغلاق الواجهة"
closeBtn.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
closeBtn.TextColor3 = Color3.new(1,1,1)
closeBtn.Font = Enum.Font.GothamBold
closeBtn.TextSize = 18
closeBtn.MouseButton1Click:Connect(function()
    gui:Destroy()
end)
