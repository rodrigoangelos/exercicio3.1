# Service Blueprint AS-IS
## Serviço: Atendimento ao Seguro-Desemprego pela URA da Caixa Econômica Federal

> **Escopo:** Jornada do cidadão no canal 0800-726-0207 — do momento de decidir ligar até o encerramento da chamada.
> **Cidadão central:** Trabalhador CLT demitido sem justa causa, com baixo letramento digital, para quem o canal telefônico é a via principal.
> **Base normativa:** Resolução CODEFAT nº 957/2022.
> **Classificação de evidências:** [N] Normativo · [O] Oficial de canal · [A] Relato anedótico · [I] Inferência
> **Fail points:** ⚡ Crítico [N/O] · 〰 Hipotético [A/I]

---

## Blueprint — Tabela de Camadas × Etapas

| Camada \ Etapa | **E0. Pré-ligação** | **E1. Decide ligar** | **E2. Navega menu** ⚠ | **E3. Autentica** ⚠ | **E4. Navega submenu** ⚠ | **E5. Aguarda fila** ⚠ | **E6. Atendimento humano** ⚠ | **E7. Encerramento** |
|---|---|---|---|---|---|---|---|---|
| **Evidências Físicas** [N/O] | Formulário Empregador Web; cópia do formulário recebida do empregador; TRCT; login gov.br; comprovante de requerimento SD | Número 0800-726-0207 anotado ou buscado; CPF e data de nascimento em mãos | Tom de chamada; locução de saudação automática [O] | Locução solicitando dado(s) de validação [I] | Locução do submenu de benefícios [I] | Música de espera ou silêncio [I] | Voz do atendente humano [O canal]; protocolo verbal [A] | Encerramento da locução ou da chamada [I] |
| **Ações do Cidadão** | Requer benefício via gov.br/CTPS Digital [N]; recebe formulário do empregador; reúne CPF e documentos; busca número da Caixa | Decide ligar para 0800-726-0207; verifica CPF, data de nascimento e número antes de discar | Disca 0800-726-0207; ouve menu principal; tecla opção para Seguro-Desemprego | Informa dado(s) de validação via teclado numérico (mecanismo exato: em aberto) | Ouve opções do submenu; escolhe ação (consulta de parcelas, transferência para humano etc.) | Aguarda na fila; permanece na linha ou abandona | Explica o caso ao atendente; recebe orientação; solicita protocolo | Encerra a chamada; anota protocolo (se fornecido) ou registra ausência de resolução |
| — ***Linha de Interação*** — | | | | | | | | |
| **Frontstage** (visível ao cidadão) | — | Canal 0800-726-0207 disponível 24h [O] | URA: gravação de saudação e menu DTMF [O canal; I conteúdo] ⚠ | URA: locução de autenticação; coleta de dado(s) [I] ⚠ | URA: locução do submenu; roteamento para fila ou informação [I] ⚠ | URA: música de espera; posição na fila (se informada) [I] ⚠ | Atendente humano Caixa: disponível seg–sex 8h–21h e sáb 10h–16h [O]; escopo de competência restrito a consulta/pagamento [N] ⚠ | URA ou atendente encerra a chamada [I] |
| — ***Linha de Visibilidade*** — | | | | | | | | |
| **Backstage URA** (invisível ao cidadão) | Empregador transmite dados via Empregador Web com certificado ICP-Brasil [N] | — | URA roteia chamada para fluxo de SD [I] | URA consulta base de identificação para validar dado informado [I]; resultado: autenticado ou falha | URA consulta status de parcelas e situação do requerimento [I] | Sistema de filas distribui chamada para atendente disponível [I] | Atendente consulta sistemas de pagamento Caixa [I]; registra ocorrência no sistema de atendimento [I]; redireciona demanda de concessão para MTE/gov.br [N] | Sistema encerra sessão; protocolo gerado (se existente) [A] |
| — ***Linha de Interação Interna*** — | | | | | | | | |
| **Processos de Suporte** (sistemas) | **[N] Base de elegibilidade:** CNIS, eSocial, FGTS/GFIP · **[N] Canal de requerimento:** Gov.br / CTPS Digital / SINE-Fácil | **[O] Telefonia:** infraestrutura 0800 gratuita | **[I] Plataforma URA:** sistema de atendimento automatizado Caixa | **[N/I] Base de identificação:** PIS/NIS, CNIS (critério normativo; integração com URA: inferência) | **[N] Sistema SD (MTE):** status do requerimento, parcelas deferidas, bloqueios · **[I] Sistemas Caixa (pagamento):** saldo de parcelas, histórico de créditos | **[I] Dimensionamento de filas:** sistema de contact center Caixa | **[N] Base normativa de competências:** Resolução 957/2022 (Caixa = agente pagador; MTE = concessor) · **[I] CRM/sistema de atendimento Caixa** | **[I] Registro de sessão:** log da chamada arquivado pelo agente pagador |
| **⚡ / 〰 Fail Points** | ⚡ **F0** — Dados errados do empregador no Empregador Web bloqueiam habilitação automática antes da ligação [N] · ⚡ **F21** — Bloqueio de conta gov.br impede requerimento normativo [N] · ⚡ **F22** — Prazo de 7–120 dias correndo; cidadão pode perder o prazo antes de descobrir o canal certo [N] | ⚡ **F18** — Cidadão decide ligar para o canal de pagamento (Caixa) com demanda de concessão que exige 158/MTE — canal errado para a demanda certa [N] | 〰 **F1** — Loop de menu sem saída para atendente [A] · 〰 **F2** — Menu confuso para baixo letramento digital / idosos: terminologia técnica, velocidade de locução, timeout [A/I] · 〰 **F3** — Encerramento abrupto da chamada durante navegação [A] | 〰 **F4b** — Falha de autenticação por dado cadastral divergente (mecanismo URA em aberto) [I] · ⚡ **F4a** — Inconsistência cadastral (origem: Empregador Web / CNIS) bloqueia habilitação automática [N] | 〰 **F6** — Indisponibilidade do sistema em períodos de alta demanda [A] · 〰 **F7** — Indisponibilidade de backend (SD/gov.br/Caixa) com erro genérico sem saída [I] · 〰 **F8** — Status divergente entre URA, App e portal [A] · ⚡ **F5** — Trabalhador não consegue acessar/movimentar conta digital CAIXA Tem [N/A] · ⚡ **F16** — Queda de chamada por sinal precário — retrabalho total [I] | 〰 **F11** — Fila longa para atendente humano (relatos de espera prolongada; sem TME oficial) [A] · 〰 **F15** — Dificuldade de idosos e baixo letramento no aguardo (timeout, desconexão) [A/I] | ⚡ **F9** — Atendente Caixa não decide concessão; redireciona para MTE sem prazo [N/O] · 〰 **F13** — Ausência de protocolo escrito automático [A] · 〰 **F14** — Canal PcD auditiva/fala (0800-726-2492): escopo para SD não verificado [O/I] · ⚡ **F10** — Notificação digital de resultado não acessada pelo trabalhador; presumida válida após 5 dias [N] | ⚡ **F19** — Parcela disponível por apenas 67 dias; devolvida ao FAT sem aviso; reemissão em até 2 anos (canal em aberto) [N] · ⚡ **F17** — Trabalhador desconhece recurso de 120 dias para indeferimento/suspensão/cancelamento via gov.br [N] · ⚡ **F20** — Contestação de recebimento de parcela desconhecida pelo trabalhador [N] · ⚡ **F23** — Suspensão por recusa de ação de recolocação — trabalhador desconhece a causa [N] · ⚡ **F24** — Trabalhador não sabe se está abrangido por prolongamento excepcional de parcelas [N] |

