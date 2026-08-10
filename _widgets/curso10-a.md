# Widgets

## Introdução

Uma página web tem duas naturezas muito diferentes. Há a parte que se **lê** (títulos, parágrafos, imagens, tabelas) e há a parte com que se **interage**: o botão que envia, o separador que troca de painel, o interruptor que liga as notificações, o menu que se abre, o acordeão que expande uma resposta.

A essa segunda parte chamamos **widgets**: os componentes interativos da interface. São os comandos da página.

> **Analogia: o painel de comandos**
>
> Pense na diferença entre o **livro de instruções** de uma máquina de lavar e o **painel de comandos** da máquina.
>
> O livro é para ler. O painel é para agir: tem botões que se carregam, um manípulo que roda, um interruptor que liga e desliga, luzes que dizem em que estado está o programa.
>
> Um bom painel de comandos tem três características. Cada comando **parece o que é** (um botão parece um botão, e não uma etiqueta colada), cada comando **está identificado** (diz "Iniciar", não é um quadrado anónimo), e o painel **mostra em que estado está** (a luz acesa diz que está a lavar).
>
> Os widgets de uma página são exatamente isto. E, tal como num painel de comandos, o problema não é normalmente a máquina — é o comando que ninguém consegue identificar nem alcançar.

### O que conta como widget

Alguns exemplos frequentes:

| Widget                           | O que faz                                       |
| -------------------------------- | ----------------------------------------------- |
| Botão                            | Executa uma ação                                |
| Ligação                          | Leva a outro sítio                              |
| Caixa de verificação             | Liga/desliga uma opção                          |
| Interruptor (*switch*)           | Liga/desliga uma definição, com efeito imediato |
| Separadores (*tabs*)             | Troca o painel visível                          |
| Acordeão                         | Expande e recolhe conteúdo                      |
| Menu                             | Apresenta um conjunto de ações                  |
| Caixa de diálogo                 | Interrompe a página para pedir algo             |
| Controlo deslizante (*slider*)   | Escolhe um valor numa escala                    |
| Caixa de combinação (*combobox*) | Escreve e escolhe de uma lista                  |
| Árvore, grelha, carrossel        | Estruturas interativas compostas                |

Nem tudo o que se clica é um widget no sentido técnico: um parágrafo com um `onclick` continua a ser um parágrafo. E é precisamente aí que começam os problemas deste módulo.

> **Nota de âmbito.** Os controlos nativos de formulário (`<input>`, `<select>`, `<textarea>`, etiquetas, mensagens de erro) foram tratados em detalhe no módulo de **Formulários Acessíveis**. Aqui interessa-nos o widget enquanto **componente interativo**, sobretudo quando é construído à medida com `<div>`, `<span>` e JavaScript, e quando não existe equivalente nativo em HTML.

### Widgets Nativos e Widgets à Medida

Há uma confusão que vale a pena desfazer logo, porque envenena muitas discussões de equipa: **"widget" não é o contrário de "elemento nativo"**.

Um `<button>` é um widget. Um `<input type="checkbox">` é um widget. Um `<select>` é um widget. São **widgets nativos**: componentes interativos que já vêm dentro do HTML, prontos a usar.

A verdadeira distinção é outra:

- **Widget nativo** — o HTML já traz um elemento com aquela função (`<button>`, `<a href>`, `<input>`, `<select>`, `<details>`, `<dialog>`).
- **Widget à medida** (ou *custom*) — não existe elemento nativo com aquela função, ou o nativo foi rejeitado pela equipa, e o componente é construído com `<div>`/`<span>`, CSS, JavaScript e ARIA.

Portanto a pergunta certa, quando se vai construir um componente, nunca é *"faço um widget ou uso um elemento nativo?"*. É: **"este widget já existe em HTML?"**

#### O que se recebe de graça — e o que se passa a dever

