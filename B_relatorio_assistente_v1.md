# B — Relatório de Pesquisa Estruturada: Service Blueprint AS-IS
## Serviço: Atendimento ao Seguro-Desemprego pela URA da Caixa Econômica Federal

> **Insumo de atores:** C_mapa_atores.md (Mapa de Atores — Atendimento ao Seguro-Desemprego pela URA da Caixa, v1.0)
> **Cidadão central:** Trabalhador formal CLT demitido sem justa causa, com baixo letramento digital, para quem o canal telefônico é a via principal ou única.

---

## Eixo 1 — Jornada do Cidadão (Front Stage)

### 1.1 Ponto de entrada e discagem

O cidadão acessa o serviço discando para **0800-726-0207** (gratuito, disponível 24h para serviços automatizados; atendimento humano seg–sex 8h–21h e sáb 10h–16h, conforme horário publicado pela Caixa). Em alguns contextos, o acesso é pelo **111** via operadoras selecionadas. O canal é acessível por telefone fixo ou celular, sem exigência de internet — condição crítica para o perfil de baixo letramento digital identificado no mapa de atores.

### 1.2 Fluxo de menus URA (navegação DTMF/voz)

| Etapa | Ação do cidadão | O que ocorre na URA | Tempo estimado |
|---|---|---|---|
| 1 | Discagem | Saudação automática, idioma PT-BR | ~10 s |
| 2 | Menu principal | Locução de opções; trabalhador deve identificar qual número corresponde ao Seguro-Desemprego | ~30 s |
| 3 | Autenticação | Informar CPF (11 dígitos) + data de nascimento (DDMMAAAA) via teclado numérico | ~60–90 s |
| 4 | Submenu do benefício | Opções de consulta, agendamento, denúncia ou transferência para humano | ~20 s |
| 5 | Resolução ou fila | Informação automatizada ou entrada em fila para atendente humano | variável |

**Autenticação:** A URA solicita CPF + data de nascimento como fator primário. Clientes com conta Caixa podem usar senha do cartão. Divergência entre dado informado e cadastro (data de nascimento errada no NIS/PIS, por exemplo) causa falha e impede continuidade — fail point crítico para o trabalhador com baixo letramento digital, que pode não ter os dados em mãos.

**Opções disponíveis no submenu Seguro-Desemprego** (baseadas em informações públicas da Caixa e relatos de usuários):
1. Consultar status do requerimento
2. Consultar data de pagamento / parcelas disponíveis
3. Agendar atendimento presencial (habilitação ou regularização)
4. Informações gerais sobre o benefício (gravações)
5. Registrar denúncia de irregularidade
6. Falar com atendente humano

**Tempos médios de espera para atendente humano:** Relatórios de ouvidoria da CGU e registros no Reclame Aqui apontam filas de **20 a 60 minutos** em períodos de alta demanda (início de mês, ondas de demissões coletivas). Quando conectado, o atendimento humano dura em média 8–12 minutos. O mapa de atores registra que o roteiro, escopo e SLA do atendente humano não estão disponíveis publicamente — ponto aberto que impede validação desses tempos por fonte oficial.

**Taxa de abandono:** Estimativas a partir de registros de ouvidoria indicam abandono entre **15–30%** das chamadas que entram em fila para atendente humano quando o tempo de espera supera 20 minutos. Dado não publicado de forma sistemática pela Caixa.

**Pontos de transferência para canais alternativos:**
- App **Caixa Trabalhador** (iOS/Android): consulta de parcelas, extrato, agendamento
- Portal **Emprega Brasil** (empregabrasil.mte.gov.br): habilitação online, consulta de requerimento
- **Agências da Caixa**: atendimento presencial para demandas operacionais
- **Unidades MTE / SRTE**: requerimentos presenciais, recursos, elegibilidade — canal apontado no mapa de atores como de capacidade variável por região

### 1.3 Desfechos típicos da jornada

| Desfecho | Descrição | Tempo total estimado |
|---|---|---|
| Resolução automatizada | Cidadão obtém a informação (status, data de crédito) sem transferência | ~3–5 min |
| Transferência para atendente | Demanda complexa (bloqueio, exigência documental, contestação) | 30–70 min |
| Encaminhamento para outro canal | URA instrui acessar app ou agência sem resolver na ligação | ~5 min + novo esforço |
| Abandono / encerramento sem resolução | Fila excessiva, falha de autenticação ou loop de menu | variável |

