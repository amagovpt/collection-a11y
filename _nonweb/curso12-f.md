---
title: Formulários em PDF
layout: default
nav_order: 6
---
# Formulários em PDF

## Introdução

Até aqui, o documento era um objeto para ler. A partir de agora é também um objeto para **usar**. Um formulário não se limita a transmitir informação: pede-a de volta. E é aí que a acessibilidade deixa de ser uma questão de leitura e passa a ser uma questão de **operação**.

Um formulário inacessível não é um inconveniente. É uma porta fechada. Quem não consegue preencher o formulário não se candidata ao apoio, não pede a certidão, não marca a consulta, não reclama. A barreira é total, não parcial.

### O Que Distingue um Formulário em PDF

Volte à analogia do curso. O documento é um edifício. As etiquetas são a planta. Quem vê, vê o edifício; a tecnologia de apoio lê a planta.

Num formulário em PDF, há uma complicação nova: **os campos de formulário não fazem parte do edifício — são equipamento instalado por cima dele**.

Tecnicamente, um campo de formulário num PDF é uma *anotação*: uma caixa colocada sobre a página, com coordenadas próprias, que existe numa camada separada do conteúdo. O texto "Nome completo:" que está impresso ao lado da caixa é conteúdo da página. A caixa onde se escreve é outra coisa, noutra camada. **Nada os liga automaticamente.**

Continuando a analogia: alguém instalou interruptores, torneiras e maçanetas no edifício depois de a planta estar desenhada. Se ninguém os acrescentar à planta, quem lê a planta não sabe que existem — ou sabe que existe *algo* ali, mas não o que faz nem para que serve.

Isto explica quase tudo o que corre mal nos formulários em PDF:

| O que o utilizador vidente vê | O que a tecnologia de apoio encontra, se nada for feito |
|---|---|
| Uma etiqueta "Nome completo" e uma caixa ao lado | Um texto solto e, algures, uma caixa de edição sem nome |
| Três círculos com as opções "Sim", "Não", "Não sei" | Três controlos independentes, sem pergunta associada |
| Um botão azul com a palavra "Submeter" | Um botão sem nome |
| Campos obrigatórios com contorno vermelho | Nada — a cor não é informação |

Duas consequências práticas, que convém enunciar já:

1. **Um campo de formulário só é acessível se for um campo a sério.** Uma linha desenhada, um sublinhado, uma sequência de pontos ou uma imagem digitalizada de um impresso não são campos. São desenho. Ninguém os pode preencher com o teclado, e a tecnologia de apoio não tem o que anunciar.
2. **Um formulário em PDF depende do leitor que o abre.** O mesmo ficheiro comporta-se de maneira diferente no Adobe Acrobat Reader, no visualizador integrado de um navegador e numa aplicação de telemóvel. Alguns visualizadores ignoram parte da informação de acessibilidade dos campos. Isto não invalida o trabalho, mas obriga a testar em mais do que um sítio.

#### A pergunta honesta

**Um formulário em PDF é a melhor solução?**

Regra geral, **não**. Um formulário web bem construído é quase sempre preferível: comunica erros no momento certo, adapta-se ao tamanho do ecrã, funciona sem software instalado, permite guardar e retomar, e tem um suporte de tecnologia de apoio muito mais maduro e mais previsível.

O formulário em PDF justifica-se quando o resultado tem de ser um documento com valor de original, quando o circuito é de impressão e assinatura, ou quando não existe infraestrutura web para o receber. A decisão em si — quando escolher documento e quando escolher página web — é tratada na secção "Escolher o Formato e Organizar o Trabalho". Esta secção parte do princípio de que a decisão já está tomada e o formato é mesmo o PDF.

#### Comparação com o formulário em Word

O procedimento `W7` tratou dos formulários criados e preenchidos em Word. Vale a pena ter presente onde estão as diferenças, porque determinam o esforço:

| | Word (`W7`) | PDF (esta secção) |
|---|---|---|
| Como se cria o campo | Controlos de conteúdo, no separador Programador | Anotações de formulário, na ferramenta Preparar um formulário |
| Onde se põe o nome que é anunciado | Propriedade **Título** do controlo | **Descrição da ferramenta** nas propriedades do campo |
| Campo obrigatório | Não existe; só se diz no rótulo visível | Existe: propriedade **Obrigatório** |
| Validação de formato | Não existe | Existe, com limitações importantes (ver `F6`) |
| Ordem de tabulação | Segue a ordem do texto | **Não segue nada por defeito**; tem de ser definida (ver `F4`) |
| Agrupamento de opções | Não existe mecanismo | Existe, para botões de opção (ver `F3`) |
| Esforço de produção | Baixo | Médio a alto |

Resumindo: o PDF dá mais ferramentas do que o Word, mas exige mais trabalho e mais verificação. Nenhum dos dois chega ao que um formulário web faz bem.

### Das Propriedades às Funcionalidades do Acrobat

As sete propriedades de um documento acessível, definidas na secção "Fundamentos da Acessibilidade de Documentos", aplicam-se ao formulário. Muda o instrumento que as garante.

| Propriedade | O que a garante num formulário em PDF | Procedimento |
|---|---|---|
| **Identificado** | Título, idioma e metadados do ficheiro | Tratado em `R6` |
| **Estruturado** | Cada campo existe como campo real e está etiquetado na árvore de etiquetas | `F1` |
| **Ordem de leitura correta** | Os campos ocupam o lugar certo na árvore de etiquetas, entre o rótulo e o campo seguinte | `F1`, e `R3` para a estrutura geral |
| **Percetível sem ver** | Cada campo tem uma descrição da ferramenta que diz o que é e o que se espera | `F2`, `F3` |
| **Legível** | Tipo de letra, contraste e dimensão suficientes nos rótulos e no texto introduzido | Tratado nas secções de produção; ver `F1` para a dimensão da caixa |
| **Navegável** | Ordem de tabulação previsível e coincidente com a ordem visual | `F4` |
| **Operável** | Todos os campos, botões e ações funcionam só com teclado, sem armadilhas | `F1`, `F4`, `F5` |

E acrescenta-se uma exigência que só os formulários têm: **recuperável**. Quem se engana tem de saber que se enganou, onde, e como corrigir (`F6`).

---

## Procedimentos

### F1. Criar Campos

