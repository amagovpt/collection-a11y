---
title: Interações por Teclado e Foco
layout: default
nav_order: 3
---
# Interações por Teclado e Foco

## Introdução

Nas secções anteriores tratámos daquilo que o widget **declara ser**: a sua função e o seu nome (secção «Widgets») e os seus estados, propriedades e valores (secção «Propriedades, Estados e Valores de Widgets»).

Falta a parte mais prática de todas: **como é que a pessoa mexe no widget**.

Esta secção trata da primeira e mais importante forma de o fazer — o **teclado** — e daquilo que torna o teclado utilizável: o **foco**.

> **Analogia: o holofote no palco escuro**
>
> Imagine um palco às escuras com dez atores. Só existe um holofote e ele ilumina um ator de cada vez. Quem está na plateia só percebe o que se passa se três coisas forem verdade:
>
> 1. O holofote **consegue chegar** a todos os atores que têm falas. Se houver um ator que o holofote nunca ilumina, a peça fica sem sentido.
> 2. O holofote **anda por uma ordem que se percebe** — da esquerda para a direita, e não aos saltos entre o fundo do palco e a frente.
> 3. O holofote **vê-se**. Um holofote apagado é o mesmo que não haver holofote.
>
> O foco do teclado é este holofote. Está sempre num único sítio da página, move-se de sítio em sítio, e é a única forma de muita gente saber onde está.
>
> A esta ideia junta-se uma quarta regra, tão óbvia que se esquece: **o holofote tem de conseguir sair de onde entrou**. Um ator que prenda o holofote em cima de si até ao fim do espetáculo estragou a peça.

Estas quatro ideias — **alcançar**, **ordenar**, **mostrar** e **libertar** — são o esqueleto de toda esta secção.

---

### Como as Pessoas com Deficiência Interagem com Widgets por Teclado e Foco

Há um equívoco comum: pensar que «navegação por teclado» é uma preocupação para pessoas cegas. É muito mais do que isso. O teclado é a **porta de entrada universal**, a interface que quase todas as tecnologias de apoio imitam.

#### Pessoas cegas ou com baixa visão que usam leitor de ecrã

O leitor de ecrã percorre a página e vai lendo o que encontra. Quando chega a um widget, o utilizador precisa de **parar** ali e **agir**. Esse «parar» é o foco.

Existe uma subtileza importante: os leitores de ecrã têm dois modos de funcionamento.

- **Modo de leitura** (também chamado modo de navegação ou *browse mode*): o utilizador percorre o conteúdo com as setas, salta de título em título, de ligação em ligação. As teclas são intercetadas pelo leitor de ecrã.
- **Modo de formulário/aplicação** (*forms mode*, *focus mode*): as teclas passam para a página. É neste modo que se escreve num campo ou se opera um controlo deslizante com as setas.

O leitor de ecrã decide sozinho quando trocar de modo, e decide **com base na função declarada do widget**. É por isso que a secção «Widgets» é pré-requisito desta: se o widget não diz o que é, o leitor de ecrã não sabe quando deve devolver as setas à página, e as teclas que o programador implementou nunca lá chegam.

#### Pessoas com deficiência motora

Este é o grupo mais dependente do teclado, e nem sempre usa um teclado.

- Quem tem tremor, artrite ou espasticidade pode não conseguir acertar num alvo pequeno com o rato, mas consegue premir teclas.
- Quem usa **teclados adaptados**, **varrimento por manípulo** (*switch scanning*), **sopro e sucção** (*sip-and-puff*), **apontador de cabeça** ou **controlo ocular** está, quase sempre, a gerar **eventos de teclado**. O manípulo envia Tab e Enter; o software de varrimento percorre os elementos focáveis, um a um, e a pessoa carrega no manípulo quando chega ao que quer.

Para estas pessoas, cada elemento focável a mais no caminho é tempo e esforço físico. E um elemento focável a menos é uma função que simplesmente não existe.

#### Pessoas com baixa visão que usam ampliação

Um ampliador de ecrã mostra 10 % da página de cada vez. O ampliador **segue o foco**: quando o foco muda, a janela ampliada salta para lá. Se o foco for para um sítio inesperado, a pessoa perde-se. É como se alguém lhe virasse a cabeça à força.

E se o indicador de foco for um contorno cinzento-claro de 1 píxel, ampliado 4 vezes continua a ser um contorno cinzento-claro. Não se vê.

#### Pessoas com deficiência cognitiva

Uma ordem de foco previsível reduz a carga cognitiva. Um foco que salta, desaparece ou volta atrás obriga a pessoa a reconstruir mentalmente onde está. Um esforço que se soma ao de perceber a tarefa em si.

#### Pessoas surdas ou com dificuldade de fala

Não dependem do teclado por causa da deficiência, mas beneficiam de tudo o que aqui se descreve, porque o teclado é frequentemente a alternativa ao ditado por voz num ambiente ruidoso ou partilhado.

