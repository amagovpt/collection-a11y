---
title: Interações por Rato e Toque
layout: default
nav_order: 4
---
# Interações por Rato e Toque

## Introdução

Na secção anterior tratámos do teclado: como se **chega** a um widget e como se sabe **onde estamos**. Um widget que passe nesses testes já é operável por muita gente.

Mas a maioria das pessoas, incluindo a maioria das pessoas com deficiência, não usa só teclado. Usa o dedo, o rato, uma caneta, um apontador de cabeça, um *trackball*, um sistema de seguimento ocular. Todos estes dispositivos têm um nome comum na especificação: **ponteiro**.

E é aqui que a acessibilidade deixa de ser sobre semântica e passa a ser sobre **física**. Um botão pode ter função, nome e estado impecáveis, e continuar a ser impossível de usar por ser demasiado pequeno, por exigir um gesto que a mão não faz, ou por disparar antes de a pessoa ter a certeza.

> **Analogia: atirar dardos com a mão a tremer**
>
> Imagine um jogo de dardos. Se o alvo for do tamanho de uma moeda, só os melhores acertam. Se for do tamanho de um prato, quase toda a gente acerta.
>
> Agora acrescente três regras absurdas ao jogo:
> 1. O dardo conta **no momento em que sai da mão**, mesmo que ainda não tenha chegado ao alvo — não há como desistir a meio.
> 2. Para lançar o dardo tem de descrever um oito no ar com o braço.
> 3. O alvo só aparece enquanto estiver a olhar diretamente para ele; se desviar os olhos para consultar as regras, desaparece.
>
> Estas três regras absurdas são, respetivamente, a **ativação no evento de pressão**, os **gestos complexos** e o **conteúdo dependente do rato**. Não são hipóteses académicas: estão em interfaces reais, todos os dias.

Esta secção trata das quatro exigências de qualquer interação por ponteiro:

1. **Um alvo em que se acerte.**
2. **Um gesto que a mão consiga fazer.**
3. **Um erro que se possa corrigir.**
4. **Um conteúdo que não fuja.**

---

### Como as Pessoas com Deficiência Interagem com Widgets por Rato e Toque

Há uma ideia errada muito comum: «quem tem uma limitação motora usa o teclado». Muitas pessoas **usam ponteiro**. Só o usam de forma diferente daquela que o programador imaginou.

**Pessoas com tremor, espasticidade ou perda de força**
Usam o rato ou o dedo, mas com pouca precisão. Acertam num alvo grande; falham um alvo de 12 píxeis colado a outro. Podem carregar sem querer, ou carregar durante mais tempo do que a interface espera. Um tremor pode transformar um toque simples num pequeno arrastar. E um arrastar acidental, numa interface que reordena listas, é uma alteração de dados que a pessoa nem percebeu.

**Pessoas que usam apontadores alternativos**
Uma caneta na boca, um apontador de cabeça, um *joystick* de queixo, um sistema de seguimento ocular. Todos estes dispositivos produzem **um único ponto de contacto**, e produzem-no com muito esforço. Fazer um gesto de dois dedos é fisicamente impossível; manter uma trajetória precisa durante dois segundos é exaustivo.

**Pessoas com baixa visão**
Usam ampliação. Com o ecrã ampliado a 400%, o alvo é grande. Mas o **contexto** desapareceu. A pessoa procura o botão fechar da janela de diálogo e vê apenas um pedaço de fundo cinzento. Alvos maiores e mais bem espaçados são mais fáceis de encontrar, não apenas de acertar.

**Pessoas cegas que usam ecrã tátil**
Este é o caso menos intuitivo. Com o VoiceOver ou o TalkBack ligados, os gestos **mudam de significado**: tocar já não ativa, explora; ativar exige toque duplo; deslizar o dedo já não faz *scroll*, muda de elemento. O leitor de ecrã **intercepta** os gestos antes de eles chegarem à página. Consequência prática: um widget que dependa de um deslize personalizado ou de um toque prolongado simplesmente **não recebe** esse gesto. O que chega à página é um evento de clique sintético, pelo que um widget que só ouça `touchstart` ou `mousedown` fica mudo para estes utilizadores.

**Pessoas com deficiência cognitiva**
Beneficiam de poder **hesitar**. Aproximar o dedo, ver o que acontece, mudar de ideias, afastar. Uma interface que age no primeiro contacto retira essa margem. Beneficiam também de gestos convencionais: um gesto inventado é mais uma coisa para aprender e memorizar.

