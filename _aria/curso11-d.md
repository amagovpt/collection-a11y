---
title: Notificações e Atualizações de Conteúdo
layout: default
nav_order: 4
---
# Notificações e Atualizações de Conteúdo

## Introdução

As secções anteriores trataram de três coisas: o que é uma aplicação rica e o que ela retira ao navegador (secção «Aplicações Ricas»), como se expõe a sua organização interna (secção «Estruturas e Relações») e como se garante que existe um percurso coerente e um foco bem gerido (secção «Ordem de Leitura e Foco»).

Falta uma peça — e é aquela que, na prática, mais falha.

Numa aplicação rica, **grande parte do que acontece não acontece onde a pessoa está**. O botão «Guardar» fica no fundo do formulário, mas a confirmação aparece no topo. Os filtros estão à esquerda, mas o número de resultados muda à direita. A pessoa está a escrever um relatório e, num canto do ecrã, aparece um aviso de que a sessão expira dentro de dois minutos.

Para quem vê o ecrã inteiro de uma só vez, isto resolve-se com um relance. Para quem não vê o ecrã, ou vê apenas uma pequena parte dele de cada vez, **uma mudança que não é comunicada é uma mudança que não existe**.

Esta secção trata exatamente disso: de como uma aplicação rica comunica o que mudou, a quem, com que urgência e durante quanto tempo.

### A analogia central: a cabina de um avião

Numa cabina de avião existem centenas de coisas a mudar ao mesmo tempo. Se todas avisassem o piloto, ninguém conseguiria pilotar. Se nenhuma avisasse, ninguém conseguiria aterrar. A solução foi criar **níveis**:

- **Aviso (*warning*)** — luz vermelha e som. Exige ação imediata. Interrompe tudo o resto.
- **Atenção (*caution*)** — luz âmbar. Exige atenção, mas não neste segundo.
- **Informação (*advisory*)** — aparece num mostrador. Está lá para quem for ver.
- **Registo (*log*)** — tudo fica escrito. Mesmo o que passou despercebido pode ser consultado depois.

E existe um problema clássico, documentado na aviação e na medicina: a **fadiga de alarme**. Quando tudo apita, o cérebro deixa de distinguir o que importa — e o alarme que realmente conta passa a ser ignorado como os outros.

> **Guarde esta ideia:** uma aplicação acessível não é a que anuncia tudo. É a que **anuncia a coisa certa, no nível certo, e guarda o resto onde possa ser consultado**. O silêncio e a cacofonia são falhas simétricas.

Esta analogia acompanha toda a secção: sempre que estiver a decidir como comunicar uma mudança, a pergunta é «isto é um aviso, uma atenção, uma informação ou apenas registo?».

### O que conta como notificação ou atualização

Vale a pena não meter tudo no mesmo saco. As mudanças de conteúdo têm **origens diferentes**, e a origem determina o tratamento.

| Origem da mudança | Exemplos | A pessoa está à espera? |
|---|---|---|
| **Resposta direta a uma ação** | «Guardado», «Ficheiro eliminado», erro de validação | Sim — acabou de fazer alguma coisa |
| **Progresso de um processo** | «A carregar…», barra de progresso, «12 de 40 enviados» | Sim, mas pode ter mudado de tarefa |
| **Resultado que muda noutro sítio** | Contagem de resultados após filtro, total do carrinho | Talvez — pode não saber que aquilo mudou |
| **Dados novos vindos do servidor** | Nova mensagem, novo comentário, cotação atualizada | Não — não pediu nada |
| **Passagem do tempo** | Sessão a expirar, contagem decrescente, atualização automática | Não — e pode estar a meio de outra coisa |
| **Ação de outra pessoa** | «A Ana editou este parágrafo», documento colaborativo | Não |

**O que isto muda na prática:** quanto mais abaixo na tabela, mais a mudança é uma **interrupção** e menos é uma **resposta**. Uma resposta a uma ação pode e deve ser confirmada de imediato. Uma interrupção tem de ser doseada, tem de poder ser adiada e, muitas vezes, tem de poder ser desligada.

### Onde acaba esta secção e começam as outras

Para evitar repetições, fixemos as fronteiras:

- **Se a resposta correta é mover o foco** (abrir um diálogo, entrar numa nova vista, saltar para o primeiro campo com erro), o assunto é da secção «Ordem de Leitura e Foco». Aqui tratamos do que fazer **quando o foco não se move**.
- **Se o que muda é a organização da aplicação** (marcos, cabeçalhos, relações entre zonas), o assunto é da secção «Estruturas e Relações».
- **Se o que muda é o estado de um componente individual** (`aria-expanded`, `aria-checked`, `aria-selected`, valor de um cursor deslizante), o assunto foi tratado no módulo sobre Widgets. Aqui interessa-nos o nível da **aplicação**, não o do botão.
- **A validação de formulários** tem tratamento próprio no módulo sobre Formulários. Aqui aparece apenas na parte que é arquitetura de notificação: onde vai a mensagem, com que urgência, e como se coordena com o resto.
- **A lista consolidada de critérios WCAG** fica na secção «Conclusão e Boas Práticas». Ao longo desta secção há apenas referências pontuais, no contexto em que fazem sentido.

---

### Como as Pessoas com Deficiência percebem as Notificações e Atualizações de Conteúdo

#### Um dia de trabalho que corre mal

> O **Rui** é técnico administrativo numa autarquia e é cego. Usa NVDA e conhece bem o *backoffice* onde regista pedidos de licenciamento.
>
> Preenche um pedido longo e carrega em «Submeter». Silêncio. Espera. Volta a carregar em «Submeter», porque não faz ideia se a primeira vez funcionou. Só quando percorre a página com as setas descobre, a meio, um texto encarnado: «O NIF indicado já tem um pedido em curso». A mensagem estava no ecrã há dois minutos — e o segundo clique criou um pedido duplicado.
>
> A seguir, aplica um filtro para ver apenas os pedidos de 2026. A lista muda. Ninguém lhe diz quantos resultados há. Percorre 40 linhas até perceber que o filtro devolveu zero resultados e que o que está a ler é a lista antiga, ainda em memória no leitor de ecrã.
>
> Por fim, ao escrever um parecer, ouve de repente, a meio de uma frase: **«A sua sessão expira dentro de 60 segundos.»** A frase que estava a ler foi cortada. Procura o botão para continuar ligado, não o encontra a tempo, e perde o texto.

