# Transcrições

## Introdução

Uma **transcrição** é a versão em texto de um conteúdo áudio ou audiovisual. Por outras palavras, é tudo o que se ouve, e, quando necessário, também o que se vê, passado para palavras que qualquer pessoa pode ler ao seu próprio ritmo.

A característica que melhor define uma transcrição é aquilo que a distingue das legendas: **a transcrição não está sincronizada com o vídeo**. Não aparece nem desaparece ao ritmo da imagem. É um documento completo e independente, que pode ser lido, pesquisado, imprimido ou enviado para uma linha braille sem sequer ser preciso carregar no botão "reproduzir".

> **Analogia:** pense num podcast de culinária.
>
> - As **legendas** são como palavras que surgem no ecrã, uma frase de cada vez, exatamente quando o cozinheiro as diz.
> - A **transcrição** é a receita escrita por inteiro: pode lê-la do início ao fim, procurar "quanto sal", imprimi-la e levá-la para a cozinha — tudo sem ligar o vídeo.

Existem dois tipos de transcrição, e a diferença entre eles é central para todo esta secção:

- **Transcrição básica** — inclui o diálogo/narração e os sons importantes que não são fala (por exemplo, *[aplausos]* ou *[música tensa]*). É suficiente para conteúdo **só de áudio**, como um podcast.
- **Transcrição descritiva** — acrescenta a descrição da **informação visual importante** (quem entra em cena, o que acontece no ecrã, texto que aparece na imagem). É o que permite compreender totalmente um **vídeo** apenas através do texto.

Ao longo da secção vamos ver quem depende destas transcrições, como as disponibilizar corretamente numa página web e como escrever uma transcrição que seja de facto útil.

> **Nota de âmbito:** a decisão sobre *quando* uma transcrição é a alternativa certa (em vez de, ou além de, legendas ou audiodescrição) é tratada na secção **Escolher a Alternativa Certa**. A forma de *descrever* bem a informação visual é aprofundada na secção **Descrição de Informação Visual**. Aqui concentramo-nos na própria transcrição: o que é, como a codificar e como a tornar boa.

### Como as Pessoas com Deficiência dependem de Transcrições

As legendas resolvem muitas situações, mas a transcrição é a solução preferida, e, por vezes, a única possível, para vários públicos.

**Pessoas surdas ou com perda auditiva que preferem ler ao seu ritmo.**
As legendas passam à velocidade do vídeo. Quem lê mais devagar, ou quem quer voltar atrás numa parte técnica, fica em desvantagem. Com uma transcrição, a pessoa controla o ritmo: pára, relê, salta.

**Pessoas surdocegas.**
Este é o caso mais importante de todos. Uma pessoa surdocega **não vê o vídeo nem ouve o áudio**. As legendas no ecrã são-lhe inúteis, porque não as consegue ver. A audiodescrição é-lhe inútil, porque não a consegue ouvir. O **único** caminho que lhe resta é o texto: uma **transcrição descritiva** enviada para uma **linha braille**, que ela lê com os dedos. Para esta pessoa, a transcrição não é uma comodidade. É a diferença entre aceder e não aceder ao conteúdo.

**Pessoas com deficiências cognitivas ou dificuldades de leitura/atenção.**
Um texto estático, que não desaparece, permite reler, procurar e digerir a informação sem a pressão do tempo.

**Muitas outras pessoas, sem qualquer deficiência.**
A transcrição é procurável pelos motores de busca, permite copiar uma citação, consultar rapidamente um conteúdo longo, ou seguir um tutorial num ambiente onde não se pode ter som (por exemplo, num escritório aberto). Isto reforça uma ideia recorrente na acessibilidade: o que resolve o problema de alguns beneficia toda a gente.

### Requisitos de Acessibilidade para Transcrições

Do ponto de vista normativo, a transcrição é uma das formas de cumprir vários critérios das WCAG. Nesta fase interessa-nos apenas perceber **que situações exigem transcrição** e **que tipo de transcrição** cada uma pede. De forma simplificada:

- **Conteúdo só de áudio** (ex.: podcast): precisa de uma **transcrição básica** que dê acesso a todo o conteúdo falado e aos sons relevantes. Isto corresponde ao critério **1.2.1 (Nível A)**.
- **Conteúdo só de vídeo, sem som** (ex.: uma animação silenciosa que demonstra um processo): precisa de uma alternativa em texto que descreva o que se vê (ou de uma faixa de áudio equivalente). Também abrangido pelo **1.2.1 (Nível A)**.
- **Vídeo com áudio** (o caso mais comum): aqui a transcrição entra como **alternativa multimédia completa**, isto é, uma **transcrição descritiva** que junta o diálogo e a descrição do visual. Uma alternativa completa pode ser usada para cumprir o **1.2.3 (Nível A)** e é o que satisfaz o critério mais exigente **1.2.8 (Nível AAA)**.

A ideia-chave a reter é simples: **quanto mais informação estiver "presa" na imagem, mais a transcrição tem de ser descritiva** para ser equivalente ao original.

---

## Técnicas de Codificação

