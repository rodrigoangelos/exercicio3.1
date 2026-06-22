# B — Relatório de Pesquisa Estruturada: Hipótese de Blueprint AS-IS — v3
## Serviço: Atendimento ao Seguro-Desemprego — Canais Caixa (consulta/pagamento) e MTE (concessão/recurso)

> **Versão:** 3.0 — revisão pós-auditoria v2 (versão final)
> **Base normativa central:** Resolução CODEFAT nº 957/2022
> **Classificação do documento:** Hipótese estruturada de blueprint AS-IS, parcialmente sustentada por normativos; Eixo 1 (URA) é hipótese operacional pendente de validação empírica.
> **Cidadão central:** Trabalhador formal CLT demitido sem justa causa, com baixo letramento digital.

---

## Nota metodológica e classificação de evidências

Este documento distingue quatro níveis de evidência:

- **[N]** Normativo — fundado em Resolução CODEFAT nº 957/2022, lei ou decreto
- **[O]** Oficial de canal — publicado em portal oficial (Caixa, gov.br, MTE) sem ser norma
- **[A]** Relato anedótico — Reclame Aqui, ouvidoria, fóruns; útil para hipóteses, não valida operação
- **[I]** Inferência — hipótese analítica sem fonte direta; requer validação

**Seções marcadas com ⚠ Hipótese** devem ser validadas por ligação-teste, transcrição da URA ou documentação interna da Caixa antes de uso em blueprint AS-IS definitivo.

---

## Resposta às Falhas da Auditoria v2

### Falhas das auditorias v1 remanescentes na v2

**1.2 (residual) "Agendamento" atribuído ao App Benefícios Sociais CAIXA → CORRIGIDO**
Removido. O App Benefícios Sociais CAIXA oferece informações, calendário e consulta de situação de parcelas — sem comprovação de agendamento de atendimento. Veja tabela de canais revisada.

**1.3 (residual) Fluxo de URA como etapa do serviço → CORRIGIDO**
O fluxo de menus foi rebaixado explicitamente para "roteiro de validação / hipótese a testar" com marcação ⚠ Hipótese. Não aparece mais como etapa verificada do serviço.

**1.4 (residual) "Agendamento se disponível na URA" na tabela de evidências → CORRIGIDO**
Removido da tabela de evidências físicas da URA. Se houver agendamento, é competência MTE/SINE/SRTE/158, não da URA Caixa.

**1.6 (residual) Tempo estimado de autenticação sem base → CORRIGIDO**
Todos os tempos estimados do fluxo URA foram removidos. Sem transcrição ou teste da URA, qualquer estimativa de duração é especulativa.

**1.7 (residual) "Senha do cartão Caixa" no corpo do fluxo → CORRIGIDO**
Removido do corpo do fluxo. Mantido apenas na lista de hipóteses a validar (seção final).

**1.13 (residual) "Benefício previdenciário-trabalhista" → CORRIGIDO**
Seguro-Desemprego não é benefício previdenciário. Corrigido para **"benefício trabalhista do Programa Seguro-Desemprego"** em todas as ocorrências.

**3.2 (residual) SINE-Fácil omitido → CORRIGIDO**
SINE-Fácil adicionado como canal MTE/digital para solicitação, consulta e recurso (conforme FAQ gov.br). Veja tabela de canais.

**3.3 (residual) Recurso de 120 dias simplificado → CORRIGIDO**
Expandido: recurso de 120 dias cabe para indeferimento, montante, suspensão **e cancelamento** (Resolução 957/2022). Incluído o requisito de conta gov.br nível Prata ou Ouro para o serviço digital de recurso.

**3.8 (residual) Fluxo interno Caixa→MTE no blueprint → CORRIGIDO**
Removido do blueprint AS-IS. Mantidas apenas as duas trilhas comprovadas por normativos: (i) exceção de concessão/recurso → MTE/gov.br/CTPS Digital/SRTE/SINE; (ii) exceção de pagamento/saque → agente pagador Caixa.

**F4 (residual) Classificação dupla → CORRIGIDO**
Separado em dois fail points distintos: F4a (inconsistência cadastral na habilitação — base normativa) e F4b (falha de autenticação telefônica — hipótese/inferência, pois mecanismo da URA é desconhecido).

