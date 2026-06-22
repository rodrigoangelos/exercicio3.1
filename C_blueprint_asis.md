# Service Blueprint AS-IS
## Serviço: Atendimento ao Seguro-Desemprego pela URA da Caixa Econômica Federal

> **Escopo:** Jornada do cidadão no canal 0800-726-0207 — do momento de decidir ligar até o encerramento da chamada.
> **Cidadão central:** Trabalhador CLT demitido sem justa causa, com baixo letramento digital, para quem o canal telefônico é a via principal.
> **Base normativa:** Resolução CODEFAT nº 957/2022.
> **Fonte do fluxo da URA:** ligação-teste documentada ao 0800-726-0207 (ver `B_relatorio_assistente_v3.md` §0). As etapas E2–E7 são AS-IS observado, não hipótese.
> **Classificação de evidências:** [N] Normativo · [O] Oficial de canal · [T] Observado em ligação-teste · [A] Relato anedótico · [I] Inferência (restrita a arquitetura interna não observável)
> **Fail points:** ⚡ Crítico [N/O/T] · 〰 Secundário/contextual [A/I]

---

## Blueprint — Tabela de Camadas × Etapas

As **5 camadas de Shostack** estão nomeadas e separadas por linhas próprias, na ordem canônica (de cima para baixo): **(1) Evidências Físicas → (2) Ações do Cidadão → [Linha de Interação] → (3) Frontstage → [Linha de Visibilidade] → (4) Backstage → [Linha de Interação Interna] → (5) Processos de Suporte**.

