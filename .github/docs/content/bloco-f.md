<!-- markdownlint-disable -->

# Métricas e Análise de Desempenho: Perspectiva para Desenvolvedores

## Resumo Executivo

Este documento apresenta os fundamentos essenciais de métricas e análise de desempenho em produtos digitais, com foco na perspectiva do desenvolvedor de software. Aborda quatro pilares fundamentais: (1) métricas essenciais para gestão de produtos incluindo OKRs e KPIs; (2) análise de dados para tomada de decisão estruturada; (3) ferramentas de analytics como Google Analytics, Mixpanel e Power BI; e (4) ajustes estratégicos baseados em feedback e métricas.

A gestão baseada em métricas diferencia-se da intuição ao fornecer evidências quantificáveis para decisões de produto, reduzindo riscos e aumentando a taxa de sucesso de iniciativas. Para desenvolvedores, compreender esses conceitos é essencial para instrumentar código adequadamente, construir dashboards de monitoramento eficazes, interpretar dados de performance e contribuir estrategicamente para otimizações que geram impacto mensurável no negócio e na experiência do usuário.

## 1. Introdução e Conceitos Fundamentais

### 1.1 Definição de Métricas em Produtos Digitais

Métricas são medidas quantificáveis que permitem avaliar o desempenho, progresso e saúde de um produto digital. No contexto de desenvolvimento de software, métricas transcendem código e infraestrutura, conectando implementação técnica a resultados de negócio e comportamento de usuários.

Uma métrica eficaz possui cinco características críticas:

1. **Mensurável**: Pode ser capturada e quantificada de forma objetiva
   - *Exemplo*: Tempo de resposta de API (medido em milissegundos)
2. **Relevante**: Conecta-se diretamente a objetivos de negócio ou produto
   - *Exemplo*: Taxa de conversão em processo de checkout
3. **Acionável**: Fornece insights que permitem tomada de decisão
   - *Exemplo*: Taxa de abandono em etapa específica de funil
4. **Comparável**: Permite análise temporal ou benchmarking
   - *Exemplo*: Crescimento MoM (Month-over-Month) de usuários ativos
5. **Compreensível**: Pode ser interpretada por stakeholders técnicos e não-técnicos
   - *Exemplo*: NPS (Net Promoter Score) de -100 a +100

### 1.2 Categorias de Métricas

**Métricas de Negócio**
- Avaliam impacto comercial e financeiro do produto
- Exemplo: MRR (Monthly Recurring Revenue), LTV (Lifetime Value), CAC (Customer Acquisition Cost)
- Relevância para desenvolvedores: Justificam investimentos em features e infraestrutura

**Métricas de Produto**
- Medem engajamento, adoção e retenção de funcionalidades
- Exemplo: DAU/MAU, Feature Adoption Rate, Stickiness
- Relevância para desenvolvedores: Validam hipóteses de features e priorizam backlog

**Métricas Técnicas**
- Avaliam performance, confiabilidade e qualidade do código
- Exemplo: Uptime, Latency P95, Error Rate, Code Coverage
- Relevância para desenvolvedores: Monitoram saúde técnica e guiam otimizações

**Métricas de Experiência do Usuário**
- Mensuram satisfação e qualidade de interação
- Exemplo: NPS, CSAT, Time to First Value, Task Success Rate
- Relevância para desenvolvedores: Identificam pontos de fricção em interfaces

### 1.3 Dados vs. Métricas vs. Insights

É fundamental compreender a hierarquia de informação em produtos digitais:

**Dados Brutos**
- Registros individuais de eventos e interações
- Exemplo: Log de requisição HTTP com timestamp, endpoint, status code, latency
- Características: Alto volume, baixo contexto, não processado

**Métricas**
- Agregação e cálculo sobre dados brutos
- Exemplo: Latência P95 das últimas 24h = 420ms
- Características: Condensado, mensurável, comparável

**Insights**
- Interpretação de métricas que gera ação
- Exemplo: "Latência P95 aumentou 40% após deploy de v2.3, impactando conversão em 8%"
- Características: Contexto, causação, recomendação

Para desenvolvedores, a progressão de dados → métricas → insights representa a jornada de instrumentação técnica (logs, eventos) para contribuição estratégica (recomendações baseadas em dados).

### 1.4 Cultura Data-Driven vs. Data-Informed

**Data-Driven (Guiado por Dados)**
- Decisões são ditadas exclusivamente por métricas
- Riscos: Otimização míope, falta de visão estratégica, paralisia por análise
- Exemplo problemático: Rejeitar feature inovadora porque dados históricos não provam ROI

**Data-Informed (Informado por Dados)**
- Dados são um dos inputs para decisão, junto com visão, estratégia e intuição
- Benefícios: Equilíbrio entre evidência e inovação
- Exemplo saudável: Usar dados de abandono em checkout para priorizar refatoração de UX, mas incluir validação qualitativa com usuários

Para desenvolvedores, a abordagem data-informed permite questionar métricas de vaidade (pageviews) e propor métricas de impacto (task completion rate), além de contextualizar dados técnicos com impacto de negócio.

## 2. Métricas Essenciais para Gestão de Produtos

### 2.1 OKRs (Objectives and Key Results)

OKRs são um framework de definição de metas que conecta objetivos qualitativos aspiracionais a resultados-chave mensuráveis. Desenvolvidos na Intel e popularizados pelo Google, OKRs fornecem clareza sobre o que deve ser alcançado e como medir sucesso.

#### 2.1.1 Estrutura de OKRs

**Objective (Objetivo)**
- Declaração qualitativa, inspiradora e aspiracional
- Responde: "O que queremos alcançar?"
- Características: Memorável, motivador, time-bound (geralmente trimestral)
- Exemplo para desenvolvedores: "Tornar nossa API a mais rápida e confiável do mercado"

**Key Results (Resultados-Chave)**
- Métricas quantitativas que comprovam alcance do objetivo
- Responde: "Como saberemos que alcançamos o objetivo?"
- Características: Mensuráveis, específicos, desafiadores mas atingíveis
- Exemplo para o objetivo acima:
  - KR1: Reduzir latência P95 de 500ms para 200ms
  - KR2: Aumentar uptime de 99.5% para 99.95%
  - KR3: Reduzir taxa de erros 5xx de 0.5% para 0.1%

#### 2.1.2 Exemplos de OKRs para Contexto de Desenvolvimento

**Exemplo 1: Performance e Escalabilidade**
- **Objetivo**: Garantir que nossa plataforma escale para suportar crescimento de 10x em usuários
- **KR1**: Reduzir tempo de resposta de queries de banco de 800ms para 100ms
- **KR2**: Implementar caching que resulte em 60% de cache hit rate
- **KR3**: Reduzir uso de memória por usuário de 50MB para 15MB

**Exemplo 2: Developer Experience (DX)**
- **Objetivo**: Tornar nossa plataforma de desenvolvimento a mais produtiva da empresa
- **KR1**: Reduzir tempo de build de 15min para 5min
- **KR2**: Aumentar code coverage de 60% para 85%
- **KR3**: Reduzir tempo de onboarding de novos desenvolvedores de 2 semanas para 3 dias

**Exemplo 3: Experiência do Usuário**
- **Objetivo**: Melhorar significativamente a experiência de onboarding de usuários
- **KR1**: Aumentar taxa de ativação (completar onboarding) de 40% para 70%
- **KR2**: Reduzir Time to First Value de 5min para 90 segundos
- **KR3**: Aumentar NPS de novos usuários de 30 para 60

#### 2.1.3 Benefícios de OKRs para Desenvolvedores

**Alinhamento Estratégico**
- Conecta trabalho técnico diário a objetivos de negócio
- Exemplo: Refatoração de código justificada por KR de redução de latência

**Foco e Priorização**
- Limita WIP (Work in Progress) a iniciativas que movem KRs
- Exemplo: Rejeitar feature requests que não contribuem para OKRs do trimestre

**Transparência e Autonomia**
- Visibilidade de OKRs permite que desenvolvedores proponham soluções técnicas
- Exemplo: Propor migração de banco de dados baseado em KR de performance

**Mensuração de Impacto**
- Demonstra contribuição técnica em linguagem de negócio
- Exemplo: "Minha otimização de query moveu KR2 de 45% para 58%"

### 2.2 KPIs (Key Performance Indicators)

KPIs são métricas quantitativas que avaliam a eficácia de processos, funcionalidades ou produtos em alcançar objetivos estratégicos. Diferente de OKRs (que são time-bound e aspiracionais), KPIs são contínuos e representam saúde operacional.

#### 2.2.1 Categorias de KPIs

**KPIs de Engajamento**
- Medem como usuários interagem com o produto

**Taxa de Ativação (Activation Rate)**
```
Activation Rate = (Usuários que completaram ação-chave / Total de sign-ups) × 100
```
- Exemplo: 65% dos usuários que se cadastram completam tutorial interativo
- Relevância técnica: Identifica pontos de fricção em fluxos de onboarding

**Tempo Médio de Sessão (Average Session Duration)**
```
Avg Session Duration = Soma de duração de sessões / Número de sessões
```
- Exemplo: Usuários passam em média 8min por sessão no dashboard
- Relevância técnica: Valida hipóteses de features sticky vs. features utilitárias

**DAU/MAU (Daily Active Users / Monthly Active Users)**
```
Stickiness = DAU / MAU × 100
```
- Exemplo: 5000 DAU / 20000 MAU = 25% stickiness
- Relevância técnica: Alto stickiness (>20%) indica produto com uso frequente
- Benchmark: Facebook ~60%, SaaS típico 10-20%

**KPIs de Retenção**
- Medem capacidade de manter usuários ao longo do tempo

**Taxa de Retenção (Retention Rate)**
```
Retention Rate (Day N) = (Usuários ativos em Day N / Usuários que se cadastraram em Day 0) × 100
```
- Exemplo: 40% dos usuários que se cadastraram ainda estão ativos após 30 dias
- Relevância técnica: Curva de retenção (D1, D7, D30) revela quando usuários abandonam

**Churn Rate (Taxa de Cancelamento)**
```
Churn Rate = (Usuários cancelados no período / Total de usuários no início do período) × 100
```
- Exemplo: 5% dos assinantes cancelam por mês
- Relevância técnica: Permite calcular vida útil esperada do cliente (1/churn rate)
- Benchmark: SaaS B2B aceitável: 5-7% anual; B2C: 5-7% mensal

