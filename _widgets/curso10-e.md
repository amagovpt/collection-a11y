---
title: Interações por Fala
layout: default
nav_order: 5
---
# Interações por Fala

## Introdução

Nas secções anteriores vimos duas formas de operar um widget: pelo **teclado** e pelo **apontador** — rato, dedo, caneta.

Existe uma terceira forma, muito menos conhecida por quem desenvolve, mas usada todos os dias por milhares de pessoas: **a voz**.

Falamos aqui de **comando por voz** (*speech input*, ou controlo por fala): software que ouve o utilizador e executa ações na interface. Exemplos: o Dragon NaturallySpeaking e o Dragon Professional, o Controlo por Voz da Apple (macOS e iOS), o Voice Access do Android, o Acesso por Voz do Windows.

> **Atenção a uma confusão frequente**
>
> «Interações por fala» **não** é o mesmo que «o leitor de ecrã fala».
>
> - O leitor de ecrã fala **para** o utilizador — é **saída** de informação. Isso já foi tratado nas secções «Widgets» e «Propriedades, Estados e Valores de Widgets».
> - O comando por voz é o utilizador a falar **para** a interface — é **entrada** de comandos. É disto que trata esta secção.
>
> São coisas diferentes, com requisitos diferentes, e é perfeitamente possível uma página funcionar bem com leitor de ecrã e ser praticamente inutilizável por voz.

> **Analogia central: o ajudante que só lê o que está escrito**
>
> Imagine que está sentado numa cadeira, do outro lado da sala, e tem um ajudante à frente do painel de comandos de uma máquina. Você não pode tocar em nada; só pode dizer-lhe o que fazer, com base no manual de instruções que tem ao pé de si. E o ajudante tem uma regra estranha: **só reconhece os comandos pelo nome que está escrito ao lado deles**. Não conhece a máquina, não adivinha, não interpreta.
>
> - Você diz «carrega no Iniciar» e existe um botão com «Iniciar» escrito → funciona.
> - Você diz «carrega no Iniciar» mas o botão só tem um triângulo desenhado, sem texto → o ajudante não faz nada. Não sabe qual é.
> - Você diz «carrega no Iniciar» mas ao no painel de comandos que o assistente vê está escrito «Começar processo de lavagem» → o ajudante procura «Iniciar», não encontra, e não faz nada. **O botão está lá, à vista, igual àquele que está indicado no manual que consultou — e mesmo assim não obedece.**
> - Você diz «carrega no Iniciar» e existem **três** botões «Iniciar» no painel → o ajudante hesita e pergunta qual, ou põe números em cima de todos.
>
> Este ajudante é o software de comando por voz. E o exemplo do botão que se vê com um nome e responde por outro é a falha número um desta secção, e uma das mais difíceis de detetar, porque **não se vê no ecrã**.

### Como as Pessoas com Deficiência Interagem com Widgets por Fala

#### Quem usa comando por voz

**Pessoas com limitações motoras nos membros superiores**
Tetraplegia, esclerose múltipla, distrofia muscular, paralisia cerebral, amputação. Para muitas destas pessoas a voz é o **único** meio de entrada, ou o meio principal, complementado por um interruptor ou por um apontador de cabeça.

**Pessoas com lesões por esforço repetitivo, tendinite, artrite ou dor crónica**
Aqui a voz é frequentemente uma forma de **racionar** o uso das mãos: escrevem por voz, navegam por voz, e reservam o rato para o que a voz não consegue fazer. É um grupo muito maior do que se pensa e, muitas vezes, temporário ou intermitente.

**Pessoas com limitações temporárias ou situacionais**
Um braço engessado, um pós-operatório, alguém a segurar uma criança ao colo. Não são «utilizadores com deficiência» num sentido permanente, mas beneficiam exatamente das mesmas boas práticas.

**Pessoas com dislexia ou dificuldades de escrita**
Usam sobretudo o ditado para introduzir texto, mais do que os comandos de navegação.

**Utilizadores combinados**
Há quem use leitor de ecrã **e** voz, ou ampliação **e** voz. Não se pode assumir que quem fala vê bem, nem que quem vê bem não fala.

#### Como funciona, na prática

O software de comando por voz opera essencialmente em três modos. Compreender os três explica quase todos os requisitos que se seguem.

**1. Comandos por nome — «Clicar Guardar»**
É o modo rápido e o preferido. O software lê a árvore de acessibilidade da página, recolhe os **nomes acessíveis** dos elementos interativos, e compara-os com o que o utilizador disse. Se corresponder, aciona o elemento.