**F10/F21 duplicação → CORRIGIDO**
Fundidos em um único fail point F10: "Notificação digital não acessada, não compreendida ou presumida válida sem ciência efetiva do trabalhador." Inclui a previsão normativa de que a notificação é considerada válida após cinco dias da disponibilização no ambiente de acesso (Resolução 957/2022) [N].

**F12 (residual) Callback como "inferência" → CORRIGIDO**
Rebaixado para **em aberto**: como a árvore da URA não foi validada, ausência de callback também não pode ser afirmada. Mantido apenas na lista de hipóteses a validar (V1).

**F13 (residual) Protocolo sem evidência → CORRIGIDO**
Reclassificado como hipótese anedótica [A], não como fail point confirmado. Requer teste de atendimento humano ou norma interna da Caixa para validação.

**F24 (residual) "Tem direito" excessivo → CORRIGIDO**
Reformulado: "Trabalhador não sabe se está abrangido por prolongamento excepcional autorizado em ato normativo específico" — dependente de contexto e regulamentação, não direito individual automático.

### Falhas novas introduzidas pela v2

**Nova falha 1 — "Único número oficial" → CORRIGIDO**
Reformulado: "O número Caixa Cidadão associado à consulta de benefícios sociais é **0800-726-0207**. A Caixa também lista outros canais (Alô CAIXA e similares), que devem ser distinguidos por finalidade. Para fins deste blueprint, o canal de interesse é o 0800-726-0207 em sua função de consulta de Seguro-Desemprego."

**Nova falha 2 — "Agendamento" no App Benefícios Sociais CAIXA → CORRIGIDO**
Removido. Veja 1.2 residual acima.

**Nova falha 3 — SINE-Fácil omitido → CORRIGIDO**
Adicionado. Veja tabela de canais e 3.2 residual acima.

**Nova falha 4 — Doméstico: tensão entre Resolução e FAQ → CORRIGIDO**
Separado explicitamente: trabalhador formal usa canais digitais (gov.br/CTPS Digital); **empregado doméstico deve agendar atendimento presencial pela central 158**, conforme FAQ operacional público do gov.br — há tensão com a redação geral da Resolução 957/2022. Marcado como **em aberto para reconciliação** (V11).

**Nova falha 5 — CAGED/RAIS como bases normativas → CORRIGIDO**
Corrigido: bases normativamente citadas na Resolução 957/2022 para aferição automática de critérios são **CNIS, FGTS, GFIP, eSocial e documento judicial**. CAGED e RAIS removidos como bases operacionais confirmadas; mantidos apenas como hipótese [I].

**Nova falha 6 — "MTE/SPPE" como sigla institucional → CORRIGIDO**
Substituído por "MTE / área responsável pela gestão de benefícios do SD" em referências institucionais, salvo quando citando norma específica que usa a sigla.

**Nova falha 7 — Transbordo para humano como fato → CORRIGIDO**
Separado: "atendimento humano disponível no canal Caixa Cidadão" é fato [O] (horário publicado); "transbordo após submenu de Seguro-Desemprego com demanda específica" é hipótese [I] a validar (V3).

**Nova falha 8 — SMS de crédito sem evidência suficiente → CORRIGIDO**
Todos os SMS classificados como [I] — prática possível, não verificada por fonte oficial. Removidos de evidências físicas sem ressalva. Mantidos na tabela de evidências com marcação explícita.

**Nova falha 9 — Recurso de 120 dias apenas para indeferimento → CORRIGIDO**
Veja 3.3 residual acima. Expandido para indeferimento, montante, suspensão e cancelamento.

**Nova falha 10 — "Reemissão via canal do agente pagador" → CORRIGIDO**
Reformulado: "Canal de solicitação de reemissão: **em aberto**. A Resolução 957/2022 prevê que parcela devolvida pode ser reemitida por solicitação do beneficiário ou decisão judicial, mas não especifica o canal. Não atribuído à Caixa sem fonte." (V9)

---

## Eixo 1 — Dois Front Stages: Caixa (pagamento/consulta) e MTE (concessão/recurso)

> **Princípio interpretativo:** O cidadão percebe um único serviço ("Seguro-Desemprego"), mas interage com dois sistemas institucionalmente distintos. Confundir os dois é o fail point estrutural central (F18).

### 1.1 Mapa de canais

