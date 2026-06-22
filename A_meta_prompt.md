# A — Meta-prompt: Pesquisa estruturada para Service Blueprint AS-IS
## Serviço: Atendimento ao Seguro-Desemprego pela URA (Unidade de Resposta Audível) da Caixa Econômica Federal

---

## Meta-prompt

Você é um analista de serviços públicos especializado em mapeamento de jornadas (service design) e tem experiência com os canais de atendimento da Caixa Econômica Federal e do Ministério do Trabalho e Emprego (MTE), operador do Programa Seguro-Desemprego.

**Contexto do serviço a ser pesquisado:**
- **Serviço:** Atendimento ao Seguro-Desemprego (consulta de status do requerimento, informações sobre parcelas, agendamento, habilitação, denúncias de irregularidade e dúvidas gerais sobre o benefício).
- **Canal:** URA (Unidade de Resposta Audível) — o sistema de atendimento telefônico automatizado da Caixa, acessado pelo número 0800-726-0207 (ou 111, dependendo da linha), que combina menus de voz (DTMF/reconhecimento de voz) com transferência para atendentes humanos quando necessário.
- **Órgão responsável:** Caixa Econômica Federal, na condição de agente operador do FAT (Fundo de Amparo ao Trabalhador), sob normativos do Ministério do Trabalho e Emprego (MTE) e da Secretaria de Políticas Públicas de Emprego (SPPE/MTE).
- **Público:** trabalhadores demitidos sem justa causa (e demais categorias elegíveis: pescador artesanal, empregado doméstico, resgatado de trabalho escravo) que buscam informações ou resolução de pendências sobre o benefício.

**Tarefa solicitada:**

Realize uma pesquisa estruturada — usando fontes oficiais (Caixa, MTE/SPPE, gov.br, Portal Emprega Brasil, legislação do Seguro-Desemprego: Lei nº 7.998/1990, Resoluções CODEFAT) e fontes secundárias confiáveis (reportagens, ouvidorias, Procon, fóruns de reclamação como Reclame Aqui, relatórios de ouvidoria da CGU) — que sustente a construção de um **Service Blueprint AS-IS** para este serviço. A pesquisa deve cobrir, no mínimo, os cinco eixos abaixo:

1. **Jornada do cidadão (linha de frente / front stage):** mapeie passo a passo a experiência de quem liga para a URA — desde a discagem, passando pelos menus de opções (autenticação por CPF/NIS e senha ou data de nascimento), as opções disponíveis (status do benefício, datas de pagamento, agendamento de habilitação, transferência para atendente humano, encerramento da chamada), até a resolução (ou não) da demanda. Inclua tempos médios de espera, taxas de abandono de chamada e pontos de transferência para canais alternativos (app, agências, Atendimento Caixa 0800).

2. **Processos de bastidor (backstage):** descreva o que ocorre fora da visão do cidadão — quais sistemas são consultados pela URA (ex.: bases do CAGED/eSocial, sistema do Seguro-Desemprego, cadastro do PIS/NIS), quais equipes da Caixa e do MTE atuam na manutenção da URA, validação de dados, liberação de parcelas, tratamento de exceções e escalonamento para análise manual (ex.: bloqueios por divergência cadastral, indícios de fraude, óbito do empregador, rescisão contestada).

3. **Evidências físicas (physical evidence) de cada etapa:** identifique os artefatos tangíveis e digitais que aparecem em cada etapa — comprovante de ligação/protocolo de atendimento, SMS/e-mail de confirmação, extrato de pagamento, carta de exigência/pendência, telas do aplicativo Caixa Trabalhador e do Portal Emprega Brasil, documentos exigidos para habilitação (TRCT, carteira de trabalho digital, requerimento do seguro-desemprego).

4. **Normativos aplicáveis:** levante a base legal e regulatória que rege o serviço — Lei nº 7.998/1990 (institui o Programa Seguro-Desemprego), Resoluções do CODEFAT vigentes sobre prazos, habilitação e pagamento, normas de atendimento da Caixa enquanto agente operador, Lei Geral de Proteção de Dados (LGPD) quanto à autenticação de dados pessoais na URA, e normas de acessibilidade em atendimento telefônico (Lei Brasileira de Inclusão).

5. **Fail points conhecidos:** identifique falhas recorrentes relatadas — loops de menu sem saída para atendente humano, indisponibilidade do sistema em horários de pico, falha de autenticação por dados cadastrais desatualizados, informações desencontradas entre URA, app e agência, tempo de espera excessivo, encerramento abrupto da chamada, ausência de retorno sobre pendências documentais e dificuldade de pessoas com deficiência visual/auditiva ou idosos em navegar pelos menus.

**Anexo de referência:** considere como insumo o mapa de atores produzido no exercício 2.1 (mapa de atores do mesmo serviço), que já identifica os principais stakeholders envolvidos (cidadão/segurado, atendente humano de retaguarda, sistemas da Caixa, MTE/SPPE, empregador/ex-empregador, órgãos de controle). Use esse mapa para garantir que todos os atores relevantes estejam representados nos cinco eixos acima.

**Formato de saída esperado:** um relatório estruturado em tópicos, organizado pelos cinco eixos descritos, com citação das fontes consultadas (URLs e/ou nomes de documentos normativos), de forma que possa alimentar diretamente a construção de um Service Blueprint AS-IS (camadas: ações do cidadão, linha de visibilidade, ações de bastidor, sistemas de suporte, evidências físicas) na etapa seguinte deste exercício.
