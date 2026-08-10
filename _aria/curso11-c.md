---
title: Ordem de Leitura e Foco
layout: default
nav_order: 3
---
# Ordem de Leitura e Foco

## Introdução

Na secção «Aplicações Ricas» vimos a aplicação como um **edifício**: um espaço que muda de forma enquanto lá estamos dentro. Na secção «Estruturas e Relações» tratámos da **planta** desse edifício — que zonas existem, como se chamam, o que está dentro de quê.

Esta secção trata de duas coisas diferentes que costumam ser confundidas:

- a **ordem de leitura** — o percurso pelo qual o conteúdo é apresentado a quem não o vê todo de uma vez;
- o **foco** — o sítio exato onde a pessoa está neste momento e para onde as teclas que ela premir vão ser entregues.

> **Analogia central: o percurso pintado no chão**
>
> Imagine um edifício público com um percurso pintado no chão, daqueles que se seguem sem ter de perguntar nada a ninguém. O percurso leva-o da entrada ao atendimento, do atendimento à sala de espera, da sala de espera ao balcão.
>
> A **ordem de leitura** é essa linha pintada no chão: a sequência por que as coisas aparecem.
>
> O **foco** é o sítio onde os seus pés estão neste preciso momento.
>
> Num edifício bem sinalizado acontecem quatro coisas: a linha pintada corresponde às portas que existem mesmo; quando abre uma porta, os seus pés passam para a divisão seguinte; quando sai de uma sala, volta ao corredor onde estava e não à rua; e há sempre luz suficiente para ver onde está.
>
> Numa aplicação mal construída, a linha pintada leva a uma parede, a porta abre-se mas os pés ficam onde estavam, sair de uma sala atira-o para a entrada do edifício, e às vezes a luz apaga-se sem aviso.

Estes quatro comportamentos são exatamente os quatro princípios que organizam esta secção. Chamemos-lhes os **quatro C**:

| Princípio | Pergunta a que responde |
|---|---|
| **Coerência** | A ordem por que o conteúdo é lido e tabulado corresponde ao que se vê? |
| **Continuidade** | Quando o conteúdo muda, o foco vai para o sítio certo — em vez de se perder? |
| **Contenção** | O foco fica dentro dos limites certos, sem entrar onde não deve nem ficar preso? |
| **Consciência** | É possível saber, a cada momento, onde se está? |

### Onde acaba esta secção e começam as outras

Para não repetir conteúdo, convém marcar as fronteiras logo no início.

O módulo sobre **Widgets** já tratou da mecânica do foco ao nível do componente: o que é o `tabindex` e para que servem os valores `0` e `-1`, como se desenha um indicador de foco visível com `:focus-visible`, como funciona o `tabindex` móvel dentro de um componente composto, e como se prende e liberta o foco dentro de uma janela modal. **Nada disso se repete aqui.** Quando for necessário, remete-se para lá.

O que esta secção acrescenta é a **escala da aplicação**: não o foco dentro de um botão ou de um menu, mas o percurso ao longo de uma interface inteira que se reorganiza, carrega ecrãs novos sem recarregar a página, insere painéis, apaga linhas e mantém barras fixas por cima de tudo.

E há uma fronteira ainda mais importante, com a secção seguinte:

> **Regra prática:** quando alguma coisa muda no ecrã, há duas formas de a pessoa ficar a saber — **levar lá o foco** ou **anunciar sem mexer no foco**. Esta secção trata da primeira. A secção «Notificações e Atualizações de Conteúdo» trata da segunda.

| Situação | O foco deve mover-se? | Onde se trata |
|---|---|---|
| A pessoa navegou para outra vista | Sim | Esta secção |
| Abriu-se um painel ou diálogo que exige atenção | Sim | Esta secção |
| A pessoa apagou um item de uma lista | Sim (para o item seguinte) | Esta secção |
| Um resultado de pesquisa foi atualizado enquanto se escreve | Não | «Notificações e Atualizações de Conteúdo» |
| Um ficheiro acabou de ser guardado automaticamente | Não | «Notificações e Atualizações de Conteúdo» |
| Um erro de validação apareceu no fim do formulário | Depende da gravidade | Ambas — ver as duas secções |

---

### Como as Pessoas com Deficiência acedem à Ordem de Leitura e Foco

O ponto mais difícil de transmitir em formação é este: **a ordem que a maioria das pessoas vê não é a ordem que existe.** O que se vê é o resultado de folhas de estilo aplicadas a um documento; o que as tecnologias de apoio percorrem é o documento. Quando os dois divergem, quem vê não repara e quem não vê tropeça.

Vejamos como isto se manifesta em cada situação.

#### Pessoas cegas que usam leitor de ecrã

Um leitor de ecrã percorre o conteúdo por uma ordem: a **ordem do código-fonte** tal como o navegador a expõe na árvore de acessibilidade. Não percorre por proximidade visual. Duas caixas lado a lado no ecrã podem estar a centenas de linhas de distância uma da outra no documento, e serão lidas como se nada tivessem a ver uma com a outra.

Além disso, como vimos na primeira secção deste módulo, o leitor de ecrã mantém uma cópia navegável do conteúdo. Essa cópia tem um **cursor de leitura**, a posição de onde a próxima seta para baixo continua a ler. Quando o conteúdo da página muda, esse cursor pode ficar num sítio que já não existe, ou ser reposicionado no início. Mover o foco é a forma mais fiável de reposicionar também esse cursor de leitura.

> Uma consequência que apanha muita gente de surpresa: **quando o foco se move por código, o leitor de ecrã lê o que está no destino.** Isso é uma ferramenta poderosíssima. E uma arma apontada aos pés de quem a usa sem cuidado, porque mover o foco para o sítio errado interrompe a leitura e deixa a pessoa perdida.

#### Pessoas com baixa visão que usam ampliação

Quem usa ampliação a 400% vê, de cada vez, uma área equivalente a um cartão de visita. A ligação entre o que está a ver e o resto da interface é feita de memória e de deslocação.

Para estas pessoas, o foco é o que **puxa o ecrã**: a ampliação segue o foco. Se o foco saltar para um elemento que está a 3000 píxeis de distância, o ecrã salta com ele e a pessoa perde a referência. Se, pelo contrário, o foco não se mover quando um painel se abre noutro canto do ecrã, a pessoa simplesmente **não vê que aconteceu alguma coisa**: o painel está fora do seu campo de visão ampliado.

#### Pessoas com limitações motoras que usam teclado ou varrimento

Quem navega com `Tab` paga cada passo. Uma ordem de foco que vai e volta pela página — coluna da direita, depois a esquerda, depois outra vez a direita — não é apenas confusa: é cansativa e, para quem usa varrimento por manípulo, pode significar dezenas de segundos por cada elemento saltado.

Para estas pessoas, um foco que se perde é particularmente caro. Quando o foco «cai» para o `<body>`, premir `Tab` recomeça no princípio da aplicação. Se estavam no passo 4 de um formulário longo, voltam ao topo.

#### Pessoas com deficiência cognitiva ou de atenção

