# Conclusão e Boas Práticas

## Recapitulação

Este curso começou com uma imagem: **o documento é um edifício e as etiquetas são a planta**. Quem vê, vê o edifício. A tecnologia de apoio não vê o edifício — lê a planta. Um documento sem etiquetas é uma fotografia da fachada: bonita, fiel, e completamente inútil para quem precisa de lá entrar.

Tudo o que se fez desde então foi variação sobre essa ideia. No Word e no PowerPoint, construiu-se o edifício e desenhou-se a planta ao mesmo tempo. Na conversão para PDF, entregou-se — ou perdeu-se — a planta. Na verificação e correção, foi preciso abrir a planta e redesenhá-la à mão. Nos formulários, instalou-se equipamento novo dentro do edifício e teve de se registá-lo na planta, um a um.

A secção "Fundamentos da Acessibilidade de Documentos" fixou sete propriedades de um documento acessível. Todas as secções seguintes trataram delas, em aplicações diferentes. Vale a pena voltar a vê-las juntas, agora que os procedimentos estão todos conhecidos — porque é assim que se percebe que o curso não tinha cinco temas, tinha sete, repetidos em três formatos.

> **Nota de leitura.** As tabelas seguintes **não repetem procedimentos**: remetem para eles. Cada identificador — `W`, `PP`, `C`, `R`, `F` — aponta para o procedimento onde a matéria está explicada. Esta recapitulação serve para reorganizar o que já se sabe, não para ensinar de novo.

---

### 1. Identificado

**O que é:** o documento diz o que é e em que língua está escrito, antes de alguém começar a lê-lo. Título nas propriedades do ficheiro, idioma declarado, metadados corretos.

| Formato | Onde se resolve |
|---|---|
| Word | `W6` — idioma e título do documento |
| PowerPoint | Sem procedimento próprio: resolve-se exatamente como no Word (`W6`) |
| Conversão | `C2`, `C3` — o título e o idioma só chegam ao PDF se o método de exportação os transportar |
| PDF | `R6` — título, idioma e metadados; **e a definição do título como título do documento, não como nome do ficheiro** |
| Formulários | `R6` aplica-se igualmente |

**O que reter:** esta é a propriedade mais barata de todo o curso e a mais frequentemente esquecida. Três campos, um minuto de trabalho, e é o primeiro som que a pessoa ouve quando abre o ficheiro. Um PDF publicado com o título `Documento1` ou `relatorio_final_v7_REV_JF.docx` falha aqui — e falha logo à porta.

### 2. Estruturado

**O que é:** cada elemento é aquilo que parece. Um cabeçalho é um cabeçalho e não texto grande a negrito. Uma lista é uma lista e não parágrafos começados por travessão. Uma tabela tem cabeçalhos declarados.

| Formato | Onde se resolve |
|---|---|
| Word | `W1` (estilos e cabeçalhos), `W2` (listas e colunas), `W3` (tabelas) |
| PowerPoint | `PP1` (esquemas de diapositivo), `PP2` (títulos de diapositivo), `PP5` (tabelas) |
| Conversão | `C1` (preparar a origem), `C4` (confirmar que as etiquetas sobreviveram) |
| PDF | `R2` (painel de etiquetas), `R5` (tabelas) |
| Formulários | `F1` (campos reais e etiquetados), `F3` (agrupar campos relacionados) |

**O que reter:** a estrutura é a única propriedade que **não se consegue improvisar depois**. Todas as outras se corrigem com mais ou menos trabalho. Um documento sem estrutura na origem obriga a reconstruir a planta etiqueta a etiqueta no Acrobat — que foi, provavelmente, a parte mais penosa deste curso. Meia hora bem aplicada no Word poupa um dia no Acrobat.

### 3. Ordenado (ordem de leitura correta)

**O que é:** a ordem por que a tecnologia de apoio percorre o conteúdo é a mesma ordem que faz sentido para quem lê. Ordem visual e ordem de leitura coincidem.

| Formato | Onde se resolve |
|---|---|
| Word | Resulta naturalmente de `W1` e `W2`; as caixas de texto flutuantes são a exceção perigosa (`W4`) |
| PowerPoint | `PP1` e `PP3` — o painel de ordem de leitura |
| Conversão | `C1` (corrigir antes), `C4` (confirmar depois) |
| PDF | `R3` — corrigir a ordem de leitura na árvore de etiquetas |
| Formulários | `F1` (o campo no sítio certo da árvore), `F4` (ordem de tabulação) |

**O que reter:** é a propriedade mais invisível do curso. Um documento com ordem de leitura errada **não tem mau aspeto nenhum**. Nada no ecrã denuncia o problema. Só se descobre ouvindo o documento, ou abrindo o painel certo. É por isso que o PowerPoint, que parece o formato mais fácil, é na prática o mais traiçoeiro.

### 4. Percetível sem ver

**O que é:** tudo o que só existe em imagem, cor, forma ou som tem uma alternativa em texto. Imagens com texto alternativo, gráficos descritos, vídeo com legendas, informação que não depende da cor.

| Formato | Onde se resolve |
|---|---|
| Word | `W4` — texto alternativo e objetos; marcar o decorativo como decorativo |
| PowerPoint | `PP4` (imagens, gráficos, SmartArt), `PP7` (multimédia e animações) |
| Conversão | `C1` — o texto alternativo em falta na origem não aparece por magia no PDF |
| PDF | `R4` (texto alternativo), `R7` (PDF digitalizado e OCR) |
| Formulários | `F2` — a descrição do campo é a alternativa em texto do que o rótulo mostra |

**O que reter:** «percetível sem ver» não é só texto alternativo em fotografias. É também: o gráfico cuja mensagem só está nas cores das barras; o diapositivo que diz "conforme se vê no lado direito"; a tabela cujo significado está no sombreado das células; o campo obrigatório assinalado apenas com um asterisco vermelho.

### 5. Legível

**O que é:** o texto vê-se e lê-se sem esforço. Tamanho suficiente, contraste suficiente, espaçamento suficiente, e texto que é mesmo texto — não uma imagem de texto.

