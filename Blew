--========================================================
-- 🩸 ROENDAR DEV PANEL
-- Roblox Studio / YOUR OWN EXPERIENCE
-- Place in StarterPlayer > StarterPlayerScripts
--
-- X BUTTON IS UNDER THE MENU
-- 🩸 ICON REOPENS THE MENU
-- SETTINGS REMAIN ACTIVE WHEN MENU IS CLOSED
--========================================================

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UIS = game:GetService("UserInputService")
local Lighting = game:GetService("Lighting")

local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

--========================================================
-- COLORS
--========================================================

local BLACK = Color3.fromRGB(5,5,7)
local DARK = Color3.fromRGB(12,12,16)
local PANEL = Color3.fromRGB(21,21,27)
local RED = Color3.fromRGB(145,15,28)
local RED2 = Color3.fromRGB(210,25,45)
local WHITE = Color3.fromRGB(245,245,245)
local GREY = Color3.fromRGB(145,145,150)
local GREEN = Color3.fromRGB(35,125,65)

--========================================================
-- SETTINGS
--========================================================

local Settings = {

	-- AIM / DEBUG
	AimDebug = false,
	AimFOV = 150,
	AimSmooth = 50,
	AimPart = "Head",
	AimVisibleOnly = true,

	-- ESP / DEBUG VISUALS
	ESPEnabled = false,
	ESPNames = true,
	ESPHealth = false,
	ESPDistance = false,
	ESPHighlight = false,
	ESPTeamCheck = true,
	ESPMaxDistance = 1000,

	-- WEAPON TESTING
	WeaponDebug = false,
	InfiniteAmmo = false,
	InstantReload = false,
	NoRecoil = false,
	NoSpread = false,
	DamageMultiplier = 100,

	-- MOVEMENT
	WalkSpeedEnabled = false,
	WalkSpeed = 16,

	JumpEnabled = false,
	JumpPower = 50,

	GravityEnabled = false,
	Gravity = 196,

	Fly = false,
	NoClip = false,
	InfiniteJump = false,

	Sprint = false,
	SprintSpeed = 32,

	-- WORLD
	Fullbright = false,
	TimeEnabled = false,
	Time = 14,

	FogEnabled = true,
	FogStart = 0,
	FogEnd = 100000,

	CameraFOV = 70,
	ThirdPerson = false,

	-- PLAYER
	ForceField = false,
	AutoRespawn = false,
	RespawnDelay = 1,
	TeleportToSpawn = false,

	-- UI
	FPSCounter = true,
	PingCounter = true,
	DebugStats = false,
	Notifications = true,
	ShowKeybinds = true,
	CompactMode = false,
	MenuScale = 100,
	UITransparency = 0
}

--========================================================
-- GUI
--========================================================

local UI = Instance.new("ScreenGui")
UI.Name = "RoendarDevPanel"
UI.ResetOnSpawn = false
UI.IgnoreGuiInset = true
UI.DisplayOrder = 999
UI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
UI.Parent = PlayerGui

--========================================================
-- MAIN HOLDER
--========================================================

local Holder = Instance.new("Frame")
Holder.Name = "Holder"
Holder.Size = UDim2.fromOffset(600,500)
Holder.Position = UDim2.new(.5,-300,.5,-250)
Holder.BackgroundTransparency = 1
Holder.Parent = UI

--========================================================
-- MAIN MENU
--========================================================

local Main = Instance.new("Frame")
Main.Name = "Main"
Main.Size = UDim2.fromOffset(600,460)
Main.Position = UDim2.fromOffset(0,0)
Main.BackgroundColor3 = BLACK
Main.BorderSizePixel = 0
Main.Active = true
Main.Parent = Holder

Instance.new("UICorner",Main).CornerRadius = UDim.new(0,12)

local MainStroke = Instance.new("UIStroke")
MainStroke.Color = RED
MainStroke.Thickness = 2
MainStroke.Parent = Main

--========================================================
-- HEADER
--========================================================

local Header = Instance.new("Frame")
Header.Size = UDim2.new(1,0,0,42)
Header.BackgroundColor3 = DARK
Header.BorderSizePixel = 0
Header.Active = true
Header.Parent = Main

Instance.new("UICorner",Header).CornerRadius = UDim.new(0,12)

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1,-20,1,0)
Title.Position = UDim2.fromOffset(12,0)
Title.BackgroundTransparency = 1
Title.Text = "🩸 ROENDAR DEV PANEL"
Title.TextColor3 = WHITE
Title.TextSize = 13
Title.Font = Enum.Font.GothamBold
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = Header