> **Analogia: comprar uma porta ou fazer uma porta**
>
> Uma porta comprada numa loja de material de construção vem com dobradiças, fechadura, medidas normalizadas e certificação corta-fogo. Encaixa no vão, e o inspetor reconhece-a.
>
> Uma porta feita à medida na garagem pode ficar linda. Mas as dobradiças, a fechadura, a resistência ao fogo e a certificação passam todas a ser **da sua responsabilidade** — e ninguém avisa quando falta alguma. A porta parece uma porta. Só não abre quando é preciso.
>
> Escolher um `<div>` em vez de um `<button>` é escolher fazer a porta na garagem. É uma escolha legítima em casos raros. Só que raramente se assume a dívida que vem com ela.

Um widget nativo entrega, sem uma linha de código:

| O que o widget nativo traz                                   | O que tem de reconstruir num widget à medida                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Função na árvore de acessibilidade                           | `role` correto, e correto em todos os níveis                 |
| Nome acessível a partir do conteúdo                          | `aria-label` ou `aria-labelledby`, mantidos e traduzidos     |
| Foco de teclado                                              | `tabindex`, gestão do foco                                   |
| Resposta ao `Enter` e ao `Espaço`                            | Gestores de eventos de teclado, um a um                      |
| Estados (`disabled`, `checked`) refletidos automaticamente   | Atributos ARIA de estado, atualizados por si em cada mudança |
| Reconhecimento por comandos de voz                           | Depende do `role` e do nome que declarar                     |
| Adaptação ao modo de alto contraste do sistema               | Regras de CSS próprias                                       |
| Comportamento esperado em telemóvel e em leitor de ecrã móvel | Testes em cada plataforma                                    |
| Correções automáticas quando o navegador é atualizado        | Manutenção sua, para sempre                                  |

#### Então quando é que um widget à medida se justifica?

Em três situações, e poucas mais:

1. **Não existe nativo.** Separadores, menus de aplicação, árvores, acordeões multi-painel, carrosséis. O HTML não os tem.
2. **O nativo existe mas não é personalizável ao ponto necessário.** O caso clássico é o `<select>`, cuja lista aberta não é estilizável de forma consistente. Note-se que é um caso, e não uma regra: `<button>`, `<a>` e `<input type="checkbox">` (com `<label>`) estilizam-se sem qualquer sacrifício de acessibilidade.
3. **É preciso um comportamento que o nativo não tem.** Por exemplo, uma caixa de combinação com pesquisa e resultados assíncronos.

Não se justifica por: "o `<div>` é mais limpo", "assim não herda estilos", "a nossa biblioteca de componentes faz assim", ou "o designer desenhou diferente".

**Exemplo de decisão — o acordeão**

```html
<!-- Opção A: nativo -->
<details>
  <summary>Quais são os prazos de entrega?</summary>
  <p>Entre 3 e 5 dias úteis.</p>
</details>
<!-- Opção B: à medida (esqueleto) -->
<h3>
  <button type="button" aria-expanded="false" aria-controls="p1" id="b1">
    Quais são os prazos de entrega?
  </button>
</h3>
<div id="p1" role="region" aria-labelledby="b1" hidden>
  <p>Entre 3 e 5 dias úteis.</p>
</div>
```

**O que funciona bem e o que exige cuidado:**

A opção A é uma linha de HTML e traz tudo: função, nome, foco, teclado, estado de expansão. É a escolha certa para um FAQ simples. A opção B dá controlo total sobre a animação, a estilização do triângulo e o comportamento de abrir só um painel de cada vez — mas, em troca, obriga a manter o `aria-expanded` sincronizado a cada clique, a manter o `hidden` coerente e a testar em várias combinações de leitor de ecrã. **O acréscimo de código não é o custo; o custo é o acréscimo de responsabilidade.**

*(O `aria-expanded` e o `aria-controls` deste exemplo são tratados na secção* Propriedades, Estados e Valores de Widgets*.)*

Se responder honestamente à pergunta *"o que é que o nativo não me dá?"* e a resposta for só estética, a decisão está tomada: use o nativo e estilize-o.

### As três perguntas de qualquer widget

Todo o widget tem de responder, de forma que uma máquina consiga ler, a três perguntas:

1. **O que é isto?** → a sua **função** (o papel)
2. **Como se chama?** → o seu **nome**
3. **Como está agora?** → o seu **estado ou valor**

