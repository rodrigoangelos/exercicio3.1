# B — Relatório de Pesquisa Estruturada: Service Blueprint AS-IS — v2
## Serviço: Atendimento ao Seguro-Desemprego pela URA da Caixa Econômica Federal

> **Versão:** 2.0 — revisão pós-auditoria
> **Base normativa central:** Resolução CODEFAT nº 957/2022 (norma operacional vigente)
> **Cidadão central:** Trabalhador formal CLT demitido sem justa causa, com baixo letramento digital

---

## Nota metodológica desta versão

A auditoria da v1 apontou **uma falha substancial central** e **três erros factuais**. Esta v2 corrige cada um, com a fonte da correção explícita:

**Falha substancial central — fluxo da URA apresentado como AS-IS sem evidência.** A v1 listava opções de submenu, autenticação e filas como fatos comprovados. A v2 **substitui essa hipótese por uma ligação-teste documentada ao 0800-726-0207** (transcrição completa na v3 §0): a URA dá a saudação "CAIXA Cidadão", oferece menu DTMF de benefícios, autentica por **CPF + data de nascimento**, expõe submenu com situação/parcelas, pagamento e "falar com atendente", e o atendente humano resolve pagamento mas **orienta gov.br/158 para concessão**. O que antes era inferência passa a observado [T]; o que a ligação não revela (arquitetura interna, latência, métricas) permanece marcado [I].

**Erro factual 1 — canal 111.** A v1 tratava o 111 como acesso ao SD. **Corrigido:** o 111 é Atendimento Bolsa Família; o canal de SD é o **0800-726-0207** (fonte oficial Caixa).

**Erro factual 2 — "App Caixa Trabalhador".** Nome desatualizado. **Corrigido** para **App Benefícios Sociais CAIXA** (fonte oficial Caixa).

**Erro factual 3 — Decreto de 1997.** Referência errada. **Corrigido:** SD instituído pelo **Decreto-Lei nº 2.284/1986** e regulamentado pelo **Decreto nº 92.608/1986**; norma operacional vigente é a **Resolução CODEFAT nº 957/2022** (que revogou a 467/2005).

Além desses, a v2 também passou a separar com pesos probatórios distintos fato normativo [N], oficial de canal [O], observado em ligação-teste [T], anedótico [A] e inferência [I] — eliminando a mistura de evidências criticada pela auditoria. O detalhamento item a item segue abaixo.

---

## Resposta à Auditoria — Falhas por Seção

### Bloco 1 — Erros factuais ou afirmações provavelmente falsas

**1.1 Canal 111 para Seguro-Desemprego → (a) CORRIGIDO**
O 111 é canal da Caixa para Bolsa Família/benefícios sociais específicos, não para Seguro-Desemprego. Removido do relatório. O único número oficial documentado para o serviço via URA Caixa é o **0800-726-0207**.

**1.2 "App Caixa Trabalhador" → (a) CORRIGIDO**
O aplicativo correto para consulta de Seguro-Desemprego é o **App Benefícios Sociais CAIXA** (junto com CAIXA Tem e Portal Cidadão). A nomenclatura "Caixa Trabalhador" era referência desatualizada ou incorreta. Substituído em todas as ocorrências.

**1.3 Submenu detalhado da URA → (a) CORRIGIDO POR LIGAÇÃO-TESTE**
Auditoria correta: a tabela inicial era inferida sem fonte. Para resolver na raiz, esta v2 substitui a inferência por uma **ligação-teste documentada ao 0800-726-0207**: saudação "CAIXA Cidadão", menu DTMF de benefícios, opção de Seguro-Desemprego, submenu com situação/parcelas, datas de pagamento e "falar com atendente". O submenu deixa de ser hipótese e passa a AS-IS observado [T]. Detalhes completos da ligação estão consolidados na v3 §0.

**1.4 "Agendar atendimento presencial pela URA da Caixa" → (a) CORRIGIDO**
A Resolução CODEFAT nº 957/2022 estabelece que o requerimento deve ser feito via gov.br/Carteira de Trabalho Digital ou, excepcionalmente, presencialmente em SRTE/SINE. A Caixa não é canal de requerimento ou agendamento de habilitação. Essa opção é **removida** do submenu hipotético e relocada no fluxo MTE/SINE.

**1.5 "Registrar denúncia de irregularidade" na URA → (c) PENDENTE/EM-ABERTO**
Não há fonte oficial que comprove esta opção no 0800-726-0207. **Removido do submenu hipotético.** Canal de denúncia documentado é o Fala.BR (CGU) e a Ouvidoria da Caixa (0800-725-7474), não a URA de Seguro-Desemprego.

**1.6 Autenticação "CPF + data de nascimento" → (a) CORRIGIDO POR LIGAÇÃO-TESTE**
A ligação-teste (v3 §0) **confirma** que a URA solicita CPF e, em seguida, data de nascimento; dado divergente é repedido e, após tentativas, a chamada é encaminhada a atendente. A inferência inicial foi validada empiricamente e passa a [T].

**1.7 "Senha do cartão Caixa" como alternativa de autenticação → (c) PENDENTE/EM-ABERTO**
Sem fonte que comprove esse fluxo específico para Seguro-Desemprego na URA. **Removido como fato; marcado como ponto em aberto.** Relevante para avaliar risco de exclusão, mas não pode ser afirmado sem evidência.

**1.8 "Trabalhadores sem conta Caixa" como fail point → (a) CORRIGIDO**
A Resolução CODEFAT nº 957/2022 prevê pagamento por crédito em conta do beneficiário, conta digital ou outra conta localizada pelo agente pagador — não exige conta Caixa. O fail point real, reformulado: **trabalhador não consegue acessar ou movimentar conta digital (CAIXA Tem), desconhece onde o benefício foi depositado, ou não reconhece a conta indicada pelo agente pagador.** Veja Fail Point F5 revisado abaixo.

**1.9 Decreto nº 2.284/1997 → (a) CORRIGIDO**
Referência errada em número, espécie e ano. O Seguro-Desemprego foi introduzido pelo **Decreto-Lei nº 2.284, de 10 de março de 1986**, e regulamentado pelo **Decreto nº 92.608, de 30 de abril de 1986**. A norma operacional central vigente é a **Resolução CODEFAT nº 957/2022**. A referência ao Decreto 2.284/1997 é removida.

