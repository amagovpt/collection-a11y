---
title: Descrição de Informação Visual
layout: default
nav_order: 5
---
# Descrição de Informação Visual

## Introdução

Há informação num vídeo que só existe para os olhos. Um gesto, uma expressão, uma pessoa que entra em silêncio numa sala, uma palavra escrita no ecrã, um gráfico que aparece durante uma explicação. Quem vê o vídeo apanha tudo isto sem esforço. Quem não consegue ver o ecrã fica apenas com o som. E o som, muitas vezes, não conta a história toda.

A **descrição de informação visual**, habitualmente chamada **audiodescrição**, resolve exactamente este problema. É uma narração adicional que descreve, por palavras, aquilo que é importante e que só se percebe a olhar. Essa narração encaixa nas pausas do áudio original, para que a pessoa continue a ouvir os diálogos e os sons normais do vídeo e receba, nos intervalos, a informação visual que lhe faltaria.

> **Analogia: o amigo no cinema**
>
> Imagine que vai ao cinema com um amigo que é cego. Nos momentos de silêncio — antes de alguém falar, ou quando a cena muda — inclina-se e sussurra-lhe ao ouvido: *"Ela abre a gaveta e tira uma fotografia antiga."* Não fala por cima dos diálogos, não descreve tudo, só o essencial para que ele acompanhe. A audiodescrição é este amigo, transformado numa faixa de narração planeada.

Vale a pena fixar já uma distinção que evita muita confusão. As **legendas** existem para quem não consegue *ouvir* o vídeo: transformam o som em texto. A **audiodescrição** existe para quem não consegue *ver* o vídeo: transforma a imagem em som. São sentidos diferentes e problemas diferentes — um vídeo pode precisar de ambos, de um, ou de nenhum.

### Como as Pessoas com Deficiência dependem de Descrição de Informação Visual

Nem toda a gente que beneficia da audiodescrição depende dela da mesma forma:

- **Pessoas cegas** não recebem nenhuma informação do ecrã. Ouvem a banda sonora, mas tudo o que é apenas visual desaparece. Costumam usar um leitor de ecrã e navegar recorrendo a áudio; a audiodescrição é, para elas, a única forma de saber o que está a acontecer visualmente.
- **Pessoas com baixa visão** podem ver formas e movimento, mas perder detalhes: quem é quem, uma expressão facial, texto pequeno no ecrã. Para estas pessoas a audiodescrição preenche as lacunas.
- **Pessoas com certas dificuldades cognitivas** podem beneficiar de ter o que acontece no ecrã dito de forma clara e explícita, em vez de terem de o interpretar sozinhas.
- **Situacionalmente**, também beneficia quem está a "ver" um vídeo sem olhar para o ecrã — por exemplo, a ouvir enquanto conduz.

O ponto central é este: **estas pessoas conseguem ouvir o vídeo, mas não conseguem ver o que ele mostra.** Se a informação importante estiver só na imagem, ela perde-se por completo. A não ser que alguém a diga em voz alta.

> **Exemplo — o que se perde sem descrição**
>
> Um vídeo de culinária. O apresentador, em silêncio, levanta dois frascos, aponta para um deles e faz que sim com a cabeça. Depois continua a falar.
>
> Quem vê, percebe qual foi o ingrediente escolhido. Quem não vê, ouve apenas alguns segundos de silêncio seguidos da conversa, sem saber o que se passou.
>
> Com audiodescrição, o silêncio passa a conter: *"O apresentador mostra dois frascos — canela à esquerda, noz-moscada à direita — e escolhe a canela."*
>
> **Análise:** a descrição não inventa nada nem interpreta intenções; limita-se a dizer o que qualquer pessoa veria. Encaixa exactamente no momento de silêncio, sem atropelar a fala que vem a seguir. Sem ela, o momento fica incompreensível para quem não vê.

### Requisitos de Acessibilidade para Descrição de Informação Visual

A regra prática de partida é simples:

> **Só é preciso descrever a informação visual que ainda não é transmitida pelo áudio.**

Se a banda sonora já diz tudo o que é importante ver (porque o narrador descreve o que mostra, ou porque as personagens dizem em voz alta o que estão a fazer) o vídeo já é acessível a quem não o vê, e não é preciso acrescentar descrição. A audiodescrição serve para cobrir aquilo que *falta* no áudio, não para duplicar o que já lá está.

Há dois níveis de audiodescrição, conforme o espaço disponível:

- **Audiodescrição padrão** — a descrição encaixa nas pausas naturais que já existem no áudio original. É a situação mais comum e mais simples.
- **Audiodescrição alargada (ou expandida)** — quando as pausas naturais são demasiado curtas para descrever tudo o que é importante, o vídeo *pausa temporariamente* para dar tempo à narração e retoma depois. Usa-se em conteúdos muito densos de informação visual (por exemplo, um vídeo educativo cheio de diagramas).

Quanto ao enquadramento nos critérios de acessibilidade, importa reter três ideias:

- Ao **nível A**, para vídeo pré-gravado com informação visual essencial, é preciso fornecer **ou** uma audiodescrição **ou** uma alternativa completa em texto. É uma escolha.
- Ao **nível AA** — que corresponde à baseline legal em Portugal (Decreto-Lei n.º 83/2018, alinhado com a EN 301 549 e as WCAG 2.1 AA) — a **audiodescrição passa a ser exigida** para o vídeo pré-gravado. Deixa de ser uma alternativa entre outras e torna-se um requisito.
- A **audiodescrição alargada** e a **alternativa completa em texto** correspondem a exigências mais elevadas (nível AAA), acima da baseline legal, mas são boas práticas relevantes para conteúdos exigentes.

## Técnicas de Codificação

Há três formas principais de fazer chegar a descrição ao utilizador. Não são alternativas exclusivas. A escolha depende do conteúdo e das ferramentas disponíveis. 

### 1. Versão do vídeo com descrição integrada

A abordagem mais robusta e mais compatível: gerar uma segunda versão do vídeo em que a narração de descrição já está misturada na banda sonora. Disponibiliza-se essa versão como alternativa (por exemplo, um botão "Ver com audiodescrição") ou como faixa de áudio adicional.

```html
<p>
  <a href="documentario.mp4">Ver documentário</a> |
  <a href="documentario-audiodescricao.mp4">Ver documentário com audiodescrição</a>
</p>
```

**Análise:** funciona em qualquer reprodutor e em qualquer navegador, porque a descrição já faz parte do ficheiro de áudio — não depende de suporte técnico especial. A desvantagem é o esforço de produção (é preciso gravar e misturar) e o facto de o utilizador ter de escolher uma versão à partida. Ainda assim, é frequentemente a opção mais segura.

### 2. Faixa de texto de descrição — `<track kind="descriptions">`

O HTML permite associar ao vídeo uma faixa de **texto** com descrições cronometradas, num ficheiro WebVTT, através do elemento `<track>` com `kind="descriptions"`. A ideia é que o leitor de ecrã (ou o reprodutor) leia esse texto em voz sintetizada nos momentos indicados.

```html
<video controls>
  <source src="documentario.mp4" type="video/mp4">
  <track kind="captions"     src="legendas-pt.vtt"   srclang="pt" label="Português">
  <track kind="descriptions" src="descricao-pt.vtt"  srclang="pt" label="Descrição">
</video>
```

O ficheiro `descricao-pt.vtt` contém as descrições e os tempos em que devem ser lidas:

```
WEBVTT

00:00:04.000 --> 00:00:07.000
Uma mulher abre a porta de um armazém abandonado.

00:00:15.000 --> 00:00:18.000
No quadro branco, lê-se: "Reunião às 15h".
```

