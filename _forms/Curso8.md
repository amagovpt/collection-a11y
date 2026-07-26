# Formulários

## Introdução

Quase tudo o que fazemos online passa por um formulário. Iniciar sessão, pesquisar, comprar um bilhete, pedir a segunda via de um documento, marcar uma consulta ou submeter um pedido a um serviço público. Em todos estes casos existe um formulário a intermediar a relação entre a pessoa e o sistema.

Podemos pensar num formulário como uma **conversa estruturada**. O sítio faz perguntas ("Qual é o seu nome?", "Que valor pretende transferir?") e a pessoa responde. Se essa conversa for clara, ordenada e paciente, qualquer pessoa consegue chegar ao fim. Se for confusa, apressada ou cheia de armadilhas, muita gente desiste, e uma parte dessas pessoas desiste *não porque não quer*, mas porque a forma como o formulário foi construído lhes fecha a porta.

> **Analogia — o balcão de atendimento**
>
> Imagine um balcão de um serviço público. Do outro lado está um funcionário que faz perguntas e preenche os campos por si. Um bom funcionário fala devagar, explica o que é preciso, avisa quando algo está mal preenchido e não se importa de repetir. Um mau funcionário fala baixo, de costas, não explica os campos e, quando erramos, limita-se a rasgar a folha e mandar começar de novo.
>
> Um formulário acessível é o "bom funcionário": comunica de forma clara com **todas** as pessoas, incluindo aquelas que não veem o ecrã, que não usam rato, ou que precisam de mais tempo. Um formulário inacessível é o "mau funcionário" — e o problema é que ninguém o pode substituir, porque está escrito no código.

Neste módulo vamos perceber o que torna um formulário acessível de uma forma geral: quem depende dessa acessibilidade, que requisitos existem e que decisões técnicas fazem a diferença logo à partida. Os aspetos mais específicos — a estrutura e o posicionamento dos campos, os rótulos e instruções, as mensagens de erro e os formulários com vários passos — serão abordados mais à frente. Por isso, aqui vamos concentrar-nos nos alicerces.

### Como as Pessoas com Deficiência usam Formulários

Não existe "o utilizador com deficiência". Existem pessoas muito diferentes, com necessidades muito diferentes, e a mesma barreira pode ser invisível para umas e intransponível para outras. Vale a pena conhecer, em traços gerais, como cada grupo interage com um formulário.

**Pessoas cegas** costumam usar um *leitor de ecrã* — um programa que lê em voz alta (ou envia para uma linha braille) aquilo que está no ecrã. A pessoa não vê o formulário como um todo; percorre-o campo a campo, geralmente com o teclado. Para ela, cada campo tem de "dizer" claramente três coisas: **o que é** (é uma caixa de texto? um botão?), **como se chama** (o que devo escrever aqui?) e **em que estado está** (está preenchido? tem erro? é obrigatório?). Se esta informação não existir no código, o leitor de ecrã simplesmente não a consegue anunciar.

**Pessoas com baixa visão** podem ver o ecrã, mas com ampliação, cores invertidas ou tipos de letra maiores. Quando o ecrã está muito ampliado, vê-se apenas um pequeno pedaço de cada vez — como olhar para uma sala através do rolo de papel higiénico. Um campo cuja etiqueta está longe do campo, ou cujo erro aparece num canto distante, pode passar completamente despercebido.

**Pessoas com limitações motoras** podem não conseguir usar o rato. Muitas navegam **só com o teclado**, outras usam comandos de voz, um único botão (*switch*) ou dispositivos adaptados. Para estas pessoas, é essencial poder alcançar e ativar todos os campos e botões sem depender de um clique preciso num ponto do ecrã.

**Pessoas com deficiência cognitiva ou dificuldades de aprendizagem** beneficiam de formulários curtos, com linguagem simples, uma coisa de cada vez e sem pressão de tempo. Perguntas ambíguas, jargão técnico ou campos que "desaparecem" com um temporizador criam barreiras reais.

**Pessoas surdas ou com perda auditiva** normalmente não têm problemas com o texto de um formulário, mas são prejudicadas se a única forma de avisar de um erro for um som (por exemplo, um "bip" quando algo está mal). Aquilo que é comunicado por áudio tem de estar também disponível de forma visual e textual.

> **O que reter deste retrato**
>
> Repare que quase todas estas pessoas dependem, no fundo, de **duas coisas**: que a informação exista de forma estruturada no código (para o leitor de ecrã a poder anunciar) e que tudo seja operável sem rato (para quem usa teclado, voz ou switch). Estas duas ideias vão acompanhar-nos ao longo de todo o módulo.

### Requisitos de Acessibilidade para Formulários

As Diretrizes de Acessibilidade para o Conteúdo Web (WCAG) organizam a acessibilidade em quatro princípios simples. Aplicados aos formulários, podem ler-se assim:

- **Percetível** — a pessoa consegue *aperceber-se* de que existe um campo, do que ele pede e do que lá escreveu. Isto vale para quem vê e para quem ouve através de um leitor de ecrã.
- **Operável** — a pessoa consegue *usar* o formulário com o método que tem: rato, teclado, voz ou toque. Nenhuma interação pode depender exclusivamente do rato.
- **Compreensível** — as perguntas fazem sentido, o comportamento é previsível e, quando algo corre mal, a pessoa percebe o quê e como corrigir.
- **Robusto** — o formulário funciona com diferentes tecnologias de apoio, hoje e no futuro, porque foi construído com código correto e padronizado.

Num nível prático, e para este capítulo introdutório, três requisitos gerais sobressaem e vão orientar as boas decisões técnicas:

1. **Usar elementos nativos** de formulário sempre que possível. O HTML já traz caixas de texto, listas, caixas de verificação e botões que são acessíveis de origem. Recriá-los "à mão" com `<div>` obriga a repor, uma a uma, todas as características que se perderam.
2. **Garantir a operabilidade por teclado.** Se conseguir preencher e submeter o formulário inteiro usando apenas <kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>, <kbd>Espaço</kbd>, <kbd>Enter</kbd> e as setas, está no bom caminho.
3. **Expor o nome, a função e o estado** de cada campo ao código (o chamado *name, role, value*). É isto que permite a um leitor de ecrã dizer "Caixa de texto, E-mail, obrigatório, vazio".

## Técnicas de Codificação

Boa parte da acessibilidade de um formulário decide-se em escolhas técnicas que se fazem uma vez e beneficiam toda a gente. Vejamos as principais.

### Escolher o elemento certo para cada tarefa

O HTML oferece elementos próprios para cada tipo de interação: `<input>` para dados curtos, `<textarea>` para textos longos, `<select>` para escolher de uma lista, `<button>` para ações. Estes elementos são reconhecidos por teclado e por leitores de ecrã **sem que seja preciso fazer mais nada**.

```html
<!-- BOM -->
<button type="submit">Submeter pedido</button>

<!-- MAU -->
<div class="botao" onclick="submeter()">Submeter pedido</div>
```

**O que funciona e o que falha aqui:** O `<button>` recebe foco com o <kbd>Tab</kbd>, ativa-se com <kbd>Enter</kbd> ou <kbd>Espaço</kbd> e é anunciado como "botão" pelo leitor de ecrã. Tudo de graça. O `<div>` é apenas um retângulo decorado: não recebe foco pelo teclado, não responde ao <kbd>Enter</kbd> e o leitor de ecrã não faz ideia de que é clicável. Para o pôr ao nível do `<button>`, teria de lhe acrescentar `tabindex`, tratar eventos de teclado e adicionar `role="button"`. Muito trabalho para reconstruir algo que já existia.

> **Analogia:** usar um `<div>` como botão é como fabricar uma cadeira a partir de tábuas soltas quando havia uma cadeira pronta ao lado. Pode até *parecer* uma cadeira, mas alguém se vai magoar quando tentar sentar-se.

### Usar o tipo (`type`) apropriado nos campos

O atributo `type` do `<input>` não é um detalhe estético. Ele diz ao navegador que espécie de dado é esperado, o que ajuda a validação, ajusta o teclado apresentado nos telemóveis e melhora a compreensão para toda a gente.

```html
<!-- BOM -->
<input type="email" name="email">
<input type="tel" name="telefone">
<input type="date" name="data_nascimento">

<!-- MENOS BOM -->
<input type="text" name="email">
<input type="text" name="telefone">
```

**O que funciona e o que falha aqui:** Com `type="email"`, um telemóvel mostra logo o teclado com o símbolo "@"; com `type="tel"`, aparece o teclado numérico. Isto reduz erros e esforço, sobretudo para quem tem dificuldades motoras ou cognitivas. Usar sempre `type="text"` obriga a pessoa a procurar teclas e abre a porta a mais enganos. Não é *errado* em termos de código, mas desperdiça uma ajuda que não custa nada dar.

### Ajudar o preenchimento automático com `autocomplete`

Quando um campo pede um dado pessoal comum (nome, e-mail, morada, telefone), o atributo `autocomplete` diz ao navegador *qual* é esse dado, permitindo-lhe oferecer o preenchimento automático.

```html
<!-- BOM -->
<input type="text" name="nome" autocomplete="name">
<input type="email" name="email" autocomplete="email">
<input type="text" name="cp" autocomplete="postal-code">
```

**O que funciona e o que falha aqui:** Para uma pessoa com limitações motoras, escrever a morada completa pode ser demorado e cansativo; o preenchimento automático poupa-lhe esse esforço. Para uma pessoa com dificuldades de memória, evita ter de recordar dados de cor. Sem `autocomplete`, o navegador não sabe que aquele campo é o "código postal" e não consegue ajudar. Este requisito corresponde ao critério WCAG *Identificar a Finalidade da Entrada* (1.3.5).

### Manter a operabilidade por teclado

Como vimos, muita gente não usa rato. A regra prática é simples: **tudo o que se faz com o rato tem de se poder fazer com o teclado**. Se usar apenas elementos nativos, isto acontece quase automaticamente. Os problemas surgem sobretudo quando se constroem componentes personalizados (menus, "dropdowns" desenhados de raiz, botões falsos).

```html
<!-- BOM: controlo nativo, já funciona com teclado -->
<select name="distrito">
  <option value="">Escolha um distrito</option>
  <option value="lisboa">Lisboa</option>
  <option value="porto">Porto</option>
</select>

<!-- ARRISCADO: lista personalizada feita com div/span -->
<div class="dropdown" onclick="abrir()">Escolha um distrito</div>
```

**O que funciona e o que falha aqui:** O `<select>` abre-se com o teclado, percorre-se com as setas e anuncia cada opção, sem código extra. A versão em `<div>` obriga a reprogramar todo esse comportamento (foco, setas, <kbd>Enter</kbd>, <kbd>Escape</kbd>, anúncio de opções) e, se um único desses pormenores ficar por fazer, a pessoa que navega com teclado fica bloqueada. A recomendação é clara: **apenas construir um controlo personalizado quando não existir mesmo possibilidade de usar o nativo** e, nesse caso, faça-o com ARIA e teste-o exaustivamente com teclado e leitor de ecrã.

### Envolver os campos num `<form>` e ter um botão de submissão real

Parece óbvio, mas é frequente encontrar "formulários" que na verdade são um conjunto de campos soltos. Envolver os controlos num elemento `<form>` e terminar com um botão de submissão verdadeiro traz comportamentos que os utilizadores esperam, como submeter com a tecla <kbd>Enter</kbd>.

```html
<!-- BOM -->
<form action="/pedido" method="post">
  <!-- campos aqui -->
  <button type="submit">Enviar</button>
</form>
```