> **Retenha isto:** um widget que funciona bem com teclado funciona quase sempre bem com varrimento, sopro e sucção, controlo ocular e leitor de ecrã. O teclado não é *um* caso de uso. É o **denominador comum**.

---

### Requisitos de Acessibilidade para Interações por Teclado e Foco

Sete requisitos, agrupados pelas quatro ideias da analogia do holofote.

#### Alcançar

**1. Tudo o que se opera tem de ser operável por teclado.**
Se existe uma ação que se faz com o rato, tem de existir uma forma de a fazer com o teclado. Não precisa de ser a mesma forma, nem com o mesmo número de gestos. Precisa de existir e de produzir o mesmo resultado. Esta é a exigência do critério **2.1.1 Teclado** (nível A) e não tem exceções úteis na prática. (A única exceção prevista pelas WCAG é para funções que dependem do **traçado** do movimento, como um programa de desenho à mão livre; um menu que se abre ao passar o rato não é, de todo, um desses casos.)

**2. Nada de armadilhas.**
Se o foco entra numa zona, tem de conseguir sair dela **usando apenas o teclado**. Se não sair, a pessoa fica presa: a única saída é fechar o separador do navegador e perder o trabalho. É o critério **2.1.2 Sem Armadilha de Teclado** (nível A).

#### Ordenar

**3. A ordem de foco tem de seguir o significado.**
A sequência pela qual o foco percorre a página tem de preservar o sentido e a operabilidade. Se o formulário se lê de cima para baixo, o foco desce de cima para baixo. Se um menu abre por baixo do botão, o passo seguinte é o primeiro item do menu, não o rodapé. Critério **2.4.3 Ordem do Foco** (nível A).

**4. As teclas têm de ser as que a pessoa espera.**
Um botão faz-se com Enter e com Espaço. Uma caixa de verificação alterna com Espaço. Uma caixa de diálogo modal fecha-se com Escape. Não porque exista uma lei que o diga, mas porque é o que toda a gente aprendeu a esperar do sistema operativo e é o que as tecnologias de apoio pressupõem. Um widget que declara `role="button"` e só responde a Enter está a mentir sobre o que é.

#### Mostrar

**5. O foco tem de ser visível.**
Tem de haver um indicador visível de onde está o foco — critério **2.4.7 Foco Visível** (nível AA). E não basta existir: as WCAG 2.2 acrescentaram que o indicador não pode ficar **completamente escondido** por outro conteúdo, como uma barra fixa no topo ou um banner de *cookies* (**2.4.11 Foco Não Obscurecido (Mínimo)**, nível AA).

**6. A pessoa tem de saber operar o widget.**
Se um widget usa teclas que não são óbvias, isso tem de estar dito em algum lado — em texto visível, numa descrição associada, ou num painel de ajuda. Um controlo que se opera com Ctrl+Shift+seta e não o diz a ninguém é, para efeitos práticos, inoperável.

#### Libertar (e não sabotar)

**7. Receber o foco não pode provocar mudanças de contexto.**
Chegar a um elemento não é o mesmo que o ativar. Se o simples facto de o foco pousar num elemento abre uma janela, submete um formulário ou muda de página, quem navega com Tab nunca conseguirá passar por ali. Critério **3.2.1 Ao Focar** (nível A).

**Bónus, e cada vez mais relevante:** atalhos com **uma única tecla** (letras, números, sinais de pontuação, sem modificadores) têm de poder ser desligados, remapeados, ou só funcionar quando o widget respetivo tem o foco — critério **2.1.4 Atalhos de Teclas de Caracteres** (nível A). Quem usa reconhecimento de fala dita palavras que o navegador recebe como sequências de teclas soltas; um atalho «S» para «Seguinte» transforma uma frase ditada num rasto de destruição. 

---

## Técnicas de Codificação

### Técnica 1: Usar o elemento nativo — a técnica que dispensa todas as outras

Um `<button>` é focável, responde a Enter e a Espaço, tem indicador de foco, funciona em todos os navegadores e não precisa de uma linha de JavaScript para nada disso.

```html
<!-- Exemplo 1a: o caminho curto -->
<button type="button" onclick="mostrarDetalhes()">
  Ver detalhes
</button>
```

```html
<!-- Exemplo 1b: o caminho longo, para obter exatamente o mesmo -->
<div role="button" tabindex="0"
     onclick="mostrarDetalhes()"
     onkeydown="if (event.key === 'Enter' || event.key === ' ') {
                  event.preventDefault();
                  mostrarDetalhes();
                }">
  Ver detalhes
</div>
```

**O que funciona bem e o que funciona mal:**

