local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/cat"))() --you can go into the github link and copy all of it and modify it for yourself.
local Window = Library:CreateWindow("Farming Monter:", Vector2.new(492, 598), Enum.KeyCode.RightControl) --you can change your UI keybind
local AimingTab = Window:CreateTab("Bring Monter") --you can rename this tab to whatever you want --you can also change the tabs code, for example "AimingTab" can be changed to "FunnyCoolTab" etc.

local Cache = { DevConfig = {} };

Cache.DevConfig["FolderSettingPath"] = "KryptonHub";
Cache.DevConfig["FileSettingPath"] = "Settings";
Cache.DevConfig["ListOfMonter"] = game:GetService("HttpService"):JSONDecode(game:HttpGet("https://raw.githubusercontent.com/KangKung02/just-bin/main/OPL_MT.lua"));

local SettingSection = AimingTab:CreateSector("Setting", "left")

SettingSection:AddTextbox("Weapon Name", nil, function(WPNTB)
    WeaponNameTB = WPNTB
end)


SettingSection:AddDropdown("Type Position", {"X", "Y"}, "Y", true, function(TPSTDD)
    TypePositionDD = TPSTDD

end)

SettingSection:AddToggle("Using One Hit", false, function(USOHTG)
    UsingOneHitTG = TPMTG
end)

SettingSection:AddSlider("Distance", -16, 7, 16, 1, function(DTSD)
    DistanceSD = DTSD
end)

SettingSection:AddToggle("No Clip", false, function(NCTG)
    NoClipTG = NCTG
end)

SettingSection:AddToggle("Bypass One Hit", false, function(BPOHTG)
    ByPassOneHitTG = BPOHTG
end)

local testSection = AimingTab:CreateSector("Teleport Monter", "Right")  --you can  change the section code, for example "testsection" can be changed to "FunnyCoolSection" etc.

testSection:AddDropdown("Select Monter", Cache.DevConfig["ListOfMonter"], "", false, function(SLMDD)
SelectMonter = SLMDD
end)

testSection:AddButton("Set All", function(IhateGayPeople)
    local Content = {};
    for _, Value in pairs(Cache.DevConfig["ListOfMonter"]) do
        Content[Value] = true;
    end
    SelectMonter:SetValue(Content);
end)

testSection:AddToggle("Teleport Monter", false, function(TPMTG)
    TeleportMonter = TPMTG
end)

while wait() do
	pcall(function()
		if TeleportMonter == true then
			if game:GetService("Workspace").Enemies[SelectMonter]:FindFirstChild("HumanoidRootPart") and game:GetService("Workspace").Enemies[SelectMonter]:FindFirstChild("Humanoid") and game:GetService("Workspace").Enemies[SelectMonter].Humanoid.Health > 0 then
				if TypePositionDD == "X" then
					game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Enemies[SelectMonter].HumanoidRootPart.Position + Vector3.new(0, 0, 7), game:GetService("Workspace").Enemies[SelectMonter].HumanoidRootPart.Position);
					if UsingOneHitTG == true then game:GetService("Workspace").Enemies[SelectMonter].Humanoid.Health = 0 end;
				elseif 	TypePositionDD == "Y" then
					game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Enemies[SelectMonter].HumanoidRootPart.Position + Vector3.new(0, 7, 0), game:GetService("Workspace").Enemies[SelectMonter].HumanoidRootPart.Position);
					if UsingOneHitTG == true then game:GetService("Workspace").Enemies[SelectMonter].Humanoid.Health = 0 end;
				end
			end		
		end	
	end)
end	

