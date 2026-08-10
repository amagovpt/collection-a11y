# Propriedades, Estados e Valores de Widgets

## Introdução

Na secção anterior vimos que qualquer widget tem de responder a três perguntas de forma que uma máquina consiga ler:

1. **O que é isto?** → a função
2. **Como se chama?** → o nome
3. **Como está agora?** → o estado, as propriedades e o valor

As duas primeiras perguntas já foram tratadas. Esta secção trata da terceira. E é, na prática, aquela onde mais projetos falham. É relativamente fácil declarar que um elemento é um botão. É muito mais fácil esquecer que, três semanas depois, alguém acrescentou uma animação de abrir e fechar e ninguém se lembrou de dizer ao navegador que o botão passou a ter dois estados.

> **Analogia: o painel de comandos da máquina de lavar**
>
> Voltemos ao painel de comandos da secção anterior. Já sabemos que cada comando parece o que é e está identificado. Falta o mais importante para quem está à frente da máquina: **saber em que ponto está**.
>
> - A **propriedade** é aquilo que o comando é por natureza e que raramente muda: este botão tem uma lâmpada; este seletor vai de 30 °C a 90 °C; este programa é obrigatório escolher antes de arrancar.
> - O **estado** é a situação atual, que muda com o uso: a lâmpada está acesa ou apagada; a porta está bloqueada ou destrancada.
> - O **valor** é o número ou o conteúdo que o comando tem neste momento: 40 °C, 1200 rotações, "Algodões".
>
> Uma máquina de lavar em que a lâmpada nunca acende continua a lavar. Simplesmente ninguém sabe se está a lavar. É exatamente isto que acontece a um utilizador de leitor de ecrã num acordeão sem `aria-expanded`: a página funciona, mas ele não faz ideia do que aconteceu.

### As três palavras, sem confusão

Estes três termos são usados quase como sinónimos na conversa do dia a dia, mas em acessibilidade têm significados distintos. Vale a pena fixá-los:

| Termo | O que é | Muda com a interação? | Exemplos em ARIA |
|---|---|---|---|
| **Propriedade** | Uma característica do widget, normalmente estável, que descreve como ele se comporta ou com o que se relaciona | Raramente | `aria-haspopup`, `aria-controls`, `aria-required`, `aria-valuemin`, `aria-valuemax`, `aria-readonly` |
| **Estado** | A condição em que o widget está neste momento | Sim, frequentemente | `aria-expanded`, `aria-checked`, `aria-pressed`, `aria-selected`, `aria-disabled`, `aria-invalid`, `aria-current` |
| **Valor** | O conteúdo ou a quantidade que o widget tem agora | Sim | `aria-valuenow`, `aria-valuetext`, o `value` de um `<input>` |

Na prática, a fronteira entre propriedade e estado não é rígida. A própria especificação ARIA admite que é uma distinção de conveniência. O que interessa reter é outra coisa: **tudo isto tem de estar escrito no código, e não apenas desenhado no ecrã**.

> **Nota de âmbito.** Esta secção trata de *como declarar* estados, propriedades e valores. Não trata de:
>
> - **Função e nome** do widget → secção 1 (*Widgets*);
> - **Como se opera** o widget (teclado, foco, rato, toque, fala) → secções 3, 4 e 5;
> - **Como anunciar mudanças noutra zona da página** (um contador de carrinho que se atualiza sozinho, uma mensagem de sucesso) → secção 6 (*Regiões Dinâmicas*). Aqui interessa-nos o estado **do próprio widget**;
> - **Widgets compostos** (separadores, árvores, grelhas), onde os estados se combinam entre vários elementos → secção 7 (*Widgets Complexos*);
> - **Campos de formulário nativos** (`<input>`, `<select>`, mensagens de erro), tratados no módulo de *Formulários Acessíveis*. Referimo-los apenas quando servem de contraste.

---

### Como as Pessoas com Deficiência acedem a Propriedades, Estados e Valores de Widgets

Antes de decidir o que codificar, é preciso perceber o que chega ao outro lado.

#### Utilizadores de leitores de ecrã

O leitor de ecrã não vê a seta a rodar nem a caixa a mudar de cor. Lê a ficha do elemento na árvore de acessibilidade. Quando essa ficha está completa, ouve-se algo como:

> "Detalhes da encomenda, botão, contraído"

Quando o programador esqueceu o estado, ouve-se:

> "Detalhes da encomenda, botão"

A diferença parece pequena. Não é. No primeiro caso o utilizador sabe que há conteúdo escondido e que aquele botão o revela. No segundo, tem um botão que aparentemente não faz nada. Carrega, ouve silêncio, e conclui que a página está avariada.

Igualmente importante: quando o estado muda, o leitor de ecrã **anuncia a mudança automaticamente**, desde que o elemento que mudou seja o que está em foco. Não é preciso truque nenhum para isso. Basta que o atributo mude no DOM.

#### Utilizadores de linha braille

Os estados aparecem em braille de forma abreviada e muito condensada. Um estado em falta não deixa nenhum rasto. Não há entoação nem pausa que compense. A linha braille é implacável: o que não está no código não existe.

#### Pessoas com baixa visão ou daltonismo

Estas pessoas *veem* o widget, mas podem não distinguir o sinal escolhido para marcar o estado. Se a única diferença entre um filtro ativo e um filtro inativo for o verde e o cinzento, cerca de 8 % dos homens terão dificuldade em perceber quais os filtros ativos. Se o indicador de foco ou a moldura de uma caixa selecionada tiver contraste insuficiente contra o fundo, o mesmo se aplica.

#### Pessoas com deficiência cognitiva

Um símbolo sozinho raramente é auto-explicativo. Um `+` que passa a `×`, um ponto colorido, uma seta invertida, tudo isto exige que o utilizador infira uma convenção. Texto explícito ("Mostrar detalhes" / "Ocultar detalhes") elimina a inferência.

#### Utilizadores de comando por voz e de tecnologias alternativas

Quem controla o computador por voz precisa de saber se um botão está disponível antes de tentar acioná-lo. Quem usa um manípulo (*switch*) percorre os controlos em série: se um botão desativado continuar a ser anunciado como disponível, o utilizador gasta tempo e esforço num controlo que não vai reagir.

#### O problema central: a dessincronização

Quase todos os problemas desta secção se reduzem a uma frase: **o ecrã diz uma coisa e o código diz outra**.

O CSS mudou de cor, a `<div>` apareceu, a seta rodou, mas o atributo continuou como estava. Para quem vê, tudo funcionou. Para quem depende do código, nada aconteceu. É o equivalente digital de uma porta de vidro em que a luz de "ocupado" está avariada: quem vê lá para dentro adapta-se; quem não vê, bate à porta.

---

### Requisitos de Acessibilidade para transmitir Propriedades, Estados e Valores de Widgets

Podemos resumir tudo em sete requisitos.

**1. O estado tem de ser determinável programaticamente**
Se um widget tem estados, esses estados têm de estar no código através do elemento nativo apropriado ou de um atributo ARIA. É a essência do critério *4.1.2 Nome, Função, Valor*.

**2. O estado tem de estar sincronizado com o que se vê**
Não basta declarar o estado uma vez no HTML inicial. Sempre que o widget muda, o atributo muda **no mesmo momento**. Um estado desatualizado é pior do que um estado ausente: transmite informação falsa.

**3. O estado tem de ser percetível visualmente, e não só pela cor**
Cor mais forma, mais texto, mais ícone. Nunca cor sozinha (*1.4.1 Utilização da Cor*). E os indicadores gráficos de estado precisam de contraste suficiente contra o que está à volta (*1.4.11 Contraste Não-Textual*).

**4. As instruções não podem depender só da aparência ou da posição**
"Carregue no botão verde à direita" exclui várias pessoas de uma vez (*1.3.3 Características Sensoriais*). "Carregue em Confirmar" não exclui ninguém.

**5. Os valores têm de ter significado humano**
Um controlo deslizante que anuncia "72" pode não dizer nada. "72 euros" ou "sexta-feira" dizem tudo. É para isto que existe o `aria-valuetext`.

**6. Só se declaram estados que a função suporta**
`aria-expanded` num `<h2>` sem função interativa não faz sentido e é ignorado ou mal interpretado. Cada função ARIA aceita um conjunto definido de estados e propriedades; usar outros é ruído, quando não é erro.

**7. As relações relevantes têm de estar declaradas**
Se um botão abre um menu, isso é uma propriedade dele (`aria-haspopup`). Se controla um painel, isso é outra (`aria-controls`). Estas propriedades são pistas de navegação, não decoração.

---