- O exemplo **1a** está correto e não tem manutenção. O comportamento de teclado vem do navegador; ninguém o pode partir num *refactor*.
- O exemplo **1b** também funciona — mas repare no que foi preciso: declarar a função (`role`), tornar focável (`tabindex="0"`), tratar duas teclas, e ainda travar o comportamento por omissão do Espaço (que, sem `preventDefault()`, faria a página deslizar para baixo). São quatro oportunidades de errar para obter zero benefício.
- O **1b** ainda está incompleto: falta o estilo de foco, falta o comportamento de `disabled`, e falta o facto de o `<div>` não ser submetido nem ativado por um formulário. Um `<button>` traz tudo isso.

**A regra prática:** só se constrói um widget de raiz quando **não existe** equivalente nativo em HTML (separadores, árvores, controlos deslizantes com dois manípulos, grelhas editáveis). Quando existe, usa-se.

---

### Técnica 2: `tabindex` — as três variantes e as duas que interessam

O atributo `tabindex` faz duas coisas distintas: decide se um elemento é **focável** e decide se está na **sequência de Tab**. Não são a mesma coisa, e confundi-las é a origem de metade dos problemas.

| Valor | Focável com Tab? | Focável por código (`elemento.focus()`)? | Quando usar |
|---|---|---|---|
| `tabindex="0"` | Sim, na posição que ocupa no DOM | Sim | Widget personalizado que deve estar na sequência normal |
| `tabindex="-1"` | Não | Sim | Elemento que só recebe foco por gestão explícita |
| `tabindex="1"` ou superior | Sim, **antes de todos os outros** | Sim | Praticamente nunca |

```html
<!-- Exemplo 2a: tabindex positivo -->
<input tabindex="3" id="nome">
<input tabindex="1" id="email">
<input tabindex="2" id="telefone">
```

**O que funciona mal:** o `tabindex` positivo cria uma **segunda fila** que passa à frente de toda a página. O foco vai ao email, ao telefone, ao nome — e só depois recomeça no cabeçalho da página, do princípio. Cada elemento novo que alguém acrescente ao longo dos anos obriga a renumerar tudo. Numa aplicação com dezenas de componentes, isto torna-se ingerível em semanas. A solução correta é sempre a mesma: **corrigir a ordem do código-fonte**, não numerar a fuga.

```html
<!-- Exemplo 2b: tabindex="-1" bem usado -->
<div id="painel-resultados" tabindex="-1">
  <h2>12 resultados encontrados</h2>
  ...
</div>
```

```js
// Depois de a pesquisa devolver resultados:
document.getElementById('painel-resultados').focus();
```

**O que funciona bem:** o painel não entra na fila do Tab (seria ruído para toda a gente), mas pode receber o foco quando faz sentido — quando os resultados chegam. O `<h2>` é lido, e a pessoa fica no início do conteúdo novo em vez de continuar no campo de pesquisa a perguntar-se se aconteceu alguma coisa.

> **Cuidado com um efeito colateral:** um `tabindex="-1"` num contentor faz com que ele possa receber foco por clique do rato em alguns navegadores, o que desenha um contorno inesperado. Resolve-se com `:focus-visible` (Técnica 5), não removendo o contorno.

---

### Técnica 3: Tratar as teclas certas, no evento certo

Quando não há alternativa a um widget personalizado, há três regras.

**Use `keydown`, não `keypress`.** O evento `keypress` está obsoleto e nunca dispara para teclas como Escape ou as setas.

**Compare com `event.key`, não com `event.keyCode`.** `event.key` devolve o nome da tecla (`"Enter"`, `" "`, `"Escape"`, `"ArrowDown"`), é legível e não está obsoleto.

**Trave o comportamento por omissão quando o roubar.** Espaço faz deslizar a página; setas fazem deslizar a página; Enter submete formulários.

```js
// Exemplo 3a: um botão personalizado, feito com cuidado
elemento.addEventListener('keydown', function (event) {
  switch (event.key) {
    case 'Enter':
    case ' ':
      event.preventDefault();   // impede o deslize da página com Espaço
      ativar();
      break;
  }
});
```

```js
// Exemplo 3b: o erro mais comum de todos
elemento.addEventListener('keydown', function (event) {
  if (event.key === 'Enter') {
    ativar();
  }
});
```

**O que funciona mal em 3b:** falta o Espaço. Um utilizador de leitor de ecrã que chegue a um `role="button"` e prima Espaço, o gesto que aprendeu para botões, não vê nada acontecer. Pior: a página desliza para baixo, e ele perde a noção de onde estava. O widget diz que é um botão e comporta-se como uma ligação.

> **Nota:** botões e ligações **não são a mesma coisa** no teclado, mesmo quando parecem iguais no ecrã. `<a href>` ativa-se **só** com Enter. `<button>` ativa-se com Enter **e** Espaço. Esta diferença não é um capricho: sinaliza «navego para outro sítio» *versus* «executo uma ação aqui». Quando se declara `role="button"`, herda-se a expectativa do botão.

---

