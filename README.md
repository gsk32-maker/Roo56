--[==[
    Map: BlockSpin
    Script Created by: A_1g
]==]

local player = game.Players.LocalPlayer
local runService = game:GetService("RunService")

-- إشعار الترحيب بالحقوق
pcall(function()
    game:GetService("StarterGui"):SetCore("SendNotification", {
        Title = "BlockSpin Script",
        Text = "تم تفعيل السكربت بنجاح - حقوق: A_1g",
        Duration = 5
    })
end)

-- إنشاء الواجهة (GUI)
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local TitleLabel = Instance.new("TextLabel")
local FarmButton = Instance.new("TextButton")
local ButtonCorner = Instance.new("UICorner")

-- حماية الواجهة لكي تظهر داخل المنفذ
if syn and syn.protect_gui then
    syn.protect_gui(ScreenGui)
    ScreenGui.Parent = game.CoreGui
elseif gethui then
    ScreenGui.Parent = gethui()
else
    ScreenGui.Parent = game.CoreGui
end

MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
MainFrame.Position = UDim2.new(0.5, -110, 0.4, -75)
MainFrame.Size = UDim2.new(0, 220, 0, 140)
MainFrame.Active = true
MainFrame.Draggable = true

TitleLabel.Name = "TitleLabel"
TitleLabel.Parent = MainFrame
TitleLabel.BackgroundTransparency = 1
TitleLabel.Size = UDim2.new(1, 0, 0, 40)
TitleLabel.Font = Enum.Font.GothamBold
TitleLabel.Text = "BlockSpin | A_1g"
TitleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TitleLabel.TextSize = 16

FarmButton.Name = "FarmButton"
FarmButton.Parent = MainFrame
FarmButton.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
FarmButton.Position = UDim2.new(0.1, 0, 0.45, 0)
FarmButton.Size = UDim2.new(0, 176, 0, 50)
FarmButton.Font = Enum.Font.GothamBold
FarmButton.Text = "Auto Farm: OFF"
FarmButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FarmButton.TextSize = 14

ButtonCorner.CornerRadius = UDim.new(0, 8)
ButtonCorner.Parent = FarmButton

-- متغيرات الفارم
local farming = false

-- زر التفعيل والتعطيل
FarmButton.MouseButton1Click:Connect(function()
    farming = not farming
    if farming then
        FarmButton.Text = "Auto Farm: ON"
        FarmButton.BackgroundColor3 = Color3.fromRGB(50, 200, 50)
    else
        FarmButton.Text = "Auto Farm: OFF"
        FarmButton.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
    end
end)

-- حلقة التشغيل
runService.RenderStepped:Connect(function()
    if farming then
        pcall(function()
            -- كود الفارم الخاص بك هنا
        end)
    end
end)
