# Requisitos do Projeto - Agendamento de Consultas Médicas

## 📋 Visão Geral

Este documento detalha todos os requisitos funcionais e não-funcionais do aplicativo móvel de agendamento de consultas médicas. Os requisitos estão organizados por módulo e classificados por status de implementação.

---

## 🎯 Status Global

| Total | Prontos | Em Progresso | Não Iniciados |
|-------|---------|--------------|---------------|
| 10    | 5       | 3            | 2             |

---

## 📦 Módulo 1: Cadastro de Usuários

### REQ-1.1: Cadastro de Pacientes ✅ PRONTO

**Status:** ✅ Pronto  
**Prioridade:** CRÍTICA  
**Complexidade:** Média

**Descrição:**
O sistema deve permitir que novos pacientes se registrem fornecendo informações pessoais e de contato.

**Critérios de Aceitação:**
- [ ] Paciente fornece: nome completo, CPF, email, telefone, data de nascimento
- [ ] Sistema valida CPF (dígitos verificadores)
- [ ] Email deve ser único no sistema
- [ ] Telefone em formato brasileiro (11 9XXXX-XXXX)
- [ ] Senha com mínimo 8 caracteres (letras maiúsc/minúsc + números + especiais)
- [ ] Confirmar email antes de ativar conta (link de verificação)
- [ ] Aceitar termos de privacidade (obrigatório)

**Dependências:** Nenhuma

**Notas:** Feature completa e testada

---

### REQ-1.2: Cadastro de Médicos ✅ PRONTO

**Status:** ✅ Pronto  
**Prioridade:** CRÍTICA  
**Complexidade:** Média

**Descrição:**
O sistema deve permitir que médicos se registrem e criem perfis profissionais.

**Critérios de Aceitação:**
- [ ] Médico fornece: nome completo, CPF, CRM (Conselho Regional de Medicina), especialidade(s)
- [ ] Sistema valida CRM junto a banco de dados de órgão regulador (opcional para MVP)
- [ ] Email único
- [ ] Telefone profissional
- [ ] Bio/descrição profissional (opcional)
- [ ] Foto de perfil (upload, máx 5MB)
- [ ] Pode listar múltiplas especialidades

**Dependências:** Nenhuma

**Notas:** Feature completa; validação de CRM pode ser implementada em v2.0

---

### REQ-1.3: Autenticação e Login ✅ PRONTO

**Status:** ✅ Pronto  
**Prioridade:** CRÍTICA  
**Complexidade:** Média

**Descrição:**
O sistema deve autenticar pacientes e médicos de forma segura.

**Critérios de Aceitação:**
- [ ] Login com email + senha
- [ ] Validar credenciais contra banco de dados
- [ ] Gerar token JWT válido por 24h
- [ ] Refresh token para estender sessão
- [ ] Logout efetivo (invalidar token)
- [ ] Recuperação de senha via email (link com token de 15min)
- [ ] Limite de tentativas de login (5 tentativas = bloqueio 30min)
- [ ] Log de acessos (auditoria)

**Dependências:** REQ-1.1, REQ-1.2

**Notas:** Feature completa e segura

---

### REQ-1.4: Perfil de Usuário ✅ PRONTO

**Status:** ✅ Pronto  
**Prioridade:** ALTA  
**Complexidade:** Baixa

**Descrição:**
Usuários (paciente/médico) devem poder visualizar e editar seus dados de perfil.

**Critérios de Aceitação:**
- [ ] Visualizar dados pessoais (leitura)
- [ ] Editar email, telefone, bio (se médico)
- [ ] Editar foto de perfil
- [ ] Mudar senha
- [ ] Visualizar histórico de logins recentes
- [ ] Opção de deletar conta (soft delete, após 30 dias)

**Dependências:** REQ-1.3

**Notas:** Feature completa

---

## 📅 Módulo 2: Gestão de Agenda Médica

### REQ-2.1: Criar Agenda de Consultas 🔄 EM PROGRESSO

**Status:** 🔄 Em Progresso  
**Prioridade:** CRÍTICA  
**Complexidade:** Alta

**Descrição:**
Médicos devem poder criar e gerenciar sua agenda de disponibilidade para consultas.

**Critérios de Aceitação:**
- [ ] Médico define: dias da semana ativos, horário início/fim de expediente
- [ ] Definir duração padrão de consulta (15min, 30min, 1h, etc)
- [ ] Criar slots de disponibilidade automáticos (ex: gera slots de 30min entre 8h-18h)
- [ ] Excluir/bloquear datas (feriados, férias, ausências)
- [ ] Visualizar agenda em vista semanal/mensal
- [ ] Editar slots individuais (mudar hora, bloquear, liberar)
- [ ] Sincronizar com calendário externo (Google Calendar, Outlook) - opcional v2.0

