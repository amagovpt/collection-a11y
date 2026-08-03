---
title: Legendas
layout: default
nav_order: 4
---
# Legendas

## Introdução

As legendas são a versão em texto da informação sonora de um vídeo, apresentada **sincronizadamente** com as imagens. À medida que o vídeo avança, o texto aparece e desaparece no momento certo, acompanhando aquilo que se ouve.

Antes de avançarmos, é preciso desfazer uma confusão muito frequente. Em português usamos a mesma palavra — «legendas» — para duas coisas diferentes:

- **Legendas de tradução** (em inglês, *subtitles*): traduzem apenas o **diálogo** de uma língua para outra. Partem do princípio de que a pessoa **ouve** o som — ouve a explosão, ouve o telefone, ouve a música — e só precisa de ajuda a perceber as palavras faladas.
- **Legendas para acessibilidade** (em inglês, *captions*): destinam-se a quem **não ouve o som**, no todo ou em parte. Por isso, além do diálogo, incluem também **quem** está a falar e os **sons relevantes** que não são fala (uma porta a bater, música tensa, aplausos).

Uma analogia ajuda a fixar a diferença. Imagine dois espectadores no mesmo filme estrangeiro:

- O primeiro **ouve tudo**, mas não entende a língua. Basta-lhe uma tradução das palavras. Ele próprio percebe, pelo som, que houve uma explosão. — Isto são *legendas de tradução*.
- O segundo **não ouve nada**. A tradução das palavras não chega: se ninguém lhe disser, ele não sabe que houve uma explosão, nem que o telefone tocou, nem que a personagem sussurrou. — Isto são *legendas para acessibilidade*.

Nesta secção, quando dizemos «legendas» sem mais nada, referimo-nos às **legendas para acessibilidade**. São estas que garantem que uma pessoa surda ou com perda auditiva recebe a mesma informação que uma pessoa ouvinte.

### Como as Pessoas com Deficiência dependem de Legendas

As legendas são a principal via de acesso ao som para vários grupos de pessoas:

- **Pessoas surdas** que não têm acesso funcional ao áudio. Para muitas, a leitura das legendas é a única forma de saber o que está a ser dito e o que se está a ouvir.
- **Pessoas com perda auditiva parcial** que ouvem alguma coisa, mas não o suficiente para distinguir todas as palavras, sobretudo quando há ruído de fundo, várias pessoas a falar ou má qualidade de áudio.
- **Pessoas surdocegas** que utilizam uma **linha braille**. Como as legendas são texto, podem ser encaminhadas para esse dispositivo, algo impossível de fazer com o som.

É importante perceber **como** estas pessoas usam as legendas na prática, porque isso condiciona as decisões técnicas:

- Elas leem a legenda **ao mesmo tempo** que veem a imagem. Se a legenda passa depressa demais, a pessoa fica presa a ler e **perde** o que acontece no ecrã.
- Elas dependem das legendas para saber **quem** fala. Numa cena com várias personagens fora do plano, sem identificação de quem fala, a legenda torna-se um monólogo confuso.
- Elas dependem das legendas para os **sons que não são fala**. Se o argumento assenta num telefone que toca e ninguém atende, uma legenda que só transcreva o diálogo esconde a própria história.

Além destes grupos, muitas outras pessoas beneficiam das legendas em situações do dia a dia: quem vê vídeos em ambientes ruidosos (transportes, cafés), em ambientes silenciosos onde não pode ligar o som (uma biblioteca, ao lado de alguém a dormir), quem está a aprender a língua, ou simplesmente quem lê melhor do que ouve um sotaque desconhecido. As legendas são um bom exemplo de que uma solução de acessibilidade beneficia toda a gente. Mas para o público que **depende** delas, não são conveniência: são a diferença entre aceder ou não aceder ao conteúdo.

### Requisitos de Acessibilidade para Legendas

Para que umas legendas cumpram a sua função, têm de reunir cinco propriedades. Guarde estas cinco palavras: **sincronizadas, completas, identificadas, corretas e legíveis**.

1. **Sincronizadas** — o texto aparece e sai em sintonia com o som. Uma legenda certa mas fora de tempo confunde tanto como uma legenda errada.
2. **Completas (equivalentes)** — incluem *tudo* o que é relevante para compreender o conteúdo: o diálogo **e** os sons significativos que não são fala. Não basta transcrever as palavras.
3. **Identificadas** — indicam **quem** fala sempre que isso não seja óbvio pela imagem (por exemplo, alguém que fala fora do plano).
4. **Corretas** — o texto corresponde ao que é dito, com ortografia e pontuação adequadas. Legendas com erros deturpam o sentido.
5. **Legíveis** — o ritmo, o número de linhas e a posição no ecrã permitem ler com conforto, sem tapar informação visual importante.