| Formato | Onde se resolve |
|---|---|
| Word | `W8` — tipo de letra, contraste e espaçamento, aplicados através dos estilos |
| PowerPoint | `PP9` — contraste e legibilidade em projeção, que é um caso mais exigente |
| Conversão | Herda-se da origem; a exportação não altera aparência |
| PDF | `R7` — um PDF digitalizado só é legível depois de OCR |
| Formulários | `F1` — caixas com altura suficiente para o texto introduzido não ficar cortado |

**O que reter:** esta é a única propriedade que **beneficia toda a gente, sem exceção**, e a única que se avalia a olho. É também aquela em que o design gráfico da organização costuma opor mais resistência. O argumento que funciona não é o legal: é mostrar o mesmo diapositivo projetado ao fundo de uma sala.

### 6. Navegável

**O que é:** é possível saltar, procurar e situar-se sem ler tudo do princípio ao fim. Cabeçalhos que geram marcadores, títulos únicos, ligações que dizem para onde vão.

| Formato | Onde se resolve |
|---|---|
| Word | `W1` (a hierarquia de cabeçalhos), `W5` (texto das hiperligações) |
| PowerPoint | `PP2` (títulos únicos e descritivos), `PP6` (hiperligações) |
| Conversão | `C2` — gerar marcadores a partir dos cabeçalhos na exportação |
| PDF | `R2` (a árvore de etiquetas), `R6` (metadados e vista inicial) |
| Formulários | `F4` — a navegação de um formulário é a ordem de tabulação |

**O que reter:** a navegabilidade é o retorno visível do trabalho feito na estrutura. Ninguém aplica estilos de cabeçalho por gostar de estilos: aplica-os para que, mais tarde, o painel de navegação, o índice automático e os marcadores do PDF existam sozinhos. É a propriedade que melhor demonstra aos formandos que a acessibilidade não é trabalho extra — é o mesmo trabalho, feito pela ordem certa.

### 7. Operável

**O que é:** tudo o que se pode acionar funciona só com teclado, de forma previsível e sem armadilhas.

| Formato | Onde se resolve |
|---|---|
| Word | `W7` — formulários em Word com controlos de conteúdo |
| PowerPoint | `PP7` — controlo sobre animações, transições e reprodução automática |
| Conversão | Os campos de formulário só sobrevivem com o método de exportação certo (`C2`) |
| PDF | Ligações e marcadores acionáveis por teclado (`R2`, `R6`) |
| Formulários | `F1`, `F4`, `F5`, `F6` — é aqui que a propriedade vive de facto |

**O que reter:** a operabilidade só existe verdadeiramente quando o documento tem funcionalidade — ou seja, em formulários e em conteúdo interativo. Num relatório em Word ou num PDF de leitura, quem garante a operação é a aplicação de leitura, não o autor. Esta distinção volta a aparecer, com consequências, na tabela de critérios WCAG mais abaixo.

---

### E uma oitava, só para formulários: recuperável

A secção "Formulários em PDF" acrescentou uma exigência que os documentos de leitura não têm: **quem se engana tem de saber que se enganou, onde, e como corrigir** (`F6`). Não é uma das sete propriedades do curso, porque não se aplica a documentos que não pedem nada a ninguém. Mas num formulário é tão importante como qualquer uma delas.

### A leitura de conjunto

Se este curso tivesse de caber numa frase, seria esta:

> **A planta desenha-se na origem, verifica-se na exportação, e corrige-se no PDF apenas quando não há alternativa.**

As três secções que tratam do PDF — conversão, verificação e correção, formulários — existem porque a realidade não é ideal: há documentos antigos, há originais perdidos, há circuitos que exigem PDF. Mas o custo cresce sempre na mesma direção. Corrigir na origem custa minutos. Corrigir no PDF custa horas. Refazer um documento digitalizado custa dias. A decisão de onde intervir foi tratada na secção "Escolher o Formato e Organizar o Trabalho", e é a decisão de gestão mais rentável de todo o curso.

---

## Recursos Adicionais

Os recursos nacionais vêm primeiro, porque são eles que definem o enquadramento aplicável em Portugal e a linguagem usada nas avaliações oficiais.


| Recurso | O que é | Para que serve neste curso |
|---|---|---|
| **WCAG 2.1** (W3C) | As diretrizes propriamente ditas, com os documentos de apoio *Understanding* e *Techniques* | Fonte primária dos critérios listados mais abaixo. Os *Understanding* explicam a intenção de cada critério, o que é indispensável para os aplicar a documentos |
| **WCAG2ICT** (Nota do W3C) | Explica como ler as WCAG fora da web | A chave de tradução: onde as WCAG dizem "página web", o WCAG2ICT diz como entender isso num documento. Não cria requisitos novos |
| **EN 301 549** (ETSI/CEN/CENELEC) | Norma europeia de acessibilidade em contratação pública de TIC | A **cláusula 10** é a que trata de documentos não-web. É o texto que a lei portuguesa convoca |
| **PDF/UA — ISO 14289-1** | Norma técnica do PDF acessível | Define como o ficheiro PDF tem de estar construído por dentro |
| **PDF Association** e o **Protocolo Matterhorn** | Organização e lista de pontos de verificação do PDF/UA | Traduz a norma numa lista de falhas concretas e verificáveis, incluindo as que nenhuma ferramenta deteta automaticamente |
| **Documentação de acessibilidade da Microsoft** (support.microsoft.com) | Páginas de apoio do Word e do PowerPoint | Referência para caminhos de menu e comportamentos do verificador integrado, que mudam entre versões |
| **Documentação de acessibilidade da Adobe** (helpx.adobe.com) | Páginas de apoio do Acrobat | Referência para as ferramentas de acessibilidade, o painel de etiquetas e a preparação de formulários |

> **Sugestão de ordem de leitura, para quem quiser aprofundar.** Primeiro o Decreto-Lei n.º 83/2018, para saber o que é obrigatório. Depois o WCAG2ICT, para saber como ler as WCAG num documento. Só depois a EN 301 549 e o PDF/UA, que são textos normativos densos e pouco pedagógicos. Ler pela ordem inversa é a forma mais rápida de desistir.