--========================================================
-- SIDEBAR
--========================================================

local Sidebar = Instance.new("Frame")
Sidebar.Size = UDim2.fromOffset(115,400)
Sidebar.Position = UDim2.fromOffset(8,50)
Sidebar.BackgroundColor3 = DARK
Sidebar.BorderSizePixel = 0
Sidebar.Parent = Main

Instance.new("UICorner",Sidebar).CornerRadius = UDim.new(0,8)

local SideLayout = Instance.new("UIListLayout")
SideLayout.Padding = UDim.new(0,5)
SideLayout.SortOrder = Enum.SortOrder.LayoutOrder
SideLayout.Parent = Sidebar

local SidePadding = Instance.new("UIPadding")
SidePadding.PaddingTop = UDim.new(0,8)
SidePadding.PaddingLeft = UDim.new(0,7)
SidePadding.PaddingRight = UDim.new(0,7)
SidePadding.Parent = Sidebar

--========================================================
-- CONTENT
--========================================================

local Content = Instance.new("Frame")
Content.Size = UDim2.new(1,-133,1,-58)
Content.Position = UDim2.fromOffset(125,50)
Content.BackgroundColor3 = DARK
Content.BorderSizePixel = 0
Content.Parent = Main

Instance.new("UICorner",Content).CornerRadius = UDim.new(0,8)

--========================================================
-- PAGES
--========================================================

local Pages = {}
local Tabs = {}

local Categories = {
	"AIM",
	"ESP",
	"WEAPON",
	"MOVE",
	"WORLD",
	"PLAYER",
	"UI"
}

local function createPage(name)

	local page = Instance.new("ScrollingFrame")
	page.Name = name
	page.Size = UDim2.new(1,-14,1,-14)
	page.Position = UDim2.fromOffset(7,7)
	page.BackgroundTransparency = 1
	page.BorderSizePixel = 0
	page.ScrollBarThickness = 3
	page.ScrollBarImageColor3 = RED2
	page.AutomaticCanvasSize = Enum.AutomaticSize.Y
	page.CanvasSize = UDim2.new()
	page.Visible = false
	page.Parent = Content

	local layout = Instance.new("UIListLayout")
	layout.Padding = UDim.new(0,6)
	layout.Parent = page

	local padding = Instance.new("UIPadding")
	padding.PaddingBottom = UDim.new(0,10)
	padding.Parent = page

	Pages[name] = page
end

local function createTab(name)

	local button = Instance.new("TextButton")
	button.Size = UDim2.new(1,0,0,30)
	button.BackgroundColor3 = PANEL
	button.BorderSizePixel = 0
	button.Text = name
	button.TextColor3 = GREY
	button.TextSize = 8
	button.Font = Enum.Font.GothamBold
	button.Parent = Sidebar

	Instance.new("UICorner",button).CornerRadius = UDim.new(0,6)

	Tabs[name] = button
end

for _,name in ipairs(Categories) do
	createPage(name)
	createTab(name)
end

local function switchPage(name)

	for n,b in pairs(Tabs) do
		b.BackgroundColor3 = n == name and RED or PANEL
		b.TextColor3 = n == name and WHITE or GREY
	end

	for n,p in pairs(Pages) do
		p.Visible = n == name
	end
end

for _,name in ipairs(Categories) do

	Tabs[name].MouseButton1Click:Connect(function()
		switchPage(name)
	end)

end

--========================================================
-- UI HELPERS
--========================================================

local function Section(page,text)

	local label = Instance.new("TextLabel")
	label.Size = UDim2.new(1,-4,0,22)
	label.BackgroundTransparency = 1
	label.Text = text
	label.TextColor3 = RED2
	label.TextSize = 9
	label.Font = Enum.Font.GothamBold
	label.TextXAlignment = Enum.TextXAlignment.Left
	label.Parent = page

end

local function Toggle(page,text,key,callback)

	local button = Instance.new("TextButton")
	button.Size = UDim2.new(1,-4,0,30)
	button.BackgroundColor3 = Settings[key] and GREEN or PANEL
	button.BorderSizePixel = 0
	button.TextColor3 = Settings[key] and WHITE or GREY
	button.TextSize = 8
	button.Font = Enum.Font.GothamBold
	button.TextXAlignment = Enum.TextXAlignment.Left
	button.Parent = page

	Instance.new("UICorner",button).CornerRadius = UDim.new(0,6)

	local pad = Instance.new("UIPadding")
	pad.PaddingLeft = UDim.new(0,10)
	pad.Parent = button

	local function update()

		button.Text =
			text.."  [ "..(Settings[key] and "ON" or "OFF").." ]"

		button.BackgroundColor3 =
			Settings[key] and GREEN or PANEL

		button.TextColor3 =
			Settings[key] and WHITE or GREY

	end

	update()

	button.MouseButton1Click:Connect(function()

		Settings[key] = not Settings[key]

		update()

		if callback then
			callback(Settings[key])
		end

	end)

