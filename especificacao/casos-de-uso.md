# Casos de Uso

## 1. Objetivo

Descrever os principais comportamentos do sistema de gestão de eventos a partir dos objetivos dos participantes, organizadores, equipe financeira e palestrantes. Este documento utiliza os requisitos funcionais (RF), as regras de negócio (RN) e as dúvidas e lacunas (DL) identificados na análise.

## 2. Atores

| Ator | Responsabilidade no sistema |
|---|---|
| Participante | Consultar eventos, realizar e acompanhar inscrições, cancelar participação e obter comprovantes/certificados. |
| Organizador | Criar eventos, configurar regras, administrar agenda, vagas, participantes e certificados. |
| Equipe financeira | Consultar e atualizar pagamentos e processar reembolsos conforme as políticas definidas. |
| Palestrante | Consultar a própria programação e os participantes de suas atividades, dentro dos limites de acesso. |
| Sistema de pagamento | Serviço externo opcional para processar transações de eventos pagos. |
| Serviço de notificações | Serviço responsável pelo envio de mensagens, quando o canal for definido. |

A equipe de TI é responsável pela construção e manutenção da solução, mas não é considerada ator funcional dos casos de uso de negócio.

## 3. Modelo conceitual

- Um **evento** possui uma ou mais **atividades**.
- Uma atividade pode ser um workshop, palestra ou outro tipo de programação.
- Uma inscrição vincula um participante a um evento e, quando aplicável, às atividades escolhidas.
- O comportamento de pagamento, cancelamento, lista de espera, certificado e notificações pode variar conforme a política do evento.

## 4. Visão geral dos casos de uso

| ID | Caso de uso | Atores principais | RF relacionados |
|---|---|---|---|
| UC-01 | Consultar eventos e programação | Participante | RF-01, RF-16 |
| UC-02 | Realizar inscrição | Participante, Sistema de pagamento | RF-02, RF-03, RF-10, RF-15, RF-18, RF-19, RF-21 |
| UC-03 | Acompanhar inscrição e obter comprovante | Participante, Serviço de notificações | RF-04, RF-06, RF-08 |
| UC-04 | Cancelar inscrição e solicitar reembolso | Participante, Equipe financeira | RF-05, RF-20 |
| UC-05 | Emitir certificado | Participante, Organizador | RF-07, RF-17 |
| UC-06 | Cadastrar e configurar evento | Organizador | RF-09, RF-14, RF-16, RF-17 |
| UC-07 | Controlar vagas e lista de espera | Organizador, Participante, Serviço de notificações | RF-10, RF-11, RF-12 |
| UC-08 | Gerenciar participantes | Organizador | RF-13 |
| UC-09 | Processar pagamento e reembolso | Equipe financeira, Sistema de pagamento | RF-18, RF-19, RF-20, RF-21 |
| UC-10 | Consultar programação e participantes da atividade | Palestrante | RF-22, RF-23 |
| UC-11 | Administrar acessos por perfil | Organizador ou administrador autorizado | RF-24 |

## 5. Especificação dos casos de uso

### UC-01 - Consultar eventos e programação

**Objetivo:** permitir a consulta dos eventos ativos e de suas atividades.

**Atores:** participante.

**Pré-condições:** o sistema deve estar disponível; eventos ativos podem ser consultados conforme a política de acesso.

**Fluxo principal:**

1. O participante acessa a área de eventos.
2. O sistema apresenta eventos ativos com nome, data, horário, local, tipo, vagas e valor.
3. O participante seleciona um evento.
4. O sistema apresenta a descrição, regras, agenda e atividades disponíveis.
5. O participante pode retornar à lista ou iniciar UC-02.

**Fluxos alternativos:**

- Se não houver eventos ativos, o sistema informa que não existem eventos disponíveis.
- Se uma atividade estiver lotada, o sistema informa a situação e apresenta a opção de lista de espera quando essa política estiver habilitada.

**Regras e requisitos:** RN-01, RN-02, RN-08, RN-17; RF-01, RF-16.

### UC-02 - Realizar inscrição