**Pessoas com limitações temporárias ou situacionais**
Um braço engessado, um bebé ao colo, um autocarro aos solavancos, luvas no inverno. Não são «pessoas com deficiência», mas usam a interface exatamente nas mesmas condições, e as mesmas soluções servem-nas. É o argumento mais fácil de vender a uma equipa cética.

---

### Requisitos de Acessibilidade para Interações por Rato e Toque

Reunindo as necessidades acima, uma interação por ponteiro acessível cumpre cinco requisitos:

**1. O alvo tem de ser suficientemente grande e suficientemente espaçado**
Não basta que o elemento seja visível: a **área sensível** ao toque tem de ser generosa. Um ícone de 16×16 píxeis pode ter uma área de toque de 44×44 sem mudar de aspeto.

**2. Nenhuma funcionalidade pode depender de um gesto complexo**
Gestos de vários dedos (pinça, dois dedos) ou baseados em trajetória (deslizar, arrastar, desenhar) têm de ter sempre uma alternativa de **ponteiro único e sem trajetória**: um toque simples, um clique num botão.

**3. A ativação tem de ser cancelável**
A ação acontece quando se **larga**, não quando se **carrega**. E afastar o dedo antes de largar cancela. Este requisito existe para dar à pessoa uma última hipótese de mudar de ideias.

**4. Nada de funcionalidade exclusiva do rato**
Se existe só com `:hover`, não existe para toque. Se existe só com clique-direito, não existe para muita gente. Todo o comportamento de ponteiro tem de ter um equivalente por teclado e por toque.

**5. Conteúdo que aparece ao passar o ponteiro tem de ser controlável**
Uma dica de contexto ou um menu suspenso acionado por `:hover` tem de poder ser **fechado** sem mover o ponteiro, tem de permitir que o ponteiro **entre lá dentro** sem desaparecer, e tem de **permanecer** até deixar de ser preciso.

> **Referência contextual.** Os critérios WCAG que amarram esta secção são o **2.5.1 — Gestos de Ponteiro (A)**, o **2.5.2 — Cancelamento do Ponteiro (A)**, o **2.5.4 — Ativação por Movimento (A)** e o **1.4.13 — Conteúdo em Foco ou ao Passar o Ponteiro (AA)**. A WCAG 2.2 acrescentou o **2.5.7 — Movimentos de Arrastar (AA)** e o **2.5.8 — Tamanho do Alvo, Mínimo (AA)**; o **2.5.5 — Tamanho do Alvo, Melhorado (AAA)** já existia na 2.1.
>
> Uma nota importante sobre a base legal: em Portugal, o Decreto-Lei n.º 83/2018 e a norma EN 301 549 fixam a **WCAG 2.1, Nível AA** como requisito. Isso significa que o **2.5.7** e o **2.5.8** ainda **não** fazem parte da obrigação legal atual — mas representam a direção clara das normas e resolvem problemas reais. Trate-os como o próximo patamar, não como opcional. A lista completa e organizada está na secção final do módulo.

---

## Técnicas de Codificação

### Técnica 1 — Deixar o navegador tratar do ponteiro

Antes de qualquer técnica sofisticada, a regra que resolve a maior parte dos casos: **use o elemento nativo e o evento `click`**.

O evento `click` não é «o evento do rato». É o **evento de ativação** do navegador. Dispara com o rato, com o dedo, com o Enter num `<button>`, com o toque duplo do VoiceOver, com um comando de voz. E dispara já com o comportamento de cancelamento correto — no `up`, não no `down`.

**Exemplo mau:**

```html
<div class="cartao" onmousedown="abrirDetalhe()">
  Encomenda #4471
</div>
```

**O que está mal neste exemplo:**

Três falhas de uma vez. Primeiro, `mousedown` dispara no instante em que o botão do rato desce: quem carregar por engano não tem como recuar, e quem tem tremor ativa coisas sem querer. Segundo, `mousedown` **não existe no toque** de forma fiável nem nos leitores de ecrã de ecrã tátil — o widget fica inerte. Terceiro, sendo um `<div>`, não é focável nem acionável por teclado (a secção *Interações por Teclado e Foco* trata desse lado).

**Exemplo bom:**

```html
<button type="button" class="cartao" onclick="abrirDetalhe()">
  Encomenda #4471
</button>
```

**Porque funciona bem:**

Um só evento cobre rato, dedo, teclado, voz e leitor de ecrã. E o `click` do navegador já implementa o requisito de cancelamento: se carregar no botão e arrastar o dedo para fora antes de largar, **não acontece nada**. Experimente — é um comportamento que existe há décadas e que muitas interfaces personalizadas deitam fora sem perceber.