| Canal | Operador | Função | Horário | Evidência |
|---|---|---|---|---|
| **0800-726-0207** (Caixa Cidadão) | Caixa | Consulta de parcelas, pagamento, saque, transferência para humano | 24h (automático); seg–sex 8h–21h e sáb 10h–16h (humano) | [O] |
| **0800-726-2492** | Caixa | Atendimento a PcD auditiva/fala; escopo para SD: **em aberto** | A verificar | [O] canal; [I] escopo SD |
| **158** (Central Alô Trabalho) | MTE | Informações sobre SD, CTPS Digital, gov.br, CAGED; agendamento presencial para recurso; canal principal para doméstico | Dias úteis | [O] |
| **gov.br / CTPS Digital** | MTE | Requerimento (trabalhador formal), acompanhamento, recurso, notificações digitais | 24h | [N] |
| **SINE-Fácil** | MTE | Solicitação, consulta e recurso (canal digital MTE) | 24h | [O] FAQ gov.br |
| **App Benefícios Sociais CAIXA** | Caixa | Informações, calendário, consulta de situação de parcelas | 24h | [O] |
| **CAIXA Tem** | Caixa | Conta digital, movimentação de saldo de parcelas | 24h | [O] |
| **Agências / lotéricas / CAIXA Aqui** | Caixa | Saque e pagamento presencial | Horário comercial | [O] |
| **SINE / SRTE / postos autorizados** | MTE | Requerimento presencial (exceção); recurso | Dias úteis | [N] |

**Modalidade doméstica [tensão normativa resolvida — V11]:** 
- Trabalhador formal: canais digitais (gov.br/CTPS Digital) conforme Resolução 957/2022 [N].
- Empregado doméstico: deve agendar atendimento presencial pela **central 158** (conforme FAQ operacional público do gov.br) [O].

A FAQ pública do gov.br afirma explicitamente: "Empregado Doméstico: deverá agendar atendimento presencial pela central 158." Essa orientação está em tensão com a redação geral da Resolução 957/2022, que trata requerimento digital como regra. A prática operacional pública (FAQ) toma precedência por refletir execução atual.

### 1.2 Pré-jornada: o empregador no Empregador Web [N]

Antes de qualquer interação do trabalhador, o **empregador** transmite os dados da rescisão ao MTE via **Empregador Web** (certificado digital ICP-Brasil), conforme Resolução CODEFAT nº 957/2022. Dados transmitidos incluem: nome, nome da mãe, PIS/NIS, CPF, data de nascimento, sexo, endereço, CTPS, datas de admissão/demissão, salários, CBO, meses trabalhados. O empregador deve disponibilizar cópia do formulário ao trabalhador. Erros nessa transmissão causam bloqueios na habilitação automática — **Fail Point F0 [N]**.

### 1.3 Requerimento normativo [N]

O trabalhador formal deve se cadastrar no **portal gov.br** ou **Carteira de Trabalho Digital** e acessar o serviço "solicitar o seguro-desemprego". O atendimento presencial (SINE/SRTE) é exceção para quem não consegue usar meios digitais. O serviço de recurso digital exige **conta gov.br nível Prata ou Ouro**.

### 1.4 ⚠ Hipótese: fluxo de menus URA 0800-726-0207 [I]

> **Nenhum item abaixo foi confirmado** por gravação, transcrição, árvore de URA, manual operacional ou ligação-teste. Este roteiro é **hipótese a testar** (ver lista de validações pendentes, seção final), não AS-IS verificado.

| Etapa | Ação do cidadão | O que pode ocorrer na URA (hipótese) |
|---|---|---|
| 1 | Discagem para 0800-726-0207 | Saudação automática |
| 2 | Menu principal | Opções por DTMF; cidadão identifica opção para benefícios/Seguro-Desemprego |
| 3 | Autenticação | Dado(s) pessoal(is) de validação — **mecanismo exato: em aberto** |
| 4 | Submenu | Opções de consulta de parcelas, pagamento, transferência para humano — **conteúdo exato: em aberto** |
| 5 | Resolução ou fila | Informação automatizada ou fila para atendente humano |

**Atendimento humano disponível no canal [O]:** seg–sex 8h–21h e sáb 10h–16h (publicado pela Caixa) [O]. Escopo de competência [N]: atendente Caixa resolve apenas consultas de pagamento e saque, **não decide concessão** — demandas de concessão/recurso devem ser redirecionadas para MTE/gov.br/158. Critério exato de transbordo: **em aberto [I]** (requer teste de atendimento ou manual operacional).

