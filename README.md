local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ==================== CRIA A GUI ====================
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "GhotsHubMenu"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 520, 0, 380)
mainFrame.Position = UDim2.new(0.5, -260, 0.5, -190)
mainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
mainFrame.BorderSizePixel = 0
mainFrame.Parent = screenGui

local stroke = Instance.new("UIStroke")
stroke.Color = Color3.fromRGB(0, 255, 255)
stroke.Thickness = 3
stroke.Parent = mainFrame

local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 12)
corner.Parent = mainFrame

-- ==================== TÍTULO ====================
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 50)
title.BackgroundTransparency = 1
title.Text = "GHOTS HUB FARM BAÚ"
title.TextColor3 = Color3.fromRGB(0, 255, 255)
title.Font = Enum.Font.GothamBold
title.TextSize = 28
title.Parent = mainFrame

-- ==================== AVATAR + NICK (do jogador real) ====================
local avatarFrame = Instance.new("Frame")
avatarFrame.Size = UDim2.new(0, 180, 0, 180)
avatarFrame.Position = UDim2.new(0, 30, 0, 70)
avatarFrame.BackgroundTransparency = 1
avatarFrame.Parent = mainFrame

local avatar = Instance.new("ImageLabel")
avatar.Size = UDim2.new(1, 0, 1, 0)
avatar.BackgroundTransparency = 1
avatar.Image = "https://www.roblox.com/headshot-thumbnail/image?userId=" .. player.UserId .. "&width=420&height=420&format=png"
avatar.Parent = avatarFrame

local avatarCorner = Instance.new("UICorner")
avatarCorner.CornerRadius = UDim.new(0, 12)
avatarCorner.Parent = avatar

local nick = Instance.new("TextLabel")
nick.Size = UDim2.new(1, 0, 0, 40)
nick.Position = UDim2.new(0, 0, 1, 10)
nick.BackgroundTransparency = 1
nick.Text = player.DisplayName          -- ← NICK DA PESSOA QUE ESTÁ USANDO
nick.TextColor3 = Color3.fromRGB(255, 255, 255)
nick.Font = Enum.Font.GothamBold
nick.TextSize = 24
nick.TextStrokeTransparency = 0.7
nick.Parent = avatarFrame

-- ==================== FPS + ICONES ====================
local rightFrame = Instance.new("Frame")
rightFrame.Size = UDim2.new(0, 180, 0, 80)
rightFrame.Position = UDim2.new(1, -210, 0, 70)
rightFrame.BackgroundTransparency = 1
rightFrame.Parent = mainFrame

local discordIcon = Instance.new("ImageLabel")
discordIcon.Size = UDim2.new(0, 60, 0, 60)
discordIcon.Position = UDim2.new(0, 10, 0, 0)
discordIcon.Image = "rbxassetid://6031094678"  -- Discord
discordIcon.Parent = rightFrame

local ytIcon = Instance.new("ImageLabel")
ytIcon.Size = UDim2.new(0, 60, 0, 60)
ytIcon.Position = UDim2.new(0, 100, 0, 0)
ytIcon.Image = "rbxassetid://6031097220"  -- YouTube
ytIcon.Parent = rightFrame

local fpsLabel = Instance.new("TextLabel")
fpsLabel.Size = UDim2.new(1, 0, 0, 30)
fpsLabel.Position = UDim2.new(0, 0, 1, 5)
fpsLabel.BackgroundTransparency = 1
fpsLabel.Text = "[FPS]: 60"
fpsLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
fpsLabel.Font = Enum.Font.GothamBold
fpsLabel.TextSize = 20
fpsLabel.Parent = rightFrame

-- Atualiza FPS ao vivo
spawn(function()
    local last = tick()
    local frames = 0
    while wait() do
        frames += 1
        if tick() - last >= 1 then
            fpsLabel.Text = "[FPS]: " .. frames
            frames = 0
            last = tick()
        end
    end
end)

-- ==================== CRIADOR ====================
local creator = Instance.new("TextLabel")
creator.Size = UDim2.new(0.9, 0, 0, 50)
creator.Position = UDim2.new(0.05, 0, 0, 270)
creator.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
creator.Text = "Criador: tharlysson"
creator.TextColor3 = Color3.fromRGB(0, 255, 255)
creator.Font = Enum.Font.GothamBold
creator.TextSize = 22
creator.Parent = mainFrame

local creatorStroke = Instance.new("UIStroke")
creatorStroke.Color = Color3.fromRGB(0, 255, 255)
creatorStroke.Thickness = 2
creatorStroke.Parent = creator

local creatorCorner = Instance.new("UICorner")
creatorCorner.CornerRadius = UDim.new(0, 8)
creatorCorner.Parent = creator

-- ==================== ESTATÍSTICAS INFERIORES ====================
local statsFrame = Instance.new("Frame")
statsFrame.Size = UDim2.new(0.9, 0, 0, 70)
statsFrame.Position = UDim2.new(0.05, 0, 1, -90)
statsFrame.BackgroundTransparency = 1
statsFrame.Parent = mainFrame

-- Baba Negra Motos
local babaFrame = Instance.new("Frame")
babaFrame.Size = UDim2.new(0.48, 0, 1, 0)
babaFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
babaFrame.Parent = statsFrame

local babaLabel = Instance.new("TextLabel")
babaLabel.Size = UDim2.new(1, 0, 0.6, 0)
babaLabel.BackgroundTransparency = 1
babaLabel.Text = "Baba Negra Motos"
babaLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
babaLabel.Font = Enum.Font.GothamBold
babaLabel.TextSize = 18
babaLabel.Parent = babaFrame

local babaValue = Instance.new("TextLabel")
babaValue.Size = UDim2.new(1, 0, 0.4, 0)
babaValue.Position = UDim2.new(0, 0, 0.6, 0)
babaValue.BackgroundTransparency = 1
babaValue.Text = "x 12"
babaValue.TextColor3 = Color3.fromRGB(0, 255, 255)
babaValue.Font = Enum.Font.GothamBold
babaValue.TextSize = 28
babaValue.Parent = babaFrame

-- Baú Farmando (NOVA MUDANÇA)
local bauFrame = Instance.new("Frame")
bauFrame.Size = UDim2.new(0.48, 0, 1, 0)
bauFrame.Position = UDim2.new(0.52, 0, 0, 0)
bauFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
bauFrame.Parent = statsFrame

local bauLabel = Instance.new("TextLabel")
bauLabel.Size = UDim2.new(1, 0, 0.6, 0)
bauLabel.BackgroundTransparency = 1
bauLabel.Text = "Baú Farmando"
bauLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
bauLabel.Font = Enum.Font.GothamBold
bauLabel.TextSize = 18
bauLabel.Parent = bauFrame

local bauValue = Instance.new("TextLabel")
bauValue.Size = UDim2.new(1, 0, 0.4, 0)
bauValue.Position = UDim2.new(0, 0, 0.6, 0)
bauValue.BackgroundTransparency = 1
bauValue.Text = "x 27"
bauValue.TextColor3 = Color3.fromRGB(0, 255, 255)  -- cyan igual ao outro
bauValue.Font = Enum.Font.GothamBold
bauValue.TextSize = 28
bauValue.Parent = bauFrame

-- Cantos arredondados
for _, f in pairs({babaFrame, bauFrame}) do
    local c = Instance.new("UICorner")
    c.CornerRadius = UDim.new(0, 10)
    c.Parent = f
end

print("✅ GHOTS HUB FARM BAÚ carregado! Avatar e Nick são do jogador atual.")
