---
title: Do Word e do PowerPoint para PDF
layout: default
nav_order: 4
---
# Do Word e do PowerPoint para PDF

## Introdução

Esta secção trata de um único gesto: transformar um ficheiro Word ou PowerPoint num ficheiro PDF.

É um gesto que a maior parte das pessoas faz sem pensar, várias vezes por semana, em poucos segundos. E é, provavelmente, o momento em que se destrói mais acessibilidade por unidade de tempo em toda a administração pública portuguesa.

A razão é simples de enunciar e difícil de aceitar:

> **Um documento de origem acessível não gera automaticamente um PDF acessível.** O resultado depende do método de exportação utilizado. O mesmo ficheiro Word, com os mesmos estilos, o mesmo texto alternativo e o mesmo idioma, pode dar origem a um PDF perfeitamente estruturado ou a um PDF completamente vazio de estrutura — consoante o comando que se escolheu no menu.

Na analogia do curso, isto vê-se bem. O documento é o edifício e as etiquetas são a planta. Ao trabalhar no Word ou no PowerPoint, seguindo os procedimentos `W1`–`W8` e `PP1`–`PP9`, construiu-se o edifício e desenhou-se a planta ao mesmo tempo. A exportação é o momento da entrega:

- **Exportar bem** é entregar o edifício **com a planta**. Quem vê, vê o edifício. Quem não vê, tem a planta.
- **Imprimir para PDF** é fotografar o edifício de fora e deitar a planta no lixo. Fica uma imagem bonita, e mais ninguém consegue lá entrar.

O trabalho todo das duas secções anteriores está, neste momento, dependente de uma caixa de verificação.

### O Problema Que Esta Secção Resolve

Um cenário real, e comum.

> Uma técnica prepara um relatório de 60 páginas em Word. Aplica estilos de cabeçalho em toda a estrutura (`W1`), marca as tabelas com linha de cabeçalho (`W3`), escreve texto alternativo em todas as imagens (`W4`), define o idioma e o título do documento (`W6`). Executa o verificador de acessibilidade do Word e o painel fica limpo. O documento está pronto.
>
> Para publicar, faz o que sempre fez: **Ficheiro → Imprimir → impressora "Microsoft Print to PDF" → Imprimir**. Sai um PDF com bom aspeto, com as mesmas 60 páginas, o mesmo grafismo, os mesmos cabeçalhos a azul.
>
> Uma semana depois, chega uma reclamação de um utilizador de leitor de ecrã: o documento não tem cabeçalhos, não tem tabelas, não tem descrições de imagens e não se consegue navegar.

**O que correu mal neste exemplo:** absolutamente nada no documento de origem — e tudo no último clique. O comando "Imprimir" existe para produzir páginas para papel. Ele desenha no PDF aquilo que desenharia numa folha: manchas de texto e de imagem em posições da página. Não transporta estilos, não transporta relações, não transporta texto alternativo, porque nada disso existe em papel. As oito horas de trabalho de estruturação foram deitadas fora num segundo, sem qualquer aviso, sem qualquer mensagem de erro, e sem que o resultado pareça diferente aos olhos de quem o produziu.

**O que teria funcionado:** o mesmo documento, exportado com **Ficheiro → Guardar Como → PDF**, com a opção de etiquetas de estrutura ativa, produz um PDF etiquetado em que os cabeçalhos são cabeçalhos, as tabelas são tabelas e as imagens têm descrição. Zero trabalho adicional. Apenas um comando diferente.

É por isto que esta secção existe. Ela é curta em procedimentos e enorme em consequências. Se levar deste curso uma única frase, que seja esta: **nunca imprimir para PDF um documento que se pretende acessível**.

---

## Antes de Começar

Esta secção assume que o documento de origem já está pronto e acessível. Se não estiver, não vale a pena avançar: **a exportação preserva ou destrói estrutura, mas nunca a cria**. Um documento Word sem estilos de cabeçalho não passa a ter cabeçalhos no PDF por ter sido bem exportado; passa a ter, no PDF, a mesma ausência de cabeçalhos que tinha na origem — fielmente transportada.

