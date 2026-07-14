# Plano: Recuperação de Projeto de Agendamento Médico (2 meses)

## Resumo Executivo

**TL;DR:** Priorizar estabilização da integração com prontuário como bloqueador crítico (Fase 1), reorganizar sprints para proteger as funcionalidades em progresso, implementar gestão rigorosa de requisitos para evitar scope creep, e comunicar trade-offs com stakeholders.

---

## Contexto do Projeto

- **Escopo:** Aplicativo móvel para agendamento de consultas médicas
- **Status:** 50% completo (5/10 funcionalidades prontas, 3 em progresso, 2 não iniciadas)
- **Equipe:** 4 desenvolvedores + 1 tester (fixa)
- **Restrição:** Marco final em 2 meses (não pode ser movido)

### Desafios Identificados

1. **Instabilidade na integração com prontuário** — API confusa/incompleta, mudanças recentes no sistema externo, gerando retrabalho e atrasos
2. **Mudanças de requisitos de stakeholders** — alterações incrementais no fluxo de agendamento, novas validações e regras de negócio
3. **Pressão de recursos** — equipe sobrecarregada, dificuldades para cumprir prazos inicialmente estimados

---

## Estratégia Geral

**Prioridade 1 → 2 → 3:**
1. Estabilizar integração com prontuário (bloqueador crítico)
2. Finalizar funcionalidades em progresso
3. Incorporar novos requisitos incrementalmente + iniciar funcionalidades restantes

---

## Plano de Ação Detalhado

### **Fase 1: Estabilização da Integração (Semanas 1-3)**

#### 1.1 Designar Força-Tarefa de API
- **Alocação:** 2 desenvolvedores + 1 tester em dedicação total à integração prontuário
- **Objetivo:** Eliminar retrabalho e criar confiabilidade comprovada
- **Justificativa:** Bloqueador crítico — sem isso, as fases 2-3 sofrerão atrasos

#### 1.2 Documentar a API do Prontuário
- Analisar código existente de integração para reverter-engenheirar comportamento real
- Solicitar ao sistema externo externo:
  - Lista completa de mudanças recentes
  - Endpoints atualizados e deprecados
  - Erros comuns e limitações
  - Manutenção programada ou downtime esperado
- Criar documento interno com:
  - Casos de uso reais (chamadas da aplicação vs. respostas esperadas)
  - Tratamento de erros por cenário
  - Limites de taxa e timeouts
  - Exemplos de integração correta
- **Entrega:** Documento de referência acessível a todos developers e tester

#### 1.3 Criar Testes de Regressão + Mock do Prontuário
- Implementar testes automatizados que validem cada mudança de versão da API externa
- Setup: ambiente de mock que simula respostas do prontuário
  - Objetivo: não depender de sistema externo instável durante desenvolvimento
  - Cobertura: todos os endpoints críticos (agendamento, consulta, cancelamento, etc.)
- Prioridade: testes das 3 funcionalidades em progresso que dependem da integração
- **Resultado:** Suite de testes rodando em CI/CD com cobertura mínima de 80%

#### 1.4 Validação da Fase 1
- ✅ Integração passou em 100% dos testes de regressão
- ✅ Zero bugs de integração em 1 sprint completo
- ✅ Tempo médio de resposta da API dentro de SLA (ex: <500ms)
- ✅ Documentação atualizada e acessível à equipe

---

### **Fase 2: Finalizar Funcionalidades em Progresso (Semanas 2-6, paralelo com Fase 1)**

#### 2.1 Reorganizar Recursos
- **Força-tarefa integração:** 2 devs + tester (dedicados na Fase 1)
- **Força-tarefa funcionalidades:** 2 devs restantes trabalhando nas 3 features em progresso
  - Opção A: 1 dev por feature (se complexidades similares)
  - Opção B: 2 devs em dupla por feature crítica (se complexidades diferentes)
- **Comunicação:** Alinhamento diário entre as duas forças-tarefa (status bloqueadores)