Uma ordem previsível reduz a carga mental. Quando os passos aparecem sempre pela mesma ordem e o foco vai sempre para onde é razoável esperar, a pessoa não tem de reconstruir o modelo da interface a cada interação.

O contrário — o foco a saltar sozinho, o conteúdo a reorganizar-se, o ecrã a deslocar-se sem intervenção da pessoa — pode ser suficiente para tornar a tarefa impossível, mesmo que tecnicamente tudo esteja «acessível».

#### Pessoas que usam comando por voz

Quem usa comando por voz diz «clicar em Guardar». Se existirem três «Guardar» na página, o software numera-os. Esta forma de trabalhar depende de o comando estar **visível e alcançável**: um botão escondido debaixo de uma barra fixa, ou um painel que ficou aberto atrás de outro, não pode ser referido.

#### Pessoas surdocegas com linha braille

A linha braille mostra uma janela de 40 células — cerca de meia linha de texto. Toda a experiência é sequencial e local. Uma ordem de leitura ilógica é, aqui, o equivalente a ler um livro com as páginas trocadas.

---

### Requisitos de Acessibilidade para Ordem de Leitura e Foco

Os requisitos que se seguem estão agrupados pelos quatro C. Cada um indica, entre parêntesis, o critério WCAG que lhe está mais próximo; a lista completa e organizada por níveis aparece na secção «Conclusão e Boas Práticas» deste módulo.

#### Coerência

**R1 — A ordem do código corresponde à ordem que se vê.**
Se a sequência tem significado — passos, prioridades, relação entre um rótulo e o que ele descreve —, essa sequência tem de estar no documento e não apenas no arranjo visual (WCAG 1.3.2 *Sequência com Significado*).

**R2 — A ordem de foco preserva o significado e a operabilidade.**
Percorrer a aplicação com `Tab` deve produzir um percurso que se compreende e que não obriga a saltos para trás e para a frente (WCAG 2.4.3 *Ordem de Focagem*).

**R3 — A ordem mantém-se coerente em todas as larguras de ecrã e níveis de ampliação.**
Uma interface que a 100% se lê por uma ordem e a 400% por outra obriga a pessoa a aprender duas aplicações (relacionado com WCAG 1.4.10 *Reflow*).

**R4 — Conteúdo novo aparece junto daquilo que o originou.**
Sugestões de pesquisa, painéis expandidos, mensagens associadas a um campo: no documento, devem estar tão perto quanto possível do controlo que os produziu.

#### Continuidade

**R5 — Cada vista tem um ponto de entrada definido.**
Quando a aplicação muda de vista sem recarregar a página, o foco tem de ir deliberadamente para um sítio que dê contexto — tipicamente o cabeçalho principal da vista nova.

**R6 — O foco nunca se perde.**
Se o elemento que tem o foco é removido ou escondido, alguém tem de decidir, antes de o destruir, quem herda o foco. O valor por omissão — o foco cair para o `<body>` — é sempre a pior opção.

**R7 — O foco regressa à origem.**
Quando uma camada temporária fecha (painel, diálogo, menu, editor em linha), o foco volta ao controlo que a abriu. Se esse controlo já não existir, volta a um ponto estável e próximo.

**R8 — O foco não muda sozinho sem motivo.**
Mover o foco é uma interrupção. Só se justifica quando a pessoa fez alguma coisa que a espera ou quando existe uma situação suficientemente grave para o exigir.

#### Contenção

**R9 — O que está visualmente inativo está tecnicamente inativo.**
Se um painel modal cobre a aplicação, o resto da aplicação não pode continuar a receber `Tab` nem a ser lido pelo leitor de ecrã.

**R10 — Não existem armadilhas.**
De qualquer ponto da aplicação é possível sair usando apenas o teclado, sem recorrer ao rato e sem recarregar a página (WCAG 2.1.2 *Sem Armadilhas de Teclado*).

**R11 — Receber foco não desencadeia mudanças de contexto.**
Chegar a um elemento não pode, por si só, submeter um formulário, mudar de página, abrir uma janela ou reorganizar o ecrã (WCAG 3.2.1 *Em Foco*).

#### Consciência

**R12 — O elemento com foco está visível e não obscurecido.**
Não basta o indicador de foco existir: ele tem de não ficar debaixo de uma barra fixa, de um banner de cookies ou de um widget de conversação (WCAG 2.4.7 *Foco Visível*; WCAG 2.4.11 *Foco Não Obscurecido (Mínimo)*).

**R13 — Existem formas de saltar percursos repetidos.**
Numa aplicação com barras laterais e cabeçalhos persistentes, tem de haver forma de os ultrapassar sem os percorrer (WCAG 2.4.1 *Ignorar Blocos*).

**R14 — Voltar atrás devolve a pessoa ao sítio onde estava.**
Depois de abrir um detalhe e regressar à lista, a posição de leitura e o foco devem ser restaurados, e não repostos no topo.

---

## Técnicas de Codificação

As técnicas seguem a mesma arrumação: primeiro a ordem (Coerência), depois o movimento do foco (Continuidade), depois os limites (Contenção) e por fim a perceção (Consciência).

---

### Coerência: pôr a ordem no sítio certo

#### T1 — A ordem do documento é a única ordem verdadeira

O CSS moderno permite reorganizar visualmente o conteúdo com uma facilidade perigosa: `order` em Flexbox, `grid-area` e `grid-auto-flow: dense` em Grid, `flex-direction: row-reverse`, `position: absolute`, `float`. Nenhuma destas propriedades muda a ordem do documento — e, portanto, nenhuma delas muda a ordem de leitura ou de tabulação.

**Exemplo problemático:**

```html
<div class="acoes">
  <button type="button" class="secundario">Cancelar</button>
  <button type="submit" class="primario">Guardar alterações</button>
</div>
```

```css
.acoes {
  display: flex;
  flex-direction: row-reverse;
  gap: 1rem;
}
```

**O que corre mal aqui:** visualmente, «Guardar alterações» aparece à direita e «Cancelar» à esquerda — o arranjo que a equipa de design queria. Mas o `row-reverse` só inverteu o desenho. Quem usa `Tab` chega primeiro a «Cancelar» (que está à direita) e depois a «Guardar» (que está à esquerda). O foco anda **da direita para a esquerda**, ao contrário de tudo o resto na aplicação. Quem usa ampliação vê o indicador de foco saltar para trás e não percebe porquê. É uma falha direta do critério 2.4.3.

**Versão corrigida:**

```html
<div class="acoes">
  <button type="submit" class="primario">Guardar alterações</button>
  <button type="button" class="secundario">Cancelar</button>
</div>
```

```css
.acoes {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  gap: 1rem;
}

/* Se o desenho exigir «Cancelar» à esquerda de «Guardar»,
   inverte-se a ordem no HTML, não no CSS. */
```

**Porque funciona:** o botão principal está primeiro no documento e primeiro na ordem de foco. O alinhamento à direita é obtido com `justify-content`, que posiciona sem reordenar. Regra a fixar: **use CSS para posicionar, nunca para reordenar.**