### 1.5 Desfechos típicos da jornada

| Desfecho | Descrição | Evidência |
|---|---|---|
| Resolução automatizada na URA | Informação de saldo/data de crédito sem transferência | [I] |
| Transferência para atendente Caixa | Demanda não coberta pela URA ou opção do cidadão | [O] canal existe; [I] fluxo específico |
| Redirecionamento para outro canal | URA orienta App Benefícios Sociais CAIXA, CAIXA Tem, gov.br, 158 | [I] |
| Abandono / encerramento sem resolução | Fila longa, falha de autenticação, loop ou queda | [A] |
| Cidadão no canal errado (F18) | Demanda de concessão/recurso trazida ao 0800; redirecionamento para 158/gov.br sem resolução | [N]/[I] |

---

## Eixo 2 — Processos de Bastidor (Backstage)

### 2.1 Sistemas referenciados

| Sistema | Finalidade | Evidência |
|---|---|---|
| **Empregador Web (MTE)** | Transmissão de dados da rescisão pelo empregador | [N] Res. 957/2022 |
| **CNIS** | Validação de vínculo, salários, tempo de trabalho | [N] |
| **eSocial** | Confirmação de rescisão, motivo, data de demissão | [N] Res. 957/2022 |
| **FGTS / GFIP** | Aferição automática de critérios de elegibilidade | [N] Res. 957/2022 |
| **Documento judicial** | Aferição de critérios em casos específicos | [N] Res. 957/2022 |
| **Sistema SD (MTE / área responsável)** | Status do requerimento, parcelas, bloqueios | [N] existência; [I] arquitetura interna |
| **Gov.br / CTPS Digital** | Requerimento, notificações, autenticação do cidadão | [N] Res. 957/2022 |
| **Dataprev** | Opera sistemas de processamento dos requerimentos | [I] — mencionada em docs TCU; arquitetura em aberto |
| **Sistemas Caixa (pagamento)** | Crédito em conta, saldo de parcelas, comprovação | [I] arquitetura interna em aberto |
| **INSS** | Verificação de acúmulo de benefício previdenciário (critério de suspensão) | [N] critério; [I] integração técnica |
| **CAGED / RAIS** | Bases analíticas históricas — **não citadas como bases operacionais na Res. 957/2022** | [I] |

### 2.2 Atores de bastidor

**Empregador / ex-empregador:** Transmite dados via Empregador Web [N]. Primeiro elo e primeira fonte de falha (F0).

**MTE / área responsável pela gestão de benefícios do SD:** Decide elegibilidade, processa habilitação automática ou manual, gere recursos administrativos, emite notificações digitais, opera 158, gov.br/CTPS Digital e unidades presenciais [N].

**Dataprev:** Opera sistemas de processamento dos requerimentos (arquitetura exata: **em aberto**) [I].

**Caixa — agente pagador:** Executa pagamento conforme indicação do MTE; arquiva comprovantes por cinco anos [N]; mantém URA e canal humano; trata bloqueios operacionais de pagamento (conta incorreta, parcela devolvida ao FAT) [N/I].

> **Regra estrutural:** A Caixa não decide concessão nem elegibilidade. Exceções de concessão/recurso seguem para MTE/gov.br/CTPS Digital/SRTE/SINE. Exceções de pagamento/saque seguem para o agente pagador Caixa. Fluxo interno Caixa→MTE com etapas detalhadas (registro de ocorrência, ticket, SLA) é **hipótese não comprovada** e está fora deste blueprint.

### 2.3 Recurso administrativo [N]

Competência do MTE. Prazo: **120 dias** contados da notificação — para indeferimento, montante incorreto, suspensão **ou cancelamento** (Resolução 957/2022). Canal: gov.br ou CTPS Digital. Requisito: conta gov.br **nível Prata ou Ouro**. Agendamento presencial para recurso: central **158**.

### 2.4 Ciclo de pagamento [N]