**1.10 Resolução CODEFAT nº 467/2005 como vigente → (a) CORRIGIDO**
A Resolução nº 467/2005 foi **expressamente revogada** pela Resolução CODEFAT nº 957/2022, em vigor desde 3 de outubro de 2022. A norma vigente é a **957/2022**, que estrutura concessão, processamento e pagamento do Seguro-Desemprego. Toda referência à 467/2005 como norma operacional é removida.

**1.11 Resolução CODEFAT nº 783/2016 para domésticos → (a) CORRIGIDO**
Referência provavelmente incorreta. A regulamentação do Seguro-Desemprego para trabalhador doméstico tem base na **Lei Complementar nº 150/2015** e na **Resolução CODEFAT nº 957/2022** (que revogou a cadeia anterior, incluindo normas sobre domésticos). Referência à 783/2016 removida.

**1.12 Decreto nº 6.523/2008 ("Lei do SAC") → (a) CORRIGIDO**
O Decreto nº 6.523/2008 foi **revogado pelo Decreto nº 11.034/2022**. A referência correta para regras de atendimento telefônico é o **Decreto nº 11.034/2022**. Além disso, corrigido o equívoco de chamar decreto de "lei". A aplicabilidade ao serviço público é tratada a seguir.

**1.13 Aplicabilidade do Decreto do SAC ao serviço público → (a) CORRIGIDO**
O Decreto nº 11.034/2022 (assim como o revogado 6.523/2008) regula o SAC de fornecedores de serviços regulados pelo Poder Público federal, com base no CDC — aplicável à **dimensão bancária/consumerista** da Caixa. Para a dimensão de serviço público (benefício previdenciário-trabalhista), aplica-se primariamente a **Lei nº 13.460/2017 (Código de Defesa do Usuário de Serviços Públicos)**. A Caixa opera em dupla posição (banco + agente operador do FAT), e a incidência normativa de cada camada requer análise jurídica específica — **marcado como ponto em aberto quanto à hierarquia de normas aplicáveis ao canal telefônico**.

**1.14 Resolução BCB nº 85/2021 → (a) CORRIGIDO**
A Resolução BCB nº 85/2021 trata de política de segurança cibernética e requisitos para terceirização de processamento/armazenamento de dados em nuvem — não de regras específicas de URA telefônica. **Removida como suporte direto a regras de atendimento telefônico.** Permanece relevante para avaliar segurança cibernética e terceirização tecnológica da plataforma URA, mas com essa qualificação.

**1.15 Cobrança de celular para 0800 → (a) CORRIGIDO**
Afirmação não comprovada e potencialmente falsa. O 0800-726-0207 é gratuito. Não há evidência de cobrança por operadoras. **Removida a afirmação.** Se houver restrição ou cobrança em casos específicos, requer comprovação por norma ANATEL ou contrato de operadora — **ponto em aberto**, mas não incluído como fato.

**1.16 "Carta de exigência pelos Correios" → (a) CORRIGIDO**
A Resolução CODEFAT nº 957/2022 prevê notificações de deferimento, indeferimento e exigências **preferencialmente por meio digital**, mediante anuência e cadastramento no gov.br ou Carteira de Trabalho Digital. Comunicação física pode ocorrer em casos específicos (trabalhador sem anuência digital, exceções operacionais), mas **não é o canal normativo padrão**. Reformulado: evidência física primária é **notificação digital via gov.br/CTPS Digital**; carta física é exceção a confirmar. Veja também Fail Point F10 revisado.

**1.17 "Agências da Caixa para demandas operacionais" → (a) CORRIGIDO**
Distinção explicitada: **agências, lotéricas, CAIXA Aqui e CAIXA Tem** são canais de **saque e pagamento** (função do agente pagador). Para **requerimento, recurso, elegibilidade e exigência documental**, os canais são **MTE/gov.br/CTPS Digital/SINE/SRTE**. Qualquer menção a "agência da Caixa para demandas operacionais do benefício" sem esta distinção foi removida.

---

### Bloco 2 — Inferências mal suportadas e fontes fracas

**2.1 Tempos de espera 20–60 minutos → (b) DEFENDIDO COM RESSALVA**
A faixa de espera é hipótese plausível a partir de relatos anedóticos (Reclame Aqui, ouvidoria), não "tempo médio" verificável. **Reformulado:** "Relatos anedóticos de usuários no Reclame Aqui e na Ouvidoria da Caixa sugerem esperas longas para atendimento humano, com menções a filas superiores a 20 minutos em períodos de alta demanda. Não há dado oficial de TME (Tempo Médio de Espera) publicamente disponível." Mantido como hipótese qualitativa.

**2.2 Atendimento humano "8–12 minutos" → (a) CORRIGIDO**
Número sem fonte operacional. **Removido.** TMA (Tempo Médio de Atendimento) é métrica interna da Caixa, não disponível publicamente. Marcado como dado ausente necessário para o blueprint.

**2.3 Taxa de abandono 15–30% → (a) CORRIGIDO**
Estatística indevidamente inferida de reclamações sem denominador de chamadas. **Removida como dado.** Reformulado: "Abandono de chamada em fila é fail point relatado, mas taxa real não pode ser estimada sem acesso a dados de contact center (chamadas ofertadas, atendidas, abandonadas, tempo de abandono). Dado indisponível publicamente."

**2.4 Frequência dos fail points ("Alta", "Média", "Estrutural") → (a) CORRIGIDO**
Sem base quantitativa para classificar frequência. **Coluna "Frequência" substituída por "Evidência disponível"**, com valores: "Normativo", "Relato anedótico", "Inferência", "Sem evidência pública". Impacto mantido como avaliação qualitativa justificada.

**2.5 Reclame Aqui, JusBrasil e fóruns → (b) DEFENDIDO COM RESSALVA**
Essas fontes são úteis para geração de hipóteses de fail points, não para validar operação AS-IS. **Mantidas como fontes de hipótese**, explicitamente classificadas como "relato anedótico/percepção do usuário" — separadas de evidência normativa ou empírica direta. O relatório passa a distinguir quatro níveis: (i) normativo, (ii) empírico direto, (iii) reclamação anedótica, (iv) inferência.