**Dependências:** REQ-1.2

**Notas:** 60% pronto; faltam refinamentos em sincronização e edge cases

**Bloqueadores:** Nenhum crítico

---

### REQ-2.2: Disponibilidade em Tempo Real 🔄 EM PROGRESSO

**Status:** 🔄 Em Progresso  
**Prioridade:** ALTA  
**Complexidade:** Média

**Descrição:**
O sistema deve mostrar em tempo real quais slots estão disponíveis para agendamento.

**Critérios de Aceitação:**
- [ ] Atualizar disponibilidade após cada novo agendamento
- [ ] Mostrar slots verdes (disponível), vermelhos (ocupado), cinza (bloqueado)
- [ ] Filtrar por especialidade
- [ ] Filtrar por intervalo de data
- [ ] Cache de disponibilidade (atualizar a cada 5min ou em tempo real)
- [ ] Não mostrar slots no passado

**Dependências:** REQ-2.1, REQ-3.1 (agendamento)

**Notas:** 70% pronto; cache/real-time precisa validação com integração prontuário

**Bloqueadores:** Instabilidade integração prontuário afeta atualização em tempo real

---

### REQ-2.3: Histórico de Consultas do Médico ✅ PRONTO

**Status:** ✅ Pronto  
**Prioridade:** ALTA  
**Complexidade:** Média

**Descrição:**
Médicos visualizam suas consultas passadas e futuras.

**Critérios de Aceitação:**
- [ ] Listar consultas em ordem cronológica (passadas + futuras)
- [ ] Filtrar por data, paciente, especialidade
- [ ] Visualizar detalhes: paciente, data/hora, status, notas
- [ ] Marcar consulta como realizada
- [ ] Adicionar notas pós-consulta (integra com prontuário)

**Dependências:** REQ-3.1

**Notas:** Feature completa

---

## 📋 Módulo 3: Agendamento de Consultas

### REQ-3.1: Agendar Consulta 🔄 EM PROGRESSO

**Status:** 🔄 Em Progresso  
**Prioridade:** CRÍTICA  
**Complexidade:** Alta

**Descrição:**
Pacientes devem poder agendar consultas com médicos disponíveis.

**Critérios de Aceitação:**
- [ ] Paciente busca médico por nome, especialidade, disponibilidade
- [ ] Visualizar perfil do médico (foto, bio, avaliações - opcional)
- [ ] Selecionar data e hora de slot disponível
- [ ] Confirmar agendamento (revisar dados antes de confirmar)
- [ ] Sistema retorna confirmação com ID da consulta
- [ ] Enviar confirmação por email e SMS
- [ ] Validação: não permitir agendar <2h antes (ex: não agendar p/ daqui 1h)
- [ ] Validação: paciente não pode ter 2 consultas no mesmo horário

**Novas Validações Solicitadas por Stakeholders (REQ-3.1.1):**
- [ ] Máximo 3 consultas por semana por paciente (regra de negócio)
- [ ] Paciente só pode agendar com até 30 dias de antecedência
- [ ] Médico pode definir mínimo de intervalo entre consultas (ex: 1h para recuperação)

**Dependências:** REQ-1.1, REQ-2.1, REQ-5.1 (integração prontuário)

**Notas:** 50% pronto; novas validações em análise; bloqueado por instabilidade integração

**Bloqueadores:** 🚨 Instabilidade integração prontuário → não consegue confirmar agendamento vs. prontuário (CRÍTICO)

---

### REQ-3.2: Cancelar Agendamento ✅ PRONTO

**Status:** ✅ Pronto  
**Prioridade:** ALTA  
**Complexidade:** Média

**Descrição:**
Pacientes e médicos podem cancelar agendamentos com aviso mínimo.

**Critérios de Aceitação:**
- [ ] Cancelar até 24h antes da consulta (sem penalidade)
- [ ] Cancelar <24h = notificar médico (não impede)
- [ ] Cancelamento libera slot para outros pacientes
- [ ] Motivo do cancelamento (opcional, para feedback)
- [ ] Email de confirmação de cancelamento
- [ ] Marcar como "cancelado" (não deletar dado)
- [ ] Histórico de cancelamentos do paciente (transparência)

