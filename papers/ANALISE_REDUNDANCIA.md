# Análise de redundância dos PDFs por tema

## Critério e resultado

Foram examinados os **57 PDFs das oito pastas**, comparando pergunta, objeto, método ou conjunto de dados, e contribuição declarada. As páginas indicadas abaixo são **páginas físicas do PDF**, começando em 1; em alguns artigos elas diferem da numeração impressa. O [catálogo](CATALOGO.md) contém os nomes completos e os links de todos os arquivos. Uma conclusão semelhante ou o uso do mesmo benchmark não bastam para classificar dois estudos como substituíveis: dados, protocolo ou análise próprios também contam.

**Não há redundância integral demonstrada entre artigos científicos da mesma pasta.** Há um documento secundário que pode sair de uma seleção de *evidência primária* e uma revisão ampla que pode sair de uma seleção *estritamente sobre programação*. Essas recomendações condicionais não significam que todo o texto dos dois PDFs seja coberto pelos demais. Nenhum PDF foi removido.

## Candidatos a retirar da seleção principal

### 1. Relatório de recomendações de benchmarks — pasta 08

PDF: [Pesquise_os_benchmarks_datasets_mais_confiveis_.pdf](08_Relatorios_e_divulgacao/Pesquise_os_benchmarks_datasets_mais_confiveis_.pdf). **Recomendação: retirar da seleção de fontes acadêmicas primárias; manter apenas se for útil como registro da busca inicial.** Trata-se de um relatório de três páginas de conteúdo produzido com auxílio do Consensus, com tabela e recomendação de uma bateria de benchmarks, sem dataset, protocolo experimental ou resultado próprio. O conteúdo central das páginas 1–2 remete a estudos presentes no acervo:

| Conteúdo no relatório | PDF que oferece a evidência diretamente e onde encontrá-la |
|---|---|
| SWE-bench como base de avaliação de issues em repositórios Python (p. 1–2) | [SWE-bench](01_Benchmarks_e_datasets_de_software/SWE-BENCH%20CAN%20LANGUAGE%20MODELS%20RESOLVE%20REAL-WORLD%20GIHUB%20ISSUES.pdf), resumo na p. 1 e formulação da tarefa e avaliação na seção 2.2, p. 3. |
| SWE-PolyBench para avaliação multilíngue executável e análise de complexidade (p. 1–2) | [SWE-PolyBench](01_Benchmarks_e_datasets_de_software/SWE-PolyBench%20A%20multi-language%20benchmark%20for%20repository%20level%20evaluation%20of%20coding%20agents.pdf), resumo na p. 1, construção e categorias nas pp. 4–5, métricas de complexidade na p. 6. |
| Multi-SWE-bench para Go, Rust e outras linguagens, com curadoria humana (p. 1–2) | [Multi-SWE-bench](01_Benchmarks_e_datasets_de_software/Multi-SWE-bench%20A%20Multilingual%20Benchmark%20for%20Issue%20Resolving.pdf), resumo na p. 1 e seção 3.1 de construção nas pp. 5–7. |
| FeatureBench e ProjDevBench para tarefas maiores do que correção pontual (p. 1–2) | [FeatureBench](01_Benchmarks_e_datasets_de_software/FeatureBench%20Benchmarking%20Agentic%20Coding%20for%20Complex%20Feature%20Development.pdf), resumo na p. 1 e desenho da tarefa nas pp. 4–5; [ProjDevBench](01_Benchmarks_e_datasets_de_software/ProjDevBench%20Benchmarking%20AI%20Coding%20Agents%20on%20end-to-end%20project%20development.pdf), resumo na p. 1, coleta das tarefas e avaliação nas pp. 4–5. |
| Necessidade de controlar o *scaffold* ao comparar modelos (p. 2) | [The Scaffold Effect in Coding Agents](02_Validade_e_protocolos_de_avaliacao/The%20Scaffold%20Effect%20in%20Coding%20Agents%20Harness%20Choice%20as%20a%20Hidden%20Variable%20in%20Coding-Agent%20Evaluation.pdf), resumo na p. 1, protocolo nas pp. 2–3 e comparação de custo, acerto e falhas nas pp. 3–5; [Scaffold Effects on GAIA](02_Validade_e_protocolos_de_avaliacao/Scaffold%20Effects%20on%20GAIA%20A%20Controlled%20Comparison.pdf), resumo na p. 1 e três configurações de scaffold na p. 4. |

