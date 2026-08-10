---
title: Regiões Dinâmicas
layout: default
nav_order: 6
---
# Regiões Dinâmicas

## Introdução

Imagine que está numa estação de comboios. Olha para o painel de partidas e vê que o seu comboio parte da linha 3. Vai comprar um café e, entretanto, o painel muda: o comboio passou para a linha 7. Se ninguém anunciar essa alteração pelo altifalante, quem não estiver a olhar para o painel perde o comboio.

Nas páginas web acontece exactamente o mesmo. Muitas coisas mudam **sem que a página seja recarregada** e **sem que o foco se mova**:

- uma mensagem de erro que aparece por baixo de um campo de formulário;
- o contador do carrinho de compras que passa de "2 artigos" para "3 artigos";
- uma lista de resultados que encolhe à medida que escrevemos numa caixa de pesquisa;
- uma notificação que surge a dizer "Alterações guardadas" e desaparece três segundos depois;
- uma nova mensagem que chega numa conversa de apoio ao cliente.

Para quem vê o ecrã inteiro, estas mudanças são evidentes: o olho é atraído pelo movimento e pela cor. Para quem não vê o ecrã, ou vê apenas uma pequena parte dele, estas mudanças são **silenciosas e invisíveis**.

Uma **região dinâmica** (em inglês, *live region*) é a forma de dizer ao navegador e às tecnologias de apoio: *"esta zona da página pode mudar sozinha; quando mudar, avisa a pessoa"*. É o altifalante da estação.

> **Analogia central desta secção:** a região dinâmica é o **altifalante da estação de comboios**. O painel (o ecrã) mostra a informação a quem olha; o altifalante (a região dinâmica) leva a informação a quem não está a olhar. E, tal como numa estação, o altifalante deve ser usado com critério: se anunciar tudo o que se passa, ninguém percebe nada.

**Âmbito desta secção.** Aqui tratamos apenas de **como comunicar alterações que acontecem longe do foco**. A regra de fronteira é simples: **se a pessoa provocou a mudança e o foco deve ir para o novo conteúdo, o assunto é foco. Se a mudança tem de ser comunicada sem mexer no foco, o assunto é região dinâmica.**

---

### Como as Pessoas com Deficiência dependem de Regiões Dinâmicas

Nem todas as pessoas dependem das regiões dinâmicas da mesma maneira. Vale a pena perceber quem precisa de quê.

#### Pessoas cegas que usam leitores de ecrã

O leitor de ecrã não "vê" a página: constrói uma representação da página e lê-a por ordem, ponto a ponto, onde a pessoa está a navegar. É como ler um livro com uma lanterna numa sala escura: só existe o que está no feixe de luz.

Se uma mensagem aparecer noutro ponto da página, fora do feixe, a pessoa **não fica a saber**. Só descobrirá se, por acaso, voltar atrás e reler a página inteira. A região dinâmica é o que faz com que o leitor de ecrã interrompa (ou complemente) a leitura para dizer: *"Alterações guardadas"*.

#### Pessoas com baixa visão que usam ampliação de ecrã

Com uma ampliação de 400%, a pessoa vê talvez um sexto do ecrã de cada vez. Está concentrada no campo "Código postal", em baixo, e a mensagem de erro aparece no topo da página, dentro de uma caixa vermelha bem visível, mas para quem vê o ecrã todo. Para quem está ampliado, aquela caixa está tão longe como se estivesse noutro separador.

Muitas destas pessoas usam também leitor de ecrã ou saída de voz; para elas, a região dinâmica resolve o problema. Para as restantes, a solução é sobretudo de **desenho**: colocar a mensagem **junto** ao ponto onde a acção acontece.

#### Pessoas com deficiência motora

Quem navega apenas por teclado, por manípulos (*switches*) ou por varrimento move-se devagar. Se uma notificação aparece e desaparece em 3 segundos, ou se um resultado importante surge a 40 tabulações de distância, a informação existe mas é inalcançável na prática.

