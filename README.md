local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "AutoFarmOPL", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Tab3 = Window:MakeTab({
	Name = "Auto Quest",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab3:AddSection({
	Name = "Auto Compass"
})

Tab3:AddToggle({
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


Tab3:AddToggle({
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

Tab3:AddToggle({
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