**O que corre mal aqui:** três falhas diferentes, que convém não confundir.

1. A confirmação **existia em texto, mas não foi comunicada** — foi escrita no ecrã sem qualquer mecanismo que a anunciasse.
2. O resultado do filtro **nem sequer existia em texto** — o número de resultados só existia na perceção visual da lista.
3. O aviso de sessão **foi comunicado, mas com o nível errado e demasiado tarde** — interrompeu a leitura em curso e não deu tempo útil para agir.

Note-se que nenhuma destas falhas se resolve com ARIA nos campos. São falhas de **arquitetura de comunicação**.

#### Pessoas cegas que usam leitor de ecrã

Como se viu na secção «Aplicações Ricas», o leitor de ecrã trabalha sobre uma representação estruturada da página e, no modo de navegação, sobre uma cópia navegável desse conteúdo. Daqui decorrem quatro consequências para as notificações:

- **Escrever no ecrã não é falar.** Inserir texto no DOM não produz, por si só, qualquer anúncio.
- **O anúncio é efémero.** Ao contrário do texto no ecrã, que fica lá para ser relido, o anúncio passa. Se a pessoa estava a falar ao telefone, se o leitor estava a meio de outra frase, se a mensagem foi demasiado longa — perdeu-se. Rever o que foi anunciado é possível em alguns leitores de ecrã, mas é uma operação de recurso, que a maioria das pessoas não faz no dia a dia.
- **Um anúncio urgente corta o que estava a ser dito.** É o equivalente sonoro de alguém falar por cima. Usado com parcimónia, salva. Usado por sistema, torna a aplicação inutilizável.
- **A leitura tem um ritmo próprio.** Quem lê em braille avança linha a linha, à sua velocidade. Conteúdo que se reescreve sozinho por baixo da leitura é conteúdo que se perde.

#### Pessoas com baixa visão que usam ampliação

Este é o grupo mais esquecido no desenho de notificações.

> **Analogia:** usar o ecrã com ampliação a 400% é como ver uma sala através de um rolo de papel. A sala continua toda lá — mas de cada vez só se vê um palmo dela.

Uma notificação que aparece no canto inferior direito, enquanto a pessoa trabalha no canto superior esquerdo, **simplesmente não acontece**. E, quando desaparece ao fim de quatro segundos, nem sequer deixa rasto para ser encontrada mais tarde.

Há ainda um problema inverso: notificações fixas no topo ou no fundo do ecrã (barras de *cookies*, avisos de sistema, «toasts» persistentes) ocupam, em ecrã ampliado, uma fatia enorme do espaço visível e podem **tapar precisamente o elemento que tem o foco**.

#### Pessoas surdas ou com perda auditiva

Qualquer notificação que dependa **apenas** de um som — um *bip* ao chegar mensagem, um sinal sonoro de erro — não existe para estas pessoas. O som pode ser um reforço; nunca o único canal.

#### Pessoas com limitações motoras

O problema aqui é o **tempo**. Uma notificação com uma ação associada («Mensagem eliminada. **Anular**») que desaparece em quatro segundos exige alcançar um alvo, no ecrã, em quatro segundos. Para quem usa um manípulo, varrimento, controlo ocular ou apontador de cabeça, quatro segundos podem não chegar sequer para atravessar meio ecrã.

O mesmo se aplica a contagens decrescentes de sessão e a conteúdos que se atualizam automaticamente por baixo do ponteiro: clicar no sítio certo depende de o sítio certo continuar no mesmo lugar.

#### Pessoas com dificuldades cognitivas, de atenção ou de memória

Para este grupo, o excesso é tão incapacitante como a falta:

- Notificações a aparecer e a desaparecer partem a linha de raciocínio e obrigam a recomeçar a tarefa.
- Mensagens vagas («Ocorreu um erro», «Operação não concluída») não dizem o que fazer a seguir.
- Conteúdo que se atualiza sozinho enquanto se lê obriga a reencontrar o sítio onde se ia.
- Informação crítica que só aparece durante alguns segundos exige memória de trabalho que nem toda a gente tem disponível.

Pessoas com ansiedade ou com perturbações do foro cognitivo são também as mais afetadas por avisos alarmistas e por contagens decrescentes visíveis e permanentes.

#### Pessoas sensíveis a movimento

Notificações que entram a deslizar, a saltar ou a piscar podem provocar desconforto, náusea ou, em casos extremos, crises. A informação é necessária; a animação, quase nunca.

#### O denominador comum

Repare que todos estes grupos precisam da mesma coisa, por razões diferentes:

**A informação tem de existir em texto, chegar sem obrigar a procurar, não interromper mais do que o necessário e permanecer acessível depois do momento em que apareceu.**

São os quatro princípios que organizam o resto desta secção: **Existir, Chegar, Dosear, Persistir**.

---

### Requisitos de Acessibilidade para Notificações e Atualizações de Conteúdo

#### Existir

**R1 — Toda a mudança significativa tem de existir como texto.**
Um ícone que roda, uma linha que muda de cor, um número que aparece a verde: nada disto é informação para toda a gente. Se a mudança importa, tem de haver **texto** que a descreva.
*Relaciona-se com WCAG 1.4.1 (Utilização de Cor, A) e 4.1.3 (Mensagens de Estado, AA).*