---

## Exercícios de Consolidação

Estes exercícios atravessam o curso todo. Ao contrário dos exercícios das secções anteriores, não treinam um procedimento: treinam **decisão, verificação e conjunto**. Recomenda-se fazê-los com documentos reais da organização.

### Exercício 1 — Fechar a grelha das sete propriedades

*Objetivo:* medir o percurso feito desde a primeira secção.

Recupere a grelha preenchida no Exercício 3 da secção "Fundamentos da Acessibilidade de Documentos" — aquela em que auditou um documento da sua organização pelas sete propriedades, antes de saber como se corrigia seja o que fosse.

Volte ao mesmo documento e preencha a grelha outra vez. Depois compare as duas versões e responda:

- Que falhas tinha identificado corretamente à primeira?
- Que falhas **não tinha visto** na altura, e vê agora?
- Que falhas achava graves e afinal são menores, e vice-versa?
- Para cada falha, escreva o identificador do procedimento que a corrige.

*O que se pretende:* a diferença entre as duas grelhas é a medida do curso. Se a segunda grelha for igual à primeira, o problema não é do formando — é do documento, que provavelmente já estava bom.

### Exercício 2 — O percurso completo de um documento

*Objetivo:* juntar todas as secções num único fluxo.

Escolha um documento Word de pelo menos dez páginas, com imagens, pelo menos uma tabela e hiperligações. Leve-o do princípio ao fim:

1. Corrija-o no Word usando `W1` a `W8`.
2. Execute o verificador integrado e resolva tudo o que ele acusar.
3. Faça a verificação manual dos pontos que o verificador **não** deteta.
4. Exporte para PDF pelo método correto (`C2`).
5. Confirme que as etiquetas sobreviveram (`C4`).
6. Execute o verificador do Acrobat (`R1`) e registe o que ele acusa.

Registe o **tempo gasto em cada etapa**. Depois responda: quanto do tempo total foi corrigir a origem e quanto foi corrigir o PDF? E se o documento já estivesse bem construído desde o início, quanto tempo teria demorado a etapa 4?

*O que se pretende:* interiorizar a economia do curso. Quem faz este exercício uma vez raramente volta a discutir se vale a pena aplicar estilos.

### Exercício 3 — Decidir onde intervir

*Objetivo:* aplicar a árvore de decisão da secção "PDF: Verificação e Correção".

Para cada situação, decida: **corrigir na origem e reexportar**, **corrigir diretamente no PDF**, ou **refazer o documento**. Justifique em duas frases.

a) Um regulamento de 2019 em PDF, sem etiquetas, com o ficheiro Word original disponível e uma revisão prevista para o próximo trimestre.

b) Um cartaz digitalizado de um evento realizado o ano passado, ainda publicado no sítio da entidade.

c) Um formulário de candidatura em PDF, com campos criados no Acrobat, cuja origem em Word já não corresponde à versão publicada.

d) Uma apresentação de 80 diapositivos que foi projetada uma vez numa conferência e depois publicada em PDF, sem que ninguém volte a usá-la.

e) Um manual de procedimentos internos, em PDF, atualizado três a quatro vezes por ano, com origem em Word bem estruturada mas exportado sempre por impressão para PDF.

*O que se pretende:* perceber que a resposta depende de três variáveis — se a origem existe, se o documento vai voltar a ser alterado, e se ainda é necessário — e não do estado do PDF.

### Exercício 4 — A auditoria de cinco minutos

*Objetivo:* criar um hábito de triagem rápida, aplicável a muitos ficheiros.

Reúna cinco PDF publicados pela sua organização. Para cada um, em cinco minutos ou menos, verifique apenas quatro coisas:

1. O documento tem título nas propriedades? (`R6`)
2. O documento tem etiquetas? (`R1`)
3. O documento tem marcadores gerados a partir dos cabeçalhos? (`C2`)
4. Selecionando e copiando um parágrafo, sai texto ou não sai nada? (`R7`)

Classifique cada documento em três categorias: **aceitável**, **corrigível**, **refazer**. Some os tempos.

*O que se pretende:* uma organização com centenas de documentos publicados não consegue auditar tudo em profundidade. Consegue triar. Estas quatro perguntas separam, com grande fiabilidade, o que precisa de atenção urgente do que não precisa.

### Exercício 5 — Traduzir para quem decide

*Objetivo:* preparar a conversa que decide se este trabalho é feito ou não.

Escreva uma nota de **uma página**, dirigida a um dirigente sem formação técnica, que responda a três perguntas:

- Porque é que os documentos que publicamos têm de ser acessíveis? (Enquadramento legal, sem jargão.)
- O que está mal hoje na nossa produção de documentos? (Com base no Exercício 4, com números.)
- O que proponho mudar, e quanto custa? (Fluxo de trabalho, formação, ferramentas.)

Regras: nenhuma sigla sem explicação, no máximo uma referência a um número de critério WCAG, e uma proposta concreta com prazo.

*O que se pretende:* a maior parte dos projetos de acessibilidade documental não falha por falta de competência técnica. Falha porque ninguém conseguiu explicar o problema a quem tem de o autorizar.

### Exercício 6 — O formulário sem rato

*Objetivo:* consolidar a secção de formulários pela via mais direta.

Pegue num formulário em PDF publicado por uma entidade pública — pode ser da sua organização ou de outra. Afaste o rato da secretária e preencha-o do princípio ao fim usando apenas o teclado. Depois repita com um leitor de ecrã (`NVDA` ou `VoiceOver`), sem olhar para o ecrã.

Registe: cada campo em que não percebeu o que devia escrever; cada momento em que a ordem de tabulação saltou para um sítio inesperado; cada erro que cometeu e que não conseguiu perceber como corrigir.

Para cada problema, indique o procedimento `F` que o teria evitado.