end

local function Slider(page,text,key,min,max,step)

	local holder = Instance.new("Frame")
	holder.Size = UDim2.new(1,-4,0,50)
	holder.BackgroundColor3 = PANEL
	holder.BorderSizePixel = 0
	holder.Parent = page

	Instance.new("UICorner",holder).CornerRadius = UDim.new(0,6)

	local label = Instance.new("TextLabel")
	label.Size = UDim2.new(1,-80,0,20)
	label.Position = UDim2.fromOffset(10,3)
	label.BackgroundTransparency = 1
	label.TextColor3 = WHITE
	label.TextSize = 8
	label.Font = Enum.Font.GothamBold
	label.TextXAlignment = Enum.TextXAlignment.Left
	label.Parent = holder

	local minus = Instance.new("TextButton")
	minus.Size = UDim2.fromOffset(30,22)
	minus.Position = UDim2.new(1,-68,0,24)
	minus.BackgroundColor3 = RED
	minus.BorderSizePixel = 0
	minus.Text = "-"
	minus.TextColor3 = WHITE
	minus.Font = Enum.Font.GothamBold
	minus.TextSize = 10
	minus.Parent = holder

	Instance.new("UICorner",minus).CornerRadius = UDim.new(0,5)

	local plus = Instance.new("TextButton")
	plus.Size = UDim2.fromOffset(30,22)
	plus.Position = UDim2.new(1,-34,0,24)
	plus.BackgroundColor3 = RED
	plus.BorderSizePixel = 0
	plus.Text = "+"
	plus.TextColor3 = WHITE
	plus.Font = Enum.Font.GothamBold
	plus.TextSize = 10
	plus.Parent = holder

	Instance.new("UICorner",plus).CornerRadius = UDim.new(0,5)

	local function update()

		label.Text =
			text..": "..tostring(Settings[key])

	end

	update()

	minus.MouseButton1Click:Connect(function()

		Settings[key] = math.clamp(
			Settings[key] - step,
			min,
			max
		)

		update()

	end)

	plus.MouseButton1Click:Connect(function()

		Settings[key] = math.clamp(
			Settings[key] + step,
			min,
			max
		)

		update()

	end)

end

local function Select(page,text,key,options)

	local button = Instance.new("TextButton")
	button.Size = UDim2.new(1,-4,0,30)
	button.BackgroundColor3 = PANEL
	button.BorderSizePixel = 0
	button.TextColor3 = WHITE
	button.TextSize = 8
	button.Font = Enum.Font.GothamBold
	button.TextXAlignment = Enum.TextXAlignment.Left
	button.Parent = page

	Instance.new("UICorner",button).CornerRadius = UDim.new(0,6)

	local index = table.find(options,Settings[key]) or 1

	local function update()

		Settings[key] = options[index]
		button.Text = text..": "..tostring(Settings[key])

	end

	update()

	button.MouseButton1Click:Connect(function()

		index = index % #options + 1
		update()

	end)

end

--========================================================
-- AIM
--========================================================

Section(Pages.AIM,"AIM / TARGET DEBUG")

Toggle(Pages.AIM,"Aim Debug","AimDebug")
Slider(Pages.AIM,"FOV","AimFOV",25,500,25)
Slider(Pages.AIM,"Smoothness","AimSmooth",0,100,5)

Select(
	Pages.AIM,
	"Debug Part",
	"AimPart",
	{
		"Head",
		"UpperTorso",
		"HumanoidRootPart"
	}
)

Toggle(Pages.AIM,"Visible Only","AimVisibleOnly")

--========================================================
-- ESP
--========================================================

Section(Pages.ESP,"PLAYER DEBUG VISUALS")

Toggle(Pages.ESP,"ESP Master","ESPEnabled")
Toggle(Pages.ESP,"Names","ESPNames")
Toggle(Pages.ESP,"Health","ESPHealth")
Toggle(Pages.ESP,"Distance","ESPDistance")
Toggle(Pages.ESP,"Highlights","ESPHighlight")
Toggle(Pages.ESP,"Team Check","ESPTeamCheck")
Slider(Pages.ESP,"Max Distance","ESPMaxDistance",50,3000,50)