**O que funciona e o que falha aqui:** Dentro de um `<form>`, premir <kbd>Enter</kbd> num campo de texto submete o formulário. Um automatismo que muitos utilizadores de teclado usam sem pensar. Um botão `type="submit"` real é anunciado corretamente e cumpre essa função. Sem `<form>` e sem botão real, perde-se este comportamento esperado e a pessoa fica sem saber como concluir.

## Recomendações para Conteúdo Acessível

Nem tudo se resolve no código. A forma como *escrevemos e organizamos* o formulário, as decisões de conteúdo, tem tanto peso como as decisões técnicas. Estas recomendações aplicam-se a qualquer formulário, independentemente da tecnologia.

**Peça apenas o que é mesmo necessário.** Cada campo é um obstáculo. Um formulário curto é mais fácil para toda a gente e essencial para quem se cansa depressa ou se distrai facilmente.

> **Exemplo:** um formulário de subscrição de uma newsletter que pede nome, apelido, morada completa, data de nascimento e profissão.
>
> **Análise:** para enviar um e-mail periódico basta... o e-mail. Cada campo extra afasta pessoas e, no caso de quem tem dificuldades motoras ou cognitivas, o desânimo é maior. Menos campos não é só "mais bonito", é mais acessível.

**Use linguagem simples e direta nas perguntas.** Evite jargão, siglas por explicar e frases ambíguas. Se um termo técnico for inevitável, explique-o.

> **Exemplo:** um campo chamado apenas "NIF/NIPC/NISS".
>
> **Análise:** para quem conhece as siglas, tudo bem; para muita gente, é um enigma. Uma alternativa mais clara seria "Número de identificação fiscal (NIF)" e, se forem aceites vários, indicá-lo de forma explícita. Perguntas claras reduzem erros para *todos*, não apenas para pessoas com deficiência.

**Agrupe o que faz parte do mesmo assunto.** Um formulário que salta de tema em tema é cansativo de acompanhar, sobretudo para quem o percorre linearmente com um leitor de ecrã. 

**Não imponha limites de tempo desnecessários.** Formulários que "expiram" ou campos que se fecham sozinhos penalizam quem escreve mais devagar, quem usa tecnologias de apoio ou quem simplesmente precisa de pensar. Se um limite for mesmo obrigatório (por razões de segurança, por exemplo), avise com antecedência e permita prolongá-lo.

**Indique com clareza o que é obrigatório e o que é opcional.** A pessoa deve saber, *antes* de submeter, que campos tem mesmo de preencher. 

### Erros Comuns

Alguns erros repetem-se tanto que vale a pena tê-los sempre debaixo de olho:

- **Botões e ligações falsos.** Usar `<div>` ou `<span>` com um `onclick` em vez de `<button>` ou `<a>`. Resultado: quem usa teclado não os alcança e o leitor de ecrã não os anuncia como acionáveis.
- **Depender só de `type="text"`.** Ignorar `type="email"`, `type="tel"`, `type="number"`, etc., desperdiça validação e teclados adaptados que ajudariam toda a gente.
- **Controlos personalizados sem suporte de teclado.** "Dropdowns", interruptores e seletores desenhados de raiz que só respondem ao rato deixam de fora uma parte dos utilizadores.
- **Esconder ou "roubar" o foco.** Componentes que movem o foco para sítios inesperados, ou que o prendem numa zona sem saída, desorientam quem navega por teclado.
- **CAPTCHAs só visuais ou só sonoros.** Um teste que obriga a "ler letras distorcidas" exclui quem não vê; se a alternativa for apenas áudio, exclui quem não ouve. Sempre que possível, prefira métodos que não dependam de um único sentido.

> **Nota:** dois erros muito frequentes — usar o texto de exemplo (*placeholder*) como se fosse a etiqueta do campo, e mostrar mensagens de erro pouco claras — são tratados em profundidade mais à frente. Por isso não os desenvolvemos aqui, mas fica o aviso de que existem.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Um formulário é uma **conversa estruturada** entre a pessoa e o sistema; torná-lo acessível é garantir que essa conversa funciona para toda a gente.
- Pessoas diferentes usam os formulários de formas diferentes — com leitor de ecrã, com ampliação, só com teclado, com voz — mas quase todas dependem de **informação bem estruturada no código** e de **operabilidade sem rato**.
- A regra de ouro técnica é **usar elementos nativos do HTML** (`<input>`, `<select>`, `<textarea>`, `<button>`, `<form>`): são acessíveis de origem e poupam imenso trabalho.
- Escolher o **`type` certo** e usar **`autocomplete`** ajuda toda a gente e é essencial para quem tem dificuldades motoras ou cognitivas.
- **Só se constrói um controlo personalizado** quando o nativo não serve — e, mesmo aí, com muita atenção ao suporte ao teclado e à correção do ARIA.
- No conteúdo: peça só o necessário, use linguagem simples, não imponha limites de tempo desnecessários.

### Exercícios Práticos

**Exercício 1 — Encontrar o botão falso**
Recebeu o seguinte trecho de código:

```html
<div class="botao-enviar" onclick="enviar()">Enviar</div>
```

a) Explique, por palavras suas, dois problemas de acessibilidade deste código.
b) Reescreva-o de forma acessível.

> *Pista:* pense em quem navega só com teclado e em como um leitor de ecrã anuncia (ou não) este elemento.

**Exercício 2 — Escolher o `type` certo**
Um formulário de contacto pede: nome, e-mail, número de telemóvel e mensagem. Todos os campos estão como `type="text"`.

a) Que `type` deveria ter cada campo (e que elemento, no caso da mensagem)?
b) Explique que benefício concreto traz cada alteração para um utilizador de telemóvel.

**Exercício 3 — Cortar o supérfluo**
Um formulário para descarregar um documento público pede: nome, apelido, e-mail, morada, código postal, data de nascimento, profissão e habilitações.

a) Se o objetivo é apenas enviar o documento por e-mail, que campos manteria e quais removeria?
b) Justifique a sua decisão do ponto de vista da acessibilidade e do esforço pedido à pessoa.

**Exercício 4 — Teste do teclado**
Escolha um formulário real (por exemplo, o de pesquisa ou de contacto de um sítio à sua escolha) e tente preenchê-lo e submetê-lo **usando apenas o teclado** (<kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>, setas, <kbd>Espaço</kbd>, <kbd>Enter</kbd>).

a) Conseguiu alcançar todos os campos e o botão de submissão?
b) Houve algum ponto em que ficou "preso" ou sem saber onde estava o foco?
c) Registe uma barreira que tenha encontrado e proponha uma correção.

> *Sugestão de reflexão:* muitas das barreiras que encontrar neste exercício vão ligar-se diretamente aos temas dos próximos capítulos — estrutura, rótulos, mensagens de erro e formulários com vários passos.



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

# Rótulos e Instruções

## Introdução

Imagine que chega a uma cozinha desconhecida e encontra uma fila de frascos todos iguais, sem qualquer etiqueta. Um tem sal, outro tem açúcar, outro tem farinha. Para quem vê, ainda é possível adivinhar pela cor ou pela textura. Mas para quem não vê, ou para quem se distrai com facilidade, aqueles frascos são um enigma perigoso: basta trocar o sal pelo açúcar para estragar o bolo.

Um formulário sem rótulos é exactamente esta cozinha. Os campos estão lá — caixas de texto, listas, botões — mas ninguém explica o que se espera dentro de cada um. O **rótulo** (em inglês, *label*) é a etiqueta que diz "aqui escreve-se o teu nome", "aqui escolhe-se a data de nascimento", "aqui confirma-se a palavra-passe". As **instruções** são a informação extra que ajuda a preencher correctamente: "a data deve ter o formato DD/MM/AAAA", "a palavra-passe precisa de pelo menos 8 caracteres", "campos com asterisco são obrigatórios".

Neste capítulo vamos concentrar-nos em duas perguntas simples:

- **Como identificar cada campo** de forma clara e para que essa identificação chegue a toda a gente, incluindo a quem usa tecnologias de apoio.
- **Como dar instruções** no momento certo, antes de a pessoa preencher, para evitar erros em vez de os corrigir depois.

> **Nota de âmbito:** o *agrupamento visual* de campos (por exemplo, juntar "morada de faturação" e "morada de envio") e a *ordem de leitura* são tratados na secção **Estrutura e Posicionamento**. O texto das mensagens que surgem *depois* de um erro é tratado na secção **Notificações e Mensagens de Erro**. Aqui interessa-nos o que aparece **antes** de a pessoa preencher: a etiqueta do campo e a ajuda que evita o erro.

### Como as Pessoas com Deficiência dependem de Rótulos e Instruções

Um rótulo bem feito não é uma decoração. É a única forma de muitas pessoas saberem o que fazer. Vejamos como diferentes grupos dependem dele.

**Pessoas cegas que usam leitor de ecrã.** O leitor de ecrã lê o que está no ecrã em voz alta. Quando a pessoa salta de campo em campo com a tecla `Tab`, o leitor anuncia o rótulo de cada campo: *"Nome, caixa de texto"*, *"País, lista"*. Se o campo não tiver um rótulo associado de forma correcta, o leitor não tem nada para anunciar e diz apenas *"caixa de texto"* — o equivalente a chegar ao frasco sem etiqueta. A pessoa fica sem saber o que ali escrever.

**Pessoas com baixa visão que ampliam o ecrã.** Quem usa ampliação vê apenas uma pequena parte do ecrã de cada vez, como quem lê um jornal através de uma lupa. Se o rótulo estiver longe do campo, ou muito acima, pode ficar fora da zona ampliada e a pessoa perde a ligação entre a etiqueta e a caixa correspondente.

**Pessoas com deficiência cognitiva ou dificuldades de aprendizagem.** Rótulos claros e instruções antecipadas reduzem o esforço de memória e a ansiedade. Uma instrução como "usa o formato DD/MM/AAAA" evita que a pessoa tenha de adivinhar e falhar várias vezes. Rótulos consistentes ao longo do sítio (usar sempre "Telemóvel" e não ora "Telemóvel", ora "Contacto móvel", ora "Nº de telefone") ajudam a criar hábitos e a reconhecer os campos.

**Pessoas com limitações motoras.** Aqui há um benefício menos óbvio mas muito importante: quando o rótulo está **associado** ao campo, clicar no texto do rótulo coloca o cursor no campo. Isto aumenta muito a área "clicável". Para quem tem dificuldade em acertar com o rato ou com o dedo numa pequena caixa de seleção, poder clicar na palavra "Aceito os termos" em vez da minúscula caixa quadrada faz toda a diferença.

**Pessoas que usam software de reconhecimento de voz.** Quem controla o computador por voz diz coisas como *"clicar em Enviar"* ou *"clicar em Pesquisar"*. Para isto funcionar, o nome que o software "ouve" tem de coincidir com o texto que a pessoa vê. Se o botão mostra "Pesquisar" mas por baixo tem um nome acessível diferente, o comando de voz falha.

### Requisitos de Acessibilidade para Rótulos e Instruções

Os requisitos abaixo têm correspondência em critérios das WCAG (as diretrizes internacionais de acessibilidade). Aqui apresentamo-los em linguagem simples.

- **Todos os campos que pedem informação têm de ter um rótulo ou uma instrução.** Ninguém deve ter de adivinhar o que escrever. *(Corresponde ao critério 3.3.2 — Rótulos ou Instruções.)*

- **A ligação entre o rótulo e o campo tem de ser "percetível pelo programa", não apenas visual.** Não basta o rótulo estar ao lado do campo aos olhos de quem vê; o código tem de dizer explicitamente "este texto é o rótulo daquele campo", para que o leitor de ecrã os associe. *(Corresponde ao critério 1.3.1 — Informação e Relações, e ao 4.1.2 — Nome, Função, Valor.)*

