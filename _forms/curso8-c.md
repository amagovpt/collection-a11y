# Rótulos e Instruções

## Introdução

Imagine que chega a uma cozinha desconhecida e encontra uma fila de frascos todos iguais, sem qualquer etiqueta. Um tem sal, outro tem açúcar, outro tem farinha. Para quem vê, ainda é possível adivinhar pela cor ou pela textura. Mas para quem não vê, ou para quem se distrai com facilidade, aqueles frascos são um enigma perigoso: basta trocar o sal pelo açúcar para estragar o bolo.

Um formulário sem rótulos é exactamente esta cozinha. Os campos estão lá — caixas de texto, listas, botões — mas ninguém explica o que se espera dentro de cada um. O **rótulo** (em inglês, *label*) é a etiqueta que diz "aqui escreve-se o teu nome", "aqui escolhe-se a data de nascimento", "aqui confirma-se a palavra-passe". As **instruções** são a informação extra que ajuda a preencher correctamente: "a data deve ter o formato DD/MM/AAAA", "a palavra-passe precisa de pelo menos 8 caracteres", "campos com asterisco são obrigatórios".

Neste capítulo vamos concentrar-nos em duas perguntas simples:

- **Como identificar cada campo** de forma clara e para que essa identificação chegue a toda a gente, incluindo a quem usa tecnologias de apoio.
- **Como dar instruções** no momento certo, antes de a pessoa preencher, para evitar erros em vez de os corrigir depois.

> **Nota de âmbito:** o *agrupamento visual* de campos (por exemplo, juntar "morada de faturação" e "morada de envio") e a *ordem de leitura* são tratados na secção **Estrutura e Posicionamento**. O texto das mensagens que surgem *depois* de um erro é tratado na secção **Notificações e Mensagens de Erro**. Aqui interessa-nos o que aparece **antes** de a pessoa preencher: a etiqueta do campo e a ajuda que evita o erro.

### Como as Pessoas com Deficiência dependem de Rótulos e Instruções

Um rótulo bem feito não é uma decoração. É a única forma de muitas pessoas saberem o que fazer. Vejamos como diferentes grupos dependem dele.

**Pessoas cegas que usam leitor de ecrã.** O leitor de ecrã lê o que está no ecrã em voz alta. Quando a pessoa salta de campo em campo com a tecla `Tab`, o leitor anuncia o rótulo de cada campo: *"Nome, caixa de texto"*, *"País, lista"*. Se o campo não tiver um rótulo associado de forma correcta, o leitor não tem nada para anunciar e diz apenas *"caixa de texto"* — o equivalente a chegar ao frasco sem etiqueta. A pessoa fica sem saber o que ali escrever.

**Pessoas com baixa visão que ampliam o ecrã.** Quem usa ampliação vê apenas uma pequena parte do ecrã de cada vez, como quem lê um jornal através de uma lupa. Se o rótulo estiver longe do campo, ou muito acima, pode ficar fora da zona ampliada e a pessoa perde a ligação entre a etiqueta e a caixa correspondente.

**Pessoas com deficiência cognitiva ou dificuldades de aprendizagem.** Rótulos claros e instruções antecipadas reduzem o esforço de memória e a ansiedade. Uma instrução como "usa o formato DD/MM/AAAA" evita que a pessoa tenha de adivinhar e falhar várias vezes. Rótulos consistentes ao longo do sítio (usar sempre "Telemóvel" e não ora "Telemóvel", ora "Contacto móvel", ora "Nº de telefone") ajudam a criar hábitos e a reconhecer os campos.

**Pessoas com limitações motoras.** Aqui há um benefício menos óbvio mas muito importante: quando o rótulo está **associado** ao campo, clicar no texto do rótulo coloca o cursor no campo. Isto aumenta muito a área "clicável". Para quem tem dificuldade em acertar com o rato ou com o dedo numa pequena caixa de seleção, poder clicar na palavra "Aceito os termos" em vez da minúscula caixa quadrada faz toda a diferença.

**Pessoas que usam software de reconhecimento de voz.** Quem controla o computador por voz diz coisas como *"clicar em Enviar"* ou *"clicar em Pesquisar"*. Para isto funcionar, o nome que o software "ouve" tem de coincidir com o texto que a pessoa vê. Se o botão mostra "Pesquisar" mas por baixo tem um nome acessível diferente, o comando de voz falha.

