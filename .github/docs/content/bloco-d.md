<!-- markdownlint-disable -->
# Bloco D: Desenvolvimento e Gestão de Produto - Perspectiva para Desenvolvedores

## Resumo Executivo

O desenvolvimento e gestão de produtos digitais constituem disciplinas estratégicas que transcendem a implementação técnica, abrangendo desde a definição de roadmaps até a colaboração cross-funcional entre equipes de produto, design e tecnologia. Este documento explora cinco dimensões fundamentais: metodologias ágeis (Scrum e Kanban) como frameworks para entregas iterativas e incrementais; o ciclo de vida completo de desenvolvimento de produtos desde pesquisa até acompanhamento pós-lançamento; estratégias de roadmap de produto e frameworks de priorização para direcionamento estratégico; gestão disciplinada de backlog e sprint planning para estruturação de trabalho em tarefas executáveis; e práticas de colaboração multidisciplinar que quebram silos organizacionais.

Para desenvolvedores de software, dominar esses conceitos representa evolução de executor tático para contribuidor estratégico, capacitando participação ativa em decisões de produto, compreensão do impacto de negócio de implementações técnicas, e comunicação efetiva com stakeholders não-técnicos. A gestão eficaz de backlog reduz ambiguidade através de histórias de usuário bem escritas e critérios de aceitação claros, minimizando retrabalho. Sprint planning disciplinado oferece oportunidade de influenciar escopo técnico, levantar riscos arquiteturais, e negociar inclusão de dívida técnica em backlog usando frameworks de priorização baseados em dados. A colaboração cross-funcional quebra silos através de envolvimento antecipado em decisões, workshops de cocriação, e alinhamento em outcomes de negócio ao invés de outputs técnicos.

Este material apresenta frameworks práticos (RICE, MoSCoW, Kano Model, MUSCLE), templates de documentação técnica (user stories, acceptance criteria, technical spikes), estratégias de comunicação entre equipes, e casos reais que demonstram como metodologias ágeis, priorização baseada em dados e colaboração multidisciplinar convergem para criar produtos que equilibram excelência técnica com geração de valor mensurável. O objetivo é equipar desenvolvedores com competências que transcendem conhecimento técnico, preparando-os para atuar como tech leads, engineering managers e contribuidores estratégicos no desenvolvimento de produtos digitais de impacto.

## 1. Introdução e Conceitos Fundamentais

### 1.1 Desenvolvimento de Produtos vs. Desenvolvimento de Projetos

O desenvolvimento de produtos digitais diferencia-se fundamentalmente do desenvolvimento de projetos tradicionais em três dimensões críticas:

**Horizonte Temporal e Continuidade**

Projetos possuem início e fim bem definidos, com escopo fixo e entrega única. Produtos, por outro lado, são organismos vivos que evoluem continuamente baseado em feedback de mercado, dados de uso e mudanças tecnológicas. Um projeto típico de migração de banco de dados tem término claro quando a migração é concluída; um produto como IDE (Visual Studio Code) evolui perpetuamente através de releases incrementais que adicionam funcionalidades, corrigem bugs e adaptam-se a novas linguagens de programação.

**Foco em Valor vs. Foco em Entrega**

Projetos medem sucesso por entrega dentro de prazo, escopo e orçamento (triângulo de ferro da gestão de projetos). Produtos medem sucesso por geração de valor mensurável para usuários e negócio, utilizando métricas como retenção, engajamento, NPS (Net Promoter Score), revenue e market share. Um desenvolvedor em contexto de projeto foca em "implementar todas as funcionalidades especificadas no prazo"; um desenvolvedor em contexto de produto foca em "construir funcionalidades que resolvem problemas reais e geram adoção mensurável".

**Aprendizado Iterativo vs. Execução Linear**

Projetos seguem metodologia waterfall ou híbrida com fases sequenciais (requisitos → design → implementação → testes → deploy). Produtos abraçam incerteza através de ciclos iterativos curtos que validam hipóteses, coletam feedback e adaptam direção baseado em aprendizados. Build-Measure-Learn loop popularizado por Lean Startup exemplifica essa abordagem: construir MVP (Minimum Viable Product), medir impacto com dados reais, aprender com resultados e iterar.

### 1.2 O Papel do Desenvolvedor na Gestão de Produtos

Desenvolvedores modernos atuam como contribuidores estratégicos além de executores técnicos, participando ativamente de:

**Descoberta de Produto (Product Discovery)**

Validação de viabilidade técnica de hipóteses através de protótipos, spikes técnicos e provas de conceito. Exemplo: antes de comprometer 3 meses de desenvolvimento em feature de real-time collaboration, desenvolvedor lidera spike de 1 semana testando WebRTC vs. WebSocket vs. Operational Transform para validar arquitetura viável.

**Definição de Escopo Técnico**

Tradução de requisitos de negócio em especificações técnicas, identificação de dependências arquiteturais e estimativa fundamentada de esforço. Exemplo: Product Manager solicita "integração com Google Calendar"; desenvolvedor mapeia escopo técnico (OAuth 2.0, Calendar API v3, sync bidirecional, conflict resolution) e identifica complexidade oculta.

**Priorização Informada por Dados Técnicos**

Contribuição para decisões de priorização com perspectiva de custo técnico, dívida técnica e risco arquitetural. Exemplo: feature de relatórios customizados tem alto valor de negócio mas requer refatoração do data layer; desenvolvedor quantifica trade-off usando framework RICE para informar decisão.

**Comunicação de Trade-offs Técnicos**

Articulação de trade-offs entre velocidade e qualidade, MVP vs. solução escalável, build vs. buy para stakeholders não-técnicos. Exemplo: explicar para Product Manager que implementação in-house de payment processing levaria 6 meses vs. integração com Stripe em 2 semanas, mas com vendor lock-in.

### 1.3 Fundamentos de Metodologias Ágeis

Metodologias ágeis emergem como resposta a limitações de waterfall no contexto de desenvolvimento de software, priorizando:

**Manifesto Ágil - Valores Fundamentais**

1. **Indivíduos e interações** sobre processos e ferramentas
2. **Software funcionando** sobre documentação abrangente
3. **Colaboração com cliente** sobre negociação de contrato
4. **Resposta a mudanças** sobre seguir plano

**Princípios Ágeis Relevantes para Desenvolvimento de Produtos**

- Entregas frequentes de software funcionando (semanas ao invés de meses)
- Colaboração diária entre pessoas de negócio e desenvolvedores
- Construir projetos ao redor de indivíduos motivados com ambiente e suporte necessários
- Excelência técnica e bom design aumentam agilidade
- Simplicidade - arte de maximizar trabalho não feito
- Reflexão regular sobre como se tornar mais eficaz e ajuste de comportamento

**Frameworks Ágeis - Scrum vs. Kanban**

Scrum estrutura trabalho em iterações time-boxed (sprints) com papéis, artefatos e cerimônias bem definidas. Kanban foca em fluxo contínuo através de visualização, limitação de WIP (Work In Progress) e otimização de throughput. Scrum adequa-se a equipes que valorizam cadência previsível e cerimônias estruturadas; Kanban adequa-se a equipes que lidam com alta variabilidade e priorizam flexibilidade.

## 2. Metodologias Ágeis: Scrum e Kanban

### 2.1 Scrum - Framework de Entregas Iterativas

Scrum organiza desenvolvimento em sprints de 1-4 semanas (tipicamente 2 semanas), cada um produzindo incremento potencialmente shippable do produto.

#### 2.1.1 Papéis no Scrum

**Product Owner (PO)**

Responsável por maximizar valor do produto e trabalho da equipe de desenvolvimento. Responsabilidades incluem:

- Gerenciar e priorizar Product Backlog baseado em valor de negócio
- Assegurar que backlog é visível, transparente e compreendido
- Aceitar ou rejeitar incrementos de produto ao final de cada sprint
- Tomar decisões sobre escopo e trade-offs

Para desenvolvedores: PO é parceiro estratégico, não chefe. Boas práticas incluem educar PO sobre complexidade técnica, propor alternativas de menor custo para atingir mesmo outcome, e questionar premissas quando dados técnicos contradizem hipóteses de negócio.

**Scrum Master (SM)**

Facilitador que assegura que time entende e pratica Scrum. Responsabilidades incluem:

- Facilitar cerimônias Scrum (planning, daily, review, retrospective)
- Remover impedimentos que bloqueiam progresso da equipe
- Proteger equipe de interrupções externas e mudanças de escopo mid-sprint
- Coaching em práticas ágeis e melhoria contínua

Para desenvolvedores: SM não é gerente de projeto. Boas práticas incluem sinalizar impedimentos proativamente, contribuir para retrospectivas com dados concretos sobre processo, e colaborar na identificação de melhorias de produtividade.

**Development Team (Devs)**

Time auto-organizado e cross-funcional que entrega incremento "Done" ao final de cada sprint. Características:

- Tamanho ideal: 3-9 pessoas (pequeno o suficiente para agilidade, grande o suficiente para completar trabalho significativo)
- Cross-funcional: possui todas habilidades necessárias para criar incremento (frontend, backend, QA, DevOps)
- Auto-organizado: decide internamente como transformar Product Backlog em incremento funcional

Para desenvolvedores: responsabilidade é coletiva, não individual. Boas práticas incluem pair programming para conhecimento compartilhado, code review rigoroso, e foco em outcome da sprint ao invés de tarefas individuais.

#### 2.1.2 Artefatos do Scrum

**Product Backlog**

Lista ordenada de tudo que pode ser necessário no produto, evoluindo constantemente. Itens de maior ordem (topo) são mais detalhados e estimados; itens de menor ordem são mais vagos.

Exemplo de Product Backlog estruturado:

```markdown
## Product Backlog - Sistema de Autenticação

### High Priority (Next Sprint)
1. [STORY-123] Como usuário, quero fazer login com Google OAuth para acessar rapidamente
   - Estimativa: 8 pontos
   - Valor de Negócio: Alto (reduz fricção de signup em 40% baseado em A/B test)
   - Dependências: Nenhuma
   - Acceptance Criteria: (ver detalhes abaixo)

2. [STORY-124] Como desenvolvedor, quero migrar sessões de cookies para JWT para escalar horizontalmente
   - Estimativa: 13 pontos
   - Valor Técnico: Alto (desbloqueio para multi-region deployment)
   - Dependências: Nenhuma
   - Acceptance Criteria: (ver detalhes abaixo)

### Medium Priority (Backlog Refinado)
3. [STORY-125] Como usuário, quero autenticação de 2 fatores para maior segurança
   - Estimativa: 21 pontos (épico - quebrar em histórias menores)
   - Valor de Negócio: Médio (requisito para clientes enterprise)

### Low Priority (Backlog Grooming Necessário)
4. [EPIC-45] Suporte para login com biometria em mobile apps
   - Estimativa: TBD
   - Valor de Negócio: TBD (validar com research)
```