#### 2.2 Estimar Impacto de Novos Requisitos
- Analisar alterações solicitadas por stakeholders:
  - **Essencial:** incorporar nas sprints das 3 features em progresso (se couber)
  - **Nice-to-have:** alocar para pós-marco final ou v2.0
  - **Crítico:** replanejar se muda escopo significativamente
- Priorizar com stakeholders: qual requisito movê-lo é aceitável se prazos ficarem críticos?

#### 2.3 Executar Sprints com Buffer de Resiliência
- **Velocidade esperada:** 60-70% (contexto com integração instável + mudanças de requisitos)
- **Buffer:** 30-40% para revisões de código, testes, correções de bugs
- **Cadência:** Sprint semanal com reunião de planejamento (seg) e retrospectiva (sex)
- **Métricas:** rastrear velocity real para replanejamento dinâmico

#### 2.4 Validação da Fase 2
- ✅ 3 funcionalidades em progresso concluídas
- ✅ Validadas e testadas pelo tester (testes funcionais + integração)
- ✅ Código revisado e documentado
- ✅ Integração com prontuário estável para essas features

---

### **Fase 3: Funcionalidades Não Iniciadas (Semana 4 em diante)**

#### 3.1 Iniciar as 2 Funcionalidades Restantes
- **Timing:** somente após Fase 1 estar completamente estável + integração prontuário validada
- **Justificativa:** evita perder tempo reescrevendo se integração mudar novamente
- **Alocação:** devs liberados da Fase 2 (após conclusão de cada feature)

#### 3.2 Testes Finais e QA
- Semana 7-8: tester executa testes de regressão completo
- Validar: todas as 10 funcionalidades, fluxos ponta-a-ponta, integração prontuário
- Corrigir bugs críticos e menores

#### 3.3 Validação da Fase 3
- ✅ 10/10 funcionalidades prontas
- ✅ Aplicativo estável em ambiente de teste
- ✅ Documentação atualizada
- ✅ Pronto para entrega

---

## Gestão Contínua (Todas as Fases)

### 4.1 Comunicação com Stakeholders
- **Frequência:** Semanal (ex: toda terça-feira, 10h)
- **Formato:** Status das 3 prioridades
  1. Integração prontuário (estabilidade, documentação)
  2. Features em progresso (completion %)
  3. Novos requisitos (impacto, priorização)
- **Mensagem crítica:** "Quais são os trade-offs aceitáveis se prazos ficarem críticos?"
  - Reduzir escopo de requisitos nice-to-have?
  - Postergar feature específica?
  - Estender deadline em X semanas?
- **Transparência:** compartilhar riscos e mitigações regularmente

### 4.2 Rastreamento de Riscos
- **Risco 1 (CRÍTICO):** Integração prontuário não estabiliza a tempo
  - Impacto: projeto inteiro em risco
  - Mitigação: força-tarefa dedicada desde semana 1 + suporte técnico acionado imediatamente
  - Plano B: contatar suporte do sistema externo em paralelo, preparar fallback manual/parcial
  
- **Risco 2 (ALTO):** Requisitos continuam mudando ao longo do projeto
  - Impacto: scope creep + prazos em risco
  - Mitigação: Change Control Board semanal + stakeholders decidem prioridades
  - Plano B: incorporar apenas "essencial"; nice-to-have vira v2.0
  
- **Risco 3 (MÉDIO):** Equipe não consegue manter velocity esperada (60-70%)
  - Impacto: funcionalidades não terminarão a tempo
  - Mitigação: monitorar velocity diária, realocar se necessário, testes paralelos
  - Plano B: priorizar as 10 funcionalidades core, deferir melhorias

### 4.3 Métricas de Acompanhamento
- **Integração:** % testes passando, bugs por semana, tempo médio resposta API
- **Funcionalidades:** Velocity por sprint, % concluído, bugs encontrados vs. corrigidos
- **Equipe:** Horas dedicadas, absenteísmo, satisfação
- **Stakeholders:** Requisitos aprovados vs. pendentes, mudanças por semana