Esta secção trata das duas primeiras perguntas: **identificar** o widget e **dar-lhe nome**. A terceira pergunta (estados, propriedades e valores) tem secção própria, a seguinte. Também não tratamos aqui de como o widget se **opera**: isso pertence às secções *Interações por Teclado e Foco*, *Interações por Rato e Toque* e *Interações por Fala*.

Por outras palavras: esta secção é sobre **o que o widget declara ser**. As secções seguintes são sobre o que ele **faz** e como **reage**.

------

### Como as Pessoas com Deficiência acedem a Widgets

Para perceber os requisitos, é preciso perceber primeiro o que está do outro lado do ecrã.

#### A árvore de acessibilidade: a "ficha técnica" de cada elemento

Quando o navegador carrega uma página, não constrói apenas o que se vê. Constrói também, em paralelo, a **árvore de acessibilidade**: uma versão simplificada da página em que cada elemento traz uma ficha com o essencial: *função*, *nome*, *estado*, *valor*, *relações*.

> **Analogia: o inventário do armazém**
>
> Imagine um armazém enorme. Quem lá entra e vê, encontra as coisas pelo aspeto e pela posição. Quem não vê, depende do **inventário**: uma lista onde cada objeto tem um código de categoria e uma etiqueta com o nome.
>
> A árvore de acessibilidade é esse inventário. As tecnologias de apoio não "olham" para a página: leem o inventário.
>
> Se um objeto entrar no armazém sem ficha de inventário, ele existe fisicamente. Mas para quem depende da lista, **não existe**. E se estiver registado com a categoria errada ("caixa de cartão" quando é um extintor), é pior do que não estar registado: engana.

É por isto que um `<div>` estilizado como botão pode ser perfeitamente visível e perfeitamente inútil: entra no inventário como "um bloco de conteúdo qualquer".

#### Quem depende de quê

**Utilizadores de leitor de ecrã (cegueira, baixa visão severa)** Ouvem a ficha do inventário. Um `<button>` é anunciado, tipicamente, como *"Guardar, botão"* — nome e função. Além disso, os leitores de ecrã permitem **navegar por tipo de elemento**: saltar de botão em botão, listar todas as ligações, listar todos os campos de formulário. Um widget sem função declarada fica fora de todas essas listas. É como um livro que não consta do catálogo da biblioteca: está lá, mas ninguém o encontra a não ser por acaso.

**Utilizadores de ampliação de ecrã (baixa visão)** Veem, muitas vezes, 10% ou 15% do ecrã de cada vez. Um widget tem de ser reconhecível **isoladamente**, sem depender do contexto visual à volta. Um ícone solto ao canto, cujo significado só se percebe vendo a página inteira, é inutilizável com ampliação.

**Utilizadores de comandos de voz (limitações motoras)** Dizem, em voz alta, o nome do comando: *"clicar em Guardar"*. Se o widget não tiver nome acessível, ou se o nome falado não corresponder ao texto visível, o comando falha. 

**Utilizadores de teclado e de dispositivos alternativos (limitações motoras)** Dependem de o widget ser alcançável e acionável sem rato. 

**Pessoas com deficiência cognitiva ou de aprendizagem** Dependem de os widgets serem **convencionais e previsíveis**. Um controlo que se comporta como nunca nenhum se comportou obriga a aprender a interface em vez de usar a interface. Nomes claros e componentes reconhecíveis reduzem a carga mental para toda a gente.

**Pessoas com daltonismo** Precisam que a identidade do widget não dependa só da cor. Um "botão" que é apenas texto azul, sem qualquer outra pista, é indistinguível do texto normal para muita gente.

------

### Requisitos de Acessibilidade para Widgets

Reduzido ao essencial, e no âmbito desta secção, um widget acessível cumpre quatro requisitos:

**1. Função declarada programaticamente** O widget tem de dizer o que é, de forma legível por máquina. Não basta parecer um botão: tem de **ser** um botão na árvore de acessibilidade.

**2. Nome acessível adequado** Tem de ter um nome que descreva o seu propósito. "Botão", sem mais, não chega. "Ler mais" repetido dezassete vezes numa página também não.

