# Documentação do Projeto - Agendamento de Consultas Médicas

## 📋 Contexto do Projeto

Este repositório contém a documentação e planejamento do **Aplicativo Móvel de Agendamento de Consultas Médicas**, um projeto em desenvolvimento na disciplina de **Engenharia de Software (Módulo 04)** da UFG.

### Visão Geral

O aplicativo móvel visa facilitar o agendamento de consultas médicas com funcionalidades como:
- ✅ Cadastro de usuários (pacientes e médicos)
- ✅ Gestão de agenda médica
- ✅ Agendamento de consultas
- ✅ Sistema de notificações
- ✅ Integração com sistema externo de prontuário eletrônico

### Status Atual (2026-07-06)

- **Progresso:** 50% completo (5/10 funcionalidades prontas, 3 em progresso, 2 não iniciadas)
- **Equipe:** 4 desenvolvedores + 1 tester
- **Marco de Entrega:** 2 meses a partir de hoje
- **Statusdo projeto:** Em recuperação/estabilização

---

## 🚨 Desafios Identificados

### 1. Instabilidade na Integração com Prontuário
- **Problema:** API confusa/incompleta, documentação desatualizada e mudanças recentes no sistema externo
- **Impacto:** Retrabalho contínuo e atrasos nas funcionalidades dependentes
- **Solução:** Força-tarefa dedicada para documentação, testes e estabilização (Fase 1)

### 2. Mudanças de Requisitos de Stakeholders
- **Problema:** Requisições incrementais de novas validações e regras de negócio durante desenvolvimento
- **Impacto:** Pressão adicional na equipe já sobrecarregada
- **Solução:** Change Control Board semanal com priorização clara

### 3. Pressão de Recursos
- **Problema:** Equipe fixa (5 pessoas), carga aumentada, dificuldades para cumprir prazos
- **Impacto:** Risco de atrasos na entrega final
- **Solução:** Realocação de recursos para focar no bloqueador crítico (integração); velocity reduzida mas controlada

---

## 📚 Documentos Principais

### `plano-recuperacao-projeto.md`
Plano detalhado em 3 fases para recuperação do projeto nos próximos 2 meses:
- **Fase 1 (Semanas 1-3):** Estabilização da integração com prontuário
- **Fase 2 (Semanas 2-6):** Finalização das funcionalidades em progresso
- **Fase 3 (Semana 4+):** Inicialização das funcionalidades restantes + QA final

Inclui: timeline, alocação de recursos, métricas, riscos e planos de contingência.

---

## 👥 Equipe

| Papel | Quantidade | Responsabilidades |
|-------|-----------|-------------------|
| Desenvolvedor | 4 | Implementação de features, correção de bugs, documentação de código |
| Tester | 1 | Testes funcionais, regressão, integração; validação de requisitos |
| Gerente de Projeto | 1 (você) | Coordenação, stakeholder management, mitigação de riscos |

### Forças-Tarefa Propostas
- **Integração Prontuário:** 2 devs + 1 tester (Fase 1, semanas 1-3)
- **Funcionalidades em Progresso:** 2 devs (Fase 2, semanas 2-6)
- **Funcionalidades Restantes:** 2 devs (Fase 3, semana 4+)

---

## 📅 Timeline de Alto Nível

| Período | Foco Principal | Marcos |
|---------|-------|-------|
| **Semanas 1-3** | Estabilizar integração prontuário | API documentada, testes de regressão passando |
| **Semanas 2-6** | Finalizar 3 funcionalidades em progresso | 8/10 features prontas |
| **Semanas 4-8** | Iniciar 2 features restantes + QA | 10/10 features prontas |
| **Semana 8 (Final)** | Entrega ao cliente | Aplicativo pronto para produção |

---

## 🎯 Prioridades

1. **CRÍTICA:** Estabilizar integração com prontuário (bloqueador)
2. **ALTA:** Finalizar funcionalidades em progresso
3. **MÉDIA:** Incorporar novos requisitos de stakeholders (incrementalmente)
4. **BAIXA:** Nice-to-have / v2.0

