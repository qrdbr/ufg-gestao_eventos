# Casos de Uso

## 1. Objetivo

Descrever os principais comportamentos do sistema de gestão de eventos a partir dos objetivos dos participantes, organizadores, equipe financeira e palestrantes. Este documento utiliza os requisitos funcionais (RF), as regras de negócio (RN) e as dúvidas e lacunas (DL) identificados na análise.

## 2. Atores

| Ator | Responsabilidade no sistema |
|---|---|
| Participante | Consultar eventos, realizar e acompanhar inscrições, cancelar participação e obter comprovantes/certificados. |
| Organizador | Criar eventos, configurar regras, administrar agenda, vagas e participantes. |
| Equipe financeira | Consultar e atualizar pagamentos e processar reembolsos conforme as políticas definidas. |
| Palestrante | Consultar a própria programação e os participantes de suas atividades, dentro dos limites de acesso. |
| Sistema de pagamento | Serviço externo opcional para processar transações de eventos pagos. |
| Serviço de notificações | Serviço responsável pelo envio de notificações e certificados ao participante por e-mail. |

A equipe de TI é responsável pela construção e manutenção da solução, mas não é considerada ator funcional dos casos de uso de negócio.

## 3. Modelo conceitual

- Um **evento** possui uma ou mais **atividades**.
- Uma atividade pode ser um workshop, palestra ou outro tipo de programação.
- Uma inscrição vincula um participante a um evento e, quando aplicável, às atividades escolhidas.
- As categorias de evento seguem uma política comum de inscrição, pagamento, cancelamento e lista de espera; configurações específicas por evento continuam possíveis nos termos das regras de negócio. Eventos gratuitos e pagos seguem os ramos aplicáveis da política comum.

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
2. O sistema verifica vagas, duplicidade, conflito com inscrições em andamento/pendentes ou confirmadas do participante e demais regras do evento.
3. O participante confirma seus dados e a inscrição.
4. Antes de confirmar ou reservar a vaga, o sistema revalida capacidade e conflito de horário.
5. Para evento gratuito ou inscrição sem pagamento prévio, o sistema confirma a inscrição.
6. Para inscrição que exige pagamento prévio, o sistema encaminha o participante ao pagamento e reserva a vaga assim que o pagamento é iniciado.
7. O sistema registra o status adequado, atualiza as vagas e disponibiliza a confirmação ou o status pendente.

**Fluxos alternativos:**

- Se não houver vaga e houver lista de espera habilitada, o participante pode entrar na lista de espera.
- Se houver conflito de horário, o sistema bloqueia a atividade conflitante e informa o motivo.
- Se houver conflito com outra inscrição em andamento/pendente ou confirmada, o sistema não reserva a vaga nem confirma a nova inscrição, exibe alerta explicativo e envia notificação por e-mail.
- Se o evento estiver lotado e não aceitar lista de espera, o sistema impede a inscrição.
- Se o pagamento falhar, o sistema mantém o status coerente e informa a falha, sem duplicar a inscrição.
- Se um boleto ou Pix vencer sem confirmação, o sistema libera a vaga para nova inscrição ou para convocação do próximo participante da lista de espera.

**Pós-condições:** inscrição criada com status confirmada, pendente ou em lista de espera; vagas e histórico atualizados.

**Regras e requisitos:** RN-01, RN-02, RN-06, RN-07, RN-08, RN-09, RN-10, RN-11, RN-21; RF-02, RF-03, RF-10, RF-11, RF-15, RF-18, RF-19, RF-21.

**Dependência em aberto:** DL-12. A reserva da vaga no início do pagamento e sua liberação após vencimento de boleto/Pix foram definidas em DL-06/RN-07; o bloqueio de conflito de horário foi definido em DL-07/RN-10.
**Dependências parcialmente abertas:** DL-12 — a instituição financeira confirma o pagamento, mas ainda falta definir quais inscrições exigem confirmação prévia. A reserva da vaga no início do pagamento e sua liberação após vencimento de boleto/Pix foram definidas em DL-06/RN-07; o bloqueio de conflito de horário foi definido em DL-07/RN-10.