**Sprint Backlog**

Subset do Product Backlog selecionado para sprint atual, mais plano de entrega criado pela Development Team. Atualizado diariamente conforme trabalho progride.

Exemplo de Sprint Backlog (Sprint 23 - Autenticação OAuth):

```markdown
## Sprint 23 Backlog (2 semanas - Jan 15-26)
Sprint Goal: Implementar login com Google OAuth e reduzir signup friction

### User Stories Committed
- [STORY-123] Login com Google OAuth (8 pts)
- [STORY-124] Migração para JWT (13 pts)
Total: 21 pontos (velocity média: 20-24 pontos)

### Tasks Breakdown
STORY-123 - Google OAuth:
- [ ] Setup Google Cloud Console e obter credentials (Dev: Ana, 2h)
- [ ] Implementar OAuth 2.0 flow com Passport.js (Dev: Carlos, 8h)
- [ ] Criar endpoint /auth/google/callback (Dev: Carlos, 4h)
- [ ] Integrar com user provisioning existente (Dev: Ana, 6h)
- [ ] Adicionar botão "Login with Google" no frontend (Dev: Marina, 4h)
- [ ] Escrever testes de integração (Dev: Marina, 6h)
- [ ] Atualizar documentação de API (Dev: Carlos, 2h)

STORY-124 - JWT Migration:
- [ ] Implementar geração e validação de JWT (Dev: Pedro, 6h)
- [ ] Criar middleware de autenticação (Dev: Pedro, 4h)
- [ ] Migrar endpoints para usar JWT auth (Dev: Ana, 12h)
- [ ] Implementar refresh token mechanism (Dev: Pedro, 8h)
- [ ] Atualizar SDK do cliente (Dev: Marina, 6h)
- [ ] Testes de carga com JWT vs cookies (Dev: Carlos, 4h)
- [ ] Documentação de migração (Dev: Ana, 2h)

### Definition of Done
- [ ] Código revisado e aprovado por pelo menos 1 dev
- [ ] Cobertura de testes >= 80%
- [ ] Documentação atualizada (API docs, README)
- [ ] Deploy em staging e validação com PO
- [ ] Performance metrics dentro de SLA (p95 < 200ms)
```

**Incremento (Product Increment)**

Soma de todos itens do Product Backlog completados durante sprint atual e sprints anteriores. Incremento deve estar em estado "Done" - funcionando e potencialmente shippable, mesmo se PO decidir não fazer release.

Definition of Done (DoD) típica para equipe de desenvolvimento:

```markdown
## Definition of Done - Engineering Team

### Code Quality
- [ ] Code review aprovado por senior developer
- [ ] Sem violações de linter ou static analysis
- [ ] Cobertura de testes >= 80% (unit + integration)
- [ ] Sem vulnerabilidades de segurança (SAST scan)

### Funcionalidade
- [ ] Todos acceptance criteria atendidos
- [ ] Testado manualmente em staging environment
- [ ] Validado por Product Owner
- [ ] Acessibilidade WCAG 2.1 AA (se aplicável a UI)

### Documentação
- [ ] Comentários no código para lógica complexa
- [ ] API documentation atualizada (OpenAPI/Swagger)
- [ ] README atualizado se há mudanças em setup
- [ ] Changelog entry criado

### DevOps
- [ ] Deploy em staging via CI/CD pipeline
- [ ] Monitoring e alertas configurados
- [ ] Performance metrics dentro de SLA
- [ ] Rollback plan documentado

### Compliance
- [ ] LGPD/GDPR compliance verificado (se aplicável)
- [ ] Logs de auditoria implementados (se aplicável)
- [ ] Database migrations testadas (up e down)
```

#### 2.1.3 Cerimônias do Scrum

**Sprint Planning (4-8 horas para sprint de 2-4 semanas)**

Reunião onde time planeja trabalho da sprint. Dividida em duas partes:

*Parte 1 - O Quê (What):* Product Owner apresenta itens de maior prioridade do backlog. Time discute e entende acceptance criteria. Time decide quantos itens consegue completar baseado em velocity histórica.

*Parte 2 - Como (How):* Development Team quebra user stories em tarefas técnicas granulares (4-8 horas cada). Time identifica dependências, riscos e impedimentos potenciais.

Exemplo de discussão em Sprint Planning:

```
PO: "Próxima prioridade é STORY-123, login com Google OAuth. Precisamos reduzir
     fricção no signup porque estamos perdendo 60% dos usuários no registration form."

Dev (Ana): "Entendi o problema de negócio. Para implementar, precisamos:
            1. Setup no Google Cloud Console
            2. Implementar OAuth 2.0 flow
            3. Integrar com nosso user provisioning
            Estimativa: 8 pontos. Alguma dependência de backend?"

Dev (Carlos): "Sim, precisamos armazenar Google user ID. Requer migration no DB.
               Adiciono task técnica: 'Create migration to add google_id column'."

PO: "Faz sentido. Qual critério de aceitação?"

Dev (Marina): "Sugiro:
               - Usuário clica 'Login with Google' e é redirecionado para consent screen
               - Após autorização, usuário é criado/logado automaticamente
               - Email do Google é usado como email primário
               - Erro handling para OAuth failures
               Concordam?"

Time: "Concordamos. Committing STORY-123 para sprint."
```

**Daily Scrum / Standup (15 minutos)**

Reunião diária para sincronização rápida. Cada membro responde:

1. O que fiz ontem que ajudou a atingir Sprint Goal?
2. O que farei hoje para ajudar a atingir Sprint Goal?
3. Vejo algum impedimento bloqueando meu progresso ou do time?

Boas práticas:

- Foco em progresso toward Sprint Goal, não atividades individuais
- Discussões técnicas detalhadas levadas para reuniões separadas após standup
- Impedimentos sinalizados para Scrum Master resolver
- Uso de board visual (Jira, Trello) para transparência

Exemplo de Daily Scrum eficaz:

```
Carlos: "Ontem completei OAuth callback endpoint. Hoje vou integrar com user
         provisioning. Sem impedimentos."

Ana: "Ontem criei migration para google_id. Hoje integro OAuth com provisioning
      (pairing com Carlos). Impedimento: preciso de acesso ao Google Cloud Console."

Scrum Master: "Ana, te adiciono no GCP hoje de manhã."

Marina: "Ontem criei botão de login. Hoje escrevo testes de integração. Sem
         impedimentos."
```

**Sprint Review (2-4 horas para sprint de 2-4 semanas)**

Reunião ao final da sprint para inspecionar incremento e adaptar Product Backlog. Development Team demonstra trabalho completado. Stakeholders dão feedback. Product Owner declara o que está "Done".

Estrutura típica:

1. PO recapitula Sprint Goal e itens commitados
2. Devs demonstram features funcionando (live demo, não slides)
3. Stakeholders fazem perguntas e dão feedback qualitativo
4. Discussão sobre próximos passos e ajustes de roadmap baseado em aprendizados
5. Revisão de métricas (velocity, burndown, qualidade)

**Sprint Retrospective (1.5-3 horas para sprint de 2-4 semanas)**

Reunião após Sprint Review onde time reflete sobre processo e identifica melhorias. Estrutura:

1. Set the stage: criar ambiente seguro para feedback honesto
2. Gather data: coletar fatos sobre o que aconteceu na sprint
3. Generate insights: discutir por que coisas aconteceram
4. Decide what to do: identificar 1-3 melhorias concretas para próxima sprint
5. Close: agradecer participação e reforçar compromissos

Exemplo de ação de Retrospective:

```markdown
## Retrospective Sprint 23 - Action Items

### Problema Identificado
"Code reviews estão demorando 2-3 dias, bloqueando merge de PRs e criando
work-in-progress excessivo."

### Root Cause
- Time não tem ritual dedicado para code review
- Desenvolvedores priorizam novo código sobre reviews
- Falta de notificações visíveis para PRs pendentes

### Action Items (Owner: Time, Due: Sprint 24)
1. Implementar "Review Hour" daily 2-3pm onde todos focam em code reviews
2. Configurar Slack bot para notificar PRs pendentes > 24h
3. Adicionar métrica "Time to Review" no dashboard da equipe
4. Meta: reduzir median time to review de 48h para 12h

### Success Metrics
- Track median time to review semanalmente
- Avaliar impacto em Sprint 24 Retrospective
```

### 2.2 Kanban - Fluxo Contínuo de Trabalho

Kanban emergiu do Toyota Production System como método de gestão visual de fluxo de trabalho, focando em limitar work-in-progress e otimizar throughput.

#### 2.2.1 Princípios do Kanban

**1. Visualizar Fluxo de Trabalho**

Board Kanban representa fluxo através de colunas que mapeiam estados do trabalho. Board típico para equipe de desenvolvimento:

```
| Backlog | To Do | In Development | Code Review | QA | Done |
|---------|-------|----------------|-------------|-----|------|
| [50]    | [8]   | [3]            | [2]         | [1] | [∞]  |
         WIP Limit:      3              2          1
```

Cada card representa work item (user story, bug fix, tech debt). Time move cards da esquerda para direita conforme trabalho progride.

**2. Limitar Work in Progress (WIP)**

WIP limits previnem multitasking excessivo e forçam foco em completar trabalho iniciado antes de puxar novo trabalho. Benefícios:

- Redução de context switching (custo cognitivo de trocar entre tarefas)
- Identificação de bottlenecks (coluna com WIP constantemente no limite sinaliza gargalo)
- Faster time to market (completar 3 features em 1 semana > completar 10 features em 1 mês)

Exemplo de WIP limit em ação:

```
Situação: Coluna "Code Review" tem WIP limit de 2 e está cheia.
Ação: Desenvolvedores param de pushar novos PRs e focam em revisar PRs existentes.
Resultado: Code reviews não acumulam; fluxo continua balanceado.
```

**3. Gerenciar Fluxo**

Medir e otimizar tempo que trabalho leva para fluir através do sistema (lead time e cycle time).

- **Lead Time**: tempo desde criação do work item até conclusão (perspectiva do cliente)
- **Cycle Time**: tempo desde início do trabalho até conclusão (perspectiva do time)

Métricas de fluxo:

```python
# Exemplo: calcular cycle time médio a partir de dados Jira

import pandas as pd
from datetime import datetime

# Dados de tickets completados
tickets = pd.DataFrame({
    'ticket_id': ['STORY-101', 'STORY-102', 'STORY-103'],
    'started_at': ['2025-01-10', '2025-01-12', '2025-01-15'],
    'completed_at': ['2025-01-15', '2025-01-18', '2025-01-20']
})

# Converter para datetime
tickets['started_at'] = pd.to_datetime(tickets['started_at'])
tickets['completed_at'] = pd.to_datetime(tickets['completed_at'])

# Calcular cycle time em dias
tickets['cycle_time_days'] = (tickets['completed_at'] - tickets['started_at']).dt.days

# Métricas
average_cycle_time = tickets['cycle_time_days'].mean()
p95_cycle_time = tickets['cycle_time_days'].quantile(0.95)

print(f"Average Cycle Time: {average_cycle_time:.1f} days")
print(f"P95 Cycle Time: {p95_cycle_time:.1f} days")

# Output:
# Average Cycle Time: 5.0 days
# P95 Cycle Time: 5.0 days
```

**4. Tornar Políticas Explícitas**

Documentar e tornar visível critérios para mover cards entre colunas (Definition of Ready, Definition of Done para cada coluna).

Exemplo de políticas Kanban:

```markdown
## Kanban Board Policies

### Backlog → To Do
- User story tem acceptance criteria claros
- Estimativa de esforço realizada
- Dependências identificadas
- Aprovado por Product Owner

### To Do → In Development
- WIP limit não excedido
- Desenvolvedor disponível
- Todas dependências resolvidas

### In Development → Code Review
- Código completo e funcionando em local environment
- Testes unitários escritos (coverage >= 80%)
- Auto-revisão completa (self code review)

### Code Review → QA
- Pelo menos 1 aprovação de code review
- CI pipeline passando (build + tests)
- Deploy em staging environment

### QA → Done
- Todos acceptance criteria validados
- Performance dentro de SLA
- Aprovado por Product Owner
- Deployed to production
```

#### 2.2.2 Kanban vs. Scrum

| Dimensão | Scrum | Kanban |
|----------|-------|--------|
| **Cadência** | Iterações time-boxed (sprints) | Fluxo contínuo |
| **Papéis** | Product Owner, Scrum Master, Dev Team | Nenhum papel prescrito |
| **Cerimônias** | Planning, Daily, Review, Retro | Nenhuma cerimônia prescrita (mas geralmente daily standup) |
| **Mudanças** | Não durante sprint | A qualquer momento |
| **Priorização** | No início de cada sprint | Contínua (pull do topo do backlog) |
| **Métricas** | Velocity (story points/sprint) | Lead time, cycle time, throughput |
| **WIP Limits** | Implícito (capacidade da sprint) | Explícito (por coluna) |
| **Melhor para** | Trabalho previsível, time novo em ágil | Trabalho variável, interrupções frequentes, operações |

**Quando usar Scrum:**

- Equipe nova em metodologias ágeis (estrutura ajuda adoção)
- Stakeholders preferem cadência previsível para releases
- Produto em fase de crescimento com roadmap claro
- Time co-localizado que valoriza cerimônias presenciais

**Quando usar Kanban:**

- Equipe madura em ágil buscando flexibilidade
- Trabalho com alta variabilidade (bugs urgentes, suporte, infra)
- Times distribuídos em múltiplos fusos horários
- Foco em otimização de fluxo e redução de lead time

**Scrumban (híbrido):**

Muitas equipes combinam elementos: sprints de Scrum com WIP limits de Kanban, planning estruturado com fluxo contínuo, etc.

## 3. Ciclo de Vida de Desenvolvimento de Produto

### 3.1 Fases do Ciclo de Vida

O desenvolvimento de produtos digitais envolve seis fases iterativas, frequentemente sobrepostas:

#### 3.1.1 Pesquisa e Análise de Mercado

Compreender problema, usuários e contexto de mercado antes de construir solução.

**Atividades:**

- Pesquisa com usuários (entrevistas, surveys, observação)
- Análise de concorrência e benchmarking
- Validação de problem-solution fit
- Definição de hipóteses a testar

**Envolvimento do desenvolvedor:**

- Participar de entrevistas com usuários para compreender contexto técnico
- Avaliar soluções concorrentes de perspectiva arquitetural
- Validar viabilidade técnica de hipóteses
- Contribuir para estimativas de esforço em discovery

Exemplo de hipótese técnica em discovery:

```markdown
## Hipótese: Real-time Collaboration

### Problema
Usuários relatam dificuldade em colaborar em documentos simultaneamente
(baseado em 15 entrevistas com clientes enterprise)

### Hipótese de Solução
Implementar edição colaborativa real-time estilo Google Docs

### Validação Técnica (Spike)
- Arquitetura: WebSocket vs. WebRTC vs. Operational Transform
- Conflitos: Last-write-wins vs. CRDTs (Yjs, Automerge)
- Escala: Quantos usuários simultâneos por documento?
- Offline: Como sincronizar edições offline?

### Esforço Estimado
- MVP (10 usuários/doc, conflitos simples): 3-4 semanas
- Production-ready (100 usuários/doc, CRDTs): 8-12 semanas

### Decisão
Fazer spike de 1 semana com Yjs + WebSocket para validar viabilidade
antes de commitar full implementation
```

#### 3.1.2 Concepção do Produto

Traduzir aprendizados de research em especificação de produto.

**Artefatos:**

- Product vision statement
- User personas
- User journey maps
- Feature list priorizada
- Architecture Decision Records (ADRs)

**Envolvimento do desenvolvedor:**

Arquitetura inicial, decisões de stack tecnológico, identificação de riscos técnicos.

Exemplo de ADR (Architecture Decision Record):

```markdown
# ADR-003: Escolha de Framework para Real-time Collaboration

## Status
Accepted (2025-01-15)

## Context
Precisamos implementar edição colaborativa real-time para documentos.
Requisitos:
- Suporte para 100+ usuários simultâneos por documento
- Resolução automática de conflitos
- Performance em redes instáveis (mobile)
- Sync offline-first

## Decision
Usar Yjs como CRDT framework + WebSocket para transport layer.

## Consequences

### Positive
- Yjs resolve conflitos automaticamente via CRDTs
- Suporte nativo para offline-first
- Biblioteca madura (usado por Notion, Linear)
- Performance excelente (benchmarks: 100k ops/s)

### Negative
- Curva de aprendizado para equipe
- Payload maior que Operational Transform
- Vendor lock-in (migração futura custosa)

### Risks Mitigated
- Spike técnico validou viabilidade (1 semana)
- POC com 50 usuários simultâneos bem-sucedido

## Alternatives Considered
1. **Operational Transform (OT)**: Mais complexo de implementar, bugs sutis
2. **Last-write-wins**: Perde edições, experiência ruim
3. **Build from scratch**: 6+ meses de desenvolvimento, alto risco

## References
- Yjs documentation: https://docs.yjs.dev
- CRDT benchmark: https://github.com/automerge/automerge-perf
```

#### 3.1.3 Desenvolvimento

Construção iterativa do produto através de sprints ou fluxo contínuo.

**Práticas de desenvolvimento:**

- TDD (Test-Driven Development) para qualidade
- Continuous Integration para feedback rápido
- Feature flags para deploy seguro
- Code review para conhecimento compartilhado

Exemplo de feature flag para rollout gradual:

```typescript
// Implementação de feature flag para real-time collaboration

import { FeatureFlag } from '@/lib/feature-flags';

interface Document {
  id: string;
  content: string;
  enableRealtimeCollaboration?: boolean;
}

class DocumentEditor {
  private featureFlags: FeatureFlag;

  constructor(featureFlags: FeatureFlag) {
    this.featureFlags = featureFlags;
  }

  async loadDocument(documentId: string, userId: string): Promise<Document> {
    const document = await this.fetchDocument(documentId);

    // Gradual rollout: 10% de usuários
    const isRealtimeEnabled = await this.featureFlags.isEnabled(
      'realtime-collaboration',
      userId,
      { rolloutPercentage: 10 }
    );

    if (isRealtimeEnabled) {
      // Nova implementação com Yjs
      return this.loadWithYjs(document);
    } else {
      // Implementação legacy
      return this.loadLegacy(document);
    }
  }

  private async loadWithYjs(document: Document): Promise<Document> {
    // Inicializar Yjs document, WebSocket connection, awareness, etc.
    // ...
  }

  private async loadLegacy(document: Document): Promise<Document> {
    // Implementação antiga sem real-time
    // ...
  }
}
```

#### 3.1.4 Testes e Validação

Validação de qualidade técnica e valor de negócio antes de release.

**Tipos de testes:**

- **Unit tests**: Funções individuais (coverage >= 80%)
- **Integration tests**: Interação entre componentes
- **E2E tests**: Fluxos críticos de usuário
- **Performance tests**: Load testing, stress testing
- **Security tests**: SAST, DAST, dependency scanning

Exemplo de teste de integração para real-time collaboration:

```typescript
// Integration test para sincronização real-time

import { test, expect } from '@playwright/test';
import * as Y from 'yjs';
import { WebsocketProvider } from 'y-websocket';

test.describe('Real-time Collaboration', () => {
  test('múltiplos usuários editam documento simultaneamente', async ({
    browser,
  }) => {
    // Setup: criar 2 browser contexts (2 usuários)
    const context1 = await browser.newContext();
    const context2 = await browser.newContext();
    const page1 = await context1.newPage();
    const page2 = await context2.newPage();

    // User 1 cria documento
    await page1.goto('/documents/new');
    const documentId = await page1.locator('[data-testid="document-id"]').textContent();

    // User 2 abre mesmo documento
    await page2.goto(`/documents/${documentId}`);

    // User 1 escreve texto
    await page1.locator('[data-testid="editor"]').type('Hello from User 1');

    // Aguardar sincronização via WebSocket
    await page2.waitForTimeout(500);

    // Validar: User 2 vê texto de User 1
    const content2 = await page2.locator('[data-testid="editor"]').textContent();
    expect(content2).toContain('Hello from User 1');

    // User 2 edita simultaneamente
    await page2.locator('[data-testid="editor"]').type(' - and User 2');
    await page1.waitForTimeout(500);

    // Validar: User 1 vê edição de User 2
    const content1 = await page1.locator('[data-testid="editor"]').textContent();
    expect(content1).toContain('Hello from User 1 - and User 2');

    // Validar: sem conflitos (CRDT merge)
    expect(content1).toBe(content2);
  });

  test('sincronização offline-first funciona', async ({ page }) => {
    await page.goto('/documents/123');

    // Simular offline
    await page.context().setOffline(true);

    // Editar documento offline
    await page.locator('[data-testid="editor"]').type('Offline edit');

    // Validar: edição salva localmente
    const offlineContent = await page.evaluate(() => {
      return localStorage.getItem('doc-123');
    });
    expect(offlineContent).toContain('Offline edit');

    // Voltar online
    await page.context().setOffline(false);

    // Aguardar sync
    await page.waitForSelector('[data-testid="sync-status"][data-synced="true"]');

    // Validar: edição sincronizada para servidor
    const response = await page.request.get('/api/documents/123');
    const serverContent = await response.json();
    expect(serverContent.content).toContain('Offline edit');
  });
});
```

