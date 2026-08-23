# Regras de Negócio

## Objetivo

Registrar as regras que orientam o comportamento do processo de negócio do sistema de gestão de eventos, definindo limites, políticas e validações operacionais.

## Regras de Negócio Identificadas

### RN-01 - Capacidade máxima por evento
- Nome: Limite de vagas por evento
- Descrição: Cada evento deve possuir uma quantidade máxima de vagas definida pelo organizador. A inscrição deve ser bloqueada quando o número de participantes confirmados atingir esse limite.
- Impacto: Organizador, participante, gestão de inscrições
- Exceções: Eventos com lista de espera podem aceitar inscrições em espera mesmo quando a capacidade for atingida.

### RN-02 - Lista de espera para eventos lotados
- Nome: Cadastro em lista de espera
- Descrição: Quando um evento estiver lotado, o sistema deve permitir que participantes se cadastrem em lista de espera e sejam chamados conforme surgirem vagas.
- Impacto: Participante, organizador
- Exceções: A lista de espera só deve existir para eventos que permitirem essa política.

### RN-03 - Regras específicas de cancelamento por evento
- Nome: Política de cancelamento configurável por evento
- Descrição: Cada evento pode permitir ou não o cancelamento de inscrição, além de estabelecer prazos e condições para essa ação.
- Impacto: Participante, organizador, financeiro
- Exceções: Eventos sem cancelamento permitido não devem aceitar cancelamento pela própria interface.

### RN-04 - Prazo para cancelamento
- Nome: Prazo máximo para cancelamento
- Descrição: A inscrição deve poder ser cancelada somente dentro do prazo estabelecido para aquele evento, se houver permissão para cancelamento.
- Impacto: Participante, financeiro
- Exceções: Caso o evento defina prazo ilimitado, essa regra pode ser adaptada pela organização.

### RN-05 - Reembolso condicionado
- Nome: Reembolso em casos específicos
- Descrição: O reembolso deve ocorrer apenas quando a situação do participante ou do evento estiver dentro das condições de reembolso definidas pela organização.
- Impacto: Financeiro, participante, organizador
- Exceções: Eventos gratuitos ou sem política de reembolso não devem gerar reembolso.

### RN-06 - Confirmar pagamento antes da liberação da inscrição
- Nome: Pagamento obrigatório para confirmação
- Descrição: Para eventos pagos, a inscrição deve ser liberada somente após a confirmação do pagamento, quando essa regra for exigida.
- Impacto: Financeiro, participante, organizador
- Exceções: Eventos gratuitos podem dispensar confirmação de pagamento.
- Status: Bloqueado por DL-12 (critério de exigência de confirmação prévia de pagamento) — a regra acima descreve a condicionalidade ("quando exigida"), mas não o critério que define quando ela se aplica, até essa dúvida ser respondida pelos stakeholders.

### RN-07 - Vaga reservada no pagamento
- Nome: Reserva de vaga durante processamento do pagamento
- Descrição: A vaga deve ser reservada de acordo com a política definida pelo evento para evitar sobreposição de inscrições durante o processo de pagamento.
- Impacto: Participante, organizador, financeiro
- Exceções: O comportamento pode variar conforme a regra do evento; em alguns casos a reserva ocorre após confirmação do pagamento.
- Status: Bloqueado por DL-06 (momento da reserva de vaga) — a regra acima descreve a variação possível, mas não define a política padrão até essa dúvida ser respondida pelos stakeholders.

### RN-08 - Eventos gratuitos e pagos
- Nome: Distinção entre eventos gratuitos e pagos
- Descrição: O sistema deve tratar eventos gratuitos e pagos de forma distinta, com regras diferentes para inscrição, pagamento e confirmação.
- Impacto: Financeiro, participante, organizador
- Exceções: Eventos gratuitos não exigem processamento tributário ou cobrança de taxa.

### RN-09 - Registro do status da inscrição
- Nome: Status da inscrição
- Descrição: Cada inscrição deve possuir um status explícito, como confirmada, pendente, cancelada, em lista de espera ou reembolsada.
- Impacto: Participante, organizador, financeiro
- Exceções: Status pode variar conforme regras do evento e do processo de pagamento.

### RN-10 - Impedimento de inscrições conflitantes
- Nome: Conflito de horário entre atividades
- Descrição: O sistema deve impedir que um participante se inscreva em duas atividades que ocorram simultaneamente, quando essa regra for aplicável.
- Impacto: Participante, organizador
- Exceções: O evento pode permitir múltiplas inscrições em atividades simultâneas se isso for explicitamente configurado.

### RN-11 - Inscrição em vários workshops do mesmo dia
- Nome: Múltiplas inscrições em workshops do mesmo dia
- Descrição: O participante pode se inscrever em vários workshops do mesmo dia, desde que não haja conflito de horário ou outra restrição definida pelo evento.
- Impacto: Participante, organizador
- Exceções: Se houver sobreposição de horários, a segunda inscrição deve ser bloqueada.

