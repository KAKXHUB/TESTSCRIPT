local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "AUTOFARM " .. Fluent.Version,
    SubTitle = "by PeetJKA",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

local Tabs = {
    Main = Window:AddTab({ Title = "Main", Icon = "gem" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" }),
    Quest = Window:AddTab({ Title = "Quest", Icon = "briefcase-business" }),
    Start = Window:AddTab({ Title = "Start", Icon = "chart-bar" }),
    Playerss = Window:AddTab({ Title = "Players", Icon = "users" })
}

local Cache = { DevConfig = {} };

Cache.DevConfig["ListOfBox"] = {"Common Box", "Uncommon Box", "Rare Box", "Ultra Rare Box"};
Cache.DevConfig["ListOfDrink"] = {"Cider+", "Lemonade+", "Juice+", "Smoothie+"};
Cache.DevConfig["ListOfDrinkFormMixer"] = {"Cider", "Lemonade", "Juice", "Smoothie", "Milk", "Golden Apple"};




local Options = Fluent.Options



    local Section = Tabs.Main:AddSection("Farm Beri")


    Tabs.Main:AddParagraph({
        Title = "Position",
        Content = "This is a paragraph.\nSecond line!"
    })

    Tabs.Main:AddButton({
        Title = "Set Position",
        Description = "Very important button",
        Callback = function()
            game.Workspace.Spawns.Spawn1.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn2.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn3.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn4.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn5.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn6.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn8.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn9.CFrame = CFrame.new(-1558, 215, 9935)
            game.Workspace.Spawns.Spawn10.CFrame = CFrame.new(-1558, 215, 9935)
        end
    })

    
    Tabs.Main:AddButton({
        Title = "Set Positio(ตั้งที่เกิดเอง)",
        Description = "Very important button",
        Callback = function()
            local Content = game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
                game.Workspace.Spawns.Spawn1.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn2.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn3.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn4.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn5.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn6.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn7.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn8.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn9.CFrame = CFrame.new(Content)
                game.Workspace.Spawns.Spawn10.CFrame = CFrame.new(Content)
        end
    })

    Tabs.Main:AddButton({
        Title = "Reset Position",
        Description = "Very important button",
        Callback = function()
            local Content = game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
            game.Workspace.Spawns.Spawn1.CFrame = CFrame.new(-8, 213.710159, -296)
            game.Workspace.Spawns.Spawn2.CFrame = CFrame.new(-128, 213.710159, -753)
            game.Workspace.Spawns.Spawn3.CFrame = CFrame.new(45, 221.710159, -72)
            game.Workspace.Spawns.Spawn4.CFrame = CFrame.new(-237, 222.710159, -1108)
            game.Workspace.Spawns.Spawn5.CFrame = CFrame.new(-206, 221.710159, -110.5)
            game.Workspace.Spawns.Spawn6.CFrame = CFrame.new(-76, 212.710159, -892)
            game.Workspace.Spawns.Spawn7.CFrame = CFrame.new(-428, 213.710159, -154)
            game.Workspace.Spawns.Spawn8.CFrame = CFrame.new(-127, 217, -983.200012)
            game.Workspace.Spawns.Spawn9.CFrame = CFrame.new(720, 237, 1191.80005)
            game.Workspace.Spawns.Spawn10.CFrame = CFrame.new(-1281.5, 213.710159, -1353)
        end
    })

    local Toggle = Tabs.Main:AddToggle("MyToggleSTD", {Title = "Start Auto Die", Default = false })


    spawn(function()
        while wait(3) do
            pcall(function()
                if Options.MyToggleSTD.Value then
                    if game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible then
                        wait(3)
                        firesignal(game.Players.LocalPlayer.PlayerGui.Load.Frame.Load.MouseButton1Click)
                        wait(3)
                        repeat
                            local player = game.Players.LocalPlayer
                            local character = player.Character or player.CharacterAdded:Wait()
                            local humanoid = character:FindFirstChildOfClass("Humanoid")

                            if humanoid then
                                humanoid.Health = 0
                            end
                            wait(0.1)
                        until game.Players.LocalPlayer.PlayerGui.Load.Frame.Visible
                    end
                end
            end)
        end
    end)


    local Section = Tabs.Main:AddSection("Player2")


    Tabs.Main:AddButton({
        Title = "Save Zone",
        Description = "Very important button",
        Callback = function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Vector3.new(100000, 3500, 80000));
            local Base = Instance.new("Part", game.Workspace);
            Base.Size = Vector3.new(50, 1, 50);
            Base.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0, -3, 0);
            Base.Anchored = true;
        end
    })


    players = {}

    for i,v in pairs(game:GetService("Players"):GetChildren()) do

    table.insert(players,v.Name)

    end
    
    local Dropdown = Tabs.Main:AddDropdown("DropdownPlayer", {
        Title = "Select Players",
        Values = players,
        Multi = false,
        Default = 1
    })


    DropdownPlayer:OnChanged(function(ValueSelectPlayer)
        SelectPlayer = ValueSelectPlayer
    end)

    Tabs.Main:AddButton({
        Title = "Reset Player",
        Description = "Very important button",
        Callback = function()
            DropdownPlayer:SetValue(players)
        end
    })

    Tabs.Main:AddButton({
        Title = "Teleport Player",
        Description = "Very important button",
        Callback = function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(SelectPlayer).Character.HumanoidRootPart.Position + Vector3.new(0, 5, 0));
        end
    })


    local Section = Tabs.Quest:AddSection("Sam Quest")


    local Toggle = Tabs.Quest:AddToggle("MyToggleASQ", {Title = "Auto Sam Quest", Default = false })
    local Toggle = Tabs.Quest:AddToggle("MyToggleACQ", {Title = "Auto Compass Quest", Default = false })
    local Toggle = Tabs.Quest:AddToggle("MyToggleAUB", {Title = "Auto Unbox Box", Default = false })
    local Toggle = Tabs.Quest:AddToggle("MyToggleALTF", {Title = "Loot Fruit , Compass", Default = false })


    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleASQ.Value then return end;
                game.Workspace.Merchants.QuestMerchant.Clickable.Retum:FireServer("Claim1");
            end)
        end
    end);

    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleACQ.Value then return end;
                local Compass = game.Players.LocalPlayer.Backpack:FindFirstChild("Compass");
                local Compass2 = game.Players.LocalPlayer.Character:FindFirstChild("Compass");
                if Compass or Compass2 then
                    local OldPostiton = game.Players.LocalPlayer.Character.HumanoidRootPart.Position;
                    game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                    Compass.Parent = game.Players.LocalPlayer.Character;
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Compass.Poser.Value);
                    Compass:Activate();
                    wait(1);
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(OldPostiton);
                end
            end)
        end
    end);

    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleAUB.Value then return end;
                for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                    if table.find(Cache.DevConfig["ListOfBox"], Value.Name) then
                        game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                        Value.Parent = game.Players.LocalPlayer.Character;
                        Value:Activate();
                    end
                end
            end)
        end
    end);

    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleALTF.Value then return end; 
                    for i, v in pairs(game.Workspace.Trees.Tree.Model:GetChildren()) do
                        if v.ClassName == "Tool" then
                            fireclickdetector(v.Main.ClickDetector)
                        end
                    end
                    for i, v in pairs(game.Workspace:GetChildren()) do
                        if string.match(v.Name, "Box") and v:FindFirstChild("Handle") then
                            v.Handle.CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position)
                        end
                    end
            end)
        end
    end);
    
    local Section = Tabs.Quest:AddSection("Auto Claim")

    local Toggle = Tabs.Quest:AddToggle("MyToggleATCHR", {Title = "Auto Claim Hourly Reward", Default = false })
    local Toggle = Tabs.Quest:AddToggle("MyToggleATCDRW", {Title = "Auto Claim Daily Reward", Default = false })


    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleATCHR.Value then return end;
                game.Workspace.UserData["User_" .. game.Players.LocalPlayer.UserId].ClaimRewardHourly:FireServer("RewardMark");
            end)
        end
    end);
    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleATCDRW.Value then return end;
                game.Workspace.UserData["User_" .. game.Players.LocalPlayer.UserId].ClaimRewardDaily:FireServer("RewardMark");
            end)
        end
    end);

