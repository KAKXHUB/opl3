Weapon_Name = "Flintlock"
Teleport_Monter = true
Select_Teleport_Monter = "Lv3 Crab"
Type_Position = "Y"
Distance = "7"
Using_One_Hit = true
No_Clip = true
Bypass_One_Hit = true

 spawn(function()
    local function Attack(Obj)
        if not Weapon_Name or Weapon_Name == "" then return end;
        local ListTools = {"Slingshot", "Stars", "Crossbow", "Flintlock"};
        local Tool;
        repeat
            game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
            for _, v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if not Tool and v.ClassName == "Tool" and string.match(string.lower(v.Name), string.lower(Weapon_Name)) then
                    v.Parent = game.Players.LocalPlayer.Character;
                    Tool = v;
                    break;
                end
            end
            if not Weapon_Name then return end;
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
        until OldKill < game:GetService("Workspace").UserData["User_" .. game.Players.LocalPlayer.UserId].Data.Kills.Value or not Teleport_Monter or TimeOut > 10;
    end
    while wait() do
        pcall(function()
            if not Teleport_Monter or not IsSpawned() then return end;
            for _, Value in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                if not Teleport_Monter then return end;
                if Select_Teleport_Monter[Value.Name] and Value:FindFirstChild("HumanoidRootPart") and Value:FindFirstChild("Humanoid") and Value.Humanoid.Health > 0 then
                    if Type_Position == "X" then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Value.HumanoidRootPart.Position + Vector3.new(0, 0, Distance), Value.HumanoidRootPart.Position);
                        if Using_One_Hit then Value.Humanoid.Health = 0 end;
                        Attack(Value);
                    elseif Type_Position == "Y" then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Value.HumanoidRootPart.Position + Vector3.new(0, Distance, 0), Value.HumanoidRootPart.Position);
                        if Using_One_Hit then Value.Humanoid.Health = 0 end;
                        Attack(Value);
                    end
                end
            end
        end)
    end
end);

--Toggles["Farming Beri:Farming Monter:Teleport Monter"]:OnChanged(function()
--    Toggles["Miscellaneous:Left:Basic:No Clip"]:SetValue(Teleport_Monter);
--end)

game:GetService("RunService").Stepped:Connect(function()
    if No_Clip and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
        game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
    end
end)

game:GetService("RunService").RenderStepped:Connect(function()
    if Bypass_One_Hit then
        setscriptable(game.Players.LocalPlayer, "SimulationRadius", true);
        game.Players.LocalPlayer.SimulationRadius = math.huge * math.huge;
    end
end);

game.Players.LocalPlayer.SimulationRadiusChanged:Connect(function(radius)
    if Bypass_One_Hit then
        radius = 9e9;
        return radius;
    end
end);