Repare no ponto crítico: o utilizador diz aquilo que **vê** no ecrã; o software procura naquilo que está **programado**. Se os dois não coincidirem, o comando falha.

**2. Comandos por tipo de elemento — «Mostrar links», «Clicar botão»**
O utilizador pede ao software que numere ou liste todos os elementos de um determinado tipo. Isto só funciona se o elemento **declarar corretamente a sua função**. Um `<div>` com um `onclick` não é um botão para o software de voz, é decoração. Não aparece na lista.

**3. Grelha e rato virtual — «Mostrar grelha», «Rato para 27», «Clicar»**
É o modo de último recurso: sobrepõe-se uma grelha numerada ao ecrã e o utilizador vai reduzindo a grelha até o cursor cair em cima do alvo. Serve para tudo o que os modos 1 e 2 não alcançam.

> **O que isto custa realmente**
>
> Acionar um botão bem feito por voz: **duas palavras**, «Clicar Guardar». Um segundo.
>
> Acionar o mesmo botão através da grelha: «Mostrar grelha» → «7» → «4» → «2» → «Clicar». Cinco comandos, cada um com hipótese de erro de reconhecimento, cerca de quinze a vinte segundos. E depois há um segundo botão. E um terceiro.
>
> Quando dizemos que um widget «ainda é acessível por voz porque há sempre a grelha», estamos a dizer o mesmo que quem diz que um edifício sem elevador é acessível «porque há sempre as escadas». Tecnicamente há uma forma; na prática, o custo é a exclusão.

#### O que o comando por voz não consegue fazer bem

É importante saber onde estão os limites, porque isso determina o que não se deve exigir ao utilizador:

- **Gestos contínuos**: arrastar, redimensionar, desenhar, deslizar. Existem comandos («arrastar de X para Y»), mas são lentos e frágeis.
- **Sobreposição (*hover*)**: manter o cursor imóvel sobre um elemento durante algum tempo é difícil por voz.
- **Alvos pequenos ou muito juntos**: quando é preciso recorrer à grelha, um alvo pequeno é um alvo falhado.
- **Prazos**: qualquer coisa que desapareça ao fim de poucos segundos é incompatível com uma interação que demora quinze.

As duas primeiras estão tratadas em detalhe na secção «Interações por Rato e Toque»; note-se apenas que **as boas práticas de apontador beneficiam diretamente quem usa voz**, porque a voz acaba por conduzir um apontador virtual.

### Requisitos de Acessibilidade para Interações por Fala

Sete requisitos. Os três primeiros são a essência; os restantes evitam armadilhas.

**R1 — O nome que se vê tem de estar no nome que a máquina lê**
Se um widget tem um rótulo visível em texto, o seu nome acessível tem de **conter** esse texto, e de preferência começar por ele. Este é o requisito central desta secção e corresponde ao critério WCAG **2.5.3 Rótulo no Nome** (nível A).

**R2 — Todo o widget acionável tem de ter um nome falável**
Um ícone sozinho não tem nome falável. «Clicar lápis» só funciona se algures existir a palavra escrita, ou, no mínimo, se o nome acessível for uma palavra previsível que o utilizador consiga adivinhar a partir do ícone.

**R3 — A função tem de estar declarada correctamente**
Sem função correta, o widget desaparece dos comandos «Mostrar botões», «Clicar link», «Mostrar campos». A construção da função foi tratada na secção «Widgets»; aqui interessa a **consequência**: função errada = widget invisível para a voz.

**R4 — Nomes distinguíveis entre si**
Cinco «Ver mais» na mesma página obrigam sempre a um passo de desambiguação. Nomes únicos e curtos poupam esse passo.

**R5 — Nomes pronunciáveis e curtos**
Um nome acessível como «Botão de submissão do formulário de candidatura n.º 4 (obrigatório)» é literalmente impossível de dizer. O reconhecimento de fala funciona melhor com uma a três palavras.

**R6 — Nada de essencial pode depender só de gesto contínuo ou de sobreposição**
Tem de haver sempre um caminho de acionamento simples: um clique num alvo nomeado.

**R7 — O ditado não pode disparar ações**
Quando o utilizador dita texto, palavras soltas podem escapar para a página. Se a página tiver atalhos de tecla única, o ditado aciona-os por acidente. Isto liga-se ao critério **2.1.4 Atalhos de Teclas de Caracteres** (nível A), tratado na secção «Interações por Teclado e Foco» — mas vale a pena reter que **um dos principais prejudicados pelos atalhos de tecla única é quem usa voz**, e não quem usa teclado.