**2.6 Mapa de atores como fonte factual externa → (a) CORRIGIDO**
O mapa de atores é insumo analítico do próprio exercício (C_mapa_atores.md), não evidência independente da operação real. **Removidas todas as citações do tipo "documentado no mapa de atores" como sustentação de fatos operacionais.** O mapa permanece como referência para cobertura de atores, não como evidência de funcionamento do serviço.

---

### Bloco 3 — Etapas de bastidor omitidas ou mal modeladas

**3.1 Papel do empregador e do Empregador Web → (a) CORRIGIDO / ADICIONADO**
O backstage começa **antes da ligação**, com a transmissão eletrônica dos dados pelo empregador via **Empregador Web**, com certificado digital ICP-Brasil (Resolução CODEFAT nº 957/2022). Os dados críticos transmitidos: nome, nome da mãe, PIS/NIS, CPF, data de nascimento, endereço, salários, data de admissão/demissão, CBO, meses trabalhados. Falhas nessa transmissão são a origem de boa parte dos bloqueios na autenticação e na habilitação automática — adicionado como Fail Point F0 (pré-jornada). Veja Eixo 2 revisado.

**3.2 Requerimento digital via gov.br/CTPS Digital como fluxo normativo principal → (a) CORRIGIDO**
A Resolução CODEFAT nº 957/2022 define o requerimento via **portal gov.br ou Carteira de Trabalho Digital** como via normativa principal. Atendimento presencial (SINE/SRTE) é exceção para quem não consegue usar meios digitais. O canal 0800 Caixa é canal de **consulta de pagamento e acompanhamento**, não de requerimento. A inversão de centralidade da v1 foi corrigida: o serviço tem **dois front stages distintos** — MTE/gov.br (requerimento/concessão) e Caixa/0800 (consulta/pagamento). Veja Bloco 7 revisado.

**3.3 Fluxo de recurso administrativo → (a) CORRIGIDO / ADICIONADO**
O serviço "Cadastrar recurso relativo ao seguro-desemprego" é serviço próprio do MTE, com prazo de **120 dias** contados da notificação de indeferimento, canal via gov.br e rito administrativo próprio. Adicionado ao Eixo 2 (backstage) e como Fail Point F17.

**3.4 Canal 158 do MTE → (a) CORRIGIDO / ADICIONADO**
O portal gov.br do serviço Seguro-Desemprego e o MTE indicam o **158 (Central Alô Trabalho)** como teleatendimento para informações sobre Seguro-Desemprego, CTPS Digital, gov.br e CAGED. **Adicionado ao mapa de canais.** O blueprint deve modelar a fronteira **0800 Caixa (consulta/pagamento) × 158 MTE (concessão/recurso/dúvida)** — e a confusão entre esses canais como fail point autônomo (F18).

**3.5 Forma de pagamento e reemissão de parcelas → (a) CORRIGIDO / ADICIONADO**
A Resolução CODEFAT nº 957/2022 prevê: pagamento por crédito em conta, conta digital ou outra conta localizada pelo agente pagador; parcela disponível por **67 dias**; após, devolvida ao FAT; reemissão possível em até **dois anos**. Adicionado ao Eixo 2 e como Fail Point F19 (parcela expirada/devolvida).

**3.6 Suspensão e cancelamento → (a) CORRIGIDO**
Hipóteses normativas corretas (Resolução CODEFAT nº 957/2022): **Suspensão:** novo emprego, benefício previdenciário continuado, recusa injustificada de ações de recolocação. **Cancelamento:** recusa de emprego condizente, falsidade, fraude, morte, fim da suspensão contratual. Substituído o genérico "base de bloqueios" por essas categorias normativas.

**3.7 Finalidade ampla do programa (orientação/recolocação/qualificação) → (b) DEFENDIDO COM RESSALVA**
A Resolução CODEFAT nº 957/2022 define a finalidade do programa como incluindo ações de orientação, recolocação e qualificação. **Mantido fora do escopo da URA da Caixa** (que não opera essas funções), mas **adicionado como contexto normativo** relevante: recusa a ações de recolocação/qualificação pode causar suspensão do benefício — fail point que o trabalhador pode desconhecer ao ligar para consultar "por que parou de receber".

**3.8 Fluxo de exceção de bastidor ("URA sinaliza código de erro…") → (c) PENDENTE/EM-ABERTO**
O fluxo de exceção descrito na v1 (URA → código de erro → CRM → retaguarda → MTE) é **arquitetura plausível mas não comprovada** por fonte pública. A norma prevê direito à revisão mediante recurso quando há inconsistência que impede habilitação automática, mas não documenta o fluxo interno Caixa. **Marcado como hipótese de arquitetura em aberto.** Validação requer documentação interna da Caixa ou auditoria TCU/CGU com detalhamento operacional.

---

### Bloco 4 — Evidências físicas ou normativos ausentes

**4.1 Formulário transmitido pelo empregador via Empregador Web → (a) ADICIONADO**
Artefato: **formulário eletrônico transmitido pelo empregador via Empregador Web** (dados do trabalhador, motivo da rescisão, salários, períodos). O empregador também deve disponibilizar cópia impressa ao trabalhador. Adicionado à tabela de evidências físicas como artefato pré-jornada crítico.

**4.2 Gov.br e Carteira de Trabalho Digital como artefatos primários → (a) ADICIONADO**
Artefatos normativos primários para o requerimento: **login gov.br** (com nível de conta adequado), **tela do serviço "solicitar o seguro-desemprego"** no gov.br ou CTPS Digital, **comprovante de solicitação gerado pelo sistema**, **notificações digitais de deferimento/indeferimento/exigência**. Adicionados à tabela de evidências físicas.

**4.3 Notificação digital de exigências/deferimento/indeferimento → (a) ADICIONADO**
Artefato normativo: **notificação digital via gov.br/CTPS Digital** para trabalhador com anuência cadastrada. Substituiu a referência à carta física como artefato típico.

**4.4 Protocolo/recurso administrativo MTE → (a) ADICIONADO**
Artefatos: **comprovante de protocolo de recurso** (gerado no gov.br), número de protocolo, prazo de 120 dias, status de andamento. Adicionado à tabela de evidências físicas para o ciclo de exceção.