--========================================================
-- WEAPON
--========================================================

Section(Pages.WEAPON,"WEAPON TESTING")

Toggle(Pages.WEAPON,"Weapon Debug","WeaponDebug")
Toggle(Pages.WEAPON,"Infinite Ammo","InfiniteAmmo")
Toggle(Pages.WEAPON,"Instant Reload","InstantReload")
Toggle(Pages.WEAPON,"No Recoil","NoRecoil")
Toggle(Pages.WEAPON,"No Spread","NoSpread")
Slider(Pages.WEAPON,"Damage Multiplier","DamageMultiplier",0,300,10)

--========================================================
-- MOVEMENT
--========================================================

Section(Pages.MOVE,"MOVEMENT")

Toggle(Pages.MOVE,"Custom Speed","WalkSpeedEnabled")
Slider(Pages.MOVE,"WalkSpeed","WalkSpeed",1,150,1)

Toggle(Pages.MOVE,"Custom Jump","JumpEnabled")
Slider(Pages.MOVE,"JumpPower","JumpPower",1,200,5)

Toggle(Pages.MOVE,"Custom Gravity","GravityEnabled")
Slider(Pages.MOVE,"Gravity","Gravity",0,500,5)

Toggle(Pages.MOVE,"Fly","Fly")
Toggle(Pages.MOVE,"NoClip","NoClip")
Toggle(Pages.MOVE,"Infinite Jump","InfiniteJump")

Toggle(Pages.MOVE,"Sprint","Sprint")
Slider(Pages.MOVE,"Sprint Speed","SprintSpeed",16,150,2)

--========================================================
-- WORLD
--========================================================

Section(Pages.WORLD,"WORLD / CAMERA")

Toggle(Pages.WORLD,"Fullbright","Fullbright")

Toggle(Pages.WORLD,"Custom Time","TimeEnabled")
Slider(Pages.WORLD,"Time","Time",0,24,1)

Toggle(Pages.WORLD,"Fog","FogEnabled")
Slider(Pages.WORLD,"Fog Start","FogStart",0,100000,1000)
Slider(Pages.WORLD,"Fog End","FogEnd",100,100000,1000)

Slider(Pages.WORLD,"Camera FOV","CameraFOV",40,120,5)

Toggle(Pages.WORLD,"Third Person","ThirdPerson")

--========================================================
-- PLAYER
--========================================================

Section(Pages.PLAYER,"PLAYER / ADMIN")

Toggle(Pages.PLAYER,"Force Field","ForceField")

Toggle(Pages.PLAYER,"Auto Respawn","AutoRespawn")
Slider(Pages.PLAYER,"Respawn Delay","RespawnDelay",0,10,.5)

Toggle(
	Pages.PLAYER,
	"Teleport To Spawn",
	"TeleportToSpawn",
	function(enabled)

		if not enabled then
			return
		end

		local character = LocalPlayer.Character
		if not character then
			return
		end

		local root = character:FindFirstChild("HumanoidRootPart")
		if not root then
			return
		end

		local spawn = workspace:FindFirstChildOfClass("SpawnLocation")

		if spawn then
			root.CFrame = spawn.CFrame + Vector3.new(0,4,0)
		end

	end
)

--========================================================
-- UI
--========================================================

Section(Pages.UI,"INTERFACE")

Toggle(Pages.UI,"FPS Counter","FPSCounter")
Toggle(Pages.UI,"Ping Counter","PingCounter")
Toggle(Pages.UI,"Debug Stats","DebugStats")
Toggle(Pages.UI,"Notifications","Notifications")
Toggle(Pages.UI,"Show Keybinds","ShowKeybinds")
Toggle(Pages.UI,"Compact Mode","CompactMode")

Slider(Pages.UI,"Menu Scale","MenuScale",75,150,5)
Slider(Pages.UI,"Transparency","UITransparency",0,100,5)

--========================================================
-- X BUTTON UNDER MENU
--========================================================

local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.fromOffset(600,34)
CloseButton.Position = UDim2.fromOffset(0,466)
CloseButton.BackgroundColor3 = Color3.fromRGB(55,12,18)
CloseButton.BorderSizePixel = 0
CloseButton.Text = "X   •   CLOSE MENU"
CloseButton.TextColor3 = RED2
CloseButton.TextSize = 10
CloseButton.Font = Enum.Font.GothamBold
CloseButton.Parent = Holder