#### 3.1.5 Lançamento do Produto

Deploy em produção e comunicação para usuários.

**Estratégias de lançamento:**

- **Big Bang**: Release completo para 100% dos usuários (risco alto)
- **Gradual Rollout**: Release incremental (10% → 50% → 100%) com feature flags
- **Blue-Green Deployment**: Manter versão antiga em paralelo para rollback rápido
- **Canary Release**: Release para subset de infraestrutura (1 servidor) antes de escalar

Exemplo de gradual rollout com observabilidade:

```typescript
// Gradual rollout com monitoring e auto-rollback

import { FeatureFlag, Analytics, Monitoring } from '@/lib';

class RolloutManager {
  private featureFlags: FeatureFlag;
  private analytics: Analytics;
  private monitoring: Monitoring;

  async executeRollout(featureName: string) {
    const stages = [
      { percentage: 10, duration: '24h', errorThreshold: 0.01 },
      { percentage: 50, duration: '48h', errorThreshold: 0.005 },
      { percentage: 100, duration: 'permanent', errorThreshold: 0.001 },
    ];

    for (const stage of stages) {
      console.log(`Rollout ${featureName} para ${stage.percentage}%`);

      // Habilitar feature para X% de usuários
      await this.featureFlags.setRolloutPercentage(featureName, stage.percentage);

      // Monitorar métricas durante duração do stage
      const metrics = await this.monitorStage(featureName, stage.duration);

      // Verificar health metrics
      if (metrics.errorRate > stage.errorThreshold) {
        console.error(`Error rate ${metrics.errorRate} excede threshold ${stage.errorThreshold}`);
        await this.rollback(featureName);
        throw new Error(`Rollout aborted: high error rate`);
      }

      if (metrics.p95Latency > 1000) {
        console.error(`p95 latency ${metrics.p95Latency}ms excede SLA`);
        await this.rollback(featureName);
        throw new Error(`Rollout aborted: high latency`);
      }

      console.log(`Stage ${stage.percentage}% completed successfully`);
    }
  }

  private async monitorStage(featureName: string, duration: string) {
    // Coletar métricas durante período
    const metrics = await this.monitoring.query({
      feature: featureName,
      duration: duration,
      metrics: ['error_rate', 'p95_latency', 'conversion_rate'],
    });

    return metrics;
  }

  private async rollback(featureName: string) {
    console.log(`Rolling back ${featureName} to 0%`);
    await this.featureFlags.setRolloutPercentage(featureName, 0);
    await this.analytics.trackEvent('feature_rollback', { feature: featureName });
  }
}
```

#### 3.1.6 Acompanhamento e Iteração

Monitorar métricas, coletar feedback e iterar baseado em dados.

**Métricas de produto a monitorar:**

- **Adoção**: % de usuários que usaram nova feature (pelo menos 1x)
- **Engajamento**: Frequência de uso (DAU/MAU ratio)
- **Retenção**: % de usuários que continuam usando após 7/30/90 dias
- **Satisfação**: NPS, CSAT, feedback qualitativo
- **Performance**: Latência, error rate, disponibilidade

Exemplo de dashboard de métricas pós-lançamento:

```sql
-- Query para calcular adoption rate de real-time collaboration

WITH feature_users AS (
  SELECT DISTINCT user_id
  FROM events
  WHERE event_name = 'realtime_collaboration_used'
    AND timestamp >= NOW() - INTERVAL '30 days'
),
total_users AS (
  SELECT COUNT(DISTINCT user_id) as count
  FROM users
  WHERE created_at < NOW() - INTERVAL '30 days'  -- Usuários existentes antes do lançamento
)
SELECT
  (SELECT COUNT(*) FROM feature_users) AS users_adopted,
  (SELECT count FROM total_users) AS total_users,
  ROUND(
    100.0 * (SELECT COUNT(*) FROM feature_users) / (SELECT count FROM total_users),
    2
  ) AS adoption_rate_percent
;

-- Output:
-- users_adopted | total_users | adoption_rate_percent
-- 1,234         | 10,000      | 12.34
```

## 4. Roadmap de Produto e Priorização

### 4.1 Tipos de Roadmap

Roadmaps comunicam visão de produto e plano de execução para diferentes audiências.

#### 4.1.1 Roadmap Estratégico (Visão de Longo Prazo)

Timeline de 6-12 meses focado em temas e objetivos de negócio, não features específicas.

Exemplo de roadmap estratégico:

```markdown
## Product Roadmap 2025 - Plataforma de Colaboração

### Q1 2025: Foundation
**Tema:** Estabelecer fundação técnica para colaboração real-time
- Migrar para arquitetura event-driven (Kafka)
- Implementar CRDT engine (Yjs) para sync
- OKR: Reduzir latência de sincronização p95 de 2s para 200ms

### Q2 2025: Collaboration
**Tema:** Habilitar colaboração real-time em documentos
- Edição simultânea multi-usuário
- Cursors e presence awareness
- Comentários inline real-time
- OKR: 30% dos usuários ativos adotam colaboração real-time

### Q3 2025: Intelligence
**Tema:** Adicionar inteligência com AI para produtividade
- AI-powered suggestions durante escrita
- Auto-formatting e correções
- Smart templates baseados em contexto
- OKR: Usuários com AI feature têm 2x mais engagement

### Q4 2025: Platform
**Tema:** Abrir plataforma para desenvolvedores externos
- Public API para integrações
- SDK para JavaScript/Python
- Marketplace de extensões
- OKR: 100 desenvolvedores publicam extensões
```

#### 4.1.2 Roadmap Tático (Visão de Médio Prazo)

Timeline de 3-6 meses focado em features e iniciativas específicas.

Exemplo de roadmap tático (formato Now-Next-Later):

```markdown
## Roadmap Tático - Q1 2025

### Now (Em desenvolvimento - Jan 2025)
- [EPIC-101] Real-time collaboration MVP
  - Status: In Progress (60% complete)
  - Team: 3 backend + 2 frontend devs
  - ETA: Jan 31
  - Value: Desbloqueio para clientes enterprise ($500k ARR)

- [EPIC-102] Performance optimization
  - Status: In Progress (30% complete)
  - Team: 1 backend dev
  - ETA: Feb 15
  - Value: Reduzir churn causado por lentidão (salvando $200k ARR)

### Next (Próximos 3 meses - Feb-Mar 2025)
- [EPIC-103] Offline-first sync
  - Dependencies: EPIC-101 (Real-time collaboration)
  - Team: 2 backend + 1 frontend dev
  - Effort: 6 weeks
  - Value: Suporte para mobile users (20% da base)

- [EPIC-104] Advanced permissions
  - Dependencies: Nenhuma
  - Team: 1 backend + 1 frontend dev
  - Effort: 4 weeks
  - Value: Requisito para enterprise deals ($1M pipeline)

### Later (Backlog - Apr+ 2025)
- [EPIC-105] Video/audio calls in-app
- [EPIC-106] Version history e rollback
- [EPIC-107] AI writing assistant
```

#### 4.1.3 Roadmap de Lançamento (Release Plan)

Timeline de 4-8 semanas focado em sprints e entregas concretas.

Exemplo de release plan:

```markdown
## Release Plan - Real-time Collaboration v1.0

### Sprint 1 (Jan 15-26)
**Features:**
- [STORY-101] WebSocket connection infrastructure
- [STORY-102] Yjs document initialization
- [STORY-103] Basic text sync (sem formatting)

**Technical Debt:**
- [TECH-50] Refactor document model para suportar CRDTs

**Deliverable:** Backend pronto para sync textual simples

### Sprint 2 (Jan 29 - Feb 9)
**Features:**
- [STORY-104] Rich text formatting sync (bold, italic, links)
- [STORY-105] Cursor positions e user awareness
- [STORY-106] Conflict resolution UI

**Deliverable:** Prototype funcional para demo interna

### Sprint 3 (Feb 12-23)
**Features:**
- [STORY-107] Offline sync e conflict resolution
- [STORY-108] Performance optimization (100+ users)
- [STORY-109] Error handling e reconnection logic

**Testing:**
- [QA-50] Load testing com 200 usuários simultâneos
- [QA-51] Chaos engineering (network failures)

**Deliverable:** Beta release para early adopters (50 usuários)

### Sprint 4 (Feb 26 - Mar 8)
**Features:**
- [STORY-110] Onboarding UI e tutorials
- [STORY-111] Analytics e monitoring
- [STORY-112] Bug fixes do beta feedback

**Deliverable:** Production release v1.0 (gradual rollout 10%→50%→100%)
```

### 4.2 Frameworks de Priorização

Decidir o que construir primeiro é talvez a decisão mais crítica em gestão de produtos.

#### 4.2.1 RICE Framework

RICE quantifica prioridade baseado em 4 fatores:

- **Reach (Alcance)**: Quantos usuários serão impactados por período?
- **Impact (Impacto)**: Qual magnitude do impacto? (escala: 3=massive, 2=high, 1=medium, 0.5=low, 0.25=minimal)
- **Confidence (Confiança)**: Quão confiante estamos nas estimativas? (escala: 100%=high, 80%=medium, 50%=low)
- **Effort (Esforço)**: Quantos person-months de trabalho?

**Fórmula:**

```
RICE Score = (Reach × Impact × Confidence) / Effort
```

Exemplo de cálculo RICE:

```markdown
## Priorização de Features - Q1 2025

### Feature A: Real-time Collaboration
- **Reach:** 5,000 usuários/quarter (50% da base ativa)
- **Impact:** 3 (massive - diferenciador competitivo)
- **Confidence:** 80% (já validado com protótipo)
- **Effort:** 3 person-months (2 devs × 6 semanas)
- **RICE Score:** (5000 × 3 × 0.8) / 3 = **4,000**

### Feature B: Dark Mode
- **Reach:** 8,000 usuários/quarter (80% da base)
- **Impact:** 1 (medium - melhoria de UX)
- **Confidence:** 100% (baixa complexidade)
- **Effort:** 0.5 person-months (1 dev × 2 semanas)
- **RICE Score:** (8000 × 1 × 1.0) / 0.5 = **16,000**

### Feature C: Advanced Search
- **Reach:** 2,000 usuários/quarter (20% power users)
- **Impact:** 2 (high - 3x productivity gain)
- **Confidence:** 50% (incerteza técnica - Elasticsearch vs custom)
- **Effort:** 2 person-months (1 backend dev × 2 meses)
- **RICE Score:** (2000 × 2 × 0.5) / 2 = **1,000**

### Decisão de Priorização
1. **Dark Mode** (RICE: 16,000) - Quick win, alto ROI
2. **Real-time Collaboration** (RICE: 4,000) - Estratégico, diferenciador
3. **Advanced Search** (RICE: 1,000) - Validar demanda antes de investir
```

