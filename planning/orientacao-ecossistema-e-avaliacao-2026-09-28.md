# Orientação para construir e avaliar o ecossistema de agentes

Data: 28 de setembro de 2026.

Este documento registra a orientação apresentada na conversa sobre escopo, fundamentos, bibliografia, avaliação e publicação. É um documento de planejamento, sem resultados experimentais próprios. A orientação de publicação aqui apresentada atualiza a proposta preliminar do parecer anterior: planejar um artigo principal reunindo o ecossistema e sua avaliação; artigos adicionais dependem de contribuições independentes.

**Sim, é válido construir esse ecossistema com esse objetivo. A literatura justifica investigar a proposta; ainda não permite afirmar que ela alcançará, simultaneamente, qualidade equivalente, menor custo e menor tempo.** Isso é justamente o que os experimentos precisam determinar.

## 1. Qual é o escopo: construir o ecossistema ou investigar em quais condições ele funciona?

**O objetivo principal continua sendo construir e avaliar o ecossistema.** Sua formulação proposta é:

> Desenvolver e avaliar um ecossistema de agentes para engenharia de software que utilize modelos baratos como executores principais e intervenções seletivas de modelos avançados, buscando qualidade comparável à de um agente com modelo avançado, com menor custo monetário e menor tempo de execução.

A pergunta principal do artigo acompanha esse objetivo:

> O ecossistema proposto consegue preservar a qualidade das entregas de um agente baseado em modelo avançado, reduzindo custo e tempo?

A pergunta anteriormente sugerida — “em quais classes de tarefas e condições...” — é uma pergunta secundária, que explica os resultados:

> Em quais tarefas essa vantagem aparece, quais componentes a produzem e onde ela deixa de existir?

Não é necessário fazer um artigo preliminar inteiro sobre isso. É possível construir, avaliar e analisar essas condições no mesmo trabalho.

Essa distinção importa porque uma média favorável pode esconder resultados diferentes: economia em correções localizadas e prejuízo em mudanças arquiteturais, por exemplo. Investigar isso torna a conclusão útil sem mudar o objetivo.

### Em que se apoia a viabilidade?

Há três linhas de evidência:

| Evidência | O que sustenta para a ideia | O que ainda não demonstra |
|---|---|---|
| Otimização conjunta de custo e acerto | É possível melhorar a relação entre os dois em algumas configurações. | Que qualquer framework ou tarefa terá esse benefício. |
| Roteamento entre modelos baratos e fortes | Informações obtidas durante a execução podem ajudar a decidir quando gastar com um modelo forte. | Que auxílio limitado do forte sempre basta para preservar qualidade. |
| Engenharia do agente | Contexto, ferramentas, validação e organização do trabalho podem alterar os resultados do mesmo modelo. | Que adicionar mais componentes necessariamente melhora o sistema. |

