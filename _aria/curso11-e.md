---
title: Conclusão e Boas Práticas
layout: default
nav_order: 5
---
# Conclusão e Boas Práticas

Chegámos ao fim do módulo. As quatro secções anteriores trataram, cada uma, de uma pergunta diferente sobre a mesma coisa: uma interface que se comporta como um programa, mas que continua a viver dentro de um navegador.

---

## Recapitulação

### O fio condutor de todo o módulo

Se houver uma única frase a reter deste módulo, é esta:

> **Numa aplicação rica, tudo aquilo que o navegador fazia de graça passa a ser responsabilidade de quem programa.**

Num sítio Web tradicional, quando se clica numa ligação, o navegador faz automaticamente cinco coisas: carrega conteúdo novo, muda o título da janela, recoloca o ponto de partida da leitura no início do documento, regista a mudança no histórico e atualiza o endereço. Ninguém tem de programar nada disto — acontece.

Numa aplicação rica, o conteúdo muda sem a página recarregar. O navegador deixa de fazer essas cinco coisas. E, se ninguém as fizer em substituição, elas simplesmente **deixam de existir** — não para toda a gente, mas para quem depende delas para se orientar.

Foi isto que o módulo tratou, em quatro camadas sucessivas:

| Secção | Pergunta a que responde | Ideia central |
|---|---|---|
| **Aplicações Ricas** | *O que mudou quando a Web passou a ser aplicação?* | A aplicação tem de repor os sinais que o navegador deixou de dar |
| **Estruturas e Relações** | *O que é que existe aqui, e o que anda junto com o quê?* | O significado que está no desenho tem de estar também no código |
| **Ordem de Leitura e Foco** | *Por onde se anda, e para onde se vai quando algo muda?* | Existe um percurso, e esse percurso tem de fazer sentido |
| **Notificações e Atualizações de Conteúdo** | *Como é que se fica a saber o que aconteceu sem estar a olhar?* | Mudanças que não movem o foco continuam a precisar de voz |

Repare na progressão: **arquitetura → semântica → percurso → comunicação**. Não é uma ordem arbitrária. É também a ordem correta para trabalhar num projeto real, e a ordem em que os problemas se resolvem mais barato.

### O que levar de cada secção

#### Da secção «Aplicações Ricas»

A distinção entre documento e aplicação não é uma questão de tecnologia usada, mas de **comportamento**: há mudança de estado sem recarregamento de página, há vistas que se substituem, há componentes que não existem em HTML. Sempre que isso acontece, a aplicação assume obrigações que antes eram do navegador.

Vimos também que a maior parte das falhas graves em aplicações ricas **não são falhas de ARIA**. São falhas de arquitetura: mudança de vista que ninguém anuncia, título que nunca muda, endereço que não reflete o que está no ecrã, botão de retroceder que atira a pessoa para fora da aplicação. Podemos ter todos os campos perfeitamente rotulados e ter, ainda assim, uma aplicação impossível de usar.

> **A regra que resume a secção:** se o elemento **leva a algum lado**, é uma ligação; se **faz alguma coisa**, é um botão; se não é nenhum dos dois, provavelmente não devia ser clicável. Toda a acessibilidade de uma aplicação assenta em não deitar fora o HTML antes de chegar ao ARIA.

#### Da secção «Estruturas e Relações»

O ecrã comunica muito mais do que aquilo que está escrito. Uma caixa com sombra diz «isto é uma unidade». Uma coluna estreita à esquerda diz «isto é navegação». Um texto pequeno debaixo de um campo diz «isto explica aquele campo». Um espaço em branco diz «isto acabou, começa outra coisa».

**Nada disto chega às tecnologias de apoio a menos que exista também no código.** Foi esse o trabalho desta secção: transformar em estrutura programática aquilo que o desenho comunica visualmente — regiões, agrupamentos, hierarquia de títulos, listas que são mesmo listas, e relações explícitas entre elementos que se referem uns aos outros.

> **A regra que resume a secção:** se for preciso *ver* o ecrã para perceber que dois elementos andam juntos, então essa relação ainda não existe. Existe apenas uma sugestão visual.

#### Da secção «Ordem de Leitura e Foco»

Aqui trabalhámos os **quatro C**: coerência (o que se lê corresponde ao que se vê), continuidade (quando o conteúdo muda, o foco vai para o sítio certo), contenção (o foco fica dentro dos limites certos, sem se prender nem escapar) e consciência (é possível saber sempre onde se está).

A distinção mais importante da secção — e a que mais confusão causa — é entre **a ordem que se vê** e **a ordem que existe**. O que se vê é o resultado de folhas de estilo aplicadas a um documento; o que as tecnologias de apoio percorrem é o documento. Quando os dois divergem, quem vê não repara e quem não vê tropeça. Um `order` do CSS Flexbox mal usado é invisível para a esmagadora maioria das pessoas da equipa e é uma barreira diária para quem navega com teclado.