**Limite da substituição:** a p. 2 do relatório também menciona ReCode, BigCodeBench e SEC-bench, cujos PDFs não estão nesta coleção. Logo, os PDFs acima cobrem sua *recomendação central sobre os benchmarks presentes no acervo*, mas não cada exemplo externo. O relatório pode servir como lista de pistas bibliográficas; ele não substitui a verificação dos estudos originais.

### 2. Revisão geral de agentes — pasta 04

PDF: [From LLM Reasoning to Autonomous AI Agents: A Comprehensive Review](04_Arquiteturas_processos_e_treinamento/From%20LLM%20Reasoning%20to%20Autonomous%20AI%20Agents%20a%20comprehensive%20review.pdf). **Recomendação condicional: tirar desta seleção se o recorte for exclusivamente agentes de programação; conservar se protocolos e aplicações gerais de agentes também fizerem parte da pesquisa.** A revisão abrange cerca de 60 benchmarks de vários domínios, aplicações em saúde, ciência e finanças e protocolos MCP/ACP/A2A (resumo, pp. 1–2; protocolos, pp. 38–40). Não apresenta um experimento original de agente de programação. Sua visão introdutória de agentes de software (pp. 3–4) e a classificação de aplicações em engenharia de software (pp. 27–30) se sobrepõem **parcialmente** a:

- [AI Agentic Programming: A Survey of Techniques, Challenges, and Opportunities](04_Arquiteturas_processos_e_treinamento/AI%20Agentic%20Programming%20A%20Survey%20of%20Techniques%20challanges%20and%20oportunities.pdf), definição e fluxo de agentes de programação nas pp. 1–6, taxonomia e sistemas nas pp. 13–16, avaliação e desafios nas pp. 17–20.
- [From Prompt to Process](04_Arquiteturas_processos_e_treinamento/From%20Prompt%20to%20Process%20a%20Process%20Taxonomy%20and%20Comparative%20Assessment%20of%20Frameworks%20Supporting%20AI%20Software%20Development%20Agents.pdf), resumo nas pp. 1–2 e método de comparação de frameworks nas pp. 3–4, para a parte de processos de desenvolvimento.
- Estudos primários da própria pasta, como [Agentless](04_Arquiteturas_processos_e_treinamento/Agentless%20Demystifying%20LLM-based%20Software%20Engineering%20Agents.pdf) (resumo, p. 1) e [SWE-Gym](04_Arquiteturas_processos_e_treinamento/Training%20Software%20Engineering%20Agents%20and%20Verifiers%20with%20SWE-Gym.pdf) (resumo, p. 1), quando a questão for arquitetura ou treinamento concretos.

**Limite da substituição:** a revisão inclui trabalhos de engenharia de software ausentes da pasta e material substancial sobre outros domínios e protocolos. Portanto, ela é **periférica ao recorte**, não redundante em sentido estrito. Sua retirada sacrifica essa cobertura geral.

## Revisão de cada pasta

As tabelas indicam a contribuição que impede classificar o PDF como substituível pelos demais da **mesma pasta**. Os dois candidatos condicionais estão marcados acima.

### 01 — Benchmarks e datasets de software (11)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| SWE-bench original | Define a tarefa de resolver issues reais em repositórios Python e seu protocolo executável; manter como fonte fundadora. |
| SWE-bench Goes Live | Introduz coleta continuamente atualizável e montagem automatizada de ambientes; manter. |
| SWE-rebench V2 | Coleta em escala voltada a tarefas e ambientes de treinamento, com independência de linguagem; manter. |
| SWE-PolyBench | Inclui Java, JavaScript, TypeScript e Python, tipos de mudança e análise sintática; manter. |
| Multi-SWE-bench | Inclui Go, Rust, C e C++ e curadoria manual multilíngue; manter. Não substitui as tarefas de SWE-PolyBench. |
| SWE-Compass | Cruza tipos de tarefa, cenários e linguagens em um desenho unificado; manter. |
| Rust-SWE-bench | Isola resolução de issues e estratégias para repositórios Rust; manter. |
| SWE-Bench Mobile | Estuda tarefas iOS industriais com entradas multimodais e base Swift/Objective-C; manter. |
| FeatureBench | Avalia desenvolvimento de funcionalidades, inclusive a partir do zero; manter. |
| ProjDevBench | Avalia desenvolvimento de projeto completo com execução e revisão de código; manter. |
| SWE-AGI | Exige construir sistemas em MoonBit a partir de especificações e padrões; manter. |

