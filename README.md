repeat
    wait();
until game:IsLoaded() and  game.Players and (game.Workspace:FindFirstChild('Trees') and game.Workspace.Trees:FindFirstChild('Tree') and  game.Workspace.Trees.Tree:FindFirstChild('Model')) and (game.Workspace:FindFirstChild('Island14') and game.Workspace.Island14:FindFirstChild('PedestalSpots'));
setfflag("HumanoidParallelRemoveNoPhysics", "False")
setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
setfflag("CrashPadUploadToBacktraceToBacktraceBaseUrl", "")
setfflag("CrashUploadToBacktracePercentage", "0")
setfflag("CrashUploadToBacktraceBlackholeToken", "")
setfflag("CrashUploadToBacktraceWindowsPlayerToken", "")

game:GetService("Players").LocalPlayer.Idled:Connect(function()
    game:GetService("VirtualUser"):Button2Down(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
    wait();
    game:GetService("VirtualUser"):Button2Up(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
end)

local Global_V = {}
-- pcall(function()
--     local req = (syn and syn.request) or (http and http.request) or request;
--     local GetDataFormServer = req({
--         Url = 'http://kangisloser.xyz/GetData',
--         Method = 'POST',
--         Headers = {
--             ["Content-Type"] = "application/json"
--         };
--         Body = game:GetService('HttpService'):JSONEncode({
--             GameId = tostring(game.PlaceId)
--         }),
--     })
--     local Body = game:GetService("HttpService"):JSONDecode(GetDataFormServer.Body)
--     Global_V = {
--         Version_script = Body.Version,
--         Script_enabled = Body.ScriptEnabled
--     }
-- end)

-- if getgenv().IsKangDev == "Haachamaissocute!" then
    Global_V = {
        Version_script = "0.0.0 [In Development]";
        Script_enabled = true;
    }
-- end
if not Global_V.Script_enabled then
    return game.Players.LocalPlayer:Kick("Script was disabled.")
end
local UITab = {};
local Cache = { DevConfig = {} };

Cache.DevConfig["FolderSettingPath"] = "KryptonHub";
Cache.DevConfig["FileSettingPath"] = "Settings";
Cache.DevConfig["ListOfMonter"] = game:GetService("HttpService"):JSONDecode(game:HttpGet("https://raw.githubusercontent.com/KangKung02/just-bin/main/OPL_MT.lua"));
Cache.DevConfig["ListOfRareDveilFruit"] = game:GetService("HttpService"):JSONDecode(game:HttpGet("https://raw.githubusercontent.com/KangKung02/just-bin/main/OPL_LF.json"));
Cache.DevConfig["ListOfDveilFruit"] = game:GetService("HttpService"):JSONDecode(game:HttpGet("https://raw.githubusercontent.com/KangKung02/just-bin/main/OPL_ALF.json"));
Cache.DevConfig["ListOfMods"] = game:GetService("HttpService"):JSONDecode(game:HttpGet("https://raw.githubusercontent.com/KangKung02/just-bin/main/OPL_ML.json"));
Cache.DevConfig["FindFruitArgumet"] = loadstring(game:HttpGet"https://raw.githubusercontent.com/KangKung02/The-Last-Krypton/master/Back-End/src/public/api/UWU.lua")();
Cache.DevConfig["ListOfBox"] = {"Common Box", "Uncommon Box", "Rare Box", "Ultra Rare Box"};
Cache.DevConfig["ListOfRareBox"] = {"Rare Box", "Ultra Rare Box"};
Cache.DevConfig["ListOfKeySkill"] = {"Z", "X", "C", "V", "B", "N", "F", "G", "H", "J", "K", "L"};
Cache.DevConfig["ListOfTypeSkillTaget"] = {"Mouse", "Yourself", "Monsters", "Players"};
Cache.DevConfig["ListOfInstantKillWeapon"] = {"Kogatana", "Seastone Cestus", "Yoru"};
Cache.DevConfig["ListOfStorage"] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
Cache.DevConfig["ListOfRod"] = {"Wood Rod", "Sturdy Rod", "Super Rod"};
Cache.DevConfig["ListOfDrink"] = {"Cider+", "Lemonade+", "Juice+", "Smoothie+"};
Cache.DevConfig["ListOfDrinkFormMixer"] = {"Cider", "Lemonade", "Juice", "Smoothie", "Milk", "Golden Apple"};
Cache.DevConfig["ListOfTeleportPositon"] = {
    ["House Island"] = CFrame.new(882, 269, 1219);
    ["Sand Island"] = CFrame.new(-204, 221, -113);
    ["Sam island"] = CFrame.new(-1282, 217, -1353);
    ["Fountain Island"] = CFrame.new(-238, 225, -1108);
    ["Castle Island"] = CFrame.new(-3137, 353, -4111);
    ["Evil Island"] = CFrame.new(-5275, 515, -7849);
    ["Racetrack Island"] = CFrame.new(-6447, 275, 4612);
    ["Small Snow Island"] = CFrame.new(-1897, 224, 3296);
    ["Big Snow Island"] = CFrame.new(6672, 417, -1475);
    ["Krizma Island"] = CFrame.new(-1071, 360, 1671);
    ["Bar Island"] = CFrame.new(1505, 260, 2171);
    ["Moon Island"] = CFrame.new(3205, 356, 1658);
    ["Vokun Island"] = CFrame.new(4617, 216, 4951);
    ["Pyramid Island"] = CFrame.new(118, 215, 4774);
    ["Aura Island"] = CFrame.new(-1558, 215, 9935);
    ["Stone Island"] = CFrame.new(-2728, 252, 1071);
    ["Fishing Island"] = CFrame.new(-1692, 215, -326);
    ["Old stone Island"] = CFrame.new(2054, 487, -701);
    ["Boss Island"] = CFrame.new(4853, 569, -7207);
    ["Sand castle Island"] = CFrame.new(1016, 223, -3282);
    ["Mansion Island"] = CFrame.new(1798, 217, 903);
    ["Near voken Island"] = CFrame.new(1063, 217, 3353);
};
Cache.DevConfig["ListOfTeleportPositonOnlyIndex"] = {"House Island", "Sand Island", "Sam island", "Fountain Island", "Castle Island", "Evil Island", "Racetrack Island", "Small Snow Island", "Big Snow Island", "Krizma Island", "Bar Island", "Moon Island", "Vokun Island", "Pyramid Island", "Aura Island", "Stone Island", "Fishing Island", "Old stone Island", "Boss Island", "Sand castle Island", "Mansion Island", "Near voken Island"}
Cache.DevConfig["ListOfKeyboardKey"] = {"A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"}
local CheckPath = function(Path, ...)
    local Args = {...};
    for _, v in pairs(Args) do
        if Path:FindFirstChild(v) then
            Path = Path[v]
        else
            return false;
        end
    end
    return true;
end

local function ToFullName(name)
    for _, v in pairs(game.Players:GetChildren()) do
        if tostring(name) == "@all" and v.Name ~= game.Players.LocalPlayer.Name then
            return v;
        end
        if string.match(string.lower(v.Name), string.lower(tostring(name))) and v.Name ~= game.Players.LocalPlayer.Character then
            return v;
        end
    end
end

local function GetlistNamePlayers()
    local Content = {};
    for _, Value in pairs(game.Players:GetChildren()) do
        if Value.Name ~= game.Players.LocalPlayer.Name then
            table.insert(Content, Value.Name);
        end
    end
    return Content;
end

local function InstanceToName(t)
    local Content = {};
    for _, Value in pairs(t) do
        table.insert(Content, Value.Name);
    end
    return Content;
end

local function GetTableLen(t)
    local count = 0;
    for _ in next, t do
        count += 1;
    end
    return count;
end

local function IsSpawned()
    return not game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible;
end

local KangFindNearest = function(Path)
    local ObjectNearest;
    local NearestList = {};
    for i, v in pairs(Path) do
        if v.Name ~= game.Players.LocalPlayer.Name and v.Character:FindFirstChild("Humanoid") and v.Character:FindFirstChild("HumanoidRootPart") and v.Character.Humanoid.Health > 0 then
            table.insert(NearestList, v);
        end
    end
    if NearestList[1] ~= nil then
        ObjectNearest = NearestList[1];
    end
    if ObjectNearest ~= nil then
        for i, v in pairs(NearestList) do
            if (game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - v.Character:FindFirstChild("HumanoidRootPart").Position).magnitude <= (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - ObjectNearest.Character:FindFirstChild("HumanoidRootPart").Position).magnitude then
                ObjectNearest = v;
            end
        end
    end
    return ObjectNearest;
end;

local function IsNumber(Text)
    return pcall(function()
        local a = tonumber(Text) + 0;
    end)
end;

local function to_hex(color)
    return string.format("0x%02X%02X%02X", color.R * 0xFF, color.G * 0xFF, color.B * 0xFF);
end



local MyFile = {};
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/KangKung02/LinoriaLib/main/addons/SaveManager.lua"))();
SaveManager:SetFolder(Cache.DevConfig["FolderSettingPath"]);
SaveManager:SetFile("Settings");
SaveManager:IgnoreThemeSettings()
function MyFile:Load()
    SaveManager:Load();
    if not self.IsLoaded then
        self.IsLoaded = true
    end
end

local MethodsAutoTableUI = {
    __index = function(self, key)
        if not rawget(self, key) then
            rawset(self, key, {})
        end
        return rawget(self, key)
    end,
    __newindex = function(self, key, value)
        if #rawget(self, key) == 0 then
            rawset(self, "Main", value)
        end
        return rawset(self, key, value)
    end
}
setmetatable(UITab, MethodsAutoTableUI);

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/KangKung02/LinoriaLib/main/Library.lua"))();
Ui_Configs["FirstOnChanged"] = false;
local Windows = Library:CreateWindow(string.format("Krypton %s - %s", "Premium", Global_V.Version_script));

UITab["Farming Beri"]["Main"] = Windows:AddTab("Farming Beri");

UITab["Farming Beri"]["Left"] = UITab["Farming Beri"]["Main"]:AddLeftTabbox("Auto Die");
UITab["Farming Beri"]["Right"] = UITab["Farming Beri"]["Main"]:AddRightTabbox("Farming Monter");

UITab["Farming Beri"]["Left"]["Player 1"] = UITab["Farming Beri"]["Left"]:AddTab("Player 1");
UITab["Farming Beri"]["Left"]["Player 2"] = UITab["Farming Beri"]["Left"]:AddTab("Player 2");

UITab["Farming Beri"]["Left"]["Player 1"]:AddInput("Farming Beri:Auto Die:Player 1:Position", { Text = "Position" });


UITab["Farming Beri"]["Left"]["Player 1"]:AddButton("Set Position", function()
    local Position = game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
    local Content = string.format("%s, %s, %s", math.floor(tonumber(Position.X)), math.floor(tonumber(Position.Y)), math.floor(tonumber(Position.Z)));
    Options["Farming Beri:Auto Die:Player 1:Position"]:SetValue(Content);
end);
UITab["Farming Beri"]["Left"]["Player 1"]:AddToggle("Farming Beri:Auto Die:Player 1:Set Spawn Position", { Text = "Set Spawn Position" });
UITab["Farming Beri"]["Left"]["Player 1"]:AddToggle("Farming Beri:Auto Die:Player 1:Start Sacrifice", { Text = "Start Sacrifice" });
-- UITab["Farming Beri"]["Left"]["Player 1"]:AddToggle("Farming Beri:Auto Die:Player 1:Start Sacrifice [Beta]", { Text = "Start Sacrifice [Beta]" });


UITab["Farming Beri"]["Left"]["Player 2"]:AddInput("Farming Beri:Auto Die:Player 2:Player 1 Name", { Text = "Player 1 Name"});
UITab["Farming Beri"]["Left"]["Player 2"]:AddButton("Teleport To Player 1", function()
    if not Options["Farming Beri:Auto Die:Player 2:Player 1 Name"].Value or Options["Farming Beri:Auto Die:Player 2:Player 1 Name"].Value == "" then return end;
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(ToFullName(Options["Farming Beri:Auto Die:Player 2:Player 1 Name"].Value).Character.HumanoidRootPart.Position + Vector3.new(0, 5, 0));
end);

UITab["Farming Beri"]["Left"]["Player 2"]:AddButton("Safe Zone", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Vector3.new(100000, 3500, 80000));
    local Base = Instance.new("Part", game.Workspace);
    Base.Size = Vector3.new(50, 1, 50);
    Base.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0, -3, 0);
    Base.Anchored = true;
end);