**Implementação de RICE em código:**

```typescript
// Calculadora RICE para priorização automatizada

interface Feature {
  id: string;
  name: string;
  reach: number;           // Usuários impactados por quarter
  impact: 0.25 | 0.5 | 1 | 2 | 3;  // Minimal, Low, Medium, High, Massive
  confidence: number;      // 0-1 (50% = 0.5, 100% = 1.0)
  effort: number;          // Person-months
}

function calculateRICE(feature: Feature): number {
  return (feature.reach * feature.impact * feature.confidence) / feature.effort;
}

function prioritizeFeatures(features: Feature[]): Feature[] {
  return features
    .map(f => ({
      ...f,
      riceScore: calculateRICE(f)
    }))
    .sort((a, b) => b.riceScore - a.riceScore);
}

// Exemplo de uso
const features: Feature[] = [
  {
    id: 'EPIC-101',
    name: 'Real-time Collaboration',
    reach: 5000,
    impact: 3,
    confidence: 0.8,
    effort: 3
  },
  {
    id: 'EPIC-102',
    name: 'Dark Mode',
    reach: 8000,
    impact: 1,
    confidence: 1.0,
    effort: 0.5
  },
  {
    id: 'EPIC-103',
    name: 'Advanced Search',
    reach: 2000,
    impact: 2,
    confidence: 0.5,
    effort: 2
  }
];

const prioritized = prioritizeFeatures(features);
console.table(prioritized.map(f => ({
  Name: f.name,
  'RICE Score': Math.round(f.riceScore),
  Rank: prioritized.indexOf(f) + 1
})));

// Output:
// ┌─────────┬────────────────────────────┬─────────────┬──────┐
// │ (index) │            Name            │ RICE Score  │ Rank │
// ├─────────┼────────────────────────────┼─────────────┼──────┤
// │    0    │       'Dark Mode'          │    16000    │  1   │
// │    1    │ 'Real-time Collaboration'  │     4000    │  2   │
// │    2    │    'Advanced Search'       │     1000    │  3   │
// └─────────┴────────────────────────────┴─────────────┴──────┘
```

#### 4.2.2 MoSCoW Method

MoSCoW categoriza features em 4 buckets:

- **Must Have**: Crítico para release (deal-breaker)
- **Should Have**: Importante mas não crítico (pode ser adiado)
- **Could Have**: Desejável se houver tempo (nice-to-have)
- **Won't Have**: Explicitamente fora de escopo

Exemplo de MoSCoW para release:

```markdown
## MoSCoW Prioritization - Real-time Collaboration v1.0

### Must Have (Blockers para release)
- [x] Sincronização de texto entre usuários
- [x] Cursors e presence awareness (quem está online)
- [x] Auto-save e conflict resolution
- [ ] Load testing para 100+ usuários simultâneos
- [ ] Error handling e reconnection
Regra: **100% Must Have completo antes de release**

### Should Have (Importante, mas pode ser v1.1)
- [ ] Formatting sync (bold, italic, underline)
- [ ] Comentários inline real-time
- [ ] Version history básico
- [ ] Notificações de edição

### Could Have (Nice-to-have se houver tempo)
- [ ] @mentions com autocomplete
- [ ] Emoji reactions em comentários
- [ ] Keyboard shortcuts customizáveis
- [ ] Modo presentation

### Won't Have (Explicitamente fora de escopo v1.0)
- Video/audio calls (planejado para v2.0)
- AI writing assistant (Q3 2025 roadmap)
- Mobile apps (web-only em v1.0)
- Integração com Slack/Teams
```

#### 4.2.3 Kano Model

Kano Model categoriza features baseado em impacto em satisfação do cliente:

- **Basic Needs (Must-be)**: Esperados; ausência causa insatisfação, presença não aumenta satisfação
- **Performance Needs (One-dimensional)**: Mais é melhor; relação linear entre presença e satisfação
- **Excitement Needs (Attractive)**: Inesperados; ausência não causa insatisfação, presença aumenta muito satisfação
- **Indifferent**: Cliente não se importa
- **Reverse**: Presença causa insatisfação

Exemplo de categorização Kano:

```markdown
## Kano Analysis - Collaborative Document Editor

### Basic Needs (Must-be Quality)
- Salvar documento sem perder dados
- Load time < 3 segundos
- Funcionar nos navegadores principais (Chrome, Firefox, Safari)
- Segurança (auth, permissions)
**Ação:** Implementar como requisito mínimo

### Performance Needs (One-dimensional Quality)
- Velocidade de sincronização (quanto mais rápido, melhor)
- Suporte para documentos grandes (mais páginas, melhor)
- Uptime (99% → 99.9% → 99.99%)
**Ação:** Otimizar continuamente

### Excitement Needs (Attractive Quality)
- AI auto-complete enquanto escreve
- Smart templates baseados em contexto
- Integração com Figma para design embeds
- Comandos por voz
**Ação:** Diferenciar competitivamente; investir após basics

### Indifferent
- 50 vs. 100 níveis de undo/redo (usuários não notam)
- Escolha entre 500 fontes (opções demais confunde)
**Ação:** Não investir esforço

### Reverse
- Animações excessivas (causa distração)
- Gamification em ferramenta profissional
**Ação:** Evitar completamente
```

## 5. Gestão de Backlog e Sprint Planning

### 5.1 Anatomia de um Product Backlog

Backlog bem gerenciado é lista viva, priorizada e refinada continuamente.

#### 5.1.1 Estrutura Hierárquica

```
Tema
  └─ Épico
      └─ User Story
          ├─ Task (implementação)
          ├─ Task (testes)
          └─ Task (documentação)
```

Exemplo de hierarquia:

```markdown
## Backlog Hierarquia

### Tema: Collaboration
Objetivo: Transformar produto single-player em multiplayer

#### Épico: Real-time Co-editing
Valor: Permitir múltiplos usuários editarem documento simultaneamente
Estimativa: 40 story points (~6-8 semanas)

##### User Story: Sync de Texto
**Como** usuário editando documento
**Quero** ver edições de outros usuários em tempo real
**Para** colaborar sem conflitos e retrabalho

**Acceptance Criteria:**
- [ ] Edições aparecem em < 500ms para outros usuários
- [ ] Cursores de outros usuários são visíveis
- [ ] Conflitos são resolvidos automaticamente (CRDT)
- [ ] Funciona com 100+ usuários simultâneos (load test)

**Tasks:**
- [TASK-301] Setup WebSocket server com y-websocket (8h)
- [TASK-302] Integrar Yjs no editor frontend (12h)
- [TASK-303] Implementar awareness protocol (cursors) (6h)
- [TASK-304] Criar testes de sincronização (8h)
- [TASK-305] Load testing com 200 usuários (4h)
- [TASK-306] Monitoring e alertas (4h)

**Estimativa:** 13 story points
**Prioridade:** Alta (bloqueador para clientes enterprise)
**Dependencies:** Nenhuma
```

#### 5.1.2 Critérios de Aceitação (Acceptance Criteria)

Acceptance Criteria definem quando user story está "Done" de perspectiva funcional.

**Formato Given-When-Then (Gherkin):**

```gherkin
# STORY-123: Login com Google OAuth

Scenario: Usuário se autentica com Google pela primeira vez
  Given eu sou um novo usuário sem conta
  When eu clico no botão "Login with Google"
  And autorizo acesso no Google consent screen
  Then uma nova conta é criada automaticamente
  And eu sou redirecionado para dashboard
  And meu email do Google é usado como email primário

Scenario: Usuário existente faz login com Google
  Given eu tenho conta existente com email user@example.com
  And minha conta já está conectada ao Google
  When eu clico no botão "Login with Google"
  Then eu sou autenticado automaticamente
  And não é criada conta duplicada

Scenario: Erro no OAuth flow
  Given eu inicio login com Google
  When o Google OAuth retorna erro (usuário cancela ou falha técnica)
  Then eu vejo mensagem clara explicando o erro
  And sou redirecionado para tela de login
  And erro é logado para debugging
```

**Formato Checklist (mais comum em desenvolvimento):**

```markdown
## Acceptance Criteria - STORY-123: Google OAuth Login

### Funcional
- [ ] Botão "Login with Google" visível na tela de login
- [ ] Ao clicar, usuário é redirecionado para Google consent screen
- [ ] Após autorização, usuário é criado/logado automaticamente
- [ ] Email do Google é usado como email primário
- [ ] Se conta já existe com mesmo email, fazer merge (não duplicar)

### Error Handling
- [ ] Se usuário cancela OAuth, mostrar mensagem e voltar para login
- [ ] Se Google API falha, mostrar erro genérico e logar detalhes
- [ ] Rate limiting configurado (max 100 logins/min por IP)

### Segurança
- [ ] OAuth 2.0 state parameter para prevenir CSRF
- [ ] Tokens armazenados com encriptação
- [ ] Expiração de sessão configurada (7 dias)

### Performance
- [ ] Login completo em < 3 segundos (p95)
- [ ] Suporta 100 logins simultâneos sem degradação

### UX
- [ ] Loading state visível durante OAuth redirect
- [ ] Mensagem de boas-vindas para novos usuários
- [ ] Notificação se login é primeiro (onboarding)
```

#### 5.1.3 Estimativa de Esforço

Estimativas ajudam a planejar capacidade e prever entregas.

**Story Points (relativo) vs. Hours (absoluto):**

- **Story Points:** Medida relativa de complexidade (Fibonacci: 1, 2, 3, 5, 8, 13, 21)
  - Vantagens: Independente de quem implementa, captura incerteza
  - Desvantagens: Abstrato, curva de aprendizado

- **Hours:** Estimativa absoluta de tempo
  - Vantagens: Concreto, fácil de entender
  - Desvantagens: Varia por desenvolvedor, ignora incerteza

**Planning Poker (técnica de estimativa colaborativa):**

```
Facilitador lê user story e acceptance criteria.
Cada desenvolvedor escolhe card secretamente (1, 2, 3, 5, 8, 13, 21, ?).
Todos revelam simultaneamente.
Se há consenso (todos mesmo número), adotar estimativa.
Se há discrepância (ex: 3 e 13), desenvolvedores explicam raciocínio.
Repetir até convergir.

Exemplo:
STORY-123: Google OAuth Login
- Dev A: 5 pontos ("OAuth é biblioteca pronta, só configurar")
- Dev B: 13 pontos ("Mas precisamos testar error handling, CSRF, rate limiting...")
Discussão: Dev B levanta complexidade não óbvia.
Consenso: 8 pontos (meio termo, reflete incerteza)
```

