# EngMan Copilot — FIAP × Motiva
*CIRA — Confiabilidade Inteligente e Reconhecimento de Alterações*

## Identificação
- Anna Luisa Santos de Lima - RM 575081 - 1CCPR


## Problema abordado
A Motiva destaca o desafio de evoluir a Engenharia de Manutenção por meio de uma abordagem orientada à confiabilidade dos ativos eletroeletrônicos rodoviários. A proposta envolve utilizar o histórico de falhas para apoiar a definição de estratégias de manutenção preventiva, inspeção e manutenção baseada em condição (CBM), além de avaliar a necessidade de retrofit. Nesse contexto, o EngMan Copilot busca facilitar o acesso às informações técnicas e históricas necessárias para apoiar essas análises, respeitando os limites dos dados disponíveis.


## Recorte e persona
Recorte A — Diagnóstico e Confiabilidade

### Delimitação inicial do domínio
Para a primeira versão do EngMan Copilot, foi definido um domínio de atuação específico: equipamentos de CFTV, especialmente câmeras PTZ. Essa delimitação permite desenvolver e avaliar as funcionalidades de consulta por TAG, recuperação de histórico de falhas, identificação de possíveis causas e apoio à priorização de ocorrências em um contexto técnico mais controlado.
Embora a base de conhecimento contenha um inventário simulado de diferentes categorias de ativos eletroeletrônicos, o atendimento funcional inicial do assistente ficará restrito aos equipamentos de CFTV/PTZ. As demais categorias serão utilizadas como parte da estrutura demonstrativa do inventário e poderão ser consideradas em futuras expansões do projeto.

### Persona principal — Engenheiro de Manutenção
O Engenheiro de Manutenção é responsável por analisar ocorrências, identificar reincidências, avaliar a criticidade dos equipamentos e definir estratégias de manutenção. O principal desafio dessa persona é tomar decisões fundamentadas em informações técnicas e históricas, evitando conclusões sem evidências suficientes. Por isso, o assistente deverá apresentar fontes, diferenciar fatos de hipóteses e indicar o nível de confiança das respostas.


## Escopo do assistente
### O que o EngMan Copilot fará
- Consultar informações cadastrais de ativos CFTV/PTZ por meio da TAG.
- Recuperar o histórico de falhas e intervenções desses equipamentos.
- Identificar possíveis padrões de reincidência.
- Consultar procedimentos de manutenção preventiva e inspeção aplicáveis ao domínio definido.
- Apresentar hipóteses de causas prováveis para falhas relatadas.
- Consultar critérios de criticidade e apoiar a priorização.
- Recomendar o tipo de intervenção mais adequado entre corretiva, preventiva, inspeção e manutenção baseada em condição (CBM).
- Elaborar rascunhos de ordens de serviço para revisão humana.
- Informar as fontes utilizadas nas respostas.
- Indicar quando não houver dados suficientes para responder.

### O que o EngMan Copilot recusará
- Responder sobre ativos que não estejam contemplados no domínio funcional inicial.
- Inventar TAGs, modelos, números de série, métricas ou históricos.
- Emitir laudos técnicos, pareceres de engenharia ou ART.
- Autorizar ou executar intervenções físicas.
- Substituir procedimentos oficiais de segurança.
- Orientar intervenções elétricas que contrariem ou substituam procedimentos oficiais e requisitos aplicáveis das NR-10 e NR-35.
- Utilizar dados pessoais ou informações operacionais confidenciais sem autorização.


## Arquitetura da solução
A arquitetura proposta utiliza Inteligência Artificial Generativa, RAG e ferramentas de consulta estruturada para fornecer respostas fundamentadas na base de conhecimento.

1. Entrada - o Engenheiro de Manutenção informa a TAG do equipamento, o sintoma observado ou sua dúvida.
2. Guardrail de entrada - verifica se a solicitação está dentro do escopo e identifica pedidos perigosos ou tentativas de manipulação das instruções.
3. Montagem do contexto - reúne o system prompt, o histórico da conversa, os dados recuperados pela técnica RAG e os resultados das ferramentas.
4. Chamada ao LLM - processa a solicitação utilizando o modelo de linguagem escolhido e parâmetros definidos.
5. Decisão de tool - identifica se as informações disponíveis são suficientes ou se é necessário consultar outra ferramenta.
6. Execução da tool - consulta os dados simulados do ativo, histórico, procedimentos ou indicadores e devolve os resultados ao contexto.
7. Guardrail de saída - verifica se a resposta respeita o escopo, apresenta fontes e diferencia fatos de hipóteses.
8. Resposta e histórico - apresenta a resposta ao usuário e registra o contexto necessário para manter a continuidade do atendimento.


## Stack e justificativa técnica
### Modelos de linguagem (LLM)

