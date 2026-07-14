# Identificação de Riscos do Projeto

## Contexto

Este documento consolida os principais riscos do projeto de desenvolvimento do aplicativo móvel de agendamento de consultas médicas, considerando o cenário atual de recuperação, a dependência crítica com a integração do prontuário eletrônico e o prazo de entrega previsto em aproximadamente 2 meses.

## Objetivo

Identificar, registrar e classificar os riscos que podem comprometer escopo, prazo, qualidade, comunicação e satisfação dos stakeholders.

## Metodologia de Identificação

A identificação foi realizada com base em:
- contexto do plano de recuperação;
- estado atual do projeto (50% completo, 3 funcionalidades em progresso, 2 não iniciadas);
- requisitos funcionais e não funcionais já levantados;
- dependências técnicas e de negócio;
- limitações de equipe e prazo.

## Registro de Riscos

| ID | Risco | Causa Primária | Gatilho | Impacto | Categoria |
|---|---|---|---|---|---|
| R1 | Instabilidade da integração com o prontuário eletrônico | API incompleta, documentação desatualizada e mudanças no sistema externo | Falhas em endpoints, respostas inconsistentes ou indisponibilidade da API | Atraso geral do projeto, retrabalho e risco de não entregar funcionalidades críticas | Técnico / Externo |
| R2 | Mudança contínua de requisitos | Stakeholders solicitam novas validações e regras de negócio durante o desenvolvimento | Novos pedidos semanais ou alterações após o início da implementação | Escopo em expansão, retrabalho e pressão sobre prazo | Requisitos / Negócio |
| R3 | Sobrecarga da equipe | Equipe fixa com alta demanda e poucas pessoas para responder a múltiplas frentes | Aumento de tarefas simultâneas e baixa capacidade de resposta | Atraso na entrega, redução de produtividade e maior risco de defeitos | Recursos / Pessoal |
| R4 | Atraso nas funcionalidades em progresso | Dependência de integração e replanejamento contínuo | Features com implementação incompleta ou bloqueada | Impacto direto em metas de sprint e no marco final | Cronograma |
| R5 | Deficiência de documentação técnica | Processo de integração e regras de negócio não documentadas com clareza | Falta de alinhamento entre desenvolvedores, tester e stakeholders | Maior retrabalho, falhas de interpretação e baixa rastreabilidade | Processo / Qualidade |
| R6 | Falhas de comunicação entre equipe e stakeholders | Informações parciais sobre riscos, impactos e decisões | Ausência de alinhamento semanal ou decisões tardias | Conflitos, má priorização e expectativas desalinhadas | Comunicação |
| R7 | Falta de cobertura de testes e validação | Priorização de desenvolvimento em detrimento de testes | Bugs críticos identificados tardiamente | Queda de qualidade, retrabalho e risco de entrega instável | Qualidade |
| R8 | Dependência excessiva de terceiros | Integração com sistema externo controlado por parceiro ou fornecedor | Demora na resposta de suporte ou mudanças nas políticas do fornecedor | Atrasos e dificuldade para resolver bloqueios técnicos | Externo / Fornecedor |
| R9 | Risco de não atendimento a SLA operacional | Tempo de resposta da API e disponibilidade do ambiente não atendem às necessidades | Latência elevada, timeout ou indisponibilidade recorrente | Prejuízo à experiência do usuário e risco de rollback | Operação / Desempenho |
| R10 | Baixa aceitação do produto pelos usuários finais | Requisitos não alinhados com as necessidades reais de uso | Feedback tardio ou resistência à mudança | Reprocesso, retrabalho e possível insatisfação do cliente | Usuário / Negócio |

## Classificação Inicial

### Riscos Críticos
- R1: Instabilidade da integração com o prontuário
- R2: Mudança contínua de requisitos
- R3: Sobrecarga da equipe

### Riscos Altos
- R4: Atraso nas funcionalidades em progresso
- R6: Falhas de comunicação
- R8: Dependência excessiva de terceiros

### Riscos Médios
- R5: Deficiência de documentação técnica
- R7: Falta de cobertura de testes
- R9: Não atendimento a SLA operacional

### Riscos Menores
- R10: Baixa aceitação do produto pelos usuários finais

## Próximos Passos

1. Validar os riscos com a equipe e com os stakeholders principais.
2. Definir responsáveis por cada risco.
3. Transformar os riscos em ações de mitigação no plano semanal de recuperação.
4. Revisar o registro a cada semana durante o período de recuperação.
