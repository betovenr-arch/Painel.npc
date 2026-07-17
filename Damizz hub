-- Serviços do Roblox
local TweenService = game:GetService("TweenService")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

-- Criando a Interface Principal
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "CyberPanelGui"
ScreenGui.Parent = game:GetService("CoreGui") or Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

-- 1. BOTÃO DA LOGO (Direita)
local LogoButton = Instance.new("TextButton")
LogoButton.Name = "LogoButton"
LogoButton.Parent = ScreenGui
LogoButton.AnchorPoint = Vector2.new(1, 0) -- Ancorado no canto superior direito
LogoButton.Position = UDim2.new(1, -15, 0, 15)
LogoButton.Size = UDim2.new(0, 55, 0, 55)
LogoButton.BackgroundColor3 = Color3.fromRGB(15, 15, 22)
LogoButton.BackgroundTransparency = 0.2
LogoButton.Font = Enum.Font.GothamBold
LogoButton.Text = "⚜️"
LogoButton.TextSize = 35
LogoButton.TextColor3 = Color3.fromRGB(200, 200, 200)

local LogoCorner = Instance.new("UICorner")
LogoCorner.CornerRadius = UDim.new(0, 12)
LogoCorner.Parent = LogoButton

local LogoStroke = Instance.new("UIStroke")
LogoStroke.Color = Color3.fromRGB(100, 0, 255)
LogoStroke.Thickness = 3
LogoStroke.Parent = LogoButton

-- 2. PAINEL PRINCIPAL (À esquerda da logo)
local MainPanel = Instance.new("Frame")
MainPanel.Name = "MainPanel"
MainPanel.Parent = ScreenGui
MainPanel.AnchorPoint = Vector2.new(1, 0) -- Ancorado à direita para ficar ao lado da logo
MainPanel.Position = UDim2.new(1, -85, 0, 15)
MainPanel.Size = UDim2.new(0, 240, 0, 200)
MainPanel.BackgroundColor3 = Color3.fromRGB(10, 10, 14)
MainPanel.BackgroundTransparency = 0.1
MainPanel.Visible = false
MainPanel.ClipsDescendants = true

local PanelCorner = Instance.new("UICorner")
PanelCorner.CornerRadius = UDim.new(0, 12)
PanelCorner.Parent = MainPanel

local PanelStroke = Instance.new("UIStroke")
PanelStroke.Color = Color3.fromRGB(0, 180, 255)
PanelStroke.Thickness = 2
PanelStroke.Parent = MainPanel

local PanelTitle = Instance.new("TextLabel")
PanelTitle.Parent = MainPanel
PanelTitle.Size = UDim2.new(1, 0, 0, 40)
PanelTitle.BackgroundTransparency = 1
PanelTitle.Font = Enum.Font.GothamBold
PanelTitle.Text = "⚡CONTROL NPCS⚡"
PanelTitle.TextColor3 = Color3.fromRGB(220, 220, 220)
PanelTitle.TextSize = 16

-- 3. ABAS
local TabBar = Instance.new("Frame")
TabBar.Parent = MainPanel
TabBar.BackgroundTransparency = 1
TabBar.Position = UDim2.new(0, 10, 0, 45)
TabBar.Size = UDim2.new(1, -20, 0, 30)

local function criarTab(nome, pos)
    local btn = Instance.new("TextButton")
    btn.Parent = TabBar
    btn.Size = UDim2.new(0.32, 0, 1, 0)
    btn.Position = pos
    btn.BackgroundColor3 = Color3.fromRGB(15, 15, 20)
    btn.Font = Enum.Font.GothamBold
    btn.Text = nome
    btn.TextColor3 = Color3.fromRGB(130, 130, 130)
    btn.TextSize = 10
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 5)
    return btn
end

local TabNpcs = criarTab("NPCS", UDim2.new(0,0,0,0))
local TabConfig = criarTab("CONFIG", UDim2.new(0.34,0,0,0))
local TabExcluido = criarTab("EXCLUIDO", UDim2.new(0.68,0,0,0))

-- Páginas
local function criarPagina()
    local p = Instance.new("Frame")
    p.Parent = MainPanel
    p.BackgroundTransparency = 1
    p.Position = UDim2.new(0, 10, 0, 85)
    p.Size = UDim2.new(1, -20, 1, -95)
    p.Visible = false
    local layout = Instance.new("UIListLayout")
    layout.Parent = p
    layout.Padding = UDim.new(0, 10)
    layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
    return p
end