---

### Técnica 2 — Aumentar o alvo sem mudar o desenho

O problema clássico: o designer quer um ícone pequeno e discreto; a acessibilidade quer um alvo grande. Não são incompatíveis — a **área sensível** e a **área visível** são coisas diferentes.

**Exemplo mau:**

```html
<button class="fechar">✕</button>

<style>
.fechar {
  width: 16px;
  height: 16px;
  padding: 0;
  border: none;
  background: none;
}
</style>
```

**O que está mal neste exemplo:**

16×16 píxeis. Fica abaixo do mínimo de 24×24 do critério 2.5.8 e muito abaixo dos 44×44 recomendados pelo 2.5.5. Para uma pessoa com tremor a tentar fechar uma janela de diálogo, isto é um alvo de dardos do tamanho de uma moeda. Note também que o rótulo é um caráter «✕», um problema de **nome**, tratado na secção *Widgets*.

**Exemplo bom (solução simples — `padding`):**

```html
<button class="fechar" aria-label="Fechar">
  <svg aria-hidden="true" focusable="false" width="16" height="16">…</svg>
</button>

<style>
.fechar {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 44px;
  min-height: 44px;
  padding: 14px;      /* 16 + 14 + 14 = 44 */
  border: none;
  background: none;
}
</style>
```

**Porque funciona bem:**

O ícone continua com 16 píxeis. O **alvo** tem 44. Não se mexeu no desenho, mexeu-se no espaço à volta. O `padding` faz parte da área sensível do botão, e é a solução mais barata que existe para o tamanho do alvo.

**Exemplo bom (quando o `padding` estraga o alinhamento — pseudo-elemento):**

```css
.fechar {
  position: relative;
  width: 16px;
  height: 16px;
}

.fechar::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 44px;
  height: 44px;
}
```

**Porque funciona bem:**

O pseudo-elemento é invisível mas capta o ponteiro. A caixa do botão continua a ocupar 16×16 no fluxo, pelo que o alinhamento com os elementos vizinhos não muda, mas o alvo real cresce para 44×44 centrados no ícone.

**Cuidado com este truque:** áreas invisíveis que se sobrepõem são pior do que alvos pequenos. Se dois ícones estiverem a 20 píxeis um do outro e ambos tiverem um alvo invisível de 44, os alvos cruzam-se e a pessoa acerta no botão errado, sem qualquer pista visual de porquê. Se for usar a técnica, **garanta espaçamento suficiente** entre os elementos. Alvo grande e alvos que não se pisam são o mesmo requisito.

---

### Técnica 3 — Dar alternativa a gestos de trajetória

Um gesto de trajetória é aquele em que **o caminho importa**: deslizar, arrastar, desenhar, girar. Se o caminho importa, quem não consegue traçar um caminho não usa a funcionalidade.

**Exemplo mau:**

```html
<!-- Galeria de imagens: muda de imagem só com swipe -->
<div class="galeria" id="galeria">
  <img src="foto-1.jpg" alt="Fachada do edifício">
</div>

<script>
  // deteta deslize horizontal e muda a foto
  galeria.addEventListener('touchstart', guardarPosicaoInicial);
  galeria.addEventListener('touchend', calcularDirecaoEMudarFoto);
</script>
```

**O que está mal neste exemplo:**

A única forma de mudar de foto é um deslize. Falha o 2.5.1 (gesto baseado em trajetória sem alternativa de ponteiro único). Quem usa apontador de cabeça não desliza. Quem usa VoiceOver nem sequer recebe o gesto — o leitor de ecrã fica com ele. E, como não há botões, também não há nada para o teclado alcançar: um único erro de conceção que fecha a porta a três grupos ao mesmo tempo.

**Exemplo bom:**

```html
<div class="galeria">
  <img src="foto-1.jpg" alt="Fachada do edifício">

  <button type="button" class="anterior">Foto anterior</button>
  <button type="button" class="seguinte">Foto seguinte</button>
</div>

<script>
  // O deslize CONTINUA a funcionar — é um extra, não o único caminho.
  galeria.addEventListener('touchstart', guardarPosicaoInicial);
  galeria.addEventListener('touchend', calcularDirecaoEMudarFoto);
</script>
```

**Porque funciona bem:**

