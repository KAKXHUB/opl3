local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "AutoFarmOPL", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})





local Tab2 = Window:MakeTab({
	Name = "Auto Quest",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab2:AddSection({
	Name = "Drink"
})




local Cache = { DevConfig = {} };

Cache.DevConfig["ListOfDrink"] = {"Cider+", "Lemonade+", "Juice+", "Smoothie+"};
Cache.DevConfig["ListOfDrinkFormMixer"] = {"Cider", "Lemonade", "Juice", "Smoothie", "Milk", "Golden Apple"};



Tab2:AddDropdown({
	Name = "Select Drink",
	Default = "",
	Options = Cache.DevConfig["ListOfDrink"],
	Callback = function(SD)
		SelectDrink = SD
	end    
})

Tab2:AddTextbox({
	Name = "Amount Drink",
	Default = "1",
	TextDisappear = true,
	Callback = function(AD)
		AmountDrink = AD
	end	  
})

Tab2:AddButton({
	Name = "Buy Drink",
	Callback = function()
        if not AmountDrink or not string.match(AmountDrink, "%d+") or tonumber(string.match(AmountDrink, "%d+")) < 0 then return end;
        for _ = 1, tonumber(string.match(AmountDrink, "%d+")) do
            game.Workspace.Merchants.BetterDrinkMerchant.Clickable.Retum:FireServer(SelectDrink)
        end
  	end    
})

Tab2:AddToggle({
	Name = "Auto Drink",
	Default = false,
	Callback = function(ADK)
		AutoDrink = ADK
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoDrink then return end;
            for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if table.find(Cache.DevConfig["ListOfDrink"], Value.Name) then
                    game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                    Value.Parent = game.Players.LocalPlayer.Character;
                    Value:Activate();
                end
            end
        end)
    end
end);

Tab2:AddToggle({
	Name = "Auto Drop Drink",
	Default = false,
	Callback = function(ADD)
		AutoDropDrink = ADD
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoDropDrink then return end;
            for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if table.find(Cache.DevConfig["ListOfDrink"], Value.Name) then
                    game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                    Value.Parent = game.Players.LocalPlayer.Character;
                    Value.Parent = game.Workspace;
                end
            end
        end)
    end
end);

Tab2:AddToggle({
	Name = "Auto Farm Juice",
	Default = false,
	Callback = function(AFJ)
		AutoFarmJuice = AFJ
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoFarmJuice then return end;
            for _, Value in pairs(game:GetService("Workspace").Barrels.Crates:GetChildren()) do
                if Value:FindFirstChild("ClickDetector") then
                    fireclickdetector(Value.ClickDetector);
                end
            end;
            for _, Value in pairs(game:GetService("Workspace").Barrels.Barrels:GetChildren()) do
                if Value:FindFirstChild("ClickDetector") then
                    fireclickdetector(Value.ClickDetector);
                end
            end;
            wait(0.1);
            for _, v in pairs(game:GetService("Workspace").Island8.Kitchen:GetChildren()) do
                if v.Name == "Folder" and v:FindFirstChild("JuicingBowl") then
                    fireclickdetector(v.JuicingBowl.Bowl.ClickDetector);
                end
            end;
        end)
    end
end);

Tab2:AddToggle({
	Name = "Auto Drink Everything",
	Default = false,
	Callback = function(ADE)
		AutoDrinkEveryting = ADE
	end    
})

spawn(function()
    while wait() do
        pcall(function()
            if not AutoDrinkEveryting then return end;
            for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                for _, ValueFormList in pairs(Cache.DevConfig["ListOfDrinkFormMixer"]) do
                    if string.match(Value.Name, ValueFormList) then
                        game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                        Value.Parent = game.Players.LocalPlayer.Character;
                        Value:Activate();
                        spawn(function()
                            wait(20);
                            Value:Destroy();
                        end)
                    end
                end
                wait();
            end
        end)
    end
end);