UITab["Farming Beri"]["Right"]["Bring Monter"] = UITab["Farming Beri"]["Right"]:AddTab("Bring Monter");
UITab["Farming Beri"]["Right"]["Teleport Monter"] = UITab["Farming Beri"]["Right"]:AddTab("Teleport Monter");
UITab["Farming Beri"]["Right"]["Settings"] = UITab["Farming Beri"]["Main"]:AddRightGroupbox("Settings");


UITab["Farming Beri"]["Right"]["Settings"]:AddSlider("Farming Beri:Farming Monter:Settings:Distance", { Text = "Distance", Default = 7, Min = -16, Max = 16, Rounding = 0 });
UITab["Farming Beri"]["Right"]["Settings"]:AddDropdown("Farming Beri:Farming Monter:Settings:Type Position", { Text = "Type Position", Default = "Y", Values = {"X", "Y"} });
UITab["Farming Beri"]["Right"]["Settings"]:AddToggle("Farming Beri:Farming Monter:Settings:Bypass One Hit", { Text = "Bypass One Hit" });
UITab["Farming Beri"]["Right"]["Settings"]:AddToggle("Farming Beri:Farming Monter:Settings:Using One Hit", { Text = "Using One Hit" });
UITab["Farming Beri"]["Right"]["Settings"]:AddInput("Farming Beri:Farming Monter:Settings:Weapon Name", { Text = "Weapon Name" });

UITab["Farming Beri"]["Right"]["Bring Monter"]:AddDropdown("Farming Beri:Farming Monter:Select Bring Monter", { Text = "Select Bring Monter", Values = Cache.DevConfig["ListOfMonter"], Multi = true });
UITab["Farming Beri"]["Right"]["Bring Monter"]:AddButton("Set All", function()
    local Content = {};
    for _, Value in pairs(Cache.DevConfig["ListOfMonter"]) do
        Content[Value] = true;
    end
    Options["Farming Beri:Farming Monter:Select Bring Monter"]:SetValue(Content);
end)
UITab["Farming Beri"]["Right"]["Bring Monter"]:AddButton("Reset Selecter", function()
    if not Options["Farming Beri:Farming Monter:Select Bring Monter"] then return end;
    Options["Farming Beri:Farming Monter:Select Bring Monter"]:NewList(Cache.DevConfig["ListOfMonter"]);
end);

UITab["Farming Beri"]["Right"]["Bring Monter"]:AddToggle("Farming Beri:Farming Monter:Bring Monter", { Text = "Bring Monter" });

UITab["Farming Beri"]["Right"]["Teleport Monter"]:AddDropdown("Farming Beri:Farming Monter:Select Teleport Monter", { Text = "Select Teleport Monter", Values = Cache.DevConfig["ListOfMonter"], Multi = true });
UITab["Farming Beri"]["Right"]["Teleport Monter"]:AddButton("Set All", function()
    local Content = {};
    for _, Value in pairs(Cache.DevConfig["ListOfMonter"]) do
        Content[Value] = true;
    end
    Options["Farming Beri:Farming Monter:Select Teleport Monter"]:SetValue(Content);
end)
UITab["Farming Beri"]["Right"]["Teleport Monter"]:AddButton("Reset Selecter", function()
    if not Options["Farming Beri:Farming Monter:Select Teleport Monter"] then return end;
    Options["Farming Beri:Farming Monter:Select Teleport Monter"]:NewList(Cache.DevConfig["ListOfMonter"]);
end);
UITab["Farming Beri"]["Right"]["Teleport Monter"]:AddToggle("Farming Beri:Farming Monter:Teleport Monter", { Text = "Teleport Monter" });

