# Widgets Complexos

## Introdução

Até aqui, este módulo tratou de **peças soltas**. Vimos como se declara o que um widget é e como se chama, como se comunica o seu estado e o seu valor, como se opera com teclado, apontador e voz e como se anunciam mudanças que acontecem sem o foco se mexer. Esta secção trata do que acontece quando essas peças se juntam.

Um **widget complexo** (também chamado *widget composto*) é um componente feito de **vários elementos que só fazem sentido em conjunto**: um conjunto de separadores, uma caixa de pesquisa com sugestões, um menu, uma árvore de pastas, uma grelha de dados editável, uma janela modal.

> **Analogia: a orquestra e a partitura**
>
> Tem dez músicos excelentes. Cada instrumento está afinado, cada músico sabe tocar. Se os puser todos em palco e disser «toquem», o resultado é ruído.
>
> O que falta não é talento: é a **partitura**. A partitura diz quem entra primeiro, quem responde a quem, quem se cala enquanto outro toca, e quando é que a peça acaba.
>
> Um widget complexo é a orquestra. Cada `role`, cada `aria-expanded`, cada `tabindex` é um músico afinado. A **partitura** é o *padrão* (*pattern*): o conjunto de regras que diz como é que aquelas peças se relacionam entre si e como é que a pessoa as conduz.
>
> A boa notícia é que **as partituras já estão escritas**. Chamam-se *ARIA Authoring Practices Guide* (APG) e são publicadas pelo W3C. Este é, provavelmente, o ponto mais importante desta secção: em widgets complexos, quem improvisa a partitura falha quase sempre.

### O que muda quando um widget é complexo

A diferença não é de grau, é de natureza. Num botão, há **um** elemento e **um** significado. Num conjunto de separadores há:

| Aspeto | Widget simples | Widget complexo |
|---|---|---|
| Elementos envolvidos | Um | Vários, com papéis diferentes |
| Relações | Nenhuma | Contentor ↔ filhos, controlo ↔ conteúdo controlado |
| Foco | Um destino | Um ponto de entrada + navegação interna |
| Estado | Local ao elemento | Um elemento muda, outro reage |
| Teclado | Tab e Enter/Espaço | Tab para entrar, setas para navegar dentro |

É essa última linha que costuma apanhar as equipas de surpresa, por isso vale a pena isolá-la já:

> **Regra do «uma paragem, muitas escolhas»**
> Um widget composto ocupa **uma única paragem** na navegação por `Tab`. Lá dentro, a pessoa navega com as **setas**.
>
> Se tiver dez separadores e cada um for uma paragem do `Tab`, quem navega por teclado tem de premir `Tab` dez vezes para passar ao lado do componente. Multiplique isso por uma barra lateral com trinta itens e percebe-se porque é que este detalhe não é cosmético.

A mecânica de como se implementa essa navegação interna — `tabindex` móvel (*roving tabindex*) e `aria-activedescendant` — pertence a esta secção, porque só faz sentido em componentes compostos. A base de teclado e foco (chegar, ordem, mostrar, libertar) foi tratada na secção «Interações por Teclado e Foco» e é pressuposta a partir daqui.

---

### Como as Pessoas com Deficiência Interagem com Widgets Complexos

Nas secções anteriores vimos **como** cada tecnologia de apoio opera um controlo. Aqui interessa outra coisa: **como é que a pessoa constrói na cabeça um mapa de uma coisa que não vê toda de uma vez**.

#### Pessoas cegas com leitor de ecrã

Um leitor de ecrã não descreve ecrãs: descreve **um elemento de cada vez**. Quem vê um conjunto de separadores percebe num instante que há cinco separadores, que o terceiro está ativo e que o conteúdo em baixo pertence a esse terceiro. Quem ouve recebe isto por fatias:

> *«Separadores. Envio, separador, 3 de 5, selecionado.»*

Repare no que aquela frase carrega: **o que é** (separador), **onde está** (3 de 5), **como está** (selecionado) e **em que grupo vive** (separadores). Se qualquer uma destas fatias faltar, a pessoa fica com um mapa incompleto. E um mapa incompleto é pior do que nenhum, porque dá confiança errada.

Estes utilizadores também usam **dois modos de operação** que convém conhecer:

- **Modo de leitura** (*browse mode*, no NVDA e JAWS): as setas navegam pelo **texto** da página, letra a letra, linha a linha. O leitor de ecrã intercepta as teclas antes de a página as receber.
- **Modo de foco** (*focus mode*, ou modo de aplicação): as teclas passam **diretamente** para o widget.

A troca entre modos costuma ser automática e é despoletada pelos `role` que usamos. Um `role="listbox"` faz o leitor de ecrã entrar em modo de foco. Um `<div>` com setas programadas à mão, não: as setas são apanhadas pelo leitor de ecrã e o widget nunca as recebe. **Este é o motivo técnico pelo qual «programei as setas em JavaScript» não é suficiente.**

#### Pessoas com baixa visão e ampliação de ecrã

Com ampliação a 400%, vê-se uma janela do tamanho de um cartão de visita. Um menu que abre a 600 píxeis de distância do botão que o abriu simplesmente **não existe** para esta pessoa: ela carrega no botão, nada parece acontecer, e desiste.

Em widgets complexos, esta questão aparece de forma muito concreta: **o conteúdo que aparece tem de aparecer perto do controlo que o fez aparecer**, e o foco tem de ir lá ter (ou ficar onde estava, conforme o padrão) de forma previsível.

