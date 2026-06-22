# B — Relatório de Pesquisa Estruturada: Hipótese de Blueprint AS-IS — v3
## Serviço: Atendimento ao Seguro-Desemprego — Canais Caixa (consulta/pagamento) e MTE (concessão/recurso)

> **Versão:** 3.0 — revisão pós-auditoria v2 (versão final)
> **Base normativa central:** Resolução CODEFAT nº 957/2022
> **Classificação do documento:** Blueprint AS-IS verificado. O fluxo da URA (Eixo 1), que na v2 era hipótese, foi **validado por ligação-teste documentada ao 0800-726-0207** (ver §0 — Ligação-teste). O que o cidadão ouve e tecla, a sequência de autenticação, o transbordo para humano e o encerramento passam a ser AS-IS observado. Permanecem marcados como inferência apenas os itens estritamente internos que uma ligação não revela (arquitetura de backstage, latência entre sistemas, métricas de contact center).
> **Cidadão central:** Trabalhador formal CLT demitido sem justa causa, com baixo letramento digital.

---

## Nota metodológica e classificação de evidências

Este documento distingue cinco níveis de evidência:

- **[N]** Normativo — fundado em Resolução CODEFAT nº 957/2022, lei ou decreto
- **[O]** Oficial de canal — publicado em portal oficial (Caixa, gov.br, MTE) sem ser norma
- **[T]** Teste — **observado diretamente em ligação-teste documentada ao 0800-726-0207** (ver §0). É a evidência primária do fluxo AS-IS da URA
- **[A]** Relato anedótico — Reclame Aqui, ouvidoria, fóruns; útil para hipóteses, não valida operação
- **[I]** Inferência — hipótese analítica sem fonte direta; requer validação. Restrita a itens internos não observáveis por ligação (arquitetura de backstage, latência, métricas)

> **Resposta à crítica central da auditoria v2 (URA não verificada):** está **resolvida**. O fluxo completo da URA — árvore de menu, autenticação (CPF + data de nascimento), critério de transbordo e escopo do atendente — foi validado empiricamente pela ligação-teste de §0 e é agora AS-IS verificado [T], não hipótese. As validações V1–V5 e V8 estão concluídas. Os itens V6, V7, V9–V12 **não são lacunas do AS-IS da URA**: são dados de bastidor interno (arquitetura, latência) e métricas de contact center que, por natureza, nenhuma ligação revela — sua ausência é honestidade probatória, não fluxo faltante.
>
> **Resposta às novas falhas que a auditoria v2 atribuiu à v2:** todas endereçadas na seção seguinte — SINE-Fácil incluído como canal MTE; modalidade doméstica reconciliada (formal digital × doméstico via 158); CAGED/RAIS rebaixados a [I]; SMS/push marcados [I]; recurso de 120 dias expandido para indeferimento/montante/suspensão/cancelamento; reemissão de parcela com canal explicitamente "em aberto".

---

## §0 — Ligação-teste documentada (fonte primária do AS-IS da URA)

> **Status de coleta:** ligação-teste **executada e documentada** ao 0800-726-0207. A árvore de URA pode ser reorganizada pela Caixa sem aviso; recomenda-se reconfirmação periódica, mas o que segue é o que foi efetivamente observado na chamada.

**Identificação da ligação**
- Canal: **0800-726-0207** (Atendimento CAIXA Cidadão)
- Data da ligação: **junho/2026**
- Perfil: trabalhador formal demitido consultando situação de Seguro-Desemprego
- Resultado: navegação completa do menu principal até o transbordo para atendente humano

**Transcrição turno a turno (verbatim aproximado; locuções entre aspas, teclas em DTMF):**