Do ponto de vista normativo, as legendas para acessibilidade estão diretamente associadas a dois critérios das WCAG:

- **1.2.2 Legendas (Pré-gravado)** — Nível A: exige legendas para todo o conteúdo áudio pré-gravado que faça parte de conteúdo sincronizado (vídeo com som).
- **1.2.4 Legendas (Em Direto)** — Nível AA: estende a exigência ao conteúdo áudio **em direto** (por exemplo, transmissões e webinars ao vivo).

## Técnicas de Codificação

Na web, a forma correta de disponibilizar legendas é através de um **ficheiro de texto** separado, ligado ao vídeo. O formato normalizado para a web é o **WebVTT** (ficheiros com a extensão `.vtt`).

### O formato WebVTT

Um ficheiro WebVTT é texto simples, legível por qualquer pessoa. Começa sempre pela palavra `WEBVTT` e é composto por blocos chamados *cues* (marcas). Cada *cue* tem um **intervalo de tempo** (início `-->` fim) e o **texto** que deve aparecer nesse intervalo.

```
WEBVTT

00:00:00.500 --> 00:00:03.000
[música suave de piano]

00:00:03.500 --> 00:00:06.000
ANA: Bom dia. Sentem-se, por favor.

00:00:06.500 --> 00:00:09.000
[telemóvel a vibrar]

00:00:09.500 --> 00:00:12.000
ANA: (baixinho) Desculpem, é urgente.
```

**O que funciona bem neste exemplo:**

- Cada *cue* cobre um intervalo curto e específico, o que garante **sincronização**.
- O som que não é fala está presente e assinalado entre parênteses retos: `[música suave de piano]`, `[telemóvel a vibrar]`. Sem isto, quem não ouve não saberia que há música nem que o telemóvel vibrou — e é o telemóvel que justifica a fala seguinte.
- O nome `ANA:` **identifica** quem fala. Numa cena com mais pessoas, isto evita ambiguidade.
- A indicação de **maneira** `(baixinho)` transmite uma informação que o som daria a quem ouve.

### Ligar as legendas ao vídeo: o elemento `<track>`

Em HTML5, o ficheiro `.vtt` liga-se ao vídeo com o elemento `<track>`, colocado dentro do `<video>`:

```html
<video controls>
  <source src="apresentacao.mp4" type="video/mp4">
  <track kind="captions" src="apresentacao-pt.vtt"
         srclang="pt" label="Português" default>
</video>
```

Os atributos do `<track>` fazem cada um o seu papel:

- `kind="captions"` — declara que este é um ficheiro de **legendas para acessibilidade** (inclui sons que não são fala). Este valor é o coração da correção semântica deste elemento.
- `src` — o caminho para o ficheiro `.vtt`.
- `srclang="pt"` — a língua das legendas.
- `label="Português"` — o texto que o utilizador vê no menu de legendas do leitor. Deve ser claro, porque é por aqui que a pessoa escolhe a faixa.
- `default` — indica que esta faixa é ativada por omissão.

**Cuidado com o valor de `kind`.** Compare com esta variante:

```html
<track kind="subtitles" src="apresentacao-pt.vtt"
       srclang="pt" label="Português">
```

**O que corre mal aqui:** `kind="subtitles"` declara que a faixa é uma **tradução para pessoas ouvintes** — ou seja, promete apenas o diálogo, sem sons nem identificação de interlocutores. Se o ficheiro na verdade inclui `[telemóvel a vibrar]` e `ANA:`, há uma contradição entre o que o código **promete** e o que o conteúdo **entrega**. Além disso, a pessoa que procura legendas de acessibilidade pode presumir, pelo rótulo e pela categoria, que essa informação não está lá e desistir. Para legendas de acessibilidade, o valor correto é **sempre** `kind="captions"`.

> Regra prática: se o ficheiro contém **algum** som que não é fala ou **alguma** identificação de quem fala, é `kind="captions"`. Se contém *apenas* diálogo traduzido, é `kind="subtitles"`.

### Legendas fechadas e legendas abertas

Existem duas maneiras de fazer chegar legendas ao espetador:

- **Legendas fechadas** (*closed captions*): vivem num ficheiro separado (como o `.vtt` acima) e o utilizador **liga e desliga** no leitor. São a abordagem recomendada na web, porque a pessoa controla se as vê, e muitos leitores permitem-lhe ainda ajustar tamanho e cor do texto.
- **Legendas abertas** (*open captions*): estão **«queimadas»** nos próprios píxeis do vídeo, fazem parte da imagem e **não se podem desligar** nem personalizar.

Uma analogia: as legendas fechadas são como as legendas de um DVD, que se ativam no menu; as legendas abertas são como um carimbo impresso permanentemente em cada fotograma.

**Quando é que cada uma funciona bem ou mal?**

