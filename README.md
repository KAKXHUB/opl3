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
