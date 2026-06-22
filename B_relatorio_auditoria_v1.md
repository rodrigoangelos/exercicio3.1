Auditoria rigorosa da pesquisa

Conclusão geral: a pesquisa tem utilidade como hipótese inicial de blueprint, mas mistura fatos oficiais, inferências operacionais não verificadas, relatos anedóticos e normas desatualizadas como se tivessem o mesmo grau probatório. O principal problema é que ela descreve um fluxo detalhado de URA, submenu, autenticação, filas, backstage e tratamento de exceções sem evidência pública suficiente para sustentar esse nível de granularidade.

Abaixo estão as falhas substantivas identificadas.

⸻

1) Erros factuais ou afirmações provavelmente falsas

1.1 O canal 111 foi tratado como acesso ao Seguro-Desemprego

Trecho auditado: “Em alguns contextos, o acesso é pelo 111 via operadoras selecionadas.”

Falha: A fonte oficial da Caixa lista o 111 como “Atendimento Bolsa Família”, enquanto o Seguro-Desemprego aparece nos canais de consulta da Caixa como App CAIXA Tem, App Benefícios Sociais CAIXA, Portal Cidadão e 0800 726 0207. A pesquisa não demonstrou que o 111 seja canal de URA para Seguro-Desemprego.  

Justificativa: Isso altera o ponto de entrada da jornada. O 111 não deveria aparecer como caminho do serviço sem prova específica.

⸻

1.2 “App Caixa Trabalhador” está desatualizado ou, no mínimo, mal especificado

Trechos auditados:
“App Caixa Trabalhador (iOS/Android): consulta de parcelas, extrato, agendamento”
“App Caixa Trabalhador | Telas de consulta de parcelas, status, extrato, agendamento; push notification de pagamento”

Falha: As fontes atuais da Caixa apontam como canal pertinente o App Benefícios Sociais CAIXA, além do CAIXA Tem e Portal Cidadão; o resultado oficial descreve o aplicativo Benefícios Sociais CAIXA como canal para Seguro-Desemprego, Abono Salarial, INSS e Pé-de-Meia.  

Justificativa: O relatório usa uma nomenclatura antiga/provavelmente incorreta como evidência física central. Isso compromete a camada de canais digitais do blueprint.

⸻

1.3 O relatório atribui à URA funções que não foram comprovadas

Trecho auditado: “Opções disponíveis no submenu Seguro-Desemprego: 1. Consultar status do requerimento; 2. Consultar data de pagamento / parcelas disponíveis; 3. Agendar atendimento presencial; 4. Informações gerais; 5. Registrar denúncia de irregularidade; 6. Falar com atendente humano.”

Falha: A Caixa informa o 0800 726 0207 como atendimento referente a PIS, Benefícios Sociais, FGTS e Cartão Social, com atendimento eletrônico 24h e humano em horários determinados; mas a pesquisa não cita gravação, transcrição, árvore de URA, manual operacional ou teste controlado que comprove esse submenu específico.  

Justificativa: Esse é um erro metodológico grave: a tabela transforma hipótese de navegação em fato operacional. Em blueprint AS-IS, menu real precisa vir de evidência direta.

⸻

1.4 “Agendar atendimento presencial” pela URA da Caixa é não comprovado e possivelmente deslocado

Trecho auditado: “Agendar atendimento presencial (habilitação ou regularização)”

Falha: A Resolução CODEFAT nº 957/2022 estabelece que o trabalhador deve requerer o benefício pelo portal gov.br/Carteira de Trabalho Digital e, se não puder usar meios digitais, presencialmente em unidades das Superintendências Regionais do Trabalho ou SINE. Não há suporte, nas fontes verificadas, para “agendamento de habilitação” pela URA da Caixa.  

Justificativa: A pesquisa confunde o papel da Caixa como agente pagador/canal de consulta com a prestação do serviço administrativo de requerimento/habilitação pelo MTE/SINE.

⸻

1.5 “Registrar denúncia de irregularidade” no submenu de Seguro-Desemprego não foi comprovado

Trecho auditado: “Registrar denúncia de irregularidade”

Falha: A pesquisa não apresenta fonte oficial ou evidência empírica de que a URA 0800 726 0207 tenha opção específica de denúncia de irregularidade do Seguro-Desemprego.