**3. Aparência coerente com a função** O que parece um botão deve ser um botão; o que é uma ligação deve parecer uma ligação. A promessa visual e a promessa programática têm de ser a mesma promessa.

**4. Robustez** O widget tem de continuar a funcionar em combinações diferentes de navegador e tecnologia de apoio, e quando o utilizador altera o tamanho do texto, o zoom ou as cores.

Os requisitos de **estado e valor** (secção *Propriedades, Estados e Valores de Widgets*), **operabilidade** (secções sobre teclado, rato e fala) e **anúncio de alterações** (secção *Regiões Dinâmicas*) completam o quadro, mas nenhum deles salva um widget que falhe os quatro acima. Nome e função são a fundação.

> **Referência contextual.** O critério WCAG que ancora esta secção é o **4.1.2 — Nome, Função, Valor (Nível A)**, complementado pelo **1.3.1 — Informação e Relações (Nível A)**. A lista completa e organizada dos critérios do módulo está na secção final do módulo.

------

## Técnicas de Codificação

### Técnica 1 — Usar o elemento HTML nativo (a regra que resolve 80% dos casos)

A primeira regra do ARIA é, ironicamente, **não usar ARIA**: se existe um elemento HTML nativo com a semântica e o comportamento pretendidos, use-o.

**Exemplo mau:**

```html
<div class="btn" onclick="guardar()">Guardar</div>
```

**O que está mal neste exemplo:**

Visualmente pode estar impecável. Programaticamente, este elemento:

- entra na árvore de acessibilidade **sem função** — o leitor de ecrã lê apenas o texto "Guardar", como leria um parágrafo, e o utilizador não tem forma de saber que aquilo se pode acionar;
- **não aparece** na lista de botões do leitor de ecrã;
- **não recebe foco** com o teclado;
- **não responde** ao `Enter` nem ao `Espaço`;
- **não é acionável por comando de voz** ("clicar em Guardar" não encontra um botão);
- não fica desativado com `disabled`, não participa em formulários, não herda o modo de alto contraste do sistema.

Repare que a lista de problemas é longa, mas o erro é um só: usou-se uma peça sem função para fazer o trabalho de uma peça com função.

**Exemplo bom:**

```html
<button type="button" onclick="guardar()">Guardar</button>
```

**O que funciona bem neste exemplo:**

Uma linha resolve tudo o que a lista anterior enumerava. O `<button>` traz de origem: a função (`button`), o nome (o seu conteúdo de texto, "Guardar"), o foco de teclado, a resposta a `Enter` e `Espaço`, o suporte a `disabled`, e a integração com comandos de voz e alto contraste.

> **Analogia: a tomada elétrica**
>
> Ninguém constrói uma tomada de raiz para ligar um candeeiro. A tomada é normalizada: qualquer ficha encaixa, qualquer eletricista a reconhece, cumpre a norma sem esforço.
>
> `<button>`, `<a>`, `<input type="checkbox">` são as tomadas normalizadas da web. Um `<div>` com ARIA é uma tomada feita à mão: pode funcionar, mas tem de ser você a garantir tudo o que a norma garantia. E a garantir outra vez em cada navegador.

Um `<button>` estiliza-se livremente. Se a razão para usar `<div>` é o aspeto, essa razão não existe:

```css
button.limpo {
  all: unset;
  cursor: pointer;
  /* e depois estilize à vontade — mas reponha sempre um indicador de foco */
}
```

> Reponha sempre um indicador de foco visível ao usar `all: unset`. O tema é tratado na secção *Interações por Teclado e Foco*.

### Técnica 2 — Quando não há elemento nativo: declarar a função com `role`

Alguns widgets não existem em HTML: separadores, menus de aplicação, árvores, acordeões, interruptores. Aí, o atributo `role` do ARIA declara a função em falta.

```html
<div role="tablist" aria-label="Definições da conta">
  <button type="button" role="tab" id="tab-perfil">Perfil</button>
  <button type="button" role="tab" id="tab-privacidade">Privacidade</button>
</div>
```

