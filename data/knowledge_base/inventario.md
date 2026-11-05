# Base de Conhecimento — EngMan Copilot

> **AVISO:** Todos os dados apresentados são fictícios, gerados por inteligência artificial e destinados exclusivamente a fins acadêmicos.

## 1. Objetivo da base de conhecimento

A base de conhecimento reúne informações estruturadas para apoiar o EngMan Copilot na consulta de ativos eletroeletrônicos rodoviários, análise de históricos de falhas, localização de procedimentos e avaliação de criticidade.

O conteúdo foi organizado para permitir que o assistente:

- Identifique ativos por TAG.
- Consulte características técnicas cadastradas.
- Recupere ocorrências anteriores.
- Identifique padrões de falha.
- Localize procedimentos relacionados aos sintomas.
- Apoie a classificação de prioridade.
- Consulte conceitos e métricas de Engenharia de Confiabilidade.

A base deve ser atualizada somente com documentos autorizados e informações verificáveis.

## 2. Inventário simulado de ativos

O catálogo abaixo contém 30 ativos fictícios, distribuídos em diferentes categorias de equipamentos eletroeletrônicos.

| TAG | Ativo | Categoria | Localização simulada | Criticidade |
|---|---|---|---|---|
| CFTV-0412 | Câmera PTZ | CFTV | Km 412 | Alta |
| CFTV-0413 | Câmera fixa | CFTV | Km 413 | Média |
| CFTV-0414 | Câmera PTZ | CFTV | Km 414 | Alta |
| CFTV-0415 | Câmera fixa | CFTV | Km 415 | Média |
| CFTV-0416 | Câmera PTZ | CFTV | Km 416 | Alta |
| CFTV-0417 | Câmera fixa | CFTV | Km 417 | Média |
| CFTV-0418 | Câmera PTZ | CFTV | Km 418 | Alta |
| CFTV-0419 | Câmera fixa | CFTV | Km 419 | Média |
| CFTV-0420 | Câmera PTZ | CFTV | Km 420 | Alta |
| CFTV-0421 | Câmera fixa | CFTV | Km 421 | Média |
| RAD-0101 | Sensor de tráfego | Monitoramento | Km 401 | Alta |
| RAD-0102 | Sensor de tráfego | Monitoramento | Km 402 | Média |
| RAD-0103 | Sensor de tráfego | Monitoramento | Km 403 | Alta |
| RAD-0104 | Sensor de tráfego | Monitoramento | Km 404 | Média |
| RAD-0105 | Sensor de tráfego | Monitoramento | Km 405 | Média |
| PMV-0201 | Painel de mensagem variável | Sinalização | Km 410 | Alta |
| PMV-0202 | Painel de mensagem variável | Sinalização | Km 411 | Alta |
| PMV-0203 | Painel de mensagem variável | Sinalização | Km 412 | Média |
| PMV-0204 | Painel de mensagem variável | Sinalização | Km 413 | Alta |
| PMV-0205 | Painel de mensagem variável | Sinalização | Km 414 | Média |
| OCR-0301 | Leitor OCR | Arrecadação | Praça A | Alta |
| OCR-0302 | Leitor OCR | Arrecadação | Praça B | Alta |
| OCR-0303 | Leitor OCR | Arrecadação | Praça C | Média |
| OCR-0304 | Leitor OCR | Arrecadação | Praça D | Alta |
| OCR-0305 | Leitor OCR | Arrecadação | Praça E | Média |
| REDE-0501 | Switch de comunicação | Rede | Sala técnica A | Alta |
| REDE-0502 | Switch de comunicação | Rede | Sala técnica B | Alta |
| REDE-0503 | Roteador industrial | Rede | Sala técnica C | Alta |
| REDE-0504 | Switch de comunicação | Rede | Sala técnica D | Média |
| REDE-0505 | Roteador industrial | Rede | Sala técnica E | Alta |

