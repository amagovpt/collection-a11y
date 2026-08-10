# Estruturas e Relações

## Introdução

Na secção anterior vimos **o que é uma aplicação rica** e porque é que ela levanta problemas de acessibilidade que um sítio Web tradicional não levanta: o conteúdo muda sem a página recarregar, vários painéis coexistem no mesmo ecrã, e grande parte do significado é comunicada por posição, por cor, por espaçamento e por caixas desenhadas com CSS.

Esta secção trata da primeira pergunta que qualquer pessoa faz quando chega a uma aplicação:

> **«O que é que existe aqui, e o que é que anda junto com o quê?»**

Para quem vê o ecrã, a resposta é imediata e inconsciente. O olho percebe, em menos de um segundo, que aquela barra em cima é o cabeçalho, que aquela coluna estreita à esquerda é o menu, que aqueles seis retângulos cinzentos são seis pedidos, e que aquele texto pequeno debaixo da caixa é uma explicação sobre a caixa e não um parágrafo solto.

Nada disto é evidente para quem não vê o ecrã. E nada disto é evidente para um leitor de ecrã, para um comando de voz ou para um sistema de ampliação. **A não ser que o código o diga.**

> ### Analogia central: a fotografia e a planta
>
> Imagine um edifício. Há duas maneiras de o conhecer.
>
> A primeira é ver uma **fotografia**: percebe-se logo onde ficam as janelas, onde está a porta, o que é grande e o que é pequeno.
>
> A segunda é ler a **planta**: uma folha onde estão marcadas as divisões, com o nome de cada uma («cozinha», «sala», «arrecadação»), a indicação de que móveis pertencem a que divisão e as legendas que dizem o que é cada coisa.
>
> Quando uma pessoa usa a aplicação com os olhos, está a ver a **fotografia**.
> Quando uma pessoa usa a aplicação com um leitor de ecrã, com voz ou com ampliação forte, está a receber a **planta**.
>
> O navegador constrói essa planta a partir do código. Chama-se **árvore de acessibilidade**.
>
> E daqui sai a regra que atravessa toda esta secção:
>
> **Se a parede só existe na fotografia e não na planta, para efeitos práticos aquela parede não existe.**

Uma divisória feita com uma sombra de CSS, um grupo criado com 24 píxeis de espaço em branco, um título feito com `<div class="titulo-grande">`, tudo isso aparece na fotografia e não aparece na planta. O trabalho desta secção é garantir que a planta é desenhada.

**O que esta secção trata:** regiões, cabeçalhos, agrupamentos e ligações explícitas entre elementos.

**O que esta secção não trata:** a *ordem* pela qual as coisas são lidas e a gestão do foco quando a aplicação muda — isso é a secção *Ordem de Leitura e Foco*; e o anúncio de alterações que acontecem sozinhas — isso é a secção *Notificações e Atualizações de Conteúdo*. 

---

### Como as Pessoas com Deficiência percebem as Estruturas e Relações de Aplicações Ricas

Uma aplicação rica costuma ter três características que agravam os problemas de estrutura:

1. **Muita coisa ao mesmo tempo no ecrã.** Um painel de gestão pode ter, em simultâneo, um menu, filtros, uma lista de resultados, um painel de detalhe e uma barra de estado.
2. **Densidade de repetição.** A mesma ação («Ver», «Editar», «Remover») aparece dezenas de vezes, uma vez por linha.
3. **Estrutura que muda sem a página mudar.** Um clique substitui metade do ecrã, e a planta antiga deixa de servir.

Vejamos como isto é sentido por diferentes pessoas, com base numa aplicação imaginária mas muito comum: um **gestor de pedidos** com menu lateral, filtros, uma lista de pedidos em cartões e um painel de detalhe à direita.

#### Pessoas cegas que usam leitor de ecrã

O leitor de ecrã lê **em série**: uma coisa de cada vez, do princípio para o fim. Ler um painel de gestão do princípio ao fim demoraria vários minutos.

Por isso ninguém trabalha assim. Quem usa leitor de ecrã com regularidade navega **por saltos**, usando a estrutura como um mapa: salta de região em região (tecla <kbd>D</kbd> no NVDA), de cabeçalho em cabeçalho (tecla <kbd>H</kbd>), de lista em lista (tecla <kbd>L</kbd>), ou abre uma lista de todos os cabeçalhos da página (<kbd>Insert</kbd>+<kbd>F7</kbd> no NVDA, rotor <kbd>VO</kbd>+<kbd>U</kbd> no VoiceOver).

**Quando a estrutura existe**, a Teresa entra na aplicação, salta para a região principal, vê que há cinco cabeçalhos («Filtros», «Pedidos por validar», «Detalhe do pedido»…), escolhe um e trabalha a partir dali. Trinta segundos.

**Quando a estrutura não existe**, tudo isto desaparece. A lista de cabeçalhos vem vazia, não há regiões para onde saltar, e a aplicação transforma-se numa sequência interminável de texto e botões sem hierarquia. A Teresa é obrigada a percorrer tudo com a seta para baixo, a decorar por onde ia, e a recomeçar do princípio sempre que alguma coisa muda.

E há um efeito mais subtil: **sem agrupamento, os elementos perdem o dono**. Numa lista de vinte cartões de pedido, se os cartões não estiverem agrupados, a Teresa ouve «Pedido 4711 — 250 euros — Ver — Editar — Remover — Pedido 4712 — 310 euros — Ver — Editar…» sem qualquer separação. Não é impossível de perceber, mas exige um esforço de memória constante para saber a que pedido pertence o «Remover» que está prestes a acionar. Com agrupamento, ouve «lista com 20 itens; item 1 de 20, Pedido 4711…».

