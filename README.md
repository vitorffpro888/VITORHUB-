
local VITOR_HUB = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local AutoFarmButton = Instance.new("TextButton")

VITOR_HUB.Name = "VITOR_HUB"
VITOR_HUB.Parent = game.CoreGui

MainFrame.Name = "MainFrame"
MainFrame.Parent = VITOR_HUB
MainFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
MainFrame.Position = UDim2.new(0.5, -100, 0.5, -50)
MainFrame.Size = UDim2.new(0, 200, 0, 150)

Title.Name = "vitor hub"
Title.Parent = MainFrame
Title.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Title.Size = UDim2.new(1, 0, 0.2, 0)
Title.Font = Enum.Font.SourceSans
Title.Text = "VITOR HUB"
Title.TextColor3 = Color3.fromRGB(0, 0, 0)
Title.TextScaled = true

AutoFarmButton.Name = "farm level"
AutoFarmButton.Parent = MainFrame
AutoFarmButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
AutoFarmButton.Position = UDim2.new(0.1, 0, 0.3, 0)
AutoFarmButton.Size = UDim2.new(0.8, 0, 0.2, 0)
AutoFarmButton.Font = Enum.Font.SourceSans
AutoFarmButton.Text = "Auto Farm"
AutoFarmButton.TextColor3 = Color3.fromRGB(0, 0, 0)
AutoFarmButton.TextScaled = true

local function autoFarm()
    while true do
        wait(1)
        -- código de auto farm
        for _, enemy in pairs(game.Workspace.Enemies:GetChildren()) do
            if enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
                wait(0.5)
                game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool"):Activate()
            end
        end
    end
end

AutoFarmButton.MouseButton1Click:Connect(function()
    autoFarm()
end)

return VITOR_HUB
