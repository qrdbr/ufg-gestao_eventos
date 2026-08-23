# Requisitos Funcionais

## Objetivo

Registrar as funcionalidades que o sistema de gestão de eventos deve oferecer para atender aos objetivos de participantes, organizadores, equipe financeira e palestrantes. A equipe de TI é responsável pela construção e manutenção da solução, mas não constitui um módulo funcional do sistema.

## Critério de priorização

A prioridade de cada requisito considera dois fatores combinados: (a) se o requisito integra o fluxo essencial de inscrição/gestão de eventos ou uma dor explícita do contexto do projeto (controle de vagas, pagamentos, cancelamentos, certificados), e (b) a intensidade da linguagem usada pelo stakeholder na entrevista — falas de necessidade ("precisamos", "quero") pesam mais que falas sugestivas ("gostaria", "seria interessante"). **Alta**: essencial ao fluxo central ou expressa como necessidade. **Média**: melhoria/refinamento sobre um fluxo já coberto, expressa de forma sugestiva, ou dependente de uma dúvida ainda aberta em `duvidas-e-lacunas.md`. **Baixa**: conveniência adicional, sem fala direta de stakeholder a sustentá-la.

## Nota sobre numeração

Os identificadores RF-XX seguem a ordem de leitura do documento (por módulo), renumerados nesta revisão (REV-07) para eliminar a inconsistência em que RF-23/RF-24 apareciam fora de ordem, antes dos módulos 3 e 4. Mapa de renumeração (ID anterior → ID atual), para quem tiver referências antigas:

| ID anterior | ID atual | Item |
|---|---|---|
| RF-23 | RF-17 | Emissão de certificados automática ou condicionada |
| RF-17 | RF-18 | Pagamento de inscrições |
| RF-18 | RF-19 | Confirmação de pagamento antes da liberação da inscrição |
| RF-19 | RF-20 | Reembolso da inscrição |
| RF-20 | RF-21 | Reserva de vaga no pagamento |
| RF-21 | RF-22 | Consulta de programação para palestrantes |
| RF-22 | RF-23 | Consulta de participantes inscritos por atividade |
| RF-24 | RF-24 | Gestão de acesso por perfil de usuário (inalterado) |

Todos os demais IDs (RF-01 a RF-16) permanecem inalterados.

## Agrupamento por público (stakeholder)

### 1. Módulo de Participantes

#### RF-01 - Visualização de eventos disponíveis
- Nome: Visualização de eventos disponíveis
- Descrição: O sistema deve permitir que participantes visualizem, em um único local, todos os eventos disponíveis, com informações relevantes como nome, data, horário, local, tipo de evento, vagas disponíveis e valores.
- Prioridade: Alta
- Critério de aceite: Diante de um participante autenticado, o sistema deve exibir uma listagem com todos os eventos ativos e suas informações principais, sem necessidade de contato manual com a organização.
- Observações: A listagem deve facilitar a busca e a navegação entre diferentes eventos.

#### RF-02 - Inscrição em eventos
- Nome: Inscrição em eventos
- Descrição: O sistema deve permitir que participantes realizem inscrição em eventos, workshops e atividades específicas, registrando os dados do participante e vinculando a inscrição ao evento correspondente.
- Prioridade: Alta
- Critério de aceite: Ao selecionar um evento com vaga disponível e confirmar a inscrição, o sistema deve registrar a participação e atualizar o número de inscritos.
- Observações: A inscrição deve ser validada conforme regras de disponibilidade, pagamento e conflito de horários.