O deslize não foi removido — foi **complementado**. Isto é essencial de perceber: o 2.5.1 não proíbe gestos, exige alternativas. Quem gosta de deslizar continua a deslizar; quem não consegue carrega no botão. Dois botões resolvem o gesto, o teclado e o comando por voz de uma assentada.

> O padrão completo do carrossel — anúncio da mudança, contador «3 de 12», controlo de rotação automática — pertence à secção *Widgets Complexos*. Aqui interessa só o gesto.

---

### Técnica 4 — Dar alternativa ao arrastar

Arrastar é o gesto de trajetória mais comum e o mais difícil de todos: exige manter a pressão **e** manter a precisão **e** manter o movimento, ao mesmo tempo. É o alvo do critério 2.5.7 (WCAG 2.2).

**Exemplo mau:**

```html
<h2>Ordene as suas prioridades</h2>
<ul class="ordenavel">
  <li draggable="true">Atendimento presencial</li>
  <li draggable="true">Atendimento telefónico</li>
  <li draggable="true">Atendimento online</li>
</ul>
```

**O que está mal neste exemplo:**

Arrastar e largar é a **única** forma de ordenar. Para quem tem tremor, a lista salta para o sítio errado; para quem usa seguimento ocular, o gesto é impraticável; num ecrã ampliado a 400%, o destino do arrastar está fora do ecrã visível.

**Exemplo bom:**

```html
<h2>Ordene as suas prioridades</h2>
<ul class="ordenavel">
  <li draggable="true">
    <span id="item-1">Atendimento presencial</span>
    <button type="button" aria-labelledby="subir-1 item-1">
      <span id="subir-1">Subir</span>
    </button>
    <button type="button" aria-labelledby="descer-1 item-1">
      <span id="descer-1">Descer</span>
    </button>
  </li>
  …
</ul>
```

**Porque funciona bem:**

Cada item ganhou dois botões de ponteiro único. O arrastar mantém-se para quem o prefere. E os nomes acessíveis resultantes — «Subir, Atendimento presencial» — dizem a que item o botão pertence, o que é indispensável quando se ouve a lista em vez de a ver.

**Outros casos de arrastar e as suas alternativas:**

| Onde há arrastar | Alternativa de ponteiro único |
|---|---|
| Deslizador de preço | Campos de texto para mínimo e máximo, ou botões `−` / `+` |
| Reordenar cartões num quadro | Menu «Mover para…» em cada cartão |
| Carregar ficheiros por arrastar | Botão «Escolher ficheiro» sempre visível |
| Mapa que se arrasta | Botões de deslocação e campo de pesquisa de morada |
| Assinatura desenhada | Alternativa de assinatura escrita ou carregada |

> **Nota:** o critério 2.5.7 tem uma exceção para os casos em que o arrastar é **essencial** à atividade (por exemplo, um simulador de desenho livre). A exceção é estreita: «é mais cómodo assim» não é essencial. Na dúvida, dê a alternativa.

---

### Técnica 5 — Ativar ao largar, não ao carregar

Este é o requisito que quase ninguém conhece e que quase todas as interfaces personalizadas quebram: o **2.5.2 — Cancelamento do Ponteiro**.

A ideia é a do dardo que ainda pode ser travado: entre carregar e largar existe uma janela de arrependimento. Essa janela é uma funcionalidade de acessibilidade, não um detalhe técnico.

**Exemplo mau:**

```html
<div class="opcao" onpointerdown="apagarConta()">Apagar conta</div>
```

**O que está mal neste exemplo:**

A conta é apagada no instante em que o dedo toca no ecrã. Uma pessoa com tremor que roce o elemento sem intenção nenhuma perdeu a conta. Não há como cancelar, não há como recuar, não há sequer como perceber o que aconteceu. É o pior caso possível: ação destrutiva no evento de pressão.

**Exemplo bom:**

```html
<button type="button" onclick="confirmarApagarConta()">Apagar conta</button>
```

**Porque funciona bem:**

O `click` só dispara se o `down` **e** o `up` ocorrerem sobre o mesmo elemento. Carregar e arrastar para fora antes de largar cancela de graça, sem código. É este comportamento que a Técnica 1 preserva e que qualquer manipulação manual de `pointerdown` deita fora.

**Quando é mesmo preciso reagir ao `pointerdown`:**

Há casos legítimos: um piano virtual, um jogo, um botão que abre um menu com pré-visualização. O critério permite-os desde que exista uma de quatro saídas: não haver ação no `down`, poder abortar antes do `up`, o `up` **desfazer** o que o `down` fez, ou o `down` ser essencial.