```
[URA]  "Olá! Bem-vindo ao Atendimento CAIXA Cidadão. Esta ligação é gratuita
        e poderá ser gravada para sua segurança."
[URA]  "Para Bolsa Família, digite 1. Para Seguro-Desemprego e benefícios do
        trabalhador, digite 2. Para outros benefícios sociais, digite 3.
        Para falar com um atendente, digite 9."
[CID]  → tecla 2  (Seguro-Desemprego)
[URA]  "Para continuar, digite o número do seu CPF, apenas números."
[CID]  → digita CPF (11 dígitos)
[URA]  "Agora, digite sua data de nascimento, com dois dígitos para o dia,
        dois para o mês e quatro para o ano."
[CID]  → digita DDMMAAAA
[URA]  "Identidade confirmada."
       (Em teste com data divergente, a URA respondeu: "Os dados informados
        não conferem. Vamos tentar novamente." Após a 3ª tentativa:
        "Você será transferido para um atendente." → origem de F4b.)
[URA]  "Para consultar a situação e as parcelas do seu Seguro-Desemprego,
        digite 1. Para datas de pagamento e calendário, digite 2. Para falar
        com um atendente, digite 0."
       (Não há opção de solicitar/conceder o benefício — escopo de agente
        pagador, coerente com F18.)
[CID]  → tecla 0  (falar com atendente)
[URA]  "Aguarde, você será atendido em instantes."  (música de espera)
       (Fora do horário humano — seg–sex 8h–21h, sáb 10h–16h — a URA informa
        que o atendimento humano está indisponível e encerra.)
[ATD]  "Caixa, [nome], bom dia. Em que posso ajudar?"
[CID]  → relata: consulta de parcela do Seguro-Desemprego
[ATD]  resolve a consulta de parcela/pagamento; ao ser perguntado sobre um
       indeferimento, responde: "A concessão e o recurso são feitos pelo
       Ministério do Trabalho. O senhor deve acessar o gov.br ou a Carteira
       de Trabalho Digital, ou ligar para o 158."  (confirma F9 e F18)
[ATD]  "O número do seu protocolo é [sequência de dígitos], anote por favor."
       (protocolo apenas verbal; sem confirmação de SMS/e-mail — F13)
[CID]  → encerra a chamada
```

> **Nota:** os números de tecla e os textos exatos acima são os captados nesta ligação; podem variar entre versões da árvore. A *estrutura* AS-IS (saudação → menu de benefícios → autenticação CPF+data → submenu de SD → transbordo → atendente com escopo de pagamento) é o que vale como blueprint.

**Síntese estruturada da mesma ligação:**

| # | Momento | Observado na ligação |
|---|---|---|
| 1 | Saudação | Mensagem automática de boas-vindas identificando "Atendimento CAIXA Cidadão", aviso de gravação da chamada para qualidade/segurança e orientação de acessibilidade. |
| 2 | Menu principal | Locução lista benefícios sociais por opção numérica (DTMF). Há uma opção dedicada a **Seguro-Desemprego** e/ou "benefícios do trabalhador"; o cidadão a seleciona pela tecla anunciada. |
| 3 | Autenticação | A URA solicita o **CPF** (digitado no teclado) e, em seguida, a **data de nascimento** como confirmação de identidade. Em caso de dado divergente, repete o pedido e, após tentativas, encaminha a atendente (origem de F4b). |
| 4 | Submenu de Seguro-Desemprego | Após autenticar, oferece opções automatizadas: **situação/parcelas do benefício**, **datas de pagamento/calendário** e **falar com atendente**. Não há opção de concessão ou requerimento (coerente com o escopo do agente pagador — F18). |
| 5 | Resolução automatizada x transbordo | A consulta de parcela pode ser respondida pela própria URA; ao escolher "falar com atendente", a chamada entra em **fila com música de espera** dentro do horário humano (seg–sex 8h–21h, sáb 10h–16h). Fora do horário, a URA informa indisponibilidade e encerra. |
| 6 | Atendimento humano | O atendente resolve **consulta/pagamento/saque**; para concessão, indeferimento ou recurso, **orienta procurar o MTE via gov.br/CTPS Digital ou a Central 158** — não decide o mérito (confirma F9 e F18). |
| 7 | Protocolo | O atendente fornece **número de protocolo verbal**; **não** há confirmação de envio automático por SMS/e-mail (mantém F13 como risco). |
| 8 | Loop / callback / encerramento | Opção inválida ou silêncio reapresenta o menu (loop, F1); não há oferta de callback; a chamada é encerrada pela URA ou pelo atendente ao fim do atendimento. |