### Técnica 4: A ordem de foco vem do DOM (e o CSS mente)

O navegador constrói a sequência de Tab a partir da **ordem do código-fonte**. O CSS pode mudar o que se vê sem mudar essa sequência, e é aí que nasce o problema.

```html
<!-- Exemplo 4a: CSS a reordenar visualmente -->
<style>
  .barra { display: flex; }
  .btn-guardar   { order: 2; }
  .btn-cancelar  { order: 1; }
</style>

<div class="barra">
  <button class="btn-guardar">Guardar</button>
  <button class="btn-cancelar">Cancelar</button>
</div>
```

**O que funciona mal:** no ecrã vê-se «Cancelar | Guardar». Com Tab, o foco vai primeiro a Guardar e depois a Cancelar. Quem vê o ecrã e usa teclado carrega no que pensa ser Cancelar e guarda. Quem usa ampliação vê o holofote saltar da direita para a esquerda sem razão aparente. O mesmo se aplica a `flex-direction: row-reverse`, a `grid-area` e a `position: absolute`.

```html
<!-- Exemplo 4b: a ordem visual e a ordem do código coincidem -->
<div class="barra">
  <button class="btn-cancelar">Cancelar</button>
  <button class="btn-guardar">Guardar</button>
</div>
```

**O que funciona bem:** o que se vê é o que se percorre. A regra é simples de enunciar e chata de cumprir: **o CSS pode mudar o aspeto, não pode mudar a sequência**. Se a ordem visual desejada não bate certo com a ordem do código, é o código que muda.

O teste é gratuito: percorra a página com Tab e diga em voz alta o que espera que seja o próximo. Se falhar, a ordem está errada.

---

### Técnica 5: O indicador de foco — nunca `outline: none` sozinho

```css
/* Exemplo 5a: a linha de CSS mais destrutiva da web */
*:focus { outline: none; }
```

**O que funciona mal:** apaga o holofote da página inteira. Para quem usa rato, não muda nada. É por isso que este erro sobrevive tanto tempo sem ser detetado. Para quem usa teclado, a página fica inutilizável: continua a funcionar, mas ninguém sabe onde está.

```css
/* Exemplo 5b: um indicador desenhado de propósito */
:focus-visible {
  outline: 3px solid #005fcc;
  outline-offset: 2px;
  border-radius: 2px;
}

/* Só se remove o contorno por omissão onde se põe um melhor */
:focus:not(:focus-visible) {
  outline: none;
}
```

**O que funciona bem:**

- `:focus-visible` aplica o indicador quando o navegador percebe que a interação é de teclado, e não quando é um clique de rato. É este o mecanismo correto para «não quero contorno ao clicar» — e não apagar o contorno para toda a gente.
- `outline` (e não `border` ou `box-shadow`) não altera o cálculo do espaço: o elemento não «salta» ao receber foco.
- `outline-offset` afasta o contorno do elemento e evita que ele se confunda com a moldura do próprio botão.
- 3 px de espessura numa cor com bom contraste sobrevive à ampliação e ao daltonismo. O contorno fino por omissão de alguns navegadores, sobre um fundo escuro, não sobrevive.

**Sobre o foco tapado.** Uma barra de navegação fixa (`position: sticky`) é a causa mais frequente de foco invisível: o elemento recebe foco, a página desliza — e o elemento fica **debaixo** da barra.

```css
/* Exemplo 5c: reservar espaço para a barra fixa ao deslizar */
:root { scroll-padding-top: 6rem; }  /* altura da barra + folga */
```

**O que funciona bem:** o navegador passa a deslizar o suficiente para o elemento focado ficar abaixo da barra. Duas linhas de CSS resolvem um critério de nível AA das WCAG 2.2.

---

### Técnica 6: Gerir o foco quando o conteúdo muda

Aqui o navegador deixa de ajudar. Quando o programador altera a página, o foco passa a ser responsabilidade sua.

Há três momentos críticos.

#### 6.1. Abrir uma caixa de diálogo modal

O padrão tem quatro passos: **guardar** onde estava, **mover** para dentro, **conter** enquanto está aberta, **devolver** ao fechar.

```html
<!-- Exemplo 6a: com o elemento nativo -->
<button type="button" id="btn-abrir">Eliminar conta</button>

<dialog id="confirmacao">
  <h2>Eliminar a conta?</h2>
  <p>Esta ação não pode ser anulada.</p>
  <button type="button" id="btn-cancelar">Cancelar</button>
  <button type="button" id="btn-confirmar">Eliminar</button>
</dialog>
```

```js
const dialogo = document.getElementById('confirmacao');

document.getElementById('btn-abrir').addEventListener('click', () => {
  dialogo.showModal();   // move o foco para dentro, contém o Tab,
                         // trata o Escape e torna o resto da página inerte
});

document.getElementById('btn-cancelar').addEventListener('click', () => {
  dialogo.close();       // devolve o foco ao botão que abriu
});
```