**Observação:** A classificação de criticidade é fictícia e serve apenas para demonstrar o funcionamento da ferramenta `calcular_prioridade`. Em uma aplicação real, os critérios deverão ser definidos e validados pela Engenharia de Manutenção.

## 3. Fichas técnicas resumidas

As fichas abaixo apresentam características genéricas para os equipamentos simulados. Não correspondem a modelos comerciais específicos.

### 3.1 Câmera PTZ — CFTV

- **Categoria:** Monitoramento por vídeo.
- **Função:** Capturar imagens e permitir movimentação horizontal, vertical e zoom.
- **Componentes genéricos:** Lente, sensor de imagem, mecanismo de movimentação, alimentação e interface de comunicação.
- **Sintomas possíveis:** Perda de imagem, imagem intermitente, falha de movimentação, perda de comunicação e baixa qualidade de imagem.
- **Informações necessárias para diagnóstico:** TAG, horário, duração, condições ambientais, registros de comunicação e histórico de ocorrências.
- **Limitação:** Não é possível confirmar defeitos de componentes apenas pela descrição de um sintoma.

### 3.2 Câmera fixa — CFTV

- **Categoria:** Monitoramento por vídeo.
- **Função:** Capturar imagens de uma área determinada.
- **Componentes genéricos:** Sensor de imagem, lente, alimentação e interface de comunicação.
- **Sintomas possíveis:** Imagem indisponível, baixa definição, interferência e perda de conexão.
- **Informações necessárias:** TAG, localização, horário, condição de iluminação e histórico.

### 3.3 Sensor de tráfego

- **Categoria:** Monitoramento de tráfego.
- **Função:** Coletar informações relacionadas ao fluxo de veículos.
- **Sintomas possíveis:** Ausência de dados, leituras inconsistentes e perda de comunicação.
- **Informações necessárias:** TAG, período de indisponibilidade, registros de leitura e comunicação.

### 3.4 Painel de mensagem variável (PMV)

- **Categoria:** Sinalização.
- **Função:** Exibir mensagens e informações aos usuários da rodovia.
- **Sintomas possíveis:** Falha de exibição, caracteres incorretos, perda de comunicação e indisponibilidade.
- **Informações necessárias:** TAG, mensagem esperada, mensagem exibida e registros do sistema.

### 3.5 Leitor OCR

- **Categoria:** Arrecadação e identificação.
- **Função:** Realizar reconhecimento óptico de caracteres em imagens.
- **Sintomas possíveis:** Baixa taxa de reconhecimento, leitura incompleta e indisponibilidade.
- **Informações necessárias:** TAG, período, condições de captura e registros de leitura.

### 3.6 Equipamentos de rede

- **Categoria:** Comunicação.
- **Função:** Permitir comunicação entre dispositivos e sistemas.
- **Sintomas possíveis:** Perda de conectividade, latência elevada, instabilidade e indisponibilidade.
- **Informações necessárias:** TAG, registros de conexão, período, topologia disponível e histórico.

## 4. Histórico simulado de falhas

A tabela contém 50 registros sintéticos de ocorrências distribuídos entre dez ativos. Os registros são exemplos para avaliação de consultas históricas e identificação de recorrência.

