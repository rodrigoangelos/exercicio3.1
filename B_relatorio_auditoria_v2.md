Parecer geral

A v2 é substancialmente melhor que a v1, mas ainda não pode ser tratada como AS-IS verificado da URA. Ela corrigiu a maioria dos erros normativos e passou a distinguir melhor Caixa × MTE, fato × hipótese. Porém, ainda há três problemas estruturais:

1. Correções apenas declaradas: vários itens foram marcados como “hipótese/em aberto”, mas continuam aparecendo em tabelas operacionais como se fossem parte do blueprint.
2. Novas afirmações não suportadas: especialmente sobre App Benefícios Sociais CAIXA, SINE-Fácil, CAGED/RAIS, agendamento e métricas/canais.
3. Pontos abertos remanescentes continuam centrais: árvore da URA, autenticação, transbordo para humano, SLA, protocolo, integração PcD e fluxo interno Caixa–MTE.

A base normativa central usada pela v2 — Resolução CODEFAT nº 957/2022 — está correta. Ela prevê requerimento via gov.br/Carteira de Trabalho Digital, recurso administrativo, notificações digitais, papel do Empregador Web, pagamento, devolução ao FAT em 67 dias e reemissão em até dois anos.  

⸻

A) Falhas do audit_v1: foram endereçadas?

Síntese por bloco

Bloco da audit_v1	Resultado na v2	Veredito
1. Erros factuais	Majoritariamente corrigidos	Parcialmente aprovado
2. Inferências mal suportadas	Melhorou a classificação probatória	Parcialmente aprovado
3. Backstage omitido	Corrigiu pontos essenciais	Aprovado com ressalvas
4. Evidências/normativos ausentes	Corrigiu boa parte	Aprovado com ressalvas
5. Fail points omitidos	Ampliou corretamente	Aprovado com ajustes
6. Afirmações jurídicas excessivas	Corrigiu o tom	Aprovado
7. Governança/mensuração	Adicionou lista boa de métricas	Aprovado, mas ainda não operacionalizado

⸻

1. Erros factuais ou afirmações provavelmente falsas

1.1 Canal 111

Trecho v2: “O 111 é canal da Caixa para Bolsa Família/benefícios sociais específicos, não para Seguro-Desemprego. Removido do relatório.”

Veredito: Endereçado.

A Caixa lista o 0800 726 0207 como Atendimento CAIXA Cidadão e o 111 como Atendimento Bolsa Família; logo a remoção foi correta.  

⸻

1.2 “App Caixa Trabalhador”

Trecho v2: “O aplicativo correto para consulta de Seguro-Desemprego é o App Benefícios Sociais CAIXA…”

Veredito: Endereçado, mas com erro novo.

A substituição por App Benefícios Sociais CAIXA está correta: a Caixa informa que o app dá acesso a informações sobre Seguro-Desemprego, Abono Salarial, INSS e Pé-de-Meia.  

Falha nova: a v2 depois atribui ao App Benefícios Sociais CAIXA “agendamento”, sem evidência. O resultado oficial fala em informações, calendário, situação de parcelas e serviços correlatos, não em agendamento de atendimento de Seguro-Desemprego pelo app da Caixa.  

⸻

1.3 Submenu detalhado da URA

Trecho v2: “Marcado como hipótese operacional não verificada.”

Veredito: Parcialmente endereçado.

A v2 reconhece corretamente que não há árvore de URA, gravação ou transcrição. Mas ainda mantém um “fluxo de menus URA” com tempos estimados e etapas. Isso é aceitável como hipótese de pesquisa, não como AS-IS.

Falha residual: a tabela deveria ser rebaixada visualmente para “roteiro de validação” ou “hipótese a testar”, não permanecer dentro da jornada como etapa do serviço.

⸻

1.4 Agendamento presencial pela URA da Caixa

Trecho v2: “Essa opção é removida do submenu hipotético e relocada no fluxo MTE/SINE.”

Veredito: Parcialmente endereçado.

