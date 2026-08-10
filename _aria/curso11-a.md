# Aplicações Ricas

## Introdução

Durante muitos anos, a Web funcionou como um livro muito grande. Cada página era um documento; clicar numa ligação era virar a folha. O navegador sabia perfeitamente o que estava a acontecer, porque era ele que fazia acontecer: pedia o documento novo ao servidor, deitava fora o antigo e apresentava o seguinte.

Hoje, uma parte significativa dos serviços que usamos já não funciona assim. O Portal das Finanças, a área de cliente de um banco, uma plataforma de candidaturas, um mapa interativo, um editor de documentos online, um painel de indicadores, em todos estes casos **a página nunca é substituída**. O conteúdo é montado, desmontado e remontado dentro da mesma página, à medida que a pessoa vai interagindo. A estas interfaces chamamos **aplicações ricas** (em inglês, *Rich Internet Applications*).

### A analogia da sala que se remonta à nossa volta

Imagine que entra num edifício de serviços públicos à antiga. Para tratar de um assunto, percorre corredores e entra em salas diferentes: sala do atendimento, sala do pagamento, sala do arquivo. Cada mudança de sala é evidente. Há uma porta, há uma placa com o nome da sala, há um percurso que se pode refazer para trás.

Numa aplicação rica, a pessoa **nunca sai da mesma sala**. Em vez de a pessoa se deslocar, é a sala que se remonta à volta dela: as paredes mudam de sítio, o balcão desaparece, aparece uma mesa nova com formulários diferentes. Para quem vê, isto é ótimo. É rápido, não há esperas, não há ecrãs em branco entre passos. Para quem não vê, ou vê apenas um pequeno pedaço do ecrã de cada vez, ou não consegue acompanhar mudanças rápidas, **a sala mudou em silêncio**.

Esta é a ideia central desta secção, e do módulo inteiro: uma aplicação rica não é mais difícil de tornar acessível porque usa tecnologia complicada. É mais difícil porque **deixou de haver quem faça o trabalho de sinalização automaticamente**.

### O que o navegador deixou de fazer por nós

Vale a pena tornar isto muito concreto. Quando uma página web tradicional é substituída por outra, o navegador faz, sem que ninguém lho peça, pelo menos cinco coisas:

1. **Anuncia a chegada.** O leitor de ecrã diz o título da nova página.
2. **Recoloca o ponto de partida.** O foco e o cursor de leitura voltam ao início do documento.
3. **Atualiza o endereço.** O URL na barra de endereços passa a corresponder ao que está no ecrã.
4. **Alimenta o histórico.** O botão «retroceder» passa a poder desfazer aquele passo.
5. **Reconstrói a árvore de acessibilidade.** As tecnologias de apoio recebem uma representação nova e completa do conteúdo.

Numa aplicação rica, **nenhuma destas cinco coisas acontece sozinha**, porque do ponto de vista do navegador não se passou nada: continua a ser a mesma página, carregada uma única vez, que entretanto mudou por dentro.

> **O que isto significa na prática:** a acessibilidade de uma aplicação rica é, em boa medida, o trabalho de **repor manualmente aquilo que o navegador fazia de graça**. Não é trabalho extra opcional; é a fatura que se paga por ter escolhido uma arquitetura que dispensa o navegador.

### Não é «site» contra «aplicação»: é um contínuo

É tentador dividir o mundo em dois: sites de conteúdo de um lado, aplicações do outro. Na realidade existe um contínuo, e a maioria dos projetos reais está algures no meio:

| Grau | Exemplo típico | O que muda sem recarregar a página |
|---|---|---|
| Página com pequenos comportamentos | Notícia com um acordeão de «leia mais» | Um bloco de texto |
| Página com zonas dinâmicas | Listagem com filtros e ordenação | Uma lista de resultados |
| Aplicação de vista única | Formulário de candidatura em vários passos | O conteúdo principal inteiro |
| Aplicação completa | Editor, mapa, painel de gestão | Praticamente tudo, incluindo a navegação |

Quanto mais se avança nesta tabela, maior é a quantidade de trabalho de sinalização que passa para o lado de quem desenvolve. Mas repare: **mesmo o primeiro grau já tem o problema**. Um acordeão que abre em silêncio é, em ponto pequeno, exatamente a mesma falha da aplicação que troca a vista inteira em silêncio.

### Os quatro princípios que organizam este módulo

Todo este módulo pode ser arrumado em quatro verbos. Vamos usá-los repetidamente, nesta secção e nas seguintes:

- **Anunciar** — o que mudou tem de ser comunicado a quem não viu a mudança.
- **Preservar** — as garantias que a Web já dava (endereço, retroceder, ampliar, atalhos, preferências do sistema) não podem ser destruídas pela aplicação.
- **Expor** — tudo o que existe visualmente tem de ter um equivalente que as tecnologias de apoio consigam ler.
- **Controlar** — quem manda no ritmo, no movimento e na sequência é a pessoa que está a usar, não a aplicação.

Esta secção é a **secção de enquadramento** do módulo: trata da aplicação como um todo: a sua arquitetura, o seu ciclo de vida, as suas obrigações gerais. As três secções seguintes aprofundam três frentes específicas:

- a secção «Estruturas e Relações» trata de como se expõe a organização interna da aplicação;
- a secção «Ordem de Leitura e Foco» trata de percursos, sequência e gestão do foco;
- a secção «Notificações e Atualizações de Conteúdo» trata de como se comunicam mudanças que ocorrem sem o foco se mover.

Além disso, este módulo **parte do princípio de que o módulo sobre Widgets já foi feito**. Aqui não voltamos a tratar de como se declara o papel, o nome, o estado e o valor de um componente individual, nem das convenções de teclado de cada padrão. Aqui tratamos do **edifício**, não das maçanetas das portas.

---

### Como as Pessoas com Deficiência interagem com Aplicações Ricas