**Velocity (métrica de capacidade do time):**

```
Velocity = Story Points completados por sprint

Exemplo:
Sprint 1: 18 pontos completados
Sprint 2: 22 pontos completados
Sprint 3: 20 pontos completados
Velocity média: (18 + 22 + 20) / 3 = 20 pontos/sprint

Uso para planejamento:
Backlog tem 60 pontos.
Com velocity de 20 pontos/sprint, estimativa = 3 sprints.
```

### 5.2 Sprint Planning

Sprint Planning é cerimônia onde time decide o que entregar na próxima sprint.

#### 5.2.1 Preparação (Backlog Refinement)

Antes de Planning, Product Owner refina backlog em sessões de grooming:

- Escrever/atualizar user stories
- Definir acceptance criteria
- Estimar story points
- Identificar dependências
- Ordenar por prioridade

**Critério de "Ready" (Definition of Ready):**

```markdown
## Definition of Ready - User Story Checklist

Uma user story está pronta para sprint planning quando:

### Clareza
- [ ] Título descritivo e específico
- [ ] Descrição no formato "Como... Quero... Para..."
- [ ] Acceptance criteria claros e testáveis
- [ ] Mockups/wireframes anexados (se aplicável a UI)

### Estimativa
- [ ] Story points estimados (planning poker)
- [ ] Complexidade acordada pelo time
- [ ] Esforço cabe em 1 sprint (se > 13 pontos, quebrar)

### Dependências
- [ ] Dependências técnicas identificadas
- [ ] Dependências externas (APIs, third-party) mapeadas
- [ ] Bloqueadores resolvidos ou mitigation plan

### Valor
- [ ] Valor de negócio articulado
- [ ] Alinhado com roadmap e OKRs
- [ ] Prioridade relativa definida

Se qualquer checkbox faltar, story volta para refinement.
```

#### 5.2.2 Estrutura de Sprint Planning

**Parte 1: O Quê (2-4 horas)**

Product Owner apresenta objetivo da sprint e itens de maior prioridade.

```markdown
## Sprint 24 Planning - Parte 1

### Sprint Goal
Lançar MVP de real-time collaboration para beta users (50 clientes)

### Prioridades (ordenadas por valor)
1. [STORY-123] Sincronização de texto real-time (13 pts)
2. [STORY-124] Cursors e awareness (5 pts)
3. [STORY-125] Auto-save e conflict resolution (8 pts)
4. [STORY-126] Error handling e reconnection (5 pts)
**Total: 31 pontos**

### Capacity da Sprint
- Duração: 2 semanas (10 dias úteis)
- Desenvolvedores: 4 (Ana, Carlos, Marina, Pedro)
- Velocity média: 20-24 pontos
- Feriados/férias: nenhum
- **Capacity estimada: 22 pontos**

### Decisão
Time commita 26 pontos (STORY-123, 124, 125):
- Levemente acima de velocity (stretch goal)
- STORY-126 fica como buffer (adicionar se sobrar tempo)
```

**Parte 2: Como (2-4 horas)**

Development Team quebra user stories em tasks e discute implementação.

```markdown
## Sprint 24 Planning - Parte 2

### STORY-123: Sincronização de Texto (13 pts)

#### Abordagem Técnica (Discussão)
**Carlos:** "Proposta: usar Yjs como CRDT library + y-websocket para transport."
**Ana:** "Precisamos WebSocket server? Podemos usar y-websocket-server do NPM?"
**Pedro:** "Sim, mas precisamos configurar Redis para persistence. Adiciono task."
**Marina:** "Frontend usa Monaco editor. Compatível com Yjs?"
**Carlos:** "Sim, há binding pronto: y-monaco. Task: integrar binding."

#### Tasks Identificadas
- [x] [TASK-401] Setup WebSocket server com y-websocket (Dev: Carlos, 8h)
  - Instalar y-websocket-server
  - Configurar porta e CORS
  - Deploy em staging

- [ ] [TASK-402] Configurar Redis para persistence (Dev: Pedro, 4h)
  - Setup Redis cluster
  - Integrar y-redis persistence provider
  - Testar failover

- [ ] [TASK-403] Integrar y-monaco no frontend (Dev: Marina, 12h)
  - Instalar y-monaco binding
  - Conectar WebSocket client
  - Sincronizar editor state

- [ ] [TASK-404] Implementar authentication no WebSocket (Dev: Ana, 6h)
  - Validar JWT em connection
  - Verificar permissions
  - Rate limiting

- [ ] [TASK-405] Testes de sincronização (Dev: Marina, 8h)
  - Unit tests para provider
  - Integration tests com Playwright
  - Load test com 100 conexões

- [ ] [TASK-406] Monitoring e alertas (Dev: Carlos, 4h)
  - Metrics: conexões ativas, latência, erros
  - Dashboards no Grafana
  - Alertas no PagerDuty

**Estimativa Total:** 42 horas (13 pontos ≈ 40-50 horas)
```

#### 5.2.3 Sprint Board (Kanban Board para Sprint)

Após Planning, tasks vão para sprint board:

```
┌─────────────────────────────────────────────────────────────────┐
│                        Sprint 24 Board                          │
├────────────┬────────────┬────────────┬────────────┬─────────────┤
│ To Do      │ In Prog    │ Code Rev   │    QA      │    Done     │
│ (WIP: ∞)   │ (WIP: 4)   │ (WIP: 2)   │ (WIP: 2)   │   (WIP: ∞)  │
├────────────┼────────────┼────────────┼────────────┼─────────────┤
│ TASK-402   │ TASK-401   │            │            │             │
│ Redis      │ WebSocket  │            │            │             │
│ (Pedro)    │ (Carlos)   │            │            │             │
│            │            │            │            │             │
│ TASK-403   │ TASK-404   │            │            │             │
│ y-monaco   │ WS Auth    │            │            │             │
│ (Marina)   │ (Ana)      │            │            │             │
│            │            │            │            │             │
│ TASK-405   │            │            │            │             │
│ Tests      │            │            │            │             │
│ (Marina)   │            │            │            │             │
│            │            │            │            │             │
│ TASK-406   │            │            │            │             │
│ Monitoring │            │            │            │             │
│ (Carlos)   │            │            │            │             │
└────────────┴────────────┴────────────┴────────────┴─────────────┘
```

Conforme sprint progride, tasks movem da esquerda para direita até "Done".

## 6. Colaboração Cross-Funcional

### 6.1 Estrutura de Squad Multidisciplinar

Squad moderna inclui múltiplas disciplinas trabalhando em sincronia:

- **Product Manager (PM):** Define o quê construir e por quê
- **Designer (UX/UI):** Define como deve funcionar e parecer
- **Desenvolvedores (Eng):** Constroem solução técnica
- **QA/Test Engineer:** Valida qualidade
- **Data Analyst:** Fornece insights baseados em dados

**Modelo de Squad (inspirado em Spotify):**

```
Squad "Collaboration" (6-8 pessoas)
├── Product Manager (1)
│   └── Responsabilidade: Roadmap, priorização, stakeholder management
├── Designer (1)
│   └── Responsabilidade: User research, wireframes, protótipos
├── Engenharia (4)
│   ├── Backend Dev (2): API, WebSocket, database
│   ├── Frontend Dev (2): React components, state management
│   └── Responsabilidade: Implementação técnica, code quality
└── QA Engineer (1)
    └── Responsabilidade: Test planning, automation, validação

Características:
- Autonomous: Decide como atingir objetivos
- Cross-functional: Todas skills necessárias para entregar
- Co-located (ou sync timezone): Facilita comunicação
- Long-lived: Time estável (não temporário como projetos)
```

### 6.2 Rituais de Colaboração

#### 6.2.1 Kickoff de Feature (Trio: PM + Design + Eng)

Antes de começar desenvolvimento, trio alinha compreensão de problema e solução.

```markdown
## Feature Kickoff - Real-time Collaboration

### Participantes
- PM (Ana): Product Owner
- Design (Bruno): UX Designer
- Eng Lead (Carlos): Tech Lead

### Agenda

**1. Contexto de Negócio (PM)**
- Por que?: Clientes enterprise pedem colaboração (bloqueador para $500k deal)
- Quem?: 50 beta users (clientes pagantes, uso intenso)
- Quando?: MVP em 4 semanas (deadline: fim de Q1)
- Sucesso?: 80% beta users adotam feature, NPS >= 8

**2. Solução de UX (Design)**
- Wireframes: [Link para Figma]
- Fluxo: Usuário entra em doc → vê avatares de outros usuários → edita simultaneamente
- Interações: Cursors coloridos, presence indicators, conflict-free editing
- Edge cases: Offline editing, network failures

**3. Viabilidade Técnica (Eng)**
- Arquitetura: Yjs (CRDT) + WebSocket + Redis
- Complexidade: Alta (novos padrões, infra nova)
- Riscos: Escalabilidade (100+ users/doc), offline sync
- Trade-offs: Build (8 semanas) vs. Buy Firepad (2 semanas + vendor lock-in)
- Decisão: Build com Yjs (mais controle, menos lock-in)

**4. Quebra em Milestones**
- Milestone 1 (2 semanas): Backend + basic sync
- Milestone 2 (1 semana): Frontend + cursors
- Milestone 3 (1 semana): Offline sync + polish

**5. Definição de Done**
- Load tested para 200 users/doc
- Offline-first funciona (IndexedDB + sync on reconnect)
- Latência p95 < 500ms
- Validado por 5 beta users (qualitative feedback)

### Action Items
- [ ] PM: Recrutar 5 beta testers (esta semana)
- [ ] Design: Finalizar protótipo interativo (3 dias)
- [ ] Eng: Spike técnico Yjs + Redis (1 semana)
```

#### 6.2.2 Design Review (Validação de UX antes de Dev)

Antes de desenvolvimento, time valida design para identificar gaps e edge cases.

```markdown
## Design Review - Realtime Collaboration UI

### Protótipo
[Link para Figma Prototype]

### Feedback da Engenharia

**Carlos (Backend):**
"Design mostra 'typing indicator' quando usuário está digitando. Como detectar?
- Opção 1: Enviar evento a cada keystroke (muito tráfego)
- Opção 2: Enviar evento 1x quando começa a digitar, 1x quando para (otimizado)
Sugestão: usar Opção 2 com debounce de 2s."

**Marina (Frontend):**
"Design mostra avatar do usuário no cursor. Como lidar com 20+ usuários na tela?
- Risco: UI poluída, cursors sobrepostos
Sugestão: mostrar max 5 cursors mais próximos do viewport, resto em sidebar."

**Pedro (DevOps):**
"Design assume conexão estável. Como indicar quando usuário está offline?
Sugestão: banner discreto 'Offline - edições serão sincronizadas quando reconectar'."

### Decisões
- [ ] Designer atualiza prototype com offline state
- [ ] Designer simplifica cursors para evitar poluição visual
- [ ] Eng implementa typing indicator com debounce
```