UITab["HunterX"]["Main"] = Windows:AddTab("HunterX");

UITab["HunterX"]["Left"] = UITab["HunterX"]["Main"]:AddLeftTabbox("HunterX Left");
UITab["HunterX"]["Right"] = UITab["HunterX"]["Main"]:AddRightTabbox("HunterX Right");

UITab["HunterX"]["Left"]["Settings"] = UITab["HunterX"]["Main"]:AddLeftGroupbox("Settings");
UITab["HunterX"]["Left"]["AboutTagets"] = UITab["HunterX"]["Left"]:AddTab("About Tagets");
UITab["HunterX"]["Left"]["Other"] = UITab["HunterX"]["Left"]:AddTab("Other");

UITab["HunterX"]["Right"]["Webhook"] = UITab["HunterX"]["Right"]:AddTab("Webhook");
UITab["HunterX"]["Right"]["Server Hop"] = UITab["HunterX"]["Right"]:AddTab("Server Hop");

UITab["HunterX"]["Left"]["Settings"]:AddDropdown("HunterX:HunterX Left:Settings:Select Tagets", { Text = "Select Tagets", Values = GetlistNamePlayers(), Multi = true });
UITab["HunterX"]["Left"]["Settings"]:AddInput("HunterX:HunterX Left:Settings:Select Tagets [Box]", { Text = "Select Tagets [Box]" });
UITab["HunterX"]["Left"]["Settings"]:AddButton("Set Select Box To List", function()
    if not Options["HunterX:HunterX Left:Settings:Select Tagets [Box]"].Value or Options["HunterX:HunterX Left:Settings:Select Tagets [Box]"].Value == "" then return end;
    local PlayersName = ToFullName(Options["HunterX:HunterX Left:Settings:Select Tagets [Box]"].Value);
    if not PlayersName then return end;
    PlayersName = PlayersName.Name;
    local Old = Options["HunterX:HunterX Left:Settings:Select Tagets"].Value;
    Old[PlayersName] = true;
    Options["HunterX:HunterX Left:Settings:Select Tagets"]:SetValue(Old);
end)
UITab["HunterX"]["Left"]["Settings"]:AddButton("Set Everyone To List", function()
    local Content = {};
    for _, Value in pairs(Options["HunterX:HunterX Left:Settings:Select Tagets"].Values) do
        Content[Value] = true;
    end
    Options["HunterX:HunterX Left:Settings:Select Tagets"]:SetValue(Content);
end)


UITab["HunterX"]["Left"]["Settings"]:AddButton("Refresh", function()
    if not Options["HunterX:HunterX Left:Settings:Select Tagets"] then return end;
    Options["HunterX:HunterX Left:Settings:Select Tagets"]:NewList(GetlistNamePlayers());
end);
UITab["HunterX"]["Left"]["Settings"]:AddDropdown("HunterX:HunterX Left:Settings:Type Position", { Text = "Type Position", Values = {"X", "Y"}, Default = "X" });

UITab["HunterX"]["Left"]["Settings"]:AddSlider("HunterX:HunterX Left:Settings:Distance", { Text = "Distance", Default = 7, Min = -16, Max = 16, Rounding = 0 });
UITab["HunterX"]["Left"]["Settings"]:AddInput("HunterX:HunterX Left:Settings:Hit Box Size", { Text = "Hit Box Size" });
UITab["HunterX"]["Left"]["Settings"]:AddInput("HunterX:HunterX Left:Settings:Aim Bot Distance", { Text = "Aim Bot Distance", Default = 999999999999999 });
UITab["HunterX"]["Left"]["Settings"]:AddInput("HunterX:HunterX Left:Settings:Esp Distance", { Text = "Esp Distance", Default = 999999999999999 });
UITab["HunterX"]["Left"]["Settings"]:AddLabel("Esp Color"):AddColorPicker("HunterX:HunterX Left:Settings:Esp Color", { Default = Color3.fromRGB(96, 59, 226) });


UITab["HunterX"]["Left"]["AboutTagets"]:AddToggle("HunterX:HunterX Left:AboutTagets:Bring Tagets", { Text = "Bring Tagets" });
UITab["HunterX"]["Left"]["AboutTagets"]:AddToggle("HunterX:HunterX Left:AboutTagets:Teleport Tagets", { Text = "Teleport Tagets" });
UITab["HunterX"]["Left"]["AboutTagets"]:AddToggle("HunterX:HunterX Left:AboutTagets:Teleport And Back Tagets", { Text = "Teleport And Back Tagets" });
UITab["HunterX"]["Left"]["AboutTagets"]:AddToggle("HunterX:HunterX Left:AboutTagets:View Tagets", { Text = "View Tagets" });
UITab["HunterX"]["Left"]["AboutTagets"]:AddToggle("HunterX:HunterX Left:AboutTagets:Aim Bot Tagets", { Text = "Aim Bot Tagets" });
UITab["HunterX"]["Left"]["AboutTagets"]:AddToggle("HunterX:HunterX Left:AboutTagets:Esp Tagets", { Text = "Esp Tagets" });


