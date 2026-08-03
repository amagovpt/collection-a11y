# Leitores de Multimédia

## Introdução

Até aqui, o módulo concentrou-se no *conteúdo* das alternativas ao multimédia: como escrever uma boa transcrição, como sincronizar legendas, como descrever informação visual ou integrar língua gestual. Mas há uma peça que junta tudo isto e a coloca ao alcance das pessoas: o **leitor de multimédia**.

O leitor é a interface com que a pessoa carrega em "reproduzir", sobe o volume, ativa as legendas ou salta para um determinado momento do vídeo. Por outras palavras, o conteúdo pode estar impecável, mas se os controlos do leitor não forem acessíveis, uma parte dos utilizadores fica sem forma de chegar a esse conteúdo.

> **Analogia — o comando da televisão**
>
> Imagine o melhor programa de televisão de sempre, com legendas perfeitas e audiodescrição de qualidade. Agora imagine que o comando tem os botões em branco (não se percebe o que faz cada um), alguns botões estão colados (não se conseguem premir) e outros são tão pequenos que falha sempre o alvo. O programa continua excelente, mas ninguém o consegue operar.
>
> Um leitor de multimédia é esse comando. Esta parte do módulo não é sobre o "programa" (o conteúdo), é sobre o **comando** e sobre garantir que **todos** o conseguem usar.

Convém deixar claro o âmbito desta parte, para não repetir o que é tratado noutras secções:

- **Está aqui:** os controlos do leitor — como são construídos, se funcionam com teclado, toque, rato e voz, se têm nomes claros, se anunciam o seu estado, se são visíveis e suficientemente grandes — e a **experiência de controlar as alternativas** (ligar/desligar legendas, mostrar a transcrição, controlar a audiodescrição, dimensionar a janela de língua gestual).
- **Não está aqui:** como *produzir* essas alternativas (ver as secções *Transcrições*, *Legendas*, *Descrição de Informação Visual* e *Língua Gestual*); como *escolher* que alternativa usar (ver *Escolher a Alternativa Certa*); e o controlo de reprodução automática de áudio e de movimento/flashes, que é tratado em *Multimédia e Animações*. 

### Como as Pessoas com Deficiência dependem de Leitores de Multimédia Acessíveis

Cada grupo de utilizadores opera o leitor de uma forma diferente. Perceber *como* ajuda a perceber *o que* é preciso garantir.

**Pessoas cegas (leitores de ecrã)**
Não veem os botões: dependem de o leitor de ecrã anunciar o que cada controlo é (o *nome*), que tipo de controlo é (a *função* — botão, deslizador…) e em que estado está (a *situação* — a reproduzir/em pausa, com som/sem som, legendas ligadas/desligadas). Navegam entre os controlos com a tecla `Tab` e ativam-nos com `Enter` ou barra de espaço. Um botão sem nome é anunciado como "botão", o equivalente a um botão em branco no comando.

**Pessoas com baixa visão**
Veem, mas precisam que os controlos tenham **contraste suficiente** para se distinguirem do fundo (sobretudo quando estão sobrepostos ao vídeo), que o **indicador de foco** seja claramente visível ao navegar por teclado, e que os controlos continuem a funcionar quando a página é ampliada. Controlos que só aparecem ao passar o rato por cima ("hover") desaparecem no momento em que a pessoa precisa deles.

**Pessoas com limitações motoras (utilizam só teclado ou dispositivos alternativos)**
Muitas não usam rato. Precisam de chegar a **todos** os controlos por teclado, sem ficarem presas ("bloqueio do teclado"), e de que os alvos sejam **suficientemente grandes** para serem selecionados. Precisam também de que nenhum controlo dependa de um gesto complexo (arrastar em trajetória, usar dois dedos) sem uma alternativa simples.

**Pessoas que usam controlo por voz**
Comandam a interface por fala ("clicar Reproduzir"). Para isto funcionar, o **nome visível** do controlo tem de coincidir com o nome que o software reconhece. Um botão que mostra "Reproduzir" mas cujo nome acessível é "botão 3" é impossível de acionar por voz.

