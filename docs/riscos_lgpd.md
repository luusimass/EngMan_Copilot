# Análise de Riscos, Ética e LGPD — EngMan Copilot

**Projeto:** EngMan Copilot — FIAP × Motiva Rodovias  
**Responsável:** Anna Luisa Santos de Lima  
**RM:** 575081  
**Turma:** 1CCPR  
**Recorte:** A — Diagnóstico e Confiabilidade  
**Versão:** 1.0

## 1. Objetivo

Este documento identifica os principais riscos relacionados ao desenvolvimento e à utilização do EngMan Copilot, um assistente inteligente voltado ao apoio da Engenharia de Manutenção no diagnóstico e na confiabilidade de ativos eletroeletrônicos rodoviários.

O objetivo é estabelecer medidas preventivas para reduzir erros de interpretação, respostas incorretas, exposição de informações e recomendações que possam comprometer a segurança operacional.

O EngMan Copilot deve atuar como ferramenta de apoio à análise técnica, sem substituir a avaliação dos profissionais responsáveis ou os procedimentos oficiais da empresa.

## 2. Identificação e mitigação dos riscos

### Risco 01 — Alucinação da inteligência artificial

**Descrição:** O modelo pode gerar informações incorretas ou inexistentes, como TAGs, modelos de equipamentos, históricos de falhas, métricas e procedimentos técnicos.

**Impacto:** Diagnósticos equivocados, decisões inadequadas de manutenção e perda de confiabilidade nas informações apresentadas.

**Mitigações:**
- Restringir as respostas às informações disponíveis na base de conhecimento.
- Exigir identificação das fontes utilizadas.
- Determinar no system prompt que o assistente nunca invente dados.
- Informar explicitamente quando uma informação não estiver disponível.
- Utilizar casos de avaliação da categoria `factual` e `dado_inexistente`.

**Componentes relacionados:** System Prompt, RAG, Base de Conhecimento e Eval Set.

### Risco 02 — Injeção de prompt (Prompt Injection)

**Descrição:** Um usuário pode tentar manipular o comportamento do assistente por meio de comandos que solicitem a desconsideração das instruções originais ou a divulgação de informações restritas.

**Impacto:** Respostas fora do escopo, exposição indevida de informações e descumprimento das regras estabelecidas para o sistema.

**Mitigações:**
- Manter as instruções principais protegidas e separadas das mensagens dos usuários.
- Não permitir que comandos externos substituam as regras do system prompt.
- Tratar documentos recuperados como fontes de informação, e não como instruções de controle.
- Avaliar tentativas de manipulação por meio de testes específicos de jailbreak.

**Componentes relacionados:** System Prompt, Arquitetura e Eval Set.

### Risco 03 — Risco operacional e de segurança

**Descrição:** O assistente pode apresentar orientações inadequadas para atividades que envolvam eletricidade, equipamentos energizados, trabalho em altura ou intervenções físicas.

**Impacto:** Acidentes, danos aos equipamentos, riscos à integridade dos profissionais e comprometimento da operação rodoviária.

**Mitigações:**
- Não fornecer instruções que substituam procedimentos oficiais de segurança.
- Não orientar intervenções elétricas ou físicas sem autorização e qualificação apropriadas.
- Encaminhar solicitações de risco aos profissionais responsáveis.
- Incluir testes específicos para situações de risco operacional.
- Reforçar que a ferramenta não substitui treinamentos, normas ou procedimentos oficiais.

**Componentes relacionados:** System Prompt, Guardrails e Eval Set.

### Risco 04 — Viés na priorização de manutenção

**Descrição:** A inteligência artificial pode priorizar incorretamente uma ocorrência devido a dados incompletos, critérios inconsistentes ou informações históricas pouco representativas.

**Impacto:** Alocação inadequada de recursos, atrasos em intervenções importantes e decisões que não refletem a criticidade real do ativo.

**Mitigações:**
- Utilizar uma matriz de criticidade documentada.
- Considerar os critérios disponíveis, como segurança, impacto operacional, disponibilidade e criticidade do equipamento.
- Identificar dados faltantes antes de recomendar uma prioridade.
- Apresentar a justificativa da classificação.
- Manter a decisão final sob responsabilidade do profissional de Engenharia de Manutenção.

**Componentes relacionados:** Base de Conhecimento, Ferramenta `calcular_prioridade` e System Prompt.

### Risco 05 — Exposição de dados pessoais e LGPD

**Descrição:** Documentos, registros de manutenção ou mensagens podem conter informações pessoais de funcionários ou terceiros que não sejam necessárias para o funcionamento do assistente.

**Impacto:** Exposição indevida de dados pessoais, violação de privacidade e possíveis desconformidades com a Lei Geral de Proteção de Dados Pessoais (Lei nº 13.709/2018).

**Mitigações:**
- Evitar o armazenamento de dados pessoais desnecessários.
- Remover ou anonimizar informações pessoais antes da inclusão de documentos na base de conhecimento.
- Restringir o acesso às informações conforme a necessidade de utilização.
- Não utilizar dados pessoais de terceiros nas respostas.
- Definir critérios de retenção e descarte de informações.