*O que se pretende:* nenhum verificador automático preenche formulários. Este exercício encontra, em quinze minutos, falhas que nenhuma ferramenta acusa.

---

## Lista de Verificação Final

Esta lista é para usar, não para ler. Cada item é uma verificação com resposta **sim** ou **não** — sem "mais ou menos" — e remete para o procedimento onde a correção está explicada.

Sugere-se imprimir a lista do formato que se usa mais e mantê-la à vista até os hábitos estarem formados.

### Word

**Estrutura e ordem**

- [ ] Todos os títulos e subtítulos usam estilos de cabeçalho (`Título 1`, `Título 2`, …) e não formatação manual. — `W1`
- [ ] A hierarquia de cabeçalhos não salta níveis (não há um `Título 3` logo a seguir a um `Título 1`). — `W1`
- [ ] Há exatamente um `Título 1`, correspondente ao título do documento. — `W1`
- [ ] Todas as listas foram criadas com o comando de lista, e não com travessões, asteriscos ou números escritos à mão. — `W2`
- [ ] Não há texto disposto em colunas através de tabulações ou de tabelas de desenho. — `W2`
- [ ] Todas as tabelas têm a linha de cabeçalho marcada como tal e a opção de repetir o cabeçalho nas páginas seguintes. — `W3`
- [ ] Nenhuma tabela tem células unidas, linhas em branco a servir de espaçamento, ou tabelas dentro de tabelas. — `W3`
- [ ] Nenhuma tabela é usada para dispor conteúdo que não é tabular. — `W3`
- [ ] Todas as imagens estão alinhadas com o texto e não flutuantes por cima dele. — `W4`

**Conteúdo não textual**

- [ ] Todas as imagens que transmitem informação têm texto alternativo escrito por uma pessoa. — `W4`
- [ ] Todas as imagens meramente decorativas estão assinaladas como decorativas. — `W4`
- [ ] Nenhum texto alternativo começa por "imagem de" ou "gráfico de", nem repete a legenda visível. — `W4`
- [ ] Nenhuma informação essencial existe apenas dentro de uma imagem de texto. — `W4`, `W8`
- [ ] Nenhuma informação é transmitida apenas pela cor. — `W8`

**Ligações e idioma**

- [ ] O texto de todas as hiperligações descreve o destino e faz sentido lido isoladamente (nada de "clique aqui" ou de URL crus). — `W5`
- [ ] O idioma do documento está definido corretamente. — `W6`
- [ ] As passagens noutra língua têm o idioma próprio marcado. — `W6`
- [ ] As propriedades do ficheiro têm um **título** preenchido, distinto do nome do ficheiro. — `W6`

**Formulários**

- [ ] Todos os campos são controlos de conteúdo e não linhas, sublinhados ou tabulações. — `W7`
- [ ] Todos os controlos têm a propriedade **Título** preenchida com o nome que deve ser anunciado. — `W7`

**Aparência**

- [ ] O contraste entre texto e fundo cumpre o mínimo exigido. — `W8`
- [ ] O tamanho de letra do corpo do texto respeita o mínimo adotado pela organização. — `W8`
- [ ] O espaçamento entre linhas e entre parágrafos vem dos estilos, e não de linhas em branco ou de teclas `Enter` repetidas. — `W8`, `W1`

**Verificação**

- [ ] O verificador de acessibilidade (separador **Rever** → **Verificar Acessibilidade**) não acusa erros nem avisos por resolver. — Secção de verificação do Word
- [ ] Foi feita a verificação manual do que o verificador não deteta: qualidade do texto alternativo, sentido do texto das ligações, correção da hierarquia de cabeçalhos e adequação do contraste. — Secção de verificação do Word

### PowerPoint

**Estrutura e ordem**

- [ ] Todos os diapositivos foram construídos a partir de um esquema de diapositivo, com marcadores de posição, e não com caixas de texto desenhadas à mão. — `PP1`
- [ ] Todos os diapositivos têm título, incluindo os que não o mostram visualmente. — `PP2`
- [ ] Nenhum título de diapositivo se repete (nada de cinco diapositivos chamados "Resultados"). — `PP2`
- [ ] A ordem de leitura foi verificada diapositivo a diapositivo no painel próprio e corresponde à ordem visual pretendida. — `PP3`
- [ ] Nenhum objeto ficou esquecido fora da área do diapositivo mas dentro do ficheiro. — `PP3`

**Conteúdo não textual**

- [ ] Todas as imagens informativas têm texto alternativo. — `PP4`
- [ ] Todos os gráficos têm alternativa em texto que transmite a **conclusão**, não apenas a descrição do tipo de gráfico. — `PP4`
- [ ] Todos os elementos SmartArt têm alternativa em texto, ou o conteúdo está também em texto normal. — `PP4`
- [ ] Os elementos decorativos estão assinalados como decorativos. — `PP4`
- [ ] Todas as tabelas têm linha de cabeçalho marcada. — `PP5`
- [ ] Nenhum diapositivo depende da cor, da posição ou da forma para transmitir informação ("o quadrado verde à direita"). — `PP9`

**Multimédia e movimento**

- [ ] Todos os vídeos com som têm legendas. — `PP7`
- [ ] Todo o áudio isolado tem transcrição. — `PP7`
- [ ] Nada arranca automaticamente ao abrir ou ao entrar no diapositivo, ou, se arranca, pode ser parado. — `PP7`
- [ ] Não há transições automáticas por tempo que impeçam quem lê devagar de acompanhar. — `PP7`
- [ ] Nenhuma animação pisca mais do que três vezes por segundo. — `PP7`

**Ligações, notas e aparência**

- [ ] O texto das hiperligações descreve o destino. — `PP6`
- [ ] As notas do orador contêm o que foi dito e não está no diapositivo, e o ficheiro é distribuído com elas. — `PP8`
- [ ] O contraste é suficiente **em condições de projeção**, não apenas no ecrã do portátil. — `PP9`
- [ ] O tamanho de letra respeita o mínimo definido para projeção. — `PP9`
- [ ] O idioma da apresentação está definido e as propriedades do ficheiro têm título preenchido. — `W6`

