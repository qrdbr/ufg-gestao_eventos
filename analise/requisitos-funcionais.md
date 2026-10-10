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
- Critério de aceite: Se um workshop conflitar com outra inscrição em andamento/pendente ou confirmada do participante, o sistema deve bloquear a nova inscrição e informar a incompatibilidade.
- Observações: Deve existir validação para impedir que o participante se inscreva em atividades que ocorram ao mesmo tempo. Prioridade ajustada de Alta para Média (REV-12): refinamento da RF-02, baseado em fala sugestiva do participante ("gostaria de me inscrever"), não bloqueia o fluxo essencial de inscrição.

#### RF-04 - Comprovante de inscrição
- Nome: Emissão de comprovante de inscrição
- Descrição: Após a confirmação da inscrição, o sistema deve gerar e disponibilizar um comprovante para o participante, com dados do evento, data da inscrição e status da participação.
- Prioridade: Média
- Critério de aceite: Após uma inscrição confirmada, o sistema deve gerar o comprovante com os dados do evento, data da inscrição e status da participação, e enviá-lo ao e-mail do participante.
- Observações: O envio por e-mail foi definido em DL-05. Prioridade ajustada de Alta para Média (REV-12): fala do participante é sugestiva ("seria interessante"), item de conveniência que não bloqueia a confirmação da inscrição em si.

#### RF-05 - Cancelamento de inscrição
- Nome: Cancelamento de inscrição
- Descrição: O sistema deve permitir que o participante cancele uma inscrição, sem a necessidade de contato direto com a organização, desde que a política do evento permita essa ação.
- Prioridade: Alta
- Critério de aceite: Quando o evento permitir cancelamento e faltarem pelo menos sete dias úteis para sua data de início, o participante deve conseguir cancelar a inscrição e receber confirmação do sistema. Com menos de sete dias úteis restantes, o sistema deve bloquear a ação e informar o prazo aplicável.
- Observações: O prazo foi definido em DL-01 e registrado em RN-04. A elegibilidade para reembolso é tratada separadamente em RF-20 e RN-05.

#### RF-06 - Acompanhamento do status da inscrição
- Nome: Acompanhamento do status da inscrição
- Descrição: O participante deve visualizar o status de sua inscrição, incluindo pendente, confirmada, cancelada, em lista de espera e reembolsada, quando aplicável.
- Prioridade: Média
- Critério de aceite: A interface do participante deve exibir, de forma clara, o status atual da inscrição e a data da última alteração.
- Observações: O status deve permitir clareza sobre a situação atual da participação. Prioridade ajustada de Alta para Média (REV-12): não há fala direta de stakeholder pedindo esse acompanhamento; é funcionalidade de suporte a RF-02/RF-05, não citada como necessidade explícita.

#### RF-07 - Emissão de certificado
- Nome: Emissão de certificado
- Descrição: O sistema deve emitir automaticamente certificado após a conclusão do evento para cada participante com frequência registrada igual ou superior a 75%.
- Prioridade: Alta
- Critério de aceite: Após a conclusão do evento, participantes com frequência registrada de pelo menos 75% devem ter o certificado gerado e enviado por e-mail; participantes abaixo desse limite não devem recebê-lo.
- Observações: A política e as fontes de presença foram definidas em DL-04 e registradas em RN-13/RN-23: Zoom ou Google Meet para eventos online; lista de chamada para presenciais. A base de cálculo, o procedimento de registro presencial e o mecanismo de obtenção dos dados das plataformas ainda precisam ser especificados antes da implementação.

#### RF-08 - Notificações e comprovantes
- Nome: Envio de comprovantes e notificações
- Descrição: O sistema deve enviar por e-mail comprovantes de inscrições confirmadas e notificações de confirmação, cancelamento, lista de espera, pagamento, lembretes e demais eventos relevantes ao participante.
- Prioridade: Média
- Critério de aceite: Sempre que ocorrer uma mudança relevante no processo de inscrição, o sistema deve enviar a notificação ao endereço de e-mail do participante.
- Observações: O envio de comprovantes, certificados e notificações por e-mail foi definido em DL-05. A prioridade é Média por se tratar de suporte aos fluxos principais.

