---
title: Documentos Word
layout: default
nav_order: 2
---
# Documentos Word

## Introdução

### O Que Distingue o Word

Na secção "Fundamentos da Acessibilidade de Documentos" vimos que um documento é como um edifício e que as etiquetas são a planta desse edifício. Quem vê, vê o edifício. A tecnologia de apoio lê a planta.

O Word tem uma característica que nenhuma outra aplicação deste curso tem: **é onde a planta é desenhada**. Não é onde a planta se corrige, nem onde se verifica se ela sobreviveu a uma exportação. É onde ela nasce.

Isto tem três consequências práticas.

**Primeira: no Word, a estrutura é barata.** Aplicar um estilo de cabeçalho demora um segundo. Corrigir a mesma falha mais tarde, num PDF já gerado, pode demorar uma tarde. Todo o trabalho que se faz corretamente aqui poupa trabalho a jusante — e todo o trabalho que se faz mal aqui é herdado por todos os formatos que venham a seguir.

**Segunda: no Word, o conteúdo flui.** Ao contrário de um PDF, um documento Word não tem páginas fixas: tem um fluxo de texto que se reorganiza quando alguém aumenta o tamanho da letra, muda o tipo de letra ou estreita a janela. Uma pessoa com baixa visão que ponha o documento a 300% continua a conseguir lê-lo linha a linha. Esta é uma vantagem enorme — mas só funciona se não a estragarmos com caixas de texto, tabelas usadas para desenhar o aspeto da página ou espaços em branco a fazer de margens.

**Terceira: o documento Word não é apenas um passo intermédio.** Muitos documentos são distribuídos em `.docx` e lidos diretamente nesse formato. Os leitores de ecrã leem ficheiros Word nativamente e usam a estrutura que lá encontram. Um `.docx` mal estruturado é, por si só, uma barreira — mesmo que nunca chegue a ser convertido para PDF.

> **Analogia.** No Word, estamos a construir o edifício e a desenhar a planta ao mesmo tempo, com o mesmo gesto. Cada estilo aplicado é uma linha na planta. Se em vez de aplicar estilos pintarmos o texto à mão — negrito, corpo 16, centrado —, o edifício fica com bom aspeto e a planta fica em branco.

### Das Propriedades às Funcionalidades do Word

As sete propriedades de um documento acessível foram definidas na secção "Fundamentos da Acessibilidade de Documentos". A tabela seguinte mostra onde cada uma se obtém no Word e em que procedimento desta secção é tratada.

| Propriedade | No Word obtém-se com | Procedimento |
|---|---|---|
| Identificado | Título nas propriedades do ficheiro; idioma do documento | W6 |
| Estruturado | Estilos de cabeçalho, listas automáticas, tabelas com linha de cabeçalho | W1, W2, W3 |
| Com ordem de leitura correta | Fluxo único de texto; objetos alinhados com o texto; colunas verdadeiras | W2, W4 |
| Percetível sem ver | Texto alternativo em imagens, gráficos e outros objetos | W4 |
| Legível | Tipo de letra, tamanho, contraste, espaçamento; idioma correto | W8, W6 |
| Navegável | Cabeçalhos + Painel de Navegação; texto de ligação com sentido | W1, W5 |
| Operável | Controlos de conteúdo com título, em vez de linhas para preencher à mão | W7 |

Repare numa coisa: **a mesma funcionalidade serve várias propriedades**. Os estilos de cabeçalho (W1) dão estrutura, dão navegação e dão ordem de leitura, tudo ao mesmo tempo. É por isso que W1 é o procedimento mais importante desta secção.

---

## Procedimentos

Cada procedimento segue a mesma estrutura: o que se pretende, os passos no Word, um exemplo antes e depois, e a explicação do que muda para quem usa tecnologia de apoio.

Os caminhos de menu referem-se ao Microsoft Word do Microsoft 365, em português europeu. Alguns nomes de comandos variam entre versões e canais de atualização.

---

### W1. Estilos e Cabeçalhos

**O que se pretende**

Um documento **estruturado** e **navegável**. Este é o procedimento que cria a planta do edifício — todos os outros a completam.

Depende dele:

- quem usa leitor de ecrã e navega saltando de cabeçalho em cabeçalho, em vez de ouvir o documento inteiro do princípio ao fim;
- quem tem baixa visão e amplia muito o documento, e precisa de saber onde está sem ver a página toda;
- quem tem dificuldades de concentração ou de leitura e precisa de um mapa do documento;
- quem vai exportar o documento para PDF ou HTML, porque é daqui que saem as etiquetas;
- e quem quer um índice automático que funcione.

> **O ponto mais importante desta secção.** Os estilos não são decoração. Não são uma forma mais rápida de pôr o texto bonito. **São o mecanismo que cria a estrutura do documento.**
>
> Quando alguém escreve "1. Enquadramento", seleciona o texto e põe negrito, tamanho 16 e cor azul, está a **pintar o edifício**. Quando aplica o estilo "Título 1", está a **desenhar a planta**. No ecrã, os dois resultados podem ser indistinguíveis. Para a tecnologia de apoio, um deles é um cabeçalho e o outro é um parágrafo qualquer que por acaso está em negrito.
>
> Um documento com formatação direta é uma fotografia do edifício. Bonita, legível para quem vê, e completamente muda para quem lê a planta.

**Passos no Word**

1. **Aplicar um cabeçalho:** coloque o cursor no parágrafo e vá a **Base → grupo Estilos** e escolha **Título 1**, **Título 2**, **Título 3**, conforme o nível.
   - Atalhos de teclado: `Ctrl+Alt+1`, `Ctrl+Alt+2`, `Ctrl+Alt+3`. `Ctrl+Shift+N` devolve o parágrafo ao estilo **Normal**.
2. **Ver a lista completa de estilos:** **Base → grupo Estilos →** botão de expansão no canto inferior direito do grupo (`Alt+Ctrl+Shift+S`).
3. **Mudar o aspeto de um estilo** (em vez de formatar à mão): clique com o botão direito sobre o estilo na galeria → **Modificar…**. Altere tipo de letra, tamanho, cor e espaçamento aí. A alteração aplica-se a todo o documento de uma vez.
4. **Ver a planta:** **Ver → Painel de Navegação** (`Ctrl+F` também o abre). O painel mostra a lista hierárquica dos cabeçalhos. Se o painel estiver vazio ou desarrumado, o documento não tem estrutura.

**Regras de hierarquia**