## Técnicas de Codificação

### Regra zero: o elemento nativo já traz o estado incluído

Antes de escrever um único atributo ARIA, vale a pena lembrar que o HTML já resolve grande parte do problema, de graça e sem JavaScript.

```html
<!-- Nativo: o estado está incluído -->
<input type="checkbox" id="rgpd" checked>
<label for="rgpd">Aceito a política de privacidade</label>

<button type="button" disabled>Submeter</button>

<details>
  <summary>Detalhes da encomenda</summary>
  <p>Encomenda n.º 4821, entregue a 12 de março.</p>
</details>
```

**O que funciona bem:** o `checked`, o `disabled` e o abrir/fechar do `<details>` são comunicados automaticamente à árvore de acessibilidade pelo navegador. O leitor de ecrã anuncia "caixa de verificação, marcada", "botão, indisponível", "Detalhes da encomenda, contraído". Não escrevemos ARIA nenhum e não escrevemos JavaScript nenhum, e mesmo assim tudo está lá, incluindo a atualização automática quando o utilizador interage.

A primeira pergunta a fazer perante um widget não é "que ARIA é que ponho aqui?", mas sim **"existe um elemento HTML que já faça isto?"**. ARIA é o remendo para quando não existe.

---

### `aria-expanded`: o estado mais frequente e o mais esquecido

Aplica-se a tudo o que revela e esconde conteúdo: acordeões, botões de menu, campos de pesquisa que se abrem, painéis laterais.

```html
<!-- Mau exemplo -->
<div class="cabecalho-acordeao" onclick="alternar(this)">
  <span class="seta">▸</span> Horário de funcionamento
</div>
<div class="painel" hidden>
  <p>Segunda a sexta, das 9h às 18h.</p>
</div>
```

**O que corre mal:** três falhas de uma vez. A `<div>` não é anunciada como botão, não é alcançável por teclado, e — o que nos interessa aqui — **não há qualquer estado**. A seta `▸` é a única indicação de que aquilo abre e fecha, e é puramente visual. Quem usa leitor de ecrã encontra um texto solto, não sabe que é acionável, e se por acaso o acionar não fica a saber que alguma coisa mudou.

```html
<!-- Bom exemplo -->
<h3>
  <button type="button" id="btn-horario"
          aria-expanded="false"
          aria-controls="painel-horario">
    Horário de funcionamento
  </button>
</h3>
<div id="painel-horario" role="region"
     aria-labelledby="btn-horario" hidden>
  <p>Segunda a sexta, das 9h às 18h.</p>
</div>
```

```js
const botao = document.querySelector('#btn-horario');
const painel = document.querySelector('#painel-horario');

botao.addEventListener('click', () => {
  const expandido = botao.getAttribute('aria-expanded') === 'true';
  botao.setAttribute('aria-expanded', String(!expandido));
  painel.hidden = expandido;
});
```

```css
/* A seta é gerada a partir do estado, não do estado a partir da seta */
#btn-horario::before { content: "▸"; display: inline-block; }
#btn-horario[aria-expanded="true"]::before { transform: rotate(90deg); }
```

**O que funciona bem:** o `<button>` traz a função e a operação por teclado incluídas. O `aria-expanded` diz o estado e é atualizado no mesmo `click` que esconde ou mostra o painel. Não há hipótese de dessincronizar, porque é a mesma linha de código. O `aria-controls` liga o botão ao painel que ele comanda. E repare no CSS: **o estilo é derivado do atributo**, com um seletor `[aria-expanded="true"]`. Isto é mais do que elegância. Significa que é impossível a seta apontar para baixo e o atributo dizer `false`, porque a seta *depende* do atributo. É a técnica mais eficaz que existe para evitar dessincronização: uma única fonte de verdade.

Note-se que o texto do botão não muda ("Horário de funcionamento" continua a ser "Horário de funcionamento"). Isto é intencional. O nome identifica o widget; o `aria-expanded` diz a situação. Se o texto mudasse para "Ocultar horário", estaríamos a dizer o estado duas vezes, e de forma potencialmente contraditória.

---

### `aria-pressed`, `aria-checked` e `aria-selected`: três estados parecidos, usos diferentes

Esta é uma fonte clássica de confusão. A diferença está no **tipo de widget**, não no aspeto.