- **Os rótulos têm de ser descritivos.** "Campo 1" não descreve nada. "Nome próprio" descreve. *(Corresponde ao critério 2.4.6 — Cabeçalhos e Rótulos.)*

- **O nome que o programa reconhece tem de incluir o texto visível.** Se a pessoa vê "Enviar", o comando de voz "clicar em Enviar" tem de funcionar. *(Corresponde ao critério 2.5.3 — Rótulo no Nome.)*

- **Campos que pedem dados pessoais comuns devem identificar o seu propósito.** O programa deve conseguir saber que um campo é para o "nome", outro para o "e-mail", outro para o "código postal", para que ferramentas de preenchimento automático e personalização funcionem. *(Corresponde ao critério 1.3.5 — Identificar o Objetivo da Entrada.)*

## Técnicas de Codificação

Nesta secção vemos, na prática, como escrever o código. Todos os exemplos usam HTML simples. Depois de cada exemplo há uma explicação do que funciona bem ou mal.

### 1. Associar o rótulo ao campo com `<label>` e `for`

A forma mais robusta e recomendada é usar o elemento `<label>` com o atributo `for`, que aponta para o atributo `id` do campo. Os dois têm de ter o mesmo valor.

```html
<label for="nome-proprio">Nome próprio</label>
<input type="text" id="nome-proprio">
```

**O que funciona bem:** o `for="nome-proprio"` e o `id="nome-proprio"` criam uma ligação explícita. O leitor de ecrã anuncia *"Nome próprio, caixa de texto"*. Além disso, clicar no texto "Nome próprio" coloca o cursor na caixa — a tal área clicável maior que ajuda quem tem limitações motoras. É a solução mais compatível com todas as tecnologias de apoio.

**Atenção:** o `id` tem de ser **único** em toda a página. Se dois campos partilharem o mesmo `id`, a associação parte-se e os resultados tornam-se imprevisíveis.

### 2. Envolver o campo com o rótulo (associação implícita)

Também é possível colocar o campo **dentro** do `<label>`. Neste caso, a associação existe mesmo sem `for` e `id`.

```html
<label>
  Nome próprio
  <input type="text">
</label>
```

**O que funciona bem:** é conciso e a associação é automática. Útil, por exemplo, em caixas de seleção onde o texto anda sempre colado à caixa.

**O que pode correr mal:** alguns leitores de ecrã e alguns componentes complexos lidam pior com esta forma do que com a explícita. Além disso, se o layout separar visualmente o texto do campo, o código fica mais difícil de gerir. Por isso, quando houver dúvidas, prefira a associação explícita com `for` (técnica 1).

### 3. Dar um nome a controlos sem texto visível: `aria-label`

Alguns controlos não têm texto ao lado. Por exemplo, um botão de pesquisa que mostra apenas um ícone de lupa. Aos olhos de quem vê, a lupa "explica-se" sozinha. Para o leitor de ecrã, um botão sem texto é um botão mudo.

```html
<!-- Mau exemplo: botão sem nome -->
<button>
  <svg><!-- ícone de lupa --></svg>
</button>

<!-- Bom exemplo: nome fornecido com aria-label -->
<button aria-label="Pesquisar">
  <svg aria-hidden="true"><!-- ícone de lupa --></svg>
</button>
```

**O que funciona bem no bom exemplo:** o `aria-label="Pesquisar"` dá um nome ao botão que o leitor de ecrã anuncia. O `aria-hidden="true"` no ícone diz à tecnologia de apoio para o ignorar, evitando leituras estranhas do desenho.

**O que falha no mau exemplo:** o botão não tem texto nem `aria-label`. O leitor de ecrã anuncia apenas *"botão"*, sem dizer para quê. E como o texto "Pesquisar" não aparece em lado nenhum, quem usa comando de voz também não consegue ativá-lo.

> **Cuidado:** use `aria-label` apenas quando **não existe** texto visível para servir de rótulo. Sempre que houver texto no ecrã, o melhor é usá-lo como rótulo real (técnicas 1 ou 2). Um rótulo visível ajuda toda a gente; um rótulo "invisível" só ajuda quem usa leitor de ecrã.

### 4. Construir o nome a partir de texto já existente: `aria-labelledby`

Às vezes o rótulo já está escrito noutro elemento e não queremos repeti-lo. O `aria-labelledby` aponta para o `id` desse texto.

```html
<h2 id="titulo-envio">Morada de envio</h2>
<button id="btn-editar" aria-labelledby="btn-editar titulo-envio">Editar</button>
```

**O que funciona bem:** o botão passa a ser anunciado como *"Editar, Morada de envio"*, o que esclarece qual das várias "moradas" este botão edita. Muito útil quando a mesma palavra (por exemplo, "Editar") se repete pela página.

**O que ter em conta:** o `aria-labelledby` **substitui** qualquer outro nome. Aponte sempre para texto que exista mesmo na página.

### 5. Associar instruções e ajuda ao campo: `aria-describedby`

O rótulo diz *o quê*. As instruções dizem *como*. Para ligar uma instrução a um campo, de forma que o leitor de ecrã a leia logo a seguir ao rótulo, usa-se o `aria-describedby`, que aponta para o `id` do texto de ajuda.

```html
<label for="palavra-passe">Palavra-passe</label>
<input type="password" id="palavra-passe" aria-describedby="ajuda-pp">
<p id="ajuda-pp">Mínimo de 8 caracteres, com pelo menos um número.</p>
```

**O que funciona bem:** quando o cursor entra no campo, o leitor de ecrã anuncia *"Palavra-passe, caixa de texto, Mínimo de 8 caracteres, com pelo menos um número"*. A instrução chega **no momento em que é útil** e a pessoa não tem de a ir procurar. Como a instrução é texto normal na página, também está visível para toda a gente.

**A diferença essencial:** o rótulo (`<label>`) identifica o campo; a descrição (`aria-describedby`) acrescenta ajuda. Não confunda os dois papéis: o campo precisa sempre de rótulo; a descrição é um extra.

### 6. Indicar campos obrigatórios

Quando um campo é obrigatório, isso deve ser comunicado de duas formas: para os olhos e para o programa.

```html
<label for="email">E-mail (obrigatório)</label>
<input type="email" id="email" required aria-required="true">
```

**O que funciona bem:** a palavra "(obrigatório)" no rótulo é clara para toda a gente e não depende de cor nem de símbolos. O atributo `required` faz o próprio navegador tratar o campo como obrigatório, e o `aria-required="true"` garante que os leitores de ecrã o anunciam como tal.

**Sobre o asterisco:** é comum marcar campos obrigatórios com um asterisco (`*`). Não há problema em usá-lo, **desde que** se explique, no início do formulário, o que significa. Por exemplo, "Os campos marcados com * são obrigatórios". Nunca dependa **só** da cor (vermelho) para indicar obrigatoriedade, porque quem não distingue cores não a percebe. 

### 7. Identificar o propósito do campo: `autocomplete`

Para campos que pedem dados pessoais comuns (nome, e-mail, telefone, morada), o atributo `autocomplete` diz ao navegador e a tecnologias de apoio, qual é o propósito do campo.

```html
<label for="tel">Telemóvel</label>
<input type="tel" id="tel" autocomplete="tel">

<label for="cp">Código postal</label>
<input type="text" id="cp" autocomplete="postal-code">
```

**O que funciona bem:** com estes valores, o navegador consegue oferecer preenchimento automático correcto, poupando trabalho a toda a gente e reduzindo erros. Para pessoas com limitações motoras ou de memória, preencher automaticamente o próprio nome e morada é uma enorme ajuda. Este atributo também permite que algumas ferramentas personalizem o formulário (por exemplo, mostrando um ícone junto ao campo).

**O que ter em conta:** use os **valores normalizados** definidos na especificação (`name`, `email`, `tel`, `postal-code`, `street-address`, etc.). Um valor inventado como `autocomplete="telefone-do-utilizador"` não é reconhecido e não produz qualquer benefício.

## Recomendações para Conteúdo Acessível

As técnicas de código só resolvem metade do problema. A outra metade é **o que se escreve** nos rótulos e nas instruções. Aqui ficam recomendações práticas de redação.

**Escreva rótulos curtos, mas concretos.** Um bom rótulo diz exactamente o que se pede, sem palavras a mais. Prefira "Nome próprio" a "Por favor, escreva aqui o seu primeiro nome"; prefira "Data de nascimento" a "Data".

*Exemplo:*

```
Mau:  Campo    →  Bom:  Nome da empresa
Mau:  Data     →  Bom:  Data de nascimento
Mau:  Info     →  Bom:  Comentários adicionais
```

**O que melhora:** os rótulos "bons" dizem à pessoa o que ali colocar sem obrigar a adivinhar. Isto ajuda especialmente quem tem dificuldades cognitivas e quem, com o leitor de ecrã, só ouve o rótulo e mais nada.

**Ponha a informação importante no início do rótulo.** Quem usa leitor de ecrã e salta rapidamente entre campos beneficia de ouvir logo a palavra-chave. "Telemóvel (opcional)" é melhor do que "(Opcional) o seu número de telemóvel".

**Dê as instruções ANTES do campo, não depois.** Se a regra de preenchimento aparecer só depois da caixa, muita gente já a preencheu — e errou — antes de a ler. Coloque o formato ou a regra junto ao rótulo ou logo abaixo dele, e associe-a com `aria-describedby` (técnica 5).

*Exemplo:*

```html
<!-- Recomendado: instrução antes de preencher -->
<label for="nif">NIF</label>
<span id="ajuda-nif">Nove dígitos, sem espaços.</span>
<input type="text" id="nif" aria-describedby="ajuda-nif">
```

**O que funciona bem:** a pessoa lê "Nove dígitos, sem espaços" antes de escrever, e evita o erro. Prevenir é sempre melhor do que corrigir.

**Seja consistente em todo o sítio.** Use sempre a mesma palavra para o mesmo conceito. Se numa página o campo se chama "Telemóvel" e noutra "Contacto", a pessoa tem de reaprender o formulário de cada vez. A consistência reduz o esforço para toda a gente e é essencial para quem tem dificuldades cognitivas.

**Evite depender apenas do "placeholder".** O texto cinzento que aparece dentro da caixa antes de escrever (o *placeholder*) parece um rótulo, mas comporta-se de forma muito diferente — como veremos já a seguir nos erros comuns.

**Faça o texto visível coincidir com o nome do programa.** Se o botão mostra "Guardar alterações", o nome acessível deve começar por "Guardar alterações" (e não, por exemplo, "Submeter formulário"). Assim, o comando de voz "clicar em Guardar alterações" funciona.

### Erros Comuns

**Erro 1 — Usar o *placeholder* como se fosse rótulo.**

```html
<!-- Errado -->
<input type="text" placeholder="Nome próprio">
```

**Porque é um problema:** o texto do *placeholder* **desaparece** assim que a pessoa começa a escrever. É como uma instrução escrita a giz num quadro que se apaga no momento em que se pega no lápis: quem se distrai ou quem precisa de reler já não tem a etiqueta. Além disso, o cinzento-claro habitual tem contraste fraco e alguns leitores de ecrã não o anunciam de forma fiável. **A correção:** use um `<label>` real e, se quiser, mantenha o *placeholder* apenas para um exemplo curto ("ex.: Maria").

**Erro 2 — Campo sem qualquer rótulo associado.**

```html
<!-- Errado -->
<p>Nome próprio</p>
<input type="text">
```

**Porque é um problema:** aos olhos de quem vê, o texto "Nome próprio" está ao lado do campo e parece um rótulo. Mas, no código, não há ligação nenhuma entre os dois. É apenas um parágrafo por acaso próximo da caixa. O leitor de ecrã anuncia só *"caixa de texto"*. **A correção:** transforme o parágrafo em `<label for="...">` ligado ao `id` do campo.