A preparação está nas secções "Documentos Word" (`W1`–`W8`) e "Apresentações PowerPoint" (`PP1`–`PP9`). O procedimento `C1` recapitula apenas o que é preciso confirmar **imediatamente antes** de exportar, incluindo alguns pontos que só se tornam problema no momento da conversão.

### Escolher o Método de Exportação

Este é o ponto de decisão da secção. Tudo o resto são detalhes.

O Word e o PowerPoint oferecem vários caminhos para chegar a um ficheiro PDF. Parecem equivalentes. Não são. Uns entregam a planta, outros deitam-na fora.

| Método | Caminho | Preserva a estrutura? |
|---|---|---|
| **Guardar Como / Guardar uma Cópia** | Ficheiro → Guardar Como → tipo **PDF** → botão **Opções** | **Sim**, se a opção de etiquetas estiver ativa |
| **Exportar** | Ficheiro → Exportar → **Criar Documento PDF/XPS** → botão **Opções** | **Sim**, se a opção de etiquetas estiver ativa (é o mesmo motor do anterior) |
| **Separador Acrobat no friso** | Separador **Acrobat** → **Criar PDF** | **Sim**, se as preferências do PDFMaker estiverem corretas |
| **Imprimir para PDF** | Ficheiro → Imprimir → impressora "Microsoft Print to PDF" ou "Adobe PDF" | **Não.** Destrói toda a estrutura |
| **Imprimir → Guardar como PDF** (menu da caixa de impressão) | Ficheiro → Imprimir → menu **PDF** → Guardar como PDF | **Não.** Destrói toda a estrutura |
| **Digitalizar o documento impresso** | Fora da aplicação | **Não.** Produz uma imagem, sem sequer texto |

Os três primeiros métodos são aceitáveis. Os três últimos não são.

**Como distinguir sempre, sem decorar a tabela:** a pergunta a fazer é *"estou a dizer à aplicação que quero um ficheiro, ou estou a dizer-lhe que quero páginas impressas?"*. Guardar e exportar são operações sobre ficheiros: a aplicação sabe que o destino é outro programa, e por isso envia tudo o que sabe sobre o conteúdo. Imprimir é uma operação sobre papel: a aplicação prepara tinta em posições da folha, e mais nada. Uma impressora não tem interesse nenhum em saber que aquela linha é um cabeçalho de nível 2.

> **Analogia.** Guardar como PDF é enviar o processo completo por correio, com a planta lá dentro. Imprimir para PDF é fotocopiar a fachada do edifício. As duas coisas cabem num envelope do mesmo tamanho e ninguém percebe a diferença até tentar usar o que está lá dentro.

**Uma nota sobre o separador Acrobat.** Quando o Adobe Acrobat está instalado, pode aparecer um separador **Acrobat** no friso do Word e do PowerPoint. O comando **Criar PDF** desse separador usa um componente chamado PDFMaker, que faz o mesmo que o Guardar Como e ainda mais: pode converter os campos de formulário do Word em campos de formulário do PDF, e dá mais controlo sobre marcadores e ligações. É uma boa opção — desde que se confirme, uma vez, que as preferências têm a acessibilidade ativa (ver `C2`). Se as preferências estiverem mal configuradas, o PDFMaker também produz PDF sem etiquetas.

**Um aviso sobre o Word para Mac.** Na versão para macOS, a caixa de diálogo de gravação apresenta duas opções em vez de uma caixa de verificação: uma orientada para a distribuição eletrónica e acessibilidade, e outra orientada para a impressão. **A opção orientada para impressão produz um PDF sem etiquetas.** É a escolha por defeito em alguns cenários e é uma armadilha frequente.

---

## Procedimentos

Cada procedimento segue a mesma estrutura das secções anteriores: o que se pretende, os passos na aplicação, um exemplo, e a explicação do que muda para quem usa tecnologia de apoio.

Os caminhos de menu referem-se ao Microsoft 365 e ao Adobe Acrobat, em português europeu. 

---

### C1. Preparar o Documento de Origem

**O que se pretende**

Garantir que aquilo que vai ser transportado para o PDF vale a pena ser transportado — e resolver, antes da exportação, um conjunto pequeno de problemas que **só se manifestam depois dela**.

**Passos**

*Parte A — confirmar o que já foi feito (nada de novo aqui):*