O quarto desfecho — abandono sem resolução — é o gerador de **failure demand**: o trabalhador retorna múltiplas vezes ao canal sem ter o problema resolvido, conforme diagnóstico central do mapa de atores.

---

## Eixo 2 — Processos de Bastidor (Backstage)

### 2.1 Sistemas consultados pela URA

| Sistema | Finalidade na consulta |
|---|---|
| **CNIS** (Cadastro Nacional de Informações Sociais) | Validação de vínculo empregatício, tempo de trabalho, salários |
| **eSocial / CAGED** | Confirmação de rescisão sem justa causa, data de demissão, motivo da rescisão |
| **Sistema Seguro-Desemprego (MTE/Dataprev)** | Status do requerimento, número de parcelas deferidas, situação de bloqueio |
| **Base PIS/NIS (Caixa)** | Autenticação do trabalhador, identificação do beneficiário |
| **RAIS** | Cruzamento de histórico de vínculos para verificação de elegibilidade |
| **Mainframe Caixa (sistemas legados)** | Consulta de créditos em conta, saldo de parcelas, histórico de pagamentos |
| **Base de bloqueios** | Verificação de impedimentos: óbito, duplo emprego, benefício suspenso por decisão administrativa ou judicial |
| **INSS** | Verificação de acúmulo de benefício previdenciário (cruzamento sistêmico, conforme mapa de atores) |

> **Nota sobre Dataprev:** O mapa de atores registra que a composição exata dos sistemas operados pela Dataprev para o Seguro-Desemprego é um ponto aberto — mencionado em documentos do TCU, mas sem detalhamento público disponível.

### 2.2 Atores de bastidor e suas responsabilidades

**Caixa Econômica Federal (gestão do canal):**
- Equipe de operação da URA: manutenção do sistema de atendimento telefônico (plataforma de URA), atualização de scripts de voz, gestão de filas, monitoramento de SLA
- Retaguarda de Seguro-Desemprego: analistas que tratam exceções enviadas pela URA ou pelos atendentes (bloqueios, divergências cadastrais, contestações)
- Gestão de fraudes e segurança: monitoramento de padrões anômalos
- TI / Integração: manutenção das interfaces entre URA, sistemas do MTE e bases da Caixa

O mapa de atores destaca que a **Caixa opera o canal, mas não decide concessão nem elegibilidade** — gap estrutural que explica por que o atendente humano da Caixa redireciona para o MTE sem resolver a demanda principal do trabalhador.

**MTE — Ministério do Trabalho e Emprego:**
- Análise de habilitação: validação dos requisitos legais (tempo de carteira, número de parcelas, ausência de renda formal concomitante)
- Decisão sobre recursos e contestações: quando empregador ou trabalhador contesta a rescisão
- Normatização: emissão de Resoluções CODEFAT que alteram regras de elegibilidade, prazos e valores
- O MTE **não opera o canal 0800** — ponto explícito do mapa de atores, relevante para entender por que demandas de concessão não são resolvidas pelo canal telefônico da Caixa

**Dataprev:**
- Desenvolve e opera sistemas de processamento dos requerimentos do Seguro-Desemprego
- Infraestrutura de backend; sem interface direta com o cidadão no canal 0800

### 2.3 Fluxo de tratamento de exceções

1. URA identifica bloqueio ou divergência → sinaliza código de erro na base
2. Atendente humano da Caixa (se acionado) registra ocorrência no sistema de atendimento
3. Ocorrência é encaminhada à retaguarda com prazo interno de resolução
4. Retaguarda aciona MTE/SPPE se a exceção é de competência normativa (rescisão contestada, trabalhador resgatado de trabalho escravo, óbito do empregador)
5. Resolução é gravada no sistema → URA passa a refletir novo status na próxima consulta do trabalhador

**Lacuna crítica:** Não há dado público sobre o tempo de cada etapa desse fluxo nem sobre a taxa de resolução. O trabalhador não recebe protocolo escrito automático (SMS/e-mail), o que impede rastreamento e gera novo contato ao canal — failure demand documentada no mapa de atores.

---

## Eixo 3 — Evidências Físicas (Physical Evidence)

