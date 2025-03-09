--// Biblioteca Orion
local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Orion/main/source"))()

--// Configuração
local Window = OrionLib:MakeWindow({
    Name = "Sigma Universal",
    HidePremium = false,
    IntroEnabled = false,
    SaveConfig = false,
    ConfigFolder = "SigmaUniversal"
})

--// Variáveis Globais
_G.KeyInput = ""
local CorrectKey = "bravo123" -- Defina a Key correta aqui

--// Função para Salvar a Key
local function saveKey()
    writefile("SigmaUniversalKey.txt", _G.KeyInput)
end

--// Função para Carregar a Key
local function loadKey()
    if isfile("SigmaUniversalKey.txt") then
        return readfile("SigmaUniversalKey.txt")
    end
    return ""
end

_G.KeyInput = loadKey()

--// Função para Iniciar o Script Principal
local function MakeScriptHub()
    local scriptURL = "https://raw.githubusercontent.com/ScriptBrv/Sigma-Universal-Estados-Unidos/main/script.lua"
    local success, response = pcall(function()
        return loadstring(game:HttpGet(scriptURL))()
    end)
    
    if not success then
        OrionLib:MakeNotification({
            Name = "Erro ao carregar o script",
            Content = "Verifique o link do script!",
            Image = "rbxassetid://4483345998",
            Time = 5
        })
    end
end

--// Aba Principal (Login de Key)
local KeyTab = Window:MakeTab({
    Name = "🔑 Key System",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

KeyTab:AddTextbox({
    Name = "Insira a Key",
    Default = _G.KeyInput,
    TextDisappear = false,
    Callback = function(Value)
        _G.KeyInput = Value
    end
})

KeyTab:AddButton({
    Name = "Verificar Key",
    Callback = function()
        if _G.KeyInput == CorrectKey then
            OrionLib:MakeNotification({
                Name = "Sucesso!",
                Content = "Key correta! Carregando o script...",
                Image = "rbxassetid://4483345998",
                Time = 3
            })
            saveKey()
            wait(1)
            MakeScriptHub()
        else
            OrionLib:MakeNotification({
                Name = "Erro",
                Content = "Key incorreta! Tente novamente.",
                Image = "rbxassetid://4483345998",
                Time = 3
            })
        end
    end
})

--// Aba de Informações
local InfoTab = Window:MakeTab({
    Name = "ℹ️ Info",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

InfoTab:AddLabel("Sigma Universal - Versão 1.0")
InfoTab:AddLabel("Criado por BlaZito")
InfoTab:AddButton({
    Name = "Fechar GUI",
    Callback = function()
        OrionLib:Destroy()
    end
})

--// Inicializa Orion
OrionLib:Init()