---

## Técnicas de Codificação

### T1 — Usar elementos nativos com texto visível

A técnica mais eficaz não exige ARIA nenhum.

```html
<!-- Bem -->
<button type="submit">Guardar rascunho</button>
<a href="/perfil">O meu perfil</a>
```

**O que funciona bem:** a função vem do elemento (`button`, `a`), o nome acessível vem do conteúdo de texto, e o texto visível é exatamente esse conteúdo. Nome visível e nome programático são **a mesma string, pela sua própria construção** — não há como divergirem. «Clicar Guardar rascunho» funciona; «Mostrar links» inclui «O meu perfil». Zero atributos, zero manutenção.

### T2 — O erro do `aria-label` que substitui o texto visível

Este é o ponto onde a maioria dos projetos falha.

```html
<!-- Mal -->
<button aria-label="Submeter o formulário de candidatura">
  Enviar
</button>
```

**O que corre mal:** o `aria-label` **substitui** o conteúdo do elemento no cálculo do nome acessível. O utilizador vê «Enviar». Diz «Clicar Enviar». O software procura um elemento chamado «Enviar» e não encontra nenhum porque, para a máquina, aquele botão chama-se «Submeter o formulário de candidatura». O botão está visível, o utilizador identificou-o corretamente, e não acontece nada.

O mais cruel é que este código foi escrito **com boa intenção**: alguém quis dar mais contexto ao leitor de ecrã. Melhorou uma tecnologia de apoio e partiu outra. Viola o critério 2.5.3.

```html
<!-- Bem: contexto acrescentado sem quebrar o rótulo visível -->
<button aria-label="Enviar candidatura">
  Enviar
</button>
```

**O que funciona bem:** o nome acessível **começa pela palavra visível** («Enviar») e só depois acrescenta contexto. «Clicar Enviar» funciona, e o leitor de ecrã continua a ter a informação adicional. A regra prática é simples: **se usa `aria-label` num elemento que tem texto visível, o texto visível deve aparecer no início do `aria-label`, escrito exatamente da mesma forma.**

### T3 — `aria-labelledby` a apontar para o texto visível

Quando o contexto já existe em texto na página, é preferível reutilizá-lo a reescrevê-lo.

```html
<!-- Bem -->
<h3 id="titulo-fatura">Fatura FT2026/1147</h3>
<p>Emitida a 3 de março de 2026 — 148,20 €</p>
<button id="btn-desc" aria-labelledby="btn-desc titulo-fatura">
  Descarregar
</button>
```

**O que funciona bem:** o nome acessível resulta da concatenação pela ordem indicada — «Descarregar Fatura FT2026/1147». Começa pelo texto visível do próprio botão, portanto «Clicar Descarregar» funciona. E, como o nome é construído a partir do HTML que já existe, **não há duas fontes de verdade para manter sincronizadas**: se o título da fatura mudar, o nome acessível muda com ele. Repare no truque de incluir o `id` do próprio botão como primeiro item da lista — é assim que se recupera o texto do elemento.

### T4 — Ícones sem texto: dar-lhes uma palavra

O botão só com ícone é a segunda grande fonte de problemas. Não tem palavra nenhuma para dizer.

```html
<!-- Mal -->
<button>
  <svg aria-hidden="true" focusable="false"><use href="#icone-lixo"/></svg>
</button>
```

**O que corre mal:** o SVG está escondido da árvore de acessibilidade (o que está certo, para não ser lido como imagem), mas nada o substituiu. O botão fica **sem nome nenhum**: o leitor de ecrã anuncia «botão», e o utilizador de voz vê um caixote do lixo e não tem forma de o invocar. Resta a grelha.

```html
<!-- Aceitável -->
<button aria-label="Eliminar">
  <svg aria-hidden="true" focusable="false"><use href="#icone-lixo"/></svg>
</button>
```

**O que funciona razoavelmente:** já existe nome. «Clicar Eliminar» funciona, **desde que o utilizador adivinhe que o ícone se chama «Eliminar»**. Podia chamar-se «Apagar», «Remover» ou «Lixo». O utilizador acerta à segunda ou à terceira tentativa. Não é uma falha de conformidade (não há rótulo visível em texto, logo o 2.5.3 não se aplica), mas é uma falha de usabilidade real.

```html
<!-- Melhor -->
<button>
  <svg aria-hidden="true" focusable="false"><use href="#icone-lixo"/></svg>
  <span class="rotulo-icone">Eliminar</span>
</button>
```

