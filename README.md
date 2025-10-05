--// Slayer Online GUI
local player = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.Name = "SlayerOnlineGUI"
gui.ResetOnSpawn = false

--// Main Frame
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 600, 0, 350)
mainFrame.Position = UDim2.new(0.5, -300, 0.5, -175)
mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
mainFrame.BorderColor3 = Color3.fromRGB(100, 100, 100)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = gui

local uiCornerMain = Instance.new("UICorner", mainFrame)
uiCornerMain.CornerRadius = UDim.new(0, 10)

--// Title Bar
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
title.BorderColor3 = Color3.fromRGB(100, 100, 100)
title.Text = "Slayer Online"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.GothamBold
title.TextSize = 20
title.Parent = mainFrame

local uiCornerTitle = Instance.new("UICorner", title)
uiCornerTitle.CornerRadius = UDim.new(0, 10)

--// Left Scrolling Frame (Categorias)
local leftFrame = Instance.new("ScrollingFrame")
leftFrame.Size = UDim2.new(0.45, -10, 1, -50)
leftFrame.Position = UDim2.new(0, 10, 0, 50)
leftFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
leftFrame.BorderColor3 = Color3.fromRGB(80, 80, 80)
leftFrame.ScrollBarThickness = 6
leftFrame.CanvasSize = UDim2.new(0, 0, 2, 0)
leftFrame.Parent = mainFrame

local uiCornerLeft = Instance.new("UICorner", leftFrame)
uiCornerLeft.CornerRadius = UDim.new(0, 10)

local listLeft = Instance.new("UIListLayout", leftFrame)
listLeft.Padding = UDim.new(0, 8)
listLeft.FillDirection = Enum.FillDirection.Vertical
listLeft.HorizontalAlignment = Enum.HorizontalAlignment.Center
listLeft.SortOrder = Enum.SortOrder.LayoutOrder

-- Função para criar botões na esquerda
local function createLeftButton(name)
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(0.9, 0, 0, 40)
	btn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	btn.TextColor3 = Color3.fromRGB(255, 255, 255)
	btn.Text = name
	btn.Font = Enum.Font.Gotham
	btn.TextSize = 16
	btn.BorderSizePixel = 0
	btn.AutoButtonColor = true

	local corner = Instance.new("UICorner", btn)
	corner.CornerRadius = UDim.new(0, 8)

	btn.MouseEnter:Connect(function()
		btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	end)
	btn.MouseLeave:Connect(function()
		btn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	end)

	btn.Parent = leftFrame
	return btn
end

-- Botões principais
local farmBtn = createLeftButton("Farming Level")
local killBtn = createLeftButton("Kill Aura")
local collectBtn = createLeftButton("Auto Collect")

--// Right Scrolling Frame (Ações)
local rightFrame = Instance.new("ScrollingFrame")
rightFrame.Size = UDim2.new(0.45, -10, 1, -50)
rightFrame.Position = UDim2.new(0.55, 0, 0, 50)
rightFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
rightFrame.BorderColor3 = Color3.fromRGB(80, 80, 80)
rightFrame.ScrollBarThickness = 6
rightFrame.CanvasSize = UDim2.new(0, 0, 2, 0)
rightFrame.Parent = mainFrame

local uiCornerRight = Instance.new("UICorner", rightFrame)
uiCornerRight.CornerRadius = UDim.new(0, 10)

local listRight = Instance.new("UIListLayout", rightFrame)
listRight.Padding = UDim.new(0, 8)
listRight.FillDirection = Enum.FillDirection.Vertical
listRight.HorizontalAlignment = Enum.HorizontalAlignment.Center
listRight.SortOrder = Enum.SortOrder.LayoutOrder

-- Função para criar botões de ação
local function createActionButton(name, debugText)
	local btn = Instance.new("TextButton")
	btn.Size = UDim2.new(0.9, 0, 0, 40)
	btn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	btn.TextColor3 = Color3.fromRGB(255, 255, 255)
	btn.Text = name
	btn.Font = Enum.Font.Gotham
	btn.TextSize = 16
	btn.BorderSizePixel = 0
	btn.AutoButtonColor = true

	local corner = Instance.new("UICorner", btn)
	corner.CornerRadius = UDim.new(0, 8)

	btn.MouseEnter:Connect(function()
		btn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
	end)
	btn.MouseLeave:Connect(function()
		btn.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	end)

	btn.MouseButton1Click:Connect(function()
		print(debugText)
	end)

	btn.Parent = rightFrame
end

-- Botões de ações (debug)
createActionButton("Ativar Farming", "Farming Level ativado")
createActionButton("Configurar Dano", "Kill Aura configurada")
createActionButton("Coletar Itens", "Auto Collect iniciado")

print("✅ Slayer Online GUI carregada com sucesso!")