| ID | TAG | Data | Sintoma registrado | Intervenção registrada |
|---|---|---|---|---|
| H001 | CFTV-0412 | 2026-10-12 | Perda de imagem noturna | Inspeção registrada |
| H002 | CFTV-0412 | 2026-10-28 | Perda de imagem noturna | Verificação de comunicação |
| H003 | CFTV-0412 | 2026-09-15 | Oscilação de imagem | Inspeção registrada |
| H004 | CFTV-0412 | 2026-08-20 | Perda temporária de conexão | Reinicialização registrada |
| H005 | CFTV-0412 | 2026-07-10 | Imagem com baixa definição | Verificação registrada |
| H006 | CFTV-0413 | 2026-10-05 | Imagem indisponível | Inspeção registrada |
| H007 | CFTV-0413 | 2026-09-11 | Oscilação de imagem | Verificação registrada |
| H008 | CFTV-0413 | 2026-08-16 | Perda de comunicação | Inspeção registrada |
| H009 | CFTV-0413 | 2026-07-22 | Imagem com baixa definição | Limpeza registrada |
| H010 | CFTV-0413 | 2026-06-18 | Indisponibilidade temporária | Verificação registrada |
| H011 | CFTV-0414 | 2026-10-09 | Falha de movimentação PTZ | Inspeção registrada |
| H012 | CFTV-0414 | 2026-09-14 | Perda de imagem | Verificação registrada |
| H013 | CFTV-0414 | 2026-08-19 | Perda de comunicação | Inspeção registrada |
| H014 | CFTV-0414 | 2026-07-21 | Oscilação de imagem | Verificação registrada |
| H015 | CFTV-0414 | 2026-06-12 | Falha intermitente | Inspeção registrada |
| H016 | RAD-0101 | 2026-10-03 | Ausência de dados de tráfego | Inspeção registrada |
| H017 | RAD-0101 | 2026-09-08 | Leituras inconsistentes | Verificação registrada |
| H018 | RAD-0101 | 2026-08-13 | Perda de comunicação | Inspeção registrada |
| H019 | RAD-0101 | 2026-07-17 | Indisponibilidade temporária | Verificação registrada |
| H020 | RAD-0101 | 2026-06-21 | Oscilação nas leituras | Inspeção registrada |
| H021 | RAD-0102 | 2026-10-07 | Leituras inconsistentes | Verificação registrada |
| H022 | RAD-0102 | 2026-09-12 | Ausência de dados | Inspeção registrada |
| H023 | RAD-0102 | 2026-08-18 | Perda de comunicação | Verificação registrada |
| H024 | RAD-0102 | 2026-07-23 | Falha intermitente | Inspeção registrada |
| H025 | RAD-0102 | 2026-06-25 | Dados incompletos | Verificação registrada |
| H026 | PMV-0201 | 2026-10-02 | Falha de exibição | Inspeção registrada |
| H027 | PMV-0201 | 2026-09-06 | Perda de comunicação | Verificação registrada |
| H028 | PMV-0201 | 2026-08-11 | Caracteres incorretos | Inspeção registrada |
| H029 | PMV-0201 | 2026-07-15 | Indisponibilidade temporária | Verificação registrada |
| H030 | PMV-0201 | 2026-06-20 | Falha de atualização | Inspeção registrada |
| H031 | PMV-0202 | 2026-10-06 | Mensagem não exibida | Inspeção registrada |
| H032 | PMV-0202 | 2026-09-10 | Falha de atualização | Verificação registrada |
| H033 | PMV-0202 | 2026-08-15 | Perda de comunicação | Inspeção registrada |
| H034 | PMV-0202 | 2026-07-19 | Caracteres incorretos | Verificação registrada |
| H035 | PMV-0202 | 2026-06-23 | Indisponibilidade temporária | Inspeção registrada |
| H036 | OCR-0301 | 2026-10-04 | Baixa taxa de reconhecimento | Inspeção registrada |
| H037 | OCR-0301 | 2026-09-09 | Leitura incompleta | Verificação registrada |
| H038 | OCR-0301 | 2026-08-14 | Falha de comunicação | Inspeção registrada |
| H039 | OCR-0301 | 2026-07-18 | Reconhecimento inconsistente | Verificação registrada |
| H040 | OCR-0301 | 2026-06-22 | Indisponibilidade temporária | Inspeção registrada |
| H041 | REDE-0501 | 2026-10-08 | Perda de conectividade | Inspeção registrada |
| H042 | REDE-0501 | 2026-09-13 | Latência elevada | Verificação registrada |
| H043 | REDE-0501 | 2026-08-17 | Instabilidade de comunicação | Inspeção registrada |
| H044 | REDE-0501 | 2026-07-20 | Perda temporária de conexão | Verificação registrada |
| H045 | REDE-0501 | 2026-06-24 | Indisponibilidade temporária | Inspeção registrada |
| H046 | REDE-0502 | 2026-10-10 | Perda de conectividade | Inspeção registrada |
| H047 | REDE-0502 | 2026-09-16 | Instabilidade de comunicação | Verificação registrada |
| H048 | REDE-0502 | 2026-08-21 | Latência elevada | Inspeção registrada |
| H049 | REDE-0502 | 2026-07-25 | Perda de conexão | Verificação registrada |
| H050 | REDE-0502 | 2026-06-28 | Indisponibilidade temporária | Inspeção registrada |