**Análise:** é uma solução leve — texto simples, fácil de rever e de traduzir. Mas tem um problema prático importante: **o suporte nativo dos navegadores para `kind="descriptions"` é muito fraco.** A maioria dos navegadores não converte automaticamente estas descrições em voz. Para que funcionem de forma fiável, é preciso um reprodutor preparado para as ler. Por isso, esta técnica não deve ser usada isoladamente sem testar se, na prática, a descrição chega mesmo a ser ouvida. Repare-se ainda no exemplo: a segunda descrição trata o *texto que aparece no ecrã* como informação visual — porque é. Texto que só está na imagem também precisa de ser dito.

### 3. Faixas de áudio múltiplas

Alguns formatos e reprodutores permitem incluir, no mesmo vídeo, mais do que uma faixa de áudio: a normal e uma faixa já com descrição. O utilizador escolhe qual ouvir, tal como escolheria um idioma diferente.

**Análise:** combina o melhor das duas abordagens anteriores. A descrição é áudio real (bem produzido, com voz humana se se quiser) e o utilizador liga-a e desliga-a sem trocar de página. Em contrapartida, depende de o formato do vídeo e o reprodutor suportarem seleção de faixas de áudio, o que nem sempre acontece.

## Recomendações para Conteúdo Acessível

Escrever uma boa descrição é um trabalho cuidado. A tecnologia entrega a narração; a qualidade decide se ela ajuda ou atrapalha. Princípios a seguir:

- **Descrever só o que importa para compreender.** O objectivo não é narrar tudo, é dar à pessoa a informação de que precisa para acompanhar. Detalhes decorativos irrelevantes só ocupam as pausas e cansam.
- **Ser objectivo, não interpretar.** Diga o que se vê, não o que acha que significa. *"Franze a testa e afasta o olhar"* é melhor do que *"fica magoada"* — a segunda versão tira à pessoa o direito de tirar as suas próprias conclusões.
- **Nunca falar por cima do essencial.** A descrição encaixa nas pausas; não atropela diálogos nem sons importantes (uma explosão, uma campainha que faz avançar a história). Se não há espaço, considere a descrição alargada.
- **Ser conciso e usar o presente.** Frases curtas, no presente ("ela entra", "ele aponta"), acompanham melhor o ritmo do vídeo.
- **Ler o texto que aparece no ecrã.** Títulos, legendas gravadas na imagem, nomes de intervenientes, informação em diapositivos, créditos relevantes — tudo isto é informação visual que tem de ser dita.
- **Identificar quem age ou fala** quando o áudio não deixa claro. Se três pessoas estão em cena e uma delas se levanta, diga qual.
- **Acompanhar o tom do conteúdo.** A descrição de uma comédia e a de um documentário sério não soam da mesma maneira; o registo deve encaixar.

Sobre *quando* pensar na descrição: o momento ideal é **desde o início da produção**, integrando-a no guião, para que haja pausas suficientes e não seja preciso encaixá-la à pressa no fim. Esse planeamento é aprofundado na secção *Boas Práticas de Produção* — aqui basta reter que a descrição corre muito melhor quando é prevista, não remendada.

> **Exemplo bom**
>
> Cena: alguém procura algo numa gaveta, em silêncio, e encontra-o. Pausa de 3 segundos no áudio.
>
> Descrição: *"Abre a gaveta, remexe entre papéis e tira uma chave pequena."*
>
> **Análise:** cabe na pausa, é objectiva (não diz "finalmente encontra o que queria"), está no presente e conta exactamente o que faria falta a quem não vê. Nada a mais, nada a menos.

> **Exemplo mau**
>
> Para a mesma cena: *"Nesta cena emocionante, a nossa protagonista, claramente desesperada e à beira das lágrimas, procura freneticamente a chave que finalmente lhe vai mudar a vida, enquanto o realizador nos mostra o seu talento com um belíssimo enquadramento."*
>
> **Análise:** falha em quase tudo. É demasiado longa para caber na pausa (vai sobrepor-se ao que vem a seguir), interpreta emoções e intenções em vez de descrever, e comenta a realização — informação que não ajuda a pessoa a acompanhar a história. Uma descrição assim atrapalha mais do que ajuda.