**O que funciona bem neste exemplo:**

A função certa está declarada em cada nível: o contentor diz que é uma lista de separadores, cada controlo diz que é um separador. O leitor de ecrã deixa de anunciar "botão" e passa a anunciar "separador", que é o que o utilizador precisa de saber. E, mesmo com `role="tab"`, os elementos continuam a ser `<button>`, o que significa que o comportamento de teclado base vem de graça.

**O que ainda falta neste exemplo:**

Um `tablist` completo precisa de indicar qual o separador selecionado, qual o painel que cada separador controla, e de gerir a navegação por setas. Isso é conteúdo das secções *Propriedades, Estados e Valores de Widgets* e *Interações por Teclado e Foco*, e o padrão completo é tratado na secção *Widgets Complexos*. Aqui, o ponto é apenas este: **`role` declara a função, e mais nada**. Não muda o comportamento, não muda o aspeto, não adiciona teclado.

> **Aviso importante: `role` é uma etiqueta, não uma peça.**
>
> Escrever `role="button"` num `<div>` é como colar uma etiqueta que diz "extintor" numa caixa de cartão. O leitor de ecrã acredita, anuncia "botão", e o utilizador tenta usar uma coisa que não faz o que promete.
>
> Daqui sai a regra mais útil deste módulo: **ARIA errado é pior do que nenhum ARIA**. Sem ARIA, o utilizador encontra um conteúdo confuso. Com ARIA errado, encontra uma promessa falsa.

### Técnica 3 — Famílias de funções (o mapa do território)

Não é preciso decorar a lista, é preciso saber que ela existe e onde consultá-la (o *ARIA Authoring Practices Guide*, do W3C).

- **Funções de widget simples:** `button`, `checkbox`, `radio`, `switch`, `link`, `slider`, `spinbutton`, `searchbox`, `option`, `tab`, `menuitem`, `menuitemcheckbox`, `progressbar`
- **Funções de widget composto** (têm filhos e regras próprias de navegação): `tablist`, `menu`, `menubar`, `listbox`, `radiogroup`, `combobox`, `tree`, `grid`, `toolbar` → secção *Widgets Complexos*
- **Funções de janela:** `dialog`, `alertdialog`
- **Funções de estrutura e de região dinâmica:** `alert`, `status`, `log` → secção *Regiões Dinâmicas*
- **Funções de remoção de semântica:** `presentation` / `none`

### Técnica 4 — Dar nome ao widget

O **nome acessível** é o texto pelo qual o widget é anunciado e chamado. Há três formas principais de o definir, por ordem de preferência:

**a) O conteúdo do próprio elemento — o melhor caso**

```html
<button type="button">Adicionar ao carrinho</button>
```

O nome é o texto visível. Não há duplicação, não há dessincronização, não há tradução esquecida.

**b) `aria-label` — quando não há texto visível**

```html
<button type="button" aria-label="Fechar">
  <svg aria-hidden="true" focusable="false"><!-- ícone × --></svg>
</button>
```

**O que funciona bem neste exemplo:**

O botão de ícone ganha nome. O `aria-hidden="true"` no `<svg>` impede que o ícone contribua com ruído para o nome, e o `focusable="false"` evita um problema conhecido do SVG em alguns navegadores. O resultado é anunciado como *"Fechar, botão"*.

**O que exige cuidado:**

`aria-label` **substitui** o conteúdo. Se aparecer num elemento que já tem texto visível, o texto visível deixa de ser lido. E é aí que nasce um dos erros mais comuns da secção seguinte.

**c) `aria-labelledby` — quando o nome já está escrito noutro sítio**

```html
<h3 id="titulo-fatura">Fatura de março</h3>
<button type="button" aria-labelledby="acao-desc titulo-fatura">
  <span id="acao-desc">Transferir</span>
</button>
```

**O que funciona bem neste exemplo:**

O nome resultante é *"Transferir Fatura de março"*. Isto resolve o clássico problema das listas com dez botões "Transferir" — cada um passa a ter um nome único e compreensível fora de contexto, sem que seja preciso poluir o ecrã com texto repetido. Repare também na ordem: `aria-labelledby` concatena os elementos **pela ordem em que os IDs são listados**, não pela ordem em que aparecem na página.