**KPIs de Receita**
- Medem impacto financeiro do produto

**MRR (Monthly Recurring Revenue)**
```
MRR = Soma de receitas recorrentes mensais de todos assinantes ativos
```
- Exemplo: $500k MRR com 1000 clientes = $500 ARPU (Average Revenue Per User)
- Relevância técnica: Justifica investimentos em features enterprise vs. freemium

**LTV (Lifetime Value)**
```
LTV = (ARPU × Margem Bruta) / Churn Rate
```
- Exemplo: ($50 ARPU × 70% margem) / 5% churn = $700 LTV
- Relevância técnica: Comparado com CAC (Customer Acquisition Cost), define viabilidade de canais de aquisição
- Benchmark saudável: LTV/CAC > 3x

**Taxa de Conversão (Conversion Rate)**
```
Conversion Rate = (Usuários que converteram / Total de visitantes) × 100
```
- Exemplo: 2.5% dos visitantes do site se tornam clientes pagantes
- Relevância técnica: Análise de funil identifica gargalos técnicos (performance, bugs)

**KPIs de Satisfação**
- Medem percepção de qualidade e valor

**NPS (Net Promoter Score)**
```
NPS = % Promotores (9-10) - % Detratores (0-6)
```
- Escala: -100 (todos detratores) a +100 (todos promotores)
- Exemplo: 50% promotores, 10% detratores → NPS = +40
- Relevância técnica: Correlaciona com qualidade técnica (bugs reduzem NPS)
- Benchmark: Excelente >50, Bom 30-50, Aceitável 0-30

**CSAT (Customer Satisfaction Score)**
```
CSAT = (Respostas positivas 4-5 / Total de respostas) × 100
```
- Exemplo: "Como você avalia o suporte?" → 80% responderam 4 ou 5 (de 5)
- Relevância técnica: Pode ser aplicado a features específicas

**KPIs de Desempenho Técnico**
- Medem saúde e qualidade da infraestrutura

**Uptime (Disponibilidade)**
```
Uptime = (Tempo total - Tempo de downtime) / Tempo total × 100
```
- Exemplo: 99.95% uptime = ~22 minutos de downtime por mês
- Relevância técnica: SLAs (Service Level Agreements) são baseados em uptime
- Benchmark: 99.9% (três noves) = bom; 99.99% (quatro noves) = excelente

**Latência P95 (95th Percentile Response Time)**
```
P95 = Valor abaixo do qual 95% das requisições são respondidas
```
- Exemplo: P95 = 300ms significa que 95% das requests são respondidas em <300ms
- Relevância técnica: P95 melhor que média para capturar outliers
- Benchmark: APIs REST: P95 <500ms; GraphQL: P95 <1s

**Taxa de Erros (Error Rate)**
```
Error Rate = (Requisições com erro 5xx / Total de requisições) × 100
```
- Exemplo: 0.1% error rate em produção
- Relevância técnica: Erros 5xx indicam problemas no servidor
- Benchmark: <0.1% para produção de alta qualidade

#### 2.2.2 Framework AARRR (Pirate Metrics)

O framework AARRR, criado por Dave McClure, fornece uma estrutura para KPIs ao longo do ciclo de vida do usuário:

**Acquisition (Aquisição)**
- Como usuários descobrem o produto
- KPIs: Tráfego orgânico, taxa de conversão de landing page, CAC
- Exemplo técnico: Otimização de SEO, performance de página de destino

**Activation (Ativação)**
- Primeira experiência positiva do usuário
- KPIs: Taxa de ativação, Time to First Value
- Exemplo técnico: Onboarding interativo, setup wizard

**Retention (Retenção)**
- Usuários retornam ao produto
- KPIs: D1/D7/D30 retention, churn rate
- Exemplo técnico: Notificações push, email drip campaigns

**Revenue (Receita)**
- Usuários pagam pelo produto
- KPIs: MRR, LTV, ARPU
- Exemplo técnico: Paywall estratégico, checkout otimizado

**Referral (Indicação)**
- Usuários recomendam o produto
- KPIs: Viral coefficient, NPS
- Exemplo técnico: Programa de referral com incentivos

### 2.3 North Star Metric

A North Star Metric é a métrica única que melhor captura o valor central que o produto entrega aos clientes. Serve como bússola estratégica para toda a organização.

#### 2.3.1 Características de uma North Star Metric Eficaz

1. **Expressa valor para o cliente**: Não apenas métrica de vaidade
2. **Representa visão e estratégia**: Alinhada com missão da empresa
3. **É leading indicator de receita**: Prediz crescimento futuro
4. **É acionável**: Equipe pode influenciar através de features

#### 2.3.2 Exemplos de North Star Metrics

**Airbnb**: Número de noites reservadas
- Por quê: Captura valor para hóspedes (estadias) e anfitriões (receita)
- Leading indicator: Mais noites → mais receita de comissões

**Slack**: Mensagens enviadas por equipe
- Por quê: Engajamento profundo indica produto essencial
- Leading indicator: Equipes engajadas convertem para planos pagos

**Spotify**: Horas de música ouvida
- Por quê: Escuta frequente indica valor entregue e retenção
- Leading indicator: Mais horas → maior probabilidade de conversão Premium

**GitHub**: Número de pull requests mergeados
- Por quê: Colaboração ativa indica valor para desenvolvedores
- Leading indicator: Equipes colaborativas convertem para planos Team/Enterprise

#### 2.3.3 North Star Metric para Produtos Técnicos

**API/Plataforma de Desenvolvedores**: Número de API calls bem-sucedidas por mês
- Captura adoção (desenvolvedores integrando) e engajamento (uso recorrente)
- Leading indicator de receita (pricing baseado em volume)

**Ferramenta de CI/CD**: Número de deploys para produção por semana
- Captura valor (velocidade de entrega) e adoção (equipes usando)
- Leading indicator de retenção (equipes dependentes da ferramenta)

**Plataforma de Observabilidade**: Número de alerts acionáveis configurados
- Captura valor (monitoramento proativo) e maturidade de uso
- Leading indicator de expansão (mais serviços monitorados → planos maiores)

### 2.4 Implementação de Métricas no Código

Para desenvolvedores, métricas não são apenas dashboards — requerem instrumentação técnica adequada.

#### 2.4.1 Instrumentação de Eventos

**Event Tracking Básico**
```javascript
// Exemplo com Mixpanel (JavaScript)
mixpanel.track('User Signed Up', {
  'signup_method': 'email',
  'utm_source': 'google_ads',
  'user_role': 'developer'
});

mixpanel.track('Feature Used', {
  'feature_name': 'API_Key_Creation',
  'user_plan': 'pro',
  'timestamp': new Date().toISOString()
});
```

**Event Tracking com Contexto**
```python
# Exemplo com Segment (Python)
analytics.track(
    user_id='user_123',
    event='Checkout Completed',
    properties={
        'revenue': 49.99,
        'currency': 'USD',
        'products': ['pro_plan_monthly'],
        'checkout_duration_seconds': 45,
        'payment_method': 'credit_card'
    }
)
```

#### 2.4.2 Métricas Técnicas com OpenTelemetry

**Instrumentação de Latência**
```python
from opentelemetry import trace
from opentelemetry.instrumentation.flask import FlaskInstrumentor

# Auto-instrumentação de aplicação Flask
FlaskInstrumentor().instrument_app(app)

# Instrumentação manual de operação crítica
tracer = trace.get_tracer(__name__)

@app.route('/api/users/<user_id>')
def get_user(user_id):
    with tracer.start_as_current_span("get_user_from_db"):
        user = db.query(User).filter(User.id == user_id).first()
    return jsonify(user.to_dict())
```

**Métricas de Negócio com Custom Metrics**
```python
from prometheus_client import Counter, Histogram

# Contador de conversões
conversions_counter = Counter(
    'checkouts_completed_total',
    'Total number of completed checkouts',
    ['plan_type', 'payment_method']
)

# Histograma de valor de transação
transaction_value = Histogram(
    'checkout_value_usd',
    'Value of checkout transactions in USD',
    buckets=[10, 50, 100, 500, 1000]
)

@app.route('/checkout/complete', methods=['POST'])
def complete_checkout():
    plan = request.json['plan']
    amount = request.json['amount']
    payment_method = request.json['payment_method']

    # Processar checkout...

    # Registrar métricas
    conversions_counter.labels(
        plan_type=plan,
        payment_method=payment_method
    ).inc()

    transaction_value.observe(amount)

    return {'status': 'success'}
```

#### 2.4.3 Feature Flags com Métricas

```typescript
// Exemplo com LaunchDarkly (TypeScript)
import * as LaunchDarkly from 'launchdarkly-node-server-sdk';

const ldClient = LaunchDarkly.init(process.env.LD_SDK_KEY);

async function getUserDashboard(userId: string) {
  const user = { key: userId };

  // Avaliar feature flag
  const showNewDashboard = await ldClient.variation(
    'new-dashboard-redesign',
    user,
    false // default value
  );

  // Registrar evento customizado
  ldClient.track('dashboard_viewed', user, {
    dashboard_version: showNewDashboard ? 'v2' : 'v1',
    load_time_ms: 234
  });

  if (showNewDashboard) {
    return renderNewDashboard(userId);
  } else {
    return renderLegacyDashboard(userId);
  }
}
```

## 3. Análise de Dados para Tomada de Decisão

### 3.1 Fundamentos de Análise de Dados

Análise de dados é o processo sistemático de coletar, processar, interpretar e transformar dados brutos em insights acionáveis que fundamentam decisões estratégicas e operacionais.

#### 3.1.1 Ciclo de Análise de Dados

**1. Coleta de Dados**
- Fontes internas: Banco de dados transacional, logs de aplicação, eventos de produto
- Fontes externas: APIs de terceiros, dados de mercado, feedback de usuários
- Exemplo técnico: ETL pipeline que agrega dados de PostgreSQL, logs do Datadog e eventos do Mixpanel

**2. Processamento e Limpeza**
- Remoção de duplicatas, tratamento de valores nulos, normalização
- Exemplo técnico: Script Python com pandas para limpar dados antes de análise
```python
import pandas as pd

# Carregar dados brutos
df = pd.read_csv('user_events.csv')

# Remover duplicatas
df = df.drop_duplicates(subset=['user_id', 'event_timestamp'])

# Tratar valores nulos
df['country'] = df['country'].fillna('Unknown')

# Normalizar timestamps
df['event_timestamp'] = pd.to_datetime(df['event_timestamp'])
```