> **A regra que resume a secção:** o CSS reorganiza a *apresentação*, nunca o *conteúdo*. Se a ordem visual desejada não corresponde à ordem do código, é o código que deve mudar.

#### Da secção «Notificações e Atualizações de Conteúdo»

A última secção tratou do que acontece quando alguma coisa muda **e o foco não se move**: resultados que se atualizam enquanto se escreve, guardar automático, contadores, mensagens de progresso, notificações que aparecem a um canto e desaparecem sozinhas.

Este é o único caso em que o «altifalante» — as regiões *live* — é a ferramenta certa. Nos restantes, mover o foco é melhor, porque leva a pessoa até à informação em vez de lhe atirar a informação ao ouvido e a deixar sem saber onde é que aquilo está.

> **A regra que resume a secção:** anunciar não é o mesmo que informar. Uma mensagem anunciada e depois removida do ecrã existiu durante um segundo e meio para quem a ouviu, e nunca existiu para quem chegou tarde.

### A decisão que atravessa o módulo inteiro

Quase todos os problemas práticos de uma aplicação rica se resolvem respondendo bem a uma única pergunta: **mudou alguma coisa no ecrã — e agora?**

Esta tabela junta o que ficou disperso pelas quatro secções e é, provavelmente, a página mais útil de todo o módulo:

| O que mudou | O que fazer | Secção onde foi tratado |
|---|---|---|
| A pessoa navegou para outra vista | Atualizar o título, definir novo ponto de partida do foco, atualizar o endereço e o histórico | «Aplicações Ricas» + «Ordem de Leitura e Foco» |
| Abriu-se um diálogo ou painel que exige atenção | Mover o foco para dentro, conter o foco, devolver ao ponto de origem ao fechar | «Ordem de Leitura e Foco» |
| A pessoa apagou ou removeu um item de uma lista | Mover o foco para um destino previsível e confirmar a ação | «Ordem de Leitura e Foco» + «Notificações» |
| Apareceu conteúdo novo imediatamente a seguir ao controlo que o pediu | Não mexer no foco; a estrutura e a relação já o explicam | «Estruturas e Relações» |
| Resultados atualizaram-se enquanto a pessoa escrevia | Anunciar com delicadeza, sem interromper, sem mover o foco | «Notificações e Atualizações de Conteúdo» |
| Uma operação em segundo plano falhou | Anunciar de imediato e deixar a mensagem no ecrã, acessível depois | «Notificações e Atualizações de Conteúdo» |
| Mudou apenas o estado de um componente (aberto, selecionado, premido) | Refletir o estado nas propriedades do próprio componente | Módulo sobre **Widgets** |

**Porque é que esta tabela é importante:** obriga a separar três mecanismos que muitas equipas confundem — mover o foco, anunciar sem mover o foco, e atualizar o estado de um componente. Usar o mecanismo errado é a causa da maior parte das aplicações que «têm ARIA» e continuam inutilizáveis: aplicações que anunciam tudo em modo urgente e não deixam ninguém trabalhar, ou que roubam o foco a cada resposta do servidor, ou que atualizam silenciosamente metade do ecrã sem nunca dizer nada.

### Uma nota sobre método

Vale a pena terminar com uma observação que não é técnica.

Em quase todos os exemplos deste módulo, a versão problemática e a versão corrigida **produzem exatamente o mesmo ecrã**. São visualmente indistinguíveis. Isto tem duas consequências práticas:

- **Não se deteta este tipo de problemas a olhar.** Detetam-se a navegar com teclado, a ouvir com leitor de ecrã e a inspecionar a árvore de acessibilidade.
- **Também não se detetam com ferramentas automáticas.** Uma ferramenta automática consegue dizer que falta um rótulo ou que o contraste é insuficiente. Não consegue dizer que o foco foi para o sítio errado depois de apagar uma linha, nem que a mudança de vista não foi anunciada, nem que a ordem de tabulação contradiz o desenho. Estas são precisamente as falhas mais graves das aplicações ricas.

A avaliação automática é um bom primeiro filtro. Nunca é uma conclusão.

---

## Recursos Adicionais

### Normas e especificações técnicas