**Teste rápido:** desative o CSS da página (nas ferramentas do navegador ou com uma extensão). Se o conteúdo, em texto puro, continuar a fazer sentido de cima para baixo, a ordem de leitura está correta. Se aparecerem os rodapés a meio e os menus no fim, há trabalho a fazer.

---

#### T2 — Conteúdo novo nasce junto do que o originou

Muitas bibliotecas de componentes inserem elementos flutuantes — sugestões, painéis, dicas, calendários — no fim do `<body>`, e depois posicionam-nos por cima do controlo com CSS. Visualmente ficam colados ao campo. No documento ficam a uma distância enorme.

**Exemplo problemático:**

```html
<main>
  <label for="pesquisa">Pesquisar processos</label>
  <input id="pesquisa" type="search" autocomplete="off">
  <!-- ... 400 linhas de aplicação ... -->
</main>
<footer> ... </footer>

<!-- inserido por JavaScript, no fim do documento -->
<ul class="sugestoes">
  <li>Processo 2024/118 — Licenciamento</li>
  <li>Processo 2024/204 — Obras</li>
</ul>
```

**O que corre mal aqui:** quem vê o ecrã tem as sugestões por baixo do campo. Quem lê com leitor de ecrã em modo de navegação tem-nas depois do rodapé, no fim de tudo. A pessoa escreve, ouve silêncio, e conclui que não há resultados. Nem sequer é um problema de ARIA: é um problema de **sítio**.

**Versão corrigida:**

```html
<div class="campo-pesquisa">
  <label for="pesquisa">Pesquisar processos</label>
  <input id="pesquisa" type="search" autocomplete="off"
         aria-controls="lista-sugestoes" aria-expanded="true">

  <ul id="lista-sugestoes" class="sugestoes">
    <li>Processo 2024/118 — Licenciamento</li>
    <li>Processo 2024/204 — Obras</li>
  </ul>
</div>
```

```css
.campo-pesquisa { position: relative; }
.sugestoes { position: absolute; top: 100%; left: 0; right: 0; }
```

**Porque funciona:** o painel está imediatamente a seguir ao campo no documento, pelo que é o próximo conteúdo a ser lido e a próxima paragem lógica. O posicionamento visual é tratado com `position: absolute` dentro de um contentor relativo — isso é posicionar, não reordenar. A ligação semântica entre o campo e a lista (o padrão *combobox*, com `role`, `aria-expanded` e navegação por setas) pertence à secção «Widgets Complexos» do módulo anterior e não se repete aqui.

> **Exceção com regra:** as janelas modais são o caso em que se aceita — e muitas vezes se recomenda — colocar o elemento no fim do documento ou numa camada superior (`<dialog>` com `showModal()`). Nesse caso, o que garante a coerência não é a proximidade no documento, mas a **gestão explícita do foco** e a desativação do resto (técnicas T6 e T8).

---

#### T3 — A mesma ordem em todas as larguras

Interfaces responsivas costumam reorganizar-se. O erro está em fazer essa reorganização com propriedades que separam o visual do documento.

**Exemplo problemático:**

```css
.painel { display: flex; flex-direction: column; }

@media (max-width: 48rem) {
  .resumo   { order: 1; }
  .detalhes { order: 3; }
  .acoes    { order: 2; }
}
```

**O que corre mal aqui:** em ecrã largo, a ordem lida é resumo → detalhes → ações. Em ecrã estreito, o que se vê é resumo → ações → detalhes, mas o que se lê continua a ser resumo → detalhes → ações. A mesma aplicação passa a ter duas ordens diferentes, consoante quem a usa. Para uma pessoa cega que dá apoio telefónico a um colega que vê, a conversa torna-se impossível: estão literalmente a ler documentos diferentes.

**Versão corrigida:**

```css
/* Uma só ordem no documento: resumo, ações, detalhes.
   O ecrã largo distribui em grelha, sem reordenar. */
.painel {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: 1fr;
}

@media (min-width: 48rem) {
  .painel { grid-template-columns: 2fr 1fr; }
  .resumo   { grid-column: 1; }
  .detalhes { grid-column: 1; }
  .acoes    { grid-column: 2; grid-row: 1 / span 2; }
}
```

**Porque funciona:** a ordem do documento foi decidida uma vez, a pensar na leitura sequencial (o que é mais importante primeiro). O CSS coloca as caixas em colunas diferentes, o que muda o **sítio** mas não a **sequência**. Sim, em ecrã largo a coluna da direita é lida depois — mas é a mesma sequência em ambos os casos, e isso é o que importa.

> **Aviso sobre Grid e Flexbox:** quando se usa `grid-column`/`grid-row` para colocar itens em posições que não seguem a ordem do documento, está-se novamente a criar divergência. A regra prática é: **posicionar em colunas e linhas é aceitável; trocar a sequência de cima para baixo dentro da mesma coluna não é.**

---

### Continuidade: mover o foco quando o conteúdo muda

#### T4 — Definir o foco inicial de cada vista (e usar `autofocus` com parcimónia)

Quando uma página carrega, o foco está no início do documento. Isso está certo por omissão, porque permite ler a página desde o princípio e usar os mecanismos de salto.

**Exemplo problemático:**

```html
<!-- No topo de todas as páginas da aplicação -->
<input type="search" id="pesquisa-global" autofocus>
```

**O que corre mal aqui:** o `autofocus` num campo de pesquisa global tem três efeitos indesejados. Primeiro, o leitor de ecrã salta a leitura do início da página e anuncia apenas o campo, pelo que a pessoa não fica a saber onde está. Segundo, entra imediatamente em modo de formulários, o que significa que as teclas de navegação rápida deixam de funcionar até a pessoa premir `Escape`. Terceiro, em ecrãs pequenos, o teclado virtual abre-se e ocupa metade do ecrã antes de a pessoa ter decidido o que quer fazer.

**Versão corrigida:**

```html
<!-- Regra: sem autofocus nas vistas gerais. -->
<input type="search" id="pesquisa-global">
```

```html
<!-- Exceção legítima: uma vista cuja única razão de existir é aquele campo -->
<dialog id="dialogo-procurar">
  <h2>Procurar no documento</h2>
  <label for="termo">Termo a procurar</label>
  <input id="termo" type="text" autofocus>
</dialog>
```

**Porque funciona:** o `autofocus` é adequado quando não existe ambiguidade nenhuma sobre o que a pessoa quer fazer a seguir — o caso típico é um diálogo com um só campo. Em tudo o resto, deixar o foco no início do documento respeita a autonomia de quem lê.

---

#### T5 — Mover o foco quando a aplicação muda de vista

Este é o problema clássico das aplicações de página única. A pessoa clica em «Processos» no menu lateral, o conteúdo principal é substituído, o endereço muda — mas para o navegador não houve navegação nenhuma. Não há recarregamento, não há reposição do foco, não há anúncio.

**Exemplo problemático:**

```js
function irPara(rota) {
  history.pushState({}, '', rota);
  const html = renderizar(rota);
  document.querySelector('#conteudo').innerHTML = html;
}
```

