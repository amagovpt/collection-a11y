# Escolher a Alternativa Certa

## Introdução

Nas restantes secções deste módulo vamos aprender, em detalhe, *como* se produz cada tipo de alternativa: transcrições, legendas, descrição da informação visual e língua gestual. Esta secção tem um objetivo diferente e anterior a todos esses: ajudar a **decidir qual (ou quais) dessas alternativas o nosso conteúdo realmente precisa**.

É uma distinção importante. Saber legendar um vídeo não serve de nada se o que aquele conteúdo precisava era de uma transcrição. E oferecer uma transcrição perfeita não resolve o problema de um vídeo que também precisava de audiodescrição.

Pense-se num médico. Antes de prescrever um medicamento, faz um diagnóstico. Prescrever antibióticos a quem tem uma constipação é ao mesmo tempo inútil e um desperdício. Com as alternativas ao conteúdo multimédia acontece o mesmo: **primeiro diagnostica-se o que o conteúdo é e quem precisa de aceder a ele; só depois se "prescreve" a alternativa certa.**

Esta secção é esse diagnóstico. No fim, deverá conseguir olhar para qualquer peça de multimédia (um vídeo de formação, um *podcast*, uma animação, uma transmissão em direto) e saber, com segurança, que alternativas são obrigatórias, quais são recomendáveis e quais seriam redundantes.

### Como as Pessoas com Deficiência dependem de Alternativas a Conteúdo Multimédia

Para escolher bem, precisamos primeiro de um modelo mental simples de *porque* estas alternativas existem.

Um conteúdo multimédia pode comunicar em **dois canais ao mesmo tempo**:

- O **canal sonoro** — fala, música, efeitos sonoros, tom de voz.
- O **canal visual** — o que se vê no ecrã: ações, texto, expressões faciais, gráficos, cores, cenário.

Uma pessoa que percebe os dois canais recebe a mensagem completa. O problema surge quando uma deficiência bloqueia o acesso a um dos canais, ou aos dois.

Uma boa forma de pensar nisto é como uma **tradução entre línguas**. O vídeo "fala" simultaneamente a "língua do som" e a "língua da imagem". Algumas pessoas só compreendem uma dessas línguas:

- Uma pessoa **surda ou com dificuldades auditivas** não recebe a "língua do som". Precisa que o som seja traduzido para o mundo visual ou textual.
- Uma pessoa **cega ou com baixa visão** não recebe a "língua da imagem". Precisa que a imagem seja traduzida para o mundo sonoro ou textual.
- Uma pessoa **surdocega** não recebe nenhum dos dois canais. Precisa que *ambos* sejam traduzidos para texto (texto esse que a sua tecnologia de apoio pode converter em braille).

Cada alternativa que estudaremos neste módulo é, na prática, **um tradutor entre canais**:

| Alternativa | Traduz... | Beneficia sobretudo |
|---|---|---|
| Legendas | som → texto visual sincronizado | Pessoas surdas e com dificuldades auditivas |
| Transcrição | som (e imagem) → texto não sincronizado | Pessoas surdocegas e todos os que preferem texto |
| Audiodescrição | imagem → som | Pessoas cegas e com baixa visão |
| Língua gestual | som → gesto visual | Pessoas surdas cuja primeira língua é a língua gestual |

Escolher a alternativa certa é, portanto, **escolher qual tradução o nosso conteúdo precisa** — e isso depende de que "línguas" o conteúdo usa e de quem precisa de o compreender.

Um ponto que costuma passar despercebido: as legendas e a língua gestual servem *o mesmo canal* (traduzem o som para o visual), mas **não servem as mesmas pessoas**. Muitas pessoas surdas cuja primeira língua é a Língua Gestual Portuguesa (LGP) leem português escrito com esforço, tal como qualquer pessoa lê uma segunda língua com mais dificuldade do que a materna. Para essas pessoas, as legendas ajudam mas não substituem a língua gestual. Voltaremos a este ponto quando falarmos de erros comuns.

