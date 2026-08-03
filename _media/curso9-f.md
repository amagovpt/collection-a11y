# Língua Gestual

## Introdução

Imagine que cresceu a comunicar com a sua família numa língua e que, mais tarde, alguém lhe entrega um filme legendado noutra língua diferente. Consegue decifrar algumas palavras, mas o esforço é grande e as piadas, as emoções e os detalhes escapam-lhe. É mais ou menos isto que acontece a muitas pessoas surdas quando lhes oferecemos apenas legendas.

Este é o ponto de partida desta secção, e é também o equívoco mais comum sobre a acessibilidade multimédia: assumir que, se um vídeo tem legendas, então está "tratado" para as pessoas surdas. Não está. As legendas são fundamentais e resolvem muitas situações, mas dependem de saber ler bem a língua escrita. E, para uma parte importante da comunidade surda, a língua escrita **não é** a primeira língua.

A primeira língua é a **língua gestual**. Em Portugal, é a **Língua Gestual Portuguesa (LGP)**.

> **Nota importante sobre terminologia**
> A LGP é uma língua natural e completa, com gramática, sintaxe e vocabulário próprios. **Não é** "português feito com as mãos" nem uma tradução gesto-a-gesto do português. A ordem das frases, a construção do significado e até a forma como o tempo verbal é expresso são diferentes do português falado ou escrito. Da mesma forma, a LGP é diferente da língua gestual americana (ASL), da espanhola (LSE) ou de qualquer outra. Não existe uma língua gestual "universal".

Este ponto é essencial para o resto da secção: como a LGP é uma língua distinta do português, ler legendas em português obriga a pessoa surda a trabalhar numa **segunda língua**. Fornecer interpretação em LGP é, para muitas pessoas, dar-lhes acesso ao conteúdo na sua **língua materna**.

### Como as Pessoas com Deficiência dependem de Língua Gestual

Nem todas as pessoas surdas usam língua gestual, e é importante perceber porquê, para não cairmos em soluções "tamanho único".

**Pessoas surdas de nascença ou com surdez pré-linguística** (que ficaram surdas antes de adquirir a língua falada) muitas vezes têm a língua gestual como **primeira língua**. Cresceram a pensar e a comunicar em LGP. Para estas pessoas, o português escrito foi aprendido depois, como uma segunda língua, e o grau de fluência na leitura varia muito de pessoa para pessoa. Para muitas, seguir legendas rápidas é cansativo e deixa-as a perder informação.

**Pessoas que ensurdeceram mais tarde na vida** (por exemplo, por idade ou doença) já dominavam o português falado e escrito. Estas pessoas costumam preferir **legendas** e podem nem sequer conhecer LGP. Para elas, a interpretação em língua gestual não acrescenta grande coisa.

Daqui tiramos uma conclusão prática: **a língua gestual e as legendas servem pessoas diferentes e não se substituem uma à outra.** São complementares.

Além do acesso à informação "literal", a língua gestual transporta algo que as legendas dificilmente conseguem: **a expressão e a emoção**. Na LGP, a expressão facial, a intensidade do gesto e os movimentos do corpo não são "decoração" — fazem parte da gramática e do significado. Uma sobrancelha levantada pode transformar uma afirmação numa pergunta.

> **Analogia**
> Pense na diferença entre ler a letra de uma canção num papel e ouvir alguém a cantá-la. A letra dá-lhe as palavras; a interpretação dá-lhe o ritmo, a emoção e a intenção. As legendas são a letra no papel. A interpretação em LGP é a canção cantada.
>
> **O que esta analogia mostra:** a interpretação em língua gestual não é apenas "as legendas noutro formato." Transmite camadas de significado (tom, ênfase, emoção) que o texto plano perde. Por isso é que, para conteúdo emocional, narrativo ou dirigido à comunidade surda, a LGP faz uma diferença enorme.

### Requisitos de Acessibilidade para Língua Gestual

Aqui é preciso ser rigoroso, porque há muita confusão sobre "o que é obrigatório".

Nas WCAG (as diretrizes internacionais de acessibilidade), o critério que trata diretamente deste tema é apenas um:

- **1.2.6 Língua Gestual (Pré-gravado)** — Nível **AAA**: para todo o conteúdo áudio pré-gravado em multimédia sincronizado (vídeo com som), é fornecida interpretação em língua gestual.