| Recurso | Para que serve |
|---|---|
| **WCAG 2.1** (`w3.org/TR/WCAG21/`) | O texto normativo que constitui a base legal atual em Portugal, através da EN 301 549 |
| **WCAG 2.2** (`w3.org/TR/WCAG22/`) | Versão mais recente. Acrescenta critérios muito relevantes para aplicações ricas. Ainda não é a base legal, mas está prestes a sê-lo |
| **Understanding WCAG** e **How to Meet WCAG** (`w3.org/WAI/WCAG22/quickref/`) | Documentos de apoio do W3C: intenção de cada critério, técnicas suficientes e falhas documentadas. É aqui que se resolve a maior parte das dúvidas de interpretação |
| **EN 301 549** | Norma harmonizada europeia. É o instrumento que transforma as WCAG em requisito de contratação pública e de conformidade legal |
| **WAI-ARIA 1.2** (`w3.org/TR/wai-aria-1.2/`) | Especificação normativa dos papéis, estados e propriedades ARIA |
| **ARIA in HTML** (`w3.org/TR/html-aria/`) | Diz que combinações de ARIA são válidas em cada elemento HTML. Evita a maior parte dos erros de ARIA mal aplicado |
| **ARIA Authoring Practices Guide (APG)** (`w3.org/WAI/ARIA/apg/`) | Padrões de referência para componentes: teclas esperadas, papéis, estados. Guia de implementação, não documento normativo |

> **Cuidado com o APG.** É um recurso excelente e muito usado, mas é um guia de *padrões*, não uma norma. Copiar um padrão do APG sem perceber o que cada atributo faz produz componentes que parecem corretos e falham no essencial. Use-se como referência de comportamento esperado, não como código para colar.

### Ferramentas de verificação

Nenhuma destas ferramentas verifica acessibilidade sozinha. Verificam-se **com** elas.

**Leitores de ecrã** — é indispensável testar com pelo menos um, e desejável com dois em plataformas diferentes:

- **NVDA** (Windows, gratuito) — o mais acessível para quem está a começar a testar
- **JAWS** (Windows, comercial) — muito usado profissionalmente em Portugal
- **VoiceOver** (macOS e iOS, integrado) — indispensável para testar o comportamento em iOS

**Controlo por voz e entrada alternativa:**

- **Dragon NaturallySpeaking**, **Controlo por Voz** da Apple, **Voice Access** (Android e Windows) — para verificar se os nomes visíveis dos controlos correspondem ao que a pessoa diz em voz alta

**Inspeção técnica:**

- **Árvore de acessibilidade** das ferramentas de programador do navegador — mostra exatamente o que a aplicação está a expor às tecnologias de apoio, que é frequentemente diferente do que se julga estar a expor
- **Validadores automáticos** integrados no navegador ou na cadeia de integração contínua — bons para detetar regressões em atributos e contraste

**Verificação sem ferramentas nenhumas** — o teste mais barato e mais revelador que existe:

1. Desligar o rato.
2. Percorrer uma tarefa completa da aplicação usando apenas `Tab`, `Shift+Tab`, setas, `Enter`, `Espaço` e `Escape`.
3. Registar todos os momentos em que se deixou de saber onde se estava.

Se a lista não estiver vazia, ainda há trabalho por fazer — e esse trabalho está descrito nas quatro secções anteriores.

---

## Exercícios de Consolidação

Estes exercícios distinguem-se dos exercícios de cada secção por serem **integradores**: nenhum se resolve com o conteúdo de uma única secção. Reproduzem a forma como os problemas aparecem na vida real, que é toda misturada.

Sugere-se realizá-los pela ordem apresentada, porque a dificuldade é crescente.

### Exercício 1 — O percurso completo 

**Ponto de partida:** escolha uma aplicação rica real que use com frequência — um serviço público *online*, uma plataforma interna da sua organização, uma aplicação de gestão.

**Tarefa:** execute uma tarefa completa e realista (por exemplo: autenticar-se, submeter um pedido, verificar o estado) **sem usar o rato**, e registe num documento:

1. Todos os pontos em que perdeu a noção de onde estava
2. Todas as mudanças de conteúdo que aconteceram sem qualquer sinal percetível
3. Todos os controlos que não conseguiu alcançar ou ativar
4. O que aconteceu ao carregar em `Alt+Seta esquerda` (retroceder) a meio da tarefa
5. O que aconteceu ao recarregar a página a meio da tarefa

**Entrega:** uma lista de problemas, cada um classificado por secção do módulo (arquitetura, estrutura, foco, notificação).

**O que este exercício treina:** a capacidade de olhar para um sintoma («perdi-me») e identificar a causa técnica correta. É a competência mais transferível de todo o módulo.

### Exercício 2 — Da causa ao critério

**Ponto de partida:** a lista de problemas produzida no Exercício 1.

**Tarefa:** para cada problema encontrado, preencha uma linha desta tabela:

| Problema observado | Quem é afetado e como | Critério WCAG em causa | Nível | É obrigação legal em Portugal? |
|---|---|---|---|---|

Use a secção «Critérios de Sucesso WCAG Relacionados», mais abaixo, como referência.

**O que este exercício treina:** traduzir observação em linguagem normativa. É esta tradução que permite defender uma correção perante quem decide orçamentos e prioridades — e que distingue «acho que isto está mal» de «isto falha o critério 4.1.3, que é obrigatório».