**O que funciona bem:** o método `showModal()` do elemento `<dialog>` faz, de graça, aquilo que durante anos foram duzentas linhas de JavaScript: contém o foco, torna o resto do documento inerte para as tecnologias de apoio, fecha com Escape e restitui o foco ao elemento que a abriu. É a Técnica 1 aplicada às caixas de diálogo.

```js
// Exemplo 6b: um modal "à mão", como se vê em muitos projetos
function abrir() {
  painel.style.display = 'block';
}
function fechar() {
  painel.style.display = 'none';
}
```

**O que funciona mal:**

- O foco **nunca entra** no painel. Quem usa teclado carrega no botão, o painel aparece, e o foco continua no botão. Tab leva a pessoa para o conteúdo *atrás* do painel, que ela não consegue ver porque está tapado por uma camada escura. É o pesadelo perfeito: focar coisas invisíveis.
- Não há Escape.
- Ao fechar, se o foco estivesse dentro do painel, o elemento focado desaparece e o foco cai no `<body>`. A pessoa é atirada para o início da página e tem de percorrer tudo outra vez para voltar ao sítio.

**Se tiver mesmo de o fazer à mão** (por exemplo, por compatibilidade com navegadores antigos), o esqueleto é:

```js
let elementoAnterior = null;

function abrir() {
  elementoAnterior = document.activeElement;   // 1. guardar
  painel.hidden = false;
  conteudoDeFundo.setAttribute('inert', '');   // 3. conter (o resto fica inerte)
  painel.querySelector('h2').focus();          // 2. mover (o h2 tem tabindex="-1")
}

function fechar() {
  conteudoDeFundo.removeAttribute('inert');
  painel.hidden = true;
  elementoAnterior?.focus();                   // 4. devolver
}
```

> O atributo `inert` é a ferramenta certa para «esta parte da página não existe agora»: remove os elementos do Tab, do rato **e** da árvore de acessibilidade, tudo de uma vez. É muito melhor do que percorrer todos os elementos a guardar e repor `tabindex`.

#### 6.2. Remover o elemento que tem o foco

```js
// Exemplo 6c: apagar uma linha de uma lista
function apagarLinha(botaoApagar) {
  botaoApagar.closest('li').remove();
}
```

**O que funciona mal:** o botão que tinha o foco deixou de existir. O foco cai no `<body>`. Para um utilizador de leitor de ecrã, a página fica em silêncio e o cursor volta ao topo depois de apagar cada linha. Apagar cinco linhas passa a ser um exercício de paciência.

```js
// Exemplo 6d: decidir para onde vai o foco antes de apagar
function apagarLinha(botaoApagar) {
  const linha = botaoApagar.closest('li');
  const proxima = linha.nextElementSibling || linha.previousElementSibling;

  linha.remove();

  if (proxima) {
    proxima.querySelector('button').focus();   // vai para a linha vizinha
  } else {
    document.getElementById('btn-adicionar').focus();   // lista vazia: vai para um destino seguro
  }
}
```

**O que funciona bem:** o foco vai para o sítio mais próximo do que a pessoa estava a fazer, e há sempre um plano B. A regra geral: **antes de destruir o elemento focado, decida quem herda o foco.**

#### 6.3. Expandir e recolher conteúdo

```html
<!-- Exemplo 6e: um acordeão -->
<h3>
  <button type="button" aria-expanded="false" aria-controls="painel-1" id="btn-1">
    Horário de funcionamento
  </button>
</h3>
<div id="painel-1" hidden>
  <p>Segunda a sexta, das 9h às 17h.</p>
</div>
```

**O que funciona bem — e o que se deve resistir a fazer:** aqui **não se mexe no foco**. O foco fica no botão. A pessoa carrega, o `aria-expanded` passa a `true`, o painel aparece **imediatamente a seguir ao botão no código** e o próximo Tab entra naturalmente lá. Mover o foco para dentro do painel seria roubar o controlo sem necessidade e impediria a pessoa de voltar a fechar com um simples Espaço.

A regra que distingue os dois casos:

| Situação | Mover o foco? |
|---|---|
| O conteúdo novo aparece **logo a seguir** ao controlo no código | **Não.** O Tab chega lá sozinho. |
| O conteúdo novo é **modal** (diálogo, painel sobreposto) | **Sim.** E devolver ao fechar. |
| O conteúdo novo aparece **noutro sítio** da página (resultados, passo seguinte) | **Sim**, se a tarefa continua lá. |
| O conteúdo é uma **mensagem** que não exige ação | **Não.** É trabalho para uma região dinâmica. |

O painel tem de estar mesmo escondido enquanto está recolhido — com `hidden`, `display: none` ou `visibility: hidden`. Um painel escondido apenas com `height: 0; overflow: hidden` continua a ter conteúdo focável lá dentro, e o Tab vai parar a botões invisíveis. Este é, provavelmente, o erro mais difícil de detetar de toda esta secção, porque no ecrã está tudo bem.