#### Pessoas com baixa visão que usam ampliação

Quem trabalha com ampliação a 400% vê, de cada vez, uma pequena janela do ecrã, por vezes menos de um vigésimo da área total. É como ler um jornal através do tubo de um rolo de papel.

Nessas condições, **a proximidade visual deixa de funcionar**. Um rótulo que está 200 píxeis à esquerda do campo pode estar fora da janela ampliada. Uma caixa cinzenta que agrupa cinco controlos não se vê como caixa: vê-se um bocado de cinzento sem princípio nem fim.

O Miguel, que usa ampliação, depende de duas coisas: de **títulos frequentes e informativos**, que lhe dizem em que zona da aplicação está quando volta a olhar; e de que a informação relacionada esteja **perto**, no ecrã e no código. Quando o código exprime as relações (o rótulo pertence ao campo, a descrição pertence ao painel), o leitor de ecrã que ele usa em conjunto com a ampliação repõe o contexto que os olhos não alcançam.

#### Pessoas com limitações motoras que usam voz ou teclado

Quem comanda o computador por voz («Clicar em Guardar», «Mostrar números») ou com um número reduzido de teclas paga um custo por cada movimento. Uma estrutura bem feita reduz esse custo: permite dizer o equivalente a «ir para a região principal» em vez de premir <kbd>Tab</kbd> quarenta vezes para atravessar o menu.

Há também um problema específico de aplicações ricas: **elementos com o mesmo nome**. Se existirem quinze ligações com o texto «Ver detalhes», o comando de voz não tem forma de saber qual delas se pretende, e a pessoa fica dependente de contar números no ecrã. Dar nomes distintos, aproveitando a relação com o título do cartão, resolve o problema para toda a gente.

#### Pessoas com dificuldades cognitivas ou de atenção

Uma aplicação rica pede muito à memória de trabalho. Estrutura clara é, aqui, sobretudo uma questão de **redução de carga**: blocos identificados, títulos que dizem o que está dentro, organização que se mantém igual de vista para vista, e nada de hierarquias com sete níveis.

#### O que isto nos diz

Todas estas pessoas dependem da mesma coisa — **que a organização visível esteja escrita no código** — e cada uma consome essa organização de maneira diferente. Não é preciso desenhar quatro soluções: é preciso desenhar uma planta correta.

---

### Requisitos de Acessibilidade para transmitir Estruturas e Relações de Aplicações Ricas

Uma planta útil responde a quatro perguntas. Os requisitos desta secção organizam-se à volta delas.

| Pergunta | Requisitos |
|---|---|
| **Onde estou?** | R1, R2 |
| **O que há aqui?** | R3, R4 |
| **O que está junto?** | R5 |
| **O que se relaciona com o quê?** | R6, R7 |
| *(transversal)* | R8, R9 |

#### R1 — A aplicação está dividida em regiões identificáveis

O ecrã tem de estar mapeado em zonas com significado (cabeçalho, navegação, conteúdo principal, painéis complementares, rodapé), usando marcação que o navegador reconheça. Todo o conteúdo relevante deve pertencer a uma região; não deve haver conteúdo «solto» fora do mapa.

Isto é o que torna possível saltar blocos repetidos — o objetivo do critério **2.4.1 Ignorar Blocos (A)**.

#### R2 — Regiões do mesmo tipo têm nomes que as distinguem

Duas navegações, três regiões complementares ou quatro painéis do mesmo tipo só são úteis se tiverem nome. «Navegação» e «Navegação» não ajudam ninguém; «Principal» e «Categorias do catálogo» ajudam.

#### R3 — Existe uma hierarquia de cabeçalhos que reflete a organização real

Cada bloco com significado próprio tem um título, e os níveis de título exprimem a relação entre blocos: o que está dentro de quê. O nível é escolhido pela **hierarquia**, nunca pelo tamanho da letra.

Os títulos têm de ser descritivos — critério **2.4.6 Cabeçalhos e Etiquetas (AA)**. Utilizar cabeçalhos para organizar o conteúdo é ainda objeto do critério **2.4.10 Cabeçalhos de Secção (AAA)**: acima da linha exigida por lei em Portugal, mas uma prática que vale a pena adotar em aplicações complexas.

#### R4 — Painéis importantes são regiões nomeadas, não caixas anónimas

Numa aplicação, um painel de detalhe, uma área de resultados ou uma zona de filtros funcionam como divisões do edifício. Devem ser expostos como tal, com nome próprio.

#### R5 — Conjuntos de elementos são expostos como conjuntos

Se são dez pedidos, o código deve dizer que são dez itens de uma lista. Se são cinco opções de filtro que respondem à mesma pergunta, o código deve dizer que são um grupo com um rótulo comum. A quantidade e a pertença fazem parte da informação, não da decoração.

#### R6 — As relações entre elementos são explícitas

Um rótulo pertence a um campo. Uma descrição pertence a um painel. Um título dá nome ao cartão que encabeça. Um botão que expande alguma coisa está ligado ao que expande. Quando essa ligação existe apenas na disposição visual, tem de ser escrita no código.

#### R7 — Estruturas incompletas declaram a sua dimensão real

Em listas virtualizadas, paginação infinita ou árvores carregadas por níveis, o que está no DOM é apenas uma fatia. O código tem de declarar quantos itens existem no total e que posição ocupa cada um, para que a pessoa não fique com a ideia de que a lista tem oito elementos quando tem oitocentos.

#### R8 — A estrutura anunciada corresponde à estrutura vista

Não pode haver contradição entre a planta e a fotografia. Um cabeçalho de nível 2 que visualmente é o título principal, uma «lista» que visualmente é uma tabela, um grupo que na prática junta coisas sem relação — tudo isto confunde mais do que a ausência de marcação.