**R2 — As mensagens de estado têm de ser percetíveis sem receber o foco.**
Confirmações, erros, contagens de resultados e avisos de progresso têm de ser comunicados **sem obrigar a mover o foco** para eles. Esta é a formulação literal do critério 4.1.3, e é o requisito estruturante desta secção.
*WCAG 4.1.3 (Mensagens de Estado, AA).*

**R3 — Os erros têm de ser identificados em texto e ligados ao seu contexto.**
Não basta dizer que houve um erro: tem de se dizer **qual** e **onde**.
*WCAG 3.3.1 (Identificação de Erro, A) e 3.3.3 (Sugestão para Erros, AA). O tratamento detalhado da validação está no módulo sobre Formulários.*

#### Chegar

**R4 — O canal tem de ser proporcional à consequência.**
Uma confirmação de gravação não pode ser tratada como um alarme; uma perda iminente de dados não pode ser tratada como um sussurro. Cada mensagem tem de ser encaminhada para o nível certo.

**R5 — A notificação visual tem de ser encontrável a partir do ponto de ação.**
Quem tem o ecrã ampliado só vê a zona onde está a trabalhar. Sempre que possível, a confirmação ou o erro devem aparecer **junto ao elemento que os provocou**, e não num canto distante.
*Relaciona-se com WCAG 1.4.10 (Refluxo, AA).*

**R6 — A notificação não pode tapar o que a pessoa está a usar.**
Barras, faixas e «toasts» fixos não devem cobrir o elemento que tem o foco.
*A WCAG 2.2 formalizou isto no critério 2.4.11 (Foco Não Obscurecido — Mínimo, AA). A base legal atual em Portugal assenta na WCAG 2.1, pelo que este ponto deve ser entendido como boa prática já consolidada e como preparação para a atualização da norma.*

#### Dosear

**R7 — Interromper é a exceção, não a regra.**
Cortar a fala de um leitor de ecrã, roubar o foco ou abrir um diálogo modal são atos de força. Justificam-se quando há risco de perda de dados, de segurança ou de tempo; não se justificam para dizer «Guardado».
*Relaciona-se com WCAG 3.2.1 (Em Foco, A) e 3.2.2 (Ao Introduzir Dados, A).*

**R8 — Conteúdo que se move, pisca ou se atualiza automaticamente tem de poder ser pausado, parado ou ocultado.**
Aplica-se a tickers, feeds em tempo real, carrosséis de avisos e listas que se reordenam sozinhas, sempre que durem mais de cinco segundos e coexistam com outro conteúdo.
*WCAG 2.2.2 (Colocar em Pausa, Parar, Ocultar, A).*

**R9 — Idealmente, as interrupções devem poder ser adiadas ou suprimidas pela própria pessoa.**
Um modo «não incomodar» durante uma tarefa longa é uma funcionalidade de acessibilidade, não um luxo.
*WCAG 2.2.4 (Interrupções) é de nível AAA — está acima da base legal, mas é uma boa prática com impacto real, sobretudo em aplicações de trabalho usadas muitas horas por dia.*

#### Persistir

**R10 — Tem de haver tempo suficiente para ler e para agir.**
Se existe um limite de tempo, tem de ser possível desligá-lo, ajustá-lo ou prolongá-lo com um aviso atempado.
*WCAG 2.2.1 (Temporização Ajustável, A).*

**R11 — Nada de importante pode existir apenas numa mensagem efémera.**
Se uma mensagem contém uma ação (anular, tentar de novo, ver detalhes) ou informação que a pessoa vai precisar de reler, tem de existir também num sítio permanente.

**R12 — Deve existir forma de rever o que foi comunicado.**
Um registo, um centro de notificações, uma zona de estado sempre presente. É o «livro de bordo» da analogia da cabina: quem falhou o aviso pode ir consultá-lo.

---

## Técnicas de Codificação

### T1 — Escolher o canal antes de escrever código

A primeira decisão não é técnica, é editorial. Antes de escolher `role` ou `aria-live`, responda a três perguntas:

1. **A pessoa perde alguma coisa se não souber disto?** Se não, não anuncie.
2. **Tem de agir imediatamente?** Se sim, é aviso. Se não, é atenção ou informação.
3. **A resposta certa é levá-la a outro sítio?** Se sim, o assunto é gestão de foco (secção «Ordem de Leitura e Foco»), não notificação.

A tabela seguinte resume o encaminhamento:

| Situação | Canal recomendado | Interrompe? |
|---|---|---|
| Confirmação de uma ação («Guardado») | `role="status"` | Não |
| Contagem de resultados após filtro ou pesquisa | `role="status"` | Não |
| Progresso de uma operação longa | `role="status"` com marcos, ou `role="progressbar"` | Não |
| Chegada de dados novos não solicitados | `role="status"` com resumo, ou botão «Mostrar novidades» | Não |
| Erro de validação após submissão | `role="alert"` **ou** mover o foco para o resumo de erros | Sim |
| Falha que impede a pessoa de continuar | `role="alert"` | Sim |
| Perda iminente de dados ou de sessão | Diálogo com `role="alertdialog"` e foco | Sim, deliberadamente |
| Registo contínuo (conversa, consola, histórico) | `role="log"` | Não |

**O que funciona bem nesta tabela:** a esmagadora maioria das mensagens de uma aplicação cai na primeira linha — e a primeira linha não interrompe ninguém.

**O que corre mal quando não se faz esta triagem:** a equipa cria um único componente de notificação, configura-o como `assertive` «para garantir», e passa a cortar a fala do leitor de ecrã dezenas de vezes por sessão. É a fadiga de alarme, transposta para a Web.

### T2 — A região de estado tem de existir antes de ter conteúdo

Esta é a causa número um de «pus `aria-live` e não anuncia nada».

O leitor de ecrã tem de **conhecer** a região antes de ela mudar. Se a região for criada e preenchida ao mesmo tempo, muitas combinações de navegador e leitor de ecrã não anunciam nada.