#### Pessoas com deficiências cognitivas ou de atenção

Estas pessoas beneficiam de mensagens claras e previsíveis, mas são também as mais prejudicadas pelo **excesso** de anúncios. Uma página que anuncia cada tecla premida, cada resultado parcial e cada mudança de contador transforma-se em ruído. Aqui, mais anúncios significa menos acessibilidade.

#### Pessoas surdocegas com linha braille

A informação chega em texto, célula a célula. Anúncios longos, repetidos ou interrompidos a meio são particularmente penalizadores: obrigam a "reler" fisicamente com os dedos.

**Conclusão prática:** a região dinâmica não é um extra para leitores de ecrã. É a versão em texto de um sinal que, no ecrã, é dado por cor, movimento e posição. Sem ela, essa informação simplesmente **não existe** para uma parte dos utilizadores.

---

### Requisitos de Acessibilidade para Regiões Dinâmicas

Para que uma alteração dinâmica seja acessível, tem de cumprir seis requisitos. Pense neles como uma lista de verificação mental.

**1. A mudança tem de ser percetível sem mover o foco.**
A pessoa está a preencher o campo "Telefone"; o contador de caracteres actualiza-se. Ninguém pode ser atirado para outro sítio da página só para saber isso. A informação vai ter com a pessoa; a pessoa não vai ter com a informação.

**2. A informação tem de existir em texto.**
Um círculo que muda de cor, um ícone que aparece, uma barra que enche, nada disto é informação para quem não vê. Tem de haver texto associado, mesmo que seja texto visualmente escondido para quem vê.

**3. O nível de urgência tem de ser adequado.**
Há mensagens que podem esperar que a pessoa acabe a frase ("3 resultados encontrados") e há mensagens que não podem esperar ("A sua sessão termina em 30 segundos"). Interromper sempre é tão mau como nunca interromper.

**4. A região tem de existir *antes* de a mudança acontecer.**
Este é o erro técnico mais frequente e o mais difícil de detectar. Explicamos porquê mais à frente, mas fixe a ideia: **o altifalante tem de estar instalado antes do anúncio**. Não se instala o altifalante ao mesmo tempo que se fala.

**5. A mensagem tem de ser compreensível isoladamente.**
O anúncio chega sem contexto visual. "Erro" não chega. "Erro: o NIF tem de ter 9 dígitos" chega.

**6. A quantidade tem de ser gerível.**
Anunciar tudo é equivalente a não anunciar nada. Cada anúncio compete com os outros e com o que a pessoa está a fazer.

Em termos normativos, o critério WCAG mais directamente ligado a esta secção é o **4.1.3 Mensagens de Estado (Nível AA)**: mensagens de estado que informam sobre o sucesso, o resultado ou o progresso de uma acção têm de poder ser determinadas por tecnologias de apoio **sem receberem foco**. Mensagens de erro em formulários envolvem também o **3.3.1 Identificação de Erro (Nível A)**, e notificações que desaparecem sozinhas tocam no **2.2.1 Ajuste do Tempo (Nível A)**. A lista completa e consolidada dos critérios aplicáveis a todo o módulo encontra-se na secção final, *Conclusão e Boas Práticas*.

---

## Técnicas de Codificação

### A ferramenta base: `aria-live`

O atributo `aria-live` marca um elemento como região dinâmica. Aceita três valores:

| Valor | Comportamento | Quando usar |
|---|---|---|
| `off` | Não anuncia. É o valor por omissão de qualquer elemento. | Para desligar temporariamente uma região. |
| `polite` | Espera que a pessoa faça uma pausa e só depois anuncia. | **Quase sempre.** Confirmações, resultados, contadores, estados. |
| `assertive` | Interrompe imediatamente o que estiver a ser lido. | Raramente. Só quando não agir tem consequências. |

**Analogia:** `polite` é o colega que espera que acabe a chamada para lhe dar o recado. `assertive` é o colega que lhe arranca o telefone da mão. Há situações para o segundo — um incêndio, por exemplo — mas são poucas.