#### R9 — A estrutura mantém-se coerente quando a vista muda

Numa aplicação de página única, mudar de vista é o equivalente a mudar de página. A nova vista tem de ter a sua própria estrutura completa e coerente, e as regiões estáveis (menu, cabeçalho) devem manter-se onde estavam — o que se relaciona com o critério **3.2.3 Navegação Consistente (AA)**.

Todos estes requisitos assentam num único critério central: **1.3.1 Informação e Relações (nível A)** — *a informação, a estrutura e as relações transmitidas visualmente têm de poder ser determinadas programaticamente*. É o critério mais violado da norma, e é praticamente sempre por causa de estruturas que só existem no CSS.

O quadro completo de critérios, com níveis e enquadramento legal, está na secção final do módulo.

---

## Técnicas de Codificação

As técnicas seguintes estão ordenadas do mapa geral para o detalhe: primeiro as divisões do edifício, depois os letreiros, depois os grupos, depois as ligações entre peças.

### T1 — Desenhar o mapa com elementos nativos

O primeiro passo é substituir os `<div>` estruturais por elementos que o navegador já sabe interpretar.

**Mal:**

```html
<div class="topo">
  <img src="logo.svg" alt="Empresa">
</div>
<div class="menu-lateral">
  <a href="/pedidos">Pedidos</a>
  <a href="/clientes">Clientes</a>
</div>
<div class="conteudo">
  <div class="titulo-pagina">Gestor de Pedidos</div>
  <!-- ... -->
</div>
<div class="painel-lateral">
  <div class="titulo-painel">Atividade recente</div>
</div>
<div class="rodape">© 2026</div>
```

**Bem:**

```html
<header>
  <img src="logo.svg" alt="Empresa">
</header>

<nav aria-label="Principal">
  <ul>
    <li><a href="/pedidos">Pedidos</a></li>
    <li><a href="/clientes">Clientes</a></li>
  </ul>
</nav>

<main>
  <h1>Gestor de Pedidos</h1>
  <!-- ... -->
</main>

<aside aria-label="Atividade recente">
  <h2>Atividade recente</h2>
</aside>

<footer>© 2026</footer>
```

**O que muda:** no primeiro exemplo, a árvore de acessibilidade recebe cinco caixas genéricas — cinco divisões sem nome na planta. A Teresa prime <kbd>D</kbd> para saltar entre regiões e não acontece nada; não há regiões.

No segundo, o navegador expõe automaticamente cinco marcos de referência: `banner`, `navigation`, `main`, `complementary` e `contentinfo`. A Teresa passa a poder saltar diretamente para o conteúdo principal, e o Miguel — que usa comando de voz — consegue navegar por zonas em vez de percorrer a aplicação inteira.

**Cuidados a ter:**

- `<header>` e `<footer>` só produzem `banner` e `contentinfo` quando estão ao nível do `<body>`. Dentro de um `<article>` ou de uma `<section>`, são apenas cabeçalho e rodapé desse bloco — o que é correto, mas não são marcos de referência.
- Deve haver **um só** `<main>` visível de cada vez.
- Para a zona de pesquisa existe o elemento `<search>`; onde for preciso garantir compatibilidade com navegadores mais antigos, use `role="search"` num contentor:
  ```html
  <search>
    <label for="q">Pesquisar pedidos</label>
    <input id="q" type="search">
  </search>
  ```
- **Não exagere.** Uma aplicação com quinze marcos de referência é tão inútil como uma sem nenhum. Se tudo é importante, nada é importante.

### T2 — Dar nome às regiões repetidas

Assim que existe mais do que uma região do mesmo tipo, o nome deixa de ser opcional.

**Mal:**

```html
<nav>…menu principal…</nav>
<nav>…caminho de navegação…</nav>
<nav>…paginação dos resultados…</nav>
```

**Bem:**

```html
<nav aria-label="Principal">…</nav>
<nav aria-label="Percurso">…</nav>
<nav aria-label="Paginação dos resultados">…</nav>
```

**O que muda:** no primeiro caso, a lista de regiões do leitor de ecrã mostra «navegação, navegação, navegação» — três portas iguais sem placa. No segundo, mostra «navegação Principal», «navegação Percurso», «navegação Paginação dos resultados».

**Detalhe que se erra muito:** não escreva o tipo da região dentro do nome. Com `aria-label="Navegação principal"`, o leitor de ecrã anuncia «navegação, navegação principal». O papel já é dito pela própria região; o nome só precisa de dizer *qual*.

Quando já existe um título visível para a zona, prefira ligá-lo em vez de repetir o texto:

```html
<aside aria-labelledby="titulo-atividade">
  <h2 id="titulo-atividade">Atividade recente</h2>
  …
</aside>
```

Assim o nome nunca fica dessincronizado do que se vê no ecrã — um problema real quando a interface é traduzida ou reescrita.

### T3 — Cabeçalhos: o índice da aplicação

Os cabeçalhos são a estrutura de navegação mais usada por quem usa leitor de ecrã. Numa aplicação, o critério de escolha do nível é sempre o mesmo: **o que está dentro de quê**.

**Mal:**

```html
<h1>Gestor de Pedidos</h1>

<h4>Filtros</h4>            <!-- h4 porque a letra tinha de ser pequena -->
<div class="titulo-painel">Pedidos por validar</div>   <!-- nem sequer é cabeçalho -->
<h3>Detalhe do pedido</h3>
```

**Bem:**