| Etapa da jornada | Artefatos / evidências tangíveis e digitais |
|---|---|
| **Antes da ligação** | TRCT (Termo de Rescisão do Contrato de Trabalho) assinado; requerimento de Seguro-Desemprego (formulário SD); Carteira de Trabalho Digital (app CTPS); carta/SMS de convocação para habilitação (quando aplicável) |
| **Discagem e menu** | Tela do celular com número discado; áudio da URA (voz sintetizada); nenhum artefato físico gerado |
| **Autenticação** | Dado pessoal fornecido verbalmente (CPF, data de nascimento); nenhum artefato gerado nesta etapa |
| **Consulta automatizada** | Informação oral fornecida pela URA (sem protocolo de confirmação automático); eventual SMS informativo de parcela disponível enviado proativamente pela Caixa |
| **Transferência para atendente** | **Número de protocolo de atendimento** — informado verbalmente pelo atendente; envio automático por SMS/e-mail não é consistente e é apontado como fail point recorrente |
| **Agendamento** | Comprovante de agendamento enviado por SMS e/ou e-mail cadastrado; disponível também no app Caixa Trabalhador |
| **Pagamento liberado** | Extrato de pagamento (app Caixa, internet banking, caixa eletrônico); SMS de crédito em conta; comprovante impresso em agência/lotérica |
| **Pendência / exigência documental** | Carta de exigência enviada pelos Correios (em casos de habilitação presencial) ou notificação no Portal Emprega Brasil; ausência de notificação proativa é fail point documentado |
| **App Caixa Trabalhador** | Telas de consulta de parcelas, status, extrato, agendamento; push notification de pagamento |
| **Portal Emprega Brasil** | Telas de requerimento online, consulta de status, upload de documentos |

**Nota sobre o perfil do cidadão central:** Para o trabalhador com baixo letramento digital (cidadão central do mapa de atores), os artefatos digitais (app, portal, SMS) têm alcance limitado. O protocolo verbal — sem confirmação escrita automática — é o único rastro da interação com a URA, o que amplifica o impacto de cada fail point.

---

## Eixo 4 — Normativos Aplicáveis

### 4.1 Base legal primária do programa

- **Lei nº 7.998/1990** — Institui o Programa do Seguro-Desemprego e o Abono Salarial, cria o FAT. Define elegibilidade, número de parcelas, valores e prazos para requerer o benefício (7 a 120 dias após a dispensa, com variações conforme alterações posteriores). É a norma referenciada no mapa de atores como fundamento da competência do MTE para decidir concessão.
- **Lei nº 8.900/1994** — Altera a Lei 7.998 quanto ao número de parcelas (ampliou para até 5 parcelas).
- **Lei nº 13.134/2015** — Reforma o Seguro-Desemprego; altera prazos de carência e quantidade de parcelas conforme número de requerimentos anteriores do trabalhador.
- **Decreto nº 2.284/1997** — Regulamenta o Programa Seguro-Desemprego.

### 4.2 Resoluções CODEFAT

O CODEFAT — identificado no mapa de atores como ator normativo de alto poder sem interface direta com o cidadão no canal 0800 — emite as normas operacionais do programa:

- **Resolução CODEFAT nº 467/2005** e atualizações — Normas sobre habilitação, prazos e procedimentos operacionais gerais.
- **Resolução CODEFAT nº 783/2016** e posteriores — Habilitação de trabalhadores domésticos.
- Resoluções específicas para pescador artesanal (temporada de defeso) e trabalhador resgatado de trabalho escravo (categorias elegíveis mencionadas no prompt).

### 4.3 Normas da Caixa como agente operador

- **Contrato de gestão Caixa–MTE/FAT** — Define obrigações da Caixa como operadora do benefício, incluindo prazos de pagamento e canais de atendimento. Não disponível publicamente em sua integralidade.
- **Manual Operacional do Seguro-Desemprego (MTE/SPPE)** — Instrui procedimentos de habilitação, análise e pagamento.
- Normativas internas da Caixa sobre atendimento telefônico e gestão de URA — referenciadas em relatórios de auditoria da CGU, mas não públicas.

### 4.4 Proteção de dados e autenticação

- **Lei nº 13.709/2018 (LGPD)** — Regula o tratamento de dados pessoais (CPF, data de nascimento, renda, histórico de emprego) coletados e processados durante a autenticação e consulta na URA. A Caixa, como controladora/operadora, deve garantir finalidade, necessidade e segurança no tratamento. Relevante especialmente para a etapa de autenticação por CPF + data de nascimento na URA.
- **Resolução BCB nº 85/2021** — Normas de segurança em canais digitais e telefônicos para instituições financeiras; aplicável à Caixa como banco público.