**Objetivo:** registrar a inscrição do participante em um evento ou em atividades do evento.

**Atores:** participante; sistema de pagamento, quando aplicável.

**Pré-condições:** participante autenticado; evento ativo; dados obrigatórios preenchidos.

**Fluxo principal:**

1. O participante seleciona o evento e as atividades desejadas.
2. O sistema verifica vagas, duplicidade, conflito de horário e regras do evento.
3. O participante confirma seus dados e a inscrição.
4. Para evento gratuito ou inscrição sem pagamento prévio, o sistema confirma a inscrição.
5. Para inscrição que exige pagamento prévio, o sistema encaminha o participante ao pagamento.
6. O sistema registra a inscrição com o status adequado.
7. O sistema atualiza vagas e disponibiliza a confirmação ou o status pendente.

**Fluxos alternativos:**

- Se não houver vaga e houver lista de espera habilitada, o participante pode entrar na lista de espera.
- Se houver conflito de horário, o sistema bloqueia a atividade conflitante e informa o motivo.
- Se o evento estiver lotado e não aceitar lista de espera, o sistema impede a inscrição.
- Se o pagamento falhar, o sistema mantém o status coerente e informa a falha, sem duplicar a inscrição.
- Se a vaga for reservada durante o pagamento, o comportamento seguirá a política definida para o evento.

**Pós-condições:** inscrição criada com status confirmada, pendente ou em lista de espera; vagas e histórico atualizados.

**Regras e requisitos:** RN-01, RN-02, RN-06, RN-07, RN-08, RN-09, RN-10, RN-11, RN-21; RF-02, RF-03, RF-10, RF-11, RF-15, RF-18, RF-19, RF-21.

**Dependências em aberto:** DL-03, DL-06, DL-07 e DL-12.

### UC-03 - Acompanhar inscrição e obter comprovante

**Objetivo:** permitir que o participante consulte a situação da inscrição e acesse seu comprovante.

**Atores:** participante; serviço de notificações, quando configurado.

**Pré-condições:** participante autenticado e com inscrição registrada.

**Fluxo principal:**

1. O participante acessa "Minhas inscrições".
2. O sistema apresenta evento, atividades, data e status da inscrição.
3. O participante seleciona uma inscrição.
4. O sistema disponibiliza o comprovante conforme o status e a política do evento.
5. Quando houver mudança relevante, o sistema envia notificação pelo canal configurado.

**Fluxos alternativos:**

- Para inscrição pendente, o sistema informa a pendência e a próxima ação esperada.
- Para inscrição em lista de espera, o sistema apresenta a posição ou o status disponível conforme a regra definida.
- Se o canal de notificação ainda não estiver definido, o comprovante permanece disponível no portal, sem presumir um canal externo.

**Regras e requisitos:** RN-09, RN-12, RN-22; RF-04, RF-06, RF-08.

**Dependência em aberto:** DL-05.

### UC-04 - Cancelar inscrição e solicitar reembolso

**Objetivo:** permitir o cancelamento dentro das condições do evento e iniciar o reembolso quando aplicável.

**Atores:** participante; equipe financeira.

**Pré-condições:** participante autenticado; inscrição existente; evento com cancelamento permitido.

**Fluxo principal:**

1. O participante acessa uma inscrição confirmada.
2. O sistema verifica a política e o prazo de cancelamento.
3. O participante confirma o cancelamento.
4. O sistema altera o status para cancelada, libera a vaga quando aplicável e registra a operação.
5. O sistema verifica se existe direito a reembolso.
6. Se houver direito, o sistema registra a solicitação para processamento financeiro.
7. O sistema informa o resultado ao participante.

**Fluxos alternativos:**

- Se o prazo tiver expirado, o sistema bloqueia o cancelamento e informa a regra aplicável.
- Se o evento não permitir cancelamento, o sistema bloqueia a ação.
- Se não houver direito a reembolso, o cancelamento é registrado sem solicitação financeira.

**Regras e requisitos:** RN-03, RN-04, RN-05, RN-09, RN-20, RN-21; RF-05, RF-13, RF-14, RF-20.

**Dependências em aberto:** DL-01 e DL-02.