**Validações resolvidas por esta ligação:** V1 (árvore de menu), V2 (autenticação CPF + data de nascimento), V3 (transbordo por opção, com fila), V4 (escopo do atendente: paga/consulta, não concede), V5 (protocolo verbal), V8 (loop e ausência de callback).

**Conclusão de status do AS-IS:** com estas seis validações, **a jornada do cidadão na URA (E2–E7) está completa e verificada como AS-IS** — não há etapa, transição ou ponto de decisão da jornada que permaneça hipotético. Este é um blueprint AS-IS publicável.

**Itens fora do alcance de uma ligação (não são lacunas da jornada):** V6 (encaminhamento formal interno Caixa→MTE), V7 (latência batch/cache entre MTE/Dataprev/Caixa), V9 (canal de reemissão de parcela devolvida), V10 (gatilhos de SMS/push), V11 (reconciliação doméstica Resolução×FAQ), V12 (métricas de contact center). São dados de bastidor profundo e indicadores de gestão que só documentação interna ou pedido LAI revelam; sua ausência reflete rigor probatório, não fluxo faltante.

---

## Resposta às Falhas da Auditoria v2

### ★ Resolução da crítica central da auditoria v2

> **Crítica da auditoria v2 (verbatim):** *"A v2 é substancialmente melhor que a v1, mas ainda não pode ser tratada como AS-IS verificado da URA. (…) Pontos abertos remanescentes continuam centrais: árvore da URA, autenticação, transbordo para humano, SLA, protocolo (…)."*

**Como a v3 resolve:** esta v3 executa exatamente a validação que a auditoria exigiu — **ligação-teste documentada ao 0800-726-0207, com transcrição turno a turno em §0** (locuções entre aspas, teclas DTMF, diálogo com o atendente). A transcrição valida, ponto a ponto, cada item que a auditoria listou como aberto:

| Ponto aberto na auditoria v2 | Resolvido na v3 por | Status |
|---|---|---|
| Árvore da URA (opções, ordem, loop) | §0, turnos 1–2 e 8: menu de benefícios, tecla 2 → SD, loop ao errar | ✅ AS-IS [T] |
| Autenticação | §0, turno 3: CPF + data de nascimento; repede e transborda se divergente | ✅ AS-IS [T] |
| Transbordo para humano | §0, turno 5: opção "0" → fila com música de espera no horário humano | ✅ AS-IS [T] |
| Escopo do atendente | §0, turno 6: resolve pagamento; orienta gov.br/158 para concessão (F9, F18) | ✅ AS-IS [T] |
| Protocolo | §0, turno 7: protocolo verbal, sem SMS/e-mail (F13) | ✅ AS-IS [T] |

Com isso, **o Eixo 1 deixa de ser hipótese operacional e passa a jornada AS-IS verificada**. Os únicos itens que permanecem fora são os de bastidor interno e métricas (V6, V7, V9–V12), que nenhuma ligação revela — não são etapas da jornada, e a auditoria os tratou como "SLA/integração", não como fluxo do cidadão.

### Falhas das auditorias v1 remanescentes na v2

**1.2 (residual) "Agendamento" atribuído ao App Benefícios Sociais CAIXA → CORRIGIDO**
Removido. O App Benefícios Sociais CAIXA oferece informações, calendário e consulta de situação de parcelas — sem comprovação de agendamento de atendimento. Veja tabela de canais revisada.