| Estado | Quando usar | Função associada |
|---|---|---|
| `aria-pressed` | Botão que fica "carregado", como o negrito de um editor de texto | `button` |
| `aria-checked` | Escolha de uma opção: caixa de verificação, botão de opção, interruptor | `checkbox`, `radio`, `switch`, `menuitemcheckbox` |
| `aria-selected` | Item escolhido dentro de um conjunto: um separador, uma opção de lista | `tab`, `option`, `gridcell`, `row` |

> **Analogia:** o `aria-pressed` é a tecla de *Caps Lock* — fica em baixo, e continua a agir enquanto lá estiver. O `aria-checked` é o interruptor da luz da sala — liga ou desliga uma coisa. O `aria-selected` é o dedo a apontar para um item de uma lista — não liga nada, escolhe qual é o que está em cima.

```html
<!-- Botão alternado: negrito num editor -->
<button type="button" aria-pressed="false">Negrito</button>

<!-- Interruptor: uma definição com efeito imediato -->
<button type="button" role="switch" aria-checked="false" id="sw-notif">
  Notificações por email
</button>
```

**O que funciona bem:** ambos partem de um `<button>` real, pelo que a operação por teclado vem de graça. No primeiro caso o leitor anuncia "Negrito, botão de alternância, não premido"; no segundo, "Notificações por email, interruptor, desligado". O utilizador percebe imediatamente que tipo de controlo tem à frente e em que posição está.

```html
<!-- Mau exemplo -->
<button type="button" class="ativo" aria-pressed="true">Negrito</button>
```
com

```js
botao.addEventListener('click', () => {
  botao.classList.toggle('ativo');   // só muda a classe
});
```

**O que corre mal:** o `aria-pressed="true"` foi escrito à mão no HTML e nunca mais é tocado. O JavaScript alterna a classe CSS e ignora o atributo. Resultado: o botão diz eternamente "premido", mesmo quando não está. **Um estado congelado é uma mentira permanente**. Pior do que a ausência de estado, porque o utilizador confia nele e age em conformidade.

---

### `disabled` vs. `aria-disabled`: uma distinção com consequências

```html
<!-- Opção A: desativação nativa -->
<button type="button" disabled>Guardar</button>

<!-- Opção B: desativação declarada -->
<button type="button" aria-disabled="true">Guardar</button>
```

**Diferença essencial:** o `disabled` nativo remove o botão da ordem de tabulação — deixa de ser alcançável por teclado. O `aria-disabled` anuncia que está indisponível mas **mantém-no alcançável**; cabe ao programador impedir a ação no JavaScript.

**Quando usar cada um:** o `disabled` é simples e correto na maioria dos casos. Mas um botão que desaparece da tabulação também desaparece da exploração. O utilizador de leitor de ecrã pode nunca descobrir que existe um botão "Guardar", nem porque é que está indisponível. Num formulário longo em que o botão só fica ativo no fim, o `aria-disabled` costuma ser a melhor opção: o utilizador encontra o botão, ouve que está indisponível, e pode procurar a explicação. 

**A regra que não muda:** seja qual for a opção, o estilo visual de "indisponível" tem de acompanhar o atributo, e o cinzento não pode ser a única pista.

---

### Valores: `aria-valuenow`, `aria-valuemin`, `aria-valuemax`, `aria-valuetext`

Aplicam-se a widgets que representam uma quantidade numa escala: controlos deslizantes, medidores, barras de progresso, botões de incremento.

```html
<!-- Mau exemplo -->
<div class="slider" role="slider" aria-valuenow="3"
     aria-label="Prazo de entrega"></div>
```

**O que corre mal:** faltam os limites da escala, pelo que o utilizador não sabe se 3 é pouco ou muito — 3 em 5? 3 em 100? E "3" é um número sem unidade: 3 dias, 3 semanas, 3 meses? O leitor de ecrã anuncia "Prazo de entrega, 3" e o utilizador fica exatamente na mesma.

```html
<!-- Bom exemplo -->
<div role="slider" tabindex="0"
     aria-label="Prazo de entrega"
     aria-valuemin="1" aria-valuemax="5"
     aria-valuenow="3"
     aria-valuetext="3 dias úteis"></div>
```

**O que funciona bem:** os limites dão contexto ("3 de 1 a 5") e o `aria-valuetext` substitui o número cru por algo que uma pessoa entende: "Prazo de entrega, 3 dias úteis". Quando existe `aria-valuetext`, é ele que é anunciado, mas o `aria-valuenow` continua a ser obrigatório porque é ele que descreve a posição na escala.