Repare no nível: **AAA**. Isto tem uma consequência prática importante em Portugal. O enquadramento legal (Decreto-Lei n.º 83/2018 e a norma EN 301 549) tem como base o cumprimento das WCAG ao nível **AA**. Ou seja, a interpretação em língua gestual **está acima do mínimo legal de conformidade AA** e não é, por si só, exigida por esse baseline.

Não conclua daqui que a língua gestual é "opcional" ou pouco importante. Significa apenas que:

1. **Do ponto de vista da conformidade AA**, um vídeo pode estar conforme com legendas (1.2.2) e audiodescrição (1.2.5) sem interpretação em LGP.
2. **Do ponto de vista da inclusão real**, para muitos serviços — sobretudo do setor público, de saúde, educação, emergência ou conteúdos dirigidos à comunidade surda — a interpretação em LGP é o que faz a diferença entre "tecnicamente conforme" e "genuinamente acessível".

Vale também a pena lembrar o contexto nacional: a **Língua Gestual Portuguesa está reconhecida na Constituição da República Portuguesa** (artigo 74.º) como meio de expressão e de acesso à educação e à igualdade de oportunidades das pessoas surdas. Este reconhecimento reforça a expectativa de que serviços públicos disponibilizem informação em LGP, mesmo quando as WCAG a colocam apenas ao nível AAA.

> **Em resumo:** conheça a distinção. Quando alguém disser "o vídeo já é acessível porque tem legendas", saiba explicar que as legendas cumprem o critério AA de legendas, mas que a interpretação em LGP é uma camada adicional (AAA) dirigida a um público diferente, e que em muitos contextos portugueses é fortemente recomendada.

---

## Técnicas de Codificação

A interpretação em LGP é, do ponto de vista técnico, **um vídeo de uma pessoa a interpretar**, que tem de estar **sincronizado** com o conteúdo principal. A questão de programação é: como o disponibilizamos?

Existem três abordagens principais. Vamos ver cada uma com exemplos.

### Abordagem 1 — Intérprete embutido no próprio vídeo ("gravado por cima")

Nesta abordagem, o intérprete é gravado e montado dentro do vídeo original, tipicamente num canto (formato *picture-in-picture*). O vídeo é depois exportado como um único ficheiro.

```html
<video controls>
  <source src="apresentacao-com-lgp.mp4" type="video/mp4">
  <track kind="captions" src="apresentacao-pt.vtt" srclang="pt" label="Português">
</video>
```

**O que funciona bem:** é a abordagem mais simples de publicar. Não há sincronização a gerir com código. A interpretação já está "colada" à imagem. Funciona em qualquer leitor de vídeo.

**O que funciona mal:** o intérprete está **sempre visível** e não pode ser desligado por quem não precisa dele. Além disso, se o intérprete estiver num canto pequeno, é difícil ampliá-lo e uma interpretação em LGP só é útil se as mãos, o rosto e o tronco forem bem visíveis. É a opção mais "rígida".

### Abordagem 2 — Vídeo de interpretação separado e sincronizado (*picture-in-picture* controlável)

Aqui temos **dois vídeos**: o principal e o da interpretação. Um pouco de código mantém-nos sincronizados e permite ao utilizador ligar/desligar ou redimensionar a janela do intérprete.

```html
<div class="reprodutor">
  <video id="principal" controls>
    <source src="apresentacao.mp4" type="video/mp4">
    <track kind="captions" src="apresentacao-pt.vtt" srclang="pt" label="Português">
  </video>

  <video id="lgp" muted aria-label="Interpretação em Língua Gestual Portuguesa">
    <source src="apresentacao-lgp.mp4" type="video/mp4">
  </video>

  <button id="alternar-lgp" aria-pressed="true">
    Ocultar interpretação em LGP
  </button>
</div>
```

```javascript
const principal = document.getElementById('principal');
const lgp = document.getElementById('lgp');
const botao = document.getElementById('alternar-lgp');

// Manter os dois vídeos sincronizados
principal.addEventListener('play', () => lgp.play());
principal.addEventListener('pause', () => lgp.pause());
principal.addEventListener('seeked', () => {
  lgp.currentTime = principal.currentTime;
});

// Permitir ligar/desligar a interpretação
botao.addEventListener('click', () => {
  const visivel = lgp.hidden === false;
  lgp.hidden = visivel;
  botao.setAttribute('aria-pressed', String(!visivel));
  botao.textContent = visivel
    ? 'Mostrar interpretação em LGP'
    : 'Ocultar interpretação em LGP';
});
```

