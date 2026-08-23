# Requisitos Não Funcionais

## Objetivo

Registrar restrições, critérios de qualidade e requisitos de operação do sistema de gestão de eventos, considerando desempenho, segurança, disponibilidade, usabilidade, privacidade e confiabilidade.

## Requisitos Não Funcionais Identificados

### RNF-01 - Tempo de resposta da interface
- Nome: Tempo de resposta da interface
- Descrição: A interface do sistema deve responder de forma ágil às ações de navegação, busca, inscrição e consulta de dados, mesmo com aumento no número de usuários.
- Critério de aceitação: A página inicial e os processos de inscrição devem carregar em até 3 segundos em condições normais de uso, em rede estável.
- Prioridade: Alta
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-02 - Disponibilidade do sistema
- Nome: Disponibilidade do sistema
- Descrição: O sistema deve estar disponível para uso durante os períodos de operação do evento, minimizando indisponibilidades por manutenção ou falhas técnicas.
- Critério de aceitação: O sistema deve atingir disponibilidade de no mínimo 99% em operação normal, com exceção de janelas de manutenção previamente agendadas.
- Prioridade: Alta
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-03 - Segurança de autenticação e autorização
- Nome: Segurança de autenticação e autorização
- Descrição: O sistema deve garantir que apenas usuários autorizados acessem áreas e informações conforme o perfil de cada stakeholder.
- Critério de aceitação: Usuários sem permissão não devem visualizar nem alterar dados de outros perfis, e a autenticação deve exigir credenciais válidas.
- Prioridade: Alta
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-04 - Proteção de dados pessoais
- Nome: Proteção de dados pessoais
- Descrição: Os dados dos participantes devem ser armazenados e processados conforme boas práticas de privacidade, limitando o acesso apenas ao necessário para cada processo.
- Critério de aceitação: Informações sensíveis devem estar protegidas por controle de acesso e não devem ser exibidas a usuários sem autorização.
- Prioridade: Alta
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-05 - Conformidade com privacidade e LGPD
- Nome: Conformidade com privacidade e LGPD
- Descrição: O sistema deve respeitar regras de privacidade e proteção de dados, especialmente no armazenamento e uso de informações pessoais de participantes.
- Critério de aceitação: O sistema deve permitir consentimento, uso mínimo necessário e controle do titular sobre seus dados, conforme a legislação aplicável.
- Prioridade: Alta
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-06 - Integridade dos dados de inscrições e pagamentos
- Nome: Integridade dos dados de inscrições e pagamentos
- Descrição: As informações de inscrição, pagamento, cancelamento e status devem ser mantidas com consistência e segurança, evitando inconsistências no sistema.
- Critério de aceitação: Não deve haver duplicidade de inscrições, inconsistência de status de pagamento ou perda de registros em operações normais.
- Prioridade: Alta

### RNF-07 - Confiabilidade e tolerância a falhas
- Nome: Confiabilidade e tolerância a falhas
- Descrição: O sistema deve manter operação estável mesmo na ocorrência de falhas pontuais, evitando perda de dados e inconsistências no processo de inscrição.
- Critério de aceitação: Em caso de falha temporária, o sistema deve recuperar a operação sem perda de transações relevantes e com alertas adequados para os administradores.
- Prioridade: Alta

### RNF-08 - Escalabilidade
- Nome: Escalabilidade
- Descrição: O sistema deve suportar crescimento no número de eventos, participantes, inscrições e consultas sem degradação significativa do desempenho.
- Critério de aceitação: O sistema deve manter desempenho aceitável com aumento proporcional do volume de usuários e cadastros durante campanhas de inscrições intensas.
- Prioridade: Média

### RNF-09 - Usabilidade
- Nome: Usabilidade da interface
- Descrição: O sistema deve ser fácil de usar para participantes, organizadores, equipe financeira e palestrantes, evitando processos complexos ou ambíguos.
- Critério de aceitação: Usuários com pouca experiência devem conseguir realizar inscrição, consulta e cancelamento de forma intuitiva sem treinamento extensivo.
- Prioridade: Alta

### RNF-10 - Acessibilidade
- Nome: Acessibilidade
- Descrição: A solução deve ser acessível a usuários com diferentes necessidades, incluindo navegação por teclado, contraste adequado, leitura de conteúdo e uso de tecnologias assistivas.
- Critério de aceitação: A interface deve atender, ao menos em nível básico, diretrizes de acessibilidade web e permitir navegação por leitores de tela e teclado.
- Prioridade: Média
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-11 - Compatibilidade com navegadores e dispositivos
- Nome: Compatibilidade com navegadores e dispositivos
- Descrição: O sistema deve funcionar corretamente em navegadores modernos e em diferentes dispositivos, como desktop, tablet e smartphones.
- Critério de aceitação: As funcionalidades principais do sistema devem ser utilizáveis em navegadores atuais e em dispositivos móveis com layout responsivo.
- Prioridade: Média

