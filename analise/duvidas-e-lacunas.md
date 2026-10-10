# Dúvidas e Lacunas

## Objetivo

Registrar ambiguidades, inconsistências e pontos pendentes que precisam ser esclarecidos junto aos stakeholders antes da especificação final do sistema.

## Status consolidado

| Situação | Dúvidas | Definições registradas |
|---|---|---|
| **Resolvidas** | DL-01 a DL-08, DL-10 e DL-11 | Prazo de cancelamento; critérios de reembolso; ordem da lista de espera; emissão de certificados e frequência mínima; envio de comprovantes, certificados e notificações por e-mail; reserva/liberação de vagas no pagamento; bloqueio de inscrições conflitantes; dados de evento e participantes visíveis ao palestrante; política comum para as categorias de evento; permissões básicas dos perfis, inclusive da equipe financeira. |
| **Parcialmente resolvidas** | DL-09 e DL-12 | Referências de qualidade adotadas, mas metas operacionais e alguns detalhes de segurança/privacidade pendentes; instituição financeira confirma pagamentos, mas falta definir quais inscrições exigem confirmação prévia. |
| **Abertas** | — | Nenhuma dúvida está totalmente aberta; há detalhes pendentes nas dúvidas parcialmente resolvidas. |

**Nota:** “Resolvida” indica que a decisão de negócio principal foi registrada. Detalhes necessários à implementação continuam explicitados nas respectivas dúvidas, como o cálculo e a obtenção dos dados de frequência em DL-04 e a identificação do vencimento do pagamento em DL-06.

### Definições pendentes para fechar as dúvidas parcialmente resolvidas

- **DL-09 — Critérios verificáveis restantes:** definir o nível de verificação do OWASP ASVS, metas e condições de teste para desempenho/disponibilidade, políticas operacionais de privacidade (como retenção/exclusão) e se PCI DSS se aplica após escolha do fluxo/provedor de pagamento. WCAG 2.2 nível AA foi adotado como alvo de acessibilidade. Os valores sugestivos dos RNFs não são metas aprovadas.
- **DL-12 — Aplicabilidade da confirmação prévia:** a confirmação da instituição financeira deve ser exigida para todos os pagamentos, para certos tipos de evento/inscrição ou segundo outro critério objetivo? A instituição financeira já está definida como fonte da confirmação.

## Lista de Dúvidas e Lacunas

### DL-01 - Prazo de cancelamento da inscrição
- Questão: Até quando o participante pode cancelar sua inscrição?
- Contexto: Durante as entrevistas, ficou indicado que o cancelamento deve ser permitido em alguns casos, mas não foi definido o prazo máximo. A definição recebida estabelece o limite em sete dias úteis antes do evento.
- Resolução: O participante pode cancelar a inscrição até sete dias úteis antes da data de início do evento, desde que a política do evento permita cancelamento. Quando faltar menos de sete dias úteis para o evento, o cancelamento não será permitido pelo sistema.
- Impacto: Afeta regras de reembolso, status da inscrição e validação da operação.
- Responsável / origem: Participantes e organizadores
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 1 da lista de Observações gerais)

### DL-02 - Critérios de reembolso
- Questão: Em quais situações haverá reembolso?
- Contexto: Foi definido que o reembolso é aplicável em caso de cancelamento do evento pela organização ou de problema de saúde do participante comprovado por atestado médico.
- Resolução: São elegíveis a reembolso as inscrições pagas quando a organização cancelar o evento ou quando o participante apresentar atestado médico que comprove problema de saúde. O sistema deve registrar o motivo e a comprovação para análise/processamento financeiro. O valor (integral ou parcial), o prazo de processamento e o tratamento de eventos gratuitos não foram especificados nesta definição e não devem ser presumidos. Como o atestado contém dado de saúde, seu tratamento deve observar proteção e acesso restrito, com requisitos a validar em DL-09 e DL-11.
- Impacto: Afeta o fluxo financeiro, a comunicação com o participante e a regra de negócio da inscrição.
- Responsável / origem: Equipe financeira e organizadores
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 2 da lista de Observações gerais)

### DL-03 - Funcionamento da lista de espera
- Questão: Como a lista de espera será operacionalizada?
- Contexto: Foi informado que a lista de espera deve existir em eventos lotados. A prioridade de convocação foi definida pela ordem de inscrição.
- Resolução: Quando uma vaga ficar disponível, o participante com inscrição mais antiga na lista de espera deve ter prioridade para convocação; os demais seguem na mesma ordem cronológica de inscrição.
- Impacto: Define a ordem de preenchimento de vagas e a experiência do participante.
- Responsável / origem: Organizadores e participantes
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 3 da lista de Observações gerais)

