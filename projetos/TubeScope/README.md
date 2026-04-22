<div align="center">

# TubeScope

<p><strong>Analise canais do YouTube em segundos</strong></p>
<p>Insights de performance, vídeos em alta, engajamento, gráficos e recomendações de publicação em uma interface moderna.</p>

<p>
  <a href="https://tube-scope.replit.app/">🚀 Acessar o app</a>
</p>

<p>
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind-38BDF8?style=for-the-badge&logo=tailwindcss&logoColor=white" />
</p>

</div>

---

## ✨ Sobre o app

TubeScope é uma ferramenta de análise competitiva para YouTube que ajuda a entender rapidamente como qualquer canal público está performando. Basta colar uma URL, @handle ou ID do canal para ver vídeos em alta, métricas de engajamento, gráficos de desempenho e insights de publicação.

### O que ele entrega
- Resolução de URL, @handle e ID de canal
- Dashboard com KPIs, gráfico e tabela de vídeos
- Destaque para vídeos em alta e engajamento
- Filtros por período e ordenação por performance
- Insights de frequência de postagem
- Exportação em CSV
- Busca recente salva localmente

---

## 🎨 Destaques visuais

- Interface escura com acento vermelho estilo YouTube
- Componentes com animações suaves
- Gráficos e tabelas pensados para leitura rápida
- Layout responsivo para desktop e mobile

---

## 🛠️ Stack usada

### Frontend
- React + TypeScript
- Vite
- Tailwind CSS
- shadcn/ui
- TanStack Query
- Recharts
- Framer Motion
- Wouter

### Backend
- Node.js
- Express
- TypeScript
- Pino
- YouTube Data API v3
- Cache em memória com TTL

### Ferramentas compartilhadas
- OpenAPI
- Orval
- Zod
- pnpm workspaces

---

## 📌 Principais recursos

| Recurso | Descrição |
|---|---|
| Channel Analysis | Aceita URL, @handle e ID |
| Performance Dashboard | KPIs, gráficos e destaques |
| Video Table | Views, likes, comments e engagement |
| Publishing Insights | Frequência e consistência de posts |
| Smart Filters | Ordenação por views, likes, comments e mais |
| CSV Export | Baixe os dados filtrados |
| Recent Searches | Reabra canais rapidamente |
| Dark UI | Visual moderno e profissional |

---

## 🧭 Como funciona

1. O usuário insere a URL, @handle ou ID do canal.
2. O backend resolve o canal para um ID canônico.
3. Os dados e vídeos recentes são buscados na YouTube Data API.
4. O app calcula engajamento, tendências e insights.
5. A interface exibe tudo em um dashboard interativo.

---

## 📁 Estrutura do projeto

```bash
.
├── artifacts/
│   ├── tubescope/       # Frontend React + Vite
│   └── api-server/      # API Express
├── lib/
│   ├── api-spec/        # OpenAPI
│   ├── api-client-react # Hooks gerados
│   └── api-zod/         # Schemas gerados
└── pnpm-workspace.yaml
```

---

## 🚀 Como rodar

```bash
pnpm install
pnpm --filter @workspace/api-server run dev
pnpm --filter @workspace/tubescope run dev
```

---

## 💼 Feito para portfólio

Esse projeto foi pensado para chamar atenção de recrutadores, mostrando:
- visão de produto
- capricho visual
- arquitetura full-stack limpa
- uso real de API externa
- análise de dados com UX clara

---

## 🌐 Link oficial

**TubeScope:** https://tube-scope.replit.app/

---

## Licença

MIT