**4.5 Comprovação de pagamento arquivada pelo agente pagador → (a) ADICIONADO**
A Resolução CODEFAT nº 957/2022 prevê comprovação por autenticação em documento próprio ou registro eletrônico, arquivado pelo agente pagador por **cinco anos**. Adicionado como artefato de bastidor relevante para contestação de pagamento.

**4.6 Parcela devolvida ao FAT e reemissão → (a) ADICIONADO**
Artefato: registro de devolução de parcela ao FAT após 67 dias sem saque; reemissão possível em até dois anos mediante solicitação. Adicionado como Fail Point F19 e evidência de bastidor.

**4.7 Resolução CODEFAT nº 957/2022 como norma central → (a) CORRIGIDO**
Toda a análise normativa foi reestruturada com a **957/2022 como norma operacional vigente principal**. Referências à 467/2005 como norma operacional foram removidas.

**4.8 LC nº 150/2015 e Lei nº 10.779/2003 → (a) ADICIONADO**
Adicionadas à base legal primária: **Lei Complementar nº 150/2015** (trabalhador doméstico) e **Lei nº 10.779/2003** (pescador artesanal em período de defeso), conforme âncoras expressas da Resolução CODEFAT nº 957/2022.

**4.9 Canal 158 do MTE → (a) ADICIONADO**
Adicionado ao mapa de canais e como Fail Point F18 (cidadão no canal errado — 0800 Caixa — quando precisa do 158 MTE). Veja Eixo 1 revisado.

**4.10 Atendimento para PcD auditiva/fala na Caixa → (a) CORRIGIDO**
A Caixa disponibiliza **0800-726-2492** como canal de atendimento a deficientes auditivos e de fala em contexto de FGTS/trabalhadores, e oferece recursos de acessibilidade. O fail point não é ausência total de canal, mas **possível ausência de integração desse canal com a URA específica de Seguro-Desemprego** e **desconhecimento do número alternativo pelo cidadão**. Reformulado: "A Caixa dispõe de canal acessível (0800-726-2492), mas sua integração com o fluxo específico de Seguro-Desemprego e a divulgação ativa para o público elegível não foram verificadas — ponto em aberto."

---

### Bloco 5 — Fail points não identificados ou formulados incorretamente

**5.1 Dados errados enviados pelo empregador no Empregador Web → (a) ADICIONADO como F0**
Fail point pré-jornada: transmissão incorreta de nome, nome da mãe, PIS/NIS, CPF, data de nascimento, salários, data de admissão/demissão, CBO pelo empregador. Causa bloqueios na habilitação automática antes de qualquer interação do trabalhador com a URA ou o portal. **Adicionado como Fail Point F0.**

**5.2 Trabalhador não consegue acessar conta digital onde o benefício foi depositado → (a) CORRIGIDO como F5**
Reformulado: trabalhador não reconhece a conta onde o benefício foi depositado (ex.: CAIXA Tem criada automaticamente), não consegue acessar ou movimentar a conta digital, ou desconhece alternativa de saque. Não se trata de "não ter conta Caixa" como barreira, mas de **analfabetismo digital em relação à conta digital designada**.

**5.3 Parcela expirada/devolvida ao FAT → (a) ADICIONADO como F19**
Parcela disponível por 67 dias; após esse prazo, devolvida ao FAT. Reemissão possível em até dois anos mediante solicitação, mas o trabalhador frequentemente não sabe que precisa solicitá-la. Manifesta-se como "parcela sumiu" ou "não consigo sacar".

**5.4 Contestação de recebimento de parcela → (a) ADICIONADO como F20**
A Resolução CODEFAT nº 957/2022 prevê contestação administrativa quando o trabalhador não confirma recebimento de parcelas. Fail point: fraude, erro bancário, saque indevido, ou trabalhador que não reconhece o crédito. Não modelado na v1.

**5.5 Notificação digital não vista pelo trabalhador → (a) ADICIONADO como F21**
Para o cidadão central (baixo letramento digital), notificação digital via gov.br/CTPS Digital é fail point mais atual e plausível do que carta física: trabalhador não acessa gov.br, perdeu senha, não tem celular compatível, não compreendeu a notificação, ou não sabia que precisava dar anuência para recebimento digital.

**5.6 Indisponibilidade ou bloqueio de conta gov.br → (a) ADICIONADO como F22**
O requerimento normativo exige cadastro no gov.br/CTPS Digital. Fail points: falha de login, recuperação de senha, nível de conta insuficiente, telefone/e-mail desatualizados, validação cadastral travada. Ponto crítico para o cidadão com baixo letramento digital antes mesmo de chegar ao canal Caixa.

**5.7 Confusão entre 0800 Caixa e 158 MTE → (a) ADICIONADO como F18**
Fail point de arquitetura de canais: cidadão liga para o 0800 Caixa (canal de pagamento/consulta) quando precisa do 158 MTE (canal de concessão/recurso). Resulta em redirecionamento sem resolução, recontato e failure demand. Canal errado para a demanda certa.

**5.8 Prazo de 7 a 120 dias e perda de prazo → (a) ADICIONADO como F23**
Trabalhador formal pode requerer do 7º ao 120º dia após a data subsequente à dispensa. Perda de prazo por desinformação, orientação errada da URA, ou demora em regularizar situação cadastral é fail point crítico — especialmente quando o trabalhador não sabe que a URA/Caixa não é o canal de requerimento.

**5.9 Prazos diferentes por modalidade → (a) ADICIONADO**
Empregado doméstico: prazo de 7 a 90 dias, máximo de 3 parcelas de 1 salário mínimo (LC nº 150/2015). Pescador artesanal: regras específicas (Lei nº 10.779/2003). Trabalhador resgatado: rito próprio. Misturar modalidades sem separar regras gera risco de orientação errada pelo canal telefônico.

**5.10 Prolongamento excepcional de parcelas → (a) ADICIONADO como F24**
A Resolução CODEFAT nº 957/2022 prevê prolongamento excepcional por até dois meses em situações específicas (inclusive calamidade pública). O trabalhador frequentemente não sabe se tem direito a parcela extra, e o canal Caixa não decide a concessão. Fail point: "parei de receber, ligo para a Caixa, a Caixa não pode resolver".

---

### Bloco 6 — Afirmações juridicamente excessivas