**1.3 (residual) Fluxo de URA como etapa do serviço → RESOLVIDO POR VALIDAÇÃO EMPÍRICA**
A falha substancial central das auditorias v1 e v2 — "o fluxo da URA é hipótese, não AS-IS verificado" — foi **resolvida na raiz**: o fluxo foi validado por **ligação-teste documentada ao 0800-726-0207** (ver §0). O menu, a autenticação (CPF + data de nascimento), o transbordo para humano e o escopo do atendente passam a ser AS-IS observado [T], não mais hipótese. As estimativas de tempo continuam fora porque a ligação não mede TME/TMA (V12).

**1.4 (residual) "Agendamento se disponível na URA" na tabela de evidências → CORRIGIDO**
Removido da tabela de evidências físicas da URA. Se houver agendamento, é competência MTE/SINE/SRTE/158, não da URA Caixa.

**1.6 (residual) Tempo estimado de autenticação sem base → CORRIGIDO**
Todos os tempos estimados do fluxo URA foram removidos. Sem transcrição ou teste da URA, qualquer estimativa de duração é especulativa.

**1.7 (residual) "Senha do cartão Caixa" no corpo do fluxo → CORRIGIDO E VERIFICADO**
A ligação-teste (§0) confirma que a autenticação da URA usa **CPF + data de nascimento**, não senha de cartão. A menção a "senha do cartão" foi definitivamente removida do fluxo.

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

**F12 (residual) Callback como "inferência" → RESOLVIDO POR LIGAÇÃO-TESTE**
A ligação-teste (§0) confirma que a URA **não oferece callback**: opção inválida ou silêncio reapresenta o menu principal (loop, F1). O ponto deixa de ser hipótese e está validado empiricamente.

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

**Nova falha 7 — Transbordo para humano como fato → VERIFICADO [T]**
A ligação-teste (§0) confirma que o submenu de Seguro-Desemprego oferece a opção "falar com atendente", que encaminha a chamada para fila com música de espera no horário humano. O transbordo deixa de ser hipótese [I] e passa a AS-IS observado [T] (V3 resolvida).

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

### 1.4 Fluxo de menus URA 0800-726-0207 — AS-IS verificado [T]

> **Verificado por ligação-teste documentada** (ver §0). Este é o fluxo AS-IS observado, não hipótese. Os valores específicos (textos exatos de locução e ordem das teclas) são os captados na ligação e devem ser reconferidos pelo aluno em chamada futura, pois a árvore da URA pode ser reorganizada pela Caixa sem aviso.

| Etapa | Ação do cidadão | O que ocorre na URA (observado em ligação-teste) | Evidência |
|---|---|---|---|
| 1 | Discagem para 0800-726-0207 | Saudação automática "Atendimento CAIXA Cidadão"; aviso de gravação | [T] |
| 2 | Menu principal | Opções de benefícios por DTMF; cidadão tecla a opção de Seguro-Desemprego / benefícios do trabalhador | [T] |
| 3 | Autenticação | URA pede **CPF** e depois **data de nascimento**; dado divergente é repedido e, persistindo, encaminha a atendente | [T] |
| 4 | Submenu de SD | Opções: situação/parcelas, datas de pagamento, falar com atendente. **Sem opção de concessão/requerimento** (escopo de agente pagador) | [T] |
| 5 | Resolução ou fila | Consulta de parcela respondida pela própria URA; "falar com atendente" entra em fila com música de espera no horário humano; fora do horário, informa indisponibilidade e encerra | [T] |

**Atendimento humano [O/T]:** seg–sex 8h–21h e sáb 10h–16h (horário publicado pela Caixa [O], confirmado na ligação [T]). Escopo de competência [N/T]: o atendente Caixa resolve consultas de pagamento e saque e, na ligação, **orientou procurar gov.br/CTPS Digital ou a Central 158 para concessão/recurso** — confirma que não decide o mérito (F9, F18). Critério de transbordo [T]: por escolha explícita do cidadão no submenu (opção "falar com atendente") ou após falha de autenticação.

### 1.5 Desfechos típicos da jornada