### Requisitos de Acessibilidade para Rótulos e Instruções

Os requisitos abaixo têm correspondência em critérios das WCAG (as diretrizes internacionais de acessibilidade). Aqui apresentamo-los em linguagem simples.

- **Todos os campos que pedem informação têm de ter um rótulo ou uma instrução.** Ninguém deve ter de adivinhar o que escrever. *(Corresponde ao critério 3.3.2 — Rótulos ou Instruções.)*

- **A ligação entre o rótulo e o campo tem de ser "percetível pelo programa", não apenas visual.** Não basta o rótulo estar ao lado do campo aos olhos de quem vê; o código tem de dizer explicitamente "este texto é o rótulo daquele campo", para que o leitor de ecrã os associe. *(Corresponde ao critério 1.3.1 — Informação e Relações, e ao 4.1.2 — Nome, Função, Valor.)*

- **Os rótulos têm de ser descritivos.** "Campo 1" não descreve nada. "Nome próprio" descreve. *(Corresponde ao critério 2.4.6 — Cabeçalhos e Rótulos.)*

- **O nome que o programa reconhece tem de incluir o texto visível.** Se a pessoa vê "Enviar", o comando de voz "clicar em Enviar" tem de funcionar. *(Corresponde ao critério 2.5.3 — Rótulo no Nome.)*

- **Campos que pedem dados pessoais comuns devem identificar o seu propósito.** O programa deve conseguir saber que um campo é para o "nome", outro para o "e-mail", outro para o "código postal", para que ferramentas de preenchimento automático e personalização funcionem. *(Corresponde ao critério 1.3.5 — Identificar o Objetivo da Entrada.)*

## Técnicas de Codificação

Nesta secção vemos, na prática, como escrever o código. Todos os exemplos usam HTML simples. Depois de cada exemplo há uma explicação do que funciona bem ou mal.

### 1. Associar o rótulo ao campo com `<label>` e `for`

A forma mais robusta e recomendada é usar o elemento `<label>` com o atributo `for`, que aponta para o atributo `id` do campo. Os dois têm de ter o mesmo valor.

```html
<label for="nome-proprio">Nome próprio</label>
<input type="text" id="nome-proprio">
```

**O que funciona bem:** o `for="nome-proprio"` e o `id="nome-proprio"` criam uma ligação explícita. O leitor de ecrã anuncia *"Nome próprio, caixa de texto"*. Além disso, clicar no texto "Nome próprio" coloca o cursor na caixa — a tal área clicável maior que ajuda quem tem limitações motoras. É a solução mais compatível com todas as tecnologias de apoio.

**Atenção:** o `id` tem de ser **único** em toda a página. Se dois campos partilharem o mesmo `id`, a associação parte-se e os resultados tornam-se imprevisíveis.

### 2. Envolver o campo com o rótulo (associação implícita)

Também é possível colocar o campo **dentro** do `<label>`. Neste caso, a associação existe mesmo sem `for` e `id`.

```html
<label>
  Nome próprio
  <input type="text">
</label>
```

**O que funciona bem:** é conciso e a associação é automática. Útil, por exemplo, em caixas de seleção onde o texto anda sempre colado à caixa.

**O que pode correr mal:** alguns leitores de ecrã e alguns componentes complexos lidam pior com esta forma do que com a explícita. Além disso, se o layout separar visualmente o texto do campo, o código fica mais difícil de gerir. Por isso, quando houver dúvidas, prefira a associação explícita com `for` (técnica 1).

### 3. Dar um nome a controlos sem texto visível: `aria-label`

Alguns controlos não têm texto ao lado. Por exemplo, um botão de pesquisa que mostra apenas um ícone de lupa. Aos olhos de quem vê, a lupa "explica-se" sozinha. Para o leitor de ecrã, um botão sem texto é um botão mudo.

```html
<!-- Mau exemplo: botão sem nome -->
<button>
  <svg><!-- ícone de lupa --></svg>
</button>

<!-- Bom exemplo: nome fornecido com aria-label -->
<button aria-label="Pesquisar">
  <svg aria-hidden="true"><!-- ícone de lupa --></svg>
</button>
```

**O que funciona bem no bom exemplo:** o `aria-label="Pesquisar"` dá um nome ao botão que o leitor de ecrã anuncia. O `aria-hidden="true"` no ícone diz à tecnologia de apoio para o ignorar, evitando leituras estranhas do desenho.