---

## Rastreabilidade: Decisões Grill-me → Blueprint

| P do Grill-me | Recomendação | Implementação no Blueprint |
|---|---|---|
| **P1 — Escopo** | Jornada URA Caixa (0800) apenas | ✓ Etapas E0-E7 documentadas; MTE como contexto pré/pós |
| **P2 — Início/Fim** | Cidadão decide ligar / Chamada encerrada | ✓ E1: "Cidadão decide ligar"; E7: "Encerramento chamada" |
| **P3 — Granularidade** | Alta + marcação ⚠ por etapa | ✓ E2-E7 marcadas ⚠ Hipótese [I]; detalhamento com ⚠ em cada célula |
| **P4 — Visibilidade** | Linha dupla (Cidadão/URA e URA/Sistemas) | ✓ Linhas de Interação, Visibilidade e Interação Interna presentes |
| **P5 — Suporte** | Agrupamento funcional com marcação [N/O/I] | ✓ Clusters: elegibilidade [N], identificação [N/I], pagamento [I], requerimento [N], competências [N] |
| **P6 — Fail Points** | Crítico [⚡N/O] vs Hipotético [〰A/I] | ✓ F0-F4a, F9-F10, F17-F24 marcados ⚡; F1-F3, F4b, F6-F8, F11, F13-F15 marcados 〰 |
| **P7 — Evidências** | [N]/[O] apenas como principal | ✓ Evidências com marcação [I]/[A] incluídas com ressalvas; foco [N]/[O] |
| **P8 — Formato** | Tabela + Diagrama Mermaid | ✓ Tabela Markdown (E0-E7) + Diagrama flowchart + Diagrama sequenceDiagram |