### Exercício 3 — A vista que nunca chegou

**Ponto de partida:** um pequeno excerto de código de uma aplicação de página única em que a mudança de vista é feita substituindo o conteúdo de um contentor, sem mais nada.

**Tarefa:** em pares, transformem essa mudança de vista numa mudança de vista acessível. Devem decidir e justificar:

- O que acontece ao título do documento
- O que acontece ao endereço e ao histórico
- Para onde vai o foco, e porquê esse destino e não outro
- Se há ou não anúncio adicional, e com que urgência
- O que acontece se a nova vista demorar dois segundos a carregar
- O que acontece se a nova vista falhar a carregar

**Entrega:** o código corrigido e um parágrafo curto por cada decisão.

**O que este exercício treina:** a articulação entre as quatro secções num único ponto do código. Repare que a mesma linha de código toca em arquitetura, foco e notificação ao mesmo tempo — e que a decisão sobre o caso de erro é tão importante como a decisão sobre o caso feliz.

### Exercício 4 — Auditoria cruzada

**Ponto de partida:** escolha uma vista de uma aplicação (pode ser um painel com filtros e resultados, um assistente por passos, ou uma área de gestão com tabela editável).

**Tarefa:** faça passagens diferente sobre a mesma vista:

- **Passagem A** — apenas teclado, sem leitor de ecrã, a registar percurso e visibilidade do foco
- **Passagem B** — leitor de ecrã, a registar o que é anunciado e o que fica em silêncio
- **Passagem C** — ampliação a 400% e largura de 320 pixéis CSS, a registar o que desaparece, o que exige deslocamento nos dois eixos e o que fica tapado por barras fixas

No fim, compare os três registos.

**O que este exercício treina:** a perceção de que estas três passagens encontram problemas **diferentes**, com pouca sobreposição. Uma equipa que só testa com leitor de ecrã não encontra os problemas da pessoa C. Uma equipa que só testa com teclado não encontra os da pessoa B. É por isto que uma única forma de teste nunca chega.

### Exercício 5 — Escrever para quem não vê o ecrã

**Ponto de partida:** recolha seis mensagens reais de uma aplicação que conheça — mensagens de carregamento, de sucesso, de erro, de estado vazio, de progresso, de confirmação.

**Tarefa:** reescreva cada uma de modo a que:

- Faça sentido isolada, sem se ver o ecrã e sem contexto visual
- Diga o que aconteceu **e** o que fazer a seguir, quando aplicável
- Comece pela informação mais importante
- Não dependa de cor, de ícone, de posição ou de proximidade visual para ser compreendida

Para cada uma, indique também: deve ser anunciada com urgência, com delicadeza, ou não deve ser anunciada de todo?

**O que este exercício treina:** a parte do trabalho que não é código. Grande parte da inacessibilidade de aplicações ricas está em texto escrito por pessoas que assumiam, sem darem por isso, que o ecrã estaria a ser visto.

### Exercício 6 — O argumento

**Ponto de partida:** uma equipa de desenvolvimento diz: *«Isto é uma aplicação interna, usada por vinte pessoas, e sabemos que nenhuma delas tem deficiência. Não vale o esforço.»*

**Tarefa:** prepare uma resposta de três minutos, com pelo menos um argumento de cada tipo:

- **Legal** — o que diz o Decreto-Lei n.º 83/2018 e a quem se aplica
- **Factual** — porque é que a premissa «nenhuma delas tem deficiência» é frágil (deficiências adquiridas, limitações temporárias, situações contextuais, envelhecimento, pessoas que ainda não entraram na equipa)
- **Económico** — o custo comparado de corrigir na arquitetura *versus* corrigir depois de a aplicação estar em produção
- **De qualidade** — o que é que estas correções melhoram para toda a gente, independentemente de deficiência

**O que este exercício treina:** a competência que decide se todo o resto será alguma vez aplicado. Saber implementar não chega se não se conseguir explicar porquê a quem aprova o trabalho.

---

## Lista de Verificação Final

Esta lista serve para revisão de uma aplicação rica antes de entrar em produção, ou como guião de uma revisão por pares. Está organizada pelas quatro secções do módulo.

**Não substitui uma avaliação de conformidade completa.** É um filtro de qualidade centrado nos pontos onde as aplicações ricas falham com mais frequência e com maior gravidade.

### Arquitetura da aplicação