### RNF-12 - Manutenibilidade
- Nome: Manutenibilidade do sistema
- Descrição: O sistema deve ser desenvolvido de forma organizada e modular, permitindo ajustes, correções e evoluções sem grande esforço.
- Critério de aceitação: Mudanças de regra de negócio, como cancelamento, vagas e emissão de certificados, devem ser implementáveis com impacto mínimo em outras áreas.
- Prioridade: Média

### RNF-13 - Observabilidade e monitoramento
- Nome: Observabilidade e monitoramento
- Descrição: O sistema deve permitir acompanhamento de falhas, erros, transações relevantes e uso das funcionalidades, favorecendo manutenção e suporte.
- Critério de aceitação: Os administradores devem conseguir identificar falhas de negócio e erros técnicos por meio de logs, métricas ou alertas.
- Prioridade: Média

### RNF-14 - Backup e recuperação
- Nome: Backup e recuperação
- Descrição: O sistema deve realizar backups periódicos e permitir recuperação dos dados em caso de falhas, corrupção ou perda acidental.
- Critério de aceitação: Dados críticos do sistema devem ser restauráveis em um período definido e sem perda relevante de informações.
- Prioridade: Alta

### RNF-15 - Performance em períodos de pico
- Nome: Performance em períodos de pico
- Descrição: O sistema deve manter desempenho aceitável durante períodos de alta demanda, como abertura de inscrições ou final de prazo de inscrição.
- Critério de aceitação: Mesmo com grande volume de acessos simultâneos, o sistema deve continuar a processar inscrições e consultas com tempos aceitáveis.
- Prioridade: Alta
- **Observação:** Critério sugestivo porque não foram especificados itens como segurança, tempo de resposta, acessibilidade e proteção de dados.

### RNF-16 - Consistência de comunicação e notificações
- Nome: Consistência de comunicação e notificações
- Descrição: As notificações do sistema devem ser entregues de forma confiável e com conteúdo claro, de modo a reduzir dúvidas sobre inscrições e pagamentos.
- Critério de aceitação: Mensagens de confirmação, cancelamento, lembrete e reembolso devem ser entregues sem atraso excessivo e com conteúdo correto.
- Prioridade: Média

### RNF-17 - Auditabilidade
- Nome: Auditabilidade
- Descrição: O sistema deve registrar ações relevantes realizadas por usuários e administradores, possibilitando rastreio de alterações e eventos importantes.
- Critério de aceitação: Alterações como confirmação de pagamento, cancelamento de inscrição, aprovação de lista de espera e emissão de certificado devem ser registradas com data e usuário responsável.
- Prioridade: Média

### RNF-18 - Resiliência de processamento de pagamentos
- Nome: Resiliência de processamento de pagamentos
- Descrição: O sistema deve tratar de forma robusta operações de pagamento e recusa de transações, evitando inconsistências no status da inscrição.
- Critério de aceitação: Falhas no processamento do pagamento não devem resultar em inscrição inconsistente, duplicada ou sem registro do status correto.
- Prioridade: Alta

### RNF-19 - Tratamento de concorrência
- Nome: Tratamento de concorrência
- Descrição: O sistema deve controlar situações em que vários usuários tentam inscrever-se ao mesmo tempo em um evento com vagas limitadas.
- Critério de aceitação: Não deve ocorrer excedente de vagas nem inscrever o mesmo participante duas vezes em um mesmo evento por concorrência simultânea.
- Prioridade: Alta

### RNF-20 - Qualidade e clareza das mensagens do sistema
- Nome: Qualidade e clareza das mensagens do sistema
- Descrição: O sistema deve apresentar mensagens claras e objetivas em caso de erro, bloqueio de inscrição, falha de pagamento ou indisponibilidade de atividade.
- Critério de aceitação: O usuário deve receber orientações suficientes para entender o problema e a próxima ação esperada.
- Prioridade: Média

## Resumo

Os requisitos não funcionais identificados cobrem áreas fundamentais para o funcionamento confiável e seguro do sistema, especialmente em processos sensíveis como inscrição, pagamento, cancelamento, listas de espera e manejo de dados pessoais. Os principais focos são segurança, disponibilidade, performance em picos de uso, privacidade, confiabilidade e acessibilidade.