------------------------------------

    local Section = Tabs.Start:AddSection("Drink")

    local Dropdown = Tabs.Start:AddDropdown("DropdownSelectDrink", {
        Title = "Select Drink",
        Values = Cache.DevConfig["ListOfDrink"],
        Multi = false,
        Default = 1
    })

    DropdownSelectDrink:OnChanged(function(ValueSelectDrink)
        SelectDrink = ValueSelectDrink
    end)

    local Input = Tabs.Start:AddInput("InputDrink", {
        Title = "Amount Drink",
        Default = "Default",
        Placeholder = "Placeholder",
        Numeric = false, 
        Finished = false
    })

    Tabs.Start:AddButton({
        Title = "Buy Drink",
        Description = "Very important button",
        Callback = function()
            if not InputDrink.Value or not string.match(InputDrink.Value, "%d+") or tonumber(string.match(InputDrink.Value, "%d+")) < 0 then return end;
            for _ = 1, tonumber(string.match(InputDrink.Value, "%d+")) do
                game.Workspace.Merchants.BetterDrinkMerchant.Clickable.Retum:FireServer(SelectDrink)
            end
        end
    })

    local Toggle = Tabs.Start:AddToggle("MyToggleATDWT", {Title = "Auto Drink", Default = false })

    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleATDWT.Value then return end;
                for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                    if table.find(Cache.DevConfig["ListOfDrink"], Value.Name) then
                        game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                        Value.Parent = game.Players.LocalPlayer.Character;
                        Value:Activate();
                    end
                end
            end)
        end
    end);

    local Toggle = Tabs.Start:AddToggle("MyToggleATDDWT", {Title = "Auto Drop Drink", Default = false })

    spawn(function()
        while wait() do
            pcall(function()
                if not Options.MyToggleATDDWT.Value then return end;
                for _, Value in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                    if table.find(Cache.DevConfig["ListOfDrink"], Value.Name) then
                        game.Players.LocalPlayer.Character.Humanoid:UnequipTools();
                        Value.Parent = game.Players.LocalPlayer.Character;
                        Value.Parent = game.Workspace;
                    end
                end
            end)
        end
    end);

    -------------------------------

    local Section = Tabs.Playerss:AddSection("Setting Taget")

    
    local Dropdown = Tabs.Playerss:AddDropdown("DropdownPlayerrr", {
        Title = "Select Players",
        Values = players,
        Multi = false,
        Default = 1
    })


    DropdownPlayerrr:OnChanged(function(ValueSelectPlayerrrr)
        SelectPlayerrrr = ValueSelectPlayerrrr
    end)

    Tabs.Playerss:AddButton({
        Title = "Reset Player",
        Description = "Very important button",
        Callback = function()
            DropdownPlayerrr:SetValue(players)
        end
    })


    local Slider = Tabs.Playerss:AddSlider("SliderDistancePlayer", {
        Title = "Distance",
        Description = "This is a slider",
        Default = 6,
        Min = -16,
        Max = 16,
        Rounding = 1,
        Callback = function(ValueDistancePLY)
            DistancePlayer = tonumber(ValueDistancePLY)
        end
    })



    local Section = Tabs.Playerss:AddSection("About Taget")

    Tabs.Playerss:AddButton({
        Title = "Teleport Player",
        Description = "Very important button",
        Callback = function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(SelectPlayerrrr).Character.HumanoidRootPart.Position + Vector3.new(0, 5, 0));
        end
    })

    local Toggle = Tabs.Playerss:AddToggle("MyToggleLTLPP", {Title = "Loop Teleport", Default = false })
    local Toggle = Tabs.Playerss:AddToggle("MyToggleBPLY", {Title = "Bring Player", Default = false })
    local Toggle = Tabs.Playerss:AddToggle("MyToggleVPRY", 
    {
        Title = "View Player", 
        Description = "Toggle description",
        Default = false
        Callback = function(state)
            if state then
                game.Workspace.CurrentCamera.CameraSubject = SelectPlayerrrr.Character.Humanoid
            else
                game.Workspace.CurrentCamera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid
            end
        end 
    })


    spawn(function()
        while wait() do
            pcall(function()
                local Ply = SelectPlayerrrr
                if Options.MyToggleBPLY.Value then
                    Ply.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 2) + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * DistancePlayer
                end
                if Options.MyToggleLTLPP.Valuet then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =  Ply.Character.HumanoidRootPart.CFrame * CFrame.new(2, 0, 0) + Ply.Character.HumanoidRootPart.CFrame.lookVector * DistancePlayer
                end
            end)
        end
    end)




-- Addons:
-- SaveManager (Allows you to have a configuration system)
-- InterfaceManager (Allows you to have a interface managment system)

-- Hand the library over to our managers
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

-- Ignore keys that are used by ThemeManager.
-- (we dont want configs to save themes, do we?)
SaveManager:IgnoreThemeSettings()

-- You can add indexes of elements the save manager should ignore
SaveManager:SetIgnoreIndexes({})

-- use case for doing it this way:
-- a script hub could have themes in a global folder
-- and game configs in a separate folder per game
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")

InterfaceManager:BuildInterfaceSection(Tabs.Settings)
SaveManager:BuildConfigSection(Tabs.Settings)


Window:SelectTab(1)

Fluent:Notify({
    Title = "Fluent",
    Content = "The script has been loaded.",
    Duration = 8
})

-- You can use the SaveManager:LoadAutoloadConfig() to load a config
-- which has been marked to be one that auto loads!
SaveManager:LoadAutoloadConfig()