**3. Análise e Exploração**
- Análise estatística, visualização, identificação de padrões
- Exemplo técnico: Análise de coortes para entender retenção

**4. Interpretação de Resultados**
- Contextualização de dados, identificação de causas, formulação de hipóteses
- Exemplo técnico: Correlacionar queda de retenção com deploy de versão específica

**5. Tomada de Decisão e Ação**
- Recomendações baseadas em insights, priorização de iniciativas
- Exemplo técnico: Priorizar rollback de feature baseado em aumento de churn

### 3.2 Tipos de Análise de Dados

#### 3.2.1 Análise Descritiva (O que aconteceu?)

**Objetivo**: Sumarizar dados históricos para compreender o passado

**Técnicas**:
- Agregações: Médias, somas, contagens
- Visualizações: Gráficos de linhas, barras, pizza
- Relatórios: Dashboards de KPIs

**Exemplo Prático**:
```sql
-- Análise descritiva de receita por plano (último trimestre)
SELECT
  plan_type,
  COUNT(DISTINCT user_id) as total_customers,
  SUM(amount) as total_revenue,
  AVG(amount) as avg_revenue_per_customer
FROM subscriptions
WHERE created_at >= DATE_TRUNC('quarter', CURRENT_DATE - INTERVAL '3 months')
GROUP BY plan_type
ORDER BY total_revenue DESC;
```

**Output**:
```
plan_type    | total_customers | total_revenue | avg_revenue_per_customer
-------------|-----------------|---------------|-------------------------
Enterprise   | 45              | $225,000      | $5,000
Pro          | 1,200           | $144,000      | $120
Basic        | 5,500           | $82,500       | $15
```

**Insight**: Enterprise representa apenas 0.6% dos clientes mas 49% da receita → foco em retenção de contas Enterprise

#### 3.2.2 Análise Diagnóstica (Por que aconteceu?)

**Objetivo**: Identificar causas raiz de eventos ou tendências

**Técnicas**:
- Análise de correlação
- Drill-down (decomposição de métricas)
- Análise de coortes
- Root cause analysis

**Exemplo Prático - Investigação de Queda de Conversão**:

**Passo 1**: Identificar anomalia
```sql
-- Conversão por semana (últimas 8 semanas)
SELECT
  DATE_TRUNC('week', signup_date) as week,
  COUNT(DISTINCT user_id) as signups,
  COUNT(DISTINCT CASE WHEN converted = true THEN user_id END) as conversions,
  ROUND(100.0 * COUNT(DISTINCT CASE WHEN converted = true THEN user_id END) / COUNT(DISTINCT user_id), 2) as conversion_rate
FROM users
WHERE signup_date >= CURRENT_DATE - INTERVAL '8 weeks'
GROUP BY week
ORDER BY week;
```

**Output**:
```
week       | signups | conversions | conversion_rate
-----------|---------|-------------|----------------
2025-09-01 | 1,200   | 300         | 25.00%
2025-09-08 | 1,350   | 324         | 24.00%
2025-09-15 | 1,100   | 275         | 25.00%
2025-09-22 | 1,500   | 225         | 15.00% ⚠️
```

**Passo 2**: Drill-down por fonte de tráfego
```sql
SELECT
  utm_source,
  COUNT(DISTINCT user_id) as signups,
  ROUND(100.0 * COUNT(DISTINCT CASE WHEN converted = true THEN user_id END) / COUNT(DISTINCT user_id), 2) as conversion_rate
FROM users
WHERE signup_date >= '2025-09-22'
GROUP BY utm_source;
```

**Output**:
```
utm_source   | signups | conversion_rate
-------------|---------|----------------
organic      | 400     | 28.00%
google_ads   | 800     | 8.00% ⚠️
referral     | 300     | 30.00%
```

**Passo 3**: Análise de performance técnica
- Investigar latência de página de checkout na semana de 09-22
- Correlacionar com logs de erros JavaScript
- Descobrir: Deploy em 09-21 introduziu bug que quebrava checkout no Chrome mobile

**Insight**: Queda de conversão causada por bug técnico em checkout, correlacionado com campanha de Google Ads focada em mobile

#### 3.2.3 Análise Preditiva (O que pode acontecer?)

**Objetivo**: Usar dados históricos para prever comportamentos futuros

**Técnicas**:
- Regressão linear/logística
- Séries temporais (ARIMA, Prophet)
- Machine learning (classificação, clustering)

**Exemplo Prático - Predição de Churn**:

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

# Carregar dados históricos de usuários
df = pd.read_sql("""
  SELECT
    u.user_id,
    u.tenure_days,
    u.login_frequency_7d,
    u.feature_usage_score,
    u.support_tickets_count,
    u.plan_type,
    u.churned
  FROM users u
  WHERE u.signup_date < CURRENT_DATE - INTERVAL '90 days'
""", db_connection)

# Preparar features
X = df[['tenure_days', 'login_frequency_7d', 'feature_usage_score', 'support_tickets_count']]
X = pd.get_dummies(X, columns=['plan_type'])  # One-hot encoding
y = df['churned']

# Dividir em treino e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Treinar modelo
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Avaliar
y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))

# Identificar usuários com alta probabilidade de churn
current_users = pd.read_sql("SELECT * FROM users WHERE churned = false", db_connection)
churn_probabilities = model.predict_proba(current_users[feature_columns])[:, 1]
at_risk_users = current_users[churn_probabilities > 0.7]

print(f"Usuários em risco de churn: {len(at_risk_users)}")
```

**Output**:
```
              precision    recall  f1-score   support
Not Churned       0.92      0.95      0.93      1500
Churned           0.78      0.68      0.73       500

Usuários em risco de churn: 342
```

**Ação**: Criar campanha de retenção automatizada para os 342 usuários em risco

#### 3.2.4 Análise Prescritiva (O que fazer?)

**Objetivo**: Recomendar ações específicas baseadas em análises preditivas

**Técnicas**:
- Otimização matemática
- Simulação (Monte Carlo)
- A/B testing
- Sistemas de recomendação

**Exemplo Prático - Otimização de Pricing**:

```python
import numpy as np
from scipy.optimize import minimize

# Dados históricos: relação entre preço e conversão
prices = np.array([10, 15, 20, 25, 30, 35, 40])
conversion_rates = np.array([0.45, 0.38, 0.30, 0.22, 0.15, 0.10, 0.06])
monthly_visitors = 10000

# Função de receita esperada
def expected_revenue(price):
    # Interpolação de taxa de conversão baseada em dados históricos
    conversion_rate = np.interp(price, prices, conversion_rates)
    return -1 * (price * conversion_rate * monthly_visitors)  # Negativo para minimização

# Otimizar
result = minimize(expected_revenue, x0=25, bounds=[(10, 40)])
optimal_price = result.x[0]
optimal_conversion = np.interp(optimal_price, prices, conversion_rates)
optimal_revenue = -result.fun

print(f"Preço ótimo: ${optimal_price:.2f}")
print(f"Taxa de conversão esperada: {optimal_conversion:.2%}")
print(f"Receita mensal esperada: ${optimal_revenue:,.2f}")
```

**Output**:
```
Preço ótimo: $18.50
Taxa de conversão esperada: 32%
Receita mensal esperada: $59,200
```

**Recomendação**: Reduzir preço de $25 para $18.50 pode aumentar receita em 23%

### 3.3 Desafios na Implementação de Cultura Data-Driven

#### 3.3.1 Qualidade de Dados

**Problema**: Garbage in, garbage out
- Dados duplicados, inconsistentes ou incompletos geram insights errôneos

**Solução para Desenvolvedores**:
- Validação de dados na camada de aplicação
- Testes de integridade de dados no pipeline de ETL
- Monitoramento de data quality metrics

```python
# Exemplo de validação com Great Expectations
import great_expectations as ge

df = ge.read_csv('user_events.csv')

# Definir expectativas
df.expect_column_values_to_not_be_null('user_id')
df.expect_column_values_to_be_between('age', min_value=18, max_value=100)
df.expect_column_values_to_be_in_set('event_type', ['signup', 'login', 'checkout'])

# Validar
validation_result = df.validate()
if not validation_result['success']:
    raise ValueError("Data quality check failed!")
```

#### 3.3.2 Silos de Dados

**Problema**: Dados fragmentados em sistemas desconectados
- Exemplo: Dados de produto no Mixpanel, dados de suporte no Zendesk, dados financeiros no Stripe

**Solução para Desenvolvedores**:
- Data warehouse centralizado (Snowflake, BigQuery, Redshift)
- Ferramentas de ETL/ELT (Fivetran, Airbyte, dbt)
- Customer Data Platform (Segment, RudderStack)

#### 3.3.3 Paralisia por Análise

**Problema**: Excesso de dados gera indecisão
- Exemplo: Equipe passa semanas analisando dados sem tomar ação

**Solução para Desenvolvedores**:
- Definir SLA para análises (ex: decisões devem ser tomadas em 3 dias)
- Adotar abordagem data-informed (não data-driven puro)
- Usar regra 80/20: 80% de confiança é suficiente para maioria das decisões

#### 3.3.4 Falta de Expertise Técnica

**Problema**: Equipes não têm habilidades de SQL, estatística ou visualização

**Solução para Desenvolvedores**:
- Investir em treinamento (cursos de SQL, estatística básica)
- Contratar analytics engineer ou data analyst
- Usar ferramentas de self-service BI (Metabase, Looker, Mode)

## 4. Ferramentas de Analytics

### 4.1 Google Analytics

Google Analytics é a ferramenta mais popular de analytics web, focada em monitorar tráfego, comportamento de usuários e conversões em websites e aplicativos.

#### 4.1.1 Funcionalidades Principais

**Monitoramento de Tráfego**
- Sessões, pageviews, usuários únicos
- Fontes de tráfego (orgânico, pago, direto, referral)
- Geografia e dispositivos (desktop, mobile, tablet)

**Análise de Comportamento**
- Fluxo de usuários (path analysis)
- Tempo médio na página, bounce rate
- Eventos customizados (cliques, downloads, vídeos)

**Conversões e Objetivos**
- Configuração de goals (ex: completar checkout)
- Funis de conversão
- E-commerce tracking (receita, transações, produtos)

**Segmentação Avançada**
- Criar segmentos customizados (ex: usuários mobile do Brasil)
- Análise de coortes
- Comparação entre segmentos

#### 4.1.2 Implementação Técnica

**GA4 (Google Analytics 4) - Event-Based Tracking**

```html
<!-- Instalação do GA4 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

