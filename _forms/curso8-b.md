# Estrutura e Posicionamento

## Introdução

Quando falamos de **estrutura e posicionamento** de um formulário, estamos a considerar aspetos que podem parecer básicos e são, muitas vezes, invisíveis a olho nu: **a ordem pela qual os campos aparecem, a forma como estão agrupados e o sítio onde estão colocados no ecrã**.

Pense num formulário como se fosse a arrumação de uma cozinha. Pode ter os melhores utensílios do mundo (bons rótulos, boas instruções), mas se as facas estiverem na casa de banho e o sal ao lado da máquina de lavar, cozinhar torna-se um pesadelo. A estrutura e o posicionamento são a "arrumação" do formulário: aquilo que faz com que cada coisa esteja no sítio certo, na ordem certa e junto das coisas com que se relaciona.

Um pormenor central, que vamos repetir várias vezes porque é decisivo: **aquilo que se vê no ecrã e aquilo que está escrito no código nem sempre são a mesma coisa**. Com CSS é possível mover visualmente os campos para qualquer lado. Mas muitas pessoas com deficiência não "veem" o formulário. Recebem-no na ordem em que está escrito no código. Se as duas ordens não coincidirem, o formulário parte-se para estas pessoas.

### Como as Pessoas com Deficiência dependem da Estrutura e Posicionamento dos Formulários

Diferentes pessoas "leem" um formulário de maneiras muito diferentes. A estrutura e o posicionamento afetam cada uma delas de forma distinta.

**Pessoas cegas que usam leitores de ecrã** percorrem o formulário **de forma linear**, um elemento de cada vez, pela ordem em que está no código; não pela ordem em que está no ecrã. É como ouvir um audiolivro: ouve-se palavra a palavra, do princípio para o fim, sem poder "dar uma vista de olhos" à página toda. Se o código disser primeiro "Código Postal" e só depois "Morada", é essa a ordem que a pessoa ouve, mesmo que no ecrã a morada apareça em cima.

> **Analogia:** Imagine um livro cujas páginas foram encadernadas fora de ordem. Visualmente, alguém a folhear depressa pode até saltar para a página certa. Mas quem lê o livro do princípio ao fim, página a página, vai encontrar o capítulo 5 antes do capítulo 2. O leitor de ecrã lê "página a página" (elemento a elemento) na ordem do código.

**Pessoas que navegam só com o teclado** (por não usarem rato, por deficiência motora ou por preferência) movem-se entre campos com a tecla **Tab**. Dependem totalmente da **ordem de foco** ser previsível: carregar em Tab deve levar ao campo seguinte "lógico", não a um campo aleatório no outro extremo do ecrã. Se a ordem saltar de forma imprevisível, a pessoa perde-se e pode nem sequer chegar a alguns campos.

**Pessoas com baixa visão** ampliam frequentemente o conteúdo (por vezes 200%, 400% ou mais). Com muita ampliação, um formulário em duas ou três colunas obriga a andar constantemente para a esquerda e para a direita para ler cada linha, como tentar ler um jornal em papel A3 através de uma lupa pequena. A estrutura tem de **adaptar-se** (fazer *reflow*) a uma única coluna estreita.

**Pessoas com deficiência cognitiva ou de atenção** beneficiam enormemente de campos **agrupados** por assunto e de um posicionamento **previsível e consistente**. Um formulário onde os campos relacionados estão juntos e bem separados dos restantes reduz a sobrecarga mental. Um formulário com campos relacionados espalhados, aumenta a confusão e os erros.

**Pessoas com deficiência motora** que usam o rato, um ecrã tátil ou apontadores dependem dos campos e botões estarem **suficientemente espaçados e com tamanho suficiente**. Botões colados uns aos outros levam a toques errados — carrega-se em "Cancelar" quando se queria "Submeter".

### Requisitos de Acessibilidade para Estrutura e Posicionamento de Formulários

Traduzindo o que vimos acima em requisitos concretos, um formulário bem estruturado e posicionado deve:

1. **Ter uma ordem no código que faça sentido quando lida sequencialmente.** Se lermos o formulário do primeiro ao último elemento, sem ver o ecrã, a sequência tem de continuar a ter lógica. (Relaciona-se com o critério WCAG 1.3.2 *Sequência com Significado*.)

2. **Ter uma ordem de foco (Tab) previsível.** Carregar em Tab deve percorrer os campos numa ordem lógica, normalmente a mesma que a leitura visual. (WCAG 2.4.3 *Ordem de Foco*.)