A correção conceitual está certa: requerimento e atendimento presencial pertencem à esfera MTE/SINE/SRTE, não à Caixa. A Resolução 957/2022 prevê requerimento via gov.br/CTPS Digital e, na impossibilidade, atendimento presencial em SRTE/SINE.  

Falha residual/nova: no Eixo 3, a v2 mantém: “Agendamento (se disponível na URA)”. Isso contradiz a correção. Se não há evidência, esse item deveria sair da tabela de evidências físicas da URA.

⸻

1.5 Denúncia de irregularidade na URA

Trecho v2: “Removido do submenu hipotético.”

Veredito: Endereçado.

A v2 corrige adequadamente e desloca denúncia para Fala.BR/Ouvidoria.

⸻

1.6 Autenticação CPF + data de nascimento

Trecho v2: “Marcado como hipótese plausível não verificada.”

Veredito: Parcialmente endereçado.

A v2 parou de afirmar como fato, o que é correto. Mas ainda estima “~60–90 s” para uma autenticação cujo mecanismo é desconhecido.

Falha residual: tempo estimado de autenticação continua sem base.

⸻

1.7 Senha do cartão Caixa

Trecho v2: “Removido como fato; marcado como ponto em aberto.”

Veredito: Endereçado, mas com resíduo.

No Eixo 1.3, a v2 ainda diz: “Clientes com conta Caixa podem ter alternativa por senha — não verificado.” Isso é melhor que a v1, mas ainda mantém um mecanismo sem evidência dentro da jornada.

Correção recomendada: remover do corpo do fluxo e manter apenas em “hipóteses a validar”.

⸻

1.8 Trabalhadores sem conta Caixa

Trecho v2: “Fail point real: trabalhador não consegue acessar ou movimentar conta digital…”

Veredito: Endereçado.

A correção está alinhada à Resolução 957/2022: o pagamento pode ser feito em conta indicada pelo trabalhador; se houver erro ou impossibilidade, pode ser disponibilizado em conta digital ou outra conta localizada pelo agente pagador; e, se isso não for possível, por outras formas disponíveis.  

⸻

1.9 Decreto nº 2.284/1997

Trecho v2: “Referência errada… removida.”

Veredito: Endereçado.

⸻

1.10 Resolução CODEFAT nº 467/2005

Trecho v2: “A norma vigente é a 957/2022.”

Veredito: Endereçado.

A Resolução 957/2022 é corretamente tratada como norma operacional central. Ela revogou a cadeia normativa anterior e estrutura concessão, processamento e pagamento.  

⸻

1.11 Resolução CODEFAT nº 783/2016

Trecho v2: “Referência à 783/2016 removida.”

Veredito: Endereçado.

⸻

1.12 Decreto SAC 2008

Trecho v2: “Referência correta: Decreto nº 11.034/2022.”

Veredito: Endereçado.

O Decreto nº 11.034/2022 revogou expressamente o Decreto nº 6.523/2008.  

⸻

1.13 Aplicabilidade do SAC ao serviço público

Trecho v2: “Aplica-se à dimensão bancária/consumerista… Lei 13.460/2017 à dimensão de serviço público.”

Veredito: Endereçado, com uma impropriedade nova.

A distinção entre camada consumerista/bancária e serviço público é correta. Porém, a v2 usa a expressão “benefício previdenciário-trabalhista”. Seguro-Desemprego não é benefício previdenciário; é benefício/programa trabalhista financiado pelo FAT. A expressão deve ser corrigida para “benefício trabalhista” ou “benefício do Programa do Seguro-Desemprego”.

⸻

1.14 Resolução BCB nº 85/2021

Trecho v2: “Removida como suporte direto a regras de atendimento telefônico.”

Veredito: Endereçado.

⸻

1.15 Cobrança por celular para 0800

Trecho v2: “Removida a afirmação.”

Veredito: Endereçado.

⸻

1.16 Carta de exigência pelos Correios

Trecho v2: “Notificação digital via gov.br/CTPS Digital… carta física é exceção a confirmar.”

Veredito: Endereçado.

A Resolução 957/2022 prevê notificações sobre deferimento, indeferimento ou exigências exclusivamente por meio digital, mediante anuência e cadastramento no gov.br ou na CTPS Digital.  