1. Execute o verificador de acessibilidade da aplicação uma última vez e resolva tudo o que aparecer. No Word: **Rever → Verificar Acessibilidade**. No PowerPoint: o mesmo caminho.
2. Confirme que o documento tem **título** nas propriedades do ficheiro e **idioma** correto (`W6`). Estes dois valores viajam para o PDF e evitam trabalho de correção mais tarde.
3. Confirme que a estrutura está feita com estilos e não com formatação manual (`W1`), que as listas são listas verdadeiras (`W2`), que as tabelas têm linha de cabeçalho marcada (`W3`) e que as imagens têm texto alternativo ou estão marcadas como decorativas (`W4`, `PP4`).
4. No PowerPoint, confirme que todos os diapositivos têm título (`PP2`) e que a ordem de leitura está verificada diapositivo a diapositivo (`PP3`).

*Parte B — problemas específicos da exportação:*

5. **Retire o conteúdo essencial das caixas de texto flutuantes.** No Word, uma caixa de texto posicionada livremente sobre a página tende a ficar fora do fluxo principal de etiquetas do PDF, ou a aparecer numa posição inesperada da ordem de leitura. Passe esse conteúdo para o corpo do documento.
6. **Retire o conteúdo essencial dos cabeçalhos e rodapés.** O que está no cabeçalho e no rodapé de uma página Word é normalmente exportado como **artefacto** — isto é, como decoração que a tecnologia de apoio ignora. Está correto que assim seja para números de página e logótipos repetidos; está errado se lá estiver o único sítio onde consta o nome do serviço ou a data de validade do documento.
7. **Resolva as marcas de revisão e os comentários.** Aceite ou rejeite as alterações registadas e elimine os comentários. Um documento exportado com marcas de revisão visíveis leva-as para dentro do PDF, muitas vezes de forma ilegível.
8. **Elimine páginas e diapositivos vazios**, linhas de tabela vazias usadas para dar espaço, e sequências de parágrafos vazios usadas para empurrar conteúdo. Todos eles geram etiquetas vazias no PDF, que a tecnologia de apoio anuncia sem nada dizer.
9. **No PowerPoint, verifique o que está fora da área do diapositivo.** Objetos arrastados para fora da margem, que não aparecem na projeção, podem continuar a existir na ordem de leitura e a ser lidos. Use o Painel de Seleção para os encontrar e elimine-os.
10. Guarde o ficheiro de origem. **Ele não é um rascunho descartável: é a fonte da verdade.** Esta ideia é desenvolvida na secção "Escolher o Formato e Organizar o Trabalho".

**Exemplo**

> Um serviço prepara um folheto informativo em Word. O título "Apoio à Habitação — Candidaturas 2026" está numa caixa de texto sobre uma faixa de cor, no topo da primeira página, porque assim é que ficava bem alinhado com o grafismo. O resto do documento está impecavelmente estruturado.

**O que corre mal neste exemplo:** ao exportar, aquele título tem grande probabilidade de acabar no fim da estrutura de etiquetas, depois de todo o texto da página, ou de ser lido como um parágrafo solto sem nível de cabeçalho. Quem lê com um leitor de ecrã percorre o documento inteiro e só no fim descobre do que trata. Quem navega por cabeçalhos não encontra o principal. Nada disto aparece no verificador do Word, que se dá por satisfeito com uma caixa de texto que tem texto lá dentro.

**A correção:** colocar o título no corpo do documento, com o estilo **Título 1**, e obter o efeito visual com sombreado de parágrafo em vez de caixa de texto. O aspeto final é o mesmo. A planta passa a existir.

**O que muda para quem usa tecnologia de apoio:** o documento passa a ter um ponto de entrada. O primeiro cabeçalho é o assunto, e não uma frase a meio do segundo parágrafo.

---

### C2. Exportar a Partir do Word

**O que se pretende**

Produzir um PDF **etiquetado**, com marcadores de navegação e com as propriedades do documento preservadas.

**Passos — via Guardar Como**