|Critério | Llama 3.1 8B | Qwen2.5 7B |
|---|---|---|
|Tipo | Modelo de linguagem aberto | Modelo de linguagem aberto |
|Execução proposta | Local, via Ollama | Local, via Ollama |
|Ponto de avaliação | Qualidade das respostas e aderência às instruções | Qualidade das respostas e aderência às instruções |
|Trade-off | Pode exigir mais recursos computacionais | Pode apresentar diferenças de desempenho conforme a tarefa |

### Bancos vetoriais
| Critério | Chroma | FAISS |
|---|---|---|
|Finalidade | Armazenamento e recuperação vetorial | Busca por similaridade vetorial |
|Ponto de avaliação | Facilidade de integração e gerenciamento de documentos | Desempenho e flexibilidade na busca |
|Trade-off | Camada de gerenciamento mais simples | Exige maior estruturação da aplicação ao redor da busca |

### Escolha 
A combinação inicial a ser avaliada será **Llama 3.1 8B + Ollama + Chroma**, considerando a possibilidade de execução local e a facilidade de organização da base documental.  A alternativa Qwen2.5 7B e o FAISS serão mantidos como referências de comparação. A escolha final dependerá dos testes e dos recursos computacionais disponíveis.


## Base de conhecimento
A base de conhecimento será organizada para permitir a recuperação de informações técnicas relevantes durante o atendimento. Na Sprint 01, será apresentado um inventário simulado com 30 ativos de diferentes categorias de equipamentos eletroeletrônicos rodoviários. Apesar da diversidade do inventário, o domínio funcional inicial do EngMan Copilot será restrito a câmeras CFTV, especialmente equipamentos PTZ. Os demais ativos integram a estrutura demonstrativa da base de conhecimento e representam possibilidades de expansão futura.
Os dados de ativos e históricos serão sintéticos, identificados expressamente como simulados, pois não representam registros reais da Motiva.

### Documentos previstos
|Documento | Conteúdo principal | Teor|
|---|---|---|
|Catálogo de ativos | TAG, tipo, fabricante, modelo, localização e criticidade | Simulado| 
|Plano de manutenção preventiva | Tarefas, periodicidade, responsáveis e recursos | Simulado| 
|Histórico de falhas | TAG, data, sintoma, causa identificada e reparo | Simulado| 
|Procedimentos operacionais (POPs) | Inspeção, limpeza, ajustes e testes | Simulado| 
|Fichas técnicas | Especificações dos equipamentos | Simulado| 
|Matriz de criticidade | Impactos e critérios de priorização | Simulado| 
|Glossário de siglas | CFTV, CBM, RCM, MTBF, MTTR e demais termos | Real| 
|Normas e requisitos de segurança | Resumos dos requisitos aplicáveis de NR-10 e NR-35 | Real| 
|Briefing Motiva | Contexto do desafio e informações institucionais | Real| 
|Boletins de ocorrência | Relatos técnicos e condições observadas em campo | Simulado|

### RAG

Os documentos serão divididos em chunks para indexação e recuperação por similaridade semântica. Cada trecho deverá conter metadados que permitam filtrar as informações.

- TAG do equipamento;
- Tipo de ativo;
- Data do registro;
- Categoria do documento;
- Tipo de ocorrência.

O assistente deverá priorizar documentos relacionados à TAG consultada e apresentar a origem das informações recuperadas. O tamanho dos chunks e a estratégia de recuperação serão definidos e justificados considerando a janela de contexto dos modelos avaliados.
Privacidade: dados pessoais de empregados, imagens de ocupantes, placas identificáveis e informações contratuais sensíveis não deverão integrar a base de conhecimento.


## System prompt
O system prompt será desenvolvido em português do Brasil e estruturado em sete blocos e as regras centrais serão impedir a geração de informações inexistentes, diferenciar fatos de hipóteses, exigir referências documentais e estabelecer limites para solicitações perigosas ou fora do escopo.

1. PAPEL
2. OBJETIVO
3. ESCOPO
4. REGRAS
5. FORMATO
6. TOM
7. BORDA


## Eval set
O conjunto de avaliação será utilizado para verificar a qualidade, a segurança e a aderência do assistente ao escopo definido. Cada caso conterá os campos `id`, `categoria`, `entrada_usuario`, `contexto_esperado`, `resposta_ideal`, `criterios_avaliacao` e `deve_recusar`.

|Categoria | Objetivo|
|---|---|
|Factual | Verificar a recuperação correta de informações presentes na base| 
|Instrucional | Avaliar a elaboração de orientações e rascunhos de ordens de serviço| 
|Ambíguo | Verificar se o assistente solicita esclarecimentos|
|Dado_inexistente | Avaliar se reconhece a ausência de informações| 
|Out_of_scope | Verificar a recusa de assuntos fora do domínio| 
|Jailbreak | Avaliar a resistência a tentativas de manipulação| 
|Risco_operacional | Verificar a recusa de orientações perigosas| 
|Memoria_contexto | Avaliar a coerência com informações anteriores da conversa| 