**O que se pretende**

Que cada ponto de resposta do formulário seja um **campo real**, com o tipo certo, e que esse campo exista também na árvore de etiquetas — ou seja, na planta do edifício.

Depende disto quem usa leitor de ecrã (que só encontra o que está na planta), quem navega só com teclado (que só alcança o que é um controlo verdadeiro), quem usa software de reconhecimento de voz (que precisa de um alvo nomeável para dizer "clicar em…") e quem tem tremor ou pouca precisão motora (que precisa de alvos com dimensão utilizável).

**Passos no Acrobat**

1. **Abrir a ferramenta de formulários:** **Todas as ferramentas → Preparar um formulário**.
2. **Deixar o Acrobat propor os campos:** ao abrir a ferramenta, o Acrobat analisa a página e propõe campos onde reconhece linhas, caixas e sublinhados. Aceite a proposta como **ponto de partida**, nunca como resultado final. A deteção automática acerta na posição e falha quase sempre no nome e frequentemente no tipo.
3. **Rever o tipo de cada campo.** Selecione o campo e confirme o tipo na barra de ferramentas ou nas propriedades:
   - **Campo de texto** — resposta livre, curta ou longa;
   - **Caixa de verificação** — escolhas independentes, em que se pode marcar várias ou nenhuma;
   - **Botão de opção** — escolha única dentro de um conjunto (ver `F3`);
   - **Lista pendente** — escolha única a partir de uma lista fechada e longa;
   - **Caixa de listagem** — lista visível, com uma ou várias escolhas;
   - **Botão** — ação (ver `F5`);
   - **Campo de assinatura** — assinatura digital.
4. **Ajustar a dimensão da caixa.** Arraste as pegas para dar espaço suficiente à resposta esperada. Para respostas longas, abra as propriedades do campo → separador **Opções** → marque **Multilinha** e, se fizer sentido, **Deslocar texto longo**.
5. **Garantir que os campos estão etiquetados.** Abra o painel de etiquetas (**Ver → Mostrar/Ocultar → Painéis de navegação → Etiquetas**) e confirme que cada campo aparece como uma etiqueta `<Form>` no sítio certo da árvore, logo a seguir ao respetivo rótulo. Se houver campos ausentes da árvore, use o menu **Opções** do painel de etiquetas → **Localizar** → procure **Anotações não etiquetadas** → **Etiquetar elemento**.

> **Atalho útil.** Se o formulário vier de um documento Word ou PowerPoint bem construído, o trabalho de estrutura já está feito e só falta acrescentar os campos. Se o PDF for uma digitalização de papel, tem primeiro de passar por OCR — tratado em `R7` — e mesmo assim o resultado será sempre mais frágil.

**Antes e depois**

*Antes* — o impresso foi desenhado no Word com sublinhados e exportado para PDF:

```
Nome completo: _________________________________________

Data de nascimento: ____ / ____ / ________

Observações:
_________________________________________________________
_________________________________________________________
```

Ao abrir este PDF, o utilizador vê linhas onde escrever. Mas não há onde escrever. A tecla `Tab` não pára em lado nenhum, porque não há nada onde parar. O leitor de ecrã lê "Nome completo, dois pontos, sublinhado sublinhado sublinhado sublinhado" — uma sequência de carateres sem função. Quem quiser responder tem de imprimir, escrever à mão e digitalizar. Para quem não vê, ou não tem impressora, ou não tem destreza manual, o formulário simplesmente não existe.

*Depois* — os mesmos três pontos convertidos em campos reais:

| Ponto do formulário | Tipo de campo | Configuração |
|---|---|---|
| Nome completo | Campo de texto | Linha simples, largura suficiente para cerca de 50 carateres |
| Data de nascimento | Campo de texto (um só, não três) | Formato de data definido no separador Formatar (ver `F6`) |
| Observações | Campo de texto | Multilinha, com deslocamento de texto longo |

Repare na decisão da data: **um campo em vez de três**. Três caixas separadas para dia, mês e ano obrigam a três paragens do `Tab`, três anúncios do leitor de ecrã e três oportunidades de erro, para recolher uma única informação. Um campo com formato definido e o formato indicado na descrição resolve o mesmo problema com um terço do esforço.

**Porque funciona**

Um campo real entra em três circuitos ao mesmo tempo. Entra no circuito do teclado, e passa a ser alcançável com `Tab`. Entra na árvore de etiquetas, e passa a constar da planta que a tecnologia de apoio lê. E entra na lista de controlos que o software de reconhecimento de voz consegue nomear e ativar.

Um sublinhado não entra em nenhum destes circuitos. É tinta.

Este é o requisito de base do critério 4.1.2 (Nome, Função, Valor): cada componente de interface tem de ter uma função determinável por meios programáticos. Uma linha desenhada não tem função nenhuma.

---

### F2. Etiquetas, Dicas e Descrições

**O que se pretende**

Que cada campo anuncie, a quem não vê a página, **o que é pedido ali**.

Este é o procedimento mais mal compreendido de toda a matéria, porque o Acrobat oferece vários sítios onde se pode escrever texto associado a um campo, e **só um deles é o que a tecnologia de apoio anuncia**.

Depende disto quem usa leitor de ecrã, quem usa ampliação de ecrã (que vê o campo mas não o rótulo, por estarem fora do mesmo enquadramento) e quem usa reconhecimento de voz.

**Os cinco sítios onde se escreve texto — e o que cada um faz**

Abra as propriedades de um campo (duplo clique sobre o campo, com a ferramenta de formulários ativa) e percorra os separadores.

| Onde | Separador | Para que serve | É anunciado? |
|---|---|---|---|
| **Nome** | Geral | Identificador interno do campo. Serve para exportar dados, para cálculos e para agrupar botões de opção. | **Não**, em princípio. Alguns leitores recorrem a ele quando não encontram mais nada — mas é um recurso de emergência, não uma solução. |
| **Descrição da ferramenta** | Geral | **É o nome acessível do campo.** É também a dica que aparece ao passar o rato. | **Sim. É este.** |
| **Valor de exportação** ou **Escolha do botão** | Opções | Valor de dados que o campo devolve quando é marcado. | **Não.** É dado, não é rótulo. |
| **Etiqueta** de um botão | Opções | Texto desenhado na face do botão. Visível. | **Não fiavelmente.** O botão precisa na mesma de descrição da ferramenta. |
| **Texto alternativo** da etiqueta `<Form>` | Painel de etiquetas → Propriedades | Alternativa textual ao nível da estrutura. | **Às vezes** — e é aqui que nascem os conflitos. |