Justificativa: Denúncia é função sensível; colocá-la no front stage sem prova cria uma jornada falsa e pode induzir desenho de serviço baseado em capacidade inexistente.

⸻

1.6 A autenticação “CPF + data de nascimento” foi afirmada sem fonte

Trecho auditado: “A URA solicita CPF + data de nascimento como fator primário.”

Falha: A pesquisa não apresenta evidência direta da URA. Há base normativa mostrando que CPF, NIS, data de nascimento e outros dados são transmitidos pelo empregador no Empregador Web, mas isso não comprova que a URA use CPF + data de nascimento como autenticação primária.  

Justificativa: O relatório inferiu a autenticação de bases cadastrais para o fluxo telefônico. São camadas distintas.

⸻

1.7 “Clientes com conta Caixa podem usar senha do cartão” foi afirmado sem evidência

Trecho auditado: “Clientes com conta Caixa podem usar senha do cartão.”

Falha: Não há fonte citada que demonstre esse passo no fluxo de Seguro-Desemprego da URA.

Justificativa: A exigência ou alternativa por senha de cartão muda drasticamente o risco de exclusão, fraude e abandono. Não pode ser lançada como fato sem captura da URA, manual ou página oficial.

⸻

1.8 “Trabalhadores sem conta Caixa” como fail point é mal sustentado

Trecho auditado: “F5 — Trabalhadores sem conta Caixa: Alguns fluxos de autenticação avançada exigem senha do cartão Caixa, excluindo trabalhadores que não possuem conta no banco.”

Falha: A Resolução CODEFAT nº 957/2022 prevê pagamento por crédito em conta de titularidade do beneficiário, conta digital ou outra conta localizada pelo agente pagador; e, na impossibilidade, por outras formas disponíveis. A Caixa também informa que, para o Seguro-Desemprego, o pagamento pode ocorrer em conta indicada pelo trabalhador, inclusive de outro banco, ou por alternativas de saque.  

Justificativa: “Não ter conta Caixa” não é, por si, barreira operacional demonstrada. A barreira real poderia ser “não conseguir acessar conta digital/CAIXA Tem”, “restrição cadastral”, “sem Cartão Social/senha” ou “dificuldade de saque”, mas isso não foi formulado corretamente.

⸻

1.9 A pesquisa usa Decreto nº 2.284/1997 como regulamento do Seguro-Desemprego

Trecho auditado: “Decreto nº 2.284/1997 — Regulamenta o Programa Seguro-Desemprego.”

Falha: O MTE informa que o Seguro-Desemprego foi introduzido pelo Decreto-Lei nº 2.284, de 10 de março de 1986, e regulamentado pelo Decreto nº 92.608, de 30 de abril de 1986.  

Justificativa: A referência normativa está errada em número, espécie normativa e ano.

⸻

1.10 Resolução CODEFAT nº 467/2005 aparece como norma vigente operacional

Trecho auditado: “Resolução CODEFAT nº 467/2005 e atualizações — Normas sobre habilitação, prazos e procedimentos operacionais gerais.”

Falha: A Resolução CODEFAT nº 957/2022 revogou a Resolução nº 467/2005; a própria norma lista a Resolução nº 467/2005 entre as revogadas e entrou em vigor em 3 de outubro de 2022.  

Justificativa: Para auditoria AS-IS em 2026, a referência central deveria ser a Resolução CODEFAT nº 957/2022, não a 467/2005.

⸻

1.11 Resolução CODEFAT nº 783/2016 é referência suspeita para domésticos

Trecho auditado: “Resolução CODEFAT nº 783/2016 e posteriores — Habilitação de trabalhadores domésticos.”

Falha: As fontes encontradas apontam a regulamentação histórica do doméstico pela Resolução CODEFAT nº 754/2015 e, atualmente, pela Resolução CODEFAT nº 957/2022; a busca pela 783 retornou norma de qualificação profissional, não a regulamentação principal do Seguro-Desemprego doméstico.  

Justificativa: É uma referência normativa provavelmente incorreta.

⸻

1.12 Decreto do SAC de 2008 está revogado

Trecho auditado: “Decreto nº 6.523/2008 (Lei do SAC) — Regula o atendimento telefônico…”

