local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/random%202"))()
local One = library:Window("Speed Control")

local speedValue = 16 -- Default speed value

-- Box for speed input
One:Box("Speed", "Enter speed value", function(value)
    -- Update speed value
    speedValue = tonumber(value) or 16 -- Default speed is 16 if input is invalid
    print("Speed set to " .. speedValue)
    game.StarterGui:SetCore("SendNotification", {
        Title = "Speed Control";
        Text = "Speed set to " .. speedValue;
        Duration = 5;
    })
end)

-- Toggle for enabling/disabling speed control
One:Toggle("Enable Speed Control", function(state)
    local player = game.Players.LocalPlayer
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        if state then
            player.Character.Humanoid.WalkSpeed = speedValue
            print("Speed control enabled")
            game.StarterGui:SetCore("SendNotification", {
                Title = "Speed Control";
                Text = "Speed control enabled";
                Duration = 5;
            })
        else
            player.Character.Humanoid.WalkSpeed = 16 -- Reset to default speed
            print("Speed control disabled")
            game.StarterGui:SetCore("SendNotification", {
                Title = "Speed Control";
                Text = "Speed control disabled";
                Duration = 5;
            })
        end
    end
end)