**Pessoas surdas ou com perda auditiva**
Não têm dificuldade em operar o leitor, mas dependem de **encontrar e ativar facilmente** o controlo de legendas ou de aceder à transcrição/língua gestual. Se o botão de legendas estiver escondido, mal identificado ou desligado por omissão sem forma óbvia de o ligar, o conteúdo em áudio fica inacessível. 

**Pessoas com dificuldades cognitivas**
Beneficiam de controlos em número reduzido, claros, previsíveis e consistentes, com rótulos compreensíveis e ícones convencionais. Uma barra cheia de botões ambíguos aumenta a carga cognitiva e leva ao abandono.

### Requisitos de Acessibilidade para Leitores de Multimédia

Reunindo o que os vários grupos precisam, um leitor acessível tem de cumprir, no essencial:

1. **Ser operável por vários métodos de interação** — rato, teclado, toque e voz. Não basta funcionar com rato.
2. **Ter controlos com nome, função e estado expostos** — cada botão/deslizador identifica-se, diz o que é e comunica alterações de estado (ex.: passou de "Reproduzir" a "Pausar"). *(WCAG 4.1.2 Nome, Função, Valor — Nível A.)*
3. **Ser totalmente utilizável com teclado, sem bloqueios** — todos os controlos alcançáveis e acionáveis com teclado; o foco entra e sai do leitor livremente. *(WCAG 2.1.1 Teclado e 2.1.2 Sem Bloqueio do Teclado — Nível A.)*
4. **Ter o foco do teclado sempre visível** — sabe-se onde se está. *(WCAG 2.4.7 Foco Visível — Nível AA.)*
5. **Ter controlos fáceis de encontrar e com contraste suficiente** — os ícones e os limites dos controlos distinguem-se do fundo. *(WCAG 1.4.11 Contraste Não Textual — Nível AA.)*
6. **Ter alvos suficientemente grandes e não exigir gestos complexos** — cómodo no toque e no rato. *(WCAG 2.5.1 Gestos de Ponteiro — Nível A; 2.5.8 Tamanho do Alvo (Mínimo) — Nível AA, introduzido na WCAG 2.2.)*
7. **Ter o nome visível incluído no nome acessível** — para o controlo por voz. *(WCAG 2.5.3 Rótulo no Nome — Nível A.)*
8. **Oferecer controlo claro sobre as alternativas** — ativar/desativar legendas, mostrar a transcrição, controlar a audiodescrição e dimensionar/posicionar a janela de língua gestual.

Note-se ainda que o controlo de **áudio de reprodução automática** (silenciar/controlar volume quando o som arranca sozinho) obedece ao critério 1.4.2 (Controlo de Áudio) e é tratado na secção *Multimédia e Animações*. O que é responsabilidade do leitor é **disponibilizar** controlos de volume e silêncio acessíveis; *quando e como* o áudio pode arrancar sozinho é discutido nessa secção.

## Técnicas de Codificação

Há dois caminhos para construir um leitor: usar os controlos nativos do navegador ou construir controlos personalizados. Comecemos pelo mais robusto.

### 1. O ponto de partida: controlos nativos do HTML

Os elementos `<video>` e `<audio>` do HTML têm um atributo `controls`. Quando presente, o navegador desenha um conjunto de controlos que já vêm, em regra, operáveis por teclado e identificados para os leitores de ecrã pelo próprio sistema operativo.

```html
<video controls width="640"
       aria-label="Entrevista com a diretora do projeto">
  <source src="entrevista.mp4" type="video/mp4">
  <track kind="captions" src="entrevista-pt.vtt"
         srclang="pt" label="Português" default>
</video>
```

**O que funciona bem neste exemplo:**

- O atributo `controls` fornece reprodução/pausa, volume, barra de progresso e ecrã inteiro sem código adicional. Esses controlos já são, na maioria dos navegadores atuais, alcançáveis por teclado e anunciados por leitores de ecrã.
- Como existe um `<track kind="captions">`, o navegador acrescenta **automaticamente** um botão de legendas ao leitor. Ou seja: fornecer a faixa de legendas dá, de borla, o controlo para a ligar.
- O `aria-label` dá ao elemento de vídeo um nome, útil quando há vários vídeos na página.