### Requisitos de Acessibilidade para as Alternativas a Conteúdo Multimédia

Felizmente, não temos de decidir tudo com base na intuição. As WCAG (na Diretriz 1.2, *Conteúdo multimédia dependente do tempo*) dão-nos exatamente a lógica de decisão. Nesta secção interessa-nos essa lógica; a lista completa e detalhada dos critérios está consolidada na secção final do módulo (*Critérios de Sucesso WCAG Relacionados*), pelo que aqui usamos os números apenas para ancorar cada decisão.

A decisão assenta em **três perguntas**:

**Pergunta 1 — Que tipo de conteúdo é?**

- **Só áudio** (por exemplo, um *podcast* ou uma entrevista em áudio). Não há imagem a considerar.
- **Só vídeo** (por exemplo, uma animação silenciosa que mostra um processo, ou um vídeo sem qualquer som). Não há som a considerar.
- **Multimédia sincronizada** — áudio e vídeo em simultâneo, sincronizados (a esmagadora maioria dos vídeos: uma aula gravada, um tutorial, uma reportagem).

**Pergunta 2 — É pré-gravado ou em direto?**

O conteúdo em direto é muito mais exigente de tornar acessível (não há tempo para legendar com calma depois), e as WCAG refletem isso: só exigem, no nível AA, legendas em direto — não exigem audiodescrição em direto.

**Pergunta 3 — O que está em cada canal já está no outro?**

Esta é a pergunta mais subtil e a mais esquecida. Se tudo o que é dito também aparece escrito no ecrã, ou se tudo o que se vê já é narrado em voz alta, algumas alternativas podem tornar-se redundantes. Pelo contrário, tornam-se indispensáveis se essa informação *só* existe num dos canais.

Cruzando as respostas, obtemos os requisitos. A tabela seguinte resume o essencial ao nível legalmente exigido em Portugal (WCAG 2.1 AA, por via do Decreto-Lei n.º 83/2018 e da EN 301 549):

| Tipo de conteúdo | Alternativa obrigatória | Critério WCAG (nível) |
|---|---|---|
| Só áudio, pré-gravado | Transcrição | 1.2.1 (A) |
| Só vídeo, pré-gravado | Descrição textual **ou** banda sonora equivalente | 1.2.1 (A) |
| Multimédia sincronizada, pré-gravada | Legendas | 1.2.2 (A) |
| Multimédia sincronizada, pré-gravada | Audiodescrição | 1.2.5 (AA) |
| Multimédia sincronizada, **em direto** | Legendas em direto | 1.2.4 (AA) |

Há dois pormenores nesta tabela que valem ouro na hora de decidir:

1. **As legendas (1.2.2) não têm alternativa: são sempre obrigatórias** para conteúdo sincronizado pré-gravado com som. Não há a opção "ou transcrição". Uma transcrição, por muito boa que seja, **não** cumpre o critério das legendas.
2. **A audiodescrição escala de nível.** No nível A (1.2.3), pode escolher-se entre audiodescrição *ou* uma alternativa multimédia completa em texto. Mas no nível AA (1.2.5) — o nosso mínimo legal — a **audiodescrição passa a ser obrigatória**; a alternativa em texto deixa de ser suficiente por si só. Como a base legal em Portugal é AA, na prática **um vídeo com informação visual importante precisa mesmo de audiodescrição.**

Existem ainda requisitos de nível AAA — língua gestual (1.2.6), audiodescrição alargada (1.2.7) e alternativa multimédia completa (1.2.8) — que não são legalmente obrigatórios, mas que representam o nível de excelência e que veremos como decisão opcional mais à frente.

## Técnicas de Codificação

Como esta secção é sobre *escolher*, e não sobre *produzir*, a "codificação" aqui resume-se a duas coisas: **saber ler, no código, que tipo de conteúdo temos** e **saber onde cada alternativa se liga**. Os detalhes de cada técnica (o formato WebVTT das legendas, a sincronização da audiodescrição, etc.) ficam para as secções dedicadas.