⸻

1.17 Agências da Caixa para demandas operacionais

Trecho v2: “Agências/lotéricas/CAIXA Aqui e CAIXA Tem são canais de saque e pagamento… requerimento/recurso/elegibilidade são MTE/gov.br/CTPS Digital/SINE/SRTE.”

Veredito: Endereçado.

A própria Caixa distingue sua função de agente pagador e canais de consulta da competência do MTE para concessão/gestão.  

⸻

2. Inferências mal suportadas e fontes fracas

2.1 Espera de 20–60 minutos

Trecho v2: “Hipótese plausível… relatos anedóticos… não há dado oficial de TME.”

Veredito: Parcialmente endereçado.

A v2 removeu a pretensão de “tempo médio”. Bom. Mas chamar de “defendido” é excessivo. O correto seria “mantido apenas como hipótese anedótica”.

⸻

2.2 Atendimento humano 8–12 minutos

Trecho v2: “Removido.”

Veredito: Endereçado.

⸻

2.3 Abandono 15–30%

Trecho v2: “Removida como dado.”

Veredito: Endereçado.

⸻

2.4 Frequência dos fail points

Trecho v2: “Coluna Frequência substituída por Evidência disponível.”

Veredito: Endereçado.

Boa correção metodológica.

⸻

2.5 Reclame Aqui, JusBrasil e fóruns

Trecho v2: “Mantidas como fontes de hipótese.”

Veredito: Endereçado.

A classificação por nível probatório é adequada. Ainda assim, JusBrasil/fóruns deveriam ser removidos da lista principal e mantidos em apêndice de “sinais fracos”, porque não são fontes operacionais.

⸻

2.6 Mapa de atores como fonte factual

Trecho v2: “Usado exclusivamente para cobertura de atores.”

Veredito: Endereçado.

⸻

3. Backstage omitido ou mal modelado

3.1 Empregador / Empregador Web

Trecho v2: “Backstage começa antes da ligação… Empregador Web… certificado digital ICP-Brasil.”

Veredito: Endereçado.

A Resolução 957/2022 prevê transmissão eletrônica exclusiva pelo Empregador Web, com certificado digital ICP-Brasil, e lista os dados transmitidos: nome, nome da mãe, PIS, CPF, data de nascimento, sexo, endereço, CTPS, datas, salários, CBO, meses trabalhados etc.  

⸻

3.2 Requerimento digital via gov.br/CTPS Digital

Trecho v2: “Via normativa principal.”

Veredito: Endereçado, com lacuna nova.

A Resolução 957/2022 sustenta gov.br/CTPS Digital.  

Falha nova: a v2 praticamente omite o SINE-Fácil, que aparece nas Perguntas Frequentes do gov.br como canal de solicitação/consulta/recurso para o trabalhador formal.  

⸻

3.3 Recurso administrativo

Trecho v2: “Prazo de 120 dias contados da notificação.”

Veredito: Endereçado, mas incompleto.

A Resolução 957/2022 prevê recurso em 120 dias contra indeferimento, montante, suspensão ou cancelamento.  

Ponto aberto/nova nuance: a página pública de FAQ do gov.br também fala em “revisão” em até dois anos contados da demissão.   A v2 precisa distinguir:

* recurso administrativo da Resolução 957/2022: 120 dias da notificação;
* revisão/novo documento no FAQ gov.br: até dois anos da demissão;
* reemissão de parcela não sacada: até dois anos da emissão da parcela.

Hoje a v2 usa “120 dias” corretamente, mas simplifica demais o ecossistema de revisão/recurso.

⸻

3.4 Canal 158 do MTE

Trecho v2: “Adicionado ao mapa de canais.”

Veredito: Endereçado.

O serviço de recurso no gov.br aponta a central telefônica 158 para dúvidas e informa que o agendamento presencial para recurso pode passar pela central 158.  

⸻

3.5 Forma de pagamento e reemissão

Trecho v2: “Parcela disponível por 67 dias; devolvida ao FAT; reemissão em até dois anos.”