Falha: O Decreto nº 6.523/2008 foi revogado pelo Decreto nº 11.034/2022.  

Justificativa: A pesquisa usa norma revogada para avaliar atendimento telefônico. Além disso, chama decreto de “Lei do SAC”, o que é tecnicamente impreciso.

⸻

1.13 Aplicabilidade do Decreto do SAC ao serviço público foi tratada de modo simplista

Trecho auditado: “Decreto nº 6.523/2008 … Regula o atendimento telefônico de empresas prestadoras de serviços regulados.”

Falha: Mesmo à época, o decreto regulamentava SAC no âmbito de fornecedores de serviços regulados pelo Poder Público federal, com base no Código de Defesa do Consumidor. O serviço analisado é um benefício público operado por banco público como agente pagador, não uma relação comum de consumo. A pesquisa não enfrentou a distinção entre SAC bancário/consumerista, atendimento Caixa Cidadão e serviço público regido pela Lei nº 13.460/2017.  

Justificativa: Pode haver incidência de normas de atendimento bancário/consumerista em canais da Caixa, mas isso exige análise jurídica específica; o relatório presumiu aplicabilidade.

⸻

1.14 Resolução BCB nº 85/2021 foi mal caracterizada

Trecho auditado: “Resolução BCB nº 85/2021 — Normas de segurança em canais digitais e telefônicos para instituições financeiras.”

Falha: A Resolução BCB nº 85/2021 é apontada por fonte do próprio BCB como norma sobre política de segurança cibernética e requisitos para contratação de serviços de processamento/armazenamento de dados e computação em nuvem, não como norma específica de atendimento telefônico/URA.  

Justificativa: A norma pode ser relevante para segurança cibernética e terceirização tecnológica, mas não sustenta diretamente regras de URA telefônica.

⸻

1.15 A pesquisa afirma que 0800 por celular pode gerar cobrança em fila

Trecho auditado: “Em ligações de celular para 0800, algumas operadoras cobram o tempo de espera em fila…”

Falha: O próprio relatório afirma que o número é gratuito. A Caixa qualifica o 0800 726 0207 como atendimento telefônico 0800, e o Decreto do SAC revogado citado pelo próprio relatório tratava de gratuidade de SAC; a pesquisa não traz evidência de cobrança por operadoras.  

Justificativa: É uma alegação forte e potencialmente falsa. Se houver bloqueio ou limitação de celular, isso precisa ser demonstrado por norma da Anatel, contrato da Caixa ou teste de operadoras.

⸻

1.16 “Carta de exigência pelos Correios” não foi sustentada e conflita com digitalização

Trecho auditado: “Carta de exigência enviada pelos Correios (em casos de habilitação presencial) ou notificação no Portal Emprega Brasil.”

Falha: A Resolução CODEFAT nº 957/2022 prevê que notificações sobre deferimento, indeferimento ou exigências podem ocorrer exclusivamente por meio digital, mediante anuência e cadastramento no gov.br ou Carteira de Trabalho Digital.  

Justificativa: Pode haver comunicações físicas em casos específicos, mas o relatório não prova que “carta pelos Correios” seja evidência típica do fluxo AS-IS.

⸻

1.17 “Agências da Caixa para demandas operacionais” foi amplo demais

Trecho auditado: “Agências da Caixa: atendimento presencial para demandas operacionais”

Falha: A Caixa atua como agente pagador; a concessão, gestão e indicação dos trabalhadores são do MTE. A Caixa informa que o MTE responde por concessão/valor e que a Caixa disponibiliza canais de consulta conforme calendário de pagamento.  

Justificativa: O relatório deveria distinguir: agência/lotérica/CAIXA Aqui para saque/pagamento e canais MTE/SINE/SRTE para requerimento, recurso, elegibilidade e exigência.

⸻

2) Inferências mal suportadas e fontes fracas

2.1 Tempos de espera de 20–60 minutos foram apresentados como quase-fato

Trecho auditado: “Relatórios de ouvidoria da CGU e registros no Reclame Aqui apontam filas de 20 a 60 minutos…”

Falha: A pesquisa não cita relatório específico, período, amostra, método, URL, extração do Reclame Aqui ou filtragem. Reclame Aqui é fonte de percepção, enviesada por autorreclamação, não base estatística.

