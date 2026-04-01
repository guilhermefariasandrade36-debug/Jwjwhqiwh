local player = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local gui = Instance.new("ScreenGui", game.CoreGui)

--------------------------------------------------
-- BOTÃO ABRIR
--------------------------------------------------

local open = Instance.new("TextButton", gui)
open.Size = UDim2.new(0,60,0,60)
open.Position = UDim2.new(0,100,0,200)
open.Text = "XIT"
open.BackgroundColor3 = Color3.fromRGB(0,255,0)
open.TextColor3 = Color3.new(0,0,0)
open.Active = true
open.Draggable = true
Instance.new("UICorner", open)

--------------------------------------------------
-- MENU
--------------------------------------------------

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0,300,0,300)
frame.Position = UDim2.new(0.5,-150,0.5,-150)
frame.BackgroundColor3 = Color3.fromRGB(20,20,20)
frame.Visible = false
frame.Active = true
frame.Draggable = true
Instance.new("UICorner", frame)

--------------------------------------------------
-- TÍTULO
--------------------------------------------------

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,40)
title.Text = "SCRIPT XIT 🔥"
title.TextColor3 = Color3.fromRGB(0,255,0)
title.BackgroundTransparency = 1
title.TextScaled = true

--------------------------------------------------
-- SPEED
--------------------------------------------------

local speedLabel = Instance.new("TextLabel", frame)
speedLabel.Position = UDim2.new(0,10,0,60)
speedLabel.Size = UDim2.new(0,120,0,30)
speedLabel.Text = "Speed:"
speedLabel.TextColor3 = Color3.fromRGB(0,255,0)
speedLabel.BackgroundTransparency = 1

local speedBox = Instance.new("TextBox", frame)
speedBox.Position = UDim2.new(0,140,0,60)
speedBox.Size = UDim2.new(0,60,0,30)
speedBox.Text = "16"
speedBox.BackgroundColor3 = Color3.fromRGB(0,0,0)
speedBox.TextColor3 = Color3.fromRGB(0,255,0)

--------------------------------------------------
-- BOTÃO SPEED
--------------------------------------------------

local speedBtn = Instance.new("TextButton", frame)
speedBtn.Position = UDim2.new(0.5,-75,0,100)
speedBtn.Size = UDim2.new(0,150,0,35)
speedBtn.Text = "APLICAR SPEED"
speedBtn.BackgroundColor3 = Color3.fromRGB(0,255,0)

--------------------------------------------------
-- NOCLIP
--------------------------------------------------

local noclip = false

local noclipBtn = Instance.new("TextButton", frame)
noclipBtn.Position = UDim2.new(0.5,-75,0,150)
noclipBtn.Size = UDim2.new(0,150,0,35)
noclipBtn.Text = "NOCLIP OFF"
noclipBtn.BackgroundColor3 = Color3.fromRGB(0,255,0)

--------------------------------------------------
-- FUNÇÃO SPEED (SEM BUG)
--------------------------------------------------

speedBtn.MouseButton1Click:Connect(function()
	local num = tonumber(speedBox.Text)
	
	if num and player.Character and player.Character:FindFirstChild("Humanoid") then
		player.Character.Humanoid.WalkSpeed = num
	end
end)

--------------------------------------------------
-- FUNÇÃO NOCLIP
--------------------------------------------------

noclipBtn.MouseButton1Click:Connect(function()
	noclip = not noclip
	noclipBtn.Text = noclip and "NOCLIP ON" or "NOCLIP OFF"
end)

RunService.Stepped:Connect(function()
	if noclip and player.Character then
		for _,v in ipairs(player.Character:GetDescendants()) do
			if v:IsA("BasePart") then
				v.CanCollide = false
			end
		end
	end
end)

--------------------------------------------------
-- ABRIR / FECHAR
--------------------------------------------------

open.MouseButton1Click:Connect(function()
	frame.Visible = not frame.Visible
end)# Jwjwhqiwh