1. **Ficheiro → Guardar Como** (ou **Guardar uma Cópia**, em ficheiros guardados na nuvem).
2. Escolha a pasta de destino e, na lista de tipos de ficheiro, escolha **PDF (\*.pdf)**.
3. **Antes de gravar**, clique no botão **Opções**. 
4. Na caixa **Opções**, confirme:
   - **Etiquetas de estrutura do documento para acessibilidade** — **ativa**. Esta é a caixa de verificação de que depende tudo.
   - **Criar marcadores utilizando: Títulos** — **ativa**. Gera o painel de marcadores do PDF a partir dos estilos de cabeçalho.
   - **Propriedades do documento** — **ativa**. Transporta o título e restantes propriedades.
   - **Compatível com ISO 19005-1 (PDF/A)** — **desativada**, salvo se houver requisito de arquivo que a obrigue. O PDF/A serve a preservação a longo prazo, não a acessibilidade, e ativá-lo pode alterar o comportamento das restantes opções.
5. Confirme com **OK** e depois **Guardar**.
6. A opção de qualidade — **Padrão** ou **Tamanho mínimo** — afeta a compressão das imagens, não as etiquetas. Prefira **Padrão** para documentos com imagens que precisem de ser legíveis quando ampliadas.

**Passos — via separador Acrobat**

1. Separador **Acrobat** → **Preferências** (ou **Definições**).
2. Confirme que está ativa a opção de **ativar acessibilidade e refluir com PDF etiquetado**. Confirme também as opções de conversão de marcadores e de ligações.
3. Feche as preferências e clique em **Criar PDF**.
4. Indique o nome e a pasta e confirme.

**Exemplo**

> Dois PDF do mesmo relatório, gerados no mesmo computador, com cinco minutos de intervalo. O primeiro por **Imprimir → Microsoft Print to PDF**. O segundo por **Guardar Como → PDF**, com as opções acima. Abertos lado a lado no Acrobat, são indistinguíveis: mesmo aspeto, mesmo número de páginas, tamanho semelhante.
>
> Em **Ficheiro → Propriedades → Descrição**, o primeiro diz **PDF Etiquetado: Não**. O segundo diz **PDF Etiquetado: Sim**. No primeiro, o painel de marcadores está vazio. No segundo, tem a árvore completa dos cabeçalhos.

**O que este exemplo demonstra:** a diferença entre um documento acessível e um documento inacessível pode ser invisível a olho nu, custar zero segundos de trabalho adicional e depender inteiramente de qual dos dois comandos do menu **Ficheiro** se escolheu. É por isso que este erro é tão persistente: não dá sinal nenhum a quem o comete.

**O que muda para quem usa tecnologia de apoio:** no PDF etiquetado, o leitor de ecrã anuncia os cabeçalhos e permite navegar por eles; anuncia as tabelas e associa cada célula ao seu cabeçalho; lê o texto alternativo das imagens; sabe em que idioma está o texto. No PDF impresso, anuncia uma sucessão de linhas soltas, se conseguir sequer encontrar texto.

---

### C3. Exportar a Partir do PowerPoint

**O que se pretende**

O mesmo que em `C2`, com três decisões adicionais que só existem neste formato.

**Passos**

1. **Ficheiro → Guardar Como** → tipo **PDF (\*.pdf)** → botão **Opções**.
2. Na caixa **Opções**, para além das opções já descritas em `C2`, confirme:
   - **Publicar o quê: Diapositivos.** Esta é a decisão mais importante desta caixa. Ver a explicação em baixo.
   - **Incluir diapositivos ocultos** — ativa apenas se o conteúdo desses diapositivos for para ser lido. Um diapositivo oculto que é exportado passa a fazer parte do documento para quem o lê com tecnologia de apoio, mesmo que nunca tenha sido projetado.
   - **Diapositivos com moldura** — indiferente para a acessibilidade.
   - **Incluir comentários** — normalmente desativada.
3. Confirme com **OK** e depois **Guardar**.

**A decisão do "Publicar o quê"**

A lista oferece várias opções. Só uma serve.

| Opção | O que produz | Serve? |
|---|---|---|
| **Diapositivos** | Uma página por diapositivo, com a estrutura do diapositivo | **Sim** |
| **Folhetos** (2, 3, 6, 9 por página) | Miniaturas dos diapositivos dispostas numa grelha | **Não.** Os diapositivos passam a imagens numa página; a estrutura desaparece |
| **Páginas de notas** | O diapositivo em cima e as notas em baixo | **Não**, como formato de distribuição principal |
| **Vista de destaques** | Apenas o texto dos marcadores de posição | **Não** |