**Dependências:** REQ-3.1

**Notas:** Feature completa

---

### REQ-3.3: Reagendar Consulta 🔄 EM PROGRESSO

**Status:** 🔄 Em Progresso  
**Prioridade:** MÉDIA  
**Complexidade:** Média

**Descrição:**
Pacientes podem reagendar consultas já agendadas.

**Critérios de Aceitação:**
- [ ] Selecionar nova data/hora do mesmo médico
- [ ] Validar disponibilidade da nova data
- [ ] Validar se ainda está dentro do período permitido (30 dias)
- [ ] Notificar médico sobre reagendamento
- [ ] Manter referência antiga (auditoria)
- [ ] Limite: máximo 2 reagendamentos por consulta

**Dependências:** REQ-3.1, REQ-3.2

**Notas:** 40% pronto; lógica de múltiplos reagendamentos ainda em design

**Bloqueadores:** Nenhum crítico

---

## 🔔 Módulo 4: Notificações

### REQ-4.1: Notificações por Email 🔄 EM PROGRESSO

**Status:** 🔄 Em Progresso  
**Prioridade:** ALTA  
**Complexidade:** Média

**Descrição:**
Sistema envia notificações por email para confirmações, lembretes e atualizações.

**Critérios de Aceitação:**
- [ ] Confirmação de agendamento (enviada ao paciente e médico)
- [ ] Lembrete 24h antes da consulta
- [ ] Lembrete 1h antes da consulta (opcional)
- [ ] Notificação de cancelamento
- [ ] Notificação de reagendamento
- [ ] Email deve incluir: data/hora, médico/paciente, ID consulta, link para cancelar
- [ ] Template HTML profissional
- [ ] Unsubscribe option (opcional)

**Dependências:** REQ-3.1, REQ-3.2, REQ-3.3

**Notas:** 50% pronto; templates finalizando, agendador de emails sendo integrado

**Bloqueadores:** Nenhum crítico

---

### REQ-4.2: Notificações por SMS (Opcional) 📋 NÃO INICIADO

**Status:** 📋 Não Iniciado  
**Prioridade:** MÉDIA  
**Complexidade:** Média

**Descrição:**
Sistema envia notificações por SMS para lembretes (opcional, depende de integradora SMS).

**Critérios de Aceitação:**
- [ ] SMS de lembrete 24h antes
- [ ] SMS de lembrete 1h antes
- [ ] SMS de confirmação (se paciente marcou preferência)
- [ ] Máx 160 caracteres por SMS
- [ ] Respeitar horário silencioso (7-22h)

**Dependências:** REQ-3.1, REQ-3.2

**Notas:** Funcionalidade de nice-to-have; integração com Twilio ou semelhante

**Prioridade no Projeto:** Pospor para v2.0 se houver restrição de prazo

---

### REQ-4.3: Notificações Push (Opcional) 📋 NÃO INICIADO

**Status:** 📋 Não Iniciado  
**Prioridade:** BAIXA  
**Complexidade:** Alta

**Descrição:**
Sistema envia notificações push no aplicativo móvel.

**Critérios de Aceitação:**
- [ ] Push de confirmação de agendamento
- [ ] Push de lembrete 24h e 1h antes
- [ ] Usuário pode desabilitar notificações
- [ ] Funcionamento mesmo offline (quando reconecta)
- [ ] Deep link para ir direto para consulta agendada

**Dependências:** REQ-3.1, REQ-3.2

**Notas:** Requer integração Firebase Cloud Messaging ou Apple Push Notifications

**Prioridade no Projeto:** v2.0 ou pós-MVP

---

## 🔗 Módulo 5: Integração com Prontuário Eletrônico

### REQ-5.1: Sincronização de Agendamentos com Prontuário 🔴 BLOQUEADO

**Status:** 🔴 Bloqueado (instabilidade de API)  
**Prioridade:** CRÍTICA  
**Complexidade:** Muito Alta

**Descrição:**
Agendamentos confirmados devem ser sincronizados com o sistema de prontuário eletrônico.

**Critérios de Aceitação:**
- [ ] Após paciente confirmar agendamento, enviar para prontuário
- [ ] Prontuário recebe: ID paciente, ID médico, data/hora, especialidade
- [ ] Validar resposta do prontuário (sucesso/erro)
- [ ] Se falhar, retentar (exponential backoff: 1s, 2s, 4s, 8s, máx 5 tentativas)
- [ ] Log de todas as sincronizações (auditoria)
- [ ] Tratamento de erros: timeout >5s = falha
- [ ] Endpoint: [URL do prontuário]/api/agendamentos (a confirmar)