#### RF-03 - Inscrição em múltiplos workshops no mesmo dia
- Nome: Inscrição em vários workshops no mesmo dia
- Descrição: O sistema deve permitir a inscrição simultânea do participante em diferentes workshops que ocorram no mesmo dia, desde que não haja conflito de horário ou restrição do evento.
- Prioridade: Média
- Critério de aceite: Se dois workshops forem incompatíveis por conflito de horário, o sistema deve bloquear a segunda inscrição e informar a incompatibilidade.
- Observações: Deve existir validação para impedir que o participante se inscreva em atividades que ocorram ao mesmo tempo. Prioridade ajustada de Alta para Média (REV-12): refinamento da RF-02, baseado em fala sugestiva do participante ("gostaria de me inscrever"), não bloqueia o fluxo essencial de inscrição.

#### RF-04 - Comprovante de inscrição
- Nome: Emissão de comprovante de inscrição
- Descrição: Após a confirmação da inscrição, o sistema deve gerar e disponibilizar um comprovante para o participante, com dados do evento, data da inscrição e status da participação.
- Prioridade: Média
- Critério de aceite: Após uma inscrição confirmada, o sistema deve apresentar o comprovante na interface do participante e/ou enviá-lo por e-mail.
- Observações: O comprovante pode ser enviado por e-mail ou disponibilizado no portal do participante. Prioridade ajustada de Alta para Média (REV-12): fala do participante é sugestiva ("seria interessante"), item de conveniência que não bloqueia a confirmação da inscrição em si.

#### RF-05 - Cancelamento de inscrição
- Nome: Cancelamento de inscrição
- Descrição: O sistema deve permitir que o participante cancele uma inscrição, sem a necessidade de contato direto com a organização, desde que a política do evento permita essa ação.
- Prioridade: Média
- Critério de aceite: Quando a inscrição estiver dentro do prazo permitido e o evento permitir cancelamento, o participante deve conseguir cancelar a inscrição e receber confirmação do sistema.
- Observações: O cancelamento deve seguir regras específicas de prazo, condições do evento e possíveis reembolsos. Prioridade ajustada de Alta para Média (REV-15): critério de aceite depende do prazo definido em DL-01, ainda aberta — aplicando de forma consistente o mesmo critério de dependência já usado para rebaixar RF-11.

#### RF-06 - Acompanhamento do status da inscrição
- Nome: Acompanhamento do status da inscrição
- Descrição: O participante deve visualizar o status de sua inscrição, incluindo pendente, confirmada, cancelada, em lista de espera e reembolsada, quando aplicável.
- Prioridade: Média
- Critério de aceite: A interface do participante deve exibir, de forma clara, o status atual da inscrição e a data da última alteração.
- Observações: O status deve permitir clareza sobre a situação atual da participação. Prioridade ajustada de Alta para Média (REV-12): não há fala direta de stakeholder pedindo esse acompanhamento; é funcionalidade de suporte a RF-02/RF-05, não citada como necessidade explícita.

#### RF-07 - Emissão de certificado
- Nome: Emissão de certificado
- Descrição: O sistema deve permitir a emissão de certificado para o participante após a realização do evento ou atividade, conforme regras estabelecidas pela organização.
- Prioridade: Média
- Critério de aceite: Após o evento ou quando a regra de presença for atendida, o participante deve conseguir acessar e baixar seu certificado.
- Observações: A emissão pode depender da confirmação de presença ou de outros critérios definidos pelo evento. Prioridade ajustada de Alta para Média (REV-15): critério de aceite depende da regra de presença/emissão definida em DL-04, ainda aberta — aplicando de forma consistente o mesmo critério de dependência já usado para rebaixar RF-11.

#### RF-08 - Notificações e comprovantes
- Nome: Envio de comprovantes e notificações
- Descrição: O sistema deve enviar comprovantes de inscrição, confirmações, cancelamentos, lembretes e demais notificações aos participantes por meio dos canais definidos pela organização.
- Prioridade: Baixa
- Critério de aceite: Sempre que houver uma mudança relevante no processo de inscrição, o participante deve receber notificação por e-mail ou outro canal informado.
- Observações: E-mail, mensagens diretas ou portal do participante podem ser utilizados conforme a estratégia da empresa. Prioridade ajustada de Alta para Baixa (REV-12): não há fala direta de stakeholder solicitando notificações; o canal de envio depende de DL-05, ainda aberta, o que naturalmente empurra este item para uma fase posterior.