**Exemplo incorreto:**

```javascript
// A região nasce já com o texto lá dentro
function confirmar(mensagem) {
  const div = document.createElement('div');
  div.setAttribute('role', 'status');
  div.textContent = mensagem;
  document.body.appendChild(div);
}
```

**Exemplo correto:**

```html
<!-- Existe desde o carregamento da página, vazia -->
<div id="zona-estado" role="status" class="apenas-leitor-ecra"></div>
```

```javascript
const zonaEstado = document.getElementById('zona-estado');

function anunciar(mensagem) {
  // Limpar e escrever no ciclo seguinte garante que a mudança é detetada,
  // mesmo quando a mensagem é igual à anterior.
  zonaEstado.textContent = '';
  window.setTimeout(() => { zonaEstado.textContent = mensagem; }, 100);
}

anunciar('Pedido guardado.');
```

E a classe que a esconde visualmente sem a esconder das tecnologias de apoio:

```css
.apenas-leitor-ecra {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  white-space: nowrap;
  border: 0;
}
```

**O que funciona bem:** a região está no DOM desde o início, o leitor de ecrã já a «vigia», e qualquer texto que lá seja escrito é anunciado. Limpar antes de escrever resolve o caso de duas mensagens iguais seguidas — que, sem isso, não seriam detetadas como mudança.

**O que corre mal com `display: none` ou com o atributo `hidden`:** uma região escondida dessa forma **não anuncia**. Se precisar de esconder visualmente, use a técnica de recorte acima; se precisar de esconder mesmo, então não é uma região de estado.

> **Nota importante:** o texto de uma região de estado nunca deve ser gerado por CSS, através de `::before` ou `::after`. Esse texto não é conteúdo do documento e pode não chegar às tecnologias de apoio. O texto tem de estar no HTML.

### T3 — `status`, `alert` e `log`: o que cada um faz

Estes três papéis são regiões dinâmicas com configurações já definidas. Usá-los é preferível a montar `aria-live` à mão, porque trazem o comportamento correto por omissão.

| Papel | Equivalente | Lê a região toda? | Quando usar |
|---|---|---|---|
| `role="status"` | `aria-live="polite"` + `aria-atomic="true"` | Sim | Confirmações, contagens, progresso |
| `role="alert"` | `aria-live="assertive"` + `aria-atomic="true"` | Sim | Erros e situações que exigem ação imediata |
| `role="log"` | `aria-live="polite"` + `aria-atomic="false"` | Não, só o que foi acrescentado | Conversas, históricos, consolas |

**Exemplo — confirmação simples:**

```html
<div role="status" class="apenas-leitor-ecra"></div>
```

**Exemplo — erro que impede continuar:**

```html
<div role="alert" class="aviso-erro">
  Não foi possível guardar: a ligação ao servidor falhou. Tente novamente.
</div>
```

**Exemplo — registo de conversa:**

```html
<div role="log" aria-label="Conversa">
  <p><strong>Ana:</strong> Bom dia.</p>
  <p><strong>Rui:</strong> Bom dia, já enviei o documento.</p>
</div>
```

**O que funciona bem:** com `role="log"`, apenas a mensagem nova é lida. Se fosse `role="status"`, cada nova mensagem faria o leitor de ecrã reler a conversa inteira — o que torna qualquer conversa com mais de cinco linhas impossível de seguir.

**O que corre mal com o uso indiscriminado de `role="alert"`:** um `alert` interrompe. Se a aplicação usar `alert` para «Rascunho guardado automaticamente» de dois em dois minutos, a pessoa é interrompida a meio de cada frase que lê. Não é acessibilidade; é sabotagem bem-intencionada.

> Existe ainda o elemento `<output>`, que já se comporta como `role="status"` e é a escolha natural para resultados calculados a partir de campos de formulário: `<output id="total">0,00 €</output>`.

### T4 — Anunciar mudanças de vista sem duplicar a gestão do foco

Quando a aplicação troca de vista, há três sinais a emitir, e é importante não os confundir nem os duplicar:

1. **Título do documento** — para o histórico, os separadores e as tecnologias de apoio.
2. **Ponto de partida** — o foco, tratado na secção «Ordem de Leitura e Foco».
3. **Anúncio** — apenas quando o ponto 2 não for suficiente.

```javascript
function mudarVista(titulo) {
  document.title = titulo + ' — Plataforma de Apoios';

  const cabecalho = document.querySelector('#conteudo-principal h1');
  cabecalho.textContent = titulo;
  cabecalho.setAttribute('tabindex', '-1');
  cabecalho.focus(); // ponto de partida
}
```

**O que funciona bem:** o foco no cabeçalho faz com que o leitor de ecrã leia o título da nova vista **naturalmente**, sem qualquer anúncio adicional. O título do documento fica correto para quem navega por separadores ou usa o histórico.

**O que corre mal se acrescentar também um anúncio:** a pessoa ouve «Pedidos de licenciamento, cabeçalho de nível 1» seguido de «Navegou para Pedidos de licenciamento». Duas vezes a mesma informação. **Se o foco se move para o sítio certo, não anuncie.** O anúncio serve para os casos em que o foco fica onde estava — por exemplo, quando a mudança é parcial e a pessoa continua a trabalhar no mesmo painel.

### T5 — Estados de carregamento e progresso

Uma operação longa tem três momentos a comunicar: começou, vai a meio, acabou. O erro comum é comunicar o meio com demasiada frequência.

**Exemplo incorreto:**

```javascript
// Atualiza a percentagem a cada tick — dezenas de anúncios por segundo
barra.setAttribute('aria-valuenow', percentagem);
zonaEstado.textContent = `A carregar: ${percentagem}%`;
```

**Exemplo correto:**

```html
<button id="btn-importar">Importar ficheiro</button>

<div id="zona-progresso" role="status" class="apenas-leitor-ecra"></div>

<div id="barra" role="progressbar"
     aria-label="Progresso da importação"
     aria-valuemin="0" aria-valuemax="100" aria-valuenow="0"></div>
```