### 4.1 Exemplo de análise de recorrência

**Ativo:** CFTV-0412

**Período analisado:** últimos 30 dias de referência, considerando os registros de 12/10/2026 e 28/10/2026.

**Evidências disponíveis:**
- Duas ocorrências de perda de imagem noturna.
- Repetição do sintoma em datas diferentes.
- Uma inspeção registrada e uma verificação de comunicação registrada.

**Interpretação:** Os registros indicam repetição do sintoma no período analisado. Isso permite levantar a hipótese de uma falha recorrente, mas não confirma sua causa.

**Dados ainda necessários:**
- Resultado detalhado das inspeções.
- Condições ambientais durante as ocorrências.
- Registros de alimentação e comunicação.
- Confirmação técnica da causa.

## 5. Plano de manutenção preventiva simulado

**Identificador:** PMP-CFTV-001  
**Categoria:** Câmeras de monitoramento  
**Finalidade:** Demonstrar a organização de um plano preventivo para ativos CFTV.

| Atividade | Objetivo | Periodicidade ilustrativa | Registro esperado |
|---|---|---|---|
| Inspeção visual | Identificar alterações externas | Mensal | Condição visual |
| Verificação de imagem | Avaliar disponibilidade e qualidade | Mensal | Resultado da verificação |
| Verificação de comunicação | Identificar instabilidades registradas | Mensal | Estado da conexão |
| Análise do histórico | Identificar repetição de sintomas | Trimestral | Relatório de ocorrências |
| Revisão técnica | Avaliar necessidade de intervenção | Conforme análise | Parecer do responsável |

**Observação:** As periodicidades são exemplos acadêmicos. Não devem ser interpretadas como cronograma oficial ou recomendação de manutenção da Motiva.

## 6. Procedimentos operacionais simulados (POPs)

Os procedimentos abaixo são resumos conceituais para demonstrar a recuperação de documentos pela base de conhecimento. Não são instruções oficiais de execução.

### POP-001 — Registro de ocorrência de CFTV

**Objetivo:** Padronizar a documentação de ocorrências relacionadas aos equipamentos de monitoramento.

**Informações necessárias:**
1. TAG do ativo.
2. Localização.
3. Data e horário.
4. Descrição do sintoma.
5. Condições em que o sintoma ocorreu.
6. Evidências disponíveis.
7. Responsável pelo registro, conforme sistema autorizado.

**Resultado esperado:** Registro organizado e rastreável da ocorrência.

### POP-002 — Consulta de histórico de falhas

**Objetivo:** Orientar a análise documental de ocorrências anteriores.

**Informações necessárias:**
1. Identificação do ativo por TAG.
2. Período de consulta.
3. Descrição das ocorrências.
4. Intervenções registradas.
5. Resultados documentados.

**Resultado esperado:** Histórico consolidado, com identificação de possíveis repetições de sintomas.

### POP-003 — Avaliação de criticidade e priorização

**Objetivo:** Apoiar a avaliação de prioridade das ocorrências.

**Critérios considerados:**
1. Impacto potencial à segurança.
2. Impacto na operação.
3. Disponibilidade do ativo.
4. Criticidade cadastrada.
5. Recorrência documentada.
6. Dados faltantes.

