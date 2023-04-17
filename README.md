Options["Farming Beri:Farming Monter:Settings:Weapon Name"].Value = "Flintlock"
Toggles["Farming Beri:Farming Monter:Teleport Monter"].Value = true
Options["Farming Beri:Farming Monter:Select Teleport Monter"].Value = "Lv3 Crab"
Options["Farming Beri:Farming Monter:Settings:Type Position"].Value = "Y"
Options["Farming Beri:Farming Monter:Settings:Distance"].Value = "7"
Toggles["Farming Beri:Farming Monter:Settings:Using One Hit"].Value = true
Toggles["Miscellaneous:Left:Basic:No Clip"].Value = true
Toggles["Farming Beri:Farming Monter:Settings:Bypass One Hit"].Value = true

 spawn(function()
    local function Attack(Obj)
        if not Options["Farming Beri:Farming Monter:Settings:Weapon Name"].Value or Options["Farming Beri:Farming Monter:Settings:Weapon Name"].Value == "" then return end;
        local ListTools = {"Slingshot", "Stars", "Crossbow", "Flintlock"};
        local Tool;
        repeat
            game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
            for _, v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if not Tool and v.ClassName == "Tool" and string.match(string.lower(v.Name), string.lower(Options["Farming Beri:Farming Monter:Settings:Weapon Name"].Value)) then
                    v.Parent = game.Players.LocalPlayer.Character;
                    Tool = v;
                    break;
                end
            end
            if not Options["Farming Beri:Farming Monter:Settings:Weapon Name"].Value then return end;
            wait();
        until Tool;
        local TimeOut = 0;
        local OldKill = game:GetService("Workspace").UserData["User_" .. game.Players.LocalPlayer.UserId].Data.Kills.Value;
        repeat
            pcall(function()
                if table.find(ListTools, Tool.Name) then
                    Tool.RemoteEvent:FireServer(CFrame.new(Obj.HumanoidRootPart.Position), Obj.HumanoidRootPart);
                else
                    Tool:Activate();
                end
            end);
            TimeOut += 1;
            wait(0.1);
        until OldKill < game:GetService("Workspace").UserData["User_" .. game.Players.LocalPlayer.UserId].Data.Kills.Value or not Toggles["Farming Beri:Farming Monter:Teleport Monter"].Value or TimeOut > 10;
    end
    while wait() do
        pcall(function()
            if not Toggles["Farming Beri:Farming Monter:Teleport Monter"].Value or not IsSpawned() then return end;
            for _, Value in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                if not Toggles["Farming Beri:Farming Monter:Teleport Monter"].Value then return end;
                if Options["Farming Beri:Farming Monter:Select Teleport Monter"].Value[Value.Name] and Value:FindFirstChild("HumanoidRootPart") and Value:FindFirstChild("Humanoid") and Value.Humanoid.Health > 0 then
                    if Options["Farming Beri:Farming Monter:Settings:Type Position"].Value == "X" then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Value.HumanoidRootPart.Position + Vector3.new(0, 0, Options["Farming Beri:Farming Monter:Settings:Distance"].Value), Value.HumanoidRootPart.Position);
                        if Toggles["Farming Beri:Farming Monter:Settings:Using One Hit"].Value then Value.Humanoid.Health = 0 end;
                        Attack(Value);
                    elseif Options["Farming Beri:Farming Monter:Settings:Type Position"].Value == "Y" then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Value.HumanoidRootPart.Position + Vector3.new(0, Options["Farming Beri:Farming Monter:Settings:Distance"].Value, 0), Value.HumanoidRootPart.Position);
                        if Toggles["Farming Beri:Farming Monter:Settings:Using One Hit"].Value then Value.Humanoid.Health = 0 end;
                        Attack(Value);
                    end
                end
            end
        end)
    end
end);

Toggles["Farming Beri:Farming Monter:Teleport Monter"]:OnChanged(function()
    Toggles["Miscellaneous:Left:Basic:No Clip"]:SetValue(Toggles["Farming Beri:Farming Monter:Teleport Monter"].Value);
end)

game:GetService("RunService").Stepped:Connect(function()
    if Toggles["Miscellaneous:Left:Basic:No Clip"].Value and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
        game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
    end
end)

game:GetService("RunService").RenderStepped:Connect(function()
    if Toggles["Farming Beri:Farming Monter:Settings:Bypass One Hit"].Value then
        setscriptable(game.Players.LocalPlayer, "SimulationRadius", true);
        game.Players.LocalPlayer.SimulationRadius = math.huge * math.huge;
    end
end);

game.Players.LocalPlayer.SimulationRadiusChanged:Connect(function(radius)
    if Toggles["Farming Beri:Farming Monter:Settings:Bypass One Hit"].Value then
        radius = 9e9;
        return radius;
    end
end);