### DL-04 - Emissão de certificados e confirmação de presença
- Questão: Os certificados serão emitidos automaticamente ou dependerão da confirmação de presença? Essa confirmação será obrigatória para todos os eventos ou variável por evento?
- Contexto: Foi solicitado que os certificados possam ser emitidos após o evento. Foi definido que a emissão será automática para participantes com frequência mínima de 75%.
- Resolução: Após a conclusão do evento, o sistema deve emitir automaticamente certificado para cada participante cuja frequência registrada seja igual ou superior a 75%. Em eventos online, a presença deve ser identificada por dados do Zoom ou do Google Meet; em eventos presenciais, deve ser identificada por lista de chamada. Participantes abaixo do limite não recebem o certificado.
- Detalhes a especificar antes da implementação: a base de cálculo da frequência (evento completo ou atividades), o procedimento de registro da lista presencial e o mecanismo de obtenção dos dados do Zoom/Google Meet (por exemplo, integração ou importação) não foram definidos; não devem ser presumidos.
- Impacto: Afeta a lógica de negócio, a geração automatizada dos certificados e a experiência dos participantes.
- Responsável / origem: Organizadores e participantes
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 4 da lista de Observações gerais)

### DL-05 - Canal de envio de comprovantes e notificações
- Questão: Como serão enviados comprovantes de inscrição e demais notificações?
- Contexto: Foi definido que certificados, notificações do sistema e comprovantes de inscrição serão enviados por e-mail.
- Resolução: Após a confirmação da inscrição, o comprovante deve ser enviado ao endereço de e-mail do participante. Certificados e notificações do sistema também são enviados por e-mail, conforme as regras relacionadas.
- Impacto: Afeta comunicação do sistema, experiência do usuário e requisitos de integração.
- Responsável / origem: Organizadores e equipe financeira
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 5 da lista de Observações gerais)

### DL-06 - Momento da reserva de vaga
- Questão: A vaga será reservada no início do pagamento ou somente após confirmação da transação?
- Contexto: A vaga será reservada quando o participante iniciar o pagamento. Se um boleto ou Pix vencer sem confirmação, a vaga será liberada para outro participante.
- Resolução: Reservar a vaga no início do processo de pagamento. Se o pagamento por boleto ou Pix não for confirmado até o vencimento, liberar a vaga para nova inscrição ou convocação da lista de espera, respeitando a ordem definida em RN-24.
- Detalhe a especificar antes da implementação: o sistema deve receber ou determinar a data/hora de vencimento do boleto ou Pix; o tratamento de outras falhas de pagamento não foi definido nesta decisão.
- Impacto: Afeta a disponibilidade de vagas e a consistência do processo de inscrição.
- Responsável / origem: Organizadores e equipe financeira
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 6 da lista de Observações gerais)

### DL-07 - Tratamento de inscrições com horários conflitantes
- Questão: Como o sistema deve tratar tentativas de inscrição em atividades com horários conflitantes?
- Contexto: Foi definido que, se o participante tentar se inscrever em um curso que conflita com outra inscrição em andamento ou já efetivada, a reserva da nova vaga deve ser impedida e o participante alertado.
- Resolução: Antes de confirmar a inscrição ou reservar vaga, o sistema deve verificar se o participante possui inscrição em andamento/pendente ou confirmada em outra atividade com sobreposição de horário. Havendo conflito, não deve criar a nova reserva e deve exibir um alerta explicativo ao participante e enviar a notificação por e-mail.
- Impacto: Afeta validação da inscrição, experiência do usuário e consistência da programação.
- Responsável / origem: Organizadores e participantes
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 7 da lista de Observações gerais)

### DL-08 - Informação acessível aos palestrantes
- Questão: Quais informações dos participantes poderão ser visualizadas pelos palestrantes, e qual é o conjunto mínimo de dados necessário para essa consulta?
- Contexto: Foram definidos os dados do evento e os dados mínimos de participantes que o palestrante poderá visualizar nas atividades vinculadas a ele.
- Resolução: O palestrante pode visualizar data, descrição, palestrante e valor do evento, além do nome e sexo dos participantes inscritos em suas atividades. CPF e RG, e outros dados pessoais não especificados para esse perfil, não devem ser exibidos ao palestrante.
- Impacto: Afeta a privacidade dos dados, a interface e a regra de acesso por perfil.
- Responsável / origem: Palestrantes e organização
- Status: Resolvida
- Origem do levantamento: Observação direta da entrevista (item 8 da lista de Observações gerais)