```html
<h1>Gestor de Pedidos</h1>

<section aria-labelledby="h-filtros">
  <h2 id="h-filtros" class="titulo-painel">Filtros</h2>
  …
</section>

<section aria-labelledby="h-lista">
  <h2 id="h-lista" class="titulo-painel">Pedidos por validar</h2>
  <h3>Resultados de hoje</h3>
  …
</section>

<section aria-labelledby="h-detalhe">
  <h2 id="h-detalhe" class="titulo-painel">Detalhe do pedido</h2>
  …
</section>
```

```css
.titulo-painel {
  font-size: 1rem;
  font-weight: 600;
  text-transform: uppercase;
}
```

**O que muda:** no primeiro exemplo, a lista de cabeçalhos dá um salto de `h1` para `h4`, e o título «Pedidos por validar» pura e simplesmente não aparece — a lista de pedidos fica sem título na planta. No segundo, a lista de cabeçalhos lê-se como um índice: *Gestor de Pedidos → Filtros; Pedidos por validar → Resultados de hoje; Detalhe do pedido*. O aspeto visual é tratado por CSS, que é onde deve ser tratado.

**Teste rápido e barato:** escreva numa folha, por ordem, todos os cabeçalhos do ecrã com a respetiva indentação. Se aquilo não se parece com o índice de um relatório, a hierarquia está errada.

**Nota:** `role="heading"` com `aria-level` existe e funciona, mas só se justifica quando não é possível usar `<h1>`–`<h6>`. Um cabeçalho nativo traz o nível, o papel e o comportamento sem código adicional.

### T4 — Transformar painéis em regiões nomeadas

Uma `<section>` **sem nome acessível não é um marco de referência**: é apenas uma caixa. Com nome, passa a ser uma divisão da planta, com placa na porta.

**Mal:**

```html
<section class="painel-detalhe">
  <h2>Detalhe do pedido</h2>
  …
</section>
```

**Bem:**

```html
<section aria-labelledby="h-detalhe" class="painel-detalhe">
  <h2 id="h-detalhe">Detalhe do pedido</h2>
  …
</section>
```

**O que muda:** o cabeçalho, sozinho, permite saltar para o início do painel. Mas não diz onde é que o painel *acaba*, nem permite ao leitor de ecrã anunciar «saiu da região Detalhe do pedido». Com `aria-labelledby`, a `<section>` passa a `region` com nome, e o painel ganha fronteiras.

**Critério de bom senso:** promova a região apenas os blocos a que uma pessoa quereria voltar diretamente. Painéis de detalhe, áreas de resultados, zonas de filtros — sim. Cada cartão de uma lista de cinquenta — não; isso são itens de lista (T5).

### T5 — Agrupar o que anda junto: listas

Sempre que existirem vários elementos irmãos com a mesma natureza, o código deve dizê-lo.

**Mal:**

```html
<div class="grelha-pedidos">
  <div class="cartao">
    <div class="titulo">Pedido #4711</div>
    <p>250,00 €</p>
    <a href="/pedidos/4711">Ver detalhes</a>
  </div>
  <div class="cartao">…</div>
  <div class="cartao">…</div>
</div>
```

**Bem:**

```html
<ul class="grelha-pedidos">
  <li>
    <article aria-labelledby="p-4711">
      <h3 id="p-4711">Pedido #4711</h3>
      <p>250,00 €</p>
      <a href="/pedidos/4711" id="l-4711">Ver detalhes</a>
    </article>
  </li>
  <li>…</li>
  <li>…</li>
</ul>
```

**O que muda:** no primeiro exemplo, a Teresa ouve conteúdo em fila contínua e não sabe quantos pedidos existem nem onde acaba cada um. No segundo, ouve «lista com 3 itens» e, em cada item, «item 2 de 3». Ganha três informações que antes não tinha: **que é um conjunto**, **quantos são** e **onde está**.

O `<article>` com `aria-labelledby` não é obrigatório, mas é útil: dá ao cartão um nome próprio, o que permite a alguns leitores de ecrã anunciar de que cartão se trata ao entrar nele.

**Atenção à ordem de leitura:** a disposição em grelha é feita por CSS. Se a grelha reordenar visualmente os cartões, cria-se uma contradição entre a fotografia e a planta — problema tratado na secção *Ordem de Leitura e Foco*.

### T6 — Agrupar controlos relacionados

Quando vários controlos respondem em conjunto à mesma pergunta, o rótulo comum tem de estar ligado a todos eles.

**Mal:**

```html
<p class="rotulo-grupo">Estado do pedido</p>
<label><input type="checkbox" name="estado" value="novo"> Novo</label>
<label><input type="checkbox" name="estado" value="pago"> Pago</label>
<label><input type="checkbox" name="estado" value="enviado"> Enviado</label>
```

**Bem:**

```html
<fieldset>
  <legend>Estado do pedido</legend>
  <label><input type="checkbox" name="estado" value="novo"> Novo</label>
  <label><input type="checkbox" name="estado" value="pago"> Pago</label>
  <label><input type="checkbox" name="estado" value="enviado"> Enviado</label>
</fieldset>
```

**O que muda:** no primeiro caso, quem chega à caixa «Pago» pelo teclado ouve apenas «Pago, caixa de verificação, não assinalada». Pago o quê? O parágrafo com o rótulo do grupo ficou para trás e nunca mais é dito. No segundo, ouve «Estado do pedido, agrupamento — Pago, caixa de verificação, não assinalada». O contexto viaja com o controlo.

Quando não é possível usar `<fieldset>` (por exemplo, porque o estilo do componente o torna impraticável, ou porque os elementos agrupados não são campos de formulário), o equivalente em ARIA é:

```html
<div role="group" aria-labelledby="g-estado">
  <span id="g-estado">Estado do pedido</span>
  …
</div>
```

