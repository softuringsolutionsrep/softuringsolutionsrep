# Konqi — Seu GPS Financeiro 🧭

<div align="center">

![Status](https://img.shields.io/badge/Status-Em%20Produção-brightgreen)
![Versão](https://img.shields.io/badge/Versão-0.1.0-blue)
![React](https://img.shields.io/badge/React-18.x-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-4.x-38BDF8?logo=tailwindcss&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-20.x-339933?logo=node.js&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15.x-4169E1?logo=postgresql&logoColor=white)

**Gestão inteligente de investimentos para o mercado brasileiro**

[🌐 Acessar o app](https://konqi.com.br)

</div>

---

## 📖 Sobre o Projeto

O **Konqi** é um **GPS Financeiro** — uma plataforma web que guia você pelo caminho certo para seus objetivos de investimento.

Assim como um GPS recalcula a rota quando você desvia, o Konqi monitora sua carteira em tempo real, detecta desvios em relação à alocação ideal para o seu perfil e sugere exatamente o que comprar ou vender para voltar ao curso certo. Tudo isso de forma simples, visual e automatizada.

### ✨ Por que o Konqi?

- 📊 **Visão unificada** — toda a sua carteira em um só lugar
- 🎯 **Rebalanceamento automatizado** — sugestões de compra e venda baseadas no seu perfil
- 🏆 **Metas financeiras** — cálculo automático de aportes mensais para atingir seus objetivos
- 📈 **Simulações de investimento** — projete o crescimento do seu patrimônio
- 🔒 **Autenticação segura** — login via Clerk com suporte a Google e e-mail

---

## 🎨 Funcionalidades Principais

### 1. Dashboard
Visão geral do patrimônio total, distribuição por categoria e recomendações de rebalanceamento em destaque.

### 2. Carteira (Portfolio)
Adicione e gerencie ativos de todas as classes: Renda Fixa (Pós-fixado, Inflação, Prefixado), Renda Variável (Brasil, EUA, Global), Criptomoedas, Ouro e Moedas.

### 3. Rebalanceamento Inteligente
Compare sua alocação atual com a alocação ideal do seu perfil de investidor (Conservador, Moderado, Arrojado ou Muito Arrojado). Receba sugestões priorizadas de compra e venda.

### 4. Objetivos Financeiros
Crie metas (reserva de emergência, aposentadoria, viagem, etc.) e receba o cálculo automático do aporte mensal necessário, considerando juros compostos e todas as suas metas em conjunto.

### 5. Simulações
Projete o crescimento de um aporte único ou recorrente ao longo do tempo, com taxas reais de mercado.

### 6. Histórico de Operações
Registro completo de todas as compras e vendas, com cálculo automático de preço médio e quantidade.

### 7. Painel Admin
Área exclusiva para administradores com métricas da plataforma, listagem e gestão de usuários.

---

## 🛠️ Stack Tecnológica

### Frontend
| Tecnologia | Uso |
|---|---|
| [React 18](https://react.dev/) | Biblioteca UI principal |
| [TypeScript](https://www.typescriptlang.org/) | Tipagem estática |
| [Tailwind CSS v4](https://tailwindcss.com/) | Estilização utilitária |
| [Radix UI / shadcn/ui](https://ui.shadcn.com/) | Componentes acessíveis |
| [Recharts](https://recharts.org/) | Gráficos e visualizações |
| [Motion (Framer Motion)](https://motion.dev/) | Animações fluidas |
| [React Router DOM v6](https://reactrouter.com/) | Roteamento SPA |
| [Vite 6](https://vite.dev/) | Build tool e dev server |

### Backend
| Tecnologia | Uso |
|---|---|
| [Node.js 20](https://nodejs.org/) | Runtime do servidor |
| [Express.js 5](https://expressjs.com/) | Framework HTTP |
| [tsx](https://tsx.is/) | Execução de TypeScript sem transpilação |
| [Nodemailer](https://nodemailer.com/) | Envio de e-mails |
| [Multer](https://github.com/expressjs/multer) | Upload de arquivos |

### Banco de Dados
| Tecnologia | Uso |
|---|---|
| [PostgreSQL](https://www.postgresql.org/) | Banco de dados principal |
| [Neon](https://neon.tech/) | Hospedagem serverless do PostgreSQL |
| [node-postgres (pg)](https://node-postgres.com/) | Driver de conexão |

### Autenticação
| Tecnologia | Uso |
|---|---|
| [Clerk](https://clerk.com/) | Autenticação completa (Google, e-mail/senha) |

### APIs Externas
| API | Uso |
|---|---|
| [Brapi](https://brapi.dev/) | Cotações de ações e FIIs brasileiros |
| [CoinGecko](https://www.coingecko.com/api) | Preços de criptomoedas |

---

## 🗂️ Estrutura do Projeto

```
konqi/
├── src/
│   ├── assets/              # Imagens e recursos estáticos
│   ├── components/
│   │   ├── pages/           # Páginas do app (Dashboard, Portfolio, etc.)
│   │   └── ui/              # Componentes reutilizáveis (shadcn/ui)
│   ├── contexts/            # Contextos globais (UserContext, PortfolioContext)
│   ├── lib/                 # Serviços e utilitários
│   │   ├── api-service.ts   # Cliente REST para o backend
│   │   ├── price-service.ts # Busca de cotações
│   │   └── portfolio-profiles.ts # Alocações ideais por perfil
│   ├── styles/              # Estilos globais (Tailwind v4)
│   └── types/               # Definições TypeScript
├── server/
│   └── index.ts             # API Express.js com todos os endpoints
├── scripts/                 # Scripts utilitários (seed, migração)
├── public/                  # Arquivos públicos
├── package.json
└── vite.config.ts
```

---

## 🚀 Como Executar Localmente

### Pré-requisitos

- [Node.js 20+](https://nodejs.org/)
- [npm](https://www.npmjs.com/)
- Instância PostgreSQL (local ou [Neon](https://neon.tech/))
- Conta no [Clerk](https://clerk.com/) (para autenticação)

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/<seu-usuario>/konqi.git
cd konqi
```

2. **Instale as dependências**
```bash
npm install
```

3. **Configure as variáveis de ambiente** (veja a seção abaixo)

4. **Inicie o frontend**
```bash
npm run dev
```

5. **Inicie o backend** (em outro terminal)
```bash
npm run dev:server
```

6. **Acesse no navegador**
```
http://localhost:5000
```

---

## 🔑 Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto com as seguintes variáveis:

### Frontend (prefixo `VITE_`)

```env
# Clerk — chave publicável (obrigatório)
VITE_CLERK_PUBLISHABLE_KEY=pk_test_...

# Clerk — chave publicável de desenvolvimento (opcional, sobrescreve a anterior)
VITE_CLERK_DEV_PUBLISHABLE_KEY=pk_test_...

# Chave de acesso ao painel admin em desenvolvimento (opcional)
VITE_DEV_ADMIN_KEY=sua_chave_aqui
```

### Backend

```env
# PostgreSQL — string de conexão (obrigatório)
DATABASE_URL=postgresql://usuario:senha@host:porta/banco

# Clerk — chave secreta para verificação de tokens (obrigatório)
CLERK_SECRET_KEY=sk_test_...

# Clerk — chave secreta de produção (obrigatório em produção)
CLERK_PROD_SECRET_KEY=sk_live_...

# Porta do servidor backend (padrão: 3001)
PORT=3001

# Ambiente de execução
NODE_ENV=development

# Chave de acesso admin para operações privilegiadas
DEV_ADMIN_KEY=sua_chave_aqui

# SMTP — configurações para envio de e-mail (opcional)
SMTP_HOST=smtp.exemplo.com
SMTP_PORT=587
SMTP_USER=seu@email.com
SMTP_PASS=sua_senha_smtp
```

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Siga os passos abaixo:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Faça o commit das suas alterações (`git commit -m 'Adiciona MinhaFeature'`)
4. Faça o push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

---

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

---

<div align="center">

Feito com ❤️ para ajudar brasileiros a investir com mais inteligência.

**[konqi.com.br](https://konqi.com.br)**

</div>