**O que corre mal aqui:** o conteúdo mudou, o foco continua no item do menu que foi clicado. Para quem vê, é evidente que a página mudou. Para quem usa leitor de ecrã, o foco está no mesmo sítio, o título do separador continua igual e nada foi anunciado. A pessoa fica sem saber se o clique funcionou. Muitas vezes clica de novo — e, se o segundo clique fizer alguma coisa diferente, a confusão aumenta.

**Versão corrigida:**

```js
function irPara(rota) {
  history.pushState({}, '', rota);

  const vista = renderizar(rota);           // devolve um elemento
  const conteudo = document.querySelector('#conteudo');
  conteudo.replaceChildren(vista);

  // 1. Atualizar o título do documento
  document.title = `${vista.dataset.titulo} — Portal de Serviços`;

  // 2. Mover o foco para o cabeçalho da nova vista
  const cabecalho = vista.querySelector('h1');
  cabecalho.setAttribute('tabindex', '-1');
  cabecalho.focus();

  // 3. Repor a posição de leitura no topo da vista
  window.scrollTo(0, 0);
}
```

```css
/* O cabeçalho recebe foco por código, não por Tab.
   O indicador só aparece quando faz sentido mostrá-lo. */
h1:focus { outline: none; }
h1:focus-visible { outline: 3px solid; outline-offset: 4px; }
```

**Porque funciona:** três coisas acontecem ao mesmo tempo, e as três são necessárias.

O **título do documento** muda, o que é lido pelo leitor de ecrã em algumas configurações e é o que a pessoa ouve se voltar ao separador mais tarde. Serve também de referência no histórico do navegador.

O **foco no `<h1>`** faz duas coisas de uma vez: o leitor de ecrã anuncia o cabeçalho — que é, por definição, a melhor frase possível para dizer «está aqui» — e o cursor de leitura é reposicionado ali, pelo que a seta para baixo continua a partir do início da vista nova. O `tabindex="-1"` permite que o elemento receba foco por código sem entrar na fila do `Tab`.

O **reposicionamento do scroll** garante que quem vê e quem amplia não fica a meio de uma vista que já não é a mesma.

> **Alternativa aceitável:** em vez do `<h1>`, focar um contentor com `tabindex="-1"` e um rótulo acessível. Funciona, mas anuncia menos contexto. O cabeçalho continua a ser a escolha mais informativa.
>
> **O que não fazer:** confiar apenas numa região dinâmica para anunciar «Página Processos carregada» sem mover o foco. O anúncio ouve-se, mas o cursor de leitura fica onde estava e a pessoa tem de o ir procurar. Regiões dinâmicas servem para mudanças que **não** exigem deslocação — ver a secção «Notificações e Atualizações de Conteúdo».

---

#### T6 — Devolver o foco quando uma camada fecha

Painéis laterais, diálogos, editores em linha e menus são camadas temporárias. Quem os abre tem de saber para onde devolver o foco quando eles fecham.

**Exemplo problemático:**

```js
function fecharPainel() {
  painel.hidden = true;
}
```

**O que corre mal aqui:** o foco estava dentro do painel. Quando o painel fica `hidden`, o elemento focado deixa de existir para efeitos de interação e o foco cai para o `<body>`. A partir daí, `Tab` recomeça no topo da aplicação. Quem estava a meio de uma lista longa volta ao princípio, e a pessoa que usa leitor de ecrã ouve silêncio — que é a coisa mais desorientadora que uma aplicação lhe pode oferecer.

**Versão corrigida:**

```js
let origemDoFoco = null;

function abrirPainel(gatilho) {
  origemDoFoco = gatilho;
  painel.hidden = false;
  painel.querySelector('h2').setAttribute('tabindex', '-1');
  painel.querySelector('h2').focus();
}

function fecharPainel() {
  painel.hidden = true;

  // O elemento de origem ainda existe no documento?
  const destino = (origemDoFoco && origemDoFoco.isConnected)
    ? origemDoFoco
    : document.querySelector('#lista-processos'); // ponto estável de recurso

  destino.focus();
  origemDoFoco = null;
}
```

**Porque funciona:** guarda-se a referência ao elemento que abriu a camada **antes** de fazer seja o que for, e devolve-se-lhe o foco no fim. A verificação `isConnected` cobre o caso muito comum em aplicações ricas: a pessoa abriu um painel para editar um item, e a ação que fez lá dentro apagou esse item — o botão que abriu o painel já não existe. Sem recurso alternativo, o `focus()` falha silenciosamente e o foco perde-se. Com recurso alternativo, a pessoa aterra num ponto estável e próximo.

> O elemento de recurso deve ser escolhido com critério: o contentor da lista, o cabeçalho da secção, o botão «Adicionar». **Nunca** o topo da página, exceto se não houver mesmo nada mais próximo.

Note-se que a mecânica de **prender** o foco dentro de um diálogo modal enquanto ele está aberto foi tratada na secção «Interações por Teclado e Foco» do módulo anterior. Aqui interessa a outra metade: o que acontece **antes** e **depois**.

---

#### T7 — Decidir quem herda o foco antes de destruir um elemento

Apagar uma linha, remover um ficheiro de uma lista, fechar um separador: são operações em que o elemento que tem o foco é precisamente o que vai desaparecer.

**Exemplo problemático:**

```js
botaoApagar.addEventListener('click', () => {
  const linha = botaoApagar.closest('li');
  linha.remove();
});
```

**O que corre mal aqui:** no momento em que a linha é removida, o botão que tinha o foco vai com ela. O foco cai para o `<body>`. Se a pessoa quiser apagar três itens seguidos, tem de percorrer a lista inteira com `Tab` entre cada um. É um dos erros mais frequentes e um dos mais irritantes de usar.

**Versão corrigida:**

```js
function apagarItem(botaoApagar) {
  const item = botaoApagar.closest('li');
  const lista = item.parentElement;

  // Decidir o herdeiro ANTES de destruir
  const seguinte = item.nextElementSibling;
  const anterior = item.previousElementSibling;

  let destino;
  if (seguinte) {
    destino = seguinte.querySelector('button.apagar');
  } else if (anterior) {
    destino = anterior.querySelector('button.apagar');
  } else {
    // A lista ficou vazia
    destino = document.querySelector('#adicionar-item');
  }

  const nome = item.dataset.nome;
  item.remove();
  destino.focus();

  anunciar(`${nome} removido.`); // ver «Notificações e Atualizações de Conteúdo»
}
```

**Porque funciona:** a decisão sobre o herdeiro é tomada enquanto o elemento ainda está no documento e ainda tem vizinhos. A ordem de preferência — item seguinte, item anterior, controlo de recurso — mantém a pessoa no mesmo contexto e permite repetir a operação sem custo. O anúncio complementa o movimento do foco: o foco diz *onde estou*, o anúncio diz *o que aconteceu*. As duas coisas são precisas.

---

### Contenção: manter o foco dentro dos limites certos

#### T8 — Desativar o resto da aplicação com `inert`