#### Pessoas com limitações motoras

Já sabemos das secções anteriores que estas pessoas podem usar apenas teclado, um interruptor único, ou controlo por voz. O que muda nos widgets complexos é o **custo do erro**:

- Um menu que fecha assim que o rato sai da área obriga a uma precisão que muita gente não tem.
- Um componente com trinta paragens de `Tab` é trinta ativações de interruptor. Para quem usa varrimento (*scanning*), cada ativação pode demorar segundos.

#### Pessoas com deficiência cognitiva ou de aprendizagem

Widgets complexos são, por definição, mais exigentes: exigem perceber que há mais conteúdo escondido, onde está, e como voltar atrás. Aqui os inimigos são a **inconsistência** (o mesmo componente comporta-se de forma diferente em páginas diferentes) e a **invenção** (um componente que não se parece com nada que a pessoa já usou). Um acordeão que se parece com um acordeão e funciona como um acordeão é acessibilidade cognitiva.

#### Um exemplo do mesmo widget, visto de três formas

Um seletor de datas, para três pessoas:

- **Quem vê:** uma grelha, o mês em cima, o dia de hoje com um círculo.
- **Quem usa leitor de ecrã:** *«Escolher data, botão, expandido»* → *«Julho de 2026, grelha»* → *«17, quinta-feira, 17 de julho de 2026, selecionado»*. A grelha só é compreensível se os cabeçalhos das colunas (dias da semana) estiverem marcados como cabeçalhos e se cada célula tiver um nome completo — «17» sozinho não chega.
- **Quem usa apenas teclado:** setas para andar dia a dia, `PageUp`/`PageDown` para mudar de mês, `Home`/`End` para início e fim de semana, `Esc` para fechar sem escolher.

**O que isto mostra:** o mesmo componente tem de contar **a mesma história** por três canais diferentes. Não são três produtos: é um produto com três saídas coerentes.

---

### Requisitos de Acessibilidade para Widgets Complexos

Sete requisitos, todos específicos de componentes compostos. Os requisitos de base (nome, função, estado, teclado, foco visível, alvo de toque) aplicam-se a **cada peça** e foram tratados nas secções próprias.

#### 1. Seguir um padrão conhecido, em vez de inventar

Se o componente se parece com um dos padrões do APG, deve **comportar-se** como esse padrão. As pessoas transportam expectativas de site para site: `Esc` fecha, setas navegam, `Enter` ativa. Um componente original obriga cada utilizador a aprender do zero. E quem usa tecnologia de apoio paga essa aprendizagem em minutos, não em segundos.

#### 2. Declarar a estrutura, não só as peças

Não basta que cada peça tenha o seu `role`. As **relações** têm de estar declaradas: que este separador controla aquele painel, que esta caixa de texto tem aquela lista associada, que este botão abre aquele menu. É a diferença entre um monte de tijolos e uma parede.

#### 3. Respeitar a hierarquia obrigatória de papéis

Muitos `role` de ARIA têm **filhos obrigatórios**. Um `role="tablist"` tem de conter `role="tab"`. Um `role="listbox"` tem de conter `role="option"`. Se meter um `<div>` decorativo pelo meio, a relação parte-se e o leitor de ecrã deixa de conseguir dizer «3 de 5».

#### 4. Uma paragem de `Tab` por componente

Já enunciado acima. Implementa-se com `tabindex` móvel ou `aria-activedescendant` (ver «Técnicas de Codificação»).

#### 5. Teclado completo e convencional dentro do componente

Cada padrão tem o seu conjunto de teclas. Não é opcional e não é negociável: `Esc` que não fecha um menu é um defeito, não uma preferência de design.

#### 6. Gerir o foco quando a estrutura muda

Abrir um diálogo, apagar uma linha de uma grelha, colapsar um ramo de uma árvore — tudo isto mexe com o sítio onde o foco está. Os princípios estão na secção «Interações por Teclado e Foco»; aqui aplicam-se a estruturas onde o foco pode desaparecer **para dentro** de conteúdo colapsado.

#### 7. Não esconder conteúdo apenas para uns

Um painel colapsado tem de estar escondido **para toda a gente**, visual e programaticamente. Um `<div>` com `height: 0; overflow: hidden` continua a ser lido pelo leitor de ecrã e continua a receber `Tab`. A pessoa passa a navegar dentro de conteúdo que não está lá. Este é um dos erros mais frequentes e mais desorientadores.

---

## Técnicas de Codificação

### Técnica 0 — Antes de codificar: precisa mesmo deste widget?

Esta técnica não escreve nenhuma linha de código, e é a que poupa mais problemas.

Muitos widgets complexos existem porque alguém quis poupar espaço, não porque a interação exigia. Antes de construir:

- Um **conjunto de separadores** com dois separadores de três linhas cada resolve-se com dois títulos e dois parágrafos.
- Um **acordeão** de perguntas frequentes com cinco perguntas pode ser uma lista de perguntas e respostas visíveis.
- Um **carrossel** de três imagens costuma ser três imagens.

**O que funciona bem:** conteúdo sempre visível funciona com todas as tecnologias de apoio, é encontrado pelo `Ctrl+F` do navegador, é indexado, imprime bem e não tem estados para gerir.

**O que corre mal:** cada widget complexo que se constrói é uma dívida permanente, para manter, testar e explicar.