#### Exemplo 1 — Confirmação após guardar

```html
<!-- Existe no HTML desde o início, vazio -->
<div id="estado" role="status" aria-live="polite"></div>

<button type="button" id="guardar">Guardar rascunho</button>
```

```js
document.getElementById('guardar').addEventListener('click', async () => {
  const ok = await guardarRascunho();
  document.getElementById('estado').textContent =
    ok ? 'Rascunho guardado às 14:32.' : 'Não foi possível guardar. Tente novamente.';
});
```

**O que funciona bem neste exemplo:**

- O contentor existe no HTML **desde o carregamento da página** e está vazio. O altifalante estava instalado antes do anúncio.
- Só o **texto** é inserido depois. A mudança de conteúdo é o que dispara o anúncio.
- Usa `polite`: guardar um rascunho não é uma emergência.
- A mensagem é útil sozinha: inclui a hora, o que dá confiança a quem não vê o ecrã.
- Quem vê o ecrã vê a mesma frase, no mesmo sítio. Não há duas realidades diferentes.

#### Exemplo 2 — O mesmo caso, mal feito

```html
<button type="button" id="guardar">Guardar rascunho</button>
<div id="zona"></div>
```

```js
document.getElementById('guardar').addEventListener('click', async () => {
  const ok = await guardarRascunho();
  document.getElementById('zona').innerHTML =
    '<div role="status" aria-live="polite">✔</div>';
});
```

**O que corre mal neste exemplo:**

- A região dinâmica é **criada no mesmo instante** em que recebe conteúdo. O navegador só passa a vigiar a região depois de ela existir; quando começa a vigiar, o conteúdo já lá estava. Resultado típico: **nada é anunciado**. E, pior, o comportamento varia entre navegadores e leitores de ecrã. Pode funcionar na máquina de quem programou e falhar na do utilizador.
- O conteúdo é um "✔". Um leitor de ecrã pode ler "marca de verificação", pode ler "sinal", ou pode não ler nada. Não é uma mensagem, é um símbolo.
- Não há qualquer tratamento do caso de erro.

**Correcção:** manter o `<div id="estado" role="status" aria-live="polite"></div>` fixo no HTML e escrever apenas texto lá dentro, como no Exemplo 1.

---

### Os atalhos: `role="status"` e `role="alert"`

Escrever `aria-live` à mão funciona, mas existem papéis (*roles*) que já trazem o comportamento certo embutido. São mais legíveis e menos propensos a erro.

| Papel | Equivalente aproximado | Uso típico |
|---|---|---|
| `role="status"` | `aria-live="polite"` + `aria-atomic="true"` | Confirmações, contadores, resultados, estados. |
| `role="alert"` | `aria-live="assertive"` + `aria-atomic="true"` | Erros que bloqueiam, avisos de sessão a expirar. |
| `role="log"` | `aria-live="polite"` + `aria-relevant="additions"` | Conversas, consolas, históricos onde só interessa o que é novo. |
| `role="timer"` | `aria-live="off"` | Contagens decrescentes (não anuncia por omissão — e ainda bem). |

**Recomendação prática:** use `role="status"` e `role="alert"`. Só desça ao nível dos atributos `aria-live`/`aria-atomic`/`aria-relevant` quando precisar de um comportamento que estes papéis não dão.

#### Exemplo 3 — Erro de validação num formulário

```html
<label for="nif">NIF</label>
<input id="nif" type="text" inputmode="numeric"
       aria-describedby="nif-erro" aria-invalid="false">
<p id="nif-erro" role="alert"></p>
```

```js
const campo = document.getElementById('nif');
const erro = document.getElementById('nif-erro');

campo.addEventListener('blur', () => {
  const valido = /^\d{9}$/.test(campo.value.trim());
  campo.setAttribute('aria-invalid', String(!valido));
  erro.textContent = valido ? '' : 'O NIF tem de ter exactamente 9 dígitos.';
});
```

**O que funciona bem:**

