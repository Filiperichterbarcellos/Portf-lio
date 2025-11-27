# RFC – Tibia Pulse 1.0.1

**Título:** Sistema de Suporte Avançado para Jogadores de Tibia  
**Autor:** Filipe Richter Barcellos  
**Curso:** Engenharia de Software  
**Entrega:** 2025  

---

##  Resumo

Plataforma web que centraliza dados de personagens, rastreamento de bosses, calculadoras e um **Guide** com recomendações de quests/hunts e progresso salvo por usuário.  
Inspirado em ferramentas como **Exevo Pan**, mas com foco em **onboarding** e **acompanhamento contínuo**.

**Stack principal:**

- **Frontend:** React 18 (Vite + Tailwind CSS + shadcn/ui)
- **Backend:** Node.js + Express
- **Banco:** PostgreSQL + Prisma
- **Infra/Deploy:** Azure (Static Web App + App Service)
- **Proxy de scraping:** Azure Functions (TrackerProxy) para contornar bloqueios (403) em rastreamento.

---

##  Contexto e Motivação

- Tibia oferece pouca orientação para iniciantes; após o level 8 o jogador fica sem direção.
- Ferramentas atuais não cobrem **onboarding** nem **trilhas guiadas**.
- Necessidade de uma experiência única, com:
  - Dados consolidados
  - Progresso salvo por usuário
  - UX moderna e responsiva

---

##  Objetivos

**Objetivo principal**

- Plataforma de suporte com:
  - Dados de mercado/bosses
  - Onboarding via **Guide** (trilha de quests/hunts com progresso salvo)

**Objetivos secundários**

- Consultar status de personagens (TibiaData + scraping de `tibia.com` + GuildStats).
- Rastrear bosses e permitir **favoritar**.
- Implementar calculadoras (ex.: coins, loot) e worlds com fallback.
- Autenticação simplificada via **Google** (login via Discord removido).
- Guide com recomendações de quests/hunts e progresso salvo (**GuideProgress**).
- UI estável, sem sumir listas quando chamadas à API falharem.

---

##  Escopo e Limitações

**Incluído no escopo:**

- Busca de personagens.
- Bosses com favoritos.
- Lista de worlds com fallback.
- Calculadoras (coins, loot etc.).
- Guide com progresso por usuário.
- Blog com changelog e posts (conteúdo estático).

**Excluído no MVP:**

- App mobile nativo.
- Notificações push.
- Login via Discord (removido).
- Integração com TibiaTrade/Bazar.

**Dados de tracker:**

- Uso de **proxy próprio** em Azure Functions (`TrackerProxy`) para contornar erros **403** em integrações como GuildStats.

---

##  Arquitetura

**Frontend**

- React 18 + Vite
- Tailwind CSS + shadcn/ui
- React Router
- Domínio: `www.tibiapulse.com.br`
- Deploy em **Azure Static Web Apps**

**Backend**

- Node.js + Express
- Swagger para documentação (`/docs`)
- CORS configurado
- Deploy em **Azure App Service**

**Banco de Dados**

- PostgreSQL (Azure)
- ORM: Prisma

**Proxy / Scraping**

- Azure Functions (HTTP trigger)
- Uso de `TRACKER_PROXY_URL` para GuildStats e outros endpoints bloqueados

**Infra / Padrões**

- Azure Static Web Apps (frontend) + App Service (API)
- CI/CD com GitHub Actions + `prisma migrate deploy`
- Padrão **MVC**:
  - Controllers
  - Services
  - Routes
  - DTOs tipados
  - Middlewares (auth, error handler)

---

##  Modelagem (Prisma – `schema.prisma`)

**User**

- `id`
- `email`
- `name`
- `mainCharacter`
- `provider` (GOOGLE)
- `favorites` (relação)
- `guideProgress` (relação)

**Favorite**

- `id`
- `userId`
- `type` (`BOSS` / `AUCTION`)
- `key`
- `snapshot` (JSON)
- Constraint única: `(userId, type, key)`

**GuideProgress**

- `id`
- `userId`
- `type` (`QUEST` / `HUNT`)
- `slug`
- `status` (`NOT_STARTED` / `IN_PROGRESS` / `DONE`)
- `updatedAt`

---

##  Fluxos Principais

### Autenticação

- OAuth2 via **Google**
- Tokens **JWT**
- Provedor ativo: apenas Google (Discord removido)

### Characters

- Consulta via **TibiaData** + scraping de `tibia.com`
- Fallback via:
  - Proxy público (AllOrigins/Jina)
  - **TrackerProxy** (Azure Functions) para GuildStats:
    - abas de `history`
    - `deaths`
    - outras métricas relevantes

### Bosses

- Kill statistics via TibiaData
- Possibilidade de **favoritar bosses** (salvo em `Favorite.snapshot`)

### Worlds

- Lista de worlds com fallback se API principal falhar (`ERR_BAD_RESPONSE`)

### Guide

- Endpoints:
  - `GET /api/guide/quests`
  - `GET /api/guide/hunts`
  - `GET /api/guide/progress` (auth)
  - `PUT /api/guide/progress` (auth)
- Não exige filtro por personagem.
- Front mantém as listas mesmo se a chamada de progresso falhar.
- Progresso também fica visível em **"Minha conta"**.

### Blog

- Posts em `src/data/blog.ts`
- Contém changelog da versão **1.0.1**.

---

##  Endpoints (principais)

```http
GET  /api/characters/:name

GET  /api/bosses
GET  /api/bosses/killstats/:world

GET  /api/worlds
GET  /api/worlds/:name

GET  /api/guide/quests
GET  /api/guide/hunts
GET  /api/guide/progress       (auth)
PUT  /api/guide/progress       (auth)

POST /api/auth/google
POST /api/auth/callback        (fluxo OAuth)

GET  /health
GET  /docs                     (Swagger)
