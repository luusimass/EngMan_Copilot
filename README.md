# EngMan Copilot — FIAP × Motiva

## Identificação
CIRA - Confiabilidade Inteligente e Reconhecimento de Alterações
- Anna Luisa Santos de Lima - RM 575081 - 1CCPR


## Problema abordado
A Engenharia de Manutenção da Motiva precisa lidar com falhas em ativos eletroeletrônicos presentes nas rodovias concedidas. Para realizar diagnósticos e definir intervenções adequadas, os profissionais precisam consultar informações técnicas, históricos de falhas, procedimentos operacionais e indicadores de criticidade. A dificuldade de localizar e relacionar essas informações pode tornar o diagnóstico mais demorado, dificultar a identificação de falhas recorrentes e prejudicar a priorização das atividades de manutenção.

O EngMan Copilot propõe utilizar Inteligência Artificial Generativa combinada à técnica RAG (Retrieval-Augmented Generation) para apoiar os profissionais na consulta dessas informações, na identificação de possíveis causas e na elaboração de recomendações fundamentadas em documentos disponíveis. O assistente terá caráter consultivo: não substituirá a avaliação de profissionais habilitados nem executará intervenções nos equipamentos.


## Recorte e persona
### Recorte A — Diagnóstico e Confiabilidade

### Persona principal — Engenheiro de Manutenção
O Engenheiro de Manutenção é responsável por analisar ocorrências, identificar reincidências, avaliar a criticidade dos equipamentos e definir estratégias de manutenção. O principal desafio dessa persona é tomar decisões fundamentadas em informações técnicas e históricas, evitando conclusões sem evidências suficientes. Por isso, o assistente deverá apresentar fontes, diferenciar fatos de hipóteses e indicar o nível de confiança das respostas.


## Escopo do assistente
### O que o EngMan Copilot fará
- Consultar informações cadastrais dos ativos por meio da TAG.
- Recuperar o histórico de falhas e intervenções.
- Identificar possíveis padrões de reincidência.
- Consultar procedimentos de manutenção preventiva e inspeção.
- Apresentar hipóteses de causas prováveis para falhas relatadas.
- Consultar critérios de criticidade e apoiar a priorização.
- Recomendar o tipo de intervenção mais adequado entre corretiva, preventiva, inspeção e manutenção baseada em condição (CBM).
- Elaborar rascunhos de ordens de serviço para revisão humana.
- Informar as fontes utilizadas nas respostas.
- Indicar quando não houver dados suficientes para responder.

### O que o EngMan Copilot recusará
- Inventar TAGs, modelos, números de série, métricas ou históricos.
- Emitir laudos técnicos, pareceres de engenharia ou ART.
- Autorizar ou executar intervenções físicas.
- Substituir procedimentos oficiais de segurança.
- Orientar intervenções elétricas que contrariem ou substituam procedimentos oficiais e requisitos aplicáveis das NR-10 e NR-35.
- Responder a assuntos fora do escopo definido.
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

Critério | Llama 3.1 8B | Qwen2.5 7B 
Tipo | Modelo de linguagem aberto | Modelo de linguagem aberto 
Execução proposta | Local, via Ollama | Local, via Ollama 
Ponto de avaliação | Qualidade das respostas e aderência às instruções | Qualidade das respostas e aderência às instruções 
Trade-off | Pode exigir mais recursos computacionais | Pode apresentar diferenças de desempenho conforme a tarefa 

### Bancos vetoriais
| Critério | Chroma | FAISS 
Finalidade | Armazenamento e recuperação vetorial | Busca por similaridade vetorial 
Ponto de avaliação | Facilidade de integração e gerenciamento de documentos | Desempenho e flexibilidade na busca 
Trade-off | Camada de gerenciamento mais simples | Exige maior estruturação da aplicação ao redor da busca 

### Escolha 
A combinação inicial a ser avaliada será **Llama 3.1 8B + Ollama + Chroma**, considerando a possibilidade de execução local e a facilidade de organização da base documental.  A alternativa Qwen2.5 7B e o FAISS serão mantidos como referências de comparação. A escolha final dependerá dos testes e dos recursos computacionais disponíveis.


## Base de conhecimento
A base de conhecimento será organizada para permitir a recuperação de informações técnicas relevantes durante o atendimento. Na Sprint 01, será entregue o inventário dos documentos previstos, com seus respectivos campos e origens. Os dados de ativos e históricos serão sintéticos, identificados expressamente como simulados, pois não representam registros reais da Motiva.