- O `<p>` com `role="alert"` está no HTML desde o início, vazio, imediatamente a seguir ao campo. Está no sítio certo para quem usa ampliação **e** é anunciado a quem usa leitor de ecrã.
- A mensagem diz **o que está errado e o que se espera** — não diz apenas "inválido".
- O `aria-describedby` garante que, se a pessoa voltar ao campo mais tarde, o erro é relido como descrição do campo. O `role="alert"` trata do momento em que o erro surge; o `aria-describedby` trata de todos os momentos seguintes. São complementares, não alternativas.
- Ao corrigir, o texto é limpo e o `aria-invalid` volta a `false`. O estado do campo acompanha a realidade.

**Atenção a uma nuance:** validar em cada tecla premida com um `role="alert"` seria insuportável — a pessoa ouviria "O NIF tem de ter exactamente 9 dígitos" nove vezes seguidas enquanto escreve. Validar no `blur` (quando sai do campo) é o comportamento adequado.

---

### `aria-atomic`: ler a peça inteira ou só o que mudou?

Por omissão, o leitor de ecrã anuncia **apenas a parte que mudou**. Com `aria-atomic="true"`, anuncia **o conteúdo completo da região**, mesmo que só uma palavra tenha mudado.

#### Exemplo 4 — Contador de carrinho

```html
<!-- Versão A -->
<div aria-live="polite">
  Carrinho: <span id="n">2</span> artigos
</div>

<!-- Versão B -->
<div aria-live="polite" aria-atomic="true">
  Carrinho: <span id="n">2</span> artigos
</div>
```

Quando o `2` passa a `3`:

- A **Versão A** anuncia apenas: *"3"*. Fora de contexto, é ininteligível. Três o quê?
- A **Versão B** anuncia: *"Carrinho: 3 artigos"*. Compreensível sozinho.

**O que isto nos ensina:** sempre que a região contiver texto fixo à volta do valor que muda, precisa de `aria-atomic="true"`. Como `role="status"` já implica `aria-atomic="true"`, escrever `<div role="status">Carrinho: <span id="n">2</span> artigos</div>` resolve o problema sem atributos extra.

**Quando *não* usar `aria-atomic="true"`:** numa conversa de chat com 50 mensagens, `aria-atomic="true"` faria o leitor reler as 50 mensagens de cada vez que chegasse uma nova. É aqui que `role="log"` (que anuncia só as adições) é a escolha certa.

---

### `aria-relevant`: que tipo de mudanças interessam?

Indica se interessam adições (`additions`), remoções (`removals`), alterações de texto (`text`) ou tudo (`all`). O valor por omissão é `additions text` — adições e alterações de texto — e serve para a esmagadora maioria dos casos.

**Conselho honesto:** o suporte deste atributo é irregular entre leitores de ecrã e o valor por omissão está quase sempre certo. Se está a pensar em `aria-relevant`, provavelmente o problema é outro. Deixe-o em paz.

---

### `aria-busy`: "ainda estou a arrumar"

Quando uma região vai sofrer várias alterações seguidas, `aria-busy="true"` diz ao leitor de ecrã para esperar. Quando passa a `false`, o conjunto é anunciado de uma vez.

#### Exemplo 5 — Lista de resultados que é reconstruída

```js
const lista = document.getElementById('resultados');

lista.setAttribute('aria-busy', 'true');   // silêncio, estou a trabalhar
lista.innerHTML = '';
for (const r of resultados) {
  lista.appendChild(criarItem(r));
}
lista.setAttribute('aria-busy', 'false');  // já pode anunciar
```

**O que funciona bem:** sem `aria-busy`, cada um dos 20 itens adicionados poderia gerar um anúncio. A pessoa ouviria uma metralhadora de fragmentos. Com `aria-busy`, há um único momento de anúncio.

**Cuidado:** se `aria-busy="true"` ficar por engano (por exemplo, porque um pedido falhou antes de o repor), a região fica **muda para sempre**. Reponha sempre em `finally`.

---

### A alternativa nativa: `<output>`