```css
/* Em ecrãs estreitos, o rótulo esconde-se visualmente
   mas continua na árvore de acessibilidade */
@media (max-width: 40rem) {
  .rotulo-icone {
    position: absolute;
    width: 1px; height: 1px;
    padding: 0; margin: -1px;
    overflow: hidden;
    clip-path: inset(50%);
    white-space: nowrap;
  }
}
```

**O que funciona bem:** quando há espaço, a palavra está lá, à vista. O utilizador de voz lê-a e enuncia-a, e toda a gente percebe melhor o ícone. Quando não há espaço, a técnica de ocultação visual mantém o texto na árvore de acessibilidade, portanto o nome continua a existir e o comando continua a funcionar. **Nunca usar `display: none` nem `visibility: hidden` para isto**. Esses removem o elemento da árvore e o nome desaparece.

Note-se que uma dica visual (*tooltip*) que só aparece com o cursor em cima **não resolve** o problema: quem usa voz tem dificuldade em manter a sobreposição, e a palavra que precisa de dizer só se revela exatamente com o gesto que não consegue fazer.

### T5 — Rótulos de campos: o `placeholder` não conta

```html
<!-- Mal -->
<input type="text" placeholder="Número de contribuinte">
```

**O que corre mal:** o `placeholder` desaparece assim que se escreve, e o suporte a este atributo como fonte de nome acessível é inconsistente entre navegadores e tecnologias de apoio. Além disso, o utilizador de voz precisa de dizer «Clicar Número de contribuinte» para levar o foco ao campo antes de ditar, e o nome pode simplesmente não estar lá.

```html
<!-- Bem -->
<label for="nif">Número de contribuinte</label>
<input type="text" id="nif" name="nif" autocomplete="off">
```

**O que funciona bem:** o `<label>` associado dá um nome estável, que não desaparece com o conteúdo, e que é exatamente o texto que o utilizador vê. Como bónus, clicar no rótulo põe o foco no campo, o que aumenta a área de alvo para toda a gente, incluindo para quem opera a grelha de voz.

### T6 — Nomes que se conseguem dizer

```html
<!-- Mal -->
<button aria-label="Item 47b — configurações avançadas de sincronização (beta)">⚙</button>
<a href="/rel/q3">Relatório Q3 (PDF, 2,4 MB, abre em nova janela)</a>
```

**O que corre mal:** o primeiro nome é praticamente impossível de pronunciar de forma reconhecível — números, letras soltas, travessões, parênteses. O segundo obriga o utilizador a dizer treze palavras, incluindo «2,4 MB», para acionar um link. Na maioria dos casos o software aceita correspondências parciais, mas não é garantido, e o utilizador não tem como saber onde é que a correspondência começa e acaba.

```html
<!-- Bem -->
<button aria-label="Sincronização">⚙</button>

<a href="/rel/q3">
  Relatório Q3
  <span class="meta">(PDF, 2,4 MB — abre em nova janela)</span>
</a>
```

**O que funciona bem:** no primeiro caso, uma palavra, dizível. No segundo, o nome acessível continua a incluir toda a informação (o `<span>` faz parte do conteúdo do link), mas começa por «Relatório Q3» — e os softwares de voz privilegiam a correspondência pelo início do nome. «Clicar Relatório Q3» funciona.

### T7 — Desambiguar nomes repetidos

```html
<!-- Problemático -->
<article><h3>Portugal reduz consumo</h3><a href="/n/1">Ler mais</a></article>
<article><h3>Nova ponte no Douro</h3><a href="/n/2">Ler mais</a></article>
<article><h3>Orçamento aprovado</h3><a href="/n/3">Ler mais</a></article>
```

**O que corre mal:** «Clicar Ler mais» encontra três correspondências. O software sobrepõe números aos três links e o utilizador tem de fazer um segundo comando — «2» — para escolher. Não é fatal (é o comportamento previsto, e é assim que a maioria dos leitores de notícias funciona), mas duplica o esforço em todas as páginas de listagem.

```html
<!-- Melhor -->
<article>
  <h3 id="n1">Portugal reduz consumo</h3>
  <a href="/n/1" id="l1" aria-labelledby="l1 n1">Ler mais</a>
</article>
```

**O que funciona bem:** o nome acessível passa a ser «Ler mais Portugal reduz consumo» — único. E, crucialmente, continua a começar por «Ler mais», portanto quem quiser usar o comando genérico com desambiguação por número **continua a poder fazê-lo**. Ganham-se as duas coisas.

