--// RBH WHITE FLUENT KEY SYSTEM (EXPLOIT)

local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")

-- CONFIG
local CORRECT_KEY = "RBH-FreeKey-broockhaven-9A3F1C8E2-5D4B-49A7-B2E1-KP7M_2025-V1945.1000"
local DISCORD_KEY_LINK = "https://discord.gg/ffuFGauPdS"
local CLICK_SOUND_ID = "rbxassetid://71294801358152"

-- CLEAN OLD GUI
pcall(function()
    if CoreGui:FindFirstChild("RBH_KeySystem") then
        CoreGui.RBH_KeySystem:Destroy()
    end
end)

-- GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "RBH_KeySystem"
ScreenGui.IgnoreGuiInset = true
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = CoreGui

-- SHADOW
local Shadow = Instance.new("ImageLabel")
Shadow.Size = UDim2.new(0, 460, 0, 320)
Shadow.Position = UDim2.new(0.5, -230, 0.5, -160)
Shadow.BackgroundTransparency = 1
Shadow.Image = "rbxassetid://1316045217"
Shadow.ImageTransparency = 0.6
Shadow.Parent = ScreenGui

-- MAIN FRAME
local Main = Instance.new("Frame")
Main.Size = UDim2.new(0, 440, 0, 300)
Main.Position = UDim2.new(0.5, -220, 0.5, -150)
Main.BackgroundColor3 = Color3.fromRGB(255,255,255)
Main.BackgroundTransparency = 0.15
Main.BorderSizePixel = 0
Main.Parent = ScreenGui
Instance.new("UICorner", Main).CornerRadius = UDim.new(0,16)

-- TITLE
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1,0,0,45)
Title.BackgroundTransparency = 1
Title.Text = "RBH Key System"
Title.Font = Enum.Font.GothamBold
Title.TextSize = 24
Title.TextColor3 = Color3.fromRGB(20,20,20)
Title.Parent = Main

-- WARNING
local Warning = Instance.new("TextLabel")
Warning.Size = UDim2.new(0.9,0,0,45)
Warning.Position = UDim2.new(0.05,0,0.18,0)
Warning.BackgroundTransparency = 1
Warning.TextWrapped = true
Warning.Text = "WARNING: When the main script loads, the game may freeze for a few seconds. This is normal and it will stabilize shortly."
Warning.Font = Enum.Font.Gotham
Warning.TextSize = 14
Warning.TextColor3 = Color3.fromRGB(200,0,0)
Warning.Parent = Main

-- KEY BOX
local KeyBox = Instance.new("TextBox")
KeyBox.Size = UDim2.new(0.9,0,0,40)
KeyBox.Position = UDim2.new(0.05,0,0.45,0)
KeyBox.BackgroundColor3 = Color3.fromRGB(245,245,245)
KeyBox.TextColor3 = Color3.fromRGB(20,20,20)
KeyBox.PlaceholderText = "Enter your key here"
KeyBox.ClearTextOnFocus = false
KeyBox.Font = Enum.Font.Gotham
KeyBox.TextSize = 18
KeyBox.Parent = Main
Instance.new("UICorner", KeyBox).CornerRadius = UDim.new(0,10)

-- CLICK SOUND
local function playClick()
    local s = Instance.new("Sound")
    s.SoundId = CLICK_SOUND_ID
    s.Volume = 2
    s.Parent = CoreGui
    s:Play()
    task.delay(2, function() s:Destroy() end)
end

-- VERIFY BUTTON
local Verify = Instance.new("TextButton")
Verify.Size = UDim2.new(0.42,0,0,40)
Verify.Position = UDim2.new(0.05,0,0.65,0)
Verify.BackgroundColor3 = Color3.fromRGB(220,0,0)
Verify.Text = "VERIFY KEY"
Verify.Font = Enum.Font.GothamBold
Verify.TextSize = 18
Verify.TextColor3 = Color3.new(1,1,1)
Verify.Parent = Main
Instance.new("UICorner", Verify).CornerRadius = UDim.new(0,10)

-- GET KEY BUTTON
local GetKey = Instance.new("TextButton")
GetKey.Size = UDim2.new(0.42,0,0,40)
GetKey.Position = UDim2.new(0.53,0,0.65,0)
GetKey.BackgroundColor3 = Color3.fromRGB(30,30,30)
GetKey.Text = "GET KEY"
GetKey.Font = Enum.Font.GothamBold
GetKey.TextSize = 18
GetKey.TextColor3 = Color3.new(1,1,1)
GetKey.Parent = Main
Instance.new("UICorner", GetKey).CornerRadius = UDim.new(0,10)

-- STATUS
local Status = Instance.new("TextLabel")
Status.Size = UDim2.new(1,0,0,30)
Status.Position = UDim2.new(0,0,0.85,0)
Status.BackgroundTransparency = 1
Status.Text = ""
Status.Font = Enum.Font.Gotham
Status.TextSize = 16
Status.TextColor3 = Color3.fromRGB(20,20,20)
Status.Parent = Main

-- LOGIC
Verify.MouseButton1Click:Connect(function()
    playClick()
    if KeyBox.Text == CORRECT_KEY then
        Status.Text = "Key accepted. Loading script..."
        task.wait(0.6)
        ScreenGui:Destroy()

        -- EXECUÇÃO CORRETA DO SCRIPT PRINCIPAL
        loadstring(game:HttpGet("https://raw.githubusercontent.com/THEMRREDBLACK/RED-BLACK-HUB-BROOCKHAVEN-V5/refs/heads/main/obfuscated_script-1766958566349.lua.txt"))()
    else
        Status.Text = "Invalid key. Get it on Discord."
    end
end)

GetKey.MouseButton1Click:Connect(function()
    playClick()
    pcall(function()
        setclipboard(DISCORD_KEY_LINK)
    end)
    Status.Text = "Discord link copied to clipboard."
end)