**Resultado esperado:** Classificação justificada, sujeita à validação do profissional responsável.

## 7. Matriz de criticidade simulada

A matriz abaixo demonstra como os ativos podem ser classificados para fins de organização e priorização.

| Nível | Descrição ilustrativa | Tratamento esperado |
|---|---|---|
| Baixa | Impacto operacional limitado | Acompanhamento e avaliação conforme planejamento |
| Média | Impacto moderado na disponibilidade | Avaliação técnica e programação de intervenção |
| Alta | Impacto significativo na operação ou monitoramento | Análise prioritária pelo responsável |
| Crítica | Potencial impacto grave à segurança ou continuidade operacional | Encaminhamento imediato conforme procedimentos oficiais |

A classificação de prioridade não deve ser definida exclusivamente pelo modelo de IA. A ferramenta deve apresentar critérios e justificativas, considerando a matriz cadastrada e as informações disponíveis.

## 8. Glossário de Engenharia de Confiabilidade

| Termo | Definição |
|---|---|
| Ativo | Equipamento ou sistema utilizado em uma operação. |
| Falha | Evento em que um ativo deixa de cumprir sua função requerida. |
| Disponibilidade | Capacidade de um ativo estar em condição de operação quando necessário. |
| Confiabilidade | Probabilidade de um ativo desempenhar sua função sem falhar durante determinado intervalo, sob condições estabelecidas. |
| TAG | Identificador único utilizado para localizar um ativo. |
| MTBF | Tempo médio entre falhas de um equipamento reparável. |
| MTTR | Tempo médio necessário para reparar um equipamento. |
| λ (lambda) | Taxa de falhas, que pode ser estimada por falhas divididas pelo tempo de operação em um modelo simplificado. |
| R(t) | Função de confiabilidade: probabilidade de sobrevivência sem falha até o tempo t. |
| RGA | Reliability Growth Analysis, análise de crescimento da confiabilidade ao longo do desenvolvimento ou das ações de melhoria. |
| LDA | Life Data Analysis, análise estatística de dados de vida e tempos até falha. |
| RAG | Retrieval-Augmented Generation, abordagem que recupera informações de uma base para contextualizar respostas de um modelo generativo. |
| Criticidade | Avaliação da importância de um ativo considerando seus impactos e consequências de falha. |
| Manutenção corretiva | Intervenção realizada após a identificação de uma falha. |
| Manutenção preventiva | Intervenção planejada para reduzir a probabilidade de falha ou degradação. |
| Manutenção baseada em condição | Estratégia que utiliza indicadores e condições observadas para orientar intervenções. |

### 8.1 Fórmulas ilustrativas

**Taxa de falhas simplificada:**

\[
\lambda = \frac{N}{T}
\]

Onde:
- \(N\) = quantidade de falhas observadas.
- \(T\) = tempo total de operação observado.

**Confiabilidade para taxa de falhas constante:**

\[
R(t) = e^{-\lambda t}
\]

Essas expressões dependem de premissas estatísticas. A ferramenta não deve calcular ou apresentar resultados sem os dados necessários e sem explicitar as premissas adotadas.

RGA e LDA exigem métodos e dados específicos. Não devem ser tratados como uma única fórmula ou calculados apenas a partir de uma descrição textual de falha.

## 9. Resumo de requisitos de segurança

O assistente deve respeitar os seguintes limites:

- Não orientar intervenções em equipamentos energizados.
- Não fornecer instruções que substituam procedimentos oficiais de segurança.
- Não orientar atividades em altura sem considerar os requisitos e autorizações aplicáveis.
- Não autorizar bloqueios, liberações ou intervenções físicas.
- Não emitir laudos técnicos ou assumir responsabilidade profissional.
- Encaminhar situações de risco ao responsável competente.
- Diferenciar informações documentadas de hipóteses.

Este resumo não substitui normas regulamentadoras, treinamentos ou procedimentos oficiais.

## 10. Boletins simulados de ocorrência