### 2. Módulo de Organizadores

#### RF-09 - Cadastro e gestão de eventos
- Nome: Cadastro e gestão de eventos
- Descrição: Os organizadores devem poder criar, editar, ativar e desativar eventos, definindo informações como nome, descrição, data, local, capacidade, tipo de evento, regras de cancelamento e forma de pagamento.
- Prioridade: Alta
- Critério de aceite: Um organizador autenticado deve conseguir cadastrar um novo evento e alterar os dados básicos sem intervenção manual externa.
- Observações: O cadastro deve ser centralizado para facilitar a gestão do portfólio de eventos.

#### RF-10 - Controle automático de vagas
- Nome: Controle automático de vagas
- Descrição: O sistema deve controlar automaticamente a quantidade de vagas disponíveis de cada evento e impedir novas inscrições quando a capacidade for atingida.
- Prioridade: Alta
- Critério de aceite: Quando o número de inscrições atingir o limite do evento, o sistema deve impedir novas inscrições confirmadas e exibir a situação de lotado.
- Observações: A regra deve considerar vagas totais e vagas remanescentes por atividade.

#### RF-11 - Lista de espera
- Nome: Gestão de lista de espera
- Descrição: Quando um evento atingir a capacidade máxima, o sistema deve permitir a criação de uma lista de espera para participantes interessados em ocupar vagas disponíveis posteriormente.
- Prioridade: Média
- Critério de aceite: Quando houver lotação, o sistema deve aceitar inscrições em lista de espera e, ao surgirem vagas, notificar o próximo participante em ordem.
- Observações: O sistema deve permitir a movimentação automática entre lista de espera e participantes confirmados. Prioridade ajustada de Alta para Média (REV-12): fala do organizador é sugestiva ("seria interessante"), e a regra de ordenação ainda depende de DL-03, em aberto.

#### RF-12 - Acompanhamento de inscritos em tempo real
- Nome: Acompanhamento de inscritos em tempo real
- Descrição: O sistema deve disponibilizar para os organizadores o número atual de inscritos em cada evento, atualizado em tempo real.
- Prioridade: Média
- Critério de aceite: A dashboard do organizador deve refletir o total de inscritos e vagas disponíveis em tempo real após cada inscrição, cancelamento ou confirmação.
- Observações: Este acompanhamento deve permitir visão geral do evento e apoio à tomada de decisão. Prioridade ajustada de Alta para Média (REV-12): fala do organizador é sugestiva ("Gostaríamos"), é uma melhoria de gestão sobre a RF-10, não uma trava operacional em si.

#### RF-13 - Gestão de participantes por evento
- Nome: Gestão de participantes por evento
- Descrição: Os organizadores devem poder visualizar a lista de participantes inscritos em cada evento, acompanhar status e filtrar por critérios relevantes.
- Prioridade: Alta
- Critério de aceite: Um organizador deve conseguir consultar a lista de participantes de um evento e visualizar seu status atual.
- Observações: A gestão deve incluir informações necessárias para controle administrativo do evento.

#### RF-14 - Política de cancelamento por evento
- Nome: Definição de regras de cancelamento por evento
- Descrição: O sistema deve permitir que cada evento tenha regras próprias sobre a possibilidade de cancelamento, prazos e condições aplicáveis.
- Prioridade: Alta
- Critério de aceite: Para cada evento, o organizador deve conseguir configurar se permite cancelamento, o prazo máximo e eventuais restrições.
- Observações: Nem todos os eventos podem permitir cancelamento, e essa regra deve ser configurável pelo organizador.

