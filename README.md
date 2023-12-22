-- Configuration
local KICK_MESSAGE = "You have been kicked from the game."
 
-- Create GUI
local gui = Instance.new("ScreenGui")
gui.Name = "Kick GUI"
 
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 100)
frame.Position = UDim2.new(0.5, -100, 0.5, -50)
frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
frame.BorderSizePixel = 0
frame.Parent = gui
 
local label = Instance.new("TextLabel")
label.Size = UDim2.new(1, 0, 0.5, 0)
label.Position = UDim2.new(0, 0, 0, 0)
label.BackgroundTransparency = 1
label.Font = Enum.Font.SourceSans
label.Text = "Kick a Player"
label.TextColor3 = Color3.fromRGB(0, 0, 0)
label.TextSize = 20
label.Parent = frame
 
local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(1, -20, 0.3, 0)
textBox.Position = UDim2.new(0, 10, 0.5, -20)
textBox.PlaceholderText = "Enter Player Name"
textBox.Font = Enum.Font.SourceSans
textBox.TextColor3 = Color3.fromRGB(0, 0, 0)
textBox.TextSize = 14
textBox.Parent = frame
 
local kickButton = Instance.new("TextButton")
kickButton.Size = UDim2.new(1, -20, 0.2, 0)
kickButton.Position = UDim2.new(0, 10, 0.8, -10)
kickButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
kickButton.BorderSizePixel = 0
kickButton.Font = Enum.Font.SourceSans
kickButton.Text = "Kick Player"
kickButton.TextColor3 = Color3.fromRGB(255, 255, 255)
kickButton.TextSize = 16
kickButton.Parent = frame
 
-- Kick Function
local function KickPlayer(playerName)
    local player = game.Players:FindFirstChild(playerName)
    if player then
        player:Kick(KICK_MESSAGE)
    end
end
 
-- Connect Kick Button to Kick Function
kickButton.MouseButton1Click:Connect(function()
    local playerName = textBox.Text
    KickPlayer(playerName)
end)
 
-- Show GUI
gui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