```javascript
let ultimoMarco = -1;

function atualizarProgresso(percentagem) {
  // O valor visual/programático acompanha tudo:
  barra.setAttribute('aria-valuenow', percentagem);

  // O anúncio só acontece em marcos de 25%:
  const marco = Math.floor(percentagem / 25);
  if (marco > ultimoMarco) {
    ultimoMarco = marco;
    document.getElementById('zona-progresso').textContent =
      `Importação a ${marco * 25} por cento.`;
  }
}

function terminar(numeroRegistos) {
  document.getElementById('zona-progresso').textContent =
    `Importação concluída. ${numeroRegistos} registos importados.`;
}
```

**O que funciona bem:** o valor exato está sempre disponível para quem o quiser consultar (na `progressbar`), mas os anúncios são quatro, não quatrocentos. E a mensagem final é útil: diz **o resultado**, não apenas que acabou.

**O que corre mal na versão incorreta:** o leitor de ecrã entra num monólogo contínuo de percentagens, impossível de interromper, e a pessoa não consegue fazer mais nada enquanto isso durar.

Para zonas que ficam temporariamente inconsistentes durante uma atualização em bloco, `aria-busy` evita anúncios a meio:

```javascript
lista.setAttribute('aria-busy', 'true');
// ... redesenhar as 200 linhas ...
lista.setAttribute('aria-busy', 'false');
```

### T6 — Pesquisa e filtros: dizer sempre quantos

Sempre que um filtro, uma pesquisa ou uma ordenação muda uma lista, o resultado tem de ser dito. E, se a pesquisa acontece enquanto se escreve, tem de haver um atraso deliberado.

```html
<label for="pesquisa">Pesquisar pedidos</label>
<input type="search" id="pesquisa" aria-controls="lista-pedidos">

<p id="contador" role="status"></p>

<ul id="lista-pedidos"><!-- resultados --></ul>
```

```javascript
let temporizador;

document.getElementById('pesquisa').addEventListener('input', (evento) => {
  clearTimeout(temporizador);
  temporizador = setTimeout(() => {
    const resultados = filtrar(evento.target.value);
    desenharLista(resultados);

    document.getElementById('contador').textContent =
      resultados.length === 0
        ? 'Nenhum pedido corresponde à pesquisa.'
        : `${resultados.length} pedidos encontrados.`;
  }, 700);
});
```

**O que funciona bem:** o atraso de 700 ms garante que o anúncio acontece quando a pessoa faz uma pausa, e não a cada tecla premida. O caso de zero resultados é tratado explicitamente — é precisamente o caso em que o silêncio é mais enganador, porque a lista antiga pode continuar a ser lida como se fosse a nova.

**O que corre mal sem atraso:** escrever «licenciamento» produz treze anúncios consecutivos, cada um a cortar o anterior. Na prática, a pessoa não ouve nenhum deles até parar de escrever — e nessa altura já perdeu a informação intermédia.

### T7 — «Toasts» que não deixam ninguém para trás

O «toast» — a caixinha que aparece num canto e desaparece sozinha — é o padrão mais problemático das aplicações ricas. Não é proibido; exige regras.

```html
<!-- Contentor fixo, presente desde o início -->
<div id="area-toasts" role="status" aria-label="Notificações"
     class="area-toasts"></div>
```

```javascript
function mostrarToast(texto, { acao = null, persistente = false } = {}) {
  const caixa = document.createElement('div');
  caixa.className = 'toast';
  caixa.textContent = texto;

  if (acao) {
    const botao = document.createElement('button');
    botao.type = 'button';
    botao.textContent = acao.rotulo;
    botao.addEventListener('click', acao.executar);
    caixa.appendChild(botao);
  }

  // Botão de fechar sempre disponível
  const fechar = document.createElement('button');
  fechar.type = 'button';
  fechar.textContent = 'Fechar notificação';
  fechar.addEventListener('click', () => caixa.remove());
  caixa.appendChild(fechar);

  document.getElementById('area-toasts').appendChild(caixa);

  // Só desaparece sozinho se não tiver ação associada
  if (!acao && !persistente) {
    setTimeout(() => caixa.remove(), 8000);
  }
}
```

```css
.toast { transition: opacity 200ms ease; }

@media (prefers-reduced-motion: reduce) {
  .toast { transition: none; }
}
```

As regras que este código concretiza:

- **Não rouba o foco.** O «toast» é uma informação, não uma interrupção.
- **Tem sempre forma de fechar**, para quem usa ampliação e precisa de libertar o ecrã.
- **Se tem uma ação, não desaparece sozinho.** Um botão «Anular» com quatro segundos de vida é inutilizável para muita gente.
- **Se desaparece, dura o suficiente** — oito segundos é um mínimo razoável para mensagens curtas.
- **Respeita a preferência de movimento reduzido.**
- **A ação existe também noutro sítio.** Se a pessoa fechou o «toast» de «Pedido eliminado — Anular», tem de conseguir recuperar o pedido a partir de uma lista de eliminados ou de um histórico.

**O que corre mal no «toast» típico:** aparece no canto inferior direito (fora do campo de visão de quem usa ampliação), desaparece em quatro segundos (curto demais para quem usa varrimento ou controlo ocular), contém a única forma de anular a operação (informação crítica em suporte efémero) e desliza para dentro com uma animação (desconfortável para quem é sensível a movimento). Quatro barreiras num componente com quinze palavras.

### T8 — Quando a notificação exige uma decisão

Se a aplicação **não pode continuar** sem uma resposta, então já não é uma notificação: é uma pergunta. Nesse caso, o canal correto é um diálogo modal com `role="alertdialog"`, foco gerido e devolvido, e uma saída clara.

