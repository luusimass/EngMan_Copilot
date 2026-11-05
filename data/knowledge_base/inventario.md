# Base de Conhecimento — EngMan Copilot

> **AVISO:** Este documento contém exclusivamente dados fictícios para fins acadêmicos que foram gerados por IA.

## 1. Objetivo da base de conhecimento
A base de conhecimento tem como objetivo fornecer informações estruturadas para apoiar o EngMan Copilot na consulta de ativos, análise de históricos de falhas, identificação de possíveis causas e recomendação de intervenções de manutenção. O conteúdo está organizado em:

1. Catálogo simulado de ativos.
2. Histórico simulado de falhas.
3. Plano de manutenção preventiva.
4. Procedimentos operacionais simulados (POPs).
5. Fichas técnicas ilustrativas.
6. Matriz de criticidade.
7. Glossário de Engenharia de Confiabilidade.
8. Requisitos gerais de segurança.
9. Contexto do desafio.
10. Boletins simulados de ocorrência.

## 2. Catálogo de ativos
O catálogo abaixo contém 30 ativos fictícios, com foco em equipamentos de CFTV e infraestrutura eletroeletrônica rodoviária.

| TAG | Equipamento | Categoria | Localização fictícia | Criticidade |
|---|---|---|---|---|
| CFTV-0412 | Câmera PTZ | CFTV | KM 412 | Alta |
| CFTV-0413 | Câmera fixa | CFTV | KM 413 | Média |
| CFTV-0414 | Câmera PTZ | CFTV | KM 414 | Alta |
| CFTV-0415 | Câmera fixa | CFTV | KM 415 | Média |
| CFTV-0416 | Câmera PTZ | CFTV | KM 416 | Alta |
| CFTV-0420 | Câmera fixa | CFTV | KM 420 | Média |
| CFTV-0421 | Câmera PTZ | CFTV | KM 421 | Alta |
| CFTV-0422 | Câmera fixa | CFTV | KM 422 | Média |
| CFTV-0423 | Câmera PTZ | CFTV | KM 423 | Alta |
| CFTV-0424 | Câmera fixa | CFTV | KM 424 | Média |
| CFTV-0430 | Câmera PTZ | CFTV | KM 430 | Alta |
| CFTV-0431 | Câmera fixa | CFTV | KM 431 | Média |
| CFTV-0432 | Câmera PTZ | CFTV | KM 432 | Alta |
| CFTV-0433 | Câmera fixa | CFTV | KM 433 | Média |
| CFTV-0434 | Câmera PTZ | CFTV | KM 434 | Alta |
| CFTV-0440 | Câmera fixa | CFTV | KM 440 | Média |
| CFTV-0441 | Câmera PTZ | CFTV | KM 441 | Alta |
| CFTV-0442 | Câmera fixa | CFTV | KM 442 | Média |
| CFTV-0443 | Câmera PTZ | CFTV | KM 443 | Alta |
| CFTV-0444 | Câmera fixa | CFTV | KM 444 | Média |
| NVR-0412 | Gravador de vídeo | Gravação | KM 412 | Alta |
| NVR-0420 | Gravador de vídeo | Gravação | KM 420 | Alta |
| NVR-0430 | Gravador de vídeo | Gravação | KM 430 | Alta |
| SW-0412 | Switch de rede | Comunicação | KM 412 | Média |
| SW-0420 | Switch de rede | Comunicação | KM 420 | Média |
| SW-0430 | Switch de rede | Comunicação | KM 430 | Média |
| UPS-0412 | Nobreak | Energia | KM 412 | Alta |
| UPS-0420 | Nobreak | Energia | KM 420 | Alta |
| UPS-0430 | Nobreak | Energia | KM 430 | Alta |
| SENSOR-0412 | Sensor ambiental | Monitoramento | KM 412 | Baixa |

**Observações:**
- Todos os TAGs são identificadores fictícios.
- A localização em quilômetros é ilustrativa.
- A criticidade é uma classificação acadêmica simulada.
- Fabricante, modelo, número de série e características específicas não foram definidos quando não há dados disponíveis.
- O assistente não deve deduzir essas informações apenas com base no TAG.

## 3. Histórico simulado de falhas

O histórico contém 50 registros fictícios para permitir testes de consulta, identificação de recorrência e análise de sintomas.

Os registros não representam falhas reais. As descrições são exemplos de dados que poderiam ser armazenados em um sistema de manutenção.

