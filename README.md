# Gestão de Eventos

Este repositório foi estruturado para registrar a análise e a especificação do projeto.

## Contexto do Projeto

A empresa Eventus organiza congressos, workshops e eventos corporativos. Atualmente, o gerenciamento das inscrições é realizado por meio de formulários on-line e planilhas eletrônicas, dificultando o controle de vagas, pagamentos, cancelamentos e emissão de certificados.

Com o crescimento do número de eventos realizados, a empresa decidiu desenvolver um sistema para centralizar essas atividades, oferecendo uma melhor experiência aos participantes e maior controle para os organizadores.

## Estrutura

- `analise/`: artefatos de análise inicial
- `especificacao/`: documentos de especificação em evolução

## Stakeholders Identificados e Interesses

- Participantes: inscrever-se em eventos, acompanhar inscrições, cancelar participação e emitir certificados.
- Organizadores: criar eventos, controlar vagas, acompanhar inscrições e gerenciar participantes.
- Equipe Financeira: confirmar pagamentos e controlar reembolsos.
- Palestrantes: consultar a programação e informações sobre participantes de suas atividades.
- Equipe de TI: desenvolver e manter o sistema.

## Reflexão sobre o Uso da Inteligência Artificial

### 1. Ferramenta GenAI Utilizada

- GitHub Copilot (produção dos artefatos)
- Claude Code (utilizado como revisor)

### 2. Apoio da IA nas diferentes etapas da atividade

A IA colaborou significativamente na elaboração dos documentos de Requisitos Funcionais (RF) e Requisitos Não Funcionais (RN). Embora algumas revisões tenham sido necessárias, seu uso permitiu antecipar o trabalho e organizar os requisitos com mais agilidade, além de possibilitar um cruzamento mais abrangente das informações. Dessa forma, foram identificados e incluídos itens que poderiam ser esquecidos caso a atividade fosse realizada exclusivamente de forma manual.

### 3. Sugestões da GenIA que foram aceitas

- Inclusão de critérios de segurança, tempo de resposta, acessibilidade e proteção de dados. Itens adicionais com destaque em relação aos demais, reforçando a necessidade de adoção e revisão.

### 4. Sugestões da GenIA que foram descartadas ou modificadas

- Duplicidade na lista de dúvidas e lacunas. Três pares de itens tratavam da mesma questão com redações diferentes. Consolidação gerando uma redução de 15 para 12 dúvidas reais.
- Incorporada a sugestão de bloqueio de RF e RN devido à existência de dúvida em aberto (DL).

### 5. Artefatos de especificação produzidos

- **Casos de Uso:** descrevem os fluxos de interação entre os usuários e o sistema, detalhando os objetivos, as etapas e as regras envolvidas. São importantes para organizar as funcionalidades e facilitar a validação dos requisitos pelos stakeholders.
- **Protótipos simples das telas:** representam a disposição inicial das informações e das funcionalidades nas telas do sistema. São importantes para validar a organização da interface e identificar ajustes de usabilidade antes da implementação.
