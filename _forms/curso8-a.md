# Formulários

## Introdução

Quase tudo o que fazemos online passa por um formulário. Iniciar sessão, pesquisar, comprar um bilhete, pedir a segunda via de um documento, marcar uma consulta ou submeter um pedido a um serviço público. Em todos estes casos existe um formulário a intermediar a relação entre a pessoa e o sistema.

Podemos pensar num formulário como uma **conversa estruturada**. O sítio faz perguntas ("Qual é o seu nome?", "Que valor pretende transferir?") e a pessoa responde. Se essa conversa for clara, ordenada e paciente, qualquer pessoa consegue chegar ao fim. Se for confusa, apressada ou cheia de armadilhas, muita gente desiste, e uma parte dessas pessoas desiste *não porque não quer*, mas porque a forma como o formulário foi construído lhes fecha a porta.

> **Analogia — o balcão de atendimento**
>
> Imagine um balcão de um serviço público. Do outro lado está um funcionário que faz perguntas e preenche os campos por si. Um bom funcionário fala devagar, explica o que é preciso, avisa quando algo está mal preenchido e não se importa de repetir. Um mau funcionário fala baixo, de costas, não explica os campos e, quando erramos, limita-se a rasgar a folha e mandar começar de novo.
>
> Um formulário acessível é o "bom funcionário": comunica de forma clara com **todas** as pessoas, incluindo aquelas que não veem o ecrã, que não usam rato, ou que precisam de mais tempo. Um formulário inacessível é o "mau funcionário" — e o problema é que ninguém o pode substituir, porque está escrito no código.

Neste módulo vamos perceber o que torna um formulário acessível de uma forma geral: quem depende dessa acessibilidade, que requisitos existem e que decisões técnicas fazem a diferença logo à partida. Os aspetos mais específicos — a estrutura e o posicionamento dos campos, os rótulos e instruções, as mensagens de erro e os formulários com vários passos — serão abordados mais à frente. Por isso, aqui vamos concentrar-nos nos alicerces.

### Como as Pessoas com Deficiência usam Formulários

Não existe "o utilizador com deficiência". Existem pessoas muito diferentes, com necessidades muito diferentes, e a mesma barreira pode ser invisível para umas e intransponível para outras. Vale a pena conhecer, em traços gerais, como cada grupo interage com um formulário.

**Pessoas cegas** costumam usar um *leitor de ecrã* — um programa que lê em voz alta (ou envia para uma linha braille) aquilo que está no ecrã. A pessoa não vê o formulário como um todo; percorre-o campo a campo, geralmente com o teclado. Para ela, cada campo tem de "dizer" claramente três coisas: **o que é** (é uma caixa de texto? um botão?), **como se chama** (o que devo escrever aqui?) e **em que estado está** (está preenchido? tem erro? é obrigatório?). Se esta informação não existir no código, o leitor de ecrã simplesmente não a consegue anunciar.

**Pessoas com baixa visão** podem ver o ecrã, mas com ampliação, cores invertidas ou tipos de letra maiores. Quando o ecrã está muito ampliado, vê-se apenas um pequeno pedaço de cada vez — como olhar para uma sala através do rolo de papel higiénico. Um campo cuja etiqueta está longe do campo, ou cujo erro aparece num canto distante, pode passar completamente despercebido.

**Pessoas com limitações motoras** podem não conseguir usar o rato. Muitas navegam **só com o teclado**, outras usam comandos de voz, um único botão (*switch*) ou dispositivos adaptados. Para estas pessoas, é essencial poder alcançar e ativar todos os campos e botões sem depender de um clique preciso num ponto do ecrã.

**Pessoas com deficiência cognitiva ou dificuldades de aprendizagem** beneficiam de formulários curtos, com linguagem simples, uma coisa de cada vez e sem pressão de tempo. Perguntas ambíguas, jargão técnico ou campos que "desaparecem" com um temporizador criam barreiras reais.

**Pessoas surdas ou com perda auditiva** normalmente não têm problemas com o texto de um formulário, mas são prejudicadas se a única forma de avisar de um erro for um som (por exemplo, um "bip" quando algo está mal). Aquilo que é comunicado por áudio tem de estar também disponível de forma visual e textual.

> **O que reter deste retrato**
>
> Repare que quase todas estas pessoas dependem, no fundo, de **duas coisas**: que a informação exista de forma estruturada no código (para o leitor de ecrã a poder anunciar) e que tudo seja operável sem rato (para quem usa teclado, voz ou switch). Estas duas ideias vão acompanhar-nos ao longo de todo o módulo.

### Requisitos de Acessibilidade para Formulários