**A regra prática, em duas linhas:**

> Escreva sempre a **descrição da ferramenta**. Deixe o **texto alternativo** da etiqueta `<Form>` vazio, a menos que tenha uma razão específica para o usar.

Porquê? Porque quando os dois estão preenchidos com textos diferentes, o comportamento varia entre leitores de ecrã e entre visualizadores. Uns anunciam um, outros anunciam o outro, outros anunciam os dois seguidos. O utilizador ouve "Nome completo, Nome, caixa de edição" e não sabe se lhe estão a pedir uma coisa ou duas. Um único sítio preenchido é sempre mais previsível do que dois.

**Passos no Acrobat**

1. Com a ferramenta **Preparar um formulário** ativa, faça duplo clique sobre o campo.
2. No separador **Geral**:
   - **Nome:** um identificador curto, sem espaços nem acentos, único no documento — por exemplo `nome_completo`. Este é o nome dos dados.
   - **Descrição da ferramenta:** o texto que o utilizador vai ouvir. Este é o rótulo.
   - Marque **Obrigatório** se o campo for de preenchimento obrigatório.
3. Repita para **todos** os campos, incluindo botões.

**O que escrever na descrição da ferramenta**

- **Repita o rótulo visível, palavra por palavra.** Se na página está escrito "Nome completo", a descrição diz "Nome completo". Textos diferentes para a mesma coisa confundem quem usa reconhecimento de voz, que diz em voz alta o que está escrito no ecrã.
- **Acrescente o formato esperado**, se houver: "Data de nascimento (dd/mm/aaaa)".
- **Acrescente a indicação de obrigatório**, mesmo tendo marcado a propriedade: "Nome completo (obrigatório)". A propriedade existe, mas nem todos os visualizadores a anunciam. A redundância aqui é barata e útil.
- **Não escreva o tipo de campo.** "Caixa de texto do nome" faz o leitor de ecrã anunciar "Caixa de texto do nome, caixa de edição". O tipo já é anunciado pelo próprio leitor.
- **Não deixe a descrição igual ao nome interno.** "campo_txt_03" não diz nada a ninguém.

**Antes e depois**

*Antes* — formulário gerado por deteção automática, com as propriedades por defeito:

| Nome | Descrição da ferramenta | Obrigatório |
|---|---|---|
| `Texto1` | *(vazio)* | Não |
| `Texto2` | *(vazio)* | Não |
| `CaixaVerificação1` | *(vazio)* | Não |

O que o leitor de ecrã anuncia, campo a campo: "Texto1, caixa de edição". "Texto2, caixa de edição". "Caixa de verificação 1, caixa de verificação, não marcada."

O utilizador ouve os nomes internos, que são etiquetas de arrumação e não perguntas. Não faz ideia do que lhe está a ser pedido. Note-se que este é o **resultado normal** da deteção automática quando ninguém a revê: o formulário parece completo, abre bem, os campos aceitam texto — e é inutilizável para quem não vê o ecrã.

*Depois* — as mesmas propriedades revistas:

| Nome | Descrição da ferramenta | Obrigatório |
|---|---|---|
| `nome_completo` | Nome completo (obrigatório) | Sim |
| `data_nascimento` | Data de nascimento (dd/mm/aaaa) | Não |
| `autoriza_dados` | Autorizo o tratamento dos meus dados para efeitos de candidatura | Não |

Agora o leitor de ecrã anuncia: "Nome completo (obrigatório), caixa de edição". "Data de nascimento (dd barra mm barra aaaa), caixa de edição". "Autorizo o tratamento dos meus dados para efeitos de candidatura, caixa de verificação, não marcada."

Repare no terceiro campo. O rótulo visível ao lado da caixa é uma frase inteira, e a descrição repete a frase inteira. É tentador abreviar para "Autorização", mas a abreviatura tiraria ao utilizador exatamente a informação de que precisa para decidir se marca ou não. Numa caixa de verificação de consentimento, o rótulo **é** o conteúdo.

**Porque funciona**

O rótulo impresso na página e a caixa de formulário são, para a máquina, dois objetos sem relação. A proximidade visual é uma pista para os olhos, não é informação. A descrição da ferramenta é a única ligação explícita entre a pergunta e o sítio da resposta — é o equivalente, no mundo do PDF, a dizer na planta "este interruptor acende a luz do corredor".

É isto que satisfaz o critério 3.3.2 (Rótulos ou Instruções) e a parte "Nome" do critério 4.1.2.

---

### F3. Agrupar Campos Relacionados

**O que se pretende**

Que um conjunto de opções que responde a **uma só pergunta** seja percebido como um conjunto, e que a pergunta chegue a quem não a vê.

Depende disto quem usa leitor de ecrã e quem tem dificuldades cognitivas ou de memória de trabalho, que precisa de ver a pergunta e as opções juntas, sem ter de as reter.

**O problema**

Num formulário em papel, a pergunta "Modalidade de participação" está escrita por cima de três círculos. Os olhos captam o conjunto de uma vez: uma pergunta, três opções, escolha uma.

Um leitor de ecrã não capta conjuntos. Percorre controlos, um a um. Se cada botão de opção só souber dizer "Presencial", "Em linha", "Misto", o utilizador ouve três palavras soltas e tem de adivinhar a que pergunta respondem — sobretudo se tiver chegado ali com `Tab`, saltando o texto da pergunta.

Ao contrário do HTML, que tem um mecanismo próprio para isto, **o PDF não tem uma forma fiável de associar uma legenda a um grupo de campos**. A solução é mais rudimentar e mais direta: repetir o contexto em cada opção.

**Passos no Acrobat**

*Para botões de opção — escolha única:*

1. Crie todos os botões do conjunto.
2. Nas propriedades de cada um, separador **Geral**, dê a **todos exatamente o mesmo Nome** — por exemplo `modalidade`. É o nome partilhado que faz o Acrobat tratá-los como um grupo mutuamente exclusivo: marcar um desmarca os outros.
3. No separador **Opções**, dê a cada botão uma **Escolha do botão** diferente — `presencial`, `online`, `misto`. É este valor que distingue as opções nos dados.
4. Na **Descrição da ferramenta** de cada botão, escreva **a pergunta e a opção**: "Modalidade de participação: presencial".