**Verificação**

- [ ] O verificador de acessibilidade não acusa erros nem avisos por resolver. — Secção de verificação do PowerPoint
- [ ] Foi feita a verificação manual do que o verificador não deteta, com especial atenção à ordem de leitura. — Secção de verificação do PowerPoint

### PDF

**Antes de exportar**

- [ ] O documento de origem passou integralmente na lista do Word ou do PowerPoint acima. — `C1`
- [ ] O documento de origem está guardado e versionado, e continuará a ser a fonte de futuras alterações. — Secção "Escolher o Formato e Organizar o Trabalho"
- [ ] O método de exportação escolhido é **Guardar Como / Guardar uma Cópia**, **Exportar**, ou o separador **Acrobat**. Não é impressão para PDF. — `C2`, `C3`
- [ ] Nas opções de exportação, a marcação de etiquetas de estrutura está ativa. — `C2`, `C3`
- [ ] Nas opções de exportação, a criação de marcadores a partir dos cabeçalhos está ativa. — `C2`
- [ ] Se o documento de origem tem campos de formulário que devem funcionar no PDF, foi usado o método que os converte. — `C2`

**Depois de exportar**

- [ ] O PDF tem etiquetas. — `C4`, `R1`
- [ ] O painel de marcadores mostra a estrutura de cabeçalhos do documento. — `C4`
- [ ] Selecionar e copiar um parágrafo devolve texto legível, e não caracteres estranhos nem nada. — `R7`
- [ ] O verificador de acessibilidade do Acrobat foi executado e não deixa erros por resolver. — `R1`
- [ ] A árvore de etiquetas reflete a estrutura real: cabeçalhos como cabeçalhos, listas como listas, tabelas como tabelas. — `R2`
- [ ] A ordem de leitura foi percorrida e corresponde à ordem visual. — `R3`
- [ ] Os elementos puramente gráficos e os cabeçalhos e rodapés de página estão marcados como artefactos e não são lidos. — `R2`
- [ ] Todas as figuras têm texto alternativo, e as decorativas estão marcadas como artefacto. — `R4`
- [ ] Todas as tabelas têm células de cabeçalho declaradas e âmbito definido. — `R5`
- [ ] O documento tem título preenchido **e** está configurado para mostrar o título, não o nome do ficheiro. — `R6`
- [ ] O idioma do documento está definido. — `R6`
- [ ] Se o documento tem definições de segurança, elas não bloqueiam o acesso por tecnologia de apoio. — `R6`
- [ ] Se o documento tem origem numa digitalização, foi feito OCR e o resultado foi revisto, não apenas executado. — `R7`

**Se o PDF tiver formulário**

- [ ] Todos os campos são campos reais; não há linhas nem sublinhados a fazer de campo. — `F1`
- [ ] Todos os campos têm a **descrição da ferramenta** preenchida com o nome que deve ser anunciado. — `F2`
- [ ] Nenhum campo tem simultaneamente descrição da ferramenta e texto alternativo com conteúdos diferentes. — `F2`
- [ ] Os botões de opção do mesmo grupo partilham o mesmo nome; as caixas de verificação têm nomes distintos. — `F3`
- [ ] Cada opção de um grupo tem, na sua descrição, a pergunta a que responde. — `F3`
- [ ] A ordem de tabulação foi definida em **todas** as páginas e corresponde à ordem visual. — `F4`
- [ ] Todos os botões têm descrição e nenhuma ação está associada à entrada ou saída de foco. — `F5`
- [ ] Os campos obrigatórios são identificados por texto, não apenas por cor ou por asterisco. — `F6`
- [ ] As mensagens de erro dizem qual é o campo e o que está errado, e o formato esperado é indicado **antes** de o utilizador escrever. — `F6`
- [ ] O formulário foi percorrido do princípio ao fim só com teclado. — Secção de verificação de formulários
- [ ] O formulário foi percorrido com leitor de ecrã, sem olhar para o ecrã. — Secção de verificação de formulários

---

## Critérios de Sucesso WCAG Relacionados

Esta é a **única secção do curso onde aparecem tabelas consolidadas de critérios**. Ao longo das secções anteriores, os critérios foram referidos pontualmente, quando ajudavam a perceber a razão de um procedimento. Aqui aparecem todos juntos, para servirem de referência.

Três avisos antes de ler as tabelas.

**Primeiro: nem todos os critérios das WCAG se aplicam a documentos.** As WCAG foram escritas para a web. A leitura para fora da web faz-se através do WCAG2ICT, e a EN 301 549 formaliza-a na cláusula 10. Alguns critérios ficam sem objeto num documento — por exemplo, os que falam de conjuntos de páginas ou de navegação repetida. Não estão nas tabelas porque não se aplicam, e não porque foram esquecidos.

**Segundo: os critérios de operação só se aplicam quando o documento tem funcionalidade.** Um relatório em PDF que só se lê não tem nada para operar: quem trata do teclado é a aplicação de leitura. Os critérios sobre teclado, foco e erros aplicam-se quando o documento **contém elementos interativos** — sobretudo formulários. Nas tabelas, isso está indicado.

**Terceiro: o nível A e o nível AA são a base legal em Portugal; o nível AAA não é.** O Decreto-Lei n.º 83/2018, através da EN 301 549, fixa a exigência no nível AA. Os critérios de nível AAA são boa prática recomendada, e nunca devem ser apresentados a uma organização como obrigação.

### Nível A e AA — Base Legal

**Nível A**