**O que funciona bem:** dá controlo ao utilizador. Quem precisa da interpretação ativa-a; quem não precisa desliga-a. O vídeo do intérprete pode ser servido em melhor qualidade e, com CSS, ampliado. O botão comunica o seu estado a tecnologias de apoio através de `aria-pressed`.

**O que funciona mal (se mal feito):** a sincronização entre dois vídeos é frágil. Se um dos ficheiros carregar mais devagar, podem "descolar-se". É preciso testar em ligações lentas e tratar o *buffering*. Note também que o vídeo de LGP está `muted`: só um deve produzir som, para não haver duas faixas de áudio a sobrepor-se.

### Abordagem 3 — Versão alternativa com interpretação, ligada a partir do conteúdo principal

Em vez de integrar tudo num só reprodutor, oferece-se uma **versão inteiramente interpretada** como alternativa acessível, claramente ligada a partir do conteúdo original.

```html
<figure>
  <video controls>
    <source src="informacao-servico.mp4" type="video/mp4">
    <track kind="captions" src="informacao-servico-pt.vtt" srclang="pt" label="Português">
  </video>
  <figcaption>
    <a href="informacao-servico-lgp.html">
      Ver esta informação com interpretação em Língua Gestual Portuguesa
    </a>
  </figcaption>
</figure>
```

**O que funciona bem:** é robusto e simples de manter. Cada vídeo é independente, sem sincronização a gerir. É uma boa opção quando a interpretação foi produzida à parte ou quando o vídeo principal não pode ser reeditado.

**O que funciona mal:** obriga a pessoa a sair do fluxo principal e a "escolher a outra versão", o que é menos integrado. A ligação tem de ser **explícita e fácil de encontrar**. Se estiver escondida no fundo da página, é como não existir.

> **Sobre os avatares de língua gestual**
> Talvez ouça falar de *avatares* — personagens 3D geradas por software que "gesticulam" automaticamente a partir de texto. São tentadores porque parecem baratos e automáticos. Hoje, porém, têm limitações sérias: têm grande dificuldade em reproduzir a **expressão facial** e a **prosódia**, que, como vimos, fazem parte da gramática da LGP. O resultado é muitas vezes mecânico e difícil de compreender, e a própria comunidade surda tende a rejeitá-lo para conteúdo real.
>
> **O que isto significa na prática:** para conteúdo que importa, prefira **intérpretes humanos**. Os avatares podem ter espaço em experiências muito controladas e repetitivas, mas não substituem, neste momento, uma interpretação humana de qualidade.

---

## Recomendações para Conteúdo Acessível

A interpretação em LGP só cumpre a sua função se a pessoa conseguir **ver bem** o que está a ser gesticulado. Estas recomendações concentram-se nisso.

**1. Dimensão suficiente.** O intérprete tem de ser grande o bastante para que os detalhes das mãos e da expressão facial sejam legíveis. Um selo minúsculo no canto do ecrã não serve. Sempre que possível, permita ampliar a janela do intérprete.

**2. Rosto, mãos e tronco visíveis e sem cortes.** Como a expressão facial e os movimentos do tronco fazem parte da língua, o enquadramento tem de incluir, no mínimo, da cintura para cima. Cortar as mãos ou o topo da cabeça destrói informação gramatical.

**3. Contraste com o fundo e com a roupa.** O fundo deve contrastar com a pele e com a roupa do intérprete, para que as mãos se destaquem. Tradicionalmente usa-se um fundo liso e escuro com roupa de cor sólida.

**4. Boa iluminação e sem sombras nas mãos ou no rosto.** Sombras no rosto escondem a expressão; sombras nas mãos escondem a configuração dos dedos. Iluminação frontal e uniforme é essencial.

**5. A língua certa para o público certo.** Para um público português, use **Língua Gestual Portuguesa**. Não assuma que "língua gestual internacional" ou ASL servem. A escolha da língua gestual deve corresponder à comunidade a que o conteúdo se destina.

**6. Intérpretes qualificados.** Recorra a intérpretes de LGP profissionais e, idealmente, com experiência no tipo de conteúdo (jurídico, médico, educativo…). A fluência e a naturalidade da interpretação afetam diretamente a compreensão.

**7. Sincronização com o áudio original.** A interpretação deve acompanhar o discurso em tempo real, sem atrasos que obriguem a pessoa a saltar entre a imagem principal e o intérprete.

**8. Torne a alternativa fácil de encontrar.** Se usar uma versão interpretada separada (Abordagem 3), a ligação deve ser óbvia e descrever claramente o que oferece ("com interpretação em LGP"), e não estar escondida.