*Para caixas de verificação — escolha múltipla:*

1. Dê a cada caixa um **Nome diferente**. Nomes iguais transformariam as caixas num grupo exclusivo, que não é o que se pretende.
2. Na **Descrição da ferramenta** de cada uma, escreva igualmente o contexto e a opção: "Áreas de interesse: acessibilidade digital".

*Em qualquer dos casos:*

3. Reforce o agrupamento visualmente — um cabeçalho, uma moldura, espaço em branco em volta — e confirme, no painel de etiquetas, que o texto da pergunta antecede as etiquetas `<Form>` das opções na árvore.

**Antes e depois**

*Antes:*

Pergunta impressa na página: **Modalidade de participação**

| Nome | Escolha do botão | Descrição da ferramenta |
|---|---|---|
| `opcao1` | `Sim` | Presencial |
| `opcao2` | `Sim` | Em linha |
| `opcao3` | `Sim` | Misto |

Dois erros de uma vez. Primeiro, os nomes são diferentes, por isso não há grupo nenhum: o utilizador pode marcar as três opções ao mesmo tempo, o que a pergunta não permite. Segundo, a descrição não tem a pergunta. Quem chega com `Tab` ouve "Presencial, botão de opção, não selecionado" e fica sem saber presencial em quê.

*Depois:*

| Nome | Escolha do botão | Descrição da ferramenta |
|---|---|---|
| `modalidade` | `presencial` | Modalidade de participação: presencial |
| `modalidade` | `online` | Modalidade de participação: em linha |
| `modalidade` | `misto` | Modalidade de participação: misto |

Agora o nome partilhado cria o grupo. As setas do teclado percorrem as três opções e marcam uma de cada vez. E o anúncio passa a ser autossuficiente: "Modalidade de participação: presencial, botão de opção, 1 de 3, não selecionado."

O "1 de 3" não foi escrito por ninguém — é o leitor de ecrã que o deduz, precisamente porque os três botões partilham o nome e formam um grupo verdadeiro. A informação de estrutura, quando existe, produz benefícios que não foram programados um a um.

> **Sobre a repetição.** Escrever "Modalidade de participação" três vezes parece redundante, e é — para quem vê. Para quem ouve, não é redundância: é a única forma de a pergunta acompanhar cada opção. Mantenha o prefixo curto, para não tornar a audição pesada.

**Porque funciona**

O nome partilhado é o que existe de mais próximo, no PDF, de um mecanismo de agrupamento. Dá exclusividade mútua, dá navegação por setas e dá a contagem de posição no grupo. A repetição do contexto na descrição compensa aquilo que o formato não sabe fazer: transportar a legenda do grupo até cada elemento.

Isto liga-se ao critério 1.3.1 (Informação e Relações): a relação entre a pergunta e as opções tem de ser determinável por meios programáticos, e não apenas visível.

---

### F4. Ordem de Tabulação

**O que se pretende**

Que a tecla `Tab` percorra os campos pela ordem em que uma pessoa os leria — e não por uma ordem arbitrária.

Depende disto quem navega só com teclado, quem usa leitor de ecrã e quem usa comutadores ou outros dispositivos de acesso sequencial. Para essas pessoas, a ordem de tabulação **é** o formulário: é a única sequência que existe.

**O ponto que surpreende toda a gente**

A ordem de tabulação num PDF **não segue a ordem visual dos campos**. Não segue a posição na página, não segue a coluna, não segue a linha.

Por defeito, segue **a ordem por que os campos foram criados**.

Isto significa que, se acrescentou o campo "Código postal" no fim do trabalho porque se tinha esquecido dele, o `Tab` vai levar o utilizador ao código postal **depois** de todos os outros campos — mesmo que na página o código postal esteja a meio, entre a morada e a localidade. Visualmente está tudo bem. Com teclado, o utilizador salta do meio do formulário para o fim, e volta atrás, sem perceber porquê.

A analogia é direta: é como uma visita guiada ao edifício que segue a ordem por que as divisões foram construídas, e não a ordem por que estão dispostas. O guia leva os visitantes à cozinha, depois à água-furtada, depois de volta à sala.

**Passos no Acrobat**

Há duas formas. Use a primeira sempre que puder.

*Forma recomendada — herdar a ordem da estrutura do documento:*

1. Abra o painel de miniaturas de páginas (**Ver → Mostrar/Ocultar → Painéis de navegação → Miniaturas de página**).
2. Selecione **todas** as páginas (clique na primeira, `Shift` + clique na última, ou `Ctrl+A`).
3. Clique com o botão direito → **Propriedades da página** → separador **Ordem de tabulação**.
4. Escolha **Utilizar a estrutura do documento** → **OK**.

Isto faz a ordem de tabulação seguir a árvore de etiquetas. Como a árvore já foi posta em ordem — o trabalho de `R3` —, os campos passam a ser percorridos pela mesma sequência por que o documento é lido. É a opção mais robusta, porque mantém as duas ordens sincronizadas: se corrigir uma, corrige a outra.

**Atenção:** a definição é **por página**. Se a alterar apenas na primeira, as restantes ficam como estavam. Daí o passo 2.

*Forma manual — reordenar campo a campo:*

1. Na ferramenta **Preparar um formulário**, no painel de campos à direita, abra o menu de ordenação e escolha **Ordenar por ordem de tabulação**.
2. Arraste os campos na lista até a sequência corresponder à ordem de leitura pretendida.

Use esta forma quando a estrutura do documento não estiver fiável, ou para acertos pontuais.

**Antes e depois**

Imagine um formulário de contacto com os campos dispostos em duas colunas:

```
Nome            [_________]        Telefone     [_________]
Morada          [_________]        Correio el.  [_________]
Código postal   [_________]        Localidade   [_________]
```

*Antes* — ordem por criação, tal como saiu da deteção automática seguida de dois acrescentos:

`Nome → Morada → Telefone → Correio eletrónico → Localidade → Código postal`

