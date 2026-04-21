# 🏋️ Treinup (https://treinup.app.br/lp)

Plataforma completa de gestão de treinos para alunos, personal trainers e academias.

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Planos](#-planos-free-vs-premium)
- [Arquitetura](#-arquitetura)
- [Rodando Localmente](#-rodando-localmente)
- [Variáveis de Ambiente](#-variáveis-de-ambiente)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Contato](#-sobre-o-desenvolvedor)

---

## 🚀 Sobre o Projeto

O **Treinup** é uma plataforma SaaS de gestão de treinos que conecta alunos, personal trainers e academias em um único ecossistema. O objetivo é eliminar planilhas e anotações dispersas, oferecendo uma experiência digital fluida para quem treina e para quem prescreve treinos.

**Problemas que resolve:**

- Alunos sem acesso fácil ao seu plano de treino atualizado
- Personais que perdem tempo gerenciando treinos em planilhas
- Academias sem visibilidade sobre o relacionamento professor–aluno
- Falta de padronização na periodização e acompanhamento de carga

---

## ✨ Funcionalidades

### 🎓 Aluno

| Funcionalidade | Free | Premium |
|---|---|---|
| Visualizar treinos prescritos pelo professor | ✅ | ✅ |
| Criar treinos próprios (até 2) | ✅ | ✅ |
| Criar treinos próprios (ilimitados) | ❌ | ✅ |
| Catálogo de exercícios básico | ✅ | ✅ |
| Catálogo completo + vídeos demonstrativos | ❌ | ✅ |
| Periodização A e B | ✅ | ✅ |
| Periodização C e Livre | ❌ | ✅ |
| Até 6 exercícios por treino | ✅ | ✅ |
| Exercícios ilimitados por treino | ❌ | ✅ |
| Exportar treino em PDF | ❌ | ✅ |
| Dashboard de progresso | ✅ | ✅ |

### 🏃 Personal Trainer / Professor

- Gerenciar lista de alunos vinculados
- Criar e editar treinos personalizados para cada aluno
- Definir séries, repetições, carga e tempo de descanso
- Organizar treinos por periodização (A / B / C / Livre)
- Visualizar histórico e evolução dos alunos

### 🏢 Admin (Academia)

- Painel de gestão de usuários
- Criação e remoção de professores e alunos
- Transferência de alunos entre professores
- Controle do plano de assinatura da academia

---

## 💳 Planos Free vs Premium

O Treinup adota um modelo **freemium** voltado para alunos individuais, com planos pagos que desbloqueiam o potencial completo da plataforma.

| Recurso | Free | Premium |
|---|---|---|
| Treinos próprios | Até 2 | Ilimitados |
| Exercícios por treino | Até 6 | Ilimitados |
| Periodizações disponíveis | A e B | A, B, C, Livre |
| Acesso a vídeos | ❌ | ✅ |
| Exportação em PDF | ❌ | ✅ |
| Catálogo de exercícios | Básico | Completo |

Além do plano individual, há planos específicos para **Personal Trainers** e **Academias**, que incluem funcionalidades de gestão de equipes e múltiplos alunos. Pagamentos e assinaturas são processados pelo **Stripe**, com suporte a webhooks para sincronização automática de status e reconciliação em produção.

---

## 🏗 Arquitetura

O Treinup é uma aplicação **full-stack TypeScript** com frontend SPA e backend REST API, servidos pelo mesmo servidor em produção.

```
┌─────────────────────────────────────────────────────────┐
│                     CLIENTE (SPA)                       │
│                                                         │
│  React 18 + Vite 6 + TypeScript                         │
│  ├─ react-router v7 (roteamento & rotas por role)       │
│  ├─ Tailwind CSS v4 (estilização utility-first)         │
│  ├─ Framer Motion v12 (animações)                       │
│  ├─ Radix UI / Shadcn UI (componentes acessíveis)       │
│  ├─ Clerk (React SDK) (autenticação no frontend)        │
│  └─ @react-pdf/renderer (geração de PDF no browser)     │
└────────────────────┬────────────────────────────────────┘
                     │ HTTP / REST
┌────────────────────▼────────────────────────────────────┐
│                  SERVIDOR (Node.js)                     │
│                                                         │
│  Express 5 + TypeScript + TSX                           │
│  ├─ /api/auth      → autenticação local & Clerk         │
│  ├─ /api/users     → perfis e planos de usuário         │
│  ├─ /api/workouts  → CRUD de treinos & exercícios       │
│  ├─ /api/exercises → catálogo de exercícios             │
│  ├─ /api/stripe    → checkout, webhooks & assinaturas   │
│  └─ /api/admin     → gestão administrativa              │
└──────────┬──────────────────────────┬───────────────────┘
           │                          │
┌──────────▼──────────┐  ┌────────────▼──────────────────┐
│     PostgreSQL      │  │      Serviços Externos         │
│                     │  │                                │
│  Tabelas:           │  │  ┌──────────┐ ┌──────────┐    │
│  ├─ users           │  │  │  Stripe  │ │  Clerk   │    │
│  ├─ workouts        │  │  │ Payments │ │   Auth   │    │
│  ├─ workout_        │  │  └──────────┘ └──────────┘    │
│  │  exercises       │  └────────────────────────────────┘
│  └─ stripe_webhook_ │
│     events          │
└─────────────────────┘
```

**Fluxo de autenticação (produção):**
1. Usuário faz login via Clerk (OAuth ou e-mail/senha)
2. Clerk emite um JWT que é enviado em cada requisição à API
3. O clerkMiddleware valida o token no servidor Express
4. O backend consulta o PostgreSQL pelo clerk_user_id para recuperar o perfil interno e o plano ativo

**Fluxo de assinatura:**
1. Usuário seleciona um plano em /plans
2. É redirecionado para o Checkout hospedado pelo Stripe
3. Após pagamento, o Stripe dispara um webhook para /api/stripe/webhook
4. O servidor valida a assinatura e atualiza o plano no banco de dados
5. No startup de produção, reconcileSubscriptions() corrige inconsistências causadas por falhas na entrega de webhooks

---

## 💻 Rodando Localmente

### Pré-requisitos

- Node.js 20+
- pnpm 9+
- PostgreSQL 14+

### Instalação

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/treinup.git
cd treinup

# 2. Instale as dependências
pnpm install

# 3. Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env com sua string de conexão do PostgreSQL

# 4. Inicie o servidor e o frontend em paralelo
pnpm run dev:all
```

O frontend estará disponível em http://localhost:5173 e a API em http://localhost:5000.

> **Nota:** Em desenvolvimento, o Clerk está desabilitado por padrão. O sistema utiliza autenticação simples com tokens locais, permitindo login rápido sem precisar configurar credenciais externas.

### Seed do banco de dados

O banco é populado automaticamente com dados de demonstração quando a tabela users está vazia. Para forçar um re-seed manualmente:

```bash
pnpm run seed
```

### Scripts disponíveis

| Comando | Descrição |
|---|---|
| pnpm run dev | Inicia o frontend Vite |
| pnpm run server | Inicia o servidor Express |
| pnpm run dev:all | Inicia frontend e backend em paralelo |
| pnpm run build | Gera o build de produção |
| pnpm run start | Inicia o servidor em modo produção |
| pnpm run seed | Popula o banco com dados de demonstração |

---

## 🔑 Variáveis de Ambiente

Crie um arquivo .env na raiz do projeto com as seguintes variáveis:

```env
# Banco de dados PostgreSQL (obrigatório)
DATABASE_URL=postgresql://usuario:senha@localhost:5432/treinup

# Clerk — necessário apenas em produção
CLERK_SECRET_KEY=sk_live_...
VITE_CLERK_PUBLISHABLE_KEY=pk_live_...

# Stripe — necessário apenas em produção
STRIPE_SECRET_KEY=sk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...

# IDs de preço por plano e ciclo de cobrança
STRIPE_PRICE_PREMIUM_MONTHLY=price_...
STRIPE_PRICE_PREMIUM_YEARLY=price_...
STRIPE_PRICE_PERSONAL_MONTHLY=price_...
STRIPE_PRICE_PERSONAL_YEARLY=price_...
STRIPE_PRICE_ACADEMIA_MONTHLY=price_...
STRIPE_PRICE_ACADEMIA_YEARLY=price_...

# URL base da aplicação
APP_BASE_URL=https://seu-dominio.com
```

| Variável | Obrigatória | Descrição |
|---|---|---|
| DATABASE_URL | ✅ Sempre | String de conexão PostgreSQL |
| CLERK_SECRET_KEY | Produção | Chave secreta do Clerk |
| VITE_CLERK_PUBLISHABLE_KEY | Produção | Chave pública do Clerk (frontend) |
| STRIPE_SECRET_KEY | Produção | Chave secreta do Stripe |
| STRIPE_WEBHOOK_SECRET | Produção | Secret para validação de webhooks |
| STRIPE_PRICE_PREMIUM_MONTHLY | Produção | ID do preço mensal Premium |
| STRIPE_PRICE_PREMIUM_YEARLY | Produção | ID do preço anual Premium |
| STRIPE_PRICE_PERSONAL_MONTHLY | Produção | ID do preço mensal Personal |
| STRIPE_PRICE_PERSONAL_YEARLY | Produção | ID do preço anual Personal |
| STRIPE_PRICE_ACADEMIA_MONTHLY | Produção | ID do preço mensal Academia |
| STRIPE_PRICE_ACADEMIA_YEARLY | Produção | ID do preço anual Academia |
| APP_BASE_URL | Produção | URL pública da aplicação |

---

## 📁 Estrutura do Projeto

```
treinup/
├── src/
│   └── app/
│       ├── components/   # Componentes reutilizáveis (Layout, UI, etc.)
│       ├── config/       # Configurações de negócio (planConfig.ts)
│       ├── context/      # Contextos React (AuthContext)
│       ├── data/         # Dados estáticos e tipos (mockData, exercícios)
│       ├── services/     # Chamadas à API (fetch helpers)
│       ├── pages/        # Páginas da aplicação por role
│       └── routes.tsx    # Rotas e proteção por role de usuário
├── server/
│   ├── routes/           # Endpoints da API (auth, users, workouts, stripe, admin)
│   ├── db.ts             # Pool de conexão e schema do PostgreSQL
│   ├── index.ts          # Entry point do servidor Express
│   ├── seed.ts           # Dados iniciais para desenvolvimento
│   └── seed-cli.ts       # CLI para re-seed manual
├── public/               # Assets estáticos
├── package.json
└── vite.config.ts
```

---

## 🧑‍💻 Sobre o Desenvolvedor

Desenvolvido como projeto full-stack de portfólio, com foco em arquitetura escalável, integração com serviços de pagamento e experiência do usuário.

**Tecnologias demonstradas neste projeto:**

- Arquitetura Full-Stack TypeScript de ponta a ponta
- Controle de acesso baseado em roles (RBAC) com rotas protegidas
- Integração com Stripe: Checkout, Webhooks e reconciliação de assinaturas
- Autenticação segura com Clerk (JWT) e fallback para desenvolvimento local
- Design system acessível com Radix UI e Tailwind CSS v4
- Animações fluidas com Framer Motion
- Geração de documentos PDF diretamente no browser

> Aberto a oportunidades. Entre em contato pelo LinkedIn ou por e-mail.