**Custom Events**
```javascript
// Evento de signup
gtag('event', 'sign_up', {
  'method': 'email',
  'user_role': 'developer'
});

// Evento de compra (e-commerce)
gtag('event', 'purchase', {
  'transaction_id': 'T12345',
  'value': 49.99,
  'currency': 'USD',
  'items': [{
    'item_id': 'pro_plan',
    'item_name': 'Pro Plan Monthly',
    'price': 49.99,
    'quantity': 1
  }]
});

// Evento customizado de feature usage
gtag('event', 'api_key_created', {
  'key_type': 'production',
  'user_plan': 'enterprise'
});
```

**Enhanced E-commerce Tracking**
```javascript
// Visualização de produto
gtag('event', 'view_item', {
  'items': [{
    'item_id': 'pro_plan',
    'item_name': 'Pro Plan',
    'price': 49.99
  }]
});

// Adicionar ao carrinho
gtag('event', 'add_to_cart', {
  'items': [{
    'item_id': 'pro_plan',
    'quantity': 1
  }]
});

// Início do checkout
gtag('event', 'begin_checkout', {
  'items': [{
    'item_id': 'pro_plan',
    'price': 49.99
  }]
});
```

#### 4.1.3 Casos de Uso para Desenvolvedores

**Otimização de Performance de Páginas**
- Analisar bounce rate por página
- Correlacionar tempo de carregamento com engajamento
- Identificar páginas lentas que causam abandono

**Attribution Modeling**
- Compreender jornada multi-touch (usuário visita via blog → Google Ads → converte)
- Justificar investimentos em SEO ou conteúdo
- Exemplo: 60% das conversões têm touchpoint em blog técnico → investir em conteúdo

**A/B Testing com Google Optimize**
- Testar variações de landing page
- Medir impacto em taxa de conversão
- Exemplo: Testar CTA "Start Free Trial" vs. "Get Started Free"

#### 4.1.4 Limitações do Google Analytics

**Foco em Web Analytics**
- Não é ideal para analytics de produto (in-app behavior)
- Limitado para rastrear ações pós-signup dentro de SaaS

**Amostragem de Dados**
- Em volumes altos (>500k sessões/mês), relatórios usam amostragem
- Pode gerar imprecisões em análises granulares

**Privacidade e Ad Blockers**
- ~25% dos usuários usam ad blockers que bloqueiam GA
- GDPR e LGPD requerem consentimento explícito

### 4.2 Mixpanel

Mixpanel é uma plataforma de product analytics focada em rastrear eventos granulares dentro de aplicações digitais, ideal para SaaS e produtos mobile.

#### 4.2.1 Funcionalidades Principais

**Event-Based Analytics**
- Rastreamento de ações específicas (não apenas pageviews)
- Exemplo: "User Created API Key", "Dashboard Filtered", "Export Clicked"

**Análise de Funis**
- Mapear jornada multi-step
- Identificar drop-offs em cada etapa
- Exemplo: Funil de onboarding: Signup → Email Verify → Profile Setup → First Action

**Retenção e Coortes**
- Curvas de retenção (D1, D7, D30)
- Análise de coortes por atributos (ex: usuários que se cadastraram via Google Ads)

**User Profiles**
- Enriquecer perfis com propriedades customizadas
- Histórico completo de eventos por usuário
- Segmentação avançada

**Testes A/B Nativos**
- Feature flags integrados
- Análise estatística automática
- Exemplo: Testar impacto de novo onboarding em ativação

#### 4.2.2 Implementação Técnica

**Instalação (JavaScript)**
```javascript
// Inicialização
mixpanel.init('YOUR_PROJECT_TOKEN');

// Identificar usuário
mixpanel.identify('user_123');

// Definir propriedades de usuário
mixpanel.people.set({
  '$email': 'developer@example.com',
  '$name': 'Jane Doe',
  'plan': 'pro',
  'signup_date': '2025-09-01'
});

// Rastrear evento
mixpanel.track('Feature Used', {
  'feature_name': 'API_Analytics',
  'feature_section': 'Dashboard',
  'session_duration_seconds': 120
});
```

**Instalação (Python - Backend)**
```python
from mixpanel import Mixpanel

mp = Mixpanel('YOUR_PROJECT_TOKEN')

# Rastrear evento de conversão (backend)
mp.track('user_123', 'Subscription Created', {
    'plan': 'enterprise',
    'billing_cycle': 'annual',
    'amount_usd': 5000,
    'payment_method': 'invoice'
})

# Atualizar perfil de usuário
mp.people_set('user_123', {
    'plan': 'enterprise',
    'mrr': 417,  # $5000/12
    'upgrade_date': '2025-11-09'
})
```

**Análise de Funil**
```javascript
// Passo 1: Signup
mixpanel.track('Signup Completed', {
  'method': 'email'
});

// Passo 2: Email Verification
mixpanel.track('Email Verified');

// Passo 3: Onboarding Started
mixpanel.track('Onboarding Started');

// Passo 4: First Action
mixpanel.track('First API Request Made', {
  'endpoint': '/v1/users',
  'response_time_ms': 145
});
```

#### 4.2.3 Casos de Uso para Desenvolvedores

**Product-Led Growth (PLG)**
- Identificar "aha moments" (primeira ação que prediz retenção)
- Exemplo: Usuários que fazem ≥5 API requests na primeira semana têm 3x mais retenção

**Feature Adoption**
- Medir % de usuários que adotam novas features
- Correlacionar uso de features com churn
- Exemplo: Usuários que usam "Team Collaboration" têm 50% menos churn

**Otimização de Onboarding**
- Análise de funil para identificar drop-offs
- Exemplo: 40% dos usuários abandonam em "Payment Information" → simplificar checkout

**Segmentação Comportamental**
- Criar segmentos baseados em ações (power users, at-risk users)
- Exemplo: Power Users = usuários com >100 eventos/semana

#### 4.2.4 Mixpanel vs. Google Analytics

| Aspecto | Google Analytics | Mixpanel |
|---------|------------------|----------|
| **Foco** | Web analytics (tráfego, SEO) | Product analytics (in-app behavior) |
| **Modelo de Dados** | Session-based | Event-based |
| **Rastreamento** | Pageviews + eventos | Eventos granulares |
| **User Tracking** | Anonymous cookies | Identified users |
| **Análise de Produto** | Limitado | Avançado (funis, retenção, coortes) |
| **Pricing** | Grátis (até 10M hits/mês) | Grátis até 20M events/mês, depois pago |
| **Ideal Para** | Websites, blogs, e-commerce | SaaS, mobile apps, produtos digitais |

### 4.3 Power BI

Power BI é uma plataforma de business intelligence da Microsoft focada em visualização de dados, criação de dashboards interativos e análise empresarial.

#### 4.3.1 Funcionalidades Principais

**Integração com Múltiplas Fontes**
- Conectores nativos: SQL Server, PostgreSQL, MySQL, Oracle, Salesforce, Google Analytics, APIs REST
- Combinar dados de fontes heterogêneas em modelos unificados

**Modelagem de Dados**
- Relacionamentos entre tabelas (star schema, snowflake schema)
- DAX (Data Analysis Expressions) para cálculos customizados
- Medidas calculadas, colunas calculadas, tabelas calculadas

**Visualizações Interativas**
- 30+ tipos de gráficos (barras, linhas, mapas, treemaps, scatter plots)
- Dashboards interativos com drill-down e filtros cross-visual
- Custom visuals (marketplace com centenas de visualizações)

**Análise Preditiva**
- Integração com R e Python para machine learning
- Quick Insights (detecção automática de padrões)
- Forecasting com séries temporais

**Colaboração e Compartilhamento**
- Power BI Service (cloud) para compartilhar relatórios
- Controle de acesso granular (RLS - Row-Level Security)
- Embedded analytics (iframe em aplicações web)

#### 4.3.2 Implementação Técnica

**Conexão com Banco de Dados**
```sql
-- Exemplo: Consulta SQL customizada no Power BI
SELECT
    u.user_id,
    u.email,
    u.signup_date,
    u.plan,
    COUNT(DISTINCT e.event_id) as total_events,
    SUM(CASE WHEN e.event_type = 'api_request' THEN 1 ELSE 0 END) as api_requests,
    MAX(e.event_timestamp) as last_activity
FROM users u
LEFT JOIN events e ON u.user_id = e.user_id
WHERE u.signup_date >= DATEADD(month, -3, GETDATE())
GROUP BY u.user_id, u.email, u.signup_date, u.plan;
```

**DAX para Métricas Calculadas**
```dax
// Medida: MRR (Monthly Recurring Revenue)
MRR =
SUMX(
    FILTER(
        subscriptions,
        subscriptions[status] = "active"
    ),
    subscriptions[amount]
)

// Medida: Churn Rate
Churn Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS(subscriptions),
        subscriptions[status] = "cancelled"
    ),
    CALCULATE(
        COUNTROWS(subscriptions),
        subscriptions[status] = "active",
        PREVIOUSMONTH(subscriptions[start_date])
    )
)

// Medida: LTV (Lifetime Value)
LTV =
DIVIDE(
    [MRR] * [Gross Margin],
    [Churn Rate]
)

// Coluna calculada: Tenure (dias desde signup)
Tenure Days =
DATEDIFF(
    users[signup_date],
    TODAY(),
    DAY
)
```

**Modelo de Dados (Star Schema)**
```
Fact Table: subscriptions
- subscription_id
- user_id (FK)
- plan_id (FK)
- start_date (FK to date_dim)
- amount
- status

Dimension Table: users
- user_id (PK)
- email
- signup_date
- country

Dimension Table: plans
- plan_id (PK)
- plan_name
- billing_cycle

Dimension Table: date_dim
- date (PK)
- year
- quarter
- month
- week
```

#### 4.3.3 Casos de Uso para Desenvolvedores

**Executive Dashboards**
- KPIs de alto nível para C-level (MRR, growth rate, churn)
- Drill-down de MRR por segmento de cliente
- Exemplo: Dashboard com cards de MRR, MRR growth MoM, churn rate, NPS