- Pagamento: crédito em conta indicada pelo trabalhador, conta digital (CAIXA Tem) ou outra conta localizada pelo agente pagador; se impossível, outras formas disponíveis
- Parcela disponível: **67 dias** após liberação
- Após 67 dias sem saque: devolvida ao FAT
- Reemissão: possível em até **dois anos** por solicitação do beneficiário ou decisão judicial — canal de solicitação: **em aberto**, não atribuído à Caixa sem fonte [N prazo; I canal]
- Comprovação: autenticação em documento próprio ou registro eletrônico, arquivado pelo agente pagador por **cinco anos** [N]
- Suspensão normativa [N]: novo emprego com salário formal, benefício previdenciário de prestação continuada, recusa injustificada de ações de orientação/recolocação/qualificação
- Cancelamento normativo [N]: recusa de emprego condizente, falsidade, fraude, morte, fim da suspensão contratual

### 2.5 Finalidade ampla do programa [N]

A Resolução 957/2022 define a finalidade do SD como incluindo ações de **orientação, recolocação e qualificação profissional** — não apenas pagamento. Relevante porque recusa a essas ações pode causar **suspensão** do benefício, fail point que o trabalhador pode desconhecer ao ligar consultando "por que parei de receber" (F23).

---

## Eixo 3 — Evidências Físicas (Physical Evidence)

| Etapa | Artefatos / evidências | Evidência |
|---|---|---|
| **Pré-jornada (empregador)** | Formulário transmitido via Empregador Web; cópia do formulário disponibilizada ao trabalhador pelo empregador; TRCT | [N] |
| **Requerimento (canal MTE)** | Login gov.br; tela do serviço "solicitar o seguro-desemprego" (gov.br ou CTPS Digital); comprovante de solicitação gerado pelo sistema; app Carteira de Trabalho Digital | [N] / [O] |
| **Notificação de resultado** | Notificação digital via gov.br/CTPS Digital (canal normativo principal); presumida válida após 5 dias da disponibilização [N]; comunicação por outros meios: exceção não detalhada na norma | [N] |
| **Discagem e menu URA** ⚠ | Tela do celular com número discado; áudio da URA | [O] canal; [I] conteúdo |
| **Autenticação na URA** ⚠ | Dado(s) pessoal(is) fornecido(s) verbalmente — mecanismo em aberto | [I] |
| **Consulta automatizada na URA** ⚠ | Informação oral da URA | [I] |
| **Atendimento humano Caixa** ⚠ | Número de protocolo verbal — envio automático por SMS/e-mail: não verificado | [A] / [I] |
| **Pagamento liberado** | Extrato no App Benefícios Sociais CAIXA / CAIXA Tem; comprovante de saque em agência/lotérica; registro eletrônico arquivado pelo agente pagador por 5 anos | [O] / [N] |
| **SMS / push de crédito** | Prática possível — não verificada por fonte oficial | [I] |
| **Exigência documental** | Notificação digital via gov.br/CTPS Digital; presumida válida após 5 dias [N] | [N] |
| **Recurso por indeferimento / suspensão / cancelamento** | Comprovante de protocolo de recurso via gov.br; conta gov.br Prata ou Ouro exigida; prazo 120 dias; agendamento via 158 | [N] / [O] |
| **Parcela expirada / reemissão** | Registro de devolução ao FAT após 67 dias; solicitação de reemissão — canal em aberto; prazo até 2 anos | [N] prazo; [I] canal |

---

## Eixo 4 — Normativos Aplicáveis

### 4.1 Base legal primária

- **Lei nº 7.998/1990** — Institui o Programa Seguro-Desemprego e o Abono Salarial; cria o FAT.
- **Lei nº 8.900/1994** — Altera número de parcelas (até 5).
- **Lei nº 13.134/2015** — Altera prazos de carência e parcelas conforme histórico de requerimentos.
- **Lei Complementar nº 150/2015** — Contrato de trabalho doméstico; base para modalidade específica do SD.
- **Lei nº 10.779/2003** — SD para pescador artesanal durante período de defeso.
- **Decreto-Lei nº 2.284/1986** — Introdução histórica do SD.
- **Decreto nº 92.608/1986** — Regulamentação histórica.

### 4.2 Normativo operacional central

- **Resolução CODEFAT nº 957/2022** (vigor: 3 out. 2022) — Concessão, processamento e pagamento do Programa SD. Revogou a Resolução nº 467/2005 e cadeia normativa anterior. **Referência central para o blueprint AS-IS em 2026.**

### 4.3 Proteção de dados e segurança

- **Lei nº 13.709/2018 (LGPD)** — Tratamento de dados pessoais nos sistemas de requerimento e autenticação.
- **Resolução BCB nº 85/2021** — Segurança cibernética e terceirização de dados para IF; aplicável à infraestrutura tecnológica da Caixa, **não** diretamente às regras de atendimento telefônico.