**Componentes relacionados:** Base de Conhecimento, Arquitetura e Política de Dados.

### Risco 06 — Exposição de informações operacionais confidenciais

**Descrição:** O assistente pode recuperar ou apresentar informações internas que não deveriam ser disponibilizadas a determinados usuários.

**Impacto:** Divulgação de informações estratégicas, operacionais ou técnicas, podendo comprometer a segurança e a confidencialidade da operação.

**Mitigações:**
- Aplicar controle de acesso aos documentos e às ferramentas.
- Separar informações públicas, internas e restritas.
- Não inserir informações confidenciais sem autorização.
- Registrar as fontes utilizadas nas consultas.
- Limitar o acesso conforme o perfil e a finalidade de utilização.

**Componentes relacionados:** Arquitetura, RAG e Base de Conhecimento.

### Risco 07 — Excesso de confiança nas respostas da IA

**Descrição:** O usuário pode interpretar uma hipótese ou recomendação do assistente como um diagnóstico definitivo, deixando de realizar a validação técnica necessária.

**Impacto:** Decisões incorretas, intervenções inadequadas e dependência excessiva da ferramenta.

**Mitigações:**
- Diferenciar claramente fatos, hipóteses e recomendações.
- Apresentar o nível de confiança da resposta e sua justificativa.
- Informar limitações e dados faltantes.
- Exigir validação humana para decisões de manutenção.
- Não apresentar hipóteses como causas confirmadas.

**Componentes relacionados:** System Prompt, Formato de Resposta e Eval Set.

### Risco 08 — Excesso de contexto e perda de informações relevantes

**Descrição:** Conversas extensas ou grandes volumes de documentos podem ultrapassar a capacidade de contexto do modelo, ocasionando perda de informações importantes ou mistura de dados de diferentes ativos.

**Impacto:** Respostas inconsistentes, associação incorreta de históricos e perda de precisão nos diagnósticos.

**Mitigações:**
- Estabelecer limite de contexto para as conversas.
- Recuperar informações relevantes por TAG e metadados.
- Priorizar documentos relacionados à solicitação atual.
- Resumir o histórico da conversa quando necessário.
- Não misturar informações de ativos diferentes.
- Solicitar novamente informações quando o contexto não estiver disponível.

**Componentes relacionados:** Arquitetura, RAG, System Prompt e Eval Set.

## 3. Diretrizes de privacidade e proteção de dados

O desenvolvimento do EngMan Copilot considera os princípios de proteção de dados estabelecidos pela Lei Geral de Proteção de Dados Pessoais (LGPD).

As principais diretrizes são:

1. **Finalidade:** utilizar informações exclusivamente para apoiar as atividades de diagnóstico e confiabilidade previstas no escopo do projeto.
2. **Necessidade:** limitar a utilização de dados ao mínimo necessário para a finalidade estabelecida.
3. **Segurança:** adotar medidas para evitar acessos não autorizados e incidentes envolvendo informações.
4. **Prevenção:** identificar riscos antes da utilização dos documentos e das ferramentas.
5. **Transparência:** informar quando os dados utilizados forem simulados ou quando uma informação não estiver disponível.
6. **Responsabilidade:** manter a utilização da ferramenta sujeita à supervisão dos profissionais responsáveis.

A base de conhecimento proposta não deve conter dados pessoais desnecessários, imagens de pessoas, informações contratuais sensíveis ou documentos confidenciais sem autorização.

## 4. Responsabilidade e supervisão humana

O EngMan Copilot possui caráter consultivo. Suas respostas devem auxiliar os profissionais na consulta de informações, análise de históricos e identificação de possíveis causas de falhas.

A ferramenta não possui autoridade para liberar equipamentos, autorizar intervenções físicas, substituir procedimentos de segurança ou emitir laudos técnicos e documentos de responsabilidade profissional.

Toda decisão relacionada à execução de atividades de manutenção deve ser validada pelo profissional responsável, conforme os procedimentos e critérios oficiais aplicáveis.

## 5. Considerações finais

A identificação e a mitigação dos riscos são fundamentais para garantir que o EngMan Copilot seja utilizado de maneira segura, responsável e confiável.

As medidas propostas devem ser consideradas desde a arquitetura até a avaliação das respostas, mantendo consistência entre o system prompt, a base de conhecimento, as ferramentas e os casos de teste.

A análise de riscos deverá ser revisada conforme o projeto evoluir e novas funcionalidades forem incorporadas.

## 6. Referências

- FIAP. Challenge Integrador — EngMan Copilot: Documentação e orientações da Sprint 01.
- BRASIL. Lei nº 13.709, de 14 de agosto de 2018. Lei Geral de Proteção de Dados Pessoais (LGPD). Disponível em: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm
- OWASP Foundation. OWASP Top 10 for Large Language Model Applications. Disponível em: https://genai.owasp.org/