UITab["HunterX"]["Left"]["Other"]:AddButton("Check Inventory", function()
    local Detector = {
        ListOfRareFruit = {};
        ListOfNormalFruit = {};
        ListOfNormalBox = {};
        ListOfRareBox = {};
    };

    function Detector:Add(Argument)
        local Content;
        if Argument.IsFruit then
            Content = string.format("Fruit Name : %s, Owner Name : %s, Position : %s, IsRare : %s", Argument.FruitName or "None", Argument.Owner or "None", Argument.Position or "None", (Argument.IsRare and "Yes") or "No");
            if Argument["IsRare"] then
                table.insert(self.ListOfRareFruit, Content);
            else
                table.insert(self.ListOfNormalFruit, Content);
            end
        else
            Content = string.format("Box Name : %s, Owner Name : %s, Position : %s, IsRare : %s", Argument.FruitName or "None", Argument.Owner or "None", Argument.Position or "None", (Argument.IsRare and "Yes") or "No");
            if Argument["IsRare"] then
                table.insert(self.ListOfRareBox, Content);
            else
                table.insert(self.ListOfNormalBox, Content);
            end
        end
    end;

    for _, Players in pairs(game.Players:GetChildren()) do
        if Players.Name ~= game.Players.LocalPlayer.Name then
            for _, Item in pairs(Players.Backpack:GetChildren()) do
                if Item.ClassName == "Tool" and string.match(Item.Name, "Fruit") then
                    Detector:Add({
                        ["FruitName"] = Item.Name;
                        ["Owner"] = Players.Name;
                        ["Position"] = "Backpack";
                        ["IsRare"] = table.find(Cache.DevConfig["ListOfRareDveilFruit"], Item.Name);
                        ["IsFruit"] = true;
                    });
                elseif Item.ClassName == "Tool" and table.find(Cache.DevConfig["ListOfBox"], Item.Name) then
                    Detector:Add({
                        ["FruitName"] = Item.Name;
                        ["Owner"] = Players.Name;
                        ["Position"] = "Backpack";
                        ["IsRare"] = table.find(Cache.DevConfig["ListOfRareBox"], Item.Name);
                        ["IsFruit"] = false;
                    });
                end
            end

            for _, Item in pairs(Players.Character:GetChildren()) do
                if Item.ClassName == "Tool" and string.match(Item.Name, "Fruit") then
                    Detector:Add({
                        ["FruitName"] = Item.Name;
                        ["Owner"] = Players.Name;
                        ["Position"] = "Hand";
                        ["IsRare"] = table.find(Cache.DevConfig["ListOfRareDveilFruit"], Item.Name);
                        ["IsFruit"] = true;
                    });
                elseif Item.ClassName == "Tool" and table.find(Cache.DevConfig["ListOfBox"], Item.Name) then
                    Detector:Add({
                        ["FruitName"] = Item.Name;
                        ["Owner"] = Players.Name;
                        ["Position"] = "Hand";
                        ["IsRare"] = table.find(Cache.DevConfig["ListOfRareBox"], Item.Name);
                        ["IsFruit"] = false;
                    });
                end
            end
        end
    end

    for _, Item in pairs(game.Workspace:GetChildren()) do
        if Item.ClassName == "Tool" and table.find(Cache.DevConfig["ListOfBox"], Item.Name) then
            Detector:Add({
                ["FruitName"] = Item.Name;
                ["Owner"] = "None";
                ["Position"] = "Ground";
                ["IsRare"] = table.find(Cache.DevConfig["ListOfRareBox"], Item.Name);
                ["IsFruit"] = false;
            });
        end
    end

    for _, Item in pairs(game.Workspace.Trees.Tree.Model:GetChildren()) do
        if Item.ClassName == "Tool" and string.match(Item.Name, "Fruit") then
            Detector:Add({
                ["FruitName"] = Item.Name;
                ["Position"] = "Ground";
                ["IsRare"] = table.find(Cache.DevConfig["ListOfRareDveilFruit"], Item.Name);
                ["IsFruit"] = true;
            });
        end
    end

    for _, Path in pairs(game:GetService("Workspace").Island14.PedestalSpots:GetChildren()) do
        for _, Item in pairs(Path:GetChildren()) do
            if Item.ClassName == "Tool" and string.match(Item.Name, "Fruit") then
                Detector:Add({
                    ["FruitName"] = Item.Name;
                    ["Position"] = "Pedestal";
                    ["IsRare"] = table.find(Cache.DevConfig["ListOfRareDveilFruit"], Item.Name);
                    ["IsFruit"] = true;
                });
            end
        end
    end

    for _, Item in pairs(game:GetService("Workspace").Altar.FruitReceptical:GetChildren()) do
        if Item.ClassName == "Tool" and string.match(Item.Name, "Fruit") then
            Detector:Add({
                ["FruitName"] = Item.Name;
                ["Position"] = "Rebirth Pedestal";
                ["IsRare"] = table.find(Cache.DevConfig["ListOfRareDveilFruit"], Item.Name);
                ["IsFruit"] = true;
            });
        end
    end

    print("--------------------------------------->");

    for _, Value in pairs(Detector.ListOfRareFruit) do
        print(string.format("** %s **", Value));
    end
    
    for _, Value in pairs(Detector.ListOfNormalFruit) do
        print(Value);
    end

    for _, Value in pairs(Detector.ListOfRareBox) do
        print(string.format("** %s **", Value));
    end
    
    for _, Value in pairs(Detector.ListOfNormalBox) do
        print(Value);
    end
    print("<---------------------------------------");
end);
UITab["HunterX"]["Left"]["Other"]:AddToggle("HunterX:HunterX Left:Other:Loot Devil Fruit", { Text = "Loot Devil Fruit" });
UITab["HunterX"]["Left"]["Other"]:AddToggle("HunterX:HunterX Left:Other:Loot Box", { Text = "Loot Box" });
UITab["HunterX"]["Left"]["Other"]:AddToggle("HunterX:HunterX Left:Other:Loot Compass", { Text = "Loot Compass" });
UITab["HunterX"]["Left"]["Other"]:AddToggle("HunterX:HunterX Left:Other:Loot Drink", { Text = "Loot Drink" });

UITab["HunterX"]["Right"]["Webhook"]:AddInput("HunterX:HunterX Right:Webhook:Your Webhook Url", { Text = "Your Webhook Url" });
UITab["HunterX"]["Right"]["Webhook"]:AddButton("Send Test", function()
    if not Options["HunterX:HunterX Right:Webhook:Your Webhook Url"].Value then return end;
    if not string.find(Options["HunterX:HunterX Right:Webhook:Your Webhook Url"].Value, "https://discord.com/api/webhooks") then return end;
    local My_Request = (syn and syn.request) or (http and http.request) or request;
    My_Request({
        Url = Options["HunterX:HunterX Right:Webhook:Your Webhook Url"].Value;
        Method = "POST",
        Headers = {["Content-Type"] = "application/json"};
        Body = game:GetService("HttpService"):JSONEncode({
            ["embeds"] = {{
                ["color"] = (Options["HunterX:HunterX Right:Webhook:Webhook Color"].Value and tonumber(to_hex(Options["HunterX:HunterX Right:Webhook:Webhook Color"].Value))) or tonumber("0x4934eb");
                ["title"] = "Krypton Notification";
                ["fields"] = {{
                    ["name"] = "Just Test.";
                    ["value"] = "Hello World!";
                    ["inline"] = false;
                }}
            }}
        });
    });
end);
UITab["HunterX"]["Right"]["Webhook"]:AddSlider("HunterX:HunterX Right:Webhook:Delay Time", { Text = "Delay Time", Default = 30, Min = 1, Max = 360, Rounding = 0, Suffix = "s" });
UITab["HunterX"]["Right"]["Webhook"]:AddLabel("Webhook Color"):AddColorPicker("HunterX:HunterX Right:Webhook:Webhook Color", { Default = Color3.new(0.431372, 0.196078, 0.807843) });
UITab["HunterX"]["Right"]["Webhook"]:AddDropdown("HunterX:HunterX Right:Webhook:Select Notification Fruit", { Text = "Select Notification Fruit", Values = Cache.DevConfig["ListOfDveilFruit"], Multi = true });
UITab["HunterX"]["Right"]["Webhook"]:AddDropdown("HunterX:HunterX Right:Webhook:Select Notification Box", { Text = "Select Notification Box", Values = Cache.DevConfig["ListOfBox"], Multi = true });
UITab["HunterX"]["Right"]["Webhook"]:AddButton("Set Rare Fruit", function()
    if not Options["HunterX:HunterX Right:Webhook:Select Notification Fruit"] then return end;
    local Content = {};
    for _, Value in pairs(Cache.DevConfig["ListOfRareDveilFruit"]) do
        Content[Value] = true;
    end
    Options["HunterX:HunterX Right:Webhook:Select Notification Fruit"]:SetValue(Content);
end);
UITab["HunterX"]["Right"]["Webhook"]:AddToggle("HunterX:HunterX Right:Webhook:Notification Fruit", { Text = "Notification Fruit" });
UITab["HunterX"]["Right"]["Webhook"]:AddToggle("HunterX:HunterX Right:Webhook:Notification Aura Fruit", { Text = "Notification Aura Fruit" });
UITab["HunterX"]["Right"]["Webhook"]:AddToggle("HunterX:HunterX Right:Webhook:Notification Box", { Text = "Notification Box" });

UITab["HunterX"]["Right"]["Server Hop"]:AddSlider("HunterX:HunterX Right:Server Hop:Dalay Time", { Text = "Delay Time", Default = 20, Min = 1, Max = 120, Rounding = 0, Suffix = "s" });
UITab["HunterX"]["Right"]["Server Hop"]:AddInput("HunterX:HunterX Right:Server Hop:Job Id", { Text = "Job Id" });
UITab["HunterX"]["Right"]["Server Hop"]:AddButton("Hop With Job Id", function()
    if not Options["HunterX:HunterX Right:Server Hop:Job Id"].Value then return end;
    game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, Options["HunterX:HunterX Right:Server Hop:Job Id"].Value);
end);
UITab["HunterX"]["Right"]["Server Hop"]:AddButton("Get Job Id", function()
    setclipboard(game.JobId);
    print(game.JobId);
end);