```html
<div role="alertdialog" aria-labelledby="tit-aviso" aria-describedby="desc-aviso">
  <h2 id="tit-aviso">A sessão vai terminar</h2>
  <p id="desc-aviso">
    A sua sessão termina dentro de 5 minutos por inatividade.
    O trabalho não guardado será perdido.
  </p>
  <button type="button" id="continuar">Continuar ligado</button>
  <button type="button" id="terminar">Terminar sessão agora</button>
</div>
```

**O que funciona bem:** o aviso chega com **cinco minutos** de antecedência, e não sessenta segundos; diz explicitamente qual é a consequência; e a ação principal está a um clique.

**O que corre mal quando se usa um diálogo para tudo:** cada confirmação de gravação passa a exigir um clique para fechar. É a diferença entre um alarme e uma campainha de porta tocada a cada dez segundos.

### T9 — Dados que chegam sozinhos: nunca reorganizar debaixo dos dedos

Numa lista que recebe atualizações do servidor — mensagens, pedidos, comentários — inserir conteúdo novo no topo faz com que tudo o resto se desloque. Para quem usa ampliação, o que estava a ler saiu do campo de visão. Para quem usa apontador, o botão que ia premir mudou de sítio. Para quem usa leitor de ecrã, a posição de leitura deixa de corresponder ao conteúdo.

**Exemplo incorreto:**

```javascript
socket.on('novoPedido', (pedido) => {
  lista.prepend(criarLinha(pedido)); // empurra tudo para baixo
});
```

**Exemplo correto:**

```html
<button type="button" id="btn-novidades" hidden></button>
<ul id="lista-pedidos"><!-- ... --></ul>
<div id="aviso-novidades" role="status" class="apenas-leitor-ecra"></div>
```

```javascript
let porMostrar = [];

socket.on('novoPedido', (pedido) => {
  porMostrar.push(pedido);

  const botao = document.getElementById('btn-novidades');
  botao.hidden = false;
  botao.textContent = `Mostrar ${porMostrar.length} pedidos novos`;

  // Um único anúncio, com um resumo, não um por cada pedido
  anunciarComResumo(porMostrar.length);
});

document.getElementById('btn-novidades').addEventListener('click', () => {
  porMostrar.forEach((p) => lista.prepend(criarLinha(p)));
  porMostrar = [];
  document.getElementById('btn-novidades').hidden = true;
});
```

**O que funciona bem:** a pessoa controla o momento em que a lista muda. Nada se mexe sem que ela peça. O anúncio é um resumo agregado, não um anúncio por cada item que chega.

**O que corre mal na versão incorreta:** numa hora de ponta, com dez pedidos por minuto, a lista salta a cada seis segundos e o leitor de ecrã tenta anunciar cada um deles. É impossível trabalhar.

Se, por requisito do produto, a atualização tiver mesmo de ser automática e contínua, então tem de existir um controlo visível para a **pausar** — é o que exige o critério 2.2.2 (Colocar em Pausa, Parar, Ocultar, A).

### T10 — Limites de tempo: avisar cedo e permitir prolongar

```javascript
const DURACAO_SESSAO = 30 * 60 * 1000;   // 30 minutos
const ANTECEDENCIA   =  5 * 60 * 1000;   // avisar 5 minutos antes

let avisoAgendado = setTimeout(mostrarAvisoSessao, DURACAO_SESSAO - ANTECEDENCIA);

function reiniciarContagem() {
  clearTimeout(avisoAgendado);
  avisoAgendado = setTimeout(mostrarAvisoSessao, DURACAO_SESSAO - ANTECEDENCIA);
}
```

Três regras práticas:

1. **Avisar com antecedência útil** — não sessenta segundos. Quem lê com leitor de ecrã ou com ampliação precisa de mais tempo só para localizar e compreender o aviso.
2. **Permitir prolongar com uma ação simples**, sem obrigar a reautenticar.
3. **Não perder o trabalho.** Guardar o rascunho localmente antes de terminar a sessão transforma um desastre num contratempo.

**O que corre mal quando se ignora isto:** o limite de tempo é uma barreira desproporcionada. Uma pessoa que escreve com um manípulo pode levar quinze minutos a preencher um formulário que outra preenche em três — e o temporizador não sabe distinguir «inativo» de «a trabalhar devagar».

### T11 — Evitar a duplicação e a repetição

Três hábitos que reduzem drasticamente o ruído:

**Não anuncie o que o foco já vai dizer.** Se, ao submeter um formulário com erros, mover o foco para o resumo de erros, esse resumo será lido. Um `role="alert"` adicional produziria uma leitura dupla.

**Agregue em vez de repetir.** Cinco ficheiros carregados produzem uma mensagem («5 ficheiros carregados»), não cinco.

**Não repita o óbvio.** Se a pessoa acabou de premir «Adicionar ao carrinho» e o botão mudou para «Remover do carrinho», o leitor de ecrã já lhe dirá isso quando ela lá estiver. A confirmação separada só se justifica se houver mais informação a dar (por exemplo, o novo total).

### T12 — Um sítio onde tudo fica registado

O «livro de bordo» da analogia. Numa aplicação de trabalho, uma zona permanente com as últimas mensagens de sistema resolve, de uma vez, três problemas: quem não ouviu, quem não viu e quem viu mas precisa de reler.

```html
<section aria-labelledby="tit-notificacoes">
  <h2 id="tit-notificacoes">Notificações recentes</h2>
  <ul>
    <li><time datetime="2026-07-25T10:14">10:14</time> — Pedido 2026/318 submetido.</li>
    <li><time datetime="2026-07-25T10:09">10:09</time> — Importação concluída: 42 registos.</li>
  </ul>
</section>
```

**O que funciona bem:** é conteúdo normal, encontrável por marcos e cabeçalhos, legível ao ritmo de cada pessoa, e não exige tecnologia especial. É a solução mais simples e a mais frequentemente esquecida.

---

## Recomendações para Conteúdo Acessível

### Para quem escreve as mensagens

