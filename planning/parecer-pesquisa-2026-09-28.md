# Parecer de planejamento da pesquisa

Data da consulta: 28 de setembro de 2026.

Este documento organiza decisões de pesquisa. Não contém resultados experimentais próprios nem estabelece originalidade definitiva. A auditoria combina os PDFs locais, a planilha do Elicit e consultas a fontes primárias. A leitura foi orientada a objetivos, métodos, comparadores e limitações relevantes; não constitui uma revisão sistemática, reprodução dos estudos ou leitura exaustiva de todos os apêndices.

## 1. Avaliação da proposta

A proposta aborda um problema relevante: escolher quanto gastar em execução e verificação para entregar alterações corretas em repositórios. Seu principal risco científico é o escopo excessivo. Linguagens, benchmarks, contexto, multiagentes, roteamento, verificadores e treinamento de controladores contêm perguntas distintas e diversos antecedentes diretos.

Um framework extensível é um artefato útil, mas sua quantidade de recursos não demonstra contribuição científica. O artigo precisa identificar uma relação mensurável, apresentar um método ou produzir evidência que os estudos anteriores ainda não fornecem.

Recorte recomendado: **alocação do orçamento entre implementação, verificação, troca de modelo e encerramento, com avaliação independente dos patches entregues**.

Pergunta principal candidata: em que condições uma política adaptativa diminui o custo por tarefa corretamente resolvida, preservando qualidade e cobertura de atendimento, frente a políticas simples e métodos publicados?

Definir dois desfechos diferentes: resolver corretamente a tarefa e decidir corretamente se a solução deve ser entregue. Um sistema pode produzir bons patches e rejeitá-los, ou produzir patches incorretos e aceitá-los. As duas falhas precisam aparecer.

## 2. Originalidade e antecedentes próximos

Minha sugestão anterior de pesquisar um controlador precisa ser delimitada: já existem estudos diretamente relacionados. Não apresentar apenas a combinação de modelos baratos e fortes, ou uma decisão aprendida de parada, como novidade.