### UC-03 - Acompanhar inscrição e obter comprovante

**Objetivo:** permitir que o participante consulte a situação da inscrição e acesse seu comprovante.

**Atores:** participante; serviço de notificações por e-mail.

**Pré-condições:** participante autenticado e com inscrição registrada.

**Fluxo principal:**

1. O participante acessa "Minhas inscrições".
2. O sistema apresenta evento, atividades, data e status da inscrição.
3. O participante seleciona uma inscrição.
4. Após confirmação da inscrição, o sistema envia o comprovante ao e-mail do participante.
5. Quando houver mudança relevante, o sistema envia notificação ao e-mail do participante.

**Fluxos alternativos:**

- Para inscrição pendente, o sistema informa a pendência e a próxima ação esperada.
- Para inscrição em lista de espera, o sistema apresenta a posição ou o status disponível conforme a regra definida.
- Para inscrições pendentes ou em lista de espera, o comprovante pode ser diferente ou não ser enviado, conforme a regra do evento.

**Regras e requisitos:** RN-09, RN-12, RN-22; RF-04, RF-06, RF-08.

**Regra definida:** comprovantes de inscrições confirmadas, notificações e certificados são enviados por e-mail, conforme DL-05/RN-12/RN-13.

### UC-04 - Cancelar inscrição e solicitar reembolso

**Objetivo:** permitir o cancelamento dentro das condições do evento e iniciar o reembolso quando aplicável.

**Atores:** participante; equipe financeira.

**Pré-condições:** participante autenticado; inscrição existente; evento com cancelamento permitido.

**Fluxo principal:**

1. O participante acessa uma inscrição confirmada.
2. O sistema verifica se o evento permite cancelamento e se faltam pelo menos sete dias úteis para sua data de início.
3. O participante confirma o cancelamento.
4. O sistema altera o status para cancelada, libera a vaga quando aplicável e registra a operação.
5. O sistema verifica se existe direito a reembolso.
6. Se houver direito, o sistema registra o motivo e, em caso de problema de saúde, o atestado médico apresentado, para análise/processamento financeiro.
7. O sistema informa o resultado ao participante.

**Fluxos alternativos:**

- Se o prazo tiver expirado, o sistema bloqueia o cancelamento e informa a regra aplicável.
- Se o evento não permitir cancelamento, o sistema bloqueia a ação.
- Se não houver direito a reembolso, o cancelamento é registrado sem solicitação financeira.
- Se a organização cancelar o evento, o sistema registra as inscrições pagas elegíveis para reembolso e encaminha os casos à equipe financeira.
- Se o participante solicitar reembolso por problema de saúde, o sistema registra a solicitação para análise mediante apresentação de atestado médico. Essa condição de reembolso não define, por si só, uma exceção ao prazo de cancelamento da RN-04; a regra de cancelamento continua sendo aplicada separadamente.

**Regras e requisitos:** RN-03, RN-04, RN-05, RN-09, RN-20, RN-21; RF-05, RF-13, RF-14, RF-20.

O prazo de cancelamento foi definido em DL-01 e está registrado em RN-04. Os critérios de elegibilidade para reembolso estão definidos em DL-02/RN-05; valor e prazo de processamento do reembolso não foram especificados. O atestado contém dado de saúde e deve ter acesso restrito, conforme validação pendente de DL-09 e DL-11.

### UC-05 - Emitir certificado

**Objetivo:** disponibilizar o certificado após o atendimento às condições do evento.

**Atores:** participante; sistema; serviço de e-mail.

**Pré-condições:** evento concluído; presença registrada conforme a modalidade — dados do Zoom ou Google Meet para online, lista de chamada para presencial — e método de apuração definido.

**Fluxo principal:**

1. O evento é concluído.
2. O sistema obtém os registros de presença conforme a modalidade e calcula a frequência segundo a base definida.
3. Se a frequência for igual ou superior a 75%, o sistema gera automaticamente o certificado com os dados definidos.
4. O sistema envia o certificado ao e-mail do participante.
5. O participante acessa o certificado recebido.
6. O sistema registra a emissão no histórico.