Antes de falar de requisitos e de código, é preciso perceber o que está realmente em jogo para cada pessoa. As dificuldades das aplicações ricas não são as mesmas para todos, e algumas são contraintuitivas.

#### Pessoas cegas que usam leitor de ecrã

Um leitor de ecrã não lê o ecrã. Lê uma **representação estruturada da página** que o navegador lhe fornece — a chamada árvore de acessibilidade — e, para permitir a leitura contínua com as setas, mantém uma espécie de **fotocópia navegável** desse conteúdo (o «modo de navegação», também conhecido como *browse mode* ou modo virtual).

Isto tem duas consequências decisivas em aplicações ricas:

**Primeira: mudar o ecrã não é o mesmo que avisar a pessoa.** Os leitores de ecrã modernos atualizam a sua fotocópia quando o conteúdo muda, mas **não anunciam espontaneamente** que mudou, nem para onde é que a pessoa deve ir a seguir. A pessoa pode continuar a ler tranquilamente uma zona que, no ecrã, já não existe da mesma forma, ou, pior, premir uma seta e cair num sítio completamente diferente daquele onde estava.

**Segunda: existem dois modos de funcionamento.** Em leitores de ecrã de ambiente Windows, como o NVDA e o JAWS, há um modo de navegação (as teclas servem para ler e saltar: `H` para cabeçalhos, `T` para tabelas, setas para percorrer texto) e um **modo de foco** ou modo de formulários (as teclas são entregues diretamente à aplicação, para se poder escrever num campo ou operar um componente com setas). A troca entre modos é normalmente automática, com base no tipo de componente que tem o foco.

> **Analogia:** o modo de navegação é o modo «visita guiada ao museu»: anda-se pela sala inteira, lê-se tudo, salta-se de quadro em quadro. O modo de foco é o modo «operar a máquina»: as teclas deixam de servir para andar e passam a servir para trabalhar. Uma aplicação rica bem construída deixa a pessoa alternar naturalmente entre visitar e operar. Uma aplicação mal construída prende a pessoa num dos modos.

Daqui resulta um alerta importante que se ouve pouco: **o conteúdo de uma aplicação rica continua a ter de poder ser lido, não apenas operado.** Uma interface onde só se consegue chegar ao conteúdo carregando em `Tab` (porque o texto está todo dentro de componentes interativos, ou porque a aplicação forçou o modo de aplicação) é uma interface onde a leitura corrida deixou de ser possível.

#### Pessoas com baixa visão que usam ampliação

Quem usa ampliação de ecrã a 400% vê, tipicamente, **uma pequena janela do ecrã de cada vez**. 

> **Analogia:** imagine que está a ler um jornal grande através de um tubo de papel. Consegue ler tudo, mas só um pedaço de cada vez, e tem de se lembrar onde está o resto.

Numa aplicação rica, isto cria um problema específico: **as mudanças acontecem frequentemente fora da janela visível**. A pessoa carrega num botão no canto inferior direito e a confirmação aparece no canto superior esquerdo; o total do carrinho atualiza-se numa barra lateral; um painel de filtros altera uma lista que está a três ecrãs de distância. Nada disto é percetível.

Acresce que aplicações ricas são particularmente propensas a **layouts que não sobrevivem à ampliação**: painéis lado a lado que se sobrepõem, barras de ferramentas fixas que ocupam metade da altura útil, tabelas de dados com dezenas de colunas, janelas modais que ficam maiores do que o ecrã e não permitem deslocamento.

#### Pessoas com deficiência motora

Para quem usa apenas teclado, um manípulo (*switch*), um ponteiro de cabeça ou controlo por voz, uma aplicação rica é sobretudo uma questão de **economia de movimentos**.

Cada interação custa. Numa aplicação com uma barra lateral de 40 ligações repetida em todas as vistas, chegar ao conteúdo pode custar 40 pressões de tecla — de cada vez. Numa aplicação que só se opera por arrastamento (arrastar um cartão de uma coluna para outra, arrastar um marcador num mapa, arrastar para reordenar), pode simplesmente não haver forma de operar.

Há ainda um problema muito frequente e muito subestimado: **as sessões que expiram**. Preencher um formulário longo com um manípulo pode demorar quarenta minutos. Uma sessão que termina ao fim de quinze e apaga tudo não é uma inconveniência, é uma exclusão.

#### Pessoas com deficiência cognitiva, dislexia ou perturbações da atenção

As aplicações ricas são, por natureza, **densas em informação e em possibilidades**. Isso cria dificuldades específicas:

- **Carga de memória.** Se a aplicação muda de vista sem deixar rasto (sem título, sem indicação de passo, sem histórico), a pessoa tem de guardar na cabeça onde está e como lá chegou.
- **Imprevisibilidade.** Coisas que acontecem sozinhas (painéis que se abrem ao passar o rato, conteúdos que se reordenam, campos que se submetem automaticamente) obrigam a reaprender a interface a cada utilização.
- **Irreversibilidade.** Sem «anular» e sem confirmação, o receio de errar transforma-se em receio de usar.
- **Pressão temporal.** Contadores, mensagens que desaparecem ao fim de três segundos e sessões que expiram penalizam quem precisa de mais tempo para ler e decidir.

#### Pessoas com epilepsia fotossensível ou perturbações vestibulares

As aplicações ricas usam muita animação: transições entre vistas, painéis que deslizam, elementos que se afastam a velocidades diferentes (*parallax*), listas que se reorganizam com movimento. Para quem tem perturbações vestibulares, movimento amplo no ecrã pode provocar náuseas e tonturas reais, com efeitos que duram horas. Para quem tem epilepsia fotossensível, intermitências rápidas podem desencadear crises.

#### Pessoas surdas ou com dificuldades auditivas

O impacto é menor no caso geral, mas existe em dois pontos concretos das aplicações ricas: **sinais sonoros usados como único meio de informar** (o «bip» que indica que a mensagem foi enviada, o som que assinala erro) e **conteúdo em tempo real** (videochamadas, transmissões, salas de conversação), onde é preciso garantir alternativas.