| Trabalho verificado | Proximidade com a proposta | Consequência para o projeto |
| --- | --- | --- |
| [AI Agents That Matter](https://arxiv.org/abs/2407.01502) | Discute otimização conjunta de custo e acerto, sobreajuste e reprodutibilidade. | Custo-benefício já é motivação estabelecida. |
| [RouteLLM](https://arxiv.org/abs/2406.18665) | Aprende a escolher entre modelos de diferentes custos e capacidades. | Roteamento barato/forte isoladamente não basta como contribuição. |
| [SWE-Router](https://arxiv.org/abs/2607.00053) | Usa uma trajetória inicial de um modelo barato para decidir continuidade ou escalonamento em engenharia de software. | Comparador particularmente próximo para roteamento durante a execução. |
| [Training Software Engineering Agents and Verifiers with SWE-Gym](https://arxiv.org/abs/2412.21139) | Treina agentes e verificadores e estuda seleção de soluções em tempo de inferência. | Verificador aprendido e uso de múltiplas tentativas também têm antecedentes diretos. |
| [Verify, Repair, Repeat, or Stop?](https://arxiv.org/abs/2607.17641) | Modela aceitação/rejeição equivocadas e reparos que corrigem ou danificam candidatos. | Parada com verificador falível é um problema já formulado. O estudo inclui MBPP, matemática e uso de ferramentas; conferir a transferência para reparos em repositórios. |
| [LoopArena](https://arxiv.org/abs/2608.28281) | Avalia um controlador que orienta um executor fixo, solicita verificações e decide quando parar. | Considerar seu protocolo e baselines antes de criar uma avaliação de controladores. |
| [Knowing When to Ask for Help](https://arxiv.org/abs/2608.24087) | Formula escalonamento durante a geração como decisão bayesiana de parada. | Ler as hipóteses teóricas e o alcance da validação em código antes de reivindicar novidade em escalonamento. |

Uma lacuna candidata, ainda por confirmar, é a combinação de decisões por papel, verificação imperfeita, custo monetário observado, possibilidade de abstenção e transferência entre repositórios/modelos. A combinação precisa produzir uma descoberta ou método verificável; reunir componentes conhecidos não garante originalidade.

Dois cuidados ao interpretar esses concorrentes: VRR-Stop usa uma aproximação local de estabilidade e independência condicional dos pareceres; essas condições podem falhar entre revisões do mesmo patch. LoopArena calcula custos padronizados sem cache, e a economia destacada compara avaliação de trechos com avaliação completa; não deve ser interpretada como economia automática de adicionar um controlador. Fontes: métodos de [VRR-Stop](https://arxiv.org/html/2607.17641v1) e de [LoopArena](https://arxiv.org/html/2608.28281v1).

## 3. Auditoria do acervo atual

Inventário confirmado: 31 PDFs, distribuídos em 7, 10 e 14 arquivos nas buscas 01, 02 e 03. As duas cópias de SWE-PolyBench são idênticas por SHA-256. Um PDF é um relatório de busca. Restam 29 documentos científicos distintos, sem equiparar preprint, artigo de posição, survey e estudo experimental. Há também uma planilha do Elicit. `references.bib` está vazio; os itens precisam ser incorporados pelo Zotero/Better BibTeX antes de citações no manuscrito.

As prioridades abaixo são relativas ao recorte proposto. Não são notas de qualidade científica dos artigos.

### Search-01

| Documento local | Uso recomendado | Limite da inferência / decisão |
| --- | --- | --- |
| [Measuring The Impact Of Programming Language Distribution](<../papers/search-01/Measuring The Impact Of Programming Language Distribution.pdf>) | Essencial para distinguir distribuição de treino de desempenho por linguagem. | O estudo manipula a composição do treino em seu cenário. Isso não revela a composição de modelos proprietários atuais. |
| [SWE-PolyBench](<../papers/search-01/SWE-PolyBench A multi-language benchmark for repository level evaluation of coding agents.pdf>) | Candidato a avaliação principal ou externa; permite estratificação. | Frequências de linguagens são desiguais. Comparar por linguagem e repositório, além da média agregada. |
| [The Best Programming Language for Tokenmaxxing](<../papers/search-01/The Best Programming Language for Tokenmaxxing.pdf>) | Prioridade alta para custo por linguagem e análise de trajetórias. | Consumo de tokens não equivale automaticamente a dólares; o cenário usa problemas de programação, não todo o ciclo de manutenção. |
| [Frontier Coding Agents Use Metaprogramming](<../papers/search-01/Frontier Coding Agents Use Metaprogramming to adapt to unfamilliar programming languages.pdf>) | Prioridade alta como evidência contrária à ideia de compensar qualquer limitação com mais tentativas. | O estudo observa que recursos extras não resgatam todos os modelos fracos no cenário de linguagens esotéricas. Generalização para PRs comuns precisa de teste. |
| [Do programming languages still matter... chess engines](<../papers/search-01/Do programming languages still matter to your AI coding agent teammate evidence at scale from chess engines.pdf>) | Apoio para qualidade multidimensional e desempenho do software gerado. | Estudo de caso em motores de xadrez não estima efeito universal de linguagem ou paradigma. |
| [An Agentic Evaluation Framework... PETSc](<../papers/search-01/An Agentic Evaluation Framework for Ai-generated Scientific Code in PETSc.pdf>) | Apoio para qualidade além de passar testes: convenções, uso de biblioteca e desempenho. | Avaliação especializada em computação científica; usar como exemplo metodológico, não como benchmark principal genérico. |
| [AI Agentic Programming: A Survey](<../papers/search-01/AI Agentic Programming A Survey of Techniques challanges and oportunities.pdf>) | Mapa de termos e referências para busca por citações. | Survey não substitui estudo primário para justificar ganho de um mecanismo. |

Síntese: usar linguagem como fator de generalização e potencial moderador do efeito. Adiar a hipótese causal sobre distribuição da internet. Python ir melhor em determinado estudo não estabelece superioridade universal, e linguagem não isola paradigma de programação.

### Search-02

| Documento local | Uso recomendado | Limite da inferência / decisão |
| --- | --- | --- |
| [SWE-bench](<../papers/search-02/SWE-BENCH CAN LANGUAGE MODELS RESOLVE REAL-WORLD GIHUB ISSUES.pdf>) | Entender tarefas, separação dos testes e avaliação de patches; âncora histórica. | A versão original difere de Verified. Exposição de tarefas e defeitos nos testes precisam ser tratados. |
| SWE-PolyBench, segunda cópia | Reutilizar o registro da busca 01. | Duplicata não é evidência independente. |
| [Multi-SWE-bench](<../papers/search-02/Multi-SWE-bench A Multilingual Benchmark for Issue Resolving.pdf>) | Prioridade alta se Rust/Go/C/C++ fizerem parte das alegações. | Ambiente, tamanho das tarefas e ferramentas diferem por linguagem. |
| [FeatureBench](<../papers/search-02/FeatureBench Benchmarking Agentic Coding for Complex Feature Development.pdf>) | Candidato a validação externa para desenvolvimento de funcionalidades. | Mais difícil não significa necessariamente mais confiável; inspecionar testes, interfaces e custo do cenário escolhido. |
| [ProjDevBench](<../papers/search-02/ProjDevBench Benchmarking AI Coding Agents on end-to-end project development.pdf>) | Validação futura para construção de projetos completos. | Muda o problema em relação a reparar issues e pode tornar o primeiro estudo excessivamente caro. |
| [SWE-AGI](<../papers/search-02/SWE-AGI Benchmarking Specification-Driven Software Construction with MoonBit in the Era of Autonomous Agents.pdf>) | Apoio para tarefas guiadas por especificações. | MoonBit e seu desenho específico não sustentam generalidade multilíngue. Adiar execução. |
| [Agent-as-a-Judge](<../papers/search-02/Agent-as-a-Judge evaluate agents with agents.pdf>) | Prioridade alta para verificadores que buscam evidências. | Concordância humana no conjunto estudado não transforma o avaliador em oráculo universal. |
| [Automatically Benchmarking... / PRDBench](<../papers/search-02/Automatically Benchmarking LLM Code Agents through agent-driven annotation and evaluation.pdf>) | Prioridade alta para requisitos, critérios e avaliador especializado. | Alinhamento com humanos depende do cenário e treinamento. Registrar a versão local, que contém PRDJudge, ao comparar com registros anteriores do artigo. |
| [From LLM Reasoning to Autonomous AI Agents](<../papers/search-02/From LLM Reasoning to Autonomous AI Agents a comprehensive review.pdf>) | Contextualização ampla e descoberta de fontes. | Baixa prioridade para a justificativa específica de roteamento/parada. |
| [Relatório “Pesquise os benchmarks...”](<../papers/search-02/Pesquise_os_benchmarks_datasets_mais_confiveis_.pdf>) | Documento de triagem e origem de consultas. | Não tratar como artigo primário. A tabela agrupa SWE-bench/Verified e PRDBench/ProjDevBench de forma que pode confundir tamanhos e protocolos. Voltar às fontes originais. |

A [planilha do Elicit](<../papers/search-02/Elicit - Benchmarks para avaliar agentes de programação.xlsx>), aba Data, A1:E17, já distingue SWE-bench original de Verified e registra contaminação, Rust-SWE-bench, SWE-rebench V2, SWE-ABS e Terminal-Bench. Assim, esses temas estão parcialmente identificados na triagem, embora vários artigos não estejam entre os PDFs locais. As células trazem resumos e referências; não substituem a conferência dos métodos primários. O rótulo “melhor opção” deve ser tratado como recomendação de busca, não resultado de comparação sistemática.

### Search-03

| Documento local | Uso recomendado | Limite da inferência / decisão |
| --- | --- | --- |
| [Agentless](<../papers/search-03/Agentless Demystifying LLM-Based Software Engineering Agents.pdf>) | Essencial como contraponto de simplicidade e candidato a baseline. | É um pipeline estruturado; não é equivalente a um prompt único sem ferramentas. |
| [The Scaffold Effect in Coding Agents](<../papers/search-03/The Scaffold Effect in Coding Agents Harness Choice as a Hidden Variable in Coding-Agent Evaluation.pdf>) | Essencial para controle do harness e contabilidade de recursos. | A amostra e os intervalos de confiança limitam conclusões de acerto; não generalizar diferença de tokens como diferença monetária. |
| [Unlocking Model Potentials... / icat-agent](<../papers/search-03/Unlocking Model Potentials Through Adaptive Multi-Agent Scaffolding for Efficient Issue Resolution.pdf>) | Essencial como concorrente de editor/validador, isolamento de contexto e adaptação do fluxo. | Separar ganhos de divisão de papéis, ferramentas, orçamento e estratégia de exploração. |
| [SWE-Skills-Bench](<../papers/search-03/SWE-Skills-Bench Do Agent Skills Actually Help in Real-World Software Engineering.pdf>) | Prioridade alta para utilidade marginal e overhead de instruções. | Evidência sobre skills no cenário estudado não prova ineficácia geral de frameworks. |
| [Putting It All into Context](<../papers/search-03/Putting It All into Context Simplifying Agents with LCLMs.pdf>) | Prioridade alta se contexto entrar no experimento. | Compara estratégias e modelos com janelas longas; não estabelece um percentual universal de reinício. |
| [Claw-SWE-Bench](<../papers/search-03/Claw-SWE-Bench A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks.pdf>) | Prioridade alta para contrato comum entre ferramentas e avaliação de sistemas completos. | Comparar produtos completos responde uma pergunta diferente de isolar efeito do modelo. |
| [Efficient Benchmarking of AI Agents](<../papers/search-03/Efficient Benchmarking of AI Agents.pdf>) | Planejamento de piloto e triagem de configurações. | Preservar rankings não equivale a estimar taxa absoluta de sucesso. Selecionar dificuldade intermediária muda a população avaliada. |
| [Scaffold Effects on GAIA](<../papers/search-03/Scaffold Effects on GAIA A Controlled Comparison.pdf>) | Apoio ao desenho fatorial, repetição e auditoria de desvios do protocolo. | GAIA não é manutenção de software. Suas três tentativas por pergunta são uma decisão do estudo, não regra de todo benchmark. |
| [Spec Kit Agents](<../papers/search-03/Spec Kit Agents Context-Grounded Agentic Workflows.pdf>) | Apoio para requisitos e verificação ancorada no repositório. | Nota de juiz e testes medem coisas diferentes; inspecionar rubrica, efeito e independência da avaliação. |
| [From Prompt to Process](<../papers/search-03/From Prompt to Process a Process Taxonomy and Comparative Assessment of Frameworks Supporting AI Software Development Agents.pdf>) | Taxonomia para posicionar o ecossistema. | Cobertura de recursos e adoção não demonstram melhora de acerto ou custo. |
| [Position: Coding Benchmarks Are Misaligned...](<../papers/search-03/Position Coding Benchmarks Are Misaligned with Agentic Software Engineering.pdf>) | Motivação e ameaças à validade. | Artigo de posição; suas críticas não são estimativas experimentais de eficácia. |
| [SWE-Compass](<../papers/search-03/SWE-Compass Towards Unified Evaluation of Agentic Coding Abilities for Large Language Models.pdf>) | Ampliação futura de categorias de tarefas. | Mais tipos de tarefa multiplicam as condições. Seu protocolo de tentativa única não representa limite universal. |
| [SOEN-101 / FlowGen](<../papers/search-03/SOEN-101 Code Generation by Emulating Software Process Models Using Large Language Model Agents.pdf>) | Antecedente de papéis e processos com agentes. | Avaliação com modelos antigos e tarefas de geração de funções; não extrapolar o tamanho do efeito para repositórios atuais. |
| [SWE-Bench Mobile](<../papers/search-03/SWE-Bench Mobile Can Large Language Model Agents Develop Industry-Level Mobile Applications.pdf>) | Validade externa para UI, especificações e ambiente industrial. | Infraestrutura e acesso específicos; adiar como benchmark principal se mobile não for o domínio do estudo. |

### Lacunas de cobertura

O acervo é forte em benchmarks e arquiteturas. Precisa aprofundar: decisão sequencial, limites de inferência por repetição, confiabilidade de verificadores, problema do oráculo de testes, correção de patches além dos testes disponíveis, abstenção/calibração, metodologia experimental e custo total. A leitura de métodos recentes deve ser combinada a fundamentos anteriores a 2024; idade não invalida teoria ou método experimental.

## 4. O que implementar, adiar e descartar

| Decisão | Recurso ou ideia | Justificativa |
| --- | --- | --- |
| Implementar primeiro | Execução reproduzível, adaptadores de modelos, orçamento global e logs por chamada | São necessários para medir qualquer hipótese e reproduzir resultados. |
| Implementar primeiro | Separação entre agente executor, verificador acessível e avaliador final oculto | Evita que o sistema use respostas da avaliação para decidir que terminou. |
| Implementar primeiro | Critérios de aceitação ligados a evidências e estados entregar/continuar/escalar/abster | Permite avaliar a qualidade da decisão de encerramento. |
| Implementar primeiro | Políticas simples e configuração de papéis | Fornece baselines e permite alternar qual modelo executa/revisa. |
| Testar como hipótese | Modelo barato executa, forte revisa | Comparar também forte executa, barato revisa, além de modelos únicos. Revisão pode custar mais que a economia na geração. |
| Testar como hipótese | Subagente para analisar logs | Comparar com filtragem determinística, consulta sob demanda e resumo pelo próprio executor. Medir perda de informação e custo adicional. |
| Testar depois | Contexto contínuo, compactação, reinício com estado estruturado | Exige separar perda de informação, reconstrução, cache e recuperação de arquivos. |
| Adiar | Paralelismo amplo e edição concorrente | Introduz custos de coordenação, conflitos e variação de latência. Começar com trajetórias isoladas ou leitor separado. |
| Adiar | Treinar controlador com RL e muitas ações | Primeiro demonstrar vantagem possível e coletar dados adequados. Classificador simples ou regra pode bastar. |
| Adiar | Benchmark próprio, UI, marketplace e muitos provedores | Expande esforço sem resolver a hipótese científica inicial. |
| Descartar como representação principal | “QI” escalar dos modelos | Usar desempenho observado por papel/tarefa e estimativas de incerteza. |
| Descartar como pressuposto | Mais tentativas sempre aproximam qualquer modelo do topo | Pode haver incapacidade estratégica, erros correlacionados e aceitação de falsos positivos. |
| Descartar como alegação inicial | Framework universal ou avaliação sem viés | Declarar população, condições e limites de generalização; controlar vieses identificáveis. |
| Descartar como regra universal | Resetar em x% do contexto; exatamente dez repetições | Ambos exigem justificativa empírica ligada ao objetivo do estudo. |

## 5. Programa de artigos recomendado

> Atualização após esclarecimento do escopo: a orientação vigente é planejar um artigo principal que reúna o ecossistema e sua avaliação. A divisão abaixo permanece como alternativa condicional, não como sequência obrigatória. Ver [orientação consolidada, seção 6](orientacao-ecossistema-e-avaliacao-2026-09-28.md#6-um-artigo-ou-vários-qual-sequência).

### Artigo 1: estudo empírico focalizado

Título de trabalho: “When to Spend on Verification: Cost and Reliability of Heterogeneous Coding-Agent Pipelines”. O título expressa a pergunta, sem antecipar superioridade.

O primeiro artigo deve caracterizar quando gastar em revisão, reparo ou execução forte compensa. Um resultado negativo ou uma fronteira clara de aplicabilidade pode ser contribuição, desde que o experimento esclareça algo ainda não estabelecido pelos concorrentes.

Perguntas de pesquisa propostas:

1. Sob orçamento monetário e limite de tempo comparáveis, como diferentes alocações entre execução e verificação alteram a taxa de resolução e o custo por solução correta?
2. Quais sinais disponíveis durante a execução ajudam a detectar uma entrega incorreta ou a necessidade de escalonamento?
3. Em quais situações revisões adicionais corrigem defeitos, rejeitam soluções corretas ou introduzem regressões?
4. Os efeitos se mantêm em repositórios, linguagens e pares de modelos não usados para ajustar as políticas?

Estrutura sugerida:

1. Introdução: problema, lacuna específica frente aos concorrentes, objetivo e contribuições sustentadas pelos resultados finais.
2. Fundamentos e trabalhos relacionados: roteamento, verificadores, parada e avaliação de software; comparação explícita com os mais próximos.
3. Formulação: tarefa, orçamento, papéis, informação visível, critérios de conclusão e qualidade-alvo.
4. Desenho do estudo: tarefas, auditoria dos testes, modelos, políticas, métricas, repetições e plano estatístico.
5. Resultados organizados pelas perguntas de pesquisa, incluindo falhas e custos de coordenação.
6. Discussão: mecanismos plausíveis, aplicabilidade e implicações para quem desenvolve agentes.
7. Ameaças à validade e reprodutibilidade.
8. Conclusão limitada ao que foi demonstrado.

O ecossistema aparece como instrumento reproduzível. Descrever arquitetura apenas no nível necessário para entender e reproduzir as intervenções.

### Artigo 2: método adaptativo, condicionado ao primeiro

Título de trabalho: “Adaptive Verification and Escalation for Coding Agents under Cost Constraints”.

Só seguir se os dados indicarem que informações observáveis permitem superar uma política fixa razoável. Demonstrar generalização, overhead, custo de treinamento/calibração, acerto das decisões e ganho sobre métodos próximos. Comparar com regressão/árvore ou regra simples, além de modelos sofisticados. Usar avaliação reservada nova e explicar o que é distinto do primeiro artigo.

Se o primeiro estudo não produzir contribuição empírica independente, incorporá-lo como análise motivadora do artigo do método. Evitar dividir o mesmo resultado em dois artigos pequenos.

Não recomendo iniciar um artigo separado para cada pasta de busca, nem uma revisão genérica de frameworks. Um artigo de contexto só se justifica com pergunta e intervenção próprias. A investigação causal de distribuição de linguagens exigiria outro programa, possivelmente com treino controlado.

## 6. Desenho experimental mínimo defensável

Começar com resolução de issues em repositórios. Escolher uma família de benchmark para desenvolvimento e uma avaliação externa viável. Usar amostragem estratificada por repositório/linguagem, sem escolher apenas casos em que o framework já funcionou. Fixar versões e inspecionar se as tarefas têm especificações e testes adequados.

Baselines essenciais, no mesmo ambiente controlado:

- Agente mínimo com modelo barato e agente mínimo com modelo forte.
- Agente mínimo com instruções bem elaboradas e orçamento de ajuste comparável ao da proposta.
- Barato executa + barato revisa; barato executa + forte revisa; forte executa + barato revisa. A configuração forte + forte pode ser referência de custo/qualidade se viável.
- Repetições ou reparos com política fixa e mesma contabilidade de orçamento.
- Política simples de escalonamento, como escalar após falta de progresso definida previamente.
- Método publicado próximo à decisão que será modificada, com adaptação documentada quando necessária.

Não executar o produto cartesiano de todos os modelos, papéis, contextos, linguagens, limites e prompts. Fazer piloto para viabilidade e variância, selecionar intervenções e reservar a avaliação confirmatória. O custo de selecionar configurações também deve ser registrado.

A unidade básica de comparação é a mesma tarefa sob políticas diferentes. Repetições da mesma tarefa não são novas tarefas independentes. Separar desenvolvimento, calibração e teste por repositório quando possível; evitar que variantes da mesma issue vazem entre partições. Randomizar/intercalar a ordem das condições para reduzir efeitos temporais do serviço.

Dez repetições é uma escolha candidata, não garantia de poder estatístico. Planejar amostra usando a menor diferença relevante e a variância do piloto. Se a alegação for “qualidade semelhante por menor custo”, definir uma margem de não inferioridade; ausência de diferença estatística não prova equivalência. Usar diferenças pareadas e intervalos de confiança respeitando agrupamento por tarefa/repositório.

Métricas mínimas:

- Resolução segundo avaliação externa, sobre todas as tarefas designadas.
- Custo total por tarefa e soma dos custos dividida pelo número de tarefas corretamente resolvidas, incluindo tentativas fracassadas e verificadores.
- Proporção de entregas aceitas pelo sistema que falham na avaliação externa, com denominador explícito.
- Cobertura: proporção de tarefas entregues, recusadas/escaladas a humano e encerradas por orçamento.
- Tempo de parede, mediana e cauda; consumo de CPU/GPU/ferramentas quando relevante.
- Regressões introduzidas após uma revisão e correções válidas indevidamente rejeitadas.
- Calibração dos escores, se forem usados como probabilidades.

Avaliar custo e qualidade como curva, não apenas um quociente. Um sistema que resolve apenas tarefas fáceis ou se abstém de quase tudo pode parecer barato e preciso. Exigir cobertura e resolução global evita essa leitura.

## 7. Pontos ainda insuficientemente considerados

**Informação de avaliação.** O agente não deve acessar testes ocultos, gold patch, commit da solução ou respostas do avaliador final. Avaliações offline intermediárias são possíveis para pesquisa, mas seus resultados não podem orientar o agente em execução. Selecionar retrospectivamente a melhor tentativa com o oráculo é limite idealizado, não política implantável.

**Correção dos testes.** Um teste pode aceitar um patch errado ou rejeitar uma implementação alternativa válida. Testes adicionais também precisam de auditoria. Combinar testes externos, inspeção de casos e, quando cabível, propriedades, mutação e revisão humana cega.

**Confundimento de linguagem.** Rust e Python podem aparecer em domínios, repositórios e dificuldades diferentes. Estratificar não basta para provar causalidade da linguagem, e muito menos da distribuição de treino. Modelar ou restringir os confundidores e limitar a alegação.

**Erro compartilhado.** Dois agentes ou dois modelos podem repetir a mesma interpretação equivocada. Separar contexto ou trocar fornecedor não garante independência. Medir sobreposição de erros entre executor e revisor.

**Fim por desistência.** Parar por falta de ganho não significa que o resultado está correto. Um controlador precisa poder encerrar sem aprovar o patch. Medir falso aceite e cobertura simultaneamente.

**Reparo destrutivo.** Mais revisões podem deteriorar um candidato correto. Preservar candidatos e registrar o que mudou para permitir análise, sem escolher pelo avaliador oculto durante a execução.

**Custos reais.** Distinguir desembolso observado, custo marginal e estimativa padronizada. Assinatura já paga não demonstra custo econômico zero. Somar execução, revisão, planejamento, resumos, chamadas falhas faturadas e ferramentas; reportar separadamente infraestrutura e intervenção humana. Não inferir preço de API de um produto sem dados compatíveis.

**Contexto e cache.** Uma conversa contínua não assegura que o prefixo seja processado ou cobrado uma única vez. Registrar uso efetivamente reportado, cache e reconstrução de estado. Não comparar tokens sem distinguir entrada, saída e categorias de cache. Reinício pode economizar histórico e exigir releitura; ambos entram no custo.

**Ponto de equilíbrio do controlador.** Medir custo de coleta, treinamento e calibração, além do custo por decisão. Se a economia por tarefa for positiva, uma aproximação inicial do volume para amortização é custo de preparação dividido pela economia por tarefa. Atualizações frequentes podem exigir recalibração e elevar esse volume.

**Feedback parcial e decisões sequenciais.** O log mostra a consequência da ação escolhida, não a de todas as alternativas. Para aprender escalonamento/parada, coletar explorações controladas e ramificações de estados quando viável. Reavaliar uma política em logs de outra não captura automaticamente como suas novas ações mudariam a trajetória. Um contextual bandit pode servir para escolha isolada; controle multietapas tem dependência temporal e pode exigir outra formulação.

**Vazamento entre treino e teste.** Sinais de dificuldade baseados no tamanho do gold patch ou nos arquivos da solução não estão disponíveis na implantação. Somente informação presente até a decisão pode ser entrada do controlador. Avaliação futura precisa incluir modelos/versões e repositórios não vistos, com custos recalculados de modo transparente.

**Falhas de infraestrutura.** Registrar instalação, timeout, API, limite de contexto e erro de agente separadamente. Definir exclusões antes da avaliação. Não descartar seletivamente falhas que tornam uma condição mais cara ou menos eficaz.

**Generalização e humanos.** Acertar testes de benchmark não prova manutenibilidade, qualidade arquitetural ou redução de trabalho do mantenedor. Se essas forem alegações, precisam de critérios e avaliação humana próprios. Alegação de modelo agnóstico exige evidência em mais de uma família, embora não obrigue contratar um fornecedor específico.

## 8. Próximas buscas bibliográficas

### Search-04: concorrentes diretos e limites do ganho por orçamento

Ler primeiro:

1. [The Limits of Inference Scaling Through Resampling, ICLR 2026](https://proceedings.iclr.cc/paper_files/paper/2026/hash/95591b7557edea46ae1d90b0e9e825c5-Abstract-Conference.html). Confronta diretamente a hipótese de modelos fracos compensarem capacidade com repetição quando o verificador falha. Não extrapolar suas condições para todo tipo de busca/reparo.
2. [SWE-Router](https://arxiv.org/abs/2607.00053). Referência para escalonamento baseado na trajetória.
3. [Verify, Repair, Repeat, or Stop?](https://arxiv.org/abs/2607.17641). Referência para parada, falso aceite e dano por reparo; preprint sob revisão na página consultada.
4. [LoopArena](https://arxiv.org/abs/2608.28281). Protocolo para avaliar controle do processo separado da capacidade do executor.
5. [Knowing When to Ask for Help](https://arxiv.org/abs/2608.24087). Escalonamento e competência estimada durante a geração.
6. [AI Agents That Matter](https://arxiv.org/abs/2407.01502), [RouteLLM](https://arxiv.org/abs/2406.18665), [SWE-Gym](https://arxiv.org/abs/2412.21139) e [Budget-Aware Tool Use](https://arxiv.org/abs/2511.17006). Fundamentos e comparadores adicionais; observar que o foco principal de Budget-Aware Tool Use é busca na web.

Consultas candidatas:

```text
("software engineering agents" OR "coding agents") AND (routing OR escalation OR "model selection") AND (cost OR budget)
("LLM agents" OR "coding agents") AND ("optimal stopping" OR termination OR "verify repair")
(verifier OR "test-time scaling") AND (resampling OR "best-of-N") AND ("false positives" OR cost)
```

### Search-05: confiabilidade da avaliação e decisão de entregar

Prioridades:

- [The Oracle Problem in Software Testing: A Survey](https://discovery.ucl.ac.uk/id/eprint/1471263/), IEEE TSE 2015. Base para entender como decidir se comportamento é correto.
- [EvalPlus: Is Your Code Generated by ChatGPT Really Correct?](https://arxiv.org/abs/2305.01210). Testes insuficientes e correção real no contexto avaliado.
- [SWE-ABS](https://arxiv.org/abs/2603.00520), já identificado na planilha, com [implementação dos autores](https://github.com/OpenAgentEval/SWE-ABS). Investigar fortalecimento de testes e seus limites.
- [LLM Evaluators Recognize and Favor Their Own Generations](https://arxiv.org/abs/2404.13076). Viés de avaliação; sua existência no domínio estudado motiva testar, não presumir o mesmo tamanho de efeito em patches.
- [Conformal Selective Prediction with General Risk Control](https://arxiv.org/abs/2603.24704). Possível fundamento para abstenção; garantias dependem de hipóteses e não se transferem automaticamente para trajetórias adaptativas.
- [Experimentation in Software Engineering, edição de 2024](https://link.springer.com/book/10.1007/978-3-662-69306-3). Planejamento, medidas, experimentos e ameaças à validade.

Pesquisar também a tradição de avaliação de correção de patches em reparo automático, testes metamórficos, testes baseados em propriedades, mutação, calibração e avaliação seletiva. Essas áreas fornecem alternativas a confiar apenas em outro LLM.

```text
"automated program repair" AND ("patch correctness" OR overfitting OR "test oracle")
("code review" OR verifier) AND (LLM OR agent) AND (calibration OR "false acceptance" OR reliability)
("selective prediction" OR abstention OR "risk coverage") AND (LLM OR agents)
("empirical software engineering") AND ("non-inferiority" OR "effect size" OR replication OR "power analysis")
```

### Search-06: estado, contexto e coordenação, após fixar o recorte

Ler [Why Do Multi-Agent LLM Systems Fail?](https://arxiv.org/abs/2503.13657), [Lost in Compaction](https://arxiv.org/abs/2608.11242) e [The Illusion of Diminishing Returns: Measuring Long Horizon Execution in LLMs](https://arxiv.org/abs/2509.09677), além de icat-agent e Putting It All into Context já presentes. Investigar transferência de estado entre modelos, erros em resumos e custo do cache.

```text
("coding agents" OR "software engineering agents") AND ("context compaction" OR "context reset" OR "state transfer")
("multi-agent" OR "agent orchestration") AND ("correlated errors" OR "coordination cost" OR termination)
("LLM routing") AND ("distribution shift" OR "unseen models" OR "off-policy evaluation")
```

### Atualização da seleção de benchmarks

Promover da planilha para leitura integral: [SWE-rebench V2](https://arxiv.org/abs/2602.23866), [Does SWE-Bench-Verified Test Agent Ability or Model Memory?](https://arxiv.org/abs/2512.10218) e, se Rust for central, [Rust-SWE-bench](https://arxiv.org/abs/2602.22764). Considerar também [SWE-bench Goes Live!](https://arxiv.org/abs/2505.23419).

Atualizar a avaliação de SWE-bench Verified com a [auditoria de fevereiro de 2026](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/) e examinar a [auditoria de SWE-bench Pro de julho de 2026](https://openai.com/index/separating-signal-from-noise-coding-evaluations/). São análises de um fornecedor, não consenso independente. Elas são motivo para inspecionar instâncias e combinar evidências, não para substituir automaticamente um leaderboard por outro.

Benchmark recente, linguagem nova ou conjunto privado não garantem ausência de contaminação nem teste correto. Verificar acesso, licença, custo de execução, datas das instâncias, exposição pública e diferenças entre conjunto de treino e avaliação.

## 9. Como conduzir a leitura daqui em diante

Usar buscas em IEEE Xplore, ACM Digital Library, proceedings de conferências, OpenReview e arXiv, complementadas por busca retroativa e prospectiva de citações. Registrar consulta, base, data e decisão de inclusão. Priorizar trabalhos recentes para números e concorrência; preservar fundamentos metodológicos antigos quando relevantes.

Para cada trabalho, preencher uma ficha: pergunta, contribuição, tarefa/população, modelos/versões, harness, informação disponível ao agente, verificador, avaliador final, orçamento, custo real ou estimado, amostra/repetições, independência das observações, baselines, ablações, incerteza, código/dados e limitações. Registrar a página/seção que sustenta cada conclusão. Separar alegações dos autores da interpretação para este projeto.

Antes de escolher o artigo do método, produzir uma matriz comparativa entre SWE-Router, VRR-Stop, LoopArena, icat-agent e a proposta. Em seguida, um piloto deve responder se existe economia possível sob qualidade e cobertura comparáveis e se os sinais para escolher ações estão disponíveis antes da decisão. Só depois investir em treinamento de um controlador.

Nenhum novo item foi inserido manualmente em `references.bib`. As fontes externas acima são candidatas verificadas para inclusão e leitura via Zotero; não são chaves bibliográficas prontas para o manuscrito.