Ter uma boa transcrição não basta: ela tem de estar **disponível de forma acessível** na página. Uma transcrição perfeita escondida onde ninguém a encontra é como não existir. Vejamos as técnicas para a disponibilizar bem.

### Opção 1 — Transcrição na própria página, junto ao vídeo

A abordagem mais robusta é colocar a transcrição em **texto real**, na mesma página, imediatamente a seguir ao leitor de multimédia.

```html
<video controls src="entrevista.mp4">
  <track kind="captions" src="entrevista-pt.vtt" srclang="pt" label="Português">
</video>

<h2>Transcrição da entrevista</h2>
<p><strong>Entrevistadora:</strong> Bom dia. Pode explicar-nos o que é a acessibilidade web?</p>
<p><strong>Convidado:</strong> Com certeza. É a prática de garantir que os sítios web podem ser usados por todas as pessoas…</p>
<p><em>[o convidado aponta para um diagrama no ecrã com três pilares]</em></p>
```

**O que funciona bem neste exemplo:**

- A transcrição é **texto real**, portanto é lida por leitores de ecrã, enviada para linhas braille, pesquisável e selecionável.
- Está **junto ao vídeo**, com um título (`<h2>`) claro que a identifica.
- Cada intervenção **identifica quem fala** e há uma marcação da informação visual (o diagrama), o que a torna uma transcrição descritiva.

### Opção 2 — Transcrição recolhível (expansível)

Se a transcrição é longa e não quer que ocupe muito espaço, pode escondê-la num bloco expansível com o elemento nativo `<details>`. Este elemento é acessível por omissão: pode ser aberto e fechado com o teclado e o seu estado é comunicado às tecnologias de apoio.

```html
<details>
  <summary>Ver transcrição completa</summary>
  <h3>Transcrição</h3>
  <p><strong>Narrador:</strong> Bem-vindos ao nosso tutorial…</p>
  <!-- restante transcrição -->
</details>
```

**O que funciona bem:**
- O `<summary>` funciona como um botão real, focável e operável por teclado, sem ser preciso escrever JavaScript.
- O texto do `<summary>` — "Ver transcrição completa" — diz claramente o que vai acontecer.

**O que pode correr mal:**

- Se, em vez de `<details>`, se construir o mesmo efeito com uma `<div>` clicável e JavaScript, é fácil esquecer o foco por teclado e o anúncio do estado (aberto/fechado). Havendo uma solução nativa que já resolve isto, prefira-a.

### Opção 3 — Ligação para a transcrição

Quando a transcrição vive noutra página (ou é muito extensa), disponibilize uma **ligação clara e explícita**, colocada junto ao vídeo.

```html
<!-- BOM -->
<a href="transcricao-webinar.html">Transcrição do webinar "Introdução à Acessibilidade"</a>

<!-- MAU -->
<p>Transcrição disponível <a href="transcricao-webinar.html">aqui</a>.</p>
```

**Comparação:**

- Na versão **boa**, o texto da ligação descreve o destino. Um utilizador de leitor de ecrã que navegue pela lista de ligações da página percebe imediatamente para onde vai.
- Na versão **má**, a ligação diz apenas "aqui". Fora de contexto, é impossível saber o que é.

### Estruturar o texto da transcrição

Uma transcrição não é um bloco de texto único e interminável. Deve usar a **estrutura semântica do HTML** para se tornar navegável:

```html
<h2>Transcrição — Reunião de Câmara, 3 de março</h2>

<h3>Abertura</h3>
<p><strong>Presidente:</strong> Declaro aberta a sessão…</p>

<h3>Ponto 1 — Orçamento</h3>
<p><strong>Vereador Silva:</strong> Relativamente ao orçamento…</p>
```

**O que funciona bem:**

- Os títulos (`<h2>`, `<h3>`) permitem que um leitor de ecrã salte diretamente para a secção "Ponto 1 — Orçamento", tal como uma pessoa normovisual percorreria os cabeçalhos com os olhos.
- A identificação do orador com `<strong>` dá destaque visual **sem** inventar significado semântico que não existe. Se quisermos ir mais longe, os diálogos podem ser marcados com listas de definição, associando cada orador (`<dt>`) à sua fala (`<dd>`).

---

## Recomendações para Conteúdo Acessível

Uma transcrição só é útil se for **fiel, completa e legível**. Estas recomendações ajudam a lá chegar.

**1. Inclua tudo o que se ouve — não só as palavras.**
Além do diálogo, registe os sons com significado: *[campainha toca]*, *[risos do público]*, *[música alegre]*. Quem não ouve precisa de saber que estes sons aconteceram, porque muitas vezes fazem parte da mensagem.

**2. Identifique sempre quem está a falar.**
Numa conversa com várias pessoas, sem a indicação do orador, o texto vira um emaranhado impossível de seguir.

> **Exemplo mau:**
> Então, o que achaste?
> Achei ótimo.
> A sério? A mim não me convenceu.
>
> **Exemplo bom:**
> **Ana:** Então, o que achaste?
> **Bruno:** Achei ótimo.
> **Ana:** A sério? A mim não me convenceu.
>
> **Análise:** no primeiro caso é impossível saber quem discorda de quem. No segundo, a conversa recupera todo o sentido. A identificação do orador é barata de fazer e essencial para a compreensão.

