# Sprint Planning - Sprint 01 (Projeto Lumen)

**Data:** 25/03/2026  
**Participantes:** Facilitador (Scrum Master), Time de Desenvolvimento (Equipe)  
**Sprint Duration:** 1 semana (5 dias úteis)  
**Sprint Goal:** Estruturar a base do ecossistema, estabelecendo a comunicação de postagens no backend, padronização do frontend web e o fluxo principal do aplicativo Android (Autenticação e Sessão Pomodoro).

---

## 📊 Sprint Capacity

- **Velocity anterior:** N/A
- **Capacidade estimada:** N/A
- **Dias úteis disponíveis:** 5 dias
- **Impedimentos conhecidos:** Acesso do laboratório com máquinas que suportam Android Studio em horário contra o turno de aula

- **Cálculo da velocidade estimada:**
  > N/A

---

## 🎯 Sprint Goal

> Entregar os endpoints fundamentais de comunidade no backend, unificar a identidade visual do cliente web e garantir que o aplicativo Android tenha um fluxo funcional de ponta a ponta: desde o login até a sala de sessão sincronizada.

---

## 📋 User Stories Selecionadas

### Backend (API & Dados)

**Endpoint de Postagem**
- **Prioridade:** Alta
- **Story Points:** 3
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Validar se o `communityId` enviado no corpo da requisição existe no banco.
  - [ ] Verificar se o `userId` (extraído do JWT) está na lista de membros da comunidade. Retornar `403 Forbidden` caso contrário.
  - [ ] Persistir a postagem no banco utilizando o Prisma.
  - [ ] Documentar o uso do endpoint (formato do payload e respostas), anexar na tarefa e sinalizar no grupo.
**Notas técnicas:** Implementar seguindo a arquitetura de módulos e controllers do NestJS.

**Endpoint de Curtir Postagem**
- **Prioridade:** Média
- **Story Points:** 2
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Se não houver curtida prévia do usuário, criar o registro de "Like".
  - [ ] Se o usuário já curtiu, remover o registro (ação de toggle/descurtir).
  - [ ] Retornar o status atualizado e a contagem total de likes do post.
  - [ ] Documentar o uso do endpoint, anexar na tarefa e sinalizar no grupo.

---

### Frontend Web (UI/UX & Arquitetura)

**Padronização de UI/UX e Refatoração de CSS**
- **Prioridade:** Alta
- **Story Points:** 3
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Criar o arquivo `styles/variables.css` utilizando CSS Variables (`:root`) para cores, fontes e espaçamentos.
  - [ ] Substituir valores fixos nos arquivos CSS atuais pelas novas variáveis.
  - [ ] Garantir comportamento responsivo (Mobile First) com uso correto de Media Queries.

**Guia de Arquitetura e Organização Frontend**
- **Prioridade:** Média
- **Story Points:** 3
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Documentar estrutura de pastas (ex: `/js/services`, `/js/utils`, `/js/components`).
  - [ ] Padronizar e exemplificar o uso de `import/export`.
  - [ ] Documentar o padrão para chamadas `fetch()` para a API e sanitização de dados injetados no DOM (prevenção de XSS).
  - [ ] Anexar o documento na tarefa e informar no grupo.

---

### Mobile (Android)

**<Android> Interface de Cadastro**
- **Prioridade:** Alta
- **Story Points:** 5
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Desenvolver layouts seguindo o protótipo do Figma.
  - [ ] Implementar validação local de formato de e-mail e regra de senha mínima.
  - [ ] Consumir os endpoints de registro do backend.
  - [ ] Tratar erros (ex: e-mail já em uso) e exibir alertas claros ao usuário.

**<Android> Interface de Login**
- **Prioridade:** Alta
- **Story Points:** 5
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Desenvolver os inputs e botões conforme protótipo.
  - [ ] Consumir os endpoints de autenticação do backend.
  - [ ] Salvar o Token JWT recebido no `EncryptedSharedPreferences` para persistência segura da sessão.
  - [ ] Tratar falhas de login (credenciais inválidas, falha de rede) com alertas.

**<Android> Interface de Home**
- **Prioridade:** Alta
- **Story Points:** 3
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Implementar o layout base da tela principal.
  - [ ] Configurar a navegação (Intents/Navigation Component) para as outras telas do sistema, especialmente a sessão.

**<Android> Interface de Sessão**
- **Prioridade:** Crítica
- **Story Points:** 8
- **Assignee:** Time de Desenvolvimento
- **Critérios de Aceitação:**
  - [ ] Desenvolver a UI do cronômetro Pomodoro.
  - [ ] Criar gerenciamento de estados visuais (Focus / Rest) e exibir lista de participantes ativos.
  - [ ] Conectar eventos via WebSockets/Socket.io para sincronização do tempo e status entre os dispositivos e o backend.

---

**Total Comprometido:** 32 pontos

---

## ✅ Definition of Done

- [ ] Código revisado (Peer review ou validação cruzada no repositório).
- [ ] Endpoints testados e documentados (via Postman/Swagger ou Markdown).
- [ ] UI refatorada testada em pelo menos duas resoluções de tela (Mobile e Desktop).
- [ ] App Android compila sem erros, e JWT é persistido adequadamente.
- [ ] Comunicação WebSocket testada com pelo menos dois clientes simultâneos.
- [ ] Commitado no repositório com mensagem descritiva.
- [ ] Validação do Professor/Product Owner.

---

## 🎲 Riscos e Dependências

| Risco/Dependência | Impacto | Mitigação | Responsável |
|-------------------|---------|-----------|-------------|
| **Mobile dependente da API** (dependem do Backend auth) | Alto | Utilizar mocks/dados estáticos no Android até que o backend de Auth esteja deployado ou rodando localmente. | Time de dev |
| **Sincronia do Pomodoro** | Alto | Fazer uma prova de conceito simples do WebSocket no Android antes de integrar com a UI final. | Time de dev |
| **Refatoração CSS** pode quebrar telas existentes | Médio | Fazer substituição gradual das variáveis e revisar visualmente tela a tela. | Time de dev |

---

## 📝 Notas e Decisões

### Decisões Tomadas
- O JWT deve ser trafegado no Header `Authorization: Bearer <token>` em todas as chamadas `fetch()` no front web e no Retrofit/OkHttp no Android.
- O Prisma será utilizado para garantir o schema robusto nas operações de posts e likes.

### Action Items
- [ ] Definir e documentar o payload exato que o WebSocket enviará para os clientes de Android (ex: evento `timer_tick`, `session_start`).
- [ ] Validar o protótipo de UI da Home com a equipe antes da codificação final.

---

## 🤖 Sugestão de Assistência IA (opcional)

- [ ] Geração do Schema Prisma inicial para `Posts`, `Likes` e relação com `Communities` e `Users`.
- [ ] Refatoração das regras de CSS para extração automática do `:root`.
- [ ] Criação do Client do WebSocket em Java/Kotlin para o Android.
- [ ] Estrutura do módulo/controller base no NestJS para a rota de `/posts`.