### Documentos previstos
Documento | Conteúdo principal | Origem 
Catálogo de ativos | TAG, tipo, fabricante, modelo, localização e criticidade | Simulado 
Plano de manutenção preventiva | Tarefas, periodicidade, responsáveis e recursos | Simulado 
Histórico de falhas | TAG, data, sintoma, causa identificada e reparo | Simulado 
Procedimentos operacionais (POPs) | Inspeção, limpeza, ajustes e testes | Simulado 
Fichas técnicas | Especificações dos equipamentos | Real e simulado 
Matriz de criticidade | Impactos e critérios de priorização | Simulado 
Glossário de siglas | CFTV, CBM, RCM, MTBF, MTTR e demais termos | Real 
Normas e requisitos de segurança | Resumos dos requisitos aplicáveis de NR-10 e NR-35 | Real 
Briefing Motiva | Contexto do desafio e informações institucionais | Real 
Boletins de ocorrência | Relatos técnicos e condições observadas em campo | Simulado 

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

Categoria | Objetivo 
factual | Verificar a recuperação correta de informações presentes na base 
instrucional | Avaliar a elaboração de orientações e rascunhos de ordens de serviço 
ambíguo | Verificar se o assistente solicita esclarecimentos 
dado_inexistente | Avaliar se reconhece a ausência de informações 
out_of_scope | Verificar a recusa de assuntos fora do domínio 
jailbreak | Avaliar a resistência a tentativas de manipulação 
risco_operacional | Verificar a recusa de orientações perigosas 
memoria_contexto | Avaliar a coerência com informações anteriores da conversa 


## Tools especificadas
As ferramentas permitirão que o assistente consulte informações estruturadas, sem depender exclusivamente da interpretação de documentos. Os parâmetros, tipos de dados, descrições e valores permitidos serão formalizados em JSON Schema. As ferramentas deverão retornar apenas informações disponíveis nas fontes simuladas ou documentadas.


Tool proposta | Função | Parâmetros principais 
`consultar_ativo_por_tag` | Recuperar o cadastro de um equipamento | `tag` 
`consultar_historico_falhas` | Consultar falhas e intervenções anteriores | `tag`, `limite_registros` 
`consultar_procedimento` | Recuperar procedimentos aplicáveis ao ativo | `tipo_ativo`, `tipo_procedimento` 
`calcular_prioridade` | Apoiar a classificação de prioridade com critérios definidos | `criticidade`, `impacto_seguranca`, `impacto_arrecadacao`, `disponibilidade` 


## Riscos e mitigações
O projeto considera os riscos associados à utilização de Inteligência Artificial em um ambiente de infraestrutura rodoviária.

Risco | Impacto | Mitigação proposta 
Alucinação | Decisões técnicas incorretas | Restringir respostas à base e às tools; informar ausência de dados 
Prompt injection | Manipulação das instruções | Guardrail de entrada e testes de jailbreak 
Risco operacional | Acidentes e danos físicos | Recusar orientações perigosas e encaminhar aos procedimentos oficiais 
Viés na priorização | Priorização inadequada de ativos | Utilizar critérios explícitos e auditáveis 
Exposição de dados pessoais | Violação de privacidade | Não incluir dados pessoais na base 
Confidencialidade operacional | Exposição de informações internas | Utilizar dados simulados e avaliar execução local 
Excesso de confiança | Hipóteses tratadas como diagnósticos confirmados | Diferenciar fato e hipótese e exigir validação humana 
Perda de contexto | Associação incorreta entre ativos | Reforçar a TAG consultada e controlar o histórico 


## Limitações conhecidas
- O projeto não possui acesso a uma base operacional real da Motiva.
- Os cadastros de ativos e históricos utilizados inicialmente serão simulados.
- A qualidade das respostas dependerá da disponibilidade e da consistência dos documentos.
- O assistente não substitui profissionais habilitados nem procedimentos oficiais.
- Hipóteses de diagnóstico deverão ser verificadas em campo.
- A avaliação da solução nesta etapa será documental e baseada nos artefatos especificados, sem implementação de código ou integração real.


## Referências
- FIAP. Challenge Sprint — EngMan Copilot: FIAP × Motiva Rodovias.
- Motiva Rodovias. Briefing Inovação Aberta FIAP — EngMan Motiva. 16 set. 2026.
- Ministério do Trabalho e Emprego. Norma Regulamentadora NR-10 — Segurança em Instalações e Serviços em Eletricidade.
- Ministério do Trabalho e Emprego. Norma Regulamentadora NR-35 — Trabalho em Altura.
- Materiais didáticos da disciplina Prompt Engineering & Artificial Intelligence — FIAP.