Com teclado, o utilizador escreve o nome, salta para a morada, atravessa para a coluna da direita, volta à esquerda, atravessa outra vez. E o código postal aparece no fim, depois da localidade, invertendo a ordem visual. Quem vê o ecrã percebe o salto e adapta-se, com irritação. Quem não vê perde completamente o mapa: ouve os campos por uma ordem que não corresponde a nenhuma lógica de morada.

*Depois* — com **Utilizar a estrutura do documento** e a árvore de etiquetas em ordem:

`Nome → Telefone → Morada → Correio eletrónico → Código postal → Localidade`

A sequência acompanha agora a leitura linha a linha, tal como a página está desenhada. O código postal voltou ao lugar, porque a árvore de etiquetas o tem no lugar certo — e não porque alguém o arrastou.

**Porque funciona**

Ao herdar a ordem da estrutura, deixa de haver duas ordens a manter em paralelo. A planta do edifício passa a comandar o percurso da visita. Qualquer correção futura na estrutura propaga-se sozinha para a tabulação, o que elimina a fonte de erro mais comum: corrigir uma e esquecer a outra.

É o que o critério 2.4.3 (Ordem de Foco) exige — que a sequência de navegação preserve o significado — e uma condição de 2.1.1 (Teclado), porque uma ordem caótica pode tornar campos praticamente inalcançáveis num formulário longo.

---

### F5. Botões e Ações

**O que se pretende**

Que os botões tenham nome, sejam alcançáveis e ativáveis com teclado, e que não façam nada de inesperado.

Depende disto toda a gente que não usa rato, e em especial quem usa leitor de ecrã, para quem um botão sem nome é um beco sem saída.

**Passos no Acrobat**

1. **Criar o botão:** na ferramenta **Preparar um formulário**, escolha o tipo **Botão** e desenhe-o na página.
2. **Dar-lhe o texto visível:** propriedades → separador **Opções** → **Esquema:** Só etiqueta → **Etiqueta:** "Submeter candidatura".
3. **Dar-lhe o nome acessível:** separador **Geral** → **Descrição da ferramenta:** "Submeter candidatura". Sim, repete-se o texto da etiqueta. A etiqueta é desenho; a descrição é informação.
4. **Definir a ação:** separador **Ações** → **Selecionar acionador:** `Rato solto` → **Selecionar ação:** escolha a adequada:
   - **Submeter um formulário** — envia os dados para um endereço indicado;
   - **Repor formulário** — limpa os campos;
   - **Executar um item de menu → Imprimir**;
   - **Abrir uma ligação web**.
5. **Clique em Adicionar** e confirme os parâmetros.

**Regras**

- **O acionador é sempre `Rato solto`.** Apesar do nome, este acionador dispara igualmente com `Enter` ou `Espaço` quando o botão tem o foco. Os acionadores `Rato para baixo`, `Rato para dentro` e `Rato para fora` dependem de movimento e pressão do rato e devem ser evitados em ações com consequências.
- **Nunca ponha uma ação com consequências no acionador `Ao receber o foco`.** Um formulário que se submete, se limpa ou que abre uma janela só porque o `Tab` passou por ali é intransitável para quem navega com teclado — e viola o critério 3.2.1 (Ao Receber o Foco).
- **Um botão de reposição precisa de confirmação** ou, melhor ainda, não precisa de existir. É o botão que mais estragos causa: fica ao lado do botão de submissão, apaga tudo sem aviso e não tem desfazer.
- **Botões só com ícone precisam de descrição na mesma.** Um ícone de impressora sem descrição é anunciado como "botão", e mais nada.
- **Se o formulário for para imprimir e entregar em mão, diga-o.** Um formulário sem botão de submissão deve explicar, em texto na página, o que fazer a seguir.

**Antes e depois**

*Antes:*

| Elemento | Etiqueta visível | Descrição da ferramenta | Acionador |
|---|---|---|---|
| Botão 1 | *(ícone de seta)* | *(vazio)* | Rato solto |
| Botão 2 | Limpar | *(vazio)* | Rato solto |

O primeiro botão é anunciado como "botão". O utilizador tem de o premir para descobrir o que faz — e, num formulário, premir para descobrir é uma aposta cara. O segundo é anunciado como "botão", igualmente sem nome, e apaga o formulário inteiro sem aviso nem confirmação. Um utilizador de leitor de ecrã que ande a explorar os controlos com `Tab` e `Enter` pode perder vinte minutos de trabalho sem chegar a perceber o que aconteceu.

*Depois:*

| Elemento | Etiqueta visível | Descrição da ferramenta | Acionador | Ação |
|---|---|---|---|---|
| Botão 1 | Submeter candidatura | Submeter candidatura | Rato solto | Submeter um formulário |
| Botão 2 | Limpar formulário | Limpar formulário — apaga todas as respostas | Rato solto | Repor formulário |

Os dois botões passam a anunciar-se: "Submeter candidatura, botão"; "Limpar formulário — apaga todas as respostas, botão". O segundo diz o que faz **antes** de o fazer. Não é uma confirmação a sério, mas é o aviso que o formato permite dar, e transforma uma armadilha num risco informado.

**Porque funciona**

Um botão é o único ponto do formulário onde uma ação irreversível acontece. Nomear o botão é dar ao utilizador a informação necessária para decidir. Escolher bem o acionador é garantir que a decisão é dele — e não do foco do teclado a passar de raspão.

---

### F6. Validação e Mensagens de Erro

**O que se pretende**

Que quem se engana perceba **que** se enganou, **onde** se enganou e **como** corrigir.

Depende disto quem usa leitor de ecrã, quem tem dificuldades cognitivas ou de aprendizagem, e — na verdade — toda a gente. As mensagens de erro são o ponto onde os formulários mais falham, em qualquer formato.

**O que o Acrobat sabe fazer, e o que não sabe**

Convém ser franco sobre os limites, porque determinam a estratégia.

O Acrobat sabe:

- impor um **formato** a um campo (data, número, percentagem, código postal com máscara);
- impor um **intervalo** de valores numéricos;
- marcar um campo como **obrigatório**;
- mostrar uma **caixa de alerta** quando o valor não passa.

O Acrobat **não** sabe:

- associar a mensagem de erro ao campo, na estrutura, como o HTML faz;
- mostrar todos os erros de uma vez, numa lista, no fim;
- impedir a submissão de forma clara e explicada.