| Critério | Nome | O que exige | Aplicação concreta a documentos |
|---|---|---|---|
| 1.1.1 | Conteúdo não textual | Todo o conteúdo não textual tem alternativa em texto com finalidade equivalente | Texto alternativo em imagens, gráficos e SmartArt; decorativo marcado como decorativo — `W4`, `PP4`, `R4`, `F2` |
| 1.2.1 | Só áudio e só vídeo (pré-gravado) | Alternativa em texto para áudio isolado; alternativa para vídeo sem som | Transcrição do áudio inserido num diapositivo — `PP7` |
| 1.2.2 | Legendas (pré-gravado) | Vídeo com som tem legendas sincronizadas | Vídeos inseridos em apresentações — `PP7` |
| 1.2.3 | Audiodescrição ou alternativa a multimédia (pré-gravado) | Informação visual essencial do vídeo é transmitida por outra via | Vídeos com conteúdo visual que o som não cobre — `PP7` |
| 1.3.1 | Informação e relações | A estrutura visível existe também de forma programática | Estilos de cabeçalho, listas reais, tabelas com cabeçalho, campos com etiqueta — `W1`, `W2`, `W3`, `PP1`, `PP2`, `PP5`, `R2`, `R5`, `F1`, `F3` |
| 1.3.2 | Sequência com significado | A ordem de leitura preserva o sentido | Painel de ordem de leitura e árvore de etiquetas — `PP3`, `C1`, `C4`, `R3` |
| 1.3.3 | Características sensoriais | As instruções não dependem só de forma, cor, tamanho ou posição | Evitar "ver o quadro à direita" ou "os itens a verde" — `W8`, `PP9`, `F6` |
| 1.4.1 | Utilização da cor | A cor não é o único meio de transmitir informação | Estado, obrigatoriedade ou categoria assinalados também por texto — `W8`, `PP9`, `F6` |
| 1.4.2 | Controlo de áudio | Áudio automático com mais de 3 segundos pode ser parado | Som que arranca sozinho num diapositivo — `PP7` |
| 2.1.1 | Teclado | Toda a funcionalidade é operável por teclado | **Só quando há funcionalidade**: campos, botões e ações de formulário — `F1`, `F4`, `F5`; controlos em Word — `W7` |
| 2.1.2 | Sem bloqueio do teclado | O foco nunca fica preso num elemento | **Só com funcionalidade**: percurso completo do formulário com `Tab` — `F4` |
| 2.2.1 | Temporização ajustável | Limites de tempo podem ser desligados, ajustados ou prolongados | Avanço automático de diapositivos por tempo — `PP7` |
| 2.2.2 | Colocar em pausa, parar, ocultar | Movimento automático com mais de 5 segundos pode ser parado | Animações e transições automáticas — `PP7` |
| 2.3.1 | Três flashes ou abaixo do limiar | Nada pisca mais de três vezes por segundo | Animações e vídeo em apresentações — `PP7` |
| 2.4.2 | Documento com título | O documento tem um título que descreve o seu tema ou finalidade | Propriedade **Título** do ficheiro e do PDF — `W6`, `C2`, `C3`, `R6` |
| 2.4.3 | Ordem de focagem | A ordem de foco preserva o sentido e a operabilidade | **Só com funcionalidade**: ordem de tabulação dos campos — `F4` |
| 2.4.4 | Finalidade da ligação (em contexto) | O destino de cada ligação percebe-se pelo texto ou pelo contexto próximo | Texto das hiperligações — `W5`, `PP6` |
| 2.5.3 | Etiqueta no nome | O nome anunciado inclui o texto visível do rótulo | O rótulo visível do campo e a descrição da ferramenta têm de coincidir — `F2` |
| 3.1.1 | Idioma do documento | O idioma predominante está declarado | Idioma no Word, no PowerPoint e nas propriedades do PDF — `W6`, `R6` |
| 3.2.1 | Em foco | Receber foco não desencadeia mudanças de contexto | **Só com funcionalidade**: nenhuma ação associada à entrada de foco num campo — `F5` |
| 3.2.2 | Na introdução de dados | Introduzir dados não desencadeia mudanças de contexto sem aviso | **Só com funcionalidade**: nada acontece sozinho ao escrever num campo — `F5`, `F6` |
| 3.3.1 | Identificação de erros | O erro é identificado e descrito em texto | Mensagens de validação do formulário — `F6` |
| 3.3.2 | Etiquetas ou instruções | Os campos têm etiquetas e as instruções necessárias | Rótulo visível e descrição do campo; formato esperado indicado à partida — `W7`, `F2`, `F6` |
| 4.1.2 | Nome, função, valor | Cada elemento interativo expõe nome, função e valor à tecnologia de apoio | **Só com funcionalidade**: campos etiquetados na árvore e com descrição — `F1`, `F2`, `R2` |

**Nível AA**

| Critério | Nome | O que exige | Aplicação concreta a documentos |
|---|---|---|---|
| 1.4.3 | Contraste (mínimo) | 4.5:1 para texto normal, 3:1 para texto grande | Cores dos estilos, dos gráficos e dos diapositivos — `W8`, `PP9` |
| 1.4.4 | Redimensionamento do texto | O texto pode ser ampliado até 200 % sem perda de conteúdo ou função | Não fixar texto em imagens nem em caixas que cortam o conteúdo — `W8`, `PP9` |
| 1.4.5 | Imagens de texto | O texto é texto, salvo casos justificados como logótipos | Cabeçalhos, tabelas e diagramas inseridos como imagem — `W4`, `PP4`, `R7` |
| 1.4.10 | Refluxo | O conteúdo adapta-se a larguras reduzidas sem obrigar a deslocação em duas direções | No PDF, a vista de refluxo só funciona com etiquetas corretas — `R2`, `R3` |
| 1.4.11 | Contraste de conteúdo não textual | 3:1 para elementos de interface e para partes essenciais de gráficos | Limites de campos de formulário, séries de gráficos, ícones informativos — `PP4`, `F1` |
| 1.4.12 | Espaçamento do texto | Aumentar espaçamento entre linhas, parágrafos, palavras e letras não perde conteúdo | Não usar caixas de dimensão fixa que cortam texto ao aumentar o espaçamento — `W8` |
| 2.4.6 | Cabeçalhos e etiquetas | Cabeçalhos e etiquetas descrevem o tema ou a finalidade | Cabeçalhos que dizem o que vem a seguir; títulos de diapositivo únicos; rótulos de campo claros — `W1`, `PP2`, `F2` |
| 2.4.7 | Foco visível | O elemento com foco é visualmente identificável | **Só com funcionalidade**: o campo ativo do formulário é distinguível — `F1`, `F4` |
| 3.1.2 | Idioma das partes | As passagens noutra língua estão marcadas | Citações, títulos e expressões estrangeiras — `W6` |
| 3.3.3 | Sugestão após erro | Quando se conhece a correção, ela é sugerida ao utilizador | Mensagem que indica o formato esperado, não apenas que há erro — `F6` |
| 3.3.4 | Prevenção de erros (jurídicos, financeiros, de dados) | Submissões com consequências são reversíveis, verificadas ou confirmadas | Formulários de candidatura ou declaração: revisão antes de submeter — `F5`, `F6` |
| 4.1.3 | Mensagens de estado | Mudanças de estado são comunicadas sem mover o foco | **Só com funcionalidade**: avisos de validação que aparecem sem o utilizador dar por isso — `F6` |