**O que corre mal com os folhetos:** é uma escolha frequente por parecer económica — nove diapositivos numa folha poupa papel. Mas o formato de folheto trata cada diapositivo como uma imagem colocada numa página, e o resultado é um PDF sem cabeçalhos, sem títulos de diapositivo e, em muitos casos, sem texto selecionável nas miniaturas. Poupa-se papel e perde-se o documento.

**Sobre as notas do orador.** As notas escritas ao abrigo de `PP8` **não são exportadas** quando se publica "Diapositivos". Isto é uma decisão a tomar conscientemente:

- Se as notas contêm apenas apoio à oralidade, está bem que fiquem de fora.
- Se as notas contêm a descrição alargada de um gráfico, ou informação que só existe ali, essa informação **desaparece do PDF**. Nesse caso, a solução correta não é publicar em páginas de notas: é trazer a informação para o diapositivo antes de exportar, ou preparar um documento Word separado, acessível, com o conteúdo desenvolvido.

**Exemplo**

> Uma apresentação de 30 diapositivos é distribuída como PDF "6 diapositivos por página", para ficar em 5 páginas em vez de 30. O grafismo é o mesmo, a leitura em ecrã até é mais confortável para quem vê.

**O que corre mal neste exemplo:** para quem usa leitor de ecrã, o documento passou de 30 unidades navegáveis com títulos a 5 páginas com 30 imagens sem descrição. Os títulos de diapositivo, cuidadosamente escritos ao abrigo de `PP2` para servirem de navegação, deixaram de existir enquanto títulos. A economia de páginas custou o documento inteiro.

**A alternativa:** exportar em **Diapositivos** e, se a preocupação for o consumo de papel, tratar isso na impressão — a caixa de impressão do Acrobat permite imprimir várias páginas por folha sem alterar o ficheiro. O documento mantém-se acessível; o papel poupa-se na mesma.

**O que muda para quem usa tecnologia de apoio:** com "Diapositivos", cada diapositivo é uma página com um título, e o painel de marcadores funciona como índice da apresentação. Com "Folhetos", não há nada.

---

### C4. Confirmar Que as Etiquetas Sobreviveram

**O que se pretende**

Uma verificação **rápida e imediata**, feita nos trinta segundos a seguir à exportação, para responder a duas perguntas: *o PDF tem etiquetas?* e *o texto é mesmo texto?*

Isto não é uma auditoria. A verificação aprofundada — verificador de acessibilidade do Acrobat, painel de etiquetas, correção da ordem de leitura — pertence à secção "PDF: Verificação e Correção". O objetivo aqui é apanhar, ainda com o Word ou o PowerPoint abertos, o caso em que a exportação correu mal e basta repeti-la.

> **Analogia.** É o gesto de abrir o envelope antes de o entregar, só para confirmar que a planta lá está. Não é ler a planta toda — é ver se está lá.

**Passos**

1. **Abra o PDF no Adobe Acrobat.**
2. **Ficheiro → Propriedades** (atalho `Ctrl` + `D`), separador **Descrição**. Em baixo, à direita, procure a linha **PDF Etiquetado**.
   - **Sim** → a exportação preservou a estrutura. Continue.
   - **Não** → a exportação falhou. **Não tente corrigir o PDF.** Volte ao ficheiro de origem e repita `C2` ou `C3` com as opções certas.
3. **Ainda nessa caixa**, confirme que o campo **Título** tem o título real do documento e não o nome do ficheiro nem a primeira linha de texto. Se estiver vazio, o valor não veio da origem: reveja `W6` e volte a exportar. A configuração fina do título e dos metadados no Acrobat é tratada em `R6`, na secção seguinte.
4. **Teste a seleção de texto.** Clique no meio de um parágrafo e arraste, ou faça `Ctrl` + `A`.
   - Se o texto fica realçado palavra a palavra → é texto.
   - Se a página inteira fica realçada como um bloco único, ou se nada acontece → **o PDF é uma imagem**. Isto acontece quando o documento foi digitalizado ou quando alguém colou capturas de ecrã em vez de texto. O tratamento deste caso está em `R7`.