#### Uma história para juntar tudo

> A Marta é cega e usa o NVDA. Vai submeter um pedido de apoio numa plataforma pública, num formulário de quatro passos.
>
> Preenche o primeiro passo e carrega em «Seguinte». No ecrã, tudo muda: aparece o passo 2. Para a Marta, não acontece nada — o leitor de ecrã fica em silêncio. Ela carrega na seta para baixo e ouve «Rendimentos do agregado, campo de edição». Não sabe se avançou, se falhou alguma coisa, se ainda está no passo 1 ou já no 2. Sobe até ao topo com `Ctrl+Home` para tentar perceber, e ouve o mesmo cabeçalho de sempre: «Plataforma de Apoios». O título da janela também não mudou.
>
> A meio do passo 3, decide verificar um valor que introduziu no passo 1. Carrega em `Alt+Seta esquerda`, o atalho de retroceder do navegador. A aplicação nunca registou os passos no histórico: o navegador leva-a para fora da plataforma, para a página onde estava antes. Ao voltar, o formulário está vazio.

**O que corre mal aqui:** repare que **nenhum dos problemas da Marta é um problema de ARIA**. Todos os campos podem estar perfeitamente rotulados. O que falhou foi arquitetura: a mudança de vista não foi anunciada, o título não foi atualizado, o foco não foi recolocado e o histórico não foi alimentado. São exatamente as quatro primeiras das cinco coisas que o navegador fazia de graça.

---

### Requisitos de Acessibilidade para Aplicações Ricas

Os requisitos que se seguem são os requisitos **ao nível da aplicação**. Estão organizados pelos quatro princípios e cada um indica onde é aprofundado.

#### Anunciar

**R1 — Cada mudança significativa de vista tem de ser percetível sem ver o ecrã.**
Quando a aplicação substitui o conteúdo principal, tem de haver um sinal equivalente ao que o navegador daria: título atualizado, ponto de partida definido e, quando apropriado, um anúncio. A ausência de sinal é a falha número um das aplicações ricas.

**R2 — Os estados transitórios têm de existir para todos.**
«A carregar», «a guardar», «guardado», «falhou», «sem resultados» são informação, não decoração. Se só existirem como um ícone que roda ou como uma cor, não existem para uma parte das pessoas.

#### Preservar

**R3 — A aplicação tem de continuar a ser Web.**
Endereços que identificam o que está no ecrã, botão de retroceder funcional, possibilidade de partilhar ou guardar nos favoritos uma vista concreta, recarregar sem perder o sítio. Estas não são funcionalidades bonitas: são o mecanismo de orientação de que muitas pessoas dependem.

**R4 — A aplicação não pode anular as adaptações da pessoa.**
Ampliação até 200% sem perda de conteúdo ou funcionalidade (WCAG 1.4.4, AA), disposição adaptável a 320 CSS pixels de largura sem deslocamento nos dois eixos (WCAG 1.4.10, AA), espaçamento de texto ajustável (WCAG 1.4.12, AA), respeito pelas preferências do sistema quanto a movimento e cor, e atalhos do navegador e das tecnologias de apoio intocados (WCAG 2.1.4, A).

**R5 — O conteúdo tem de continuar legível, não apenas operável.**
Deve ser possível percorrer a aplicação em modo de leitura, com cabeçalhos, regiões e texto corrido acessíveis à leitura sequencial, e não apenas saltar entre controlos com `Tab`.

#### Expor

**R6 — O que é visível tem de ser programaticamente determinável.**
Se o ecrã mostra que há três filtros ativos, que a linha 4 está selecionada, que o separador «Documentos» é o que está aberto, essa informação tem de estar na marcação, e não apenas no estado interno do JavaScript ou numa classe CSS.

**R7 — Toda a funcionalidade tem de estar disponível por teclado.**
Sem exceções para funcionalidades «avançadas». Arrastar e largar, desenhar, redimensionar painéis, reordenar listas, tudo precisa de um caminho alternativo (WCAG 2.1.1, A; e sem armadilhas de teclado, 2.1.2, A).

#### Controlar

**R8 — A pessoa controla o tempo.**
Limites de tempo ajustáveis, adiáveis ou eliminados; avisos antes de expirar; dados preservados quando a sessão termina (WCAG 2.2.1, A). Conteúdos que se movem, piscam ou atualizam automaticamente durante mais de cinco segundos têm de poder ser pausados, parados ou ocultados (WCAG 2.2.2, A).

**R9 — Nada muda de contexto sem a pessoa pedir.**
Receber o foco não pode desencadear mudanças de contexto (WCAG 3.2.1, A); alterar um campo também não (WCAG 3.2.2, A). Guardar automaticamente é ótimo; **submeter** automaticamente não é.

**R10 — A pessoa controla o movimento.**
Nada pisca mais de três vezes por segundo (WCAG 2.3.1, A). E, embora WCAG 2.3.3 (Animação a partir de Interações) seja nível AAA, respeitar a preferência de movimento reduzido do sistema é hoje uma boa prática elementar e custa muito pouco a implementar.

---

## Técnicas de Codificação

As técnicas que se seguem são técnicas de **arquitetura da aplicação**. Não repetem as técnicas de componente individual do módulo sobre Widgets.

### T1 — Manter os elementos nativos como base, mesmo dentro de uma aplicação

O erro mais caro numa aplicação rica não é usar mal o ARIA: é ter deitado fora o HTML antes de chegar ao ARIA.

**Exemplo problemático:**

```html
<!-- Navegação principal de uma aplicação -->
<div class="nav">
  <div class="nav-item active" onclick="router.go('/inicio')">Início</div>
  <div class="nav-item" onclick="router.go('/pedidos')">Pedidos</div>
  <div class="nav-item" onclick="router.go('/perfil')">Perfil</div>
</div>
```

**Exemplo corrigido:**

