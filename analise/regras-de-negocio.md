# Regras de Negócio

## Objetivo

Registrar as regras que orientam o comportamento do processo de negócio do sistema de gestão de eventos, definindo limites, políticas e validações operacionais.

## Regras de Negócio Identificadas

### RN-01 - Capacidade máxima por evento
- Nome: Limite de vagas por evento
- Descrição: Cada evento deve possuir uma quantidade máxima de vagas definida pelo organizador. Vagas confirmadas e vagas reservadas por pagamentos em andamento contam como ocupadas; novas vagas não podem ser reservadas quando a capacidade total estiver comprometida.
- Impacto: Organizador, participante, gestão de inscrições
- Exceções: Eventos com lista de espera podem aceitar inscrições em espera quando não houver vaga disponível, inclusive enquanto todas as vagas estiverem confirmadas ou reservadas por pagamentos em andamento.

### RN-02 - Lista de espera para eventos lotados
- Nome: Cadastro em lista de espera
- Descrição: Quando um evento estiver lotado e a política permitir lista de espera, o sistema deve permitir que participantes se cadastrem. Quando surgir uma vaga, a prioridade de convocação deve seguir a ordem cronológica de inscrição na lista.
- Impacto: Participante, organizador
- Exceções: A lista de espera só deve existir para eventos que permitirem essa política.

### RN-03 - Regras específicas de cancelamento por evento
- Nome: Política de cancelamento configurável por evento
- Descrição: Cada evento pode permitir ou não o cancelamento de inscrição. Quando permitido, o prazo máximo deve respeitar o limite de sete dias úteis antes da data de início do evento, definido em RN-04.
- Impacto: Participante, organizador, financeiro
- Exceções: Eventos sem cancelamento permitido não devem aceitar cancelamento pela própria interface.

### RN-04 - Prazo para cancelamento
- Nome: Prazo máximo para cancelamento
- Descrição: Se o evento permitir cancelamento, o participante pode cancelar a inscrição até sete dias úteis antes da data de início do evento. Quando faltar menos de sete dias úteis para o início, o sistema deve bloquear o cancelamento.
- Impacto: Participante, financeiro
- Exceções: Esta regra não habilita cancelamento para eventos cuja política não o permita, conforme RN-03.

### RN-05 - Reembolso condicionado
- Nome: Reembolso em casos específicos
- Descrição: Para inscrições pagas, há elegibilidade para reembolso quando a organização cancela o evento ou quando o participante apresenta atestado médico que comprove problema de saúde. A solicitação e a comprovação devem ser registradas para análise/processamento pela equipe financeira.
- Impacto: Financeiro, participante, organizador
- Exceções: Eventos gratuitos não geram reembolso de valor de inscrição. O valor a reembolsar (integral ou parcial) e o prazo de processamento não estão definidos nesta regra e não devem ser presumidos.

### RN-06 - Confirmar pagamento antes da liberação da inscrição
- Nome: Pagamento obrigatório para confirmação
- Descrição: Quando a confirmação prévia de pagamento for exigida, a inscrição deve ser liberada somente após a confirmação do pagamento pela instituição financeira.
- Impacto: Financeiro, participante, organizador
- Exceções: Eventos gratuitos podem dispensar confirmação de pagamento.
- Status: Parcialmente bloqueado por DL-12 — a instituição financeira foi definida como fonte de confirmação, mas o critério que define quais inscrições exigem confirmação prévia ainda está pendente.

### RN-07 - Vaga reservada no pagamento
- Nome: Reserva de vaga durante processamento do pagamento
- Descrição: O sistema deve reservar a vaga quando o participante iniciar o pagamento. Se o boleto ou Pix vencer sem confirmação, o sistema deve liberar a vaga para outro participante.
- Impacto: Participante, organizador, financeiro
- Exceções: A vaga liberada deve poder ser ocupada por nova inscrição ou destinada ao próximo participante da lista de espera, conforme RN-02/RN-24. O tratamento de outras falhas de pagamento não foi definido.

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
- Descrição: O sistema deve impedir a inscrição e a reserva de vaga em uma atividade com horário conflitante com outra inscrição em andamento/pendente ou confirmada do mesmo participante.
- Impacto: Participante, organizador
- Exceções: A tentativa bloqueada deve gerar um alerta explicativo ao participante e uma notificação por e-mail, conforme RN-22.

### RN-11 - Inscrição em vários workshops do mesmo dia
- Nome: Múltiplas inscrições em workshops do mesmo dia
- Descrição: O participante pode se inscrever em vários workshops do mesmo dia, desde que não haja conflito de horário ou outra restrição definida pelo evento.
- Impacto: Participante, organizador
- Exceções: Se houver sobreposição de horários, a segunda inscrição deve ser bloqueada.

### RN-12 - Emissão de comprovante após inscrição
- Nome: Geração do comprovante de inscrição
- Descrição: Após a inscrição ser confirmada, o sistema deve gerar e enviar o comprovante de inscrição ao e-mail do participante.
- Impacto: Participante, organização
- Exceções: Caso a inscrição esteja pendente ou em lista de espera, o comprovante pode ser diferente ou não ser emitido dependendo da regra do evento.