#### 6.2.3 Technical Spike (Validação de Viabilidade)

Antes de commitar esforço significativo, time faz spike para reduzir incerteza técnica.

```markdown
## Technical Spike - Yjs CRDT Performance

### Objetivo
Validar que Yjs consegue lidar com requisitos de escala:
- 100+ usuários simultâneos por documento
- Documentos de até 10,000 linhas
- Latência p95 < 500ms

### Metodologia
1. Setup ambiente de teste com y-websocket-server + Redis
2. Criar script de load testing com Playwright
3. Simular 100 clients editando simultaneamente
4. Medir latência, memory usage, CPU

### Resultados

**Cenário 1: 50 usuários, documento 1,000 linhas**
- Latência p95: 180ms ✅
- Memory (server): 250 MB ✅
- CPU (server): 40% ✅

**Cenário 2: 100 usuários, documento 1,000 linhas**
- Latência p95: 420ms ✅
- Memory (server): 480 MB ✅
- CPU (server): 75% ✅

**Cenário 3: 100 usuários, documento 10,000 linhas**
- Latência p95: 1,200ms ❌ (excede SLA)
- Memory (server): 1.2 GB ⚠️
- CPU (server): 90% ⚠️

### Conclusões
- Yjs funciona bem para casos típicos (< 5,000 linhas)
- Documentos grandes precisam otimização (lazy loading, pagination)
- Decisão: Implementar limit de 5,000 linhas para MVP
- Follow-up: Investigar pagination para v1.1

### Code do Load Test
```typescript
// load-test-yjs.ts
import { test } from '@playwright/test';

test('100 concurrent users editing', async ({ browser }) => {
  const clients = [];
  const startTime = Date.now();

  // Criar 100 browser contexts
  for (let i = 0; i < 100; i++) {
    const context = await browser.newContext();
    const page = await context.newPage();
    await page.goto('http://localhost:3000/doc/test');
    clients.push(page);
  }

  // Todos editam simultaneamente
  await Promise.all(
    clients.map((page, i) =>
      page.locator('[data-testid="editor"]').type(`User ${i} editing`)
    )
  );

  const endTime = Date.now();
  const latency = endTime - startTime;

  console.log(`Latency for 100 users: ${latency}ms`);
});
```
```

#### 6.2.4 Engenharia + PM Sync (Alinhamento Contínuo)

Time faz sync regular (2-3x por semana) para alinhar progresso e decisões emergentes.

```markdown
## Eng + PM Sync - Sprint 24 Day 5

### Progress Update (Eng)
**Carlos:** "WebSocket server funcionando. 50 conexões simultâneas testadas. Próximo: integrar Redis."
**Ana:** "Auth no WebSocket completo. Bloqueio: preciso de review de segurança."
**Marina:** "y-monaco integrado, sincronizando texto. Bug: formatting (bold/italic) não sincroniza."
**Pedro:** "Redis cluster up. Configurando persistence provider."

### Blockers
- Marina: Formatting não sincroniza
  - Root cause: Monaco usa formato proprietário, Yjs usa Delta
  - Solução: Criar adapter entre formatos
  - ETA: +2 dias (não impacta Sprint Goal, pode ser v1.1)
  - **Decisão PM:** MVP sem formatting sync, adicionar no backlog

- Ana: Review de segurança bloqueado
  - Security team com backlog de 2 semanas
  - Risco: Atrasar launch
  - **Decisão PM:** PM escala para VP Eng para fast-track review

### Scope Changes
- **Remove:** Formatting sync (moved to v1.1)
- **Add:** Basic presence indicators (cursors apenas, sem avatars)
- Impacto: Reduz scope em 3 pts, aumenta confiança em deadline

### Action Items
- [ ] Marina: Criar ticket para formatting sync (backlog)
- [ ] PM: Escalar security review com VP Eng
- [ ] Carlos: Pair com Pedro em Redis integration (desbloquear)
```

### 6.3 Documentação Compartilhada (Single Source of Truth)

Times colaborativos mantêm documentação centralizada e atualizada.

**RFCs (Request for Comments) para decisões técnicas:**

```markdown
# RFC-015: Escolha de CRDT Library para Real-time Collaboration

## Status
Proposed (2025-01-10) → Under Review (2025-01-12) → Accepted (2025-01-15)

## Authors
Carlos (Backend Lead), Marina (Frontend Lead)

## Summary
Proposta de usar Yjs como CRDT library para implementar real-time collaboration.

## Motivation
Precisamos escolher tecnologia para sync de documentos entre múltiplos usuários.
Requisitos:
- Conflict-free merging (CRDTs)
- Offline-first support
- Performance para 100+ usuários simultâneos
- Maturidade e comunidade ativa

## Detailed Design

### Arquitetura
```
Client (Browser)              Server (Node.js)           Persistence
┌─────────────────┐          ┌──────────────────┐       ┌──────────┐
│ Monaco Editor   │          │ y-websocket      │       │  Redis   │
│      ↕          │  WS      │   -server        │       │          │
│ Yjs Document ◄──┼──────────┼► Yjs Document ───┼──────►│ Y.Doc    │
│      ↕          │          │                  │       │ Snapshots│
│ y-monaco binding│          │                  │       │          │
└─────────────────┘          └──────────────────┘       └──────────┘
```

### Alternatives Considered
1. **Operational Transform (OT)**: Google Docs usa, mas complexo e propenso a bugs
2. **Automerge**: CRDT alternativo, mas performance inferior (benchmarks: 10x mais lento)
3. **Build from scratch**: Levaria 6+ meses, alto risco

### Trade-offs
**Pros:**
- Conflict resolution automático (CRDTs)
- Offline-first nativo
- Madura (5+ anos, usado por Notion, Linear)
- Performance excelente (benchmarks)

**Cons:**
- Payload maior que OT (~30% mais bytes)
- Curva de aprendizado (conceitos novos)
- Vendor lock-in (migrar para outro CRDT seria custoso)

### Open Questions
- Q: Como lidar com permissões granulares (editar apenas seção do doc)?
- A: Usar sub-documents do Yjs (cada seção é Y.Doc separado)

- Q: Como migrar documentos existentes para Yjs format?
- A: Script de migração batch (converte HTML → Y.Doc via y-prosemirror)

## Implementation Plan
1. Spike de 1 semana (validar viabilidade) ✅ Done
2. Setup infrastructure (Redis + WebSocket server) - Sprint 24
3. Integrar frontend (y-monaco) - Sprint 24
4. Testes de carga - Sprint 25
5. Beta release - Sprint 26

## Success Metrics
- Load test: 200 usuários simultâneos com latência p95 < 500ms
- Adoption: 80% beta users usam colaboração real-time
- Quality: Zero data loss incidents

## Reviewers
- [x] Pedro (DevOps): Approved (Redis setup OK)
- [x] Ana (Security): Approved com ressalva (adicionar rate limiting)
- [x] Bruno (Design): Approved
- [x] PM: Approved

## Decision
**Accepted** em 2025-01-15. Mover para implementação.
```

## 7. Conclusões

O desenvolvimento e gestão de produtos digitais transcendem execução técnica, exigindo de desenvolvedores pensamento estratégico, colaboração cross-funcional e foco em outcomes de negócio mensuráveis. As metodologias ágeis - seja Scrum com sua estrutura de sprints e cerimônias, seja Kanban com seu foco em fluxo contínuo - fornecem frameworks para entregas iterativas e incrementais que reduzem risco através de feedback rápido.

O ciclo de vida completo de desenvolvimento - desde pesquisa e descoberta até acompanhamento pós-lançamento - enfatiza a importância de validação contínua de hipóteses, aprendizado baseado em dados reais de usuários, e adaptação de roadmap baseado em insights emergentes. Desenvolvedores que participam ativamente de discovery, contribuem para definição de escopo técnico, e articulam trade-offs entre velocidade e qualidade tornam-se contribuidores estratégicos que influenciam não apenas como construir, mas o quê construir.

Estratégias de roadmap e frameworks de priorização (RICE, MoSCoW, Kano) capacitam decisões baseadas em dados sobre alocação de recursos escassos, maximizando impacto por unidade de esforço. A gestão disciplinada de backlog - através de hierarquia clara (temas → épicos → stories → tasks), acceptance criteria bem definidos, e Definition of Ready/Done rigorosas - reduz ambiguidade e minimiza retrabalho causado por requisitos mal compreendidos.

A colaboração cross-funcional entre produto, design e tecnologia quebra silos através de rituais estruturados (kickoffs de feature, design reviews, technical spikes), documentação compartilhada (RFCs, ADRs), e comunicação contínua focada em alinhamento de contexto. Squads autônomas e multidisciplinares, quando equipadas com habilidades complementares e objetivos claros, entregam valor de forma mais eficiente que equipes organizadas por função técnica.

Para desenvolvedores, dominar esses conceitos representa evolução de executor tático para líder técnico que influencia outcomes de produto através de contribuições que transcendem código. A capacidade de questionar premissas com base em dados técnicos, propor alternativas de menor custo para atingir mesmos resultados de negócio, e comunicar complexidade técnica em linguagem acessível a stakeholders não-técnicos são competências diferenciadoras que separam desenvolvedores seniores de desenvolvedores juniores.

O desenvolvimento de produtos digitais é disciplina que equilibra arte e ciência: ciência de frameworks estruturados, métricas quantitativas e processos repetíveis; arte de empatia com usuários, criatividade em soluções, e julgamento qualitativo sobre quando seguir dados e quando questionar premissas subjacentes. Desenvolvedores que abraçam essa dualidade tornam-se não apenas construtores de software, mas arquitetos de produtos que geram impacto mensurável e sustentável para usuários e negócios.

## 8. Referências Bibliográficas

### Livros Fundamentais

1. **Cagan, M.** (2017). *Inspired: How to Create Tech Products Customers Love*. Wiley. ISBN: 978-1119387503
   - Referência definitiva sobre gestão de produtos, abordando discovery, delivery e cultura de produto.

2. **Knapp, J., Zeratsky, J., & Kowitz, B.** (2016). *Sprint: How to Solve Big Problems and Test New Ideas in Just Five Days*. Simon & Schuster. ISBN: 978-1501121746
   - Framework estruturado para discovery rápido e validação de hipóteses através de protótipos.

3. **Sutherland, J., & Schwaber, K.** (2020). *The Scrum Guide*. Scrum.org.
   - Guia oficial de Scrum, definindo papéis, artefatos e cerimônias.
   - Disponível em: https://scrumguides.org/