Justificativa: Pode ser hipótese plausível, mas não “tempo médio”. Deveria constar como “relatos anedóticos sugerem esperas longas; sem base oficial de ASA/tempo médio”.

⸻

2.2 Atendimento humano “8–12 minutos” não tem sustentação

Trecho auditado: “Quando conectado, o atendimento humano dura em média 8–12 minutos.”

Falha: Não há fonte operacional, relatório de contact center, SLA, TMA ou auditoria citada.

Justificativa: TMA é métrica interna; sem base, o número é inventado ou especulativo.

⸻

2.3 Taxa de abandono de 15–30% é especulativa

Trecho auditado: “Estimativas a partir de registros de ouvidoria indicam abandono entre 15–30%…”

Falha: Reclamações de ouvidoria não permitem estimar abandono de fila sem denominador de chamadas, chamadas ofertadas, atendidas, abandonadas e tempo de abandono.

Justificativa: É estatística operacional indevidamente inferida de base inadequada.

⸻

2.4 Frequência dos fail points foi inventada

Trecho auditado: tabela final com “Alta”, “Média”, “Média-alta”, “Estrutural”.

Falha: A pesquisa não apresenta base quantitativa para frequência.

Justificativa: Impacto pode ser avaliado qualitativamente; frequência exige dados. A tabela deveria marcar “não mensurado” ou “sem evidência pública”.

⸻

2.5 Reclame Aqui, JusBrasil e fóruns foram usados sem controle probatório

Trecho auditado: “Fontes secundárias e de percepção do usuário: Reclame Aqui… JusBrasil / fóruns trabalhistas…”

Falha: São fontes úteis para descobrir hipóteses, mas fracas para validar operação AS-IS. JusBrasil costuma replicar peças, decisões ou conteúdo jurídico sem representar operação de canal; fóruns e RA são autorrelatos.

Justificativa: O relatório deveria separar evidência: oficial/normativa, evidência empírica direta, reclamações anedóticas e inferências.

⸻

2.6 “Mapa de atores” foi usado como fonte factual externa

Trecho auditado: múltiplos: “conforme mapa de atores”, “documentada no mapa de atores”, “ponto explícito do mapa…”

Falha: O mapa de atores é insumo analítico do próprio exercício, não evidência independente da operação real.

Justificativa: O relatório circulariza: usa um artefato anterior para confirmar achados que precisariam ser validados por documentos oficiais, testes ou dados operacionais.

⸻

3) Etapas de bastidor omitidas ou mal modeladas

3.1 Papel do empregador e do Empregador Web ficou subdimensionado

Trecho auditado: Eixo 2 lista sistemas, mas o fluxo de exceções começa na “URA identifica bloqueio”.

Falha: A Resolução CODEFAT nº 957/2022 coloca o empregador como ator de bastidor essencial: na dispensa sem justa causa, ele comunica ao MTE os dados necessários ao requerimento, exclusivamente pelo portal Empregador Web, com certificado digital ICP-Brasil, e deve disponibilizar formulário ao trabalhador.  

Justificativa: O backstage real começa antes da ligação, com transmissão de dados pelo empregador. Falhas de nome da mãe, PIS, CPF, data de nascimento, salários, data de admissão/demissão e CBO são pontos críticos omitidos.

⸻

3.2 Requerimento digital via gov.br/Carteira de Trabalho Digital foi tratado como canal alternativo, não como fluxo normativo principal

Trecho auditado: “Portal Emprega Brasil: habilitação online, consulta de requerimento” e “Pontos de transferência para canais alternativos”.

Falha: Pela Resolução CODEFAT nº 957/2022, o trabalhador deve se cadastrar no portal gov.br ou Carteira de Trabalho Digital e usar o serviço digital “solicitar o seguro-desemprego”; o presencial é exceção quando não puder usar as plataformas digitais.  

Justificativa: O relatório inverte a centralidade: telefone da Caixa é canal de consulta/pagamento, enquanto o requerimento é MTE/gov.br/CTPS Digital/SINE/SRTE.

⸻

3.3 Fluxo de recurso administrativo foi pouco descrito