O elemento `<output>` é uma região dinâmica por natureza: tem implicitamente `role="status"`. É a escolha ideal para resultados de cálculos.

```html
<label for="valor">Valor (€)</label>
<input id="valor" type="number" value="100">

<label for="taxa">Taxa de IVA (%)</label>
<input id="taxa" type="number" value="23">

<p>Total com IVA: <output id="total" for="valor taxa">123,00 €</output></p>
```

**O que funciona bem:** menos código, menos ARIA, comportamento correcto por omissão. A primeira regra do uso de ARIA continua a valer: **se existe elemento HTML nativo com a semântica certa, use-o**.

---

### O padrão do anunciador partilhado

Numa aplicação com muitas notificações, criar uma região por cada mensagem é convite ao erro. O padrão robusto é ter **duas regiões permanentes**, criadas uma vez, e escrever nelas.

```html
<!-- Perto do fim do <body>, sempre presentes, visualmente escondidas -->
<div id="anunciador-polido"    role="status" class="apenas-leitor-ecra"></div>
<div id="anunciador-urgente"   role="alert"  class="apenas-leitor-ecra"></div>
```

```css
/* Esconde visualmente mas mantém disponível para leitores de ecrã.
   NUNCA usar display:none nem visibility:hidden aqui — removeriam
   o conteúdo também para as tecnologias de apoio. */
.apenas-leitor-ecra {
  position: absolute;
  width: 1px; height: 1px;
  padding: 0; margin: -1px;
  overflow: hidden;
  clip-path: inset(50%);
  white-space: nowrap;
  border: 0;
}
```

```js
function anunciar(mensagem, urgente = false) {
  const alvo = document.getElementById(
    urgente ? 'anunciador-urgente' : 'anunciador-polido'
  );
  alvo.textContent = '';            // limpa primeiro
  requestAnimationFrame(() => {     // garante que o navegador vê duas mudanças
    alvo.textContent = mensagem;
  });
}

anunciar('Filtro aplicado. 12 resultados.');
anunciar('A sua sessão expira em 1 minuto.', true);
```

**O que funciona bem:**

- As regiões existem desde o início. Nunca há o problema de "criar e preencher ao mesmo tempo".
- Limpar antes de escrever resolve o caso de **repetir a mesma mensagem duas vezes**: se o texto for idêntico ao anterior, alguns leitores de ecrã não detectam mudança nenhuma e ficam calados. Limpar e voltar a escrever força a detecção.
- Duas regiões separadas evitam misturar urgências.

**O que exige cuidado:**

- Esta região é invisível. Se a mensagem **também** for útil para quem vê o ecrã — e normalmente é — a mensagem visível deve existir na mesma, e não deve ser duplicada aqui (senão é anunciada duas vezes). O anunciador escondido é para informação que, no ecrã, é transmitida por meios não textuais: cor, movimento, posição, ícone.

---

### Quando *não* usar uma região dinâmica

Nem todas as mudanças precisam de altifalante. Há duas alternativas melhores em muitos casos:

1. **Mover o foco.** Se a mudança exige acção imediata da pessoa e cria um novo contexto — abrir um diálogo, entrar num passo seguinte — o correcto é levar o foco lá. 
2. **Usar propriedades e estados.** Se o que mudou foi o estado de um controlo (um botão que passou a "expandido", uma caixa que passou a "marcada"), isso comunica-se com `aria-expanded`, `aria-checked` e afins — não com um anúncio. 

**Regra de decisão em três perguntas:**

| Pergunta | Se sim → |
|---|---|
| A mudança é o estado de um controlo que a pessoa acabou de usar? | Propriedade/estado ARIA. |
| A mudança cria um novo contexto que exige acção imediata? | Mover o foco. |
| A mudança é informação que a pessoa deve saber mas pode continuar o que estava a fazer? | Região dinâmica. |

---

## Recomendações para Conteúdo Acessível

Até aqui falámos de código. Mas o código só transporta a mensagem; a qualidade da mensagem é uma questão de conteúdo.