```js
const tecla = document.querySelector('#do-central');

tecla.addEventListener('pointerdown', () => tocarNota('do'));
tecla.addEventListener('pointerup', () => pararNota('do'));
tecla.addEventListener('pointerleave', () => pararNota('do')); // arrastar para fora cancela
```

**Porque funciona bem:**

Aqui o `down` é essencial: um instrumento tem de soar quando se carrega, não quando se larga. E existe saída: sair do elemento com o dedo ainda em baixo pára a nota. A ação é **reversível**, que é exatamente o que o critério pede.

---

### Técnica 6 — Usar eventos de ponteiro, não eventos de rato

Se tiver mesmo de escrever gestão de ponteiro à mão, escreva-a uma vez só. A API de **Pointer Events** unifica rato, dedo e caneta num único conjunto de eventos.

**Exemplo mau:**

```js
elemento.addEventListener('mousedown', iniciar);
elemento.addEventListener('mousemove', mover);
elemento.addEventListener('mouseup', terminar);
```

**O que está mal neste exemplo:**

Só o rato. No telemóvel, os navegadores emulam alguns eventos de rato por compatibilidade, mas de forma inconsistente e com atraso; gestos de caneta ficam de fora. O resultado típico é o widget «quase funcionar» no telemóvel, o que é pior do que não funcionar de todo, porque ninguém o deteta em testes.

**Exemplo bom:**

```js
elemento.addEventListener('pointerdown', iniciar);
elemento.addEventListener('pointermove', mover);
elemento.addEventListener('pointerup', terminar);
elemento.addEventListener('pointercancel', cancelar);

function iniciar(evento) {
  // Ignorar toques secundários: garante ponteiro único
  if (!evento.isPrimary) return;
  elemento.setPointerCapture(evento.pointerId);
  …
}
```

**Porque funciona bem:**

Um só conjunto de eventos para todos os dispositivos. `evento.isPrimary` protege contra toques acidentais de um segundo dedo, comuns em quem tem controlo motor reduzido. `setPointerCapture` garante que o widget continua a receber os eventos mesmo que o dedo saia da sua área, evitando o clássico «arrastar que se perde a meio». E `pointercancel` dá-lhe um sítio onde repor o estado quando o sistema interrompe o gesto.

**Continua a ser preciso:** isto resolve a **compatibilidade** de dispositivos, não o requisito 2.5.1. Um gesto implementado com Pointer Events continua a ser um gesto. A alternativa de ponteiro único da Técnica 3 é sempre necessária.

---

### Técnica 7 — Conteúdo ao passar o ponteiro que não foge

O critério 1.4.13 aplica-se a tudo o que apareça por cima do conteúdo quando se passa o ponteiro (ou se recebe foco): dicas de contexto, pré-visualizações, menus suspensos. Exige três propriedades: **dispensável**, **percorrível** e **persistente**.

**Exemplo mau:**

```html
<span class="termo" data-dica="Rendimento coletável é o valor sobre o qual incide o imposto, depois de aplicadas as deduções.">
  rendimento coletável
</span>

<style>
.termo:hover::after {
  content: attr(data-dica);
  position: absolute;
  …
}
</style>
```

**O que está mal neste exemplo:**

Três falhas. **Não é dispensável:** não há forma de fechar a dica sem tirar o rato dali. Quem usa ampliação pode ter a dica a tapar exatamente o texto que queria ler a seguir. **Não é percorrível:** o `::after` desaparece se o rato tentar entrar nele, o que impossibilita ler uma dica longa que exija *scroll*, ou selecionar texto lá dentro. **Aparece só com `:hover`:** não aparece por teclado, nem no toque.

**Exemplo bom:**

```html
<button type="button" class="termo" aria-describedby="dica-rc">
  rendimento coletável
</button>

<div id="dica-rc" role="tooltip" class="dica" hidden>
  Valor sobre o qual incide o imposto, depois de aplicadas as deduções.
</div>

<style>
.dica { padding: 12px; }          /* área generosa: o ponteiro pode entrar */
.dica:hover { display: block; }   /* não desaparece quando o rato entra */
</style>

<script>
const termo = document.querySelector('.termo');
const dica  = document.getElementById('dica-rc');

function mostrar() { dica.hidden = false; }
function esconder() { dica.hidden = true; }

termo.addEventListener('pointerenter', mostrar);
termo.addEventListener('focus', mostrar);
termo.addEventListener('click', () => dica.hidden = !dica.hidden); // funciona no toque

document.addEventListener('keydown', (e) => {
  if (e.key === 'Escape') esconder();     // dispensável
});

// Só esconde quando o ponteiro sai do termo E da dica
function talvezEsconder() {
  requestAnimationFrame(() => {
    if (!termo.matches(':hover') && !dica.matches(':hover') && !termo.matches(':focus')) {
      esconder();
    }
  });
}
termo.addEventListener('pointerleave', talvezEsconder);
dica.addEventListener('pointerleave', talvezEsconder);
</script>
```

