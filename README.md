-- Load Orion Library
local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/ScriptBrv/LibraryOrion/refs/heads/main/LibraryOrion"))()

-- Configuration of the main window using OrionLib
local Window = OrionLib:MakeWindow({
    Name = "Key System |Universal|",           -- Name displayed in the window and intro
    HidePremium = false,                    -- Hide premium features (false to display them)
    SaveConfig = true,                      -- Automatically save settings
    ConfigFolder = "KeySystemUniversal",    -- Folder where settings will be saved
    IntroEnabled = true,                    -- Enable intro on opening
    IntroText = "Key System |Universal|",     -- Text displayed in the intro
    IntroIcon = "rbxassetid://71065081734857"  -- ID of the icon displayed in the intro
})
        
-- Function to save the Key locally
local function saveKey(key)
    writefile("Key_Saved1.txt", key)
end

-- Function to load the saved Key
local function loadKey()
    if isfile("Key_Saved1.txt") then
        return readfile("Key_Saved1.txt")
    end
    return nil
end

-- Initial notification
OrionLib:MakeNotification({
    Name = "Logged In!",
    Content = "You are logged in as a player",
    Image = "rbxassetid://4483345998",
    Time = 5
})

-- Global variables for the Key
_G.Keys = "keysasa"
_G.KeyInput = loadKey() or ""

-- Function to start the main script
local function MakeScriptHub()
    local CentralHub =  loadstring(game:HttpGet("https://raw.githubusercontent.com/ScriptCentral-br/ScriptCentralUs/refs/heads/main/CentralUs.md"))()
end

-- Notification functions
local function CorrectKeyNotification()
    OrionLib:MakeNotification({
        Name = "Correct Key",
        Content = "You have entered the correct Key!",
        Image = "rbxassetid://4483345998",
        Time = 5
    })
end

local function IncorrectKeyNotification()
    OrionLib:MakeNotification({
        Name = "Incorrect Key",
        Content = "You have entered an incorrect Key!",
        Image = "rbxassetid://4483345998",
        Time = 5
    })
end

-- Check if the Key is already saved and correct
if _G.KeyInput == _G.Key then
    MakeScriptHub()
    CorrectKeyNotification()
else
    -- Create the Key tab
    local Tab = Window:MakeTab({
        Name = "Key",
        Icon = "rbxassetid://71897903163299",
        PremiumOnly = false
    })

    Tab:AddTextbox({
        Name = "Enter Key",
        Default = "",
        TextDisappear = true,
        Callback = function(Value)
            _G.KeyInput = Value
        end
    })

    Tab:AddButton({
        Name = "Verify Key",
        Callback = function()
            if _G.KeyInput == _G.Key then
                saveKey(_G.KeyInput)
                MakeScriptHub()
                CorrectKeyNotification()
            else
                IncorrectKeyNotification()
            end
        end
    })

    -- Create the Key acquisition tab
    local GetKeyTab = Window:MakeTab({
        Name = "Get Key!",
        Icon = "rbxassetid://71897903163299",
        PremiumOnly = false
    })

    local keyLink = "https://link-hub.net/1265230/scriptcentral-key1"
    local tutorialLink = "https://youtu.be/7XHT3mZGY8k"

    GetKeyTab:AddButton({
        Name = "Key (Link copied automatically)",
        Callback = function()
            setclipboard(keyLink)
            OrionLib:MakeNotification({
                Name = "Link Copied",
                Content = "The link for the Key has been copied to the clipboard!",
                Image = "rbxassetid://4483345998",
                Time = 5
            })
        end
    })

    GetKeyTab:AddLabel("Tutorial on how to get the Key")

    GetKeyTab:AddButton({
        Name = "Key Tutorial",
        Callback = function()
            setclipboard(tutorialLink)
            OrionLib:MakeNotification({
                Name = "Tutorial Copied",
                Content = "The tutorial link has been copied to the clipboard!",
                Image = "rbxassetid://4483345998",
                Time = 5
            })
        end
    })
end

-- Premium Accounts Tab
local MudbuxxTab = Window:MakeTab({
    Name = "Premium Accounts",
    Icon = "rbxassetid://112234897935385",
    PremiumOnly = false
})

MudbuxxTab:AddSection({ Name = "MudBuxx" })
MudbuxxTab:AddLabel("Tired of spending hours leveling up?")
MudbuxxTab:AddLabel("Mudbuxx has the best Blox Fruits accounts for you!")

MudbuxxTab:AddSection({ Name = "MudBuxx Link" })

local storeLink = "https://discord.gg/NspaGPydhC"

MudbuxxTab:AddButton({
    Name = "MudBuxx (Link copied automatically)",
    Callback = function()
        setclipboard(storeLink)
        OrionLib:MakeNotification({
            Name = "Link Copied",
            Content = "The MudBuxx link has been copied to the clipboard!",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
})

MudbuxxTab:AddLabel("Paste the link in Google or Discord!")

-- Social Media Tab
local socialTab = Window:MakeTab({
    Name = "Social Media",
    Icon = "rbxassetid://74631185733034",
    PremiumOnly = false
})

socialTab:AddLabel("My social media")

socialTab:AddButton({
    Name = "YouTube",
    Callback = function()
        setclipboard("https://www.youtube.com/@BlaZitoRobloxScript/videos")
        OrionLib:MakeNotification({
            Name = "Link Copied",
            Content = "The channel link has been copied!",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
})

socialTab:AddButton({
    Name = "Discord (Server)",
    Callback = function()
        setclipboard("https://discord.gg/NyhbVzG8qz")
        OrionLib:MakeNotification({
            Name = "Link Copied",
            Content = "The Discord link has been copied!",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
})

-- Discord Tab
local DiscordTab = Window:MakeTab({
    Name = "Discord",
    Icon = "rbxassetid://90685941326593",
    PremiumOnly = false
})

DiscordTab:AddLabel("Join our Discord")

DiscordTab:AddButton({
    Name = "Discord Link",
    Callback = function()
        setclipboard("https://discord.gg/NyhbVzG8qz")
        OrionLib:MakeNotification({
            Name = "Link Copied",
            Content = "The Discord link has been copied to the clipboard!",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
})

OrionLib:Init()