**3. Numa transcrição descritiva, descreva o visual importante — mas só o importante.**
Se o vídeo mostra algo que o áudio não explica (um gráfico, uma ação, uma expressão facial decisiva, texto no ecrã), essa informação tem de estar no texto. O objetivo é que quem lê a transcrição fique a saber o mesmo que quem vê o vídeo. 

**4. Coloque a transcrição perto do conteúdo e torne-a fácil de encontrar.**
A transcrição deve estar imediatamente identificável a partir do vídeo. Ninguém deve ter de procurar no rodapé do site ou adivinhar onde ela está.

**5. Limpe as transcrições geradas automaticamente.**
As ferramentas automáticas são um bom ponto de partida, mas produzem erros, trocam nomes próprios e não identificam oradores nem sons. Uma transcrição automática **não revista** raramente cumpre o critério de ser uma alternativa fiel.

**6. Garanta que a transcrição é texto acessível.**
Deve ser texto real e não uma imagem de texto (um *screenshot* de um documento), nem um PDF digitalizado sem camada de texto. Se for texto real, funciona em qualquer leitor de ecrã e em qualquer linha braille.

### Erros Comuns

- **Confundir transcrição com legendas.** As legendas estão sincronizadas com o vídeo; a transcrição é um documento autónomo e não sincronizado. Fornecer apenas legendas **não** substitui a transcrição para os públicos que dependem de leitura ao seu ritmo ou de braille.
- **Colar as legendas concatenadas e chamar-lhe transcrição.** Juntar as linhas do ficheiro de legendas produz um texto sem identificação de oradores, sem descrição do visual e, muitas vezes, cortado a meio das frases. É melhor do que nada, mas não é uma boa transcrição, sobretudo se o vídeo tiver informação visual relevante.
- **Fornecer só uma transcrição básica para um vídeo cheio de informação visual.** Se o essencial está na imagem (por exemplo, uma demonstração passo a passo), uma transcrição que só tem o áudio deixa de fora o mais importante. Nesse caso é preciso uma transcrição **descritiva**.
- **Publicar transcrição automática sem revisão.** Nomes errados, pontuação inexistente e ausência de oradores tornam o texto pouco fiável.
- **Transcrição como imagem ou PDF inacessível.** Um *screenshot* de texto ou um PDF digitalizado sem camada de texto não são lidos por tecnologias de apoio. Na prática, para quem delas depende, a transcrição não existe.
- **Texto de ligação vago.** "Clique aqui" para chegar à transcrição obriga o utilizador a adivinhar o destino.
- **Transcrição escondida.** Estar disponível "algalgures no site" não chega; tem de estar associada e próxima do conteúdo a que se refere.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A **transcrição** é a versão em texto de um conteúdo áudio/audiovisual, **não sincronizada** e lida ao ritmo do utilizador — ao contrário das legendas.
- Há dois tipos: **básica** (fala + sons relevantes, suficiente para áudio) e **descritiva** (acrescenta a informação visual, necessária para vídeo).
- A transcrição é a **única via de acesso para pessoas surdocegas**, através da leitura em **linha braille**; e beneficia muitos outros públicos, com e sem deficiência.
- Deve ser **texto real**, **estruturado** com títulos, com **oradores identificados** e disponibilizada **junto ao conteúdo** (na página, num bloco `<details>`, ou por ligação clara).
- Transcrições **automáticas exigem revisão**; imagens de texto e PDF digitalizados **não** são transcrições acessíveis.

### Exercícios Práticos

**Exercício 1 — Identificar o tipo necessário**
Para cada conteúdo, indique se basta uma transcrição **básica** ou se é preciso uma transcrição **descritiva**, e justifique:
a) Um podcast de entrevistas, só áudio.
b) Um tutorial em vídeo onde a formadora executa passos no ecrã enquanto os narra.
c) Uma animação silenciosa que ilustra o ciclo da água, sem qualquer som.

**Exercício 2 — Corrigir uma transcrição**
Melhore o excerto abaixo, aplicando as recomendações da secção (identificação de oradores, sons relevantes, informação visual):

> Bom dia a todos. Hoje vamos falar de acessibilidade. Como podem ver neste gráfico, os números subiram. Muito interessante, não achas? Sem dúvida.

**Exercício 3 — Disponibilizar na página**
Escreva o HTML para disponibilizar uma transcrição longa de um webinar, escondida por omissão mas acessível por teclado, com um título e um controlo de abertura com texto significativo. Explique por que razão escolheu o elemento que usou.

**Exercício 4 — Caça ao erro**
Um colega disponibilizou a transcrição de um vídeo institucional como uma imagem PNG exportada de um documento, ligada com o texto "aqui". Enumere os problemas de acessibilidade desta solução e proponha uma alternativa.

**Exercício 5 — Reflexão**
Explique, por palavras suas, por que motivo as legendas não substituem a transcrição para uma pessoa surdocega. Que tipo de transcrição é indispensável e através de que dispositivo é lida?

