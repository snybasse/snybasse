- 👋 Hi, I’m @snybasse
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ... goncalvesmartinsbernardo7@gmail.com
- 😄 Pronouns: ...ele
- ⚡ Fun fact: ...

<!---
snybasse/snybasse is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your 








local Players = game:GetService("Players")
local Workspace = game.Workspace

print("👤 Clone Repulsor do rhhrfuy Ativado!")

-- Função para alertar os jogadores
local function enviarMensagem(texto)
	for _, player in pairs(Players:GetPlayers()) do
		if player:FindFirstChild("PlayerGui") then
			local mensagem = Instance.new("Message")
			mensagem.Parent = player.PlayerGui
			mensagem.Text = texto
			wait(3)
			mensagem:Destroy()
		end
	end
end

-- Função para criar o Clone Repulsor do jogador "rhhrfuy"
local function criarCloneRepulsor()
	-- Verifica se o jogador "rhhrfuy" está no jogo
	local jogadorAlvo = Players:FindFirstChild("rhhrfuy")
	if not jogadorAlvo or not jogadorAlvo.Character or not jogadorAlvo.Character:FindFirstChild("HumanoidRootPart") then
		print("❌ Jogador rhhrfuy não encontrado!")
		return
	end

	-- Cria o clone do "rhhrfuy"
	local clone = jogadorAlvo.Character:Clone()
	clone.Parent = Workspace
	clone:SetPrimaryPartCFrame(jogadorAlvo.Character.HumanoidRootPart.CFrame + Vector3.new(0, 5, 0))
	clone.Name = "CloneRepulsor"

	-- Adiciona a área que empurra os jogadores
	local clonePart = clone:FindFirstChild("HumanoidRootPart")
	if clonePart then
		local repulsor = Instance.new("Part")
		repulsor.Size = Vector3.new(10, 10, 10)
		repulsor.Transparency = 1 -- Invisível
		repulsor.Anchored = true
		repulsor.Position = clonePart.Position
		repulsor.Parent = Workspace

		-- Empurra quem chegar perto
		repulsor.Touched:Connect(function(hit)
			local humanoid = hit.Parent:FindFirstChild("Humanoid")
			if humanoid and hit.Parent ~= clone then
				local forca = Instance.new("BodyVelocity")
				forca.MaxForce = Vector3.new(100000, 100000, 100000)
				forca.Velocity = (hit.Position - clonePart.Position).unit * 300 -- Empurra forte!
				forca.Parent = hit.Parent:FindFirstChild("HumanoidRootPart")
				game.Debris:AddItem(forca, 0.5) -- Remove a força após 0.5 segundos
			end
		end)

		-- Mantém o repulsor seguindo o clone
		while clone.Parent do
			repulsor.Position = clonePart.Position
			wait(0.1)
		end
		repulsor:Destroy()
	end

	-- Remove o clone após 30 segundos
	enviarMensagem("👤 O Clone Repulsor de rhhrfuy apareceu! Cuidado para não ser lançado!")
	game.Debris:AddItem(clone, 30) -- Clone some depois de 30 segundos
end

-- Cria o Clone Repulsor a cada 20 segundos
while true do
	wait(20)
	criarCloneRepulsor()
end