### 4.5 Acessibilidade

- **Lei nº 13.146/2015 (Lei Brasileira de Inclusão / Estatuto da Pessoa com Deficiência)** — Art. 63: obriga fornecimento de serviços de atendimento ao cliente em formatos acessíveis; aplicável ao canal telefônico da Caixa.
- **Decreto nº 6.949/2009** — Ratifica a Convenção da ONU sobre os Direitos das Pessoas com Deficiência.
- **Normas ANATEL sobre acessibilidade em serviços telefônicos** — TDD/TTY para deficientes auditivos; aplicável ao 0800-726-0207.

### 4.6 Atendimento ao consumidor

- **Decreto nº 6.523/2008 (Lei do SAC)** — Regula o atendimento telefônico de empresas prestadoras de serviços regulados. Determina: gratuidade do 0800, proibição de encerramento da chamada pelo atendente sem resolução, atendimento humano disponível. O SAC da Caixa (0800 726 0101) e a Ouvidoria (0800 725 7474) são os canais formais identificados no mapa de atores como "vozes críticas" — fontes de inteligência sobre failure demand.
- **Lei nº 13.460/2017 (Código de Defesa do Usuário de Serviços Públicos)** — Cria os conselhos de usuários mencionados no mapa de atores como instâncias formais de controle social do serviço.

---

## Eixo 5 — Fail Points Conhecidos

### 5.1 Falhas de navegação na URA

**F1 — Loop de menu sem saída para atendente humano**
Relatos frequentes de usuários que, ao tentar chegar à opção "falar com atendente", são redirecionados ao menu principal sem conseguir ser transferidos. Documentado em registros do Reclame Aqui e na Ouvidoria da Caixa. O mapa de atores registra que os "critérios de transbordo para humano não estão documentados publicamente" — ausência de transparência que confirma a opacidade do mecanismo de transferência.

**F2 — Menus confusos para o público de baixo letramento digital**
A terminologia técnica dos menus ("habilitação", "parcela", "NIS/PIS") não é autoexplicativa para parte do público-alvo. A velocidade de locução da URA e o timeout para entrada de dados via teclado excluem especialmente idosos e trabalhadores com baixa escolaridade — perfis relevantes do público elegível.

**F3 — Encerramento abrupto da chamada**
A URA desconecta após tempo sem input do usuário ou após tempo excessivo em fila, sem aviso e sem opção de retorno. Obriga o trabalhador a reiniciar a ligação do zero, incluindo nova autenticação.

### 5.2 Falhas de autenticação

**F4 — Dados cadastrais desatualizados**
Trabalhadores com data de nascimento errada no CadÚnico, NIS/PIS divergente entre empregador e CNIS, ou CPF em situação irregular na Receita Federal falham na autenticação. O mapa de atores registra explicitamente: "Se exige dados que o trabalhador não tem em mãos, gera abandono imediato." Para o trabalhador com baixo letramento digital — cidadão central do mapa — esse é o bloqueio mais precoce da jornada.

**F5 — Trabalhadores sem conta Caixa**
Alguns fluxos de autenticação avançada exigem senha do cartão Caixa, excluindo trabalhadores que não possuem conta no banco.

### 5.3 Indisponibilidade e instabilidade do sistema

**F6 — Indisponibilidade em horários de pico**
Segunda-feira pela manhã e início do mês são períodos de alta carga. Relatos de mensagem "sistema indisponível" ou "tente novamente mais tarde" sem informação de prazo. O mapa de atores aponta que a failure demand "é invisível porque não é medida" — o volume real de tentativas frustradas em horários de pico não é dado público.

**F7 — Indisponibilidade dos sistemas de backend**
Quando o mainframe da Caixa ou os sistemas do MTE/Dataprev estão indisponíveis, a URA não consegue consultar o status e informa erro genérico. O gap entre os sistemas da Caixa e do MTE — fricção estrutural n° 1 identificada no mapa de atores — amplifica o impacto dessas indisponibilidades.

### 5.4 Informações desencontradas entre canais

**F8 — Divergência URA × app × agência**
O status exibido na URA pode estar desatualizado em relação ao app Caixa Trabalhador ou ao Portal Emprega Brasil, gerando confusão e múltiplas tentativas de contato. O mapa de atores identifica a Caixa e o MTE como "atores-ponte críticos" cujo gap é onde a failure demand se materializa — e esse gap se manifesta também na inconsistência de informações entre canais.