**Regra prática:** use `<fieldset>`/`<legend>` sempre que for viável, e `role="group"` como alternativa consciente — nunca por comodidade.

### T7 — Ligar elementos entre si por identificador

Há duas propriedades ARIA que servem para escrever no código relações que existem no ecrã:

- **`aria-labelledby`** — «o nome deste elemento está *ali*».
- **`aria-describedby`** — «a explicação adicional deste elemento está *ali*».

O caso mais rentável numa aplicação rica é o das ações repetidas.

**Mal:**

```html
<h3>Pedido #4711</h3>
<a href="/pedidos/4711">Ver detalhes</a>
…
<h3>Pedido #4712</h3>
<a href="/pedidos/4712">Ver detalhes</a>
```

**Bem:**

```html
<h3 id="p-4711">Pedido #4711</h3>
<a href="/pedidos/4711" id="l-4711"
   aria-labelledby="l-4711 p-4711">Ver detalhes</a>

<h3 id="p-4712">Pedido #4712</h3>
<a href="/pedidos/4712" id="l-4712"
   aria-labelledby="l-4712 p-4712">Ver detalhes</a>
```

**O que muda:** a lista de ligações do leitor de ecrã deixa de mostrar vinte entradas idênticas e passa a mostrar «Ver detalhes Pedido #4711», «Ver detalhes Pedido #4712»… E quem usa comando de voz passa a poder identificar a ligação pretendida.

**Dois pormenores importantes:**

1. `aria-labelledby` aceita vários identificadores, e o nome final é a concatenação **pela ordem em que estão escritos**. Colocar primeiro o identificador do próprio elemento faz com que o texto visível («Ver detalhes») continue a ser o começo do nome. Isto importa para quem usa comando de voz: o nome acessível tem de conter o texto que se vê.
2. `aria-labelledby` **substitui** o conteúdo do elemento como nome, e `aria-label` substitui tudo. São instrumentos poderosos e destrutivos: se apontarem para um identificador que não existe, o elemento fica sem nome.

Para descrições, o padrão é o mesmo:

```html
<label for="ref">Referência interna</label>
<input id="ref" type="text" aria-describedby="ajuda-ref">
<p id="ajuda-ref">Formato: três letras seguidas de quatro dígitos.</p>
```

Sem `aria-describedby`, aquele parágrafo é apenas texto que está por baixo — na planta, não pertence a ninguém.

### T8 — Relacionar um comando com o conteúdo que ele controla

Em painéis expansíveis, acordeões e menus, existe uma relação entre **o botão** e **a área que ele abre**.

```html
<h3>
  <button type="button"
          aria-expanded="false"
          aria-controls="painel-envio"
          id="botao-envio">
    Dados de envio
  </button>
</h3>
<div id="painel-envio" hidden>
  …
</div>
```

**O que funciona bem:** `aria-expanded` comunica o estado (fechado/aberto) e é bem suportado por todas as tecnologias de apoio relevantes. Colocar o botão dentro de um cabeçalho mantém a área expansível dentro do índice da aplicação. E colocar o painel **imediatamente a seguir** ao botão no DOM cria a relação mais fiável de todas: a proximidade.

**O que é preciso saber sobre `aria-controls`:** o suporte é irregular. Alguns leitores de ecrã oferecem um atalho para saltar para o elemento controlado; outros ignoram completamente o atributo. Por isso: use-o, porque documenta a intenção e ajuda onde é suportado, mas **nunca conte com ele como única forma de exprimir a relação**.

**E `aria-owns`?** Serve para dizer «este elemento, apesar de estar noutro sítio do DOM, é filho deste». É a saída de emergência para casos em que o painel é desenhado no fim do `<body>` (padrão comum em bibliotecas de componentes que usam *portals*). Duas advertências: o suporte é desigual, e o atributo reordena a árvore de acessibilidade sem reordenar o foco, o que pode criar uma incoerência nova. **Corrigir o DOM é quase sempre melhor do que remendá-lo com `aria-owns`.**

### T9 — Estruturas parciais: declarar a dimensão real

Listas virtualizadas e carregamento progressivo são a norma em aplicações ricas. O problema é que o DOM passa a conter uma fatia, e a planta passa a mentir sobre o tamanho do edifício.

**Mal:**

```html
<ul>
  <li>Pedido #4711</li>
  <li>Pedido #4712</li>
  <li>Pedido #4713</li>
</ul>
<!-- na realidade existem 240 pedidos; só 3 estão no DOM -->
```

**Bem:**

```html
<ul aria-label="Pedidos">
  <li aria-setsize="240" aria-posinset="97">Pedido #4711</li>
  <li aria-setsize="240" aria-posinset="98">Pedido #4712</li>
  <li aria-setsize="240" aria-posinset="99">Pedido #4713</li>
</ul>
```

**O que muda:** sem estes atributos, o leitor de ecrã anuncia «lista com 3 itens, item 1 de 3» — e a Teresa conclui, com toda a lógica, que a pesquisa devolveu três pedidos. Com eles, ouve «item 97 de 240»: sabe que a lista é grande e sabe onde está dentro dela.

É o equivalente a um livro com páginas numeradas: mesmo que só se tenha três folhas na mão, a numeração diz que fazem parte de um conjunto maior.

**Uso relacionado:** `aria-level` cumpre um papel semelhante em estruturas em árvore (`role="treeitem"`), declarando a profundidade de cada nó quando os níveis são carregados a pedido.

**Cuidado:** estes atributos são uma declaração de honra. Se os números estiverem errados ou desatualizados, a informação passa a ser pior do que a ausência dela.

### T10 — Não deixar o CSS apagar a estrutura