### RN-12 - Emissão de comprovante após inscrição
- Nome: Geração do comprovante de inscrição
- Descrição: Após a inscrição ser confirmada, o sistema deve gerar e disponibilizar um comprovante de inscrição para o participante.
- Impacto: Participante, organização
- Exceções: Caso a inscrição esteja pendente ou em lista de espera, o comprovante pode ser diferente ou não ser emitido dependendo da regra do evento.

### RN-13 - Emissão de certificado após evento
- Nome: Emissão de certificado
- Descrição: O certificado deve ser emitido após a conclusão do evento ou quando a condição estabelecida pelo evento for satisfeita, como presença confirmada.
- Impacto: Participante, organizador
- Exceções: O evento pode exigir validação de presença antes da emissão do certificado.

### RN-14 - Conteúdo mínimo do certificado
- Nome: Conteúdo do certificado
- Descrição: O certificado deve conter elementos mínimos definidos pela organização, como nome do participante, evento, carga horária, data e assinatura/validação do evento.
- Impacto: Participante, organizador
- Exceções: Certificados de workshops ou eventos internos podem ter conteúdo específico.

### RN-15 - Acesso do palestrante à programação
- Nome: Consulta da programação por palestrante
- Descrição: Os palestrantes devem ter acesso apenas à programação e às informações relevantes de suas próprias atividades.
- Impacto: Palestrante, organizador
- Exceções: Informações de outras atividades ou participantes não relacionadas devem permanecer indisponíveis.

### RN-16 - Acesso do palestrante aos participantes
- Nome: Visualização de participantes por palestrante
- Descrição: O palestrante pode consultar os participantes de sua atividade somente conforme as regras de privacidade e consentimento da organização.
- Impacto: Palestrante, participante, organizador
- Exceções: Informações pessoais sensíveis devem ser ocultadas ou limitadas.

### RN-17 - Controle de agenda por evento
- Nome: Agenda de atividades
- Descrição: Cada evento deve conter uma agenda com atividades, horários, locações, responsáveis e vagas associadas, sendo administrada pelo organizador.
- Impacto: Organizador, participante, palestrante
- Exceções: A estrutura da agenda pode variar conforme tipo de evento.

### RN-18 - Atualização em tempo real de inscrições
- Nome: Monitoramento de inscrições em tempo real
- Descrição: As informações de participantes, vagas e status devem ser atualizadas em tempo real para permitir acompanhamento do organizador.
- Impacto: Organizador, participante
- Exceções: A atualização pode ter pequenas latências em condições específicas de rede ou processamento.

### RN-19 - Acesso por perfil de usuário
- Nome: Permissão de acesso por perfil
- Descrição: Cada usuário deve ter acesso somente às funcionalidades e dados designados ao seu perfil, como participante, organizador, financeiro ou palestrante.
- Impacto: Sistema em geral
- Exceções: Acesso a módulos administrativos deve ser restrito e auditado.

### RN-20 - Registro de histórico e auditoria
- Nome: Auditoria de operações
- Descrição: Ações relevantes do sistema, como alteração de status, confirmação de pagamento, cancelamento e geração de certificado, devem ser registradas para rastreio e auditoria.
- Impacto: Organizadores, financeira, suporte
- Exceções: Registros acessíveis apenas a usuários autorizados.

### RN-21 - Validação obrigatória antes da confirmação
- Nome: Validação de regras antes da confirmação
- Descrição: Antes de confirmar uma inscrição, o sistema deve verificar regras como capacidade, conflito de horário, pagamento e política do evento.
- Impacto: Participante, organizador, financeiro
- Exceções: Em casos de sistema em manutenção ou indisponibilidade, a regra pode ser aplicada após recuperação.

### RN-22 - Notificações após eventos relevantes
- Nome: Notificações do sistema
- Descrição: O sistema deve enviar notificações para o participante em casos de inscrição confirmada, cancelamento, lista de espera, pagamento e emissão de certificado.
- Impacto: Participante, organização
- Exceções: O canal de entrega pode variar conforme a política da organização.

### RN-23 - Política de confirmação de presença
- Nome: Confirmação de presença
- Descrição: O evento pode exigir confirmação de presença para eventualmente liberar certificado ou concluir a participação do participante.
- Impacto: Participante, organizador
- Exceções: Eventos sem presença obrigatória podem emitir certificados automaticamente.

### RN-24 - Gerenciamento de vagas e fila de espera
- Nome: Ordenação da lista de espera
- Descrição: Quando uma vaga se torna disponível, o participante da lista de espera deve ser convocado conforme a ordem de cadastro ou outra regra definida pela organização.
- Impacto: Organizador, participante
- Exceções: Política de prioridade pode variar por evento.

## Resumo

As regras de negócio levantadas cobrem o ciclo principal de operação do sistema: gestão de eventos, inscrição, vagas, cancelamento, lista de espera, pagamento, reembolso, emissão de certificado, programação e acesso por perfil. Elas definem a lógica operacional que orienta a implementação e a validação do sistema.