5. **Teste o painel de marcadores.** Abra o painel lateral de marcadores. Se exportou com a opção de marcadores ativa e o documento tem cabeçalhos (Word) ou títulos de diapositivo (PowerPoint), deve estar lá a árvore de navegação. Se estiver vazio, a opção não ficou ativa.
6. **Teste o refluxo.** **Ver → Zoom → Refluir** (atalho `Ctrl` + `4`). O documento passa a apresentar-se numa coluna única. 
   - Se o texto reaparece numa ordem que faz sentido → bom sinal.
   - Se aparece baralhado, com legendas no meio de frases ou o rodapé a meio da página → há problemas de ordem de leitura a resolver na secção seguinte (`R3`).

**Exemplo**

> Um técnico exporta uma apresentação, faz a verificação de `C4` e encontra **PDF Etiquetado: Sim**, texto selecionável, marcadores presentes. Passa ao refluxo e vê, no diapositivo 4, o texto de uma caixa lateral a aparecer **antes** do título.

**O que este exemplo mostra:** a exportação funcionou — a planta foi entregue. O que está errado é a planta, e o erro vem da origem: aquele diapositivo tem a ordem de objetos trocada (`PP3`). **A correção certa é no PowerPoint, não no PDF.** Corrigir a ordem no Acrobat resolve um ficheiro; corrigir no PowerPoint resolve o ficheiro e todas as versões futuras. Esta decisão — corrigir o PDF ou voltar à origem — é o primeiro assunto da secção "PDF: Verificação e Correção".

**O que muda para quem usa tecnologia de apoio:** nada, ainda. `C4` não corrige nada. Serve para saber, cedo e barato, se o trabalho seguinte é repetir uma exportação de dez segundos ou reparar um PDF à mão durante uma tarde.

---

## Limites

### O Que Não é Possível Recuperar

A exportação bem feita transporta muito. Não transporta tudo. Vale a pena saber, antes de exportar, o que vai ficar pelo caminho — porque quase sempre há uma decisão a tomar na origem, e não no destino.

**1. O que não existe na origem.** Já foi dito e volta a dizer-se, porque é o mais importante: a exportação não inventa estrutura. Um documento sem cabeçalhos dá um PDF sem cabeçalhos. Uma imagem sem texto alternativo dá uma imagem sem texto alternativo no PDF. A qualidade máxima do PDF é a qualidade do ficheiro de origem.

**2. A semântica interna de gráficos e SmartArt.** Um gráfico do Word ou do PowerPoint chega ao PDF como imagem com texto alternativo. As séries, os eixos e os valores deixam de ser dados e passam a desenho. Daí a insistência de `W4` e `PP4` em ter os valores essenciais também em texto.

**3. As fórmulas matemáticas.** Uma equação escrita no editor de equações chega ao PDF sem a sua estrutura matemática. É lida como uma sequência de símbolos, ou nem isso. Se a matemática for essencial, é preciso acompanhá-la de uma descrição em texto.

**4. Os controlos de formulário do Word.** Os controlos de conteúdo criados ao abrigo de `W7` **não se transformam automaticamente em campos preenchíveis do PDF** quando se usa Guardar Como. O separador Acrobat pode fazê-lo, e o Acrobat pode criar os campos de raiz. Esse trabalho — e a etiquetagem correta dos campos — é o assunto da secção "Formulários em PDF".

**5. As notas do orador.** Como explicado em `C3`, ficam fora do PDF.

**6. O contraste e a legibilidade.** Se o texto tinha contraste insuficiente na origem, tem contraste insuficiente no PDF. Nenhuma opção de exportação corrige cor.

**7. Um PDF impresso não se "desimprime".** Este é o limite mais duro. Não existe comando que devolva as etiquetas a um PDF gerado por impressão. Só há dois caminhos: **voltar à origem e reexportar** — rápido, correto, quase sempre a escolha certa — ou **etiquetar o PDF à mão no Acrobat**, um trabalho que, num documento de 60 páginas com tabelas, se conta em horas ou dias. Quem tiver perdido o ficheiro de origem descobrirá, nessa altura, porque é que o ponto 10 do procedimento `C1` insiste em guardá-lo.

---

## Recomendações para Conteúdo Acessível