---

### Técnica 7: Um único Tab por widget composto — `tabindex` móvel

Um grupo de dez separadores não deve exigir dez Tabs para o atravessar. A convenção é: **Tab entra e sai do grupo; as setas movem-se dentro do grupo**.

```html
<!-- Exemplo 7a: tabindex móvel (roving tabindex) -->
<div role="tablist" aria-label="Definições da conta">
  <button role="tab" aria-selected="true"  tabindex="0"  id="t1">Perfil</button>
  <button role="tab" aria-selected="false" tabindex="-1" id="t2">Segurança</button>
  <button role="tab" aria-selected="false" tabindex="-1" id="t3">Notificações</button>
</div>
```

```js
// Ao mover com as setas: o separador antigo passa a -1, o novo passa a 0 e recebe foco.
function irPara(novo, antigo) {
  antigo.tabIndex = -1;
  novo.tabIndex = 0;
  novo.focus();
}
```

**O que funciona bem:** em cada momento **só um** elemento do grupo está na fila do Tab. Quem atravessa a página com Tab gasta um passo no grupo inteiro, não dez. Quem quer usar o grupo entra nele e usa as setas, que é o que qualquer pessoa faz num menu do sistema operativo.

Note também que este exemplo respeita a Técnica 1: os separadores são `<button>`, não `<div>`. Ganham a ativação por Enter e Espaço de borla; só o `role` e o `tabindex` é que foram alterados.

---

## Recomendações para Conteúdo Acessível

Estas recomendações não são código. São decisões que se tomam antes de escrever código, e que muitas vezes cabem a quem escreve o conteúdo ou desenha a interface.

**Diga quais são as teclas, quando não são óbvias.**
Enter e Espaço num botão não precisam de explicação. Ctrl+Shift+seta para reordenar uma lista precisa. Ponha a instrução em texto visível junto ao widget, ou associe-a como descrição. Não a esconda num manual em PDF.

```html
<!-- Exemplo 8a -->
<h2 id="titulo-lista">Ordem das perguntas</h2>
<p id="ajuda-lista">
  Use as setas para cima e para baixo para percorrer as perguntas.
  Prima Espaço para agarrar uma pergunta e as setas para a mover.
</p>
<ul role="listbox" aria-labelledby="titulo-lista" aria-describedby="ajuda-lista">
  ...
</ul>
```

**O que funciona bem:** a instrução está em texto visível, logo, serve toda a gente, incluindo quem tem dificuldades motoras e não sabia que havia alternativa ao arrastar. E está associada ao widget, pelo que é lida por quem chega ali com um leitor de ecrã sem ter passado pelo parágrafo.

**Não invente atalhos de tecla única.**
Se o produto precisa mesmo deles, dê uma forma de os desligar e não os deixe ativos quando o foco está num campo de texto. Prefira modificadores (Alt, Ctrl) pois não colidem com o ditado por voz nem com as teclas rápidas dos leitores de ecrã.

**Seja consistente em todo o produto.**
Se o Escape fecha um painel numa página, tem de fechar em todas. Um utilizador de teclado constrói memória muscular; uma exceção custa-lhe mais do que a regra lhe poupou.

**Não abuse do `autofocus`.**
Faz sentido no campo de pesquisa de um motor de busca, onde a pesquisa *é* a página. Não faz sentido no terceiro campo de um formulário longo: atira quem usa leitor de ecrã para o meio da página, sem contexto, e faz a página deslizar antes de a pessoa ter lido o cabeçalho.

**Reveja a ordem visual com quem desenha, não depois.**
A ordem do foco é uma decisão de *design*, não um detalhe de implementação. Se a maqueta põe o botão principal à esquerda e o secundário à direita em telemóvel, e ao contrário em computador, alguém vai ser tentado a resolver isso com `order` do CSS. Essa conversa tem de acontecer no *design*.

**Peça o percurso do foco como parte da especificação de cada componente.**
Uma especificação de componente que diz «abre um painel ao clicar» está incompleta. A versão completa diz: que teclas o ativam, para onde vai o foco quando abre, o que faz o Escape, para onde volta o foco quando fecha.

**Teste com o teclado antes de testar com o que quer que seja.**
Ponha o rato de lado durante cinco minutos e faça a tarefa principal do sítio só com Tab, Shift+Tab, Enter, Espaço, setas e Escape. Se não conseguir, também não vale a pena testar com leitor de ecrã: os problemas que encontrar vão ser estes, disfarçados.

---

### Erros Comuns

**Erro 1 — `outline: none` sem substituto.**
Já visto na Técnica 5. É o erro mais frequente e o mais fácil de corrigir. Nasce sempre da mesma frase: «aquele contorno azul é feio».
*Correção:* desenhe um indicador melhor; não apague o único que existe.

