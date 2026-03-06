local vu32 = {}

function vu32:MakeWindow(config)

local CoreGui = game:GetService("CoreGui")
local UIS = game:GetService("UserInputService")

if CoreGui:FindFirstChild("HYSR0_PerfectNeon") then
CoreGui.HYSR0_PerfectNeon:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "HYSR0_PerfectNeon"
ScreenGui.Parent = CoreGui
ScreenGui.ResetOnSpawn = false

local OuterFrame = Instance.new("Frame")
OuterFrame.Size = UDim2.new(0,760,0,480)
OuterFrame.Position = UDim2.new(0.5,-380,0.5,-240)
OuterFrame.BackgroundColor3 = Color3.fromRGB(10,10,10)
OuterFrame.Parent = ScreenGui
OuterFrame.Active = true

Instance.new("UICorner",OuterFrame).CornerRadius = UDim.new(0,10)

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1,0,0,40)
Title.BackgroundTransparency = 1
Title.Font = Enum.Font.GothamBold
Title.TextSize = 24
Title.TextColor3 = Color3.fromRGB(255,255,255)
Title.Text = config.Title
Title.Parent = OuterFrame

local MainBody = Instance.new("Frame")
MainBody.Size = UDim2.new(1,-20,1,-50)
MainBody.Position = UDim2.new(0,10,0,40)
MainBody.BackgroundColor3 = Color3.fromRGB(20,20,20)
MainBody.Parent = OuterFrame

Instance.new("UICorner",MainBody).CornerRadius = UDim.new(0,8)

local Sidebar = Instance.new("Frame")
Sidebar.Size = UDim2.new(0,200,1,0)
Sidebar.BackgroundTransparency = 1
Sidebar.Parent = MainBody

local TabList = Instance.new("ScrollingFrame")
TabList.Size = UDim2.new(1,0,1,0)
TabList.BackgroundTransparency = 1
TabList.BorderSizePixel = 0
TabList.ScrollBarThickness = 2
TabList.Parent = Sidebar

local TabLayout = Instance.new("UIListLayout")
TabLayout.Padding = UDim.new(0,5)
TabLayout.Parent = TabList

local RightPanel = Instance.new("Frame")
RightPanel.Size = UDim2.new(1,-210,1,0)
RightPanel.Position = UDim2.new(0,210,0,0)
RightPanel.BackgroundTransparency = 1
RightPanel.Parent = MainBody

local PageContainer = Instance.new("Frame")
PageContainer.Size = UDim2.new(1,0,1,0)
PageContainer.BackgroundTransparency = 1
PageContainer.Parent = RightPanel

---

-- DRAG MENU

local dragging = false
local dragStart
local startPos

OuterFrame.InputBegan:Connect(function(input)
if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
dragging = true
dragStart = input.Position
startPos = OuterFrame.Position
end
end)

UIS.InputChanged:Connect(function(input)

if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then

local delta = input.Position - dragStart

OuterFrame.Position = UDim2.new(
startPos.X.Scale,
startPos.X.Offset + delta.X,
startPos.Y.Scale,
startPos.Y.Offset + delta.Y)

end

end)

UIS.InputEnded:Connect(function(input)

if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
dragging = false
end

end)

---

-- WINDOW FUNCTIONS

local window = {}

function window:AddMinimizeButton(cfg)

local Button = Instance.new("ImageButton")
Button.Size = cfg.Size
Button.Position = UDim2.new(0,10,1,-45)
Button.BackgroundColor3 = cfg.Button.BackgroundColor3
Button.BackgroundTransparency = cfg.Button.BackgroundTransparency
Button.Parent = ScreenGui

Instance.new("UICorner",Button).CornerRadius = cfg.Corner.CornerRadius

local open = true

Button.MouseButton1Click:Connect(function()

open = not open
OuterFrame.Visible = open

end)

end

function window:MakeTab(tab)

local Name = tab[1]

local TabBtn = Instance.new("TextButton")
TabBtn.Size = UDim2.new(1,-10,0,40)
TabBtn.Text = Name
TabBtn.Font = Enum.Font.GothamSemibold
TabBtn.TextSize = 18
TabBtn.BackgroundTransparency = 1
TabBtn.TextColor3 = Color3.fromRGB(200,200,200)
TabBtn.Parent = TabList

local Page = Instance.new("Frame")
Page.Size = UDim2.new(1,0,1,0)
Page.BackgroundTransparency = 1
Page.Visible = false
Page.Parent = PageContainer

TabBtn.MouseButton1Click:Connect(function()

for _,v in pairs(PageContainer:GetChildren()) do
if v:IsA("Frame") then
v.Visible=false
end
end

Page.Visible=true

end)

return Page

end

return window

end

return vu32