**O que ainda assim é preciso ter em conta:**

- A aparência dos controlos nativos varia entre navegadores; se a identidade visual não for prioritária, esta é quase sempre a opção mais segura em acessibilidade.
- **Nunca remover `controls` sem oferecer uma alternativa acessível.** Um `<video autoplay>` sem `controls` e sem controlos personalizados deixa a pessoa sem qualquer forma de parar o vídeo.

### 2. Quando se constroem controlos personalizados

Muitas equipas optam por controlos próprios, por razões de design ou de funcionalidade. É legítimo, mas passa a ser da responsabilidade de quem desenvolve reconstruir toda a acessibilidade que os controlos nativos ofereciam. Vejamos os controlos mais importantes.

#### Botão reproduzir/pausar

Exemplo a evitar:

```html
<div class="botao-play" onclick="reproduzir()">▶</div>
```

**Porque está mal:** um `<div>` não recebe foco do teclado (não se lá chega com `Tab`), não tem função de botão (o leitor de ecrã não o anuncia como acionável), não tem nome (o carácter "▶" pode não ser anunciado, ou ser lido de forma estranha) e não comunica o estado (a reproduzir ou em pausa). É um botão do comando pintado, mas colado.

Exemplo recomendado:

```html
<button type="button" id="playPause" onclick="alternarReproducao()"
        aria-label="Reproduzir">
  <svg aria-hidden="true" focusable="false"><!-- ícone de play --></svg>
</button>
```

E, em JavaScript, quando a reprodução começa, o rótulo passa a refletir a próxima ação:

```js
botao.setAttribute("aria-label", aReproduzir ? "Pausar" : "Reproduzir");
```

**Porque funciona bem:** um `<button>` verdadeiro é focável e acionável com `Enter` e barra de espaço, sem esforço; o `aria-label` dá-lhe nome; o ícone é escondido da tecnologia de apoio com `aria-hidden="true"` e `focusable="false"` (para não ser um destino de tabulação nem ser lido). Ao atualizar o `aria-label`, o botão anuncia sempre a ação que executa — o padrão mais previsível para reproduzir/pausar.

#### Botão silenciar

Aqui, como há dois estados persistentes ("com som" e "sem som"), o padrão de alternância com `aria-pressed` funciona bem:

```html
<button type="button" id="silenciar" aria-pressed="false"
        aria-label="Silenciar">
  <svg aria-hidden="true" focusable="false"><!-- ícone --></svg>
</button>
```

Ao silenciar, atualiza-se `aria-pressed="true"`. **Porque funciona bem:** o leitor de ecrã anuncia "Silenciar, botão de alternância, ativado/desativado", deixando claro o estado atual — algo que um ícone sozinho nunca comunica a quem não o vê.

#### Deslizadores de volume e de progresso

Os deslizadores são o controlo mais falhado nos leitores personalizados. A boa notícia é que existe um elemento nativo que já é operável por teclado e anuncia o seu valor:

```html
<label for="volume">Volume</label>
<input type="range" id="volume" min="0" max="100" value="80">

<input type="range" id="progresso" min="0" max="100" value="0"
       aria-label="Barra de progresso"
       aria-valuetext="0 minutos de 5">
```

**Porque funciona bem:** o `<input type="range">` recebe foco, reage às setas do teclado e anuncia o valor sem código extra. Na barra de progresso, o `aria-valuetext` permite substituir o valor cru ("35%") por algo compreensível ("1 minuto e 45 segundos de 5 minutos"), que deve ser **atualizado dinamicamente** à medida que o vídeo avança.

Exemplo a evitar:

```html
<div class="barra" onclick="saltar(event)"></div>
```

**Porque está mal:** um `<div>` clicável só funciona com rato/toque. Não recebe foco, não reage ao teclado, não anuncia posição nem duração, e depende de calcular a posição do clique. Inutilizável para quem navega por teclado e para leitores de ecrã. Se, por razões de design, não for possível usar `<input type="range">`, é preciso reconstruir tudo à mão com `role="slider"`, `aria-valuemin`, `aria-valuemax`, `aria-valuenow`, `aria-valuetext` e suporte às setas, mas é bastante mais trabalhoso e propenso a erros. Na dúvida, prefira o elemento nativo.