UITab["HunterX"]["Right"]["Server Hop"]:AddSlider("HunterX:HunterX Right:Server Hop:Not Same Server List Max", { Text = "Not Same Server List Max", Default = 5, Min = 1, Max = 30, Rounding = 0 });
UITab["HunterX"]["Right"]["Server Hop"]:AddToggle("HunterX:HunterX Right:Server Hop:Start Hop Server", { Text = "Start Hop Server" });
UITab["HunterX"]["Right"]["Server Hop"]:AddToggle("HunterX:HunterX Right:Server Hop:Stop Hop Server When Found Select DF, Box", { Text = "Stop Hop Server When Found Select DF, Box" });

UITab["Miscellaneous"]["Main"] = Windows:AddTab("Miscellaneous");

UITab["Miscellaneous"]["Left"] = UITab["Miscellaneous"]["Main"]:AddLeftTabbox("Miscellaneous Left");
UITab["Miscellaneous"]["Left 2"] = UITab["Miscellaneous"]["Main"]:AddLeftTabbox("Miscellaneous Left 2");
UITab["Miscellaneous"]["Right"] = UITab["Miscellaneous"]["Main"]:AddRightTabbox("Miscellaneous Right");
UITab["Miscellaneous"]["Right 2"] = UITab["Miscellaneous"]["Main"]:AddRightTabbox("Miscellaneous Right 2");

UITab["Miscellaneous"]["Left"]["Basic"] = UITab["Miscellaneous"]["Left"]:AddTab("Basic");
UITab["Miscellaneous"]["Left"]["Farming"] = UITab["Miscellaneous"]["Left"]:AddTab("Farming");
UITab["Miscellaneous"]["Left"]["Haki"] = UITab["Miscellaneous"]["Left"]:AddTab("Haki");
UITab["Miscellaneous"]["Left 2"]["Fishing"] = UITab["Miscellaneous"]["Left 2"]:AddTab("Fishing");
UITab["Miscellaneous"]["Left 2"]["Drink"] = UITab["Miscellaneous"]["Left 2"]:AddTab("Drink");
UITab["Miscellaneous"]["Left 2"]["Auto Attack"] = UITab["Miscellaneous"]["Left 2"]:AddTab("Auto Attack");

UITab["Miscellaneous"]["Right"]["Skill"] = UITab["Miscellaneous"]["Right"]:AddTab("Skill");
UITab["Miscellaneous"]["Right"]["Storage"] = UITab["Miscellaneous"]["Right"]:AddTab("Storage");
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"] = UITab["Miscellaneous"]["Right 2"]:AddTab("Fruit Stats");
UITab["Miscellaneous"]["Right 2"]["Advance"] = UITab["Miscellaneous"]["Right 2"]:AddTab("Advance");
UITab["Miscellaneous"]["Right 2"]["Other"] = UITab["Miscellaneous"]["Right 2"]:AddTab("Other");
-- Kang Tag
UITab["Miscellaneous"]["Left"]["Basic"]:AddToggle("Miscellaneous:Left:Basic:Anti Mods", { Text = "Anti Mods" });
UITab["Miscellaneous"]["Left"]["Basic"]:AddToggle("Miscellaneous:Left:Basic:Infinite Jump", { Text = "Infinite Jump" });
UITab["Miscellaneous"]["Left"]["Basic"]:AddToggle("Miscellaneous:Left:Basic:No Clip", { Text = "No Clip" });
UITab["Miscellaneous"]["Left"]["Basic"]:AddToggle("Miscellaneous:Left:Basic:Keypress Teleport [Toggle]", { Text = "Keypress Teleport" }):AddKeyPicker("Miscellaneous:Left:Basic:Keypress Teleport", { Text = "Keypress Teleport", Default = "P", Mode = "Toggle" });
Options["Miscellaneous:Left:Basic:Keypress Teleport"]:OnClick(function()
    if not Toggles["Miscellaneous:Left:Basic:Keypress Teleport [Toggle]"].Value then return end;
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game.Players.LocalPlayer:GetMouse().Hit.Position + Vector3.new(0, 3, 0))
end);
UITab["Miscellaneous"]["Left"]["Basic"]:AddButton("Safe Zone", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Vector3.new(100000, 3500, 80000));
    local Base = Instance.new("Part", game.Workspace);
    Base.Size = Vector3.new(50, 1, 50);
    Base.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0, -3, 0);
    Base.Anchored = true;
end);

UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Collect Chest", { Text = "Auto Collect Chest" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Get Mission", { Text = "Auto Get Mission" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Fishing Quest", { Text = "Auto Fishing Quest" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Sam Quest", { Text = "Auto Sam Quest" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Compass Quest", { Text = "Auto Compass Quest" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Unbox Box", { Text = "Auto Unbox Box" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Claim Hourly Reward", { Text = "Auto Claim Hourly Reward" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Claim Daily Reward", { Text = "Auto Claim Daily Reward" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Farm Juice", { Text = "Auto Farm Juice" });
UITab["Miscellaneous"]["Left"]["Farming"]:AddToggle("Miscellaneous:Left:Farming:Auto Drink Everything", { Text = "Auto Drink Everything" });

UITab["Miscellaneous"]["Left"]["Haki"]:AddSlider("Miscellaneous:Left:Haki:Haki Limit Minimal", { Text = "Haki Limit Minimal", Default = 50, Min = 0, Max = 99, Rounding = 0, Suffix = "%" });
UITab["Miscellaneous"]["Left"]["Haki"]:AddSlider("Miscellaneous:Left:Haki:Haki Limit Maximum", { Text = "Haki Limit Maximum", Default = 50, Min = 0, Max = 99, Rounding = 0, Suffix = "%" });
UITab["Miscellaneous"]["Left"]["Haki"]:AddToggle("Miscellaneous:Left:Haki:Auto Use Buso Haki", { Text = "Auto Use Buso Haki" });
UITab["Miscellaneous"]["Left"]["Haki"]:AddToggle("Miscellaneous:Left:Haki:Auto Use Kenbunshoku Haki", { Text = "Auto Use Kenbunshoku Haki" });

UITab["Miscellaneous"]["Left 2"]["Fishing"]:AddDropdown("Miscellaneous:Left 2:Fishing:Select Rod", { Text = "Select Rod", Values = Cache.DevConfig["ListOfRod"] });
UITab["Miscellaneous"]["Left 2"]["Fishing"]:AddToggle("Miscellaneous:Left 2:Fishing:Auto Fishing", { Text = "Auto Fishing" });

UITab["Miscellaneous"]["Left 2"]["Drink"]:AddDropdown("Miscellaneous:Left 2:Drink:Select Drink", { Text = "Select Drink", Values = Cache.DevConfig["ListOfDrink"] });
UITab["Miscellaneous"]["Left 2"]["Drink"]:AddInput("Miscellaneous:Left 2:Drink:Amount Drink", { Text = "Amount Drink", Default = 1 });
UITab["Miscellaneous"]["Left 2"]["Drink"]:AddButton("Buy Drink", function()
    if not Options["Miscellaneous:Left 2:Drink:Amount Drink"].Value or not string.match(Options["Miscellaneous:Left 2:Drink:Amount Drink"].Value, "%d+") or tonumber(string.match(Options["Miscellaneous:Left 2:Drink:Amount Drink"].Value, "%d+")) < 0 then return end;
    for _ = 1, tonumber(string.match(Options["Miscellaneous:Left 2:Drink:Amount Drink"].Value, "%d+")) do
        game.Workspace.Merchants.BetterDrinkMerchant.Clickable.Retum:FireServer(Options["Miscellaneous:Left 2:Drink:Select Drink"].Value)
    end
end)
UITab["Miscellaneous"]["Left 2"]["Drink"]:AddToggle("Miscellaneous:Left 2:Drink:Auto Drink", { Text = "Auto Drink" });
UITab["Miscellaneous"]["Left 2"]["Drink"]:AddToggle("Miscellaneous:Left 2:Drink:Auto Drop Drink", { Text = "Auto Drop Drink" });

UITab["Miscellaneous"]["Left 2"]["Auto Attack"]:AddInput("Miscellaneous:Left 2:Auto Attack:Weapon Name", { Text = "Weapon Name" }):OnChanged(function()
    local value = Options["Miscellaneous:Left 2:Auto Attack:Weapon Name"].Value;
    while wait(3) do
        if value ~= Options["Miscellaneous:Left 2:Auto Attack:Weapon Name"].Value then
            value = Options["Miscellaneous:Left 2:Auto Attack:Weapon Name"].Value;
        else
            break;
        end
    end;
    for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
        if Value.ClassName == "Tool" and string.match(string.lower(Value.Name), string.lower(value)) then
            return Options["Miscellaneous:Left 2:Auto Attack:Weapon Name"]:SetValue(Value.Name);
        end
    end;
    for _, Value in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
        if Value.ClassName == "Tool" and string.match(string.lower(Value.Name), string.lower(value)) then
            return Options["Miscellaneous:Left 2:Auto Attack:Weapon Name"]:SetValue(Value.Name);
        end
    end;
end);
UITab["Miscellaneous"]["Left 2"]["Auto Attack"]:AddToggle("Miscellaneous:Left 2:Auto Attack:Equip Weapon", { Text = "Equip Weapon" });
UITab["Miscellaneous"]["Left 2"]["Auto Attack"]:AddToggle("Miscellaneous:Left 2:Auto Attack:Activate Weapon", { Text = "Activate Weapon" });
UITab["Miscellaneous"]["Left 2"]["Auto Attack"]:AddToggle("Miscellaneous:Left 2:Auto Attack:Click On Screen", { Text = "Click On Screen" });

UITab["Miscellaneous"]["Right"]["Skill"]:AddDropdown("Miscellaneous:Right:Skill:Select Key", { Text = "Select Key", Values = Cache.DevConfig["ListOfKeySkill"], Multi = true });
UITab["Miscellaneous"]["Right"]["Skill"]:AddSlider("Miscellaneous:Right:Skill:Delay Time", { Text = "Delay Time", Default = 1, Min = 0, Max = 60, Rounding = 1, Suffix = "s" });
UITab["Miscellaneous"]["Right"]["Skill"]:AddDropdown("Miscellaneous:Right:Skill:Type Of Taget", { Text = "Type Of Taget", Default = "Mouse", Values = Cache.DevConfig["ListOfTypeSkillTaget"] });
UITab["Miscellaneous"]["Right"]["Skill"]:AddSlider("Miscellaneous:Right:Skill:Skill Charge", { Text = "Skill Charge", Default = 100, Min = 0, Max = 100, Rounding = 1, Suffix = "%" });
UITab["Miscellaneous"]["Right"]["Skill"]:AddToggle("Miscellaneous:Right:Skill:Using Spam Skill", { Text = "Using Spam Skill" });


UITab["Miscellaneous"]["Right"]["Storage"]:AddDropdown("Miscellaneous:Right:Storage:Select Fruit", { Text = "Select Fruit", Values = Cache.DevConfig["ListOfDveilFruit"], Multi = true });
UITab["Miscellaneous"]["Right"]["Storage"]:AddDropdown("Miscellaneous:Right:Storage:Select Storage", { Text = "Select Storage", Values = Cache.DevConfig["ListOfStorage"], Multi = true });
UITab["Miscellaneous"]["Right"]["Storage"]:AddButton("Set Rare Fruit", function()
    if not Options["Miscellaneous:Right:Storage:Select Fruit"] then return end;
    local Content = {};
    for _, Value in pairs(Cache.DevConfig["ListOfRareDveilFruit"]) do
        Content[Value] = true;
    end
    Options["Miscellaneous:Right:Storage:Select Fruit"]:SetValue(Content);
end);
UITab["Miscellaneous"]["Right"]["Storage"]:AddButton("Set Empty Storage", function()
    if not Options["Miscellaneous:Right:Storage:Select Fruit"] then return end;
    local Content = {};
    for _, Value in pairs(game.Players.LocalPlayer.PlayerGui.Storage.Frame:GetChildren()) do
        if Value.ClassName == "Frame" and string.match(Value.Name, "StoredDF") and Value.Visible and Value:FindFirstChild("Button").Text == "Store" then
            Content[tonumber(string.match(Value.Name, "%d+"))] = true;
        end
    end
    Options["Miscellaneous:Right:Storage:Select Storage"]:SetValue(Content);
end);
UITab["Miscellaneous"]["Right"]["Storage"]:AddToggle("Miscellaneous:Right:Storage:Keep Aura Fruit", { Text = "Keep Aura Fruit" });
UITab["Miscellaneous"]["Right"]["Storage"]:AddToggle("Miscellaneous:Right:Storage:Keep Selected Fruit", { Text = "Keep Selected Fruit" });

UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddButton("Open Affinity Diviner", function()
    fireclickdetector(game:GetService("Workspace").Merchants.AffinityMerchant.Clickable.ClickDetector)
end);
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddDropdown("Miscellaneous:Right 2:Fruit Stats:Pay With", { Text = "Pay With", Values = {"Cash", "Gems"} });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddSlider("Miscellaneous:Right 2:Fruit Stats:Melee Stats", { Text = "Melee Stats", Default = 1, Min = 0, Max = 10, Rounding = 0 });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddSlider("Miscellaneous:Right 2:Fruit Stats:Sword Stats", { Text = "Sword Stats", Default = 1, Min = 0, Max = 10, Rounding = 0 });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddSlider("Miscellaneous:Right 2:Fruit Stats:Sniper Stats", { Text = "Sniper Stats", Default = 1, Min = 0, Max = 10, Rounding = 0 });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddSlider("Miscellaneous:Right 2:Fruit Stats:Defense Stats", { Text = "Defense Stats", Default = 1, Min = 0, Max = 10, Rounding = 0 });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddDropdown("Miscellaneous:Right 2:Fruit Stats:Lock Stats", { Text = "Lock Stats", Values = {"Melee", "Sword", "Sniper", "Defense"}, Multi = true });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddToggle("Miscellaneous:Right 2:Fruit Stats:Random Fruit 1", { Text = "Random Fruit 1" });
UITab["Miscellaneous"]["Right 2"]["Fruit Stats"]:AddToggle("Miscellaneous:Right 2:Fruit Stats:Random Fruit 2", { Text = "Random Fruit 2" });

UITab["Miscellaneous"]["Right 2"]["Advance"]:AddSlider("Miscellaneous:Right 2:Advance:Move Speed", { Text = "Move Speed", Default = 16, Min = 1, Max = 1000, Rounding = 0 });
UITab["Miscellaneous"]["Right 2"]["Advance"]:AddSlider("Miscellaneous:Right 2:Advance:Jump Power", { Text = "Jump Power", Default = 50, Min = 1, Max = 10000, Rounding = 0 });
UITab["Miscellaneous"]["Right 2"]["Advance"]:AddToggle("Miscellaneous:Right 2:Advance:No Skill Cooldown", { Text = "No Skill Cooldown" });
UITab["Miscellaneous"]["Right 2"]["Advance"]:AddToggle("Miscellaneous:Right 2:Advance:No Drowing Damage", { Text = "No Drowing Damage" });

UITab["Miscellaneous"]["Right 2"]["Other"]:AddToggle("Miscellaneous:Right 2:Other:Auto Spawn When Dead", { Text = "Auto Spawn When Dead" });
UITab["Miscellaneous"]["Right 2"]["Other"]:AddButton("Get Seastone Cestus <Need Max Melee>", function()
    game.Workspace.UserData["User_"..game.Players.LocalPlayer.UserId].UpdateMelee:FireServer("Seastone Cestus");
end);
UITab["Miscellaneous"]["Right 2"]["Other"]:AddToggle("Miscellaneous:Right 2:Other:Auto Rejoin When Disconnect", { Text = "Auto Rejoin When Disconnect" });
UITab["Miscellaneous"]["Right 2"]["Other"]:AddDropdown("Miscellaneous:Right 2:Other:Click NPCs", { Text = "Click NPCs", Values = InstanceToName(game:GetService("Workspace").Merchants:GetChildren()) }):OnChanged(function()
    if not Options["Miscellaneous:Right 2:Other:Click NPCs"].Value or not game:GetService("Workspace").Merchants[Options["Miscellaneous:Right 2:Other:Click NPCs"].Value] or not CheckPath(game:GetService("Workspace").Merchants[Options["Miscellaneous:Right 2:Other:Click NPCs"].Value], "Clickable", "ClickDetector") then return end;
    fireclickdetector(game:GetService("Workspace").Merchants[Options["Miscellaneous:Right 2:Other:Click NPCs"].Value].Clickable.ClickDetector);
end);

UITab["Misc 2"]["Main"] = Windows:AddTab("Misc 2");

UITab["Misc 2"]["Left"] = UITab["Misc 2"]["Main"]:AddLeftTabbox("Misc Left");
UITab["Misc 2"]["Right"] = UITab["Misc 2"]["Main"]:AddRightTabbox("Misc Right");

UITab["Misc 2"]["Left"]["Teleport"] = UITab["Misc 2"]["Left"]:AddTab("Teleport");
UITab["Misc 2"]["Left"]["Auto Keyboard"] = UITab["Misc 2"]["Left"]:AddTab("Auto Keyboard");

UITab["Misc 2"]["Right"]["Fake Stats[Player]"] = UITab["Misc 2"]["Right"]:AddTab("Fake Stats[Player]");
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"] = UITab["Misc 2"]["Right"]:AddTab("Fake Stats[Fruit]");


UITab["Misc 2"]["Left"]["Teleport"]:AddDropdown("Misc 2:Left:Teleport:Teleport Island", { Text = "Teleport Island", Values = Cache.DevConfig["ListOfTeleportPositonOnlyIndex"] }):OnChanged(function()
    if not Options["Misc 2:Left:Teleport:Teleport Island"].Value or not Cache.DevConfig.ListOfTeleportPositon[Options["Misc 2:Left:Teleport:Teleport Island"].Value] or not CheckPath(game.Players.LocalPlayer.Character, "HumanoidRootPart") then return end;
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Cache.DevConfig.ListOfTeleportPositon[Options["Misc 2:Left:Teleport:Teleport Island"].Value];
end);
UITab["Misc 2"]["Left"]["Teleport"]:AddDropdown("Misc 2:Left:Teleport:Teleport NPC", { Text = "Teleport NPC", Values = InstanceToName(game:GetService("Workspace").Merchants:GetChildren()) }):OnChanged(function()
    if not Options["Misc 2:Left:Teleport:Teleport NPC"].Value or not game:GetService("Workspace").Merchants[Options["Misc 2:Left:Teleport:Teleport NPC"].Value] or not CheckPath(game.Players.LocalPlayer.Character, "HumanoidRootPart") then return end;
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game:GetService("Workspace").Merchants[Options["Misc 2:Left:Teleport:Teleport NPC"].Value].HumanoidRootPart.Position + Vector3.new(0, 5, 0));
end);

UITab["Misc 2"]["Left"]["Auto Keyboard"]:AddDropdown("Misc 2:Left:Auto Keyboard:Select Key", { Text = "Select Key", Values = Cache.DevConfig["ListOfKeyboardKey"], Multi = true });
UITab["Misc 2"]["Left"]["Auto Keyboard"]:AddInput("Misc 2:Left:Auto Keyboard:Select Key [Box]", { Text = "Select Key [Box]" });
UITab["Misc 2"]["Left"]["Auto Keyboard"]:AddButton("Add Key", function()
    Options["Misc 2:Left:Auto Keyboard:Select Key [Box]"].Value = string.upper(Options["Misc 2:Left:Auto Keyboard:Select Key [Box]"].Value);
    if not Options["Misc 2:Left:Auto Keyboard:Select Key [Box]"].Value or Cache.DevConfig["ListOfKeyboardKey"][Options["Misc 2:Left:Auto Keyboard:Select Key [Box]"].Value] then return end;
    local Old = Options["Misc 2:Left:Auto Keyboard:Select Key"].Value;
    Old[Options["Misc 2:Left:Auto Keyboard:Select Key [Box]"].Value] = true;
    Options["Misc 2:Left:Auto Keyboard:Select Key"]:SetValue(Old);
end);
UITab["Misc 2"]["Left"]["Auto Keyboard"]:AddSlider("Misc 2:Left:Auto Keyboard:Delay Time", { Text = "Delay Time", Default = 3, Min = 0, Max = 120, Rounding = 1, Suffix = "s" });
UITab["Misc 2"]["Left"]["Auto Keyboard"]:AddToggle("Misc 2:Left:Auto Keyboard:Using Auto Keyboard", { Text = "Using Auto Keyboard" });


UITab["Misc 2"]["Right"]["Fake Stats[Player]"]:AddInput("Misc 2:Right:Fake Stats[Player]:Player's Name", { Text = "Player's Name" }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Player]:Player's Name"].Value or Options["Misc 2:Right:Fake Stats[Player]:Player's Name"].Value == "" then return end;
    game.Players.LocalPlayer.PlayerGui.Menu.Frame.C.Frame.Nametag.Text = tostring(Options["Misc 2:Right:Fake Stats[Player]:Player's Name"].Value);
end);

UITab["Misc 2"]["Right"]["Fake Stats[Player]"]:AddDropdown("Misc 2:Right:Fake Stats[Player]:Select Player's Stats", { Text = "Select Player's Stats", Values = {"Melee", "Sniper", "Sword", "Defense", "Haki", "TotalLevel"} })
UITab["Misc 2"]["Right"]["Fake Stats[Player]"]:AddInput("Misc 2:Right:Fake Stats[Player]:Set Player's Stats", { Text = "Set Player's Stats" }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Player]:Select Player's Stats"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Menu.Frame.C.Frame[Options["Misc 2:Right:Fake Stats[Player]:Select Player's Stats"].Value].Text = tostring(string.format("%s : %s", Options["Misc 2:Right:Fake Stats[Player]:Select Player's Stats"].Value, Options["Misc 2:Right:Fake Stats[Player]:Set Player's Stats"].Value));
end);
UITab["Misc 2"]["Right"]["Fake Stats[Player]"]:AddInput("Misc 2:Right:Fake Stats[Player]:Devil Fruit 1 Name", { Text = "Devil Fruit 1 Name" }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 1 Name"].Value or Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 1 Name"].Value == "" then return end;
    game.Players.LocalPlayer.PlayerGui.Menu.Frame.D.Frame.E.Frame.DevilFruit["00"].Ability.Text = tostring(Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 1 Name"].Value);
    game.Players.LocalPlayer.PlayerGui.Menu.Frame.C.Frame.A.DevilFruit.Text = tostring(Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 1 Name"].Value);
end);
UITab["Misc 2"]["Right"]["Fake Stats[Player]"]:AddInput("Misc 2:Right:Fake Stats[Player]:Devil Fruit 2 Name", { Text = "Devil Fruit 2 Name" }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 2 Name"].Value or Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 2 Name"].Value == "" then return end;
    game.Players.LocalPlayer.PlayerGui.Menu.Frame.D.Frame.E.Frame.DevilFruit2["00"].Ability.Text = tostring(Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 2 Name"].Value);
    game.Players.LocalPlayer.PlayerGui.Menu.Frame.C.Frame.A.DevilFruit2.Text = tostring(Options["Misc 2:Right:Fake Stats[Player]:Devil Fruit 2 Name"].Value);
end);

UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddDropdown("Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot", { Text = "Devil Fruit Slot", Values = Cache.DevConfig["ListOfStorage"] });
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddInput("Misc 2:Right:Fake Stats[Fruit]:Name", { Text = "Name" }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].DevilFruit.Text = Options["Misc 2:Right:Fake Stats[Fruit]:Name"].Value
end);
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddSlider("Misc 2:Right:Fake Stats[Fruit]:Melee Stats", { Text = "Melee Stats", Default = 1, Min = 1, Max = 10, Rounding = 0 }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].Affinities.MeleeAffinity.Value = tonumber(Options["Misc 2:Right:Fake Stats[Fruit]:Melee Stats"].Value);
end);
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddSlider("Misc 2:Right:Fake Stats[Fruit]:Sniper Stats", { Text = "Sniper Stats", Default = 1, Min = 1, Max = 10, Rounding = 0 }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].Affinities.SniperAffinity.Value = tonumber(Options["Misc 2:Right:Fake Stats[Fruit]:Sniper Stats"].Value);
end);
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddSlider("Misc 2:Right:Fake Stats[Fruit]:Sword Stats", { Text = "Sword Stats", Default = 1, Min = 1, Max = 10, Rounding = 0 }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].Affinities.SwordAffinity.Value = tonumber(Options["Misc 2:Right:Fake Stats[Fruit]:Sword Stats"].Value);
end);
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddSlider("Misc 2:Right:Fake Stats[Fruit]:Defense Stats", { Text = "Defense Stats", Default = 1, Min = 1, Max = 10, Rounding = 0 }):OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].Affinities.DefenseAffinity.Value = tonumber(Options["Misc 2:Right:Fake Stats[Fruit]:Defense Stats"].Value);
end);
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddToggle("Misc 2:Right:Fake Stats[Fruit]:Color 1 Aura", { Text = "Color 1 Aura" }):AddColorPicker("Misc 2:Right:Fake Stats[Fruit]:Color 1 Aura[Color]", { Default = Color3.fromRGB(51, 91, 175) });
UITab["Misc 2"]["Right"]["Fake Stats[Fruit]"]:AddToggle("Misc 2:Right:Fake Stats[Fruit]:Color 2 Aura", { Text = "Color 1 Aura" }):AddColorPicker("Misc 2:Right:Fake Stats[Fruit]:Color 2 Aura[Color]", { Default = Color3.fromRGB(51, 91, 175) });
Toggles["Misc 2:Right:Fake Stats[Fruit]:Color 1 Aura"]:OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].DFU1.Visible = Toggles["Misc 2:Right:Fake Stats[Fruit]:Color 1 Aura"].Value;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].DFU1.ImageColor3 = Options["Misc 2:Right:Fake Stats[Fruit]:Color 1 Aura[Color]"].Value;
end);
Toggles["Misc 2:Right:Fake Stats[Fruit]:Color 2 Aura"]:OnChanged(function()
    if not Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value then return end;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].DFU2.Visible = Toggles["Misc 2:Right:Fake Stats[Fruit]:Color 2 Aura"].Value;
    game.Players.LocalPlayer.PlayerGui.Storage.Frame["StoredDF" .. Options["Misc 2:Right:Fake Stats[Fruit]:Devil Fruit Slot"].Value].DFU2.ImageColor3 = Options["Misc 2:Right:Fake Stats[Fruit]:Color 2 Aura[Color]"].Value;