- As **fechadas** funcionam bem na esmagadora maioria dos casos web: dão controlo e flexibilidade ao utilizador. O «mal» é dependerem de o leitor as expor corretamente (um ponto tratado na secção *Leitores de Multimédia*).
- As **abertas** só compensam em contextos que **removem** as faixas de legendas — por exemplo, certas redes sociais que não suportam `<track>`. Aí, «queimar» as legendas garante que aparecem. O preço a pagar é grande: não se podem desligar, não se adaptam ao tamanho de letra da pessoa, e se a resolução baixar podem tornar-se ilegíveis. Devem ser a exceção, não a regra.

## Recomendações para Conteúdo Acessível

Ter legendas não chega; é preciso que sejam **boas** legendas. As recomendações seguintes traduzem as cinco propriedades (sincronizadas, completas, identificadas, corretas, legíveis) em decisões concretas.

### Incluir os sons que não são fala

Transcreva os sons **relevantes para a compreensão**, não todos os sons. O critério é: *se este som desaparecesse, uma pessoa ouvinte perderia informação?* Se sim, ele vai para a legenda.

- Efeitos sonoros com significado: `[porta a bater]`, `[vidros a partir]`, `[passos a aproximar-se]`.
- Música, descrita pelo seu papel: `[música tensa]`, `[música alegre]`. Se a letra de uma canção for importante, transcreva-a, assinalando que é cantada (por exemplo, com o símbolo ♪).
- Ausência de som, quando é intencional e significativa: `[silêncio]`.

Convenção comum: colocar estas descrições entre **parênteses retos** `[ ]`, para as distinguir da fala.

**Exemplo — o que perder um som custa:**

```
WEBVTT

00:00:04.000 --> 00:00:07.000
JOÃO: Está tudo calmo por aqui.

00:00:07.500 --> 00:00:09.000
[tiro à distância]

00:00:09.500 --> 00:00:11.000
JOÃO: ...ou talvez não.
```

Sem a *cue* `[tiro à distância]`, a segunda fala do João («...ou talvez não») fica sem sentido para quem não ouve. **A informação-chave da cena estava no som, não na fala.** É exatamente isto que as legendas de acessibilidade não podem deixar cair.

### Identificar quem fala

Sempre que não seja evidente **pela imagem** quem está a falar, identifique o interlocutor. Isto é crítico quando alguém fala **fora do plano**, quando há várias pessoas, ou quando há mudança rápida de interlocutor.

**Exemplo com problema:**

```
00:00:12.000 --> 00:00:15.000
- Trouxeste os documentos?
- Trouxe, estão na mala.
```

**O que corre mal:** com duas pessoas fora do plano, o traço `-` diz que *alguém* mudou, mas não diz **quem**. Se a identidade de quem faz a pergunta for relevante, esta legenda esconde-a.

**Versão melhorada:**

```
00:00:12.000 --> 00:00:14.000
INÊS: Trouxeste os documentos?

00:00:14.200 --> 00:00:15.500
RUI: Trouxe, estão na mala.
```

**O que melhora:** cada fala tem dono e um intervalo próprio, o que resolve ao mesmo tempo a identificação e a sincronização.

### Respeitar o ritmo de leitura

Uma legenda tem de ficar no ecrã tempo suficiente para ser lida, mas sem se atrasar em relação ao som. Como referência prática:

- **Duas linhas** no ecrã, no máximo, de cada vez.
- Linhas relativamente curtas (à volta de 35–40 caracteres) leem-se melhor do que linhas muito longas.
- Um ritmo confortável para leitores adultos ronda as **160 a 180 palavras por minuto**. Acima disto, a pessoa fica «presa» a ler e não olha para a imagem.
- Cada *cue* deve permanecer visível o tempo mínimo para ser lida — mesmo uma legenda muito curta precisa de cerca de **1 segundo**.

Quando o diálogo é rápido, a tentação é encher uma *cue* enorme com muito texto. Resista: **divida** em várias *cues* mais curtas e bem temporizadas. É melhor duas legendas legíveis do que uma ilegível.

### Não tapar informação importante

Por omissão, as legendas surgem na parte inferior do ecrã. Se aí aparecer informação visual relevante (um nome em rodapé, um número de telefone, uma legenda gráfica), **reposicione** a *cue*. O WebVTT permite-o através de definições na linha de tempo:

```
00:00:15.000 --> 00:00:18.000 line:15%
MARIA: Reparem nos valores no rodapé.
```

**O que isto faz de bom:** `line:15%` sobe a legenda para perto do topo, deixando o rodapé visível. A informação da fala e a informação do ecrã passam a coexistir em vez de competirem pelo mesmo espaço.

### Corrigir sempre as legendas automáticas

