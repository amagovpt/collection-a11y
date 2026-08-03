# Multimédia e Animações

## Introdução

Quando falamos de **conteúdo multimédia**, referimo-nos a tudo aquilo que uma página comunica através do som e do movimento: um ficheiro de **áudio** (um *podcast*, uma entrevista), um **vídeo** (uma aula gravada, um anúncio institucional), ou uma **animação** (um carrossel de imagens, um gráfico que se desenha sozinho, um GIF, um fundo em movimento).

Este conteúdo é poderoso porque comunica muito num curto espaço de tempo. Mas essa mesma riqueza é também a sua fragilidade: se toda a informação estiver "presa" dentro do som ou da imagem em movimento, quem não consegue ouvir, ver ou processar esse movimento fica de fora.

As soluções detalhadas para *cada* barreira — transcrições, legendas, descrição de informação visual, língua gestual e leitores de multimédia — têm secções próprias mais à frente. Aqui só as vamos apresentar, para que se perceba o mapa completo antes de descermos aos pormenores.

> **Analogia — o edifício com várias entradas**
> Imagine um edifício público com uma porta giratória, uma rampa e um elevador. Nenhuma destas entradas é "a alternativa"; são simplesmente formas diferentes de chegar ao mesmo sítio. Uma pessoa em cadeira de rodas usa a rampa, outra com uma mala usa o elevador, outra entra pela porta giratória. O conteúdo multimédia acessível funciona da mesma maneira: **a mesma informação tem de ter mais do que uma porta de acesso**. A transcrição, as legendas ou a descrição áudio não são "versões para deficientes" — são entradas alternativas para o mesmo edifício.

### Como as Pessoas com Deficiência acedem a Conteúdo Multimédia

Cada tipo de deficiência cria uma barreira diferente, e por isso depende de uma "porta" diferente. Não é preciso decorar esta lista, basta perceber a lógica: **quando um sentido não está disponível, a informação tem de existir também de outra forma.**

- **Pessoas surdas ou com dificuldades auditivas** não recebem a parte sonora. Precisam da informação do som apresentada em texto (legendas, transcrição) ou em **língua gestual**. Para uma pessoa surda de nascença, a língua gestual pode até ser a sua língua materna, e um texto escrito ser uma segunda língua.
- **Pessoas cegas ou com baixa visão** não recebem a parte visual. Precisam de saber, através do som ou de texto lido por um leitor de ecrã, aquilo que acontece na imagem e que não é dito em voz alta (por exemplo, "*a personagem aponta para a saída*").
- **Pessoas surdocegas** não recebem nem o som nem a imagem. A porta mais universal para elas é uma **transcrição em texto**, que pode ser lida numa linha braille.
- **Pessoas com deficiência cognitiva ou de aprendizagem** podem receber o som e a imagem, mas ter dificuldade em acompanhar conteúdo rápido, sem controlo ou com muitos estímulos ao mesmo tempo. Precisam de poder **parar, retroceder e reler** ao seu ritmo.
- **Pessoas com epilepsia fotossensível** podem ser prejudicadas pelo próprio conteúdo: um vídeo ou animação que pisca com força pode desencadear uma **crise convulsiva**. Aqui o objetivo não é dar uma alternativa — é **não causar dano**.
- **Pessoas com perturbações vestibulares** (que afetam o equilíbrio) podem sentir tonturas, náuseas ou desorientação com movimento no ecrã, sobretudo animações grandes, com efeito de profundidade ou de "voo". Precisam de poder **reduzir ou desligar o movimento**.
- **Pessoas com deficiência motora** podem não usar rato. Precisam de controlar a reprodução (pausa, avanço, volume) apenas com o teclado ou com tecnologia de apoio.

Repare numa distinção importante que vai orientar todo o módulo: há barreiras que se resolvem **acrescentando** informação (uma legenda, uma descrição, uma transcrição) e há barreiras que se resolvem **removendo** ou **controlando** o que causa dano (o piscar, o movimento, o som automático). 

### Requisitos de Acessibilidade para Conteúdo Multimédia

Podemos resumir tudo em três exigências simples. Um conteúdo multimédia é acessível quando a pessoa consegue:

1. **Perceber** — toda a informação transmitida pelo som existe também em texto/visual, e toda a informação transmitida pela imagem existe também em som/texto. É aqui que entram as alternativas (transcrições, legendas, descrição de informação visual, língua gestual), cada uma com a sua secção.
2. **Controlar** — a pessoa manda no conteúdo, e não o contrário. Consegue iniciar, parar, pausar e ajustar o volume, com teclado ou rato. O detalhe dos controlos do reprodutor está na secção *Leitores de Multimédia*.
3. **Não ser prejudicada** — o conteúdo nunca pisca de forma perigosa nem impõe movimento que a pessoa não pediu nem pode desligar.

Nesta secção tratamos sobretudo dos pontos **2** e **3** na sua forma mais essencial, aplicada às **animações e ao arranque automático de conteúdo**. Os pontos ligados a *alternativas* (o ponto 1) são apresentados aqui apenas como mapa e desenvolvidos nas secções seguintes.

> **Nota sobre "animação"**
> Ao longo desta secção, "animação" é um termo amplo: inclui carrosséis/*sliders* que avançam sozinhos, GIFs, texto ou notícias em movimento (*tickers*), fundos em vídeo, efeitos ao passar o rato ou ao deslocar a página (*scroll*), ícones que rodam, e vídeos que arrancam automaticamente. Todos têm em comum uma coisa: **movimento no ecrã**.

---

## Técnicas de Codificação

Esta secção mostra, com código, como tratar as três situações que são específicas desta secção: **movimento que a pessoa deve poder parar**, **conteúdo que arranca sozinho** e **respeitar a preferência de movimento reduzido**. (A codificação das legendas, das transcrições, etc., pertence às respetivas secções.)

### 1. Respeitar a preferência de "movimento reduzido"

Os sistemas operativos modernos permitem que a pessoa peça, nas definições de acessibilidade, para **reduzir o movimento** das interfaces. O navegador transmite esse pedido às páginas através de uma *media query* de CSS chamada `prefers-reduced-motion`. Basta ouvi-la.

**Exemplo — animação que respeita a preferência do utilizador**

```css
/* Comportamento normal: o cartão cresce suavemente ao passar o rato */
.cartao {
  transition: transform 0.4s ease;
}
.cartao:hover {
  transform: scale(1.08);
}

/* Se a pessoa pediu menos movimento, desligamos a animação */
@media (prefers-reduced-motion: reduce) {
  .cartao {
    transition: none;
  }
  .cartao:hover {
    transform: none;
  }
}
```

**O que funciona bem:** a animação continua a existir para quem gosta dela, mas desaparece de forma limpa para quem indicou que o movimento lhe faz mal. Ninguém tem de procurar um botão escondido nem instalar nada. A página simplesmente respeita uma preferência que a pessoa já tinha configurado no seu sistema. É a diferença entre um restaurante que *tem* uma sala calma e um que obriga toda a gente a sentar-se ao pé da coluna de som.

**Contraexemplo — a mesma animação, sem respeitar a preferência**

```css
.cartao {
  transition: transform 0.4s ease;
}
.cartao:hover {
  transform: scale(1.08);
}
/* (não há qualquer bloco prefers-reduced-motion) */
```

**O que funciona mal:** para a maioria das pessoas, o resultado é idêntico e parece perfeito. O problema é invisível para quem programou: uma pessoa com perturbação vestibular que configurou "reduzir movimento" no sistema continua a receber todo o movimento. O código "funciona", mas ignora um pedido explícito do utilizador.

Quando a animação é feita em JavaScript, o mesmo pedido pode ser lido com `matchMedia`:

```js
const querMenosMovimento =
  window.matchMedia('(prefers-reduced-motion: reduce)').matches;

if (!querMenosMovimento) {
  iniciarAnimacaoDecorativa();
}
```

### 2. Dar controlo sobre movimento que arranca sozinho

Sempre que algo **começa a mexer-se sozinho**, dura mais do que uns segundos e aparece **ao lado de outro conteúdo** (por exemplo, um carrossel por cima de um texto que a pessoa está a tentar ler), tem de existir uma forma clara de **pausar, parar ou esconder** esse movimento. Este é o requisito do critério **2.2.2 — Pausar, Parar, Ocultar** das WCAG.

**Exemplo — carrossel com botão de pausa**

```html
<section class="carrossel" aria-label="Destaques">
  <button type="button" class="carrossel__pausa" aria-pressed="false">
    Pausar destaques
  </button>
  <!-- ... imagens/slides do carrossel ... -->
</section>
```

```js
const botao = document.querySelector('.carrossel__pausa');

