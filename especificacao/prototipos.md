# Protótipos Simples dos Módulos

## 1. Objetivo

Apresentar uma primeira representação das telas e dos fluxos principais do sistema de gestão de eventos. Os protótipos são de baixa fidelidade e servem para validar organização, campos e ações antes da definição visual e técnica.

Os nomes de botões e informações são provisórios. Regras ainda dependentes de dúvidas abertas não são tratadas como decisões definitivas.

## 2. Navegação geral

```text
+--------------------------------------------------------------+
| EVENTUS                                      [Perfil] [Sair]  |
+--------------------------------------------------------------+
| Eventos | Minhas inscrições | Agenda | Notificações         |
+--------------------------------------------------------------+
| Conteúdo do módulo selecionado                               |
|                                                              |
+--------------------------------------------------------------+
```

## 3. Módulo de Participantes

### 3.1 Lista de eventos

```text
+----------------------------------------------------------------+
| Eventos disponíveis                         [Buscar evento...] |
+----------------------------------------------------------------+
| Filtros: [Tipo v] [Data v] [Gratuito/Pago v]                  |
+----------------------------------------------------------------+
| Evento                  Data        Local       Vagas  Valor   |
| Congresso Eventus       10/10/2026  Centro      120/200 R$ 80  |
| Workshop de Gestão      12/10/2026  Sala 2       08/20  Grátis  |
| Evento corporativo      20/10/2026  Auditório    Lotado R$ 120 |
|                                                                |
| [Ver detalhes] [Ver detalhes] [Ver detalhes]                 |
+----------------------------------------------------------------+
```

Relaciona-se a RF-01, RF-10, RF-16 e RN-01, RN-08, RN-17.

### 3.2 Detalhes e inscrição

```text
+----------------------------------------------------------------+
| < Voltar    Congresso Eventus                                 |
+----------------------------------------------------------------+
| Data: 10/10/2026        Local: Centro de Convenções           |
| Tipo: Congresso          Valor: R$ 80,00                      |
| Vagas: 80 disponíveis                                         |
+----------------------------------------------------------------+
| Programação                                                  |
| [ ] 09:00 Workshop A       Sala 1       20 vagas              |
| [ ] 11:00 Palestra B       Auditório    120 vagas             |
| [ ] 14:00 Workshop C       Sala 2       10 vagas              |
+----------------------------------------------------------------+
| Política de cancelamento: conforme configuração do evento     |
| Vaga reservada ao iniciar pagamento; boleto/Pix vencido libera vaga |
|                                                                |
| [Continuar inscrição]                                         |
+----------------------------------------------------------------+
```

Na confirmação, o sistema deve validar capacidade, conflito com inscrições em andamento/pendentes ou confirmadas, duplicidade, pagamento e demais regras aplicáveis. Se houver conflito, deve bloquear a reserva, exibir alerta explicativo e enviar notificação por e-mail, conforme RN-10/RN-21. A vaga é reservada no início do pagamento e, se boleto/Pix vencer sem confirmação, volta a ficar disponível conforme RN-07. O critério de confirmação prévia de pagamento permanece sujeito a DL-12. A mesma política de inscrição, pagamento, cancelamento e lista de espera aplica-se a todas as categorias, conforme DL-10. O prazo de cancelamento segue RN-04.

### 3.3 Minhas inscrições

```text
+----------------------------------------------------------------+
| Minhas inscrições                                               |
+----------------------------------------------------------------+
| Evento              Atividades       Status          Ações      |
| Congresso Eventus   Workshop A       Confirmada      [Detalhes] |
| Workshop de Gestão  Workshop único   Pendente        [Detalhes] |
| Evento corporativo  -                Lista de espera [Detalhes] |
+----------------------------------------------------------------+
| Detalhes da inscrição                                         |
| Data da inscrição: 01/09/2026                                |
| Pagamento: Pendente/Confirmado/Não aplicável                  |
|                                                                |
| [Baixar comprovante] [Cancelar inscrição] [Ver certificado]   |
+----------------------------------------------------------------+
```

A ação de cancelamento só aparece quando permitida pela política do evento e até sete dias úteis antes de sua data de início, conforme RN-04. O certificado é emitido automaticamente após o evento e enviado por e-mail aos participantes com frequência mínima de 75%, conforme RN-13/RN-23; o cálculo depende do método de apuração ainda a especificar.

## 4. Módulo de Organizadores

### 4.1 Painel de eventos

```text
+----------------------------------------------------------------+
| Painel do organizador                         [+ Novo evento]  |
+----------------------------------------------------------------+
| Evento                 Status      Confirm. Pagto. Vagas Ações  |
| Congresso Eventus      Ativo       110      10     80    [Abrir]|
| Workshop de Gestão     Rascunho    0        0      20    [Editar]|
| Evento corporativo     Encerrado   200      0      0     [Abrir]|
+----------------------------------------------------------------+
| Indicadores: 3 eventos | 320 inscritos | 100 vagas disponíveis |
+----------------------------------------------------------------+
```