**Erro 3 — Rótulos vagos ou genéricos.** "Campo 1", "Texto", "Info", "Dados". Não descrevem nada. Quem só ouve o rótulo (via leitor de ecrã) fica sem pistas. **A correção:** dê a cada rótulo o nome exacto do que pede.

**Erro 4 — Marcar obrigatoriedade só com cor.** Pintar de vermelho os campos obrigatórios não chega: quem não distingue essa cor não percebe a diferença. **A correção:** acrescente uma palavra ("obrigatório") ou um símbolo explicado (o asterisco com legenda) e o atributo `required`.

**Erro 5 — Instruções que só aparecem depois do erro.** Guardar a regra "a palavra-passe precisa de 8 caracteres" para a mostrar apenas depois de a pessoa falhar transforma uma informação preventiva numa repreensão. **A correção:** mostre a regra antes, junto ao campo.

**Erro 6 — O nome do programa não bate certo com o texto visível.** Um botão que mostra "Pesquisar" mas tem `aria-label="Botão de busca do site"` impede a utilização do comando de voz "clicar em Pesquisar". **A correção:** garanta que o nome acessível **contém** o texto visível, de preferência começando por ele.

**Erro 7 — Ícones sem nome.** Botões e ligações que são só ícones (um caixote do lixo, um lápis, um "x") sem `aria-label` ficam mudos para o leitor de ecrã. **A correção:** dê-lhes um nome com `aria-label` e esconda o ícone decorativo com `aria-hidden="true"`.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- **Todos os campos precisam de rótulo.** O rótulo é a etiqueta que diz o que se espera no campo; sem ele, quem usa leitor de ecrã fica perante um "frasco sem etiqueta".
- **A associação tem de estar no código, não só no aspeto.** Use `<label for="...">` ligado ao `id` do campo (ou o campo dentro do `<label>`). Isto também aumenta a área clicável, ajudando quem tem limitações motoras.
- **Para controlos sem texto visível** (ícones), dê um nome com `aria-label` ou `aria-labelledby`, e esconda o ícone decorativo com `aria-hidden="true"`.
- **As instruções vêm antes do preenchimento**, associadas ao campo com `aria-describedby`. Prevenir o erro é melhor do que corrigi-lo.
- **Rótulos descritivos, curtos e consistentes.** Não usar "Campo 1"; usar "Nome próprio", e sempre o mesmo termo para o mesmo conceito.
- **Obrigatoriedade comunicada por palavras**, não só por cor, e reforçada com `required`.
- **O texto visível tem de coincidir com o nome acessível do elemento**, para os comandos de voz funcionarem.
- **Campos de dados pessoais** devem usar o atributo `autocomplete` com valores normalizados.

### Exercícios Práticos

**Exercício 1 — Encontrar o frasco sem etiqueta.**
Observe o seguinte código e identifique o problema. Depois, reescreva-o de forma acessível.

```html
<p>E-mail</p>
<input type="email" placeholder="E-mail">
```

*Pistas para a resolução:* há dois problemas — o texto "E-mail" não está associado ao campo (é apenas um parágrafo) e o *placeholder* está a fazer o trabalho que devia ser do rótulo. A versão corrigida deve usar `<label for="...">` ligado a um `id`.

**Exercício 2 — Dar voz aos ícones.**
Uma barra de ferramentas tem três botões só com ícones: um lápis (editar), um caixote do lixo (eliminar) e uma estrela (marcar como favorito). Escreva o código dos três botões de forma que um leitor de ecrã anuncie o nome de cada um e que os ícones decorativos sejam ignorados.

**Exercício 3 — Instrução no momento certo.**
Tem um campo "Código postal" que exige o formato `XXXX-XXX`. Escreva o rótulo, a instrução e o campo, ligando a instrução ao campo com `aria-describedby`, de forma que a regra seja lida **antes** de a pessoa preencher.

**Exercício 4 — Caçar os erros.**
No formulário de inscrição de um sítio real (ou num exemplo à sua escolha), navegue **apenas com o teclado**, usando a tecla `Tab` para saltar de campo em campo, e, se possível, com um leitor de ecrã ligado. Anote:

1. Todos os campos que **não** anunciam um rótulo.
2. Se os campos obrigatórios são identificados por palavras (e não só por cor).
3. Se as instruções de formato aparecem **antes** ou **depois** de preencher.
   Para cada problema encontrado, escreva a correção correspondente.

**Exercício 5 — Rótulos que falam por si.**
Melhore os seguintes rótulos vagos, tornando-os descritivos: "Campo", "Data", "Número", "Info". Justifique cada escolha em uma frase.

# Notificações e Mensagens de Erro

## Introdução

Preencher um formulário é uma conversa entre a pessoa e o computador. A pessoa escreve algo, carrega num botão e espera uma resposta. Essa resposta chega quase sempre na forma de uma **notificação** ou de uma **mensagem de erro**:

- *"O seu pedido foi submetido com sucesso."*
- *"O campo Data de nascimento está vazio."*
- *"A palavra-passe tem de ter, no mínimo, 8 caracteres."*
- *"A guardar as suas alterações…"*

Estas mensagens dizem à pessoa **o que aconteceu**, **o que correu mal** e **o que fazer a seguir**. Sem elas, a pessoa fica perdida: não sabe se o formulário foi enviado, não sabe porque é que o botão "não funciona", não sabe o que corrigir.

Nesta secção tratamos especificamente da parte da conversa em que **é o sistema que fala**. Nas secções anteriores vimos como pedir informação de forma clara (rótulos e instruções) e como organizar os campos no ecrã (estrutura e posicionamento). Aqui o tema é diferente: **como é que a resposta do sistema chega, de facto, a toda a gente**, incluindo a quem não vê o ecrã, não distingue cores ou lê com dificuldade.

> **Analogia — o balcão de atendimento**
> Imagine um balcão de finanças. A pessoa entrega um papel. O funcionário pode responder de três maneiras: em silêncio, empurrando o papel de volta sem explicar (péssimo); dizendo apenas *"está mal"* (frustrante); ou dizendo *"falta aqui a sua morada, no campo 4, pode preencher e voltar a entregar"* (útil). Uma boa mensagem de erro é sempre a terceira resposta. E uma boa notificação é o funcionário confirmar em voz alta: *"pronto, ficou tratado"*, para a pessoa não sair na dúvida.

Antes de avançar, distinguimos três tipos de mensagens que vamos referir ao longo do capítulo:

- **Mensagens de erro** — avisam que algo foi introduzido de forma incorreta ou está em falta (ex.: campo obrigatório vazio, e-mail com formato inválido).
- **Mensagens de sucesso / confirmação** — confirmam que uma ação correu bem (ex.: "Inscrição concluída").
- **Mensagens de estado (status)** — informam sobre algo que está a decorrer ou mudou, sem exigir ação imediata (ex.: "A carregar…", "3 resultados encontrados").

---

### Como as Pessoas com Deficiência dependem de Notificações e Mensagens de Erro

O problema central das notificações é este: **muitas vezes elas aparecem no ecrã, mas de uma forma que só quem vê consegue perceber.** Um texto vermelho ao lado de um campo é óbvio para quem olha, e completamente invisível para quem usa um leitor de ecrã, se ninguém "avisar" o leitor de que apareceu texto novo.

Vejamos como diferentes pessoas dependem destas mensagens.

**Pessoas cegas (utilizadores de leitores de ecrã)**
Um leitor de ecrã lê o que está sob o foco ou o que a página lhe manda anunciar. Se uma mensagem de erro aparecer noutro sítio do ecrã sem "chamar" o leitor, a pessoa **não faz ideia de que ela existe**. Fica a carregar no botão "Submeter" repetidamente, sem perceber porque nada acontece. Estas pessoas precisam que as mensagens sejam **anunciadas automaticamente** e que cada erro esteja **ligado ao campo respetivo**.

**Pessoas com baixa visão**
Conseguem ver o ecrã, mas muitas vezes com ampliação ou com cores/contraste alterados. Se o único sinal de erro for *"o campo ficou vermelho"*, a pessoa que ampliou o ecrã a 400% pode nem sequer ter o campo visível na altura em que ele muda de cor. E quem tem baixa perceção de cor pode não distinguir o vermelho do cinzento à volta.

**Pessoas daltónicas**
Cerca de 1 em cada 12 homens tem algum tipo de daltonismo. Se a diferença entre "campo correto" e "campo com erro" for **apenas** a cor (verde vs. vermelho), muitas destas pessoas não veem diferença nenhuma. Precisam de um sinal adicional: um ícone, texto, um contorno diferente.

**Pessoas com deficiência cognitiva ou dificuldades de leitura**
Uma mensagem como *"Erro 0x00423: validação falhou"* não ajuda ninguém, mas prejudica sobretudo quem já tem dificuldade em processar linguagem complexa. Estas pessoas dependem de mensagens **curtas, concretas e em linguagem simples**, que digam exatamente o que fazer.

**Pessoas surdas ou com dificuldades auditivas**
Raramente pensamos nelas ao falar de formulários, mas há um erro clássico: notificações que são **apenas sonoras** (um "bip" quando algo corre mal). Se o único aviso for som, quem não ouve fica sem saber. A informação tem de estar **também em texto ou visualmente**.

**Pessoas com limitações motoras**
Podem demorar mais tempo a preencher. Se uma notificação de estado desaparecer sozinha ao fim de 3 segundos, a pessoa pode não ter chegado a lê-la. Dependem de mensagens que **não desaparecem cedo demais**.

> **A ideia-chave**
> Uma notificação que só é percetível de uma maneira (só cor, só som, só posição visual) é uma notificação que exclui alguém. A regra de ouro é: **a mesma informação, disponível por vários canais** — texto, cor *e* forma; visual *e* anunciado ao leitor de ecrã.

---

### Requisitos de Acessibilidade para Notificações e Mensagens de Erro

Podemos resumir o que uma boa mensagem tem de garantir em cinco requisitos. 

1. **Identificar o erro** — a pessoa tem de saber *qual* campo tem problema. Não basta dizer "há erros no formulário"; é preciso apontar o campo.

2. **Descrever o erro em texto** — o motivo tem de estar escrito por palavras, não apenas sinalizado por cor ou ícone. *"A data tem de estar no formato DD/MM/AAAA"* é texto; um campo a vermelho, sozinho, não é.

3. **Sugerir uma correção (quando possível)** — se o sistema sabe o que está errado, deve dizer como corrigir. *"Faltam 3 caracteres na palavra-passe"* é muito melhor do que *"palavra-passe inválida"*.

4. **Ser percetível sem depender só da cor** — o erro tem de ser distinguível também por texto, ícone ou forma, para quem não vê ou não distingue cores.

5. **Ser anunciado às tecnologias de apoio** — quando a mensagem aparece dinamicamente (sem recarregar a página), o leitor de ecrã tem de ser informado, sem que a pessoa perca o sítio onde estava.

Estes requisitos correspondem, no essencial, a critérios das WCAG que verá listados em detalhe na secção final — nomeadamente a *identificação de erros* (3.3.1), a *sugestão de correção* (3.3.3), as *mensagens de estado* (4.1.3) e o *uso da cor* (1.4.1). Aqui interessa-nos sobretudo perceber **como** cumpri-los na prática.

---

## Técnicas de Codificação

Esta secção mostra o "como se faz". A boa notícia é que o HTML e a especificação ARIA já trazem tudo o que precisamos; o difícil é usá-los de forma correta.

### 1. Ligar a mensagem de erro ao campo com `aria-describedby`