#### Agrupar os controlos

Convém agrupar os controlos e dar-lhes um nome de conjunto, para que a tecnologia de apoio os apresente como um bloco coerente:

```html
<div role="group" aria-label="Controlos de reprodução">
  <!-- botões e deslizadores -->
</div>
```

### 3. Os controlos das alternativas

Uma parte central desta secção é a **experiência de controlar as alternativas** — o que distingue um leitor "que reproduz" de um leitor "acessível". 

**Legendas** — botão de alternância, com o estado exposto:

```html
<button type="button" id="legendas" aria-pressed="false">
  Legendas
</button>
```

Quando há várias faixas (ex.: legendas em português e legendas descritivas), um menu para as escolher deve ser navegável por teclado e cada opção deve indicar qual está ativa.

**Transcrição** — muitas vezes é um bloco de texto que se expande/recolhe. Use um botão que comunique se está aberto ou fechado:

```html
<button type="button" aria-expanded="false" aria-controls="transcricao">
  Mostrar transcrição
</button>
<div id="transcricao" hidden>…</div>
```

**Porque funciona bem:** `aria-expanded` diz à pessoa se a transcrição está visível ou não; `aria-controls` liga o botão ao bloco; e usar o atributo `hidden` (em vez de esconder só visualmente) garante que o texto oculto não é lido antes do tempo.

**Audiodescrição** — quando existe uma faixa de descrição em áudio, o leitor deve oferecer um controlo claro para a ativar/desativar (à semelhança do botão de legendas). 

**Língua gestual** — quando a interpretação em língua gestual é apresentada numa janela sobre o vídeo, o leitor deve permitir **redimensionar e reposicionar** essa janela, para que quem depende dela a possa ver com conforto sem tapar informação relevante. Esses controlos seguem as mesmas regras dos restantes (teclado, nome, contraste, tamanho).

#### Ecrã inteiro

O botão de ecrã inteiro deve ter nome ("Ecrã inteiro"), ser operável por teclado, e, ponto crítico, **o modo de ecrã inteiro não pode quebrar a navegação por teclado nem prender o foco** (evitar o bloqueio do teclado). Deve ser sempre possível sair com a tecla `Esc`.

## Recomendações para Conteúdo Acessível

- **Prefira os controlos nativos** (`<video controls>` / `<audio controls>`) sempre que o design o permitir; só construa controlos personalizados quando houver uma razão real, sabendo que passa a ser responsável por reconstruir a acessibilidade.
- **Use elementos verdadeiros:** `<button>` para botões, `<input type="range">` para deslizadores. Evite `<div>`/`<span>` com `onclick` para funções interativas.
- **Dê nome a todos os controlos** e faça com que o **nome visível esteja contido no nome acessível**, para o controlo por voz funcionar (ex.: se mostra "Legendas", o nome acessível não deve ser "CC toggle").
- **Comunique o estado**, não só a ação: reproduzir/pausar, com som/sem som, legendas ligadas/desligadas, transcrição aberta/fechada.
- **Torne o foco visível.** Nunca remova o contorno de foco (`outline: none`) sem oferecer um indicador visível alternativo, com bom contraste.
- **Garanta contraste suficiente dos controlos.** Quando estiverem sobrepostos ao vídeo, use um fundo/sombra para os ícones não se perderem em cenas claras ou escuras.
- **Torne os alvos confortáveis** (recomenda-se pelo menos 24×24 px como mínimo, com folga adequada) e **não dependa de gestos complexos**: a barra de progresso deve poder ser operada com toques/cliques simples e com o teclado, não só arrastando.
- **Não esconda os controlos só no "hover".** Se aparecem ao passar o rato, têm também de aparecer ao receber foco de teclado e de estar disponíveis no toque.
- **Torne o controlo de legendas fácil de encontrar** e não dependa apenas de cor ou ícone: acompanhe com texto ou rótulo.
- **Mantenha uma ordem de foco lógica** entre os controlos (ex.: reproduzir → progresso → volume → legendas → ecrã inteiro).
- **Não confie na aparência por omissão em todos os contextos:** teste com teclado, com um leitor de ecrã e com a página ampliada a 200%.