E a caixa de alerta tem dois problemas próprios: aparece **ao sair do campo**, o que interrompe o utilizador a meio do percurso, e o seu texto por defeito é genérico e não nomeia o campo.

Daí a estratégia: **prevenir vale mais do que corrigir**. A informação sobre o que se espera deve estar no formulário *antes* de o utilizador escrever, não numa caixa depois de ele errar.

**Passos no Acrobat**

1. **Anunciar a expectativa (o passo mais importante):**
   - escreva o formato no **rótulo visível** na página: "Data de nascimento (dd/mm/aaaa)";
   - escreva-o também na **Descrição da ferramenta** do campo (`F2`);
   - se todo o formulário partilhar uma regra, ponha uma nota no topo, antes do primeiro campo.
2. **Definir o formato:** propriedades do campo → separador **Formatar** → **Selecionar categoria de formato:** Data, Número, Percentagem, Especial ou Personalizado.
3. **Definir o intervalo, se aplicável:** separador **Validar** → **O valor do campo está no intervalo** → indique mínimo e máximo.
4. **Escrever uma mensagem própria:** separador **Validar** → **Executar script de validação personalizado** → escreva um script que nomeie o campo e o problema.
5. **Marcar os campos obrigatórios:** separador **Geral** → **Obrigatório**, e repetir a indicação no rótulo visível e na descrição.

**Sobre os campos obrigatórios e a cor**

O Acrobat assinala os campos obrigatórios com um contorno vermelho. É útil, mas é **só** cor e forma. Quem não distingue vermelho, quem tem baixa visão ou quem usa modo de alto contraste pode não ver diferença nenhuma. A palavra "obrigatório" no rótulo não é opcional — é o que satisfaz o critério 1.4.1 (Uso da Cor).

**Antes e depois**

*Antes:*

Rótulo visível: **Data**
Descrição da ferramenta: `Data`
Formato: Data, `mm/dd/aa`
Mensagem: a caixa de alerta por defeito do Acrobat.

O utilizador escreve `15/03/1980`, que é a forma portuguesa. Ao sair do campo, aparece uma caixa a dizer que o valor introduzido não corresponde ao formato do campo. O utilizador fecha a caixa, olha para o campo, vê "Data" e não faz ideia do que o formulário quer. Tenta `15-03-1980`. A caixa volta. Tenta `15 março 1980`. A caixa volta.

O erro estava no formato `mm/dd/aa` — americano —, que ninguém lhe disse qual era. E a caixa de alerta, ao aparecer sozinha, tira o foco do campo: quem usa leitor de ecrã ouve o alerta, fecha-o, e muitas vezes não sabe onde o foco ficou.

*Depois:*

Rótulo visível: **Data de nascimento (dd/mm/aaaa)**
Descrição da ferramenta: `Data de nascimento (dd/mm/aaaa)`
Formato: Data, `dd/mm/aaaa`
Mensagem personalizada: "Data de nascimento: escreva a data no formato dia/mês/ano, por exemplo 15/03/1980."

O utilizador sabe o que escrever antes de escrever, porque a informação está no rótulo e na descrição — e chega-lhe tanto pelos olhos como pelos ouvidos. Se ainda assim errar, a mensagem diz **de que campo** se trata, **o que está mal** e **dá um exemplo válido**. Já não é um aviso: é uma instrução.

**Porque funciona**

Uma mensagem de erro genérica identifica que houve um problema. Uma mensagem que nomeia o campo, descreve o requisito e dá um exemplo permite resolver o problema. A diferença entre as duas é a diferença entre os critérios 3.3.1 (Identificação de Erro) e 3.3.3 (Sugestão para Erro).

E a informação antecipada — no rótulo, na descrição, na nota introdutória — é a única que funciona para toda a gente, porque evita que o erro chegue a acontecer. É o que o critério 3.3.2 (Rótulos ou Instruções) pede.

---

## Verificação

Um formulário em PDF **não se dá por verificado com o verificador automático**. O verificador de acessibilidade do Acrobat, tratado em `R1`, confirma que os campos existem, que estão etiquetados e que têm descrição. Não sabe se a descrição faz sentido, se a ordem de tabulação é razoável, ou se o formulário é preenchível de ponta a ponta.

Isso só se descobre preenchendo-o. Duas vezes: uma só com teclado, outra com leitor de ecrã.

Reserve tempo para isto. Num formulário de vinte campos, os dois testes levam menos de meia hora e apanham mais problemas do que todo o resto da verificação junto.

### Testar o Formulário com Teclado

**Preparação**

- Abra o PDF no Adobe Acrobat Reader, num computador.
- **Ponha o rato de lado.** Não lhe toque durante o teste. Se sentir a tentação de o usar, é sinal de que encontrou um problema.
- Confirme que o realce de campos está ativo, para ver onde está o foco: **Editar → Preferências → Formulários →** marque **Mostrar cor de destaque nos campos**. Nota: esta é uma definição **do visualizador**, não do ficheiro. Um utilizador com ela desligada não vê os campos destacados, o que reforça a necessidade de os campos terem contorno próprio, desenhado no documento.

**Percurso**

1. Coloque o foco no início do documento e prima `Tab` uma vez.
2. Continue a premir `Tab` até chegar ao fim do formulário, **sem saltar nada**.
3. Depois faça o caminho inverso com `Shift+Tab`.
4. Em cada campo, experimente escrever ou selecionar, conforme o tipo.

**Lista de verificação**

| O que verificar | Como | Falha se |
|---|---|---|
| **Todos os campos são alcançáveis** | Conte os campos que a página mostra e os que o `Tab` visita | O `Tab` salta algum |
| **A ordem faz sentido** | Vá seguindo com o olhar a sequência do foco | O foco salta entre colunas, volta atrás ou termina fora de sítio (rever `F4`) |
| **O foco é sempre visível** | Veja onde está o realce em cada paragem | Perde-se de vista, ou desaparece sobre fundos escuros ou imagens |
| **Não há armadilhas** | Entre e saia de todos os campos, incluindo listas e campos multilinha | `Tab` deixa de funcionar dentro de um campo e o utilizador fica preso |
| **Caixas de verificação** | `Espaço` para marcar e desmarcar | Só respondem ao rato |
| **Botões de opção** | Setas para percorrer o grupo, `Espaço` para escolher | O `Tab` visita cada botão individualmente — sinal de que não formam grupo (rever `F3`) |
| **Listas pendentes** | Setas para percorrer, `Enter` para confirmar | Abrem mas não fecham, ou selecionam ao passar |
| **Botões** | `Enter` ou `Espaço` para ativar | Nada acontece, ou algo acontece só ao passar o foco (rever `F5`) |
| **Nada dispara sozinho** | Percorra tudo sem ativar nada | Uma janela abre, o formulário limpa-se ou salta de página só por o foco lá ter passado |