Relaciona-se a RF-09, RF-10, RF-12 e RF-13.

### 4.2 Cadastro e configuração de evento

```text
+----------------------------------------------------------------+
| Novo evento                                                    |
+----------------------------------------------------------------+
| Dados gerais                                                   |
| Nome:        [______________________________________________]  |
| Descrição:   [______________________________________________]  |
| Tipo:        [Congresso v]  Data: [__/__/____]                |
| Local:       [______________________________________________]  |
| Capacidade:  [________]     Valor: [________] [Gratuito v]    |
+----------------------------------------------------------------+
| Regras do evento                                               |
| Cancelamento: [Permitir v]  Prazo: [________]                 |
| Reembolso:    [Configurar]                                    |
| Lista espera: [Ativar v]    Pagamento prévio: [Configurar v]  |
| Certificado: automático após evento; frequência mínima: 75%  |
+----------------------------------------------------------------+
| [Salvar rascunho]                              [Ativar evento] |
+----------------------------------------------------------------+
```

Cancelamento, reembolso, pagamento e lista de espera seguem as regras de negócio correspondentes; a reserva ocorre no início do pagamento e o vencimento do boleto/Pix libera a vaga (RN-07). A emissão do certificado segue a regra fixa de frequência mínima de 75% (RN-13/RN-23); o método de registro e cálculo da frequência ainda precisa ser definido.

### 4.3 Agenda e controle de atividades

```text
+----------------------------------------------------------------+
| Congresso Eventus > Agenda                      [+ Atividade]  |
+----------------------------------------------------------------+
| Horário | Atividade       | Sala       | Palestrante | Vagas    |
| 09:00   | Workshop A      | Sala 1     | Ana         | 20/30    |
| 11:00   | Palestra B      | Auditório  | Bruno       | 120/200  |
| 14:00   | Workshop C      | Sala 2     | Carla       | 10/20    |
+----------------------------------------------------------------+
| [Editar atividade] [Ajustar vagas] [Ver participantes]         |
+----------------------------------------------------------------+
```

Relaciona-se a RF-16, RN-17 e RN-24. O bloqueio de inscrição do participante em atividade conflitante com outra inscrição em andamento/pendente ou confirmada foi definido em DL-07/RN-10; isso não determina se o organizador pode cadastrar atividades com horários sobrepostos na agenda.

### 4.4 Participantes e lista de espera

```text
+----------------------------------------------------------------+
| Congresso Eventus > Participantes                              |
+----------------------------------------------------------------+
| Filtro: [Status v] [Atividade v] [Buscar nome_______________]  |
+----------------------------------------------------------------+
| Participante       Atividade       Status       Pagamento       |
| Maria Silva        Workshop A      Confirmada   Confirmado      |
| Joao Souza         Palestra B      Pendente     Pendente        |
| Ana Costa          Workshop C      Espera #1    N/A             |
+----------------------------------------------------------------+
| Total: 120   Confirmados: 110   Pagto: 5   Em espera: 5        |
| [Exportar] [Convocar próximo] [Presença conforme modalidade]  |
+----------------------------------------------------------------+
```

A convocação deve seguir a ordem cronológica de inscrição na lista de espera, conforme RN-24 e DL-03 (resolvida). Para presença que habilita certificado, eventos online usam dados do Zoom ou Google Meet e eventos presenciais usam lista de chamada; a integração/importação e o cálculo da frequência ainda precisam ser definidos. Comprovantes de inscrições confirmadas, certificados e notificações são enviados por e-mail, conforme DL-05. A exportação e os dados exibidos devem respeitar o perfil de acesso e a proteção de dados.

Vagas reservadas por pagamentos em andamento contam como ocupadas para o controle de capacidade e voltam a ficar disponíveis quando boleto ou Pix vencer sem confirmação, conforme RN-01/RN-07.

## 5. Módulo da Equipe Financeira

### 5.1 Pagamentos

```text
+----------------------------------------------------------------+
| Financeiro > Pagamentos                                        |
+----------------------------------------------------------------+
| Filtros: [Evento v] [Status v] [Período v]                    |
+----------------------------------------------------------------+
| Participante | Evento          | Valor   | Status   | Ações      |
| Maria Silva  | Congresso       | R$80,00 | Pendente | [Analisar]  |
| Pedro Lima   | Workshop        | R$00,00 | Isento   | [Detalhes]  |
| Ana Costa    | Corporativo     | R$120,00| Pago     | [Detalhes]  |
+----------------------------------------------------------------+
| Status da instituição financeira: [Pendente/Confirmado/Recusado]|
| [Ver retorno] [Tratar exceção] [Ver histórico]                 |
+----------------------------------------------------------------+
```