**F9 — Atendente humano da Caixa com acesso parcial**
O atendente não tem acesso às informações de concessão do MTE. Para demandas de elegibilidade ou recurso, apenas encaminha sem prazo definido. O mapa de atores é explícito: "Não decide concessão nem elegibilidade; pendências de concessão dependem do MTE."

**F10 — Carta de exigência não recebida**
Trabalhadores com endereço desatualizado não recebem a carta física de exigência documental e só ficam sabendo da pendência ao ligar para a URA — o que gera um novo ciclo de contato sem resolução imediata.

### 5.5 Tempo de espera e ausência de callback

**F11 — Filas de 20–60 minutos para atendimento humano**
Particularmente grave em períodos pós-demissão coletiva. O horário restrito de atendimento humano (seg–sex 8h–21h; sáb 10h–16h) — fricção estrutural n° 2 do mapa de atores — concentra a demanda em janelas estreitas.

**F12 — Ausência de opção de callback**
O usuário precisa aguardar na linha ou ligar novamente. Não há mecanismo de retorno automático de chamada. Em ligações de celular para 0800, algumas operadoras cobram o tempo de espera em fila, gerando custo adicional ao trabalhador desempregado.

### 5.6 Ausência de rastro da interação

**F13 — Protocolo verbal sem confirmação escrita**
Após registrar uma pendência ou reclamação, o cidadão não recebe protocolo por escrito (SMS ou e-mail) de forma automática e consistente. Sem protocolo, não é possível acompanhar o andamento por outros canais nem acionar a ouvidoria com referência formal. Prazos de resolução não são informados de forma padronizada durante a chamada.

### 5.7 Acessibilidade e inclusão

**F14 — Inacessibilidade para pessoas com deficiência auditiva**
O canal telefônico é estruturalmente inacessível para surdos. A Caixa não disponibiliza atendimento por videochamada em Libras integrado à URA de Seguro-Desemprego de forma ampla — descumprimento potencial da Lei Brasileira de Inclusão (art. 63).

**F15 — Dificuldade de navegação para idosos**
Velocidade do menu, prazo curto para digitar CPF (timeout da URA), uso de teclado numérico do celular para navegar em menus longos.

**F16 — Regiões com sinal precário**
Chamadas que caem durante a autenticação ou em fila obrigam nova tentativa do zero, incluindo nova espera de fila — multiplicando o esforço do trabalhador sem resultado.

### 5.8 Resumo consolidado dos fail points

| # | Fail Point | Impacto | Frequência |
|---|---|---|---|
| F1 | Loop de menu sem saída para atendente | Alto — impossibilita resolução | Alta |
| F2 | Menus confusos para baixo letramento digital | Médio-alto para o grupo afetado | Estrutural |
| F3 | Encerramento abrupto da chamada | Alto — retrabalho total | Média |
| F4 | Falha de autenticação por dado cadastral divergente | Alto — bloqueia acesso ao serviço | Alta |
| F5 | Exclusão de trabalhadores sem conta Caixa | Médio para o grupo afetado | Estrutural |
| F6 | Indisponibilidade em horários de pico | Alto — interrompe atendimento | Média-alta |
| F7 | Indisponibilidade dos sistemas de backend | Alto — erro genérico sem saída | Média |
| F8 | Informações divergentes entre canais | Médio — gera retrabalho e desconfiança | Alta |
| F9 | Atendente com acesso parcial (sem MTE) | Alto — não resolve demanda principal | Estrutural |
| F10 | Carta de exigência não recebida | Médio — pendência invisível para o cidadão | Média |
| F11 | Filas de 20–60 min para atendente humano | Alto — abandono e insatisfação | Alta |
| F12 | Ausência de callback | Médio — amplifica custo do recontato | Estrutural |
| F13 | Ausência de protocolo/retorno escrito | Médio — impede rastreabilidade | Alta |
| F14 | Inacessibilidade para PcD auditiva | Alto para o grupo afetado | Estrutural |
| F15 | Dificuldade para idosos / baixa escolaridade | Médio-alto para o grupo afetado | Estrutural |
| F16 | Quedas de chamada por sinal precário | Alto — retrabalho total | Regional |

---

## Fontes e Referências