Instance.new("UICorner",CloseButton).CornerRadius = UDim.new(0,8)

--========================================================
-- REOPEN ICON
--========================================================

local Restore = Instance.new("TextButton")
Restore.Name = "Restore"
Restore.Size = UDim2.fromOffset(54,54)
Restore.Position = UDim2.new(1,-75,1,-75)
Restore.BackgroundColor3 = BLACK
Restore.BorderSizePixel = 0
Restore.Text = "🩸"
Restore.TextColor3 = WHITE
Restore.TextSize = 20
Restore.Font = Enum.Font.GothamBold
Restore.Visible = false
Restore.Active = true
Restore.Parent = UI

Instance.new("UICorner",Restore).CornerRadius = UDim.new(1,0)

local RestoreStroke = Instance.new("UIStroke")
RestoreStroke.Color = RED2
RestoreStroke.Thickness = 2
RestoreStroke.Parent = Restore

--========================================================
-- CLOSE / RESTORE
--========================================================

local function hideMenu()

	-- ONLY GUI IS HIDDEN.
	-- Settings continue running.

	Holder.Visible = false
	Restore.Visible = true

end

local function showMenu()

	Holder.Visible = true
	Restore.Visible = false

end

CloseButton.MouseButton1Click:Connect(hideMenu)

Restore.MouseButton1Click:Connect(showMenu)

UIS.InputBegan:Connect(function(input,gp)

	if gp then
		return
	end

	if input.KeyCode == Enum.KeyCode.RightShift then

		if Holder.Visible then
			hideMenu()
		else
			showMenu()
		end

	end

end)

--========================================================
-- DRAG MAIN MENU
--========================================================

local dragging = false
local dragStart
local startPosition

Header.InputBegan:Connect(function(input)

	if input.UserInputType == Enum.UserInputType.MouseButton1
		or input.UserInputType == Enum.UserInputType.Touch then

		dragging = true
		dragStart = input.Position
		startPosition = Holder.Position

	end

end)

UIS.InputChanged:Connect(function(input)

	if not dragging then
		return
	end

	if input.UserInputType == Enum.UserInputType.MouseMovement
		or input.UserInputType == Enum.UserInputType.Touch then

		local delta = input.Position - dragStart

		Holder.Position = UDim2.new(
			startPosition.X.Scale,
			startPosition.X.Offset + delta.X,
			startPosition.Y.Scale,
			startPosition.Y.Offset + delta.Y
		)

	end

end)

UIS.InputEnded:Connect(function(input)

	if input.UserInputType == Enum.UserInputType.MouseButton1
		or input.UserInputType == Enum.UserInputType.Touch then

		dragging = false

	end

end)

--========================================================
-- MOVEMENT
--========================================================

local function getCharacter()

	return LocalPlayer.Character

end

local function getHumanoid()

	local character = getCharacter()

	if not character then
		return nil
	end

	return character:FindFirstChildOfClass("Humanoid")

end

local function getRoot()

	local character = getCharacter()

	if not character then
		return nil
	end

	return character:FindFirstChild("HumanoidRootPart")

end

--========================================================
-- FLY
--========================================================

local flyConnection

local function setFly(enabled)

	if flyConnection then
		flyConnection:Disconnect()
		flyConnection = nil
	end

	if not enabled then
		return
	end

	flyConnection = RunService.RenderStepped:Connect(function()

		local character = getCharacter()
		local root = getRoot()

		if not character or not root then
			return
		end

		local camera = workspace.CurrentCamera

		local direction = Vector3.zero

		if UIS:IsKeyDown(Enum.KeyCode.W) then
			direction += camera.CFrame.LookVector
		end

		if UIS:IsKeyDown(Enum.KeyCode.S) then
			direction -= camera.CFrame.LookVector
		end

		if UIS:IsKeyDown(Enum.KeyCode.A) then
			direction -= camera.CFrame.RightVector
		end

		if UIS:IsKeyDown(Enum.KeyCode.D) then
			direction += camera.CFrame.RightVector
		end

		if UIS:IsKeyDown(Enum.KeyCode.Space) then
			direction += Vector3.yAxis
		end

		if UIS:IsKeyDown(Enum.KeyCode.LeftControl) then
			direction -= Vector3.yAxis
		end

		if direction.Magnitude > 0 then
			direction = direction.Unit
		end

		root.AssemblyLinearVelocity =
			direction * Settings.SprintSpeed

	end)

end

--========================================================
-- NOCLIP
--========================================================