---

## Timeline de Alto Nível

| Semana | Fase 1 (Integração) | Fase 2 (Features) | Fase 3 (Finalização) | Marcos |
|--------|-------|-------|-------|-------|
| 1-3    | ✅ Estabilizar API, testes, docs | ▶️ Iniciar features | - | API documentada, testes de regressão |
| 4-6    | ✅ Validação contínua | ✅ Features prontas | ▶️ Iniciar 2 restantes | Features em progresso finalizadas |
| 7-8    | ✅ Suporte | ✅ Suporte | ✅ QA final | 10/10 funcionalidades prontas |
| Marco Final | Entrega | Entrega | Entrega | **APLICATIVO ENTREGUE** |

---

## Decisões e Trade-offs

| Decisão | Justificativa | Trade-off |
|---------|---------|---------|
| **Prioridade 1: Integração** | Bloqueador crítico — sem isso tudo falha | Força-tarefa de 2 devs dedicados significa funcionalidades 9-10 iniciam mais tarde |
| **Equipe fixa** | Sem possibilidade de contratação | Velocidade reduzida; trade-off com scope/prazo |
| **Novos requisitos incrementais** | Evitar scope creep | Nice-to-have fica para v2.0; stakeholders precisam priorizar |
| **Força-tarefa dupla em integração** | Redundância para criticidade | Funcionalidades 9-10 sofrem atraso; aceitável pois 8 features já agregam valor |

---

## Próximos Passos (Ação Imediata)

1. **Semana 1 (Início):**
   - [ ] Designar formalmente 2 devs + 1 tester para força-tarefa integração
   - [ ] Agendar reunião com suporte do sistema prontuário (SLA de resposta)
   - [ ] Iniciar documentação reversa da API (análise de código)
   - [ ] Criar ambiente de mock
   - [ ] Comunicar plano aos stakeholders

2. **Semana 2:**
   - [ ] Documentação da API - draft completo
   - [ ] Primeiros testes de regressão rodando
   - [ ] Features em progresso reorganizadas nos 2 devs restantes

3. **Semana 3:**
   - [ ] Validação Fase 1 - integração estável
   - [ ] Revisão com stakeholders - ajustes se necessário

---

## Considerações Adicionais

### A. Comunicação com Proprietário do Sistema Prontuário
- Você consegue contato técnico direto ou suporte formal?
- **Recomendação:** estabeleça SLA de resposta desde semana 1 (crítico para resolver instabilidade)
  - Exemplo: Resposta em até 24h para problemas críticos
  - Escalação: contato técnico → gerente de projeto deles se não resolvido em 48h

### B. Teste de Carga Antes de Entrega
- Com integração mais estável, há capacidade de fazer teste de carga do sistema prontuário com volume real?
- **Sugestão:** deixar para semana 7 para validar comportamento sob stress
- Coordenar com proprietário prontuário sobre disponibilidade para testes

### C. Documentação para Produção
- Após integração estável, quem fica responsável por manter docs atualizadas?
- **Recomendação:** designar 1 dev/1 tester compartilhado para manutenção de documentação durante fases 2-3
- Criar processo: issue → análise → atualização doc → review antes de merge

### D. Plano de Contingência (Se Prazos Ficarem Críticos)
**Prioridade mínima viável para entrega:**
1. ✅ Cadastro de usuários
2. ✅ Agendamento de consultas (com integração prontuário)
3. ✅ Notificações básicas
4. ✅ Gestão de agenda médica
5. ✅ Integração com prontuário (read-only)
- **Nice-to-have:** validações avançadas, relatórios, sync automático

---

## Contato & Escalação

- **Gerente de Projeto:** [seu nome]
- **Tech Lead Integração:** [nome do dev responsável]
- **Stakeholder Principal:** [nome]
- **Suporte Prontuário:** [contato técnico do sistema externo]

---

**Versão:** 1.0  
**Data:** 2026-07-06  
**Próxima Revisão:** 2026-07-13 (semana 1)