**Erro 2 — `<div onclick>`.**
Um `<div>` com um `onclick` não é focável, não responde a teclas e não se anuncia como nada. Não é «quase um botão»: é um parágrafo com um comportamento secreto que só o rato conhece.
*Correção:* `<button type="button">`.

**Erro 3 — `tabindex` positivo.**
Cria uma fila paralela que passa à frente de tudo e que fica desatualizada ao terceiro *commit*.
*Correção:* ordene o DOM.

**Erro 4 — `tabindex="0"` em coisas que não são widgets.**
Pôr `tabindex="0"` em parágrafos ou `<div>` «para o leitor de ecrã os ler» enche a fila de paragens sem função. Quem usa varrimento por manípulo paga cada uma delas em tempo real.
*Correção:* o leitor de ecrã já lê o texto. O foco é para o que se **opera**.

**Erro 5 — Só Enter num `role="button"`.**
Já visto na Técnica 3. O widget promete um botão e entrega uma ligação.
*Correção:* trate Enter **e** Espaço, com `preventDefault()` no Espaço.

**Erro 6 — Menus que só abrem com `:hover`.**
Não existe `hover` no teclado. Se o submenu só aparece ao passar o rato, ele não existe para quem usa teclado.
*Correção:* o submenu abre também ao ativar o item com teclado, com `aria-expanded` no controlo. 

**Erro 7 — Foco preso.**
Um `<iframe>` de terceiros, um leitor de vídeo, um mapa interativo ou um modal artesanal que confina o Tab e não trata o Escape. A pessoa fica presa e a única saída é fechar o separador.
*Correção:* o foco só se **contém** em modais, e um modal contido tem **sempre** Escape e um botão Fechar alcançável.

**Erro 8 — Conteúdo focável escondido.**
Painéis recolhidos com `height: 0`, carrosséis com os *slides* de fora do ecrã por `transform`, menus escondidos com `opacity: 0`. O conteúdo desapareceu do ecrã mas continua na fila do Tab. O foco vai para lá e a pessoa fica a carregar em Tab às cegas.
*Correção:* `hidden`, `display: none` ou `inert` no que está escondido. E teste sempre: carregue em Tab e veja se o indicador desaparece durante uns passos.

**Erro 9 — Foco atirado para o `<body>`.**
Ao fechar um modal, ao apagar o elemento focado, ao substituir uma zona da página por conteúdo novo. Para quem usa leitor de ecrã, isto significa voltar ao início do documento.
*Correção:* antes de destruir ou esconder, decida quem herda o foco.

**Erro 10 — Mudança de contexto ao focar.**
`onfocus="this.form.submit()"`, um `<select>` que navega ao mudar de valor com as setas, um separador que carrega uma página nova só por o foco lá passar. Quem usa Tab nunca consegue atravessar o controlo.
*Correção:* ações acontecem na **ativação** (Enter, Espaço, clique), nunca na chegada do foco.

**Erro 11 — Indicador de foco tapado pela barra fixa.**
O elemento tem foco, o contorno existe, mas está debaixo do cabeçalho *sticky* ou do banner de *cookies*.
*Correção:* `scroll-padding-top`, e verifique também o primeiro e o último elemento de cada zona.

**Erro 12 — `aria-hidden="true"` em conteúdo focável.**
Esconder um painel da árvore de acessibilidade sem o tirar da fila do Tab produz o pior dos mundos: o foco vai para um elemento que o leitor de ecrã se recusa a anunciar. O leitor de ecrã fica em silêncio absoluto.
*Correção:* `inert` (que faz as duas coisas) ou `hidden`.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **O teclado é o denominador comum.** Varrimento por manípulo, sopro e sucção, controlo ocular, leitor de ecrã e apontador de cabeça geram, quase todos, eventos de teclado. Resolver o teclado resolve muita coisa de uma vez.
2. **Quatro ideias, um holofote:** o foco tem de **alcançar** tudo o que se opera, seguir uma **ordem** que se percebe, ser **visível**, e conseguir **sair** de onde entrou.
3. **O elemento nativo é a melhor técnica de acessibilidade que existe.** `<button>`, `<a href>` e `<dialog>` trazem foco, teclas e estilos por omissão. Só se constrói de raiz o que não existe.
4. **`tabindex` tem duas variantes úteis:** `0` para entrar na fila, `-1` para poder receber foco por código. A variante positiva não é uma delas.
5. **A ordem de foco vem do DOM.** Quando o CSS reordena o que se vê, ele mente. Corrige-se no código-fonte, não com `tabindex`.
6. **Nunca `outline: none` sozinho.** `:focus-visible` com um contorno espesso e contrastado, e `scroll-padding-top` para ele não ficar debaixo da barra fixa.
7. **`role="button"` obriga a Enter e a Espaço** — e a travar o comportamento por omissão do Espaço.
8. **O foco é responsabilidade sua a partir do momento em que o conteúdo muda.** Modal: guardar, mover, conter, devolver. Elemento apagado: decidir o herdeiro antes de destruir. Acordeão: não mexer.
9. **Um Tab por widget composto.** `tabindex` móvel: Tab entra e sai, setas movem-se dentro.
10. **Cinco minutos sem rato revelam mais do que uma auditoria automática.** Nenhuma ferramenta deteta uma ordem de foco ilógica ou um foco que se perde ao fechar um painel.