#### RF-15 - Tratamento de conflitos de horário
- Nome: Tratamento de conflitos de horário
- Descrição: O sistema deve evitar que o participante se inscreva em atividades que ocorram simultaneamente, caso essa restrição seja aplicável.
- Prioridade: Média
- Critério de aceite: Ao tentar cadastrar uma atividade em horário coincidente com outra já inscrita, o sistema deve bloquear a ação e exibir mensagem de conflito.
- Observações: A validação deve ocorrer antes da confirmação da inscrição. Prioridade ajustada de Alta para Média (REV-15): a política exata de conflito para eventos com múltiplas inscrições simultâneas depende de DL-07, ainda aberta — aplicando de forma consistente o mesmo critério de dependência já usado para rebaixar RF-11.

#### RF-16 - Controle de atividades por agenda
- Nome: Controle de agenda de atividades
- Descrição: O sistema deve manter a programação organizada por evento, incluindo atividades, horários, palestrantes, salas e disponibilidade de vagas.
- Prioridade: Alta
- Critério de aceite: O organizador deve ser capaz de inserir as atividades de um evento com horário, local e responsável, e visualizar a agenda montada.
- Observações: A agenda deve facilitar o planejamento do evento e a organização das inscrições.

#### RF-17 - Emissão de certificados automática ou condicionada
- Nome: Emissão de certificados automática ou condicionada
- Descrição: O sistema deve permitir que a emissão do certificado seja configurada para ocorrer automaticamente ou somente após a confirmação de presença ou outra validação estabelecida.
- Prioridade: Média
- Critério de aceite: O organizador deve poder configurar, por evento, se a emissão do certificado será automática ou condicionada a critérios específicos, como presença confirmada.
- Observações: Essa regra deve ser definida por evento ou tipo de atividade.

### 3. Módulo de Equipe Financeira