Há decisões de estilo que, sem qualquer aviso, removem semântica do código.

**Caso 1 — listas sem marcadores.** Em Safari com VoiceOver, aplicar `list-style: none` a uma lista faz com que ela deixe de ser anunciada como lista (é um comportamento intencional do motor, pensado para listas usadas apenas como recurso de layout).

```css
/* Risco: a lista deixa de ser anunciada como lista no Safari */
.grelha-pedidos { list-style: none; }
```

```html
<!-- Solução: reafirmar o papel -->
<ul class="grelha-pedidos" role="list">
```

**Caso 2 — `display: contents`.** Este valor remove a caixa do elemento para efeitos de layout, o que é muito conveniente em grelhas CSS. Historicamente, também removia o elemento da árvore de acessibilidade. Os navegadores foram corrigindo o problema, mas o comportamento continua a variar consoante o elemento e a versão — sobretudo em tabelas e listas.

```css
/* Verificar sempre na árvore de acessibilidade */
.linha { display: contents; }
```

**O que isto nos ensina:** a estrutura não se dá por garantida só porque a marcação está correta. **Marcação correta + verificação na árvore de acessibilidade** é o padrão de trabalho (ver T12).

Nota de fronteira: o CSS também pode alterar a *ordem* de leitura (`order`, `flex-direction: row-reverse`, posicionamento em grelha). Esse problema pertence à secção *Ordem de Leitura e Foco*.

### T11 — Manter a estrutura coerente quando a vista muda

Numa aplicação de página única, navegar não recarrega nada: substitui-se conteúdo. É aqui que as plantas se estragam.

```js
function mostrarVista(vista) {
  const principal = document.querySelector('main');

  // 1. O conteúdo novo traz a sua própria estrutura completa
  principal.innerHTML = vista.html;   // inclui <h1> e secções nomeadas

  // 2. O título do documento acompanha a vista
  document.title = `${vista.titulo} — Gestor de Pedidos`;

  // 3. O menu, o cabeçalho e o rodapé não são tocados
}
```

**O que funciona bem:**

- Cada vista tem **um** `<h1>` que diz onde a pessoa está, e a sua própria hierarquia de cabeçalhos por baixo.
- O `<title>` do documento é atualizado. Para quem usa leitor de ecrã, é frequentemente a primeira coisa lida quando se muda de contexto, e é o que aparece no separador do navegador.
- As regiões estáveis mantêm-se no mesmo sítio, com os mesmos nomes.

**Erros típicos desta situação:**

- Deixar no DOM a estrutura da vista anterior, escondida com CSS mas ainda presente na árvore de acessibilidade — passando a haver dois `<h1>` e dois «Detalhe do pedido».
- Acumular vários `<main>`.
- Substituir o conteúdo e deixar o `<title>` original de quando a aplicação arrancou.

Para esconder mesmo, use `hidden` ou `display: none`, e não apenas opacidade ou posicionamento fora do ecrã.

**Fronteira:** *para onde vai o foco* depois de mudar de vista, e *como é que a pessoa é avisada* de que a vista mudou, são tratados nas secções *Ordem de Leitura e Foco* e *Notificações e Atualizações de Conteúdo*, respetivamente.

### T12 — Inspecionar a árvore de acessibilidade

A estrutura é invisível: não se confirma a olho. Três formas rápidas de a ver:

1. **Nas ferramentas de programação do navegador** — no separador de acessibilidade é possível ver a árvore completa (papéis, nomes e relações) tal como é entregue à tecnologia de apoio. É a maneira mais direta de descobrir que aquela `<section>` afinal é uma caixa genérica.
2. **Com um leitor de ecrã** — no NVDA, <kbd>Insert</kbd>+<kbd>F7</kbd> abre a lista de elementos (cabeçalhos, ligações, marcos de referência). No VoiceOver, <kbd>VO</kbd>+<kbd>U</kbd> abre o rotor. Se a lista de cabeçalhos não parecer um índice, o problema está no código.
3. **Com validadores automáticos** — o AccessMonitor sinaliza problemas de estrutura como saltos de nível de cabeçalho, ausência de `<h1>` ou marcos de referência em falta. Detetam uma parte do problema, não o problema todo: nenhum validador sabe se «Painel 3» é um bom nome.

**Uma regra que vale por muitas verificações:** desligue o CSS da página. O que sobra é, aproximadamente, o que a Teresa recebe. Se o resultado for um bloco indistinto de texto e ligações, não é o CSS que está a ajudar — é o CSS que estava a esconder a falta de estrutura.

---

## Recomendações para Conteúdo Acessível

A estrutura não é só um problema de programação. Muitas das decisões que a determinam são tomadas antes de existir código.

**Para quem desenha a interface**

- **Anote a estrutura nas maquetas.** Marque no desenho quais são as regiões, que nome tem cada uma e qual é o nível de cada título. Uma maqueta que só indica tamanhos de letra obriga a equipa de desenvolvimento a adivinhar hierarquias — e a adivinhação sai quase sempre errada.
- **Não comunique agrupamento apenas por proximidade, moldura ou cor.** Se um conjunto de controlos anda junto, dê-lhe um título visível. Ganha a Teresa, que passa a ter um rótulo de grupo, e ganha o Miguel, que com ampliação a 400% deixa de ter de adivinhar onde começa e acaba a caixa cinzenta.
- **Dê título a todos os painéis.** Um painel sem título é uma divisão sem placa na porta. Se o desenho não comporta um título visível, é um sinal de alerta — e não uma justificação para o omitir.
- **Limite a profundidade.** Uma hierarquia com mais de quatro níveis é difícil de manter e difícil de percorrer. Se precisa de `h6`, provavelmente precisa de repensar a organização.
- **Mantenha a mesma organização entre vistas.** Se os filtros estão à esquerda numa vista, devem estar à esquerda nas outras. A consistência reduz a carga cognitiva e é um requisito das WCAG (**3.2.3 Navegação Consistente**, AA).