3. **Garantir que a ordem visual e a ordem do código coincidem.** O que se vê e o que está no código devem contar a mesma história. Não usar CSS para reorganizar visualmente os campos de forma que contradiga o código.

4. **Agrupar campos relacionados.** Campos que respondem à mesma pergunta (por exemplo, um conjunto de botões de opção) ou que pertencem ao mesmo tema (por exemplo, todos os campos da morada) devem estar agrupados de forma percetível — visual e programaticamente. (WCAG 1.3.1 *Informação e Relações*.)

5. **Adaptar-se à ampliação e a ecrãs pequenos** (*reflow*), sem obrigar a deslocar horizontalmente. (WCAG 1.4.10 *Reflow*.)

6. **Colocar cada elemento junto daquilo a que diz respeito** (proximidade). O rótulo junto do campo, o texto de ajuda junto do campo, o botão de submeter no fim.

7. **Não depender apenas da posição no ecrã** para transmitir informação. Instruções como "preencha os campos da coluna da direita" excluem quem não vê a disposição. (WCAG 1.3.3 *Características Sensoriais*.)

8. **Ter alvos suficientemente grandes e espaçados.** Campos e botões interativos devem ter dimensão e espaçamento que evitem toques ou cliques acidentais. (WCAG 2.5.8 *Tamanho do Alvo (Mínimo)*.)

## Técnicas de Codificação

Vejamos como pôr estes requisitos em prática no código. Em cada exemplo mostramos primeiro o problema e depois a solução, com uma explicação do que corre bem ou mal.

### 1. A ordem no código deve ser a ordem lógica

A regra de ouro é simples: **escreva os campos no código pela ordem em que quer que sejam preenchidos.** Não confie no CSS para "consertar" a ordem depois.

**Exemplo problemático** — usar CSS para trocar a ordem visual:

```html
<style>
  .campos { display: flex; flex-direction: column; }
  .morada    { order: 1; }
  .nome      { order: 2; }  /* visualmente aparece a seguir à morada */
</style>

<div class="campos">
  <div class="nome">
    <label for="nome">Nome</label>
    <input id="nome" type="text">
  </div>
  <div class="morada">
    <label for="morada">Morada</label>
    <input id="morada" type="text">
  </div>
</div>
```

**O que corre mal:** No ecrã, a "Morada" aparece antes do "Nome" (por causa da propriedade `order` do CSS). Mas no código o "Nome" vem primeiro. Um leitor de ecrã e a navegação por teclado seguem o **código**, não o CSS: leem "Nome" e depois "Morada". A pessoa que vê e a pessoa que ouve recebem ordens diferentes — e a ordem de foco deixa de acompanhar a ordem visual. As propriedades `order` e `flex-direction: row-reverse` são muito úteis para *layout*, mas tornam-se armadilhas quando alteram a sequência de leitura.

**Exemplo correto** — a ordem visual e a ordem do código são iguais:

```html
<div class="campos">
  <div>
    <label for="nome">Nome</label>
    <input id="nome" type="text">
  </div>
  <div>
    <label for="morada">Morada</label>
    <input id="morada" type="text">
  </div>
</div>
```

**O que corre bem:** O "Nome" vem primeiro no código e primeiro no ecrã. A "Morada" vem a seguir em ambos. Toda a gente — quem vê, quem ouve e quem usa só o teclado — recebe a mesma sequência. Se precisar de um *layout* diferente, reorganize a **ordem do HTML** para que já esteja certa, e use o CSS apenas para o aspeto (margens, cores, alinhamento), não para trocar a sequência.

> **Como testar rapidamente:** desligue o CSS da página (ou leia só o código HTML de cima para baixo). Se a ordem continuar a fazer sentido, está bem. Se ficar baralhada, há um problema de sequência.

### 2. Agrupar campos relacionados com `<fieldset>` e `<legend>`

Quando vários campos respondem em conjunto à mesma pergunta — o caso clássico dos botões de opção e das caixas de verificação — é preciso agrupá-los. Em HTML isso faz-se com `<fieldset>` (a "caixa" que agrupa) e `<legend>` (o título dessa caixa).

**Exemplo problemático** — opções soltas, sem grupo:

```html
<p>Como prefere ser contactado?</p>
<input type="radio" name="contacto" id="email" value="email">
<label for="email">Email</label>
<input type="radio" name="contacto" id="telefone" value="telefone">
<label for="telefone">Telefone</label>
```

