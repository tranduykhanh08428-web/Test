local vu32 = {}

function vu32:MakeWindow(Config)

local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local UIS = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

if CoreGui:FindFirstChild("HYSR0_PerfectNeon") then
CoreGui.HYSR0_PerfectNeon:Destroy()
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "HYSR0_PerfectNeon"
ScreenGui.Parent = CoreGui
ScreenGui.ResetOnSpawn = false

---

-- UI CORE

local OuterFrame = Instance.new("Frame")
OuterFrame.Size = UDim2.new(0,760,0,480)
OuterFrame.Position = UDim2.new(0.5,-380,0.5,-240)
OuterFrame.BackgroundTransparency = 1
OuterFrame.Parent = ScreenGui

local OuterStroke = Instance.new("UIStroke")
OuterStroke.Thickness = 4
OuterStroke.Color = Color3.fromRGB(255,255,255)
OuterStroke.Transparency = 0.8
OuterStroke.Parent = OuterFrame

Instance.new("UICorner",OuterFrame).CornerRadius = UDim.new(0,15)

---

-- TITLE

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1,0,0,40)
Title.Position = UDim2.new(0,0,0,5)
Title.BackgroundTransparency = 1
Title.Font = Enum.Font.GothamBold
Title.TextSize = 24
Title.RichText = true
Title.Text = Config.Title or "HYSR0 HUD - Blox Fruit"
Title.Parent = OuterFrame

---

-- MAIN BODY

local MainBody = Instance.new("Frame")
MainBody.Size = UDim2.new(1,-20,1,-60)
MainBody.Position = UDim2.new(0,10,0,50)
MainBody.BackgroundColor3 = Color3.fromRGB(12,12,12)
MainBody.BackgroundTransparency = 0.3
MainBody.BorderSizePixel = 0
MainBody.Parent = OuterFrame

Instance.new("UICorner",MainBody).CornerRadius = UDim.new(0,10)

---

-- SIDEBAR

local Sidebar = Instance.new("Frame")
Sidebar.Size = UDim2.new(0,210,1,-10)
Sidebar.Position = UDim2.new(0,5,0,5)
Sidebar.BackgroundTransparency = 1
Sidebar.Parent = MainBody

local CurrentTabHeader = Instance.new("TextLabel")
CurrentTabHeader.Size = UDim2.new(1,-10,0,30)
CurrentTabHeader.Position = UDim2.new(0,10,0,0)
CurrentTabHeader.BackgroundTransparency = 1
CurrentTabHeader.Font = Enum.Font.GothamBold
CurrentTabHeader.TextSize = 20
CurrentTabHeader.TextColor3 = Color3.fromRGB(255,255,255)
CurrentTabHeader.Text = "Home"
CurrentTabHeader.TextXAlignment = Enum.TextXAlignment.Left
CurrentTabHeader.Parent = Sidebar

local TabList = Instance.new("ScrollingFrame")
TabList.Size = UDim2.new(1,-5,1,-35)
TabList.Position = UDim2.new(0,5,0,35)
TabList.BackgroundTransparency = 1
TabList.BorderSizePixel = 0
TabList.ScrollBarThickness = 2
TabList.CanvasSize = UDim2.new(0,0,0,0)
TabList.AutomaticCanvasSize = Enum.AutomaticSize.Y
TabList.Parent = Sidebar

local TabListLayout = Instance.new("UIListLayout")
TabListLayout.Padding = UDim.new(0,6)
TabListLayout.Parent = TabList

---

-- RIGHT PANEL

local RightPanel = Instance.new("Frame")
RightPanel.Size = UDim2.new(1,-225,1,-10)
RightPanel.Position = UDim2.new(0,220,0,5)
RightPanel.BackgroundTransparency = 1
RightPanel.Parent = MainBody

local ContentTitle = Instance.new("Frame")
ContentTitle.Size = UDim2.new(1,0,0,40)
ContentTitle.BackgroundColor3 = Color3.fromRGB(255,255,255)
ContentTitle.BackgroundTransparency = 0.95
ContentTitle.Parent = RightPanel

Instance.new("UICorner",ContentTitle).CornerRadius = UDim.new(0,6)

local ContentTitleText = Instance.new("TextLabel")
ContentTitleText.Size = UDim2.new(1,0,1,0)
ContentTitleText.BackgroundTransparency = 1
ContentTitleText.Font = Enum.Font.GothamSemibold
ContentTitleText.TextSize = 20
ContentTitleText.TextColor3 = Color3.fromRGB(230,230,230)
ContentTitleText.Text = "Welcome"
ContentTitleText.Parent = ContentTitle

local PageContainer = Instance.new("ScrollingFrame")
PageContainer.Size = UDim2.new(1,0,1,-45)
PageContainer.Position = UDim2.new(0,0,0,45)
PageContainer.BackgroundTransparency = 1
PageContainer.BorderSizePixel = 0
PageContainer.ScrollBarThickness = 2
PageContainer.CanvasSize = UDim2.new(0,0,0,0)
PageContainer.AutomaticCanvasSize = Enum.AutomaticSize.Y
PageContainer.Parent = RightPanel

---

-- LIBRARY

local Lib = {}
local FirstTab = true

function Lib:MakeTab(Config)

local Name = Config[1]

local TabBtn = Instance.new("TextButton")
TabBtn.Size = UDim2.new(1,-10,0,40)
TabBtn.BackgroundTransparency = 1
TabBtn.Text = "  "..Name
TabBtn.TextColor3 = Color3.fromRGB(180,180,180)
TabBtn.Font = Enum.Font.GothamSemibold
TabBtn.TextSize = 18
TabBtn.TextXAlignment = Enum.TextXAlignment.Left
TabBtn.Parent = TabList

local Page = Instance.new("ScrollingFrame")
Page.Size = UDim2.new(1,0,1,0)
Page.BackgroundTransparency = 1
Page.Visible = false
Page.ScrollBarThickness = 0
Page.CanvasSize = UDim2.new(0,0,0,0)
Page.AutomaticCanvasSize = Enum.AutomaticSize.Y
Page.Parent = PageContainer

local PageLayout = Instance.new("UIListLayout")
PageLayout.Padding = UDim.new(0,10)
PageLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
PageLayout.Parent = Page

TabBtn.MouseButton1Click:Connect(function()

for _,v in pairs(PageContainer:GetChildren()) do
if v:IsA("ScrollingFrame") then
v.Visible=false
end
end

Page.Visible=true
ContentTitleText.Text="Module: "..Name
CurrentTabHeader.Text=Name

end)

if FirstTab then
FirstTab=false
Page.Visible=true
ContentTitleText.Text="Module: "..Name
CurrentTabHeader.Text=Name
end

return Page

end

function Lib:AddMinimizeButton() end

return Lib

end

return vu32startPos.X.Scale,
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
