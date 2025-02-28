- 👋 Hi, I’m @snybasse
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ... goncalvesmartinsbernardo7@gmail.com
- 😄 Pronouns: ...ele
- ⚡ Fun fact: ...

<!---
snybasse/snybasse is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->







-- Script do RC7

-- Crie um novo objeto do tipo "Player" com o nome "Player1"
local player = Instance.new("Player")
player.Name = "Player1"

-- Mude a posição do jogador para (0, 0, 0)
player.Character.HumanoidRootPart.CFrame = CFrame.new(0, 0, 0)

-- Adicione um novo objeto do tipo "Tool" com o nome "Tool1" ao jogador
local tool = Instance.new("Tool")
tool.Name = "Tool1"
player.Character:FindFirstChild("Tool").Parent = tool

-- Adicione um novo objeto do tipo "Script" com o nome "Script1" ao jogador
local script = Instance.new("Script")
script.Name = "Script1"
player.Character:FindFirstChild("Script").Parent = script

-- Defina uma função que seja chamada quando o jogador pressiona o botão "E"
local function onEPressed()
    print("Botão E pressionado!")
end

-- Conecte a função ao evento "InputBegan" do jogador
player:WaitForChild("InputBegan"):Connect(onEPressed)