### 2. Módulo de Organizadores

#### RF-09 - Cadastro e gestão de eventos
- Nome: Cadastro e gestão de eventos
- Descrição: Os organizadores devem poder criar, editar, ativar e desativar eventos, definindo informações como nome, descrição, data, local, capacidade, tipo de evento, regras de cancelamento e forma de pagamento.
- Prioridade: Alta
- Critério de aceite: Um organizador autenticado deve conseguir cadastrar um novo evento e alterar os dados básicos sem intervenção manual externa.
- Observações: O cadastro deve ser centralizado para facilitar a gestão do portfólio de eventos.

#### RF-10 - Controle automático de vagas
- Nome: Controle automático de vagas
- Descrição: O sistema deve controlar automaticamente a quantidade de vagas disponíveis de cada evento, considerando participantes confirmados e vagas reservadas por pagamentos em andamento, e impedir novas reservas quando a capacidade estiver comprometida.
- Prioridade: Alta
- Critério de aceite: Quando todas as vagas estiverem confirmadas ou reservadas por pagamentos em andamento, o sistema deve impedir novas reservas e exibir a situação de lotado; vagas reservadas devem voltar a ficar disponíveis após o vencimento do boleto ou Pix sem confirmação.
- Observações: A regra deve considerar vagas totais e vagas remanescentes por atividade.

#### RF-11 - Lista de espera
- Nome: Gestão de lista de espera
- Descrição: Quando um evento atingir a capacidade máxima, o sistema deve permitir a criação de uma lista de espera para participantes interessados em ocupar vagas disponíveis posteriormente.
- Prioridade: Média
- Critério de aceite: Quando houver lotação e a lista de espera estiver habilitada, o sistema deve aceitar inscrições em espera e, ao surgir vaga, priorizar para convocação o participante que se inscreveu primeiro na lista; a notificação de convocação deve ser enviada por e-mail.
- Observações: Os participantes devem ser convocados em ordem cronológica de inscrição, conforme DL-03 e RN-24. A prioridade permanece Média porque a solicitação original do organizador foi sugestiva ("seria interessante").

#### RF-12 - Acompanhamento de inscritos em tempo real
- Nome: Acompanhamento de inscritos em tempo real
- Descrição: O sistema deve disponibilizar para os organizadores o número atual de inscritos e de vagas reservadas por pagamentos em andamento em cada evento, atualizado em tempo real.
- Prioridade: Média
- Critério de aceite: A dashboard do organizador deve refletir inscrições confirmadas, vagas reservadas por pagamentos em andamento e vagas disponíveis após inscrições, cancelamentos, confirmações e vencimentos de boleto/Pix.
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
- Descrição: O sistema deve impedir que o participante reserve vaga em atividade com horário conflitante com outra inscrição sua em andamento/pendente ou confirmada.
- Prioridade: Alta
- Critério de aceite: Antes de reservar vaga ou confirmar a inscrição, o sistema deve detectar a sobreposição, impedir a nova reserva/inscrição, exibir alerta explicativo e enviar notificação por e-mail ao participante.
- Observações: A política foi definida em DL-07 e registrada em RN-10/RN-21. A validação deve ocorrer também no momento da reserva para evitar que inscrições iniciadas concorrentemente contornem o bloqueio.

#### RF-16 - Controle de atividades por agenda
- Nome: Controle de agenda de atividades
- Descrição: O sistema deve manter a programação organizada por evento, incluindo atividades, horários, palestrantes, salas e disponibilidade de vagas.
- Prioridade: Alta
- Critério de aceite: O organizador deve ser capaz de inserir as atividades de um evento com horário, local e responsável, e visualizar a agenda montada.
- Observações: A agenda deve facilitar o planejamento do evento e a organização das inscrições.