Veredito: Endereçado.

Está de acordo com a Resolução 957/2022.  

⸻

3.6 Suspensão e cancelamento

Trecho v2: hipóteses normativas corrigidas.

Veredito: Endereçado.

A v2 agora reflete as hipóteses normativas: suspensão por novo emprego, benefício previdenciário continuado e recusa injustificada de ações de recolocação; cancelamento por recusa de emprego condizente, falsidade, fraude, morte e fim da suspensão contratual.  

⸻

3.7 Orientação/recolocação/qualificação

Trecho v2: “Mantido fora do escopo da URA, mas adicionado como contexto normativo.”

Veredito: Endereçado.

A decisão é correta: não é função da URA Caixa, mas pode afetar suspensão do benefício.

⸻

3.8 Fluxo interno de exceções Caixa → MTE

Trecho v2: “Hipótese em aberto.”

Veredito: Parcialmente endereçado.

Reconhecer como hipótese resolve o erro factual. Mas o fluxo ainda aparece como “hipótese plausível” com etapas. Sem documentação, o correto seria manter apenas duas trilhas comprovadas:

* exceção de concessão/recurso → MTE/gov.br/CTPS/SRTE/SINE;
* exceção de pagamento/saque → agente pagador Caixa.

Qualquer “URA registra ocorrência → retaguarda Caixa → MTE” deve ficar fora do blueprint AS-IS.

⸻

4. Evidências físicas e normativos ausentes

4.1 Formulário Empregador Web

Veredito: Endereçado.

A v2 adiciona corretamente o formulário transmitido e disponibilizado ao trabalhador; a norma exige que, após transmissão, o empregador disponibilize o formulário ao trabalhador.  

⸻

4.2 Gov.br e CTPS Digital

Veredito: Endereçado.

⸻

4.3 Notificação digital

Veredito: Endereçado.

⸻

4.4 Protocolo/recurso MTE

Veredito: Endereçado, com ressalva.

A v2 adiciona o protocolo de recurso. Falta incluir o requisito de conta gov.br nível Prata ou Ouro para o serviço de recurso, informado na página gov.br.  

⸻

4.5 Comprovação de pagamento arquivada por cinco anos

Veredito: Endereçado.

A Resolução 957/2022 prevê autenticação/registro eletrônico arquivado pelo agente pagador por cinco anos.  

⸻

4.6 Parcela devolvida ao FAT e reemissão

Veredito: Endereçado.

⸻

4.7 Resolução CODEFAT 957/2022

Veredito: Endereçado.

⸻

4.8 LC 150/2015 e Lei 10.779/2003

Veredito: Endereçado.

⸻

4.9 Canal 158

Veredito: Endereçado.

⸻

4.10 Atendimento PcD auditiva/fala

Veredito: Parcialmente endereçado.

A v2 corrige o excesso jurídico e reconhece o 0800-726-2492 como canal acessível. Mas ainda precisa verificar se esse canal atende Seguro-Desemprego especificamente, se transfere para o 0800 Cidadão, se resolve pagamento, se atende concessão, e qual horário.

⸻

5. Fail points

A maioria dos novos fail points está correta. A inclusão de F0, F17, F18, F19, F20, F21, F22, F23 e F24 melhora bastante o relatório.

Mas há falhas residuais:

F4 — Falha de autenticação por dado cadastral divergente

Trecho v2: “A / N (base cadastral do empregador)”

Problema: há base normativa para divergência cadastral no processo de habilitação, mas não para falha de autenticação na URA, porque o mecanismo da URA é desconhecido.

Correção: classificar como:

* habilitação/recurso por inconsistência cadastral: N;
* falha de autenticação telefônica: I/A, até validação da URA.

⸻

F6 — Indisponibilidade em horários de pico

Trecho v2: “A”

Problema: aceitável como relato, mas insuficiente para “horários de pico”. A v2 deveria separar “indisponibilidade relatada” de “pico temporal inferido”.

⸻

F7 — Indisponibilidade backend

Trecho v2: “I”

