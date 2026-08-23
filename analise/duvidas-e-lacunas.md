# Dúvidas e Lacunas

## Objetivo

Registrar ambiguidades, inconsistências e pontos pendentes que precisam ser esclarecidos junto aos stakeholders antes da especificação final do sistema.

## Lista de Dúvidas e Lacunas

### DL-01 - Prazo de cancelamento da inscrição
- Questão: Até quando o participante pode cancelar sua inscrição?
- Contexto: Durante as entrevistas, ficou indicado que o cancelamento deve ser permitido em alguns casos, mas não foi definido o prazo máximo.
- Impacto: Afeta regras de reembolso, status da inscrição e validação da operação.
- Responsável / origem: Participantes e organizadores
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 1 da lista de Observações gerais)

### DL-02 - Critérios de reembolso
- Questão: Em quais situações haverá reembolso?
- Contexto: Houve indicação de que alguns eventos têm direito a reembolso e outros não, mas não foi definida a política exata.
- Impacto: Afeta o fluxo financeiro, a comunicação com o participante e a regra de negócio da inscrição.
- Responsável / origem: Equipe financeira e organizadores
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 2 da lista de Observações gerais)

### DL-03 - Funcionamento da lista de espera
- Questão: Como a lista de espera será operacionalizada?
- Contexto: Foi informado que a lista de espera deve existir em eventos lotados, mas não foi definido se a ordem de chamada é por data de inscrição, por critérios de prioridade ou por outra regra.
- Impacto: Define a ordem de preenchimento de vagas e a experiência do participante.
- Responsável / origem: Organizadores e participantes
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 3 da lista de Observações gerais)

### DL-04 - Emissão de certificados e confirmação de presença
- Questão: Os certificados serão emitidos automaticamente ou dependerão da confirmação de presença? Essa confirmação será obrigatória para todos os eventos ou variável por evento?
- Contexto: Foi solicitado que os certificados possam ser emitidos após o evento, mas a regra específica ainda não está definida, incluindo se a exigência de confirmação de presença será padrão para todos os eventos ou configurável individualmente por evento.
- Impacto: Afeta a lógica de negócio, a geração automatizada dos certificados e a experiência dos participantes.
- Responsável / origem: Organizadores e participantes
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 4 da lista de Observações gerais)

### DL-05 - Canal de envio de comprovantes e notificações
- Questão: Como serão enviados comprovantes de inscrição e demais notificações?
- Contexto: Houve menção a comprovantes e notificações, porém não foi definido se serão enviados por e-mail, mensagem ou portal do participante.
- Impacto: Afeta comunicação do sistema, experiência do usuário e requisitos de integração.
- Responsável / origem: Organizadores e equipe financeira
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 5 da lista de Observações gerais)

### DL-06 - Momento da reserva de vaga
- Questão: A vaga será reservada no início do pagamento ou somente após confirmação da transação?
- Contexto: Foi levantado este ponto como pendente, pois isso influencia a gestão de vagas e o controle de concorrência.
- Impacto: Afeta a disponibilidade de vagas e a consistência do processo de inscrição.
- Responsável / origem: Organizadores e equipe financeira
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 6 da lista de Observações gerais)

### DL-07 - Tratamento de inscrições com horários conflitantes
- Questão: Como o sistema deve tratar tentativas de inscrição em atividades com horários conflitantes?
- Contexto: A regra de prevenção de conflito foi citada, mas a política exata ainda não foi definida para eventos que permitam múltiplas inscrições simultâneas.
- Impacto: Afeta validação da inscrição, experiência do usuário e consistência da programação.
- Responsável / origem: Organizadores e participantes
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 7 da lista de Observações gerais)

### DL-08 - Informação acessível aos palestrantes
- Questão: Quais informações dos participantes poderão ser visualizadas pelos palestrantes, e qual é o conjunto mínimo de dados necessário para essa consulta?
- Contexto: O palestrante precisa consultar participantes de suas atividades, mas não ficaram definidos quais dados serão exibidos, quais serão ocultados por privacidade, nem qual é a informação mínima necessária para atender a essa necessidade.
- Impacto: Afeta a privacidade dos dados, a interface e a regra de acesso por perfil.
- Responsável / origem: Palestrantes e organização
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 8 da lista de Observações gerais)

### DL-09 - Requisitos de segurança e privacidade
- Questão: Quais são as exigências de segurança, desempenho, disponibilidade, acessibilidade e privacidade do sistema?
- Contexto: Os entrevistados apontaram a necessidade do sistema, mas não definiram critérios específicos de segurança, tempo de resposta, acessibilidade e proteção dos dados.
- Impacto: Afeta requisitos não funcionais, arquitetura e conformidade.
- Responsável / origem: Equipe de TI, organizadores, stakeholders
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (item 9 da lista de Observações gerais)

### DL-10 - Matriz de variação de regras por tipo/categoria de evento
- Questão: O sistema deve aplicar uma política única de inscrição, pagamento, cancelamento, lista de espera e certificado para todos os eventos, ou essas regras variam conforme o tipo de evento (congresso, workshop, evento corporativo) e conforme ele ser gratuito ou pago?
- Contexto: Foi informado que alguns eventos são gratuitos e outros exigem pagamento, e que a organização realiza diferentes tipos de evento (congressos, workshops, eventos corporativos), mas não foi estabelecida uma política operacional única nem detalhada a variação de regras por categoria — abrange pagamento, confirmação, reserva de vagas, cancelamento, lista de espera e certificado.
- Impacto: Afeta cadastro de eventos, regras de pagamento, confirmação, reserva de vagas, cancelamento, lista de espera, certificado e comunicação com o participante.
- Responsável / origem: Equipe financeira e organizadores
- Status: Aberta
- Origem do levantamento: Lacuna inferida pela análise (não consta na lista de Observações gerais nem em fala literal de entrevista)

### DL-11 - Perfil e permissão dos usuários
- Questão: Quais ações cada perfil de usuário pode realizar no sistema?
- Contexto: O sistema prevê diferentes perfis, mas ainda não foi definido o conjunto exato de permissões para participantes, organizadores, financeiros e palestrantes.
- Impacto: Afeta o módulo de gestão de acessos e a segurança do sistema.
- Responsável / origem: Organizadores e equipe de TI
- Status: Aberta
- Origem do levantamento: Lacuna inferida pela análise (não consta na lista de Observações gerais nem em fala literal de entrevista)

### DL-12 - Critério para exigência de confirmação prévia de pagamento
- Questão: Qual critério define quais inscrições ou eventos pagos exigem confirmação do pagamento antes da liberação da inscrição?
- Contexto: A Equipe Financeira mencionou em entrevista que a confirmação é necessária antes de liberar "determinadas inscrições", não todo evento pago, mas o critério que define quais inscrições se enquadram nessa exigência não foi especificado.
- Impacto: Afeta RF-18, RF-19 e RN-06, além do fluxo de liberação de inscrições e a experiência do participante em eventos pagos.
- Responsável / origem: Equipe financeira
- Status: Aberta
- Origem do levantamento: Observação direta da entrevista (fala literal da Equipe Financeira, não constava na lista de Observações gerais)

## Resumo

Os pontos levantados demonstram que o sistema ainda precisa de esclarecimento em áreas críticas, como regras de cancelamento, reembolso, lista de espera, emissão de certificados, tratamento de vagas, dados de palestrantes, critérios de confirmação de pagamento e requisitos de segurança e privacidade. Esses itens devem ser discutidos com os stakeholders antes da finalização da especificação funcional e técnica.