**O que falha no mau exemplo:** o botão não tem texto nem `aria-label`. O leitor de ecrã anuncia apenas *"botão"*, sem dizer para quê. E como o texto "Pesquisar" não aparece em lado nenhum, quem usa comando de voz também não consegue ativá-lo.

> **Cuidado:** use `aria-label` apenas quando **não existe** texto visível para servir de rótulo. Sempre que houver texto no ecrã, o melhor é usá-lo como rótulo real (técnicas 1 ou 2). Um rótulo visível ajuda toda a gente; um rótulo "invisível" só ajuda quem usa leitor de ecrã.

### 4. Construir o nome a partir de texto já existente: `aria-labelledby`

Às vezes o rótulo já está escrito noutro elemento e não queremos repeti-lo. O `aria-labelledby` aponta para o `id` desse texto.

```html
<h2 id="titulo-envio">Morada de envio</h2>
<button id="btn-editar" aria-labelledby="btn-editar titulo-envio">Editar</button>
```

**O que funciona bem:** o botão passa a ser anunciado como *"Editar, Morada de envio"*, o que esclarece qual das várias "moradas" este botão edita. Muito útil quando a mesma palavra (por exemplo, "Editar") se repete pela página.

**O que ter em conta:** o `aria-labelledby` **substitui** qualquer outro nome. Aponte sempre para texto que exista mesmo na página.

### 5. Associar instruções e ajuda ao campo: `aria-describedby`

O rótulo diz *o quê*. As instruções dizem *como*. Para ligar uma instrução a um campo, de forma que o leitor de ecrã a leia logo a seguir ao rótulo, usa-se o `aria-describedby`, que aponta para o `id` do texto de ajuda.

```html
<label for="palavra-passe">Palavra-passe</label>
<input type="password" id="palavra-passe" aria-describedby="ajuda-pp">
<p id="ajuda-pp">Mínimo de 8 caracteres, com pelo menos um número.</p>
```

**O que funciona bem:** quando o cursor entra no campo, o leitor de ecrã anuncia *"Palavra-passe, caixa de texto, Mínimo de 8 caracteres, com pelo menos um número"*. A instrução chega **no momento em que é útil** e a pessoa não tem de a ir procurar. Como a instrução é texto normal na página, também está visível para toda a gente.

**A diferença essencial:** o rótulo (`<label>`) identifica o campo; a descrição (`aria-describedby`) acrescenta ajuda. Não confunda os dois papéis: o campo precisa sempre de rótulo; a descrição é um extra.

### 6. Indicar campos obrigatórios

Quando um campo é obrigatório, isso deve ser comunicado de duas formas: para os olhos e para o programa.

```html
<label for="email">E-mail (obrigatório)</label>
<input type="email" id="email" required aria-required="true">
```

**O que funciona bem:** a palavra "(obrigatório)" no rótulo é clara para toda a gente e não depende de cor nem de símbolos. O atributo `required` faz o próprio navegador tratar o campo como obrigatório, e o `aria-required="true"` garante que os leitores de ecrã o anunciam como tal.

**Sobre o asterisco:** é comum marcar campos obrigatórios com um asterisco (`*`). Não há problema em usá-lo, **desde que** se explique, no início do formulário, o que significa. Por exemplo, "Os campos marcados com * são obrigatórios". Nunca dependa **só** da cor (vermelho) para indicar obrigatoriedade, porque quem não distingue cores não a percebe. 

### 7. Identificar o propósito do campo: `autocomplete`

Para campos que pedem dados pessoais comuns (nome, e-mail, telefone, morada), o atributo `autocomplete` diz ao navegador e a tecnologias de apoio, qual é o propósito do campo.

```html
<label for="tel">Telemóvel</label>
<input type="tel" id="tel" autocomplete="tel">

<label for="cp">Código postal</label>
<input type="text" id="cp" autocomplete="postal-code">
```

**O que funciona bem:** com estes valores, o navegador consegue oferecer preenchimento automático correcto, poupando trabalho a toda a gente e reduzindo erros. Para pessoas com limitações motoras ou de memória, preencher automaticamente o próprio nome e morada é uma enorme ajuda. Este atributo também permite que algumas ferramentas personalizem o formulário (por exemplo, mostrando um ícone junto ao campo).