Quando um campo tem um erro, a mensagem de erro deve estar **programaticamente ligada** ao campo. Assim, quando a pessoa navega até ao campo com o leitor de ecrã, ouve não só o rótulo mas também a mensagem de erro.

```html
<label for="email">Endereço de e-mail</label>
<input
  type="email"
  id="email"
  name="email"
  aria-describedby="erro-email"
  aria-invalid="true"
>
<p id="erro-email" class="mensagem-erro">
  O e-mail tem de incluir o símbolo @. Exemplo: nome@dominio.pt
</p>
```

Dois pormenores importantes:

- **`aria-describedby="erro-email"`** cria a ligação. O leitor de ecrã lê a mensagem logo a seguir ao rótulo do campo.
- **`aria-invalid="true"`** marca o campo como "em erro". O leitor de ecrã anuncia algo como *"inválido"* ao entrar no campo, dando o sinal imediato de que há um problema.

**O que funciona bem:** quando a pessoa chega ao campo — mesmo minutos depois, mesmo saltando diretamente para lá — a informação do erro está lá, colada ao campo. Não é preciso ir "à procura" da mensagem noutro sítio da página.

**O que correria mal:** se a mensagem estivesse apenas visível ao lado do campo, sem `aria-describedby`, um utilizador de leitor de ecrã navegaria pelo campo e ouviria só *"Endereço de e-mail, caixa de edição"* — sem qualquer pista de que há um erro por baixo. Repare também que `aria-invalid` **só deve estar presente quando há mesmo erro**; deixá-lo sempre a `"true"` faz o leitor anunciar "inválido" em campos que estão perfeitamente corretos.

### 2. Anunciar mensagens dinâmicas com regiões *live*

O maior desafio das notificações modernas é este: muitas aparecem **sem a página recarregar** (validação em JavaScript, confirmações via AJAX). O leitor de ecrã, por omissão, não repara em texto que "surge" no ecrã. Precisamos de o avisar. Isso faz-se com **regiões live** (`aria-live`) ou com *roles* que já são regiões live por natureza (`role="alert"` e `role="status"`).

> **Analogia — o altifalante da estação**
> Uma região live é como o altifalante de uma estação de comboios. Escreve-se algo lá dentro e o leitor de ecrã "lê em voz alta" o que apareceu, mesmo que a pessoa esteja concentrada noutra parte da página. Sem o altifalante, o aviso está escrito num painel para que ninguém está a olhar.

Há duas "intensidades":

- **`role="status"`** (equivale a `aria-live="polite"`) — o leitor espera que a pessoa termine o que está a dizer e só depois anuncia. Ideal para mensagens **não urgentes**: "A guardar…", "5 resultados encontrados", "Alterações guardadas".
- **`role="alert"`** (equivale a `aria-live="assertive"`) — **interrompe** o leitor para anunciar de imediato. Reservado para mensagens **importantes e imediatas**, sobretudo erros que impedem a pessoa de continuar.

```html
<!-- Confirmação discreta: usa status/polite -->
<div role="status">
  Alterações guardadas com sucesso.
</div>

<!-- Erro que impede o envio: usa alert/assertive -->
<div role="alert">
  Não foi possível submeter o formulário. Corrija os 2 campos assinalados.
</div>
```

**O que funciona bem:** ao usar `role="alert"` para o erro de submissão, a pessoa que carregou em "Submeter" ouve imediatamente que algo falhou, mesmo estando o cursor no botão. Ao usar `role="status"` para a confirmação, o "guardado com sucesso" é lido sem interromper bruscamente.

**O que correria mal:** usar `role="alert"` para **tudo** (incluindo "A guardar…") transforma o formulário numa metralhadora de interrupções. O leitor de ecrã é cortado a cada passo e a pessoa não consegue ouvir nada até ao fim. É o equivalente a alguém que grita todas as frases. Por outro lado, pôr o erro grave num `role="status"` (polite) pode fazer com que a pessoa continue a preencher sem nunca ouvir que a submissão falhou.

> **Pormenor técnico que causa muitos bugs:** a região live tem de **já existir na página, vazia**, antes de lá colocar texto. Muitos leitores de ecrã não anunciam nada se o elemento com `role="alert"` for criado *e* preenchido no mesmo instante. O padrão fiável é: ter o contentor vazio no HTML desde o início e, quando houver mensagem, **inserir o texto lá dentro** por JavaScript.

```html
<!-- Este contentor existe desde o início, vazio -->
<div id="area-notificacoes" role="status" aria-live="polite"></div>
```

```javascript
// Mais tarde, quando a ação terminar:
document.getElementById("area-notificacoes").textContent =
  "Inscrição submetida. Vai receber um e-mail de confirmação.";
```

### 3. Resumo de erros no topo do formulário

Quando um formulário longo é submetido com vários erros, é boa prática mostrar, no topo, um **resumo** com a lista dos problemas — e cada item deve ser uma **ligação** que leva ao campo correspondente.

```html
<div role="alert" tabindex="-1" id="resumo-erros">
  <h2>Existem 2 problemas por corrigir</h2>
  <ul>
    <li><a href="#nif">O NIF tem de ter 9 dígitos.</a></li>
    <li><a href="#email">O e-mail não tem um formato válido.</a></li>
  </ul>
</div>
```

Depois de submeter, o código deve **mover o foco** para este resumo (por isso o `tabindex="-1"`, que permite receber foco por programação):

```javascript
document.getElementById("resumo-erros").focus();
```

**O que funciona bem:** a pessoa que usa teclado ou leitor de ecrã, ao carregar em "Submeter", é levada diretamente para o resumo, ouve *"Existem 2 problemas por corrigir"* e pode saltar campo a campo através das ligações. Não precisa de percorrer o formulário inteiro à procura do que falhou. É especialmente útil em formulários longos.

**O que correria mal:** apresentar o resumo mas deixar o foco no botão "Submeter" (ou pior, no topo, mas sem foco) — a pessoa é obrigada a "adivinhar" que apareceu um resumo algures. E se as ligações do resumo não apontarem mesmo para os campos (`href="#nif"` sem um campo com `id="nif"`), tornam-se becos sem saída.

### 4. Não deixar a mensagem depender só da cor

Do lado do código/estilo, garanta que o estado de erro é sinalizado por **mais do que a cor**: um ícone, texto explícito, um contorno mais espesso, uma marca `⚠`.

```html
<label for="telefone">Telefone</label>
<input type="tel" id="telefone" aria-describedby="erro-telefone" aria-invalid="true">
<p id="erro-telefone" class="mensagem-erro">
  <span aria-hidden="true">⚠ </span>
  Introduza um número com 9 dígitos, sem espaços.
</p>
```

**O que funciona bem:** aqui o erro é comunicado por texto claro *e* por um ícone. O `aria-hidden="true"` no ícone evita que o leitor de ecrã leia o símbolo de forma estranha (por exemplo, "sinal de aviso"), enquanto quem vê beneficia do reforço visual. A mensagem funciona a preto e branco, com cor, ampliada ou lida em voz alta.

**O que correria mal:** confiar apenas numa classe CSS que pinta o campo de vermelho. Para muita gente, esse vermelho é indistinguível. E para o leitor de ecrã, a cor simplesmente não existe.

---

## Recomendações para Conteúdo Acessível

A técnica coloca a mensagem no sítio certo e fá-la ser anunciada. Mas o **texto** da mensagem também tem de estar bem escrito. Uma mensagem tecnicamente perfeita que diz *"Erro de validação"* continua a não ajudar ninguém.

**Diga o que está errado E o que fazer.**
Uma boa mensagem responde a duas perguntas: *o que aconteceu?* e *o que faço agora?*

- Fraco: *"Palavra-passe inválida."*
- Bom: *"A palavra-passe tem de ter, no mínimo, 8 caracteres. A que introduziu tem 5."*

**Use linguagem simples e sem jargão.**
Evite códigos de erro, termos técnicos e frases na negativa dupla. Escreva como falaria a uma pessoa ao balcão.

- Fraco: *"O input não corresponde ao pattern esperado."*
- Bom: *"A data tem de estar no formato dia/mês/ano. Exemplo: 25/12/2025."*

**Seja específico quanto ao campo.**
*"Preencha os campos obrigatórios"* obriga a pessoa a procurar quais são. *"O campo Morada está vazio"* aponta diretamente.

**Mantenha um tom neutro e construtivo.**
A pessoa não fez nada de mal; encontrou uma dificuldade. Evite culpar (*"Introduziu mal os dados!"*) e prefira orientar (*"Confirme o número de contribuinte — deve ter 9 dígitos."*).

**Não use a mensagem para envergonhar nem para brincadeiras.**
Mensagens "engraçadas" ou dramáticas confundem quem lê literalmente e atrasam quem só quer resolver o problema.

**Confirme sempre o sucesso.**
Tão importante como avisar de erros é **confirmar que correu bem**. Depois de submeter, a pessoa precisa de ouvir/ver *"Pedido submetido"*. Sem confirmação, fica na dúvida e muitas vezes submete de novo.

**Dê tempo para ler.**
Mensagens que desaparecem sozinhas ("toast" que some ao fim de 3 segundos) prejudicam quem lê devagar ou navega com leitor de ecrã. Se usar mensagens temporárias, dê tempo generoso, deixe a pessoa fechá-las manualmente, ou mantenha a informação disponível noutro sítio.

> **Analogia — o GPS**
> Um bom GPS nunca diz apenas *"errou o caminho"*. Diz *"a recalcular… na próxima rotunda, vire à direita"*. Reconhece o problema **e** dá logo o próximo passo. As melhores mensagens de erro comportam-se como um bom GPS: em vez de castigar o erro, orientam para a saída.

### Erros Comuns

Reunimos aqui os enganos que aparecem vezes sem conta. Vale a pena usar esta lista como "o que **não** fazer".

**1. Sinalizar o erro só com cor.**
O campo fica vermelho e mais nada. Invisível para quem não vê ou não distingue a cor.
*Correção:* juntar sempre texto e/ou ícone à cor.

**2. Mensagens genéricas.**
*"Ocorreu um erro."* / *"Dados inválidos."* Não dizem qual campo nem o quê.
*Correção:* identificar o campo e descrever o problema concreto.

**3. Erros que o leitor de ecrã nunca anuncia.**
A mensagem aparece por JavaScript, mas fora de uma região live. Quem vê, pode reparar; quem usa leitor de ecrã, não.
*Correção:* usar `role="alert"` / `role="status"` (ou `aria-live`) e ligar o erro ao campo com `aria-describedby`.

**4. Usar o *placeholder* como mensagem de erro (ou como rótulo).**
O texto cinzento dentro do campo desaparece assim que a pessoa escreve — e muitos leitores de ecrã nem o leem de forma fiável. Não serve para transmitir erros nem instruções essenciais.
*Correção:* colocar o erro num elemento próprio, visível e ligado por `aria-describedby`.

**5. Notificações apenas sonoras.**
Um "bip" quando algo falha exclui quem não ouve — e nem toda a gente tem o som ligado.
*Correção:* a informação tem de estar sempre também em texto/visual.

**6. Mensagens que desaparecem depressa demais.**
O "toast" desaparece antes de a pessoa o ler ou de o leitor de ecrã o anunciar.
*Correção:* dar tempo suficiente, permitir fechar manualmente e não fazer depender ações críticas de mensagens efémeras.

**7. Abusar do `assertive` / `role="alert"`.**
Marcar tudo como urgente faz o leitor de ecrã interromper-se a cada passo, e a pessoa deixa de ouvir seja o que for.
*Correção:* reservar `alert`/`assertive` para o que é mesmo urgente; usar `status`/`polite` para o resto.