### Ler o tipo de conteúdo no próprio código

Muitas vezes, o primeiro sinal do tipo de conteúdo está no elemento HTML utilizado:

```html
<!-- Só áudio -->
<audio src="episodio-12.mp3" controls></audio>

<!-- Vídeo (pode ser só vídeo ou sincronizado) -->
<video src="aula-03.mp4" controls></video>
```

**O que isto nos diz:** um elemento `<audio>` indica, quase sempre, conteúdo *só áudio* → o caminho é a transcrição. Um elemento `<video>` exige a Pergunta 3: o vídeo tem som? Se sim, é multimédia sincronizada; se não (uma animação muda), é *só vídeo*. O elemento por si só não chega — é preciso confirmar se existe faixa de áudio com conteúdo.

### O atributo `kind`: a escolha expressa em código

Quando ligamos alternativas a um `<video>`, usamos o elemento `<track>`. E é precisamente o seu atributo `kind` que **codifica qual alternativa estamos a fornecer**:

```html
<video src="aula-03.mp4" controls>
  <track kind="captions"     src="aula-03-pt.vtt" srclang="pt" label="Português (legendas)">
  <track kind="descriptions" src="aula-03-ad.vtt" srclang="pt" label="Audiodescrição">
</video>
```

**Análise do exemplo:**

- `kind="captions"` — legendas para pessoas surdas: incluem fala **e** informação sonora não verbal (música, efeitos). É o valor correto para cumprir 1.2.2.
- `kind="descriptions"` — o "gancho" para a audiodescrição (1.2.5).
- Existe ainda `kind="subtitles"`, que **não** é a mesma coisa que `captions`: as *subtitles* destinam-se a quem ouve mas não domina a língua (é uma tradução linguística) e por isso **não descrevem os sons**. Escolher `subtitles` quando se precisava de `captions` é um erro de escolha, não de programação, porque deixa de fora quem não ouve.

O ponto essencial para esta secção é este: **o `kind` que escolhemos é a materialização da decisão**. Escolher o `kind` errado é escolher a alternativa errada, mesmo que o ficheiro esteja tecnicamente impecável.

### Onde vivem as alternativas não sincronizadas

Nem tudo se liga por `<track>`. A **transcrição** e a **descrição textual da informação visual** são normalmente texto na própria página, colocado junto ao leitor de multimédia e associado a ele por um título ou uma ligação clara:

```html
<video src="aula-03.mp4" controls>
  <track kind="captions" src="aula-03-pt.vtt" srclang="pt" label="Português">
</video>

<a href="aula-03-transcricao.html">Ver transcrição desta aula</a>
```

**Análise:** as legendas viajam *dentro* do vídeo (via `<track>`); a transcrição vive *ao lado* dele, como texto acessível a qualquer tecnologia de apoio e pesquisável. Perceber esta diferença de "morada" ajuda a não confundir as duas alternativas.

## Recomendações para Conteúdo Acessível

Reunindo tudo, aqui está uma **árvore de decisão** que pode aplicar a qualquer conteúdo. Percorra-a de cima para baixo.

**Passo 1 — Classifique o conteúdo (Pergunta 1).**

- **Só áudio?** → Forneça uma **transcrição** (1.2.1). Fim.
- **Só vídeo / animação sem som?** → Forneça uma **descrição em texto** do que acontece **ou** acrescente uma **banda sonora** que narre o mesmo (1.2.1). Fim.
- **Áudio + vídeo sincronizados?** → Continue para o Passo 2.

**Passo 2 — Trate o canal sonoro.**

- Adicione **legendas** (obrigatório e sem alternativa — 1.2.2 se pré-gravado, 1.2.4 se em direto).

**Passo 3 — Trate o canal visual.**