As Diretrizes de Acessibilidade para o Conteúdo Web (WCAG) organizam a acessibilidade em quatro princípios simples. Aplicados aos formulários, podem ler-se assim:

- **Percetível** — a pessoa consegue *aperceber-se* de que existe um campo, do que ele pede e do que lá escreveu. Isto vale para quem vê e para quem ouve através de um leitor de ecrã.
- **Operável** — a pessoa consegue *usar* o formulário com o método que tem: rato, teclado, voz ou toque. Nenhuma interação pode depender exclusivamente do rato.
- **Compreensível** — as perguntas fazem sentido, o comportamento é previsível e, quando algo corre mal, a pessoa percebe o quê e como corrigir.
- **Robusto** — o formulário funciona com diferentes tecnologias de apoio, hoje e no futuro, porque foi construído com código correto e padronizado.

Num nível prático, e para este capítulo introdutório, três requisitos gerais sobressaem e vão orientar as boas decisões técnicas:

1. **Usar elementos nativos** de formulário sempre que possível. O HTML já traz caixas de texto, listas, caixas de verificação e botões que são acessíveis de origem. Recriá-los "à mão" com `<div>` obriga a repor, uma a uma, todas as características que se perderam.
2. **Garantir a operabilidade por teclado.** Se conseguir preencher e submeter o formulário inteiro usando apenas <kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>, <kbd>Espaço</kbd>, <kbd>Enter</kbd> e as setas, está no bom caminho.
3. **Expor o nome, a função e o estado** de cada campo ao código (o chamado *name, role, value*). É isto que permite a um leitor de ecrã dizer "Caixa de texto, E-mail, obrigatório, vazio".

## Técnicas de Codificação

Boa parte da acessibilidade de um formulário decide-se em escolhas técnicas que se fazem uma vez e beneficiam toda a gente. Vejamos as principais.

### Escolher o elemento certo para cada tarefa

O HTML oferece elementos próprios para cada tipo de interação: `<input>` para dados curtos, `<textarea>` para textos longos, `<select>` para escolher de uma lista, `<button>` para ações. Estes elementos são reconhecidos por teclado e por leitores de ecrã **sem que seja preciso fazer mais nada**.

```html
<!-- BOM -->
<button type="submit">Submeter pedido</button>

<!-- MAU -->
<div class="botao" onclick="submeter()">Submeter pedido</div>
```

**O que funciona e o que falha aqui:** O `<button>` recebe foco com o <kbd>Tab</kbd>, ativa-se com <kbd>Enter</kbd> ou <kbd>Espaço</kbd> e é anunciado como "botão" pelo leitor de ecrã. Tudo de graça. O `<div>` é apenas um retângulo decorado: não recebe foco pelo teclado, não responde ao <kbd>Enter</kbd> e o leitor de ecrã não faz ideia de que é clicável. Para o pôr ao nível do `<button>`, teria de lhe acrescentar `tabindex`, tratar eventos de teclado e adicionar `role="button"`. Muito trabalho para reconstruir algo que já existia.

> **Analogia:** usar um `<div>` como botão é como fabricar uma cadeira a partir de tábuas soltas quando havia uma cadeira pronta ao lado. Pode até *parecer* uma cadeira, mas alguém se vai magoar quando tentar sentar-se.

### Usar o tipo (`type`) apropriado nos campos

O atributo `type` do `<input>` não é um detalhe estético. Ele diz ao navegador que espécie de dado é esperado, o que ajuda a validação, ajusta o teclado apresentado nos telemóveis e melhora a compreensão para toda a gente.

```html
<!-- BOM -->
<input type="email" name="email">
<input type="tel" name="telefone">
<input type="date" name="data_nascimento">

<!-- MENOS BOM -->
<input type="text" name="email">
<input type="text" name="telefone">
```

**O que funciona e o que falha aqui:** Com `type="email"`, um telemóvel mostra logo o teclado com o símbolo "@"; com `type="tel"`, aparece o teclado numérico. Isto reduz erros e esforço, sobretudo para quem tem dificuldades motoras ou cognitivas. Usar sempre `type="text"` obriga a pessoa a procurar teclas e abre a porta a mais enganos. Não é *errado* em termos de código, mas desperdiça uma ajuda que não custa nada dar.

### Ajudar o preenchimento automático com `autocomplete`

Quando um campo pede um dado pessoal comum (nome, e-mail, morada, telefone), o atributo `autocomplete` diz ao navegador *qual* é esse dado, permitindo-lhe oferecer o preenchimento automático.

```html
<!-- BOM -->
<input type="text" name="nome" autocomplete="name">
<input type="email" name="email" autocomplete="email">
<input type="text" name="cp" autocomplete="postal-code">
```