### Testar o Formulário com Leitor de Ecrã

**Preparação**

- Use o NVDA, que é gratuito e é o leitor recomendado para os exercícios deste curso, no Windows, com o Adobe Acrobat Reader.
- Se puder, repita com o JAWS. Repetir com um segundo leitor apanha diferenças de comportamento que são mais frequentes nos formulários do que em qualquer outro tipo de conteúdo.
- **Baixe o volume, não feche os olhos.** Precisa de comparar o que ouve com o que está no ecrã.

**Percurso**

*Primeira passagem — leitura corrida.* Leia o documento do princípio ao fim com as setas ou com o comando de leitura contínua. Aqui verifica que os rótulos visíveis, as instruções e o texto de enquadramento estão todos presentes e pela ordem certa.

*Segunda passagem — preenchimento.* Percorra os campos com `Tab`, como um utilizador faria, e preencha o formulário a sério.

**O que se deve ouvir em cada campo**

Um anúncio completo tem quatro partes: **nome**, **tipo**, **estado** e **valor**. Nem sempre por esta ordem, e a formulação exata varia entre leitores — o que interessa é que as quatro informações lá estejam.

| Tipo de campo | O que se deve ouvir | O que indica problema |
|---|---|---|
| **Campo de texto vazio** | "Nome completo (obrigatório), caixa de edição, em branco" | "Texto1, caixa de edição" — falta a descrição da ferramenta (`F2`) |
| **Campo de texto preenchido** | "Data de nascimento (dd/mm/aaaa), caixa de edição, 15/03/1980" | O leitor não repete o valor introduzido |
| **Caixa de verificação** | "Autorizo o tratamento dos meus dados, caixa de verificação, não marcada" | Falta o estado, ou o nome é o nome interno |
| **Botão de opção** | "Modalidade: presencial, botão de opção, 1 de 3, não selecionado" | Falta o "1 de 3" — os botões não estão agrupados (`F3`) |
| **Lista pendente** | "Distrito, caixa de combinação, Lisboa, 1 de 18" | Anuncia só "caixa de combinação" |
| **Botão** | "Submeter candidatura, botão" | Anuncia só "botão" (`F5`) |
| **Campo só de leitura** | "Total, caixa de edição, só de leitura, 250 euros" | Não indica que é só de leitura, e o utilizador tenta escrever |

**Outros pontos a confirmar**

- **O modo de formulário entra e sai como deve ser.** Ao chegar a um campo de edição, o leitor de ecrã passa ao modo de introdução de texto, e as teclas deixam de ser comandos de navegação. Confirme que entra ao chegar ao campo e que sai ao abandoná-lo.
- **As instruções gerais são ouvidas.** Se pôs uma nota no topo a explicar o formulário, confirme que ela é lida na leitura corrida e que não ficou presa numa caixa de texto fora da ordem de leitura.
- **Uma mensagem de erro é percetível e o foco não se perde.** Provoque um erro de propósito. Ouça a caixa de alerta e, depois de a fechar, verifique onde ficou o foco. Se ficou num sítio imprevisível, registe a limitação e considere abandonar a validação por alerta a favor da informação antecipada (`F6`).
- **A submissão dá resposta.** Prima o botão de submissão e confirme que alguma coisa é anunciada. Um formulário que submete em silêncio deixa o utilizador sem saber se o fez.

---

## Recomendações para Conteúdo Acessível

As decisões seguintes não são técnicas. São de escrita e de conceção, e têm mais efeito na experiência real do que quase tudo o que está nos procedimentos.

**Encurte o formulário.** Cada campo custa tempo a toda a gente e custa muito mais a quem preenche com teclado ou com leitor de ecrã. Pergunte, campo a campo, se a informação é mesmo necessária, se já não a tem, e o que aconteceria se não a pedisse.

**Explique o formulário antes de o primeiro campo.** No topo, em texto normal: para que serve, quanto tempo demora, que documentos são precisos, o que acontece depois de submeter, e a quem recorrer em caso de dúvida.

**Escreva os rótulos em linguagem clara.** "Rendimento anual ilíquido do agregado familiar" pede uma explicação; "Quanto ganharam, ao todo, as pessoas que vivem consigo, num ano, antes de descontos" já não pede. Se o termo técnico for obrigatório por razões legais, ponha-o e explique-o a seguir.

**Peça a informação pela ordem em que as pessoas a têm.** Um formulário que salta de dados pessoais para dados bancários e volta aos dados pessoais obriga o utilizador a andar para trás e para a frente nos seus papéis.

**Diga o formato antes, não depois.** Vale a pena repetir: a instrução no rótulo evita o erro; a mensagem de erro só o remedeia.

**Não bloqueie o ficheiro contra leitores de ecrã.** Se aplicar segurança ao PDF, confirme em **Ficheiro → Propriedades → separador Segurança** que o acesso ao texto por dispositivos de leitura de ecrã continua permitido. Uma restrição mal escolhida torna o documento mudo para quem mais precisa dele.

**Garanta que o formulário se pode guardar preenchido.** Um formulário que só permite imprimir obriga quem o preenche a fazer tudo de uma vez, sem interrupções. Para formulários longos, é uma barreira séria — para quem se cansa, para quem tem de procurar documentos a meio, para quem só pode usar o computador em períodos curtos.

**Ofereça sempre um caminho alternativo.** Um telefone, um endereço de correio eletrónico, um balcão. Por melhor que esteja o formulário, haverá quem não consiga usá-lo — e a alternativa não é uma concessão, é parte do serviço.

**Não use um formulário digitalizado.** Uma imagem de um impresso não é um formulário, mesmo depois de OCR. Se o original em papel é o que existe, refaça-o.

### Erros Comuns

