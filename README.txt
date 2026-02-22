👵 Joelho de Vó – Chatbot de Clima com n8n

O Joelho de Vó é um chatbot integrado ao Telegram que consulta a previsão do tempo via OpenWeather e responde de forma divertida, simulando as “previsões” do joelho da vovó 👵🌦️.

O fluxo foi desenvolvido no n8n e utiliza:

Telegram Trigger

AI Agent (validação de cidade/UF)

OpenWeather API

Lógica condicional para intensidade do clima

Respostas personalizadas baseadas na condição climática

🚀 Funcionalidades

✅ Recebe mensagens pelo Telegram
✅ Extrai cidade e UF usando IA
✅ Valida se a cidade pertence ao estado informado
✅ Consulta clima atual na OpenWeather
✅ Classifica o clima em:

☀️ Não dói

🌥️ Dói leve

🌧️ Dói muito
✅ Responde com mensagem temática da “vó”

📦 Como importar o workflow no n8n

Abra o n8n.

Vá em Workflows.

Clique em Import from File.

Selecione o arquivo JSON do workflow.

Salve.

Ative o workflow.

🔑 Configuração de Credenciais

O projeto utiliza duas integrações externas:

Telegram Bot API

OpenWeather API

Você deve configurar as credenciais antes de ativar o workflow.

🌦️ OpenWeather
1️⃣ Criar conta

Acesse:
https://openweathermap.org/api

Crie uma conta e gere sua API Key.

2️⃣ Definir variável de ambiente (recomendado)

No servidor onde o n8n está rodando, defina:

export OPENWEATHER_API_KEY="sua_chave_aqui"

Ou no Docker:

- OPENWEATHER_API_KEY=sua_chave_aqui
3️⃣ No node HTTP Request do n8n

No parâmetro appid, use:

{{$env.OPENWEATHER_API_KEY}}
🔎 Variável esperada
OPENWEATHER_API_KEY
🤖 Telegram Bot
1️⃣ Criar bot

Abra o Telegram.

Procure por @BotFather.

Digite:

/start
/newbot

Escolha nome e username.

Copie o Bot Token gerado.

2️⃣ Definir variável de ambiente (opcional)
export TELEGRAM_BOT_TOKEN="seu_token_aqui"

Ou no Docker:

- TELEGRAM_BOT_TOKEN=seu_token_aqui
3️⃣ Criar credencial no n8n

Vá em Credentials

Clique em New

Escolha Telegram API

Cole o token

Salve

🔎 Variável esperada
TELEGRAM_BOT_TOKEN
🧠 Como funciona o fluxo

Usuário envia mensagem no Telegram.

IA extrai:

cidade

UF

Se inválido → solicita correção.

Se válido → consulta OpenWeather usando:

cidade,UF,BR

Classifica condição climática.

Envia resposta personalizada.

🔐 Segurança

⚠️ Nunca exponha sua API Key diretamente no workflow.

Use:

Variáveis de ambiente

Credenciais do n8n

Nunca commit tokens no Git

🧪 Exemplo de uso

Usuário envia:

Salvador BA

Bot responde:

📍 Em Salvador o clima é céu limpo, com temperatura de 28°C.

👵 “Hoje meu joelho tá quietinho, meu filho… céu firme que é uma beleza!”
📁 Estrutura esperada de variáveis
Variável	Descrição
OPENWEATHER_API_KEY	Chave da API OpenWeather
TELEGRAM_BOT_TOKEN	Token do bot do Telegram
📌 Requisitos

n8n

Conta OpenWeather

Bot criado no Telegram

Node HTTP Request configurado

Node Telegram configurado