Essas linhas aparecem, respectivamente, em [AI Agents That Matter](https://arxiv.org/abs/2407.01502), [SWE-Router](https://arxiv.org/abs/2607.00053) e [icat-agent](https://arxiv.org/abs/2606.25514). Os dois últimos são trabalhos recentes que precisam ser confrontados diretamente com a proposta.

Existe também evidência contrária a uma versão simplificada da ideia: **repetir muitas vezes um modelo barato pode não compensar sua menor capacidade quando o verificador aceita soluções incorretas**. Isso é investigado em [The Limits of Inference Scaling Through Resampling](https://proceedings.iclr.cc/paper_files/paper/2026/hash/95591b7557edea46ae1d90b0e9e825c5-Abstract-Conference.html). O resultado se refere às condições estudadas; não invalida toda combinação de roteamento, contexto e assistência forte.

A avaliação da proposta é:

- **Viabilidade como projeto:** sim.
- **Hipótese cientificamente fundamentada:** sim.
- **Originalidade já estabelecida:** ainda não; roteamento e scaffolding já têm concorrentes próximos.
- **Superioridade comprovada:** depende dos experimentos.

A contribuição precisará estar no mecanismo desenvolvido e demonstrado — por exemplo, quando e como pedir ajuda limitada ao modelo forte mantendo a execução principal no barato.

## 2. O que as três buscas permitem concluir?

As conclusões abaixo são uma síntese crítica da bibliografia examinada, não o resultado de uma revisão sistemática ou de reproduções experimentais. As pastas representam temas de pesquisa, não artigos separados.

### Search-01: linguagens e distribuição de treinamento

**Conclusão defensável:** a composição dos dados de treinamento pode afetar o desempenho por linguagem; avaliar em uma linguagem não autoriza generalizar para todas.

O trabalho *Measuring The Impact Of Programming Language Distribution* encontra mudanças de desempenho ao modificar a distribuição de linguagens em treinamento controlado. Isso sustenta a importância da composição dos dados, mas não revela a composição dos modelos proprietários atuais. [Fonte](https://arxiv.org/abs/2302.01973).

**“Python é melhor” não deve ser adotado como conclusão geral da busca.** O resultado também depende de modelo, tarefa, bibliotecas, ferramentas, dificuldade e benchmark.

Esse tema deve entrar como justificativa metodológica e limite de generalização, sem comandar o artigo.

Aplicação prática:

- Registrar as linguagens avaliadas.
- Apresentar resultados por linguagem quando houver amostra suficiente.
- Evitar atribuir à linguagem diferenças que também podem vir de repositórios e tarefas.
- Se começar só com Python, declarar esse recorte e ampliar posteriormente.

Não é necessário investigar causalmente o treinamento dos modelos para construir o ecossistema.

### Search-02: benchmarks

**Conclusão defensável:** já foram encontradas famílias de benchmarks úteis, mas elas medem capacidades diferentes e não garantem, por si só, uma avaliação robusta.

Resolução de issues, implementação de funcionalidades, construção de projetos e desenvolvimento de interfaces não são medidas intercambiáveis. Somar todos esses benchmarks logo no início aumentaria bastante o escopo.

**É válido usar benchmarks existentes. A robustez vem da combinação entre benchmark, protocolo e qualidade da verificação.** Há evidência de patches que passam nos testes de benchmarks e continuam incorretos; o [SWE-ABS](https://arxiv.org/abs/2603.00520) investiga diretamente essa fragilidade.

Para o primeiro estudo, a proposta é escolher:

1. Uma família principal de tarefas: resolução de issues em repositórios.
2. Um conjunto para desenvolver e ajustar o sistema.
3. Um conjunto reservado para avaliação final, preferencialmente incluindo repositórios não usados no ajuste.
4. Uma verificação complementar, por testes adicionais auditados e/ou revisão cega de uma amostra, conforme a viabilidade.

SWE-bench Verified pode oferecer comparação histórica; conjuntos multilíngues ou como [SWE-rebench V2](https://arxiv.org/abs/2602.23866) são candidatos a ampliar a avaliação. A escolha final exige verificar execução, testes, exposição das soluções e custo do ambiente.

A busca de benchmarks está suficientemente desenvolvida para iniciar um piloto e selecionar candidatos. Ainda não para declarar encerrado o protocolo experimental.

**Não existe um limite universal de `max_attempts = 3`.** Repetições experimentais, tentativas internas de resolver uma tarefa e número de passos são coisas diferentes.

### Search-03: frameworks e engenharia de agentes

**Conclusão defensável:** o framework pode alterar desempenho e eficiência, mas o benefício depende do componente, do modelo e da tarefa.

Os resultados da coleção apontam em direções complementares:

- **Agentless:** um processo relativamente simples pode ser competitivo. Ele inclui localização, reparo e validação; não equivale a “apenas um prompt”. [Fonte](https://arxiv.org/abs/2407.01489).
- **The Scaffold Effect:** trocar o ambiente de execução do agente altera fortemente o consumo de tokens; muitas diferenças de acerto no estudo permanecem estatisticamente incertas. [Fonte](https://arxiv.org/abs/2607.22585).
- **icat-agent:** os autores relatam melhorias com o mesmo modelo ao modificar a organização dos agentes e do contexto. [Fonte](https://arxiv.org/abs/2606.25514).
- **SWE-Skills-Bench:** muitas skills avaliadas adicionaram pouco ou nenhum ganho, algumas com overhead significativo. Esse resultado trata de skills, não de toda engenharia de agentes. [Fonte](https://arxiv.org/abs/2603.15401).

A visão geral é: **há espaço para engenharia útil, e cada componente precisa justificar seu custo.** A busca sustenta desenvolver um sistema modular e testar suas partes.

## 3. Quais métricas e comparações usar?

Adotar qualidade, custo monetário e tempo como três resultados principais separados. Um índice único pode esconder perda de qualidade ou aumento de latência.

| Dimensão | Medida proposta |
|---|---|
| Qualidade funcional | Proporção de tarefas corretamente resolvidas segundo avaliação externa ao agente |
| Custo | Custo total por tarefa, incluindo falhas, revisões, planejamento e roteamento |
| Eficiência econômica | Custo total de todas as execuções dividido pelo número de tarefas corretamente resolvidas |
| Tempo | Tempo decorrido por tarefa, com mediana e percentil 95 |
| Confiabilidade da entrega | Proporção de entregas que o sistema aprovou, mas a avaliação externa rejeitou |
| Cobertura | Proporção de tarefas entregues, abandonadas ou encaminhadas para intervenção humana |

A taxa de resolução operacionaliza uma parte da qualidade. Manutenibilidade, segurança e qualidade visual precisam de medidas próprias se forem alegações do artigo.

Para afirmar “qualidade semelhante”, definir antes da avaliação final uma margem máxima aceitável de perda e avaliar a incerteza estatística. Não encontrar diferença significativa não demonstra equivalência.

As três configurações propostas são um bom começo:

| Configuração | Pergunta respondida |
|---|---|
| Modelo forte em agente básico bem configurado | Qual é a referência de qualidade, custo e tempo? |
| Modelo barato no mesmo agente básico | Qual é a diferença inicial entre os modelos? |
| Modelo barato + ecossistema proposto, com ajuda forte limitada | A proposta fecha essa diferença de maneira econômica? |

“Modelo sozinho” precisa significar um agente com acesso adequado a arquivos, execução e testes; um modelo sem essas ferramentas seria uma comparação injusta para tarefas de repositório.

**Para o artigo final, essas três condições precisam de controles adicionais:** pelo menos uma política simples de ajuda forte e versões do sistema com componentes principais desligados. Assim é possível distinguir o ganho de simplesmente usar o modelo forte do ganho produzido pelo roteamento.

Definir também o significado operacional de “executor principal”: papéis permitidos, intervenções do forte e orçamento. Contar apenas quem escreveu o patch não basta se o forte tiver elaborado toda a solução.

Se ficar mais barato, mas mais lento, foi demonstrada uma troca entre custo e tempo. Para sustentar o objetivo completo, os três critérios precisam ser satisfeitos na mesma comparação.

## 4. Quais temas faltam pesquisar e o que faria repensar o escopo?

Concentrar as próximas buscas nos seis temas abaixo. Os quatro primeiros devem orientar o piloto; os demais podem avançar junto da implementação.

| Tema e termos para buscar | Resposta necessária | Achado que faria mudar o projeto |
|---|---|---|
| **Roteamento e colaboração entre modelos** — `coding agents`, `model routing`, `escalation`, `heterogeneous agents` | Quando chamar o forte? Ele planeja, diagnostica, revisa ou executa? Que informação orienta essa escolha? Qual o ganho sobre regras simples? | Se um método existente já realiza a proposta, incorporar e comparar com ele; procurar uma contribuição específica. Se o forte precisar assumir quase toda a tarefa, rever a restrição ou reduzir as classes de tarefas. |
| **Limites de repetição e alocação de orçamento** — `inference scaling`, `resampling`, `budget allocation`, `correlated errors` | Mais esforço do barato gera soluções novas e corretas ou repete erros? Onde o ganho deixa de compensar custo e tempo? | Se repetição não fechar a diferença, abandonar “mais tentativas” como mecanismo central e priorizar diagnóstico, contexto ou assistência forte. |
| **Verificação e parada** — `patch correctness`, `test oracle`, `verify repair`, `optimal stopping`, `false acceptance` | Quais evidências permitem aprovar, reparar ou parar sem aprovar? Quanto custa verificar? Revisões introduzem regressões? | Se não houver verificação confiável e econômica, limitar inicialmente o sistema a tarefas com testes fortes ou incluir aprovação humana, medindo seu custo. |
| **Validade dos benchmarks e desenho experimental** — `benchmark contamination`, `test adequacy`, `non-inferiority`, `paired evaluation` | O conjunto representa as tarefas pretendidas? Os testes distinguem patches corretos? Como demonstrar qualidade comparável e generalização? | Se o benchmark medir outra capacidade ou aceitar muitos erros, trocar/complementar a avaliação e restringir as alegações. |
| **Contexto e coordenação** — `context compaction`, `state transfer`, `multi-agent coordination cost` | Reinícios, resumos e agentes auxiliares preservam informação? Economizam dinheiro e tempo após contabilizar releitura e coordenação? | Se os ganhos forem pequenos ou negativos, manter contexto e fluxo simples. Se dependerem do modelo, usar políticas configuráveis. |
| **Aprendizado do controlador** — `learned routing`, `contextual bandits`, `policy learning`, `distribution shift` | Sinais observáveis permitem decisões melhores que regras? Quantos dados são necessários? O ganho se mantém em outros modelos e repositórios? | Se regras simples forem igualmente eficazes ou o treinamento não se pagar, dispensar controlador treinado. O ecossistema continua válido. |

Leituras iniciais para essas decisões:

- **Roteamento:** [SWE-Router](https://arxiv.org/abs/2607.00053).
- **Limites do esforço adicional:** [The Limits of Inference Scaling Through Resampling](https://proceedings.iclr.cc/paper_files/paper/2026/hash/95591b7557edea46ae1d90b0e9e825c5-Abstract-Conference.html).
- **Parada e reparo:** [VRR-Stop](https://arxiv.org/abs/2607.17641).
- **Verificação dos benchmarks:** [SWE-ABS](https://arxiv.org/abs/2603.00520).
- **Contexto e organização:** icat-agent e *Putting It All into Context*, já presentes na coleção.

Para cada tema, produzir uma ficha curta com o que já funciona, em quais condições, o que falha e qual decisão isso implica para o sistema. A bibliografia orienta essas decisões; a transferência dos resultados para os modelos escolhidos precisa ser testada no piloto.

A lista consolidada de leituras está em [artigos-recomendados.md](artigos-recomendados.md).

## 5. Onde entram screenshots e outras funcionalidades para o desenvolvedor?

**Elas podem fazer parte do produto desde o início, mesmo sem constituírem a contribuição científica principal.** Não é necessário transformar cada funcionalidade em hipótese ou artigo.

No exemplo do screenshot, existem três usos diferentes:

| Uso | Como entra na avaliação |
|---|---|
| O sistema entrega uma captura para documentar o resultado | Funcionalidade de documentação e rastreabilidade; contabilizar seu custo e tempo |
| O agente usa a captura para encontrar e corrigir problemas | Componente de verificação; testar seu efeito na qualidade |
| O desenvolvedor usa a captura para revisar mais rapidamente | Hipótese sobre produtividade humana; exige estudo com desenvolvedores para afirmar esse benefício |

Uma captura comprova o estado visual observado naquele momento; não comprova sozinha a correção do frontend.

A recomendação é implementar essas funcionalidades como módulos. No primeiro artigo, descrever as que ajudam a entender o sistema e avaliar experimentalmente as que sustentam as alegações centrais.

## 6. Um artigo ou vários? Qual sequência?

**Planejar um artigo principal reunindo o ecossistema e sua avaliação.** A divisão anterior em estudo empírico seguido de método adaptativo era uma possibilidade, não uma etapa obrigatória.

O artigo principal pode seguir esta estrutura:

1. **Problema e lacuna:** custo de agentes avançados e limites das alternativas existentes.
2. **Proposta:** execução barata, assistência forte delimitada e decisões de orquestração.
3. **Implementação:** arquitetura necessária para reproduzir o método.
4. **Avaliação:** comparação com agentes básicos e métodos próximos.
5. **Análise dos componentes:** o que produz o ganho e em quais tarefas.
6. **Limitações:** falhas, condições de aplicação e generalização.

Um segundo artigo só se justifica se surgir uma contribuição independente:

- **Controlador aprendido:** se for desenvolvido um método de decisão novo, superior às regras e ao estado da arte.
- **Produtividade do desenvolvedor:** se forem avaliados revisão humana, esforço, usabilidade e funcionalidades como evidências visuais.
- **Contexto ou verificação:** se um desses componentes gerar uma contribuição própria, com avaliação suficiente.

A sequência prática recomendada é:

1. Ler os concorrentes diretos e os limites de verificação, delimitando a diferença da proposta.
2. Fixar a primeira tarefa-alvo e o protocolo de sucesso.
3. Construir um protótipo mínimo instrumentado, com barato, forte e colaboração simples.
4. Executar o piloto, medindo onde se perde qualidade, dinheiro e tempo.
5. Implementar as intervenções justificadas por essas falhas.
6. Congelar a configuração e fazer a avaliação reservada.
7. Escrever o artigo principal com o alcance demonstrado pelos resultados.

É possível começar a construir antes de terminar toda a leitura. O primeiro compromisso deve ser com um protótipo que permita testar a hipótese; o investimento em um ecossistema maior cresce conforme as evidências mostrarem quais recursos valem a pena.

## Documentos relacionados

- [Lista consolidada de artigos recomendados](artigos-recomendados.md).
- [Parecer bibliográfico anterior](parecer-pesquisa-2026-09-28.md), com inventário, ameaças à validade e consultas de busca. Para a sequência de publicação, prevalece a seção 6 deste documento.

Os links são referências de leitura para planejamento. A inclusão de citações no manuscrito deve ocorrer por Zotero e Better BibTeX; este documento não altera `references.bib`.