- Use **um único "Título 1"** por documento, para o título principal. Os grandes blocos são "Título 2", as suas divisões "Título 3", e assim sucessivamente.
- **Não salte níveis.** Depois de um "Título 2" não use um "Título 4".
- **Não use cabeçalhos para destacar texto.** Se quer só destacar, use negrito ou um estilo de carácter.
- **Não deixe cabeçalhos verdadeiros por marcar.** Se aquilo é um título de secção, tem de ter estilo de cabeçalho — mesmo que seja curto, mesmo que seja "Anexo I".

**Antes e depois**

*Antes — formatação direta:*

```
RELATÓRIO DE ATIVIDADES 2025      ← Calibri 20, negrito, centrado, azul
                                   ← linha em branco
1. Enquadramento                   ← Calibri 14, negrito
O presente relatório...            ← Calibri 11
                                   ← linha em branco
1.1 Objetivos                      ← Calibri 12, negrito, itálico
```

O que o leitor de ecrã lê: *"Relatório de atividades 2025. Em branco. 1 Enquadramento. O presente relatório… Em branco. 1.1 Objetivos."* — cinco parágrafos normais e duas linhas vazias. O Painel de Navegação está em branco. A tecla de salto entre cabeçalhos não faz nada.

*Depois — estilos:*

```
Relatório de Atividades 2025       ← estilo "Título 1"
1. Enquadramento                   ← estilo "Título 2"
O presente relatório...            ← estilo "Normal"
1.1 Objetivos                      ← estilo "Título 3"
```

O que o leitor de ecrã lê: *"Relatório de atividades 2025, cabeçalho de nível 1. 1 Enquadramento, cabeçalho de nível 2. O presente relatório… 1.1 Objetivos, cabeçalho de nível 3."*

**O que funciona melhor no segundo exemplo:** o aspeto visual pode ser exatamente o mesmo — a diferença é que agora existe uma planta. Repare também que desapareceram as linhas em branco: o espaço entre parágrafos passa a vir do próprio estilo (ver W8), o que elimina o ruído do "em branco, em branco" e evita espaços a mais quando o texto é reformatado.

**Porque funciona**

Com cabeçalhos reais, quem usa leitor de ecrã pode:

- premir `H` (no NVDA e no JAWS, em modo de leitura) para saltar para o cabeçalho seguinte, ou `1`, `2`, `3` para saltar de nível em nível;
- pedir a **lista de cabeçalhos** (`Insert+F7` no NVDA) e obter, em segundos, o índice do documento — o equivalente auditivo a folhear;
- saber sempre a que profundidade da estrutura está, porque o nível é anunciado.

Sem cabeçalhos reais, a única forma de encontrar a secção 4.2 é ouvir tudo o que vem antes dela. É a diferença entre consultar um documento e ter de o ouvir inteiro.

A estrutura de cabeçalhos é também o que suporta o critério **1.3.1 Informação e Relações** e o que dá sentido ao **2.4.6 Cabeçalhos e Etiquetas**.

---

### W2. Listas e Colunas

**O que se pretende**

Um documento **estruturado** com **ordem de leitura correta**. Uma lista tem de ser reconhecida como lista, e um texto em colunas tem de ser lido coluna a coluna, não linha a linha através das colunas.

Depende disto quem usa leitor de ecrã (que anuncia o número de itens e a posição dentro da lista) e quem amplia muito o documento (porque as listas e colunas verdadeiras reorganizam-se, e as falsas não).

**Passos no Word**

*Listas:*

1. **Base → grupo Parágrafo → Lista com Marcas** (lista não ordenada) ou **Lista Numerada** (lista ordenada).
2. Para sublistas, coloque o cursor no início do item e prima `Tab` — ou use **Base → Parágrafo → Aumentar Avanço**. `Shift+Tab` volta ao nível anterior.
3. Para listas com numeração multinível (1., 1.1, 1.1.1), use **Base → Parágrafo → Lista de Vários Níveis**.

*Colunas:*

1. Selecione o texto e vá a **Esquema → grupo Configurar Página → Colunas**.
2. Nunca crie colunas com tabulações, com espaços, com duas caixas de texto lado a lado ou com uma tabela de duas células.

**Antes e depois**

*Antes — lista escrita à mão:*

```
Documentos necessários:
- Cartão de cidadão
- Comprovativo de morada
- Declaração de IRS
```

Os hífenes foram escritos com o teclado. O leitor de ecrã lê: *"Traço cartão de cidadão. Traço comprovativo de morada. Traço declaração de IRS."* — três parágrafos independentes. Não há noção de conjunto, nem de quantos elementos existem, nem de onde a lista acaba.

*Depois — lista automática:*

O mesmo texto, com o estilo de lista com marcas aplicado. O leitor de ecrã lê: *"Lista com três itens. Marca, cartão de cidadão, um de três. Marca, comprovativo de morada, dois de três. Marca, declaração de IRS, três de três. Fim de lista."*

**O que funciona melhor no segundo exemplo:** quem ouve sabe imediatamente que vai ouvir três coisas, sabe em qual está e sabe quando a lista terminou. Numa lista de vinte requisitos, esta diferença é decisiva. E há um ganho adicional: se depois se acrescentar um item a meio de uma lista numerada, a numeração corrige-se sozinha — com números escritos à mão, ficam duas alíneas "c)".

*Antes — colunas falsas:*

Duas caixas de texto lado a lado, uma com a versão portuguesa e outra com a versão inglesa de um aviso. Visualmente, duas colunas perfeitas. Na leitura, o resultado depende da ordem em que as caixas foram inseridas — e pode ser lida primeiro a caixa da direita, ou pode nem sequer ser lida.

*Depois — colunas verdadeiras:*

O mesmo texto num fluxo único, com **Esquema → Colunas → Duas**. O leitor de ecrã lê o texto português todo e só depois o inglês, pela ordem correta. E, ao ampliar, as colunas reorganizam-se em vez de forçarem deslocação horizontal.

**Porque funciona**

Listas e colunas verdadeiras produzem estrutura no ficheiro, e não apenas um arranjo de pixels. Quem lê com os olhos vê o mesmo nos dois casos; quem depende da planta vê, num caso, uma relação explícita entre os itens e, no outro, nada.

---

### W3. Tabelas

**O que se pretende**

Uma tabela **estruturada**: cada célula de dados tem de poder ser associada ao cabeçalho que a explica. Sem isso, quem não vê a tabela ouve uma sequência de valores soltos — "2 850", "1 200", "Sim" — sem saber a que coluna pertencem.

Depende disto sobretudo quem usa leitor de ecrã, e também quem amplia muito e perde de vista a linha de cabeçalho ao percorrer a tabela.

**Regra prévia: tabelas são para dados.**

Uma tabela serve para apresentar informação que tem duas dimensões — linhas e colunas com significado. **Não serve para dispor elementos na página.** Se está a usar uma tabela para pôr um logótipo à esquerda e um texto à direita, para criar um cabeçalho de página ou para simular colunas, está a criar uma relação de dados que não existe, e a tecnologia de apoio vai anunciá-la como tal.