**8. Mostrar erros só depois de submeter, sem levar a pessoa até eles.**
O resumo aparece, mas o foco fica no botão e ninguém é conduzido aos campos.
*Correção:* mover o foco para o resumo de erros e ligar cada item ao respetivo campo.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- As notificações e mensagens de erro são a **resposta do sistema** dentro da conversa que é o formulário. Se essa resposta não chegar a toda a gente, a pessoa fica bloqueada.
- Uma boa mensagem cumpre cinco requisitos: **identifica** o campo, **descreve** o problema em texto, **sugere** a correção, **não depende só da cor** e é **anunciada** às tecnologias de apoio.
- Ligue cada erro ao seu campo com **`aria-describedby`** e marque o campo com **`aria-invalid="true"`** apenas enquanto o erro existir.
- Faça as mensagens dinâmicas serem anunciadas com **regiões live**: `role="status"` (polite) para avisos calmos, `role="alert"` (assertive) para o que é urgente. O contentor deve existir vazio antes de receber texto.
- Em formulários longos, ofereça um **resumo de erros** no topo, com ligações para os campos, e **mova o foco** para lá após a submissão.
- Escreva as mensagens em **linguagem simples**, dizendo o que aconteceu e o que fazer. Confirme sempre o **sucesso**, e dê **tempo** para ler.
- Nunca dependa de um único canal: a mesma informação deve estar disponível por **texto, cor/forma e anúncio sonoro (leitor de ecrã)** ao mesmo tempo.

### Exercícios Práticos

**Exercício 1 — Reescrever mensagens**
As mensagens seguintes são reais e todas problemáticas. Reescreva cada uma cumprindo as recomendações apresentadas antes (identificar, descrever, sugerir):

1. *"Erro."*
2. *"Campo inválido."*
3. *"E-mail incorreto."*
4. *"Preencha os campos obrigatórios."*

*Sugestão de resolução para a 3:* «O e-mail tem de incluir o símbolo @ e um domínio. Exemplo: nome@dominio.pt.»

**Exercício 2 — Ligar o erro ao campo**
Dado o campo abaixo, acrescente o que falta para que um leitor de ecrã anuncie o erro ao chegar ao campo. Deve usar `aria-describedby` e `aria-invalid`.

```html
<label for="nif">Número de Identificação Fiscal</label>
<input type="text" id="nif" name="nif">
<p>O NIF tem de ter 9 dígitos.</p>
```

**Exercício 3 — Escolher a intensidade certa**
Para cada notificação, indique se deve usar `role="status"` (polite) ou `role="alert"` (assertive) e justifique:

1. "A carregar os seus dados…"
2. "Não foi possível guardar. Verifique a sua ligação à Internet."
3. "Foram encontrados 12 resultados."
4. "A sessão vai terminar em 60 segundos por inatividade."

**Exercício 4 — Auditoria com o teclado e sem cor**
Escolha um formulário real (por exemplo, um formulário público de inscrição). Submeta-o com erros de propósito e responda:

1. Consegue perceber que há um erro **sem olhar para a cor** (por exemplo, num ecrã a preto e branco)?
2. Navegando **só com o teclado**, é levado até ao erro ou tem de o procurar?
3. Se tiver um leitor de ecrã disponível, o erro é **anunciado** ou fica em silêncio?
4. Depois de corrigir e submeter, recebe uma **confirmação de sucesso** clara?

Registe cada falha encontrada e proponha a correção correspondente com base neste capítulo.

**Exercício 5 — Construir uma região live**
Crie um pequeno formulário com um único campo "Nome" e um botão "Guardar". Ao carregar em "Guardar":

- se o campo estiver vazio, mostre um erro anunciado com `role="alert"`;
- se estiver preenchido, mostre "Nome guardado com sucesso" com `role="status"`.

Lembre-se de que o contentor da mensagem deve existir **vazio** no HTML antes de receber o texto.

# Múltiplos Passos

## Introdução

Alguns formulários são demasiado longos ou complexos para caberem confortavelmente num único ecrã. Pense num pedido de subsídio, na compra de um bilhete de avião ou na abertura de uma conta bancária online. Nestes casos, é frequente dividir o formulário em **várias etapas** (ou passos), apresentadas uma de cada vez.

Uma boa analogia é a de um formulário em papel com **várias folhas agrafadas**: preenche a primeira folha, vira a página, preenche a segunda, e assim sucessivamente. No papel, esta divisão é natural: sentimos a espessura do maço, vemos quantas folhas faltam e podemos folhear para trás para reler o que escrevemos. Num ecrã, nada disto acontece de forma automática. Se não o programarmos com cuidado, a pessoa fica sem saber em que passo está, quantos faltam, ou como voltar atrás sem perder o que já escreveu.

Esta secção trata daquilo que é **exclusivo** dos formulários com múltiplos passos: indicar o progresso, gerir o foco entre passos, preservar os dados já introduzidos, permitir rever antes de submeter e lidar com limites de tempo. 

### Como as Pessoas com Deficiência usam Formulários com Múltiplos Passos

A divisão de um formulário em etapas pode **ajudar** ou **prejudicar** muito, dependendo de como é feita. Vejamos como diferentes pessoas experienciam estes formulários.

**Pessoas cegas ou com baixa visão, que usam leitores de ecrã.** Um leitor de ecrã lê o conteúdo de cima para baixo e comunica ao utilizador aquilo que tem "foco". Quando a pessoa carrega em "Seguinte" e a página muda de passo, o leitor de ecrã **não avisa automaticamente** que houve uma mudança, a não ser que a mudança corresponda ao carregamento de uma nova página. Se o foco ficar "preso" no botão que desapareceu, a pessoa pode continuar a ouvir silêncio ou a pensar que nada aconteceu. Ela precisa de sinais claros: onde começa o novo passo, qual é o número do passo e quantos faltam.

**Pessoas com deficiência motora, que navegam só com teclado.** Estas pessoas movem-se pelo formulário com a tecla `Tab` e ativam botões com `Enter` ou `Espaço`. Um formulário longo, dividido em passos curtos, pode até ser mais confortável para elas, porque há menos campos por ecrã. Mas tudo se estraga se, ao mudar de passo, o foco saltar para um sítio inesperado (por exemplo, para o topo do menu do site), obrigando a percorrer dezenas de ligações com `Tab` até reencontrar o formulário.

**Pessoas com deficiência cognitiva ou dificuldades de atenção e memória.** São, provavelmente, quem mais beneficia da divisão em passos, desde que cada passo seja pequeno e focado numa só tarefa ("Agora só os seus dados de contacto"). Ao mesmo tempo, são também quem mais sofre quando o formulário perde os dados a meio, quando não é possível voltar atrás para confirmar algo, ou quando a pessoa não faz ideia de quanto ainda falta. A incerteza ("será que estou quase a acabar?") gera ansiedade e leva ao abandono.

**Pessoas com pouca destreza ou que preenchem devagar.** Quem escreve lentamente — por usar um teclado adaptado, comando de voz ou por qualquer outra razão — corre o risco de **esgotar o tempo da sessão** a meio de um formulário longo, perdendo tudo o que já tinha introduzido.

> **Analogia — o formulário como uma viagem de comboio.** Um formulário de vários passos é como uma viagem com transbordos. O passageiro precisa de saber três coisas: **em que estação está** (passo atual), **quantas estações faltam** (progresso) e **como voltar à estação anterior** se se enganou (navegação para trás). Sem esta informação, mesmo um passageiro experiente sente-se perdido; para quem depende de um leitor de ecrã, é como viajar sem qualquer anúncio de paragens.

### Requisitos de Acessibilidade para Formulários com Múltiplos Passos

Para que um formulário de vários passos seja acessível, deve cumprir um conjunto de requisitos próprios desta estrutura:

1. **Indicar o progresso de forma percetível.** A pessoa deve conseguir saber, a qualquer momento, em que passo está e quantos passos existem no total — e essa informação não pode depender apenas da cor ou da posição visual.

2. **Gerir o foco a cada mudança de passo.** Quando um novo passo aparece, o foco do teclado deve ser deslocado para um ponto lógico do novo passo (habitualmente o seu título), para que utilizadores de teclado e de leitor de ecrã percebam que avançaram.

3. **Anunciar a mudança a tecnologias de apoio.** A transição de passo deve ser comunicada aos leitores de ecrã, seja através da deslocação do foco para um título, seja através de uma mensagem de estado.

4. **Preservar os dados entre passos.** Voltar atrás não pode apagar o que já foi preenchido. Igualmente, a informação já dada num passo não deve ter de ser reintroduzida noutro.

5. **Permitir rever e corrigir antes de submeter.** Em formulários que envolvem compromissos legais, transações financeiras ou dados que não podem ser facilmente apagados, é necessário oferecer um passo de revisão, ou uma forma de confirmar e corrigir antes da submissão final.

6. **Respeitar o tempo do utilizador.** Se existir um limite de tempo de sessão, é preciso avisar com antecedência e permitir prolongá-lo, evitando a perda dos dados já introduzidos.

7. **Manter uma ordem e navegação previsíveis.** Os botões de avançar e recuar devem estar sempre no mesmo sítio e comportar-se de forma consistente em todos os passos.

## Técnicas de Codificação

Nesta secção mostramos padrões de código focados no que distingue os formulários de vários passos. Os campos, rótulos e mensagens de erro seguem as técnicas das secções respetivas; aqui interessa-nos a **moldura** que os envolve.

### Indicador de progresso (o "stepper")

O indicador de progresso deve comunicar a mesma informação a quem vê e a quem não vê. Uma técnica simples e robusta é usar uma lista com o passo atual marcado por `aria-current="step"`.

```html
<nav aria-label="Progresso do formulário">
  <ol class="passos">
    <li>
      <span class="visualmente-oculto">Concluído:</span> 1. Dados pessoais
    </li>
    <li aria-current="step">
      <span class="visualmente-oculto">Passo atual:</span> 2. Morada
    </li>
    <li>3. Pagamento</li>
    <li>4. Confirmação</li>
  </ol>
</nav>
```

**O que funciona bem neste exemplo**: o elemento `<nav>` com `aria-label` agrupa e nomeia a área de progresso, o `<ol>` transmite que há uma sequência ordenada e o `aria-current="step"` faz o leitor de ecrã anunciar "passo atual" ao chegar ao item 2. Além disso, a lista existe **como texto**, por isso funciona mesmo que a cor ou os ícones não sejam percetíveis. A classe `visualmente-oculto` (texto que só é lido por tecnologias de apoio) reforça o significado sem sobrecarregar visualmente o ecrã.

**O que correria mal**: se o progresso fosse desenhado apenas com círculos coloridos e uma linha, sem qualquer texto, uma pessoa com um leitor de ecrã não saberia sequer que existe um indicador de progresso, e uma pessoa daltónica poderia não distinguir o passo "feito" do passo "por fazer".

### Anunciar o número do passo

Além do indicador visual, é boa prática dar a cada passo um **título claro que inclua a sua posição na sequência**. Este título servirá também para gerir o foco (ver adiante).

```html
<h2 id="titulo-passo" tabindex="-1">Passo 2 de 4: Morada</h2>
```

**O que funciona bem**: o texto "Passo 2 de 4" dá, numa só frase, a posição e o total. O `tabindex="-1"` permite que o título receba foco por programação (sem entrar na ordem normal de tabulação), o que é essencial para a gestão de foco descrita a seguir.

### Gerir o foco na mudança de passo

Este é o ponto mais crítico e mais esquecido. Quando a pessoa avança de passo, devemos mover o foco para o título do novo passo. Assim, o leitor de ecrã lê imediatamente "Passo 3 de 4: Pagamento" e o utilizador de teclado começa no sítio certo.

