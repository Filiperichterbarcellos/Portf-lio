Sistema de Suporte Avançado para Jogadores de Tibia

Filipe Richter Barcellos

Curso: Engenharia de Software

Data de Entrega: 2025

Resumo

Este documento apresenta o desenvolvimento de uma plataforma web voltada para jogadores do jogo MMORPG Tibia. Inspirada em soluções como o Exevo Pan, a proposta é criar uma ferramenta moderna, responsiva e interativa que ofereça funcionalidades como análise de mercado, histórico de preços, rastreamento de bosses e estatísticas em tempo real. A aplicação visa atender as necessidades da comunidade ativa do jogo, utilizando tecnologias modernas como Node.js para o back-end e React.js no front-end, integradas a APIs externas para consumo de dados. Este projeto permite aplicar conhecimentos teóricos adquiridos no curso, como arquitetura de software, design de interface, segurança e boas práticas de desenvolvimento.

1 Introdução

1.1 Contexto

O Tibia é um dos MMORPGs mais antigos ainda em atividade, com uma comunidade fiel e extremamente ativa. Nos últimos anos, a demanda por ferramentas auxiliares ao jogo cresceu, especialmente para análise de mercado e gerenciamento de personagens. Embora existam soluções como o Exevo Pan, ainda há espaço para concorrência com diferenciais em usabilidade, performance e funcionalidades não exploradas.

1.2 Justificativa

A falta de plataformas alternativas ao Exevo Pan, especialmente com foco em experiência do usuário e visual moderno, abre oportunidade para o desenvolvimento de uma solução que ofereça funcionalidades complementares ou melhoradas, como integração com ferramentas de loot tracking, cotação de TC em tempo real, e visualização de histórico de preços por servidor.

1.3 Objetivos

Principal: Desenvolver uma plataforma web para jogadores de Tibia com funcionalidades avançadas de suporte ao jogo.

Secundários:

Integração com APIs como TibiaData e scrapers próprios.

Sistema de login e autenticação para funcionalidades personalizadas.

Visualização de estatísticas e gráficos interativos.

Exportação de relatórios ou dados para compartilhamento.

2 Descrição do Projeto

2.1 Tema do Projeto

Desenvolvimento de uma plataforma online para jogadores de Tibia com foco em dados de mercado, informações de personagens, alertas de bosses e ferramentas auxiliares como calculadora de Tibia Coins.

2.2 Problemas a Resolver

Dificuldade em encontrar dados confiáveis sobre preços por servidor.

Falta de ferramentas visuais para rastrear histórico de mercado.

Carência de plataformas alternativas com foco em UX/UI.

Necessidade de centralizar informações como eventos, bosses e cotação de moedas.

2.3 Limitações

A plataforma será inicialmente web (desktop/mobile), sem versão nativa mobile.

Funcionalidades como notificacões push e integrações com Discord ficam para versões futuras.

Apenas alguns servidores serão monitorados no MVP.

3 Especificação Técnica

3.1 Requisitos de Software

Requisitos Funcionais

RF1: Consulta de preço de itens por servidor.

RF2: Visualização de histórico de preços e médias.

RF3: Calculadora de conversão de Tibia Coins para R$.

RF4: Consulta de status de bosses e alertas.

RF5: Cadastro e login de usuários para recursos personalizados.

Requisitos Não Funcionais

RNF1: Tempo de resposta < 200 ms para buscas simples.

RNF2: Autenticação via OAuth2 (Google, Discord).

RNF3: Disponibilidade >= 99,5%.

RNF4: Layout responsivo e acessível.

RNF5: TLS em todas as comunicações.

3.2 Considerações de Design

Padrão MVC com separação clara entre camada de serviço, controle e apresentação.

Arquitetura em camadas: frontend, backend, banco de dados.

Design mobile-first com uso de Tailwind CSS e shadcn/ui.

Diagramas de casos de uso, componentes e containers com base no modelo C4.

3.3 Stack Tecnológica

Linguagens: JavaScript (Node.js no backend, React no frontend)

Frameworks e libs: Express.js, React 18, Tailwind CSS, shadcn/ui

ORM: Prisma

Banco de dados: PostgreSQL

Ferramentas: GitHub, Vercel, Railway, dbdiagram.io

3.4 Considerações de Segurança

Uso de OAuth2/OIDC para login seguro.

Criptografia TLS nas comunicações e dados sensíveis.

Validação de entradas para evitar ataques como SQL Injection e XSS.

4 Próximos Passos

Portfólio I: Implementação do back-end (entidades, API REST, autenticação).

Portfólio II: Interface web, integração com APIs de mercado e visualização de dados.

Portfólio III: Refino da experiência do usuário, responsividade e recursos extras.

5 Referências

TibiaData API Docs. Disponível em: https://docs.tibiadata.com/

React.js Documentation. Disponível em: https://reactjs.org/

Node.js Documentation. Disponível em: https://nodejs.org/en/docs

PostgreSQL Docs. Disponível em: https://www.postgresql.org/docs/

shadcn/ui Guide. Disponível em: https://ui.shadcn.com/

Prisma Docs. Disponível em: https://www.prisma.io/docs