**Para quem escreve os textos**

- **Escreva títulos que funcionem fora de contexto.** Um título é frequentemente ouvido isolado, numa lista de cabeçalhos, sem nada à volta. «Pedidos por validar» funciona; «Aqui» não; «Secção 3» não.
- **Use nomes iguais para coisas iguais.** Se um botão se chama «Guardar» numa vista, não lhe chame «Submeter» noutra — é o critério **3.2.4 Identificação Consistente (AA)**, e é também simples bom senso.
- **Torne únicos os textos que se repetem.** Vinte «Ver detalhes» são vinte problemas. Se o texto visível tiver de se repetir, resolva-se com a técnica T7.
- **Não use cabeçalhos como decoração,** nem texto a negrito como cabeçalho. As duas coisas produzem o mesmo tipo de erro: uma planta que não corresponde ao edifício.

**Para quem toma decisões sobre o produto**

- **Escolha a estrutura certa para os dados.** Uma matriz de dados com colunas comparáveis é uma tabela; forçá-la a cartões destrói as relações entre coluna e valor. Um conjunto de itens independentes é uma lista; forçá-lo a tabela cria relações que não existem.
- **Inclua a estrutura na definição de «pronto».** Uma funcionalidade só está concluída quando a lista de cabeçalhos faz sentido, as regiões têm nome e a árvore de acessibilidade foi vista pelo menos uma vez.

---

### Erros Comuns

**1. A aplicação inteira feita de `<div>`.** Nenhuma região, nenhum cabeçalho, nenhuma lista.
*Solução:* mapear as zonas com elementos nativos (T1) antes de qualquer outra coisa.

**2. Escolher o nível do cabeçalho pelo tamanho da letra.** Um `h4` porque o `h2` era grande demais.
*Solução:* o nível exprime hierarquia; o tamanho é CSS (T3).

**3. Várias `<nav>` sem nome.** Três portas iguais, sem placa.
*Solução:* `aria-label` distinto em cada uma (T2).

**4. Escrever o tipo da região no nome.** `aria-label="Navegação principal"` numa `<nav>` produz «navegação, navegação principal».
*Solução:* o nome diz *qual*, não *o quê*.

**5. `<section>` sem nome acessível.** Julga-se ter criado uma região; criou-se uma caixa genérica.
*Solução:* `aria-labelledby` a apontar para o título do painel (T4).

**6. Excesso de marcos de referência.** Doze regiões numa vista tornam a navegação por regiões inútil.
*Solução:* promover a região só os blocos a que se quereria voltar diretamente.

**7. Listas de cartões feitas com `<div>`.** Perde-se a contagem, a pertença e a posição.
*Solução:* `<ul>`/`<li>` reais (T5).

**8. Rótulo de grupo num parágrafo solto.** «Estado do pedido» escrito acima das caixas de verificação, sem ligação nenhuma.
*Solução:* `<fieldset>`/`<legend>` ou `role="group"` com `aria-labelledby` (T6).

**9. `aria-labelledby` a apontar para identificadores inexistentes ou duplicados.** O elemento fica sem nome, ou com o nome errado — e o erro é silencioso.
*Solução:* verificar na árvore de acessibilidade (T12); garantir identificadores únicos, sobretudo em componentes repetidos, onde é fácil gerar duplicados.

**10. Confiar em `aria-controls` para exprimir a relação.** O suporte é irregular e, sozinho, o atributo não garante nada.
*Solução:* colocar o painel imediatamente a seguir ao botão no DOM e usar `aria-expanded` para o estado (T8).

**11. Listas virtualizadas que mentem sobre o tamanho.** «Item 1 de 3» quando existem 240 resultados.
*Solução:* `aria-setsize` e `aria-posinset`, mantidos atualizados (T9).

**12. Estrutura da vista anterior deixada no DOM.** Dois `<h1>`, dois `<main>`, cabeçalhos fantasma na lista de elementos.
*Solução:* remover ou esconder com `hidden`, nunca com opacidade ou posicionamento fora do ecrã (T11).

**13. ARIA aplicado por precaução.** `role="region"` em tudo, `role="list"` em elementos que não têm itens, `role="group"` a envolver coisas sem relação.
*Solução:* ARIA descreve o que existe; não cria estrutura por magia. Um papel errado é pior do que papel nenhum, porque produz uma planta que contradiz o edifício.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A tecnologia de apoio não recebe a fotografia da aplicação: recebe a **planta** que o código produz — a árvore de acessibilidade. **Uma parede que só existe no CSS não existe.**
- Quem usa leitor de ecrã navega **por saltos**, apoiando-se em regiões, cabeçalhos e listas. Sem estrutura, não há saltos: só há a seta para baixo.
- **Regiões** dão o mapa da aplicação; devem cobrir todo o conteúdo relevante, ser poucas, e ser criadas com elementos nativos (`header`, `nav`, `main`, `aside`, `footer`, `search`).
- **Regiões repetidas precisam de nome.** O nome diz *qual*, não repete o tipo.
- **Os cabeçalhos são o índice.** O nível exprime hierarquia, nunca o tamanho da letra. Se a lista de cabeçalhos não se lê como um índice, a estrutura está errada.
- Uma **`<section>` só é uma região quando tem nome acessível**; sem nome, é uma caixa genérica.
- **Conjuntos expõem-se como conjuntos:** listas para itens repetidos, `fieldset`/`legend` ou `role="group"` para controlos que respondem à mesma pergunta. Quantidade e posição são informação.
- **Relações exprimem-se por identificador:** `aria-labelledby` para o nome, `aria-describedby` para a explicação. Em ações repetidas, é o que transforma vinte «Ver detalhes» iguais em vinte ligações distinguíveis.
- **`aria-expanded` é fiável; `aria-controls` não é.** A relação mais robusta entre um botão e o painel que ele abre continua a ser a proximidade no DOM. `aria-owns` é último recurso.
- **Estruturas parciais têm de declarar a sua dimensão real** com `aria-setsize` e `aria-posinset` — e os números têm de estar certos.
- **O CSS pode apagar semântica** (`list-style: none` no Safari, `display: contents`). Marcação correta não dispensa verificação.
- **Mudar de vista é mudar de página:** nova hierarquia de cabeçalhos completa, `<title>` atualizado, regiões estáveis intactas, estrutura antiga removida.
- Tudo isto assenta num único critério: **1.3.1 Informação e Relações (A)**. É o critério mais falhado da norma, e falha quase sempre pela mesma razão — a organização ficou só no aspeto visual.

