---
title: Notificações e Mensagens de Erro
layout: default
nav_order: 4
---
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

