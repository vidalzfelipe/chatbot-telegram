# 👵 Joelho de Vó – Chatbot de Clima com n8n
O Joelho de Vó é um chatbot integrado ao Telegram que consulta a previsão do tempo via OpenWeather e responde de forma divertida, simulando as “previsões” do joelho da vovó 👵🌦️.

O fluxo foi desenvolvido no n8n e utiliza:
  - Telegram Trigger
  - AI Agent (validação de cidade/UF)
  - OpenWeather API
  - Lógica condicional para intensidade do clima
  - Respostas personalizadas baseadas na condição climática
    
----------------------------------------------------------------------
## 🚀 Funcionalidades

- ✅ Recebe mensagens pelo Telegram
- ✅ Extrai cidade e UF usando IA
- ✅ Valida se a cidade pertence ao estado informado
- ✅ Consulta clima atual na OpenWeather
- ✅ Classifica o clima em:
  - ☀️ Não dói
  - 🌥️ Dói leve
  - 🌧️ Dói muito
- ✅ Responde com mensagem temática da “vó”
----------------------------------------------------------------------
## 📌 Requisitos
- Docker v29.1.2
- N8n v2.2.5
- Ngrok
- Conta OpenWeather
- Conta Telegram
- Token do Telegram gerado pelo BotFather
----------------------------------------------------------------------
## ⚙️ Configurações 
### 🐋 Docker Compose
- Para subir o docker compose, antes você precisa substituir as seguintes variáveis:
- [SEU_NGROK_TOKEN] = Seu Token gerado na página Your Authtoken do Ngrok (https://dashboard.ngrok.com/get-started/your-authtoken)
- [SEU_ENDPOINT_NGROK] = Seu Endpoint gerado na página Endpoints & Traffic Policy do Ngrok (https://dashboard.ngrok.com/endpoints)
- Substituindo as variáveis você terá acesso ao n8n atráves do seu endpoint gerado no Ngrok.
- Na sessão de Credenciais você será capaz de ver mais informações de como acessar o N8N

### 📦 Import o workflow no n8n
- Acesse a página Overview do seu N8N, clique em Workflows e em seguida em Create Workflow
<img width="1992" height="322" alt="image" src="https://github.com/user-attachments/assets/eac822c8-1769-4b86-a63f-70c6176f7f28" />

- Clique em (...) e em seguida clique em Import From File.
<img width="362" height="387" alt="image" src="https://github.com/user-attachments/assets/13206099-7369-4a63-a3cf-c4d9bb97f0c4" />

- Procure pelo arquivo workflow-chatbot-telegram.json no diretório onde você salvou o arquivo deste git
- Feito isso, o N8N irá fazer o import deste projeto
----------------------------------------------------------------------

## 🔑 Credenciais

### ⚡Ngrok
- Acesse https://dashboard.ngrok.com/signup e preencha o seu cadastro
- Ao finalizar, irá solicitar que você ative o Multi-Factor Authentication (MFA).
- Siga os passos e ative o MFA
- O site irá fazer mais perguntas para tentar entender o seu proposito com a ferramenta. Responda as perguntas e finalize o cadastro
- Com o cadastro finalizado, você terá acesso ao dashboard do NGrok
- Clique em Your Authtoken e guarde o seu token. Ele vai ser necessário pra subir o docker compose
<img width="1744" height="226" alt="image" src="https://github.com/user-attachments/assets/28a3c306-25e0-4d8f-8d3b-09c6d4b531d0" />

- Depois de salvar seu Token, clique em Endpoints & Traffic Polcy e em seguida em +New Endpoint
<img width="2032" height="223" alt="image" src="https://github.com/user-attachments/assets/b48a8013-155d-4e00-a2e3-b1e78fd3640d" />

- Clique em Cloud Endpoint
<img width="741" height="303" alt="image" src="https://github.com/user-attachments/assets/79184977-6ee1-4527-9b93-3f8b5e7e56d4" />

- Crie seu Endpoint
<img width="751" height="492" alt="image" src="https://github.com/user-attachments/assets/9f9dab1d-0d83-4f04-94b4-c1a161a408de" />

- Após finalizar você conseguirar encontra-lo na sua página de Endpoints & Traffic Policy
<img width="458" height="89" alt="image" src="https://github.com/user-attachments/assets/15513ade-b588-47e0-80c0-b8cfae03dd38" />

----------------------------------------------------------------------

### 💻 N8n
- No seu primeiro acesso ao n8n, será necessário que você faça um cadastro na plataforma
- Feito isso, valide o email, atualize a página e entre com suas credenciais
----------------------------------------------------------------------  
### 🌦️ OpenWeather
- Acesse https://home.openweathermap.org/users/sign_up e siga os passos para criar a sua conta
- Valide o link de confirmação que você receberá no email cadastrado após finalizar o cadastro
- Após confirmado, você será redirecionado para  https://home.openweathermap.org/
- Clique em “API Keys” ou acesse o link [https://home.openweathermap.org/api_keys](https://home.openweathermap.org/api_keys)
<img width="936" height="189" alt="image" src="https://github.com/user-attachments/assets/e42c83ed-1130-4d11-aae3-1739898e437b" />

- Nessa página você será capaz de visualizar todas as suas chaves. Por Padrão, a OpenWeather ja fornece uma
<img width="1514" height="417" alt="image" src="https://github.com/user-attachments/assets/fc10624a-3be0-4cb1-91cd-5db546db4183" />

- Caso queira criar uma chave nova, basta digitar o nome no campo API Key Name e clicar em Generate
<img width="358" height="161" alt="image" src="https://github.com/user-attachments/assets/e5346660-6cd5-4055-80c0-712fc1053cc7" />

- Vale ressaltar que ao criar uma key nova ela pode levar alguns minutos para ser validada mesmo que apareça como criada
- No node HTTP Request do N8N, terá um parâmetro chamado appid. Use suas chave de API onde tiver {{ $env.OPENWEATHER_API_KEY }}

----------------------------------------------------------------------

### 🤖 Token Bot do Telegram
- Para conseguir o token, você precisa ter acesso ao Telegram
- Feito o registro, procure por @BotFather no campo de busca. O perfil vai estar com simbolo de verificado
<img width="478" height="477" alt="image" src="https://github.com/user-attachments/assets/25afa4bb-d992-4084-a9d7-406282b757bc" />

- Envie o comando /newbot no campo de mensagem e siga as instruções para gerar o token.
<img width="656" height="320" alt="image" src="https://github.com/user-attachments/assets/17715b80-e5eb-4fa8-aea9-ed12e9a7ec7f" />

- Será solicitado primeiramente um nome para o bot e em seguida um username para o bot.
- Para o username, é necessário que o nome termine com bot, Exemplo: TetrisBot ou tetris_bot
- Feito isso, o BotFather irá fornecer seu token. Guarde em um local seguro
- Para o N8N poder utilizar o bot, será necessário criar credencial no n8n
- Em Overview no N8N, vá em Credentials e em seguida em Create Credential
<img width="1983" height="285" alt="image" src="https://github.com/user-attachments/assets/60e7ce15-99aa-41c4-9aed-503d7f26aef2" />

- Procure por Telegram API e clique em Continue
<img width="447" height="226" alt="image" src="https://github.com/user-attachments/assets/efbe887d-5dbb-4da9-8215-fd53ab51ec32" />

- Insira seu token e clique em Save
<img width="1176" height="466" alt="image" src="https://github.com/user-attachments/assets/8e52d28a-20f8-4d2e-9d29-eafa47e2aab0" />

----------------------------------------------------------------------
🧠 Como funciona o fluxo
Usuário envia mensagem no Telegram.
IA extrai:
  - cidade
  - UF

- Se inválido:
  - solicita correção.
- Se válido:
  - consulta OpenWeather usando:
  - cidade,UF,BR
  - Classifica condição climática.
  - Envia resposta personalizada.
----------------------------------------------------------------------
🧪 Exemplo de uso

- Usuário envia:
  - Salvador BA

- Bot responde:
📍 Em Salvador o clima é céu limpo, com temperatura de 28°C.
👵 “Hoje meu joelho tá quietinho, meu filho… céu firme que é uma beleza!”
----------------------------------------------------------------------