### UC-05 - Emitir certificado

**Objetivo:** disponibilizar o certificado após o atendimento às condições do evento.

**Atores:** participante; organizador.

**Pré-condições:** evento concluído; participante elegível segundo a configuração do evento.

**Fluxo principal:**

1. O organizador configura a emissão automática ou condicionada.
2. O sistema verifica a conclusão do evento e a condição de presença, quando exigida.
3. O sistema gera o certificado com os dados mínimos definidos.
4. O participante acessa e baixa o certificado.
5. O sistema registra a emissão no histórico.

**Fluxos alternativos:**

- Se a confirmação de presença for obrigatória e ainda não estiver registrada, o sistema informa que o certificado está bloqueado.
- Se a emissão for manual ou condicionada a outra validação, o sistema aguarda a ação autorizada do organizador.

**Regras e requisitos:** RN-13, RN-14, RN-20, RN-23; RF-07, RF-17.

**Dependência em aberto:** DL-04.

### UC-06 - Cadastrar e configurar evento

**Objetivo:** permitir ao organizador estruturar um evento e suas regras operacionais.

**Atores:** organizador.

**Pré-condições:** organizador autenticado e autorizado.

**Fluxo principal:**

1. O organizador acessa o cadastro de eventos.
2. O sistema solicita nome, descrição, data, local, tipo, capacidade e valor.
3. O organizador define atividades, horários, salas e palestrantes.
4. O organizador configura cancelamento, reembolso, lista de espera, pagamento e certificado.
5. O organizador salva o evento como rascunho ou ativa sua publicação.
6. O sistema valida os dados e disponibiliza o evento conforme o status escolhido.

**Fluxos alternativos:**

- Se houver dados obrigatórios ausentes ou conflito na agenda, o sistema impede a ativação e identifica os ajustes necessários.
- Se a política de alguma regra ainda não estiver definida, o organizador mantém o evento em configuração sem fechar a decisão automaticamente.

**Regras e requisitos:** RN-03, RN-05, RN-07, RN-08, RN-13, RN-17, RN-23, RN-24; RF-09, RF-14, RF-16, RF-17.

**Dependências em aberto:** DL-01, DL-02, DL-03, DL-04, DL-06, DL-07 e DL-10.

### UC-07 - Controlar vagas e lista de espera

**Objetivo:** acompanhar a ocupação e administrar a entrada de participantes quando surgirem vagas.

**Atores:** organizador; participante; serviço de notificações.

**Pré-condições:** evento cadastrado com capacidade e política de lista de espera.

**Fluxo principal:**

1. O organizador acessa o painel do evento.
2. O sistema apresenta vagas totais, ocupadas, disponíveis e participantes em espera.
3. Uma inscrição, cancelamento ou confirmação altera os totais.
4. Quando surge vaga, o sistema identifica o próximo participante conforme a regra do evento.
5. O sistema atualiza o status e notifica os envolvidos quando o canal estiver configurado.

**Fluxos alternativos:**

- Se não houver lista de espera, novas inscrições são bloqueadas ao atingir a capacidade.
- Se houver regra especial de prioridade, o sistema aplica a regra configurada em vez de assumir ordem de cadastro.

**Regras e requisitos:** RN-01, RN-02, RN-18, RN-24; RF-10, RF-11, RF-12.

**Dependência em aberto:** DL-03.

### UC-08 - Gerenciar participantes

**Objetivo:** permitir ao organizador consultar e administrar participantes de um evento.

**Atores:** organizador.

**Pré-condições:** organizador autenticado e autorizado para o evento.

**Fluxo principal:**

1. O organizador seleciona um evento.
2. O sistema apresenta a lista de participantes e seus status.
3. O organizador filtra ou pesquisa a lista.
4. O organizador consulta os dados permitidos e acompanha alterações relevantes.
5. O sistema registra ações administrativas no histórico.

**Regras e requisitos:** RN-09, RN-18, RN-19, RN-20; RF-12, RF-13, RF-24.

### UC-09 - Processar pagamento e reembolso