**Passos no Word**

1. **Criar:** **Inserir → Tabela** e escolha o número de linhas e colunas.
2. **Marcar a linha de cabeçalho:** coloque o cursor na tabela e vá a **Estrutura da Tabela → grupo Opções de Estilo de Tabela →** marque **Linha de Cabeçalho**.
3. **Repetir o cabeçalho em cada página:** selecione a primeira linha e vá a **Esquema (da tabela) → grupo Dados → Repetir Linhas de Cabeçalho**. É este comando que, para efeitos de estrutura, identifica a linha como cabeçalho — faça sempre os dois passos.
4. **Impedir que as linhas se partam entre páginas:** **Esquema (da tabela) → Propriedades → separador Linha →** desmarque **Permitir divisão da linha entre páginas**.
5. **Descrever a tabela:** **Propriedades da Tabela → separador Texto Alternativo**. Use-o para explicar o que a tabela contém, se isso não for óbvio pelo texto à volta.
6. **Legendar:** **Referências → Inserir Legenda** cria uma legenda numerada, útil quando o documento tem várias tabelas e o texto lhes faz referência.

**Regras de estrutura**

- Uma linha de cabeçalho, no topo. Sem células unidas, sem células divididas, sem tabelas dentro de tabelas.
- Sem linhas ou colunas vazias para criar espaço. O espaçamento faz-se nas propriedades da tabela, não com vazios.
- Sem células vazias sem razão: se uma célula não tem valor, escreva "—" ou "Sem dados". Uma célula vazia é ambígua — pode ser um zero, pode ser um valor desconhecido, pode ser um erro.
- **O Word não permite marcar cabeçalhos de coluna à esquerda nem associar células a mais do que um cabeçalho.** Se a sua tabela precisa disso, ela é demasiado complexa para este formato: divida-a em várias tabelas simples, cada uma com o seu cabeçalho e o seu título.

**Antes e depois**

*Antes:*

| | 2024 | 2025 |
|---|---|---|
| **Ações de formação** | 42 | 58 |
| **Participantes** | 610 | 845 |

A primeira linha não está marcada como cabeçalho; a primeira célula está vazia; os rótulos da esquerda estão a negrito, o que sugere visualmente que são cabeçalhos, mas o negrito é pintura, não é planta.

O leitor de ecrã lê, ao percorrer a segunda linha: *"Ações de formação. 42. 58."* — 42 de quê? De que ano?

*Depois:*

| Indicador | 2024 | 2025 |
|---|---|---|
| Ações de formação | 42 | 58 |
| Participantes | 610 | 845 |

Com a linha de cabeçalho marcada e repetida, o leitor de ecrã anuncia, ao entrar em cada célula: *"2025, ações de formação, 58."*

**O que funciona melhor no segundo exemplo:** a primeira célula deixou de estar vazia e passou a nomear o que está na coluna ("Indicador"); a linha de cabeçalho está marcada, e não apenas a negrito; e cada valor passa a ser anunciado com o seu contexto. Continua a ser uma tabela simples, de leitura direta — que é exatamente o objetivo.

**Porque funciona**

Quando a linha de cabeçalho está marcada, o leitor de ecrã guarda-a e repete-a a cada célula que o utilizador visita, exatamente como o olho volta ao topo da coluna para confirmar o que está a ler. Sem essa marcação, a tabela reduz-se a uma sequência linear de valores — que é a forma mais eficaz de tornar dados inúteis.

Este procedimento serve o critério **1.3.1 Informação e Relações**: a relação entre o valor e o cabeçalho existe visualmente e tem de existir também de forma programática.

---

### W4. Texto Alternativo e Objetos

**O que se pretende**

Um documento **percetível sem ver** e com **ordem de leitura correta**. Todo o conteúdo que é transmitido por uma imagem, um gráfico, um ícone ou um esquema tem de estar também disponível em texto — e todos esses objetos têm de estar num sítio previsível dentro do fluxo de leitura.

Depende disto quem usa leitor de ecrã, quem desliga as imagens por razões de largura de banda, e também quem tem dificuldades de interpretação visual e beneficia de uma explicação escrita ao lado do gráfico.

**Passos no Word**

1. **Escrever texto alternativo:** clique com o botão direito sobre a imagem → **Ver Texto Alternativo…**. Escreva a descrição no campo do painel que se abre à direita.
2. **Marcar uma imagem como decorativa:** no mesmo painel, marque **Marcar como decorativo**. Use isto apenas quando a imagem não transmite informação nenhuma — uma linha separadora, um fundo, um enfeite.
3. **Alinhar o objeto com o texto:** selecione a imagem → **Formatar Imagem → Moldar Texto → Alinhado com o Texto**. Objetos flutuantes (com moldagem "quadrado", "à frente do texto", etc.) não têm posição fiável no fluxo de leitura.
4. **Desligar o texto alternativo automático:** **Ficheiro → Opções → Facilidade de Acesso →** desmarque **Gerar automaticamente texto alternativo para mim**. As descrições automáticas ("Poderá ser uma imagem de texto") não substituem uma descrição escrita por quem sabe o que a imagem quer dizer.

**Como escrever o texto alternativo**

- Descreva a **função** da imagem naquele documento, não a imagem em si. A mesma fotografia de um edifício pode precisar de "Sede do organismo, na Avenida da Liberdade" ou de "Fachada com rampa de acesso à entrada principal", conforme o que se está a dizer.
- Não comece por "Imagem de…" ou "Fotografia de…". O leitor de ecrã já anuncia que é uma imagem.
- Seja breve. Uma ou duas frases. Se precisa de mais, a informação deve estar no corpo do texto e a imagem deve remeter para ela.
- **Gráficos e SmartArt não se descrevem, explicam-se.** O texto alternativo diz o que o gráfico mostra; os dados devem estar acessíveis noutro sítio, tipicamente numa tabela simples (ver W3) ou num parágrafo.

**Sobre caixas de texto:** evite-as. O conteúdo de uma caixa de texto vive fora do fluxo principal do documento e a sua posição na ordem de leitura é imprevisível. Se precisa de destacar um aviso, use um parágrafo com um estilo próprio — bordas, sombreado, avanço —, que continua a fazer parte do fluxo.

**Antes e depois**

*Antes:*

> Imagem de um gráfico de barras.
> Texto alternativo: `grafico_final_v3.png`

O leitor de ecrã lê: *"Gráfico underscore final underscore v3 ponto png, imagem."* O nome do ficheiro não diz nada a ninguém — e, pior, dá a ilusão de que existe descrição.

*Depois:*