**O que ter em conta:** use os **valores normalizados** definidos na especificação (`name`, `email`, `tel`, `postal-code`, `street-address`, etc.). Um valor inventado como `autocomplete="telefone-do-utilizador"` não é reconhecido e não produz qualquer benefício.

## Recomendações para Conteúdo Acessível

As técnicas de código só resolvem metade do problema. A outra metade é **o que se escreve** nos rótulos e nas instruções. Aqui ficam recomendações práticas de redação.

**Escreva rótulos curtos, mas concretos.** Um bom rótulo diz exactamente o que se pede, sem palavras a mais. Prefira "Nome próprio" a "Por favor, escreva aqui o seu primeiro nome"; prefira "Data de nascimento" a "Data".

*Exemplo:*

```
Mau:  Campo    →  Bom:  Nome da empresa
Mau:  Data     →  Bom:  Data de nascimento
Mau:  Info     →  Bom:  Comentários adicionais
```

**O que melhora:** os rótulos "bons" dizem à pessoa o que ali colocar sem obrigar a adivinhar. Isto ajuda especialmente quem tem dificuldades cognitivas e quem, com o leitor de ecrã, só ouve o rótulo e mais nada.

**Ponha a informação importante no início do rótulo.** Quem usa leitor de ecrã e salta rapidamente entre campos beneficia de ouvir logo a palavra-chave. "Telemóvel (opcional)" é melhor do que "(Opcional) o seu número de telemóvel".

**Dê as instruções ANTES do campo, não depois.** Se a regra de preenchimento aparecer só depois da caixa, muita gente já a preencheu — e errou — antes de a ler. Coloque o formato ou a regra junto ao rótulo ou logo abaixo dele, e associe-a com `aria-describedby` (técnica 5).

*Exemplo:*

```html
<!-- Recomendado: instrução antes de preencher -->
<label for="nif">NIF</label>
<span id="ajuda-nif">Nove dígitos, sem espaços.</span>
<input type="text" id="nif" aria-describedby="ajuda-nif">
```

**O que funciona bem:** a pessoa lê "Nove dígitos, sem espaços" antes de escrever, e evita o erro. Prevenir é sempre melhor do que corrigir.

**Seja consistente em todo o sítio.** Use sempre a mesma palavra para o mesmo conceito. Se numa página o campo se chama "Telemóvel" e noutra "Contacto", a pessoa tem de reaprender o formulário de cada vez. A consistência reduz o esforço para toda a gente e é essencial para quem tem dificuldades cognitivas.

**Evite depender apenas do "placeholder".** O texto cinzento que aparece dentro da caixa antes de escrever (o *placeholder*) parece um rótulo, mas comporta-se de forma muito diferente — como veremos já a seguir nos erros comuns.

**Faça o texto visível coincidir com o nome do programa.** Se o botão mostra "Guardar alterações", o nome acessível deve começar por "Guardar alterações" (e não, por exemplo, "Submeter formulário"). Assim, o comando de voz "clicar em Guardar alterações" funciona.

### Erros Comuns

**Erro 1 — Usar o *placeholder* como se fosse rótulo.**

```html
<!-- Errado -->
<input type="text" placeholder="Nome próprio">
```

**Porque é um problema:** o texto do *placeholder* **desaparece** assim que a pessoa começa a escrever. É como uma instrução escrita a giz num quadro que se apaga no momento em que se pega no lápis: quem se distrai ou quem precisa de reler já não tem a etiqueta. Além disso, o cinzento-claro habitual tem contraste fraco e alguns leitores de ecrã não o anunciam de forma fiável. **A correção:** use um `<label>` real e, se quiser, mantenha o *placeholder* apenas para um exemplo curto ("ex.: Maria").

**Erro 2 — Campo sem qualquer rótulo associado.**

```html
<!-- Errado -->
<p>Nome próprio</p>
<input type="text">
```

**Porque é um problema:** aos olhos de quem vê, o texto "Nome próprio" está ao lado do campo e parece um rótulo. Mas, no código, não há ligação nenhuma entre os dois. É apenas um parágrafo por acaso próximo da caixa. O leitor de ecrã anuncia só *"caixa de texto"*. **A correção:** transforme o parágrafo em `<label for="...">` ligado ao `id` do campo.

**Erro 3 — Rótulos vagos ou genéricos.** "Campo 1", "Texto", "Info", "Dados". Não descrevem nada. Quem só ouve o rótulo (via leitor de ecrã) fica sem pistas. **A correção:** dê a cada rótulo o nome exacto do que pede.