- [ ] Cada vista significativa tem um endereço próprio que pode ser partilhado, guardado nos favoritos e recarregado
- [ ] O botão de retroceder do navegador faz o que a pessoa espera, e não sai da aplicação
- [ ] O título do documento muda a cada mudança de vista e identifica a vista atual
- [ ] Recarregar a página não faz perder o trabalho em curso, ou avisa antes de o fazer
- [ ] Os elementos que levam a algum lado são ligações reais com `href`; os que executam ações são botões reais
- [ ] As combinações de teclas do navegador e das tecnologias de apoio continuam a funcionar
- [ ] A aplicação funciona com ampliação até 200% sem perda de conteúdo ou funcionalidade
- [ ] A aplicação funciona a 320 pixéis CSS de largura sem exigir deslocamento nos dois eixos
- [ ] Alterações de espaçamento de texto não partem a disposição nem cortam conteúdo
- [ ] As preferências do sistema quanto a movimento reduzido são respeitadas

### Estrutura e relações

- [ ] Existe uma hierarquia de títulos coerente e sem saltos de nível dentro de cada vista
- [ ] As grandes áreas da interface estão identificadas como regiões, com nomes distintos quando há mais do que uma do mesmo tipo
- [ ] Os agrupamentos que se veem no ecrã existem também no código, e não apenas como caixas desenhadas com CSS
- [ ] O que é uma lista está marcado como lista; o que é uma tabela de dados está marcado como tabela de dados
- [ ] Todas as relações entre elementos que se explicam mutuamente estão declaradas explicitamente
- [ ] Nenhuma informação depende exclusivamente de cor, forma, tamanho ou posição para ser compreendida
- [ ] Não há texto significativo gerado por CSS
- [ ] Os nomes acessíveis dos controlos incluem o texto visível desses controlos
- [ ] Os elementos escondidos visualmente estão também escondidos das tecnologias de apoio — e vice-versa

### Ordem de leitura e foco

- [ ] A ordem do código corresponde à ordem visual em todas as larguras de ecrã testadas
- [ ] Toda a funcionalidade é alcançável e operável apenas com teclado
- [ ] Não existe nenhum ponto onde o foco fique preso sem forma de sair pelo teclado
- [ ] O indicador de foco é sempre visível e nunca fica tapado por cabeçalhos fixos, rodapés fixos ou elementos flutuantes
- [ ] Quando muda a vista, o foco vai para um destino definido e previsível
- [ ] Quando abre um diálogo, o foco entra; quando fecha, regressa ao ponto de origem
- [ ] Quando se apaga um item, o foco vai para um destino sensato e nunca desaparece
- [ ] O foco nunca é movido sem que a pessoa tenha feito alguma coisa que o justifique
- [ ] Existe forma de saltar blocos repetidos de conteúdo

### Notificações e atualizações de conteúdo

- [ ] Todas as mudanças de estado importantes — a carregar, guardado, falhou, sem resultados — são percetíveis sem se ver o ecrã
- [ ] As mensagens urgentes interrompem; as não urgentes esperam
- [ ] Não existem regiões a anunciar constantemente durante a escrita ou a navegação
- [ ] Nenhuma mensagem importante desaparece antes de poder ser lida, nem fica inacessível depois de desaparecer
- [ ] Conteúdo que se atualiza ou move automaticamente pode ser pausado, parado ou ocultado
- [ ] Limites de tempo podem ser desligados, ajustados ou prolongados
- [ ] Nada se move nem pisca de forma suscetível de provocar crises
- [ ] Os erros são identificados em texto, descritos com clareza e acompanhados de indicação sobre como os corrigir

### Verificação

- [ ] A aplicação foi percorrida de ponta a ponta apenas com teclado
- [ ] A aplicação foi testada com, pelo menos, um leitor de ecrã, numa tarefa completa e não apenas em ecrãs isolados
- [ ] A aplicação foi testada com ampliação elevada e em largura reduzida
- [ ] A árvore de acessibilidade foi inspecionada nas vistas mais complexas
- [ ] A avaliação automática foi executada, e os seus resultados foram tratados como ponto de partida e não como conclusão
- [ ] Existe declaração de acessibilidade publicada e atualizada, com mecanismo de contacto funcional

---

## Critérios de Sucesso WCAG Relacionados

### Como ler esta secção

Ao longo do módulo, os critérios foram sendo referidos onde faziam sentido. Aqui estão reunidos e organizados, com uma distinção que é essencial para trabalhar em Portugal:

> **O Decreto-Lei n.º 83/2018** obriga os sítios Web e as aplicações móveis do setor público a cumprir a norma europeia **EN 301 549**. A versão dessa norma atualmente em vigor (v3.2.1) incorpora as **WCAG 2.1, níveis A e AA**.
>
> Ou seja: **os critérios de nível A e AA das WCAG 2.1 são obrigação legal. Os critérios de nível AAA não são.**

As tabelas seguintes indicam, para cada critério, o que ele exige e como se aplica concretamente ao que foi tratado neste módulo.

---

### Nível A — obrigação legal (WCAG 2.1)

