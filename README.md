local player = game.Players.LocalPlayer

-- Criar GUI
local gui = Instance.new("ScreenGui")
gui.Name = "SpeedGui"
gui.Parent = player:WaitForChild("PlayerGui")

local button = Instance.new("TextButton")
button.Size = UDim2.new(0,200,0,50)
button.Position = UDim2.new(0.5,-100,0.8,0)
button.Text = "Definir Velocidade"
button.Parent = gui
button.BackgroundColor3 = Color3.fromRGB(0,170,255)
button.TextScaled = true

button.MouseButton1Click:Connect(function()
    -- Criar caixa de texto
    local input = Instance.new("TextBox")
    input.Size = UDim2.new(0,200,0,50)
    input.Position = UDim2.new(0.5,-100,0.7,0)
    input.PlaceholderText = "Digite a velocidade"
    input.Text = ""
    input.TextScaled = true
    input.Parent = gui
    input:CaptureFocus() -- abre teclado (Gboard)

    input.FocusLost:Connect(function(enterPressed)
        if enterPressed then
            local value = tonumber(input.Text)
            if value then
                if player.Character and player.Character:FindFirstChild("Humanoid") then
                    player.Character.Humanoid.WalkSpeed = math.min(
                        value,
                        10e+938383773736363663636363736
                    )
                end
            end
            input:Destroy()
        end
    end)
end)# Roblox Speed Button

Botão para definir a velocidade do personagem no Roblox digitando um valor.

## Funções
- Botão na tela
- Abre teclado (Gboard)
- Aceita números gigantes (ex: 10e+938383773736363663636363736)
- Altera WalkSpeed

## Como usar
1. Abra o Roblox Studio
2. Vá em StarterPlayer > StarterPlayerScripts
3. Crie um LocalScript
4. Cole o código do arquivo SpeedButton.lua
5. Execute o jogo

Compatível com mobile (Android)