### 02 — Validade e protocolos de avaliação (7)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| AI Agents That Matter | Discute conjuntamente custo, validade e necessidades de quem desenvolve ou usa agentes; manter. |
| Position: Coding Benchmarks Are Misaligned | Argumenta sobre avaliação do sistema completo, incluindo harness, contexto e sinais de produção; manter como artigo de posição, distinto dos testes empíricos. |
| Efficient Benchmarking of AI Agents | Seleciona subconjuntos de tarefas para preservar rankings com custo menor; manter. |
| Claw-SWE-Bench | Propõe adaptador e protocolo para comparar harnesses gerais em tarefas de código; manter. |
| Scaffold Effects on GAIA | Comparação controlada e pré-registrada de scaffolds em GAIA; manter como evidência metodológica, embora GAIA não seja benchmark de programação. |
| The Scaffold Effect in Coding Agents | Mede harnesses de programação com modelos fixos, incluindo custo e perfis de falha; manter. |
| Does SWE-Bench-Verified Test Agent Ability or Model Memory? | Testa a hipótese de memorização por localização com informação parcial da issue; manter. |

### 03 — Juízes, testes e verificação (12)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| The Oracle Problem in Software | Revisão conceitual do problema do oráculo de teste; manter como fundamento. |
| EvalPlus / Is Your Code Generated by ChatGPT Really Correct? | Amplia casos de teste para síntese de código; manter. |
| SWE-ABS | Reforça adversarialmente suítes de testes de benchmark de agentes; manter. O alvo e o método diferem de EvalPlus. |
| The Limits of Inference Scaling Through Resampling | Analisa o limite da reamostragem diante de falsos positivos do verificador; manter. |
| Verify, Repair, Repeat, or Stop? | Decide quando interromper ciclos de verificação e reparo sob ruído; manter. |
| Agent-as-a-Judge | Introduz avaliação de etapas intermediárias e o conjunto DevAI; manter. |
| AJ-Bench | Avalia a capacidade dos próprios juízes agentes de consultar ambientes; manter. |
| Automatically Benchmarking LLM Code Agents | Automatiza anotação e avaliação de tarefas de agentes de código; manter. |
| PETSCAGENT-BENCH | Avalia código científico PETSc com critérios de biblioteca e desempenho; manter. |
| SCoRE / Conformal Selective Prediction | Oferece controle formal de risco com opção de abstenção; manter como método geral, não como estudo específico de código. |
| LLM Evaluators Recognize and Favor Their Own Generations | Testa viés de autopreferência em avaliadores LLM; manter. |
| Large Language Models Cannot Self-Correct Reasoning Yet | Examina autocorreção intrínseca sem feedback externo; manter como limite conceitual diferente de verificação externa. |

### 04 — Arquiteturas, processos e treinamento (10)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| AI Agentic Programming: A Survey | Síntese centrada em agentes de programação, suas arquiteturas, ferramentas e desafios; manter. |
| From LLM Reasoning to Autonomous AI Agents | Revisão de agentes em vários domínios e protocolos; corte **condicional por escopo**, detalhado acima. |
| From Prompt to Process | Taxonomia comparativa de frameworks e artefatos de processo; manter. |
| SOEN-101 / FlowGen | Implementa modelos de processo como waterfall, TDD e Scrum com agentes; manter. |
| Spec Kit Agents | Acrescenta sondagem do repositório às fases de desenvolvimento orientado por especificação; manter. |
| icat-agent / Unlocking Model Potentials | Adapta exploração e reparo multiagente à clareza da issue; manter. |
| SWE-Gym | Fornece ambientes para treinar agentes e verificadores; manter. |
| Putting It All into Context | Testa colocar o repositório inteiro no contexto longo em vez de explorar com ferramentas; manter. |
| Agentless | Fluxo fixo de localização, reparo e validação, sem planejamento autônomo por ferramentas; manter. |
| SWE-Skills-Bench | Isola o efeito de instruções procedurais (*skills*) em agentes de software; manter. |