```html
<nav aria-label="Principal">
  <ul>
    <li><a href="/inicio" aria-current="page">Início</a></li>
    <li><a href="/pedidos">Pedidos</a></li>
    <li><a href="/perfil">Perfil</a></li>
  </ul>
</nav>
```

```js
// O router intercepta o clique, mas o elemento continua a ser uma ligação real
document.querySelector('nav').addEventListener('click', (evento) => {
  const ligacao = evento.target.closest('a');
  if (!ligacao) return;
  // Deixar o navegador tratar de cliques com teclas modificadoras ou botão do meio
  if (evento.metaKey || evento.ctrlKey || evento.shiftKey || evento.button !== 0) return;
  evento.preventDefault();
  router.navegar(ligacao.getAttribute('href'));
});
```

**Porque é que a segunda versão é melhor:** as `<div>` da primeira versão não são anunciadas como ligações, não recebem foco com `Tab`, não respondem a `Enter`, não aparecem na lista de ligações do leitor de ecrã, não podem ser abertas num separador novo, não podem ser copiadas, e não permitem à pessoa saber qual é a vista atual. A segunda versão mantém tudo isso e continua a ser uma aplicação de página única: o `href` real serve de destino verdadeiro, o `preventDefault()` evita o recarregamento, e as combinações de teclas do navegador continuam a funcionar porque não são intercetadas.

> **Regra prática:** numa aplicação rica, se o elemento **leva a algum lado**, é `<a href>`. Se **faz alguma coisa**, é `<button>`. Se nenhum dos dois se aplica, provavelmente não devia ser clicável.

### T2 — Dar um endereço a cada vista e alimentar o histórico

**Exemplo problemático:**

```js
function mostrarVista(nome) {
  document.querySelector('#app').innerHTML = renderizar(nome);
  // O URL nunca muda: continua a ser https://exemplo.pt/app
}
```

**Exemplo corrigido:**

```js
function navegarPara(caminho) {
  history.pushState({ caminho }, '', caminho);   // 1. atualiza URL e histórico
  desenharVista(caminho);
}

// 2. Responder ao botão retroceder/avançar do navegador
window.addEventListener('popstate', (evento) => {
  desenharVista(evento.state?.caminho ?? location.pathname);
});

function desenharVista(caminho) {
  const vista = obterVista(caminho);
  document.querySelector('#app').replaceChildren(vista.conteudo);
  document.title = `${vista.titulo} — Plataforma de Apoios`;   // 3. título novo
  // A colocação do foco é tratada na secção «Ordem de Leitura e Foco»
}
```

**Porque é que a segunda versão é melhor:** a primeira versão quebra três coisas ao mesmo tempo — o endereço deixa de identificar o que está no ecrã (não se pode partilhar nem guardar nos favoritos), o botão de retroceder passa a atirar a pessoa para fora da aplicação, e recarregar a página faz perder o sítio. A segunda versão devolve as três. Repare também que `popstate` é tratado: sem isso, o botão de retroceder muda o endereço mas não muda o ecrã, o que é ainda mais confuso do que não funcionar de todo.

### T3 — Atualizar o título da página em cada mudança de vista

O título do documento é o rótulo mais barato e mais subutilizado de uma aplicação rica. É o que aparece no separador do navegador, na lista de janelas, no histórico, e é o que o leitor de ecrã anuncia quando a pessoa quer saber onde está.

**Exemplo problemático:**

```html
<title>Plataforma de Apoios</title>
<!-- ... e nunca mais muda, em nenhuma das 60 vistas da aplicação -->
```

**Exemplo corrigido:**

```js
// O mais específico primeiro, o nome do serviço no fim
document.title = 'Passo 2 de 4: Rendimentos — Pedido de apoio — Plataforma de Apoios';
```

**Porque é que a segunda versão é melhor:** quem tem doze separadores abertos vê «Plataforma de Apoios» doze vezes na primeira versão. Quem usa leitor de ecrã e pergunta «onde estou?» ouve sempre a mesma resposta. Na segunda versão, a informação distintiva vem à frente, o que é importante porque tanto os separadores do navegador como os leitores de ecrã cortam ou interrompem o texto pelo fim.

**Atenção a um detalhe:** mudar o `document.title` **não é, por si só, anunciado** pelos leitores de ecrã numa aplicação de página única. O título resolve a orientação («onde estou?»), não o anúncio («aconteceu alguma coisa»). O anúncio depende da gestão do foco, tratada na secção «Ordem de Leitura e Foco».

### T4 — Não bloquear a ampliação nem quebrar a adaptação da disposição

**Exemplo problemático:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```

```css
.painel-lateral { width: 320px; }
.area-trabalho  { width: calc(100% - 320px); float: left; }
.barra-topo     { position: fixed; height: 180px; }
```

**Exemplo corrigido:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

```css
.aplicacao {
  display: grid;
  grid-template-columns: minmax(15rem, 20rem) 1fr;
  gap: 1rem;
}

@media (max-width: 60rem) {
  .aplicacao { grid-template-columns: 1fr; }  /* passa a uma coluna */
}

.barra-topo {
  position: sticky;
  top: 0;
  max-height: 20vh;      /* nunca engole o ecrã quando se amplia */
  overflow: auto;
}
```

**Porque é que a segunda versão é melhor:** `user-scalable=no` e `maximum-scale=1` impedem literalmente a pessoa de ampliar em muitos dispositivos. É o equivalente digital a colar as lentes dos óculos. Na disposição, larguras fixas em pixels e barras fixas altas fazem com que, a 400% de ampliação, o conteúdo desapareça para fora do ecrã ou fique esmagado numa faixa de poucas linhas. A versão corrigida usa unidades relativas, define pontos de rutura em `rem` (que acompanham o tamanho de letra escolhido pela pessoa) e limita a altura das barras fixas.

### T5 — Garantir que o conteúdo existe verdadeiramente no DOM

Aplicações ricas usam frequentemente técnicas de desempenho (virtualização de listas, carregamento diferido, renderização por troços) que consistem, precisamente, em **não pôr o conteúdo no DOM**. O que não está no DOM não existe para as tecnologias de apoio.

**Exemplo problemático:**

```html
<!-- Lista "virtualizada" de 5000 resultados: só 20 existem no DOM -->
<div class="lista" style="height: 400px; overflow: auto">
  <div style="height: 200000px">
    <div class="linha">Resultado 341</div>
    <div class="linha">Resultado 342</div>
    <!-- ... apenas os visíveis; sem qualquer indicação de quantos são nem de onde estão -->
  </div>
