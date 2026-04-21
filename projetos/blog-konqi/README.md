<div align="center">

# 🟢 Blog Konqi

**Plataforma de blog sobre finanças e investimentos**

[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-Express_v5-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Drizzle_ORM-4169E1?style=flat-square&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![pnpm](https://img.shields.io/badge/pnpm-Monorepo-F69220?style=flat-square&logo=pnpm&logoColor=white)](https://pnpm.io/)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](./LICENSE)

🌐 **[blog.konqi.com.br](https://blog.konqi.com.br)**

</div>

---

## 📖 Sobre o projeto

O **Blog Konqi** é uma plataforma completa de conteúdo voltada para finanças pessoais e investimentos. O projeto foi construído do zero com uma arquitetura moderna em **monorepo**, integrando um frontend SPA em React, uma API RESTful em Node.js/Express e um banco de dados PostgreSQL gerenciado via Drizzle ORM.

Além das páginas públicas para leitores, o projeto conta com um **painel administrativo completo** — com editor de texto rico (TipTap), gerenciamento de artigos e categorias, upload de imagens e autenticação própria — tudo isso com suporte a **modo escuro** e identidade visual verde exclusiva (Konqi Green).

---

## ✨ Funcionalidades

### 🌍 Área Pública
| Funcionalidade | Descrição |
|---|---|
| **Home** | Página principal com hero section, artigos em destaque e categorias |
| **Artigo** | Página de leitura com conteúdo rico em HTML, metadados e navegação |
| **Categoria** | Listagem de artigos filtrados por categoria |
| **Busca** | Pesquisa full-text por título e conteúdo dos artigos |
| **Dark Mode** | Alternância de tema claro/escuro persistida no localStorage |
| **SEO-ready** | Meta tags dinâmicas com `react-helmet-async` em cada página |

### 🔒 Painel Admin
| Funcionalidade | Descrição |
|---|---|
| **Login** | Autenticação com usuário/senha via sessões no banco de dados |
| **Dashboard** | Visão geral com métricas de artigos e categorias |
| **Gestão de Artigos** | Criação, edição, publicação e exclusão de artigos |
| **Editor Rico** | Editor WYSIWYG (TipTap) com títulos, listas, links, imagens por URL e mais |
| **Gestão de Categorias** | CRUD completo de categorias com slugs |
| **Upload de Imagens** | Upload de capa dos artigos diretamente pelo painel |

---

## 🛠️ Stack Tecnológica

### Frontend (`artifacts/blog`)
| Tecnologia | Versão | Uso |
|---|---|---|
| **React** | 19 | Framework de UI |
| **Vite** | 7 | Bundler e dev server |
| **TypeScript** | 5.9 | Tipagem estática |
| **Tailwind CSS** | v4 | Estilização utilitária |
| **Radix UI** | — | Componentes acessíveis headless |
| **TanStack Query** | v5 | Gerenciamento de estado/cache de servidor |
| **Wouter** | v3 | Roteamento client-side leve |
| **TipTap** | v3 | Editor de texto rico (WYSIWYG) |
| **Framer Motion** | — | Animações declarativas |
| **next-themes** | — | Gerenciamento de tema (dark/light) |
| **date-fns** | v3 | Formatação de datas |
| **Zod** | — | Validação de schemas no cliente |

### Backend (`artifacts/api-server`)
| Tecnologia | Versão | Uso |
|---|---|---|
| **Node.js** | — | Runtime do servidor |
| **Express** | v5 | Framework HTTP |
| **TypeScript** | 5.9 | Tipagem estática |
| **Drizzle ORM** | — | ORM type-safe para PostgreSQL |
| **PostgreSQL** | — | Banco de dados relacional |
| **Pino** | v9 | Logging estruturado de alta performance |
| **Multer** | v2 | Upload de arquivos multipart |
| **esbuild** | — | Compilação ultra-rápida para produção |
| **Zod** | — | Validação de request/response |

### Bibliotecas Compartilhadas (`lib/`)
| Pacote | Descrição |
|---|---|
| `@workspace/db` | Schema Drizzle + cliente PostgreSQL compartilhado |
| `@workspace/api-spec` | Especificação OpenAPI (YAML) da API REST |
| `@workspace/api-zod` | Schemas Zod gerados via Orval a partir do OpenAPI spec |
| `@workspace/api-client-react` | Hooks React Query gerados via Orval (type-safe) |
| `@workspace/replit-auth-web` | Hook `useAuth` compartilhado para gerenciar sessão |

### Tooling & Infraestrutura
| Ferramenta | Uso |
|---|---|
| **pnpm Workspaces** | Monorepo com packages compartilhados |
| **Orval** | Geração de código client/Zod a partir do OpenAPI spec |
| **TypeScript Project References** | Build incremental entre pacotes da `lib/` |
| **Replit** | Plataforma de desenvolvimento e deploy |

---

## 🏗️ Arquitetura do Projeto

```
blog-konqi/
│
├── artifacts/
│   ├── api-server/         # Backend: Express v5 + TypeScript
│   │   └── src/
│   │       ├── routes/     # Endpoints REST (artigos, categorias, auth, imagens)
│   │       ├── middlewares/ # Auth session, requireAdmin
│   │       └── lib/        # Auth helper, logger
│   │
│   └── blog/               # Frontend: React 19 + Vite + Tailwind
│       └── src/
│           ├── pages/
│           │   ├── public/ # Home, Article, Category, Search
│           │   └── admin/  # Dashboard, Articles, ArticleEditor, Categories, Login
│           └── components/ # AdminRoute, layouts, UI compartilhada
│
├── lib/
│   ├── db/                 # Schema Drizzle (articles, categories, sessions)
│   ├── api-spec/           # openapi.yaml — fonte de verdade da API
│   ├── api-zod/            # Schemas Zod (gerados pelo Orval)
│   ├── api-client-react/   # Hooks React Query (gerados pelo Orval)
│   └── replit-auth-web/    # Hook useAuth compartilhado
│
└── scripts/                # Scripts de seed e utilitários
```

### Fluxo de dados
```
openapi.yaml  ──Orval codegen──►  api-zod (Zod schemas)
                                  api-client-react (React Query hooks)
                                          │
                                          ▼
React SPA  ──fetch/hooks──►  Express API  ──Drizzle ORM──►  PostgreSQL
```

---

## 🚀 Como rodar localmente

### Pré-requisitos
- [Node.js 20+](https://nodejs.org/)
- [pnpm 9+](https://pnpm.io/installation)
- [PostgreSQL](https://www.postgresql.org/) (ou uma instância remota)

### 1. Clone o repositório
```bash
git clone https://github.com/seu-usuario/blog-konqi.git
cd blog-konqi
```

### 2. Instale as dependências
```bash
pnpm install
```

### 3. Configure as variáveis de ambiente
O servidor de API não usa dotenv — exporte as variáveis diretamente no seu shell (ou use `direnv` / o mecanismo preferido do seu ambiente):

```bash
export DATABASE_URL="postgresql://usuario:senha@localhost:5432/blog_konqi"
export ADMIN_USERNAME="admin"
export ADMIN_PASSWORD="sua-senha-segura"
export PORT="8080"
```

> 💡 No **Replit**, todas essas variáveis são gerenciadas automaticamente pela plataforma via Secrets e configuração do workspace.

### 4. Aplique o schema no banco de dados
```bash
pnpm --filter @workspace/db run push
```

### 5. Popule com dados de exemplo (opcional)
```bash
pnpm --filter @workspace/api-server run seed
```

### 6. Inicie os serviços

**Backend (API):**
```bash
pnpm --filter @workspace/api-server run dev
# Disponível em http://localhost:8080
```

**Frontend (Blog):**
```bash
pnpm --filter @workspace/blog run dev
# Disponível em http://localhost:24722
```

---

## 🔑 Variáveis de Ambiente

| Variável | Obrigatório | Padrão | Descrição |
|---|---|---|---|
| `DATABASE_URL` | ✅ | — | String de conexão PostgreSQL |
| `ADMIN_PASSWORD` | ✅ | — | Senha de acesso ao painel admin |
| `ADMIN_USERNAME` | ❌ | `admin` | Usuário de acesso ao painel admin |
| `PORT` | ✅ | — | Porta do servidor de API (definida automaticamente no Replit) |
| `NODE_ENV` | ❌ | `development` | Ambiente de execução |
| `ALLOWED_ORIGIN` | ❌ | — | Origem permitida para CORS em produção |

---

## 🗄️ Schema do Banco de Dados

```
articles      → id, title, slug, excerpt, content, coverImage,
                published, publishedAt, categoryId, createdAt, updatedAt

categories    → id, name, slug, description, createdAt, updatedAt

sessions      → id, data, expiresAt, createdAt
```

---

## 🎨 Design System

O projeto utiliza uma identidade visual exclusiva chamada **Konqi Green** — uma paleta baseada em tons de verde escuro (`hsl(140, 40%, X%)`), implementada com **CSS custom properties** (variáveis semânticas) e o sistema de `@theme` do Tailwind CSS v4.

O modo escuro é totalmente suportado via `next-themes` com o atributo `class` no `<html>`, respeitando a identidade visual da marca em ambos os temas.

---

## 📡 API REST

A API segue a especificação definida em `lib/api-spec/openapi.yaml`. Os principais endpoints são:

| Método | Endpoint | Descrição | Auth |
|---|---|---|---|
| `GET` | `/api/articles` | Listar artigos (com paginação/filtros) | — |
| `GET` | `/api/articles/:slug` | Buscar artigo por slug | — |
| `POST` | `/api/articles` | Criar artigo | ✅ |
| `PUT` | `/api/articles/:id` | Atualizar artigo | ✅ |
| `DELETE` | `/api/articles/:id` | Remover artigo | ✅ |
| `GET` | `/api/categories` | Listar categorias | — |
| `POST` | `/api/categories` | Criar categoria | ✅ |
| `POST` | `/api/auth/login` | Login admin | — |
| `POST` | `/api/auth/logout` | Logout | — |
| `GET` | `/api/auth/user` | Sessão atual | — |
| `GET` | `/api/admin/images` | Listar imagens enviadas | ✅ |
| `POST` | `/api/admin/images` | Upload de imagem | ✅ |
| `GET` | `/api/healthz` | Health check | — |

---

## 👤 Autor

**Desenvolvido por [Josué Vieira]**

- 💼 [LinkedIn](https://linkedin.com/in/josue-vieira)
- 🐙 [GitHub](https://github.com/softuringsolutionsrep)

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](./LICENSE).

---

<div align="center">

**🟢 [blog.konqi.com.br](https://blog.konqi.com.br)**

*Feito com dedicação e muito TypeScript* ☕

</div>
