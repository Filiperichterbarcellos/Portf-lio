#  RFC - Sistema de Suporte Avançado para Jogadores de Tibia

**Título do Projeto:** Sistema de Suporte Avançado para Jogadores de Tibia  
**Nome do Estudante:** Filipe Richter Barcellos  
**Curso:** Engenharia de Software  
**Data de Entrega:** 2025  

---

##  Resumo

Este projeto apresenta o desenvolvimento de uma plataforma web inteligente voltada para jogadores do MMORPG Tibia. Inspirada em ferramentas como o Exevo Pan, a plataforma oferece funcionalidades essenciais como análise de mercado, histórico de preços de itens, rastreamento de bosses, além de uma calculadora de conversão de Tibia Coins para Real. O diferencial proposto é um sistema exclusivo de **trilha para iniciantes**, que visa guiar novos jogadores com dicas de evolução, locais de caça, sugestões de quests e orientação sobre vocações, superando a ausência de onboarding existente no jogo original. 

A plataforma será construída com **Node.js** no back-end e **React.js** no front-end, priorizando desempenho, modularidade e facilidade de manutenção. Além disso, será adotado o banco de dados **PostgreSQL** e a camada de estilo com **Tailwind CSS + shadcn/ui**. O projeto se propõe a aplicar práticas modernas de arquitetura de software, segurança, experiência do usuário e integração com APIs externas para oferecer uma solução robusta e acessível à comunidade Tibiana.


---

## 1. Introdução

### 1.1 Contexto

O Tibia é um jogo online lançado em 1997, inteiramente em inglês, com mínima orientação para jogadores novatos. Após o level 8, o jogador é lançado ao mundo sem direção definida. Embora isso seja parte da “magia” do jogo, representa uma barreira de entrada significativa, especialmente para novos jogadores.

### 1.2 Justificativa

Ferramentas existentes, como o Exevo Pan, oferecem suporte para jogadores avançados, mas não contemplam a experiência de onboarding. O projeto propõe a criação de uma plataforma acessível, com **um módulo dedicado à progressão de iniciantes**, promovendo uma experiência mais guiada, agradável e educativa para novos usuários.

### 1.3 Objetivos

**Objetivo Principal:**  
Desenvolver uma plataforma de suporte a jogadores de Tibia com foco em dados de mercado e onboarding de novos jogadores.

**Objetivos Secundários:**  
- Criar ferramentas de análise de preços, rastreamento de bosses e calculadoras  
- Implementar uma trilha interativa para iniciantes com guias de evolução, quests e glossário  
- Oferecer visualização e personalização da jornada do jogador  
- Utilizar tecnologias modernas para garantir escalabilidade, usabilidade e desempenho

---

## 2. Descrição do Projeto

### 2.1 Tema do Projeto
Desenvolvimento de um sistema web baseado em JavaScript fullstack, com Node.js e React, inspirado no Exevo Pan, acrescido de um **Guia Interativo para Iniciantes no Tibia**.

### 2.2 Problemas a Resolver
- Falta de onboarding no jogo original  
- Escassez de ferramentas acessíveis a jogadores novatos  
- Carência de integração entre dados de mercado e informações úteis em um só lugar  
- Dificuldade de aprendizado para iniciantes e frustração nas primeiras horas de jogo

### 2.3 Limitações
- O MVP não incluirá aplicativo mobile nativo  
- Recursos como sistema de notificações e login via Discord serão tratados como melhorias futuras  
- Cobertura inicial restrita a um conjunto de servidores selecionados

---

## 3. Especificação Técnica

### 3.1 Requisitos de Software

**Requisitos Funcionais (RF):**
- RF01: Visualizar preços de itens por servidor  
- RF02: Exibir histórico de preços com média e variação  
- RF03: Consultar status de bosses e timers  
- RF04: Utilizar calculadora de conversão de Tibia Coins para moedas do jogo e reais  
- RF05: Realizar login/autenticação via Google  
- RF06: Favoritar bosses ou itens para rastrear  
- RF07: Acessar trilha de iniciante com sugestões de up, quests e equipamentos  
- RF08: Marcar progresso na trilha de iniciante e salvar preferências

**Requisitos Não Funcionais (RNF):**
- RNF01: Resposta rápida nas APIs (<200ms)  
- RNF02: Interface mobile-first e acessível  
- RNF03: TLS obrigatório para todas as conexões  
- RNF04: Proteção contra injeções, XSS e armazenamento seguro com hash  
- RNF05: Alta disponibilidade (>=99,5%)

**Diagrama de Casos de Uso:** (ver docs/diagramas/casos-uso.png)

