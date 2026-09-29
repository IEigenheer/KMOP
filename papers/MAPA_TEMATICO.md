# Relações entre os temas

Este mapa registra as comparações que orientaram a revisão. O [catálogo](CATALOGO.md) contém a classificação individual de cada PDF.

## O que os benchmarks medem

**SWE-bench** é o ponto de partida para resolução de issues em repositórios Python. **SWE-PolyBench**, **Multi-SWE-bench** e **SWE-Compass** ampliam a cobertura de linguagens e tipos de tarefa; **Rust-SWE-bench** e **SWE-Bench Mobile** tratam ecossistemas específicos. **FeatureBench** desloca o foco para desenvolvimento de funcionalidades; **ProjDevBench** e **SWE-AGI** exigem construção mais abrangente a partir de requisitos. **SWE-bench Live** e **SWE-rebench V2** enfatizam coleta e atualização de tarefas. Por isso, todos estão no grupo de benchmarks, inclusive os multilíngues.

**PETSCAGENT-BENCH** também apresenta tarefas, mas sua contribuição distintiva é uma avaliação multidimensional de código científico, para além do resultado de testes. Ele está com os trabalhos sobre juízes e verificação. **LoopArena** apresenta um benchmark, mas isola o controle de um agente de programação ao longo de uma execução prolongada; está com os estudos de horizonte longo.

## Validade da avaliação e qualidade dos verificadores

**Claw-SWE-Bench**, **Scaffold Effects on GAIA** e **The Scaffold Effect in Coding Agents** mostram que a configuração do agente altera a interpretação de scores de modelo. **AI Agents That Matter** e **Position: Coding Benchmarks Are Misaligned** formulam problemas mais gerais de custo, reprodutibilidade e validade. **Efficient Benchmarking of AI Agents** estuda quando um subconjunto de tarefas ainda permite comparar sistemas. **Does SWE-Bench-Verified Test Agent Ability or Model Memory?** investiga contaminação. Essas perguntas são sobre a validade do *protocolo* de comparação.

**EvalPlus** e **SWE-ABS** atacam outra fonte de erro: testes insuficientes podem aceitar soluções incorretas. **The Oracle Problem in Software Testing** fornece o fundamento do problema do oráculo; **The Limits of Inference Scaling Through Resampling** mostra como falsos positivos limitam repetição de tentativas. **Verify, Repair, Repeat, or Stop?** trata a decisão de parar quando verificação e reparo são ruidosos. **Agent-as-a-Judge**, **AJ-Bench** e o trabalho sobre anotação automática investigam juízes que consultam evidências e trajetórias, enquanto **LLM Evaluators Recognize and Favor Their Own Generations** alerta para viés de autopreferência. Esses trabalhos ficaram juntos porque estudam como decidir se uma resposta está correta ou merece confiança.

## Como os agentes trabalham

**Agentless** oferece um fluxo fixo de localização, reparo e validação; **Putting It All into Context** reduz a exploração por ferramentas ao colocar o repositório no contexto longo; **icat-agent** usa coordenação adaptativa entre agentes. **FlowGen** e **Spec Kit Agents** estruturam o trabalho por processos e artefatos; o estudo **From Prompt to Process** compara esses processos. **SWE-Gym** desloca a questão para treinamento de agentes e verificadores, e **SWE-Skills-Bench** mede o efeito marginal de instruções procedurais. O agrupamento segue a arquitetura ou intervenção principal, mesmo quando o artigo usa um benchmark conhecido para demonstrá-la.

**SWE-Router**, **RouteLLM**, **MixLLM** e o estudo com *bandit feedback* escolhem modelos conforme a tarefa ou o feedback disponível. **Knowing When to Ask for Help** decide quando escalar durante a geração; **Budget-Aware Tool Use** decide como gastar chamadas de ferramentas. Eles formam um grupo de decisões sobre recursos, distinto das arquiteturas de desenvolvimento.

## Generalização, contexto e fontes complementares

Os estudos com **motores de xadrez**, **linguagens desconhecidas**, **Tokenmaxxing** e **BabelCode** perguntam como a linguagem escolhida ou sua presença nos dados altera estratégia, custo e capacidade. Esta pergunta é diferente da construção de um benchmark multilíngue.

**Lost in Compaction** estuda perda de restrições ao resumir contexto; **The Illusion of Diminishing Returns** estuda erros que se acumulam em tarefas longas; **LoopArena** avalia decisões de controle durante a execução; **Why Do Multi-Agent LLM Systems Fail?** classifica falhas de coordenação. Todos tratam da confiabilidade de uma trajetória ao longo do tempo.

O PDF de recomendações de benchmarks e as duas páginas da OpenAI sobre SWE-bench foram preservados como fontes de apoio, com o tipo de documento explicitado no catálogo. Eles se relacionam ao tema de validade da avaliação, mas não são apresentados como artigos acadêmicos.