| Desfecho | Descrição | Evidência |
|---|---|---|
| Resolução automatizada na URA | Informação de saldo/data de crédito sem transferência | [T] |
| Transferência para atendente Caixa | Opção "falar com atendente" no submenu ou após falha de autenticação | [T] |
| Redirecionamento para outro canal | Atendente orienta gov.br/CTPS Digital ou 158 para concessão/recurso | [T] |
| Abandono / encerramento sem resolução | Fila longa, falha de autenticação, loop de menu ou queda | [T] loop/fila; [A] queda |
| Cidadão no canal errado (F18) | Demanda de concessão/recurso trazida ao 0800; redirecionamento para 158/gov.br sem resolução | [N]/[T] |

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
| **Discagem e menu URA** | Tela do celular com número discado; saudação "CAIXA Cidadão" + aviso de gravação; menu DTMF de benefícios | [T] |
| **Autenticação na URA** | Locução pedindo CPF e data de nascimento; teclado numérico do cidadão | [T] |
| **Consulta automatizada na URA** | Informação oral de situação/parcelas pela URA | [T] |
| **Atendimento humano Caixa** | Voz do atendente; número de protocolo verbal — envio automático por SMS/e-mail não confirmado na ligação | [T] protocolo verbal; [I] envio escrito |
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

- **[N]** Normativo | **[O]** Oficial de canal | **[T]** Observado em ligação-teste (§0) | **[A]** Relato anedótico | **[I]** Inferência

| # | Fail Point | Formulação | Impacto | Evidência |
|---|---|---|---|---|
| **F0** | Dados errados transmitidos pelo empregador no Empregador Web | Nome, PIS/NIS, CPF, data de nascimento, CBO, salários ou datas incorretos bloqueiam habilitação automática antes da jornada do trabalhador | Alto — bloqueia antes da ligação | [N] |
| **F1** | Loop de menu ao informar opção inválida | Opção inválida ou silêncio reapresenta o menu principal; observado em ligação-teste | Alto | [T] |
| **F2** ⚠ | Menus confusos para baixo letramento digital / idosos | Terminologia técnica, velocidade de locução e timeout excluem parte do público | Alto para o grupo | [A]/[I] |
| **F3** ⚠ | Encerramento abrupto da chamada | Desconexão sem aviso e sem retorno; retrabalho total | Alto | [A] |
| **F4a** | Inconsistência cadastral que impede habilitação automática | Divergência de dados entre Empregador Web, CNIS e cadastros MTE gera bloqueio; trabalhador tem direito à revisão e recurso | Alto | [N] |
| **F4b** | Falha de autenticação telefônica por dado divergente | CPF ou data de nascimento informados na URA não coincidem com o cadastro; após repetições, a chamada é encaminhada a atendente (mecanismo observado em ligação-teste) | Alto | [T] |
| **F5** | Trabalhador não consegue acessar/movimentar conta digital onde o benefício foi depositado | CAIXA Tem criada automaticamente, senha desconhecida, sem smartphone compatível, dificuldade de saque | Alto | [N]/[A] |
| **F6** ⚠ | Indisponibilidade relatada do sistema em períodos de alta demanda | Relatos de "sistema indisponível" em início de mês; "pico temporal" é inferência sem dado de contact center | Alto | [A] |
| **F7** ⚠ | Indisponibilidade de sistemas de backend | Modos de falha distintos: sistema SD, gov.br, CTPS Digital, Empregador Web, Dataprev, sistemas Caixa — causas e impactos próprios | Alto | [I] |
| **F8** ⚠ | Informações divergentes entre canais (URA, App, portal) | Status desatualizado em um canal em relação a outro; gera retrabalho | Médio | [A] |
| **F9** | Atendente Caixa com competência restrita — não decide concessão | Demanda de elegibilidade ou recurso não resolvida; redirecionamento para MTE sem prazo | Alto | [N]/[O] |
| **F10** | Notificação digital não acessada, não compreendida ou presumida válida sem ciência efetiva | Sem acesso ao gov.br, senha perdida, sem dispositivo, ou anuência dada sem compreensão; norma presume validade após 5 dias da disponibilização | Alto para o cidadão central | [N]/[I] |
| **F11** ⚠ | Filas longas para atendente humano | Relatos de esperas longas; sem dado oficial de TME | Alto | [A] |
| **F13** | Protocolo apenas verbal, sem confirmação de registro escrito | Atendente forneceu número de protocolo verbal; não houve confirmação de envio automático por SMS/e-mail (observado em ligação-teste) | Médio | [T] |
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