**Objetivo:** controlar pagamentos e reembolsos sem gerar inconsistência na inscrição.

**Atores:** equipe financeira; sistema de pagamento.

**Pré-condições:** usuário financeiro autenticado; inscrição ou solicitação financeira registrada.

**Fluxo principal:**

1. A equipe financeira consulta inscrições pendentes ou solicitações de reembolso.
2. O sistema apresenta evento, participante, valor, status e histórico.
3. A equipe confirma ou rejeita o pagamento recebido, conforme retorno do serviço de pagamento.
4. O sistema atualiza o status da inscrição e registra a operação.
5. Para reembolso elegível, a equipe autoriza ou acompanha a execução.
6. O sistema atualiza o status para reembolsada quando a operação for concluída.

**Fluxos alternativos:**

- Em caso de falha ou recusa, o sistema mantém o pagamento como recusado ou pendente e não confirma indevidamente a inscrição.
- Se a inscrição não se enquadrar no critério de pagamento prévio, o sistema segue a política configurada.

**Regras e requisitos:** RN-05, RN-06, RN-07, RN-08, RN-09, RN-20, RN-21; RF-18, RF-19, RF-20, RF-21.

**Dependências em aberto:** DL-02, DL-06 e DL-12.

### UC-10 - Consultar programação e participantes da atividade

**Objetivo:** permitir que o palestrante consulte apenas as informações necessárias para sua atuação.

**Atores:** palestrante.

**Pré-condições:** palestrante autenticado e vinculado a uma atividade.

**Fluxo principal:**

1. O palestrante acessa sua área.
2. O sistema apresenta suas atividades, datas, horários, locais e temas.
3. O palestrante seleciona uma atividade.
4. O sistema apresenta a lista de participantes autorizada para aquela atividade.
5. O sistema oculta dados não necessários ou não autorizados.

**Fluxos alternativos:**

- Se o palestrante não estiver vinculado à atividade, o sistema bloqueia a consulta.
- Se o conjunto de dados permitido ainda não estiver definido, o sistema apresenta somente o mínimo configurado e mantém os demais dados ocultos.

**Regras e requisitos:** RN-15, RN-16, RN-19; RF-22, RF-23, RF-24.

**Dependência em aberto:** DL-08.

### UC-11 - Administrar acessos por perfil

**Objetivo:** garantir que cada perfil visualize e execute somente as ações autorizadas.

**Atores:** administrador ou organizador autorizado.

**Pré-condições:** usuário administrador autenticado.

**Fluxo principal:**

1. O administrador acessa a gestão de usuários e perfis.
2. O sistema apresenta os perfis disponíveis: participante, organizador, financeiro e palestrante.
3. O administrador associa permissões ao perfil ou ao usuário autorizado.
4. O sistema valida a alteração e registra o histórico.
5. No próximo acesso, o sistema aplica as permissões definidas.

**Fluxos alternativos:**

- Se a permissão não for compatível com o perfil, o sistema impede o salvamento.
- Usuários sem autorização não acessam a área administrativa.

**Regras e requisitos:** RN-19, RN-20, RN-21; RF-24.

**Dependência em aberto:** DL-11.

## 6. Requisitos não funcionais transversais

Todos os casos de uso devem considerar os requisitos não funcionais RNF-01 a RNF-20, especialmente:

- resposta adequada em consultas e inscrições;
- disponibilidade e recuperação diante de falhas;
- autenticação, autorização e proteção de dados;
- consistência em concorrência de inscrições e pagamentos;
- acessibilidade, usabilidade e compatibilidade com dispositivos;
- registro de auditoria e mensagens claras.

Os critérios numéricos e as exigências de segurança, desempenho, disponibilidade, acessibilidade e privacidade permanecem sujeitos à validação dos stakeholders conforme DL-09.

## 7. Rastreabilidade resumida

| Grupo de casos de uso | Requisitos cobertos |
|---|---|
| Participante | RF-01 a RF-08 |
| Organizador | RF-09 a RF-17 |
| Financeiro | RF-18 a RF-21 |
| Palestrante | RF-22 e RF-23 |
| Acessos | RF-24 |