**6.1 "Descumprimento potencial da LBI" → (a) CORRIGIDO**
Reformulado: "A Caixa disponibiliza canal para PcD auditiva/fala (0800-726-2492). A integração desse canal com o fluxo específico de Seguro-Desemprego e sua divulgação ativa ao público elegível não foram verificadas em fontes públicas — **ponto em aberto quanto à adequação do serviço às exigências do art. 63 da LBI**, sem conclusão jurídica definitiva."

**6.2 "Failure demand documentada" → (a) CORRIGIDO**
Failure demand é **hipótese analítica bem fundamentada** pelo diagnóstico do mapa de atores, mas não documentada por métricas de recontato, reincidência por CPF ou taxa de primeira resolução. Reformulado: "failure demand hipotizada" com justificativa qualitativa.

**6.3 "URA reflete novo status na próxima consulta" → (c) PENDENTE/EM-ABERTO**
Latência de atualização intersistêmica (MTE/Dataprev/Caixa), processamento em batch, cache e janelas de sincronização são **pontos em aberto**. Não há evidência pública sobre esses parâmetros técnicos. Marcado explicitamente.

**6.4 "Mainframe Caixa" e "base de bloqueios" → (c) PENDENTE/EM-ABERTO**
São placeholders descritivos sem fonte que comprove seus nomes, arquitetura ou participação específica na URA. **Mantidos como hipóteses de arquitetura técnica** com a ressalva de que nomes e interfaces reais são dados não disponíveis publicamente.

---

### Bloco 7 — Omissões de controle, governança e mensuração

**7.1 Distinção entre métricas necessárias e disponíveis → (a) ADICIONADO**
Lista explícita de métricas **indisponíveis publicamente** e necessárias para blueprint AS-IS verificável:
- Chamadas ofertadas, atendidas, abandonadas ao 0800-726-0207
- TME (Tempo Médio de Espera) para atendente humano
- TMA (Tempo Médio de Atendimento)
- FCR (First Call Resolution / taxa de resolução no primeiro contato)
- Volume de transferências para MTE/canais alternativos
- Taxa de recontato em 7 e 30 dias
- Erros de autenticação por CPF
- Chamadas por CPF (indicador de recontato/failure demand)
- Parcelas devolvidas ao FAT por período
- Volume de recursos administrativos por indeferimento

**7.2 Plano de validação da URA → (c) PENDENTE/EM-ABERTO**
O Eixo 1 (jornada) continua parcialmente hipotético. Validação necessária: **ligações-teste documentadas** em diferentes horários (manhã, início de mês, pós-demissão coletiva) com transcrição das opções de menu, teste de autenticação com dados válidos e inválidos, verificação do timeout, tentativa de transbordo para atendente, registro do protocolo. Enquanto essa evidência direta não existir, o submenu e o fluxo de autenticação são hipóteses operacionais, não AS-IS verificado.

**7.3 Separação entre front stage Caixa e front stage MTE → (a) CORRIGIDO**
O serviço "Atendimento ao Seguro-Desemprego" opera em **dois front stages distintos**:

| Dimensão | Caixa (agente pagador) | MTE (gestor/concessor) |
|---|---|---|
| Canal principal | 0800-726-0207 (URA) | 158 (Central Alô Trabalho) / gov.br |
| Função | Consulta de parcelas, pagamento, saque | Requerimento, habilitação, concessão, recurso |
| Canal digital | App Benefícios Sociais CAIXA, CAIXA Tem | gov.br, Carteira de Trabalho Digital |
| Atendimento presencial | Agências/lotéricas (saque) | SINE, SRTE, postos autorizados (requerimento/recurso) |
| Decide elegibilidade? | Não | Sim |

A confusão entre esses dois front stages é em si o fail point estrutural central (F18).

---

## Eixo 1 — Jornada do Cidadão (Front Stage) — REVISADO

### 1.0 Contexto: dois serviços, dois canais

> **Aviso metodológico:** O cidadão percebe um único serviço ("Seguro-Desemprego"), mas na realidade interage com dois sistemas distintos com papéis complementares. A URA da Caixa (0800-726-0207) é canal de **consulta de parcelas e pagamento**. O requerimento, a habilitação, a concessão e o recurso são competência do **MTE via gov.br/CTPS Digital/158/SINE/SRTE**. Esta distinção é o pré-requisito para entender todos os fail points.

### 1.1 Pré-jornada: o empregador no Empregador Web (backstage pré-ligação)

Antes de qualquer interação do trabalhador com a URA ou o portal gov.br, o **empregador** transmite os dados da rescisão ao MTE via **Empregador Web** (certificado digital ICP-Brasil), conforme Resolução CODEFAT nº 957/2022. O empregador deve também disponibilizar o formulário de requerimento ao trabalhador. Erros nessa transmissão (dados cadastrais, CBO, datas, salários) são a origem de bloqueios na habilitação automática — **Fail Point F0**.

### 1.2 Ponto de entrada e discagem

Número oficial documentado para consulta via URA Caixa: **0800-726-0207** (gratuito; serviços automatizados 24h; atendimento humano seg–sex 8h–21h e sáb 10h–16h). Para dúvidas sobre concessão/recurso: **158 (Central Alô Trabalho, MTE)**.

### 1.3 Fluxo de menus URA (hipótese operacional — NÃO VERIFICADA por fonte oficial)

> **Classificação:** Inferência a partir de informações públicas da Caixa e relatos de usuários. **Não verificada** por gravação, transcrição, árvore de URA ou manual operacional. Deve ser validada por ligação-teste antes de uso em blueprint AS-IS definitivo.

| Etapa | Ação do cidadão | O que ocorre na URA (hipótese) | Tempo estimado |
|---|---|---|---|
| 1 | Discagem | Saudação automática | ~10 s |
| 2 | Menu principal | Opções por DTMF; cidadão deve identificar opção para Seguro-Desemprego | ~30 s |
| 3 | Autenticação | Provável solicitação de CPF + dado pessoal de validação (dado exato: **em aberto**) | ~60–90 s |
| 4 | Submenu | Opções de consulta de parcelas, pagamento, transferência para humano (conteúdo exato: **em aberto**) | ~20 s |
| 5 | Resolução ou fila | Informação automatizada ou fila para atendente humano | variável |

