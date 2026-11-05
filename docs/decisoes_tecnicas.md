# Decisões Técnicas e Arquiteturais — EngMan Copilot

## 1. Objetivo

Este documento registra as principais decisões técnicas propostas para o desenvolvimento do EngMan Copilot, justificando as tecnologias selecionadas e apresentando alternativas consideradas.

A arquitetura foi planejada para permitir consultas a informações de ativos, históricos de falhas, procedimentos técnicos e critérios de priorização, utilizando inteligência artificial generativa combinada com recuperação de informações (RAG).

As escolhas descritas representam uma proposta inicial para a Sprint 01. O desempenho efetivo das tecnologias deverá ser validado durante as etapas de implementação.

## 2. Critérios de seleção

As tecnologias foram avaliadas considerando os seguintes critérios:

| Critério | Descrição |
|---|---|
| Desempenho | Capacidade de interpretar perguntas e gerar respostas relevantes. |
| Precisão | Capacidade de respeitar o contexto e evitar informações inventadas. |
| Custo | Disponibilidade e custo de utilização. |
| Privacidade | Possibilidade de controlar o ambiente de execução e os dados utilizados. |
| Integração | Compatibilidade com ferramentas de recuperação e consulta. |
| Escalabilidade | Capacidade de suportar crescimento da base de conhecimento. |
| Facilidade de implementação | Complexidade de configuração e manutenção. |

## 3. Comparação dos modelos de linguagem (LLMs)

Foram selecionados dois modelos de código aberto para avaliação inicial.

### 3.1 Llama 3.1 8B

**Desenvolvedor:** Meta.

Características consideradas:
- Modelo com 8 bilhões de parâmetros.
- Adequado para aplicações conversacionais e tarefas de interpretação de texto.
- Pode ser executado localmente por meio de ferramentas como Ollama.
- Permite experimentar diferentes configurações sem depender exclusivamente de uma API comercial.

**Vantagens:**
- Ecossistema amplo.
- Possibilidade de execução local.
- Integração com ferramentas de desenvolvimento.
- Adequado para prototipagem.

**Limitações:**
- Pode apresentar respostas inconsistentes em tarefas técnicas complexas.
- O desempenho depende dos recursos computacionais disponíveis.
- Necessita de testes para validar a precisão em Engenharia de Manutenção.

### 3.2 Qwen2.5 7B

**Desenvolvedor:** Qwen.

Características consideradas:
- Modelo com aproximadamente 7 bilhões de parâmetros.
- Suporte a diferentes tarefas de linguagem.
- Disponibilidade para execução local.
- Potencial para utilização em aplicações de recuperação e geração de respostas.

**Vantagens:**
- Alternativa para comparação de qualidade de resposta.
- Execução local em ambientes compatíveis.
- Boa flexibilidade para experimentação.
- Possibilidade de integração com ferramentas externas.

**Limitações:**
- O desempenho depende da quantização e dos recursos computacionais.
- Necessita de validação em português e em perguntas técnicas específicas.
- Pode exigir ajustes de prompt para manter respostas consistentes.

### 3.3 Comparação objetiva

| Critério | Llama 3.1 8B | Qwen2.5 7B |
|---|---|---|
| Tamanho aproximado | 8B parâmetros | 7B parâmetros |
| Execução local | Sim | Sim |
| Aplicação conversacional | Sim | Sim |
| Uso com RAG | Compatível via integração | Compatível via integração |
| Privacidade em execução local | Possível | Possível |
| Custo de licença/API | Depende da modalidade de uso | Depende da modalidade de uso |
| Adequação ao português técnico | Deve ser testada | Deve ser testada |
| Escolha | Modelo inicial proposto | Alternativa de comparação |

A comparação de precisão, latência e consumo de memória deverá ser realizada utilizando os mesmos casos de avaliação, configurações e dados de entrada.

### 3.4 Modelo selecionado

**Escolha inicial: Llama 3.1 8B.**

O modelo foi escolhido como primeira opção para a arquitetura proposta devido à disponibilidade para execução local, à integração com Ollama e à possibilidade de experimentação em um ambiente controlado.

A escolha não significa que o modelo tenha desempenho comprovadamente superior ao Qwen2.5 7B. Essa conclusão dependerá dos testes comparativos realizados na implementação.