### DL-09 - Requisitos de segurança e privacidade
- Questão: Quais são as exigências de segurança, desempenho, disponibilidade, acessibilidade e privacidade do sistema?
- Contexto: Foi definido que a equipe seguirá boas práticas reconhecidas. Para orientar sua aplicação, foram adotadas referências de segurança de aplicação, privacidade, acessibilidade e qualidade de software.
- Resolução parcial: Usar OWASP ASVS como referência verificável para segurança da aplicação; observar LGPD e orientações da ANPD para privacidade; adotar WCAG 2.2 nível AA como alvo de acessibilidade; usar ISO/IEC 25010 para organizar atributos de qualidade. ISO/IEC 27001 pode servir como referência de gestão de segurança, sem compromisso de certificação. Indicadores/objetivos de serviço (SLI/SLO) para desempenho e disponibilidade devem ser definidos a partir do perfil de carga e da operação esperada, não presumidos. PCI DSS só será aplicável se o sistema armazenar, processar ou transmitir dados de cartão; a aplicabilidade depende da solução de pagamento escolhida.
- Detalhes a especificar antes da implementação: nível/escopo de verificação do OWASP ASVS; metas e cenários de medição de desempenho e disponibilidade; regras de retenção, exclusão e acesso a dados; método de verificação de WCAG 2.2 AA; aplicabilidade de PCI DSS após definição da integração financeira.
- Impacto: Afeta requisitos não funcionais, arquitetura e conformidade.
- Responsável / origem: Equipe de TI, organizadores, stakeholders
- Status: Parcialmente resolvida (referências definidas; metas e critérios operacionais pendentes)
- Origem do levantamento: Observação direta da entrevista (item 9 da lista de Observações gerais)

### DL-10 - Matriz de variação de regras por tipo/categoria de evento
- Questão: O sistema deve aplicar uma política única de inscrição, pagamento, cancelamento e lista de espera para todos os eventos, ou essas regras variam conforme o tipo de evento (congresso, workshop, evento corporativo) e conforme ele ser gratuito ou pago?
- Contexto: A organização realiza diferentes tipos de evento (congressos, workshops, eventos corporativos), gratuitos e pagos. Foi definida uma política única de inscrição, pagamento, cancelamento e lista de espera, sem regras distintas por tipo/categoria de evento.
- Resolução: Aplicar os mesmos critérios e fluxos de inscrição, pagamento, cancelamento e lista de espera a todas as categorias. Eventos gratuitos e pagos seguem os ramos aplicáveis da política comum, conforme RN-08. Esta decisão não remove as configurações por evento já previstas em RN-02/RN-03; elas devem usar o mesmo modelo para todas as categorias.
- Impacto: Afeta cadastro de eventos, regras de pagamento, confirmação, cancelamento, lista de espera e comunicação com o participante.
- Responsável / origem: Equipe financeira e organizadores
- Status: Resolvida
- Origem do levantamento: Lacuna inferida pela análise (não consta na lista de Observações gerais nem em fala literal de entrevista)

### DL-11 - Perfil e permissão dos usuários
- Questão: Quais ações cada perfil de usuário pode realizar no sistema?
- Contexto: Foram definidas as permissões básicas para participantes, organizadores, palestrantes e equipe financeira.
- Resolução: Participantes podem visualizar todos os eventos e se inscrever; organizadores podem administrar eventos; palestrantes podem visualizar os eventos que irão ministrar e consultar somente nome e sexo dos participantes dessas atividades (DL-08); a equipe financeira pode consultar pagamentos e status, tratar divergências sem substituir a confirmação oficial da instituição financeira, analisar e processar reembolsos e consultar histórico financeiro e relatórios.
- Impacto: Afeta o módulo de gestão de acessos e a segurança do sistema.
- Responsável / origem: Organizadores e equipe de TI
- Status: Resolvida
- Origem do levantamento: Lacuna inferida pela análise (não consta na lista de Observações gerais nem em fala literal de entrevista)

### DL-12 - Critério para exigência de confirmação prévia de pagamento
- Questão: Qual critério define quais inscrições ou eventos pagos exigem confirmação do pagamento antes da liberação da inscrição?
- Contexto: A Equipe Financeira mencionou em entrevista que a confirmação é necessária antes de liberar "determinadas inscrições", não todo evento pago. Foi definido que a confirmação do pagamento deve vir da instituição financeira, mas ainda não foi definido quais inscrições se enquadram nessa exigência.
- Resolução parcial: Quando a confirmação prévia for exigida, a inscrição só deve ser liberada após a confirmação do pagamento pela instituição financeira. A instituição financeira é a fonte de confirmação; permanece pendente o critério para determinar quais inscrições exigem essa confirmação.
- Impacto: Afeta RF-18, RF-19 e RN-06, além do fluxo de liberação de inscrições e a experiência do participante em eventos pagos.
- Responsável / origem: Equipe financeira
- Status: Parcialmente resolvida (critério de aplicabilidade pendente)
- Origem do levantamento: Observação direta da entrevista (fala literal da Equipe Financeira, não constava na lista de Observações gerais)

## Resumo

O status atual é: **10 dúvidas resolvidas (DL-01 a DL-08, DL-10 e DL-11), 2 parcialmente resolvidas (DL-09 e DL-12) e nenhuma totalmente aberta**. Os critérios operacionais restantes de qualidade e aplicabilidade da confirmação prévia de pagamento permanecem descritos nos respectivos itens.