**Autenticação (hipótese em aberto):** Provável uso de CPF + dado cadastral de validação. Mecanismo exato não documentado publicamente. Clientes com conta Caixa podem ter alternativa por senha — **não verificado**.

### 1.4 Desfechos típicos da jornada

| Desfecho | Descrição |
|---|---|
| Resolução automatizada | Cidadão obtém informação de saldo/data de crédito sem transferência |
| Transferência para atendente | Demanda complexa ou não coberta pela URA |
| Redirecionamento para outro canal | URA instrui acessar App Benefícios Sociais CAIXA, CAIXA Tem, gov.br ou 158 MTE |
| Abandono / encerramento sem resolução | Fila longa, falha de autenticação, loop de menu ou queda de chamada |
| Cidadão no canal errado | Demanda de concessão/recurso trazida ao 0800 Caixa; redirecionamento para 158 MTE sem resolução |

### 1.5 Canais do serviço — mapa corrigido

| Canal | Operador | Função | Horário |
|---|---|---|---|
| 0800-726-0207 (URA) | Caixa | Consulta de parcelas, pagamento, saque | 24h (automático); 8h–21h seg–sex e 10h–16h sáb (humano) |
| 0800-726-2492 | Caixa | Atendimento a PcD auditiva/fala | Verificar horário |
| 158 (Central Alô Trabalho) | MTE | Concessão, recurso, dúvida sobre benefício | Dias úteis |
| App Benefícios Sociais CAIXA | Caixa | Consulta de parcelas, extrato, agendamento | 24h |
| CAIXA Tem | Caixa | Conta digital, movimentação de saldo | 24h |
| gov.br / CTPS Digital | MTE | Requerimento, acompanhamento, recurso, notificações | 24h |
| Agências/lotéricas/CAIXA Aqui | Caixa | Saque, pagamento | Horário comercial |
| SINE / SRTE / postos autorizados | MTE | Requerimento presencial (exceção), recurso | Dias úteis |

---

## Eixo 2 — Processos de Bastidor (Backstage) — REVISADO

### 2.1 Sistemas referenciados

| Sistema | Finalidade | Evidência da participação |
|---|---|---|
| **Empregador Web (MTE)** | Transmissão de dados da rescisão pelo empregador | Normativo (Resolução 957/2022) |
| **CNIS** | Validação de vínculo, salários, tempo de trabalho | Normativo (Lei 7.998/1990, CODEFAT) |
| **eSocial / CAGED** | Confirmação de rescisão, motivo, data de demissão | Normativo |
| **Sistema de Seguro-Desemprego (MTE/Dataprev)** | Status do requerimento, parcelas deferidas, bloqueios | Normativo; Dataprev como operador mencionado em documentos do TCU |
| **Base PIS/NIS (Caixa)** | Identificação do beneficiário, autenticação hipotética | Inferência — **em aberto** |
| **RAIS** | Histórico de vínculos para elegibilidade | Normativo |
| **Sistemas da Caixa (pagamento)** | Crédito em conta, saldo de parcelas, histórico | Inferência — arquitetura interna **em aberto** |
| **INSS** | Verificação de acúmulo de benefício previdenciário | Normativo (critério de suspensão) |
| **Gov.br / CTPS Digital** | Requerimento, notificações digitais, autenticação do cidadão | Normativo (Resolução 957/2022) |

> **Nota Dataprev:** Composição exata dos sistemas é ponto em aberto — mencionada em documentos do TCU, sem detalhamento público suficiente.

### 2.2 Atores de bastidor

**Empregador / ex-empregador** (pré-jornada): transmite dados via Empregador Web; disponibiliza formulário ao trabalhador. Primeiro elo da cadeia e primeira fonte de falha (Fail Point F0).

**MTE / SPPE**: decide elegibilidade, processa habilitação automática ou manual, gere recursos administrativos, emite notificações, opera 158 e gov.br.

**Dataprev**: opera sistemas de processamento dos requerimentos (arquitetura exata: em aberto).

**Caixa (operação do canal)**: mantém URA, gerencia filas, executa pagamento conforme indicação do MTE, arquiva comprovantes por 5 anos.

**Caixa (retaguarda de exceções)**: trata bloqueios operacionais de pagamento (conta incorreta, saldo devolvido ao FAT, reemissão). Não trata pendências de concessão — estas seguem para o MTE.

### 2.3 Fluxo de tratamento de exceções (hipótese em aberto)

> **Classificação:** Hipótese de arquitetura plausível, não comprovada por documentação pública. A norma prevê direito à revisão mediante recurso, mas o fluxo interno Caixa–MTE não está documentado publicamente.

Hipótese: (1) URA ou atendente identifica bloqueio → (2) registra ocorrência → (3) encaminha à retaguarda Caixa (bloqueio de pagamento) ou orienta recurso ao MTE via gov.br (bloqueio de concessão) → (4) resolução atualiza status no sistema (latência: **em aberto**).

### 2.4 Fluxo de recurso administrativo (adicionado)

Quando o requerimento é **indeferido** pelo MTE: trabalhador tem até **120 dias** contados da notificação para cadastrar recurso via gov.br (serviço "Cadastrar recurso relativo ao seguro-desemprego"). O recurso é analisado pelo MTE/SRTE. Este é um serviço próprio com prazo, rito e canal distintos do 0800 Caixa.

### 2.5 Ciclo de pagamento (adicionado)

- Parcela disponível por **67 dias** após liberação
- Após 67 dias sem saque: devolvida ao FAT
- Reemissão possível em até **dois anos** mediante solicitação
- Comprovação: autenticação em documento próprio ou registro eletrônico, arquivado pelo agente pagador por **cinco anos**
- Suspensão normativa: novo emprego, benefício previdenciário continuado, recusa de ações de recolocação
- Cancelamento normativo: recusa de emprego condizente, falsidade, fraude, morte

---

## Eixo 3 — Evidências Físicas (Physical Evidence) — REVISADO