botao.addEventListener('click', () => {
  const estaEmPausa = botao.getAttribute('aria-pressed') === 'true';
  if (estaEmPausa) {
    retomarCarrossel();
    botao.setAttribute('aria-pressed', 'false');
    botao.textContent = 'Pausar destaques';
  } else {
    pararCarrossel();
    botao.setAttribute('aria-pressed', 'true');
    botao.textContent = 'Retomar destaques';
  }
});
```

**O que funciona bem:** o botão é um `<button>` verdadeiro, por isso já funciona com teclado e é anunciado por um leitor de ecrã. O atributo `aria-pressed` comunica o estado atual (a mexer / em pausa), e o texto visível muda em conformidade. Uma pessoa que lê devagar consegue parar o carrossel e ler com calma, em vez de perseguir um alvo que muda de dois em dois segundos.

**Contraexemplo — GIF animado sem qualquer controlo**

```html
<img src="promocao.gif" alt="Promoção de verão">
```

**O que funciona mal:** um GIF anima em ciclo infinito e **não tem controlos** — não é possível pausá-lo. Se durar mais de cinco segundos ao lado de outro conteúdo, falha o critério 2.2.2. Além disso, se as suas cores mudarem depressa e com muito contraste, pode até tornar-se perigoso (ver ponto 4). A solução costuma ser substituir o GIF por um `<video>` com controlos, ou por uma imagem estática, ou garantir que a animação pára sozinha em poucos segundos.

### 3. Áudio que arranca sozinho

Se um som começa a tocar automaticamente e dura mais do que uns segundos, tem de existir uma forma de o **parar ou baixar o volume** (de preferência sem obrigar a pessoa a baixar o volume de todo o sistema). Isto corresponde ao critério **1.4.2 — Controlo de Áudio**.

Há aqui uma razão de acessibilidade que passa despercebida a quem ouve: uma pessoa cega usa um **leitor de ecrã**, que é *também* uma voz. Se a página começa a falar ou a tocar música por cima, as duas vozes sobrepõem-se e a pessoa deixa de conseguir navegar. É como tentar ouvir alguém ao telefone enquanto uma televisão grita ao lado.

**Recomendação prática:** evite arranque automático de som. Se for mesmo necessário (raro), o vídeo deve arrancar **sem som** e a decisão de ativar o áudio deve ser da pessoa:

```html
<video src="apresentacao.mp4" autoplay muted playsinline
       controls aria-label="Apresentação da instituição">