### 4.4 Atendimento e defesa do usuário

- **Decreto nº 11.034/2022** — Regula o SAC de fornecedores de serviços regulados (revogou o Decreto nº 6.523/2008); aplicável à dimensão bancária/consumerista da Caixa.
- **Lei nº 13.460/2017** — Código de Defesa do Usuário de Serviços Públicos; aplicável à dimensão de serviço público do benefício trabalhista. Hierarquia entre as duas normas para este canal: **em aberto, requer análise jurídica específica**.

### 4.5 Acessibilidade

- **Lei nº 13.146/2015 (LBI)** — Art. 63: atendimento ao cliente em formatos acessíveis.
- **Decreto nº 6.949/2009** — Convenção da ONU sobre direitos de pessoas com deficiência.
- **Normas ANATEL** sobre acessibilidade em serviços telefônicos.

---

## Eixo 5 — Fail Points

### Sistema de classificação de evidência

- **[N]** Normativo | **[O]** Oficial de canal | **[A]** Relato anedótico | **[I]** Inferência | **⚠** Pendente de validação empírica da URA

| # | Fail Point | Formulação | Impacto | Evidência |
|---|---|---|---|---|
| **F0** | Dados errados transmitidos pelo empregador no Empregador Web | Nome, PIS/NIS, CPF, data de nascimento, CBO, salários ou datas incorretos bloqueiam habilitação automática antes da jornada do trabalhador | Alto — bloqueia antes da ligação | [N] |
| **F1** ⚠ | Loop de menu sem saída para atendente | Cidadão é redirecionado ao menu principal sem conseguir ser transferido | Alto | [A] |
| **F2** ⚠ | Menus confusos para baixo letramento digital / idosos | Terminologia técnica, velocidade de locução e timeout excluem parte do público | Alto para o grupo | [A]/[I] |
| **F3** ⚠ | Encerramento abrupto da chamada | Desconexão sem aviso e sem retorno; retrabalho total | Alto | [A] |
| **F4a** | Inconsistência cadastral que impede habilitação automática | Divergência de dados entre Empregador Web, CNIS e cadastros MTE gera bloqueio; trabalhador tem direito à revisão e recurso | Alto | [N] |
| **F4b** ⚠ | Falha de autenticação telefônica por dado divergente | Dado(s) na URA não coincidem com cadastro — mecanismo exato da URA em aberto | Alto (se confirmado) | [I] |
| **F5** | Trabalhador não consegue acessar/movimentar conta digital onde o benefício foi depositado | CAIXA Tem criada automaticamente, senha desconhecida, sem smartphone compatível, dificuldade de saque | Alto | [N]/[A] |
| **F6** ⚠ | Indisponibilidade relatada do sistema em períodos de alta demanda | Relatos de "sistema indisponível" em início de mês; "pico temporal" é inferência sem dado de contact center | Alto | [A] |
| **F7** ⚠ | Indisponibilidade de sistemas de backend | Modos de falha distintos: sistema SD, gov.br, CTPS Digital, Empregador Web, Dataprev, sistemas Caixa — causas e impactos próprios | Alto | [I] |
| **F8** ⚠ | Informações divergentes entre canais (URA, App, portal) | Status desatualizado em um canal em relação a outro; gera retrabalho | Médio | [A] |
| **F9** | Atendente Caixa com competência restrita — não decide concessão | Demanda de elegibilidade ou recurso não resolvida; redirecionamento para MTE sem prazo | Alto | [N]/[O] |
| **F10** | Notificação digital não acessada, não compreendida ou presumida válida sem ciência efetiva | Sem acesso ao gov.br, senha perdida, sem dispositivo, ou anuência dada sem compreensão; norma presume validade após 5 dias da disponibilização | Alto para o cidadão central | [N]/[I] |
| **F11** ⚠ | Filas longas para atendente humano | Relatos de esperas longas; sem dado oficial de TME | Alto | [A] |
| **F13** ⚠ | Ausência de protocolo escrito automático após atendimento | Cidadão fica sem rastro formal da interação | Médio | [A] |
| **F14** ⚠ | Canal PcD auditiva/fala (0800-726-2492): escopo para SD não verificado | Canal existe; integração com fluxo específico de SD e divulgação ao público elegível não confirmadas | Em aberto | [O] canal; [I] escopo |
| **F15** ⚠ | Dificuldade de idosos e baixo letramento na navegação URA | Velocidade, timeout, teclado numérico, terminologia | Alto para o grupo | [A]/[I] |
| **F16** | Queda de chamada por sinal precário — retrabalho total | Obriga reinício completo, incluindo nova autenticação e nova espera | Alto em regiões afetadas | [I] |
| **F17** | Recurso administrativo desconhecido pelo trabalhador | Trabalhador não sabe que tem 120 dias e canal no gov.br para indeferimento, montante, suspensão e cancelamento; exige conta gov.br Prata ou Ouro | Alto | [N]/[I] |
| **F18** | Cidadão no canal errado: 0800 Caixa para demanda que exige 158/MTE | Canal de pagamento não resolve demanda de concessão; redirecionamento sem resolução; recontato | Alto — fail point estrutural | [N] |
| **F19** | Parcela expirada (67 dias) devolvida ao FAT — trabalhador não sabe solicitar reemissão | "Parcela sumiu"; reemissão possível em até 2 anos, mas canal de solicitação em aberto | Alto | [N] prazo; [I] canal |
| **F20** | Contestação de recebimento de parcela desconhecida pelo trabalhador | Fraude, erro bancário, saque indevido ou desconhecimento do crédito; norma prevê contestação administrativa | Alto em casos afetados | [N] |
| **F21** | Bloqueio de conta gov.br — impede requerimento normativo principal | Falha de login, recuperação de senha, nível de conta insuficiente, dados desatualizados | Alto — corta acesso antes da URA | [N]/[I] |
| **F22** | Perda de prazo para requerimento por desinformação ou canal errado | Formal: 7–120 dias após demissão; doméstico: 7–90 dias; orientação errada causa perda definitiva | Alto | [N] |
| **F23** | Suspensão por recusa de ação de recolocação — trabalhador desconhece a causa | Trabalhador liga "sem receber" sem saber que recusa de qualificação/recolocação causa suspensão | Médio | [N] |
| **F24** | Trabalhador não sabe se está abrangido por prolongamento excepcional de parcelas | Prolongamento de até 2 meses depende de ato normativo específico e situação excepcional — não é direito individual automático | Médio — depende do contexto | [N] situação; [I] aplicação individual |