### Escreva mensagens que se aguentem sozinhas

O anúncio chega ao ouvido sem cor, sem ícone e sem posição. Tudo o que resta é a frase.

| Em vez de | Escreva |
|---|---|
| "Erro" | "Erro: a data de nascimento não pode ser futura." |
| "Concluído" | "Encomenda 4821 submetida. Confirmação enviada por e-mail." |
| "3" | "3 resultados encontrados para 'bicicleta elétrica'." |
| "Inválido" | "A palavra-passe tem de ter pelo menos 8 caracteres." |
| "Não foi possível processar o seu pedido devido a um erro no servidor. Por favor tente mais tarde ou contacte o apoio ao cliente através do número 800 000 000." | "Não foi possível guardar. Tente novamente. Se persistir, contacte o apoio: 800 000 000." |

O último caso mostra o outro extremo: mensagens longas atrasam a pessoa e podem ser interrompidas a meio pela acção seguinte.

### Coloque a informação essencial no início

Quem ouve não pode "saltar à frente" facilmente. "12 resultados. Filtro por preço aplicado." é melhor do que "Filtro por preço aplicado, o que resultou em 12 resultados." A primeira palavra deve ser a que interessa.

### Prefira `polite`, quase sempre

Use `assertive` (ou `role="alert"`) apenas quando a resposta à pergunta *"o que acontece se a pessoa souber disto daqui a 5 segundos?"* for grave: a sessão termina, os dados perdem-se, uma transacção é cancelada. Se a resposta for "nada de especial", use `polite`.

### Não anuncie o que já é evidente pelo mecanismo

Se a pessoa carregou num botão "Adicionar aos favoritos" e o botão passou a ter `aria-pressed="true"`, o leitor de ecrã já anuncia "pressionado". Acrescentar uma região dinâmica que diz "Adicionado aos favoritos" produz um anúncio duplo. Escolha apenas um mecanismo.

### Dê tempo — e um caminho alternativo

Notificações que aparecem e desaparecem sozinhas (*toasts*) são um problema clássico:

- quem lê devagar não acaba a mensagem;
- quem navega por teclado não chega ao botão "Anular" antes de ele desaparecer;
- quem estava a ouvir outra coisa perde o anúncio.

Boas práticas: manter a mensagem visível pelo menos alguns segundos e proporcionalmente ao seu comprimento; **não fazer desaparecer** notificações que contenham controlos (botões, ligações); manter o rato ou o foco sobre a notificação suspende a contagem; e, sempre que possível, deixar a informação disponível noutro sítio permanente (a mensagem de erro junto ao campo, o estado da encomenda na própria página). Isto liga-se ao critério **2.2.1 Ajuste do Tempo**, consolidado na secção final.

### Escreva na língua da página

Se a página está em português, a mensagem tem de estar em português e o `lang="pt"` tem de estar declarado. Uma mensagem em inglês injectada por JavaScript numa página portuguesa será lida com pronúncia portuguesa e sai um som incompreensível. Se um termo em língua estrangeira for inevitável, marque-o: `<span lang="en">token</span>`.

### Teste com um leitor de ecrã real

Não há substituto para isto. As regiões dinâmicas são a área do ARIA com maior variação de comportamento entre implementações. Teste, no mínimo:

- **NVDA + Firefox** e **NVDA + Chrome** (Windows, gratuito);
- **VoiceOver + Safari** (macOS e iOS);
- **TalkBack + Chrome** (Android).

E teste em silêncio: feche os olhos, ou desligue o monitor, e execute a tarefa.

---

### Erros Comuns

**1. Criar a região e o conteúdo ao mesmo tempo**
O erro nº 1, já visto no Exemplo 2. Sintoma: "às vezes anuncia, às vezes não". Solução: região vazia no HTML inicial; só o texto muda.

**2. Esconder a região com `display: none` e mostrá-la ao anunciar**

```html
<!-- MAL -->
<div role="status" style="display:none">Guardado.</div>
```
```js
elemento.style.display = 'block';  // não é garantido que anuncie
```