Trecho auditado: “Retaguarda aciona MTE/SPPE se a exceção é de competência normativa…”

Falha: O serviço oficial “Cadastrar recurso relativo ao seguro-desemprego” permite revisão por recurso administrativo ao MTE quando o requerimento é indeferido, com prazo de 120 dias contados da notificação.  

Justificativa: Recurso não é apenas “retaguarda aciona MTE”; é um serviço próprio, com prazo, rito e canal. Isso deveria estar no backstage e nos fail points.

⸻

3.4 Canais MTE foram omitidos ou secundarizados

Trecho auditado: O relatório foca no 0800 Caixa e menciona MTE/SRTE apenas como encaminhamento.

Falha: O portal gov.br do serviço informa que dúvidas, reclamações ou sugestões sobre o serviço devem ser dirigidas ao teleatendimento 158; notícia oficial do MTE descreve a Central Alô Trabalho 158 como canal para informações sobre Seguro-Desemprego, CTPS Digital, gov.br e CAGED.  

Justificativa: Se a pergunta é operação do atendimento ao Seguro-Desemprego, a pesquisa deveria mapear a fronteira 0800 Caixa × 158 MTE.

⸻

3.5 Forma de pagamento e reemissão de parcelas foram omitidas

Trecho auditado: Eixo 2.1 fala em “saldo de parcelas” e “histórico de pagamentos”, mas não descreve ciclo de pagamento.

Falha: A Resolução nº 957/2022 prevê pagamento por crédito em conta, conta digital/outra conta localizada pelo agente pagador, outras formas disponíveis, comprovação por autenticação/registro eletrônico, disponibilidade da parcela por 67 dias e reemissão em até dois anos.  

Justificativa: Esses são bastidores e fail points centrais: conta incorreta, conta não localizada, parcela devolvida ao FAT, reemissão, contestação de recebimento.

⸻

3.6 Suspensão e cancelamento foram mal modelados

Trecho auditado: “Base de bloqueios: óbito, duplo emprego, benefício suspenso por decisão administrativa ou judicial”

Falha: A norma lista hipóteses de suspensão: novo emprego, benefício previdenciário continuado, recusa injustificada de ações de recolocação; e cancelamento: recusa de emprego condizente, falsidade, fraude, morte, fim da suspensão contratual.  

Justificativa: O relatório usa categorias vagas e deixa fora a lógica normativa exata de suspensão/cancelamento.

⸻

3.7 Intermediação de mão de obra e qualificação foram omitidas como parte da finalidade do programa

Trecho auditado: O serviço é tratado quase só como consulta/pagamento.

Falha: A Resolução nº 957/2022 define a finalidade do programa também como auxiliar busca ou preservação de emprego por ações integradas de orientação, recolocação e qualificação profissional.  

Justificativa: Pode não estar na URA da Caixa, mas está no serviço público Seguro-Desemprego e afeta encaminhamentos, cancelamento por recusa e atuação SINE.

⸻

3.8 Backstage de tratamento de inconsistências foi inventado em vez de normatizado

Trecho auditado:
“1. URA identifica bloqueio ou divergência → sinaliza código de erro na base
2. Atendente humano da Caixa registra ocorrência…
3. Ocorrência é encaminhada à retaguarda…
4. Retaguarda aciona MTE/SPPE…”

Falha: A norma prevê que, em inconsistência que impeça a habilitação automática, o trabalhador tem direito à revisão mediante recurso para correção dos dados. Não há evidência de que a URA abra “código de erro”, que a Caixa encaminhe à retaguarda ou que exista SLA interno Caixa→MTE para esses casos.  

Justificativa: O fluxo de exceção é uma arquitetura plausível, mas não comprovada.

⸻

4) Evidências físicas ou normativos relevantes que ficaram de fora

4.1 Formulário/requerimento transmitido pelo empregador

Trecho auditado: “Antes da ligação: TRCT; requerimento de Seguro-Desemprego (formulário SD)…”

Falha: O relatório não vinculou o formulário ao envio eletrônico pelo Empregador Web nem listou os dados críticos transmitidos pelo empregador.

Justificativa: A norma exige transmissão eletrônica e disponibilização do formulário ao trabalhador; isso é evidência física/digital essencial.  

⸻