> Mesmo gráfico.
> Texto alternativo: `Evolução do número de participantes em ações de formação, de 2021 a 2025. Crescimento contínuo, de 310 para 845.`
>
> E, logo abaixo do gráfico, no corpo do documento, uma tabela simples com os cinco valores anuais.

**O que funciona melhor no segundo exemplo:** o texto alternativo transmite a **mensagem** do gráfico — a tendência —, que é aquilo que quem vê apreende num relance. E os números exatos, que não cabem numa descrição curta, ficam disponíveis numa tabela que qualquer pessoa pode consultar, ler célula a célula ou copiar. Ninguém fica dependente de uma descrição para aceder aos dados.

**Porque funciona**

O texto alternativo é a única entrada que a tecnologia de apoio tem para o conteúdo não textual. Sem ele, a imagem é um buraco no documento: o leitor de ecrã anuncia "imagem" e segue em frente. Com um texto alternativo genérico, o buraco continua lá — apenas com uma tampa por cima.

O alinhamento com o texto resolve um problema diferente e igualmente sério: um objeto flutuante pode ser lido no início da página, no fim, entre duas frases ou em lado nenhum. É o equivalente a ter uma divisão do edifício que não aparece na planta, ou que aparece no andar errado.

Este procedimento serve o critério **1.1.1 Conteúdo Não Textual**.

---

### W5. Hiperligações

**O que se pretende**

Um documento **navegável**: cada ligação tem de dizer para onde vai, mesmo quando é lida isolada do texto à volta.

Depende disto quem usa leitor de ecrã e pede a lista de ligações do documento — uma funcionalidade comum, que apresenta as ligações fora do contexto —, e quem navega por teclado saltando de ligação em ligação.

**Passos no Word**

1. Selecione o texto que quer transformar em ligação e prima `Ctrl+K` (ou **Inserir → Ligação**).
2. No campo **Texto a apresentar**, escreva o texto visível; no campo **Endereço**, o URL.
3. Botão **Dica de Ecrã…**: acrescenta uma descrição adicional, útil para avisar de um comportamento inesperado (por exemplo, que a ligação abre um ficheiro para descarregar).
4. Para remover uma ligação: botão direito → **Remover Hiperligação**.

**Regras**

- O texto da ligação deve descrever o destino: "Formulário de candidatura", e não "aqui", "este link", "saiba mais", "clique aqui".
- **Duas ligações com o mesmo texto devem ir para o mesmo sítio.** Cinco "Mais informação" que vão para cinco páginas diferentes são cinco vezes o mesmo rótulo inútil.
- **URLs por extenso não são texto de ligação.** Um endereço longo é lido carácter a carácter por alguns leitores de ecrã, e uma cadeia de sessenta carateres alfanuméricos é impossível de reter.
- **Exceção: documentos feitos para imprimir.** Se o documento vai ser impresso, o endereço tem de estar visível em papel. Nesse caso, escreva o texto descritivo e o endereço a seguir, entre parênteses ou numa nota de rodapé — e prefira endereços curtos.
- Avise quando o destino não é uma página normal: "Guia de boas práticas (PDF, 2 MB)".

**Antes e depois**

*Antes:*

> Para consultar as regras de candidatura, clique aqui. Para descarregar o formulário, clique aqui. Para ver as datas, clique aqui.

Lista de ligações que o leitor de ecrã apresenta: *"aqui, aqui, aqui"*. O utilizador tem três ligações e nenhuma informação.

*Depois:*

> Consulte as **regras de candidatura**, descarregue o **formulário de candidatura (PDF, 340 KB)** e confirme as **datas do concurso**.

Lista de ligações: *"regras de candidatura; formulário de candidatura, PDF, 340 KB; datas do concurso"*.

**O que funciona melhor no segundo exemplo:** cada ligação é autossuficiente — funciona sozinha, fora da frase. Além disso, desapareceu a expressão "clique aqui", que pressupõe um rato: quem navega por teclado não clica, e quem usa comandos de voz precisa de dizer o nome da ligação em voz alta. Repare também que o formato e o tamanho do ficheiro estão indicados, o que evita a surpresa de um descarregamento inesperado.

**Porque funciona**

Quem lê com os olhos absorve a ligação e a frase à volta ao mesmo tempo. Quem navega por ligações recebe-as em lista, despidas de contexto. Um texto de ligação com sentido é o que torna essas duas experiências equivalentes — que é a ideia por detrás do critério **2.4.4 Finalidade da Ligação (Em Contexto)**.

---

### W6. Idioma e Título do Documento

**O que se pretende**

Um documento **identificado** e **legível**. O título diz o que o documento é, antes de ele ser aberto; o idioma diz ao sintetizador de voz como pronunciar as palavras.

Depende do título quem gere muitos ficheiros com tecnologia de apoio e precisa de os distinguir; depende do idioma toda a gente que usa síntese de voz — e depende dele também qualquer tradução automática ou correção ortográfica.

**Passos no Word**

*Título do documento:*

1. **Ficheiro → Informações**. No painel direito, em **Propriedades**, clique no campo **Título** e escreva o título real do documento.
2. Em alternativa: **Ficheiro → Informações → Propriedades → Propriedades Avançadas → separador Resumo → Título**.
3. O título é uma propriedade **independente do nome do ficheiro** e independente do texto que está na primeira página. Preencha-o sempre.

*Idioma:*

1. **Idioma principal:** selecione todo o documento (`Ctrl+A`) e vá a **Rever → Idioma → Definir Idioma de Revisão…** → escolha **Português (Portugal)** → **OK**.
2. **Passagens noutro idioma:** selecione apenas essa passagem e repita o procedimento com o idioma correspondente. Faça-o para citações, títulos de obras estrangeiras, expressões técnicas em inglês que sejam frases inteiras.
3. **Atalho:** o idioma da seleção aparece na barra de estado, em baixo; clicar aí abre a mesma caixa de diálogo.
4. **Idioma predefinido para documentos novos:** **Ficheiro → Opções → Idioma**.

**Antes e depois**

*Antes:*

- Nome do ficheiro: `Relatorio_vFinal_2_revCC.docx`
- Título nas propriedades: *(vazio)* — ou, pior, `Documento1`, ou o título de um documento antigo de que este foi cópia.
- Idioma: inglês (herdado do modelo), num documento escrito em português.

Resultado: o leitor de ecrã anuncia o documento pelo nome do ficheiro, com todos os `underscore` lidos em voz alta. E, ao ler o texto, um sintetizador em modo inglês diz *"Rel-a-TOR-ee-oh de a-tiv-i-DAY-dees"* — texto português pronunciado com fonética inglesa. É praticamente incompreensível.

*Depois:*