**O que corre mal:** Visualmente até percebemos que a pergunta "Como prefere ser contactado?" se refere às duas opções, porque está logo por cima. Mas para o leitor de ecrã essa relação não existe: a pergunta é um simples parágrafo solto, sem ligação aos botões. Quem navega campo a campo pode chegar diretamente ao botão "Email" e ouvir apenas "Email, botão de opção", sem nunca ouvir a pergunta a que está a responder.

> **Analogia:** É como ouvir alguém a dizer "Sim" ou "Talvez" sem termos ouvido a pergunta. A resposta, sozinha, não significa nada.

**Exemplo correto** — grupo com `<fieldset>` e `<legend>`:

```html
<fieldset>
  <legend>Como prefere ser contactado?</legend>
  <input type="radio" name="contacto" id="email" value="email">
  <label for="email">Email</label>
  <input type="radio" name="contacto" id="telefone" value="telefone">
  <label for="telefone">Telefone</label>
</fieldset>
```

**O que corre bem:** O `<fieldset>` cria um grupo real e o `<legend>` funciona como o "título" desse grupo. Agora, quando a pessoa chega a qualquer uma das opções, o leitor de ecrã anuncia algo como "Como prefere ser contactado? Email, botão de opção, 1 de 2". A pergunta e as respostas ficam ligadas de forma percetível para toda a gente. Por omissão, o navegador ainda desenha uma moldura à volta do grupo, o que reforça visualmente que aquelas opções andam juntas (esse aspeto pode ser ajustado com CSS sem quebrar a semântica).

Este agrupamento também é útil para **secções temáticas** — por exemplo, agrupar todos os campos de "Dados de faturação" num `<fieldset>` e todos os de "Dados de entrega" noutro. Assim, tanto quem vê como quem ouve percebe onde começa e acaba cada bloco.

### 3. Não usar tabelas para posicionar campos

Um erro antigo, mas ainda comum, é usar tabelas HTML (`<table>`) só para alinhar campos em colunas e linhas.

**Exemplo problemático:**

```html
<table>
  <tr>
    <td><label for="nome">Nome</label></td>
    <td><input id="nome" type="text"></td>
  </tr>
  <tr>
    <td><label for="email">Email</label></td>
    <td><input id="email" type="text"></td>
  </tr>
</table>
```

**O que corre mal:** Uma `<table>` diz às tecnologias de apoio "isto são dados em tabela, com linhas e colunas". Mas isto **não** são dados tabulares — é apenas um formulário. Alguns leitores de ecrã passam a anunciar "tabela, 2 colunas, 2 linhas, célula 1 de 2..." a toda a volta, acrescentando ruído e confusão sem qualquer benefício. Além disso, tabelas de *layout* costumam adaptar-se mal à ampliação e a ecrãs pequenos.

**Exemplo correto** — posicionar com CSS:

```html
<div class="campo">
  <label for="nome">Nome</label>
  <input id="nome" type="text">
</div>
<div class="campo">
  <label for="email">Email</label>
  <input id="email" type="text">
</div>

<style>
  .campo { display: grid; grid-template-columns: 8rem 1fr; gap: 0.5rem; align-items: center; }
</style>
```

**O que corre bem:** A estrutura HTML é simples e correta (rótulo + campo), sem prometer uma "tabela" que não existe. O alinhamento visual em duas colunas é conseguido com CSS (`grid`), que serve exatamente para isso. As tecnologias de apoio "veem" apenas um formulário limpo, e o *layout* pode adaptar-se facilmente a ecrãs estreitos.

> **Regra prática:** use `<table>` só quando estiver mesmo a apresentar dados em tabela (como uma folha de cálculo). Para posicionar coisas na página, use CSS.

### 4. Layout de uma coluna e adaptação a ecrãs pequenos (*reflow*)

Formulários com vários campos lado a lado dão problemas quando o conteúdo é ampliado ou visto num telemóvel.

**Exemplo problemático** — largura fixa que força deslocamento horizontal:

```html
<style>
  .linha { display: flex; gap: 1rem; width: 900px; }
</style>

<div class="linha">
  <div><label for="pnome">Primeiro nome</label><input id="pnome"></div>
  <div><label for="unome">Último nome</label><input id="unome"></div>
  <div><label for="nif">NIF</label><input id="nif"></div>
</div>
```

**O que corre mal:** A `width: 900px` fixa obriga a linha a manter sempre 900 pixéis de largura. Num ecrã estreito, ou quando o utilizador amplia bastante, a pessoa tem de andar para a direita e para a esquerda para ver cada campo — o famoso "scroll horizontal", que é particularmente penoso para quem usa ampliação.

**Exemplo correto** — largura flexível e empilhamento em ecrãs estreitos:

```html
<style>
  .linha { display: flex; flex-wrap: wrap; gap: 1rem; }
  .linha > div { flex: 1 1 12rem; }  /* cada campo encolhe e passa para baixo quando não cabe */
</style>
```

**O que corre bem:** Com `flex-wrap: wrap` e larguras flexíveis, os campos ficam lado a lado quando há espaço e passam a **empilhar-se numa única coluna** quando o ecrã é estreito ou o conteúdo está ampliado. A pessoa desloca-se apenas para baixo (movimento natural), sem *scroll* horizontal.

> **Nota:** para a maioria dos formulários, **uma única coluna** é a disposição mais segura e mais fácil de seguir para toda a gente. Reserve as várias colunas para casos em que fazem mesmo sentido (por exemplo, "Primeiro nome" e "Último nome" lado a lado).

### 5. Tamanho e espaçamento dos alvos

Campos e botões demasiado pequenos ou demasiado juntos causam toques e cliques errados, sobretudo em ecrãs táteis e para quem tem dificuldades motoras.

**Exemplo problemático:**

```html
<button style="padding: 2px 4px">Guardar</button><button style="padding: 2px 4px">Apagar</button>
```

**O que corre mal:** Os dois botões são minúsculos e estão colados um ao outro, sem qualquer espaço entre eles. É muito fácil carregar em "Apagar" quando se queria "Guardar" — e neste caso o engano tem consequências.

> **Analogia:** É como tentar carregar num botão específico de um comando cheio de botões minúsculos e encostados. Mais tarde ou mais cedo, carrega-se no errado.

**Exemplo correto:**

```html
<style>
  .acoes button {
    min-height: 44px;
    padding: 0.6rem 1.2rem;
  }
  .acoes { display: flex; gap: 1rem; }
</style>

<div class="acoes">
  <button>Guardar</button>
  <button>Apagar</button>
</div>
```

**O que corre bem:** Os botões têm uma área confortável (uma altura mínima na ordem dos 44 pixéis é uma referência comum) e há um espaço claro entre eles. Isto reduz muito os toques acidentais e ajuda praticamente toda a gente, não só quem tem deficiência motora.

### 6. Deixar o navegador tratar da ordem de foco (evitar `tabindex` positivo)

A ordem por que a tecla Tab percorre os campos segue, por omissão, a ordem do código. Regra geral, é isso que queremos, e por isso **não devemos mexer nela**.

**Exemplo problemático:**

```html
<input id="nome"  tabindex="3">
<input id="email" tabindex="1">
<input id="tel"   tabindex="2">
```

**O que corre mal:** Os valores `tabindex` positivos forçam uma ordem de foco (Email → Telefone → Nome) diferente da ordem em que os campos aparecem no ecrã e no código. Isto quase sempre confunde: a pessoa carrega em Tab e o foco "salta" para sítios inesperados. Além disso, `tabindex` positivos são difíceis de manter — basta acrescentar um campo para ter de renumerar tudo.

**Exemplo correto:**

```html
<input id="nome">
<input id="email">
<input id="tel">
```

**O que corre bem:** Sem `tabindex`, a ordem de foco segue naturalmente a ordem do código, que (como vimos no ponto 1) já deve coincidir com a ordem visual. Simples, previsível e fácil de manter. O `tabindex` só se justifica em casos especiais, normalmente com o valor `0` (para tornar focável um elemento que não o é por natureza) ou `-1` (para o retirar da navegação por Tab), nunca com valores positivos para "reordenar".

## Recomendações para Conteúdo Acessível

Para além do código, há decisões de conteúdo e de desenho que fazem toda a diferença:

- **Prefira uma única coluna.** É a disposição mais fácil de seguir e a que melhor se adapta à ampliação e aos telemóveis. Só use múltiplas colunas quando os campos são mesmo curtos e relacionados (como nome e apelido).

- **Coloque cada coisa junto daquilo a que pertence (proximidade).** O rótulo junto do campo, o texto de ajuda junto do campo, o botão de submeter no fim do formulário. Elementos relacionados devem estar visualmente próximos; elementos de secções diferentes devem estar claramente separados. É a mesma lógica de um armário bem organizado, onde os produtos do mesmo tipo estão na mesma prateleira.

- **Agrupe por assunto.** Junte os campos que fazem parte do mesmo tema ("Dados pessoais", "Morada", "Pagamento") em blocos visíveis. Isto ajuda especialmente quem tem dificuldades de atenção ou de memória, porque permite "processar" o formulário aos poucos.