## Tools especificadas
As ferramentas permitirão que o assistente consulte informações estruturadas, sem depender exclusivamente da interpretação de documentos. Os parâmetros, tipos de dados, descrições e valores permitidos serão formalizados em JSON Schema. As ferramentas deverão retornar apenas informações disponíveis nas fontes simuladas ou documentadas.

| Tool proposta | Função | Parâmetros principais |
|---|---|---|
| `consultar_ativo_por_tag` | Recuperar o cadastro de um equipamento pelo seu identificador TAG | `tag` |
| `consultar_historico_falhas` | Consultar falhas e intervenções anteriores de um ativo | `tag`, `data_inicio`, `data_fim`, `limite_registros` |
| `consultar_procedimento` | Recuperar procedimentos operacionais e documentos técnicos relacionados ao sintoma ou ativo | `tag`, `sintoma`, `tipo_intervencao` |
| `calcular_prioridade` | Apoiar a classificação da prioridade de uma ocorrência com base na matriz de criticidade | `tag`, `descricao_ocorrencia` |


## Riscos e mitigações
O projeto considera os riscos associados à utilização de Inteligência Artificial em um ambiente de infraestrutura rodoviária.

|Risco | Impacto | Mitigação proposta |
|---|---|---|
|Alucinação | Decisões técnicas incorretas | Restringir respostas à base e às tools; informar ausência de dados |
|Prompt injection | Manipulação das instruções | Guardrail de entrada e testes de jailbreak |
|Risco operacional | Acidentes e danos físicos | Recusar orientações perigosas e encaminhar aos procedimentos oficiais |
|Viés na priorização | Priorização inadequada de ativos | Utilizar critérios explícitos e auditáveis |
|Exposição de dados pessoais | Violação de privacidade | Não incluir dados pessoais na base |
|Confidencialidade operacional | Exposição de informações internas | Utilizar dados simulados e avaliar execução local |
|Excesso de confiança | Hipóteses tratadas como diagnósticos confirmados | Diferenciar fato e hipótese e exigir validação humana |
|Perda de contexto | Associação incorreta entre ativos | Reforçar a TAG consultada e controlar o histórico| 


## Limitações conhecidas
- O projeto não possui acesso a uma base operacional real da Motiva.
- Os cadastros de ativos e históricos utilizados inicialmente serão simulados.
- A qualidade das respostas dependerá da disponibilidade e da consistência dos documentos.
- O assistente não substitui profissionais habilitados nem procedimentos oficiais.
- Hipóteses de diagnóstico deverão ser verificadas em campo.
- A avaliação da solução nesta etapa será documental e baseada nos artefatos especificados, sem implementação de código ou integração real.


## Documentação do projeto
Os documentos abaixo complementam a descrição da arquitetura, das decisões técnicas, das regras de funcionamento e dos recursos previstos para o EngMan Copilot.

| Documento | Descrição |
|---|---|
| [Arquitetura da solução](docs/arquitetura.png) | Diagrama visual do funcionamento e dos componentes da solução. |
| [Decisões técnicas](docs/decisoes_tecnicas.md) | Comparação dos modelos de linguagem, bancos vetoriais e escolhas arquiteturais. |
| [Riscos e LGPD](docs/riscos_lgpd.md) | Identificação dos riscos, impactos, medidas de mitigação e cuidados com dados. |
| [System Prompt](prompts/system_prompt.md) | Instruções, regras, limites e comportamento esperado do assistente. |
| [Eval Set](evals/sprint1_eval_set.json) | Casos de teste para avaliar qualidade, segurança e aderência ao escopo. |
| [Especificação das Tools](tools/tools_spec.json) | Contratos de entrada e saída das quatro ferramentas do assistente. |
| [Base de conhecimento](data/knowledge_base/inventario.md) | Inventário de ativos, fichas técnicas, históricos e dados simulados. |
| [Arquivo de entrega da Sprint 01](sprint1_entrega.txt) | Identificação do projeto e endereço do repositório para submissão. |


## Referências
- FIAP. Challenge Sprint — EngMan Copilot: FIAP × Motiva Rodovias.
- Motiva Rodovias. Briefing Inovação Aberta FIAP — EngMan Motiva. 16 set. 2026.
- Ministério do Trabalho e Emprego. Norma Regulamentadora NR-10 — Segurança em Instalações e Serviços em Eletricidade.
- Ministério do Trabalho e Emprego. Norma Regulamentadora NR-35 — Trabalho em Altura.
- Materiais didáticos da disciplina Prompt Engineering & Artificial Intelligence — FIAP.
