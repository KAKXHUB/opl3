local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "AutoFarmOPL", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Cache = { DevConfig = {} };
Cache.DevConfig["FindFruitArgumet"] = loadstring(game:HttpGet"https://raw.githubusercontent.com/KangKung02/The-Last-Krypton/master/Back-End/src/public/api/UWU.lua")();

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
	Content = "enjoy EZ NOOB GAY",
	Image = "rbxassetid://4483345998",
	Time = 5
})

Tab:AddToggle({
	Name = "Start Spamskill",
	Default = false,
	Callback = function(STSPK)
		Spamskill = STSPK
	end    
})

local GetingSkillArgumet = function(Arg1)
    if Arg1 == "M_H" then
        local Position = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame;

        if not Position then
            Position = game.Players.LocalPlayer:GetMouse().Hit;
        end
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
local GetPowerFruitForKey = function(InputKey)
    local Export = {};
    local TableOfKey = {
        A = 1,
        B = 2,
        C = 3,
        D = 4,
        E = 5,
        F = 6
    }
    for _, v in pairs(game:GetService("Workspace").UserData["User_"..game.Players.LocalPlayer.UserId].Data:GetChildren()) do
        if v.Name:find("Basic_DF") and v.Value == string.upper(InputKey) then
            Export[1] = TableOfKey[v.Name:split("")[10]]
            Export[2] = 1
            if v.Name:match("%d") == "2" then
                Export[1] += 6
                Export[2] = 2
            end
        end
    end
    return Export;
end;

while wait() do
    pcall(function()
        if not Spamskill or not game.Players.LocalPlayer.Character:FindFirstChild("Powers") or not game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") or not game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then return end;
        local DevilFruit_Name = "Phoenix"

            print(DevilFruit_Name);
            local KeyOfFruit, CountOfFruit = unpack(GetPowerFruitForKey(Key));
            local FuritTypeArgument = Cache.DevConfig["FindFruitArgumet"]:Get(DevilFruit_Name);
            local KeyOfArgument = getsenv(game.Players.LocalPlayer.Character.Powers[DevilFruit_Name])["VTC"];
            game:GetService("Players").LocalPlayer.Character.Powers[DevilFruit_Name].RemoteEvent:FireServer(
                KeyOfArgument,
                string.format("%sPower%s", DevilFruit_Name, KeyOfFruit),
                "StartCharging",
                GetPosition()
            );
            local Args = {KeyOfArgument, string.format("%sPower%s", DevilFruit_Name, KeyOfFruit), "StopCharging"};

            for _, Value in pairs(FuritTypeArgument[string.format("Power%s", (CountOfFruit == 1 and KeyOfFruit) or CountOfFruit == 2 and KeyOfFruit - 6)]) do
                local Data = GetingSkillArgumet(Value);
                table.insert(Args, Data);
            end
            game:GetService("Players").LocalPlayer.Character.Powers[DevilFruit_Name].RemoteEvent:FireServer(unpack(Args));
            if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
                [Spamskill]:SetValue(false);
            end
        end
        wait(0.1);
    end)
end