| Critério | O que exige | Aplicação em aplicações ricas |
|---|---|---|
| **1.3.1 Informação e Relações** | A estrutura e as relações comunicadas visualmente têm de existir também no código | O critério central da secção «Estruturas e Relações». Cobre títulos, regiões, listas, agrupamentos, e relações entre elementos que se explicam mutuamente |
| **1.3.2 Sequência com Significado** | Quando a sequência afeta o significado, a sequência correta tem de ser determinável programaticamente | A ordem do código tem de corresponder à ordem visual. É o critério em causa quando se reordena visualmente com CSS |
| **1.3.3 Características Sensoriais** | As instruções não podem depender apenas de forma, tamanho, localização ou som | Nada de «o painel à direita» ou «o botão redondo» como única identificação |
| **1.4.1 Utilização da Cor** | A cor não pode ser o único meio de transmitir informação | Estados de itens, linhas com erro, elementos selecionados e indicadores de progresso não podem distinguir-se apenas pela cor |
| **2.1.1 Teclado** | Toda a funcionalidade tem de ser operável por teclado | Componentes construídos de raiz, painéis arrastáveis, menus e áreas interativas |
| **2.1.2 Sem Bloqueio do Teclado** | O foco tem de poder sair de qualquer componente usando só o teclado | Diálogos, sobreposições e painéis que retêm o foco indevidamente |
| **2.1.4 Teclas de Atalho de Caracteres** | Atalhos de tecla única têm de poder ser desligados, remapeados ou limitados ao foco | Aplicações ricas usam frequentemente atalhos como `n` ou `/`, que colidem com comandos dos leitores de ecrã e do software de reconhecimento de voz |
| **2.2.1 Ajuste do Tempo** | Limites de tempo têm de poder ser desligados, ajustados ou prolongados | Sessões que expiram, formulários com contagem decrescente, ecrãs que avançam sozinhos |
| **2.2.2 Colocar em Pausa, Parar, Ocultar** | Conteúdo em movimento, intermitente ou que se atualiza automaticamente tem de poder ser controlado | Painéis que se atualizam sozinhos, carrosséis, listas em atualização contínua |
| **2.3.1 Três Flashes ou Abaixo do Limiar** | Nada pode piscar mais de três vezes por segundo acima do limiar | Transições, animações de carregamento e efeitos visuais de notificação |
| **2.4.1 Ignorar Blocos** | Tem de haver forma de saltar blocos de conteúdo repetidos | Barras laterais e cabeçalhos de aplicação que se repetem em todas as vistas |
| **2.4.2 Página com Título** | Cada página tem de ter um título que descreve o seu tópico ou finalidade | Numa aplicação de página única, o título tem de ser **atualizado a cada mudança de vista** — é uma das cinco coisas que o navegador deixou de fazer |
| **2.4.3 Ordem de Foco** | A ordem de foco tem de preservar significado e operabilidade | O critério central da secção «Ordem de Leitura e Foco» |
| **2.5.1 Gestos com Ponteiro** | Funcionalidade que usa gestos complexos tem de ter alternativa com um único ponteiro | Arrastar para reordenar, deslizar para apagar, gestos com vários dedos |
| **2.5.2 Cancelamento do Ponteiro** | Ações não devem executar-se no início do toque, e têm de poder ser canceladas | Controlos que disparam ao premir em vez de ao largar |
| **2.5.3 Rótulo no Nome Acessível** | O nome acessível tem de conter o texto visível do controlo | Determina se o controlo pode ser ativado por comando de voz. Botões só com ícone e rótulos ARIA que contradizem o texto visível falham aqui |
| **2.5.4 Ativação por Movimento** | Funcionalidade acionada por movimento do dispositivo tem de ter alternativa e poder ser desativada | Agitar para desfazer, inclinar para navegar |
| **3.2.1 Em Foco** | Receber foco não pode desencadear mudança de contexto | Painéis que abrem só porque o foco lá passou |
| **3.2.2 Em Entrada de Dados** | Alterar um valor não pode desencadear mudança de contexto sem aviso | Selecionar uma opção e ser levado imediatamente para outra vista |
| **3.3.1 Identificação de Erros** | Erros detetados automaticamente têm de ser identificados e descritos em texto | Validação em tempo real e erros devolvidos pelo servidor |
| **3.3.2 Rótulos ou Instruções** | Tem de haver rótulos ou instruções quando se pede entrada de dados | Aplica-se também a controlos criados dinamicamente e a filtros gerados por código |
| **4.1.2 Nome, Função, Valor** | Todo o componente de interface tem de ter nome, função e estado determináveis programaticamente | O critério de base de qualquer componente construído de raiz |

> **Nota sobre o critério 4.1.1 (Análise).** Este critério existia nas WCAG 2.0 e 2.1, mas foi considerado obsoleto e **removido nas WCAG 2.2**. Não deve continuar a ser usado como fundamento de não conformidade. Os problemas reais que pretendia cobrir são hoje tratados pelo critério 4.1.2.