**Exportar é o último passo, não um passo a meio.** Faça a exportação quando o documento estiver fechado. Cada revisão posterior obriga a nova exportação — e é aí que alguém, com pressa, imprime para PDF.

**Fixe o método por escrito.** Numa equipa, o método de exportação não pode depender do hábito de cada pessoa. Escreva o caminho de menu e a lista de opções numa página, com uma captura de ecrã, e coloque-a onde os documentos são produzidos. Este é dos poucos problemas de acessibilidade que se resolve com meia página de instruções.

**Guarde sempre o ficheiro de origem, com o mesmo nome do PDF.** `relatorio-anual-2026.docx` ao lado de `relatorio-anual-2026.pdf`, na mesma pasta. Uma correção futura passa a custar minutos.

**Nunca distribua um PDF sem ter feito `C4`.** São trinta segundos. Evita, em muitos casos, tardes inteiras de correção.

**Se a exportação falhar, volte à origem.** A tentação de "arranjar rapidamente no Acrobat" é forte e quase sempre má economia. Reexportar custa dez segundos e produz um resultado melhor do que qualquer correção manual.

**Teste um documento antes de converter cem.** Se vai converter um lote com o mesmo modelo, exporte um, verifique-o a fundo e só depois faça o resto. Os erros de modelo repetem-se em todos os ficheiros.

**Pergunte, antes de exportar, se o PDF é mesmo necessário.** Muitas vezes não é, e o Word ou o próprio conteúdo publicado como página web serviriam melhor. Esta pergunta tem tratamento próprio na secção "Escolher o Formato e Organizar o Trabalho".

### Erros Comuns

**1. Imprimir para PDF.** O erro central desta secção. Produz um PDF sem etiquetas, sem cabeçalhos, sem texto alternativo, sem tabelas — e com aspeto perfeitamente normal. Não dá aviso nenhum.

**2. Desativar, ou nunca ativar, a opção de etiquetas.** A caixa **Etiquetas de estrutura do documento para acessibilidade** costuma vir ativa, mas basta que alguém a tenha desmarcado uma vez para que fique assim. Ela é o interruptor entre entregar a planta e não entregar. Confirme-a de cada vez.

**3. Exportar folhetos em vez de diapositivos.** Poupa páginas e elimina a estrutura toda da apresentação.

**4. Exportar com marcas de revisão e comentários por resolver.** Vão parar ao PDF, muitas vezes de forma ilegível e sempre de forma indesejada.

**5. Deixar conteúdo essencial em caixas de texto flutuantes ou em cabeçalhos e rodapés.** Na origem lê-se bem. No PDF, aparece fora de sítio ou não aparece de todo.

**6. Assumir que "o Word disse que estava bem".** O verificador do Word e o do PowerPoint avaliam **o ficheiro de origem**. Não sabem nada sobre o PDF que se vai produzir a seguir, nem sobre o método que se vai usar. Um painel limpo não é garantia de PDF acessível.

**7. Ativar PDF/A por hábito.** O PDF/A responde a requisitos de arquivo, não de acessibilidade. Ativar sem necessidade acrescenta restrições e pode interferir com as opções que interessam.

**8. Perder o ficheiro de origem.** Transforma uma correção de dez segundos numa correção de dois dias. Acontece com frequência quando o PDF é enviado por mensagem e o original nunca chega a ser arquivado.

**9. Corrigir sempre no PDF em vez de corrigir na origem.** Cada nova versão do documento reintroduz o mesmo erro, e a correção manual tem de ser refeita do princípio.

**10. Digitalizar o documento impresso para obter o PDF.** É o pior de todos os métodos: produz uma imagem, sem texto e sem estrutura. Acontece quando é preciso uma assinatura manuscrita — e há sempre alternativas melhores.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Um documento de origem acessível não gera automaticamente um PDF acessível.** O resultado depende do método de exportação.
2. **Guardar Como, Exportar e o separador Acrobat preservam a estrutura. Imprimir para PDF destrói-a.** Não há exceções e não há aviso.
3. **A opção "Etiquetas de estrutura do documento para acessibilidade" é o interruptor.** Confirme-a antes de gravar, de cada vez.
4. **Ative também os marcadores a partir dos títulos e as propriedades do documento.** Dão navegação e identificação ao PDF sem trabalho adicional.
5. **No PowerPoint, publique "Diapositivos".** Folhetos, páginas de notas e vista de destaques não servem para distribuição acessível.
6. **As notas do orador não vão para o PDF.** Se contêm informação essencial, essa informação tem de estar noutro sítio.
7. **A exportação preserva ou destrói estrutura; nunca a cria.** Tudo o que falta na origem falta no destino.
8. **Faça sempre a verificação imediata de `C4`:** PDF etiquetado, texto selecionável, marcadores presentes, refluxo com sentido.
9. **Se a exportação correu mal, volte à origem e reexporte.** É quase sempre mais rápido e mais correto do que reparar o PDF.
10. **O ficheiro de origem é a fonte da verdade.** Guarde-o. Um PDF impresso não se desimprime.