- Nome do ficheiro: `relatorio-atividades-2025.docx`
- Título nas propriedades: `Relatório de Atividades 2025`
- Idioma: Português (Portugal), com a citação em castelhano do capítulo 3 marcada como Espanhol (Espanha).

**O que funciona melhor no segundo exemplo:** o documento identifica-se a si próprio, com um título legível por uma pessoa e não apenas por um sistema de ficheiros. E o sintetizador muda de motor fonético a meio do documento, lendo a citação com pronúncia castelhana — que é exatamente o que uma pessoa a ler em voz alta faria.

**Porque funciona**

A propriedade "Título" é o que a tecnologia de apoio anuncia ao abrir o ficheiro, é o que aparece em muitos gestores documentais, e é também o que é transportado para os metadados do PDF quando o documento é exportado. Um título por preencher propaga-se por toda a cadeia.

Quanto ao idioma: a síntese de voz escolhe as regras de pronúncia a partir da marcação de idioma, e não do conteúdo. Um documento marcado com o idioma errado não é apenas desagradável de ouvir — é frequentemente ininteligível. Isto corresponde aos critérios **3.1.1 Idioma da Página** e **3.1.2 Idioma dos Elementos**.

---

### W7. Formulários em Word

**O que se pretende**

Um documento **operável**: quem o recebe tem de conseguir preenchê-lo com teclado, saber em que campo está, saber o que esse campo pede e não destruir o documento no processo.

Depende disto quem não usa rato, quem usa leitor de ecrã e quem usa software de reconhecimento de voz.

> **Nota de âmbito.** Este procedimento trata apenas de formulários **criados e preenchidos em Word**. Os formulários em PDF — criação de campos, ordem de tabulação, validação e mensagens de erro — são tratados na secção "Formulários em PDF".

> **Antes de continuar, uma pergunta honesta.** O Word é o formato mais fraco dos três para formulários. Não tem forma de marcar um campo como obrigatório, não tem validação anunciada, não tem mensagens de erro associadas a campos. Se o formulário se destina a distribuição alargada, um formulário web ou um formulário PDF bem construído servem melhor. A decisão sobre o formato é tratada na secção "Escolher o Formato e Organizar o Trabalho". O que se segue aplica-se quando a decisão já foi tomada e o formato é mesmo o Word.

**Passos no Word**

1. **Ativar o separador Programador:** **Ficheiro → Opções → Personalizar Friso →** na lista da direita, marque **Programador** → **OK**.
2. **Inserir campos:** **Programador → grupo Controlos** e escolha o tipo adequado:
   - **Controlo de Conteúdo de Texto Simples** — respostas curtas;
   - **Controlo de Conteúdo de Texto Formatado** — respostas longas;
   - **Caixa de Verificação** — sim/não, opções múltiplas;
   - **Lista Pendente** ou **Caixa de Combinação** — escolha entre opções fixas;
   - **Selecionador de Datas** — datas.
3. **Dar nome ao campo (passo essencial):** selecione o controlo → **Programador → Propriedades** → preencha o campo **Título**. É este texto que a tecnologia de apoio anuncia. O campo **Etiqueta** é um identificador interno e não é lido.
4. **Proteger o documento:** **Rever → Restringir Edição →** marque **Permitir apenas este tipo de edição no documento** → escolha **Preenchimento de formulários** → **Sim, Aplicar Proteção**. Com o documento protegido, o `Tab` salta de campo em campo e o resto do texto fica intacto.

**Regras**

- **Cada campo tem de ter um rótulo visível no documento e um Título nas propriedades.** O rótulo visível serve quem vê; o Título serve quem ouve. Devem dizer a mesma coisa.
- Ponha o rótulo **antes** do campo, na ordem de leitura.
- Se o campo exige um formato específico, diga-o no rótulo: "Data de nascimento (dd/mm/aaaa)".
- Indique os campos obrigatórios no próprio rótulo — "Nome completo (obrigatório)" —, porque o Word não tem outra forma de o comunicar. Um asterisco sozinho não chega: é preciso explicar o que o asterisco significa, e mesmo assim é lido apenas como "asterisco".
- Não use tabelas para desenhar o formulário se puder evitá-lo (ver W3).

**Antes e depois**

*Antes:*

```
Nome: _______________________________
Data de nascimento: ____/____/________
[ ] Autorizo o tratamento dos meus dados
```

Isto não é um formulário: é um desenho de um formulário. Os sublinhados são carateres de texto; a caixa de verificação é um par de parênteses retos. O leitor de ecrã lê: *"Nome, dois pontos, sublinhado sublinhado sublinhado sublinhado…"*. Não há onde escrever sem desalinhar tudo, e o `Tab` não salta para lado nenhum.

*Depois:*

```
Nome completo (obrigatório): [Controlo de Texto Simples — Título: "Nome completo"]
Data de nascimento (dd/mm/aaaa): [Selecionador de Datas — Título: "Data de nascimento"]
[Caixa de Verificação — Título: "Autorização de tratamento de dados"] Autorizo o tratamento dos meus dados
```

Documento protegido para preenchimento de formulários.

**O que funciona melhor no segundo exemplo:** existe agora um campo real, com um nome que a tecnologia de apoio anuncia — *"Nome completo, campo de edição"* — em vez de uma linha de sublinhados. O `Tab` percorre os campos pela ordem em que estão no documento. E o formato esperado da data está escrito no rótulo, onde toda a gente o vê e ouve, em vez de estar apenas subentendido pelas barras do desenho.

**Porque funciona**

Um controlo de conteúdo é reconhecido pelo sistema como um campo de formulário, com um nome, um tipo e um valor. Um traço de sublinhado é texto. A diferença, mais uma vez, é entre pintar o edifício e desenhá-lo na planta: no primeiro caso, quem não vê tem um documento; no segundo, tem um formulário.

Isto corresponde, em espírito, ao critério **3.3.2 Etiquetas ou Instruções** — cada campo que pede dados ao utilizador tem de dizer o que pede.

---

### W8. Tipo de Letra, Contraste e Espaçamento

**O que se pretende**

Um documento **legível**. Não é uma questão de gosto: é a diferença entre conseguir ler e desistir.

Depende disto muita gente — mais gente do que qualquer outro procedimento desta secção. Pessoas com baixa visão, pessoas com dislexia, pessoas com daltonismo, leitores mais velhos, e qualquer pessoa a ler num ecrã pequeno, com pouca luz ou com pressa.

**Passos no Word**

Faça estas escolhas **nos estilos**, não no texto selecionado:

1. **Base → grupo Estilos →** botão direito sobre **Normal** → **Modificar…** → defina tipo de letra, tamanho, espaçamento entre linhas e espaçamento antes/depois do parágrafo.
2. Repita para os estilos de cabeçalho, alterando apenas o que for necessário.
3. Para o espaçamento entre parágrafos: na mesma caixa, botão **Formatar → Parágrafo → Espaçamento (Antes/Depois)**. **Nunca** use linhas em branco para criar espaço.
4. Alinhamento: **Formatar → Parágrafo → Alinhamento → À Esquerda**.

**Regras**

*Tipo e tamanho de letra:*

- Tipos de letra simples, sem serifas decorativas nem carateres ambíguos. Evite letras condensadas, manuscritas e decorativas.
- **Corpo de texto: 12 pontos como mínimo prático**, 14 se o documento se destinar a leitura em papel por público diverso.
- Não use **maiúsculas em blocos de texto**: eliminam o perfil das palavras e tornam a leitura mais lenta. Use-as no máximo em títulos curtos.
- Use **itálico com parcimónia** — para uma expressão, não para um parágrafo.
- Não sublinhe texto que não seja ligação: o sublinhado significa "ligação".

*Espaçamento:*

- Espaçamento entre linhas de **1,15 a 1,5**.
- Espaço **antes e depois dos parágrafos** definido no estilo.
- **Alinhamento à esquerda, não justificado.** O texto justificado abre "rios" brancos irregulares entre as palavras, que dificultam a leitura a quem tem dislexia e a quem amplia muito.
- Sem parágrafos vazios, sem espaços a fazer de avanço, sem `Enter` repetido para mudar de página — para isso existe a quebra de página (`Ctrl+Enter`).

*Cor e contraste:*

- Contraste mínimo de **4,5:1** entre o texto e o fundo; **3:1** para texto grande (a partir de 18 pontos, ou 14 pontos a negrito). É o critério **1.4.3 Contraste (Mínimo)**.
- **A cor nunca pode ser a única forma de transmitir informação.** Numa tabela de prazos, "as linhas a vermelho estão em atraso" exclui quem não distingue o vermelho e quem imprime a preto e branco. Acrescente uma palavra ou um símbolo: uma coluna "Estado" com "Em atraso".
- Cuidado com os estilos predefinidos de cor cinzenta clara (por exemplo, o estilo "Subtítulo") e com marcas de água atrás do texto: são casos frequentes de contraste insuficiente.

O Word não tem um verificador de contraste que permita testar uma cor específica. Para isso é preciso uma ferramenta externa de análise de contraste de cor, à qual se dão os dois valores de cor e que devolve o rácio.

**Antes e depois**

*Antes:*

> Texto a 10 pontos, tipo de letra condensado, justificado, espaçamento simples, cinzento-claro sobre branco, com uma linha em branco entre cada parágrafo e três linhas em branco antes de cada título.

Ao ampliar para 200%, o texto justificado abre buracos enormes entre as palavras; as linhas em branco transformam-se em espaços desproporcionados; o cinzento sobre branco fica abaixo do contraste mínimo. E o leitor de ecrã anuncia "em branco" dezenas de vezes ao longo do documento.

*Depois:*

> Texto a 12 pontos, tipo de letra sem serifas de traço uniforme, alinhado à esquerda, espaçamento 1,15, preto sobre branco, com 12 pontos de espaço depois de cada parágrafo e 18 pontos antes de cada cabeçalho, definidos nos estilos.

**O que funciona melhor no segundo exemplo:** o espaçamento passou a ser uma propriedade dos estilos, o que significa que se ajusta proporcionalmente quando o texto é redimensionado e não gera ruído para quem ouve. O alinhamento à esquerda mantém o espaço entre palavras constante, o que ajuda os olhos a seguir a linha. E o contraste passa a cumprir o mínimo legal.

**Porque funciona**

Todas estas escolhas partilham um princípio: **o documento tem de resistir a ser alterado pelo leitor**. Uma pessoa com baixa visão vai aumentar a letra. Uma pessoa com dislexia pode mudar o tipo de letra. Alguém vai imprimir a preto e branco. Um documento construído com estilos, sem linhas em branco e sem informação dependente da cor sobrevive a tudo isto. Um documento pintado à mão desfaz-se ao primeiro ajuste.

---

## Verificação

### O Verificador de Acessibilidade do Word

O Word tem um verificador de acessibilidade integrado. É uma boa ferramenta e deve ser usada sempre — desde que se perceba o que ela é.

**Como usar**

1. **Rever → Verificar Acessibilidade**. Em alternativa: **Ficheiro → Informações → Verificar Problemas → Verificar Acessibilidade**.
2. Abre-se um painel à direita com os resultados agrupados, tipicamente em três categorias:
   - **Erros** — conteúdo inacessível para muitas pessoas (por exemplo, imagem sem texto alternativo);
   - **Avisos** — conteúdo difícil de compreender para muitas pessoas (por exemplo, texto de ligação pouco claro, células unidas numa tabela);
   - **Sugestões** — conteúdo que pode ser melhorado (por exemplo, ordem de cabeçalhos).
3. Clique num item para o localizar no documento. Em baixo, o painel mostra **Porque corrigir** e **Como corrigir**, com os passos.
4. Marque **Manter o verificador de acessibilidade em execução enquanto trabalho** para passar a ter um indicador permanente na barra de estado.

**Conselho de método**

Corra o verificador **cedo e várias vezes**, não apenas antes de enviar o documento. Corrigir vinte imagens sem texto alternativo no fim é uma tarefa penosa; escrever a descrição no momento em que se insere cada imagem custa dez segundos.

O Word tem também a funcionalidade **Ler em Voz Alta** (**Rever → Ler em Voz Alta**, `Ctrl+Alt+Espaço`). É útil para ouvir o documento e detetar problemas grosseiros de ordem de leitura, mas **não é um leitor de ecrã**: não anuncia cabeçalhos, não anuncia listas, não anuncia tabelas. Não a use como substituto de um teste real.

### O Que o Verificador Não Deteta

Esta é a parte mais importante desta subsecção.

> **Uma verificação limpa não significa documento acessível.** Significa que não há erros daquele tipo que uma máquina consegue detetar. O verificador conta caixas preenchidas; não avalia o que está dentro delas.

Eis, em concreto, o que passa despercebido.

**1. A qualidade do texto alternativo.** O verificador confirma que o campo não está vazio. Não confirma que serve para alguma coisa. Passam sem qualquer aviso:

- `imagem`, `foto`, `gráfico`, `logo`
- `Imagem1.png`
- `Ver gráfico acima`
- uma descrição correta do aspeto da imagem que não transmite a informação que a imagem traz ao documento.

**2. A adequação dos cabeçalhos ao conteúdo.** O verificador pode assinalar saltos de nível, mas não sabe o que é um cabeçalho. Passam sem aviso:

- um parágrafo normal a que foi aplicado o estilo "Título 2" só para ficar maior e a negrito;
- um cabeçalho verdadeiro deixado com formatação direta — para o verificador, é apenas texto;
- um cabeçalho que não descreve a secção que abre: "Considerações", "Ponto 4", "Outros".

**3. O sentido do texto das ligações.** O verificador assinala alguns casos evidentes, mas passam sem aviso:

- doze ligações com o texto "Mais informação", cada uma para um destino diferente;
- uma ligação cujo texto descreve o destino errado, porque o endereço foi atualizado e o texto não;
- uma ligação para um ficheiro de 40 MB sem qualquer aviso disso.

**4. O idioma errado.** Um documento inteiramente em português, marcado do princípio ao fim como inglês, passa na verificação sem uma única observação.

**5. Tabelas marcadas de forma errada.** Uma tabela de disposição gráfica com uma linha de cabeçalho marcada passa. Uma tabela de dados com a linha de cabeçalho marcada na linha errada passa.

**6. Tudo o que seja legibilidade e compreensão.** Texto dentro de imagens, siglas nunca expandidas, frases de sessenta palavras, jargão administrativo impenetrável. Um documento pode ser tecnicamente impecável e continuar a ser ilegível.

**Um protocolo manual, em quatro minutos**

Depois de o verificador ficar limpo, faça estes quatro testes:

1. **Abra o Painel de Navegação e leia só os cabeçalhos.** Fazem sentido sozinhos? Contam a história do documento? Se sim, a planta está boa.
2. **Leia só os textos alternativos, um a seguir ao outro.** Cada um diz o que a imagem traz ao documento?
3. **Leia só os textos das ligações, fora de contexto.** Sabe para onde vai cada uma?
4. **Ponha o documento a 300% e estreite a janela.** O texto reorganiza-se, ou obriga a arrastar a barra horizontal para ler cada linha?

E, quando for possível, faça o teste que vale por todos: **abra o documento com um leitor de ecrã** — o NVDA é gratuito e está disponível em português — e percorra-o só com o teclado. Cinco minutos a ouvir o documento ensinam mais do que uma hora de verificações automáticas.

---

## Recomendações para Conteúdo Acessível

Os procedimentos W1 a W8 tratam da mecânica. Estas recomendações tratam das decisões que se tomam antes e à volta dela.

**Comece por um modelo.** Um modelo (`.dotx`) com os estilos já definidos — tipo de letra, tamanhos, espaçamentos, hierarquia de cabeçalhos — resolve W1 e W8 de uma vez para todos os documentos da organização, e resolve-os para quem não fez esta formação. É o investimento com melhor retorno em acessibilidade documental.

**Escreva os cabeçalhos a pensar em quem só vai ler os cabeçalhos.** Muita gente lê assim: pelo índice, pelo Painel de Navegação, saltando. Um cabeçalho como "Prazos de candidatura" faz esse trabalho; "Nota" não faz.

**Não ponha informação essencial em cabeçalhos e rodapés de página.** O conteúdo dos cabeçalhos e rodapés é frequentemente ignorado pela tecnologia de apoio na leitura contínua, e é tratado como elemento decorativo quando o documento é convertido. Números de página, sim. Um prazo de entrega ou um aviso legal, não — esses vão no corpo do documento.

**Escreva por extenso na primeira ocorrência.** "Agência para a Reforma Tecnológica do Estado (ARTE)". Depois disso, use a sigla. Quem lê com síntese de voz pode ouvir a sigla soletrada ou pronunciada como palavra, e nem sempre da forma que espera.

**Evite referências espaciais.** "Na tabela acima", "conforme a caixa à direita", "ver em baixo" pressupõem uma disposição visual que pode não existir para quem lê de outra forma, e que muda quando o texto é reformatado. Prefira referências nomeadas: "na Tabela 2", "na secção Prazos".

**Um parágrafo, uma ideia.** Parágrafos curtos, frases diretas, voz ativa. Isto não é estilo: é acessibilidade cognitiva, e beneficia toda a gente.

**Não distribua imagens de texto.** Uma página digitalizada colada num documento Word é uma fotografia: não é pesquisável, não é ampliável sem perda, não é lida por ninguém. Se recebeu o conteúdo assim, transcreva-o.

**Guarde e distribua o `.docx` sempre que possível.** O documento Word é reformatável pelo leitor, ao contrário do PDF. A escolha entre distribuir um e outro é tratada na secção "Escolher o Formato e Organizar o Trabalho".

### Erros Comuns

**1. Formatar cabeçalhos à mão em vez de aplicar estilos.**
É o erro mais frequente e o mais grave: elimina toda a estrutura do documento de uma só vez. *Em vez disso:* aplique estilos de cabeçalho e altere o aspeto do estilo, não do texto (W1).

**2. Usar "Título 1" e "Título 2" pela ordem em que ficam mais bonitos.**
A hierarquia dos cabeçalhos é uma árvore, não uma paleta de tamanhos. *Em vez disso:* escolha o nível pela posição na estrutura e ajuste o aspeto no estilo (W1).

**3. Criar espaço com linhas em branco.**
Geram ruído para quem ouve e espaços descontrolados quando o texto é reformatado. *Em vez disso:* espaçamento antes/depois definido no estilo (W8).

**4. Usar tabelas para dispor elementos na página.**
Cria relações de dados que não existem. *Em vez disso:* use colunas, avanços ou estilos de parágrafo (W2, W3).

**5. Tabelas com células unidas e cabeçalhos em duas linhas.**
O Word não consegue descrever essa complexidade. *Em vez disso:* divida em tabelas simples, cada uma com o seu cabeçalho (W3).

**6. Texto alternativo que é o nome do ficheiro.**
Passa na verificação automática e não serve para nada. *Em vez disso:* descreva o que a imagem traz ao documento (W4).

**7. Imagens flutuantes.**
Posição imprevisível na ordem de leitura. *Em vez disso:* moldagem "Alinhado com o Texto" (W4).

**8. "Clique aqui".**
Inútil na lista de ligações e pressupõe um rato. *Em vez disso:* texto de ligação que descreve o destino (W5).

**9. Documento com o idioma do modelo, não o do conteúdo.**
Torna a síntese de voz incompreensível e não é assinalado pelo verificador. *Em vez disso:* defina o idioma no documento e nas passagens estrangeiras (W6).

**10. Propriedade "Título" vazia ou herdada de outro documento.**
Propaga-se a toda a cadeia, incluindo aos metadados do PDF. *Em vez disso:* preencha o título ao criar o documento (W6).

**11. Formulário desenhado com sublinhados.**
Não é preenchível com teclado e não é anunciado como campo. *Em vez disso:* controlos de conteúdo com Título (W7).