> **Regra prática:** o componente mais acessível é o que não existe. O segundo mais acessível é o nativo. O terceiro é o padrão do APG, copiado com fidelidade.

---

### Técnica 1 — Declarar relações entre peças

Quatro atributos fazem quase todo o trabalho de «costura» num widget complexo.

#### `aria-controls` — «eu comando aquilo»

```html
<button aria-expanded="false" aria-controls="painel-envio">
  Opções de envio
</button>
<div id="painel-envio" hidden>
  <!-- conteúdo -->
</div>
```

Diz que este botão comanda aquele painel. O suporte de `aria-controls` nos leitores de ecrã é irregular (o JAWS oferece um atalho para saltar para o elemento controlado; a maioria dos outros ignora-o). Ainda assim, é obrigatório em vários padrões do APG e é lido por ferramentas de auditoria.

#### `aria-expanded` — «aquilo está aberto ou fechado»

Já foi tratado na secção «Propriedades, Estados e Valores de Widgets». O que interessa aqui é **onde** o pôr: `aria-expanded` vai **no controlo que abre**, nunca no conteúdo que abre.

```html
<!-- MAL: o estado está no sítio errado -->
<button aria-controls="menu-conta">A minha conta</button>
<ul id="menu-conta" aria-expanded="false"> ... </ul>

<!-- BEM -->
<button aria-expanded="false" aria-controls="menu-conta">A minha conta</button>
<ul id="menu-conta" hidden> ... </ul>
```

**Porque é que a primeira versão falha:** a pessoa está com o foco no botão. É aí que precisa de ouvir «fechado». Se o estado estiver num elemento que está escondido, ninguém o ouve nunca — o leitor de ecrã não anuncia atributos de elementos que não estão a ser lidos.

#### `aria-haspopup` — «carregar aqui abre uma coisa por cima»

```html
<button aria-haspopup="menu" aria-expanded="false" aria-controls="menu-acoes">
  Ações
</button>
```

Anuncia-se como *«tem submenu»* ou *«menu instantâneo»*. Os valores possíveis são `menu`, `listbox`, `tree`, `grid` e `dialog` (`true` é sinónimo de `menu`). Deve corresponder ao `role` do que abre de facto.

**Erro clássico:** pôr `aria-haspopup="true"` num botão que abre um painel que é apenas um `<div>` com texto. A pessoa ouve «tem submenu», espera setas e itens de menu, e recebe um parágrafo. A promessa não foi cumprida.

#### `aria-owns` — «este é meu filho, apesar do HTML dizer o contrário»

Serve para reparar hierarquias quebradas quando o HTML não pode ser reorganizado (por exemplo, quando um menu é colocado no fim do `<body>` para escapar a um `overflow: hidden`).

```html
<ul role="menu" id="menu-pai" aria-owns="submenu-flutuante">
  <li role="menuitem">Guardar</li>
</ul>
...
<!-- no fim do body, por causa do CSS -->
<ul role="menu" id="submenu-flutuante"> ... </ul>
```

**Aviso importante:** `aria-owns` é a última opção, não a primeira. Reordena a árvore de acessibilidade mas **não** reordena a navegação por `Tab`, o que cria um descompasso entre o que o leitor de ecrã diz e por onde o teclado anda. Cada `aria-owns` no código é um sinal de que a estrutura do HTML devia ter sido resolvida de outra maneira.

---

### Técnica 2 — Respeitar os filhos obrigatórios

Este é o erro estrutural mais comum e o mais invisível em testes superficiais.

```html
<!-- MAL: um div a partir a relação -->
<div role="tablist">
  <div class="wrapper-flex">
    <button role="tab" aria-selected="true">Envio</button>
    <button role="tab" aria-selected="false">Pagamento</button>
  </div>
</div>
```

**O que corre mal:** o `role="tablist"` exige `role="tab"` como **filhos diretos** na árvore de acessibilidade. O `div.wrapper-flex` não tem `role` nenhum, mas continua a existir nessa árvore como um contentor genérico. Resultado: a lista de separadores fica «vazia» e o leitor de ecrã já não consegue dizer «1 de 2». O separador continua a ser anunciado como separador — o que engana quem testa — mas a contagem e a relação de grupo desaparecem.

```html
<!-- BEM, opção A: apagar o contentor intermédio da árvore -->
<div role="tablist">
  <div class="wrapper-flex" role="presentation">
    <button role="tab" aria-selected="true">Envio</button>
    <button role="tab" aria-selected="false">Pagamento</button>
  </div>
</div>

<!-- BEM, opção B: pôr o CSS no próprio tablist -->
<div role="tablist" class="wrapper-flex">
  <button role="tab" aria-selected="true">Envio</button>
  <button role="tab" aria-selected="false">Pagamento</button>
</div>
```

A opção B é preferível: menos ARIA, menos coisas para partir. `role="presentation"` (sinónimo de `role="none"`) remove um elemento da árvore de acessibilidade mantendo os filhos — é o «vidro transparente» que existe para o CSS mas não para o leitor de ecrã.

**Pares que têm de ser respeitados:**

| Contentor | Filhos obrigatórios |
|---|---|
| `tablist` | `tab` |
| `listbox` | `option` (ou `group` → `option`) |
| `menu` / `menubar` | `menuitem`, `menuitemcheckbox`, `menuitemradio` |
| `tree` | `treeitem` (agrupados em `group`) |
| `radiogroup` | `radio` |
| `grid` | `row` (dentro de `rowgroup`) → `gridcell` |