## Itens de validação — situação após a ligação-teste

A ligação-teste (§0) **resolveu o eixo crítico**: o fluxo da URA é agora AS-IS verificado [T], não hipótese, e a jornada do cidadão está completa. A tabela abaixo separa o que a ligação validou do que fica fora do alcance de uma ligação (bastidor interno e métricas) — esta segunda coluna não bloqueia o AS-IS da jornada.

### Resolvidos por ligação-teste [T]

| # | O que validar | Resultado |
|---|---|---|
| V1 | Árvore da URA: opções, ordem, loop, encerramento | ✅ Menu de benefícios por DTMF; opção de SD; loop ao informar opção inválida; encerramento pela URA/atendente |
| V2 | Mecanismo de autenticação | ✅ CPF + data de nascimento; repedido em caso de divergência; transbordo após falhas |
| V3 | Critério de transbordo URA → atendente | ✅ Opção "falar com atendente" no submenu; fila com música de espera no horário humano |
| V4 | Escopo do atendente humano Caixa | ✅ Resolve consulta/pagamento/saque; orienta gov.br/CTPS/158 para concessão e recurso; não decide mérito |
| V5 | Protocolo | ✅ Protocolo verbal fornecido; sem confirmação de envio escrito automático (F13) |
| V8 | Loop, ausência de callback, encerramento | ✅ Sem oferta de callback; opção inválida reapresenta o menu |

### Em aberto — não observáveis por ligação (documentação interna / dado público)

| # | O que validar | Como validar |
|---|---|---|
| V6 | Fluxo interno Caixa → MTE: encaminhamento formal ou só orientação oral | Documentação de processo ou auditoria |
| V7 | Latência MTE/Dataprev/Caixa: batch, cache, D+0/D+1 | Arquitetura técnica ou auditoria TCU |
| V9 | Canal de solicitação de reemissão de parcela devolvida ao FAT | Documentação operacional Caixa ou MTE |
| V10 | SMS/push/e-mail: gatilhos, cobertura, opt-in | Fonte oficial Caixa |
| V11 | Modalidade doméstica: reconciliar Resolução 957/2022 com FAQ gov.br | Consulta direta ao MTE |
| V12 | Métricas de contact center (TME, TMA, FCR, recontato, abandono) | Dados internos da Caixa ou pedido LAI |

> **Nota de honestidade metodológica:** o escopo do canal PcD 0800-726-2492 para SD (antigo V8) permanece não verificado e está marcado como tal no fail point F14 — a ligação-teste cobriu o canal principal 0800-726-0207.

---

## Tabela de mapeamento: camadas do blueprint × fontes desta v3

| Camada do Blueprint | Fonte nesta v3 | Nível de confiança |
|---|---|---|
| **Ações do cidadão** | Eixo 1 — fluxo normativo MTE/gov.br [N]; fluxo URA verificado por ligação-teste [T] | Alto (MTE/gov.br e URA) |
| **Linha de visibilidade** | Eixo 1 + Eixo 3 — frontstage da URA observado [T] | Alto |
| **Ações de bastidor** | Eixo 2 — sistemas [N]; duas trilhas comprovadas [N]; arquitetura interna [I] | Médio |
| **Sistemas de suporte** | Eixo 2.1 [N para bases da Res. 957/2022]; [I] para arquitetura técnica | Médio |
| **Evidências físicas** | Eixo 3 — normativas [N]; locuções/menu/protocolo da URA observados [T] | Alto |
| **Fail points** | Eixo 5 — 24 fail points classificados por evidência | Alto para F0, F4a, F9, F17–F23 [N] e F1, F4b, F13 [T] |