### 05 — Roteamento e gestão de recursos (6)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| RouteLLM | Aprende roteamento entre modelos com dados de preferência; manter. |
| MixLLM | Usa bandits contextuais e adaptação dinâmica entre modelos; manter. |
| Learning to Route LLMs from Bandit Feedback / BaRP | Aprende com o resultado parcial do modelo escolhido e diferentes preferências de custo e qualidade; manter. |
| SWE-Router | Roteia em tarefa de engenharia de software após observar parte da trajetória; manter. |
| Knowing When to Ask for Help | Formula escalonamento durante a geração como decisão bayesiana; manter. |
| Budget-Aware Tool Use | Ajusta o uso de ferramentas a um limite de chamadas, com foco em agentes de busca; manter. |

### 06 — Contexto, horizonte longo e multiagentes (4)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| Lost in Compaction | Mede perda de restrições laterais após compactar contexto; manter. |
| The Illusion of Diminishing Returns | Isola erros de execução acumulados em tarefas longas; manter. |
| LoopArena | Avalia decisões do controlador com o agente executor fixo; manter. |
| Why Do Multi-Agent LLM Systems Fail? | Taxonomia e análise de trajetórias de falha multiagente; manter. |

### 07 — Linguagens e generalização (4)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| Measuring the Impact of Programming Language Distribution | Relaciona distribuição de dados por linguagem e desempenho de modelos de código; manter. |
| The Best Programming Language for Tokenmaxxing | Compara gasto de tokens e trajetórias de agentes entre linguagens; manter. |
| Frontier Coding Agents Use Metaprogramming | Observa estratégias em linguagens pouco familiares; manter. |
| Do Programming Languages Still Matter? / Chess Engines | Compara artefatos completos, qualidade e custo de motores de xadrez em várias linguagens; manter. |

### 08 — Relatórios e divulgação (3)

| PDF (nome abreviado) | Elemento distintivo; decisão |
|---|---|
| Pesquise os benchmarks / datasets mais confiáveis | Síntese secundária de recomendações; **corte condicional como fonte primária**, detalhado acima. |
| Por que o SWE-bench Verified não mede mais capacidades de ponta? | Argumenta especificamente sobre contaminação e limites do **Verified**; manter como fonte institucional sobre essa decisão. |
| Separando sinal de ruído em avaliações de programação | Apresenta auditoria de tarefas problemáticas do **SWE-bench Pro**; manter. A referência ao Verified não substitui a discussão própria do outro texto. |

## Casos parecidos que não justificam remoção

- **SWE-PolyBench × Multi-SWE-bench × SWE-Compass:** sobrepõem-se no objetivo multilíngue, mas usam conjuntos, linguagens, categorias de tarefa e protocolos diferentes. A própria comparação de SWE-PolyBench com SWE-bench está nas pp. 3–6 de seu PDF; Multi-SWE-bench descreve seu pipeline nas pp. 5–7.
- **Scaffold Effects on GAIA × The Scaffold Effect in Coding Agents × Claw-SWE-Bench:** tratam do efeito do scaffold, mas diferem em domínio, desenho controlado e adaptação de harnesses; ver os resumos na p. 1 dos três PDFs e os métodos nas pp. 2–4.
- **EvalPlus × SWE-ABS:** ambos expõem testes fracos, mas um trata geração de funções e o outro patches de issues; a transferência do resultado de um para o outro não é automática.
- **As duas publicações da OpenAI na pasta 08:** uma questiona o Verified; a outra audita o Pro. São diagnósticos de conjuntos diferentes.

Em suma, **o único PDF que eu retiraria do núcleo de evidência primária é o relatório de recomendações da pasta 08**. A revisão geral da pasta 04 depende do recorte escolhido. Para os artigos científicos restantes, não há base suficiente para afirmar que outro PDF, ou a combinação dos demais da mesma pasta, cobre integralmente suas contribuições.