---

### Técnica 3 — Navegação interna: `tabindex` móvel

A primeira das duas formas de fazer «uma paragem, muitas escolhas». A ideia foi introduzida na secção «Interações por Teclado e Foco»; aqui interessa a implementação completa num padrão real.

**O princípio:** exatamente **um** elemento do grupo tem `tabindex="0"`; todos os outros têm `tabindex="-1"`. Quando a pessoa carrega numa seta, os valores trocam e o foco move-se com o `.focus()`.

> **Analogia: o crachá de visitante**
> Há um único crachá que dá entrada pela porta principal. Quem o tiver é quem o `Tab` encontra. Lá dentro, o crachá passa de mão em mão conforme a pessoa anda pelas salas — e, ao sair e voltar a entrar, entra-se pela sala onde se estava. Não se volta ao princípio.

```html
<div role="tablist" aria-label="Detalhes da encomenda">
  <button role="tab" id="tab-envio" aria-selected="true"
          aria-controls="painel-envio" tabindex="0">Envio</button>
  <button role="tab" id="tab-pagamento" aria-selected="false"
          aria-controls="painel-pagamento" tabindex="-1">Pagamento</button>
  <button role="tab" id="tab-fatura" aria-selected="false"
          aria-controls="painel-fatura" tabindex="-1">Fatura</button>
</div>

<div role="tabpanel" id="painel-envio" aria-labelledby="tab-envio" tabindex="0">
  <p>Entrega prevista para 21 de julho.</p>
</div>
<div role="tabpanel" id="painel-pagamento" aria-labelledby="tab-pagamento" tabindex="0" hidden>
  <p>Multibanco — referência 123 456 789.</p>
</div>
<div role="tabpanel" id="painel-fatura" aria-labelledby="tab-fatura" tabindex="0" hidden>
  <p>Fatura disponível após o envio.</p>
</div>
```

```js
const tablist = document.querySelector('[role="tablist"]');
const tabs = [...tablist.querySelectorAll('[role="tab"]')];

function activarSeparador(novo) {
  tabs.forEach(tab => {
    const activo = tab === novo;
    tab.setAttribute('aria-selected', activo);
    tab.tabIndex = activo ? 0 : -1;
    document.getElementById(tab.getAttribute('aria-controls')).hidden = !activo;
  });
  novo.focus();
}

tablist.addEventListener('keydown', e => {
  const i = tabs.indexOf(document.activeElement);
  if (i === -1) return;
  let destino = null;

  switch (e.key) {
    case 'ArrowRight': destino = tabs[(i + 1) % tabs.length]; break;
    case 'ArrowLeft':  destino = tabs[(i - 1 + tabs.length) % tabs.length]; break;
    case 'Home':       destino = tabs[0]; break;
    case 'End':        destino = tabs[tabs.length - 1]; break;
  }
  if (destino) {
    e.preventDefault();
    activarSeparador(destino);
  }
});

tabs.forEach(tab => tab.addEventListener('click', () => activarSeparador(tab)));
```

**O que funciona bem neste exemplo:**

- **Uma paragem do `Tab`** para os três separadores. O `Tab` seguinte leva ao painel.
- **Circularidade:** do último para o primeiro com `→`. É o comportamento esperado num `tablist`.
- **`preventDefault()`** nas setas evita deslocações da página enquanto se navega.
- **`aria-selected` e `tabindex` mudam sempre juntos.** É a mesma verdade dita de duas maneiras; se divergirem, o widget mente a alguém.
- **`aria-labelledby` no painel** faz com que o painel se anuncie com o nome do separador que o abriu — a pessoa sabe onde caiu.
- **`tabindex="0"` no painel** dá-lhe uma paragem própria, para que quem chega lá com `Tab` possa ler o conteúdo. É a recomendação do APG quando o painel **não** começa com um elemento focável.
- **`hidden`** esconde para toda a gente: sai do ecrã, sai da árvore de acessibilidade e sai da ordem de `Tab`. Um único atributo faz o que três linhas de CSS fazem mal.
- **Clique e teclado partilham a mesma função.** Não há dois caminhos que possam divergir.

**O que faltaria numa versão real:** o APG distingue separadores de **ativação automática** (o painel muda ao navegar com as setas — a versão acima) de **ativação manual** (as setas movem o foco, `Enter` ou `Espaço` é que muda o painel). A ativação manual é preferível quando o painel é pesado de carregar, para não disparar três carregamentos enquanto se atravessa a lista.

---

### Técnica 4 — Navegação interna: `aria-activedescendant`

A segunda forma. Aqui o foco real **nunca sai** de um único elemento; o que se move é um **ponteiro**.

> **Analogia: o cursor do rato e o dedo**
> No `tabindex` móvel, a pessoa **caminha** de sala em sala.
> Com `aria-activedescendant`, a pessoa fica sentada e **aponta** para a sala. O foco do navegador não se mexe; o leitor de ecrã lê aquilo para onde o dedo aponta.

Isto é indispensável quando é preciso **escrever num campo e navegar numa lista ao mesmo tempo** — o caso da caixa de pesquisa com sugestões.