---

### Nível AA — obrigação legal (WCAG 2.1)

| Critério | O que exige | Aplicação em aplicações ricas |
|---|---|---|
| **1.3.4 Orientação** | O conteúdo não pode restringir-se a uma única orientação do ecrã | Aplicações que só funcionam na horizontal excluem quem tem o dispositivo fixo a uma cadeira de rodas |
| **1.3.5 Identificar a Finalidade da Entrada** | A finalidade de campos sobre a própria pessoa tem de ser determinável programaticamente | Permite preenchimento automático e apresentação personalizada. Frequentemente perdido em campos construídos de raiz |
| **1.4.3 Contraste (Mínimo)** | Contraste mínimo de 4,5:1 para texto normal e 3:1 para texto grande | Aplica-se também a texto sobre painéis sobrepostos, estados desativados com significado e texto sobre fundos dinâmicos |
| **1.4.4 Redimensionar Texto** | O texto tem de poder ser ampliado até 200% sem perda de conteúdo ou funcionalidade | Disposições de aplicação com alturas fixas cortam conteúdo com facilidade |
| **1.4.10 Refluxo** | O conteúdo tem de funcionar a 320 pixéis CSS de largura sem deslocamento nos dois eixos | Painéis lado a lado, tabelas largas e barras laterais fixas são os pontos habituais de falha |
| **1.4.11 Contraste de Conteúdo Não Textual** | Contraste mínimo de 3:1 para componentes de interface e elementos gráficos necessários à compreensão | Limites de campos, indicadores de foco, ícones que transmitem estado, elementos de gráficos |
| **1.4.12 Espaçamento do Texto** | O conteúdo tem de suportar alterações de espaçamento sem perda de conteúdo ou funcionalidade | Rótulos e mensagens em caixas de altura fixa |
| **1.4.13 Conteúdo em Foco ou Passagem do Rato** | Conteúdo que aparece ao focar ou ao passar o rato tem de poder ser dispensado, alcançado e permanecer visível | Dicas, menus suspensos e pré-visualizações que aparecem ao passar o rato |
| **2.4.5 Várias Formas** | Tem de haver mais do que uma forma de localizar uma página | Pesquisa dentro da aplicação, navegação estruturada, mapa da aplicação |
| **2.4.6 Cabeçalhos e Etiquetas** | Cabeçalhos e etiquetas têm de descrever o tópico ou a finalidade | Vários painéis com o cabeçalho «Detalhes» não cumprem este critério |
| **2.4.7 Foco Visível** | Tem de existir indicador de foco visível | Falha frequentemente por remoção deliberada do contorno predefinido em folhas de estilo globais |
| **3.2.3 Navegação Consistente** | Mecanismos de navegação repetidos têm de manter ordem relativa consistente | Barras laterais que se reorganizam entre vistas |
| **3.2.4 Identificação Consistente** | Componentes com a mesma função têm de ser identificados de forma consistente | «Guardar», «Gravar» e «Confirmar» a designar a mesma ação em vistas diferentes |
| **3.3.3 Sugestão em Caso de Erro** | Quando o erro é detetável e a sugestão é conhecida, tem de ser apresentada | Não basta dizer que está errado: é preciso dizer como corrigir |
| **3.3.4 Prevenção de Erros** | Em contextos jurídicos, financeiros ou de dados, as submissões têm de ser reversíveis, verificadas ou confirmadas | Aplicações de serviços públicos caem quase sempre neste âmbito |
| **4.1.3 Mensagens de Estado** | Mensagens de estado têm de ser comunicáveis às tecnologias de apoio sem receberem foco | O critério central da secção «Notificações e Atualizações de Conteúdo» |

---

### Critérios acrescentados pelas WCAG 2.2 — ainda não exigíveis, fortemente recomendados

Estes critérios **não fazem parte da base legal atual em Portugal**, porque a versão em vigor da EN 301 549 ainda incorpora as WCAG 2.1. Espera-se que passem a ser exigíveis com a publicação da versão v4.1.1 da norma.

São aqui destacados por uma razão prática: **quase todos foram escritos a pensar exatamente em aplicações ricas**.