#### RF-17 - Processamento automático da emissão de certificados
- Nome: Processamento automático da emissão de certificados
- Descrição: O sistema deve processar automaticamente a emissão dos certificados após a conclusão do evento para participantes que atendam à frequência mínima de 75%.
- Prioridade: Média
- Critério de aceite: Ao concluir o evento, o sistema deve verificar a frequência registrada e gerar o certificado para participantes com frequência igual ou superior a 75%, sem exigir liberação manual do organizador.
- Observações: A emissão automática, o limite de 75% e as fontes de presença por modalidade foram definidos em DL-04. A base de cálculo, o procedimento para lista presencial e o mecanismo para obter dados do Zoom/Google Meet ainda devem ser especificados.

### 3. Módulo de Equipe Financeira

#### RF-18 - Pagamento de inscrições
- Nome: Processamento de pagamento
- Descrição: O sistema deve permitir a diferenciação entre eventos gratuitos e pagos, registrar o status do pagamento e, quando a confirmação prévia for exigida, liberar a inscrição somente após confirmação pela instituição financeira.
- Prioridade: Média
- Critério de aceite: Para eventos gratuitos, a inscrição pode ser validada imediatamente. Para eventos pagos, a inscrição deve ficar pendente até a confirmação do pagamento **apenas quando essa exigência estiver configurada para o evento/inscrição em questão**, e não para todo evento pago de forma automática.
- Observações: A instituição financeira é a fonte de confirmação quando o pagamento prévio for exigido. Ainda não foi definido quais inscrições se enquadram nessa exigência; esse critério é objeto de [DL-12](duvidas-e-lacunas.md#L123-L130).
- Status: Parcialmente bloqueado por DL-12 — fonte de confirmação definida; critério de aplicabilidade pendente. Prioridade ajustada de Alta para Média (REV-15): aplicando de forma consistente o mesmo critério de dependência de dúvida aberta já usado para rebaixar RF-11.

#### RF-19 - Confirmação de pagamento antes da liberação da inscrição
- Nome: Confirmação de pagamento antes da liberação da inscrição
- Descrição: O sistema deve impedir que a inscrição seja considerada válida antes da confirmação do pagamento, quando essa regra for exigida para a inscrição/evento em questão — não como padrão universal para todo evento pago.
- Prioridade: Média
- Critério de aceite: Quando a inscrição estiver entre as que exigem pagamento prévio, ela só deve ser liberada após a instituição financeira confirmar o pagamento; o critério que identifica essas inscrições permanece pendente.
- Observações: A confirmação da instituição financeira é a fonte de verdade do pagamento. O critério que define quais inscrições exigem essa confirmação é objeto de [DL-12](duvidas-e-lacunas.md#L123-L130).
- Status: Parcialmente bloqueado por DL-12 — fonte de confirmação definida; critério de aplicabilidade pendente. Prioridade ajustada de Alta para Média (REV-15): aplicando de forma consistente o mesmo critério de dependência de dúvida aberta já usado para rebaixar RF-11.

#### RF-20 - Reembolso da inscrição
- Nome: Reembolso da inscrição
- Descrição: O sistema deve suportar a definição de regras de reembolso e a execução do reembolso quando a situação do participante ou do evento enquadrar nas condições estabelecidas.
- Prioridade: Alta
- Critério de aceite: Para uma inscrição paga, o sistema deve permitir registrar solicitação de reembolso quando a organização cancelar o evento ou quando o participante apresentar atestado médico que comprove problema de saúde; a solicitação e o motivo devem ficar disponíveis para análise e processamento pela equipe financeira. Eventos gratuitos não devem gerar reembolso de valor de inscrição.
- Observações: Os critérios de elegibilidade foram definidos em DL-02 e registrados em RN-05. O valor (integral ou parcial) e o prazo de processamento não foram definidos e não devem ser presumidos. O atestado contém dado de saúde; seu tratamento e acesso devem respeitar os requisitos de privacidade e permissões, ainda pendentes de validação em DL-09 e DL-11.

#### RF-21 - Reserva de vaga no pagamento
- Nome: Reserva de vaga durante o processo de pagamento
- Descrição: O sistema deve reservar a vaga no início do processo de pagamento e liberá-la quando um boleto ou Pix vencer sem confirmação.
- Prioridade: Alta
- Critério de aceite: Ao iniciar o pagamento, a vaga deve deixar de estar disponível para outras inscrições. Se o boleto ou Pix vencer sem confirmação, a vaga deve voltar a ficar disponível ou ser destinada ao próximo participante da lista de espera, respeitando RN-24.
- Observações: A regra foi definida em DL-06 e registrada em RN-07. O sistema depende da informação de vencimento do meio de pagamento; o tratamento de outras falhas de pagamento não foi especificado.

### 4. Módulo de Palestrantes

#### RF-22 - Consulta de programação para palestrantes
- Nome: Consulta da programação dos palestrantes
- Descrição: O sistema deve permitir que os palestrantes consultem a programação de suas atividades e os dados do evento definidos para esse perfil: data do evento, descrição, palestrante e valor do evento.
- Prioridade: Média
- Critério de aceite: Um palestrante autenticado deve conseguir visualizar sua agenda de atividades no sistema e confirmar o horário e o local de cada apresentação.
- Observações: A exibição deve respeitar RN-15. Para participantes das próprias atividades, somente nome e sexo são visíveis; CPF, RG e outros dados pessoais não especificados ficam ocultos, conforme DL-08/RN-16.

#### RF-23 - Consulta de participantes inscritos por atividade
- Nome: Consulta de participantes por atividade
- Descrição: Os palestrantes devem ser capazes de consultar a lista de participantes inscritos nas atividades em que atuam, respeitando as regras de privacidade e acesso.
- Prioridade: Média
- Critério de aceite: O palestrante deve conseguir visualizar somente nome e sexo dos participantes vinculados às suas atividades; CPF, RG e outros dados pessoais não especificados devem permanecer ocultos, assim como participantes de outros eventos ou atividades.
- Observações: O conjunto mínimo de dados visível foi definido em DL-08 e registrado em RN-16.

### 5. Módulo Gestão de Acessos

#### RF-24 - Gestão de acesso por perfil de usuário
- Nome: Gestão de acesso por perfil de usuário
- Descrição: O sistema deve distinguir os acessos por perfil: participantes podem visualizar todos os eventos e se inscrever; organizadores podem administrar eventos; palestrantes podem visualizar eventos que irão ministrar e nome/sexo dos participantes dessas atividades; equipe financeira pode consultar pagamentos/status, tratar divergências, analisar/processar reembolsos e consultar histórico financeiro/relatórios.
- Prioridade: Alta
- Critério de aceite: Cada perfil consegue executar somente as ações definidas para ele; participante consulta eventos e se inscreve, organizador administra eventos, palestrante consulta seus eventos e nome/sexo dos participantes vinculados, e equipe financeira consulta pagamentos/status, trata divergências, processa reembolsos e consulta histórico/relatórios. A equipe financeira não pode sobrescrever a confirmação oficial da instituição financeira.
- Observações: As permissões por perfil foram definidas em DL-11/RN-19; os dados visíveis aos palestrantes seguem DL-08/RN-16.

## Resumo

Os requisitos funcionais foram organizados por módulo de funcionalidade e por perfil de usuário, refletindo as necessidades dos participantes, organizadores, equipe financeira e palestrantes. Essa estrutura facilita a validação do sistema por stakeholder e melhora a rastreabilidade entre necessidade de negócio, funcionalidade e critério de aceite. A numeração RF-01 a RF-24 segue a ordem de leitura por módulo (ver "Nota sobre numeração").