```html
<label for="pesquisa-concelho">Concelho</label>
<input type="text" id="pesquisa-concelho"
       role="combobox"
       aria-expanded="false"
       aria-controls="lista-concelhos"
       aria-autocomplete="list"
       autocomplete="off">

<ul role="listbox" id="lista-concelhos" aria-label="Sugestões de concelhos" hidden>
  <li role="option" id="opcao-0">Lisboa</li>
  <li role="option" id="opcao-1">Loures</li>
  <li role="option" id="opcao-2">Loulé</li>
</ul>
```

```js
const campo = document.getElementById('pesquisa-concelho');
const lista = document.getElementById('lista-concelhos');
const opcoes = [...lista.querySelectorAll('[role="option"]')];
let indice = -1;

function apontar(novoIndice) {
  opcoes.forEach(o => o.removeAttribute('aria-selected'));
  indice = novoIndice;
  if (indice === -1) {
    campo.removeAttribute('aria-activedescendant');
    return;
  }
  const opcao = opcoes[indice];
  opcao.setAttribute('aria-selected', 'true');
  campo.setAttribute('aria-activedescendant', opcao.id);
  opcao.scrollIntoView({ block: 'nearest' });
}

function abrir(estado) {
  lista.hidden = !estado;
  campo.setAttribute('aria-expanded', estado);
  if (!estado) apontar(-1);
}

campo.addEventListener('keydown', e => {
  switch (e.key) {
    case 'ArrowDown':
      e.preventDefault();
      if (lista.hidden) abrir(true);
      apontar((indice + 1) % opcoes.length);
      break;
    case 'ArrowUp':
      e.preventDefault();
      if (lista.hidden) abrir(true);
      apontar((indice - 1 + opcoes.length) % opcoes.length);
      break;
    case 'Enter':
      if (indice > -1) {
        e.preventDefault();
        campo.value = opcoes[indice].textContent;
        abrir(false);
      }
      break;
    case 'Escape':
      abrir(false);
      break;
  }
});
```

**O que funciona bem:**

- **O foco real nunca sai do campo de texto.** A pessoa continua a poder escrever, apagar, corrigir — enquanto navega nas sugestões com as setas. Com `tabindex` móvel isto seria impossível: ao mover o foco para a lista, as teclas deixavam de chegar ao campo.
- **`aria-activedescendant` aponta para o `id`** da opção ativa. O leitor de ecrã anuncia essa opção como se lá estivesse o foco.
- **`Esc` fecha sem escolher** e devolve o controlo — o comportamento que toda a gente espera.
- **`aria-expanded` no campo** avisa que há uma lista aberta. Sem ele, as sugestões aparecem em silêncio.
- **`scrollIntoView`** garante que a opção apontada está visível — decisivo para quem usa ampliação de ecrã, porque o navegador **não** faz *scroll* automático (não há foco real que o obrigue a isso).
- **`autocomplete="off"`** evita que a lista nativa do navegador se sobreponha à nossa.

**O que corre mal se se falhar um detalhe:**

- Se o `id` em `aria-activedescendant` não existir ou tiver um erro de escrita, o atributo é **silenciosamente ignorado**. Não há erro na consola. O widget parece bem e não anuncia nada.
- Se se esquecer o `scrollIntoView`, quem vê acompanha... enquanto a lista couber no ecrã. A partir da sexta sugestão, o leitor de ecrã diz «Loulé» e o ecrã mostra «Lisboa».

**Qual escolher, `tabindex` móvel ou `aria-activedescendant`?**

| | `tabindex` móvel | `aria-activedescendant` |
|---|---|---|
| Onde está o foco real | No item ativo | Fica sempre no contentor |
| *Scroll* automático | Sim, feito pelo navegador | **Não** — tem de ser programado |
| CSS `:focus` funciona no item | Sim | Não — precisa de uma classe própria |
| Bom para | Separadores, menus, barras de ferramentas, árvores | Campos de texto com lista associada, grelhas grandes |
| Suporte | Excelente e uniforme | Bom, mas com arestas em alguns pares navegador/leitor |

**Regra prática:** se a pessoa não precisa de escrever ao mesmo tempo, use `tabindex` móvel. É mais robusto e usa mecanismos nativos do navegador.

---

### Técnica 5 — Diálogos modais: o caso que compensa fazer nativo

O diálogo modal é o widget complexo mais usado e o mais frequentemente mal feito. Felizmente, o HTML já tem um.

```html
<button id="botao-abrir">Cancelar encomenda</button>

<dialog id="dialogo-cancelar" aria-labelledby="titulo-dialogo">
  <h2 id="titulo-dialogo">Cancelar a encomenda?</h2>
  <p>Esta ação não pode ser revertida.</p>
  <button id="botao-confirmar">Sim, cancelar</button>
  <button id="botao-fechar">Manter encomenda</button>
</dialog>
```

```js
const dialogo = document.getElementById('dialogo-cancelar');

document.getElementById('botao-abrir')
  .addEventListener('click', () => dialogo.showModal());

document.getElementById('botao-fechar')
  .addEventListener('click', () => dialogo.close());
```

**O que o `<dialog>` com `showModal()` faz sozinho:**

- Move o foco para dentro do diálogo.
- **Prende** o foco lá dentro (o `Tab` não sai — sem código nenhum).
- Torna o resto da página inerte: não é clicável, não é lido pelo leitor de ecrã, não recebe foco.
- Fecha com `Esc`.
- **Devolve o foco ao botão que o abriu** quando fecha.
- Anuncia-se como diálogo, com o nome vindo do `aria-labelledby`.