**Análise de Performance de APIs**
- Latência P50/P95/P99 por endpoint
- Taxa de erro por versão de API
- Exemplo: Mapa de calor mostrando endpoints mais lentos por horário do dia

**Product Analytics Warehouse**
- Combinar dados de Mixpanel (eventos) + PostgreSQL (transações) + Stripe (receita)
- Análise unificada de comportamento → conversão → receita
- Exemplo: Correlacionar uso de features (Mixpanel) com expansão de receita (Stripe)

**Operacional - SLA Monitoring**
- Dashboards de uptime, latência, error rate
- Alertas quando SLA é violado (ex: uptime <99.9%)
- Exemplo: Dashboard ops com métricas de infraestrutura (CPU, memória, latência)

#### 4.3.4 Power BI Service (Cloud) vs. Power BI Desktop

| Aspecto | Power BI Desktop | Power BI Service |
|---------|------------------|------------------|
| **Tipo** | Aplicação Windows | Web app (cloud) |
| **Uso** | Criar e modelar relatórios | Compartilhar e colaborar |
| **Colaboração** | Não | Sim (workspaces, apps) |
| **Atualização de Dados** | Manual | Scheduled refresh (até 8x/dia) |
| **Acesso** | Local | Anywhere (browser, mobile) |
| **Pricing** | Grátis | Grátis (limitado) ou Pro ($10/user/mês) |

#### 4.3.5 Boas Práticas para Desenvolvedores

**Otimização de Performance**
- Usar DirectQuery para datasets grandes (>1GB)
- Implementar aggregations para acelerar queries
- Reduzir cardinalidade de colunas (ex: agrupar timestamps por hora)

**Versionamento de Relatórios**
- Salvar arquivos .pbix em Git
- Usar deployment pipelines (Dev → QA → Prod)

**Row-Level Security (RLS)**
```dax
// Regra RLS: Usuários veem apenas dados de seu país
[Country] = USERPRINCIPALNAME()
```

**Embedded Analytics**
```html
<!-- Embed Power BI em aplicação web -->
<iframe
  width="800"
  height="600"
  src="https://app.powerbi.com/reportEmbed?reportId=xxx&groupId=yyy"
  frameborder="0"
  allowFullScreen="true">
</iframe>
```

### 4.4 Comparação de Ferramentas

| Aspecto | Google Analytics | Mixpanel | Power BI |
|---------|------------------|----------|----------|
| **Foco Principal** | Web analytics | Product analytics | Business intelligence |
| **Tipo de Dados** | Sessões, pageviews | Eventos, usuários | Qualquer (SQL, APIs, files) |
| **Granularidade** | Baixa (session-based) | Alta (event-based) | Customizável |
| **Visualizações** | Limitadas | Médio (funis, retenção) | Avançadas (30+ tipos) |
| **Análise Técnica** | Básica | Avançada (coortes, A/B) | Muito avançada (DAX, ML) |
| **Integração de Dados** | Limitada (GA + Google Ads) | Moderada (webhooks, APIs) | Ampla (100+ conectores) |
| **Pricing** | Grátis (GA4) | Freemium ($0-$999+/mês) | Freemium ($0-$20/user/mês) |
| **Curva de Aprendizado** | Baixa | Média | Alta |
| **Ideal Para** | Websites, SEO, marketing | SaaS, mobile apps, PLG | Dashboards corporativos, BI |

### 4.5 Stack de Analytics Moderno

Para produtos digitais maduros, a stack típica combina múltiplas ferramentas:

**Camada de Coleta**
- Segment ou RudderStack (Customer Data Platform)
- Envia eventos para múltiplos destinos (Mixpanel, GA, data warehouse)

**Camada de Armazenamento**
- Data warehouse (Snowflake, BigQuery, Redshift)
- Consolida dados de produto, marketing, vendas, suporte

**Camada de Transformação**
- dbt (data build tool)
- Transforma dados brutos em modelos analíticos (ex: tabelas de métricas)

**Camada de Visualização**
- Power BI, Looker ou Metabase para dashboards
- Mixpanel ou Amplitude para product analytics

**Camada de Ativação**
- Reverse ETL (Census, Hightouch)
- Envia insights de data warehouse de volta para ferramentas operacionais (Salesforce, Intercom)

**Exemplo de Arquitetura**:
```
User Actions (Web/Mobile)
  ↓
Segment (CDP)
  ↓
  ├─→ Mixpanel (Product Analytics)
  ├─→ Google Analytics (Web Analytics)
  ├─→ Snowflake (Data Warehouse)
       ↓
       dbt (Transform)
       ↓
       Power BI (Dashboards)
       ↓
       Census (Reverse ETL)
       ↓
       Salesforce (CRM - Enriquecer leads com product usage)
```

## 5. Ajustes de Estratégia com Base em Feedback e Métricas

### 5.1 Fundamentos de Ajustes Estratégicos

Ajustar estratégia com base em dados é a capacidade de modificar táticas, features ou roadmap em resposta a evidências quantitativas (métricas) e qualitativas (feedback). Diferencia-se de "perseguir números" por manter visão de longo prazo enquanto adapta execução de curto prazo.

#### 5.1.1 Por Que Ajustar Estratégias?

**Melhoria Contínua**
- Produtos digitais nunca estão "prontos" — requerem otimização iterativa
- Exemplo: Amazon faz deploys a cada 11 segundos, testando milhares de experimentos/ano

**Alinhamento com Usuário**
- Comportamento real difere de suposições iniciais
- Exemplo: Feature de "compartilhamento social" tem <1% uso → descartar e focar em APIs

**Redução de Riscos**
- Detectar problemas antes que escalem
- Exemplo: Aumento de 10% em churn rate sinaliza necessidade de investigação urgente

**Maximização de Resultados**
- Realocar recursos de iniciativas de baixo impacto para alto impacto
- Exemplo: Feature A tem 5% adoption, Feature B tem 40% → investir mais em B

#### 5.1.2 Framework de Ajustes Estratégicos

**1. Definir Objetivos Claros**
- Estabelecer KPIs de sucesso antes de lançar iniciativas
- Exemplo: "Feature de exportação deve ter ≥20% adoption em 30 dias"

**2. Coletar Feedback Qualitativo e Quantitativo**
- Quantitativo: Métricas de produto (analytics)
- Qualitativo: Entrevistas, surveys, tickets de suporte

**3. Analisar Dados e Identificar Insights**
- Correlacionar métricas (ex: uso de feature X → aumento de retenção)
- Identificar padrões (ex: usuários mobile abandonam mais que desktop)

**4. Priorizar Ajustes com Maior Impacto**
- Frameworks: RICE, matriz impacto-esforço
- Focar em quick wins (alto impacto, baixo esforço)

**5. Implementar Mudanças**
- Rollout gradual (feature flags, canary releases)
- Monitorar métricas em tempo real

**6. Iterar para Melhoria Contínua**
- Ciclo semanal ou quinzenal de revisão de métricas
- Exemplo: Ritual semanal de "Metrics Review" com equipe de produto

### 5.2 Coleta de Feedback

#### 5.2.1 Feedback Quantitativo

**In-App Surveys (NPS, CSAT)**
```html
<!-- Exemplo com Hotjar -->
<script>
    (function(h,o,t,j,a,r){
        h.hj=h.hj||function(){(h.hj.q=h.hj.q||[]).push(arguments)};
        h._hjSettings={hjid:YOUR_ID,hjsv:6};
        a=o.getElementsByTagName('head')[0];
        r=o.createElement('script');r.async=1;
        r.src=t+h._hjSettings.hjid+j+h._hjSettings.hjsv;
        a.appendChild(r);
    })(window,document,'https://static.hotjar.com/c/hotjar-','.js?sv=');
</script>
```

**Análise de Comportamento (Heatmaps, Session Recordings)**
- Ferramentas: Hotjar, FullStory, LogRocket
- Identificar padrões de uso e fricção
- Exemplo: Heatmap mostra que 80% dos usuários não veem botão "Export" → mover para posição mais visível

**Métricas de Produto**
- Analytics (Mixpanel, Amplitude)
- Exemplo: Funnel analysis revela que 60% abandonam no passo 3 de onboarding

#### 5.2.2 Feedback Qualitativo

**Entrevistas com Usuários**
- Conduzir 5-10 entrevistas por sprint
- Perguntas abertas: "O que te frustrou ao usar X?"
- Exemplo: Descobrir que desenvolvedores querem API docs interativas

**Surveys de Satisfação**
```javascript
// Exemplo com Typeform embedded
<div data-tf-widget="YOUR_FORM_ID" style="width:100%;height:500px;"></div>
<script src="//embed.typeform.com/next/embed.js"></script>
```

**Análise de Tickets de Suporte**
- Categorizar tickets por tema (bugs, feature requests, UX)
- Exemplo: 30% dos tickets são sobre "como exportar dados" → criar guia passo-a-passo

**User Testing (Moderated/Unmoderated)**
- Ferramentas: UserTesting.com, Maze, Lookback
- Observar usuários completando tarefas
- Exemplo: 70% dos usuários falham em encontrar feature de "Bulk Edit" → redesenhar navegação

### 5.3 Análise e Insights

#### 5.3.1 Análise de Coortes

Análise de coortes agrupa usuários por característica comum (data de signup, fonte de aquisição) e rastreia comportamento ao longo do tempo.

**Exemplo Prático - Retenção por Coorte de Signup**

```sql
-- Cohort Retention Analysis (PostgreSQL)
WITH cohorts AS (
  SELECT
    user_id,
    DATE_TRUNC('month', signup_date) AS cohort_month
  FROM users
),
user_activities AS (
  SELECT
    user_id,
    DATE_TRUNC('month', activity_date) AS activity_month
  FROM user_events
  WHERE event_type = 'login'
)
SELECT
  c.cohort_month,
  a.activity_month,
  COUNT(DISTINCT a.user_id) AS active_users,
  COUNT(DISTINCT c.user_id) AS cohort_size,
  ROUND(100.0 * COUNT(DISTINCT a.user_id) / COUNT(DISTINCT c.user_id), 2) AS retention_rate
FROM cohorts c
LEFT JOIN user_activities a ON c.user_id = a.user_id
GROUP BY c.cohort_month, a.activity_month
ORDER BY c.cohort_month, a.activity_month;
```