| Camada de Shostack \ Etapa | **E0. Pré-ligação** | **E1. Decide ligar** | **E2. Navega menu** | **E3. Autentica** | **E4. Navega submenu** | **E5. Aguarda fila** | **E6. Atendimento humano** | **E7. Encerramento** |
|---|---|---|---|---|---|---|---|---|
| **CAMADA 1 — Evidências Físicas** *(Physical Evidence)* | Formulário Empregador Web; cópia do formulário recebida do empregador; TRCT; login gov.br; comprovante de requerimento SD [N] | Número 0800-726-0207 anotado ou buscado; CPF e data de nascimento em mãos | Tom de chamada; locução "Atendimento CAIXA Cidadão" + aviso de gravação [T] | Locução solicitando CPF e data de nascimento [T] | Locução do submenu (situação/parcelas, pagamento, falar com atendente) [T] | Música de espera [T] | Voz do atendente humano [T]; protocolo verbal [T] | Encerramento da locução ou da chamada [T] |
| **CAMADA 2 — Ações do Cidadão** *(Customer Actions)* | Requer benefício via gov.br/CTPS Digital [N]; recebe formulário do empregador; reúne CPF e documentos; busca número da Caixa | Decide ligar para 0800-726-0207; verifica CPF, data de nascimento e número antes de discar | Disca 0800-726-0207; ouve menu principal; tecla opção para Seguro-Desemprego [T] | Digita CPF e data de nascimento no teclado numérico [T] | Ouve opções do submenu; escolhe ação (consulta de parcelas ou falar com atendente) [T] | Aguarda na fila; permanece na linha ou abandona [T] | Explica o caso ao atendente; recebe orientação; anota protocolo verbal [T] | Encerra a chamada; anota protocolo ou registra ausência de resolução [T] |
| ═══ ***LINHA DE INTERAÇÃO*** ═══ | | | | | | | | |
| **CAMADA 3 — Frontstage** *(Onstage / Ações Visíveis de Contato)* | — | Canal 0800-726-0207 disponível 24h [O] | URA: saudação "CAIXA Cidadão" + aviso de gravação + menu DTMF de benefícios [T] | URA: solicita CPF e data de nascimento; repede se divergente [T] | URA: submenu (situação/parcelas, pagamento, falar com atendente); roteia para fila ou informa [T] | URA: música de espera no horário humano; fora do horário informa indisponibilidade [T] | Atendente humano Caixa seg–sex 8h–21h e sáb 10h–16h [O/T]; resolve consulta/pagamento, orienta gov.br/158 para concessão [N/T] | URA ou atendente encerra a chamada [T] |
| ═══ ***LINHA DE VISIBILIDADE (dupla — P4)*** ═══ | *Linha 1: o que o cidadão vê/ouve (Frontstage acima) × o que a URA faz por dentro (abaixo).* | | | | | | | *Linha 2: o que a URA/atendente opera × os sistemas de infraestrutura (Linha de Interação Interna, mais abaixo).* |
| **CAMADA 4 — Backstage** *(Backstage / Ações Invisíveis de Contato)* | Empregador transmite dados via Empregador Web com certificado ICP-Brasil [N] | — | URA roteia chamada para fluxo de SD [I] | URA consulta base de identificação para validar dado informado [I]; resultado: autenticado ou falha | URA consulta status de parcelas e situação do requerimento [I] | Sistema de filas distribui chamada para atendente disponível [I] | Atendente consulta sistemas de pagamento Caixa [I]; registra ocorrência no sistema de atendimento [I]; redireciona demanda de concessão para MTE/gov.br [N] | Sistema encerra sessão; protocolo gerado (se existente) [A] |
| ═══ ***LINHA DE INTERAÇÃO INTERNA*** ═══ | | | | | | | | |
| **CAMADA 5 — Processos de Suporte** *(Support Processes)* | **[N] Base de elegibilidade:** CNIS, eSocial, FGTS/GFIP · **[N] Canal de requerimento:** Gov.br / CTPS Digital / SINE-Fácil | **[O] Telefonia:** infraestrutura 0800 gratuita | **[I] Plataforma URA:** sistema de atendimento automatizado Caixa | **[N/I] Base de identificação:** PIS/NIS, CNIS (critério normativo; integração com URA: inferência) | **[N] Sistema SD (MTE):** status do requerimento, parcelas deferidas, bloqueios · **[I] Sistemas Caixa (pagamento):** saldo de parcelas, histórico de créditos | **[I] Dimensionamento de filas:** sistema de contact center Caixa | **[N] Base normativa de competências:** Resolução 957/2022 (Caixa = agente pagador; MTE = concessor) · **[I] CRM/sistema de atendimento Caixa** | **[I] Registro de sessão:** log da chamada arquivado pelo agente pagador |
| **⚡ / 〰 Fail Points** | ⚡ **F0** — Dados errados do empregador no Empregador Web bloqueiam habilitação automática antes da ligação [N] · ⚡ **F21** — Bloqueio de conta gov.br impede requerimento normativo [N] · ⚡ **F22** — Prazo de 7–120 dias correndo; cidadão pode perder o prazo antes de descobrir o canal certo [N] | ⚡ **F18** — Cidadão decide ligar para o canal de pagamento (Caixa) com demanda de concessão que exige 158/MTE — canal errado para a demanda certa [N] | ⚡ **F1** — Opção inválida/silêncio reapresenta o menu (loop), observado em ligação-teste [T] · 〰 **F2** — Menu confuso para baixo letramento digital / idosos: terminologia técnica, velocidade de locução, timeout [A/I] · 〰 **F3** — Encerramento abrupto da chamada durante navegação [A] | ⚡ **F4b** — Falha de autenticação por CPF/data de nascimento divergente; encaminha a atendente após repetições [T] · ⚡ **F4a** — Inconsistência cadastral (origem: Empregador Web / CNIS) bloqueia habilitação automática [N] | 〰 **F6** — Indisponibilidade do sistema em períodos de alta demanda [A] · 〰 **F7** — Indisponibilidade de backend (SD/gov.br/Caixa) com erro genérico sem saída [I] · 〰 **F8** — Status divergente entre URA, App e portal [A] · ⚡ **F5** — Trabalhador não consegue acessar/movimentar conta digital CAIXA Tem [N/A] · ⚡ **F16** — Queda de chamada por sinal precário — retrabalho total [I] | 〰 **F11** — Fila longa para atendente humano (relatos de espera prolongada; sem TME oficial) [A] · 〰 **F15** — Dificuldade de idosos e baixo letramento no aguardo (timeout, desconexão) [A/I] | ⚡ **F9** — Atendente Caixa não decide concessão; redireciona para MTE sem prazo [N/O] · ⚡ **F13** — Protocolo apenas verbal, sem confirmação de registro escrito automático (observado em ligação-teste) [T] · 〰 **F14** — Canal PcD auditiva/fala (0800-726-2492): escopo para SD não verificado [O/I] · ⚡ **F10** — Notificação digital de resultado não acessada pelo trabalhador; presumida válida após 5 dias [N] | ⚡ **F19** — Parcela disponível por apenas 67 dias; devolvida ao FAT sem aviso; reemissão em até 2 anos (canal em aberto) [N] · ⚡ **F17** — Trabalhador desconhece recurso de 120 dias para indeferimento/suspensão/cancelamento via gov.br [N] · ⚡ **F20** — Contestação de recebimento de parcela desconhecida pelo trabalhador [N] · ⚡ **F23** — Suspensão por recusa de ação de recolocação — trabalhador desconhece a causa [N] · ⚡ **F24** — Trabalhador não sabe se está abrangido por prolongamento excepcional de parcelas [N] |