> **Ordem de precedência, em resumo:** `aria-labelledby` vence `aria-label`, que vence o `<label>` associado, que vence o conteúdo do elemento, que vence o `title`. Não use `title` como nome — não aparece em teclado nem em toque, e é ignorado por várias combinações.

### Técnica 5 — Não sobrepor semântica desnecessariamente

```html
<!-- Mau -->
<button role="link">Ver detalhes</button>

<!-- Mau -->
<a href="/guardar" role="button">Guardar</a>
```

**O que está mal nestes exemplos:**

Em ambos os casos há um conflito entre o que o elemento **é** e o que **diz ser**. No primeiro, o utilizador ouve "ligação" mas o `Enter` aciona um botão e não navega para lado nenhum. No segundo, ouve "botão" mas o comportamento é o de uma ligação (abre com `Enter`, mas não com `Espaço`; aparece no menu de contexto como "abrir em novo separador"). Em ambos, a decisão certa não era o ARIA — era escolher o elemento certo à partida. **Se navega, é uma ligação. Se age, é um botão.**

### Técnica 6 — Verificar o resultado

Não confie na intenção; verifique a ficha do inventário.

1. **Ferramentas de programador** → separador *Acessibilidade* → inspecione a árvore. Cada widget deve mostrar `name` e `role` corretos.
2. **Leitor de ecrã**: NVDA (gratuito, Windows), VoiceOver (macOS/iOS), TalkBack (Android). Percorra a página só com o leitor e pergunte-se: *"sabendo apenas o que ouvi, sei o que isto é e o que faz?"*
3. **Teste do foco**: `Tab` do início ao fim. Se um widget não aparece, não está lá para muita gente.
4. **Ferramentas automáticas** apanham `role` inválidos e nomes em falta, mas **não** apanham `role` errados. Um `<div role="button">` que não funciona passa em todos os validadores.

------

## Recomendações para Conteúdo Acessível

**Prefira o convencional ao criativo.** Um widget é infraestrutura, não é assinatura de autor. Quanto mais parecido for com o que existe em todo o lado, menos esforço custa a toda a gente, e mais provável é que funcione com as tecnologias de apoio, que foram afinadas ao longo de anos para os padrões conhecidos.

**Antes de construir, pergunte se é mesmo preciso.** Muitos widgets à medida existem para resolver um problema de aparência de um elemento nativo. Estilizar o nativo é quase sempre mais barato, em código e em risco, do que reimplementar a acessibilidade.

**Escreva nomes que funcionem fora de contexto.** O leitor de ecrã pode listar apenas os botões, sem o texto à volta. "Ler mais", "Aqui", "Descarregar", repetidos, são inúteis nessa lista. "Ler mais sobre o Orçamento de 2026" é útil. Faça o teste: leia só os nomes dos widgets, em voz alta, sem ver a página. Ainda faz sentido?

**Faça o nome acessível começar pelo texto visível.** Se o botão diz "Enviar pedido", o nome acessível não deve ser "Submeter formulário": quem usa comandos de voz diz o que **vê**, e o comando falharia. Quando o nome visível e o nome acessível divergem, a regra é: o acessível **contém** o visível, e começa por ele. *(Critério 2.5.3 — Etiqueta no Nome, Nível A.)*

**Não use ícones sozinhos quando pode acrescentar texto.** Um `aria-label` resolve o problema para quem usa leitor de ecrã, mas não resolve para quem **vê** o ícone e não sabe o que ele significa. O símbolo de uma disquete para "guardar" já não diz nada a muitos utilizadores.

**Seja consistente em todo o sítio.** O mesmo componente, com o mesmo nome e o mesmo comportamento, em todas as páginas. Um "Guardar" que numa página é botão e noutra é ligação obriga o utilizador a reaprender.

**Não use ARIA para tapar HTML mal escrito.** ARIA é uma camada de tradução, não uma correção. Se está a acrescentar `role` para compensar uma escolha estrutural, o problema está na estrutura.

