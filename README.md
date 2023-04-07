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
	Name = "Set Position(เลือกที่เกิดเอง)",
	Callback = function()
local Content = game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
    

game.Workspace.Spawns.Spawn1.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn2.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn3.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn4.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn5.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn6.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn7.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn8.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn9.CFrame = CFrame.new(Content)
game.Workspace.Spawns.Spawn10.CFrame = CFrame.new(Content)

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
	Name = "Start Autodie",
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



local Section2 = Tab:AddSection({
	Name = "Player 2"
})

Tab:AddButton({
	Name = "Save Zone",
	Callback = function()
      		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Vector3.new(100000, 3500, 80000));
    local Base = Instance.new("Part", game.Workspace);
    Base.Size = Vector3.new(50, 1, 50);
    Base.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0, -3, 0);
    Base.Anchored = true;
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
--------------------------------------
local Tab2 = Window:MakeTab({
	Name = "Auto Quest",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab2:AddSection({
	Name = "Auto Compass"
})

Tab2:AddToggle({
	Name = "Auto Sam Quest",
	Default = false,
	Callback = function(ASQ)
		AutoSamQuest = ASQ
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoSamQuest then return end;
            game.Workspace.Merchants.QuestMerchant.Clickable.Retum:FireServer("Claim1");
        end)
    end
end);


Tab2:AddToggle({
	Name = "Auto Compass Quest",
	Default = false,
	Callback = function(ASQ)
		AutoCompassQuest = ASQ
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoCompassQuest then return end;
            local Compass = game.Players.LocalPlayer.Backpack:FindFirstChild("Compass");
            local Compass2 = game.Players.LocalPlayer.Character:FindFirstChild("Compass");
            if Compass or Compass2 then
                local OldPostiton = game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
                game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                Compass.Parent = game.Players.LocalPlayer.Character;
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Compass.Poser.Value);
                Compass:Activate();
                wait(1);
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(OldPostiton);
            end
        end)
    end
end);

Tab2:AddToggle({
	Name = "Auto Unbox Box",
	Default = false,
	Callback = function(AUB)
		AutoUnboxBox = AUB
	end    
})

["ListOfBox"] = {"Common Box", "Uncommon Box", "Rare Box", "Ultra Rare Box"};

spawn(function()
    while wait() do
        pcall(function()
            if not AutoUnboxBox then return end;
            for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if table.find(Cache.DevConfig["ListOfBox"], Value.Name) then
                    game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                    Value.Parent = game.Players.LocalPlayer.Character;
                    Value:Activate();
                end
            end
        end)
    end
end);
--------------------------------------

local Tab3 = Window:MakeTab({
	Name = "setting",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab3:AddSection({
	Name = "Hit Box"
})

Tab3:AddTextbox({
	Name = "Hit Box Size",
	Default = "",
	TextDisappear = true,
	Callback = function(HBZ)
		HitBoxSIZE = HBZ
	end	  
})

Tab3:AddToggle({
	Name = "Start Hit Box",
	Default = false,
	Callback = function(HP)
		HITBOXEIEI = HP
	end    
})


spawn(function()
    while wait() do
        pcall(function()
            if not HITBOXEIEI then return end;
            local HitBox = HitBoxSIZE
            for _, v in pairs(game.Players:GetChildren()) do
                if v.Character:FindFirstChild("HumanoidRootPart") and v.Name ~= game.Players.LocalPlayer.Name then
                    v.Character.HumanoidRootPart.Size = Vector3.new(HitBox, HitBox, HitBox);
                    v.Character.HumanoidRootPart.Transparency = 0.9;
                    v.Character.HumanoidRootPart.BrickColor = BrickColor.new("Really blue");
                    v.Character.HumanoidRootPart.Material = "Neon";
                    v.Character.HumanoidRootPart.CanCollide = false;
                end
            end
        end)
    end
end)

local Section = Tab3:AddSection({
	Name = "Auto Attack"
})

--Tab3:AddToggle({
--	Name = "Auto Attack",
--	Default = false,
--	Callback = function(AT)
--		AuToAttackEE = AT
--	end    
--})

--spawn(function()
--    while wait() do
--        pcall(function()
--            if not AuToAttackEE then return end;
--            game:GetService("VirtualUser"):ClickButton1(Vector2.new(99999, 99999));
--        end)
--    end
--end);

Tab3:AddToggle({
	Name = "Click On Screen",
	Default = false,
	Callback = function(COS)
		ClickOnScreenEE = COS
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not ClickOnScreenEE then return end;
            game:GetService("VirtualUser"):ClickButton1(Vector2.new(99999, 99999));
        end)
    end
end);


local Section = Tab3:AddSection({
	Name = "Other"
})

Tab3:AddToggle({
	Name = "Auto Spawn When Dead",
	Default = false,
	Callback = function(ASWD)
		AutoSpawnWhenDead = ASWD
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoSpawnWhenDead or not game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible then return end;
            wait(3);
            firesignal(game.Players.LocalPlayer.PlayerGui.Load.Frame.Load.MouseButton1Click);
        end)
    end
end);

Tab3:AddToggle({
	Name = "Auto Rejoin When Disconnect",
	Default = false,
	Callback = function(ARWD)
		AutoRejounWhenDisconnect = ARWD
	end    
})

spawn(function()
	if AutoRejounWhenDisconnect then
		repeat wait() until game:GetService("CoreGui"):FindFirstChild("promptOverlay", true) and game:GetService("CoreGui"):FindFirstChild("promptOverlay", true):FindFirstChild("ErrorPrompt");
		repeat
			game:GetService("TeleportService"):Teleport(game.PlaceId);
			wait(5);
		until not game.Players;
	end
end)



-----------------------------------

local Tab4 = Window:MakeTab({
	Name = "Credit",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab4:AddSection({
	Name = "by peet😎"
})

local Section = Tab4:AddSection({
	Name = "พี่มาคกาก"
})

local Section = Tab4:AddSection({
	Name = "พี่เตอร์แก่"
})