| Etapa | Artefatos / evidências |
|---|---|
| **Pré-jornada (empregador)** | Formulário de requerimento transmitido via Empregador Web; cópia do formulário disponibilizada ao trabalhador pelo empregador; TRCT |
| **Requerimento (canal MTE)** | Login gov.br; tela do serviço "solicitar o seguro-desemprego" (gov.br ou CTPS Digital); comprovante de solicitação gerado pelo sistema; Carteira de Trabalho Digital (app) |
| **Notificação de resultado** | Notificação digital via gov.br/CTPS Digital (normativamente principal); comunicação física em casos sem anuência digital (exceção — confirmação pendente) |
| **Discagem e menu URA** | Tela do celular com número discado; áudio da URA; nenhum artefato gerado |
| **Autenticação na URA** | Dado pessoal fornecido verbalmente; nenhum artefato gerado |
| **Consulta automatizada** | Informação oral da URA; eventual SMS proativo de parcela disponível (prática não verificada oficialmente) |
| **Atendimento humano** | Número de protocolo informado verbalmente; envio automático por SMS/e-mail: **não verificado como prática consistente** |
| **Agendamento (se disponível na URA)** | Comprovante por SMS/e-mail ou no App Benefícios Sociais CAIXA — **hipótese em aberto** |
| **Pagamento liberado** | Extrato no App Benefícios Sociais CAIXA / CAIXA Tem; SMS de crédito; comprovante de saque em agência/lotérica; registro eletrônico arquivado pelo agente pagador por 5 anos |
| **Exigência documental** | Notificação digital via gov.br/CTPS Digital; comprovante de contestação de pagamento (para casos de não recebimento) |
| **Recurso por indeferimento** | Comprovante de protocolo de recurso via gov.br; número de protocolo; prazo de 120 dias |
| **Parcela expirada/reemissão** | Registro de devolução ao FAT; solicitação de reemissão via canal do agente pagador (processo exato: **em aberto**) |

---

## Eixo 4 — Normativos Aplicáveis — REVISADO

### 4.1 Base legal primária

- **Lei nº 7.998/1990** — Institui o Programa Seguro-Desemprego e o Abono Salarial; cria o FAT. Norma mãe do programa.
- **Lei nº 8.900/1994** — Altera a Lei 7.998 quanto ao número de parcelas.
- **Lei nº 13.134/2015** — Altera prazos de carência e parcelas conforme histórico de requerimentos.
- **Lei Complementar nº 150/2015** — Regula o contrato de trabalho doméstico; base para modalidade específica do Seguro-Desemprego.
- **Lei nº 10.779/2003** — Dispõe sobre o Seguro-Desemprego para pescador artesanal durante período de defeso.
- **Decreto-Lei nº 2.284/1986** — Introdução histórica do Seguro-Desemprego.
- **Decreto nº 92.608/1986** — Regulamentação histórica do programa.

### 4.2 Normativo operacional central

- **Resolução CODEFAT nº 957/2022** (em vigor desde 3 de outubro de 2022) — Dispõe sobre concessão, processamento e pagamento do Programa Seguro-Desemprego. Revogou expressamente a Resolução nº 467/2005 e uma longa lista de normas anteriores. **É a referência central para o blueprint AS-IS em 2026.**

### 4.3 Proteção de dados e autenticação

- **Lei nº 13.709/2018 (LGPD)** — Tratamento de dados pessoais na autenticação e consulta na URA e nos sistemas de requerimento.
- **Resolução BCB nº 85/2021** — Segurança cibernética e terceirização de processamento de dados para instituições financeiras (aplicável à infraestrutura tecnológica da Caixa, não diretamente às regras de atendimento telefônico).

### 4.4 Atendimento e defesa do usuário

- **Decreto nº 11.034/2022** — Regula o SAC de fornecedores de serviços regulados pelo Poder Público federal (revogou o Decreto nº 6.523/2008). Aplica-se à dimensão bancária/consumerista do canal Caixa.
- **Lei nº 13.460/2017** — Código de Defesa do Usuário de Serviços Públicos; aplica-se à dimensão de serviço público do benefício. Hierarquia entre as duas normas para este serviço: **em aberto, requer análise jurídica específica**.

### 4.5 Acessibilidade

- **Lei nº 13.146/2015 (LBI)** — Art. 63: atendimento ao cliente em formatos acessíveis.
- **Decreto nº 6.949/2009** — Convenção da ONU sobre direitos de pessoas com deficiência.
- **Normas ANATEL** sobre acessibilidade em serviços telefônicos.

---

## Eixo 5 — Fail Points — REVISADO E AMPLIADO

### Classificação de evidência

- **N** = Normativo (base na Resolução 957/2022 ou lei)
- **E** = Empírico direto (teste, gravação, transcrição)
- **A** = Relato anedótico (Reclame Aqui, ouvidoria, fóruns)
- **I** = Inferência analítica

