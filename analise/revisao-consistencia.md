# Revisão de Consistência dos Artefatos de Análise

## Objetivo

Avaliar a consistência interna e cruzada dos quatro artefatos produzidos na fase de análise (`regras-de-negocio.md`, `requisitos-funcionais.md`, `requisitos-nao-funcionais.md`, `duvidas-e-lacunas.md`) frente ao contexto do projeto, aos stakeholders identificados e às observações de entrevista registradas no [README.md](../README.md), antes de avançar para a formalização em `especificacao/`.

## Metodologia

Confronto cruzado dos quatro documentos entre si e contra o contexto/stakeholders do README, buscando: (a) duplicações e sobreposições, (b) contradições entre artefatos, (c) requisitos cuja verificabilidade depende de regras ainda em aberto, (d) dados/critérios sem lastro identificável nas entrevistas, e (e) inconsistências estruturais (numeração, ordenação, rastreabilidade).

**Rodada 2 (atualização):** o usuário forneceu o material primário completo — Contexto do Projeto, Stakeholders x Interesses (ambos idênticos ao README, sem divergência), as falas literais das entrevistas por stakeholder (Participantes, Organizadores, Equipe Financeira, Palestrantes) e a lista oficial de "Observações" (9 pontos em aberto apontados pelos próprios entrevistadores). Os achados abaixo foram atualizados/reforçados com base no confronto direto entre esse material primário e os quatro artefatos — ver "Achados adicionais" ao final.

## Achados

### REV-01 — RNF apresenta números concretos que a própria DL-09 diz não terem sido definidos (Crítico — confirmado pela fonte primária)