**Output**:
```
cohort_month | activity_month | active_users | cohort_size | retention_rate
-------------|----------------|--------------|-------------|---------------
2025-07-01   | 2025-07-01     | 1000         | 1000        | 100.00 (M0)
2025-07-01   | 2025-08-01     | 400          | 1000        | 40.00 (M1)
2025-07-01   | 2025-09-01     | 250          | 1000        | 25.00 (M2)
2025-07-01   | 2025-10-01     | 200          | 1000        | 20.00 (M3)
```

**Insight**: Retenção estabiliza em ~20% após M3 → focar em melhorar M1 retention (40% → 50%)

#### 5.3.2 Análise de Funil

**Exemplo Prático - Funil de Conversão de Trial para Pago**

```sql
-- Funnel Analysis (PostgreSQL)
WITH funnel_steps AS (
  SELECT
    user_id,
    MAX(CASE WHEN event_type = 'trial_started' THEN 1 ELSE 0 END) AS started_trial,
    MAX(CASE WHEN event_type = 'feature_used' THEN 1 ELSE 0 END) AS used_feature,
    MAX(CASE WHEN event_type = 'billing_info_added' THEN 1 ELSE 0 END) AS added_billing,
    MAX(CASE WHEN event_type = 'subscription_created' THEN 1 ELSE 0 END) AS converted
  FROM user_events
  WHERE event_date >= CURRENT_DATE - INTERVAL '30 days'
  GROUP BY user_id
)
SELECT
  SUM(started_trial) AS step1_trial_started,
  SUM(used_feature) AS step2_used_feature,
  SUM(added_billing) AS step3_added_billing,
  SUM(converted) AS step4_converted,
  ROUND(100.0 * SUM(used_feature) / SUM(started_trial), 2) AS conversion_1to2,
  ROUND(100.0 * SUM(added_billing) / SUM(used_feature), 2) AS conversion_2to3,
  ROUND(100.0 * SUM(converted) / SUM(added_billing), 2) AS conversion_3to4
FROM funnel_steps;
```

**Output**:
```
step1 | step2 | step3 | step4 | conv_1to2 | conv_2to3 | conv_3to4
------|-------|-------|-------|-----------|-----------|----------
1000  | 700   | 350   | 280   | 70.00%    | 50.00%    | 80.00%
```

**Insight**: Maior drop-off entre step2 e step3 (50%) → investigar fricção em processo de adicionar billing

**Ação**:
- Entrevistas qualitativas com usuários que abandonaram no step2
- Descobrir: Usuários não confiam em adicionar cartão antes de testar produto
- Solução: Mover "adicionar billing" para depois de 7 dias de trial

#### 5.3.3 Análise de Correlação

**Exemplo Prático - Correlação entre Uso de Features e Retenção**

```python
import pandas as pd
from scipy.stats import pearsonr

# Carregar dados
df = pd.read_sql("""
  SELECT
    u.user_id,
    u.retained_30d,
    COUNT(DISTINCT CASE WHEN e.event_type = 'api_request' THEN e.event_id END) AS api_requests,
    COUNT(DISTINCT CASE WHEN e.event_type = 'dashboard_view' THEN e.event_id END) AS dashboard_views,
    COUNT(DISTINCT CASE WHEN e.event_type = 'export_data' THEN e.event_id END) AS exports
  FROM users u
  LEFT JOIN events e ON u.user_id = e.user_id AND e.event_date < u.signup_date + INTERVAL '7 days'
  WHERE u.signup_date >= CURRENT_DATE - INTERVAL '60 days'
  GROUP BY u.user_id, u.retained_30d
""", db_connection)

# Calcular correlações
features = ['api_requests', 'dashboard_views', 'exports']
for feature in features:
    correlation, p_value = pearsonr(df[feature], df['retained_30d'])
    print(f"{feature}: r={correlation:.3f}, p={p_value:.4f}")
```

**Output**:
```
api_requests: r=0.68, p=0.0001 ✅ Forte correlação positiva
dashboard_views: r=0.22, p=0.0450 ⚠️ Fraca correlação
exports: r=0.45, p=0.0020 ✅ Moderada correlação
```

**Insight**: Uso de API nos primeiros 7 dias é o maior preditor de retenção → focar onboarding em fazer primeira API request

**Ação**:
- Criar tutorial interativo "First API Request in 5 Minutes"
- Enviar email no D2 se usuário ainda não fez API request

### 5.4 Priorização de Ajustes

#### 5.4.1 Framework RICE para Priorização

RICE = Reach × Impact × Confidence / Effort

**Reach (Alcance)**: Quantas pessoas serão afetadas por trimestre
**Impact (Impacto)**: Quanto vai melhorar a experiência (escala: 0.25 = mínimo, 3 = massivo)
**Confidence (Confiança)**: Quão certos estamos do impacto (escala: 50% = baixa, 100% = alta)
**Effort (Esforço)**: Pessoas-mês necessários

**Exemplo Prático**:

| Iniciativa | Reach | Impact | Confidence | Effort | RICE Score |
|------------|-------|--------|------------|--------|------------|
| Otimizar performance de API (reduzir P95 de 500ms→200ms) | 10000 | 2.0 | 80% | 2 | 8000 |
| Adicionar dark mode | 10000 | 0.5 | 90% | 1 | 4500 |
| Criar onboarding interativo | 2000 | 3.0 | 70% | 3 | 1400 |
| Integração com Slack | 500 | 1.5 | 60% | 4 | 112.5 |

**Priorização**: 1) Otimizar API, 2) Dark mode, 3) Onboarding, 4) Integração Slack

#### 5.4.2 Matriz Impacto-Esforço

| Impacto ↑ | Alto Esforço | Baixo Esforço |
|-----------|--------------|---------------|
| **Alto Impacto** | Major Projects (Planejar) | Quick Wins (Fazer AGORA) |
| **Baixo Impacto** | Thankless Tasks (Evitar) | Fill-Ins (Fazer se sobrar tempo) |

**Exemplo**:
- **Quick Wins**: Adicionar loading states em botões (alto impacto UX, 2h de esforço)
- **Major Projects**: Reescrever arquitetura de autenticação (alto impacto, 3 meses)
- **Fill-Ins**: Adicionar easter egg (baixo impacto, 1h)
- **Thankless Tasks**: Refatorar código legado não-crítico (baixo impacto, 2 semanas)

### 5.5 Implementação e Monitoramento

#### 5.5.1 Rollout Gradual com Feature Flags

```typescript
// Exemplo com LaunchDarkly
import * as LaunchDarkly from 'launchdarkly-node-server-sdk';

const ldClient = LaunchDarkly.init(process.env.LD_SDK_KEY);

async function getCheckoutFlow(userId: string, userPlan: string) {
  const user = {
    key: userId,
    custom: { plan: userPlan }
  };

  // Rollout: 10% dos usuários Pro veem novo checkout
  const useNewCheckout = await ldClient.variation(
    'new-checkout-flow',
    user,
    false
  );

  if (useNewCheckout) {
    return renderNewCheckout();
  } else {
    return renderLegacyCheckout();
  }
}
```

**Estratégia de Rollout**:
1. **0-5%**: Internal dogfooding (equipe interna)
2. **5-25%**: Early adopters (usuários que optaram por beta)
3. **25-50%**: Monitorar métricas críticas (conversão, error rate)
4. **50-100%**: Rollout completo se métricas são positivas

#### 5.5.2 Monitoramento em Tempo Real

**Configurar Alertas**
```yaml
# Exemplo de alerta (Prometheus + Alertmanager)
groups:
- name: conversion_alerts
  rules:
  - alert: ConversionRateDrop
    expr: |
      (
        sum(rate(checkouts_completed_total[1h]))
        /
        sum(rate(checkouts_started_total[1h]))
      ) < 0.15
    for: 30m
    labels:
      severity: critical
    annotations:
      summary: "Conversion rate dropped below 15%"
      description: "Current rate: {{ $value | humanizePercentage }}"
```

**Dashboard de Métricas-Chave**
- Visualizar KPIs em tempo real (Grafana, Datadog)
- Comparar períodos (hoje vs. semana passada)
- Segmentar por variante de experimento (A/B test)

### 5.6 Casos Práticos de Ajustes Estratégicos

#### 5.6.1 Caso: Simplificação de Checkout

**Contexto**:
- E-commerce SaaS com conversão de trial→pago de 12%
- Funil de checkout com 5 steps

**Dados**:
```
Step 1 (Plan Selection): 100% → Step 2: 85%
Step 2 (Account Info): 85% → Step 3: 70%
Step 3 (Billing Info): 70% → Step 4: 50% ⚠️
Step 4 (Review): 50% → Step 5: 45%
Step 5 (Confirm): 45% → Converted: 42%
```

**Insight**: Maior drop-off no Step 3 (billing info)

**Hipótese**: Pedir cartão cedo demais gera desconfiança

**Ação**: Remover Step 3, permitir trial sem cartão, pedir billing apenas ao final do trial

**Resultado**:
- Conversão trial→pago: 12% → 18% (+50%)
- Churn involuntário (cartão recusado) aumentou ligeiramente, mas net positive

#### 5.6.2 Caso: Otimização de Algoritmo de Recomendação

**Contexto**:
- Plataforma de conteúdo com algoritmo de recomendação baseado em popularidade
- Engagement (tempo de sessão) estagnado em 8min/sessão

**Dados**:
```sql
-- Análise de clickthrough rate por tipo de recomendação
SELECT
  recommendation_type,
  COUNT(*) AS impressions,
  SUM(CASE WHEN clicked = true THEN 1 ELSE 0 END) AS clicks,
  ROUND(100.0 * SUM(CASE WHEN clicked = true THEN 1 ELSE 0 END) / COUNT(*), 2) AS ctr
FROM recommendations
GROUP BY recommendation_type;
```

**Output**:
```
recommendation_type | impressions | clicks | ctr
--------------------|-------------|--------|------
Trending            | 100000      | 8000   | 8.00%
Personalized (ML)   | 20000       | 5000   | 25.00% ✅
```

**Insight**: Recomendações personalizadas (ML) têm 3x melhor CTR, mas só 20% das impressões

**Hipótese**: Aumentar % de recomendações ML vai melhorar engagement

**Ação**: A/B test com 50% das impressões sendo ML-based (vs. 20% no controle)