4.2 Gov.br e Carteira de Trabalho Digital como artefatos primários

Trecho auditado: “Portal Emprega Brasil” e “App Caixa Trabalhador” aparecem como artefatos.

Falha: O artefato normativo primário para requerer é o portal gov.br ou o aplicativo Carteira de Trabalho Digital, por meio do serviço “solicitar o seguro-desemprego”.  

Justificativa: A evidência física deveria incluir login gov.br, nível de conta, termo de aceite, tela do requerimento, comprovante de solicitação e notificações digitais.

⸻

4.3 Notificação digital de exigências/deferimento/indeferimento

Trecho auditado: “Carta de exigência enviada pelos Correios… ausência de notificação proativa…”

Falha: A norma prevê notificações digitais de deferimento, indeferimento e exigências mediante anuência/cadastro.  

Justificativa: O relatório omite o artefato normativo de notificação digital e privilegia carta física sem prova.

⸻

4.4 Protocolo/recurso administrativo MTE

Trecho auditado: “Sem protocolo, não é possível acompanhar…”

Falha: Para indeferimento, existe serviço de recurso administrativo ao MTE; a pesquisa não mapeia comprovante/protocolo desse recurso, anexos, prazo e status.  

Justificativa: Isso é uma evidência física central no ciclo de exceção.

⸻

4.5 Comprovação de pagamento arquivada pelo agente pagador

Trecho auditado: “Extrato de pagamento… SMS de crédito… comprovante impresso.”

Falha: A norma prevê comprovação por autenticação em documento próprio ou registro eletrônico, arquivado no agente pagador por cinco anos.  

Justificativa: É evidência física/digital de bastidor relevante para contestação de pagamento.

⸻

4.6 Parcela devolvida ao FAT e reemissão

Trecho auditado: ausente.

Falha: Parcela fica disponível por 67 dias e depois deve ser devolvida ao FAT; pode ser reemitida até dois anos.  

Justificativa: Esse é um fail point operacional concreto: trabalhador liga “sem parcela”, mas a causa pode ser devolução/reemissão, não apenas bloqueio.

⸻

4.7 Norma atual central: Resolução CODEFAT nº 957/2022

Trecho auditado: o relatório menciona 467/2005, 783/2016 e “posteriores”, mas não estrutura a análise pela 957/2022.

Falha: A Resolução nº 957/2022 dispõe sobre concessão, processamento e pagamento do Programa do Seguro-Desemprego e revogou uma longa lista de resoluções, inclusive a 467/2005.  

Justificativa: É o principal normativo operacional e deveria sustentar o blueprint.

⸻

4.8 Lei Complementar nº 150/2015 e Lei nº 10.779/2003

Trecho auditado: “Resoluções específicas para pescador artesanal… trabalhador doméstico…”

Falha: A Resolução nº 957/2022 se ancora expressamente na Lei nº 7.998/1990, na LC nº 150/2015 e na Lei nº 10.779/2003; a pesquisa não lista LC 150 e Lei 10.779 na base legal primária.  

Justificativa: Como o relatório menciona doméstico e pescador, essas leis são normativos essenciais.

⸻

4.9 Canal 158 do MTE

Trecho auditado: fontes e jornada não incluem 158 como canal operacional principal de dúvida/reclamação do MTE.

Falha: O portal do serviço e o MTE apontam 158 como teleatendimento para Seguro-Desemprego.  

Justificativa: O relatório auditado dá centralidade excessiva ao 0800 da Caixa e omite o telefone do órgão gestor.

⸻

4.10 Atendimento para pessoas com deficiência auditiva/fala da Caixa foi omitido

Trecho auditado: “A Caixa não disponibiliza atendimento por videochamada em Libras integrado à URA de Seguro-Desemprego de forma ampla…”

Falha: A Caixa divulga telefone para deficientes auditivos e de fala, como 0800 726 2492 em contexto de atendimento a trabalhadores/FGTS, e páginas da Caixa indicam recursos de acessibilidade como atendimento em Libras em sua navegação.  

Justificativa: Pode haver lacuna de integração com a URA do Seguro-Desemprego, mas o relatório erra ao tratar o canal telefônico como simplesmente “estruturalmente inacessível” sem mapear os canais acessíveis existentes.

⸻