Quando uma camada modal está aberta, tudo o resto tem de deixar de ser alcançável — por `Tab`, por rato e pelo leitor de ecrã. Durante anos isso obrigava a três operações separadas e propensas a erro.

**Exemplo problemático:**

```js
function abrirModal() {
  modal.hidden = false;
  document.querySelector('#app').setAttribute('aria-hidden', 'true');
}
```

**O que corre mal aqui:** o `aria-hidden` esconde a aplicação do leitor de ecrã, mas **não** a retira da fila do `Tab`. O resultado é o pior cenário possível: a pessoa carrega em `Tab`, o foco sai do modal e vai parar a um botão que existe, que está focado, que reage às teclas — e que o leitor de ecrã se recusa a anunciar. Silêncio total, com o foco algures.

**Versão corrigida:**

```html
<div id="app"> ... a aplicação toda ... </div>
<dialog id="modal-confirmar">
  <h2 id="titulo-modal">Confirmar eliminação</h2>
  <p>Esta operação não pode ser anulada.</p>
  <button id="confirmar">Eliminar</button>
  <button id="cancelar">Cancelar</button>
</dialog>
```

```js
const modal = document.querySelector('#modal-confirmar');
const app = document.querySelector('#app');

function abrirModal(gatilho) {
  origemDoFoco = gatilho;
  app.inert = true;          // fora do Tab, fora da árvore de acessibilidade, sem cliques
  modal.showModal();         // <dialog> trata do resto
}

function fecharModal() {
  modal.close();
  app.inert = false;
  origemDoFoco?.focus();
}
```

**Porque funciona:** o atributo `inert` faz de uma só vez o que antes exigia três hacks: retira os elementos da ordem de tabulação, retira-os da árvore de acessibilidade e desativa os eventos de apontador. É suportado por todos os navegadores atuais. Combinado com `<dialog>` e `showModal()`, obtém-se ainda a camada superior e o `Escape` para fechar sem escrever código para isso.

> **Regra de ouro:** nunca aplique `inert`, `aria-hidden` ou `hidden` a um elemento que contenha o foco atual. Mova primeiro o foco para fora, depois desative. A ordem inversa produz um foco «órfão» e comportamentos imprevisíveis.

O `inert` não serve só para modais. Em aplicações ricas é igualmente útil para:

- painéis laterais que deslizam por cima do conteúdo;
- passos de um assistente que já não estão ativos mas continuam no documento por causa da animação;
- zonas em carregamento, enquanto o conteúdo não está pronto (combinado com o anúncio adequado);
- um separador que está no documento mas escondido — embora aqui `hidden` seja normalmente suficiente e mais simples.

---

#### T9 — Não criar armadilhas de foco involuntárias

Uma armadilha é qualquer situação em que a pessoa entra num sítio e não consegue sair só com o teclado. As armadilhas intencionais (dentro de um modal) são desejáveis e temporárias. As involuntárias são falhas do critério 2.1.2 e costumam nascer de boas intenções.

**Exemplo problemático:**

```js
campoEmail.addEventListener('blur', () => {
  if (!validarEmail(campoEmail.value)) {
    mostrarErro('Endereço inválido.');
    campoEmail.focus();   // «obrigar» a corrigir antes de continuar
  }
});
```

**O que corre mal aqui:** enquanto o valor estiver inválido, qualquer tentativa de sair do campo devolve o foco ao campo. A pessoa não consegue ir ao botão de ajuda, não consegue voltar atrás para ver o que escreveu no campo anterior, não consegue chegar ao botão de cancelar. Para quem usa leitor de ecrã é ainda pior: nem sequer é evidente que ficou presa — parece que o `Tab` deixou de funcionar. E há um efeito perverso adicional: quem escreve devagar, ou usa comando por voz, dispara a validação a meio de um endereço perfeitamente correto.

**Versão corrigida:**

```js
campoEmail.addEventListener('blur', () => {
  if (!validarEmail(campoEmail.value)) {
    campoEmail.setAttribute('aria-invalid', 'true');
    campoEmail.setAttribute('aria-describedby', 'erro-email');
    mostrarErro('Indique um endereço no formato nome@dominio.pt.');
  } else {
    campoEmail.removeAttribute('aria-invalid');
    limparErro();
  }
  // O foco não é tocado. A pessoa sai quando quiser.
});
```

**Porque funciona:** o erro é assinalado de forma percetível e programaticamente associado ao campo, mas a pessoa mantém o controlo do seu percurso. O impedimento real de submeter um formulário inválido faz-se na submissão — não prendendo as pessoas. O tratamento completo de erros de formulário pertence ao módulo sobre formulários acessíveis.

**Outras armadilhas frequentes em aplicações ricas:**

| Origem | Sintoma | Correção |
|---|---|---|
| Componente de terceiros num `<iframe>` (mapa, vídeo, chat, pagamento) | O `Tab` entra e não sai | Testar sempre; exigir ao fornecedor ou isolar com um botão de saída visível |
| Editor de texto rico | O `Tab` insere uma tabulação em vez de sair | Oferecer `Escape` seguido de `Tab`, e documentar essa combinação de forma visível |
| Interceção global de teclas (`keydown` no `document`) com `preventDefault()` | O `Tab` deixa de funcionar em partes da aplicação | Nunca travar `Tab` globalmente; filtrar por alvo |
| Carrossel ou vista com deslocação infinita horizontal | O `Tab` percorre centenas de itens fora do ecrã | Retirar da tabulação o que não está visível, ou paginar |

---

#### T10 — Receber foco não é um acontecimento

O critério 3.2.1 diz uma coisa simples: chegar a um elemento não pode, por si só, mudar o contexto.

**Exemplo problemático:**

```html
<label for="distrito">Distrito</label>
<select id="distrito" onchange="location.href = '/distrito/' + this.value">
  <option value="">Escolha...</option>
  <option value="lisboa">Lisboa</option>
  <option value="porto">Porto</option>
</select>
```

**O que corre mal aqui:** em vários navegadores e leitores de ecrã, percorrer as opções de uma lista pendente com as setas dispara `change` a cada passo. Quem usa teclado nunca chega a «Porto»: é levado para a página de Lisboa mal passa por cima dela. O que para quem usa rato é um atalho conveniente, para quem usa teclado é uma porta que se fecha.

**Versão corrigida:**

```html
<label for="distrito">Distrito</label>
<select id="distrito" name="distrito">
  <option value="">Escolha...</option>
  <option value="lisboa">Lisboa</option>
  <option value="porto">Porto</option>
</select>
<button type="button" id="ir">Ver distrito</button>
```

```js
document.querySelector('#ir').addEventListener('click', () => {
  const valor = document.querySelector('#distrito').value;
  if (valor) navegarPara(`/distrito/${valor}`);
});
```

**Porque funciona:** a mudança de contexto passa a exigir uma ação deliberada e inequívoca. A pessoa pode percorrer as opções à vontade, mudar de ideias, sair e voltar. O botão custa um clique a mais a quem usa rato e evita que a interface seja inutilizável para toda a gente que não usa.