</div>
```

**Exemplo corrigido:**

```html
<div class="lista"
     role="list"
     aria-label="Resultados da pesquisa">
  <p class="visualmente-oculto">A mostrar 341 a 360 de 5000 resultados.</p>
  <div role="listitem" aria-setsize="5000" aria-posinset="341">Resultado 341</div>
  <div role="listitem" aria-setsize="5000" aria-posinset="342">Resultado 342</div>
  <!-- ... -->
</div>
<button type="button">Mostrar mais 20 resultados</button>
```

**Porque é que a segunda versão é melhor:** na primeira, quem usa leitor de ecrã não faz ideia de que existem 5000 resultados nem de que posição está a ouvir; e chegar ao resultado 4000 exige simular um deslocamento visual que não tem equivalente por teclado. A segunda versão declara o tamanho total e a posição de cada item (`aria-setsize`, `aria-posinset`), dá uma indicação textual da fatia apresentada e oferece um mecanismo operável por teclado para carregar mais. A virtualização continua a existir; o que muda é que deixa de ser invisível.

### T6 — Tornar o ciclo de vida da aplicação visível na marcação

Toda a operação numa aplicação rica tem um ciclo: inativo → a decorrer → sucesso ou erro. Esse ciclo tem de estar na marcação, não apenas no CSS.

**Exemplo problemático:**

```html
<div class="painel a-carregar"></div>
<!-- O CSS mostra um ícone a rodar; para o leitor de ecrã, o painel está simplesmente vazio -->
```

**Exemplo corrigido:**

```html
<section aria-labelledby="titulo-pedidos">
  <h2 id="titulo-pedidos">Os meus pedidos</h2>

  <div id="lista-pedidos" aria-busy="true">
    <p>A carregar os seus pedidos…</p>
  </div>
</section>
```

```js
// Quando os dados chegam
lista.setAttribute('aria-busy', 'false');
lista.replaceChildren(tabelaDePedidos);
```

**Porque é que a segunda versão é melhor:** a primeira versão comunica o estado exclusivamente através de uma animação de CSS, invisível para quem não vê, e frequentemente também para quem tem o ecrã ampliado noutra zona. A segunda versão põe texto real no ecrã e usa `aria-busy` para indicar às tecnologias de apoio que aquela zona está em transição, evitando leituras de conteúdo a meio da atualização.

**Cuidado com o exagero:** `aria-busy` não é para pôr em toda a aplicação. Aplica-se à **região que está a mudar**, e tem de ser reposto a `false`. Um `aria-busy="true"` esquecido pode fazer com que uma zona inteira deixe de ser lida.

*A questão de **anunciar** que os dados chegaram — e não apenas de os expor — pertence à secção «Notificações e Atualizações de Conteúdo».*

### T7 — Dar à pessoa o controlo do tempo

**Exemplo problemático:**

```js
// Sessão de 15 minutos, sem aviso
setTimeout(() => {
  location.href = '/sessao-expirada';   // tudo o que estava preenchido perde-se
}, 15 * 60 * 1000);
```

**Exemplo corrigido:**

```js
const DURACAO = 20 * 60 * 1000;      // 20 minutos
const AVISO_ANTES = 2 * 60 * 1000;   // aviso 2 minutos antes

let temporizador;

function iniciarContagem() {
  clearTimeout(temporizador);
  temporizador = setTimeout(mostrarAviso, DURACAO - AVISO_ANTES);
}

function mostrarAviso() {
  guardarRascunhoLocal();            // os dados ficam salvaguardados
  abrirDialogoDeAviso();             // "A sua sessão termina em 2 minutos.
                                     //  [Continuar ligado]  [Terminar sessão]"
}

// Qualquer atividade real reinicia a contagem
['click', 'keydown'].forEach((tipo) =>
  document.addEventListener(tipo, iniciarContagem, { passive: true })
);
```

**Porque é que a segunda versão é melhor:** a primeira versão viola o critério 2.2.1 de forma direta. Não avisa, não permite prolongar, e destrói o trabalho feito. A segunda cumpre os três mecanismos que a WCAG aceita: **avisa** com antecedência suficiente, **permite prolongar** com uma ação simples, e **preserva os dados** para que, mesmo que a sessão termine, nada se perca. Repare que o aviso deve ser dado com pelo menos vinte segundos de antecedência e que a ação de prolongar tem de ser simples, não pode ser «volte a autenticar-se».

> **Exceções que a norma admite:** limites de tempo essenciais (um leilão que fecha à hora marcada, um exame cronometrado) ou superiores a 20 horas não estão sujeitos a esta exigência. Na prática, a esmagadora maioria dos temporizadores das aplicações que auditamos não são essenciais, são apenas política de segurança mal calibrada.

### T8 — Respeitar as preferências que a pessoa já configurou no sistema

Muitas pessoas já disseram ao sistema operativo o que precisam. A aplicação só tem de ouvir.

**Exemplo problemático:**

```css
.vista { transition: transform 400ms ease; }
.vista-a-entrar { transform: translateX(100%); }   /* sempre, para toda a gente */
```

**Exemplo corrigido:**

```css
.vista {
  transition: transform 400ms ease;
}