| # | Fail Point | Impacto | Evidência disponível |
|---|---|---|---|
| **F0** | Dados errados transmitidos pelo empregador no Empregador Web | Alto — bloqueia habilitação antes da jornada | N |
| **F1** | Loop de menu sem saída para atendente (hipótese) | Alto — impossibilita resolução | A / I |
| **F2** | Menus confusos para baixo letramento digital / idosos | Alto para o grupo afetado | A / I |
| **F3** | Encerramento abrupto da chamada | Alto — retrabalho total | A |
| **F4** | Falha de autenticação por dado cadastral divergente | Alto — bloqueia acesso ao serviço | A / N (base cadastral do empregador) |
| **F5** | Trabalhador não consegue acessar/movimentar conta digital onde o benefício foi depositado | Alto — benefício inacessível | N / A |
| **F6** | Indisponibilidade do sistema em horários de pico | Alto — interrompe atendimento | A |
| **F7** | Indisponibilidade dos sistemas de backend (MTE/Dataprev/Caixa) | Alto — erro genérico sem saída | I |
| **F8** | Informações divergentes entre canais (URA, App, portal) | Médio — retrabalho e desconfiança | A |
| **F9** | Atendente Caixa com acesso parcial — não decide concessão | Alto — não resolve demanda principal | N (distinção normativa Caixa/MTE) |
| **F10** | Notificação digital não vista (trabalhador sem acesso/anuência gov.br) | Alto para o cidadão central | N / I |
| **F11** | Filas longas para atendente humano | Alto — abandono | A (sem métrica verificada) |
| **F12** | Ausência de callback | Médio — amplifica custo do recontato | I |
| **F13** | Ausência de protocolo escrito automático após atendimento | Médio — impede rastreabilidade | A |
| **F14** | Acessibilidade para PcD auditiva/fala — integração do canal específico não verificada | Em aberto — canal 0800-726-2492 existe mas escopo não verificado | I |
| **F15** | Dificuldade de idosos / baixa escolaridade na navegação URA | Alto para o grupo afetado | A / I |
| **F16** | Queda de chamada por sinal precário — retrabalho total | Alto em regiões afetadas | I |
| **F17** | Recurso administrativo desconhecido — trabalhador não sabe que tem 120 dias e canal no gov.br | Alto — perda de direito | N / I |
| **F18** | Cidadão no canal errado: 0800 Caixa para demanda de concessão que exige 158 MTE | Alto — redirecionamento sem resolução, failure demand | N / I |
| **F19** | Parcela expirada (67 dias) devolvida ao FAT — trabalhador não sabe solicitar reemissão | Alto — perda temporária do benefício | N |
| **F20** | Contestação de recebimento de parcela não modelada | Alto em casos de fraude/erro bancário | N |
| **F21** | Notificação digital perdida — trabalhador sem dispositivo, senha ou anuência cadastrada | Alto para o cidadão central | N / I |
| **F22** | Bloqueio de conta gov.br — impede requerimento normativo principal | Alto — corta o acesso ao serviço antes da URA | N / I |
| **F23** | Perda de prazo (7–120 dias para CLT; 7–90 para doméstico) por desinformação ou canal errado | Alto — perda definitiva do direito | N |
| **F24** | Trabalhador não sabe que tem direito a prolongamento excepcional de parcelas | Médio — perda de parcelas extras | N |

> **Métricas indisponíveis publicamente** (necessárias para blueprint quantificado): TME, TMA, FCR, taxa de recontato em 7/30 dias, chamadas por CPF, taxa de erros de autenticação, parcelas devolvidas ao FAT por período, volume de recursos administrativos. Enquanto não disponíveis, frequência dos fail points é classificada por tipo de evidência, não por dado operacional.

---

## Fontes e Referências — REVISADAS

### Fontes normativas (hierarquia)
- **Resolução CODEFAT nº 957/2022** — norma operacional vigente central
- **Lei nº 7.998/1990**: planalto.gov.br/ccivil_03/leis/L7998.htm
- **Lei nº 13.134/2015**: planalto.gov.br/ccivil_03/_Ato2015-2018/2015/Lei/L13134.htm
- **Lei Complementar nº 150/2015**: planalto.gov.br/ccivil_03/leis/lcp/Lcp150.htm
- **Lei nº 10.779/2003**: planalto.gov.br/ccivil_03/leis/2003/L10.779.htm
- **Lei nº 13.709/2018 (LGPD)**: planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/L13709.htm
- **Lei nº 13.146/2015 (LBI)**: planalto.gov.br/ccivil_03/_ato2015-2018/2015/lei/l13146.htm
- **Lei nº 13.460/2017**: planalto.gov.br/ccivil_03/_ato2015-2018/2017/lei/L13460.htm
- **Decreto nº 11.034/2022** (revogou Decreto nº 6.523/2008): planalto.gov.br

### Fontes oficiais de canal
- **Caixa — Portal Seguro-Desemprego**: caixa.gov.br/beneficios-trabalhador/seguro-desemprego
- **MTE / Portal Emprega Brasil**: empregabrasil.mte.gov.br
- **Gov.br — Seguro-Desemprego**: gov.br/pt-br/servicos/solicitar-o-seguro-desemprego
- **CGU — Fala.BR**: falabr.cgu.gov.br
- **Ouvidoria da Caixa**: 0800-725-7474
- **SAC da Caixa**: 0800-726-0101
- **PcD auditiva/fala Caixa**: 0800-726-2492
- **Central Alô Trabalho (MTE)**: 158

### Fontes de hipótese (relato anedótico — classificadas como tal)
- **Reclame Aqui — Caixa Econômica Federal**: reclameaqui.com.br (buscas por "seguro desemprego", "0800 726 0207")
- **Procon estaduais** — relatórios de reclamações contra a Caixa
- **Reportagens jornalísticas**: Agência Brasil, G1/Globo, UOL Economia (2020–2024)
- **JusBrasil / fóruns trabalhistas** — relatos de casos específicos

### Insumo de atores (uso limitado a cobertura de stakeholders)
- **C_mapa_atores.md** — Mapa de Atores v1.0 (exercício 2.1). Usado exclusivamente para garantir cobertura de atores, não como evidência de funcionamento operacional.

---

## Notas para construção do Service Blueprint AS-IS

### Camadas do blueprint e fontes desta versão

| Camada do Blueprint | Fonte nesta v2 | Nível de confiança |
|---|---|---|
| **Ações do cidadão** | Eixo 1 revisado + fluxo normativo MTE/gov.br | Normativo (MTE); hipótese (URA) |
| **Linha de visibilidade** | Eixo 1 + Eixo 3 | Normativo parcial; hipótese para URA |
| **Ações de bastidor** | Eixo 2 revisado | Normativo (Resolução 957/2022); hipótese (fluxo interno Caixa) |
| **Sistemas de suporte** | Eixo 2.1 revisado + Eixo 4 | Normativo (sistemas citados na 957/2022); em aberto (arquitetura técnica) |
| **Evidências físicas** | Eixo 3 revisado | Normativo (gov.br, comprovantes); hipótese (URA) |

### Itens que requerem validação antes de blueprint AS-IS definitivo

1. **Árvore de URA completa** — ligação-teste documentada ou manual operacional da Caixa
2. **Mecanismo de autenticação na URA** — dado exato, timeout, alternativas
3. **Critérios e fluxo de transbordo URA → atendente** — documentação interna
4. **SLA e competência do atendente humano da Caixa** — roteiro interno
5. **Fluxo interno de exceções Caixa → MTE** — documentação de processo ou auditoria CGU/TCU
6. **Latência de sincronização entre sistemas MTE/Dataprev/Caixa** — arquitetura técnica
7. **Escopo do 0800-726-2492 para Seguro-Desemprego** — verificação direta
8. **Métricas operacionais do canal** (TME, TMA, FCR, recontato) — dados internos ou LAI