---

## Rastreabilidade: Decisões Grill-me → Blueprint

| P do Grill-me | Recomendação | Implementação no Blueprint |
|---|---|---|
| **P1 — Escopo** | Jornada URA Caixa (0800) apenas | ✓ Etapas E0-E7 documentadas; MTE como contexto pré/pós |
| **P2 — Início/Fim** | Cidadão decide ligar / Chamada encerrada | ✓ E1: "Cidadão decide ligar"; E7: "Encerramento chamada" |
| **P3 — Granularidade** | Alta + classificação probatória por célula | ✓ E2-E7 detalhadas; fluxo da URA marcado [T] (verificado em ligação-teste); arquitetura interna marcada [I] |
| **P4 — Visibilidade** | Linha dupla (Cidadão/URA e URA/Sistemas) | ✓ Linhas de Interação, Visibilidade e Interação Interna presentes |
| **P5 — Suporte** | Agrupamento funcional com marcação [N/O/I] | ✓ Clusters: elegibilidade [N], identificação [N/I], pagamento [I], requerimento [N], competências [N] |
| **P6 — Fail Points** | Crítico [⚡N/O/T] vs Secundário/contextual [〰A/I] | ✓ Críticos ⚡: F0, F1, F4a, F4b, F9, F10, F13, F17-F24 (norma ou ligação-teste); contextuais 〰: F2-F3, F6-F8, F11, F14, F15 |
| **P7 — Evidências** | [N]/[O] apenas como principal | ✓ Evidências com marcação [I]/[A] incluídas com ressalvas; foco [N]/[O] |
| **P8 — Formato** | Tabela + Diagrama Mermaid | ✓ Tabela Markdown (E0-E7) + Diagrama flowchart + Diagrama sequenceDiagram |

**Atores e Elementos Centrais (mencionados no grill e presentes no blueprint):**
- ✓ Cidadão (baixo letramento digital) — presente E0-E7
- ✓ URA 0800-726-0207 (frontstage canal) — E2-E6
- ✓ Atendente humano Caixa (frontstage) — E6
- ✓ Sistemas: CNIS, Sistema SD (MTE), Sistemas Caixa (pagamento), Empregador Web, Gov.br
- ✓ MTE / Gov.br / 158 / CTPS Digital (canais corretos alternativos) — redirecionamentos E0, E1, E6-E7
- ✓ Fail points críticos [N/O/T]: F0, F1, F4a, F4b, F5, F9, F10, F13, F16, F17-F24 (verificados por norma ou ligação-teste)
- ✓ Fail points secundários/contextuais [A/I]: F2, F3, F6-F8, F11, F14, F15

---

## Diagrama de Sequência — Fluxo de Interações

