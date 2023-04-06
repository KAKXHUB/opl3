local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "AutoFarmOPL", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Tab = Window:MakeTab({
	Name = "Auto Farm Beri",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Tab2 = Window:MakeTab({
	Name = "setting",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = Tab2:AddSection({
	Name = "Hit Box"
})

Tab:AddTextbox({
	Name = "Hit Box Size",
	Default = "default box input",
	TextDisappear = true,
	Callback = function(HBZ)
		HitBoxSIZE = HBZ
	end	  
})

spawn(function()
    while wait() do
        pcall(function()
        if not string.match(HitBoxSIZE) then return end;
            local HitBox = tonumber(string.match(HitBoxSIZE));
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