Um elemento com `display: none` ou `visibility: hidden` **não existe** para o leitor de ecrã. Torná-lo visível não conta necessariamente como "mudança de conteúdo". Solução: manter a região sempre presente e mudar o **texto**; ou, se tiver de esconder, use a classe `.apenas-leitor-ecra` mostrada atrás, que esconde visualmente sem remover da árvore de acessibilidade.

**3. Usar `assertive` para tudo**
Uma página onde cada confirmação interrompe a leitura é uma página onde ninguém consegue ler nada até ao fim. `assertive` é a sirene: se tocar sempre, deixa de significar perigo.

**4. Regiões dinâmicas dentro de conteúdo que aparece e desaparece**
Uma janela modal que é adicionada ao DOM já com um `role="alert"` lá dentro tem o mesmo problema do erro nº 1. Regiões dinâmicas devem viver em elementos estáveis da página.

**5. Anunciar cada tecla premida numa pesquisa em tempo real**
Uma caixa de pesquisa que filtra à medida que se escreve, com `aria-live="polite"` nos resultados, gera um anúncio por letra: "48 resultados", "12 resultados", "3 resultados"... Solução: aplicar um atraso (*debounce*) de cerca de 500 ms a 1 segundo antes de actualizar a região, para que só o resultado estabilizado seja anunciado.

**6. Colocar `aria-live` num contentor gigante**

```html
<!-- MAL -->
<main aria-live="polite"> ... a aplicação inteira ... </main>
```

Qualquer mudança em qualquer sítio dispara anúncios. A página passa a falar sozinha, sem parar. Solução: regiões pequenas e específicas.

**7. Confiar apenas em ícones, cores ou animações**
O ✔ verde, o círculo que gira, a barra que enche. Nada disto é texto. Solução: texto associado, mesmo que escondido visualmente.

**8. Repetir a mesma mensagem e não perceber porque não é anunciada**
Escrever "Erro: campo obrigatório" numa região onde já estava exactamente "Erro: campo obrigatório" pode não gerar anúncio nenhum — o conteúdo não mudou. Solução: limpar a região antes de reescrever (o padrão do anunciador partilhado trata disto).

**9. Deixar `aria-busy="true"` por reposição falhada**
A região fica muda e ninguém percebe porquê. Solução: repor em `finally`.

**10. Usar região dinâmica onde devia mover o foco**
Um diálogo modal abre e a página anuncia "Diálogo aberto" — mas o foco fica no botão. A pessoa ouve, mas não consegue chegar lá. Solução: ver a secção *Interações por Teclado e Foco*.

**11. Duplicar mensagem visível e mensagem escondida**
A pessoa ouve tudo duas vezes. Solução: uma mensagem, um mecanismo. Se a mensagem visível está numa região dinâmica, não precisa de anunciador escondido.

**12. Esquecer os casos de erro e de vazio**
Anuncia-se "5 resultados" mas não se anuncia "Nenhum resultado encontrado" nem "A pesquisa falhou". Quem não vê o ecrã fica sem saber se a aplicação está a pensar, se avariou, ou se simplesmente não há nada. **O silêncio é sempre a pior mensagem.**

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Uma **região dinâmica** é o altifalante da página: comunica alterações que acontecem **sem recarregar a página e sem mover o foco**.
- Sem ela, a informação transmitida por cor, ícone, movimento ou posição **não existe** para quem não vê o ecrã, nem para quem vê apenas uma pequena parte dele.
- **A região tem de existir no DOM antes da mudança.** Criar região e conteúdo em simultâneo é o erro mais frequente e o mais traiçoeiro.
- **Só o texto deve mudar.** Alternar `display` não é uma mudança de conteúdo fiável.
- **Prefira `role="status"`** (educado) e reserve **`role="alert"`** (interrompe) para o que é realmente urgente. Para históricos e conversas, `role="log"`.
- **`aria-atomic="true"`** faz reler a região inteira — indispensável quando há texto fixo à volta do valor que muda; contraproducente em listas longas.
- **`aria-busy`** silencia a região durante actualizações em lote; reponha-o sempre.
- **`<output>`** é a solução nativa para resultados de cálculo, com `role="status"` implícito.
- O padrão robusto para aplicações é um **anunciador partilhado**: duas regiões permanentes (educada e urgente), limpar antes de escrever.
- **Escreva mensagens completas, curtas e com o essencial à frente.** O anúncio chega sem contexto.
- **Nem tudo é região dinâmica:** estados de controlos comunicam-se com propriedades ARIA; contextos novos comunicam-se movendo o foco.
- **Anunciar de menos deixa as pessoas às escuras; anunciar de mais deixa-as surdas.** O equilíbrio testa-se com um leitor de ecrã real.