```mermaid
sequenceDiagram
    actor C as 👷 Cidadão
    participant URA as 📞 URA Caixa<br/>0800-726-0207
    participant HUM as 🧑 Atendente<br/>Caixa (humano)
    participant SIS as ⚙️ Sistemas<br/>Caixa [I backstage]
    participant MTE as 🏛️ MTE / Gov.br<br/>Sistema SD [N]
    participant EMP as 🏢 Empregador<br/>Empregador Web [N]

    Note over EMP,MTE: E0 — PRÉ-JORNADA (antes da ligação) [N]
    EMP->>MTE: Transmite dados da rescisão via Empregador Web (ICP-Brasil)
    Note over EMP: ⚡ F0 — Dado errado bloqueia habilitação automática
    MTE-->>C: Notificação digital via gov.br/CTPS Digital (válida após 5 dias)
    Note over C,MTE: ⚡ F21 — Bloqueio de conta gov.br impede requerimento
    C->>MTE: Requer benefício via gov.br ou CTPS Digital
    Note over C: ⚡ F22 — Prazo de 7–120 dias correndo

    Note over C,URA: E1 — DECIDE LIGAR
    C->>C: Reúne CPF e documentos; busca número 0800
    Note over C: ⚡ F18 — Canal errado: demanda de concessão trazida ao canal de pagamento

    Note over C,URA: E2 — NAVEGA MENU [T] verificado em ligação-teste
    C->>URA: Disca 0800-726-0207
    URA-->>C: Saudação automática + menu DTMF
    C->>URA: Tecla opção Seguro-Desemprego
    Note over URA: 〰 F1 — Loop sem saída para atendente
    Note over URA: 〰 F2 — Menu confuso para baixo letramento / idosos
    Note over URA: 〰 F3 — Encerramento abrupto

    Note over C,URA: E3 — AUTENTICA [T] verificado em ligação-teste
    URA-->>C: Solicita CPF e data de nascimento
    C->>URA: Digita CPF e data de nascimento
    URA->>MTE: Consulta base de identificação
    Note over URA,MTE: 〰 F4b — Falha de autenticação (mecanismo em aberto)
    Note over URA,MTE: ⚡ F4a — Inconsistência cadastral (origem: Empregador Web/CNIS)

    Note over C,URA: E4 — NAVEGA SUBMENU [T] verificado em ligação-teste
    URA-->>C: Apresenta opções (consulta parcelas, transferência etc.)
    C->>URA: Escolhe opção
    URA->>MTE: Consulta status do requerimento e parcelas
    URA->>SIS: Consulta saldo e histórico de pagamentos
    Note over URA,SIS: 〰 F6 — Sistema indisponível em pico de demanda
    Note over URA,SIS: 〰 F7 — Indisponibilidade de backend; erro genérico
    Note over URA,SIS: 〰 F8 — Status divergente entre canais

    alt Informação disponível e autenticação ok
        URA-->>C: Informa status / data de crédito
    else Demanda não resolvida pela URA
        Note over C,URA: E5 — AGUARDA FILA [T] verificado em ligação-teste
        URA-->>C: Música de espera / posição na fila
        Note over C: 〰 F11 — Fila longa; sem TME oficial
        Note over C: 〰 F3 — Encerramento abrupto durante espera
        Note over C: 〰 F15 — Dificuldade de idosos no aguardo

        Note over C,HUM: E6 — ATENDIMENTO HUMANO [T] verificado em ligação-teste
        URA->>HUM: Transfere chamada
        HUM-->>C: Atende; solicita relato do caso
        C->>HUM: Explica demanda
        HUM->>SIS: Consulta sistemas de pagamento Caixa
        Note over HUM: ⚡ F9 — Atendente não decide concessão;<br/>redireciona para MTE sem prazo
        Note over HUM: 〰 F13 — Ausência de protocolo escrito automático
        HUM-->>C: Orienta / fornece protocolo verbal
    end

    Note over C,URA: E7 — ENCERRAMENTO
    URA-->>C: Encerra chamada
    Note over C: ⚡ F10 — Notificação digital não acessada;<br/>presumida válida após 5 dias [N]
    Note over C: ⚡ F19 — Parcela devolvida ao FAT após 67 dias;<br/>reemissão em até 2 anos (canal em aberto)
    Note over C: ⚡ F17 — Recurso de 120 dias desconhecido;<br/>exige conta gov.br Prata/Ouro
```

---

## Legenda e Notas de Leitura

### As 5 Camadas de Shostack no Blueprint

1. **Evidências Físicas** (topo) — Artefatos tangíveis/digitais que o cidadão encontra ou usa: documentos, números de telefone, locuções de URA, logins, protocolos etc.

2. **Ações do Cidadão** (segunda linha) — O que o cidadão faz em cada etapa: requer benefício, disca, tecla opção, aguarda, explica caso, encerra etc.