---

### Exercícios Práticos

#### Exercício 1 — Percurso do holofote (observação)

Escolha uma página de um serviço público português que use com frequência e que tenha um formulário ou um menu com submenus.

Sem tocar no rato:

1. Carregue em Tab do início ao fim e conte quantos passos precisa para chegar ao conteúdo principal.
2. Anote todos os momentos em que **perdeu de vista** o indicador de foco.
3. Anote todos os momentos em que o foco saltou para um sítio **inesperado**.
4. Tente abrir e fechar um menu. Conseguiu fechá-lo sem rato?
5. Verifique se algum elemento continua a receber foco depois de ter desaparecido do ecrã.

*Entrega:* uma tabela com três colunas — o que aconteceu, que requisito desta secção foi violado, que correção propõe.

#### Exercício 2 — Corrigir o botão falso

```html
<div class="btn" onclick="guardar()">Guardar</div>

<style>
  .btn:focus { outline: none; }
  .btn { background: #0066cc; color: white; padding: 8px 16px; }
</style>
```

1. Enumere **todos** os problemas de teclado e foco deste bloco (são pelo menos quatro).
2. Escreva a versão corrigida usando o elemento nativo.
3. Escreva a versão corrigida **sem** poder mudar o `<div>` (imagine uma restrição de um sistema legado), e compare o número de linhas com a alínea 2.

#### Exercício 3 — Ordem de foco sabotada pelo CSS

```html
<style>
  .acoes { display: flex; flex-direction: row-reverse; }
</style>

<div class="acoes">
  <button id="a">Anterior</button>
  <button id="b">Seguinte</button>
  <button id="c">Cancelar</button>
</div>
```

1. Desenhe a ordem **visual** dos botões no ecrã.
2. Escreva a ordem pela qual o **Tab** os percorre.
3. Explique porque é que isto é perigoso para quem vê o ecrã e usa teclado.
4. Corrija — sem usar `tabindex`.

#### Exercício 4 — O ciclo de vida de um modal

Construa uma caixa de diálogo de confirmação («Eliminar ficheiro?») com dois botões, Cancelar e Eliminar.

Requisitos:

- Abre a partir de um botão «Eliminar» numa lista.
- O foco entra na caixa quando abre.
- O Tab não sai da caixa enquanto ela está aberta.
- O Escape fecha.
- Ao fechar por Cancelar, o foco volta ao botão que a abriu.
- Ao fechar por Eliminar, o item desaparece da lista — e o foco **não pode** cair no `<body>`.

Faça duas versões: uma com `<dialog>` e `showModal()`, outra à mão com `inert`. Escreva um parágrafo a comparar o esforço de manutenção das duas.

#### Exercício 5 — Auditoria do indicador de foco

Numa página do seu projeto:

1. Verifique se o indicador de foco é visível em **todos** os elementos interativos, incluindo os que estão sobre fundos escuros e sobre imagens.
2. Amplie a página para 400 % e repita.
3. Se a página tiver cabeçalho fixo, percorra-a com Tab e verifique se algum elemento focado fica escondido debaixo dele. Corrija com `scroll-padding-top`.
4. Substitua o indicador por omissão por um desenhado de propósito, usando `:focus-visible`.

#### Exercício 6 — Do rato ao teclado

Encontre no seu projeto um comportamento que só existe com o rato: um menu que abre com `:hover`, um botão que só aparece quando se passa por cima de um cartão, uma ação de arrastar e largar.

1. Descreva o que acontece hoje a quem usa apenas o teclado.
2. Proponha o equivalente por teclado, indicando explicitamente: que teclas o ativam, onde fica o foco durante a operação, e o que faz o Escape.
3. Discuta: a alternativa por teclado deve produzir exatamente o mesmo resultado, mas precisa de ser exatamente o mesmo gesto?

#### Exercício 7 — `tabindex` móvel (desafio)

Pegue no exemplo 7a e implemente-o por completo:

- Seta para a direita e para a esquerda movem entre separadores.
- Home vai para o primeiro, End vai para o último.
- Ao chegar ao fim, volta ao princípio.
- Só um separador tem `tabindex="0"` em cada momento.
- Tab a partir do separador ativo salta para dentro do painel correspondente.

*Verificação:* atravesse o grupo inteiro com um único Tab. Se precisar de mais do que um, algo está errado.

---