**O que funciona e o que falha aqui:** Para uma pessoa com limitações motoras, escrever a morada completa pode ser demorado e cansativo; o preenchimento automático poupa-lhe esse esforço. Para uma pessoa com dificuldades de memória, evita ter de recordar dados de cor. Sem `autocomplete`, o navegador não sabe que aquele campo é o "código postal" e não consegue ajudar. Este requisito corresponde ao critério WCAG *Identificar a Finalidade da Entrada* (1.3.5).

### Manter a operabilidade por teclado

Como vimos, muita gente não usa rato. A regra prática é simples: **tudo o que se faz com o rato tem de se poder fazer com o teclado**. Se usar apenas elementos nativos, isto acontece quase automaticamente. Os problemas surgem sobretudo quando se constroem componentes personalizados (menus, "dropdowns" desenhados de raiz, botões falsos).

```html
<!-- BOM: controlo nativo, já funciona com teclado -->
<select name="distrito">
  <option value="">Escolha um distrito</option>
  <option value="lisboa">Lisboa</option>
  <option value="porto">Porto</option>
</select>

<!-- ARRISCADO: lista personalizada feita com div/span -->
<div class="dropdown" onclick="abrir()">Escolha um distrito</div>
```

**O que funciona e o que falha aqui:** O `<select>` abre-se com o teclado, percorre-se com as setas e anuncia cada opção, sem código extra. A versão em `<div>` obriga a reprogramar todo esse comportamento (foco, setas, <kbd>Enter</kbd>, <kbd>Escape</kbd>, anúncio de opções) e, se um único desses pormenores ficar por fazer, a pessoa que navega com teclado fica bloqueada. A recomendação é clara: **apenas construir um controlo personalizado quando não existir mesmo possibilidade de usar o nativo** e, nesse caso, faça-o com ARIA e teste-o exaustivamente com teclado e leitor de ecrã.

### Envolver os campos num `<form>` e ter um botão de submissão real

Parece óbvio, mas é frequente encontrar "formulários" que na verdade são um conjunto de campos soltos. Envolver os controlos num elemento `<form>` e terminar com um botão de submissão verdadeiro traz comportamentos que os utilizadores esperam, como submeter com a tecla <kbd>Enter</kbd>.

```html
<!-- BOM -->
<form action="/pedido" method="post">
  <!-- campos aqui -->
  <button type="submit">Enviar</button>
</form>
```

**O que funciona e o que falha aqui:** Dentro de um `<form>`, premir <kbd>Enter</kbd> num campo de texto submete o formulário. Um automatismo que muitos utilizadores de teclado usam sem pensar. Um botão `type="submit"` real é anunciado corretamente e cumpre essa função. Sem `<form>` e sem botão real, perde-se este comportamento esperado e a pessoa fica sem saber como concluir.

## Recomendações para Conteúdo Acessível

Nem tudo se resolve no código. A forma como *escrevemos e organizamos* o formulário, as decisões de conteúdo, tem tanto peso como as decisões técnicas. Estas recomendações aplicam-se a qualquer formulário, independentemente da tecnologia.

**Peça apenas o que é mesmo necessário.** Cada campo é um obstáculo. Um formulário curto é mais fácil para toda a gente e essencial para quem se cansa depressa ou se distrai facilmente.

> **Exemplo:** um formulário de subscrição de uma newsletter que pede nome, apelido, morada completa, data de nascimento e profissão.
>
> **Análise:** para enviar um e-mail periódico basta... o e-mail. Cada campo extra afasta pessoas e, no caso de quem tem dificuldades motoras ou cognitivas, o desânimo é maior. Menos campos não é só "mais bonito", é mais acessível.

**Use linguagem simples e direta nas perguntas.** Evite jargão, siglas por explicar e frases ambíguas. Se um termo técnico for inevitável, explique-o.

> **Exemplo:** um campo chamado apenas "NIF/NIPC/NISS".
>
> **Análise:** para quem conhece as siglas, tudo bem; para muita gente, é um enigma. Uma alternativa mais clara seria "Número de identificação fiscal (NIF)" e, se forem aceites vários, indicá-lo de forma explícita. Perguntas claras reduzem erros para *todos*, não apenas para pessoas com deficiência.

**Agrupe o que faz parte do mesmo assunto.** Um formulário que salta de tema em tema é cansativo de acompanhar, sobretudo para quem o percorre linearmente com um leitor de ecrã. 

**Não imponha limites de tempo desnecessários.** Formulários que "expiram" ou campos que se fecham sozinhos penalizam quem escreve mais devagar, quem usa tecnologias de apoio ou quem simplesmente precisa de pensar. Se um limite for mesmo obrigatório (por razões de segurança, por exemplo), avise com antecedência e permita prolongá-lo.

