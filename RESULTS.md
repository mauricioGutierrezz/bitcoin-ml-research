# Resultados e decisões

[← Apresentação](README.md)

Esta página reúne os números que sustentam os três marcos do portfólio. A seleção destaca contribuições de arquitetura, treinamento e avaliação, sem apresentar experimentos distintos como um ranking de desempenho.

## Marcos 1 e 2 · Comparação histórica controlada

258 previsões entre 23/11/2025 e 07/08/2026, com retorno logarítmico em horizonte de dez dias e previsões agregadas de cinco inicializações. O recorte já participou do desenvolvimento.

| Indicador | Controle comparável | Objetivo revisado |
|---|---:|---:|
| Acerto direcional (HR) | 53,88% | **55,81%** |
| Acurácia balanceada (BA) | 54,77% | **56,73%** |
| RMSE | 0,072166 | **0,070965** |
| MAE | 0,052628 | **0,050842** |

HR mede a frequência de acertos de direção. BA equilibra o desempenho entre altas e baixas. RMSE e MAE medem erro em log-retorno; valores menores são melhores. Nenhuma dessas métricas representa retorno de uma estratégia financeira.

**Leitura técnica:** a mudança apresentou melhora conjunta no ponto estimado das quatro métricas. A BA melhorou em dois de três blocos temporais e em três de cinco inicializações.

**Incerteza:** o ganho de HR foi de aproximadamente 1,94 ponto percentual, com intervalo exploratório de 95% por bootstrap em blocos de **[−1,55; +5,43] pontos percentuais**. O intervalo inclui ausência de ganho. Um dos blocos piorou em direção; o resultado não é uniforme.

**Decisão registrada:** manter a candidata para investigação posterior, sem tratar a melhora como confirmação estatística ou prospectiva.

## Marco 3 · Avaliação temporal ampliada

Análise principal: 2.228 origens de previsão entre 01/04/2020 e 07/08/2026, com cobertura não contínua. Foram realizados 25 folds de reajuste e cinco inicializações; o experimento completo também incluiu um cenário de sensibilidade com reaproveitamento de pesos em um intervalo sem novo ajuste.

| Comparação de MAE | Resultado |
|---|---:|
| MoE de referência | 0,078772 |
| MoE combinado com TCN | 0,072559 |
| Controle simples de redução de amplitude do mesmo MoE | 0,072554 |

A combinação apresentou redução aproximada de 7,9% frente ao MoE. Entretanto, seu erro foi praticamente igual ao controle simples. O intervalo ajustado da diferença de MAE entre combinação e controle foi **[−0,000902; +0,000834]**, incluindo zero.

**Decisão registrada:** não incorporar a TCN ao MoE com base nessa receita. A avaliação distingue melhora em relação ao modelo original de benefício adicional atribuível ao novo componente.

**Escala de engenharia:** o experimento completo registrou 130 grupos, sendo 125 grupos de reajuste por fold e inicialização e cinco grupos sem novo ajuste; 1.058 ajustes científicos e verificação de 5.040 arquivos de checkpoint. Esses contadores descrevem execução e integridade, não qualidade preditiva nem número de amostras independentes.

## Limites que acompanham os números

- São estudos históricos exploratórios, com dados já utilizados no desenvolvimento e sem holdout confirmatório apresentado neste portfólio.
- Os retornos futuros avaliados se sobrepõem; as inicializações compartilham datas e não constituem amostras independentes.
- O histórico de seleção de objetivos e configurações integra a interpretação dos resultados.
- A proveniência da geração integral de parte das features legadas não foi certificada de ponta a ponta.
- A avaliação ampliada tem cobertura diferente da comparação de 258 previsões. Seus números não devem ser comparados diretamente.
- Não foram apresentados resultados prospectivos, custos de negociação ou rentabilidade de uma estratégia.

Os valores foram transcritos dos registros internos consolidados de comparação controlada e avaliação temporal, conferidos em 26/10/2026. Esses registros não são publicados por conterem material privado; não há alegação de validação independente ou reprodução pública.
