<div align="center">

# BKTech — Plataforma de Gestão Interna

**Um sistema de gestão interna completo, construído para equipes modernas.**  
Controle de acesso por função, arquitetura multi-módulo, assistente com IA e colaboração em tempo real — tudo em um só lugar.

[![Acesse](https://img.shields.io/badge/Acesse-gestao.bktech.com.br-0079F2?style=for-the-badge&logo=vercel&logoColor=white)](https://gestao.bktech.com.br)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://neon.tech/)

</div>

---

## Visão Geral

A BKTech Management Platform é um sistema interno abrangente, criado para unificar as operações do dia a dia de uma empresa de tecnologia. Do pipeline comercial à gestão de RH, controle de projetos e financeiro — todos os módulos compartilham uma interface consistente, uma camada de autenticação unificada e controle de acesso por departamento.

Desenvolvido inteiramente com TypeScript em toda a stack, com forte ênfase em segurança de tipos, experiência do desenvolvedor e confiabilidade em produção.

---

## Módulos

| Módulo | Descrição |
|--------|-----------|
| **Comercial (CRM)** | Pipeline de vendas em Kanban com gestão de propostas, acompanhamento de clientes, anexos de arquivos e fluxos assistidos por IA |
| **Financeiro** | Geração automática de registros financeiros para negócios fechados, com cálculos de comissão, impostos e repasse ao fabricante |
| **Projetos** | Gestão completa de projetos e tarefas com Kanban, cronograma estilo Gantt, subtarefas hierárquicas, edição inline e atribuição de equipe |
| **POCs** | Módulo de acompanhamento de provas de conceito, espelhando o fluxo de Projetos com escopo de dados independente |
| **Contratos** | Visualização em gráfico Gantt dos prazos de contratos com indicadores de vencimento por cor |
| **Base de Conhecimento** | Wiki interna pesquisável com categorias, rastreamento de visualizações e conteúdo rico |
| **Marketing** | Calendário de eventos e gestão de campanhas com controle de orçamento e status |
| **Gestão de RH** | Diretório de colaboradores e fluxo de solicitação de férias com aprovação em múltiplos níveis |
| **KPIs** | Rastreamento de indicadores de desempenho para equipes técnicas |
| **Assistente IA** | Chat com GPT integrado a documentos internos para perguntas e respostas inteligentes |

---

## Stack Tecnológica

### Frontend
- **React 18** — interface baseada em componentes com hooks
- **TypeScript** — tipagem completa em todo o frontend
- **Vite** — servidor de desenvolvimento rápido e build de produção otimizado
- **Tailwind CSS** — estilização utilitária com tokens de design personalizados
- **shadcn/ui + Radix UI** — componentes acessíveis e composáveis
- **TanStack Query (React Query v5)** — estado do servidor, cache e mutações
- **Wouter** — roteamento client-side leve
- **Lucide React** — sistema de ícones consistente
- **Recharts** — visualização de dados (gráficos de pizza, barras e Gantt)
- **@hello-pangea/dnd** — Kanban com arrastar e soltar

### Backend
- **Node.js + Express** — servidor REST API
- **TypeScript** — tipos compartilhados com o frontend via estrutura monorepo
- **Drizzle ORM** — queries tipadas com design schema-first
- **PostgreSQL (Neon Serverless)** — banco de dados cloud-native
- **Drizzle Zod** — geração automática de schemas Zod a partir dos modelos do banco
- **Multer** — upload de arquivos multipart
- **bcryptjs** — hash de senhas
- **jsonwebtoken** — autenticação e gestão de sessões via JWT

### Integrações e Serviços
- **OpenAI API (GPT-4o)** — assistente de documentos com IA
- **Google Drive API** — recuperação de documentos para contexto da IA
- **Replit Object Storage** — armazenamento de arquivos em nuvem para anexos de propostas
- **SendGrid** — notificações por e-mail transacional

### Experiência do Desenvolvedor
- **Monorepo** — `schema.ts` compartilhado entre frontend e backend para consistência total de tipos
- **ESBuild** — empacotamento rápido para produção no servidor
- **PostCSS** — pipeline de CSS com integração ao Tailwind

---

## Destaques da Arquitetura

```
├── client/              # Frontend React (Vite)
│   ├── src/
│   │   ├── pages/       # Um arquivo por módulo/página
│   │   ├── components/  # Componentes compartilhados e específicos
│   │   ├── hooks/       # Hooks React customizados
│   │   └── lib/         # Query client, utilitários
├── server/              # Backend Express
│   ├── routes.ts        # Todos os endpoints da API
│   ├── storage.ts       # Camada de acesso ao banco (Drizzle)
│   ├── auth.ts          # Middleware JWT e guards de papel
│   └── *.ts             # Módulos por funcionalidade (IA, storage, e-mail)
└── shared/
    └── schema.ts        # Fonte única de verdade para todos os modelos de dados
```

### Decisões de Design

- **Controle de Acesso por Papel (RBAC)** — três papéis (Colaborador, Diretor, Admin) com restrição de módulos por departamento
- **Full Stack Tipado** — `shared/schema.ts` é a fonte única de verdade; os tipos do Drizzle fluem do banco até os componentes React sem duplicação
- **UI Otimista** — mutações atualizam o cache imediatamente com rollback automático em caso de erro, garantindo uma UX fluida
- **Armazenamento com Fallback** — Object Storage para produção; fallback automático para sistema de arquivos local em desenvolvimento
- **Negócios Fechados Imutáveis** — propostas fechadas são bloqueadas para edição; modal somente leitura com acesso aos anexos

---

## Funcionalidades em Destaque

- Autenticação JWT com sessões persistentes e controle por papel
- Visibilidade de módulos por departamento (cada equipe vê apenas suas ferramentas)
- Kanban com arrastar e soltar e transições de coluna com validação de status
- Hierarquia de tarefas em múltiplos níveis (tarefas → subtarefas) com numeração WBS e rastreamento de dependências
- Edição inline de células em cronogramas/Gantt com salvamento automático
- Exportação em PDF de cronogramas de projetos via `html2canvas`
- Criação automática de registros financeiros no fechamento de negócios com cálculo de comissão, impostos e repasse
- Assistente de chat com IA e recuperação de documentos (padrão RAG)
- Notificações por e-mail transacional para fluxos de aprovação
- Design responsivo — funciona em desktop e mobile

---

## Como Rodar Localmente

### Pré-requisitos

- Node.js 18+
- Banco de dados PostgreSQL (ou uma instância serverless do [Neon](https://neon.tech))

### Variáveis de Ambiente

```env
DATABASE_URL=postgresql://...
JWT_SECRET=seu_jwt_secret
OPENAI_API_KEY=sk-...
SENDGRID_API_KEY=SG....
```

### Instalação e Execução

```bash
npm install
npm run db:push     # Aplica o schema no banco de dados
npm run dev         # Inicia frontend e backend simultaneamente
```

A aplicação estará disponível em `http://localhost:5000`.

---

## Acesso em Produção

O deploy de produção está disponível em:

**[gestao.bktech.com.br](https://gestao.bktech.com.br)**

---

## Licença

Este é um projeto privado desenvolvido para uso interno. Todos os direitos reservados.

---

<div align="center">

Desenvolvido com cuidado utilizando tecnologias web modernas.

</div>