> **Como usar estas tabelas em auditoria.** Não se percorre a tabela de cima a baixo para cada documento — dá trabalho e produz relatórios que ninguém lê. Percorre-se a **Lista de Verificação Final** da secção anterior, que é acionável, e usa-se esta tabela apenas quando é preciso justificar uma não conformidade num relatório formal ou numa declaração de acessibilidade. As duas listas cobrem o mesmo terreno: uma está organizada para quem produz, a outra para quem presta contas.

### Nível AAA — Boa Prática

Os critérios seguintes **não são exigidos pela lei portuguesa**. São recomendações de nível superior. Alguns deles são, ainda assim, muito relevantes para documentos — em particular os que tratam de linguagem, porque um documento administrativo mal escrito exclui muito mais gente do que uma etiqueta mal colocada.

| Critério | Nome | O que exige | Aplicação concreta a documentos |
|---|---|---|---|
| 1.2.6 | Língua gestual (pré-gravado) | Vídeo com som tem interpretação em língua gestual | Vídeo institucional inserido numa apresentação, com interpretação em Língua Gestual Portuguesa. **Boa prática acima do exigido**, não obrigação — `PP7` |
| 1.2.8 | Alternativa a multimédia (pré-gravado) | Existe uma alternativa completa em texto para o multimédia | Documento com a transcrição integral do vídeo, incluindo o que é apenas visual — `PP7` |
| 1.4.6 | Contraste (melhorado) | 7:1 para texto normal, 4.5:1 para texto grande | Documentos destinados a público com baixa visão, ou a projeção em salas grandes — `W8`, `PP9` |
| 1.4.8 | Apresentação visual | Linha com máximo de 80 caracteres, sem justificação, espaçamento reforçado, cores ajustáveis | Corpo de texto de relatórios longos: alinhar à esquerda em vez de justificar, e espaçar as linhas — `W8` |
| 1.4.9 | Imagens de texto (sem exceção) | Texto em imagem apenas quando é essencial | Eliminar totalmente cabeçalhos e infografias que só existem como imagem — `W4`, `PP4` |
| 2.4.9 | Finalidade da ligação (apenas ligação) | O texto da ligação chega, sozinho, para perceber o destino | Ligações que funcionam quando o leitor de ecrã lista todas as ligações fora do contexto — `W5`, `PP6` |
| 2.4.10 | Cabeçalhos de secção | O conteúdo está organizado por cabeçalhos de secção | Documentos longos com hierarquia completa e granular, não apenas nos capítulos — `W1` |
| 3.1.3 | Palavras invulgares | Existe explicação para termos técnicos e expressões idiomáticas | Glossário nos documentos com linguagem administrativa ou jurídica — Recomendações |
| 3.1.4 | Abreviaturas | A forma extensa das siglas está disponível | Expandir a sigla na primeira ocorrência, ou incluir lista de siglas — Recomendações |
| 3.1.5 | Nível de leitura | O texto é compreensível por quem tem escolaridade básica, ou existe versão simplificada | Versão em linguagem clara dos documentos dirigidos ao público — Recomendações |
| 3.3.5 | Ajuda | Existe ajuda sensível ao contexto | Exemplos e explicações junto dos campos difíceis do formulário — `F2`, `F6` |
| 3.3.6 | Prevenção de erros (todos) | Qualquer submissão é reversível, verificada ou confirmada | Passo de revisão em **todos** os formulários, não só nos que têm consequências jurídicas — `F5`, `F6` |

> **Como apresentar o nível AAA numa organização.** Não como uma segunda lista de obrigações — isso desmotiva e confunde a prioridade. A forma que funciona é escolher **dois ou três** critérios AAA que sejam baratos e de grande impacto no contexto concreto, e adotá-los como norma interna. Para a administração pública portuguesa, os candidatos naturais são 3.1.4 (expandir siglas) e 3.1.5 (linguagem clara): custam pouco, não exigem ferramentas nenhumas, e melhoram a vida de toda a gente — não apenas de quem tem uma deficiência.

---

## Requisitos Específicos para Documentos Não-Web

### Porque é que as WCAG não chegam

As WCAG foram escritas para páginas web e falam a linguagem da web: páginas, conjuntos de páginas, agentes de utilizador, processos. Um documento não é nada disso. É um ficheiro, aberto numa aplicação, muitas vezes fora de linha.

Isto cria três problemas práticos.

**Primeiro, há palavras que é preciso traduzir.** Quando um critério diz "página web", o que é isso num documento de 200 páginas — o documento inteiro, ou cada página? A resposta é: o documento inteiro. É por isso que 2.4.2 se lê como *documento com título* e não como *página com título*.

**Segundo, há critérios que ficam sem objeto.** Um critério sobre navegação consistente entre páginas de um sítio não tem tradução possível para um ficheiro isolado. Não é que o documento cumpra: é que a pergunta não se aplica.

**Terceiro, há exigências que as WCAG não fazem e que os documentos precisam.** As WCAG nada dizem sobre como um ficheiro PDF deve estar construído por dentro. E, no entanto, é exatamente aí que os documentos falham.

