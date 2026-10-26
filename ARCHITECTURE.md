# Arquitetura por blocos

[← Apresentação](README.md)

A evolução do projeto é apresentada pelas responsabilidades acrescentadas ao sistema. Cada bloco responde a uma necessidade concreta; sua presença na arquitetura não implica benefício isolado comprovado.

| Bloco | Responsabilidade | Motivo da escolha |
|---|---|---|
| Preparação temporal | Organizar sequências e separar etapas de seleção, ajuste e avaliação | Respeitar a ordem do problema e tornar comparações auditáveis |
| Representação sequencial | Aprender uma representação com autoencoder baseado em GRU | Explorar estrutura temporal antes da tarefa supervisionada |
| Roteamento por regime | Selecionar o especialista conforme o contexto estimado | Investigar respostas distintas a contextos de mercado |
| Especialistas temporais | Estimar o retorno a partir da representação aprendida | Distribuir a tarefa entre modelos especializados |
| Objetivo supervisionado | Considerar erro de retorno e informação direcional | Alinhar o treinamento às duas dimensões avaliadas |
| Agregação | Combinar saídas de diferentes inicializações | Avaliar uma previsão agregada sem escolher a melhor seed |
| Avaliação e integridade | Comparar controles, períodos, erros e artefatos persistidos | Sustentar decisões com evidência e rastreabilidade |

## O que mudou em cada marco

**Base especializada:** representação sequencial, roteamento e especialistas formam o núcleo. O encoder pré-treinado permanece congelado na comparação histórica destacada.

**Evolução do treinamento:** a arquitetura foi preservada para comparar objetivos supervisionados. Isso ajuda a interpretar a mudança observada, embora a seleção de épocas também possa mudar em consequência do objetivo.

**Avaliação ampliada:** um ramo TCN independente passou a ser comparado com controles e combinações. O protocolo pergunta se a rede acrescenta informação útil além de uma transformação simples das previsões existentes. O resultado não justificou sua incorporação.

## Decisões de engenharia

- Manter separados os experimentos e seus artefatos para evitar confundir configurações e resultados.
- Conferir persistência, recarga e integridade dos artefatos nas verificações registradas.
- Preservar falhas e correções de execução, em vez de ocultar tentativas que não chegaram à avaliação.
- Tratar uma melhoria frente a um modelo como insuficiente quando um controle mais simples explica o mesmo ganho.

Detalhes de features, hiperparâmetros, fórmulas de treinamento, regras exatas de roteamento e artefatos de implementação não são divulgados.