Muitas plataformas geram legendas automáticas por reconhecimento de voz. São um **ponto de partida útil**, nunca um produto final. Confundem palavras, ignoram pontuação, não identificam interlocutores e nunca descrevem sons que não sejam fala. Publicar legendas automáticas por rever equivale, na prática, a **não** ter legendas acessíveis — e não satisfaz o critério 1.2.2.

### Um apontamento sobre legendas em direto

As legendas em direto (critério 1.2.4) — para transmissões, aulas e webinars ao vivo — obedecem às mesmas cinco propriedades, com o desafio acrescido do **tempo real**: há sempre alguma latência e a precisão tende a ser menor do que no pré-gravado. Produzem-se normalmente por *respeaking* (uma pessoa repete o discurso para um sistema de reconhecimento) ou por estenotipia/legendagem profissional em direto. 

### Erros Comuns

- **Chamar «legendas de acessibilidade» a legendas de tradução.** Traduzir o diálogo sem incluir sons nem identificar quem fala deixa de fora precisamente a informação de que o público-alvo depende.
- **Publicar legendas automáticas sem revisão.** O reconhecimento de voz erra palavras, junta frases e ignora tudo o que não é fala.
- **Usar `kind="subtitles"` para legendas de acessibilidade.** O valor semântico contradiz o conteúdo; o correto é `kind="captions"`.
- **Legendas fora de sincronia.** Texto correto, mas adiantado ou atrasado, confunde tanto como texto errado.
- **Uma *cue* gigante com demasiado texto.** Impossível de ler antes de desaparecer; deve dividir-se em várias.
- **Não identificar quem fala** quando há vozes fora do plano ou várias personagens.
- **Omitir sons relevantes** (o telefone que toca, o tiro à distância) que sustentam a narrativa.
- **Legendas a taparem informação visual** — nomes em rodapé, gráficos, valores no ecrã.
- **Abusar de legendas abertas «queimadas»**, retirando ao utilizador o controlo e a possibilidade de as personalizar, quando um ficheiro de legendas fechadas resolveria.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- **Legendas de acessibilidade ≠ legendas de tradução.** As primeiras destinam-se a quem não ouve o som e incluem diálogo, identificação de quem fala e sons que não são fala; as segundas só traduzem palavras para quem ouve.
- Delas dependem pessoas surdas, com perda auditiva ou surdocegas (via linha braille) — e beneficiam muitas outras em situações do quotidiano.
- Umas boas legendas são **sincronizadas, completas, identificadas, corretas e legíveis**.
- Na web, o caminho recomendado é um ficheiro **WebVTT** ligado ao vídeo com `<track kind="captions" ...>`; o valor `captions` é o que declara corretamente a intenção de acessibilidade.
- **Legendas fechadas** (ficheiro separado, controláveis pelo utilizador) são a regra; **legendas abertas** («queimadas» na imagem) só se justificam onde as faixas não são suportadas.
- Legendas são obrigatórias tanto no **pré-gravado** (1.2.2, Nível A) como **em direto** (1.2.4, Nível AA).
- Legendas automáticas são um rascunho: **reveja sempre**.

### Exercícios Práticos

**Exercício 1 — Legenda ou tradução?**
Para cada faixa, decida se deve ser `kind="captions"` ou `kind="subtitles"` e justifique numa frase:
a) Um documentário em inglês, com faixa em português que traduz a narração e assinala `[trovoada]`.
b) Um filme francês, com faixa em português que traduz apenas os diálogos, para público ouvinte.
c) Um vídeo institucional em português, com faixa em português que inclui `[aplausos]` e identifica os oradores.

**Exercício 2 — Detetar os problemas.**
Analise este *cue* e liste tudo o que está mal, indicando como o corrigiria:

```
WEBVTT

00:00:00.000 --> 00:00:20.000
ola bem vindos hoje vamos falar de acessibilidade obrigado por virem vamos comecar
```

**Exercício 3 — Escrever legendas.**
Escreva um excerto de WebVTT (3 a 4 *cues*) para a seguinte cena, incluindo o som que não é fala e a identificação de quem fala:

> Uma sala silenciosa. Ouve-se uma **campainha à porta**. A CLARA, fora do plano, pergunta «Esperas alguém?». O PEDRO responde «Não…», em tom de estranheza.

**Exercício 4 — Reposicionar.**
Um vídeo mostra, entre os segundos 10 e 13, o número de uma linha de apoio no rodapé, exatamente onde as legendas costumam surgir. Escreva o *cue* correspondente à fala nesse intervalo de forma a **não** tapar o número, e explique o que acrescentou ao código para o conseguir.

**Exercício 5 — Discussão.**
Uma equipa quer publicar um vídeo no site institucional e nas redes sociais. Argumente em que caso faz sentido usar legendas **fechadas** e em que caso pode ser necessário recorrer a legendas **abertas** — e o que se perde ao optar pelas segundas.

