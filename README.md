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

 