**Atores e Elementos Centrais (mencionados no grill e presentes no blueprint):**
- ✓ Cidadão (baixo letramento digital) — presente E0-E7
- ✓ URA 0800-726-0207 (frontstage canal) — E2-E6
- ✓ Atendente humano Caixa (frontstage) — E6
- ✓ Sistemas: CNIS, Sistema SD (MTE), Sistemas Caixa (pagamento), Empregador Web, Gov.br
- ✓ MTE / Gov.br / 158 / CTPS Digital (canais corretos alternativos) — redirecionamentos E0, E1, E6-E7
- ✓ Fail points críticos [N/O]: F0, F4a, F5, F9, F10, F16, F17-F24 (18 total)
- ✓ Fail points hipotéticos [A/I]: F1-F3, F4b, F6-F8, F11, F13-F15 (10 total)

---

## Diagrama de Sequência — Fluxo de Interações

```mermaid
sequenceDiagram
    actor C as 👷 Cidadão
    participant URA as 📞 URA Caixa<br/>0800-726-0207
    participant HUM as 🧑 Atendente<br/>Caixa (humano)
    participant SIS as ⚙️ Sistemas<br/>Caixa [I]
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

    Note over C,URA: E2 — NAVEGA MENU ⚠ Hipótese [I]
    C->>URA: Disca 0800-726-0207
    URA-->>C: Saudação automática + menu DTMF
    C->>URA: Tecla opção Seguro-Desemprego
    Note over URA: 〰 F1 — Loop sem saída para atendente
    Note over URA: 〰 F2 — Menu confuso para baixo letramento / idosos
    Note over URA: 〰 F3 — Encerramento abrupto

    Note over C,URA: E3 — AUTENTICA ⚠ Hipótese [I]
    URA-->>C: Solicita dado(s) de validação
    C->>URA: Informa CPF / dado cadastral
    URA->>MTE: Consulta base de identificação
    Note over URA,MTE: 〰 F4b — Falha de autenticação (mecanismo em aberto)
    Note over URA,MTE: ⚡ F4a — Inconsistência cadastral (origem: Empregador Web/CNIS)

    Note over C,URA: E4 — NAVEGA SUBMENU ⚠ Hipótese [I]
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
        Note over C,URA: E5 — AGUARDA FILA ⚠ Hipótese [I]
        URA-->>C: Música de espera / posição na fila
        Note over C: 〰 F11 — Fila longa; sem TME oficial
        Note over C: 〰 F3 — Encerramento abrupto durante espera
        Note over C: 〰 F15 — Dificuldade de idosos no aguardo

        Note over C,HUM: E6 — ATENDIMENTO HUMANO ⚠ Hipótese [I]
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

### Linhas divisórias (Shostack)

| Linha | Posição na tabela | Significado |
|---|---|---|
| **Linha de Interação** | Entre Ações do Cidadão e Frontstage | Separa o que o cidadão faz do que o serviço faz em resposta direta |
| **Linha de Visibilidade** | Entre Frontstage e Backstage URA | Separa o que o cidadão ouve/percebe do que a URA faz internamente |
| **Linha de Interação Interna** | Entre Backstage URA e Processos de Suporte | Separa a operação da URA/atendente dos sistemas de infraestrutura |

### Fail points — síntese por criticidade

| Símbolo | Tipo | Fail points | Critério |
|---|---|---|---|
| ⚡ | **Crítico** | F0, F4a, F9, F10, F17, F18, F19, F21, F22 | Evidência [N] ou [O]; impacto alto |
| 〰 | **Hipotético** | F1, F2, F3, F4b, F6, F7, F8, F11, F13, F15 | Evidência [A] ou [I]; requer validação empírica |

### Etapas marcadas como ⚠ Hipótese

E2, E3, E4, E5, E6 e E7 (tudo a partir da discagem) não foram verificadas por gravação, transcrição ou manual operacional da URA. São hipóteses operacionais que devem ser validadas pelas ligações-teste V1–V5 listadas no `B_relatorio_assistente_v3.md`.

### Camadas dos processos de suporte — agrupamento funcional

| Cluster | Sistemas | Evidência |
|---|---|---|
| Base de elegibilidade | CNIS, eSocial, FGTS/GFIP | [N] Res. 957/2022 |
| Canal de requerimento/recurso | Gov.br, CTPS Digital, SINE-Fácil | [N] Res. 957/2022 / [O] FAQ gov.br |
| Processamento dos requerimentos | Dataprev (arquitetura em aberto) | [I] docs TCU |
| Base de pagamento | Sistemas Caixa (arquitetura em aberto) | [I] |
| Dados de identificação | PIS/NIS, CNIS | [N] critério; [I] integração com URA |