**Desafios Conhecidos:**
- 🚨 Documentação da API confusa/incompleta
- 🚨 Mudanças recentes no sistema externo (breaking changes)
- 🚨 Latência inconsistente (timeouts)

**Mitigação (Fase 1):**
- [ ] Força-tarefa dedicada (2 devs + tester) — semanas 1-3
- [ ] Reverter-engenheirar comportamento da API
- [ ] Documentar API internamente
- [ ] Criar ambiente de mock para testes
- [ ] Testes de regressão automatizados

**Dependências:** REQ-3.1

**Notas:** BLOQUEADOR CRÍTICO para sucesso do projeto. Sem isso, consultas não são registradas no sistema médico.

**Timeline de Resolução:** Fim da semana 3 (validação Fase 1)

---

### REQ-5.2: Consultar Prontuário do Paciente 📋 NÃO INICIADO

**Status:** 📋 Não Iniciado  
**Prioridade:** ALTA  
**Complexidade:** Alta

**Descrição:**
Médicos podem consultar prontuário eletrônico do paciente durante ou após agendamento.

**Critérios de Aceitação:**
- [ ] Médico visualiza: histórico médico, alergias, medicamentos, diagnósticos prévios
- [ ] Buscar por ID paciente ou CPF
- [ ] Dados confidenciais (LGPD): acesso auditado, logs de consulta
- [ ] Cache de leitura (30min) para não sobrecarregar prontuário
- [ ] Tratar erros de conexão gracefully

**Dependências:** REQ-5.1, REQ-1.2

**Notas:** Depende de que REQ-5.1 esteja estável. Pospor para Fase 3.

**Prioridade no Projeto:** Iniciar após REQ-5.1 validado (semana 4+)

---

### REQ-5.3: Atualizar Prontuário com Notas da Consulta 📋 NÃO INICIADO

**Status:** 📋 Não Iniciado  
**Prioridade:** ALTA  
**Complexidade:** Alta

**Descrição:**
Após consulta, médico adiciona notas que são sincronizadas com prontuário eletrônico.

**Critérios de Aceitação:**
- [ ] Médico escreve notas pós-consulta (texto livre)
- [ ] Enviar para prontuário com timestamp
- [ ] Validação: notas só podem ser adicionadas após hora da consulta
- [ ] Editar notas até 24h após consulta (depois fica locked)
- [ ] Sincronizar com prontuário (retry logic)
- [ ] Notificar paciente que notas foram registradas (opcional)

**Dependências:** REQ-5.1, REQ-2.3

**Notas:** Depende de REQ-5.1. Iniciar após estabilização.

**Prioridade no Projeto:** Fase 3 (semana 4+)

---

## 🔒 Módulo 6: Requisitos Não-Funcionais

### REQ-6.1: Performance

**Status:** ✅ Pronto (design), 🔄 Em Validação  
**Prioridade:** ALTA

**Critérios de Aceitação:**
- [ ] Tempo de resposta <500ms para 95% das requisições
- [ ] Tempo de agendamento (clique a confirmação) <2s
- [ ] Busca de médicos <1s para 1000+ registros
- [ ] Home page carrega em <3s (mobile)
- [ ] Suportar 100 requisições simultâneas

---

### REQ-6.2: Segurança

**Status:** ✅ Pronto (design), 🔄 Em Validação  
**Prioridade:** CRÍTICA

**Critérios de Aceitação:**
- [ ] Todas as senhas hasheadas (bcrypt, mínimo 12 rounds)
- [ ] Comunicação HTTPS/TLS
- [ ] Proteção contra SQL Injection (prepared statements)
- [ ] CSRF tokens em formulários
- [ ] Rate limiting (5 tentativas de login por IP por 30min)
- [ ] Dados de cartão de crédito não armazenados (se houver pagamento)
- [ ] Logs de auditoria para ações críticas
- [ ] Conformidade LGPD (privacidade de dados)

---

### REQ-6.3: Disponibilidade

**Status:** ✅ Pronto (design)  
**Prioridade:** ALTA

**Critérios de Aceitação:**
- [ ] 99.5% uptime
- [ ] Backup automático diário
- [ ] Disaster recovery: RTO <4h, RPO <1h
- [ ] Redundância de banco de dados (replicação)

---

### REQ-6.4: Escalabilidade

**Status:** ✅ Pronto (design)  
**Prioridade:** MÉDIA