4. **Anderson, D. J.** (2010). *Kanban: Successful Evolutionary Change for Your Technology Business*. Blue Hole Press. ISBN: 978-0984521401
   - Fundamentos de Kanban aplicados a desenvolvimento de software.

5. **Patton, J.** (2014). *User Story Mapping: Discover the Whole Story, Build the Right Product*. O'Reilly Media. ISBN: 978-1491904909
   - Técnicas para estruturação de backlog e visualização de jornadas de usuário.

### Artigos e Papers Acadêmicos

6. **Beck, K., et al.** (2001). *Manifesto for Agile Software Development*. AgileManifesto.org.
   - Documento fundacional de metodologias ágeis.
   - Disponível em: https://agilemanifesto.org/

7. **Shapiro, M., et al.** (2011). *Conflict-free Replicated Data Types*. In Proceedings of the 13th International Symposium on Stabilization, Safety, and Security of Distributed Systems (SSS'11).
   - Paper acadêmico sobre CRDTs (base teórica para Yjs e colaboração real-time).

8. **Kleppmann, M., & Beresford, A. R.** (2017). *A Conflict-Free Replicated JSON Datatype*. IEEE Transactions on Parallel and Distributed Systems, 28(10), 2733-2746.
   - Fundamentos teóricos de Automerge e estruturas de dados replicadas.

### Recursos Online e Documentação Técnica

9. **Yjs Documentation** (2024). *Yjs - A CRDT framework for building collaborative applications*.
   - Disponível em: https://docs.yjs.dev/

10. **Atlassian Agile Coach** (2024). *Scrum, Kanban, and Agile Best Practices*.
    - Disponível em: https://www.atlassian.com/agile

11. **Mind the Product** (2024). *Product Management Resources and Community*.
    - Disponível em: https://www.mindtheproduct.com/

12. **Product Coalition** (2024). *Product Management Articles and Insights*.
    - Disponível em: https://productcoalition.com/

### Ferramentas e Frameworks

13. **Jira Software Documentation** (2024). *Agile Project Management with Jira*.
    - Disponível em: https://www.atlassian.com/software/jira/guides

14. **Linear Method** (2024). *How Linear Builds Products*.
    - Disponível em: https://linear.app/method

15. **Notion Product Wiki** (2024). *How Notion Approaches Product Development*.
    - Disponível em: https://www.notion.so/

### Comunidades e Blogs Especializados

16. **Lenny's Newsletter** (2024). *Product Management Strategies and Tactics*.
    - Disponível em: https://www.lennysnewsletter.com/

17. **Gibson Biddle's Blog** (2024). *Product Strategy and Leadership* (ex-VP Product Netflix).
    - Disponível em: https://gibsonbiddle.medium.com/

18. **Martin Fowler's Blog** (2024). *Software Development Practices and Patterns*.
    - Disponível em: https://martinfowler.com/

## Apêndice A: Templates e Checklists

### A.1 Template: User Story

```markdown
## [STORY-XXX] Título Descritivo da User Story

### Description
**Como** [tipo de usuário]
**Quero** [ação/funcionalidade]
**Para** [benefício/valor]

### Acceptance Criteria
- [ ] Critério 1 (testável e específico)
- [ ] Critério 2
- [ ] Critério 3

### Technical Notes
- Dependências: [outras stories, APIs, infra]
- Riscos técnicos: [incertezas, complexidade]
- Estimativa: [story points ou hours]

### Definition of Done
- [ ] Code review aprovado
- [ ] Testes unitários (coverage >= 80%)
- [ ] Testes de integração passando
- [ ] Documentação atualizada
- [ ] Deploy em staging validado por PO
```

### A.2 Template: Architecture Decision Record (ADR)

```markdown
# ADR-XXX: [Título da Decisão]

## Status
[Proposed | Accepted | Deprecated | Superseded by ADR-YYY]

## Context
[Descrever problema e restrições que motivam decisão]

## Decision
[Descrever decisão tomada e justificativa]

## Consequences

### Positive
- [Benefício 1]
- [Benefício 2]

### Negative
- [Trade-off 1]
- [Trade-off 2]

### Risks
- [Risco 1 e como mitiga]

## Alternatives Considered
1. **[Alternativa 1]**: [Por que rejeitada]
2. **[Alternativa 2]**: [Por que rejeitada]
```

### A.3 Checklist: Sprint Planning

```markdown
## Sprint Planning Checklist

### Pré-Planning (Backlog Refinement)
- [ ] Product Backlog ordenado por prioridade
- [ ] Top 10 stories têm acceptance criteria claros
- [ ] Stories estimadas com story points
- [ ] Dependências identificadas e mapeadas
- [ ] Mockups/designs finalizados (se aplicável)

### Durante Planning - Parte 1
- [ ] Sprint Goal definido e comunicado
- [ ] Velocity histórica revisada
- [ ] Capacity do time calculada (considerando férias, feriados)
- [ ] Stories selecionadas baseado em capacity
- [ ] Time commita com confiança

### Durante Planning - Parte 2
- [ ] Stories quebradas em tasks granulares (4-8h)
- [ ] Dependências técnicas discutidas
- [ ] Riscos técnicos identificados
- [ ] Tasks atribuídas a desenvolvedores
- [ ] Definition of Done revisada e acordada

### Pós-Planning
- [ ] Sprint Backlog atualizado em Jira/ferramenta
- [ ] Sprint Goal visível para todo time
- [ ] Stakeholders notificados sobre escopo da sprint
```

### A.4 Checklist: Code Review

```markdown
## Code Review Checklist

### Funcionalidade
- [ ] Código atende todos acceptance criteria
- [ ] Edge cases tratados (null, empty, errors)
- [ ] Validação de inputs implementada

### Qualidade de Código
- [ ] Código legível e bem estruturado
- [ ] Funções pequenas e single-responsibility
- [ ] Nomes de variáveis/funções descritivos
- [ ] Sem código duplicado (DRY)
- [ ] Sem code smells (god classes, long methods)

### Testes
- [ ] Testes unitários cobrem lógica principal
- [ ] Casos de erro testados
- [ ] Coverage >= 80%
- [ ] Testes de integração (se aplicável)

### Performance
- [ ] Sem N+1 queries
- [ ] Algoritmos otimizados (complexidade adequada)
- [ ] Sem memory leaks óbvios

### Segurança
- [ ] Inputs validados/sanitizados
- [ ] Sem hardcoded secrets
- [ ] OWASP top 10 considerados

### Documentação
- [ ] Comentários para lógica complexa
- [ ] README atualizado (se aplicável)
- [ ] API docs atualizados (se aplicável)
```

## Apêndice B: Glossário e Termos Técnicos

**Acceptance Criteria**: Condições específicas que user story deve atender para ser considerada "Done" de perspectiva funcional.

**Agile Manifesto**: Documento de 2001 que estabelece valores e princípios de metodologias ágeis de desenvolvimento de software.

**Architecture Decision Record (ADR)**: Documento que captura decisão arquitetural importante, contexto, alternativas consideradas e consequências.

**Backlog**: Lista priorizada de trabalho a ser feito (user stories, bugs, tech debt) mantida por Product Owner.

**Backlog Refinement (Grooming)**: Processo contínuo de adicionar detalhes, estimativas e ordem a itens do Product Backlog.

**Burndown Chart**: Gráfico que mostra trabalho restante vs. tempo em sprint, usado para prever se time completará trabalho commitado.

**CRDT (Conflict-free Replicated Data Type)**: Estrutura de dados distribuída que garante convergência eventual sem coordenação central, usada em edição colaborativa real-time.

**Cycle Time**: Tempo desde início do trabalho até conclusão (perspectiva interna do time).

**Daily Scrum (Standup)**: Reunião diária de 15 minutos onde time sincroniza progresso e identifica impedimentos.

**Definition of Done (DoD)**: Checklist compartilhada de critérios que incremento deve atender para ser considerado completo.

**Definition of Ready (DoR)**: Checklist de critérios que user story deve atender antes de ser puxada para sprint.

**Epic**: Grande corpo de trabalho que pode ser quebrado em múltiplas user stories (tipicamente > 13 story points).

**Feature Flag (Feature Toggle)**: Técnica de deploy que permite habilitar/desabilitar funcionalidades em runtime sem redeploy.

**Kanban**: Método de gestão de fluxo de trabalho que foca em visualização, limitação de WIP e otimização contínua.

**Lead Time**: Tempo desde criação do work item até conclusão (perspectiva do cliente/stakeholder).

**Minimum Viable Product (MVP)**: Versão mais simples de produto que permite validar hipóteses com menor esforço possível.

**MoSCoW**: Framework de priorização que categoriza features em Must Have, Should Have, Could Have, Won't Have.

**Product Backlog**: Lista ordenada de tudo que pode ser necessário no produto, gerenciada por Product Owner.

**Product Owner (PO)**: Papel em Scrum responsável por maximizar valor do produto e gerenciar Product Backlog.

**RICE**: Framework de priorização baseado em Reach (alcance), Impact (impacto), Confidence (confiança), Effort (esforço).

**Roadmap**: Representação visual de plano estratégico de produto ao longo do tempo, comunicando visão e prioridades.

**Scrum**: Framework ágil que organiza trabalho em sprints time-boxed com papéis, artefatos e cerimônias bem definidas.

**Scrum Master (SM)**: Facilitador que assegura que time entende e pratica Scrum, remove impedimentos.

**Sprint**: Período time-boxed (1-4 semanas) durante o qual incremento "Done" e potencialmente shippable é criado.

**Sprint Backlog**: Subset do Product Backlog selecionado para sprint, mais plano de entrega.

**Sprint Planning**: Cerimônia onde time planeja trabalho da sprint (o quê construir e como).

**Sprint Retrospective**: Cerimônia ao final da sprint onde time reflete sobre processo e identifica melhorias.

**Sprint Review**: Cerimônia ao final da sprint para inspecionar incremento e adaptar Product Backlog baseado em feedback.

**Story Points**: Unidade de medida relativa de complexidade/esforço de user story (tipicamente escala Fibonacci: 1, 2, 3, 5, 8, 13, 21).

**Technical Spike**: Work item de time-boxed research para reduzir incerteza técnica ou ganhar conhecimento.

**User Story**: Descrição informal de funcionalidade de perspectiva do usuário (formato: Como... Quero... Para...).

**Velocity**: Quantidade de story points que time consistentemente completa por sprint (métrica de capacidade).

**WIP (Work in Progress)**: Quantidade de trabalho iniciado mas não completado; Kanban limita WIP para otimizar fluxo.

**Yjs**: Framework JavaScript de CRDT para construir aplicações colaborativas real-time com sincronização peer-to-peer.
