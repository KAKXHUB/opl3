local GetingSkillArgumet = function(Arg1)
    if Arg1 == "M_H" then
        local Position = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame;

        if not Position then
            Position = game.Players.LocalPlayer:GetMouse().Hit;
  return  Position;
    elseif Arg1 == "M_T" then
        return game.Players.LocalPlayer:GetMouse().Target;
    elseif Arg1 == "C" then
        return tonumber(100);
    elseif Arg1 == "nil" then
        return false;
    elseif Arg1 == "CM" then
        return "Left";
    elseif Arg1 == "M_H_P" then
        return game.Players.LocalPlayer:GetMouse().Hit.Position;
    elseif Arg1 == "ARM_P" then
        return game.Players.LocalPlayer.Character["Right Arm"].Position;
    elseif Arg1 == "HRP_P" then
        return game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
    elseif Arg1 == "DS_SL" then
        return game.Workspace.UserData["User_"..game.Players.LocalPlayer.UserId].Data.SniperLevel.Value;
    elseif Arg1 == "DS_DL" then
        return game.Workspace.UserData["User_"..game.Players.LocalPlayer.UserId].Data.DefenseLevel.Value;
    elseif Arg1 == "GT" then
        local AllPlayers = {};
        for i, v in pairs(game.Players:GetChildren()) do
            if v.Name ~= game.Players.LocalPlayer.Name and  (game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - v.Character:FindFirstChild("HumanoidRootPart").Position).magnitude < 1000 then
                table.insert(AllPlayers, v)
            end
        end
        return AllPlayers;
    elseif Arg1 == "C_GDP" then
        local function GetDotPoint()
            local v45 = game.Players.LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0, 1000, 0);
            local v46, v47, v48 = workspace:FindPartOnRay(Ray.new(v45, (game.Players.LocalPlayer:GetMouse().Hit.p - v45).unit * 5000), game.Players.LocalPlayer.Character);
            return v47;
        end;
        return CFrame.new(GetDotPoint());
    end
end;


print(GetingSkillArgumet)
 