- Pergunte-se: *existe informação importante que só se vê e nunca se ouve?* (números num gráfico, texto no ecrã, uma ação silenciosa, quem está a falar).
  - **Sim** → é preciso **audiodescrição** (1.2.5, AA). No nível A, poderia bastar uma alternativa multimédia em texto (1.2.3), mas na base legal AA a audiodescrição torna-se obrigatória.
  - **Não** — tudo o que se vê já é dito em voz alta → a audiodescrição pode ser mínima ou dispensável. Aplicou o "teste do já transmitido".

**Passo 4 — Considere ir além do mínimo (opcional, AAA).**

- Público que usa **língua gestual** como primeira língua? → considere **interpretação em língua gestual** (1.2.6).
- As pausas na banda sonora **não chegam** para descrever tudo o que é visual? → **audiodescrição alargada** (1.2.7).
- Quer oferecer o conteúdo completo também em texto único e pesquisável? → **alternativa multimédia** (1.2.8).

### O "teste do já transmitido" na prática

Este teste evita os dois erros opostos: fornecer a menos e fornecer a mais.

**Exemplo A — vídeo onde a imagem já está no som.**
Um formador aparece a falar para a câmara e diz tudo o que interessa: "Como veem neste slide, os três passos são planear, executar e rever." Nada de importante acontece apenas visualmente.

*Análise:* precisa de legendas (o som tem de chegar a quem não ouve), mas a audiodescrição seria quase vazia — não há informação visual "escondida". Aqui, insistir numa audiodescrição elaborada seria esforço desperdiçado.

**Exemplo B — vídeo onde a imagem NÃO está no som.**
Um vídeo mostra um gráfico a crescer enquanto uma música toca, sem qualquer narração dos valores. No ecrã lê-se "vendas subiram 40%", mas isso nunca é dito.

*Análise:* uma pessoa cega ficaria apenas com música e sem a mensagem. Aqui a audiodescrição é **indispensável** — o "40%" só existe no canal visual. Este é o caso onde falhar a audiodescrição deixa a mensagem principal inacessível.

A lição: **a audiodescrição não é decorativa; é obrigatória exatamente quando a informação importante vive só na imagem.**

### Estratégia por camadas

Uma forma prática de gerir esforço e prazos: **cumpra primeiro o nível A, depois o AA, e só depois pondere o AAA.**

1. Comece pelas alternativas de nível A (transcrição para só áudio/só vídeo; legendas para sincronizado).
2. Suba para AA (audiodescrição em conteúdo pré-gravado; legendas em direto).
3. Se houver recursos e um público que beneficie claramente, avance para AAA (língua gestual, audiodescrição alargada).

Assim, mesmo que os recursos sejam limitados, garante-se sempre a conformidade legal antes de investir nos extras.

### Erros Comuns

**Erro 1 — Confundir transcrição com legendas.**
"Já pus a transcrição, portanto o vídeo está legendado." Não está. A transcrição é texto não sincronizado, ao lado do vídeo; as legendas aparecem no ecrã, sincronizadas com a fala. Cumprem critérios diferentes (1.2.1 vs. 1.2.2) e servem momentos diferentes de utilização. Uma **não substitui** a outra num vídeo sincronizado.

**Erro 2 — Legendar e esquecer a audiodescrição.**
As legendas resolvem o canal sonoro, mas deixam intacto o problema de quem não vê. Um vídeo com informação apenas visual (gráficos, texto no ecrã, ações silenciosas) continua inacessível a pessoas cegas até ter audiodescrição (1.2.5).

**Erro 3 — Escolher `subtitles` quando se precisava de `captions`.**
As *subtitles* traduzem a língua para quem ouve; **não incluem os sons**. Uma pessoa surda continua sem saber que "tocou o telefone" ou que "há música de tensão". Para acessibilidade, o valor correto é quase sempre `captions`.

