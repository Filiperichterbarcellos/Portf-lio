# 🧙 Plataforma Tibia - TCC

Projeto de TCC inspirado na estrutura e funcionalidades do Exevo Pan, com objetivo de oferecer uma plataforma moderna para jogadores de Tibia.

## 🧩 Monorepo Estruturado

- **apps/web**: aplicação frontend (React + Tailwind + shadcn/ui)
- **apps/api**: API backend em Node.js + Express + Prisma
- **packages/ui**: componentes compartilháveis
- **docs/**: documentação acadêmica e diagramas

## 🚀 Tecnologias

- Frontend: React 18, Tailwind, shadcn/ui
- Backend: Node.js, Express.js
- ORM: Prisma
- Banco: PostgreSQL
- Hospedagem: Vercel (web) + Railway (api/db)

## 📦 Como iniciar

```bash
# Backend
cd apps/api
npm install
npx prisma generate
npm run dev
```

## 📚 Créditos

Este projeto se inspira na arquitetura e proposta do [Exevo Pan](https://github.com/xandjiji/exevopan-monorepo)