5) Fail points não identificados ou formulados incorretamente

5.1 Dados errados enviados pelo empregador no Empregador Web

Trecho auditado: F4 foca “data de nascimento errada no CadÚnico, NIS/PIS divergente entre empregador e CNIS…”

Falha: O relatório não identifica como fail point próprio o erro de transmissão pelo empregador: nome, nome da mãe, PIS, CPF, data de nascimento, endereço, salários, admissão, demissão, CBO, meses trabalhados etc. Esses dados são normativamente transmitidos pelo Empregador Web.  

Justificativa: Esse é um dos maiores pontos de falha reais porque antecede a URA e afeta habilitação automática.

⸻

5.2 Conta informada incorretamente ou impossibilidade de crédito

Trecho auditado: ausente ou diluído.

Falha: A norma prevê que, se o trabalhador não informa conta, informa incorretamente ou há impossibilidade de depósito, o benefício pode ser disponibilizado em conta digital/outra conta localizada pelo agente pagador.  

Justificativa: Fail point: trabalhador não reconhece a conta onde o benefício caiu, não acessa CAIXA Tem, não consegue movimentar conta digital, ou desconhece alternativa de saque.

⸻

5.3 Parcela expirada/devolvida ao FAT

Trecho auditado: ausente.

Falha: Parcela disponível por 67 dias e devolvida ao FAT se não sacada; reemissão em até dois anos.  

Justificativa: É falha concreta de jornada: “parcela sumiu”, “não consigo sacar”, “prazo passou”.

⸻

5.4 Contestação de recebimento de parcela

Trecho auditado: ausente.

Falha: A norma prevê contestação administrativa quando o trabalhador não confirma recebimento de parcelas.  

Justificativa: É fail point relevante para fraude, erro bancário, saque indevido ou desinformação.

⸻

5.5 Notificação digital não vista

Trecho auditado: fala em carta não recebida, mas não em notificação digital.

Falha: Se notificações podem ser digitais, um fail point crítico é o trabalhador não acessar gov.br/CTPS Digital, não ter celular, perder senha, não compreender notificação ou não ter anuência bem informada.  

Justificativa: Para público com baixo letramento digital, este fail point é mais plausível e atual do que “carta dos Correios”.

⸻

5.6 Indisponibilidade ou bloqueio de conta gov.br

Trecho auditado: ausente.

Falha: O requerimento normativo depende de cadastro no gov.br/CTPS Digital; logo falhas de login, recuperação de senha, nível de conta, telefone/e-mail desatualizados e validação cadastral são pontos de ruptura.

Justificativa: O relatório foca na URA da Caixa, mas o serviço público exige etapa digital MTE/gov.br.

⸻

5.7 Confusão entre 0800 Caixa e 158 MTE

Trecho auditado: “Caixa opera o canal, mas não decide concessão… redireciona para MTE.”

Falha: O relatório identifica parcialmente o gap, mas não modela como fail point autônomo: o cidadão liga para o canal de pagamento/consulta quando precisa do canal de concessão/recurso.

Justificativa: Esse é um fail point de arquitetura de canais: front door errado, autoridade errada, perda de tempo e recontato.

⸻

5.8 Prazo de 7 a 120 dias e perda de prazo

Trecho auditado: prazo aparece só em normativo.

Falha: O trabalhador formal pode requerer do 7º ao 120º dia contado da data subsequente à dispensa.  

Justificativa: Como o serviço atende demitidos, perda de prazo por desinformação, erro de canal ou orientação errada da URA é fail point crítico e deveria estar destacado.

⸻

5.9 Prazos diferentes por modalidade

Trecho auditado: relatório trata trabalhador formal como cidadão central, mas menciona doméstico, pescador e resgatado.

Falha: Para empregado doméstico, o serviço gov.br informa prazo de 7 a 90 dias e máximo de três parcelas de um salário mínimo.  

Justificativa: Misturar modalidades sem separar regras cria risco de orientação errada.

⸻

5.10 Prolongamento excepcional de parcelas

Trecho auditado: ausente.

Falha: A Resolução nº 957/2022 prevê prolongamento excepcional por até dois meses em situações específicas, inclusive calamidade, e notícia de 2026 mostra liberação de parcelas extras em municípios atingidos.  