### Exercícios Práticos

**Exercício 1 — Os dois PDF gémeos**

Escolha um documento Word que já tenha estrutura (cabeçalhos, uma tabela, uma imagem com texto alternativo).

1. Exporte-o duas vezes: uma por **Ficheiro → Imprimir → Microsoft Print to PDF**, outra por **Ficheiro → Guardar Como → PDF**, com todas as opções de `C2`.
2. Dê-lhes nomes que os distingam e abra os dois no Acrobat, lado a lado.
3. Compare o aspeto visual. Anote as diferenças que consegue ver.
4. Aplique a ambos a verificação de `C4`, ponto por ponto.
5. Escreva três linhas de resposta a esta pergunta: **quantas das diferenças que encontrou em (4) eram visíveis em (3)?**

**Exercício 2 — Caçar a caixa de verificação**

Sem consultar este material:

1. Abra o Word e chegue à caixa de diálogo onde está a opção das etiquetas de acessibilidade. Cronometre.
2. Repita no PowerPoint.
3. Escreva as instruções, em cinco linhas no máximo, para alguém que nunca lá tenha ido.
4. Peça a um colega que siga as suas instruções sem fazer perguntas. Corrija o que ficou por explicar.

Este exercício produz o material que a recomendação "fixe o método por escrito" pede.

**Exercício 3 — Folheto contra diapositivos**

Sobre uma apresentação com pelo menos 10 diapositivos, todos com título:

1. Exporte em **Diapositivos** e em **Folhetos, 6 por página**.
2. Abra os dois no Acrobat e compare o painel de marcadores.
3. Tente selecionar o texto de um título de diapositivo em cada um.
4. Faça o teste do refluxo (`Ctrl` + `4`) nos dois.
5. Registe o tamanho dos ficheiros. **Compensa?**

**Exercício 4 — O que se perde pelo caminho**

Prepare um documento Word curto (2 a 3 páginas) que contenha, de propósito: um cabeçalho dentro de uma caixa de texto flutuante, um gráfico, uma equação, o nome do serviço apenas no rodapé, e um comentário por resolver.

1. Exporte-o corretamente, com todas as opções de `C2`.
2. Faça a verificação de `C4` e o teste do refluxo.
3. Para cada um dos cinco elementos, registe: **sobreviveu, sobreviveu mal, ou desapareceu?**
4. Corrija os cinco elementos **na origem** e reexporte.
5. Compare. Quantos se resolviam apenas com uma alteração no Word?

**Exercício 5 — O documento sem origem**

Peça a um colega que lhe entregue um PDF gerado por impressão, sem lhe dar o ficheiro Word.

1. Faça a verificação de `C4`.
2. Estime, por escrito, quanto tempo demoraria a tornar aquele PDF acessível à mão.
3. Estime quanto tempo demoraria se tivesse o ficheiro de origem.
4. Guarde estas duas estimativas. Vão ser úteis na secção seguinte, quando se colocar a pergunta "corrigir o PDF ou voltar à origem?".

**Exercício 6 — O procedimento da equipa**

Junte o que produziu no exercício 2 e escreva uma página única, para afixar, com:

- o caminho de menu correto, no Word e no PowerPoint;
- a lista de opções a confirmar;
- o que **nunca** fazer;
- os quatro pontos da verificação de `C4`;
- a quem recorrer quando o PDF sai sem etiquetas.

Mostre a página a alguém que produza documentos e não tenha feito este curso. Se essa pessoa conseguir exportar corretamente à primeira, a página está boa.