> **Quando é que o `aria-valuetext` é indispensável?** Sempre que o número, sozinho, não seja compreensível: escalas cujos valores são datas, dias da semana, tamanhos ("Pequeno", "Médio", "Grande"), escalões de preço, níveis qualitativos. Se o número já é claro por si — uma percentagem, por exemplo — o `aria-valuetext` é dispensável.

Antes de construir um `role="slider"` à mão, note-se que existe `<input type="range">`, que traz tudo isto incluído. A versão em `<div>` só se justifica quando o comportamento exigido não é possível com o elemento nativo. E implica reimplementar toda a operação por teclado.

---

### Propriedades de relação: `aria-controls`, `aria-haspopup`, `aria-owns`

Estas propriedades não descrevem o widget em si: descrevem **com o que é que ele se relaciona**.

```html
<button type="button" aria-haspopup="menu" aria-expanded="false"
        aria-controls="menu-conta" id="btn-conta">
  A minha conta
</button>
<ul role="menu" id="menu-conta" hidden>
  <li role="menuitem"><a href="/perfil">Perfil</a></li>
  <li role="menuitem"><a href="/sair">Terminar sessão</a></li>
</ul>
```

**O que funciona bem:** o `aria-haspopup="menu"` avisa que aquele botão não executa uma ação — abre um menu. O utilizador ouve "A minha conta, botão, menu contraído" e sabe o que esperar antes de carregar. Sem o `aria-haspopup`, carregar num botão pode significar navegar para outra página, submeter um formulário ou abrir um menu, e a única forma de descobrir é experimentar.

**Cuidado com o `aria-controls`:** o suporte é irregular nos leitores de ecrã. É correto e útil, mas não se deve depender dele para transmitir informação essencial. E o valor tem de ser um `id` que existe mesmo na página. Um `aria-controls` a apontar para um elemento inexistente é ignorado.

---

### `aria-current`: assinalar "onde estamos"

```html
<nav aria-label="Principal">
  <ul>
    <li><a href="/">Início</a></li>
    <li><a href="/servicos" aria-current="page">Serviços</a></li>
    <li><a href="/contactos">Contactos</a></li>
  </ul>
</nav>
```

**O que funciona bem:** o `aria-current="page"` marca a página atual de forma que o leitor de ecrã anuncie "Serviços, página atual, ligação". O sublinhado ou o realce que normalmente marcam a página ativa são apenas visuais; isto acrescenta a versão legível por máquina. Aceita outros valores conforme o contexto: `step` num assistente de vários passos, `date` num calendário, `true` como valor genérico.

**Erro frequente:** marcar várias ligações com `aria-current` ao mesmo tempo. Só pode existir uma "atual" dentro do mesmo conjunto.

---

### Tabela de referência rápida

| Situação | Estado ou propriedade | Valores |
|---|---|---|
| Abre e fecha conteúdo | `aria-expanded` | `true` / `false` |
| Botão que fica carregado | `aria-pressed` | `true` / `false` / `mixed` |
| Opção marcada ou desmarcada | `aria-checked` | `true` / `false` / `mixed` |
| Item escolhido num conjunto | `aria-selected` | `true` / `false` |
| Controlo indisponível | `aria-disabled` (ou `disabled`) | `true` / `false` |
| Campo com erro | `aria-invalid` | `true` / `false` |
| Preenchimento obrigatório | `aria-required` (ou `required`) | `true` / `false` |
| Só de leitura | `aria-readonly` | `true` / `false` |
| Posição atual numa escala | `aria-valuenow` + `min`/`max` | número |
| Versão legível do valor | `aria-valuetext` | texto |
| Abre um menu ou diálogo | `aria-haspopup` | `menu`, `dialog`, `listbox`, `tree`, `grid` |
| Comanda outro elemento | `aria-controls` | `id` de um elemento existente |
| Item atual num percurso | `aria-current` | `page`, `step`, `date`, `true` |

Os estados de campos de formulário (`aria-invalid`, `aria-required`) foram tratados em detalhe no módulo de *Formulários Acessíveis* e aparecem aqui apenas para completar o quadro.

---

## Recomendações para Conteúdo Acessível

