# Sprint Planning - Sprint 01 (Revisada)

**Data**: 25/02/2026 a 04/03/2026 (Prazo de entrega do Fluxo Principal)
**Participantes**: Facilitador (Scrum Master), Time de Desenvolvimento
**Sprint Duration**: 1 semana (5 dias úteis)
**Sprint Goal**: Início de estudos de tecnologias, setup inicial da infraestrutura e início da construção visual e estrutural do fluxo principal.

## 📊 Sprint Capacity
- Capacidade estimada: ~20h pontos
- Dias úteis disponíveis: 5 dias úteis
- Impedimentos conhecidos: Alta demanda de tempo em estudo sobre tecnologias e readequação do cronograma (sprint executada em 1 semana, com planejamento inicial de 2 semanas).

## 🎯 Sprint Goal
> Estabelecer o setup inicial de desenvolvimento, absorver a curva de aprendizado e estruturar a base do projeto, iniciando as tarefas do fluxo de autenticação.

## 📋 Histórias de Usuário e Tarefas

### Setup de Infraestrutura e Banco de Dados (Fundação)
- Prioridade: Must Have
- Assignee: Time de Desenvolvimento
- Contexto: Devido ao tempo reduzido, esta etapa consumiu a maior parte da Sprint para garantir uma base sólida.
- Tarefas Vinculadas:
    - [ ] Estudos iniciais #19 (Em Andamento)
    - [x] Definir estruturas de pastas #3
    - [x] Iniciar projeto do Backend #2
    - [ ] Revisão do Modelo de Banco de Dados #11
    - [x] Conectar com banco de dados #8 (Transferido/Em andamento)
    - [ ] Criar entidades ORM #7 (Transferido/Em andamento)

### Início do Fluxo de Autenticação (RF0001 e RF0002)
- Prioridade: Must Have
- Histórias de Usuário:
    - RF0001 (Cadastro de Usuário): Como um novo usuário, eu quero criar uma conta informando nome, e-mail, celular e senha, para acessar o sistema. 
    - RF0002 (Login de Usuário): Como um usuário registrado, eu quero fazer login com e-mail e senha, para acessar minha conta. 
    > Contexto: O desenvolvimento foi iniciado, focando na criação das telas e no esqueleto das rotas, mas a integração completa de autenticação precisará ser finalizada na próxima sprint.

- Tarefas Vinculadas:
    - [ ] Desenvolver Telas - Primeira Entrega #1 (Iniciado focado em Login/Cadastro)
    - [ ] Sistema de Usuários - Backend #5 (Apenas setup)
    - [ ] Endpoint de Cadastrar #6 (Estrutura inicial)
    - [ ] Endpoint de Login #9 (Estrutura inicial)
    - [ ] Integração do Fluxo de Autenticação #4 (Bloqueado para a próxima sprint)

### Setup de Sessão (RF0021) e Home 
> Contexto: Determinadas tarefas referentes ao uso contínuo da aplicação não puderam ser iniciadas devido ao corte no tempo da Sprint. Elas foram movidas diretamente para a Sprint 02.

- Tarefas Vinculadas:
    - [ ] Desenvolver Tela de Home #5
    - [ ] Desenvolver Tela da Sessão Ativa #6
    - [ ] Sistema de Sessão - Backend #10 (Em Andamento)
    - [ ] Endpoints e Integrações de IA/WebSockets (#13 a #18)

### ✅ Definition of Done
- [x] Ambientes de desenvolvimento configurados e repositórios organizados.
- [x] Estudos das tecnologias base concluídos para iniciar o código.
- [ ] Modelagem de banco de dados revisada.
- [ ] Telas iniciais (Login/Cadastro) mapeadas/desenhadas no código.