### Erros Comuns

- **Não fornecer qualquer descrição** num vídeo cuja informação importante é visual. É o erro base: presume-se que a banda sonora chega, quando não chega.
- **Achar que legendas ou transcrição resolvem.** Servem quem não *ouve*; não substituem a descrição para quem não *vê*. São o sentido errado. (Ver *Legendas* e *Transcrições*.)
- **Falar por cima de diálogos ou sons importantes**, tornando o vídeo mais confuso em vez de mais claro.
- **Descrever demais.** Encher todas as pausas com pormenores decorativos sobrecarrega e distrai do essencial.
- **Usar linguagem subjectiva ou interpretativa** ("parece triste", "de forma ameaçadora") em vez de descrever o que se vê.
- **Esquecer o texto no ecrã** — títulos, avisos, informação em diapositivos, nomes — deixando lacunas invisíveis a quem depende do áudio.
- **Confiar só na faixa `kind="descriptions"` sem testar.** Como o suporte nativo é fraco, a descrição pode simplesmente nunca ser lida. É preciso verificar num reprodutor que a suporte.
- **Aceitar descrições geradas automaticamente como suficientes.** Ferramentas automáticas erram, descrevem o irrelevante e falham o essencial. Servem, quando muito, de rascunho a rever por uma pessoa.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A **descrição de informação visual (audiodescrição)** transmite, por palavras, aquilo que só se percebe a ver, para quem não consegue ver o ecrã.
- É o **espelho das legendas**: as legendas servem quem não ouve, a audiodescrição serve quem não vê.
- Só é preciso descrever **o que o áudio ainda não transmite**. Se a banda sonora já diz tudo, não é necessária descrição adicional.
- Existe descrição **padrão** (encaixa nas pausas existentes) e **alargada** (o vídeo pausa para dar tempo à narração).
- Ao **nível AA**, baseline legal em Portugal, a audiodescrição é **exigida** para vídeo pré-gravado.
- Tecnicamente, pode entregar-se como **versão com descrição integrada** (mais robusta), **faixa de texto `kind="descriptions"`** (leve, mas de suporte frágil) ou **faixas de áudio múltiplas**.
- Uma boa descrição é **objectiva, concisa, encaixa nas pausas e inclui o texto que aparece no ecrã**.

### Exercícios Práticos

1. **Identificar a lacuna visual.** Escolha um vídeo curto que conheça (um anúncio, um tutorial). Feche os olhos e ouça-o do início ao fim. Anote todos os momentos em que ficou sem perceber o que estava a acontecer. Esses momentos são, precisamente, os que precisam de descrição.

2. **Escrever para as pausas.** Para um trecho de 30 segundos, marque onde há pausas no áudio e escreva uma descrição que caiba em cada uma. Verifique, lendo em voz alta e a cronometrar, se cada descrição termina antes de a fala seguinte começar.

3. **Reescrever uma má descrição.** Pegue no "exemplo mau" desta secção e reescreva-o de forma objectiva, concisa e no presente. Compare com a sua versão do exercício 2.

4. **Não esquecer o texto no ecrã.** Encontre um vídeo com informação escrita na imagem (um título, um número de telefone, um aviso). Escreva as descrições que dizem esse texto em voz alta, nos momentos certos.

5. **Ligar a faixa de descrição.** Partindo de um elemento `<video>` simples, acrescente uma faixa `<track kind="descriptions">` com um ficheiro WebVTT de duas ou três descrições cronometradas. Depois, teste num reprodutor que suporte descrições e confirme se elas são efectivamente lidas — e reflicta sobre o que faria se o reprodutor não as suportasse.

6. **Padrão ou alargada?** Dado um vídeo educativo com muitos diagramas e pausas curtíssimas, argumente se deveria usar descrição padrão ou alargada, e justifique com base no espaço disponível nas pausas.