**Critérios de Aceitação:**
- [ ] Arquitetura suporta crescimento para 10.000 usuários
- [ ] Banco de dados particionado por especialidade ou região (opcional)
- [ ] Cache distribuído (Redis)
- [ ] Load balancing de API

---

## 📊 Matriz de Rastreamento

| ID | Requisito | Status | Sprint | Responsável | Notas |
|-----|-----------|--------|--------|-------------|-------|
| REQ-1.1 | Cadastro Pacientes | ✅ | 1-2 | Dev 1 | Completo |
| REQ-1.2 | Cadastro Médicos | ✅ | 1-2 | Dev 2 | Completo |
| REQ-1.3 | Autenticação | ✅ | 1-2 | Dev 1 | Completo |
| REQ-1.4 | Perfil | ✅ | 2-3 | Dev 2 | Completo |
| REQ-2.1 | Agenda Médica | 🔄 | 3-4 | Dev 3 | 60% pronto |
| REQ-2.2 | Disponibilidade | 🔄 | 4-5 | Dev 3 | 70% pronto |
| REQ-2.3 | Histórico Médico | ✅ | 3 | Dev 4 | Completo |
| REQ-3.1 | Agendar Consulta | 🔄 | 4-5 | Dev 4 | 50% pronto, bloqueado por REQ-5.1 |
| REQ-3.2 | Cancelar | ✅ | 5 | Dev 3 | Completo |
| REQ-3.3 | Reagendar | 🔄 | 5-6 | Dev 4 | 40% pronto |
| REQ-4.1 | Email | 🔄 | 5-6 | Dev 1 | 50% pronto |
| REQ-4.2 | SMS | 📋 | 7-8 | - | Nice-to-have, v2.0 |
| REQ-4.3 | Push | 📋 | 8+ | - | v2.0 |
| REQ-5.1 | Integração Prontuário | 🔴 | 1-3 | Dev 2 + Dev 3 (Fase 1) | BLOQUEADOR CRÍTICO |
| REQ-5.2 | Consultar Prontuário | 📋 | 4-6 | - | Pospor para Fase 3 |
| REQ-5.3 | Atualizar Prontuário | 📋 | 6-8 | - | Pospor para Fase 3 |
| REQ-6.1 | Performance | ✅ 🔄 | Contínuo | Todos | Monitorando |
| REQ-6.2 | Segurança | ✅ 🔄 | Contínuo | Todos | Implementado, auditando |
| REQ-6.3 | Disponibilidade | ✅ 🔄 | Contínuo | DevOps | Design pronto |
| REQ-6.4 | Escalabilidade | ✅ 🔄 | Contínuo | DevOps | Design pronto |

---

## 🎯 Checklist de Validação (Tester)

Para cada requisito implementado, o tester deve validar:

- [ ] Funcionamento conforme critérios de aceitação
- [ ] Sem erros 5xx / 4xx inesperados
- [ ] Mensagens de erro são claras
- [ ] Comportamento em edge cases (ex: campo vazio, valores negativos)
- [ ] Sem regressões em funcionalidades relacionadas
- [ ] Performance dentro dos limites (se aplicável)
- [ ] Sem vulnerabilidades óbvias

---

## 📝 Histórico de Mudanças

| Data | Mudança | Motivação |
|------|---------|-----------|
| 2026-07-06 | Criação inicial | Documento base do projeto |
| - | Novos requisitos REQ-3.1.1 | Solicitação stakeholders (novas validações) |
| - | Prioridade de SMS/Push para v2.0 | Restrição de prazo (2 meses) |

---

## 📞 Perguntas & Clarificações

**Q1:** O limite de 3 consultas/semana aplica a cancellations também?  
**R1:** Não. Limite de 3 agendadas simultaneamente no futuro. Cancelamentos não contam.

**Q2:** Pode-se agendar feriados?  
**R2:** Não. Médicos bloqueiam feriados na agenda. Sistema deve prevenir agendamento.

**Q3:** Integração prontuário é síncrona ou assíncrona?  
**R3:** A ser definido na Fase 1. Proposta: assíncrona com fallback síncrono se <500ms.

**Q4:** LGPD: quanto tempo retém dados de usuários deletados?  
**R4:** 30 dias em soft delete, depois hard delete automático. Logs de auditoria retidos por 2 anos.

---

**Versão:** 1.0  
**Data de Criação:** 2026-07-06  
**Próxima Revisão:** 2026-07-13 (weekly)  
**Responsável:** Gerente de Projeto