## Erros Comuns

- **Botões feitos de `<div>`/`<span>`** — não recebem foco nem função; invisíveis para quem usa teclado e leitor de ecrã.
- **Botões só com ícone e sem nome acessível** — anunciados apenas como "botão"; o utilizador não sabe o que fazem.
- **Botões de alternância que não comunicam o estado** — não se percebe se as legendas ou o som estão ligados.
- **Barra de progresso e volume construídas com `<div>` clicáveis** — não funcionam por teclado nem anunciam valor/duração.
- **Remover o indicador de foco** (`outline: none`) sem substituto — quem navega por teclado deixa de saber onde está.
- **Controlos que só surgem no "hover"** — desaparecem para quem usa teclado ou toque.
- **Nome visível diferente do nome acessível** — impede o controlo por voz de acionar o botão.
- **Alvos minúsculos e colados** — falhas constantes no toque e para quem tem menor precisão motora.
- **Modo de ecrã inteiro que prende o foco** ou impede a saída por teclado — bloqueio do teclado.
- **Remover `controls` do vídeo nativo sem oferecer alternativa** — deixa a pessoa sem forma de operar o conteúdo.
- **Confundir "ter faixa de legendas" com "ter controlo de legendas"** — é preciso um botão claro para as ligar, não só o ficheiro.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- O leitor de multimédia é o **comando** através do qual as pessoas operam o conteúdo; se os controlos não forem acessíveis, o conteúdo, por melhor que seja, fica fora de alcance.
- Um leitor acessível suporta **vários métodos de interação** (rato, teclado, toque e voz), e os seus controlos têm **nome, função e estado** expostos.
- Os **controlos nativos** do HTML (`<video controls>`) são o ponto de partida mais seguro; um `<track>` de legendas faz o navegador acrescentar automaticamente o botão respetivo.
- Em **controlos personalizados**, usar elementos verdadeiros (`<button>`, `<input type="range">`), atualizar rótulos e estados (`aria-pressed`, `aria-expanded`, `aria-valuetext`), agrupar controlos e garantir foco visível.
- O leitor deve oferecer controlo claro sobre as **alternativas**: ligar/desligar legendas, mostrar a transcrição, controlar a audiodescrição e dimensionar/posicionar a janela de língua gestual.
- Critérios WCAG mais relevantes para o leitor: **2.1.1**, **2.1.2**, **2.5.1**, **2.5.3** e **4.1.2** (Nível A) e **1.4.11**, **2.4.7** e **2.5.8** (Nível AA). O controlo de áudio automático (**1.4.2**) é tratado em *Multimédia e Animações*.

### Exercícios Práticos

1. **Auditoria só com teclado.** Escolha um leitor de vídeo de um site à sua escolha. Guarde o rato de lado e tente, apenas com `Tab`, `Enter`, barra de espaço e setas: reproduzir, pausar, mudar o volume, saltar para o meio do vídeo, ligar as legendas e entrar/sair de ecrã inteiro. Registe o que falhou e a que critério WCAG corresponde cada falha.

2. **Auditoria com leitor de ecrã.** Com um leitor de ecrã (ex.: NVDA, VoiceOver), percorra os controlos do mesmo leitor. Cada controlo é anunciado com um nome claro? Os botões de alternância anunciam o estado (com som/sem som, legendas ligadas/desligadas)? Anote os controlos que são apenas "botão".

3. **Corrigir um botão.** Parta deste controlo defeituoso e reescreva-o de forma acessível, justificando cada alteração:
   ```html
   <div class="cc" onclick="ligarLegendas()">CC</div>
   ```

4. **Deslizador acessível.** Substitua uma barra de progresso feita com `<div>` clicável por uma solução operável por teclado, garantindo que anuncia o tempo decorrido e a duração total de forma compreensível.

5. **Controlo por voz.** Encontre um botão de um leitor em que o nome visível não coincida com o nome acessível. Explique porque é que uma pessoa que usa controlo por voz não o consegue acionar e proponha a correção (relacione com o critério *Rótulo no Nome*).