O mesmo princípio aplica-se a: abrir painéis ao receber foco, submeter automaticamente ao preencher o último dígito de um código, reordenar listas conforme o foco se move, e iniciar reprodução de vídeo quando um elemento entra em foco.

---

### Consciência: saber onde se está

#### T11 — Garantir que o foco fica visível apesar das barras fixas

Barras de cabeçalho fixas, rodapés com ações persistentes, banners de consentimento e widgets de conversação são omnipresentes em aplicações ricas. Todos eles têm o mesmo defeito: ficam por cima do conteúdo, incluindo por cima do elemento que acabou de receber foco.

Quando o navegador desloca a página para mostrar o elemento focado, ele coloca-o na margem do ecrã — exatamente onde está a barra fixa.

**Exemplo problemático:**

```css
.cabecalho-fixo {
  position: sticky;
  top: 0;
  height: 4rem;
  background: #fff;
  z-index: 10;
}
```

**O que corre mal aqui:** ao percorrer a aplicação com `Tab` de baixo para cima, ou ao seguir uma ligação de salto, o elemento focado fica escondido debaixo do cabeçalho. Quem usa teclado vê o ecrã mexer-se e não vê o indicador de foco: fica sem saber onde está. Quem usa ampliação não consegue sequer localizar o cursor. Falha 2.4.11 e, na prática, torna 2.4.7 inútil — o indicador existe, mas ninguém o vê.

**Versão corrigida:**

```css
:root {
  --altura-cabecalho: 4rem;
}

.cabecalho-fixo {
  position: sticky;
  top: 0;
  height: var(--altura-cabecalho);
  z-index: 10;
}

/* Reserva de espaço para tudo o que o navegador desloca para o ecrã:
   foco por teclado, ligações internas, scrollIntoView(). */
html {
  scroll-padding-top: calc(var(--altura-cabecalho) + 1rem);
  scroll-padding-bottom: 6rem; /* se houver barra de ações fixa em baixo */
}
```

**Porque funciona:** o `scroll-padding-top` diz ao navegador que a zona útil do ecrã começa mais abaixo. Ao deslocar um elemento para o campo de visão, ele fica abaixo da barra e não por trás dela. É uma única linha de CSS que resolve simultaneamente o foco por teclado, as ligações internas e as chamadas a `scrollIntoView()`.

> **Não chega só isto.** O `scroll-padding` resolve o obscurecimento por deslocação. Não resolve elementos que aparecem *por cima* sem deslocação nenhuma — o widget de conversação no canto inferior direito, o banner de cookies persistente, a notificação em forma de «torrada» (i.e., que aparece e desaparece automaticamente passado um certo tempo). Para esses, a solução é de desenho: não os sobrepor a conteúdo interativo, torná-los dispensáveis, ou deslocá-los quando alguma coisa por baixo recebe foco.

---

#### T12 — Listas longas, carregamento contínuo e regresso à posição

Aplicações ricas apresentam frequentemente listas com milhares de registos, carregadas por troços ou virtualizadas (só as linhas visíveis existem no documento).

**Exemplo problemático:**

```js
// Deslocação infinita: quando se chega ao fim, carregam-se mais 50 registos
observador.observe(sentinela);

function aoChegarAoFim() {
  const novos = await carregarMais();
  lista.insertAdjacentHTML('beforeend', novos);
}
```

**O que corre mal aqui:** três problemas de uma vez. Primeiro, nada é anunciado — para quem usa leitor de ecrã, a lista continua aparentemente igual. Segundo, com virtualização, as linhas que saem do ecrã são removidas do documento; se uma delas tinha o foco, ele perde-se. Terceiro, o rodapé e tudo o que está depois da lista tornam-se inalcançáveis, porque a lista nunca acaba — um problema conhecido como «rodapé fugidio».

**Versão corrigida:**

```html
<ul id="resultados"> ... 50 registos ... </ul>

<p id="estado-resultados" class="visualmente-oculto" role="status"></p>

<button type="button" id="carregar-mais">
  Mostrar mais 50 resultados (50 de 1240 apresentados)
</button>
```

```js
document.querySelector('#carregar-mais').addEventListener('click', async (e) => {
  const botao = e.currentTarget;
  const anteriores = lista.children.length;

  botao.disabled = true;
  const novos = await carregarMais();
  lista.insertAdjacentHTML('beforeend', novos);
  botao.disabled = false;

  const total = lista.children.length;
  botao.textContent =
    `Mostrar mais 50 resultados (${total} de 1240 apresentados)`;

  // O foco permanece no botão: a pessoa pode carregar de novo sem procurar nada.
  document.querySelector('#estado-resultados').textContent =
    `Mais ${total - anteriores} resultados adicionados. ${total} de 1240.`;
});
```

**Porque funciona:** o carregamento passa a ser uma ação deliberada, o que resolve os três problemas ao mesmo tempo. O foco fica onde estava — no botão — o que permite repetir a operação sem custo. O conteúdo novo é inserido **antes** do botão, pelo que a ordem de leitura se mantém coerente: resultados, depois «mostrar mais». O rodapé continua alcançável. E o anúncio informa quem não vê o ecrã (a técnica de região dinâmica está detalhada na secção «Notificações e Atualizações de Conteúdo»).

**Restaurar a posição ao voltar atrás:**

```js
// Antes de sair da lista para uma vista de detalhe
function abrirDetalhe(item) {
  sessionStorage.setItem('posicao-lista', JSON.stringify({
    id: item.dataset.id,
    scroll: window.scrollY,
    carregados: lista.children.length
  }));
  irPara(`/processos/${item.dataset.id}`);
}

// Ao regressar à lista
function restaurarLista() {
  const guardado = JSON.parse(sessionStorage.getItem('posicao-lista') || 'null');
  if (!guardado) return;

  await carregarAte(guardado.carregados);
  const item = lista.querySelector(`[data-id="${guardado.id}"] a`);
  if (item) {
    item.focus();   // repõe foco e cursor de leitura; o scroll acompanha
  } else {
    window.scrollTo(0, guardado.scroll);
  }
}
```

**Porque funciona:** o requisito R14 é dos que mais melhora a experiência real e dos que menos aparece em listas de verificação. Quem abriu o registo 87 de uma lista de 1240 e voltou atrás não devia ter de percorrer os 86 anteriores outra vez. Focar o item de origem repõe simultaneamente a posição visual, a posição de leitura e o ponto de partida do `Tab` — três coisas com uma única chamada.

---

## Recomendações para Conteúdo Acessível

As técnicas anteriores dirigem-se a quem escreve código. Mas muitos problemas de ordem e foco nascem antes disso — na conceção e na redação. Estas recomendações dirigem-se a quem desenha, escreve e gere produto.

### Decidir a ordem de leitura no desenho, não no código

Anote a ordem de leitura pretendida nos protótipos, numerando os blocos. É uma anotação de dez segundos que evita reuniões inteiras mais tarde. Se a numeração desenhada não puder ser a ordem do documento, isso é sinal de que o desenho precisa de ser revisto — não de que o código precisa de uma solução criativa.