## 4. Comparação dos bancos de dados vetoriais

A arquitetura prevê um banco vetorial para armazenar representações semânticas dos documentos da base de conhecimento.

Foram consideradas duas alternativas.

### 4.1 ChromaDB

Características:
- Banco vetorial voltado a aplicações de inteligência artificial.
- Suporte a armazenamento e recuperação de embeddings.
- Possibilidade de utilização local.
- Suporte a metadados e filtros de consulta.

**Vantagens:**
- Configuração relativamente simples.
- Integração com bibliotecas de RAG.
- Adequado para protótipos e aplicações de menor complexidade.
- Permite organizar documentos por metadados.

**Limitações:**
- Necessita de planejamento para crescimento e operação em ambientes maiores.
- A configuração de persistência e infraestrutura deve ser avaliada conforme a aplicação evoluir.

### 4.2 FAISS

Características:
- Biblioteca de busca por similaridade vetorial desenvolvida pela Meta.
- Voltada à pesquisa eficiente em grandes conjuntos de vetores.
- Permite diferentes estratégias de indexação.

**Vantagens:**
- Alto desempenho em operações de busca vetorial.
- Flexibilidade de indexação.
- Adequado para experimentos com grandes conjuntos de embeddings.

**Limitações:**
- Não oferece, por si só, todos os recursos de gerenciamento documental de um banco de dados completo.
- Exige implementação complementar para metadados, persistência e organização dos documentos.
- Pode aumentar a complexidade da aplicação.

### 4.3 Comparação objetiva

| Critério | ChromaDB | FAISS |
|---|---|---|
| Busca vetorial | Sim | Sim |
| Suporte a metadados | Integrado | Exige estrutura complementar |
| Persistência | Disponível | Exige gerenciamento adicional |
| Facilidade de implementação | Alta | Média |
| Flexibilidade de indexação | Boa | Alta |
| Integração com RAG | Sim | Sim, via integração |
| Escolha | Selecionado | Alternativa |

### 4.4 Banco vetorial selecionado

**Escolha inicial: ChromaDB.**

O ChromaDB foi escolhido por facilitar a organização dos documentos, o armazenamento de embeddings e a recuperação contextualizada por metadados.

Essa característica é relevante para o EngMan Copilot, pois a recuperação deverá considerar informações como TAG, categoria do ativo, tipo de documento e data da ocorrência.

O FAISS permanece como alternativa caso a aplicação necessite de otimizações específicas de busca vetorial.

## 5. Arquitetura proposta

A arquitetura combina um modelo de linguagem, recuperação de documentos e ferramentas especializadas.

### 5.1 Componentes

| Componente | Tecnologia ou recurso proposto | Responsabilidade |
|---|---|---|
| Interface | Aplicação web | Receber perguntas dos usuários. |
| Backend | Python | Gerenciar as solicitações e integrações. |
| LLM | Llama 3.1 8B | Interpretar perguntas e elaborar respostas. |
| Execução do modelo | Ollama | Disponibilizar o modelo localmente. |
| Banco vetorial | ChromaDB | Recuperar documentos por similaridade. |
| Embeddings | Modelo multilíngue compatível | Transformar documentos e perguntas em vetores. |
| Base documental | Arquivos Markdown e documentos autorizados | Armazenar conhecimento técnico. |
| Ferramentas | Funções com contratos JSON Schema | Consultar ativos, históricos, procedimentos e prioridades. |

**Observação:** A interface, o backend e os demais componentes são escolhas arquiteturais propostas, ainda não implementadas nesta Sprint.

### 5.2 Fluxo de recuperação (RAG)

1. O usuário envia uma pergunta.
2. O sistema identifica o contexto e verifica se a solicitação está dentro do escopo.
3. A pergunta é transformada em embedding.
4. O ChromaDB recupera os fragmentos relevantes.
5. O backend organiza os dados recuperados e os encaminha ao modelo.
6. O modelo produz uma resposta contextualizada.
7. As regras de saída verificam a presença de fontes, hipóteses e informações não confirmadas.
8. O assistente apresenta a resposta ao usuário.

## 6. Estratégia de embeddings e fragmentação