### Erros Comuns

**Assumir que as legendas dispensam a língua gestual.** É o erro central. As legendas servem quem lê fluentemente português; a LGP serve quem tem a língua gestual como primeira língua. Não são intermutáveis.

**Intérprete demasiado pequeno ou impossível de ampliar.** Uma janela de LGP no canto, com poucos centímetros, é decorativo e não funcional. Se as mãos não se distinguem, a interpretação é inútil.

**Cortar mãos, rosto ou tronco.** Enquadramentos apertados que "comem" os gestos amplos ou escondem a expressão facial retiram significado.

**Fundo e roupa sem contraste.** Mãos que se confundem com o fundo tornam a leitura impossível, sobretudo em sinais rápidos.

**Usar a língua gestual errada.** Publicar ASL para um público português, ou assumir uma "língua gestual universal" que não existe.

**Confiar em avatares automáticos para conteúdo real.** A tecnologia ainda não reproduz de forma fiável a expressão facial e a prosódia, que são gramaticalmente essenciais.

**Duas faixas de áudio a tocar ao mesmo tempo.** Numa solução com dois vídeos, esquecer de silenciar o vídeo do intérprete produz eco e sobreposição sonora.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A **língua gestual** é uma língua natural e completa. A **LGP** tem gramática própria e é diferente do português e de outras línguas gestuais. Não existe língua gestual universal.
- Para muitas pessoas surdas, sobretudo de surdez pré-linguística, a língua gestual é a **primeira língua** e o português escrito é uma **segunda língua**. Por isso, **legendas e interpretação em LGP servem públicos diferentes e não se substituem**.
- A expressão facial e os movimentos do corpo **fazem parte da gramática** da LGP: transmitem emoção e significado que as legendas não captam.
- Nas WCAG, a interpretação em língua gestual corresponde ao critério **1.2.6 (Nível AAA)**. Está **acima do mínimo legal AA** (Decreto-Lei n.º 83/2018 / EN 301 549), mas é fortemente recomendada em muitos contextos, sobretudo no setor público. A LGP está reconhecida na **Constituição** (artigo 74.º).
- Tecnicamente, há três caminhos: **intérprete embutido** no vídeo, **vídeo separado sincronizado** (com controlo do utilizador) e **versão alternativa interpretada** ligada a partir do conteúdo.
- O que torna a interpretação acessível é a **visibilidade**: dimensão suficiente, enquadramento completo (rosto, mãos, tronco), bom contraste, boa iluminação, a língua certa e intérpretes qualificados.
- Os **avatares** ainda não substituem intérpretes humanos para conteúdo real.

### Exercícios Práticos

**Exercício 1 — Distinguir públicos**
Uma câmara municipal vai publicar um vídeo com informação sobre um novo serviço de apoio a idosos. O responsável diz: "Já tem legendas, portanto está acessível para os surdos." Escreva uma resposta curta (3 a 5 frases) a explicar por que razão as legendas podem não bastar e em que situação a LGP faz diferença.

**Exercício 2 — Avaliar um enquadramento**
Observe (ou imagine) um vídeo em que a intérprete aparece num círculo pequeno no canto inferior direito, com roupa clara sobre um fundo também claro, e em que os gestos mais amplos saem por vezes do círculo. Identifique **três** problemas de acessibilidade e proponha uma correção para cada um.

**Exercício 3 — Escolher a técnica**
Para cada cenário, indique qual das três abordagens de codificação usaria e justifique:
(a) um vídeo institucional único que não pode ser reeditado, mas para o qual já existe uma gravação separada da intérprete;
(b) uma plataforma de formação onde os utilizadores devem poder ligar e desligar a interpretação;
(c) um pequeno vídeo promocional em que se pretende que a interpretação esteja sempre visível.

**Exercício 4 — Corrigir a sincronização**
No código da Abordagem 2, o programador esqueceu-se de silenciar o vídeo do intérprete e de sincronizar quando o utilizador arrasta a barra de tempo. Identifique as duas linhas/atributos que resolvem estes problemas e explique o que cada um faz.

**Exercício 5 — Argumentar o nível AAA**
Explique, por palavras simples, a diferença entre "este vídeo cumpre o nível AA" e "este vídeo tem interpretação em LGP". Em que tipos de conteúdo defenderia investir na interpretação em LGP mesmo não sendo exigida pelo mínimo legal? Dê dois exemplos e justifique.