@media (prefers-reduced-motion: reduce) {
  .vista {
    transition-duration: 1ms;   /* praticamente instantâneo, mas sem quebrar eventos de fim de transição */
    animation: none;
  }
}
```

```js
// Também no JavaScript, quando há animação programática
const movimentoReduzido = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
elemento.scrollIntoView({ behavior: movimentoReduzido ? 'auto' : 'smooth' });
```

**Porque é que a segunda versão é melhor:** a primeira impõe movimento a toda a gente, incluindo a quem já configurou o sistema para o evitar por razões de saúde. A segunda respeita essa configuração sem exigir nenhuma definição adicional dentro da aplicação. Note-se o pormenor de usar `1ms` em vez de `0s`: mantém os eventos `transitionend` a disparar, evitando que a lógica da aplicação encrave.

O mesmo princípio aplica-se a `prefers-color-scheme`, `prefers-contrast` e ao tamanho de letra do sistema, que é respeitado se usar `rem` em vez de `px` para tipografia.

### T9 — Não confiscar o teclado

Aplicações ricas gostam de atalhos. O problema é que **o teclado já está ocupado**: pelo navegador, pelo sistema operativo e, sobretudo, pelas tecnologias de apoio, que usam praticamente todas as teclas de carácter único no seu modo de navegação.

**Exemplo problemático:**

```js
document.addEventListener('keydown', (evento) => {
  if (evento.key === 'n') criarNovoDocumento();
  if (evento.key === 'd') apagarSelecionado();
});
```

**Exemplo corrigido:**

```js
document.addEventListener('keydown', (evento) => {
  // Nunca intercetar quando a pessoa está a escrever
  const alvo = evento.target;
  if (alvo.matches('input, textarea, [contenteditable]')) return;

  // Atalhos com modificador: não colidem com o modo de navegação dos leitores de ecrã
  if (evento.altKey && evento.key === 'n') {
    evento.preventDefault();
    criarNovoDocumento();
  }
});
```

E, se realmente forem necessários atalhos de tecla única, tem de existir uma forma de os desligar ou reconfigurar:

```html
<fieldset>
  <legend>Atalhos de teclado</legend>
  <label><input type="checkbox" name="atalhos" checked> Ativar atalhos de tecla única</label>
</fieldset>
```

**Porque é que a segunda versão é melhor:** na primeira, um utilizador de NVDA que carregue em `D` para saltar para a próxima ligação apaga um documento. Isto não é um cenário teórico: é uma das causas mais frequentes de perda de dados relatada por utilizadores de leitores de ecrã. A segunda versão exige um modificador, ignora o atalho enquanto a pessoa escreve, e o painel de definições cumpre o critério 2.1.4, que exige que atalhos de tecla única possam ser desligados, remapeados ou limitados ao elemento com foco.

### T10 — Usar `role="application"` como último recurso, e quase nunca

Este é um dos erros mais destrutivos e menos compreendidos das aplicações ricas.

**Exemplo problemático:**

```html
<body role="application">
  <!-- toda a aplicação, incluindo textos, tabelas e formulários -->
</body>
```

**Exemplo corrigido:**

```html
<body>
  <!-- ... conteúdo normal, com HTML semântico ... -->

  <!-- Apenas o componente que precisa de teclas próprias, e só ele -->
  <div role="application" aria-label="Editor de partituras">
    <!-- componente com convenções de teclado próprias, totalmente implementadas -->
  </div>
</body>
```

**Porque é que a segunda versão é melhor:** `role="application"` diz ao leitor de ecrã «desliga o modo de navegação; todas as teclas passam a ser tuas». Aplicado ao `<body>`, isso significa que a pessoa **perde a capacidade de ler**. Não pode percorrer texto com as setas, não pode saltar por cabeçalhos, não pode usar a lista de ligações. Passa a depender exclusivamente daquilo que a aplicação implementou, que é quase sempre muito menos do que aquilo que o leitor de ecrã oferecia. É o equivalente a trancar as portas do museu e dizer aos visitantes que a partir de agora só se vê o que o guia entender mostrar.

### T11 — Escolher e avaliar bibliotecas de terceiros com critério

Numa aplicação rica, uma parte substancial da interface não é escrita por quem faz o projeto: vem de bibliotecas de componentes, grelhas de dados, editores de texto, calendários e mapas. E a acessibilidade dessas peças passa a ser responsabilidade de quem as integra.

Antes de adotar uma biblioteca, verifique:

- Se produz **HTML semântico** ou uma sopa de `<div>` com ARIA por cima.
- Se os componentes seguem os padrões do **ARIA Authoring Practices Guide**.
- Se existe uma **declaração de acessibilidade** ou um relatório de conformidade credível, e se é verificável, não apenas uma afirmação de marketing.
- Se permite **passar rótulos e descrições** aos elementos internos.
- Se a documentação fala de teclado e leitores de ecrã ou se o assunto está ausente.
- Se há **problemas de acessibilidade abertos** há anos no repositório público.

**Porque é que isto importa:** substituir uma grelha de dados inacessível a meio de um projeto custa, tipicamente, dez a cinquenta vezes mais do que ter escolhido outra no início. Esta é a decisão de acessibilidade mais cara que se toma numa aplicação rica, e é tomada normalmente na primeira semana, muitas vezes por quem nunca ouviu falar de WCAG.

### T12 — Construir por camadas, para que a falha seja parcial e não total

Uma aplicação rica que só funciona quando **tudo** funciona é frágil. Se o JavaScript falhar por causa de um erro numa componente secundária, de uma rede instável ou de um bloqueador de conteúdos, a aplicação não fica degradada, fica em branco.

**Exemplo problemático:**

```html
<body>
  <div id="root"></div>   <!-- se o JavaScript não correr, a página está vazia -->
  <script src="app.js"></script>
</body>
```

**Exemplo corrigido (renderização no servidor com enriquecimento posterior):**

```html
<body>
  <div id="root">
    <!-- Conteúdo real, entregue já montado pelo servidor -->
    <nav aria-label="Principal">…</nav>
    <main>
      <h1>Os meus pedidos</h1>
      <table>…</table>
    </main>
  </div>
  <script src="app.js" defer></script>