end);

UITab["Settings-Credits"]["Main"] = Windows:AddTab("Settings - Credits");
UITab["Settings-Credits"]["Left"] = UITab["Settings-Credits"]["Main"]:AddLeftTabbox("Settings");
UITab["Settings-Credits"]["Right"] = UITab["Settings-Credits"]["Main"]:AddRightTabbox("Credits")

UITab["Settings-Credits"]["Left"]["Theme"] = UITab["Settings-Credits"]["Left"]:AddTab("Theme");
UITab["Settings-Credits"]["Left"]["FileManager"] = UITab["Settings-Credits"]["Left"]:AddTab("File Manager");

local ThemeManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/KangKung02/LinoriaLib/main/addons/ThemeManager.lua"))();
ThemeManager:SetLibrary(Library)
ThemeManager:SetFolder(Cache.DevConfig["FolderSettingPath"])
ThemeManager:ApplyToGroupbox(UITab["Settings-Credits"]["Left"]["Theme"])

local MyFileManager = {};

function MyFileManager:Save()
    local folder = SaveManager.Folder .. '/settings/';
    if not isfolder(folder) then
        makefolder(folder);
    end
    local List = {
        AutoSave = (Toggles["AutoSave"] and Toggles["AutoSave"].Value) or false;
        AutoLoad = (Toggles["AutoLoad"] and Toggles["AutoLoad"].Value) or false;
    }
    writefile(folder .. "AutoSave.json", game:GetService("HttpService"):JSONEncode(List));