---

### 3.2 Considerações de Design

**Arquitetura:**
- Adotado o padrão MVC com separação entre controle, serviço e apresentação  
- APIs RESTful com rotas desacopladas para dados públicos e privados  
- Prisma ORM para facilitar manutenção e migrações no banco

**Modelagem em Níveis (Modelo C4):**
- Nível de contexto: jogador interage com frontend via browser  
- Nível de contêiner: frontend (React), backend (Node.js + Express), banco (PostgreSQL)  
- Nível de componentes: controllers, serviços, módulos de autenticação e rastreamento  
- Nível de código: separação de rotas, DTOs e middlewares

---

### 3.3 Stack Tecnológica

| Camada        | Tecnologia                      |
|---------------|----------------------------------|
| Frontend      | React 18, Tailwind, shadcn/ui    |
| Backend       | Node.js + Express                |
| ORM           | Prisma                           |
| Banco         | PostgreSQL                       |
| APIs externas | TibiaData API + scraping         |
| Autenticação  | OAuth2 via Google                |
| DevOps        | GitHub, Vercel, Railway          |

---
A escolha da stack tecnológica foi fundamentada em critérios como robustez, produtividade, comunidade ativa e compatibilidade com o modelo arquitetural adotado.

- **Node.js (Express)**: escolhido para o back-end devido à sua leveza, escalabilidade e compatibilidade com arquiteturas baseadas em APIs REST. Sua natureza assíncrona permite lidar com múltiplas requisições de forma eficiente, o que é essencial em funcionalidades como consulta de mercado e rastreamento de bosses.

- **React.js (com Tailwind CSS e shadcn/ui)**: no front-end, o React possibilita criação de interfaces modulares e reativas, com ótimo desempenho e manutenibilidade. Tailwind CSS e shadcn/ui foram incluídos para acelerar o desenvolvimento e garantir design responsivo com boa usabilidade.

- **PostgreSQL**: banco de dados relacional que fornece segurança, integridade e alta performance para lidar com dados relacionais como usuários, alertas, itens, históricos de mercado e progresso da trilha.

- **Prisma ORM**: para facilitar a comunicação entre o back-end e o banco de dados, promovendo tipagem, segurança e maior produtividade no desenvolvimento.

- **Vercel (front) + Railway (back)**: plataformas modernas para deploy contínuo e escalável, com integração direta com GitHub.

Essa stack oferece o equilíbrio ideal entre desempenho, curva de aprendizado e boas práticas modernas, além de estar alinhada com o objetivo do projeto: construir um sistema acessível, rápido e confiável.
“A escolha dessa stack também visa facilitar a curva de aprendizado e adoção futura por parte da comunidade Tibiana e de desenvolvedores interessados em contribuir com o projeto.”

### 3.4 Considerações de Segurança

- Uso de OAuth2/OIDC para evitar manipulação de senhas diretamente  
- Todas as requisições protegidas com TLS (HTTPS)  
- Inputs validados no frontend e backend  
- Hashing com bcrypt em qualquer credencial salva  
- Proteções CSRF e CORS configuradas via middleware

---

## 4. Próximos Passos

| Etapa        | Atividades                                    | Período   |
|--------------|------------------------------------------------|-----------|
| Portfólio I  | Modelagem, banco, autenticação e APIs básicas | em breve     |
| Portfólio II | Frontend, integração de trilha e painel geral | em breve     |
| Finalização  | Testes, refino da experiência, entrega final  | em breve     |

---

## 5. Referências

- [TibiaData API](https://docs.tibiadata.com/)  
- [React.js](https://reactjs.org/)  
- [Node.js](https://nodejs.org/en/docs)  
- [Prisma ORM](https://www.prisma.io/docs)  
- [PostgreSQL](https://www.postgresql.org/docs/)  
- [shadcn/ui](https://ui.shadcn.com/)  
- [Exevo Pan GitHub](https://github.com/xandjiji)

---

## 6. Apêndices

- Diagramas: Casos de Uso, ORM, C4 (ver pasta `docs/diagramas`)  
- Protótipo de tela da trilha de iniciante (em desenvolvimento no Figma)  
- Exemplo de API REST com rotas autenticadas e públicas

---

## 7. Avaliações de Professores

**Considerações Professor/a 1:**  
Nome: __________________________________  
Assinatura: _____________________________  

**Considerações Professor/a 2:**  
Nome: __________________________________  
Assinatura: _____________________________  

**Considerações Professor/a 3:**  
Nome: __________________________________  
Assinatura: _____________________________  