Quando a confirmação prévia for exigida, o status deve refletir o retorno da instituição financeira; somente a confirmação dessa instituição libera a inscrição. Quais inscrições exigem confirmação ainda está pendente em DL-12.

### 5.2 Reembolsos

```text
+----------------------------------------------------------------+
| Financeiro > Reembolsos                                        |
+----------------------------------------------------------------+
| Solicitação       Participante | Valor   | Elegibilidade | Ação |
| REB-001           Maria Silva  | R$80,00 | Em análise    | [...] |
| REB-002           Pedro Lima   | R$00,00 | Não aplicável | [...] |
+----------------------------------------------------------------+
| Dados da solicitação                                           |
| Motivo: [Cancelamento pela organização / Saúde com atestado]   |
| Política aplicada: [Cancelamento do evento / Atestado médico]  |
|                                                                |
| [Aprovar] [Recusar] [Registrar processamento]                  |
+----------------------------------------------------------------+
```

A elegibilidade para reembolso de inscrição paga está definida em RN-05: cancelamento do evento pela organização ou problema de saúde do participante comprovado por atestado médico. O valor e o prazo de processamento não foram definidos. O prazo para cancelar a inscrição está definido em RN-04.

## 6. Módulo de Palestrantes

### 6.1 Minha programação

```text
+----------------------------------------------------------------+
| Área do palestrante                                            |
+----------------------------------------------------------------+
| Minhas atividades                                               |
| Data       Atividade       Descrição       Palestrante  Valor   |
| 10/10/26   Workshop A      ...             Ana          R$ 80   |
| 10/10/26   Palestra B      ...             Bruno        R$ 80   |
+----------------------------------------------------------------+
| [Ver participantes] [Ver detalhes da atividade]               |
+----------------------------------------------------------------+
```

O acesso é restrito às atividades vinculadas ao palestrante. Data do evento, descrição, palestrante e valor podem ser exibidos. Na lista de participantes, mostrar somente nome e sexo; CPF, RG e outros dados pessoais não especificados para esse perfil ficam ocultos, conforme DL-08/RN-16.

### 6.2 Participantes da atividade

```text
+----------------------------------------------------------------+
| Workshop A > Participantes                                     |
+----------------------------------------------------------------+
| Nome              Sexo                                         |
| Maria Silva       Feminino                                     |
| João Souza        Masculino                                    |
+----------------------------------------------------------------+
| CPF e RG não são exibidos; somente participantes da atividade. |
+----------------------------------------------------------------+
```

Relaciona-se a RF-22, RF-23, RN-15, RN-16 e RN-19.

## 7. Módulo de Gestão de Acessos

### 7.1 Usuários e perfis

```text
+----------------------------------------------------------------+
| Gestão de acessos                              [+ Novo usuário] |
+----------------------------------------------------------------+
| Usuário          Perfil             Status       Ações          |
| Maria Silva      Participante       Ativo        [Editar]       |
| Joao Souza       Organizador        Ativo        [Editar]       |
| Ana Costa        Financeiro         Ativo        [Editar]       |
| Bruno Lima       Palestrante        Ativo        [Editar]       |
+----------------------------------------------------------------+
| Perfil selecionado: [Organizador v]                            |
| [x] Criar e editar eventos     [x] Ver participantes           |
| [x] Configurar regras          [ ] Processar pagamentos        |
| [ ] Ver dados de outros perfis                                 |
|                                                                |
| [Salvar permissões]                                            |
+----------------------------------------------------------------+
```

Permissões definidas: participante consulta todos os eventos e se inscreve; organizador administra eventos; palestrante consulta os eventos que irá ministrar e somente nome/sexo dos participantes dessas atividades; equipe financeira consulta pagamentos/status, trata divergências sem sobrescrever a confirmação da instituição financeira, analisa/processa reembolsos e consulta histórico financeiro/relatórios. Os controles de interface continuam ilustrativos.

## 8. Estados essenciais

```text
Inscrição:  Pendente -> Confirmada -> Cancelada -> Reembolsada
                 |             |
                 +-> Recusada   +-> Certificado disponível

Evento:     Rascunho -> Ativo -> Lotado -> Encerrado
                         |
                         +-> Desativado

Lista:      Interessado -> Em espera -> Convocado -> Confirmado
```

As transições devem ser registradas no histórico de auditoria e respeitar as regras do evento. Os estados são uma representação inicial e podem ser refinados após as respostas às dúvidas abertas.

## 9. Requisitos não funcionais considerados

Os protótipos devem evoluir considerando WCAG 2.2 nível AA como alvo de acessibilidade, além das referências de segurança OWASP ASVS, privacidade LGPD/ANPD e qualidade ISO/IEC 25010 adotadas em DL-09. Ainda faltam nível/escopo de verificação de segurança, metas e cenários de medição de desempenho/disponibilidade e políticas operacionais de dados.