#### RF-18 - Pagamento de inscrições
- Nome: Processamento de pagamento
- Descrição: O sistema deve permitir a diferenciação entre eventos gratuitos e pagos, com registro do status do pagamento e bloqueio da inscrição até a confirmação da transação quando necessário.
- Prioridade: Média
- Critério de aceite: Para eventos gratuitos, a inscrição pode ser validada imediatamente. Para eventos pagos, a inscrição deve ficar pendente até a confirmação do pagamento **apenas quando essa exigência estiver configurada para o evento/inscrição em questão**, e não para todo evento pago de forma automática.
- Observações: A Equipe Financeira indicou a exigência de confirmação prévia para "determinadas inscrições", não para todo evento pago — a regra deve ser configurável por evento, alinhada com RN-06. O critério exato que define quais inscrições se enquadram nessa exigência é objeto de [DL-12](duvidas-e-lacunas.md#L97-L103).
- Status: Bloqueado por DL-12 (critério de exigência de confirmação prévia de pagamento) — o critério de aceite acima descreve a configurabilidade, mas não o critério em si, até essa dúvida ser respondida pelos stakeholders. Prioridade ajustada de Alta para Média (REV-15): aplicando de forma consistente o mesmo critério de dependência de dúvida aberta já usado para rebaixar RF-11.

#### RF-19 - Confirmação de pagamento antes da liberação da inscrição
- Nome: Confirmação de pagamento antes da liberação da inscrição
- Descrição: O sistema deve impedir que a inscrição seja considerada válida antes da confirmação do pagamento, quando essa regra for exigida para a inscrição/evento em questão — não como padrão universal para todo evento pago.
- Prioridade: Média
- Critério de aceite: Quando a inscrição estiver entre as "determinadas" que exigem pagamento prévio (conforme configuração do evento), ela só deve ser liberada após a confirmação do pagamento no sistema; demais inscrições pagas seguem o fluxo padrão de confirmação.
- Observações: Isso é especialmente relevante em eventos com taxa de inscrição ou vagas exclusivas. O critério que define quais inscrições se enquadram nessa exigência é objeto de [DL-12](duvidas-e-lacunas.md#L97-L103).
- Status: Bloqueado por DL-12 (critério de exigência de confirmação prévia de pagamento) — o critério de aceite acima descreve a configurabilidade, mas não o critério em si, até essa dúvida ser respondida pelos stakeholders. Prioridade ajustada de Alta para Média (REV-15): aplicando de forma consistente o mesmo critério de dependência de dúvida aberta já usado para rebaixar RF-11.

#### RF-20 - Reembolso da inscrição
- Nome: Reembolso da inscrição
- Descrição: O sistema deve suportar a definição de regras de reembolso e a execução do reembolso quando a situação do participante ou do evento enquadrar nas condições estabelecidas.
- Prioridade: Média
- Critério de aceite: Caso a regra de reembolso seja aplicável, o sistema deve registrar a solicitação, validar a elegibilidade e gerar o processo de reembolso.
- Observações: As regras devem ser configuráveis e depender do tipo de evento e da política da organização. Prioridade ajustada de Alta para Média (REV-15): critérios de elegibilidade dependem de DL-02, ainda aberta — aplicando de forma consistente o mesmo critério de dependência já usado para rebaixar RF-11.

#### RF-21 - Reserva de vaga no pagamento
- Nome: Reserva de vaga durante o processo de pagamento
- Descrição: O sistema deve definir quando a vaga será reservada: no início do pagamento ou somente após a confirmação final da transação.
- Prioridade: Média
- Critério de aceite: O sistema deve manter uma regra consistente de reserva de vaga, evitando sobreposição de inscrições para o mesmo evento.
- Observações: Essa regra deve ser consistente para evitar conflitos entre participantes e sobreposição de vagas.
- Status: Bloqueado por DL-06 (momento da reserva de vaga) — o critério de aceite acima não é verificável até essa dúvida ser respondida pelos stakeholders.

### 4. Módulo de Palestrantes

#### RF-22 - Consulta de programação para palestrantes
- Nome: Consulta da programação dos palestrantes
- Descrição: O sistema deve permitir que os palestrantes consultem a programação de suas atividades, incluindo data, horário, local, tema e participantes relacionados.
- Prioridade: Média
- Critério de aceite: Um palestrante autenticado deve conseguir visualizar sua agenda de atividades no sistema e confirmar o horário e o local de cada apresentação.
- Observações: A exibição deve respeitar os limites de informação definidos pela organização.

#### RF-23 - Consulta de participantes inscritos por atividade
- Nome: Consulta de participantes por atividade
- Descrição: Os palestrantes devem ser capazes de consultar a lista de participantes inscritos nas atividades em que atuam, respeitando as regras de privacidade e acesso.
- Prioridade: Média
- Critério de aceite: O palestrante deve conseguir visualizar somente os participantes vinculados à sua atividade e não informações de outros eventos ou públicos.
- Observações: A informação disponibilizada deve ser limitada ao necessário para a atividade do palestrante.

### 5. Módulo Gestão de Acessos

#### RF-24 - Gestão de acesso por perfil de usuário
- Nome: Gestão de acesso por perfil de usuário
- Descrição: O sistema deve distinguir os acessos de participantes, organizadores, equipe financeira e palestrantes, garantindo que cada perfil visualize apenas as informações relevantes ao seu papel.
- Prioridade: Alta
- Critério de aceite: Usuários com perfis diferentes devem receber telas, permissões e ações conforme seu papel, sem acesso indevido a dados de outros perfis.
- Observações: A autenticação e autorização devem garantir segurança e separação de responsabilidades.

## Resumo

Os requisitos funcionais foram organizados por módulo de funcionalidade e por perfil de usuário, refletindo as necessidades dos participantes, organizadores, equipe financeira e palestrantes. Essa estrutura facilita a validação do sistema por stakeholder e melhora a rastreabilidade entre necessidade de negócio, funcionalidade e critério de aceite. A numeração RF-01 a RF-24 segue a ordem de leitura por módulo (ver "Nota sobre numeração").