**Fluxos alternativos:**

- Se a frequência registrada for inferior a 75%, o sistema não emite o certificado.
- Se os dados da plataforma online ou os registros da lista presencial não estiverem disponíveis, ou se faltar definição sobre a base de cálculo, o sistema não deve presumir elegibilidade para certificado.

**Regras e requisitos:** RN-13, RN-14, RN-20, RN-23; RF-07, RF-17.

**Regra definida:** emissão automática após a conclusão do evento para frequência mínima de 75%; Zoom/Google Meet para eventos online e lista de chamada para presenciais, conforme DL-04/RN-13/RN-23. **Detalhes operacionais pendentes:** base de cálculo e mecanismos de registro/obtenção dos dados.

### UC-06 - Cadastrar e configurar evento

**Objetivo:** permitir ao organizador estruturar um evento e suas regras operacionais.

**Atores:** organizador.

**Pré-condições:** organizador autenticado e autorizado.

**Fluxo principal:**

1. O organizador acessa o cadastro de eventos.
2. O sistema solicita nome, descrição, data, local, tipo, capacidade e valor.
3. O organizador define atividades, horários, salas e palestrantes.
4. O organizador configura cancelamento, reembolso, lista de espera e pagamento; a emissão de certificados segue automaticamente RN-13/RN-23.
5. O organizador salva o evento como rascunho ou ativa sua publicação.
6. O sistema valida os dados e disponibiliza o evento conforme o status escolhido.

**Fluxos alternativos:**

- Se houver dados obrigatórios ausentes, o sistema impede a ativação e identifica os ajustes necessários. A validação de sobreposição entre atividades configuradas pelo organizador não é definida por DL-07.
- Se a política de alguma regra ainda não estiver definida, o organizador mantém o evento em configuração sem fechar a decisão automaticamente.

**Regras e requisitos:** RN-03, RN-05, RN-07, RN-08, RN-13, RN-17, RN-23, RN-24; RF-09, RF-14, RF-16, RF-17.

**Política uniforme:** as categorias de evento seguem o mesmo modelo de inscrição, pagamento, cancelamento e lista de espera, conforme DL-10. A reserva no início do pagamento e a liberação após vencimento de boleto/Pix estão definidas em DL-06/RN-07. O método/base de cálculo da frequência para certificados ainda precisa ser especificado. DL-07 define o bloqueio de conflitos na inscrição do participante, mas não determina se o organizador pode cadastrar atividades com horários sobrepostos.

### UC-07 - Controlar vagas e lista de espera

**Objetivo:** acompanhar a ocupação e administrar a entrada de participantes quando surgirem vagas.

**Atores:** organizador; participante; serviço de notificações por e-mail.

**Pré-condições:** evento cadastrado com capacidade e política de lista de espera.

**Fluxo principal:**

1. O organizador acessa o painel do evento.
2. O sistema apresenta vagas totais, ocupadas, reservadas por pagamentos em andamento, disponíveis e participantes em espera.
3. Uma inscrição, cancelamento, confirmação ou vencimento de boleto/Pix altera os totais e a disponibilidade das vagas.
4. Quando surge vaga, o sistema identifica o participante mais antigo na lista de espera, seguindo a ordem cronológica de inscrição.
5. O sistema atualiza o status e envia por e-mail a notificação de convocação ao participante.

**Fluxos alternativos:**

- Se não houver lista de espera, novas inscrições são bloqueadas ao atingir a capacidade.
- Os demais participantes permanecem na lista na ordem cronológica de inscrição após a convocação do próximo.

**Regras e requisitos:** RN-01, RN-02, RN-18, RN-24; RF-10, RF-11, RF-12.

**Regra de ordenação:** a convocação segue a ordem cronológica de inscrição, conforme RN-24 e DL-03 (resolvida). A notificação de convocação deve ser enviada por e-mail, conforme RN-22/DL-05.

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
2. O sistema apresenta evento, participante, valor, status, histórico financeiro e relatórios disponíveis ao perfil.
3. O sistema registra a confirmação ou recusa do pagamento recebida da instituição financeira.
4. O sistema atualiza o status da inscrição conforme a confirmação da instituição e registra a operação.
5. A equipe analisa a elegibilidade, autoriza/processa o reembolso aplicável e pode tratar divergências sem alterar o retorno oficial da instituição financeira.
6. O sistema atualiza o status para reembolsada quando a operação for concluída.

