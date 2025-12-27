--========================
-- TODDY HUB AIMBOT (FIX REAL)
--========================

local KEY = "Toddyhubactive"

-- SERVICES
local Players = game:GetService("Players")
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local Camera = workspace.CurrentCamera
local LocalPlayer = Players.LocalPlayer

--========================
-- CONFIG
--========================
local aimbot = false
local FOV = 150
local DrawingSupported = (Drawing ~= nil)

--========================
-- GUI
--========================
local gui = Instance.new("ScreenGui")
gui.ResetOnSpawn = false
gui.Parent = LocalPlayer:WaitForChild("PlayerGui")

--========================
-- EXECUTED TEXT
--========================
local exec = Instance.new("TextLabel", gui)
exec.Size = UDim2.new(1,0,0.2,0)
exec.Position = UDim2.new(0,0,0.4,0)
exec.BackgroundTransparency = 1
exec.Text = "Your Toddy Hub is executed."
exec.TextColor3 = Color3.fromRGB(255,0,0)
exec.Font = Enum.Font.GothamBlack
exec.TextScaled = true

task.delay(2,function() exec:Destroy() end)

--========================
-- KEY FRAME
--========================
local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0,300,0,160)
frame.Position = UDim2.fromScale(0.5,0.5)
frame.AnchorPoint = Vector2.new(0.5,0.5)
frame.BackgroundColor3 = Color3.fromRGB(15,15,15)
Instance.new("UICorner", frame)

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,35)
title.BackgroundTransparency = 1
title.Text = "🔐 TODDY HUB"
title.TextColor3 = Color3.fromRGB(255,0,0)
title.Font = Enum.Font.GothamBold
title.TextSize = 18

local box = Instance.new("TextBox", frame)
box.Size = UDim2.new(0.9,0,0,35)
box.Position = UDim2.new(0.05,0,0.4,0)
box.PlaceholderText = "Digite a key"
box.BackgroundColor3 = Color3.fromRGB(25,25,25)
box.TextColor3 = Color3.new(1,1,1)
box.BorderSizePixel = 0
Instance.new("UICorner", box)

local btn = Instance.new("TextButton", frame)
btn.Size = UDim2.new(0.9,0,0,35)
btn.Position = UDim2.new(0.05,0,0.7,0)
btn.Text = "CONFIRMAR"
btn.BackgroundColor3 = Color3.fromRGB(255,0,0)
btn.TextColor3 = Color3.new(1,1,1)
btn.BorderSizePixel = 0
Instance.new("UICorner", btn)

--========================
-- TOGGLE
--========================
local toggle = Instance.new("TextButton", gui)
toggle.Size = UDim2.new(0,200,0,40)
toggle.Position = UDim2.new(0.02,0,0.5,0)
toggle.Text = "AIMBOT: OFF"
toggle.Visible = false
toggle.BackgroundColor3 = Color3.fromRGB(15,15,15)
toggle.TextColor3 = Color3.fromRGB(255,0,0)
Instance.new("UICorner", toggle)

toggle.MouseButton1Click:Connect(function()
	if not DrawingSupported then
		toggle.Text = "EXECUTOR NÃO SUPORTA"
		return
	end
	aimbot = not aimbot
	toggle.Text = aimbot and "AIMBOT: ON" or "AIMBOT: OFF"
end)

--========================
-- KEY CHECK (GARANTIDO)
--========================
btn.MouseButton1Click:Connect(function()
	if box.Text:gsub("%s+","") == KEY then
		frame:Destroy()
		toggle.Visible = true
	else
		btn.Text = "KEY ERRADA ❌"
		task.wait(1)
		btn.Text = "CONFIRMAR"
	end
end)