| ID | TAG | Data | Sintoma registrado | Intervenção registrada |
|---|---|---|---|---|
| F001 | CFTV-0412 | 2026-10-10 | Perda de imagem noturna | Inspeção registrada |
| F002 | CFTV-0412 | 2026-10-25 | Perda de imagem noturna | Verificação registrada |
| F003 | CFTV-0412 | 2026-08-15 | Instabilidade de imagem | Inspeção registrada |
| F004 | CFTV-0412 | 2026-06-20 | Interrupção de transmissão | Verificação de conexão registrada |
| F005 | CFTV-0412 | 2026-04-12 | Imagem intermitente | Inspeção registrada |
| F006 | CFTV-0413 | 2026-10-12 | Imagem desfocada | Limpeza registrada |
| F007 | CFTV-0413 | 2026-08-19 | Oscilação de imagem | Inspeção registrada |
| F008 | CFTV-0413 | 2026-06-08 | Perda temporária de imagem | Verificação registrada |
| F009 | CFTV-0413 | 2026-04-17 | Imagem com baixa nitidez | Limpeza registrada |
| F010 | CFTV-0413 | 2026-02-11 | Falha de transmissão | Verificação registrada |
| F011 | CFTV-0414 | 2026-10-14 | Falha no movimento PTZ | Inspeção registrada |
| F012 | CFTV-0414 | 2026-08-21 | Movimento irregular | Verificação registrada |
| F013 | CFTV-0414 | 2026-06-13 | Perda de comunicação | Inspeção registrada |
| F014 | CFTV-0414 | 2026-04-22 | Imagem congelada | Verificação registrada |
| F015 | CFTV-0414 | 2026-02-18 | Instabilidade de movimento | Inspeção registrada |
| F016 | CFTV-0415 | 2026-10-16 | Imagem escura | Inspeção registrada |
| F017 | CFTV-0415 | 2026-08-23 | Perda de imagem | Verificação registrada |
| F018 | CFTV-0415 | 2026-06-15 | Imagem desfocada | Limpeza registrada |
| F019 | CFTV-0415 | 2026-04-25 | Oscilação de sinal | Inspeção registrada |
| F020 | CFTV-0415 | 2026-02-20 | Falha de transmissão | Verificação registrada |
| F021 | CFTV-0416 | 2026-10-18 | Movimento PTZ irregular | Inspeção registrada |
| F022 | CFTV-0416 | 2026-08-25 | Perda de comunicação | Verificação registrada |
| F023 | CFTV-0416 | 2026-06-17 | Imagem intermitente | Inspeção registrada |
| F024 | CFTV-0416 | 2026-04-27 | Falha de posicionamento | Verificação registrada |
| F025 | CFTV-0416 | 2026-02-22 | Interrupção de transmissão | Inspeção registrada |
| F026 | CFTV-0420 | 2026-10-20 | Imagem com baixa nitidez | Limpeza registrada |
| F027 | CFTV-0420 | 2026-08-27 | Falha de transmissão | Verificação registrada |
| F028 | CFTV-0420 | 2026-06-19 | Imagem congelada | Inspeção registrada |
| F029 | CFTV-0420 | 2026-04-29 | Oscilação de imagem | Verificação registrada |
| F030 | CFTV-0420 | 2026-02-24 | Perda temporária de imagem | Inspeção registrada |
| F031 | CFTV-0421 | 2026-10-22 | Falha no movimento PTZ | Inspeção registrada |
| F032 | CFTV-0421 | 2026-08-29 | Imagem intermitente | Verificação registrada |
| F033 | CFTV-0421 | 2026-06-21 | Perda de comunicação | Inspeção registrada |
| F034 | CFTV-0421 | 2026-04-30 | Movimento irregular | Verificação registrada |
| F035 | CFTV-0421 | 2026-02-26 | Imagem congelada | Inspeção registrada |
| F036 | CFTV-0422 | 2026-10-24 | Imagem desfocada | Limpeza registrada |
| F037 | CFTV-0422 | 2026-08-31 | Perda de imagem | Verificação registrada |
| F038 | CFTV-0422 | 2026-06-23 | Oscilação de sinal | Inspeção registrada |
| F039 | CFTV-0422 | 2026-05-02 | Imagem escura | Verificação registrada |
| F040 | CFTV-0422 | 2026-02-28 | Falha de transmissão | Inspeção registrada |
| F041 | CFTV-0423 | 2026-10-26 | Perda de comunicação | Inspeção registrada |
| F042 | CFTV-0423 | 2026-09-01 | Movimento PTZ irregular | Verificação registrada |
| F043 | CFTV-0423 | 2026-06-25 | Imagem intermitente | Inspeção registrada |
| F044 | CFTV-0423 | 2026-05-04 | Falha de posicionamento | Verificação registrada |
| F045 | CFTV-0423 | 2026-03-02 | Perda de imagem | Inspeção registrada |
| F046 | CFTV-0424 | 2026-10-28 | Imagem escura | Inspeção registrada |
| F047 | CFTV-0424 | 2026-09-03 | Imagem desfocada | Limpeza registrada |
| F048 | CFTV-0424 | 2026-06-27 | Falha de transmissão | Verificação registrada |
| F049 | CFTV-0424 | 2026-05-06 | Oscilação de imagem | Inspeção registrada |
| F050 | CFTV-0424 | 2026-03-04 | Perda temporária de imagem | Verificação registrada |

**Limitações do histórico:**
- Os registros não possuem confirmação de causa raiz.
- Não há tempos de reparo ou tempos de operação associados.
- As intervenções são descrições ilustrativas, não instruções de execução.
- Não é possível calcular MTTR, MTBF ou taxas de falha confiáveis apenas com essas informações.
- O histórico de F001 e F002 permite testar a identificação de duas ocorrências de perda de imagem noturna no C