- **Descrição:** [duvidas-e-lacunas.md:65-70](duvidas-e-lacunas.md#L65-L70) (DL-09) afirma textualmente que os entrevistados **não definiram critérios específicos** de segurança, tempo de resposta, acessibilidade e proteção de dados, com status "Aberta". No entanto, `requisitos-nao-funcionais.md` já cristaliza esses critérios como se fossem definidos: 3 segundos de resposta ([RNF-01:9-13](requisitos-nao-funcionais.md#L9-L13)), 99% de disponibilidade ([RNF-02:15-19](requisitos-nao-funcionais.md#L15-L19)), diretrizes de acessibilidade ([RNF-10:63-67](requisitos-nao-funcionais.md#L63-L67)), controles de privacidade/LGPD ([RNF-04:27-31](requisitos-nao-funcionais.md#L27-L31) e [RNF-05:33-37](requisitos-nao-funcionais.md#L33-L37)).
- **Confirmação com a fonte primária:** a observação geral #9 fornecida pelo usuário é ainda mais categórica que o resumo do DL-09: *"Não foram levantados requisitos relacionados à segurança, desempenho, disponibilidade, acessibilidade e privacidade dos dados."* Ou seja, não é apenas que os critérios numéricos não foram definidos — o próprio **tema não foi discutido em entrevista**. Isso significa que as 20 regras de `requisitos-nao-funcionais.md`, incluindo os números específicos, foram construídas inteiramente por inferência do analista/IA, sem nenhum insumo de entrevista, e sem que os stakeholders tenham sido consultados sobre desempenho, disponibilidade, acessibilidade, segurança ou privacidade.
- **Impacto:** Contradição direta entre dois artefatos da mesma fase, agora com evidência primária. Se esses números forem levados à especificação como se fossem validados, corre-se o risco de formalizar critérios de aceite nunca pactuados com os stakeholders (ex.: um SLA de 99% pode não refletir o que a Eventus precisa/pode pagar).
- **Recomendação:** Marcar **todo** `requisitos-nao-funcionais.md` como premissas de analista sujeitas a validação (não apenas os itens numéricos), e abrir explicitamente uma rodada de entrevista dedicada a NFRs antes de formalizar qualquer critério de aceite numérico em `especificacao/`.
- **Ação aplicada:** adicionada linha "Observação: Premissa (itens numéricos) sujeitos a validação..." ao final de [RNF-01](requisitos-nao-funcionais.md#L9-L14), [RNF-02](requisitos-nao-funcionais.md#L15-L20) e [RNF-10](requisitos-nao-funcionais.md#L63-L68).

### REV-02 — LGPD/privacidade não aparece em nenhuma entrevista ou interesse de stakeholder registrado (Alto)

- **Descrição:** [RNF-05:33-37](requisitos-nao-funcionais.md#L33-L37) introduz conformidade com a LGPD como requisito, mas nenhum stakeholder do [README.md:16-22](../README.md#L16-L22) (Participantes, Organizadores, Financeiro, Palestrantes, TI) tem esse interesse registrado, e a DL-09 fala genericamente em "privacidade" sem citar LGPD.
- **Impacto:** É uma boa prática defensável (dado que há dados pessoais), mas, tecnicamente, é uma suposição do analista sem rastro de entrevista — o que fragiliza a rastreabilidade que o restante do documento tenta manter (cada item tem "Responsável/origem").
- **Recomendação:** Manter o requisito, mas adicionar uma nota "premissa do analista, não levantada em entrevista" ou incluir uma nova dúvida em `duvidas-e-lacunas.md` perguntando explicitamente aos stakeholders sobre exigências legais de proteção de dados.
- **Ação aplicada:** adicionada linha "Observação: Premissa (itens numéricos) sujeitos a validação..." ao final de [RNF-04](requisitos-nao-funcionais.md#L27-L32) e [RNF-05](requisitos-nao-funcionais.md#L33-L38).

### REV-03 — Duplicações na lista de dúvidas e lacunas (Alto)

Três pares de itens tratam da mesma questão com redação diferente, o que dilui a rastreabilidade (RF/RN não sabem a qual DL apontar) e pode gerar respostas conflitantes dos stakeholders para a "mesma" pergunta feita duas vezes:

| Par duplicado | Itens |
|---|---|
| Ordem da lista de espera | [DL-03:23-28](duvidas-e-lacunas.md#L23-L28) vs [DL-14:100-105](duvidas-e-lacunas.md#L100-L105) |
| Emissão de certificado × confirmação de presença | [DL-04:30-35](duvidas-e-lacunas.md#L30-L35) vs [DL-10:72-77](duvidas-e-lacunas.md#L72-L77) |
| Dados de participantes visíveis a palestrantes | [DL-08:58-63](duvidas-e-lacunas.md#L58-L63) vs [DL-15:107-112](duvidas-e-lacunas.md#L107-L112) |

- **Recomendação:** Consolidar cada par em um único item antes de submeter a lista aos stakeholders — reduz de 15 para ~12 dúvidas reais e evita perguntar a mesma coisa duas vezes com fraseados distintos.

### REV-04 — RN-07/RF-20 apenas parafraseiam a dúvida em aberto DL-06, sem critério de aceite verificável (Alto)

- **Descrição:** [DL-06:44-49](duvidas-e-lacunas.md#L44-L49) registra como pergunta aberta se a vaga é reservada no início do pagamento ou só após confirmação. [RN-07:45-49](regras-de-negocio.md#L45-L49) e [RF-20:155-160](requisitos-funcionais.md#L155-L160) tentam formalizar isso como regra/requisito, mas na prática apenas reafirmam a ambiguidade ("pode variar conforme a regra do evento"; "deve manter uma regra consistente"). O critério de aceite de RF-20 não é testável porque a regra que ele testa ainda não existe.
- **Impacto:** Um requisito com critério de aceite não verificável não deveria avançar para especificação formal como está.
- **Recomendação:** Marcar RF-20 e RN-07 como bloqueados por DL-06; só escrever o critério de aceite definitivo depois que a dúvida for respondida.

### REV-05 — RF-17/RF-18 generalizam a fala da Equipe Financeira para "todo evento pago" (Alto — confirmado pela fonte primária)

- **Descrição:** [RN-06:39-43](regras-de-negocio.md#L39-L43) condiciona a regra a "quando essa regra for exigida" (sugerindo que mesmo eventos pagos poderiam dispensá-la), enquanto [RF-17:134-139](requisitos-funcionais.md#L134-L139) e [RF-18:141-146](requisitos-funcionais.md#L141-L146) tratam a confirmação de pagamento como obrigatória por padrão para todo evento pago, com o critério de aceite afirmando categoricamente que "a inscrição deve ficar pendente até a confirmação".
- **Confirmação com a fonte primária:** a fala literal da Equipe Financeira é *"Precisamos confirmar os pagamentos antes de liberar **determinadas** inscrições"* — não "todas as inscrições de eventos pagos". A palavra "determinadas" indica um subconjunto configurável, não uma regra universal para qualquer evento pago. Ou seja, [RN-06](regras-de-negocio.md#L39-L43) está mais fiel à entrevista; **RF-17 e RF-18 é que extrapolaram** a fala ao tratá-la como regra absoluta para "evento pago" em geral.
- **Impacto:** É uma divergência de escopo entre requisito e entrevista, não apenas uma inconsistência redacional interna — RF-17/RF-18 podem levar a uma implementação mais rígida do que a Equipe Financeira pediu (ex.: travar inscrição pendente em eventos pagos de baixo valor onde isso não é necessário).
- **Recomendação:** Reescrever RF-17/RF-18 para refletir "determinadas inscrições/eventos, conforme regra configurável", alinhando com RN-06, e registrar como nova dúvida (ou anexar à DL-06) qual é o critério que define quais inscrições exigem confirmação prévia.

### REV-06 — Sobreposição parcial entre DL-11 e DL-13 (Baixo)

- **Descrição:** [DL-11:79-84](duvidas-e-lacunas.md#L79-L84) (fluxo por evento gratuito/pago) e [DL-13:93-98](duvidas-e-lacunas.md#L93-L98) (regras específicas por tipo de evento: congresso, workshop, corporativo) tratam da mesma raiz — "o sistema tem uma política única ou variações por categoria de evento?" — sob dois recortes diferentes (forma de pagamento vs. tipo de evento).
- **Recomendação:** Não são duplicatas puras (recortes diferentes), mas vale unificar a pergunta aos stakeholders em uma única rodada sobre "matriz de variação de regras por tipo/categoria de evento", cobrindo pagamento, cancelamento, lista de espera e certificado de uma vez.

### REV-07 — Inconsistência estrutural de numeração em requisitos-funcionais.md (Baixo)

- **Descrição:** Dentro da seção "2. Módulo de Organizadores" ([requisitos-funcionais.md:67-130](requisitos-funcionais.md#L67-L130)), a sequência é RF-09 a RF-16 e depois **RF-23** ([:125-130](requisitos-funcionais.md#L125-L130)) — fora de ordem, pulando à frente dos módulos 3 e 4 (RF-17 a RF-22) que aparecem depois no documento. Isso sugere que RF-23/RF-24 foram adicionados posteriormente sem renumerar.
- **Impacto:** Não há duplicação nem lacuna de ID (todos de RF-01 a RF-24 existem uma única vez), mas a ordem de leitura do documento não bate com a ordem numérica, dificultando rastreabilidade em revisões futuras.
- **Recomendação:** Renumerar sequencialmente por módulo (ou aceitar formalmente que a numeração é cronológica, não posicional, e documentar isso no objetivo do arquivo).

### REV-08 — Ausência de glossário para a hierarquia Evento → Atividade → Workshop (Médio)

- **Descrição:** Os documentos usam "evento", "atividade" e "workshop" de forma intercambiável sem definição formal. Ex.: [RF-02:20](requisitos-funcionais.md#L20) fala em inscrição "em eventos, workshops e atividades específicas"; [RN-17:105-109](regras-de-negocio.md#L105-L109) e [RF-16:118-123](requisitos-funcionais.md#L118-L123) tratam "atividades" como componentes de um evento (com horário/local próprios), o que é coerente, mas nunca é declarado explicitamente como modelo conceitual.
- **Impacto:** Sem esse modelo explícito, RN-10/RN-11 (conflito de horário) e RF-03/RF-15 ficam sujeitos a interpretação sobre se o conflito é entre eventos, entre atividades do mesmo evento, ou entre atividades de eventos diferentes.
- **Recomendação:** Antes de formalizar, incluir um glossário curto ou um pequeno modelo conceitual (Evento 1:N Atividade; Atividade pode ser do tipo Workshop/Palestra/etc.) em `especificacao/`.

### REV-09 — Decisão de excluir "Equipe de TI" como módulo funcional não está registrada como premissa rastreável (Baixo)

- **Descrição:** O README ([:21-22](../README.md#L21-L22)) lista Equipe de TI como stakeholder com interesse "desenvolver e manter o sistema". `requisitos-funcionais.md` decide, em uma frase no Objetivo ([:5](requisitos-funcionais.md#L5)), que essa equipe "não constitui um módulo funcional do sistema". A decisão é razoável (é a equipe construtora, não uma persona de negócio), mas está registrada apenas como observação de rodapé, não como premissa formal em `duvidas-e-lacunas.md` ou equivalente.
- **Recomendação:** Elevar isso a uma premissa explícita (ex.: seção "Premissas" em cada artefato, ou item em DL marcado como "Resolvida"), para que fique claro que foi uma decisão consciente e não um esquecimento.

### REV-10 — Conteúdo mínimo do certificado (RN-14) não tem lastro identificável em entrevista (Baixo)

- **Descrição:** [RN-14:87-91](regras-de-negocio.md#L87-L91) especifica campos mínimos do certificado (nome, evento, carga horária, data, assinatura/validação) sem que o README ou qualquer outra DL mencione esse nível de detalhe como levantado em entrevista.
- **Recomendação:** É um padrão de mercado razoável, mas por consistência com o rigor de rastreabilidade do restante do documento, marcar como premissa do analista a confirmar, e não como regra levantada com o stakeholder.

## Achados adicionais (rodada 2 — confronto com a fonte primária)

### REV-11 — 6 das 15 dúvidas (DL-10 a DL-15) não têm origem rastreável na lista oficial de "Observações" (Crítico)

- **Descrição:** A lista de "Observações" fornecida pelos entrevistadores traz exatamente **9 pontos em aberto**. Ao confrontar item a item, cada um mapeia 1:1 e quase literalmente para DL-01 a DL-09:

  | # Observação original | DL correspondente |
  |---|---|
  | "até quando o participante poderá cancelar" | [DL-01](duvidas-e-lacunas.md#L9-L14) |
  | "quais situações haverá reembolso" | [DL-02](duvidas-e-lacunas.md#L16-L21) |
  | "como funcionará a lista de espera" | [DL-03](duvidas-e-lacunas.md#L23-L28) |
  | "certificados automáticos ou dependem de presença" | [DL-04](duvidas-e-lacunas.md#L30-L35) |
  | "como serão enviados comprovantes e notificações" | [DL-05](duvidas-e-lacunas.md#L37-L42) |
  | "vaga reservada no início do pagamento ou após confirmação" | [DL-06](duvidas-e-lacunas.md#L44-L49) |
  | "tratamento de inscrição em horários conflitantes" | [DL-07](duvidas-e-lacunas.md#L51-L56) |
  | "quais informações de participantes os palestrantes veem" | [DL-08](duvidas-e-lacunas.md#L58-L63) |
  | "requisitos de segurança, desempenho, disponibilidade, acessibilidade, privacidade" | [DL-09](duvidas-e-lacunas.md#L65-L70) |

  **Nenhuma das 9 observações originais dá origem a DL-10, DL-11, DL-12, DL-13, DL-14 ou DL-15.** DL-10 e DL-14 e DL-15 são reformulações de DL-04, DL-03 e DL-08 respectivamente (confirma REV-03). Já **DL-11** ("política de inscrições em eventos gratuitos/pagos"), **DL-12** ("perfil e permissão dos usuários") e **DL-13** ("tipos de eventos e regras específicas") não correspondem a nenhuma fala de entrevista nem a nenhuma observação geral — são lacunas inferidas pelo analista/IA a partir do contexto, o que é um trabalho de análise legítimo, mas o documento as apresenta com o mesmo formato e o mesmo campo "Responsável/origem" (ex.: DL-11 diz "Equipe financeira e organizadores", DL-12 diz "organizadores e equipe de TI") **como se fossem oriundas diretamente da entrevista**, sem essa distinção.
- **Impacto:** Perda de rastreabilidade entre origem real (entrevista vs. inferência) e o registro formal. Isso é importante justamente no critério que o usuário pediu para checar: consistência com "o que foi informado pelos stakeholders". 6 de 15 itens (40%) não foram, de fato, informados — foram deduzidos.
- **Recomendação:** Adicionar um campo "Origem" a cada DL com dois valores possíveis: "Observação direta da entrevista" (DL-01 a DL-09) ou "Lacuna inferida pela análise" (DL-11, DL-12, DL-13, após consolidar os duplicados DL-10/14/15 nos seus pares). Isso não invalida os itens inferidos — só evita apresentá-los como se tivessem o mesmo lastro dos demais.

### REV-12 — Priorização dos requisitos funcionais não reflete a linguagem sugestiva usada nas entrevistas (Médio)

- **Descrição:** 19 dos 24 requisitos funcionais estão marcados como "Prioridade: Alta" (apenas RF-20, RF-21, RF-22 e RF-23 são "Média"; nenhum é "Baixa"). Várias dessas prioridades "Alta" derivam de falas visivelmente sugestivas/condicionais nas entrevistas, e não de pedidos categóricos: *"Seria **interessante** receber um comprovante"* (base de [RF-04](requisitos-funcionais.md#L32-L37), Alta), *"Quando um evento lotar, **seria interessante** criar uma lista de espera"* (base de [RF-11](requisitos-funcionais.md#L83-L88), Alta).
- **Impacto:** Sem um critério de priorização explícito (ex.: MoSCoW, valor de negócio, urgência) documentado, marcar quase tudo como "Alta" reduz a utilidade da priorização para planejar um MVP ou primeira release — não há como saber pela documentação por que um item de fala "seria interessante" ficou no mesmo nível que "precisamos controlar automaticamente o número de vagas" (necessidade explícita dos organizadores).
- **Recomendação:** Antes da especificação formal, revisitar a priorização com um critério declarado (ex.: correlacionar intensidade da fala do stakeholder — "precisamos"/"não podemos" vs. "seria interessante"/"gostaria" — com a prioridade atribuída) e usar toda a escala (Alta/Média/Baixa) para permitir faseamento do desenvolvimento.

### REV-13 — Falas de entrevista validadas sem divergência (registro de confirmação)

Para constar como checagem positiva: as falas de Participantes, Organizadores e Palestrantes batem com os artefatos sem contradição relevante — cancelamento self-service ([RF-05](requisitos-funcionais.md#L39-L44) / [RN-03](regras-de-negocio.md#L21-L26)), inscrição em múltiplos workshops no mesmo dia sem conflito ([RF-03](requisitos-funcionais.md#L25-L30) / [RN-10](regras-de-negocio.md#L63-L67), reforçado pela fala "os workshops que acontecem no mesmo horário devem ocorrer simultaneamente" — que justifica o bloqueio de inscrição concorrente, e não o contradiz), controle automático de vagas ([RF-10](requisitos-funcionais.md#L76-L81) / [RN-01](regras-de-negocio.md#L9-L13)), acompanhamento em tempo real ([RF-12](requisitos-funcionais.md#L90-L95) / [RN-18](regras-de-negocio.md#L111-L115)), eventos gratuitos/pagos ([RN-08](regras-de-negocio.md#L51-L55)) e consulta de participantes por palestrante ([RF-22](requisitos-funcionais.md#L171-L176) / [RN-16](regras-de-negocio.md#L99-L103)). Nenhum achado adicional necessário nesses pontos.

## Síntese

Com o material primário completo (contexto, stakeholders, falas de entrevista e observações gerais), a análise confirma que os quatro artefatos são **estruturalmente sólidos e majoritariamente fiéis** ao que foi de fato levantado — todas as falas de Participantes, Organizadores e Palestrantes têm correspondência direta em RF/RN sem contradição (REV-13), e as 9 observações gerais mapeiam 1:1 para DL-01 a DL-09.

Os dois problemas centrais expostos por esse confronto direto com a fonte primária são:

1. **`requisitos-nao-funcionais.md` foi construído sobre um tema que a própria observação #9 diz que nunca foi discutido em entrevista** (REV-01) — não é uma lacuna de detalhe, é a ausência total do assunto na coleta de dados.
2. **Cerca de 40% da lista de dúvidas (DL-10 a DL-15) não vem das observações nem das falas registradas** (REV-11) — são inferências do analista apresentadas com o mesmo formato dos itens realmente coletados, sem indicação de origem.

A esses se soma uma extrapolação pontual de escopo identificada com evidência literal: RF-17/RF-18 generalizam para "todo evento pago" uma fala da Equipe Financeira que dizia explicitamente "**determinadas** inscrições" (REV-05).

### Prioridade sugerida antes da formalização

1. **REV-01**: marcar todo `requisitos-nao-funcionais.md` como premissa do analista (não validada em entrevista) antes de levar qualquer número a `especificacao/`.
2. **REV-11**: adicionar campo de origem a cada DL, separando o que veio das 9 observações (DL-01–09) do que foi inferido pela análise (DL-11, 12, 13, após consolidar duplicatas).
3. **REV-03 / REV-11**: consolidar as dúvidas duplicadas (DL-03/14, DL-04/10, DL-08/15).
4. **REV-05**: reescrever RF-17/RF-18 para não extrapolar a fala da Equipe Financeira ("determinadas inscrições" ≠ "todo evento pago").
5. Levar as dúvidas consolidadas aos stakeholders antes de escrever a especificação formal — ~10 dos 24 requisitos funcionais e ~7 das 24 regras de negócio dependem diretamente de alguma dúvida ainda aberta.
6. Ajustes de menor esforço: REV-04 (critério de aceite não verificável em RF-20), REV-07 (numeração), REV-08 (glossário), REV-09/REV-10 (premissas sem fonte) e REV-12 (revisar critério de priorização, hoje concentrado quase todo em "Alta").