end

function MyFileManager:Load()
    local file = SaveManager.Folder .. '/settings/AutoSave.json';
    if not isfile(file) then return end;
    local List = {"AutoSave", "AutoLoad"};
    local decoded = game:GetService("HttpService"):JSONDecode(readfile(file));
    for _, index in next, List do
        spawn(function()
            repeat wait() until Toggles[index];
            if Toggles[index].SetValue and decoded[index] then
                Toggles[index]:SetValue(decoded[index]);
            end
        end)
    end
end

MyFileManager:Load();

UITab["Settings-Credits"]["Left"]["FileManager"]:AddToggle("AutoSave", { Text = "Auto Save"} ):OnChanged(function()
    MyFileManager:Save();
end);
UITab["Settings-Credits"]["Left"]["FileManager"]:AddToggle("AutoLoad", { Text = "Auto Load"} ):OnChanged(function()
    MyFileManager:Save();
end);
UITab["Settings-Credits"]["Left"]["FileManager"]:AddButton("Save", function()
    MyFileManager:Save();
    SaveManager:Save();
end);
UITab["Settings-Credits"]["Left"]["FileManager"]:AddButton("Load", function()
    SaveManager:Load();
end);
UITab["Settings-Credits"]["Left"]["FileManager"]:AddButton("Reset Settings", function()
    local file = SaveManager.Folder .. '/settings/' .. SaveManager.File .. '.json';
    if isfile(file) then
        delfile(file)
        Library:Notify("Deleted File, Please ReJoin!");
    end
end);
UITab["Settings-Credits"]["Right"]["Credits"] = UITab["Settings-Credits"]["Right"]:AddTab("Credits");
UITab["Settings-Credits"]["Right"]["Credits"]:AddLabel("Made By : 「 Kang Kung#7271 」");
UITab["Settings-Credits"]["Right"]["Credits"]:AddLabel("Discord : \nhttps://discord.gg/B659FscCBz");
UITab["Settings-Credits"]["Right"]["Credits"]:AddBlank(5);
UITab["Settings-Credits"]["Right"]["Credits"]:AddButton("Copy Link", function()
    local Http_Request = (syn and syn.request) or (http and http.request) or request;
    Http_Request({
        Url = "http://127.0.0.1:6463/rpc?v=1",
        Method = "POST",
        Headers = {
            ["Content-Type"] = "application/json",
            ["Origin"] = "https://discord.com"
        },
        Body = game:GetService("HttpService"):JSONEncode({
            cmd = "INVITE_BROWSER",
            args = {
                code = "B659FscCBz"
            },
            nonce = game:GetService("HttpService"):GenerateGUID(false)
        }),
    })
end)


Library:Notify("Loaded Krypton Hub Press Right Control For Show, Hide UI");

SaveManager:SetIgnoreIndexes({"AutoSave", "AutoLoad", "Miscellaneous:Right 2:Other:Click NPCs", "Misc 2:Left:Teleport:Teleport Island", "Misc 2:Left:Teleport:Teleport NPC"});

spawn(function()
    repeat wait() until Toggles["AutoLoad"];
    if Toggles["AutoLoad"].Value then
        MyFile:Load();
    end
end)
spawn(function()
    repeat wait() until Toggles["AutoSave"] and Toggles["AutoLoad"].Value;
    SaveManager:AutoSave();
end)