**Pergunta a fazer em cada revisão de desenho:** «Se lêssemos este ecrã em voz alta, de cima para baixo, por que ordem apareceriam as coisas? É essa a ordem que faz sentido?»

### Documentar o comportamento do foco como parte da especificação

Ao especificar um componente ou um fluxo, descreva explicitamente:

- para onde vai o foco quando isto abre;
- para onde volta quando isto fecha;
- o que acontece ao foco se o elemento em causa for eliminado;
- o que acontece se a operação falhar.

Estas quatro linhas numa especificação valem mais do que um relatório de auditoria posterior, porque evitam o problema em vez de o documentarem.

### Escrever cabeçalhos que funcionem como ponto de chegada

Como o foco de uma vista nova aterra tipicamente no cabeçalho principal, esse cabeçalho é a primeira coisa que muita gente ouve. Deve ser específico e informativo.

- Fraco: «Detalhe», «Resultados», «Página»
- Bom: «Processo 2024/118 — Licenciamento de obra», «12 resultados para "certidão"»

### Nomear com clareza os mecanismos de salto

As ligações de salto e os atalhos de navegação devem dizer para onde levam. «Saltar para o conteúdo principal» funciona; «Saltar» não. Numa aplicação com várias zonas persistentes, pode justificar-se mais do que uma: «Saltar para os resultados», «Saltar para os filtros».

Estas ligações devem ser **visíveis ao receberem foco**. Uma ligação de salto permanentemente invisível não é utilizável por quem vê o ecrã e navega por teclado.

### Manter a posição dos elementos entre vistas

Se o botão «Guardar» está no canto superior direito numa vista e no fundo do ecrã noutra, a pessoa tem de o procurar de cada vez. A consistência de posição reduz o número de passos de `Tab` e a carga cognitiva.

### Reservar espaço no desenho para os elementos fixos

Se a interface vai ter um cabeçalho fixo de 64 píxeis, essa medida tem de estar no sistema de desenho como um valor conhecido, para que o CSS a possa usar no `scroll-padding`. Cabeçalhos de altura variável que crescem quando aparece uma mensagem são uma fonte constante de foco obscurecido.

### Testar a ordem antes de testar o resto

Cinco minutos de `Tab` do princípio ao fim de um fluxo real revelam mais do que qualquer ferramenta automática. Nenhum verificador automático deteta uma ordem de foco ilógica, um foco que se perde ao fechar um painel ou um indicador escondido debaixo de uma barra. Estes são, por natureza, problemas de teste manual.

Sugestão de protocolo mínimo para cada fluxo novo:

1. `Tab` do início ao fim, sem tocar no rato, e registo de cada salto estranho.
2. Abrir e fechar cada camada, verificando o regresso do foco.
3. Apagar um item de cada lista, verificando quem herdou o foco.
4. Repetir a 400% de ampliação.
5. Repetir com o CSS desativado, para verificar a ordem do documento.

---

### Erros Comuns

**1. Reordenar visualmente com CSS e não corrigir o documento**
O `order`, o `row-reverse` e o `grid-area` mentem à ordem de foco. É a causa número um de ordens de tabulação absurdas.
*Correção:* reordenar no HTML; usar CSS apenas para posicionar.

**2. Tentar corrigir uma ordem errada com `tabindex` positivo**
Atribuir `tabindex="1"`, `"2"`, `"3"` para «arranjar» a sequência cria uma fila paralela que precede todos os outros elementos da página e que se desatualiza ao primeiro componente novo.
*Correção:* corrigir a ordem do documento. Nunca usar valores positivos.

**3. Mudar de vista sem mexer no foco**
O caso mais frequente e mais grave em aplicações de página única. A pessoa clica, o ecrã muda, e para quem não vê nada aconteceu.
*Correção:* focar o cabeçalho da vista nova e atualizar `document.title`.

**4. Deixar o foco cair para o `<body>`**
Acontece sempre que um elemento focado é escondido, removido ou substituído sem que ninguém decida o sucessor.
*Correção:* decidir o herdeiro antes de destruir; verificar com `document.activeElement` durante os testes.

**5. Não devolver o foco à origem ao fechar uma camada**
Fecha-se o painel e a pessoa é despejada no topo da aplicação.
*Correção:* guardar a referência ao gatilho; prever um destino de recurso caso ele já não exista.

**6. `aria-hidden` sem `inert`**
Esconde do leitor de ecrã mas mantém na fila do `Tab`. Produz foco silencioso — o pior resultado possível.
*Correção:* usar `inert`, ou `hidden` quando o elemento também deve desaparecer visualmente.

**7. Aplicar `inert` ou `aria-hidden` a um contentor que tem o foco lá dentro**
O foco fica órfão e o comportamento varia de navegador para navegador.
*Correção:* mover o foco primeiro, desativar depois.

**8. Inserir conteúdo flutuante no fim do documento**
Sugestões, dicas e painéis colocados no fim do `<body>` e posicionados por CSS ficam, para leitura, depois do rodapé.
*Correção:* inserir junto do controlo de origem (exceto modais, que compensam com gestão de foco).

**9. Forçar o foco de volta a um campo inválido**
Impede a pessoa de sair, viola 2.1.2 e castiga quem escreve devagar ou usa voz.
*Correção:* assinalar o erro com `aria-invalid` e mensagem associada; validar a sério na submissão.

**10. Mudar de contexto quando um elemento recebe foco ou muda de valor**
Listas pendentes que navegam ao mudar de opção, formulários que submetem sozinhos, painéis que abrem ao passar o foco.
*Correção:* exigir uma ação explícita (botão) para qualquer mudança de contexto.

**11. Barra fixa a tapar o elemento focado**
O indicador existe, cumpre o contraste, e ninguém o vê.
*Correção:* `scroll-padding-top` (e `-bottom`) proporcional à altura das barras; rever elementos flutuantes persistentes.

**12. Deslocação infinita sem alternativa**
Anula o rodapé, perde o foco em listas virtualizadas e não anuncia nada.
*Correção:* botão «Mostrar mais», ou paginação; anunciar quantos itens foram acrescentados; manter o foco no botão.

**13. Não restaurar a posição ao voltar atrás**
Regressar de um detalhe repõe a lista no topo e obriga a refazer o percurso todo.
*Correção:* guardar item, deslocação e número de itens carregados; focar o item de origem no regresso.

**14. Deslocar o ecrã sem que a pessoa tenha feito nada**
Animações de deslocação automática, carrosséis que se movem, «scrollytelling» que reposiciona o conteúdo.
*Correção:* deslocação apenas como resposta a uma ação; respeitar `prefers-reduced-motion`.

**15. Testar a ordem de foco só com o rato**
Um verificador automático dá verde e o fluxo é inutilizável por teclado.
*Correção:* incluir o percurso de `Tab` na definição de «pronto» de cada funcionalidade.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Existem duas ordens numa aplicação: a que se vê e a que existe.** O CSS controla a primeira; o documento define a segunda. Quando divergem, quem não vê o ecrã fica com a versão errada.

