local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "AutoFarmOPL", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Tab = Window:MakeTab({
	Name = "Auto Farm Beri",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab:AddSection({
	Name = "Player 1"
})

OrionLib:MakeNotification({
	Name = "Title!",
	Content = "Notification content... what will it say??",
	Image = "rbxassetid://4483345998",
	Time = 5
})

Tab:AddButton({
	Name = "Set Position",
	Callback = function()
game.Workspace.Spawns.Spawn1.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn2.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn3.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn4.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn5.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn6.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn7.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn8.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn9.CFrame = CFrame.new(-1558, 215, 9935)
game.Workspace.Spawns.Spawn10.CFrame = CFrame.new(-1558, 215, 9935)

  	end    
})

Tab:AddButton({
	Name = "Reset Position",
	Callback = function()
game.Workspace.Spawns.Spawn1.CFrame = CFrame.new(-8, 213.710159, -296)
game.Workspace.Spawns.Spawn2.CFrame = CFrame.new(-128, 213.710159, -753)
game.Workspace.Spawns.Spawn3.CFrame = CFrame.new(45, 221.710159, -72)
game.Workspace.Spawns.Spawn4.CFrame = CFrame.new(-237, 222.710159, -1108)
game.Workspace.Spawns.Spawn5.CFrame = CFrame.new(-206, 221.710159, -110.5)
game.Workspace.Spawns.Spawn6.CFrame = CFrame.new(-76, 212.710159, -892)
game.Workspace.Spawns.Spawn7.CFrame = CFrame.new(-428, 213.710159, -154)
game.Workspace.Spawns.Spawn8.CFrame = CFrame.new(-127, 217, -983.200012)
game.Workspace.Spawns.Spawn9.CFrame = CFrame.new(720, 237, 1191.80005)
game.Workspace.Spawns.Spawn10.CFrame = CFrame.new(-1281.5, 213.710159, -1353)

  	end    
})

Tab:AddToggle({
	Name = "Start Autodei",
	Default = false,
	Callback = function(Value)
	AuTODie = Value 
	if Value then
for _ = 1, 12 do
            game.Players.LocalPlayer.Character.Drown:FireServer("NOPLS");
        end
    end
	end    
})



spawn(function()
    while wait() do
        pcall(function()
            if not AuTODie or not game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible then return end;
            wait(3);
            firesignal(game.Players.LocalPlayer.PlayerGui.Load.Frame.Load.MouseButton1Click);
            repeat wait() until not game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible;
            wait(3);
            repeat
                game.Players.LocalPlayer.Character.Drown:FireServer("NOPLS");
                wait(0.1);
            until game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible;
        end)
    end
end);

--------------

local Section2 = Tab:AddSection({
	Name = "Player 2"
})

Tab:AddButton({
	Name = "TP",
	Callback = function()
      		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1558, 215, 9935);
  	end    
})

players = {}

for i,v in pairs(game:GetService("Players"):GetChildren()) do

   table.insert(players,v.Name)

end

Tab:AddDropdown({
	Name = "Select Player",
	Default = "",
	Options = players,
	Callback = function(SelectPlayer)
		Select = SelectPlayer
	end    
})

Tab:AddButton({
	Name = "Teleport To Player",
	Callback = function()
      		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[Select].Character.HumanoidRootPart.CFrame
  	end    
})

Tab:AddToggle({
	Name = "Auto Teleport",
	Default = false,
	Callback = function(ATP)
		AutoTeleport = ATP
	end    
})

spawn(function()

while wait() do

if AutoTeleport then

pcall(function()

game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[Select].Character.HumanoidRootPart.CFrame * CFrame.new(0,30,0)

end)

end

end

end)


Tab:AddToggle({
	Name = "Bring Player",
	Default = false,
	Callback = function(BP)
		BringPlayer = BP
	end    
})

spawn(function()

while wait() do

if BringPlayer then

pcall(function()

game.Players[Select].Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,0,-3)

end)

end

end

end)

Tab:AddToggle({
	Name = "View Player",
	Default = false,
	Callback = function(VP)
		ViewPlayer = VP
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not ViewPlayer then return end;
            for _, Value in pairs(game.Players:GetChildren()) do
                if not ViewPlayer then return end;
                if Select[Value.Name] and Value.Character:FindFirstChild("HumanoidRootPart") and Value.Character:FindFirstChild("Humanoid") and Value.Character.Humanoid.Health > 0 then
                    game.Workspace.CurrentCamera.CameraSubject = Value.Character.Humanoid;
                    wait(3);
                end;
            end
        end)
    end
end);

ViewPlayer:OnChanged(function()
    if not ViewPlayer then
        game.Workspace.CurrentCamera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid;
    end
end)
  