| Erro | Porque é grave | Correção |
|---|---|---|
| Linhas e sublinhados em vez de campos | Não há nada onde escrever com teclado | `F1` |
| Aceitar a deteção automática sem rever | Os campos ficam com nomes internos e tipos errados | `F1`, `F2` |
| Descrição da ferramenta vazia | O campo é anunciado sem nome | `F2` |
| Confundir o Nome com a descrição | O utilizador ouve "campo_txt_03" | `F2` |
| Preencher a descrição **e** o texto alternativo com textos diferentes | Anúncios duplicados ou imprevisíveis, conforme o leitor | `F2` |
| Botões de opção com nomes diferentes | Deixam de ser exclusivos: pode marcar-se tudo | `F3` |
| Caixas de verificação com o mesmo nome | Passam a exclusivas: só se pode marcar uma | `F3` |
| Opções sem a pergunta na descrição | "Presencial" não responde a nada | `F3` |
| Não definir a ordem de tabulação | O `Tab` segue a ordem de criação dos campos | `F4` |
| Definir a ordem de tabulação só na primeira página | As restantes ficam por corrigir | `F4` |
| Botão sem descrição | Anunciado apenas como "botão" | `F5` |
| Ação no acionador de foco | O formulário reage sozinho à passagem do `Tab` | `F5` |
| Botão de limpar ao lado do de submeter, sem aviso | Apaga tudo, sem desfazer | `F5` |
| Campos obrigatórios assinalados só a vermelho | A cor não chega | `F6` |
| Formato de data americano num formulário português | Erros repetidos e inexplicáveis para o utilizador | `F6` |
| Mensagem de erro genérica | Diz que há um problema, não diz qual | `F6` |
| Data repartida por três campos | Triplica o esforço para recolher uma informação | `F1` |
| Segurança do PDF a bloquear leitores de ecrã | O documento fica mudo | Recomendações |
| Dar por verificado só porque o verificador não acusou nada | O verificador não preenche formulários | Verificação |

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Um campo de formulário é equipamento instalado por cima do edifício.** Só existe para a tecnologia de apoio se for acrescentado à planta — ou seja, se for um campo real e estiver etiquetado.
2. **Sublinhados não são campos.** São tinta. Não recebem foco, não recebem texto, não têm função.
3. **A deteção automática é um ponto de partida, nunca um resultado.** Acerta na posição, falha no nome e muitas vezes no tipo.
4. **A Descrição da ferramenta é o nome acessível.** O Nome é o identificador dos dados; o valor de exportação é dado; a etiqueta do botão é desenho. Só a descrição é anunciada de forma fiável.
5. **Preencha um só sítio.** Descrição da ferramenta preenchida, texto alternativo da etiqueta `<Form>` vazio. Dois textos diferentes produzem comportamentos imprevisíveis.
6. **O nome partilhado é o que agrupa os botões de opção** — e é o que faz o leitor de ecrã anunciar "1 de 3". Cada opção deve levar a pergunta na descrição.
7. **A ordem de tabulação não segue a ordem visual.** Segue a ordem de criação dos campos, até se dizer o contrário. Escolha **Utilizar a estrutura do documento**, em todas as páginas.
8. **Os botões precisam de descrição, como qualquer outro campo**, e a ação deve estar no acionador `Rato solto`, nunca no foco.
9. **Prevenir vale mais do que corrigir.** O formato esperado deve estar no rótulo e na descrição, antes de o utilizador escrever. A caixa de alerta é o último recurso, não o primeiro.
10. **A verificação faz-se preenchendo o formulário** — uma vez só com teclado, outra com leitor de ecrã. O verificador automático não substitui nenhuma das duas.
11. **A pergunta anterior a todas continua a ser se devia ser um PDF.** Um formulário web é geralmente preferível. A decisão pertence à secção "Escolher o Formato e Organizar o Trabalho".

### Exercícios Práticos

**Exercício 1 — Encontrar o formulário que não é um formulário**

Procure no sítio de uma entidade pública portuguesa um formulário em PDF descarregável. Abra-o no Acrobat Reader e prima `Tab` cinco vezes.

Responda: existem campos reais? Quantos foram visitados? O que acontece a alguém que só tenha teclado? Se não encontrar nenhum campo, tem entre mãos exatamente o caso do "antes" de `F1`. Guarde o ficheiro: vai voltar a usá-lo.

**Exercício 2 — Auditar as descrições**

Num formulário em PDF com campos reais — o que encontrou, ou um fornecido pelo formador — abra a ferramenta **Preparar um formulário** e construa uma tabela com quatro colunas: rótulo visível na página, Nome, Descrição da ferramenta, e obrigatório sim/não.

Depois assinale: quantos campos têm a descrição vazia? Em quantos a descrição é diferente do rótulo visível? Em quantos o formato esperado não está indicado em lado nenhum?

**Exercício 3 — Corrigir um grupo**

Pegue num formulário com um conjunto de botões de opção. Verifique se partilham o mesmo Nome. Se não partilharem, corrija: nome comum, escolhas de botão distintas, e a pergunta no início da descrição de cada opção.

Teste com `Tab` e com as setas antes e depois da correção, e registe a diferença no número de paragens do `Tab`.

**Exercício 4 — A ordem de tabulação**

Num formulário com campos dispostos em duas colunas, percorra-o com `Tab` e desenhe num papel o percurso do foco, numerando os campos pela ordem por que são visitados.

Depois aplique **Utilizar a estrutura do documento** a todas as páginas e repita o desenho. Compare os dois percursos. Se não mudaram, verifique a árvore de etiquetas: é provável que o problema esteja lá, e não na tabulação.

**Exercício 5 — Preencher às cegas**

Peça a um colega que preencha, com o NVDA e sem olhar para o ecrã, um formulário que você tenha corrigido. Fique a observar em silêncio, sem ajudar.

Registe: em que campos hesitou, em que campos teve de recuar, quantas vezes perguntou "o que é que isto quer?". Cada hesitação corresponde a um procedimento desta secção. Identifique qual.

**Exercício 6 — A pergunta que fica**

Escolha um formulário em PDF do seu serviço e escreva meia página a responder a três perguntas: quantas pessoas o preenchem por ano, o que aconteceria se fosse um formulário web, e o que impede essa mudança hoje.

Guarde a resposta. Vai ser o material de trabalho da secção "Escolher o Formato e Organizar o Trabalho".