- **Diga o que aconteceu e o que fazer a seguir.** «Não foi possível guardar. Verifique a ligação e tente novamente» é útil; «Erro» não é.
- **Ponha o essencial no início.** Um anúncio pode ser cortado por outro; se o mais importante estiver no fim, perde-se. Escreva «Guardado. Serão notificados 12 destinatários», não «Depois de várias verificações, e uma vez concluído o processo, foi guardado».
- **Seja curto.** Uma frase. Duas, no máximo. Textos longos em regiões dinâmicas são lidos de uma assentada e não podem ser interrompidos com facilidade.
- **Identifique o objeto.** «Pedido 2026/318 eliminado» é melhor do que «Eliminado», sobretudo em ecrãs com muitos elementos semelhantes.
- **Evite jargão e códigos.** «Erro 422» não diz nada a ninguém fora da equipa de desenvolvimento. Se o código for necessário para suporte, ponha-o **depois** da explicação em linguagem simples.
- **Mantenha a linguagem consistente.** Se «guardar» é «guardar», não seja «gravar» num sítio e «submeter» noutro.
- **Cuidado com o tom.** Avisos alarmistas e contagens decrescentes bem visíveis aumentam a ansiedade sem melhorar o desempenho de ninguém.

### Para quem desenha

- **Aproxime a mensagem do ponto de ação.** Confirmações e erros junto ao elemento que os provocou funcionam para toda a gente, e são a única solução que funciona com ampliação forte.
- **Nunca use apenas a cor.** Verde e encarnado precisam de acompanhamento: um ícone com significado, um texto, uma palavra («Erro:», «Concluído:»).
- **Garanta contraste também nos ícones e nas bordas de estado** — as componentes gráficas que transmitem informação precisam de contraste suficiente (WCAG 1.4.11, Contraste Não Textual, AA).
- **Defina uma escala de severidade e documente-a.** Quatro níveis, com regras claras sobre o que entra em cada um, evitam que tudo acabe classificado como urgente.
- **Dimensione os tempos com generosidade.** Se testar a duração de um «toast», teste-a com o ecrã ampliado a 400% e com um leitor de ecrã ligado.
- **Não anime por defeito.** E, quando animar, respeite `prefers-reduced-motion`.
- **Deixe espaço para as notificações no desenho.** Uma faixa que se sobrepõe ao conteúdo é um problema; uma faixa que empurra o conteúdo é apenas uma faixa.

### Para quem decide o produto

- **Faça o inventário das notificações da aplicação.** Muitas equipas nunca contaram quantas têm. A lista costuma ser reveladora.
- **Estabeleça um orçamento de interrupções.** Quantas vezes por sessão é aceitável cortar a atenção de alguém? Se a resposta for «uma ou duas», o número atual provavelmente está muito acima.
- **Preveja um modo silencioso** para tarefas longas.
- **Trate o registo de notificações como funcionalidade, não como extra.**

---

### Erros Comuns

**E1 — A mensagem aparece no ecrã e mais nada acontece.**
Texto inserido no DOM sem região dinâmica e sem movimento de foco. Visualmente perfeito, funcionalmente invisível. *Correção: `role="status"` ou `role="alert"`, consoante a urgência.*

**E2 — A região dinâmica é criada no momento do anúncio.**
Como se viu em T2, muitas combinações não anunciam. *Correção: criar a região vazia no arranque.*

**E3 — Tudo é `assertive`.**
«Na dúvida, assertivo» é a receita para a fadiga de alarme. *Correção: `assertive` apenas quando a consequência de não saber é imediata.*

**E4 — A região está escondida com `display: none` ou `hidden`.**
Não anuncia. *Correção: usar a técnica de recorte visual.*

**E5 — O estado só existe como cor, ícone ou animação.**
A roda que gira, o visto verde, a linha encarnada. *Correção: texto associado; e nunca texto gerado por CSS através de `::before`/`::after`, que pode não chegar às tecnologias de apoio.*

Exemplo do problema:

```css
.guardado::after { content: "Guardado"; color: green; }
```

Correção:

```html
<span class="guardado"><span class="icone" aria-hidden="true"></span> Guardado</span>
```

**E6 — Anunciar percentagem a cada atualização.**
Monólogo contínuo. *Correção: marcos, como em T5.*

**E7 — Filtrar sem dizer quantos resultados há.**
E, em especial, não dizer nada quando há zero. *Correção: contador em `role="status"`.*

**E8 — «Toast» com ação que desaparece sozinho.**
A única forma de anular tem quatro segundos de vida. *Correção: persistir enquanto houver ação; e duplicar a ação num sítio permanente.*

**E9 — Notificação fixa que tapa o elemento com foco.**
Frequente em ecrãs pequenos e em ampliação. *Correção: reservar espaço no desenho; verificar com foco em elementos junto ao rodapé.*

**E10 — Conteúdo que se reordena sozinho.**
Listas em tempo real que empurram o que se estava a ler. *Correção: acumular e mostrar a pedido (T9); disponibilizar pausa.*

**E11 — Aviso de sessão com sessenta segundos.**
Tempo insuficiente para localizar, compreender e agir. *Correção: avisar com vários minutos de antecedência e guardar o rascunho.*

**E12 — Anúncio a duplicar o que o foco já vai ler.**
Resumo de erros que recebe foco **e** `role="alert"`. *Correção: escolher um dos dois mecanismos.*

**E13 — Mensagem sem sujeito.**
«Eliminado com sucesso» — o quê? *Correção: identificar o objeto.*

