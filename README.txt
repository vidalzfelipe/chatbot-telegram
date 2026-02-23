👵 Joelho de Vó – Chatbot de Clima com n8n

O Joelho de Vó é um chatbot integrado ao Telegram que consulta a previsão do tempo via OpenWeather e responde de forma divertida, simulando as “previsões” do joelho da vovó 👵🌦️.
O fluxo foi desenvolvido no n8n e utiliza:
  - Telegram Trigger
  - AI Agent (validação de cidade/UF)
  - OpenWeather API
  - Lógica condicional para intensidade do clima
  - Respostas personalizadas baseadas na condição climática
----------------------------------------------------------------------
📌 Requisitos

- Docker
- N8n
- Conta OpenWeather
- Bot criado no Telegram
----------------------------------------------------------------------
🚀 Funcionalidades

✅ Recebe mensagens pelo Telegram
✅ Extrai cidade e UF usando IA
✅ Valida se a cidade pertence ao estado informado
✅ Consulta clima atual na OpenWeather
✅ Classifica o clima em:
  - ☀️ Não dói
  - 🌥️ Dói leve
  - 🌧️ Dói muito
✅ Responde com mensagem temática da “vó”
----------------------------------------------------------------------
📦 Como importar o workflow no n8n

Abra o n8n.
Vá em Workflows.
Clique em Import from File.
Selecione o arquivo JSON do workflow.
Salve.
Ative o workflow.
----------------------------------------------------------------------
🔑 Configuração de Credenciais
O projeto utiliza duas integrações externas:
  - Telegram Bot API
  - OpenWeather API
Você deve configurar as credenciais antes de ativar o workflow.

🌦️ OpenWeather
1️⃣ Criar conta
Acesse:
  - https://openweathermap.org/api
Crie uma conta e gere sua API Key.

2️⃣ No node HTTP Request do n8n
No parâmetro appid, use suas chave de API onde tiver OPENWEATHER_API_KEY

🤖 Telegram Bot
1️⃣ Criar bot
Abra o Telegram.
Procure por @BotFather.
Digite:
/start
/newbot
Escolha nome e username.
Copie o Bot Token gerado.

2️⃣ Criar credencial no n8n
Vá em Credentials
Clique em New
Escolha Telegram API
Cole o token
Salve
----------------------------------------------------------------------
🧠 Como funciona o fluxo
Usuário envia mensagem no Telegram.
IA extrai:
  - cidade
  - UF

Se inválido → solicita correção.
Se válido → consulta OpenWeather usando:
cidade,UF,BR
Classifica condição climática.
Envia resposta personalizada.
----------------------------------------------------------------------
🧪 Exemplo de uso

Usuário envia:
Salvador BA

Bot responde:
📍 Em Salvador o clima é céu limpo, com temperatura de 28°C.
👵 “Hoje meu joelho tá quietinho, meu filho… céu firme que é uma beleza!”
----------------------------------------------------------------------