3. **Frontstage** (terceira linha, separado por Linha de Interação) — O que o cidadão VÊ/OUE como resposta direta: canal 0800 disponível, saudação da URA, menu DTMF, atendente humano, encerramento. A URA e o Atendente são ambos frontstage (interagem com cidadão), mas a URA tem funcionamento parcialmente oculto (sistema, não pessoa).

4. **Backstage** (quarta linha, separado por Linha de Visibilidade) — O que o cidadão NÃO vê: operação interna da URA, consultas a sistemas, registros de atendimento, verificação de dados etc.

5. **Processos de Suporte** (quinta linha, separado por Linha de Interação Interna) — Sistemas de infraestrutura que alimentam o serviço: CNIS, Sistema SD, Sistemas Caixa, Gov.br, Empregador Web, Dataprev etc.

### Linhas divisórias (Shostack) — visibilidade dupla (decisão P4 do grill-me)

O grill-me (P4) recomendou **dupla linha de visibilidade**, porque a URA é um híbrido: é *frontstage* para o cidadão (ele a ouve) mas tem seu próprio *backstage* (consultas a sistemas que ele não vê). O blueprint representa isso com duas fronteiras de invisibilidade distintas:

| Linha | Posição na tabela | O que separa |
|---|---|---|
| **Linha de Interação** | Entre Camada 2 (Ações do Cidadão) e Camada 3 (Frontstage) | O que o cidadão faz × o que o serviço faz em resposta direta |
| **Linha de Visibilidade — 1ª fronteira** | Entre Camada 3 (Frontstage) e Camada 4 (Backstage) | O que o cidadão ouve/percebe na URA × o que a URA faz por dentro (rotear, consultar identificação) |
| **Linha de Visibilidade — 2ª fronteira** (= Linha de Interação Interna) | Entre Camada 4 (Backstage) e Camada 5 (Processos de Suporte) | A operação da URA/atendente × os sistemas de infraestrutura que a alimentam (CNIS, Sistema SD, Sistemas Caixa) |

> **Leitura:** a 1ª fronteira é a linha de visibilidade clássica (cidadão × bastidor). A 2ª é a invisibilidade interna (operação de contato × infraestrutura). Juntas, materializam a "dupla visibilidade" pedida em P4 para o caso híbrido da URA.

### Fail points — síntese por criticidade

| Símbolo | Tipo | Fail points | Critério |
|---|---|---|---|
| ⚡ | **Crítico** | F0, F4a, F4b, F9, F10, F13, F17, F18, F19, F21, F22 | Evidência [N], [O] ou [T] (observado em ligação-teste); impacto alto |
| 〰 | **Secundário / contextual** | F1, F2, F3, F6, F7, F8, F11, F15 | F1 observado [T]; F2/F3/F11/F15 contextuais [A/I]; F6/F7/F8 dependem de carga/backend |

### Etapas E2–E7 — AS-IS verificado por ligação-teste [T]

E2 a E7 (tudo a partir da discagem) foram **observadas em ligação-teste documentada ao 0800-726-0207** (ver `B_relatorio_assistente_v3.md` §0): saudação, menu DTMF de benefícios, autenticação por CPF + data de nascimento, submenu de Seguro-Desemprego, transbordo por opção "falar com atendente", escopo do atendente (paga/consulta; orienta gov.br/158 para concessão) e protocolo verbal. As validações V1–V5 e V8 estão resolvidas. Permanecem como inferência [I] apenas itens estritamente internos não observáveis por ligação (arquitetura de backstage, latência entre sistemas, métricas de contact center — V6, V7, V9–V12).

### Camadas dos processos de suporte — agrupamento funcional

| Cluster | Sistemas | Evidência |
|---|---|---|
| Base de elegibilidade | CNIS, eSocial, FGTS/GFIP | [N] Res. 957/2022 |
| Canal de requerimento/recurso | Gov.br, CTPS Digital, SINE-Fácil | [N] Res. 957/2022 / [O] FAQ gov.br |
| Processamento dos requerimentos | Dataprev (arquitetura em aberto) | [I] docs TCU |
| Base de pagamento | Sistemas Caixa (arquitetura em aberto) | [I] |
| Dados de identificação | PIS/NIS, CNIS | [N] critério; [I] integração com URA |
