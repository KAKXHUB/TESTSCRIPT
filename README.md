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
    Quest = Window:AddTab({ Title = "Quest", Icon = "clipboard" }),
    Start = Window:AddTab({ Title = "Stats", Icon = "chart-column" }),
    Playerss = Window:AddTab({ Title = "Players", Icon = "users" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Cache = { DevConfig = {} };

Cache.DevConfig["ListOfBox"] = {"Common Box", "Uncommon Box", "Rare Box", "Ultra Rare Box"};
Cache.DevConfig["ListOfDrink"] = {"Cider+", "Lemonade+", "Juice+", "Smoothie+"};
Cache.DevConfig["ListOfDrinkFormMixer"] = {"Cider", "Lemonade", "Juice", "Smoothie", "Milk", "Golden Apple"};




local Options = Fluent.Options

do

    local Section = Tabs.Main:AddSection("Farm Beri")


    Tabs.Main:AddParagraph({
        Title = "Position",
        Content = "Birth point"
    })

    Tabs.Main:AddButton({
        Title = "Set Position",
        Description = "Set the spawn point on the boss island.",
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
        Description = "Set the spawn point at your location.",
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
        Description = "Reset your spawn point",
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
        Description = "To the safe zone",
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

        Tabs.Main:AddButton({
        Title = "Reset Player",
        Description = "Reset player list",
        Callback = function()
            players = {}

            for i,v in pairs(game:GetService("Players"):GetChildren()) do
        
            table.insert(players,v.Name)
        
        
            DropdownPlayer:SetValue(players)
            end
        end
    })

        Tabs.Main:AddButton({
        Title = "Teleport Player",
        Description = "Teleport To Player",
        Callback = function()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Options.DropdownPlayer.Value).Character.HumanoidRootPart.Position + Vector3.new(0, 5, 0));
        end
    })






end


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