### RN-13 - Emissão de certificado após evento
- Nome: Emissão de certificado
- Descrição: Após a conclusão do evento, o sistema deve emitir automaticamente e enviar por e-mail o certificado para cada participante cuja frequência registrada seja igual ou superior a 75%. Em eventos online, a presença deve ser identificada por dados do Zoom ou do Google Meet; em eventos presenciais, deve ser identificada por lista de chamada.
- Impacto: Participante, organizador
- Exceções: Participantes com frequência registrada inferior a 75% não recebem certificado. A base de cálculo, o procedimento de registro presencial e o mecanismo de obtenção dos dados das plataformas online ainda precisam ser especificados.

### RN-14 - Conteúdo mínimo do certificado
- Nome: Conteúdo do certificado
- Descrição: O certificado deve conter elementos mínimos definidos pela organização, como nome do participante, evento, carga horária, data e assinatura/validação do evento.
- Impacto: Participante, organizador
- Exceções: Certificados de workshops ou eventos internos podem ter conteúdo específico.

### RN-15 - Acesso do palestrante à programação
- Nome: Consulta da programação por palestrante
- Descrição: Os palestrantes devem ter acesso apenas à programação e às informações relevantes de suas próprias atividades. Entre os dados do evento que podem consultar estão data do evento, descrição, palestrante e valor do evento.
- Impacto: Palestrante, organizador
- Exceções: Informações de outras atividades não relacionadas devem permanecer indisponíveis. Para os participantes de suas atividades, o palestrante pode visualizar somente nome e sexo; CPF e RG devem permanecer ocultos.

### RN-16 - Acesso do palestrante aos participantes
- Nome: Visualização de participantes por palestrante
- Descrição: O palestrante pode consultar os nomes e o sexo dos participantes inscritos em suas atividades. CPF, RG e outros dados pessoais não especificados para esse perfil não devem ser exibidos.
- Impacto: Palestrante, participante, organizador
- Exceções: O acesso é limitado às atividades vinculadas ao palestrante; CPF e RG nunca são apresentados nessa consulta, conforme a decisão registrada em DL-08.

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
- Descrição: Cada usuário deve ter acesso somente às funcionalidades e dados designados ao seu perfil. Participantes podem consultar todos os eventos e se inscrever; organizadores podem administrar eventos; palestrantes podem consultar os eventos que irão ministrar e nome/sexo dos participantes relacionados; a equipe financeira pode consultar pagamentos/status, tratar divergências, analisar/processar reembolsos e consultar histórico financeiro/relatórios.
- Impacto: Sistema em geral
- Exceções: O palestrante só pode consultar participantes vinculados às suas atividades e visualizar nome e sexo; CPF e RG devem permanecer ocultos. A equipe financeira não pode substituir ou contradizer a confirmação oficial de pagamento recebida da instituição financeira. Acesso a módulos administrativos deve ser restrito e auditado.

### RN-20 - Registro de histórico e auditoria
- Nome: Auditoria de operações
- Descrição: Ações relevantes do sistema, como alteração de status, confirmação de pagamento, cancelamento e geração de certificado, devem ser registradas para rastreio e auditoria.
- Impacto: Organizadores, financeira, suporte
- Exceções: Registros acessíveis apenas a usuários autorizados.

### RN-21 - Validação obrigatória antes da confirmação
- Nome: Validação de regras antes da confirmação
- Descrição: Antes de reservar uma vaga ou confirmar uma inscrição, o sistema deve verificar regras como capacidade, conflito de horário, pagamento e política do evento. A validação de conflito deve considerar inscrições em andamento/pendentes e confirmadas do participante.
- Impacto: Participante, organizador, financeiro
- Exceções: Se houver conflito de horário, a reserva e a confirmação devem ser bloqueadas; o participante deve receber alerta na interface e notificação por e-mail, conforme RN-10/RN-22.

### RN-22 - Notificações após eventos relevantes
- Nome: Notificações do sistema
- Descrição: O sistema deve enviar por e-mail notificações ao participante em casos de inscrição confirmada, cancelamento, lista de espera, pagamento e emissão de certificado.
- Impacto: Participante, organização
- Exceções: Comprovantes de inscrição devem ser enviados conforme RN-12; certificados são enviados conforme RN-13.

### RN-23 - Frequência mínima para emissão de certificado
- Nome: Frequência mínima para certificação
- Descrição: A emissão automática do certificado exige frequência registrada igual ou superior a 75% no evento. Para eventos online, a presença é identificada por dados do Zoom ou do Google Meet; para eventos presenciais, por lista de chamada.
- Impacto: Participante, organizador
- Exceções: Participantes abaixo do limite não recebem certificado. A base de cálculo e os mecanismos de captura/importação dos registros devem ser definidos antes da implementação.

### RN-24 - Gerenciamento de vagas e fila de espera
- Nome: Ordenação da lista de espera
- Descrição: Quando uma vaga se torna disponível, o participante com inscrição mais antiga na lista de espera deve ter prioridade para convocação; os demais seguem a mesma ordem cronológica de inscrição.
- Impacto: Organizador, participante
- Exceções: A lista de espera só se aplica quando habilitada para o evento, conforme RN-02.

## Resumo

As regras de negócio levantadas cobrem o ciclo principal de operação do sistema: gestão de eventos, inscrição, vagas, cancelamento, lista de espera, pagamento, reembolso, emissão de certificado, programação e acesso por perfil. Elas definem a lógica operacional que orienta a implementação e a validação do sistema.