**12. Informação transmitida apenas pela cor.**
Exclui quem não distingue as cores e quem imprime a preto e branco. *Em vez disso:* acrescente texto ou símbolo (W8).

**13. Correr o verificador só no fim, e tratar "zero erros" como aprovação.**
O verificador não avalia qualidade. *Em vez disso:* corra-o desde o início e faça sempre o protocolo manual de quatro pontos.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- **O Word é onde a planta se desenha.** É o momento mais barato de todo o ciclo para criar estrutura, e o momento em que os erros ficam mais caros se não forem corrigidos.
- **Os estilos não são decoração** (W1). São o mecanismo que transforma texto formatado em documento estruturado. Se houver uma única coisa a levar desta secção, é esta.
- **Listas e colunas verdadeiras** transportam relações que as listas escritas à mão e as caixas de texto não transportam (W2).
- **Tabelas são para dados**, com uma linha de cabeçalho marcada, sem células unidas, sem linhas vazias (W3).
- **O texto alternativo descreve a função da imagem naquele documento**, não a imagem; os objetos ficam alinhados com o texto para terem posição fiável na ordem de leitura (W4).
- **O texto da ligação tem de funcionar sozinho**, fora da frase que o rodeia (W5).
- **O título e o idioma identificam o documento** e determinam como ele é anunciado e pronunciado; ambos se propagam a tudo o que for gerado a partir dele (W6).
- **Um formulário em Word precisa de controlos de conteúdo com Título**, não de linhas para preencher à mão — e, muitas vezes, precisa sobretudo de não ser um formulário em Word (W7).
- **A legibilidade é uma decisão de estilos**, não de formatação pontual: tamanho, espaçamento, alinhamento à esquerda, contraste suficiente, e nunca a cor sozinha a transmitir informação (W8).
- **O verificador é um ponto de partida, não um certificado.** Ele conta caixas preenchidas; a qualidade do texto alternativo, a adequação dos cabeçalhos e o sentido das ligações continuam a depender de uma pessoa.

### Exercícios Práticos

**Exercício 1 — Diagnóstico da planta**

Abra um documento Word real da sua organização, com pelo menos cinco páginas. Abra o **Painel de Navegação** (**Ver → Painel de Navegação**) e responda:

a) O painel mostra alguma coisa?
b) Se mostra, os cabeçalhos que aparecem são todos os cabeçalhos do documento?
c) Lendo apenas os cabeçalhos, por ordem, percebe-se do que trata o documento?

Escreva três linhas com o diagnóstico.

**Exercício 2 — De pintura a planta**

Pegue nesse mesmo documento (numa cópia) e converta toda a formatação direta de títulos em estilos de cabeçalho, respeitando a hierarquia. Depois altere o tipo de letra de todos os cabeçalhos de nível 2 **modificando o estilo**, sem selecionar um único parágrafo. Cronometre.

**Exercício 3 — Reparar uma tabela**

Construa uma tabela com estes problemas: sem linha de cabeçalho marcada, com a primeira célula vazia, com duas células unidas no topo, com uma linha vazia a meio para "separar" blocos e com o estado de cada linha indicado apenas pela cor de fundo (verde/vermelho).

Corrija-a. Depois explique, em três frases, o que cada correção muda para quem usa leitor de ecrã.

**Exercício 4 — Texto alternativo**

Escreva o texto alternativo para estas três imagens, num relatório de atividades:

1. O logótipo da organização, no cabeçalho da capa.
2. Uma linha decorativa horizontal que separa duas secções.
3. Um gráfico de barras com o número de atendimentos por trimestre: 1.º — 1 200; 2.º — 1 450; 3.º — 980; 4.º — 1 610.

<details>
<summary>Ver resolução comentada</summary>

1. **Logótipo:** `Agência para a Reforma Tecnológica do Estado`. Descreve-se o que o logótipo *identifica*, não o seu desenho. Se o nome da organização já estiver escrito por extenso imediatamente ao lado, o logótipo pode ser marcado como decorativo — repeti-lo só acrescenta ruído.

2. **Linha decorativa:** nenhum. Marcar como **decorativo**. Não transmite informação; descrevê-la seria obrigar quem ouve a processar "linha horizontal cinzenta" sem qualquer ganho.

3. **Gráfico:** `Atendimentos por trimestre em 2025. Subida no segundo trimestre, quebra acentuada no terceiro e máximo anual no quarto.` E, imediatamente a seguir ao gráfico, uma tabela simples com os quatro valores. O texto alternativo dá a *mensagem* — a forma da curva —, que é o que quem vê apreende num relance; a tabela dá os *dados*, que não cabem numa descrição curta e que nenhuma pessoa consegue reter de ouvido.

**Erro típico a evitar:** escrever no ponto 3 algo como "Gráfico de barras com quatro barras azuis de alturas diferentes". É uma descrição fiel do aspeto e completamente inútil.
</details>

**Exercício 5 — Ligações fora de contexto**

Reescreva os textos de ligação deste parágrafo:

> Para saber mais sobre o programa, consulte a informação disponível [aqui]. O regulamento pode ser consultado [neste link]. Para submeter a candidatura aceda a [https://www.exemplo.gov.pt/candidaturas/2025/formulario/submissao?ref=prog2025-af].

<details>
<summary>Ver resolução comentada</summary>

> Consulte a [apresentação do programa] e o [regulamento do programa (PDF, 1,2 MB)]. As candidaturas submetem-se no [formulário de candidatura em linha].

Cada texto de ligação descreve o destino e funciona isolado numa lista. O formato e o tamanho do ficheiro estão indicados na ligação para o PDF, para evitar um descarregamento inesperado. E o URL longo desapareceu do texto visível — se este documento se destinasse a ser impresso, o endereço teria de ser acrescentado por extenso a seguir ao texto da ligação, ou numa nota de rodapé, de preferência numa versão curta.
</details>

**Exercício 6 — O que o verificador não vê**

Prepare um documento com pelo menos: dois cabeçalhos, uma tabela, duas imagens e três ligações. Trabalhe-o até o **Verificador de Acessibilidade** não devolver nenhum erro nem aviso.

Depois, introduza deliberadamente **três problemas de acessibilidade que o verificador continue a não detetar**. Identifique-os e explique, para cada um, quem é prejudicado e como.

<details>
<summary>Ver pistas</summary>

Três hipóteses, entre muitas possíveis: pôr `imagem` como texto alternativo das duas imagens; aplicar o estilo "Título 2" a um parágrafo normal só para o destacar; dar o texto "Mais informação" às três ligações, apontando para destinos diferentes. Nenhuma destas alterações produz uma única observação do verificador — e todas as três tornam o documento significativamente pior.
</details>