2. **Quatro C organizam tudo:** *Coerência* (a ordem corresponde ao que se vê), *Continuidade* (o foco vai para onde deve quando o conteúdo muda), *Contenção* (o foco fica dentro dos limites certos) e *Consciência* (é possível saber onde se está).

3. **Posicionar com CSS é legítimo; reordenar não é.** `justify-content`, `position: absolute` dentro de um contentor e a colocação em colunas de grelha resolvem quase todos os casos sem mexer na sequência.

4. **Numa aplicação de página única, mudar de vista sem mover o foco é o equivalente a não avisar ninguém.** Focar o `<h1>` da vista nova, atualizar `document.title` e repor a deslocação: três linhas que mudam tudo.

5. **O foco é uma responsabilidade que se assume no momento em que se altera o documento.** Abrir: guardar a origem e mover. Fechar: devolver, com destino de recurso. Apagar: decidir o herdeiro antes de destruir.

6. **`inert` substitui a combinação frágil de `aria-hidden` + `tabindex="-1"` + `pointer-events`,** e resolve de uma só vez a fila do `Tab`, a árvore de acessibilidade e os cliques.

7. **A chegada do foco a um elemento não é um acontecimento.** Nada de navegar, submeter ou abrir só porque o foco passou por ali.

8. **Um indicador de foco escondido é o mesmo que não existir.** `scroll-padding-top` proporcional às barras fixas é uma linha de CSS com um retorno desproporcional.

9. **Voltar atrás devia devolver a pessoa ao sítio onde estava.** Guardar e restaurar a posição de leitura é um dos requisitos menos verificados e mais sentidos por quem usa a aplicação todos os dias.

10. **Mover o foco e anunciar são ferramentas diferentes para problemas diferentes.** Se a pessoa tem de ir para lá, move-se o foco. Se só precisa de saber, anuncia-se — e isso é assunto da secção seguinte.

11. **Nenhuma ferramenta automática deteta a maior parte destes problemas.** Cinco minutos de `Tab`, uma vez a 400% e uma vez com o CSS desativado, revelam mais do que qualquer relatório.

---

### Exercícios Práticos

#### Exercício 1 — O percurso pintado no chão

Escolha uma aplicação Web que use regularmente e que tenha, pelo menos, uma barra lateral, um filtro e uma lista de resultados.

Sem tocar no rato, execute uma tarefa completa (por exemplo: filtrar, abrir um resultado, voltar à lista) e registe numa tabela:

| Momento | O que esperava | O que aconteceu | Requisito violado (R1–R14) |
|---|---|---|---|

Preste atenção especial a: quantos `Tab` são precisos para chegar ao conteúdo; o que acontece ao foco depois de aplicar um filtro; e onde fica o foco quando volta atrás.

*Entrega:* a tabela preenchida com um mínimo de cinco ocorrências e uma proposta de correção para as três mais graves.

---

#### Exercício 2 — Corrigir a ordem invertida

```html
<div class="cartao">
  <button class="favorito" aria-label="Marcar como favorito">★</button>
  <p class="preco">129 €</p>
  <h3><a href="/produto/331">Auscultadores sem fios XZ</a></h3>
  <p class="descricao">Cancelamento de ruído, 30 h de autonomia.</p>
  <button class="comprar">Adicionar ao carrinho</button>
</div>
```

```css
.cartao { display: flex; flex-direction: column; }
.cartao h3 { order: 1; }
.cartao .descricao { order: 2; }
.cartao .preco { order: 3; }
.cartao .favorito { order: 4; }
.cartao .comprar { order: 5; }
```

1. Descreva por que ordem o conteúdo é lido por um leitor de ecrã e por que ordem o `Tab` percorre os dois botões.
2. Explique porque é que isto é um problema, mesmo que o aspeto visual esteja correto.
3. Reescreva o HTML e o CSS para que o resultado visual seja idêntico e a ordem esteja correta.
4. Identifique que critério WCAG está em causa.

---

#### Exercício 3 — Implementar a mudança de vista

Parta de um esqueleto de aplicação de página única com três vistas (Lista, Detalhe, Definições) e um menu lateral.

1. Implemente a função de navegação de forma a cumprir os requisitos R5 e R14.
2. Teste com um leitor de ecrã (NVDA ou VoiceOver) e descreva o que se ouve ao mudar de vista.
3. Compare duas soluções: focar o `<h1>` e focar o contentor da vista. Qual dá mais contexto? Registe as diferenças.
4. Acrescente o restauro de posição ao voltar da vista de Detalhe para a Lista.

*Entrega:* código funcional e um parágrafo com a comparação da alínea 3.

---

#### Exercício 4 — Quem herda o foco? 

Uma lista de tarefas em que cada linha tem um botão «Concluir» e um botão «Eliminar».

1. Escreva a árvore de decisão do herdeiro do foco para cada um dos casos: eliminar a primeira linha, eliminar uma linha do meio, eliminar a última linha, eliminar a única linha existente.
2. Implemente-a.
3. Explique porque é que o anúncio da eliminação não substitui o movimento do foco, nem vice-versa.

---

#### Exercício 5 — Caça à armadilha

Em grupos de três, cada grupo recebe uma aplicação ou página com componentes de terceiros (um mapa incorporado, um leitor de vídeo, um widget de conversação, um editor de texto rico).

1. Percorra tudo com `Tab`, em ambos os sentidos (`Tab` e `Shift+Tab`).
2. Identifique todos os pontos em que ficou preso ou em que o `Tab` deixou de fazer o que era esperado.
3. Para cada um, classifique: armadilha intencional legítima, armadilha involuntária, ou ordem apenas estranha.
4. Proponha uma correção para cada armadilha involuntária, distinguindo o que pode ser corrigido internamente do que exige o fornecedor.

---

#### Exercício 6 — A barra fixa

Construa uma página com um cabeçalho fixo de 72 píxeis, uma barra de ações fixa em baixo de 64 píxeis e conteúdo longo com muitos elementos focáveis.

1. Percorra a página com `Tab` de baixo para cima e documente o que acontece ao indicador de foco.
2. Corrija com `scroll-padding`.
3. Acrescente uma ligação de salto para o conteúdo principal e verifique que o destino também não fica tapado.
4. Acrescente um widget de conversação fixo no canto inferior direito e discuta: que problemas de `2.4.11` continuam por resolver, e que soluções de desenho existem para eles?

---

#### Exercício 7 — Revisão de especificação

Recebe a seguinte especificação de funcionalidade:

> «Ao clicar em "Editar", abre-se um painel lateral com o formulário do registo. Ao guardar, o painel fecha e a lista é atualizada. Se o registo tiver sido entretanto alterado por outro utilizador, mostra-se um aviso de conflito.»

1. Identifique **todas** as decisões sobre foco e ordem de leitura que esta especificação deixa por definir.
2. Reescreva-a acrescentando essas decisões, de forma explícita e testável.
3. Escreva os critérios de aceitação correspondentes, redigidos de forma a poderem ser verificados por alguém que não conhece o código.

*Entrega:* a especificação reescrita e a lista de critérios de aceitação.