- **Mantenha a disposição consistente ao longo do formulário e do sítio.** Se num ecrã o botão principal está em baixo à direita, mantenha-o aí nos outros ecrãs. Posições que mudam de página para página obrigam a pessoa a "reaprender" o formulário a cada passo.

- **Nunca dependa apenas da posição para dar uma instrução.** Evite frases como "preencha os campos da coluna da direita" ou "veja o quadro em baixo". Quem não vê a disposição não consegue seguir. Refira-se aos campos pelo nome ("preencha o campo NIF"), não pela posição.

- **Garanta espaço à volta dos campos e botões.** Espaçamento generoso não é só estética: reduz erros de toque e torna o formulário mais fácil de ler para toda a gente.

### Erros Comuns

- **Usar CSS (`order`, `flex-direction: row-reverse`, posicionamento absoluto) para reorganizar campos**, criando uma diferença entre a ordem visual e a ordem do código.
- **Deixar campos relacionados sem agrupamento** — botões de opção e caixas de verificação sem `<fieldset>` e `<legend>`.
- **Usar tabelas (`<table>`) apenas para alinhar campos**, em vez de CSS.
- **Formulários largos que só cabem em ecrãs grandes**, obrigando a deslocamento horizontal quando ampliados ou vistos no telemóvel.
- **Campos e botões pequenos e colados**, que provocam toques e cliques acidentais.
- **Usar `tabindex` com valores positivos** para forçar uma ordem de foco, tornando a navegação imprevisível.
- **Dar instruções baseadas na posição** ("em baixo", "à direita") em vez de identificar os campos pelo nome.
- **Espalhar campos relacionados** por sítios distantes do ecrã, obrigando a pessoa a saltar de um lado para o outro.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A estrutura e o posicionamento são a "arrumação" do formulário: a **ordem** dos campos, o seu **agrupamento** e a sua **colocação** no ecrã.
- Muitas pessoas recebem o formulário pela **ordem do código**, não pela ordem visual. Por isso, **a ordem visual e a ordem do código têm de coincidir**. Não use CSS para trocar a sequência.
- **Agrupe os campos relacionados** com `<fieldset>` e `<legend>`, para que a relação entre a pergunta e as respostas seja percetível por toda a gente.
- Use **CSS, não tabelas**, para posicionar campos.
- Prefira **uma única coluna** e garanta que o formulário se **adapta** à ampliação e a ecrãs pequenos, sem deslocamento horizontal.
- Dê **tamanho e espaço suficientes** a campos e botões, para evitar toques acidentais.
- Deixe a **ordem de foco (Tab)** seguir naturalmente o código; evite `tabindex` positivos.
- **Não dependa da posição** para transmitir instruções — identifique os campos pelo nome.

### Exercícios Práticos

1. **Detetar a inversão.** Pegue no primeiro exemplo problemático deste capítulo (o que usa `order` no CSS para trocar "Nome" e "Morada"). Sem correr o código, escreva a ordem que uma pessoa **vê** e a ordem que um leitor de ecrã **ouve**. Depois corrija o exemplo para que as duas coincidam.

2. **Agrupar opções.** Crie um pequeno formulário com a pergunta "Qual o seu método de pagamento?" e três opções (Multibanco, MB WAY, Cartão de crédito) em botões de opção. Escreva-o primeiro **sem** agrupamento e depois **com** `<fieldset>` e `<legend>`. Usando o leitor de ecrã que estiver disponível, ouça as duas versões e anote a diferença.

3. **Do quadro ao CSS.** Encontre (ou escreva) um formulário simples feito com uma `<table>` de *layout* e reescreva-o sem tabela, usando CSS para o alinhamento em duas colunas. Confirme que a estrutura HTML passou a ter apenas rótulos e campos.

4. **Teste do *reflow*.** Abra um formulário no seu navegador e amplie o *zoom* para 400% (Ctrl/Cmd e "+"). Verifique se aparece deslocamento horizontal. Se aparecer, identifique o que está a impedir os campos de se empilharem numa coluna e proponha uma correção.

5. **Auditar o espaçamento.** Numa página com vários botões (por exemplo, "Guardar", "Cancelar", "Apagar"), verifique se estão suficientemente grandes e separados. Meça informalmente se seria fácil carregar no botão errado num telemóvel e ajuste o espaçamento se necessário.

6. **Caça à instrução espacial.** Procure num formulário real (ou invente) uma instrução que dependa da posição, como "preencha os campos assinalados à direita". Reescreva-a de forma que continue a fazer sentido para alguém que não veja a disposição do ecrã.