| Critério | Nível | O que exige | Aplicação em aplicações ricas |
|---|---|---|---|
| **2.4.11 Foco Não Obscurecido (Mínimo)** | AA | O elemento com foco não pode ficar completamente tapado por conteúdo criado pela própria aplicação | Barras fixas superiores e inferiores, painéis de aceitação de dados e janelas de conversa que tapam o elemento focado durante a tabulação |
| **2.5.7 Movimentos de Arrastamento** | AA | Funcionalidade que exige arrastar tem de ter alternativa que não exija arrastar | Reordenar listas, mover cartões entre colunas, redimensionar painéis |
| **2.5.8 Tamanho do Alvo (Mínimo)** | AA | Alvos de ponteiro têm de ter pelo menos 24 por 24 pixéis CSS, com exceções | Barras de ferramentas densas, ícones de ação em linhas de tabela |
| **3.2.6 Ajuda Consistente** | A | Mecanismos de ajuda repetidos têm de aparecer na mesma ordem relativa | Contacto de apoio e ajuda contextual apresentados em sítios diferentes conforme a vista |
| **3.3.7 Entrada Redundante** | A | Informação já introduzida não deve ter de ser reintroduzida no mesmo processo | Assistentes por passos que voltam a pedir os mesmos dados |
| **3.3.8 Autenticação Acessível (Mínimo)** | AA | A autenticação não pode exigir testes cognitivos sem alternativa | Códigos que exigem transcrição manual, autenticação que bloqueia a colagem de texto |

> **Recomendação prática:** numa aplicação que esteja a ser desenhada agora, adotar estes seis critérios custa muito pouco. Adaptá-los a uma aplicação já em produção, depois de a norma mudar, custa consideravelmente mais. É uma das decisões com melhor relação entre esforço e benefício que uma equipa pode tomar hoje.

---

### Nível AAA — acima do mínimo legal, boa prática

Os critérios de nível AAA **não são exigidos** pelo Decreto-Lei n.º 83/2018 nem pela EN 301 549. As próprias WCAG desaconselham exigir conformidade AAA para a totalidade de um sítio, porque nem todos os critérios são aplicáveis a todo o tipo de conteúdo.

Ainda assim, vários deles resolvem problemas que aparecem com muita frequência em aplicações ricas e que afetam pessoas reais todos os dias. Devem ser encarados como **objetivos de qualidade**, adotados criteriosamente onde acrescentam valor.

| Critério | O que exige | Porque interessa em aplicações ricas |
|---|---|---|
| **1.3.6 Identificar a Finalidade** | A finalidade de componentes, ícones e regiões tem de ser determinável programaticamente | Permite a interfaces personalizadas substituir ícones por símbolos familiares a cada pessoa. Beneficia sobretudo pessoas com deficiência cognitiva |
| **1.4.6 Contraste (Melhorado)** | Contraste de 7:1 para texto normal e 4,5:1 para texto grande | Aplicações de uso profissional prolongado beneficiam muito de contraste acima do mínimo |
| **2.1.3 Teclado (Sem Exceção)** | Toda a funcionalidade operável por teclado, sem quaisquer exceções | Elimina as exceções de traçado livre e temporização que o critério 2.1.1 permite |
| **2.2.3 Sem Restrição Temporal** | Nenhum limite de tempo essencial ao funcionamento | Aplicável a assistentes longos e a processos de submissão complexos |
| **2.2.4 Interrupções** | As interrupções podem ser adiadas ou suprimidas, exceto em emergência | Notificações de sistema que aparecem no meio de uma tarefa. Extremamente relevante para pessoas com défice de atenção |
| **2.2.5 Nova Autenticação** | Após expirar a sessão, os dados podem ser recuperados ao voltar a autenticar | Evita perder um formulário longo por causa de uma pausa |
| **2.2.6 Tempos Limite** | A pessoa é avisada da duração de inatividade que provoca perda de dados | Diretamente ligado ao anterior |
| **2.3.3 Animação a partir de Interações** | As animações desencadeadas por interação podem ser desativadas | Transições entre vistas provocam náuseas e desorientação em pessoas com perturbações vestibulares |
| **2.4.8 Localização** | Há informação sobre a localização da pessoa dentro de um conjunto de páginas | Numa aplicação com muitos níveis, saber onde se está é frequentemente o problema mais difícil |
| **2.4.12 Foco Não Obscurecido (Melhorado)** | O elemento com foco não pode ficar **sequer parcialmente** tapado | Versão exigente do critério 2.4.11 |
| **2.4.13 Aparência do Foco** | O indicador de foco tem de cumprir requisitos mínimos de área e de contraste | Torna verificável o que o critério 2.4.7 deixa em aberto. Muito recomendável adotar como norma interna de desenho |
| **3.2.5 Alteração a Pedido** | As mudanças de contexto só acontecem por iniciativa da pessoa | O oposto exato das aplicações que reorganizam o ecrã sozinhas |
| **3.3.5 Ajuda** | Há ajuda contextual disponível | Aplicações de serviços públicos com formulários complexos |
| **3.3.6 Prevenção de Erros (Todos)** | Todas as submissões são reversíveis, verificadas ou confirmadas | Alarga a todas as ações o que o critério 3.3.4 exige apenas em contextos sensíveis |
| **3.3.9 Autenticação Acessível (Melhorada)** | Nenhum teste cognitivo na autenticação, incluindo reconhecimento de objetos | Versão exigente do critério 3.3.8 |