</body>
```

**Porque é que a segunda versão é melhor:** a segunda entrega conteúdo utilizável mesmo antes de o JavaScript executar, e continua utilizável se ele falhar. Isto beneficia toda a gente — ligações lentas, dispositivos antigos, redes públicas — mas beneficia desproporcionadamente quem depende de tecnologias de apoio, porque estas trabalham sobre o DOM que existe, e não sobre o que estava previsto existir.

Não é preciso abandonar as aplicações de página única para conseguir isto: a maioria das estruturas modernas suporta renderização no servidor. É uma decisão, não uma limitação técnica.

---

## Recomendações para Conteúdo Acessível

As técnicas anteriores são para quem escreve código. As recomendações seguintes são para quem **decide o que a aplicação faz** — desenho de interação, redação de conteúdo, gestão de produto. Muitas barreiras de acessibilidade em aplicações ricas nascem aqui, muito antes da primeira linha de código.

### Dar nome a cada vista, e usar sempre o mesmo nome

Se o botão diz «Submeter pedido», o título da vista seguinte não deve dizer «Confirmação de candidatura». A pessoa tem de conseguir ligar o que fez ao que aconteceu. Este alinhamento entre o nome visível e o nome usado em títulos, cabeçalhos e mensagens é o que sustenta a orientação em interfaces onde não há mudança de página.

### Manter a consistência entre vistas

O menu principal no mesmo sítio; o botão de guardar sempre no mesmo canto; os mesmos ícones a significar sempre a mesma coisa; a mesma palavra para a mesma ação (não «Anular» numa vista e «Cancelar» noutra). É o que os critérios 3.2.3 (Navegação Consistente) e 3.2.4 (Identificação Consistente) exigem, e é o que torna uma aplicação aprendível para quem tem dificuldades de memória ou de atenção.

### Escrever mensagens que dizem o que aconteceu e o que fazer a seguir

Compare:

> «Erro 422: pedido inválido.»

com

> «Não foi possível guardar o pedido porque o NIF tem 8 dígitos e deve ter 9. Corrija o campo NIF e volte a submeter.»

**O que funciona melhor na segunda:** identifica o que falhou, identifica o campo concreto, explica a regra e diz qual é o passo seguinte. A primeira só é útil para quem tem acesso aos registos do servidor.

### Não fazer depender informação de um único canal

Um ponto vermelho num separador, um ícone a rodar, um som de confirmação, uma animação de sucesso — nenhum destes elementos deve ser o **único** portador da informação. A regra prática: leia a interface em voz alta como se estivesse a descrevê-la a alguém ao telefone. O que não conseguir dizer é o que falta escrever.

### Deixar sempre uma saída

Em aplicações ricas, as pessoas experimentam. Sem «anular», sem confirmação para ações destrutivas e sem rascunhos guardados, experimentar torna-se arriscado, e quem não pode arriscar deixa de explorar, ficando limitado ao caminho mínimo que já conhece.

### Não pedir a mesma informação duas vezes

Se a pessoa já indicou a morada no passo 1, o passo 4 não deve voltar a pedi-la: deve mostrá-la, permitir confirmá-la ou permitir escolhê-la de uma lista. Reintroduzir informação é penoso para quem escreve devagar, para quem usa voz e para quem tem dificuldades de memória. 

### Desenhar para 400% desde o início

Se a interface só faz sentido em ecrãs largos, com quatro painéis lado a lado, o problema é de conceção, não de implementação. Pergunte cedo: *como é que esta vista se comporta quando só cabe uma coluna?* Não é uma pergunta sobre telemóveis. É a mesma pergunta que a ampliação a 400% coloca num ecrã de secretária.

### Documentar o comportamento esperado

Numa aplicação rica, «como é suposto isto funcionar com o teclado?» é uma pergunta que deve ter resposta escrita antes de haver código. Especificar, para cada componente e para cada mudança de vista, qual é a ordem, onde fica o foco e o que é anunciado, poupa mais tempo do que qualquer auditoria posterior.

---

### Erros Comuns

**1. A vista muda e nada é comunicado.**
O erro fundacional. Conteúdo novo no ecrã, silêncio para as tecnologias de apoio, foco no sítio onde estava.

**2. O URL nunca muda.**
Toda a aplicação vive em `/app`. Não se pode partilhar uma vista, guardar nos favoritos, nem recarregar sem voltar ao início.

**3. O botão de retroceder atira a pessoa para fora.**
Consequência direta do erro anterior, e uma das formas mais rápidas de fazer perder trabalho.

**4. O título da página é sempre o mesmo.**
Sessenta vistas, um só título. A resposta à pergunta «onde estou?» é sempre a mesma e nunca é útil.

**5. `role="application"` no `<body>`.**
Desliga o modo de leitura em toda a aplicação e transfere para o programador a responsabilidade de reimplementar tudo o que o leitor de ecrã já fazia.

**6. Ampliação bloqueada com `user-scalable=no`.**
Frequentemente copiado de exemplos antigos, sem intenção deliberada, e com impacto imediato para quem tem baixa visão.

**7. Atalhos de tecla única sem modificador nem forma de desligar.**
Colidem com os comandos de navegação dos leitores de ecrã e provocam ações destrutivas acidentais.

**8. Funcionalidade só operável com arrastamento.**
Reordenar, mover entre colunas, ajustar valores num controlo deslizante — sem alternativa por teclado ou por menu de ações.

**9. Sessões que expiram em silêncio e apagam o trabalho feito.**
Sem aviso, sem possibilidade de prolongar, sem rascunho guardado.

**10. Elementos clicáveis que não são botões nem ligações.**
`<div onclick>` e `<span onclick>` continuam a ser o padrão mais comum em aplicações ricas — não recebem foco, não respondem a `Enter` nem a `Espaço`, e não são anunciados como acionáveis.

**11. Estados que só existem em CSS.**
A cor de fundo indica que o separador está ativo, a opacidade indica que o botão está desativado, o negrito indica que a linha está selecionada. Nada disto chega às tecnologias de apoio.

**12. Animações e transições impostas a toda a gente.**
Sem respeitar `prefers-reduced-motion`, e frequentemente sem qualquer definição alternativa dentro da aplicação.

**13. Otimizações de desempenho que apagam informação.**
Listas virtualizadas sem `aria-setsize`/`aria-posinset`, deslocamento infinito sem alternativa por teclado, conteúdo que só existe quando está visível no ecrã.

**14. Delegar a acessibilidade à biblioteca de componentes sem verificar.**
«A biblioteca é acessível» é uma afirmação que precisa de prova, não de confiança.

**15. Testar apenas com ferramentas automáticas.**
Ferramentas como o AccessMonitor são úteis e obrigatórias no fluxo de trabalho, mas analisam o DOM num momento — e o problema central de uma aplicação rica é precisamente **o que acontece entre momentos**. Nenhuma ferramenta automática deteta que a mudança de vista não foi anunciada.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Uma aplicação rica é uma sala que se remonta à volta da pessoa.** O conteúdo muda sem que a página seja substituída, e por isso as mudanças não são sinalizadas automaticamente.

2. **O navegador deixou de fazer cinco coisas de graça:** anunciar o título, recolocar o ponto de partida, atualizar o endereço, alimentar o histórico e reconstruir a árvore de acessibilidade. Repor estas cinco funções é o núcleo do trabalho.

3. **Quatro princípios organizam o módulo:** anunciar o que mudou, preservar as garantias da Web, expor o que é visível e dar o controlo do tempo e do movimento à pessoa.

4. **Não é uma questão de ARIA.** A maior parte das falhas graves em aplicações ricas são falhas de arquitetura — endereços, histórico, títulos, foco, tempo — e não falhas de atributos.

5. **HTML nativo primeiro, mesmo dentro de uma aplicação.** Ligações reais para navegar, botões reais para agir; o encaminhamento do lado do cliente pode conviver perfeitamente com ambos.

6. **Cada vista precisa de identidade:** um endereço próprio, um título próprio e uma entrada no histórico.

7. **A aplicação não pode confiscar aquilo que não lhe pertence:** a ampliação, os atalhos do navegador, as teclas dos leitores de ecrã, as preferências do sistema.

8. **Estados transitórios são informação.** «A carregar», «guardado» e «falhou» têm de existir na marcação, e não apenas numa animação ou numa cor.

9. **O tempo é da pessoa.** Limites de tempo precisam de aviso, de forma de prolongar e de preservação dos dados.

10. **`role="application"` é quase sempre a resposta errada.** Desliga a leitura e obriga a reimplementar o que já funcionava.

11. **A escolha de bibliotecas é uma decisão de acessibilidade** — provavelmente a mais cara de todas — e é tomada logo no início do projeto.

12. **As ferramentas automáticas não veem o essencial.** O que falha nas aplicações ricas acontece entre estados, e só é detetável com teste manual por teclado e com leitor de ecrã.

### Exercícios Práticos

**Exercício 1 — Diagnóstico das cinco funções perdidas**
Escolha uma aplicação rica que use com frequência (área de cliente, plataforma pública, ferramenta de trabalho). Percorra três mudanças de vista e registe, para cada uma: o URL mudou? o título mudou? o botão de retroceder funciona? o foco mudou? houve algum anúncio? Produza uma tabela de cinco colunas e classifique cada mudança de vista de 0 a 5.

**Exercício 2 — A prova do rato desligado**
Desligue o rato (fisicamente, ou tape o *touchpad*). Execute uma tarefa completa numa aplicação rica — por exemplo, submeter um pedido ou alterar uma definição. Registe todos os pontos onde ficou bloqueado ou onde perdeu a noção de onde estava o foco.

**Exercício 3 — A prova dos 400%**
Amplie o navegador para 400% (`Ctrl` e `+`, cerca de sete vezes) numa aplicação rica. Identifique: conteúdo que desapareceu, sobreposições, barras fixas que ocupam o ecrã, deslocamento horizontal e funcionalidades que deixaram de estar acessíveis.

**Exercício 4 — Corrigir a navegação**
Pegue neste excerto e reescreva-o para que a navegação continue a funcionar como aplicação de página única, mas com elementos nativos, indicação da vista atual e endereços reais:

```html
<div class="menu">
  <span class="item sel" onclick="ir('resumo')">Resumo</span>
  <span class="item" onclick="ir('detalhe')">Detalhe</span>
