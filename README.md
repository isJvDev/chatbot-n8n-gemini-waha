# 🍕 Chatbot WhatsApp da Pizzaria FATEC com IA (Gemini)

## 🌟 Visão Geral do Projeto

Este projeto demonstra a criação de um **chatbot de atendimento ao cliente** para WhatsApp usando a plataforma de automação **n8n**. O bot, chamado **"Miguel"**, é alimentado por inteligência artificial (Google Gemini) e utiliza o Redis para manter o contexto da conversa.

O objetivo é simular um processo completo de pedidos de pizza, desde o primeiro contato até a confirmação do pedido, sem a necessidade de múltiplos nós de *Switch* ou *Set* no n8n.

### ⚙️ Componentes Principais (Tecnologias)

| Componente | Função no Fluxo | Serviço Docker |
| :--- | :--- | :--- |
| **n8n** | Orquestração do Workflow e Lógica Central | `n8nio/n8n` |
| **AI Agent (Gemini)** | Processamento da Linguagem Natural e Lógica de Negócio (Cardápio, Cálculo, Fluxo) | - (Conectado via API) |
| **Redis** | Memória do Chat (Persistência do Histórico da Conversa) | `redis:latest` |
| **WAHA** | Gateway de Comunicação com o WhatsApp | `devlikeapro/waha` |

---

## 🏗️ Estrutura do Repositório

```text
meu-projeto-n8n-ia/
│
├── workflows/
│   └── whatsapp-gemini-agent.json   <-- O fluxo do n8n
│
├── .env.example                     <-- Variáveis de ambiente necessárias
├── docker-compose.yml               <-- Configuração completa da infraestrutura
└── README.md                        <-- Este arquivo

📋 Pré-requisitos
Para rodar este projeto, você precisará ter instalado e configurado:

Docker & Docker Compose: Para gerenciar os serviços n8n, Redis e WAHA.

Chave de API do Google AI Studio: Para acesso ao modelo Gemini (o nó Gemini exige esta credencial).

Configuração de WhatsApp: Acesso a uma instância WAHA (ou similar) funcionando e pronta para receber e enviar webhooks.

🛠️ Configuração e Inicialização
Siga os passos abaixo para colocar o projeto em funcionamento.

Passo 1: Obter os arquivos e o .env
Clone este repositório para sua máquina local.

Crie um arquivo chamado .env na raiz do projeto (copiando do .env.example).

Preencha as variáveis de ambiente necessárias (principalmente as senhas):
# Variáveis de Configuração
REDIS_PASSWORD=SUA_SENHA_AQUI
WAHA_API_KEY=SUA_CHAVE_WAHA
WAHA_USER=admin
WAHA_PASSWORD=sua_senha_do_dashboard

(Importante: O GOOGLE_AI_API_KEY deve ser configurado diretamente como Credencial dentro da interface do n8n, usando o tipo Google Gemini(PaLM) API).

Passo 2: Inicializar os Containers
Execute o docker-compose.yml para iniciar todos os serviços:
No terminal digite: docker compose up -d
Verifique se os três serviços (n8n, redis e waha) subiram corretamente.

Passo 3: Configurar o n8n e Importar o Fluxo
Acesse a interface do n8n em http://localhost:5678.

Importe o arquivo workflows/whatsapp-gemini-agent.json.

Crie as Credenciais:

Crie uma credencial para Google Gemini(PaLM) API usando sua chave.

Crie uma credencial para Redis usando as informações de host (redis) e a senha do seu arquivo .env.

Crie uma credencial para WAHA usando o endpoint e a chave de API (Host: http://localhost:3000, API Key: SUA_CHAVE_WAHA).

Conecte as Credenciais: No fluxo importado, clique nos nós Google Gemini Chat Model, Redis Chat Memory e WAHA, e selecione as credenciais que você acabou de criar.

Ativar o Fluxo: Ative o workflow para que o Webhook (URL de produção) seja ligado.

Passo 4: Conectar o WhatsApp
Acesse o dashboard do WAHA em http://localhost:3000 (Use o usuário/senha do .env).

Escaneie o QR Code para conectar sua conta do WhatsApp.

Quando a conexão estiver pronta, o WAHA começará a enviar mensagens recebidas para o Webhook do n8n, em http://n8n:5678/webhook/webhook.

Ótimo! Criar um README.md bem estruturado é essencial para o seu projeto no GitHub, pois ele serve como o manual de instruções e a vitrine do seu trabalho.

Vou te dar um modelo completo, formatado em Markdown, que você pode copiar, colar e adaptar. Ele inclui todos os detalhes do seu fluxo (Webhook, Gemini, Redis e WAHA).

🚀 Modelo de README.md
Markdown

# 🍕 Chatbot WhatsApp da Pizzaria FATEC com IA (Gemini)

## 🌟 Visão Geral do Projeto

Este projeto demonstra a criação de um **chatbot de atendimento ao cliente** para WhatsApp usando a plataforma de automação **n8n**. O bot, chamado **"Miguel"**, é alimentado por inteligência artificial (Google Gemini) e utiliza o Redis para manter o contexto da conversa.

O objetivo é simular um processo completo de pedidos de pizza, desde o primeiro contato até a confirmação do pedido, sem a necessidade de múltiplos nós de *Switch* ou *Set* no n8n.

### ⚙️ Componentes Principais (Tecnologias)

| Componente | Função no Fluxo | Serviço Docker |
| :--- | :--- | :--- |
| **n8n** | Orquestração do Workflow e Lógica Central | `n8nio/n8n` |
| **AI Agent (Gemini)** | Processamento da Linguagem Natural e Lógica de Negócio (Cardápio, Cálculo, Fluxo) | - (Conectado via API) |
| **Redis** | Memória do Chat (Persistência do Histórico da Conversa) | `redis:latest` |
| **WAHA** | Gateway de Comunicação com o WhatsApp | `devlikeapro/waha` |

---

## 🏗️ Estrutura do Repositório

```text
meu-projeto-n8n-ia/
│
├── workflows/
│   └── whatsapp-gemini-agent.json   <-- O fluxo do n8n
│
├── .env.example                     <-- Variáveis de ambiente necessárias
├── docker-compose.yml               <-- Configuração completa da infraestrutura
└── README.md                        <-- Este arquivo
📋 Pré-requisitos
Para rodar este projeto, você precisará ter instalado e configurado:

