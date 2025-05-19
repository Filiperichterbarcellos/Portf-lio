#  Sistema de Suporte Avançado para Jogadores de Tibia

**Filipe Richter Barcellos**  
Curso: Engenharia de Software  
Data de Entrega: 2025  

---

##  Resumo

Este projeto apresenta o desenvolvimento de uma plataforma web para jogadores de Tibia. Inspirado em ferramentas como o Exevo Pan, o sistema oferece análise de mercado, histórico de preços, rastreamento de bosses e estatísticas em tempo real. Utiliza tecnologias modernas como **Node.js** no back-end e **React.js** no front-end, integrando com APIs externas para consumo de dados. Aplica conceitos como arquitetura de software, design de interface e boas práticas de desenvolvimento.

---

##  Introdução

### Contexto

O Tibia é um dos MMORPGs mais antigos em atividade, com comunidade extremamente ativa. Há uma crescente demanda por ferramentas auxiliares para análise de mercado e gerenciamento de personagens.

### Justificativa

Mesmo com soluções como Exevo Pan, há espaço para alternativas com melhor UX/UI, integração de funcionalidades e diferenciais competitivos.

### Objetivos

**Principal:**  
Desenvolver uma plataforma web com funcionalidades avançadas para jogadores de Tibia.

**Secundários:**  
- Integração com APIs como TibiaData e scrapers próprios  
- Autenticação e funcionalidades personalizadas  
- Visualização de gráficos e estatísticas  
- Exportação de relatórios

---

##  Descrição do Projeto

### Tema
Plataforma para dados de mercado, informações de personagens, alertas de bosses e ferramentas como calculadora de Tibia Coins.

### Problemas a Resolver
- Falta de dados confiáveis por servidor  
- Ausência de histórico visual de mercado  
- Falta de alternativas com boa usabilidade  
- Centralização de eventos, bosses e economia

### Limitações
- Apenas versão web no MVP  
- Push notifications e integração com Discord em versões futuras  
- Monitoramento parcial de servidores no início

---

##  Especificação Técnica

### Requisitos Funcionais
- Consulta de preços por servidor  
- Histórico e média de preços  
- Calculadora de Tibia Coins  
- Status e alertas de bosses  
- Login de usuários

### Requisitos Não Funcionais
- Resposta rápida (< 200ms)  
- OAuth2 (Google/Discord)  
- Alta disponibilidade  
- Design responsivo  
- Criptografia (TLS)

### Considerações de Design
- Arquitetura MVC  
- Camadas separadas: front, back e banco  
- Design mobile-first com Tailwind e shadcn/ui  
- Uso de diagramas de casos de uso e modelo C4

---

##  Stack Tecnológica

- **Linguagens:** JavaScript (Node.js + React)  
- **Frameworks:** Express.js, React 18, Tailwind CSS, shadcn/ui  
- **ORM:** Prisma  
- **Banco:** PostgreSQL  
- **Ferramentas:** GitHub, Vercel, Railway, dbdiagram.io

---

##  Segurança

- OAuth2/OIDC para autenticação  
- TLS nas conexões  
- Validação contra SQL Injection e XSS

---

##  Próximos Passos

- **Portfólio I:** Backend com API e autenticação  
- **Portfólio II:** Frontend + integração com APIs  
- **Portfólio III:** Melhorias de UX/UI e responsividade

---

## 🔗 Referências

- [TibiaData API](https://docs.tibiadata.com/)  
- [React.js](https://reactjs.org/)  
- [Node.js](https://nodejs.org/en/docs)  
- [PostgreSQL](https://www.postgresql.org/docs/)  
- [shadcn/ui](https://ui.shadcn.com/)  
- [Prisma](https://www.prisma.io/docs)