Justificativa: O fail point é o cidadão não saber se tem direito a parcela extra, e a Caixa não decidir a concessão.

⸻

6) Afirmações juridicamente ou operacionalmente excessivas

6.1 “Descumprimento potencial da LBI” foi afirmado sem análise suficiente

Trecho auditado: “A Caixa não disponibiliza atendimento por videochamada em Libras integrado à URA… — descumprimento potencial da Lei Brasileira de Inclusão.”

Falha: A pesquisa não analisa quais formatos acessíveis são exigidos, quais canais acessíveis a Caixa oferece, nem se o canal específico deve ter videochamada em Libras integrada à URA.

Justificativa: Pode haver problema de acessibilidade, mas a conclusão jurídica está subfundamentada.

⸻

6.2 “Failure demand documentada” não foi documentada

Trecho auditado: “failure demand documentada no mapa de atores.”

Falha: O mapa de atores não é documentação empírica. Não há métrica de recontato, reincidência por CPF, chamadas repetidas, abandono, primeira resolução ou demanda evitável.

Justificativa: “Failure demand” deveria ser hipótese, não diagnóstico documentado.

⸻

6.3 “A URA passa a refletir novo status na próxima consulta” é arquitetura presumida

Trecho auditado: “Resolução é gravada no sistema → URA passa a refletir novo status na próxima consulta.”

Falha: Não há evidência sobre latência de atualização, sincronização entre MTE/Dataprev/Caixa, batch, cache ou janelas de processamento.

Justificativa: A pesquisa deveria tratar atualização intersistêmica como ponto aberto.

⸻

6.4 “Mainframe Caixa” e “base de bloqueios” são nomes genéricos sem comprovação

Trecho auditado: “Mainframe Caixa (sistemas legados)” e “Base de bloqueios”.

Falha: Não há fonte citada que identifique esses sistemas ou sua participação na URA.

Justificativa: Em blueprint técnico, “sistema legado” e “base de bloqueios” são placeholders, não evidência.

⸻

7) Omissões de controle, governança e mensuração

7.1 Não há distinção entre métricas necessárias e métricas disponíveis

Trecho auditado: tempos, abandono, frequência e SLA aparecem como estimativas.

Falha: O relatório deveria listar explicitamente métricas indisponíveis: chamadas ofertadas, atendidas, abandonadas, TME, TMA, FCR, transferências, quedas, bloqueios por autenticação, chamadas por CPF, recontato em 7/30 dias, erros de backend e taxa de resolução.

Justificativa: Sem essas métricas, “alta frequência” e “failure demand” são conjecturas.

⸻

7.2 Não há plano de validação da URA

Trecho auditado: todo Eixo 1.

Falha: A pesquisa deveria indicar evidência direta necessária: ligações-teste em horários distintos, transcrição do áudio, captura das opções, teste de entrada inválida, timeout, tentativa de transbordo, protocolo, acessibilidade e comparação entre 0800 e 158.

Justificativa: Sem validação, o AS-IS é parcialmente fictício.

⸻

7.3 Não há separação entre front stage da Caixa e front stage do MTE

Trecho auditado: “Serviço: Atendimento ao Seguro-Desemprego pela URA da Caixa.”

Falha: O relatório frequentemente trata o serviço completo do Seguro-Desemprego como se estivesse encapsulado na URA da Caixa.

Justificativa: O desenho correto precisa ter pelo menos duas frentes: Caixa como agente pagador/consulta e MTE como gestor/concessor/recurso.

⸻

Veredito técnico

As falhas mais graves são:

1. Fluxo de URA inventado ou não comprovado: submenu, autenticação, denúncia, agendamento e senha do cartão.
2. Normativos desatualizados/errados: Decreto 2.284/1997, Decreto SAC de 2008 revogado, Resolução 467/2005 tratada como vigente, referência suspeita à 783/2016.
3. Backstage incompleto: ausência do Empregador Web, gov.br/CTPS Digital, recurso administrativo, 158/MTE, forma de pagamento, reemissão e contestação.
4. Métricas sem base: espera, TMA, abandono e frequência dos fail points.
5. Confusão de papéis institucionais: Caixa como agente pagador/canal de consulta versus MTE como concessor/gestor do benefício.