---

### Exercícios Práticos

**Exercício 1 — Diagnóstico**

Analise este código e identifique **quatro** problemas distintos. Para cada um, explique o efeito prático para uma pessoa cega que usa leitor de ecrã.

```html
<button id="sub">Subscrever newsletter</button>
<div id="msg"></div>
```
```js
document.getElementById('sub').addEventListener('click', () => {
  const zona = document.getElementById('msg');
  zona.innerHTML = '<span aria-live="assertive" style="color:green">✔</span>';
  setTimeout(() => { zona.innerHTML = ''; }, 2000);
});
```

**Exercício 2 — Correcção**

Reescreva o código do Exercício 1 de forma acessível. O resultado deve: usar uma região permanente, comunicar sucesso **e** falha, ter mensagens compreensíveis isoladamente, e não desaparecer demasiado depressa. Justifique cada decisão em duas linhas.

**Exercício 3 — Escolha do mecanismo**

Para cada cenário, decida: **(a)** propriedade/estado ARIA, **(b)** mover o foco, **(c)** região `polite`, **(d)** região `assertive`. Justifique.

1. Um botão "Mostrar mais detalhes" expande um painel por baixo.
2. Uma tabela de faturas é ordenada por data e o número de linhas mantém-se.
3. A sessão bancária expira em 60 segundos.
4. Um carrinho de compras passa de 2 para 3 artigos.
5. O envio de um formulário falha por erro de rede.
6. Uma pesquisa com filtros passa de 40 para 6 resultados.
7. Um botão "Eliminar" abre uma janela de confirmação.
8. Um ficheiro está a ser carregado e o progresso vai em 45%.

**Exercício 4 — Construção**

Construa uma caixa de pesquisa com filtragem em tempo real sobre uma lista de 30 concelhos. Requisitos:

- os resultados actualizam-se enquanto se escreve;
- o número de resultados é anunciado, mas **não a cada tecla**;
- o caso "nenhum resultado" é comunicado;
- nada interrompe a escrita da pessoa;
- a lista visível e o anúncio dizem a mesma coisa.

Depois, teste com um leitor de ecrã. Documente: o que anunciou, o que não anunciou, e o que teve de alterar.

**Exercício 5 — Auditoria**

Escolha uma página real com conteúdo dinâmico (um site de comércio eletrónico, um formulário de um serviço público, uma aplicação que use no dia a dia). Com um leitor de ecrã ligado e o monitor desligado (ou os olhos fechados), tente completar uma tarefa que provoque alterações dinâmicas: aplicar um filtro, adicionar um artigo ao carrinho, submeter um formulário com um erro propositado.

Registe:

1. Que alterações foram anunciadas e quais ficaram em silêncio.
2. Em que momento se sentiu perdido e porquê.
3. Que anúncios foram excessivos ou repetidos.
4. Três correcções concretas, com o código sugerido.

**Exercício 6 — Discussão**

Um colega defende: *"Na dúvida, mete-se `aria-live="assertive"` — assim garantimos que ninguém perde a mensagem."* Prepare uma resposta de dois minutos, com pelo menos um exemplo concreto de como esta estratégia prejudica os utilizadores que pretende ajudar.