**Teste com pessoas.** Nenhuma ferramenta lhe diz se o nome que escolheu faz sentido. Uma pessoa diz-lhe em cinco segundos.

------

### Erros Comuns

**1. O `<div>` que finge ser botão**

```html
<div class="btn" onclick="acao()">Continuar</div>
```

Sem função, sem foco, sem teclado, sem voz. **Correção:** `<button type="button">`.

**2. O `role` que não passa de uma etiqueta**

```html
<div role="button" onclick="acao()">Continuar</div>
```

Pior do que o anterior: agora é anunciado como botão e continua sem foco e sem teclado: promete e não cumpre. **Correção:** `<button>`. Se for mesmo impossível, o `role` **exige** `tabindex="0"` e gestores de `Enter`/`Espaço`.

**3. O widget sem nome**

```html
<button type="button"><svg><!-- lupa --></svg></button>
```

Anunciado como *"botão"*, sem mais. **Correção:** `aria-label="Pesquisar"` e `aria-hidden="true"` no ícone.

**4. O `aria-label` que apaga o texto visível**

```html
<button type="button" aria-label="Enviar">Confirmar encomenda</button>
```

Vê-se "Confirmar encomenda", ouve-se "Enviar", e o comando de voz "clicar em Confirmar encomenda" falha. **Correção:** deixe o texto do elemento ser o nome; retire o `aria-label`.

**5. O `aria-labelledby` que aponta para o vazio**

```html
<button type="button" aria-labelledby="titulo-item">Editar</button>
<!-- não existe nenhum elemento com id="titulo-item" -->
```

Quando o ID não existe, a referência é ignorada. Pior, o texto "Editar" pode não ser recuperado em todas as combinações, deixando o botão sem nome. **Correção:** verificar que o ID existe, é único, e está no mesmo documento.

**6. A ligação que age e o botão que navega**

```html
<a href="#" onclick="apagarConta()">Apagar conta</a>
```

Prometeu-se navegação e executou-se uma ação destrutiva. **Correção:** `<button type="button">`. Regra: **navega → `<a href>`; faz → `<button>`**.

**7. O ícone que fala a mais**

```html
<button type="button" aria-label="Fechar">
  <svg><title>Cruz vermelha</title>...</svg>
</button>
```

Ruído no anúncio e nome duplicado. **Correção:** `aria-hidden="true"` e `focusable="false"` no ícone decorativo, e um único nome no botão.

**8. O texto azul que finge ser ligação**

```html
<span class="link-falso" onclick="abrir()">Consultar o regulamento</span>
```

Não é uma ligação: não abre em novo separador, não se copia o endereço, não aparece na lista de ligações do leitor de ecrã, e, se a distinção for só a cor, é invisível para quem tem daltonismo. **Correção:** `<a href="/regulamento">`.

**9. O `role="presentation"` a mais**

```html
<button type="button" role="presentation">Guardar</button>
```

Removeu-se a semântica de um elemento que existia precisamente pela semântica. `presentation`/`none` serve para tabelas de layout ou contentores decorativos — nunca para widgets.

**10. Confiar apenas nas ferramentas automáticas**

Um `<div role="button">` sem teclado passa em todos os validadores e falha para o utilizador. As ferramentas verificam a **sintaxe**; só uma pessoa verifica o **sentido**.