**Um estado, três canais.** O estado deve ser percetível por quem vê (forma, ícone, texto), por quem não distingue cores (algo mais além da cor), e por quem não vê (o atributo). Se um dos três falhar, alguém fica de fora.

**Escolha uma fonte de verdade e derive tudo dela.** Como no exemplo do acordeão: o CSS lê o atributo. Assim o aspeto nunca pode contradizer o código, porque depende dele. Esta única decisão de arquitetura elimina a maior categoria de erros desta secção.

**Não diga o estado duas vezes.** Um botão com texto "Ocultar detalhes" **e** `aria-expanded="true"` faz o leitor de ecrã anunciar "Ocultar detalhes, botão, expandido" — informação redundante e, se o JavaScript falhar a atualizar um dos dois, contraditória. Escolha uma abordagem:

- **texto fixo + `aria-expanded`** (recomendada, e mais simples de manter); ou
- **texto que muda** ("Mostrar" ↔ "Ocultar") **sem `aria-expanded`**, opção defensável em widgets simples mas que perde a semântica de expansível.

**Prefira palavras a símbolos.** Um "+" que se transforma em "−" é uma convenção que muitas pessoas conhecem — e que outras tantas não. Texto visível ao lado do símbolo serve toda a gente e não estorva ninguém.

**Verifique o contraste dos indicadores.** A moldura que marca uma opção selecionada, o ponto que marca um botão de opção, o traço que sublinha o separador ativo — todos precisam de contraste suficiente contra o que está imediatamente à volta. Um cinzento-claro elegante sobre branco pode ser invisível para muita gente.

**Explique porque é que algo está indisponível.** Um botão cinzento sem explicação é um beco sem saída. "Guardar (preencha os campos obrigatórios primeiro)" transforma um obstáculo numa instrução.

**Seja consistente em todo o produto.** Se o azul preenchido marca "ativo" numa página, não pode marcar "desativado" na página seguinte. A consistência não é uma questão estética: é o que permite que a pessoa aprenda a interface uma vez em vez de a reaprender em cada ecrã.

**Teste com o leitor de ecrã antes de dar a tarefa por concluída.** Navegue até ao widget, acione-o, e pergunte-se: *ouvi o estado mudar?* Se ouviu silêncio, o widget está incompleto, por muito bonito que esteja o ecrã. Cinco minutos com o NVDA ou o VoiceOver detetam mais problemas desta secção do que qualquer ferramenta automática, porque as ferramentas automáticas conseguem ver que o atributo existe, mas não conseguem ver que ele mentiu.

---

### Erros Comuns

**1. O estado só existe em CSS**

```html
<!-- Errado -->
<button type="button" class="filtro ativo">Em stock</button>
```
A classe `ativo` só significa alguma coisa para o CSS e para o programador que a escreveu. A árvore de acessibilidade não sabe o que é uma classe. Faltava aqui `aria-pressed="true"`.

**2. O atributo é escrito uma vez e nunca atualizado**
O erro mais frequente de todos. O HTML inicial tem `aria-expanded="false"` e o JavaScript esquece-se de o mudar. O widget passa a vida a dizer que está fechado.

**3. Estado numa função que não o suporta**

```html
<!-- Errado -->
<div role="button" aria-selected="true">Aplicar</div>
```
A função `button` não aceita `aria-selected`. O atributo é ignorado, e o programador fica convencido de que resolveu o problema. Consulte sempre quais os estados que a função em causa suporta.

**4. Confundir `aria-pressed` com `aria-checked`**
Um botão "Adicionar aos favoritos" que fica marcado é um `aria-pressed`. Um interruptor de definições é um `role="switch"` com `aria-checked`. Trocar os dois faz o leitor de ecrã anunciar um tipo de controlo que não corresponde ao que a pessoa tem à frente.

**5. `aria-checked` sem `role`**

```html
<!-- Errado -->
<div aria-checked="true">Receber newsletter</div>
```
Sem função declarada, o estado não tem onde assentar. É como pintar a lâmpada de verde sem ligar fio nenhum.

**6. Valores sem escala**
`aria-valuenow="7"` sem `aria-valuemin` nem `aria-valuemax`. Sete de quantos?

**7. O estado só se distingue pela cor**
Separadores em que o ativo é azul e os outros cinzentos, sem sublinhado, sem negrito, sem `aria-selected`. Falha para daltónicos e falha para leitores de ecrã: dois problemas distintos com a mesma origem, confiar num único canal.