```html
<button type="button" id="btn-seguinte">Seguinte</button>

<script>
  document.getElementById('btn-seguinte').addEventListener('click', function () {
    mostrarPasso(3); // função que troca o conteúdo visível

    // Depois de o novo passo estar no ecrã, colocar o foco no seu título:
    var titulo = document.getElementById('titulo-passo');
    titulo.focus();
  });
</script>
```

**O que funciona bem**: ao dar `focus()` ao título, garantimos que utilizadores de teclado e de leitor de ecrã "aterram" no início do novo passo, sem terem de o procurar. É o equivalente digital de um guia turístico que, ao entrar numa nova sala, nos diz "estamos agora na Sala 3, dedicada a...".

**O que correria mal**: **não fazer nada** com o foco. Nesse caso, o foco pode ficar no botão "Seguinte" — que muitas vezes já nem existe no novo passo — ou saltar para o topo do documento. O utilizador de leitor de ecrã ouve silêncio e pensa que a ação falhou, ou tem de "explorar" a página para perceber o que mudou.

### Não perder dados ao recuar (e não repetir perguntas)

Voltar atrás para corrigir uma resposta não pode apagar tudo o resto. Numa aplicação que troca de passo sem recarregar a página, isto consegue-se guardando os valores em memória e voltando a preenchê-los.

```html
<script>
  // Objeto que guarda o que já foi preenchido
  var dadosFormulario = {};

  // Antes de trocar de passo, guardar o que a pessoa escreveu
  function guardarPassoAtual(passo) {
    document.querySelectorAll('#' + passo + ' input, #' + passo + ' select')
      .forEach(function (campo) {
        dadosFormulario[campo.name] = campo.value;
      });
  }

  // Ao mostrar um passo, repor os valores guardados
  function reporValores(passo) {
    document.querySelectorAll('#' + passo + ' input, #' + passo + ' select')
      .forEach(function (campo) {
        if (dadosFormulario[campo.name] !== undefined) {
          campo.value = dadosFormulario[campo.name];
        }
      });
  }
</script>
```

**O que funciona bem**: quando a pessoa recua e volta a avançar, encontra tudo tal como o deixou. Este mesmo princípio evita a **reintrodução redundante**: se o campo "nome" já foi preenchido no passo 1, não deve voltar a ser pedido no passo 3. Quando é mesmo necessário reutilizar um valor (por exemplo, "a morada de faturação é a mesma da entrega?"), ofereça uma caixa de verificação que copie o valor automaticamente, em vez de obrigar a escrever tudo de novo.

**O que correria mal**: reconstruir o passo do zero de cada vez, deixando os campos vazios. A pessoa carrega em "Anterior" só para confirmar uma coisa e, ao voltar, descobre que perdeu meia hora de trabalho. Para quem tem dificuldades de memória ou de destreza, isto é motivo suficiente para desistir.

### Passo de revisão antes de submeter

Em formulários com consequências sérias (pagamentos, candidaturas, alterações de dados), acrescente um passo final onde tudo é apresentado para revisão, com ligações que permitem voltar a cada secção para corrigir.

```html
<h2 tabindex="-1">Passo 4 de 4: Confirme os seus dados</h2>

<h3>Dados pessoais <a href="#passo1">Editar</a></h3>
<p>Nome: Maria Silva</p>
<p>E-mail: maria.silva@exemplo.pt</p>

<h3>Morada <a href="#passo2">Editar</a></h3>
<p>Rua das Flores, 12, 1000-001 Lisboa</p>

<button type="submit">Confirmar e submeter</button>
```

**O que funciona bem**: a pessoa vê tudo reunido antes do passo irreversível e cada bloco tem uma ligação "Editar" que a leva ao passo certo — sem perder os restantes dados. A submissão só acontece quando ela carrega, conscientemente, em "Confirmar e submeter".

**O que correria mal**: submeter automaticamente ao chegar ao último campo, sem qualquer confirmação. Um clique acidental, ou um comando de voz mal interpretado, poderia concluir uma compra ou uma candidatura sem que a pessoa tivesse tido oportunidade de rever.

### Avisar antes de a sessão terminar

Se o formulário tem um limite de tempo (por segurança ou por regra do sistema), avise antes de o tempo acabar e ofereça a opção de continuar.

```html
<div role="alertdialog" aria-labelledby="aviso-titulo" aria-describedby="aviso-texto">
  <h2 id="aviso-titulo">A sua sessão está prestes a expirar</h2>
  <p id="aviso-texto">
    Por inatividade, a sessão termina dentro de 2 minutos.
    Os dados já introduzidos serão guardados.
  </p>
  <button type="button">Continuar a preencher</button>
</div>
```

**O que funciona bem**: o `role="alertdialog"` faz o leitor de ecrã anunciar o aviso de imediato e leva o foco para dentro da caixa, para que qualquer pessoa possa reagir a tempo. A mensagem indica claramente quanto tempo resta e tranquiliza sobre a preservação dos dados.

**O que correria mal**: terminar a sessão sem aviso e sem guardar nada. Uma pessoa que escreve devagar veria o seu trabalho desaparecer, muitas vezes sem sequer perceber porquê.

## Recomendações para Conteúdo Acessível

Além do código, o conteúdo e o desenho dos passos fazem toda a diferença:

- **Um passo, uma ideia.** Agrupe campos relacionados e dê a cada passo um objetivo único e claro no título ("Dados de contacto", "Método de pagamento"). Passos curtos e temáticos são mais fáceis de compreender e de completar.

- **Diga sempre onde a pessoa está e quanto falta.** "Passo 2 de 4" vale mais do que uma barra colorida sem números. Se o número total de passos for incerto, seja honesto ("Passo 2 — faltam ainda os dados de pagamento").

- **Valide cada passo no momento certo.** Verificar os campos ao concluir cada passo evita que a pessoa chegue ao fim e seja "atirada" de volta ao início. 

- **Botões consistentes e bem nomeados.** "Anterior" e "Seguinte" devem estar sempre no mesmo sítio. No último passo, o botão de avançar deve mudar para algo explícito como "Confirmar e submeter", para que ninguém submeta sem querer.

- **Permita guardar e continuar mais tarde**, sempre que o formulário for longo. É a rede de segurança para quem é interrompido ou preenche em várias sessões.

- **Deixe recuar sem penalização.** Voltar atrás deve ser tão fácil e seguro como avançar.

### Erros Comuns

- **Não gerir o foco.** O erro mais frequente: mudar de passo e deixar o foco no vazio. Utilizadores de leitor de ecrã não percebem que avançaram.
- **Indicar o progresso só com cor ou ícones.** Sem texto ("Passo 2 de 4"), a informação é inacessível a quem não vê o ecrã ou não distingue cores.
- **Apagar dados ao recuar.** Punir quem volta atrás para confirmar algo é uma das causas mais comuns de abandono.
- **Pedir a mesma informação em vários passos.** Reintroduzir dados já dados é desnecessário e cansativo; deve evitar-se sempre que possível.
- **Submeter sem revisão nem confirmação** em formulários com consequências sérias.
- **Terminar a sessão sem aviso**, perdendo tudo o que já tinha sido preenchido.
- **Mudar os botões de sítio entre passos**, obrigando a pessoa a reorientar-se a cada etapa.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Dividir um formulário longo em passos **ajuda** a compreensão, mas só se a pessoa souber sempre onde está, quanto falta e como voltar atrás.
- O **indicador de progresso** deve ser textual e percetível a todos, não apenas visual (`aria-current="step"`, "Passo X de Y").
- A **gestão do foco** a cada mudança de passo é indispensável: mover o foco para o título do novo passo é a técnica mais fiável.
- **Preservar os dados** entre passos e **não repetir perguntas** respeita o tempo e o esforço do utilizador.
- Formulários com consequências sérias precisam de um **passo de revisão** e de confirmação explícita antes da submissão.
- **Limites de tempo** exigem aviso antecipado, opção de continuar e preservação dos dados.

### Exercícios Práticos

1. **Detetar problemas de foco.** Abra um formulário de vários passos (por exemplo, um processo de compra). Preencha o primeiro passo apenas com o teclado e carregue em "Seguinte". Sem tocar no rato, verifique: onde ficou o foco? Se possível, repita com um leitor de ecrã ativo e anote se a mudança de passo foi anunciada.

2. **Testar a preservação de dados.** Preencha até ao terceiro passo de um formulário, carregue em "Anterior" duas vezes e volte a avançar. Os seus dados mantiveram-se? Descreva o que aconteceu e o impacto que isso teria numa pessoa com dificuldades de memória.

3. **Escrever um indicador de progresso acessível.** Crie o HTML de um indicador de progresso de 3 passos, em que o passo 2 é o atual. Use `aria-current` e inclua texto que identifique a posição e o total. Explique, em duas frases, porque é que a sua solução funciona também para quem não vê o ecrã.

4. **Desenhar um passo de revisão.** Para um formulário de candidatura com três secções (dados pessoais, formação, motivação), esboce o ecrã de revisão final. Indique onde colocaria as ligações "Editar" e como garantiria que ninguém submete sem confirmar.

5. **Analisar um caso real.** Escolha um serviço público ou uma loja online com formulário de vários passos. Preencha-o e avalie-o face aos sete requisitos desta lição (progresso, foco, anúncio, preservação de dados, revisão, tempo e navegação consistente). Identifique um ponto forte e o problema mais grave que encontrou.

# Conclusão e Boas Práticas

Ao longo deste módulo, olhámos para os formulários peça a peça: a forma como as pessoas com deficiência os utilizam, a estrutura e o posicionamento dos campos, os rótulos e instruções, as notificações e mensagens de erro, e os formulários com múltiplos passos.

Esta secção não introduz técnicas novas. Serve para **juntar tudo**, ver como as peças encaixam umas nas outras e ficar com um conjunto de ferramentas práticas — uma lista de verificação, exercícios e referências — que pode usar no dia a dia.

Uma analogia útil para começar: um formulário acessível é como uma **boa receita de cozinha**. Cada ingrediente (rótulo, campo, mensagem de erro) importa, mas o que faz a receita resultar é a **ordem** em que se juntam e a forma como se relacionam. Se tudo estiver tecnicamente lá, mas mal combinado, o prato não sai bem — e, num formulário, "não sair bem" significa uma pessoa que fica de fora.

---

## Recapitulação

A melhor forma de recapitular não é repetir cada capítulo, mas seguir **uma pessoa a preencher um formulário do início ao fim** e ver onde cada tema entra em jogo.

### Um percurso do princípio ao fim

Imaginemos a Sofia, uma utilizadora cega que usa um leitor de ecrã, a inscrever-se num serviço público através de um formulário com dois passos.

1. **Ela chega ao formulário e precisa de perceber o que tem pela frente.** É aqui que entra a **estrutura e o posicionamento**: os campos aparecem numa ordem lógica, agrupados por assunto (dados pessoais, depois dados de contacto), e a ordem em que o leitor de ecrã os lê é a mesma ordem em que aparecem no ecrã. Se a estrutura estivesse baralhada, a Sofia ouviria os campos numa sequência sem sentido.

2. **Em cada campo, ela precisa de saber o que lhe é pedido.** É o papel dos **rótulos e instruções**. Ao chegar ao campo do NIF, o leitor de ecrã anuncia "NIF, 9 dígitos, sem espaços". A Sofia sabe exatamente o que escrever, sem ter de adivinhar.

3. **Ela engana-se num campo — escreve um e-mail sem o `@`.** Agora entram as **notificações e mensagens de erro**. O sistema avisa-a de forma clara, diz-lhe *qual* o campo com problema e *como* o corrigir, e o leitor de ecrã anuncia esse aviso sem ela ter de o procurar.