**Indique com clareza o que é obrigatório e o que é opcional.** A pessoa deve saber, *antes* de submeter, que campos tem mesmo de preencher. 

### Erros Comuns

Alguns erros repetem-se tanto que vale a pena tê-los sempre debaixo de olho:

- **Botões e ligações falsos.** Usar `<div>` ou `<span>` com um `onclick` em vez de `<button>` ou `<a>`. Resultado: quem usa teclado não os alcança e o leitor de ecrã não os anuncia como acionáveis.
- **Depender só de `type="text"`.** Ignorar `type="email"`, `type="tel"`, `type="number"`, etc., desperdiça validação e teclados adaptados que ajudariam toda a gente.
- **Controlos personalizados sem suporte de teclado.** "Dropdowns", interruptores e seletores desenhados de raiz que só respondem ao rato deixam de fora uma parte dos utilizadores.
- **Esconder ou "roubar" o foco.** Componentes que movem o foco para sítios inesperados, ou que o prendem numa zona sem saída, desorientam quem navega por teclado.
- **CAPTCHAs só visuais ou só sonoros.** Um teste que obriga a "ler letras distorcidas" exclui quem não vê; se a alternativa for apenas áudio, exclui quem não ouve. Sempre que possível, prefira métodos que não dependam de um único sentido.

> **Nota:** dois erros muito frequentes — usar o texto de exemplo (*placeholder*) como se fosse a etiqueta do campo, e mostrar mensagens de erro pouco claras — são tratados em profundidade mais à frente. Por isso não os desenvolvemos aqui, mas fica o aviso de que existem.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Um formulário é uma **conversa estruturada** entre a pessoa e o sistema; torná-lo acessível é garantir que essa conversa funciona para toda a gente.
- Pessoas diferentes usam os formulários de formas diferentes — com leitor de ecrã, com ampliação, só com teclado, com voz — mas quase todas dependem de **informação bem estruturada no código** e de **operabilidade sem rato**.
- A regra de ouro técnica é **usar elementos nativos do HTML** (`<input>`, `<select>`, `<textarea>`, `<button>`, `<form>`): são acessíveis de origem e poupam imenso trabalho.
- Escolher o **`type` certo** e usar **`autocomplete`** ajuda toda a gente e é essencial para quem tem dificuldades motoras ou cognitivas.
- **Só se constrói um controlo personalizado** quando o nativo não serve — e, mesmo aí, com muita atenção ao suporte ao teclado e à correção do ARIA.
- No conteúdo: peça só o necessário, use linguagem simples, não imponha limites de tempo desnecessários.

### Exercícios Práticos

**Exercício 1 — Encontrar o botão falso**
Recebeu o seguinte trecho de código:

```html
<div class="botao-enviar" onclick="enviar()">Enviar</div>
```

a) Explique, por palavras suas, dois problemas de acessibilidade deste código.
b) Reescreva-o de forma acessível.

> *Pista:* pense em quem navega só com teclado e em como um leitor de ecrã anuncia (ou não) este elemento.

**Exercício 2 — Escolher o `type` certo**
Um formulário de contacto pede: nome, e-mail, número de telemóvel e mensagem. Todos os campos estão como `type="text"`.

a) Que `type` deveria ter cada campo (e que elemento, no caso da mensagem)?
b) Explique que benefício concreto traz cada alteração para um utilizador de telemóvel.

**Exercício 3 — Cortar o supérfluo**
Um formulário para descarregar um documento público pede: nome, apelido, e-mail, morada, código postal, data de nascimento, profissão e habilitações.

a) Se o objetivo é apenas enviar o documento por e-mail, que campos manteria e quais removeria?
b) Justifique a sua decisão do ponto de vista da acessibilidade e do esforço pedido à pessoa.

**Exercício 4 — Teste do teclado**
Escolha um formulário real (por exemplo, o de pesquisa ou de contacto de um sítio à sua escolha) e tente preenchê-lo e submetê-lo **usando apenas o teclado** (<kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>, setas, <kbd>Espaço</kbd>, <kbd>Enter</kbd>).

a) Conseguiu alcançar todos os campos e o botão de submissão?
b) Houve algum ponto em que ficou "preso" ou sem saber onde estava o foco?
c) Registe uma barreira que tenha encontrado e proponha uma correção.

> *Sugestão de reflexão:* muitas das barreiras que encontrar neste exercício vão ligar-se diretamente aos temas dos próximos capítulos — estrutura, rótulos, mensagens de erro e formulários com vários passos.