É para resolver estes três problemas que existem a cláusula 10 da EN 301 549 e a norma PDF/UA. Uma resolve os dois primeiros, a outra o terceiro.

> **Na analogia do curso.** As WCAG dizem **o que o edifício tem de oferecer a quem entra**: entradas acessíveis, sinalização legível, percursos que fazem sentido. A cláusula 10 diz **como ler essas regras quando o edifício não é um prédio de escritórios mas uma casa isolada** — e assinala as regras que só fazem sentido em bairros com várias casas. O PDF/UA diz **como a planta tem de estar desenhada** para que qualquer técnico a consiga ler: que símbolos usar, que camadas incluir, o que não pode faltar.

### EN 301 549, Cláusula 10

A EN 301 549 é a norma europeia de acessibilidade aplicável às TIC. É ela que o Decreto-Lei n.º 83/2018 convoca. A norma está dividida por tipos de produto: a cláusula 9 trata da web, a cláusula 11 do software, e a **cláusula 10 trata dos documentos não-web** — que é o que este curso estudou.

A cláusula 10 faz três coisas, e só três.

**1. Repete os critérios das WCAG, reescritos para documentos.** A maior parte da cláusula 10 é a lista dos critérios de nível A e AA, com o vocabulário adaptado: onde as WCAG dizem "página web", a cláusula 10 diz "documento não-web". O conteúdo do requisito não muda. É por isso que a tabela de critérios apresentada acima **é** a substância da cláusula 10.

**2. Declara sem efeito os critérios que não se aplicam.** Alguns critérios são expressamente marcados como não aplicáveis a documentos, por falarem de realidades que um ficheiro isolado não tem — nomeadamente os que tratam de blocos repetidos entre páginas, de várias formas de localizar uma página num conjunto, e de navegação e identificação consistentes ao longo de um sítio. É esta declaração que dá segurança a quem audita: não se está a ignorar o critério, está-se a aplicar a norma.

**3. Acrescenta dois requisitos que as WCAG não têm.** São requisitos sobre multimédia inserida em documentos:

- **Posicionamento das legendas** — as legendas não podem tapar informação relevante da imagem, nem ser tapadas por ela.
- **Momento da audiodescrição** — a audiodescrição deve ser inserida nas pausas do áudio original, sem se sobrepor ao que está a ser dito.

Nenhum dos dois aparece nas WCAG desta forma, e ambos são relevantes para apresentações com vídeo (`PP7`).

**O que reter, na prática:** cumprir o nível AA das WCAG, lido para documentos, é essencialmente cumprir a cláusula 10. Não é preciso comprar a norma nem estudá-la para produzir documentos acessíveis. É preciso conhecê-la para **justificar decisões** — em cadernos de encargos, em declarações de acessibilidade e em respostas a reclamações.

### PDF/UA

O **PDF/UA** (*Universal Accessibility*), formalmente ISO 14289-1, responde à terceira lacuna: diz como o ficheiro PDF tem de estar construído por dentro.

A diferença face às WCAG resume-se assim:

| | WCAG (e cláusula 10) | PDF/UA |
|---|---|---|
| Responde a | **O que** o utilizador tem de conseguir obter | **Como** o ficheiro tem de estar construído |
| Aplica-se a | Qualquer formato de documento | Apenas a ficheiros PDF |
| Exemplo de exigência | "A informação e as relações têm de ser determináveis programaticamente" | "O documento tem de estar etiquetado, e todo o conteúdo tem de ser conteúdo real ou artefacto declarado" |
| Quem verifica | Pessoa, com apoio de ferramentas | Ferramenta, com apoio de pessoa |

Em traços largos, o PDF/UA exige que o ficheiro tenha etiquetas; que a árvore de etiquetas represente a estrutura lógica real; que todo o conteúdo esteja etiquetado ou declarado como artefacto, sem terra de ninguém; que os tipos de letra estejam incorporados e com correspondência correta para caracteres, para que o texto seja extraível e pesquisável; que o idioma esteja declarado; que os campos de formulário tenham nome acessível; e que a informação nunca dependa apenas do aspeto visual.

Quem seguiu os procedimentos `R2`, `R4`, `R5`, `R6` e `F1`–`F2` deste curso já esteve a trabalhar em PDF/UA sem lhe chamar isso.

**Três avisos honestos.**

**Cumprir o PDF/UA não garante cumprir as WCAG.** Um PDF pode estar impecavelmente etiquetado e ter contraste insuficiente, texto alternativo inútil ou linguagem incompreensível. A norma técnica não avalia a qualidade do conteúdo.

**Cumprir as WCAG não garante cumprir o PDF/UA.** Há detalhes técnicos de construção do ficheiro — incorporação de tipos de letra, correspondência de caracteres, declaração de artefactos — que nenhum critério WCAG cobre diretamente e que fazem falhar a validação.

**Nenhuma ferramenta valida tudo.** O verificador do Acrobat (`R1`) não é um validador de PDF/UA completo. E mesmo os validadores especializados só verificam o que é verificável por máquina: nenhum consegue dizer se um texto alternativo descreve bem a imagem. O **Protocolo Matterhorn**, publicado pela PDF Association, é útil precisamente por separar de forma explícita os pontos que a máquina verifica dos que exigem uma pessoa.

**Quando é que o PDF/UA interessa mesmo?** Em três situações concretas: quando se compram serviços de produção de documentos e é preciso escrever uma exigência verificável no caderno de encargos; quando se produz um grande volume de PDF e se quer automatizar a validação; e quando se responde a uma reclamação e é preciso demonstrar conformidade com um critério objetivo. Para quem produz um relatório por mês no Word, o caminho continua a ser o mesmo deste curso: construir bem na origem, exportar bem, e verificar.

---

> **Fim do curso.**
>
> Se houver uma única coisa a levar daqui, que seja esta: a acessibilidade de um documento não se acrescenta no fim. Constrói-se ao mesmo tempo que o documento — e custa, então, quase nada. Tudo o resto que este curso ensinou foi como reparar o que se fez pela ordem errada.