### Métricas necessárias para blueprint quantificado — indisponíveis publicamente

| Métrica | Para validar fail points |
|---|---|
| Chamadas ofertadas, atendidas, abandonadas ao 0800-726-0207 | F1, F11 |
| TME (Tempo Médio de Espera) | F11 |
| TMA (Tempo Médio de Atendimento) | F9 |
| FCR (First Call Resolution) | F9, F18 |
| Taxa de recontato em 7 e 30 dias (por CPF) | F1, F8, F18 |
| Erros de autenticação por CPF | F4b |
| Volume de transferências para MTE/outros canais | F18 |
| Parcelas devolvidas ao FAT por período | F19 |
| Volume de recursos administrativos por tipo (indeferimento/suspensão/cancelamento) | F17 |
| SMS/push emitidos e entregues | F10 |

---

## Fontes e Referências

### Fontes normativas
- **Resolução CODEFAT nº 957/2022** — norma operacional vigente central
- **Lei nº 7.998/1990**: planalto.gov.br/ccivil_03/leis/L7998.htm
- **Lei nº 13.134/2015**: planalto.gov.br/ccivil_03/_Ato2015-2018/2015/Lei/L13134.htm
- **Lei Complementar nº 150/2015**: planalto.gov.br/ccivil_03/leis/lcp/Lcp150.htm
- **Lei nº 10.779/2003**: planalto.gov.br/ccivil_03/leis/2003/L10.779.htm
- **Lei nº 13.709/2018 (LGPD)**: planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/L13709.htm
- **Lei nº 13.146/2015 (LBI)**: planalto.gov.br/ccivil_03/_ato2015-2018/2015/lei/l13146.htm
- **Lei nº 13.460/2017**: planalto.gov.br/ccivil_03/_ato2015-2018/2017/lei/L13460.htm
- **Decreto nº 11.034/2022**: planalto.gov.br