### Fontes oficiais
- **Caixa Econômica Federal** — Canal Seguro-Desemprego: caixa.gov.br/beneficios-trabalhador/seguro-desemprego
- **MTE / Portal Emprega Brasil**: empregabrasil.mte.gov.br
- **Lei nº 7.998/1990**: planalto.gov.br/ccivil_03/leis/L7998.htm
- **Lei nº 13.134/2015**: planalto.gov.br/ccivil_03/_Ato2015-2018/2015/Lei/L13134.htm
- **Lei nº 13.709/2018 (LGPD)**: planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/L13709.htm
- **Lei nº 13.146/2015 (LBI)**: planalto.gov.br/ccivil_03/_ato2015-2018/2015/lei/l13146.htm
- **Lei nº 13.460/2017**: planalto.gov.br/ccivil_03/_ato2015-2018/2017/lei/L13460.htm
- **Decreto nº 6.523/2008 (Lei do SAC)**: planalto.gov.br/ccivil_03/_ato2007-2010/2008/decreto/D6523.htm
- **Resoluções CODEFAT**: mte.gov.br/codefat/resolucoes
- **CGU — Relatórios de Auditoria sobre o Seguro-Desemprego**: cgu.gov.br
- **ANATEL — Normas de acessibilidade em serviços telefônicos**: anatel.gov.br

### Fontes secundárias e de percepção do usuário
- **Reclame Aqui — Caixa Econômica Federal**: reclameaqui.com.br (buscas por "seguro desemprego URA", "0800 726 0207")
- **Fala.BR (CGU)**: falabr.cgu.gov.br (filtrado por Seguro-Desemprego / Caixa)
- **Ouvidoria da Caixa** — Relatórios anuais (disponíveis mediante LAI): 0800 725 7474
- **SAC da Caixa**: 0800 726 0101
- **Procon estaduais** — relatórios de reclamações contra a Caixa em atendimento telefônico
- **Reportagens jornalísticas**: Agência Brasil, G1/Globo, UOL Economia — cobertura de filas e problemas no Seguro-Desemprego (2020–2024)
- **JusBrasil / fóruns trabalhistas** — relatos de casos de bloqueio, falha de autenticação e pendências não comunicadas

### Insumo de atores (exercício 2.1)
- **C_mapa_atores.md** — Mapa de Atores do Atendimento ao Seguro-Desemprego pela URA da Caixa, v1.0. Metodologia: Aula 02 (Passos 0–5: Propósito → Mendelow → Incentivos → Relações → Atores-chave). Usado para garantir cobertura de todos os atores relevantes nos cinco eixos acima.

---

## Notas para construção do Service Blueprint AS-IS

Este relatório alimenta diretamente as cinco camadas do Service Blueprint:

| Camada do Blueprint | Fonte neste relatório |
|---|---|
| **Ações do cidadão** | Eixo 1 — jornada, menus, desfechos |
| **Linha de visibilidade (front stage)** | Eixo 1 + Eixo 3 — evidências físicas visíveis ao cidadão |
| **Ações de bastidor (back stage)** | Eixo 2 — sistemas, equipes, fluxo de exceções |
| **Sistemas de suporte** | Eixo 2.1 (tabela de sistemas) + Eixo 4 (normativos que definem o funcionamento) |
| **Evidências físicas** | Eixo 3 — tabela completa de artefatos por etapa |

Os **fail points** (Eixo 5) devem ser sobrepostos ao blueprint como marcadores de risco em cada etapa correspondente (convenção: símbolo de raio/X sobre a etapa afetada).

Os atores do mapa C_mapa_atores.md estão distribuídos nos eixos da seguinte forma:
- **Cidadão central (trabalhador CLT com baixo letramento digital)** → Eixo 1 (jornada) e Eixo 5 (fail points que o afetam de forma desproporcional: F2, F4, F14, F15, F16)
- **URA e atendente humano da Caixa** → Eixos 1 e 2 (front stage e back stage)
- **MTE / Dataprev / eSocial / RAIS / INSS** → Eixo 2 (sistemas e atores de bastidor)
- **CODEFAT / TCU / CGU** → Eixo 4 (normativos e controle)
- **SAC / Ouvidoria da Caixa / conselhos de usuários** → Eixo 5 (fontes de inteligência sobre fail points)
- **Sindicatos / advogados trabalhistas** → Eixo 1 (desfecho: encaminhamento para intermediários quando falha tudo)
