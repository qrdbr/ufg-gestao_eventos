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
| Pagamento prévio: conforme configuração do evento             |
|                                                                |
| [Continuar inscrição]                                         |
+----------------------------------------------------------------+
```

Na confirmação, o sistema deve validar capacidade, conflito de horário, duplicidade, pagamento e demais regras aplicáveis. Os campos de política permanecem configuráveis por causa de DL-01, DL-06, DL-07, DL-10 e DL-12.

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

A ação de cancelamento só aparece quando permitida pela política do evento e pelo prazo definido. O certificado só aparece quando a condição de emissão for satisfeita.

## 4. Módulo de Organizadores

### 4.1 Painel de eventos

```text
+----------------------------------------------------------------+
| Painel do organizador                         [+ Novo evento]  |
+----------------------------------------------------------------+
| Evento                 Status      Inscritos   Vagas   Ações    |
| Congresso Eventus      Ativo       120         80      [Abrir]  |
| Workshop de Gestão     Rascunho    0           20      [Editar] |
| Evento corporativo     Encerrado   200         0       [Abrir]  |
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
| Certificado:  [Automático v] Presença obrigatória: [Sim/Não]  |
+----------------------------------------------------------------+
| [Salvar rascunho]                              [Ativar evento] |
+----------------------------------------------------------------+
```

As opções de prazo, reembolso, pagamento, reserva de vaga, certificado e lista de espera devem aguardar as definições relacionadas às DLs correspondentes.

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

Relaciona-se a RF-16, RN-17 e RN-24. Conflitos de horário devem ser sinalizados, sem fixar comportamento além do que for definido em DL-07.

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
| Total: 120   Confirmados: 110   Pendentes: 5   Em espera: 5    |
| [Exportar] [Convocar próximo] [Registrar presença]             |
+----------------------------------------------------------------+
```

A ordem de convocação depende de DL-03. A exportação e os dados exibidos devem respeitar o perfil de acesso e a proteção de dados.

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
| [Confirmar pagamento] [Registrar recusa] [Ver histórico]       |
+----------------------------------------------------------------+
```

O bloqueio da inscrição por pagamento prévio deve ser aplicado apenas quando essa regra estiver configurada e definida, conforme DL-12.

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
| Motivo: [Cancelamento dentro do prazo]                         |
| Política aplicada: [A confirmar por evento]                    |
|                                                                |
| [Aprovar] [Recusar] [Registrar processamento]                  |
+----------------------------------------------------------------+
```

A elegibilidade e o prazo permanecem dependentes de DL-01 e DL-02.

## 6. Módulo de Palestrantes

### 6.1 Minha programação

```text
+----------------------------------------------------------------+
| Área do palestrante                                            |
+----------------------------------------------------------------+
| Minhas atividades                                               |
| Data       Horário  Atividade       Local       Participantes  |
| 10/10/26   09:00    Workshop A      Sala 1      20 inscritos  |
| 10/10/26   11:00    Palestra B       Auditório   120 inscritos |
+----------------------------------------------------------------+
| [Ver participantes] [Ver detalhes da atividade]               |
+----------------------------------------------------------------+
```

O acesso é restrito às atividades vinculadas ao palestrante. A quantidade e os dados dos participantes exibidos devem respeitar DL-08.

### 6.2 Participantes da atividade

```text
+----------------------------------------------------------------+
| Workshop A > Participantes                                     |
+----------------------------------------------------------------+
| Nome              Status       Informação permitida            |
| Maria Silva       Confirmada   Nome e status                   |
| Joao Souza        Confirmada   Nome e status                   |
| Ana Costa         Pendente     Nome e status                   |
+----------------------------------------------------------------+
| Dados sensíveis e informações de outros eventos não exibidos.  |
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

As permissões exibidas são uma proposta inicial. O conjunto definitivo de ações por perfil depende de DL-11.

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

Os protótipos devem evoluir considerando acessibilidade, navegação por teclado, contraste, responsividade, clareza das mensagens, proteção de dados, controle de acesso, desempenho, disponibilidade e auditabilidade, conforme RNF-01 a RNF-20. Os critérios concretos de segurança, desempenho, disponibilidade, acessibilidade e privacidade ainda dependem de validação em DL-09.