**Porque funciona bem:**

**Dispensável:** o Escape fecha a dica sem mexer o ponteiro. **Percorrível:** a dica só desaparece quando o ponteiro sai dela *e* do termo, pelo que se pode entrar lá dentro para ler ou selecionar. **Persistente:** não há temporizador que a faça desaparecer sozinha. Fica até a pessoa a dispensar ou afastar o ponteiro. E o `click` faz com que o mesmo componente funcione no toque, onde o `:hover` não existe.

> **Atenção ao `role="tooltip"`:** o suporte é irregular e a dica não é anunciada por si só. O que faz o trabalho é o `aria-describedby` no elemento que aciona a dica. Este é um caso em que a semântica correta não substitui o teste real.

---

### Técnica 8 — Não fazer da agitação do dispositivo um requisito

O critério 2.5.4 trata da funcionalidade acionada por **movimento do dispositivo** (abanar para desfazer, inclinar para navegar) ou por movimento captado por sensores.

**Exemplo mau:**

```js
window.addEventListener('devicemotion', (e) => {
  if (detetarAbanao(e)) desfazerUltimaAcao();
});
```

**O que está mal neste exemplo:**

Duas falhas simétricas. Quem tem o telemóvel num suporte de cadeira de rodas, ou não tem força para o abanar, **não consegue** desfazer. Quem tem tremor ou espasmos abana o telemóvel sem querer e **desfaz sem querer**. O gesto é ao mesmo tempo inalcançável para uns e demasiado fácil para outros.

**Exemplo bom:**

```html
<button type="button" onclick="desfazerUltimaAcao()">Desfazer</button>

<label>
  <input type="checkbox" id="abanar" checked>
  Abanar para desfazer
</label>
```

```js
window.addEventListener('devicemotion', (e) => {
  if (!document.getElementById('abanar').checked) return;
  if (detetarAbanao(e)) desfazerUltimaAcao();
});
```

**Porque funciona bem:**

Cumpre as duas metades do critério: existe uma alternativa por componente de interface **e** o gesto de movimento pode ser **desativado**. Note que o critério 2.5.4 é de **Nível A** — está dentro da base legal, e não é raro ser esquecido em aplicações web para telemóvel.

---

## Recomendações para Conteúdo Acessível

**Meça alvos, não confie no olho.** 24×24 CSS é o mínimo (2.5.8); 44×44 é o objetivo (2.5.5) e é o que as principais orientações de interface móvel recomendam há anos. Meça com as ferramentas de programador do navegador, na caixa do elemento, não no ícone.

**Trate o espaçamento como parte do alvo.** Dois botões de 44 píxeis colados são piores do que dois botões de 32 com 16 píxeis de intervalo. O 2.5.8 reconhece isto explicitamente numa exceção de espaçamento. Ligações de texto em linha corrida também têm exceção, mas listas de ligações empilhadas, tão comuns em rodapés, não têm: dê-lhes espaço.

**Faça o teste do polegar.** Abra a página no telemóvel e use-a só com o polegar da mão que segura o aparelho, em movimento. Se falhar alvos, os seus utilizadores também falham.

**Faça o teste do dedo indicador rígido.** Estique o indicador e use a página sem dobrar o dedo, com o braço apoiado. É uma aproximação grosseira a um apontador de cabeça, e revela imediatamente todos os gestos impossíveis.

**Ligue o VoiceOver ou o TalkBack no seu telemóvel.** Cinco minutos com o leitor de ecrã ligado num ecrã tátil ensinam mais sobre gestos do que cinco horas de leitura. Vai perceber, de imediato, quais dos seus gestos personalizados nunca chegam à página.

**Não desative o zoom.** `<meta name="viewport" content="user-scalable=no">` ou `maximum-scale=1` retira à pessoa com baixa visão a única ferramenta que compensa alvos pequenos. Não há justificação de desenho que compense isto.