Os embeddings serão utilizados para representar semanticamente os documentos e permitir a recuperação de conteúdos relacionados à pergunta do usuário.

A proposta inicial considera um modelo de embeddings multilíngue, adequado para textos em português.

A escolha definitiva deverá considerar:
- Qualidade de recuperação em português.
- Compatibilidade com o banco vetorial.
- Tamanho dos vetores.
- Velocidade de processamento.
- Consumo de memória.
- Facilidade de execução local.

A fragmentação inicial seguirá os parâmetros documentados em `data/knowledge_base/inventario.md`, com aproximadamente 400 a 700 tokens e sobreposição de 50 a 100 tokens, ajustáveis conforme os resultados dos testes.

## 7. Estratégia de utilização das ferramentas

O EngMan Copilot contará com ferramentas especializadas para acessar informações estruturadas. A execução de uma ferramenta não garante que os dados sejam suficientes para concluir um diagnóstico. O modelo deverá informar limitações e solicitar avaliação humana quando necessário.
As ferramentas deverão respeitar os contratos definidos em `tools/tools_spec.json`.

| Ferramenta | Finalidade |
|---|---|
| `consultar_ativo_por_tag` | Localizar dados cadastrais do equipamento. |
| `consultar_historico_falhas` | Consultar ocorrências anteriores. |
| `consultar_procedimento` | Recuperar procedimentos relacionados ao sintoma. |
| `calcular_prioridade` | Apoiar a classificação de prioridade. |


## 8. Parâmetros iniciais do modelo

Os parâmetros abaixo são valores de configuração propostos para os primeiros experimentos.

| Parâmetro | Valor inicial | Justificativa |
|---|---|---|
| Temperatura | 0,2 | Reduzir variações desnecessárias nas respostas técnicas. |
| Máximo de tokens de saída | 800 | Permitir respostas objetivas, mas suficientemente explicativas. |
| Top-k de recuperação | 5 | Recuperar até cinco fragmentos relevantes inicialmente. |
| Sobreposição de chunks | 50–100 tokens | Preservar continuidade contextual. |

Os valores poderão ser ajustados após os testes do Eval Set.

## 9. Segurança, confiabilidade e controle

A arquitetura deverá contemplar:

- Validação de entrada e saída.
- Proteção contra prompt injection.
- Controle de acesso às fontes documentais.
- Identificação de dados simulados e reais.
- Registro das fontes utilizadas.
- Separação entre fatos, hipóteses e recomendações.
- Limitação do contexto da conversa.
- Validação humana das decisões operacionais.

O assistente não deverá executar ações físicas, autorizar intervenções ou substituir procedimentos oficiais.

## 10. Limitações da proposta

- Os componentes ainda não foram implementados.
- A escolha do modelo precisa ser validada experimentalmente.
- A base de conhecimento inicial é simulada.
- O desempenho depende da qualidade dos documentos e dos embeddings.
- A precisão das métricas depende da disponibilidade de dados operacionais.
- Não há integração com sistemas reais da Motiva nesta etapa.
- A classificação de prioridade depende de uma matriz validada pela Engenharia de Manutenção.

## 11. Conclusão

A proposta técnica do EngMan Copilot prioriza uma arquitetura modular, com execução local do modelo, recuperação contextualizada de documentos e ferramentas especializadas.

A combinação inicial de Llama 3.1 8B, Ollama e ChromaDB foi selecionada por sua viabilidade para prototipagem e facilidade de integração.

As alternativas Qwen2.5 7B e FAISS foram documentadas para permitir comparação e evolução técnica.

As decisões registradas deverão ser revisadas após a implementação e a avaliação do sistema com os casos definidos no arquivo `evals/sprint1_eval_set.json`.

## 12. Referências técnicas

- Meta. Llama 3.1 — documentação e modelos. https://www.llama.com/
- Qwen. Qwen2.5 — documentação e modelos. https://qwenlm.github.io/
- Ollama. Documentação oficial. https://ollama.com/
- Chroma. Documentação oficial. https://docs.trychroma.com/
- FAISS. Facebook AI Similarity Search. https://github.com/facebookresearch/faiss
- JSON Schema. Documentação oficial. https://json-schema.org/