### T8 — Fim do formulário: não deixar o botão sem palavra

```html
<!-- Mal -->
<button type="submit" class="btn-primario"></button>
```

```css
/* O texto do botão vem daqui — do CSS, não do HTML */
.btn-primario::before {
  content: "Enviar";
}
```

Um botão cujo rótulo é fornecido apenas por CSS (`content` num pseudo-elemento) é um caso particularmente traiçoeiro: **vê-se texto no ecrã que não existe no HTML**. O leitor de ecrã pode ou não anunciá-lo, consoante o navegador; o software de voz, que lê a árvore de acessibilidade, tipicamente **não** o encontra. O utilizador vê a palavra «Enviar» com os seus próprios olhos, di-la, e nada acontece. O cenário mais confuso possível para ele, porque parece que o software de voz está avariado.

Texto que o utilizador vai precisar de dizer **vive no HTML**, nunca no CSS.

---

## Recomendações para Conteúdo Acessível

Grande parte do trabalho desta secção não é de programação. É de **redação de interface** e de **desenho**. Quem escreve os rótulos determina se a página se pode operar por voz.

**Escrever rótulos curtos, concretos e ditáveis**
Uma a três palavras. Verbos claros: «Guardar», «Enviar», «Eliminar», «Descarregar». Evitar rótulos que sejam só símbolos, números de referência ou códigos internos.

**Um rótulo, um sítio**
Se o botão diz «Guardar», a etiqueta interna diz «Guardar». Se a equipa de conteúdo mudar «Guardar» para «Gravar», alguém tem de mudar o `aria-label` também. Esta dessincronização entre o texto de interface e os atributos ARIA é a causa mais comum de falhas do critério 2.5.3 em produção, normalmente porque as duas coisas vivem em ficheiros diferentes, mantidos por pessoas diferentes.

**Preferir texto ao lado do ícone**
Sempre que o espaço permita. Beneficia quem usa voz, quem tem dificuldades cognitivas, quem não conhece a convenção do ícone e quem está com pressa.

**Não usar o mesmo texto para ações diferentes na mesma página**
E, se for inevitável, acrescentar contexto **depois** do texto comum.

**Cuidado com a tradução e com os símbolos**
Um rótulo com «€», «%», «→» ou «&» obriga o utilizador a adivinhar como se diz aquilo. «Pagar 148,20 €» é melhor do que «148,20 €» sozinho — dá-lhe uma palavra por onde pegar.

**Nomes escritos na língua da página**
O atributo `lang` correto no `<html>` (e em passagens noutra língua) permite ao software de reconhecimento aplicar o modelo linguístico certo. Um botão «Download» numa página declarada como `lang="pt"` obriga o motor a reconhecer uma palavra inglesa dentro de um modelo português — falha frequentemente. Preferir «Descarregar».

**Dar tempo**
Se um menu, uma dica ou uma notificação desaparecerem ao fim de três ou quatro segundos, quem opera por voz não chega lá. Isto liga-se aos critérios 2.2.1 e 1.4.13, consolidados na secção final.

### Erros Comuns