**Assuma dispositivos híbridos.** Um portátil com ecrã tátil, um tablet com rato *Bluetooth*, um telemóvel com caneta. «Móvel = toque» e «desktop = rato» são falsos desde 2013. Use `@media (pointer: coarse)` para **aumentar** alvos, nunca para decidir que funcionalidade existe.

**Cuidado com o toque prolongado.** É invisível (nada na interface o anuncia), colide com as funções do sistema e do leitor de ecrã, e exige manter a pressão. Precisamente o que muita gente não consegue. Se o usar, é sempre atalho de uma ação que já existe em botão visível.

**Escreva a alternativa na especificação, não no fim.** Custa cinco minutos decidir que o carrossel terá botões antes de ele existir. Custa dois dias acrescentá-los depois de a animação estar toda montada em torno do gesto.

---

### Erros Comuns

**1. Ativar no `mousedown` ou `pointerdown`**
O erro de cancelamento clássico. Retira a janela de arrependimento e transforma qualquer roçar acidental numa ação. Regra prática: se o seu código tem `mousedown` e não tem uma razão escrita para isso, é um erro. *(2.5.2)*

**2. Ícones minúsculos em barras de ferramentas**
Uma fila de ícones de 16 píxeis, colados, no canto superior direito. Cada um faz uma coisa diferente e uma delas é «apagar». Nem quem tem boa motricidade acerta à primeira. *(2.5.8, 2.5.5)*

**3. Deslizar como único caminho**
Carrosséis, separadores que só mudam com *swipe*, listas em que a única forma de apagar é deslizar para a esquerda. Falha para apontadores alternativos, para teclado e para leitores de ecrã em ecrã tátil — de uma só vez. *(2.5.1)*

**4. Arrastar e largar sem alternativa**
Reordenar listas, mover cartões, carregar ficheiros só por arrastar. O gesto mais exigente da interface, sem plano B. *(2.5.7)*

**5. Funcionalidade que só existe com `:hover`**
O menu que abre ao passar o rato, o botão «Editar» que só aparece quando se paira sobre o cartão, a informação que só está na dica. Num ecrã tátil, `:hover` não existe, ou existe de forma errática, com um primeiro toque a servir de «hover» e um segundo a ativar, o que confunde toda a gente. *(1.4.13; e a alternativa por teclado, na secção anterior)*

**6. Dicas de contexto que fogem do ponteiro**
A dica que desaparece assim que se tenta chegar lá com o rato para ler o resto ou copiar um número. Especialmente penoso com ampliação, em que percorrer a dica é a única forma de a ler toda. *(1.4.13)*

**7. Zoom desativado no `viewport`**
Continua a aparecer em código novo, quase sempre copiado de um modelo antigo. Verifique o `<meta name="viewport">` do seu projeto hoje.

**8. Alvos invisíveis que se sobrepõem**
Consequência de aplicar a Técnica 2 sem cuidado. A pessoa carrega visivelmente no ícone A e ativa o B, porque o alvo invisível do B está por cima. É pior do que o problema original, porque é indetetável a olho.

**9. Confiar na emulação de eventos de rato no toque**
`mousemove` em telemóveis funciona «às vezes», com atraso, de forma diferente em cada navegador. Widgets construídos sobre essa emulação partem-se em silêncio. *(Técnica 6)*

**10. Assumir que quem usa toque não usa leitor de ecrã**
É o pressuposto que produz mais gestos inacessíveis. Milhões de pessoas usam o telemóvel com VoiceOver ou TalkBack, e os gestos delas passam pelo leitor de ecrã antes de chegarem ao seu código.

**11. Cursor `pointer` num elemento que não é botão**
`cursor: pointer` num `<div>` é a promessa visual de um controlo sem nenhuma das obrigações. Prometer clique é assumir tudo o resto: função, nome, foco, teclado. 

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Ponteiro não é rato.** Dedo, caneta, apontador de cabeça, seguimento ocular — todos produzem um ponteiro, e nem todos com precisão ou com dois dedos.

2. **Um alvo em que se acerte.** 24×24 CSS é o mínimo, 44×44 é o objetivo. O `padding` é a solução mais barata do mundo. Espaçamento faz parte do alvo.

3. **Um gesto que a mão consiga fazer.** Nenhum gesto de trajetória ou de vários dedos pode ser o **único** caminho. Não se trata de proibir o gesto: trata-se de acrescentar o botão.

4. **Um erro que se possa corrigir.** A ação acontece ao largar, não ao carregar. É o comportamento nativo do `click`. Quase todos os incumprimentos deste requisito vêm de código que substituiu o `click` por outra coisa.