**Porque é que isto importa:** cada um destes comportamentos, feito à mão, são dezenas de linhas de JavaScript, uma lista de seletores de elementos focáveis que fica sempre desatualizada, e um caso extremo qualquer que ninguém previu. É o exemplo mais claro de «o nativo primeiro» deste módulo inteiro.

**O que ainda tem de fazer:**

- O `<dialog>` não tem `role="dialog"` explícito no HTML porque **já o tem implícito** — não o acrescente.
- Não use `aria-modal="true"` num `<dialog>` aberto com `showModal()`: é redundante e, em alguns pares navegador/leitor de ecrã, chega a atrapalhar.
- Se abrir o `<dialog>` com `.show()` (não modal) ou com o atributo `open`, **nenhuma** das garantias acima se aplica.
- Estilizar o fundo escurecido faz-se com `#dialogo-cancelar::backdrop`.

**Se tiver mesmo de construir um diálogo à mão** (por restrições de suporte ou de arquitetura), o mínimo é: `role="dialog"`, `aria-modal="true"`, nome acessível, foco movido para dentro ao abrir, foco preso, `Esc` a fechar, foco devolvido ao abrir, e o resto da página marcado com o atributo `inert`.

---

### Técnica 6 — Esconder é esconder para todos

Um widget complexo vive de mostrar e esconder. Fazê-lo mal cria «conteúdo fantasma»: invisível no ecrã, mas presente para o teclado e para o leitor de ecrã.

```html
<!-- MAL: fantasma clássico -->
<div class="painel" style="height: 0; overflow: hidden;">
  <a href="/detalhes">Ver detalhes</a>
</div>

<!-- MAL: também fantasma -->
<div class="painel" style="opacity: 0;"> ... </div>
```

**O que corre mal:** o `Tab` entra ali. A pessoa que navega por teclado vê o indicador de foco **desaparecer do ecrã** e não faz ideia de onde está. O leitor de ecrã lê conteúdo que ninguém vê. É desorientação pura.

```html
<!-- BEM -->
<div class="painel" hidden> ... </div>
```

| Técnica | Esconde do ecrã | Esconde do leitor de ecrã | Tira da ordem de `Tab` |
|---|---|---|---|
| `hidden` / `display: none` | Sim | Sim | Sim |
| `visibility: hidden` | Sim | Sim | Sim |
| `aria-hidden="true"` | **Não** | Sim | **Não** ⚠️ |
| `opacity: 0`, `height: 0` | Sim | **Não** | **Não** |
| Classe `.apenas-leitor-ecra` | Sim | **Não** (de propósito) | Não |
| `inert` | Não | Sim | Sim |

⚠️ **A combinação mais perigosa da tabela:** `aria-hidden="true"` num contentor que tem elementos focáveis lá dentro. O `Tab` leva o foco para um elemento que, para o leitor de ecrã, **não existe**. O resultado é o leitor de ecrã ficar em silêncio absoluto com o foco algures. Se usar `aria-hidden`, garanta que nada lá dentro é focável — ou use `inert`, que trata das duas coisas.

Para animar a abertura de um painel sem criar fantasmas, alterne o `hidden` no fim da animação, ou use `@starting-style` com `transition-behavior: allow-discrete`.

---

### Técnica 7 — Testar o que não se vê

Um widget complexo passa em testes automáticos e falha com pessoas. As ferramentas verificam atributos; não verificam se a experiência faz sentido. Testes mínimos, por ordem de custo:

1. **Desligue o rato.** Faça a tarefa completa só com teclado: chegar, entrar, navegar, ativar, sair, `Esc`.
2. **Inspecione a árvore de acessibilidade.** Nas ferramentas de programador do Chrome ou do Firefox, veja o componente como o leitor de ecrã o vê. Se o `tablist` aparece vazio, encontrou um `div` a mais.
3. **Ligue um leitor de ecrã.** NVDA no Windows, VoiceOver no macOS. Não precisa de ser perito: precisa de ouvir se o componente diz o que é, onde está e como está.
4. **Amplie a 400%.** O que abre, abre onde se vê?
5. **Compare com o exemplo do APG.** Abra o exemplo oficial do padrão e faça a mesma tarefa. As diferenças que sentir são defeitos seus.

---

## Recomendações para Conteúdo Acessível

Nem tudo se resolve no código. Muitas decisões que tornam um widget complexo utilizável são tomadas antes, por quem escreve e por quem desenha.

**Para quem escreve conteúdo**

- **Rótulos que funcionam fora de contexto.** Um separador chamado «Mais» é inútil quando anunciado sozinho: *«Mais, separador, 3 de 4»*. «Documentos anexos» diz alguma coisa.
- **Rotule o grupo, não só as peças.** Se a página tem dois conjuntos de separadores, `aria-label="Detalhes da encomenda"` e `aria-label="Histórico de contactos"` no `tablist` de cada um evitam que a pessoa ouça «separadores» duas vezes e não saiba qual é qual.
- **Não esconda conteúdo essencial dentro de widgets.** O prazo de recurso não pode estar no quinto separador de um acordeão colapsado. Se é essencial, está visível.
- **Rótulos curtos e distintos.** Quem usa controlo por voz diz o rótulo em voz alta (ver a secção «Interações por Fala»). «Documentos» ganha a «Documentos que foram anexados a este processo».
- **Escreva a ajuda para quem não vê o desenho.** «Selecione um dos separadores em cima» pressupõe «em cima». «Selecione uma das categorias» não pressupõe nada.