Problema: correto marcar como inferência, mas o fail point está amplo demais. Backend de pagamento Caixa, sistema MTE, gov.br, CTPS Digital, Empregador Web e Dataprev têm modos de falha distintos.

⸻

F10 e F21 são duplicados

Trechos v2:
“F10 — Notificação digital não vista…”
“F21 — Notificação digital perdida…”

Falha nova: duplicação substantiva.

Correção: fundir F10 e F21 em um único fail point: “notificação digital não acessada, não compreendida ou presumida como válida sem ciência efetiva”.

A norma torna isso relevante porque a Resolução 957/2022 permite notificação digital e presume válida a notificação após cinco dias da disponibilização no ambiente de acesso.  

⸻

F12 — Ausência de callback

Trecho v2: “I”

Problema: como a árvore da URA não foi validada, a ausência de callback também não foi validada. Deve ser “em aberto”, não “inferência” operacional.

⸻

F13 — Ausência de protocolo escrito automático

Trecho v2: “A”

Problema: continua apoiado apenas em relatos. Não há teste de atendimento humano nem norma interna. Deve ser mantido como hipótese, não como fail point confirmado.

⸻

F24 — Prolongamento excepcional

Trecho v2: “Trabalhador não sabe que tem direito a prolongamento excepcional de parcelas.”

Problema: “tem direito” é formulação excessiva. O prolongamento depende de situação excepcional e ato normativo específico; não é direito individual automático de todo trabalhador. A Resolução 957/2022 prevê prolongamento excepcional por até dois meses, mas a aplicação depende do contexto e de regras específicas.  

Correção: “trabalhador não sabe se está abrangido por prolongamento excepcional autorizado”.

⸻

6. Afirmações jurídicas excessivas

6.1 LBI

Veredito: Endereçado.

A v2 retirou a acusação de descumprimento e reformulou como ponto em aberto.

⸻

6.2 Failure demand

Veredito: Endereçado.

A v2 passou a tratar como hipótese analítica, não como métrica documentada.

⸻

6.3 Latência de atualização

Veredito: Endereçado.

Mantido corretamente como ponto em aberto.

⸻

6.4 Mainframe/base de bloqueios

Veredito: Parcialmente endereçado.

A v2 reconhece como placeholder, mas ainda mantém “Sistemas da Caixa (pagamento)” como inferência. Isso é aceitável em nível conceitual, desde que não use nomes de arquitetura interna.

⸻

7. Controle, governança e mensuração

7.1 Métricas necessárias

Veredito: Endereçado.

A lista de métricas indisponíveis é boa.

Falha residual: falta transformar essa lista em requisitos de evidência por camada do blueprint. Exemplo: para validar F1/F11/F12/F13, precisa de TME, taxa de abandono, callback disponível, protocolos emitidos por contato etc.

⸻

7.2 Plano de validação da URA

Veredito: Parcialmente endereçado.

A v2 reconhece que o Eixo 1 é hipotético. Mas continua chamando o documento de “Service Blueprint AS-IS — v2”.

Correção necessária: renomear para “hipótese de blueprint AS-IS pendente de validação empírica da URA” ou separar em:

* AS-IS normativo MTE/Caixa;
* AS-IS validado por fonte oficial;
* hipótese operacional da URA.

⸻

7.3 Separação Caixa × MTE

Veredito: Endereçado.

Essa é a maior melhora da v2.

⸻

B) Falhas novas introduzidas pela v2

Nova falha 1 — “Único número oficial documentado” é formulação forte demais

Trecho v2: “O único número oficial documentado para o serviço via URA Caixa é o 0800-726-0207.”

Problema: a página do Seguro-Desemprego da Caixa também lista “Alô CAIXA” e outros canais de atendimento, além do 0800 726 0207.  

Justificativa: Se a v2 quer falar de URA Caixa Cidadão, 0800 726 0207 é correto. Se quer falar de canais oficiais Caixa sobre Seguro-Desemprego, “único” é excessivo.

Correção: “O número oficial Caixa Cidadão associado à consulta de benefícios é 0800 726 0207; a página da Caixa também lista outros canais de atendimento Caixa, que devem ser distinguidos por finalidade.”