4. **Corrigido o erro, ela avança para o segundo passo.** Aqui aplica-se tudo o que vimos sobre **múltiplos passos**: ela sabe que está no passo 2 de 2, o que já preencheu não se perdeu, e pode voltar atrás se precisar.

O ponto-chave é este: **cada tema deste módulo resolve um momento diferente da mesma experiência**. Falhar num deles chega para bloquear a Sofia, por muito bem feito que esteja o resto.

### Os fios que ligam tudo

Se recuarmos e olharmos para as cinco secções ao mesmo tempo, há quatro princípios que atravessam todas. Vale a pena guardá-los, porque funcionam como uma bússola quando surge uma situação nova:

- **Percetível** — a informação existe de mais do que uma maneira. Um erro não é assinalado só com a cor vermelha; tem também texto. Um campo obrigatório não se distingue só por um asterisco visual; a obrigatoriedade é transmitida também ao leitor de ecrã.
- **Operável pelo teclado** — tudo o que se faz com o rato tem de se poder fazer só com o teclado, na tecla `Tab` e na tecla `Enter`. Muitas pessoas não usam rato de todo.
- **Previsível** — o formulário não surpreende o utilizador. Nada muda de página nem submete dados só porque a pessoa entrou num campo ou selecionou uma opção.
- **Tolerante ao erro** — as pessoas enganam-se, e isso é normal. Um bom formulário assume o erro à partida e ajuda a corrigi-lo, em vez de castigar quem se engana.

Sempre que tiver uma dúvida sobre um caso que não está nos manuais, faça a pergunta por estes quatro filtros. Na grande maioria das vezes, a resposta certa aparece sozinha.

### Exemplo integrado: as peças a encaixar num só campo

Para ver a integração na prática, repare como um único campo bem construído reúne o trabalho de várias secções ao mesmo tempo:

```html
<label for="email">Endereço de e-mail</label>
<input
  id="email"
  name="email"
  type="email"
  autocomplete="email"
  aria-describedby="email-ajuda email-erro"
  aria-invalid="true"
/>
<p id="email-ajuda">Vamos usar este e-mail para lhe enviar a confirmação.</p>
<p id="email-erro">Falta o símbolo @. Exemplo: nome@exemplo.pt</p>
```

**O que funciona bem neste exemplo:**

- O `<label>` está ligado ao campo pelo `for`/`id`, por isso o leitor de ecrã anuncia o nome do campo (tema dos *rótulos*).
- O `type="email"` e o `autocomplete="email"` dizem ao navegador e às tecnologias de apoio que tipo de dado é este, o que permite o preenchimento automático (tema da *estrutura e posicionamento* e dos *rótulos*).
- O `aria-describedby` liga o campo tanto à instrução de ajuda como à mensagem de erro, por isso ambas são lidas sem a pessoa ter de as ir procurar (temas das *instruções* e das *mensagens de erro*).
- O `aria-invalid="true"` marca o campo como estando com erro, de forma percetível também por quem não vê a cor (tema das *mensagens de erro*).

Repare que nada aqui é decorativo: cada atributo resolve um problema concreto de uma pessoa concreta. É esta a diferença entre um formulário que "parece" acessível e um que é mesmo acessível.

---

## Recursos Adicionais

- **acessibilidade.gov.pt** — o portal oficial do ecossistema de acessibilidade da Administração Pública. Tem tutoriais em português, ferramentas e o blogue da equipa, atualizado com frequência.

- **W3C WAI — Tutorial de Formulários** (`w3.org/WAI/tutorials/forms/`) — provavelmente o melhor recurso gratuito sobre formulários acessíveis, com exemplos comentados. 
- **ARIA Authoring Practices Guide (APG)** (`w3.org/WAI/ARIA/apg/`) — padrões para componentes mais complexos (por exemplo, campos de pesquisa com sugestões). Regra de ouro: use ARIA só quando o HTML nativo não chega.

---

## Exercícios de Consolidação

Estes exercícios são diferentes dos que fez em cada capítulo. Ali, treinou um tema de cada vez. Aqui, o objetivo é **juntar tudo**, como acontece num projeto real, onde nunca há só um problema isolado.

### Exercício 1 — Auditar um formulário existente

Escolha um formulário real de um serviço que use (a inscrição num evento, um pedido de contacto, etc.). Faça três testes, por esta ordem:

1. **Teste com o teclado.** Guarde o rato e navegue o formulário inteiro só com `Tab`, `Shift+Tab`, setas e `Enter`. Consegue chegar a todos os campos e submeter? Vê sempre onde está o foco?
2. **Teste automático.** Passe a página pelo AccessMonitor ou pelo WAVE e leia os alertas.
3. **Teste com leitor de ecrã.** Ative o leitor de ecrã do seu sistema e feche os olhos ao percorrer o formulário. Cada campo diz-lhe o que é pedido?

**Objetivo:** listar 5 problemas. Este exercício mostra uma lição importante — o teste automático sozinho **não chega**.

### Exercício 2 — Construir de raiz

Crie um formulário de inscrição completo com, no mínimo: nome, e-mail, NIF, uma escolha entre opções (por exemplo, tipo de bilhete) e um campo de observações. Aplique **todos** as secções: estrutura lógica, rótulos e instruções, tratamento de erros e, se dividir em passos, indicação clara de progresso.

**Objetivo:** no fim, percorra a sua própria lista de verificação final (mais abaixo) e confirme que cada item está cumprido.

### Exercício 3 — Reparar um formulário partido

Analise o exemplo seguinte, que tem vários problemas de propósito:

```html
<form>
  Nome <input type="text"><br>
  <input type="text" placeholder="Escreva aqui o seu e-mail"><br>
  <span style="color: red;">Preencha tudo!</span><br>
  <div onclick="enviar()">Enviar</div>
</form>
```

**O que está mal neste exemplo:**

- O texto "Nome" não é um `<label>` ligado ao campo — é texto solto, invisível para o leitor de ecrã enquanto rótulo.
- O campo de e-mail usa `placeholder` em vez de rótulo; o texto de ajuda desaparece assim que a pessoa começa a escrever, e muitos leitores de ecrã não o leem de forma fiável.
- A mensagem de erro depende **apenas da cor** vermelha, é genérica ("Preencha tudo!") e não indica qual o campo com problema.
- O botão de enviar é uma `<div>` com `onclick`. Não é alcançável nem acionável pelo teclado — quem não usa rato fica bloqueado.

**Objetivo:** reescreva este formulário corrigindo os quatro problemas. Compare depois a sua versão com o exemplo integrado da secção de recapitulação.

---

## Lista de Verificação Final

Use esta lista antes de dar um formulário por concluído. Está organizada pelos temas do módulo. Não substitui os testes reais (teclado e leitor de ecrã), mas garante que nada óbvio ficou por fazer.

**Estrutura e posicionamento**

- [ ] Os campos aparecem numa ordem lógica e a ordem de leitura (foco) acompanha a ordem visual.
- [ ] Campos relacionados estão agrupados de forma clara.
- [ ] Todo o formulário é percorrido e submetido apenas com o teclado.
- [ ] O foco do teclado é sempre visível.

**Rótulos e instruções**

- [ ] Todos os campos têm um rótulo visível e ligado ao campo.
- [ ] As instruções (formato, exemplos) estão associadas ao respetivo campo, não soltas na página.
- [ ] O `placeholder` não é usado como substituto do rótulo.
- [ ] Os campos obrigatórios são identificáveis por texto, e não só por cor ou por um asterisco visual.

**Notificações e mensagens de erro**

- [ ] Os erros dizem *qual* o campo e *como* corrigir.
- [ ] Nenhum erro depende apenas da cor para ser percebido.
- [ ] As mensagens são anunciadas ao leitor de ecrã sem a pessoa ter de as procurar.
- [ ] As confirmações de sucesso também são comunicadas de forma acessível.

**Múltiplos passos**

- [ ] O utilizador sabe em que passo está e quantos faltam.
- [ ] Os dados já preenchidos não se perdem ao avançar ou recuar.
- [ ] É possível voltar atrás e rever antes de submeter.

**Geral**

- [ ] Nada muda de página nem submete dados automaticamente ao focar ou selecionar.
- [ ] Os botões são elementos `<button>` reais (ou `<input>`), acionáveis pelo teclado.
- [ ] O formulário foi testado com teclado **e** com leitor de ecrã, não só com uma ferramenta automática.

---

## Critérios de Sucesso WCAG Relacionados

Todo o trabalho deste módulo assenta nas **WCAG** (Web Content Accessibility Guidelines). Em Portugal, é o **nível AA das WCAG 2.1** que a lei exige, através do Decreto-Lei n.º 83/2018 e da norma europeia EN 301 549.

A tabela seguinte reúne os critérios mais relevantes para formulários. Não precisa de os decorar; serve para saber a que critério "prestar contas" quando alguém lhe perguntar *porquê*.

| Critério                                                     | Nível | Porque importa nos formulários                               |
| ------------------------------------------------------------ | ----- | ------------------------------------------------------------ |
| 1.3.1 — Informação e Relações                                | A     | Rótulos, grupos e a relação entre campos têm de existir no código, não só na aparência. |
| 1.3.5 — Identificar o Objetivo da Introdução                 | AA    | Permite o preenchimento automático (`autocomplete`) de campos como nome ou e-mail. |
| 1.4.1 — Utilização da Cor                                    | A     | A cor não pode ser a única forma de assinalar um erro ou um campo obrigatório. |
| 2.1.1 — Teclado                                              | A     | Todo o formulário tem de funcionar só com o teclado.         |
| 2.4.3 — Ordem de Foco                                        | A     | A ordem de navegação com `Tab` tem de fazer sentido.         |
| 2.4.6 — Títulos e Rótulos                                    | AA    | Rótulos e cabeçalhos descrevem claramente o que se pede.     |
| 2.4.7 — Foco Visível                                         | AA    | Vê-se sempre onde está o foco do teclado.                    |
| 2.5.3 — Rótulo no Nome                                       | A     | O nome lido pelo leitor de ecrã inclui o texto visível do rótulo. |
| 3.2.1 — Ao Focar                                             | A     | Entrar num campo não provoca mudanças inesperadas.           |
| 3.2.2 — Ao Introduzir                                        | A     | Alterar um campo não submete nem muda de página sem aviso.   |
| 3.3.1 — Identificação de Erros                               | A     | Os erros são identificados e descritos em texto.             |
| 3.3.2 — Rótulos ou Instruções                                | A     | Existem rótulos e instruções quando são necessários.         |
| 3.3.3 — Sugestão perante Erros                               | AA    | Quando possível, a mensagem sugere como corrigir.            |
| 3.3.4 — Prevenção de Erros (jurídicos, financeiros, de dados) | AA    | Em ações sensíveis, permite rever, confirmar ou reverter.    |
| 4.1.2 — Nome, Função, Valor                                  | A     | Cada campo expõe corretamente o seu nome, função e estado às tecnologias de apoio. |
| 4.1.3 — Mensagens de Estado                                  | AA    | Erros e confirmações são anunciados sem mudar o foco.        |

**Novidades das WCAG 2.2 a conhecer**

Embora ainda não sejam a referência legal em Portugal, estes critérios são particularmente úteis em formulários:

| Critério                                | Nível | Porque importa nos formulários                               |
| --------------------------------------- | ----- | ------------------------------------------------------------ |
| 2.5.8 — Tamanho do Alvo (Mínimo)        | AA    | Botões e opções suficientemente grandes para tocar sem erro. |
| 3.3.7 — Introdução Redundante           | A     | Não obrigar a pessoa a reintroduzir dados que já forneceu no mesmo processo. |
| 3.3.8 — Autenticação Acessível (Mínimo) | AA    | Não exigir provas de memória (por exemplo, resolver puzzles) para entrar. |
