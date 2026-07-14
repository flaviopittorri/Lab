# Análise Qualitativa e Priorização dos Riscos

## Objetivo

Avaliar os riscos identificados com base em probabilidade, impacto e urgência, de modo a definir uma ordem de atendimento e priorização das respostas.

## Escala Qualitativa

- Probabilidade: Baixa, Média, Alta
- Impacto: Baixo, Médio, Alto, Crítico
- Prioridade: P1, P2, P3

## Matriz de Priorização

| ID | Risco | Probabilidade | Impacto | Prioridade | Justificativa |
|---|---|---|---|---|---|
| R1 | Instabilidade da integração com o prontuário | Alta | Crítico | P1 | É o bloqueador principal do projeto e afeta praticamente todas as funcionalidades dependentes |
| R2 | Mudança contínua de requisitos | Alta | Alto | P1 | Pode gerar scope creep e comprometer o cumprimento do prazo |
| R3 | Sobrecarga da equipe | Alta | Alto | P1 | Reduz produtividade e aumenta risco de falhas e retrabalho |
| R4 | Atraso nas funcionalidades em progresso | Média | Alto | P2 | Afeta a recuperação do projeto, mas pode ser controlado com replanejamento |
| R6 | Falhas de comunicação | Média | Alto | P2 | Pode agravar conflitos e dificultar decisões rápidas |
| R8 | Dependência excessiva de terceiros | Média | Alto | P2 | Pode limitar a capacidade de resposta técnica e gerar bloqueios externos |
| R5 | Deficiência de documentação técnica | Média | Médio | P2 | Impacta a execução, mas pode ser corrigida com disciplina de processo |
| R7 | Falta de cobertura de testes | Média | Médio | P2 | Aumenta risco de defeitos e retrabalho, principalmente em fase de validação |
| R9 | Não atendimento a SLA operacional | Média | Médio | P3 | Impacta a operação da solução, mas pode ser mitigado após estabilização da integração |
| R10 | Baixa aceitação do produto pelos usuários finais | Baixa | Médio | P3 | Relevante para sucesso do projeto, porém não é o principal fator de risco imediato |

## Estratégia de Tratamento

| Prioridade | Estratégia Principal | Observação |
|---|---|---|
| P1 | Mitigar | Ações imediatas e contínuas para reduzir impacto e probabilidade |
| P2 | Mitigar / Aceitar parcialmente | Requer monitoramento e controle frequente |
| P3 | Aceitar / Monitorar | Sem grande investimento inicial, mas com acompanhamento |

## Priorização por Eixo de Gestão

### 1. Atendimento imediato
- R1, R2 e R3 devem ter respostas imediatas e acompanhamento diário.

### 2. Controle semanal
- R4, R6 e R8 devem ser acompanhados em reunião semanal de status e replanejamento.

### 3. Monitoramento contínuo
- R5, R7 e R9 devem ser tratados com ações preventivas e validações periódicas.

## Critérios de Priorização

A priorização considerou:
1. impacto no objetivo principal do projeto;
2. efeito em outras atividades e dependências;
3. possibilidade de resolução dentro do prazo de recuperação;
4. relevância para stakeholders e para a qualidade final do produto.

## Recomendações de Atenção

- Concentrar esforços na estabilização da integração antes de ampliar o escopo.
- Aplicar gestão formal de mudanças para reduzir risco de scope creep.
- Acompanhar indicadores de velocidade da equipe e de defeitos por sprint.
- Criar um painel simples de riscos com status, responsável e prazo de ação.