local PageNpcs = criarPagina(); PageNpcs.Visible = true
local PageConfig = criarPagina()
local PageExcluido = criarPagina()

-- Lógica de trocar abas
local function mudarAba(ativa)
    PageNpcs.Visible = (ativa == "NPCS")
    PageConfig.Visible = (ativa == "CONFIG")
    PageExcluido.Visible = (ativa == "EXCLUIDO")
    
    TabNpcs.BackgroundColor3 = ativa == "NPCS" and Color3.fromRGB(20, 20, 30) or Color3.fromRGB(15, 15, 20)
    TabConfig.BackgroundColor3 = ativa == "CONFIG" and Color3.fromRGB(20, 20, 30) or Color3.fromRGB(15, 15, 20)
    TabExcluido.BackgroundColor3 = ativa == "EXCLUIDO" and Color3.fromRGB(20, 20, 30) or Color3.fromRGB(15, 15, 20)
end

TabNpcs.MouseButton1Click:Connect(function() mudarAba("NPCS") end)
TabConfig.MouseButton1Click:Connect(function() mudarAba("CONFIG") end)
TabExcluido.MouseButton1Click:Connect(function() mudarAba("EXCLUIDO") end)

-- 4. BOTÕES FUNCIONAIS
local function criarBotao(parent, texto, cor)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(1, 0, 0, 40)
    btn.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
    btn.Text = texto
    btn.TextColor3 = Color3.new(1,1,1)
    btn.Font = Enum.Font.GothamBold
    btn.TextSize = 14
    btn.Parent = parent
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 8)
    local s = Instance.new("UIStroke", btn)
    s.Color = cor
    s.Thickness = 2
    return btn
end

local BtnGirl = criarBotao(PageNpcs, "♀️ GIRL", Color3.fromRGB(230, 90, 160))
local BtnBoy  = criarBotao(PageNpcs, "♂️ BOY", Color3.fromRGB(50, 130, 230))
local BtnControl = criarBotao(PageConfig, "CONTROL", Color3.fromRGB(60, 190, 60))
local BtnDelete  = criarBotao(PageConfig, "DELETE ALL", Color3.fromRGB(200, 40, 60))

-- Botões da Aba EXCLUIDO
local BtnGodMod = criarBotao(PageExcluido, "GOD MOD", Color3.new(1,1,1))
local BtnKeep   = criarBotao(PageExcluido, "KEEP", Color3.fromRGB(255, 165, 0))

RunService.RenderStepped:Connect(function()
    if BtnGodMod and BtnGodMod:FindFirstChild("UIStroke") then
        BtnGodMod.UIStroke.Color = Color3.fromHSV(tick() % 5 / 5, 1, 1)
    end
end)

-- 5. FUNÇÕES DE EXECUÇÃO
BtnGirl.MouseButton1Click:Connect(function() pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/betovenr-arch/Npc-Girl/fb1c61f37a4f047307e747b823754118db463293/Damizz%20hub"))() end) end)
BtnBoy.MouseButton1Click:Connect(function() pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/betovenr-arch/Npc-Boy/refs/heads/main/Damizz%20hub"))() end) end)
BtnControl.MouseButton1Click:Connect(function() pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/randomstring0/qwertys/refs/heads/main/qwerty8.lua"))() end) end)
BtnGodMod.MouseButton1Click:Connect(function() pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/betovenr-arch/God-mod_extrem/refs/heads/main/Damizz%20hub"))() end) end)
BtnKeep.MouseButton1Click:Connect(function() pcall(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/betovenr-arch/Invent-rio/refs/heads/main/Damizz.hub"))() end) end)

BtnDelete.MouseButton1Click:Connect(function()
    local localPlayer = Players.LocalPlayer
    for _, obj in pairs(workspace:GetChildren()) do
        if obj:IsA("Model") and (obj.Name:lower():match("girl") or obj.Name:lower():match("boy") or obj:FindFirstChild("Humanoid")) then
            if obj.Name ~= localPlayer.Name then obj:Destroy() end
        end
    end
end)

-- Animação
local tamanhoOriginal = UDim2.new(0, 240, 0, 200)
local tamanhoFechado = UDim2.new(0, 240, 0, 0)
MainPanel.Size = tamanhoFechado

LogoButton.MouseButton1Click:Connect(function()
    MainPanel.Visible = not MainPanel.Visible
    MainPanel:TweenSize(MainPanel.Visible and tamanhoOriginal or tamanhoFechado, "Out", "Back", 0.3, true)
end)