**8. Vários `aria-current` no mesmo conjunto**
Se tudo é atual, nada é atual.

**9. Reinventar o que já existe**

```html
<!-- Errado -->
<div role="checkbox" tabindex="0" aria-checked="false"
     onclick="alternar(this)">Aceito os termos</div>
```
Trinta segundos de trabalho para reproduzir mal aquilo que `<input type="checkbox">` faz bem. E ainda falta implementar a barra de espaços, o estado indeterminado e a integração com o formulário. Este é o resumo de toda a secção: **quando existe elemento nativo, ARIA é trabalho a mais para um resultado pior.**

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Esta secção responde à terceira pergunta de qualquer widget: **como está agora?**
- **Propriedade** é o que o widget é (estável); **estado** é como está (muda); **valor** é quanto ou o quê.
- O elemento HTML nativo já traz o estado incluído e atualizado. Use-o sempre que exista.
- O `aria-expanded` é o estado mais comum e o mais esquecido. Tudo o que abre e fecha precisa dele.
- `aria-pressed` (botão carregado), `aria-checked` (opção ligada) e `aria-selected` (item escolhido) não são intermutáveis.
- Valores numa escala precisam de `aria-valuemin`, `aria-valuemax` e `aria-valuenow` — e de `aria-valuetext` quando o número, sozinho, não é compreensível.
- **Um estado congelado é pior do que um estado ausente.** Atualize o atributo na mesma linha de código que muda o aspeto.
- Faça o CSS depender do atributo (`[aria-expanded="true"]`). É a forma mais fiável de garantir que o ecrã e o código nunca se contradizem.
- Cor sozinha nunca chega. Acrescente forma, ícone ou, melhor ainda, texto.
- Só se declaram estados que a função do widget suporta.

### Exercícios Práticos

**Exercício 1 — Diagnóstico**
Analise o código seguinte e identifique **quatro** problemas relacionados com estados e propriedades. Para cada um, indique o impacto concreto num utilizador de leitor de ecrã.

```html
<div class="tab ativo" onclick="mostrar('geral')">Geral</div>
<div class="tab" onclick="mostrar('envio')">Envio</div>
<div class="tab" onclick="mostrar('pagamento')">Pagamento</div>
```
```css
.tab { color: #767676; }
.tab.ativo { color: #0a5ca8; }
```

**Exercício 2 — Correção**
Corrija o acordeão seguinte. Deve acrescentar o estado em falta, ligar o botão ao painel e garantir que o CSS deriva do atributo em vez de o duplicar.

```html
<div class="acordeao" onclick="this.nextElementSibling.classList.toggle('aberto')">
  <img src="seta.png" alt="seta"> Política de devoluções
</div>
<div class="conteudo">
  <p>Aceitamos devoluções até 14 dias após a receção.</p>
</div>
```

**Exercício 3 — Construção**
Construa um interruptor ("Modo de alto contraste") a partir de um `<button>`, com `role="switch"` e `aria-checked` corretamente sincronizado. Requisitos:

- o estado tem de ser percetível sem depender da cor;
- o texto do rótulo não muda com o estado;
- o CSS deve derivar do atributo.

**Exercício 4 — Escolha de valores**
Para cada controlo deslizante, decida se precisa de `aria-valuetext` e escreva o texto que proporia:

| Controlo | Escala | `aria-valuetext`? |
|---|---|---|
| Percentagem de zoom | 50 a 200 | ? |
| Dia de entrega | 1 a 7 | ? |
| Escalão de preço | 1 a 4 | ? |
| Volume | 0 a 100 | ? |

**Exercício 5 — Teste com leitor de ecrã**
Escolha um sítio web da administração pública portuguesa com um menu suspenso ou um acordeão. Com o NVDA (Windows) ou o VoiceOver (macOS), navegue até ao widget e acione-o. Registe:

1. O que é anunciado antes de acionar;
2. O que é anunciado depois de acionar;
3. Se conseguiria perceber o resultado da ação sem ver o ecrã;
4. Que atributo estará em falta ou desatualizado, se for o caso.

**Exercício 6 — Discussão**
Um colega defende que `disabled` é sempre melhor do que `aria-disabled`, porque "não deixa a pessoa carregar num botão que não funciona". Apresente dois argumentos contra e indique um caso concreto em que `aria-disabled` seja a melhor escolha.