Docker & Docker Compose: Para gerenciar os serviços n8n, Redis e WAHA.

Chave de API do Google AI Studio: Para acesso ao modelo Gemini (o nó Gemini exige esta credencial).

Configuração de WhatsApp: Acesso a uma instância WAHA (ou similar) funcionando e pronta para receber e enviar webhooks.

🛠️ Configuração e Inicialização
Siga os passos abaixo para colocar o projeto em funcionamento.

Passo 1: Obter os arquivos e o .env
Clone este repositório para sua máquina local.

Crie um arquivo chamado .env na raiz do projeto (copiando do .env.example).

Preencha as variáveis de ambiente necessárias (principalmente as senhas):

Ini, TOML

# Variáveis de Configuração
REDIS_PASSWORD=SUA_SENHA_AQUI
WAHA_API_KEY=SUA_CHAVE_WAHA
WAHA_USER=admin
WAHA_PASSWORD=sua_senha_do_dashboard
(Importante: O GOOGLE_AI_API_KEY deve ser configurado diretamente como Credencial dentro da interface do n8n, usando o tipo Google Gemini(PaLM) API).

Passo 2: Inicializar os Containers
Execute o docker-compose.yml para iniciar todos os serviços:

Bash

docker compose up -d
Verifique se os três serviços (n8n, redis e waha) subiram corretamente.

Passo 3: Configurar o n8n e Importar o Fluxo
Acesse a interface do n8n em http://localhost:5678.

Importe o arquivo workflows/whatsapp-gemini-agent.json.

Crie as Credenciais:

Crie uma credencial para Google Gemini(PaLM) API usando sua chave.

Crie uma credencial para Redis usando as informações de host (redis) e a senha do seu arquivo .env.

Crie uma credencial para WAHA usando o endpoint e a chave de API (Host: http://localhost:3000, API Key: SUA_CHAVE_WAHA).

Conecte as Credenciais: No fluxo importado, clique nos nós Google Gemini Chat Model, Redis Chat Memory e WAHA, e selecione as credenciais que você acabou de criar.

Ativar o Fluxo: Ative o workflow para que o Webhook (URL de produção) seja ligado.

Passo 4: Conectar o WhatsApp
Acesse o dashboard do WAHA em http://localhost:3000 (Use o usuário/senha do .env).

Escaneie o QR Code para conectar sua conta do WhatsApp.

Quando a conexão estiver pronta, o WAHA começará a enviar mensagens recebidas para o Webhook do n8n, em http://n8n:5678/webhook/webhook.

🧠 Lógica do Agente (System Prompt)
O agente de IA está configurado com as seguintes regras de negócio no systemMessage:

Identidade: "Miguel, atendente virtual da Pizzaria FATEC."

Fluxos: Gerencia os fluxos de Fazer Pedido, Consultar Cardápio, Status do Pedido e Encerrar.

Memória: Utiliza o Redis para lembrar o passo exato em que o cliente parou (por exemplo, após escolher o tamanho e antes de escolher o sabor).

Cálculo: Implementa regras fixas de preço para calcular o valor total do pedido.