local function updateNoClip()

	if not Settings.NoClip then
		return
	end

	local character = getCharacter()

	if not character then
		return
	end

	for _,object in ipairs(character:GetDescendants()) do

		if object:IsA("BasePart") then
			object.CanCollide = false
		end

	end

end

--========================================================
-- FORCE FIELD
--========================================================

local function updateForceField()

	local character = getCharacter()

	if not character then
		return
	end

	local existing = character:FindFirstChild("RoendarForceField")

	if Settings.ForceField then

		if not existing then

			local ff = Instance.new("ForceField")
			ff.Name = "RoendarForceField"
			ff.Visible = true
			ff.Parent = character

		end

	else

		if existing then
			existing:Destroy()
		end

	end

end

--========================================================
-- WORLD
--========================================================

local defaultLighting = {
	Brightness = Lighting.Brightness,
	ClockTime = Lighting.ClockTime,
	FogStart = Lighting.FogStart,
	FogEnd = Lighting.FogEnd,
	Ambient = Lighting.Ambient,
	OutdoorAmbient = Lighting.OutdoorAmbient
}

local function updateWorld()

	if Settings.Fullbright then

		Lighting.Brightness = 3
		Lighting.Ambient = Color3.new(1,1,1)
		Lighting.OutdoorAmbient = Color3.new(1,1,1)

	else

		Lighting.Brightness = defaultLighting.Brightness
		Lighting.Ambient = defaultLighting.Ambient
		Lighting.OutdoorAmbient = defaultLighting.OutdoorAmbient

	end

	if Settings.TimeEnabled then
		Lighting.ClockTime = Settings.Time
	else
		Lighting.ClockTime = defaultLighting.ClockTime
	end

	if Settings.FogEnabled then
		Lighting.FogStart = Settings.FogStart
		Lighting.FogEnd = Settings.FogEnd
	else
		Lighting.FogStart = 0
		Lighting.FogEnd = 100000
	end

	local camera = workspace.CurrentCamera

	if camera then

		camera.FieldOfView = Settings.CameraFOV

		if Settings.ThirdPerson then
			LocalPlayer.CameraMode = Enum.CameraMode.Classic
		end

	end

end

--========================================================
-- MOVEMENT LOOP
--========================================================

RunService.Heartbeat:Connect(function()

	local humanoid = getHumanoid()

	if humanoid then

		if Settings.WalkSpeedEnabled then
			humanoid.WalkSpeed = Settings.WalkSpeed
		end

		if Settings.JumpEnabled then
			humanoid.UseJumpPower = true
			humanoid.JumpPower = Settings.JumpPower
		end

		if Settings.Sprint and UIS:IsKeyDown(Enum.KeyCode.LeftShift) then
			humanoid.WalkSpeed = Settings.SprintSpeed
		end

	end

	if Settings.GravityEnabled then
		workspace.Gravity = Settings.Gravity
	end

	if Settings.NoClip then
		updateNoClip()
	end

	if Settings.ForceField then
		updateForceField()
	end

	if Settings.Fly then
		-- fly controller handles movement
	end

	updateWorld()

end)

--========================================================
-- FLY CALLBACK
--========================================================

local oldFly = Settings.Fly

RunService.Heartbeat:Connect(function()

	if Settings.Fly ~= oldFly then

		oldFly = Settings.Fly
		setFly(Settings.Fly)

	end

end)

--========================================================
-- INFINITE JUMP
--========================================================

UIS.JumpRequest:Connect(function()

	if Settings.InfiniteJump then

		local humanoid = getHumanoid()

		if humanoid then
			humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
		end

	end

end)

--========================================================
-- RESPAWN SETTINGS
--========================================================

LocalPlayer.CharacterAdded:Connect(function(character)

	task.wait(.2)

	if Settings.ForceField then
		updateForceField()
	end

	local humanoid = character:FindFirstChildOfClass("Humanoid")

	if humanoid then

		if Settings.WalkSpeedEnabled then
			humanoid.WalkSpeed = Settings.WalkSpeed
		end

		if Settings.JumpEnabled then
			humanoid.UseJumpPower = true
			humanoid.JumpPower = Settings.JumpPower
		end

	end

end)

--========================================================
-- START
--========================================================

switchPage("AIM")

Main.Visible = true
CloseButton.Visible = true
Restore.Visible = false

print("🩸 ROENDAR DEV PANEL LOADED")
print("RightShift = Toggle Menu")
print("X underneath menu = Close")
print("🩸 icon = Reopen")