1. **`aria-label` que substitui o texto visível.** O erro rei. Viola o 2.5.3 e é invisível numa inspeção visual.
2. **Botão só com ícone e sem nome nenhum.** Nem leitor de ecrã, nem voz.
3. **Rótulo visível só no CSS** (`::before { content: "Enviar" }`). Vê-se, não se diz.
4. **`placeholder` em vez de `<label>`.** Nome instável e inconsistente entre navegadores e tecnologias de apoio.
5. **`title` como único rótulo.** Só aparece com o cursor em cima. Exatamente o gesto que o utilizador de voz não faz bem.
6. **Nomes acessíveis com dez ou mais palavras.** Tecnicamente corretos, praticamente indizíveis.
7. **`<div onclick>` em vez de `<button>`.** Não aparece em «Mostrar botões» nem responde a «Clicar X». Desaparece de dois dos três modos de operação por voz.
8. **Texto do rótulo diferente do que a equipa de conteúdo publicou.** Dessincronização entre a interface e o ARIA após uma alteração de copy.
9. **Ícone com dica visual (*tooltip*) como única fonte da palavra.** A palavra necessária só se revela com o gesto impossível.
10. **Atalhos de tecla única ativos durante o ditado.** O utilizador dita «Sim, envio já» e a letra «s» aciona um atalho.
11. **Assumir que a grelha resolve.** Resolve como as escadas resolvem a falta de elevador.
12. **Testar só com leitor de ecrã e dar o widget por validado.** São ferramentas com requisitos diferentes; passar num teste não implica passar no outro.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Interação por fala é entrada de comandos, não saída de voz.** Não confundir com leitor de ecrã.
2. **O utilizador diz o que vê; o software procura o que está programado.** Todo o requisito desta secção decorre desta frase.
3. **O nome visível tem de estar dentro do nome acessível**, de preferência no início. É o critério WCAG 2.5.3 Rótulo no Nome (nível A) — exigível pelo Decreto-Lei n.º 83/2018.
4. **Elementos nativos com texto visível resolvem o problema de graça**, porque não existem dois nomes para desalinhar.
5. **`aria-label` num elemento com texto visível é uma zona de perigo.** Se o usar, comece pelo texto visível.
6. **`aria-labelledby` a apontar para texto que já existe** é mais robusto do que reescrever o nome à mão.
7. **Ícone sem palavra é um alvo que não se pode invocar.** Dê-lhe texto — visível, se possível; oculto visualmente, se não houver espaço; nunca via `display: none` nem só via CSS `content`.
8. **Nomes curtos, únicos, pronunciáveis, na língua da página.**
9. **A função declarada corretamente é o que faz o widget existir** para os comandos «Mostrar botões» e «Clicar link».
10. **Os atalhos de tecla única prejudicam sobretudo quem dita**, não quem usa teclado.
11. **A grelha é o último recurso, não a solução.** Se a resposta a «como é que isto se faz por voz?» for «pela grelha», o widget está mal feito.
12. **Testar por voz é um teste próprio.** Nenhuma outra tecnologia de apoio o substitui.

### Exercícios Práticos

**Exercício 1 — Encontrar a divergência**
Analise o código seguinte e identifique, para cada linha, o que o utilizador vê, o que o software de voz procura, e se o comando funciona.

```html
<button aria-label="Adicionar ao carrinho de compras">Comprar</button>
<button aria-label="Comprar agora">Comprar</button>
<button title="Comprar">🛒</button>
<button>Comprar <span class="visually-hidden">Camisola azul, tamanho M</span></button>
```

Ordene os quatro casos do melhor para o pior e justifique. Reescreva os que falham.

**Exercício 2 — Auditoria sem software**
Escolha uma página de um serviço público português. Percorra-a e faça uma tabela de três colunas: *texto visível* | *nome acessível* (use o inspetor de acessibilidade do navegador) | *coincidem?*. Conte quantos widgets falham. Registe quantos são botões só com ícone.

**Exercício 3 — Auditoria com software**
Ative o Controlo por Voz (macOS/iOS) ou o Voice Access (Android) ou o Acesso por Voz (Windows) e tente completar uma tarefa real na mesma página: por exemplo, pesquisar algo e abrir o primeiro resultado. Cronometre. Registe todos os pontos onde teve de recorrer à grelha e porquê.

**Exercício 4 — Corrigir a barra de ferramentas**
Recebeu esta barra de ferramentas de um editor de texto:

```html
<div class="toolbar">
  <div class="btn" onclick="bold()"><b>B</b></div>
  <div class="btn" onclick="italic()"><i>I</i></div>
  <div class="btn" onclick="link()"><svg>...</svg></div>
</div>
```

Reescreva-a de forma a ser operável por voz. Justifique cada alteração indicando qual dos três modos de operação por voz é que ela desbloqueia.

**Exercício 5 — Conflito de requisitos**
Um designer exige botões só com ícone numa barra lateral estreita, por razões de espaço. Um programador propõe resolver com `aria-label`. Escreva uma resposta de meia página: o que é que isso resolve, o que é que não resolve, e que três alternativas propõe (considerando texto oculto visualmente, dicas visuais persistentes, e alteração do desenho).

**Exercício 6 — Sincronização**
A equipa de conteúdo vai mudar todos os botões «Enviar» para «Submeter». Escreva as instruções que daria à equipa de desenvolvimento para garantir que nenhum `aria-label` fica desalinhado, e proponha uma verificação automática que possa correr no processo de integração contínua.

**Exercício 7 — Nomes na listagem**
Numa listagem de dez processos, cada linha tem os botões «Ver», «Editar» e «Arquivar». Proponha uma estratégia de nomes acessíveis que permita: (a) o comando genérico «Clicar Editar» com desambiguação por número, e (b) o comando direto para um processo específico. Escreva o HTML de duas linhas da listagem.