**Resultado**:
- Tempo médio de sessão: 8min → 12min (+50%)
- Rollout de ML recommendations para 100% dos usuários

#### 5.6.3 Caso: Redução de Churn com Análise Preditiva

**Contexto**:
- SaaS B2B com churn rate de 7% ao mês
- Custo de aquisição (CAC) alto torna churn insustentável

**Dados**:
- Treinar modelo de ML para predizer churn (ver seção 3.2.3)
- Identificar 342 usuários com >70% probabilidade de churn nos próximos 30 dias

**Ação**:
1. Segmentar usuários em risco em 3 grupos:
   - Baixo engajamento (não usam produto)
   - Problemas técnicos (error rate alto)
   - Insatisfação com feature (NPS baixo)
2. Intervenções customizadas:
   - Baixo engajamento → Email com tutorial + oferta de onboarding call
   - Problemas técnicos → Proactive outreach do time de suporte
   - Insatisfação → Product manager faz entrevista para entender pain points

**Resultado**:
- 40% dos usuários em risco foram salvos (137/342)
- Churn rate: 7% → 5.2% (-25%)
- ROI da iniciativa: Economia de $400k/ano em MRR preservado

### 5.7 Ferramentas para Coleta de Feedback

**Surveys e NPS**
- Typeform, SurveyMonkey, Google Forms
- Delighted (especializado em NPS)

**Analytics e Monitoramento**
- Google Analytics, Mixpanel, Amplitude (comportamento)
- Datadog, New Relic (performance técnica)
- Sentry, Rollbar (error tracking)

**Session Recording e Heatmaps**
- Hotjar, FullStory, LogRocket
- Identifica fricção em UX através de gravações de sessões

**User Testing**
- UserTesting.com (moderated testing)
- Maze (unmoderated testing com protótipos Figma)

**Feedback Direto**
- Intercom, Zendesk (tickets de suporte como fonte de feedback)
- ProductBoard (agregador de feedback de múltiplas fontes)

## 6. Conclusões

### 6.1 Síntese dos Conceitos

A gestão baseada em métricas e análise de dados representa uma mudança fundamental no desenvolvimento de produtos digitais, transformando decisões de intuitivas para evidenciadas. Para desenvolvedores, dominar esses conceitos transcende habilidades técnicas de instrumentação de código, permitindo contribuir estrategicamente para o sucesso do produto através de insights baseados em dados.

**OKRs e KPIs** fornecem clareza sobre o que deve ser alcançado e como medir sucesso, conectando trabalho técnico diário a objetivos de negócio. **Análise de dados** estrutura o processo de transformar informação bruta em insights acionáveis através de análise descritiva (o que aconteceu), diagnóstica (por que aconteceu), preditiva (o que pode acontecer) e prescritiva (o que fazer). **Ferramentas de analytics** como Google Analytics, Mixpanel e Power BI capacitam equipes a monitorar comportamento de usuários, performance técnica e saúde de negócio em tempo real. **Ajustes estratégicos** baseados em feedback contínuo garantem que produtos evoluam em resposta a necessidades reais, maximizando retorno sobre investimento e satisfação do usuário.

### 6.2 Principais Takeaways para Desenvolvedores

**1. Métricas são Parte Essencial do Código**
- Instrumentação de eventos, logs e traces não é "nice-to-have" — é requisito de produto
- Código sem métricas é código sem visibilidade de impacto

**2. Dados Conectam Código a Valor de Negócio**
- Feature bem implementada mas não usada é desperdício de recursos
- Métricas de adoção e impacto justificam investimentos técnicos

**3. Cultura Data-Informed Reduz Riscos**
- Decisões baseadas em evidências têm maior taxa de sucesso
- Experimentos estruturados (A/B tests) permitem validar hipóteses antes de rollouts completos

**4. Desenvolvedores Devem Participar de Decisões de Produto**
- Compreender métricas permite questionar requisitos e propor soluções técnicas
- Perspectiva técnica é essencial para definir OKRs realistas

**5. Ciclos Rápidos de Feedback Aceleram Aprendizado**
- Deploy contínuo + monitoramento em tempo real permite iterar rapidamente
- Cultura de experimentação requer infraestrutura técnica adequada (feature flags, observabilidade)

### 6.3 Implementação Prática

Para desenvolvedores que desejam incorporar gestão baseada em métricas em seu fluxo de trabalho:

**Curto Prazo (1-2 semanas)**
1. Instrumentar eventos-chave de produto (signup, feature usage, conversões)
2. Configurar dashboard básico com KPIs de saúde técnica (uptime, latency, error rate)
3. Participar de ritual semanal de revisão de métricas com equipe de produto

**Médio Prazo (1-3 meses)**
1. Implementar análise de funis para features críticas
2. Configurar alertas para métricas de negócio (ex: queda de conversão)
3. Conduzir A/B test para validar hipótese de otimização

**Longo Prazo (3-12 meses)**
1. Construir infraestrutura de data warehouse para analytics avançado
2. Implementar machine learning para análise preditiva (churn, LTV)
3. Estabelecer cultura de experimentação contínua com dezenas de testes paralelos

### 6.4 Métricas Essenciais para Monitorar

**Product Health**
- DAU/MAU (Stickiness): Mede uso frequente
- Retention (D1, D7, D30): Capacidade de manter usuários
- NPS: Satisfação e propensão a recomendar

**Business Health**
- MRR: Receita recorrente mensal
- Churn Rate: Taxa de cancelamento
- LTV/CAC Ratio: Eficiência de aquisição

**Technical Health**
- Uptime: Disponibilidade do serviço
- Latency P95: Performance percebida
- Error Rate: Confiabilidade técnica

### 6.5 Considerações Finais

Métricas e análise de dados não substituem visão de produto, criatividade ou empatia com usuários — complementam. O objetivo não é criar cultura obcecada por números, mas cultura que equilibra evidências quantitativas com insights qualitativos para tomar decisões informadas.

Desenvolvedores que compreendem o impacto mensurável de seu código, questionam requisitos baseados em dados, e contribuem para experimentação contínua tornam-se parceiros estratégicos essenciais para o sucesso de produtos digitais. Em um mercado cada vez mais competitivo, a capacidade de conectar excelência técnica a resultados de negócio mensuráveis é diferencial crítico para carreira e para construção de produtos que geram valor real aos usuários.

## 7. Referências Bibliográficas

DAVENPORT, Thomas H.; HARRIS, Jeanne G. **Competing on Analytics: The New Science of Winning**. Harvard Business Review Press, 2007.

DOERR, John. **Measure What Matters: How Google, Bono, and the Gates Foundation Rock the World with OKRs**. Portfolio/Penguin, 2018.

RIES, Eric. **The Lean Startup: How Today's Entrepreneurs Use Continuous Innovation to Create Radically Successful Businesses**. Crown Business, 2011.

CROLL, Alistair; YOSKOVITZ, Benjamin. **Lean Analytics: Use Data to Build a Better Startup Faster**. O'Reilly Media, 2013.

EISENMANN, Thomas; RIES, Eric; DILLARD, Sarah. **Hypothesis-Driven Entrepreneurship: The Lean Startup**. Harvard Business School Case, 2013.

KAUSHIK, Avinash. **Web Analytics 2.0: The Art of Online Accountability and Science of Customer Centricity**. Sybex, 2009.

KOHAVI, Ron; TANG, Diane; XU, Ya. **Trustworthy Online Controlled Experiments: A Practical Guide to A/B Testing**. Cambridge University Press, 2020.

MARR, Bernard. **Key Performance Indicators (KPI): The 75 Measures Every Manager Needs to Know**. Pearson Education, 2012.

PROVOST, Foster; FAWCETT, Tom. **Data Science for Business: What You Need to Know about Data Mining and Data-Analytic Thinking**. O'Reilly Media, 2013.

AMPLITUDE. **The North Star Playbook**. Disponível em: https://amplitude.com/north-star. Acesso em: 2025.

MIXPANEL. **Product Analytics Guide**. Disponível em: https://mixpanel.com/content/guide/product-analytics. Acesso em: 2025.

GOOGLE. **Google Analytics 4 Documentation**. Disponível em: https://support.google.com/analytics. Acesso em: 2025.

MICROSOFT. **Power BI Documentation**. Disponível em: https://docs.microsoft.com/en-us/power-bi. Acesso em: 2025.

SEGMENT. **The Customer Data Platform Guide**. Disponível em: https://segment.com/resources. Acesso em: 2025.

## 8. Apêndices

### Apêndice A: Templates e Frameworks

#### A.1 Template de OKRs

```markdown
## Q4 2025 OKRs - Engineering Team

### Objective 1: Tornar nossa plataforma a mais rápida e confiável do mercado

**Key Results:**
- KR1: Reduzir latência P95 de APIs de 500ms para 200ms
  - Baseline: 500ms (medido em 2025-10-01)
  - Target: 200ms
  - Métrica: Prometheus query: `histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m]))`

- KR2: Aumentar uptime de 99.5% para 99.95%
  - Baseline: 99.5% (avg últimos 3 meses)
  - Target: 99.95%
  - Métrica: `(total_time - downtime) / total_time`

- KR3: Reduzir taxa de erros 5xx de 0.5% para 0.1%
  - Baseline: 0.5%
  - Target: 0.1%
  - Métrica: `(5xx_errors / total_requests) * 100`

**Iniciativas:**
- Implementar caching em Redis para queries frequentes
- Migrar banco de dados para instâncias otimizadas
- Configurar load balancing com health checks
- Implementar circuit breakers para serviços externos
```

#### A.2 Template de Análise de Métrica

```markdown
## Análise: Queda de Conversão em Checkout

**Data**: 2025-11-09
**Analista**: [Nome]

### 1. Observação
- **Métrica**: Conversion rate (checkout started → completed)
- **Período**: Semana de 2025-11-01 a 2025-11-08
- **Anomalia**: Queda de 25% para 15% (-40%)

### 2. Segmentação
| Segmento | Baseline (Oct) | Atual (Nov) | Variação |
|----------|----------------|-------------|----------|
| Overall  | 25%            | 15%         | -40% ⚠️  |
| Desktop  | 28%            | 26%         | -7%      |
| Mobile   | 22%            | 8%          | -64% ⚠️⚠️ |

### 3. Hipóteses
- H1: Bug técnico em checkout mobile
- H2: Mudança em UI confundiu usuários mobile
- H3: Aumento em tráfego de baixa qualidade (bots, ads)

### 4. Investigação
- **Logs de erro**: Aumento de 300% em erro "Payment method validation failed" no mobile
- **Commits recentes**: Deploy de v2.3 em 2025-10-30 refatorou validação de cartão
- **User testing**: 5/5 usuários mobile falharam em submit de form

### 5. Root Cause
Bug em validação de cartão no mobile Safari (regex incompatível)

### 6. Ação
- Rollback de v2.3 (imediato)
- Fix de validação com testes cross-browser
- Deploy de v2.3.1 com fix

### 7. Resultado
- Conversion rate mobile: 8% → 22% (recuperado)
- Tempo de resolução: 6 horas
```