### Fontes oficiais de canal
- **Caixa — Seguro-Desemprego**: caixa.gov.br/beneficios-trabalhador/seguro-desemprego
- **Gov.br — solicitar o seguro-desemprego**: gov.br/pt-br/servicos/solicitar-o-seguro-desemprego
- **Gov.br — FAQ Seguro-Desemprego**: FAQ sobre prazo, modalidades, recurso, doméstico, SINE-Fácil
- **MTE / Portal Emprega Brasil**: empregabrasil.mte.gov.br
- **CGU — Fala.BR**: falabr.cgu.gov.br
- **Ouvidoria da Caixa**: 0800-725-7474
- **SAC da Caixa**: 0800-726-0101
- **Caixa — PcD auditiva/fala**: 0800-726-2492
- **Central Alô Trabalho (MTE)**: 158

### Fontes de hipótese [A] — relatos anedóticos, apenas para geração de hipóteses
- **Reclame Aqui — Caixa Econômica Federal**: reclameaqui.com.br
- **Procon estaduais** — relatórios de reclamações
- **Reportagens jornalísticas**: Agência Brasil, G1/Globo, UOL Economia (2020–2024)

### Insumo de atores (escopo limitado)
- **C_mapa_atores.md** — Mapa de Atores v1.0 (exercício 2.1). Usado exclusivamente para cobertura de stakeholders, não como evidência de funcionamento operacional.

---

## Itens pendentes de validação (lista consolidada)

Os itens abaixo impedem um blueprint AS-IS definitivo da URA. Enquanto não validados, o Eixo 1 é hipótese operacional, não jornada real.

| # | O que validar | Como validar |
|---|---|---|
| V1 | Árvore real da URA: opções, ordem, linguagem, timeout, loop, callback, encerramento | Ligação-teste documentada ou manual operacional da Caixa |
| V2 | Mecanismo de autenticação: quais dados, timeout, alternativas, erros possíveis | Ligação-teste ou documentação interna |
| V3 | Critério de transbordo URA → atendente: quando, se há bloqueio por horário, se há fila por tipo de demanda | Documentação interna ou teste |
| V4 | Escopo do atendente humano Caixa: o que consulta, resolve, registra, redireciona | Roteiro interno ou auditoria CGU/TCU |
| V5 | Protocolo: emitido sempre, verbal, SMS, e-mail, permite acompanhamento | Teste de atendimento humano |
| V6 | Fluxo Caixa → MTE: existe encaminhamento formal ou apenas orientação oral ao cidadão | Documentação de processo ou auditoria |
| V7 | Latência MTE/Dataprev/Caixa: batch, cache, D+0/D+1, janelas de atualização | Arquitetura técnica ou auditoria TCU |
| V8 | Escopo do 0800-726-2492 para SD: horário, competência, integração | Ligação-teste ou documentação Caixa |
| V9 | Canal de solicitação de reemissão de parcela devolvida ao FAT | Documentação operacional Caixa ou MTE |
| V10 | SMS/push/e-mail: existência, gatilhos, cobertura, opt-in, confiabilidade | Fonte oficial ou teste |
| V11 | Modalidade doméstica: reconciliar Resolução 957/2022 com FAQ gov.br (presencial via 158 vs. digital) | Consulta direta ao MTE ou FAQ atualizado |
| V12 | Métricas de contact center (TME, TMA, FCR, recontato, abandono, erros de autenticação) | Dados internos da Caixa ou pedido LAI |

---

## Tabela de mapeamento: camadas do blueprint × fontes desta v3

| Camada do Blueprint | Fonte nesta v3 | Nível de confiança |
|---|---|---|
| **Ações do cidadão** | Eixo 1 — fluxo normativo MTE/gov.br [N]; fluxo URA ⚠ hipótese [I] | Alto (MTE/gov.br); baixo (URA) |
| **Linha de visibilidade** | Eixo 1 + Eixo 3 | Alto (normativo); baixo (URA) |
| **Ações de bastidor** | Eixo 2 — sistemas [N]; duas trilhas comprovadas [N]; fluxo interno Caixa removido do AS-IS | Médio |
| **Sistemas de suporte** | Eixo 2.1 [N para bases da Res. 957/2022]; [I] para arquitetura técnica | Médio |
| **Evidências físicas** | Eixo 3 — normativas [N]; URA ⚠ hipótese [I] | Alto (normativo); baixo (URA) |
| **Fail points** | Eixo 5 — 24 fail points classificados por evidência | Variado; F0, F4a, F9, F17–F23 baseados em normativos |