------

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- **Widget** é qualquer componente interativo da interface — o painel de comandos da página, por oposição ao conteúdo que se lê.
- As tecnologias de apoio não veem a página: leem a **árvore de acessibilidade**, o inventário onde cada elemento declara *função*, *nome*, *estado* e *valor*.
- Esta secção trata das duas primeiras perguntas — **o que é** e **como se chama**. Estados e valores, e a operação por teclado, rato e fala, têm secções próprias.
- **"Widget" não é o contrário de "elemento nativo".** Um `<button>` é um widget — é um **widget nativo**. A distinção real é entre **widget nativo** (o HTML já o tem) e **widget à medida** (construído com `<div>`, CSS, JavaScript e ARIA).
- O widget nativo traz de origem função, nome, foco, teclado, estados, voz e alto contraste — e melhora sozinho quando os navegadores melhoram. No widget à medida, tudo isso passa a ser **responsabilidade sua**, para sempre.
- Um widget à medida só se justifica quando **não existe nativo**, quando o nativo não é personalizável ao ponto necessário (o caso do `<select>`), ou quando é preciso um comportamento que o nativo não tem. Nunca por estética.
- **Primeira regra do ARIA: não usar ARIA.** Se existe elemento nativo (`<button>`, `<a>`, `<input>`), use-o. Traz função, nome, foco, teclado e integração com o sistema, de graça.
- `role` **declara** a função; não a implementa. Não dá foco, não dá teclado, não muda o aspeto.
- **ARIA errado é pior do que nenhum ARIA:** uma etiqueta falsa engana quem depende dela.
- O nome acessível deve fazer sentido **fora de contexto** e **começar pelo texto visível**.
- **Navega → ligação. Age → botão.** Não troque, e não corrija a troca com ARIA.
- Verifique sempre na árvore de acessibilidade e com um leitor de ecrã real. As ferramentas automáticas não detetam funções erradas.

### Exercícios Práticos

**Exercício 1 — Identificar**

Escolha uma página de um serviço público português. Sem ver o código:

1. Faça uma lista de todos os widgets que consegue identificar visualmente.
2. Para cada um, escreva o que acha que é a sua **função** e qual seria um bom **nome**.
3. Abra as ferramentas de programador, vá à árvore de acessibilidade e compare com o que anotou.

*Pergunte-se: quantos widgets aparecem no inventário com a função que prometem visualmente?*

**Exercício 2 — Corrigir**

Reescreva o código seguinte de forma acessível. Não acrescente nenhum atributo ARIA que não seja indispensável e justifique cada um que mantiver.

```html
<div class="barra">
  <span class="acao" onclick="imprimir()">🖨</span>
  <div class="btn primario" onclick="submeter()" aria-label="Ok">Submeter pedido</div>
  <span class="link" onclick="location.href='/ajuda'">Precisa de ajuda?</span>
  <div role="button">Cancelar</div>
</div>
```

*Sugestão: há pelo menos cinco problemas distintos, e quatro deles resolvem-se trocando de elemento, não acrescentando ARIA.*

**Exercício 3 — Nomear**

Uma lista de faturas mostra, em cada linha, o mês e três botões idênticos: **Ver**, **Transferir**, **Anular**.

1. Explique porque é que esta lista é problemática para quem navega pela lista de botões de um leitor de ecrã.
2. Proponha **duas** soluções diferentes para tornar cada nome único, uma com `aria-label` e outra com `aria-labelledby`.
3. Indique qual prefere e porquê, tendo em conta que o sítio vai ser traduzido para inglês.

**Exercício 4 — Decidir**

Para cada caso, diga se usaria `<a href>`, `<button>` ou outro elemento, e justifique numa frase:

| Caso                                                  | Elemento? |
| ----------------------------------------------------- | --------- |
| "Saber mais" que leva a outra página                  |           |
| "Saber mais" que expande um parágrafo na mesma página |           |
| Logótipo que leva à página inicial                    |           |
| "Adicionar linha" numa tabela editável                |           |
| "Transferir PDF" que aponta para um ficheiro          |           |
| "Idioma: Português" que abre um menu de escolha       |           |

Depois, para os dois últimos casos, responda: **construiria um widget à medida ou usaria o nativo?** Escreva, em cada caso, a lista do que passaria a ser da sua responsabilidade se optasse pelo à medida.

**Exercício 5 — Ouvir**

Instale o NVDA (Windows) ou ative o VoiceOver (macOS). Escolha uma página com um componente à medida — um acordeão, um carrossel, um menu suspenso.

1. Percorra-a apenas com o leitor de ecrã, sem olhar para o ecrã.
2. Anote **literalmente** o que ouve em cada widget.
3. Marque os casos em que o que ouviu não lhe permitiu saber o que aquilo era ou o que fazia.

*Este é o teste mais honesto que existe — e o mais desconfortável. Guarde as notas: vamos voltar a esta página na secção dos estados.*