---

## ⚠️ Principais Riscos e Mitigações

| Risco | Impacto | Mitigação | Plano B |
|-------|--------|----------|---------|
| **Integração não estabiliza** | Projeto inteiro em risco | Força-tarefa dedicada semana 1 + suporte técnico | Fallback manual/parcial |
| **Requisitos continuam mudando** | Scope creep | Change Control semanal | Nice-to-have → v2.0 |
| **Equipe não mantém velocity** | Funcionalidades atrasam | Monitorar diariamente, realocar | Priorizar MVP (8 features) |

---

## 📊 Métricas de Sucesso

- ✅ Integração prontuário: 100% testes passando, <500ms latência média
- ✅ Funcionalidades: 10/10 prontas e validadas pelo tester
- ✅ Qualidade: <5 bugs críticos na entrega, documentação 100% atualizada
- ✅ Prazos: Marco final cumprido em 2 meses
- ✅ Satisfação: Stakeholders aprovam antes da entrega

---

## 🔄 Gestão de Requisitos

### Novo Requisito? Siga Este Processo:

1. **Submeter** → Stakeholder submete requisição
2. **Analisar** → Estimar impacto (horas, risco, dependências)
3. **Classificar** → Essencial vs. Nice-to-have
4. **Priorizar** → Change Control Board decide se incorpora ou adia
5. **Implementar** → Se aprovado, integrar na sprint atual/próxima
6. **Validar** → Tester valida antes de merge

---

## 📞 Comunicação

- **Reunião Stakeholders:** Semanal (terça-feira, 10h) — status integração, features, requisitos
- **Daily Standup:** Diário (10:30h) — equipe dev + tester + gerente projeto
- **Sprint Planning:** Toda segunda-feira (14h)
- **Sprint Review & Retro:** Toda sexta-feira (16h)

---

## 📁 Estrutura de Diretórios

```
Lab/
├── Docs/
│   ├── README.md                    # Este arquivo
│   ├── plano-recuperacao-projeto.md # Plano detalhado em 3 fases
│   ├── arquitetura.md              # (A adicionar) Diagrama arquitetura
│   ├── api-prontuario.md           # (A adicionar) Documentação API integração
│   └── requisitos.md               # (A adicionar) Lista de requisitos + status
├── src/                             # Código-fonte
│   ├── components/
│   ├── services/
│   ├── models/
│   └── ...
├── tests/                           # Testes automatizados
├── docs-api/                        # Documentação técnica (Swagger, etc)
└── README.md                        # README principal do projeto
```

---

## 🚀 Como Usar Esta Documentação

1. **Gerente de Projeto:** Comece com `plano-recuperacao-projeto.md` para entender a estratégia
2. **Desenvolvedores:** Consulte `api-prontuario.md` para detalhes de integração
3. **Tester:** Veja `requisitos.md` para checklist de validação
4. **Stakeholders:** Leia a seção "Prioridades" acima para entender trade-offs

---

## 📝 Notas Importantes

- ⚠️ **Este plano é vivo:** será revisado semanalmente conforme progresso
- 🔄 **Feedback contínuo:** qualquer bloqueador deve ser comunicado imediatamente
- 📊 **Transparência:** status publicado semanalmente para stakeholders
- 🎯 **Foco:** prioridade número 1 é estabilizar integração (semanas 1-3)

---

## 📅 Próxima Revisão

**Data:** 2026-07-13 (fim da semana 1)

**O que esperar:**
- Força-tarefa integração em operação
- Primeiros testes de regressão rodando
- API prontuário com documentação v0.1
- Status de funcionalidades em progresso

---

## 👨‍💼 Responsável por Esta Documentação

- **Criação:** 2026-07-06
- **Versão:** 1.0
- **Próxima Review:** 2026-07-13

---

**Sucesso no projeto! 💪**