</div>
```

**Exercício 5 — Reescrever um temporizador de sessão**
Uma aplicação termina a sessão ao fim de 10 minutos de inatividade e redireciona para a página de autenticação, perdendo o conteúdo do formulário. Escreva a especificação da correção: quanto tempo, que aviso, com que antecedência, com que opções, e o que acontece aos dados. Justifique cada decisão face ao critério 2.2.1.

**Exercício 6 — Auditar uma biblioteca**
Escolha uma biblioteca de componentes conhecida e avalie a sua grelha de dados (ou o seu calendário) segundo a lista da técnica T11. Produza uma recomendação de uma página: adotar, adotar com reservas, ou não adotar — com justificação.

**Exercício 7 — Especificar antes de codificar**
Para um formulário de candidatura em quatro passos, escreva a especificação de acessibilidade da mudança de passo, antes de existir código: o que acontece ao endereço, ao título, ao foco, ao histórico, e o que é anunciado. Guarde este documento — as secções seguintes deste módulo permitem-lhe verificar se acertou.

**Exercício 8 — Refazer o percurso da Marta**
Volte à história do início desta secção. Liste as cinco falhas concretas que a Marta encontrou e, para cada uma, indique a técnica desta secção que a resolveria. Depois indique quais das falhas seriam detetadas por uma ferramenta automática de avaliação. O resultado desta última pergunta costuma ser o argumento mais convincente numa reunião de projeto.