#### A.3 Template de Experimento A/B

```markdown
## Experimento: Novo Onboarding Interativo

**Hipótese**: Onboarding interativo aumentará activation rate de 40% para 55%

### Configuração
- **Métrica Primária**: Activation rate (completar onboarding)
- **Métricas Secundárias**:
  - Time to first value
  - D7 retention
- **Variantes**:
  - Control: Onboarding atual (tutorial estático)
  - Treatment: Onboarding interativo (passo-a-passo guiado)
- **Tráfego**: 50/50 split
- **Duração**: 14 dias
- **Sample Size**: 2000 usuários (1000 por variante)
- **Statistical Significance**: 95% confidence level

### Critérios de Sucesso
- Activation rate aumenta ≥10pp (40% → 50%+)
- Nenhuma degradação em métricas secundárias

### Implementação
```typescript
const variant = await ldClient.variation('new-onboarding', user, 'control');
if (variant === 'treatment') {
  return <InteractiveOnboarding />;
} else {
  return <LegacyOnboarding />;
}
```

### Resultados
| Métrica | Control | Treatment | Lift | P-value |
|---------|---------|-----------|------|---------|
| Activation Rate | 40% | 58% | +45% | <0.001 ✅ |
| Time to First Value | 5min | 2.5min | -50% | <0.001 ✅ |
| D7 Retention | 35% | 42% | +20% | 0.02 ✅ |

### Decisão
✅ Rollout de treatment para 100% dos usuários
```

### Apêndice B: Queries SQL Úteis

#### B.1 Análise de Retenção (Cohort Analysis)

```sql
-- Cohort Retention Analysis (PostgreSQL)
WITH cohorts AS (
  SELECT
    user_id,
    DATE_TRUNC('month', signup_date) AS cohort_month
  FROM users
),
user_activities AS (
  SELECT
    user_id,
    DATE_TRUNC('month', activity_date) AS activity_month
  FROM user_events
  WHERE event_type IN ('login', 'api_request')
  GROUP BY user_id, DATE_TRUNC('month', activity_date)
)
SELECT
  c.cohort_month,
  DATE_PART('month', AGE(a.activity_month, c.cohort_month)) AS months_since_signup,
  COUNT(DISTINCT a.user_id) AS active_users,
  COUNT(DISTINCT c.user_id) AS cohort_size,
  ROUND(100.0 * COUNT(DISTINCT a.user_id) /
    (SELECT COUNT(*) FROM cohorts c2 WHERE c2.cohort_month = c.cohort_month), 2
  ) AS retention_rate
FROM cohorts c
LEFT JOIN user_activities a ON c.user_id = a.user_id
GROUP BY c.cohort_month, months_since_signup
ORDER BY c.cohort_month, months_since_signup;
```

#### B.2 Análise de Funil

```sql
-- Funnel Analysis with Drop-off Rates
WITH funnel AS (
  SELECT
    user_id,
    MAX(CASE WHEN event_type = 'signup' THEN 1 ELSE 0 END) AS step1_signup,
    MAX(CASE WHEN event_type = 'email_verified' THEN 1 ELSE 0 END) AS step2_verified,
    MAX(CASE WHEN event_type = 'profile_completed' THEN 1 ELSE 0 END) AS step3_profile,
    MAX(CASE WHEN event_type = 'first_api_request' THEN 1 ELSE 0 END) AS step4_activated
  FROM user_events
  WHERE event_date >= CURRENT_DATE - INTERVAL '30 days'
  GROUP BY user_id
)
SELECT
  'Step 1: Signup' AS step,
  SUM(step1_signup) AS users,
  100.0 AS completion_rate,
  0.0 AS drop_off_rate
FROM funnel
UNION ALL
SELECT
  'Step 2: Email Verified',
  SUM(step2_verified),
  ROUND(100.0 * SUM(step2_verified) / NULLIF(SUM(step1_signup), 0), 2),
  ROUND(100.0 * (1 - SUM(step2_verified)::decimal / NULLIF(SUM(step1_signup), 0)), 2)
FROM funnel
UNION ALL
SELECT
  'Step 3: Profile Completed',
  SUM(step3_profile),
  ROUND(100.0 * SUM(step3_profile) / NULLIF(SUM(step2_verified), 0), 2),
  ROUND(100.0 * (1 - SUM(step3_profile)::decimal / NULLIF(SUM(step2_verified), 0)), 2)
FROM funnel
UNION ALL
SELECT
  'Step 4: First API Request',
  SUM(step4_activated),
  ROUND(100.0 * SUM(step4_activated) / NULLIF(SUM(step3_profile), 0), 2),
  ROUND(100.0 * (1 - SUM(step4_activated)::decimal / NULLIF(SUM(step3_profile), 0)), 2)
FROM funnel;
```

#### B.3 Cálculo de LTV e Churn

```sql
-- LTV (Lifetime Value) e Churn por Cohort
WITH monthly_cohorts AS (
  SELECT
    DATE_TRUNC('month', signup_date) AS cohort_month,
    COUNT(*) AS cohort_size,
    AVG(mrr) AS avg_mrr
  FROM users
  WHERE plan_type != 'free'
  GROUP BY cohort_month
),
churned_users AS (
  SELECT
    DATE_TRUNC('month', u.signup_date) AS cohort_month,
    COUNT(*) AS churned_count
  FROM users u
  WHERE u.churned_at IS NOT NULL
  GROUP BY cohort_month
)
SELECT
  mc.cohort_month,
  mc.cohort_size,
  mc.avg_mrr,
  COALESCE(cu.churned_count, 0) AS churned_users,
  ROUND(100.0 * COALESCE(cu.churned_count, 0) / mc.cohort_size, 2) AS churn_rate,
  ROUND(mc.avg_mrr / NULLIF(COALESCE(cu.churned_count, 0)::decimal / mc.cohort_size, 0), 2) AS estimated_ltv
FROM monthly_cohorts mc
LEFT JOIN churned_users cu ON mc.cohort_month = cu.cohort_month
ORDER BY mc.cohort_month DESC;
```

### Apêndice C: Glossário e Termos Técnicos

**A/B Testing**: Experimento controlado que compara duas variantes (A e B) para determinar qual performa melhor em uma métrica específica.

**AARRR (Pirate Metrics)**: Framework de métricas de produto que abrange Acquisition, Activation, Retention, Revenue, Referral.

**Activation Rate**: Percentual de usuários que completam ação-chave que representa "primeira experiência de valor" do produto.

**ARPU (Average Revenue Per User)**: Receita média por usuário, calculada como receita total / número de usuários.

**Benchmark**: Valor de referência usado para comparação (pode ser média da indústria, histórico interno, ou objetivo estratégico).

**Bounce Rate**: Percentual de sessões em que usuário saiu sem interação (métrica de web analytics).

**CAC (Customer Acquisition Cost)**: Custo total de aquisição dividido por número de clientes adquiridos.

**Churn Rate**: Taxa de cancelamento, calculada como usuários cancelados / total de usuários no início do período.

**Cohort Analysis**: Análise que agrupa usuários por característica comum (ex: mês de signup) e rastreia comportamento ao longo do tempo.

**Conversion Rate**: Percentual de usuários que completam ação desejada (ex: visitantes que se tornam clientes).

**CSAT (Customer Satisfaction Score)**: Métrica de satisfação baseada em pergunta "Como você avalia [experiência]?" (escala 1-5).

**DAU (Daily Active Users)**: Número de usuários únicos que usam produto em um dia específico.

**DAX (Data Analysis Expressions)**: Linguagem de fórmulas em Power BI para criar medidas e colunas calculadas.

**ETL (Extract, Transform, Load)**: Processo de extrair dados de fontes, transformá-los e carregá-los em destino (ex: data warehouse).

**Feature Flag**: Técnica de configuração que permite habilitar/desabilitar features em produção sem deploy.

**Funnel Analysis**: Análise de jornada multi-step para identificar drop-offs entre etapas.

**KPI (Key Performance Indicator)**: Métrica quantitativa que avalia sucesso em alcançar objetivos estratégicos.

**LTV (Lifetime Value)**: Valor total que um cliente gera durante relacionamento com empresa, calculado como (ARPU × Margem) / Churn Rate.

**MAU (Monthly Active Users)**: Número de usuários únicos que usam produto em um mês específico.

**MRR (Monthly Recurring Revenue)**: Receita recorrente mensal de todos assinantes ativos.

**NPS (Net Promoter Score)**: Métrica de lealdade calculada como % Promotores (9-10) - % Detratores (0-6).

**North Star Metric**: Métrica única que melhor captura valor central entregue aos clientes.

**OKR (Objectives and Key Results)**: Framework de metas que conecta objetivos qualitativos a resultados-chave mensuráveis.

**P95 (95th Percentile)**: Valor abaixo do qual 95% das observações se encontram (usado para latência, removendo outliers).

**Retention Rate**: Percentual de usuários que continuam ativos após período específico (ex: D7, D30).

**RICE (Reach, Impact, Confidence, Effort)**: Framework de priorização que calcula score como (Reach × Impact × Confidence) / Effort.

**ROI (Return on Investment)**: Retorno sobre investimento, calculado como (Ganho - Custo) / Custo × 100.

**Session**: Conjunto de interações de um usuário em um período (tipicamente 30min de inatividade encerra sessão).

**Stickiness**: Métrica de uso frequente, calculada como DAU / MAU × 100 (produtos sticky têm >20%).

**Time to First Value (TTFV)**: Tempo desde signup até primeira experiência de valor percebido pelo usuário.

**Uptime**: Percentual de tempo que serviço está disponível, calculado como (Total Time - Downtime) / Total Time × 100.