⸻

Nova falha 2 — App Benefícios Sociais CAIXA com “agendamento”

Trecho v2: “App Benefícios Sociais CAIXA | Consulta de parcelas, extrato, agendamento | 24h.”

Problema: não encontrei suporte oficial para “agendamento” no App Benefícios Sociais CAIXA em Seguro-Desemprego. A Caixa descreve o app como canal para informações, calendário e consulta de situação de parcelas.  

Correção: remover “agendamento”.

⸻

Nova falha 3 — SINE-Fácil omitido ou subtratado

Trecho v2: “gov.br / CTPS Digital | Requerimento, acompanhamento, recurso, notificações.”

Problema: as Perguntas Frequentes do gov.br listam o SINE-Fácil como canal de solicitação, consulta e recurso para trabalhador formal.  

Correção: incluir SINE-Fácil como canal MTE/digital, ou explicar por que foi excluído.

⸻

Nova falha 4 — Doméstico: tratamento ambíguo entre Resolução e FAQ

Trechos v2:
“gov.br / CTPS Digital | Requerimento…”
“Empregado doméstico: prazo de 7 a 90 dias…”

Problema: a v2 não deixa claro que o tratamento do doméstico tem especificidades. A FAQ pública do gov.br afirma: “Empregado Doméstico… deverá agendar atendimento presencial pela central 158.”   Já a Resolução 957/2022 remete o requerimento ao art. 5º, mas também disciplina apresentação presencial em caso de insuficiência de informações.  

Correção: separar explicitamente:

* trabalhador formal: canais digitais;
* doméstico: verificar regra operacional atual do canal, pois há tensão entre redação normativa e FAQ pública;
* SINE/SRTE/158 como fallback ou canal principal conforme modalidade.

⸻

Nova falha 5 — CAGED e RAIS continuam como “normativos” sem base suficiente

Trecho v2:
“eSocial / CAGED — Confirmação de rescisão…”
“RAIS — Histórico de vínculos para elegibilidade — Normativo.”

Problema: a Resolução 957/2022 menciona CNIS, Guia de Recolhimento do FGTS, GFIP, eSocial e documento judicial como meios para aferição automática dos critérios; não encontrei RAIS como base na norma, e CAGED aparece em outro contexto, ligado a estatísticas de representatividade, não como base operacional de confirmação de rescisão para a habilitação automática.  

Correção: trocar por:

* CNIS, FGTS, GFIP, eSocial e documento judicial como bases normativamente citadas;
* CAGED/RAIS apenas como hipótese histórica/analítica, se houver fonte específica.

⸻

Nova falha 6 — “MTE / SPPE” pode estar institucionalmente desatualizado

Trecho v2: “MTE / SPPE: decide elegibilidade…”

Problema: a v2 usa sigla organizacional específica sem demonstrar que essa unidade é a responsável atual em 2026. A Resolução 957/2022 citada usa a estrutura ministerial vigente à época da norma e suas alterações; o relatório deveria evitar sigla de secretaria se não for essencial.

Correção: usar “MTE / área responsável pela gestão de benefícios do Seguro-Desemprego” até validação institucional.

⸻

Nova falha 7 — “Atendimento humano” permanece como parte do fluxo sem validação de escopo

Trecho v2: “Transferência para atendente humano… demanda complexa ou não coberta pela URA.”

Problema: a Caixa informa horário de atendimento humano para Atendimento CAIXA Cidadão, mas isso não prova quais demandas de Seguro-Desemprego o humano resolve, nem se há transferência específica após autenticação da URA.  

Correção: manter “atendimento humano disponível no canal” como fato; manter “transbordo após submenu de Seguro-Desemprego” como hipótese a validar.

⸻

Nova falha 8 — “SMS de crédito” e “SMS proativo” seguem sem evidência

Trecho v2: “eventual SMS proativo de parcela disponível” e “SMS de crédito.”

Problema: a v2 marca um como “não verificado”, mas o outro aparece em evidência de pagamento liberado sem ressalva suficiente.