**E14 — Confiar que funciona porque funcionou uma vez.**
O comportamento das regiões dinâmicas varia entre navegadores, leitores de ecrã e versões. *Correção: testar pelo menos duas combinações diferentes (por exemplo, NVDA com Firefox e VoiceOver com Safari) antes de dar por concluído.*

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Escrever no ecrã não é comunicar.** Uma mudança que não é anunciada nem alcançada pelo foco não existe para uma parte dos utilizadores.
2. **Quatro princípios organizam tudo:** a informação tem de **existir** em texto, **chegar** à pessoa, ser **doseada** na urgência certa e **persistir** para além do instante em que apareceu.
3. **A analogia da cabina orienta as decisões:** aviso, atenção, informação, registo. O silêncio e a cacofonia são falhas simétricas.
4. **A regra fundamental é o critério 4.1.3 (Mensagens de Estado, AA):** confirmações, erros e contagens têm de ser percetíveis **sem receber o foco**.
5. **`role="status"` é o canal por omissão.** A maioria esmagadora das mensagens de uma aplicação não deve interromper ninguém.
6. **`role="alert"` é a exceção**, reservada a situações que impedem a pessoa de continuar. `role="log"` serve registos contínuos, para evitar releituras completas.
7. **A região tem de existir antes de ter conteúdo**, e não pode estar escondida com `display: none` ou `hidden`.
8. **Se o foco se move para o sítio certo, não anuncie.** Duplicar informação é ruído.
9. **Agregue.** Marcos em vez de percentagens, resumos em vez de anúncios individuais, um atraso deliberado nas pesquisas incrementais.
10. **Nada de crítico pode viver só num «toast».** Se tem uma ação, não desaparece; se desaparece, existe noutro sítio.
11. **Nada se mexe sem que a pessoa peça.** Conteúdo que se reordena sozinho tem de ter pausa ou tem de ser mostrado a pedido.
12. **Tempo é acessibilidade.** Avisos de sessão atempados, limites ajustáveis, rascunhos guardados.
13. **Um registo permanente de notificações resolve, com HTML simples, o que nenhum ARIA resolve:** dar uma segunda oportunidade a quem falhou a primeira.

---

### Exercícios Práticos

**Exercício 1 — Inventário de notificações**

Escolha uma aplicação que use com regularidade (um serviço público em linha, uma ferramenta interna, uma loja). Durante quinze minutos de utilização normal, registe **todas** as mudanças de conteúdo que observe, numa tabela com quatro colunas: *o que mudou*, *origem* (ação sua, tempo, servidor, outra pessoa), *como foi comunicado visualmente*, *canal usado para tecnologias de apoio (se algum)*.

Depois, classifique cada uma segundo a analogia da cabina: aviso, atenção, informação ou registo. Quantas estão no nível errado?

**Exercício 2 — Correção de código**

Corrija o excerto seguinte e justifique cada alteração:

```html
<form id="form-contacto">
  <label for="email">Correio eletrónico</label>
  <input type="email" id="email">
  <button type="submit">Subscrever</button>
</form>

<script>
  document.getElementById('form-contacto').addEventListener('submit', (e) => {
    e.preventDefault();
    const caixa = document.createElement('div');
    caixa.setAttribute('aria-live', 'assertive');
    caixa.style.color = 'green';
    caixa.textContent = 'OK';
    document.body.appendChild(caixa);
    setTimeout(() => caixa.remove(), 3000);
  });
</script>
```

Identifique, no mínimo, **cinco** problemas distintos.

**Exercício 3 — Construir uma zona de estado**

Construa uma pequena página com uma lista de dez itens e três controlos: um campo de pesquisa, um botão «Eliminar» em cada linha e um botão «Recarregar dados» que demora três segundos a simular.

Requisitos:

- a pesquisa anuncia o número de resultados, com atraso adequado, e trata o caso de zero;
- a eliminação confirma qual o item eliminado e oferece «Anular» de forma que continue disponível ao fim de trinta segundos;
- o recarregamento comunica início e fim, sem anunciar nada pelo meio;
- nenhuma das operações rouba o foco.

Teste com um leitor de ecrã e conte o número total de anúncios ouvidos numa sequência de cinco ações. Consegue reduzi-lo sem perder informação?

**Exercício 4 — Reescrita de mensagens**

Reescreva as mensagens seguintes segundo as recomendações desta secção:

1. «Erro.»
2. «Erro 422: Unprocessable Entity.»
3. «Operação concluída com sucesso.»
4. «Atenção! Os seus dados serão perdidos!!!»
5. «Depois de validados todos os campos e confirmados os dados junto do sistema central, o seu pedido foi finalmente registado com o número 2026/318.»

Para cada uma, indique também o canal correto.

**Exercício 5 — Auditoria com ampliação**

Repita o Exercício 1 numa aplicação à sua escolha, mas com o ecrã ampliado a 400% e a trabalhar no canto superior esquerdo da página. Registe:

1. Quantas notificações apareceram fora do seu campo de visão.
2. Quantas taparam o elemento em que estava a trabalhar.
3. Quantas continham informação que não conseguiu recuperar depois de desaparecerem.

**Exercício 6 — Discussão em grupo**

Uma equipa de produto quer que a aplicação avise, em tempo real, sempre que um colega altera um documento partilhado. A proposta técnica em cima da mesa é: `role="alert"` a cada alteração, com o nome de quem alterou.

Prepare uma resposta de três minutos que:

- explique o problema com um cenário concreto (uma reunião de duas horas, cinco pessoas a editar);
- proponha uma alternativa que continue a servir o objetivo do produto;
- indique que critério WCAG está em causa e porquê.

**Exercício 7 — Decisão de canal**

Para cada situação, decida o canal (nada / `status` / `alert` / diálogo / mover o foco) e justifique em duas linhas:

1. O carrinho de compras passou de 2 para 3 artigos.
2. O pagamento foi recusado pelo banco.
3. A ligação à internet caiu e o trabalho deixou de ser guardado.
4. Uma pesquisa devolveu 0 resultados.
5. Um relatório em segundo plano ficou pronto ao fim de dez minutos.
6. O documento foi guardado automaticamente.
7. A palavra-passe introduzida está errada.
8. Um colega juntou-se ao documento partilhado.

