local OldPositionOfSpawn = {};
Toggles["Farming Beri:Auto Die:Player 1:Set Spawn Position"]:OnChanged(function()
    if Options["Farming Beri:Auto Die:Player 1:Position"] and Options["Farming Beri:Auto Die:Player 1:Position"].Value then
        local Position = string.split(Options["Farming Beri:Auto Die:Player 1:Position"].Value, ",");
        if #Position ~= 3 then return Library:Notify("Error : Format Error!") end;
        if Toggles["Farming Beri:Auto Die:Player 1:Set Spawn Position"].Value then
            for _, Value in pairs(game.Workspace.Spawns:GetChildren()) do
                table.insert(OldPositionOfSpawn, Value.CFrame);
                Value.CFrame = CFrame.new(Position[1], Position[2], Position[3]);
            end
        else
            for Index, Value in pairs(game.Workspace.Spawns:GetChildren()) do
                Value.CFrame = OldPositionOfSpawn[Index];
            end
        end
    end
end)

Toggles["Farming Beri:Auto Die:Player 1:Start Sacrifice"]:OnChanged(function()
    if Toggles["Farming Beri:Auto Die:Player 1:Start Sacrifice"].Value then
        for _ = 1, 12 do
            game.Players.LocalPlayer.Character.Drown:FireServer("NOPLS");
        end
    end
end);

spawn(function()
    while wait() do
        pcall(function()
            if not Toggles["Farming Beri:Auto Die:Player 1:Start Sacrifice"].Value or not game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible then return end;
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