**Para quem desenha**

- **Desenhe todos os estados.** Fechado, aberto, com foco, ativo, com foco *e* ativo, desativado, em carregamento, vazio, em erro. O estado que não for desenhado será improvisado por quem programa.
- **Distinga «tem foco» de «está selecionado» visualmente.** Num conjunto de separadores, estes dois estados podem estar em separadores diferentes (com ativação manual). Se ambos forem «azul», ninguém percebe o que vai acontecer se carregar em `Enter`.
- **Não dependa só da cor** para marcar o separador ativo ou o item selecionado. Um sublinhado, um peso de letra, um ícone.
- **Prefira componentes que se parecem com o que são.** Um acordeão com setas para baixo e para cima é reconhecido. Um acordeão com pontos coloridos tem de ser aprendido.
- **Conte quantos widgets complexos há por ecrã.** Três acordeões dentro de dois separadores dentro de um modal é um sintoma de arquitetura de informação, não de interface.
- **Peça o padrão ao desenhar.** «Isto é um `tablist` do APG» é uma decisão de design, não de programação. E tomá-la cedo evita reescritas.

**Para quem decide**

- **Adotar uma biblioteca de componentes acessível é uma decisão de acessibilidade.** Muitas bibliotecas populares implementam os padrões do APG e são testadas com tecnologias de apoio; construir de raiz é assumir esse trabalho para sempre.
- **Um componente novo é uma dívida.** Cada widget original tem de ser testado com tecnologias de apoio em cada atualização.

### Erros Comuns

**1. Inventar o padrão**
Um componente que não é separadores nem acordeão nem menu, mas um bocadinho de cada. Ninguém sabe que teclas usar. Nem quem o programou. Solução: escolher um padrão do APG e segui-lo até ao fim.

**2. Trinta paragens de `Tab` num só componente**
Cada item da lista com `tabindex="0"`. O componente vira um muro. Solução: `tabindex` móvel ou `aria-activedescendant`.

**3. O `div` que parte a hierarquia**
`role="tablist"` → `div` de *layout* → `role="tab"`. A contagem «3 de 5» desaparece e ninguém dá por isso. Solução: `role="presentation"` no contentor intermédio, ou pôr o CSS no elemento certo.

**4. Conteúdo fantasma**
Painel escondido com `height: 0` ou `opacity: 0`, com ligações lá dentro a receber foco. Solução: `hidden`.

**5. `aria-hidden="true"` a esconder coisas focáveis**
O foco entra num sítio que, para o leitor de ecrã, não existe. Silêncio total. Solução: `inert`, ou garantir que nada lá dentro é focável.

**6. `aria-expanded` no elemento errado**
No painel em vez do botão. O estado nunca é ouvido. Solução: sempre no controlo.

**7. `Esc` que não faz nada**
Menu aberto, modal aberto, sugestões abertas — e `Esc` sem efeito. É o gesto universal de «tira-me daqui». Solução: implementar sempre.

**8. Diálogo modal caseiro sem foco preso**
O `Tab` sai do modal e vai para a página atrás, que continua visualmente escurecida. Quem não vê o ecrã fica a navegar num sítio inacessível. Solução: `<dialog>` com `showModal()`.

**9. `aria-haspopup` a prometer o que não existe**
«Tem submenu» num botão que abre um `div` com texto. Solução: usar o valor que corresponde ao `role` real do que abre.

**10. `role="menu"` na navegação do site**
`role="menu"` é para menus de **aplicação** (Ficheiro, Editar, Ver) — troca o leitor de ecrã para modo de aplicação e faz o `Tab` deixar de funcionar dentro do menu. A navegação de um site é uma lista de ligações dentro de `<nav>`. Solução: `<nav>` + `<ul>` + `<a>`. Um menu de navegação com submenus é um padrão de *disclosure*, não de `menu`.

**11. `aria-activedescendant` sem *scroll***
O leitor de ecrã anuncia a décima opção; o ecrã continua a mostrar a primeira. Solução: `scrollIntoView({ block: 'nearest' })`.

**12. `id` errado em `aria-activedescendant`, `aria-controls` ou `aria-labelledby`**
Falha em silêncio: sem erro, sem aviso, sem funcionalidade. Agrava-se em componentes repetidos na mesma página, onde os `id` colidem. Solução: gerar `id` únicos por instância e testar na árvore de acessibilidade.

**13. Estado visual e estado programático dessincronizados**
O separador está azul, mas `aria-selected="false"`. Duas verdades, uma para cada público. Solução: uma única fonte de verdade no código; a classe CSS e o atributo ARIA saem do mesmo sítio (por exemplo, estilizar com `[aria-selected="true"]` em vez de uma classe própria).

**14. Widget complexo para conteúdo que não precisa**
Três parágrafos em três separadores. Solução: três parágrafos.