**Erro 4 — Achar que a língua gestual é substituível pelas legendas (ou vice-versa).**
Servem o mesmo canal mas públicos diferentes. Para muitas pessoas surdas, a LGP é a primeira língua e o português escrito é uma segunda língua; as legendas ajudam, mas não igualam a compreensão em língua gestual. E, ao contrário, a língua gestual não substitui as legendas para as muitas pessoas com dificuldades auditivas que **não** usam língua gestual. Não é "ou uma ou outra": são decisões independentes.

**Erro 5 — Fornecer a mais, por precaução.**
Gastar horas a audiodescrever um vídeo em que o narrador já diz tudo o que se vê é desperdiçar esforço que faria falta noutro conteúdo. Aplicar o "teste do já transmitido" evita tanto a falta como o excesso.

**Erro 6 — Tratar conteúdo em direto como se fosse pré-gravado.**
O direto tem regras próprias: exige legendas em tempo real (1.2.4) e **não** exige audiodescrição. Planear a acessibilidade do direto *depois* do evento é tarde demais — tem de ser preparado antes.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Esta secção é sobre **decidir** qual alternativa usar; o *como* de cada uma vem nas secções seguintes.
- O multimédia comunica em dois canais — **som** e **imagem**. Cada deficiência bloqueia canais diferentes, e cada alternativa é um **tradutor** entre canais.
- A decisão assenta em três perguntas: **que tipo de conteúdo** (só áudio, só vídeo, sincronizado), **direto ou pré-gravado**, e **o que está num canal já está no outro?**
- Mapa rápido do mínimo legal (AA): só áudio → **transcrição**; só vídeo → **descrição textual ou banda sonora**; sincronizado → **legendas** (sempre) **+ audiodescrição** (quando há informação só visual); direto → **legendas em tempo real**.
- **As legendas nunca têm alternativa** em conteúdo sincronizado; **a transcrição não substitui as legendas.**
- **A audiodescrição é obrigatória no nível AA** sempre que exista informação importante que só se vê.
- Legendas e língua gestual servem o mesmo canal mas **públicos diferentes** — uma não dispensa a outra.
- Aplique a estratégia por **camadas** (A → AA → AAA) e o **"teste do já transmitido"** para nem fornecer a menos nem a mais.

### Exercícios Práticos

**Exercício 1 — Diagnóstico rápido.**
Para cada conteúdo, indique que alternativas são obrigatórias no nível AA e a que critério(s) correspondem:

a) Um episódio de *podcast* de 40 minutos, em áudio.
b) Uma animação silenciosa (GIF/vídeo sem som) que demonstra como preencher um formulário.
c) A gravação de um *webinar* com o orador a falar e *slides* com dados a aparecerem no ecrã, sem que os valores sejam ditos em voz alta.
d) Uma sessão de perguntas e respostas transmitida **em direto**, com vídeo e som.

**Exercício 2 — Aplicar o "teste do já transmitido".**
Veja (ou imagine) dois vídeos: um em que o narrador descreve tudo o que aparece no ecrã, e outro em que aparecem legendas de texto e imagens nunca mencionadas na voz. Para cada um, decida se a audiodescrição é indispensável, mínima ou dispensável, e justifique em duas frases.

**Exercício 3 — Corrigir uma escolha.**
Um colega entregou este código para um vídeo de formação com fala e efeitos sonoros importantes:

```html
<video src="modulo1.mp4" controls>
  <track kind="subtitles" src="modulo1.vtt" srclang="pt" label="Português">
</video>
<a href="modulo1-transcricao.html">Transcrição</a>
```

Identifique **dois** problemas de *escolha de alternativa* (não de sintaxe) neste exemplo e proponha a correção.

**Exercício 4 — Decidir sobre língua gestual.**
Uma instituição vai publicar um vídeo institucional dirigido, entre outros, à comunidade surda. O vídeo já terá legendas. Argumente, em três a cinco frases, se faz sentido acrescentar interpretação em língua gestual e a que critério isso corresponderia.