**Fluxos alternativos:**

- Em caso de falha ou recusa, o sistema mantém o pagamento como recusado ou pendente e não confirma indevidamente a inscrição.
- Se a inscrição não se enquadrar no critério de pagamento prévio, o sistema segue a política configurada.

**Regras e requisitos:** RN-05, RN-06, RN-07, RN-08, RN-09, RN-20, RN-21; RF-18, RF-19, RF-20, RF-21.

**Dependência parcialmente aberta:** DL-12 — a instituição financeira é a fonte de confirmação, mas ainda falta definir quais inscrições exigem confirmação prévia. As permissões financeiras estão definidas em DL-11/RN-19. A reserva no início do pagamento e a liberação da vaga após vencimento de boleto/Pix foram definidas em DL-06/RN-07. Os critérios de elegibilidade do reembolso foram definidos em DL-02/RN-05; valor e prazo de processamento não foram especificados.

### UC-10 - Consultar programação e participantes da atividade

**Objetivo:** permitir que o palestrante consulte apenas as informações necessárias para sua atuação.

**Atores:** palestrante.

**Pré-condições:** palestrante autenticado e vinculado a uma atividade.

**Fluxo principal:**

1. O palestrante acessa sua área.
2. O sistema apresenta os eventos e atividades que o palestrante irá ministrar e os dados do evento permitidos: data, descrição, palestrante e valor.
3. O palestrante seleciona uma atividade.
4. O sistema apresenta somente nome e sexo dos participantes inscritos naquela atividade, ocultando CPF, RG e demais dados pessoais não autorizados.
5. O sistema oculta dados não necessários ou não autorizados.

**Fluxos alternativos:**

- Se o palestrante não estiver vinculado à atividade, o sistema bloqueia a consulta.
- O sistema não apresenta CPF, RG nem dados de participantes de outras atividades ao palestrante.

**Regras e requisitos:** RN-15, RN-16, RN-19; RF-22, RF-23, RF-24.

**Regra definida:** DL-08/RN-16 autorizam exibir somente nome e sexo dos participantes vinculados à atividade; CPF e RG permanecem ocultos. As permissões financeiras estão definidas em DL-11/RN-19. Os critérios operacionais de segurança e qualidade continuam parcialmente pendentes em DL-09.

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

As permissões dos perfis, inclusive da equipe financeira, estão definidas em DL-11/RN-19. Os critérios de segurança e qualidade continuam sujeitos aos detalhes pendentes em DL-09.

## 6. Requisitos não funcionais transversais

Todos os casos de uso devem considerar os requisitos não funcionais RNF-01 a RNF-20, especialmente:

- resposta adequada em consultas e inscrições;
- disponibilidade e recuperação diante de falhas;
- autenticação, autorização e proteção de dados;
- consistência em concorrência de inscrições e pagamentos;
- acessibilidade, usabilidade e compatibilidade com dispositivos;
- registro de auditoria e mensagens claras.

As referências de segurança, privacidade, acessibilidade e qualidade estão definidas em DL-09 (OWASP ASVS, LGPD/ANPD, WCAG 2.2 AA e ISO/IEC 25010). Permanecem pendentes o nível de verificação do ASVS, metas e condições de medição de desempenho/disponibilidade, políticas operacionais de dados e a aplicabilidade de PCI DSS após a escolha do fluxo de pagamento. Os números existentes nos RNFs são propostas, não metas aprovadas.

## 7. Rastreabilidade resumida

| Grupo de casos de uso | Requisitos cobertos |
|---|---|
| Participante | RF-01 a RF-08 |
| Organizador | RF-09 a RF-17 |
| Financeiro | RF-18 a RF-21 |
| Palestrante | RF-22 e RF-23 |
| Acessos | RF-24 |
