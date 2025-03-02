local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()


local Window = Fluent:CreateWindow({
    Title = "MiniCezarCity" .. Fluent.Version,
    TabWidth = 160, Size = UDim2.fromOffset(580, 460), Theme = "Dark"
})


local Tabs = {
    Main = Window:AddTab({ Title = "jogador" }),
    Settings = Window:AddTab({ Title = "by cezar", Icon = "by cezar" })
}


Tabs.Main:AddButton({ Title = "auto cl", Callback = function() 

local function monitorarVida()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")

    humanoid.HealthChanged:Connect(function(health)

        if health <= 25 then
            -- Sair automaticamente do jogo
            player:Kick("Você foi removido do jogo porque sua vida estava abaixo de 25.")
        end
    end)
end
monitorarVida()
end })


Tabs.Main:AddParagraph({ Title = "auto cl ", Content = " usa um vaz para " })





Tabs.Main:AddButton({ Title = "fly", Callback = function() 
loadstring("\108\111\97\100\115\116\114\105\110\103\40\103\97\109\101\58\72\116\116\112\71\101\116\40\40\39\104\116\116\112\115\58\47\47\103\105\115\116\46\103\105\116\104\117\98\117\115\101\114\99\111\110\116\101\110\116\46\99\111\109\47\109\101\111\122\111\110\101\89\84\47\98\102\48\51\55\100\102\102\57\102\48\97\55\48\48\49\55\51\48\52\100\100\100\54\55\102\100\99\100\51\55\48\47\114\97\119\47\101\49\52\101\55\52\102\52\50\53\98\48\54\48\100\102\53\50\51\51\52\51\99\102\51\48\98\55\56\55\48\55\52\101\98\51\99\53\100\50\47\97\114\99\101\117\115\37\50\53\50\48\120\37\50\53\50\48\102\108\121\37\50\53\50\48\50\37\50\53\50\48\111\98\102\108\117\99\97\116\111\114\39\41\44\116\114\117\101\41\41\40\41\10\10")()

end })

 
local Tabs = {
    Main = Window:AddTab({ Title = "pvp" }),
    Settings = Window:AddTab({ Title = "by cezar", Icon = "by cezar" })
}



Tabs.Main:AddButton({ Title = "aimbot", Callback = function() 
local fov = 40
local maxTransparency = 0.1 -- Transparência máxima dentro do círculo (0.1 = 10% de transparência)
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local Cam = game.Workspace.CurrentCamera

local FOVring = Drawing.new("Circle")
FOVring.Visible = true
FOVring.Thickness = 2
FOVring.Color = Color3.fromRGB(128, 0, 128) -- Cor roxa
FOVring.Filled = false
FOVring.Radius = fov
FOVring.Position = Cam.ViewportSize / 2

local function updateDrawings()
    local camViewportSize = Cam.ViewportSize
    FOVring.Position = camViewportSize / 2
end

local function onKeyDown(input)
    if input.KeyCode == Enum.KeyCode.Delete then
        RunService:UnbindFromRenderStep("FOVUpdate")
        FOVring:Remove()
    end
end

UserInputService.InputBegan:Connect(onKeyDown)

local function lookAt(target)
    local lookVector = (target - Cam.CFrame.Position).unit
    local newCFrame = CFrame.new(Cam.CFrame.Position, Cam.CFrame.Position + lookVector)
    Cam.CFrame = newCFrame
end

local function calculateTransparency(distance)
    -- Ajuste a transparência com base na distância do centro do círculo
    local maxDistance = fov -- A distância máxima do centro do círculo
    local transparency = (1 - (distance / maxDistance)) * maxTransparency
    return transparency
end

local function getClosestPlayerInFOV(trg_part)
    local nearest = nil
    local last = math.huge
    local playerMousePos = Cam.ViewportSize / 2

    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= Players.LocalPlayer then
            local part = player.Character and player.Character:FindFirstChild(trg_part)
            if part then
                local ePos, isVisible = Cam:WorldToViewportPoint(part.Position)
                local distance = (Vector2.new(ePos.x, ePos.y) - playerMousePos).Magnitude

                if distance < last and isVisible and distance < fov then
                    last = distance
                    nearest = player
                end
            end
        end
    end

    return nearest
end

RunService.RenderStepped:Connect(function()
    updateDrawings()
    local closest = getClosestPlayerInFOV("Head")
    if closest and closest.Character:FindFirstChild("Head") then
        lookAt(closest.Character.Head.Position)
    end
    
    if closest then
        local ePos, isVisible = Cam:WorldToViewportPoint(closest.Character.Head.Position)
        local distance = (Vector2.new(ePos.x, ePos.y) - (Cam.ViewportSize / 2)).Magnitude
        FOVring.Transparency = calculateTransparency(distance)
    else
        FOVring.Transparency = 0.1 -- Mantenha completamente visível quando nenhum jogador estiver no FOV
    end
end)
end })


Tabs.Main:AddButton({ Title = "hitbox", Callback = function() 
_G.HeadSize = 20
_G.Disabled = true

game:GetService('RunService').RenderStepped:connect(function()
if _G.Disabled then
for i,v in next, game:GetService('Players'):GetPlayers() do
if v.Name ~= game:GetService('Players').LocalPlayer.Name then
pcall(function()
v.Character.HumanoidRootPart.Size = Vector3.new(_G.HeadSize,_G.HeadSize,_G.HeadSize)
v.Character.HumanoidRootPart.Transparency = 0.7
v.Character.HumanoidRootPart.BrickColor = BrickColor.new("Really blue")
v.Character.HumanoidRootPart.Material = "Neon"
v.Character.HumanoidRootPart.CanCollide = false
end)
end
end
end
end)
 end })



Tabs.Main:AddButton({ Title = "esp", Callback = function() 
loadstring(game:HttpGet('https://raw.githubusercontent.com/Lucasfin000/SpaceHub/main/UESP'))()

 end })


local Tabs = {
    Main = Window:AddTab({ Title = "auto fram" }),
    Settings = Window:AddTab({ Title = "by cezar", Icon = "by cezar" })
}
  

Tabs.Main:AddButton({ Title = "auto lixo", Callback = function() 

end })


Tabs.Main:AddButton({ Title = "auto plantas", Callback = function() 
loadstring(game:HttpGet('https://raw.githubusercontent.com/minicityrp/main/refs/heads/main/mobile'))()
 end })


Tabs.Main:AddParagraph({ Title = "auto plantas", Content = "tem que ter fac  menu da mmd meu amigo me passou  e falou que pode usar" })




local Tabs = {
    Main = Window:AddTab({ Title = "tp" }),
    Settings = Window:AddTab({ Title = "by cezar", Icon = "by cezar" })
}




Tabs.Main:AddButton({ Title = "tp praça", Callback = function() 
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-291.4333190917969, 4.762997627258301, 334.4155578613281)
end })



Tabs.Main:AddButton({ Title = "tp lixo", Callback = function() 
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-522.2957763671875, 4.799497604370117, -26.41012954711914)
end })



Tabs.Main:AddButton({ Title = "tp prefeitura", Callback = function() 
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2813.0810546875, -4.583141326904297, 1978.9290771484375)
 end })


Tabs.Main:AddButton({ Title = "tp garagem", Callback = function() 
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-469.88189697265625, 4.797991752624512, 361.22027587890625)
 end })
 


Window:SelectTab(1)
Fluent:Notify({ Title = "Fluent", Content = "The script has been loaded." })

