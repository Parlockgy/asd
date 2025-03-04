local Players = game:GetService("Players")

local function playAnimation(player)
    local humanoid = player.Character and player.Character:FindFirstChild("Humanoid")
    if humanoid then
        local animation = Instance.new("Animation")
        animation.AnimationId = "rbxassetid://74595342687040"
        
        local animator = humanoid:FindFirstChild("Animator")
        if not animator then
            animator = Instance.new("Animator")
            animator.Parent = humanoid
        end
        
        local track = animator:LoadAnimation(animation)
        track:Play()
        
        wait(10)  -- Espera 10 segundos
        
        track:Stop()  -- Para a animação
    end
end

for _, player in ipairs(Players:GetPlayers()) do
    player.CharacterAdded:Connect(function(character)
        wait(1)  -- Garantir que o personagem foi totalmente carregado
        playAnimation(player)
    end)
end