Correção: classificar SMS como “prática possível/não verificada”, salvo fonte oficial específica.

⸻

Nova falha 9 — Recurso de 120 dias simplificado demais

Trecho v2: “Quando o requerimento é indeferido… trabalhador tem até 120 dias…”

Problema: a Resolução 957/2022 prevê recurso de 120 dias para indeferimento, montante, suspensão ou cancelamento, não só indeferimento.   Além disso, o serviço público de recurso exige conta gov.br Prata ou Ouro.  

Correção: expandir o escopo do recurso e incluir o requisito de nível gov.br.

⸻

Nova falha 10 — “Solicitação de reemissão via canal do agente pagador” não está comprovada

Trecho v2: “solicitação de reemissão via canal do agente pagador (processo exato: em aberto).”

Problema: a norma diz que parcela devolvida pode ser reemitida por solicitação do beneficiário ou decisão judicial, mas não afirma que a solicitação seja feita via canal do agente pagador.  

Correção: “canal de solicitação de reemissão: em aberto; não atribuir à Caixa sem fonte.”

⸻

C) Pontos abertos que ainda restam

Estes continuam críticos e impedem um blueprint AS-IS definitivo:

1. Árvore real da URA 0800 726 0207: opções, ordem, linguagem, timeout, loop, transferência, encerramento.
2. Autenticação real da URA: quais dados são pedidos, se há CPF, data de nascimento, NIS, senha, cartão ou outros fatores.
3. Critério de transbordo para humano: quando a URA oferece atendente, se há bloqueios por horário, se existe fila por tipo de demanda.
4. Escopo do atendente humano Caixa: o que consulta, o que registra, o que resolve, o que redireciona.
5. Protocolo: se é sempre emitido, se é verbal, SMS, e-mail, se permite acompanhamento.
6. Fluxo Caixa → MTE: se existe encaminhamento real de ocorrência ou apenas orientação ao cidadão.
7. Latência entre MTE/Dataprev/Caixa: batch, cache, D+0/D+1, janelas de atualização.
8. Escopo do 0800-726-2492 para Seguro-Desemprego: canal acessível existe, mas integração com esse serviço específico não está comprovada.
9. SINE-Fácil e modalidade doméstica: v2 precisa reconciliar Resolução 957/2022 com FAQ operacional pública do gov.br.
10. Métricas de contact center: TME, TMA, abandono, FCR, recontato por CPF, falha de autenticação, volume por opção de menu.
11. Reemissão de parcela: canal exato, prazo operacional, evidência gerada, papel da Caixa versus MTE.
12. SMS/push/e-mail: existência, gatilhos, cobertura, opt-in e confiabilidade.

⸻

Veredito final

A v2 endereçou corretamente cerca de 70–80% das falhas substantivas da v1, especialmente os erros normativos e a confusão Caixa × MTE. Mas ainda não é uma pesquisa fechada.

Classificação técnica:

V1: fraca, com muitos fatos inventados.
V2: boa como hipótese estruturada de blueprint; falta apenas a validação empírica da URA (ligação-teste) para fechá-la como AS-IS — exigência endereçada à v3 no critério de aceitação abaixo.

A principal exigência para a próxima versão é simples e binária: separar definitivamente o que é normativo MTE/Caixa do que é fluxo telefônico observado.

**Critério de aceitação para a v3 (checklist):** o Eixo 1 da URA deixa de ser hipótese e passa a AS-IS verificado **se, e somente se**, a v3 apresentar uma ligação-teste documentada (ou transcrição/documento interno) que cubra: (1) árvore de menu, (2) mecanismo de autenticação, (3) critério de transbordo para humano, (4) escopo do atendente e (5) protocolo. Cumpridos esses cinco itens com transcrição, a crítica central está **sanada** e o blueprint torna-se publicável; os pontos de bastidor profundo (SLA, latência, integração interna) e métricas de contact center não bloqueiam o AS-IS da jornada, pois não são etapas vividas pelo cidadão. Não cumpridos, o Eixo 1 permanece rotulado como hipótese operacional.