---

### Exercícios Práticos

**Exercício 1 — Diagnóstico de código**

Analise o excerto seguinte e identifique **seis** problemas distintos de estrutura ou de relações. Para cada um, escreva: (a) qual é o problema, (b) o que é que a Teresa, cega e a usar NVDA, perde por causa dele, (c) a correção.

```html
<div class="topo">
  <div class="titulo">Gestor de Pedidos</div>
  <div class="menu">
    <a href="/pedidos">Pedidos</a>
    <a href="/clientes">Clientes</a>
  </div>
</div>

<div class="conteudo">
  <h3>Filtros</h3>
  <p class="rotulo">Estado</p>
  <label><input type="checkbox"> Novo</label>
  <label><input type="checkbox"> Pago</label>

  <h2>Resultados</h2>
  <div class="grelha">
    <div class="cartao">
      <div class="titulo-cartao">Pedido #4711</div>
      <a href="/pedidos/4711">Ver</a>
    </div>
    <div class="cartao">
      <div class="titulo-cartao">Pedido #4712</div>
      <a href="/pedidos/4712">Ver</a>
    </div>
  </div>
</div>
```

**Exercício 2 — Desenhar a planta**

Escolham uma aplicação Web que ambos usem com regularidade (correio eletrónico, banco, plataforma de gestão interna).

1. Desenhem numa folha o mapa de regiões que a aplicação **deveria** ter, com o nome de cada uma.
2. Escrevam a lista de cabeçalhos que **deveria** existir, com os níveis indentados.
3. Abram a aplicação, usem as ferramentas de programação para inspecionar a árvore de acessibilidade e comparem com o que desenharam.
4. Anotem as três diferenças mais graves.

**Exercício 3 — Reconstrução**

Reescreva o código do Exercício 1 de raiz, aplicando as técnicas T1 a T7. Requisitos mínimos:

- todas as zonas dentro de marcos de referência;
- hierarquia de cabeçalhos coerente, com um só `h1`;
- painéis expostos como regiões nomeadas;
- cartões numa lista real;
- filtros agrupados com rótulo comum;
- ligações «Ver» distinguíveis umas das outras.

**Exercício 4 — Teste com leitor de ecrã**

Na sua reconstrução do Exercício 3:

1. Abra a lista de elementos do NVDA (<kbd>Insert</kbd>+<kbd>F7</kbd>) ou o rotor do VoiceOver (<kbd>VO</kbd>+<kbd>U</kbd>).
2. Verifique as três listas: cabeçalhos, marcos de referência e ligações.
3. Responda: consegue perceber a organização da aplicação **apenas** a partir dessas três listas, sem olhar para o ecrã?
4. Se a resposta for não, identifique o que falta e corrija.

**Exercício 5 — Listas virtualizadas**

Uma lista de resultados carrega 20 itens de cada vez, num total de 347. O código atual é:

```html
<ul id="resultados">
  <li>…item…</li>
  <!-- ×20 -->
</ul>
```

1. Acrescente os atributos necessários para que a dimensão real seja anunciada.
2. Escreva, em pseudocódigo, a função que atualiza esses atributos quando são carregados mais 20 itens.
3. Explique, em duas frases, o que acontece se os valores de `aria-setsize` ficarem desatualizados após uma nova pesquisa.

**Exercício 6 — Do desenho ao código**

Peguem numa maqueta de uma vista da vossa aplicação (ou desenhem uma vista com cabeçalho, menu, filtros, lista de resultados e painel de detalhe) e produzam um **documento de anotação de estrutura** com:

- a lista de marcos de referência e o nome de cada um;
- a hierarquia de cabeçalhos, com níveis;
- os agrupamentos, e como cada um vai ser marcado;
- as relações a exprimir com `aria-labelledby` ou `aria-describedby`.

Troquem o documento com outro grupo. Cada grupo deve conseguir escrever a marcação a partir do documento do outro, sem fazer perguntas. As perguntas que tiverem de ser feitas são exatamente aquilo que falta na anotação.

**Exercício 7 — Auditoria de mudança de vista**

Numa aplicação de página única à sua escolha:

1. Registe a lista de cabeçalhos e o `<title>` na vista inicial.
2. Navegue para outra vista sem recarregar a página.
3. Volte a registar as duas coisas.
4. Verifique: o `<title>` mudou? Existe um `h1` novo e apropriado? Sobraram cabeçalhos da vista anterior? Existe mais do que um `<main>`?
5. Escreva um relatório de meia página com os resultados e as correções recomendadas.