</video>
```

**O que funciona bem:** o `muted` garante que nada "grita" quando a página abre; o `controls` devolve o comando à pessoa. **O que ainda pode correr mal:** movimento sem som continua a ser movimento — para quem tem sensibilidade vestibular, um fundo em vídeo a rodar em ciclo pode ser desconfortável mesmo estando silencioso. Por isso este ponto anda quase sempre de mãos dadas com o ponto 1 (`prefers-reduced-motion`).

### 4. Não ultrapassar os limites de piscar

Conteúdo que pisca com muita intensidade pode desencadear crises em pessoas com epilepsia fotossensível. A regra prática, definida no critério **2.3.1 — Três Flashes ou Abaixo do Limite**, é simples de recordar: **nada deve piscar mais do que três vezes por segundo**.

Não há um "código bom" a mostrar aqui. A melhor técnica é **preventiva**:

- não usar animações que alternam rapidamente entre cores muito contrastantes, sobretudo com vermelho saturado;
- se um efeito de "flash" for mesmo desejado, mantê-lo lento e suave (bem abaixo de três vezes por segundo);
- testar qualquer animação intensa com uma ferramenta de análise de flashes antes de a publicar.

**Por que isto é diferente de tudo o resto nesta secção:** as legendas ou as transcrições são *ajudas* — a sua ausência exclui alguém. O piscar perigoso é o contrário: a sua *presença* pode fazer mal fisicamente a alguém. Por isso, aqui, não há alternativa nem preferência a respeitar — é uma linha que simplesmente não se ultrapassa.

---

## Recomendações para Conteúdo Acessível

Reunindo as técnicas anteriores em orientações práticas para o dia a dia:

- **Trate o movimento como opcional por defeito.** Comece por perguntar se a animação é mesmo necessária. Se for apenas decorativa, considere torná-la subtil e curta, e desligue-a sempre que a pessoa peça movimento reduzido.
- **Nada de arranque automático que a pessoa não possa travar.** Se algo se move ou toca sozinho durante mais de uns segundos, dê sempre um controlo visível e acessível por teclado para pausar, parar ou esconder.
- **Silêncio por defeito.** Evite som automático. Se usar vídeo de fundo, arranque-o sem som e deixe a pessoa decidir se quer ouvir.
- **Fique bem abaixo do limite de piscar.** Nunca ultrapasse três flashes por segundo e desconfie de qualquer efeito rápido com cores muito contrastantes.
- **Prefira formatos com controlos a formatos sem controlos.** Um `<video>` (que pode ser pausado) é quase sempre melhor do que um GIF (que não pode).
- **Não dependa só do movimento para dar uma informação.** Se uma seta a piscar for a única forma de indicar "clique aqui", quem não perceba o movimento (ou o tenha desligado) perde a mensagem. Reforce sempre com texto ou com uma indicação estável.
- **Teste como um utilizador real.** Ative "reduzir movimento" no seu sistema, tente usar a página só com o teclado e desligue o som. O que sobra é o que muitas pessoas recebem todos os dias.

### Erros Comuns

- **Confiar no GIF para tudo.** É cómodo, mas anima em ciclo infinito, não se pausa e é difícil de controlar. É a origem de muitas falhas de 2.2.2.
- **Achar que "sem som" é o mesmo que "sem problemas".** Silenciar um vídeo resolve o áudio, mas não resolve o desconforto do movimento para quem tem sensibilidade vestibular.
- **Programar a animação e esquecer o bloco `prefers-reduced-motion`.** Como o problema é invisível para quem não configurou a preferência, passa quase sempre despercebido em testes rápidos.
- **Esconder o botão de pausa atrás do rato.** Se o controlo só aparece ao passar o cursor por cima (`:hover`), fica inacessível para quem usa teclado ou toque. O controlo tem de estar sempre disponível.
- **Usar movimento como única pista.** Depender de algo a piscar ou a saltar para chamar a atenção deixa de fora quem não percebe esse movimento.
- **Testar apenas "com os olhos e ouvidos ligados".** Se nunca desligar o som, nunca ativar movimento reduzido e nunca largar o rato, os problemas mais graves ficam sistematicamente invisíveis.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Conteúdo multimédia é tudo o que comunica por **som e movimento**: áudio, vídeo e animações. A sua força — transmitir muita informação muito depressa — é também a sua barreira.
- A regra geral é: **quando um sentido não está disponível, a mesma informação tem de existir de outra forma.** As alternativas concretas (transcrições, legendas, descrição de informação visual, língua gestual, leitores) têm secções próprias.
- Um conteúdo multimédia acessível cumpre três condições: deixa **perceber**, deixa **controlar** e **não prejudica**.
- As **animações**, ou movimento não pedido, podem ser desde apenas incómodo até causar tonturas ou, no caso do piscar intenso, uma crise convulsiva.
- Três reflexos práticos a levar desta secção: respeitar `prefers-reduced-motion`, dar sempre um controlo para pausar movimento e som automáticos, e nunca ultrapassar **três flashes por segundo**.

### Exercícios Práticos

1. **Caça ao movimento.** Escolha uma página de uma instituição pública e faça o inventário de todo o movimento: carrosséis, GIFs, vídeos de fundo, efeitos ao deslocar a página. Para cada um, responda: arranca sozinho? Dura mais de cinco segundos? Existe forma de o parar?

2. **Ativar a preferência.** Nas definições de acessibilidade do seu sistema operativo, ative "reduzir movimento". Volte à mesma página e anote o que mudou (ou não mudou). O que continua a mexer-se está, muito provavelmente, a ignorar o pedido do utilizador.

3. **Do GIF ao vídeo.** Pegue num GIF animado de uma página real e descreva, por palavras, como o converteria numa alternativa acessível: que formato usaria, que controlos acrescentaria e em que situação a versão estática seria suficiente.

4. **Detetar o perigo.** Imagine que um colega propõe um banner de destaque que alterna entre vermelho e branco cinco vezes por segundo para "chamar a atenção". Explique-lhe, em linguagem simples, por que é que isto não pode ser publicado e proponha uma alternativa que chame a atenção sem risco.

5. **Reescrever com controlo.** Dado o exemplo do GIF sem controlos apresentado nesta secção, escreva a marcação de uma alternativa em `<video>` com controlos e uma etiqueta acessível, e explique numa frase o que melhorou para o utilizador.