Os dez boletins abaixo complementam o histórico com exemplos de descrições textuais que podem ser utilizadas em consultas por similaridade.

| Boletim | TAG | Descrição resumida | Categoria |
|---|---|---|---|
| B001 | CFTV-0412 | Perda de imagem durante o período noturno | Imagem |
| B002 | CFTV-0413 | Oscilação na transmissão de vídeo | Comunicação |
| B003 | CFTV-0414 | Falha de movimentação da câmera PTZ | Movimentação |
| B004 | RAD-0101 | Ausência de registros de fluxo de veículos | Dados |
| B005 | RAD-0102 | Leituras inconsistentes do sensor | Medição |
| B006 | PMV-0201 | Painel sem atualização de mensagem | Sinalização |
| B007 | PMV-0202 | Caracteres incorretos na exibição | Exibição |
| B008 | OCR-0301 | Redução na taxa de reconhecimento | Reconhecimento |
| B009 | REDE-0501 | Instabilidade de comunicação | Rede |
| B010 | REDE-0502 | Perda temporária de conectividade | Rede |

Cada boletim deve ser tratado como registro independente. A similaridade entre descrições não comprova que as causas das falhas sejam iguais.

## 11. Organização e recuperação dos documentos (RAG)

Para permitir a recuperação de informações relevantes, a base deve ser dividida em documentos e fragmentos menores, preservando o contexto de cada informação.

### 11.1 Metadados recomendados

| Metadado | Finalidade |
|---|---|
| `document_id` | Identificação única do documento |
| `document_type` | Tipo de documento |
| `tag` | Identificação do ativo relacionado |
| `category` | Categoria do equipamento |
| `date` | Data do registro |
| `criticality` | Nível de criticidade |
| `source` | Origem da informação |
| `is_synthetic` | Identifica se o dado é simulado |
| `version` | Versão do documento |

### 11.2 Estratégia de fragmentação (chunking)

A proposta inicial é utilizar fragmentos de aproximadamente 400 a 700 tokens, com sobreposição de 50 a 100 tokens quando necessário.

Essa configuração busca preservar o contexto das informações sem recuperar documentos excessivamente extensos.

A fragmentação deverá respeitar a estrutura dos documentos:

- Inventário: separar por ativo ou grupo de ativos.
- Histórico: separar por TAG e período.
- Procedimentos: separar por objetivo, seção e atividade.
- Fichas técnicas: separar por equipamento.
- Glossário: manter conceitos completos.
- Matriz de criticidade: preservar critérios e respectivas classificações.

Os valores são parâmetros iniciais e devem ser avaliados durante a implementação.

### 11.3 Filtros de recuperação

A recuperação deverá priorizar:

1. Correspondência exata de TAG, quando informada.
2. Categoria do equipamento.
3. Tipo de documento solicitado.
4. Período de ocorrência.
5. Criticidade, quando relevante.
6. Identificação da origem e da condição de dado simulado ou real.

O assistente não deverá combinar registros de ativos diferentes sem deixar explícita a distinção.

## 12. Limitações da base de conhecimento

- Todos os registros específicos apresentados são simulados.
- Não há integração com sistemas operacionais reais.
- Os procedimentos são exemplos acadêmicos, não documentos oficiais.
- As classificações de criticidade são ilustrativas.
- Os históricos não permitem confirmar causas definitivas.
- As fichas técnicas não representam fabricantes ou modelos específicos.
- As métricas de confiabilidade dependem de dados operacionais válidos e premissas estatísticas apropriadas.

## 13. Referências

- FIAP. Challenge Integrador — EngMan Copilot: briefing e orientações da Sprint 01.
- BRASIL. Lei nº 13.709/2018 — Lei Geral de Proteção de Dados Pessoais.
- Materiais acadêmicos de Engenharia de Confiabilidade e manutenção utilizados como referência conceitual.

---

**Fim do documento — Base de Conhecimento Simulada do EngMan Copilot.**