**15. Componente que só foi testado com rato**
Passa em ferrramentas automáticas, e é inutilizável com teclado. As ferramentas automáticas não carregam em `Esc`. Solução: teste manual de teclado obrigatório antes de qualquer entrega.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Um widget complexo é uma orquestra, e a partitura já está escrita.** Os padrões do *ARIA Authoring Practices Guide* documentam estrutura, teclado e estados de cada componente. Inventar é assumir um risco que não é preciso.
2. **O componente mais acessível é o que não existe.** A seguir vem o nativo (`<dialog>`, `<details>`, `<select>`). Só depois vem o padrão do APG, copiado com fidelidade.
3. **Uma paragem de `Tab` por componente; setas lá dentro.** É a regra que separa um componente utilizável de um muro.
4. **Há duas formas de o fazer:** `tabindex` móvel (o foco anda) e `aria-activedescendant` (o foco fica e um ponteiro anda). A segunda só se justifica quando é preciso escrever e navegar ao mesmo tempo, e exige *scroll* programado.
5. **As relações têm de estar declaradas:** `aria-controls`, `aria-expanded` (sempre no controlo), `aria-haspopup` (com o valor que corresponde ao que abre) e, só em último recurso, `aria-owns`.
6. **A hierarquia de papéis não admite intrusos.** Um `div` de *layout* entre um `tablist` e os seus `tab` parte a relação em silêncio. `role="presentation"` resolve; não ter o `div` resolve melhor.
7. **Esconder é esconder para todos.** `hidden` para conteúdo que não está disponível; `inert` para conteúdo por trás de um modal. `opacity: 0` e `height: 0` criam fantasmas; `aria-hidden` com elementos focáveis lá dentro cria armadilhas.
8. **O diálogo modal nativo faz de graça o que custa centenas de linhas:** foco preso, `Esc`, inércia do fundo, devolução do foco. Use `<dialog>` com `showModal()`.
9. **Uma única fonte de verdade.** Se o aspeto visual e o atributo ARIA vierem de sítios diferentes do código, mais cedo ou mais tarde dizem coisas diferentes.
10. **`Esc` fecha. Sempre.**
11. **`role="menu"` não é para a navegação do site.** É para menus de aplicação.
12. **As ferramentas automáticas não testam widgets complexos.** Verificam atributos, não experiências. O teclado, a árvore de acessibilidade e um leitor de ecrã são o teste real.

### Exercícios Práticos

**Exercício 1 — Encontrar o intruso**
Analise o código abaixo e identifique **quatro** problemas distintos. Para cada um, explique o efeito concreto para uma pessoa que use leitor de ecrã e reescreva a linha.

```html
<div role="tablist">
  <div class="linha-flex">
    <div role="tab" aria-selected="true" tabindex="0">Dados</div>
    <div role="tab" aria-selected="false" tabindex="0">Anexos</div>
  </div>
</div>
<div role="tabpanel" style="height:0; overflow:hidden;">
  <a href="/anexo1.pdf">Descarregar anexo</a>
</div>
```

**Exercício 2 — Teclado às escuras**
Escolha um componente complexo de um sítio público (um menu, um acordeão, um seletor de datas). Desligue o rato (literalmente, se conseguir). Complete uma tarefa e registe numa tabela: chegou ao componente? Entrou? Navegou com setas ou com `Tab`? `Esc` fechou? Soube sempre onde estava o foco? Classifique cada resposta como «cumpre» / «não cumpre» e diga qual dos erros comuns desta secção explica cada falha.

**Exercício 3 — A escolha do padrão**
Para cada requisito, indique o padrão que usaria (ou se não usaria um widget) e justifique em duas linhas:
a) Perguntas frequentes com seis perguntas e respostas curtas.
b) Escolher um de 308 concelhos num formulário.
c) Escolher entre «Particular», «Empresa» e «Instituição pública».
d) Confirmar a eliminação definitiva de uma conta.
e) Mostrar a morada de faturação e a morada de entrega no mesmo espaço do ecrã.

**Exercício 4 — Traduzir para som**
Pegue no exemplo dos separadores da Técnica 3 e escreva, palavra por palavra, o que um leitor de ecrã anuncia nesta sequência: `Tab` → `→` → `→` → `Tab` → `Shift+Tab`. Depois apague `aria-labelledby` dos painéis e reescreva o guião. O que se perde?

**Exercício 5 — Reparar a árvore**
Abra as ferramentas de programador do seu navegador, separador de acessibilidade, e inspecione um conjunto de separadores num sítio real. Confirme: os `tab` são filhos diretos do `tablist` na árvore? O leitor de ecrã consegue contar? Se não, identifique o elemento intruso e proponha a correção.

**Exercício 6 — Do zero ao APG**
Implemente um acordeão de três painéis: botões com `aria-expanded` e `aria-controls`, painéis com `hidden`, cada botão dentro de um cabeçalho de nível adequado. Depois compare com o exemplo oficial do padrão *Accordion* do APG e liste as diferenças. Nota deliberada: repare que este padrão **não** usa setas nem `tabindex` móvel — cada botão é uma paragem de `Tab`. Explique porquê, à luz da regra do ponto 3 do resumo.

**Exercício 7 — Modal nativo contra modal caseiro**
Construa a mesma janela modal duas vezes: uma com `<dialog>` e `showModal()`; outra com um `<div>` e `role="dialog"`. Teste ambas só com teclado e conte quantas linhas de JavaScript foram precisas em cada caso para chegar ao mesmo comportamento. Apresente o resultado como argumento numa reunião de equipa.

**Exercício 8 — Auditoria de inventário**
Liste os widgets complexos de um produto que conheça. Para cada um, responda: existe um padrão do APG correspondente? Existe um elemento HTML nativo que faça o mesmo? É mesmo necessário? Proponha uma lista priorizada de três ações.