5. **Um conteúdo que não fuja.** Dicas e menus acionados pelo ponteiro têm de ser dispensáveis, percorríveis e persistentes.

6. **`:hover` não é uma interação, é um enfeite.** Se a funcionalidade só existe ao passar o rato, não existe no toque nem no teclado.

7. **Não confunda os planos.** Alvo grande, gesto simples e ativação cancelável não substituem função, nome e estado corretos. Um botão perfeitamente dimensionado que se declara `<div>` continua inacessível, apenas por outro motivo.

8. **O elemento nativo resolve isto quase todo, de graça.** Repare quantas técnicas desta secção se resumem a: use `<button>` e use `click`.

---

### Exercícios Práticos

#### Exercício 1 — Auditoria de alvos

Escolha uma página do seu projeto e abra as ferramentas de programador.

1. Meça a caixa de **dez** elementos interativos: ícones, ligações de rodapé, botões de fechar, caixas de verificação, controlos de paginação.
2. Marque cada um: falha o mínimo (< 24×24), cumpre o mínimo, cumpre o objetivo (≥ 44×44).
3. Para os que falham, escreva a correção concreta (valor de `padding`, alteração de `min-height`).
4. Verifique também o **espaçamento**: há dois alvos a menos de 24 píxeis um do outro?

*Discussão:* quantos dos que falham são ações destrutivas ou irreversíveis? Há aqui uma ordem de prioridade.

#### Exercício 2 — Caça ao gesto

Percorra a versão móvel do seu projeto e faça uma lista de **todos** os gestos que a interface entende: deslizar, arrastar, toque prolongado, pinça, toque duplo, abanar.

Para cada um, responda a três perguntas:
1. Qual é a alternativa de ponteiro único?
2. Essa alternativa está **visível**, ou está escondida atrás de um menu?
3. O que acontece a este gesto com o TalkBack ou o VoiceOver ligado?

#### Exercício 3 — Encontrar uma falha de cancelamento

Procure no código do seu projeto por `mousedown`, `pointerdown` e `touchstart`.

1. Para cada ocorrência, identifique o que acontece nesse momento.
2. Decida qual das quatro saídas do 2.5.2 se aplica: sem ação no `down`, aborto possível, `up` reverte, ou `down` essencial.
3. Se nenhuma se aplicar, reescreva com `click`.

*Verificação manual:* carregue no controlo, arraste o ponteiro para fora e largue. Se a ação aconteceu, falha.

#### Exercício 4 — Reparar uma dica de contexto

Pegue no exemplo mau da Técnica 7 e transforme-o num componente que cumpra o 1.4.13.

**Critérios de aceitação:**

- O Escape fecha a dica sem mexer o ponteiro.
- O ponteiro pode entrar na dica e permanecer lá sem que ela desapareça.
- A dica não desaparece sozinha por temporizador.
- A dica aparece também com o foco do teclado.
- Funciona num ecrã tátil.

*Extra:* teste com o zoom do navegador a 400%. A dica tapa o conteúdo que a pessoa estava a ler?

#### Exercício 5 — Do gesto ao botão

Escolha um componente do seu projeto que dependa de arrastar (ordenação de lista, deslizador, carregamento de ficheiros, mapa).

1. Desenhe a alternativa de ponteiro único. Que controlos acrescenta, onde ficam, como se chamam?
2. Escreva o nome acessível de cada um. (Cuidado com botões «Subir» repetidos numa lista de doze itens: subir *o quê*?)
3. Implemente, e teste **sem tocar** no gesto original.

#### Exercício 6 — Meia hora com o leitor de ecrã ligado

Ligue o VoiceOver (iOS) ou o TalkBack (Android) no seu telemóvel e use o seu projeto durante trinta minutos.

Registe: que gestos deixaram de funcionar; que controlos não encontrou; onde é que a sua «área de toque generosa» se revelou uma armadilha porque o leitor de ecrã lia dois elementos sobrepostos.

*Aviso:* vai ser frustrante. Essa frustração é o resultado do exercício.

#### Exercício 7 — Alvo invisível bem feito (desafio)

Implemente uma barra de ferramentas com cinco ícones de 16×16, com o desenho visual intacto, em que:

- Cada alvo tem pelo menos 44×44.
- Nenhum alvo se sobrepõe a outro.
- É possível demonstrar cada área de toque (por exemplo, com um `outline` temporário no pseudo-elemento).

*Verificação:* carregue exatamente entre dois ícones. Qual é ativado? Consegue justificar a resposta?

---

