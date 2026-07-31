<div align="center">

<img src="public/assets/images/logo/logo-geekbox.png" alt="GeekBox" width="220">

# GeekBox

**Tudo que você consome, em um único lugar.**

Plataforma pessoal de rastreamento e análise de entretenimento

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-000000?style=flat&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=flat&logo=chart.js&logoColor=white)
![Gemini](https://img.shields.io/badge/Google_Gemini-8E75B2?style=flat&logo=googlegemini&logoColor=white)
![License](https://img.shields.io/badge/License-Undefined-lightgrey?style=flat)

[Sobre](#-sobre) • [Funcionalidades](#-funcionalidades) • [Tecnologias](#-tecnologias) • [Arquitetura](#-arquitetura) • [Instalação](#-instalação) • [Uso](#-uso) • [API](#-api) • [Estrutura](#-estrutura-do-projeto) • [Próximos Passos](#-próximos-passos)

</div>

---

## 📖 Sobre

O **GeekBox** é uma aplicação web do tipo *entertainment tracker* desenvolvida como projeto individual na **São Paulo Tech School**, na disciplina de **Pesquisa & Inovação**.

O projeto nasceu de uma dor pessoal do autor: grande parte da sua vida sempre esteve ligada ao entretenimento — jogos, filmes, séries, livros, animes, mangás e músicas marcaram diferentes fases pessoais e acabaram se tornando parte importante de quem ele é. Só que essas informações ficavam dispersas em aplicativos separados (como Skoob, Letterboxd e Backloggd) ou anotadas de forma informal.

Mais do que um exercício acadêmico, o GeekBox é uma ferramenta que centraliza em um único ambiente o registro, o progresso e as estatísticas de consumo de mídia, transformando informações espalhadas em uma experiência organizada, visual e pessoal.

O projeto também está alinhado a dois **Objetivos de Desenvolvimento Sustentável (ODS)** da ONU:

- **ODS 9 — Indústria, Inovação e Infraestrutura**, ao abranger o desenvolvimento de jogos, filmes, séries, livros, mangás, músicas e demais formas de mídia, fomentando a indústria "geek".
- **ODS 12 — Consumo e Produção Responsáveis**, ao estimular o consumo consciente dessas mídias por parte do público.

> Projeto desenvolvido individualmente por **João Vitor da Silva Rodrigues**.

<div align="center">

<!-- 📸 SCREENSHOT: Dashboard -->
<!-- Substitua a linha abaixo pelo screenshot real do dashboard -->
`[ SCREENSHOT DO DASHBOARD AQUI ]`

<p><em>Dashboard com KPIs e gráficos de consumo</em></p>
</div>

## ✨ Funcionalidades

### 🏠 Landing Page
- Apresentação do projeto com seção *hero* e navegação por âncoras (home, sobre o projeto, dashboard)
- Navegação para login e cadastro

<div align="center">

<!-- 📸 SCREENSHOT: Landing Page -->
<!-- Substitua a linha abaixo pelo screenshot real da landing page -->
`[ SCREENSHOT DA LANDING PAGE AQUI ]`

</div>

### 🔐 Autenticação
- Cadastro de usuário (nome, email, senha, telefone e avatar)
- Login com email e senha
- Sessão gerenciada no front-end

### 🎮 Gerenciamento de itens (CRUD)
- Cadastro de itens nas **7 categorias**: jogo, livro, filme, série, anime, mangá e música
- Cada item possui gênero, status (`wishlist`, `em_progresso`, `concluido`, `pausado`, `abandonado`), classificação de 0 a 5, resenha, horas dedicadas e datas de início/conclusão
- Edição de status, classificação e resenha
- Exclusão de itens

### 📌 Wishlist
- Lista de itens que o usuário deseja consumir no futuro

### 🕒 Timeline
- Linha do tempo com o histórico de itens em progresso e concluídos

### 🎯 Metas
- Definição de metas de consumo por categoria e ano

### 📊 Dashboard (Estatísticas)
- **KPIs**: itens concluídos no ano, horas totais, média de horas semanais e taxa de conclusão
- **Gráficos interativos (Chart.js)**:
  - Consumo mensal
  - Horas consumidas por categoria
  - Metas vs. itens concluídos por ano
  - Frequência de consumo

### 🤖 Bob IA — Chatbot com IA (Gemini)
- Assistente integrada via **Google Gemini** para responder perguntas do usuário dentro da própria aplicação

## 🛠 Tecnologias

| Camada | Tecnologia | Descrição |
|---|---|---|
| Frontend | HTML5, CSS3, JavaScript | Interface web vanilla, sem frameworks |
| Fontes | Syne, DM Serif Display, DM Mono | Tipografia própria do design system |
| Gráficos | Chart.js | Visualizações interativas do dashboard |
| Backend | Node.js + Express.js | Servidor web e API REST |
| Banco de Dados | MySQL (via `mysql2`) | Persistência de dados |
| IA | Google Gemini via `@google/genai` | Chatbot "Bob IA" |
| Versionamento | Git + GitHub | Controle de versão |

### Dependências Node.js

```json
{
  "chart.js": "^4.5.1",
  "cors": "^2.8.5",
  "dotenv": "^16.4.5",
  "express": "^4.17.1",
  "mysql2": "^3.9.4",
  "nodemon": "^2.0.7",
  "@google/genai": "^0.14.1"
}
```

## 🏗 Arquitetura

O backend segue o padrão **MVC** (Model-View-Controller):

```
src/
├── controllers/   ← Lógica de negócio e validação de inputs
├── models/        ← Queries SQL e acesso ao banco de dados
├── routes/        ← Definição dos endpoints HTTP
└── database/      ← Configuração da conexão MySQL
```

```
┌─────────────────────────────────────────────────────────────┐
│                         CLIENTE                              │
│              Navegador (Chrome, Firefox, Edge...)            │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    SERVIDOR (Node.js)                        │
│                                                                │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐    │
│  │  HTML/CSS/JS │  │  Express.js  │  │   API Gemini      │    │
│  │   (public/)  │  │  (REST API)  │  │   (Bob IA)        │    │
│  └──────────────┘  └──────┬───────┘  └──────────────────┘    │
│                           │ JSON endpoints                    │
└───────────────────────────┼───────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    BANCO DE DADOS (MySQL)                    │
└─────────────────────────────────────────────────────────────┘
```

## 🗄 Banco de Dados

### Schema

```
geekbox
├── usuario     (id, nome, email, senha, telefone, avatar_url, criado_em)
├── categoria   (id_categoria, nome_categoria)
├── genero      (id, nome, id_categoria)
├── item        (id, usuario_id, categoria_id, genero_id, titulo, status,
│                classificacao, resenha, horas, iniciado_em, concluido_em,
│                url_imagem, criado_em, atualizado_em)
└── meta        (id, usuario_id, categoria_id, quantidade, ano)
```

### Diagrama de relacionamentos

```
usuario ──< item >── categoria
usuario ──< item >── genero
categoria ──< genero
usuario ──< meta >── categoria
```

O diagrama completo pode ser aberto com o [MySQL Workbench](https://www.mysql.com/products/workbench/) através dos arquivos `database/modelagem.mwb` e `database/modelagemV2.mwb`.

## 📦 Instalação

### Pré-requisitos

- [Node.js](https://nodejs.org/) v18 ou superior
- [MySQL](https://www.mysql.com/) (local ou via máquina virtual)
- Git
- Chave de API do [Google Gemini](https://ai.google.dev/)

### 1. Clone o repositório

```bash
git clone https://github.com/JotaVSRodrigues/geekbox.git
cd geekbox
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure o banco de dados

Execute os scripts SQL no seu servidor MySQL:

```bash
mysql -u seu_usuario -p < database/script-criacao.sql
mysql -u seu_usuario -p < database/script-insert.sql
```

Isso irá criar o banco com todas as tabelas, além das 7 categorias e seus respectivos gêneros já cadastrados.

### 4. Configure as variáveis de ambiente

Crie um arquivo **`.env.dev`** na raiz do projeto (para desenvolvimento):

```env
# Ambiente
AMBIENTE_PROCESSO=desenvolvimento

# Servidor
APP_HOST=localhost
APP_PORT=3000

# Banco de Dados
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=geekbox
DB_USER=seu_usuario_mysql
DB_PASSWORD=sua_senha_mysql

# IA
MINHA_CHAVE=sua_chave_da_api_gemini
```

> Para produção, crie um arquivo `.env` e altere a variável `ambiente_processo` no topo de `app.js`.

#### 🔑 Como gerar sua chave da API do Gemini

A Bob IA depende de uma chave de API gratuita do Google Gemini. Para gerar a sua:

1. Acesse o [Google AI Studio](https://aistudio.google.com/apikey).
2. Faça login com uma conta Google.
3. Clique em **"Create API key"** (ou **"Criar chave de API"**).
4. Selecione um projeto do Google Cloud já existente ou deixe o Google criar um novo projeto automaticamente.
5. Copie a chave gerada (algo como `AIza...`).
6. Cole o valor copiado na variável `MINHA_CHAVE` do seu arquivo `.env.dev` (ou `.env`, em produção):
   ```env
   MINHA_CHAVE=AIzaSy...sua_chave_aqui
   ```

> ⚠️ Nunca compartilhe essa chave publicamente nem faça commit dela no repositório — o arquivo `.env.dev`/`.env` já está listado no `.gitignore` do projeto. A camada gratuita do Gemini possui limite de requisições e tokens por minuto; se você atingir o limite, aguarde a renovação da cota ou considere um plano pago.

### 5. Inicie a aplicação

Desenvolvimento (com hot reload via nodemon):

```bash
npm run dev
```

Produção:

```bash
npm start
```

### 6. Acesse no navegador

```
http://localhost:3000
```

## 🚀 Uso

### Fluxo principal

1. Acesse a landing page em `/` e clique em **Login**
2. Cadastre-se com nome, email, telefone e senha
3. Faça login com suas credenciais
4. Na **Home**, veja um resumo do que está em progresso e recém-concluído
5. Cadastre um item escolhendo categoria, gênero e status (`wishlist`, `em progresso`, `concluído`, `pausado` ou `abandonado`)
6. Acompanhe seu histórico na **Timeline** e organize desejos futuros na **Wishlist**
7. Defina **Metas** de consumo por categoria e ano
8. Acesse o **Dashboard** para ver seus KPIs e gráficos
9. Use a **Bob IA** para tirar dúvidas dentro da própria aplicação

## 🔌 API

**Base URL:** `http://localhost:{APP_PORT}`

### Usuários

| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/usuarios/cadastrar` | Cadastra um novo usuário |
| POST | `/usuarios/autenticar` | Autentica um usuário |
| GET | `/usuarios/buscar-semanas/:id` | Busca dados semanais do usuário |

### Itens

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/itens/buscar-generos` | Lista os gêneros disponíveis |
| POST | `/itens/cadastrar-item` | Cadastra um novo item |
| GET | `/itens/buscar-wishlist/:id` | Lista os itens da wishlist |
| GET | `/itens/buscar-timeline/:id` | Lista os itens da timeline |
| GET | `/itens/buscar-item/:itemId` | Busca um item específico |
| GET | `/itens/buscar-item-progresso/:id` | Lista itens em progresso (Home) |
| GET | `/itens/buscar-item-concluido/:id` | Lista itens concluídos (Home) |
| PUT | `/itens/atualizar-resenha` | Atualiza a resenha de um item |
| PUT | `/itens/atualizar-status` | Atualiza o status de um item |
| PUT | `/itens/atualizar-classificacao` | Atualiza a classificação de um item |
| DELETE | `/itens/excluir/:itemId` | Exclui um item |

### Metas

| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/metas/cadastrar-meta` | Cadastra uma nova meta |

### Estatísticas

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/estatisticas/consumo-mensal/:id` | Consumo mensal do usuário |
| GET | `/estatisticas/horas-por-categoria/:id` | Horas consumidas por categoria |
| GET | `/estatisticas/metas-por-ano/:id` | Metas vs. itens concluídos |
| GET | `/estatisticas/frequencia-consumo/:id` | Frequência de consumo |
| GET | `/estatisticas/kpi-concluidos/:id` | KPI: itens concluídos |
| GET | `/estatisticas/kpi-horas-totais/:id` | KPI: horas totais |
| GET | `/estatisticas/kpi-horas-semanais/:id` | KPI: horas semanais |
| GET | `/estatisticas/kpi-taxa-conclusao/:id` | KPI: taxa de conclusão |

### Bob IA

| Método | Endpoint | Descrição | Body |
|---|---|---|---|
| POST | `/bobIA/perguntar` | Envia uma pergunta para a IA | `{ pergunta }` |

## 📁 Estrutura do Projeto

```
geekbox/
│
├── app.js                          # Entry point — configura Express e rotas
├── package.json
├── .gitignore
│
├── database/
│   ├── modelagem.mwb                # Modelagem do banco (v1, MySQL Workbench)
│   ├── modelagemV2.mwb              # Modelagem do banco (v2, MySQL Workbench)
│   ├── script-criacao.sql           # Script de criação das tabelas
│   └── script-insert.sql            # Script de dados iniciais (categorias e gêneros)
│
├── src/
│   ├── controllers/                 # Lógica de negócio
│   │   ├── usuarioController.js
│   │   ├── itemController.js
│   │   ├── metaController.js
│   │   └── estatisticaController.js
│   │
│   ├── models/                      # Queries e acesso ao banco de dados
│   │
│   ├── routes/                      # Endpoints HTTP
│   │   ├── index.js
│   │   ├── usuarios.js
│   │   ├── itens.js
│   │   ├── metas.js
│   │   ├── estatisticas.js
│   │   └── bobAIRoute.js            # Integração com Google Gemini
│   │
│   └── database/
│       └── config.js                # Conexão MySQL
│
└── public/                          # Frontend estático servido pelo Express
    ├── index.html                   # Landing page
    │
    ├── assets/
    │   ├── images/                  # Logo, ícones, imagens da landing page
    │   └── fonts/                   # Syne, DM Serif Display, DM Mono
    │
    ├── css/
    │   ├── style.css
    │   ├── landing-page.css
    │   ├── dashboard.css
    │   ├── wishlist.css
    │   ├── cadastro.css
    │   ├── components.css
    │   ├── hero.css
    │   └── modal.css
    │
    ├── html/
    │   ├── login.html
    │   ├── cadastro.html
    │   ├── home.html
    │   ├── dashboard.html
    │   ├── timeline.html
    │   └── wishlist.html
    │
    └── js/                          # Scripts de cada página
```

## 🎯 Escopo

**Dentro do escopo**
- Aplicação web acessível via navegador desktop
- Autenticação por e-mail e senha com sessão
- Cadastro de itens nas 7 categorias com status, classificação e resenha
- Timeline, wishlist e dashboard funcionais
- Gráficos com Chart.js (linha, donut e barras)
- Banco de dados MySQL com script SQL completo
- Back-end Node.js com Express
- Tema escuro como padrão da aplicação

**Fora do escopo (limitações do MVP)**
- Aplicativo mobile nativo (apenas versão web)
- Notificações por e-mail ou push
- Sistema de amigos ou feed social
- Perfil público acessível por outros usuários
- Pagamento ou modelo de assinatura
- Deploy em servidor de produção remoto
- Recomendações automáticas por algoritmo de machine learning
- Suporte a idiomas além do português

## 🔮 Próximos Passos

- **Recuperação de senha** — fluxo de recuperação de conta por e-mail
- **Paginação e indexação** — otimizar listagens com muitos itens cadastrados
- **Testes cross-browser** — validar compatibilidade em Chrome, Firefox e Edge
- **Deploy em produção** — hospedar a aplicação fora do ambiente de desenvolvimento local
- **Integração com APIs externas de mídia** — enriquecer o cadastro de itens com dados de fontes como RAWG, Open Library e OMDB

## 📄 Licença

Este projeto ainda não possui uma licença definida.

## 👨‍💻 Autor

**João Vitor da Silva Rodrigues** — RA: 042611001

Projeto individual desenvolvido para a disciplina de Pesquisa & Inovação — São Paulo Tech School, 2026.
Orientadora: Julia Marlene Barbosa Lima.

[GitHub](https://github.com/JotaVSRodrigues)

<div align="center">

Desenvolvido com 🎮📚🎬 para o projeto individual da São Paulo Tech School — 2026

</div>