**Erro 4 — Marcar obrigatoriedade só com cor.** Pintar de vermelho os campos obrigatórios não chega: quem não distingue essa cor não percebe a diferença. **A correção:** acrescente uma palavra ("obrigatório") ou um símbolo explicado (o asterisco com legenda) e o atributo `required`.

**Erro 5 — Instruções que só aparecem depois do erro.** Guardar a regra "a palavra-passe precisa de 8 caracteres" para a mostrar apenas depois de a pessoa falhar transforma uma informação preventiva numa repreensão. **A correção:** mostre a regra antes, junto ao campo.

**Erro 6 — O nome do programa não bate certo com o texto visível.** Um botão que mostra "Pesquisar" mas tem `aria-label="Botão de busca do site"` impede a utilização do comando de voz "clicar em Pesquisar". **A correção:** garanta que o nome acessível **contém** o texto visível, de preferência começando por ele.

**Erro 7 — Ícones sem nome.** Botões e ligações que são só ícones (um caixote do lixo, um lápis, um "x") sem `aria-label` ficam mudos para o leitor de ecrã. **A correção:** dê-lhes um nome com `aria-label` e esconda o ícone decorativo com `aria-hidden="true"`.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- **Todos os campos precisam de rótulo.** O rótulo é a etiqueta que diz o que se espera no campo; sem ele, quem usa leitor de ecrã fica perante um "frasco sem etiqueta".
- **A associação tem de estar no código, não só no aspeto.** Use `<label for="...">` ligado ao `id` do campo (ou o campo dentro do `<label>`). Isto também aumenta a área clicável, ajudando quem tem limitações motoras.
- **Para controlos sem texto visível** (ícones), dê um nome com `aria-label` ou `aria-labelledby`, e esconda o ícone decorativo com `aria-hidden="true"`.
- **As instruções vêm antes do preenchimento**, associadas ao campo com `aria-describedby`. Prevenir o erro é melhor do que corrigi-lo.
- **Rótulos descritivos, curtos e consistentes.** Não usar "Campo 1"; usar "Nome próprio", e sempre o mesmo termo para o mesmo conceito.
- **Obrigatoriedade comunicada por palavras**, não só por cor, e reforçada com `required`.
- **O texto visível tem de coincidir com o nome acessível do elemento**, para os comandos de voz funcionarem.
- **Campos de dados pessoais** devem usar o atributo `autocomplete` com valores normalizados.

### Exercícios Práticos

**Exercício 1 — Encontrar o frasco sem etiqueta.**
Observe o seguinte código e identifique o problema. Depois, reescreva-o de forma acessível.

```html
<p>E-mail</p>
<input type="email" placeholder="E-mail">
```

*Pistas para a resolução:* há dois problemas — o texto "E-mail" não está associado ao campo (é apenas um parágrafo) e o *placeholder* está a fazer o trabalho que devia ser do rótulo. A versão corrigida deve usar `<label for="...">` ligado a um `id`.

**Exercício 2 — Dar voz aos ícones.**
Uma barra de ferramentas tem três botões só com ícones: um lápis (editar), um caixote do lixo (eliminar) e uma estrela (marcar como favorito). Escreva o código dos três botões de forma que um leitor de ecrã anuncie o nome de cada um e que os ícones decorativos sejam ignorados.

**Exercício 3 — Instrução no momento certo.**
Tem um campo "Código postal" que exige o formato `XXXX-XXX`. Escreva o rótulo, a instrução e o campo, ligando a instrução ao campo com `aria-describedby`, de forma que a regra seja lida **antes** de a pessoa preencher.

**Exercício 4 — Caçar os erros.**
No formulário de inscrição de um sítio real (ou num exemplo à sua escolha), navegue **apenas com o teclado**, usando a tecla `Tab` para saltar de campo em campo, e, se possível, com um leitor de ecrã ligado. Anote:

1. Todos os campos que **não** anunciam um rótulo.
2. Se os campos obrigatórios são identificados por palavras (e não só por cor).
3. Se as instruções de formato aparecem **antes** ou **depois** de preencher.
   Para cada problema encontrado, escreva a correção correspondente.

**Exercício 5 — Rótulos que falam por si.**
Melhore os seguintes rótulos vagos, tornando-os descritivos: "Campo", "Data", "Número", "Info". Justifique cada escolha em uma frase.

