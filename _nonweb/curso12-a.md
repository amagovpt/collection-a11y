# Fundamentos da Acessibilidade de Documentos

## Introdução

Esta é a primeira secção do curso e a única inteiramente conceptual. Não há aqui passos a executar em nenhuma aplicação: há ideias a fixar.

A razão é prática. Todas as secções seguintes — Word, PowerPoint, conversão para PDF, verificação de PDF, formulários — tratam de procedimentos. Se cada uma tivesse de explicar do zero o que é uma etiqueta, o que faz um leitor de ecrã ou o que diz a lei, o curso repetir-se-ia cinco vezes. Em vez disso, tudo isso fica aqui. Quando uma secção posterior precisar de um destes conceitos, remete para esta.

Vale por isso a pena ler esta secção com atenção, mesmo para quem já tem experiência com documentos. O vocabulário definido aqui é usado, sem nova explicação, em todo o resto do curso.

### Porque Continuamos a Usar Documentos

Há duas décadas que se anuncia o fim do documento. Ele não chegou. A administração pública, as empresas e as escolas continuam a produzir e a distribuir milhões de ficheiros Word, PowerPoint e PDF por ano. As razões são reais:

- **É preciso imprimir e assinar.** Formulários, requerimentos, declarações e certidões continuam a ter uma vida em papel.
- **É preciso fixar uma versão.** Um relatório aprovado, uma ata, um caderno de encargos: nestes casos, o valor está em o conteúdo não mudar. Uma página web muda; um ficheiro fica.
- **É preciso apresentar em sala.** Uma apresentação de diapositivos serve um contexto — alguém a falar diante de uma audiência — que uma página web não serve bem.
- **É preciso enviar e guardar.** Um ficheiro anexado a uma mensagem pode ser lido sem rede, arquivado durante anos e entregue a um tribunal.
- **É o que a organização sabe fazer.** Boa parte das pessoas que produzem conteúdo público domina o Word e não domina HTML.

Nada disto significa que o documento seja sempre a escolha certa. Muitas vezes não é, e um PDF publicado num sítio web é a pior de todas as opções disponíveis. Essa decisão, publicar em documento ou publicar em página web, tem uma secção própria neste curso, "Escolher o Formato e Organizar o Trabalho". Aqui basta reter o essencial: enquanto houver documentos, é preciso que sejam acessíveis, porque um documento inacessível exclui pessoas exatamente da mesma forma que uma página web inacessível.

### Como as Pessoas com Deficiência Acedem a Documentos

Um documento não é lido de uma só maneira. É lido de muitas.

**Quem não vê** usa um **leitor de ecrã**. O leitor de ecrã transforma o conteúdo em fala sintética ou em texto numa **linha braille**. Em ambos os casos, o conteúdo chega **um elemento de cada vez, por uma ordem**. Não há vista de conjunto: não é possível olhar para a página e perceber, num relance, que há três colunas, uma caixa lateral e um rodapé.

**Quem vê pouco** amplia o documento — às vezes 400% ou mais — ou muda as cores para um contraste que lhe seja legível. Ampliar significa ver uma pequena janela de cada vez, o que torna crítico que o texto se reorganize e que a informação não dependa da posição na página.

**Quem não distingue cores** recebe o documento sem uma das camadas de informação que o autor usou. Se a única forma de saber que um campo é obrigatório é ele estar a vermelho, essa informação não chega.

**Quem não ouve** depende das legendas e da transcrição do vídeo e do áudio incluídos numa apresentação. O som que acompanha um diapositivo não existe para esta pessoa.

**Quem tem limitações motoras** pode não usar rato. Navega com teclado, com um comutador ou por comando de voz. Tudo o que só se consegue fazer apontando e clicando fica fora do seu alcance. Num formulário isso significa não conseguir preenchê-lo.

**Quem tem dislexia ou dificuldades de leitura** usa frequentemente software que lê o texto em voz alta enquanto o destaca, ou que muda o tipo de letra e o espaçamento. Estas ferramentas precisam de texto verdadeiro, não de imagens de texto.

**Quem tem limitações cognitivas ou de atenção** beneficia de estrutura clara, linguagem simples e blocos curtos, que também tornam o documento melhor para toda a gente.

Vale a pena notar duas coisas. Primeira: estas situações combinam-se. Uma pessoa idosa pode ver menos, ouvir menos e ter menos destreza, tudo ao mesmo tempo. Segunda: quase todas estas ferramentas dependem da mesma coisa: de o documento lhes dizer, por dentro, o que cada parte é. É disso que trata o resto desta secção.

## A Planta do Edifício

Toda esta secção — e todo este curso — assenta numa imagem que vale a pena guardar.

> **Um documento é um edifício. As etiquetas são a planta desse edifício.**
>
> Quem vê, vê o edifício: entra, olha em volta, percebe onde estão as divisões. Quem usa tecnologia de apoio não vê o edifício: recebe a planta e percorre-a, divisão a divisão, pela ordem em que a planta as lista.
>
> Um documento sem etiquetas é uma **fotografia do edifício, sem planta nenhuma**. Bonita, talvez fiel, mas inútil para quem precisa de saber onde ficam as portas.

Esta analogia vai reaparecer ao longo do curso. Não é decorativa: descreve com rigor o que se passa dentro de um ficheiro.

### O Que a Tecnologia de Apoio Lê Num Documento

Comecemos por desfazer um mal-entendido comum: **um leitor de ecrã não lê a página**. Não olha para o ficheiro como nós olhamos. Não vê que aquele texto está maior, mais escuro e afastado do resto, e conclui daí que é um título.

O que o leitor de ecrã recebe é uma estrutura de dados, uma lista organizada de elementos, cada um com uma **etiqueta** que diz o que ele é. É isso que se chama um **documento etiquetado**: um documento em que cada parte do conteúdo está marcada com a sua natureza.

Para cada elemento, a tecnologia de apoio pode obter:

- **O que o elemento é** — um cabeçalho, um parágrafo, um item de lista, uma tabela, uma célula, uma imagem, uma hiperligação, um campo de formulário.
- **O nível ou a posição**, quando aplicável — cabeçalho de nível 2, item 3 de 7, célula da coluna "Valor".
- **O texto** que ele contém.
- **As relações com outros elementos** — que aquela célula pertence àquela coluna e àquela linha; que aquela imagem tem aquela descrição; que aquela caixa de escrita corresponde àquele rótulo.
- **O idioma** em que está escrito.
- **O estado**, no caso de elementos interativos — se um campo é obrigatório, se está preenchido, se tem erro.

E aqui está a regra que governa tudo o resto:

> **O que não está na planta não existe para a tecnologia de apoio.**

Se o documento não disser que aquela linha é um cabeçalho, ela é apenas um parágrafo, por muito grande e negrito que esteja. Se não disser o que a imagem mostra, a imagem é silêncio. Se não disser qual é o rótulo daquele campo, o utilizador ouve "caixa de edição" e não sabe o que lá pôr.

**Exemplo — dois títulos que parecem iguais**

*Versão A.* O autor escreveu "Capítulo 2 — Prazos de Candidatura", selecionou o texto, aumentou para 18 pontos, aplicou negrito e centrou.

*Versão B.* O autor escreveu o mesmo texto e aplicou-lhe o estilo de cabeçalho de nível 1 da aplicação, que por acaso também o mostra a 18 pontos, negrito e centrado.

No ecrã, as duas versões são indistinguíveis. Impressas, são iguais.

**O que funciona e o que não funciona:** na Versão A, o autor pintou uma parede para *parecer* uma porta. A planta continua a dizer "parágrafo". O leitor de ecrã lê a linha no meio do texto corrido, sem qualquer indicação de que ali começa uma parte nova, e o utilizador não a encontra na lista de cabeçalhos do documento, porque essa lista está vazia. Na Versão B, a planta diz "cabeçalho, nível 1". O utilizador pode saltar de cabeçalho em cabeçalho, obter o índice do documento em três segundos e decidir o que quer ler. O resultado visual foi o mesmo; o documento não é o mesmo. **Formatação é aparência; estrutura é informação.** As duas coisas costumam andar juntas, mas só uma delas chega a quem não vê.

**O caso extremo: o documento digitalizado**

Um PDF obtido a partir de um digitalizador é, literalmente, uma fotografia de páginas de papel. Não tem etiquetas, não tem estrutura e muitas vezes nem sequer tem texto: tem uma imagem de letras. Para um leitor de ecrã, um documento desses é uma página em branco, ou quase. É o caso puro da fotografia do edifício sem planta, e é, ainda hoje, uma das formas mais comuns de publicar informação pública. A recuperação destes ficheiros é tratada na secção "PDF: Verificação e Correção".

### Ordem Visual e Ordem de Leitura

Há uma segunda ideia, tão importante como a primeira, e bastante menos intuitiva.

Num documento existem **duas ordens diferentes**, e elas podem não coincidir:

- A **ordem visual** é aquela que o olho segue na página: de cima para baixo, da esquerda para a direita, saltando entre colunas e caixas conforme o desenho sugere.
- A **ordem de leitura programática** é a sequência pela qual os elementos estão realmente guardados dentro do ficheiro, e é essa, e apenas essa, que a tecnologia de apoio percorre.

Na analogia: a planta do edifício lista as divisões por uma certa ordem. Normalmente, essa ordem corresponde ao percurso natural de quem visita. Mas se a planta listar a casa de banho do segundo andar entre a entrada e a sala, quem só tem a planta vai passar por lá, porque a planta é tudo o que tem.

Quando é que as duas ordens divergem? Quase sempre pela mesma razão: **o conteúdo foi colocado na página por posição, e não por sequência**. Caixas de texto arrastadas para o sítio certo, elementos acrescentados depois, colunas simuladas com tabulações, imagens colocadas por cima do texto.

**Exemplo — o diapositivo montado por camadas**

Um formador prepara um diapositivo. Escreve o título, escreve os três pontos do corpo, e no fim decide acrescentar uma nota destacada no topo, numa caixa de texto que arrasta para cima do título.

Visualmente, lê-se: nota destacada → título → três pontos.

Programaticamente, lê-se: título → três pontos → nota destacada. Porque foi essa a ordem por que os elementos foram criados.

**O que funciona mal aqui:** a audiência que vê o diapositivo recebe a nota primeiro, que é precisamente para isso que ela serve. Quem ouve o diapositivo através de um leitor de ecrã recebe-a no fim, quando já perdeu o contexto que ela devia fornecer. O erro não está na aparência, o diapositivo está bem desenhado. Está na diferença entre o que se vê e o que está guardado. Nada, na aparência do ficheiro, denuncia o problema: é preciso ir ver a planta.

**Exemplo — o boletim de duas colunas**

Um boletim informativo é montado com duas caixas de texto lado a lado, a fazer de colunas. A caixa da esquerda contém a primeira metade de um artigo; a da direita, a segunda metade.

**O que funciona mal aqui:** se as caixas foram criadas pela ordem certa, tudo corre bem por acidente. Se a caixa da direita foi criada primeiro — porque o autor começou por aí — o leitor de ecrã lê a segunda metade do artigo antes da primeira, e o texto passa a ser incompreensível sem que nenhuma palavra esteja errada. É um bom lembrete de que a ordem de leitura não é uma questão de "estar certo ou errado" na aparência: é uma propriedade invisível que tem de ser verificada de propósito.

Guardemos então a segunda regra:

> **A vista escolhe o percurso. A tecnologia de apoio recebe-o pronto. Se ninguém tratou da sequência, ela é o resultado do acaso da produção.**

## As Propriedades de um Documento Acessível

Precisamos agora de vocabulário estável. Nas secções seguintes, cada procedimento vai ser justificado por aquilo que garante, e essa justificação usa sempre uma destas sete palavras chave.

Um documento acessível é um documento **identificado, estruturado, ordenado, percetível sem ver, legível, navegável e operável**.

As três primeiras dizem respeito ao que o documento **é por dentro**: à planta. As quatro seguintes dizem respeito ao que o documento **oferece a quem o usa**: ao edifício, visto por qualquer pessoa e por qualquer caminho.

Nesta secção define-se cada propriedade e mostra-se o que acontece quando ela falta. **Como se garante cada uma em cada aplicação é matéria das secções seguintes**, e é, no fundo, o resto do curso.

### Identificado, Estruturado, Ordenado

**1. Identificado**

> Um documento identificado **diz o que é e em que língua está**, e di-lo de forma que a máquina perceba.

Isto inclui o título do documento (o título real, guardado nas suas propriedades, não apenas o nome do ficheiro nem a linha grande da primeira página) e o idioma do conteúdo, incluindo o das passagens noutra língua.

*O que acontece quando falta:* um utilizador tem sete ficheiros abertos e o leitor de ecrã anuncia-lhe sete vezes "Documento1". Ou: um relatório em português foi produzido a partir de um modelo configurado em inglês, e a voz sintética lê "acessibilidade" com pronúncia inglesa, o que a torna literalmente incompreensível. O texto está todo lá; nenhum dele chega.

**2. Estruturado**

> Um documento estruturado é aquele em que **cada parte diz o que é**: isto é um cabeçalho, isto é um parágrafo, isto é uma lista, isto é uma tabela, isto é uma imagem.

É a construção da planta. Sem estrutura não há navegação, não há relações entre células e cabeçalhos de tabela, não há nada a que a tecnologia de apoio se agarre.

*O que acontece quando falta:* um manual de 60 páginas, com nove capítulos e dezenas de subtítulos, chega ao leitor de ecrã como um bloco contínuo de parágrafos indistintos. Para encontrar o capítulo 7, o utilizador tem duas opções: ouvir tudo desde o início, ou desistir. Uma pessoa que vê resolve o mesmo problema folheando, em cinco segundos.

**3. Ordenado**

> Um documento ordenado **entrega o conteúdo pela ordem que faz sentido**, e não pela ordem em que as coisas foram colocadas na página.

É a propriedade que corresponde à secção anterior: a ordem de leitura programática coincide com a ordem lógica do conteúdo.

*O que acontece quando falta:* a legenda de uma figura é lida antes do parágrafo que a introduz; o número de página aparece a meio de uma frase; a caixa lateral com um aviso importante surge depois da conclusão. Cada elemento está correto por si; o conjunto não se percebe.

### Percetível, Legível, Navegável, Operável

**4. Percetível sem ver**

> Num documento percetível sem ver, **tudo o que a vista capta existe também em texto**.

Toda a informação transmitida por imagem, cor, posição, forma ou destaque visual tem um equivalente textual disponível para quem não recebe essa camada.

*O que acontece quando falta:* um relatório apresenta os resultados do ano num gráfico de barras, sem descrição e sem tabela de apoio. Quem não vê o gráfico não sabe os resultados. E o gráfico era o conteúdo do relatório. Ou, mais simples: a instrução "preencha os campos assinalados a vermelho" não diz nada a quem não distingue o vermelho, nem a quem não vê cor nenhuma.

**5. Legível**

> Um documento legível **pode ser lido por quem vê pouco, distingue mal as cores ou lê com esforço**.

Contraste suficiente, texto de tamanho razoável, espaçamento que respire, tipos de letra sem ornamentos desnecessários, linhas que não atravessam a página inteira e linguagem clara.

*O que acontece quando falta:* uma apresentação com texto cinzento-claro sobre fundo branco, a 14 pontos, projetada numa sala com luz. Não é só a pessoa com baixa visão que não lê: é metade da sala. Esta é a propriedade cuja falha mais gente sente, e a que mais frequentemente se despacha como "questão estética".

**6. Navegável**

> Num documento navegável, **é possível encontrar uma parte sem ler o documento todo**.

Depende diretamente da estrutura, mas não se esgota nela: exige cabeçalhos que reflitam a organização real do conteúdo, índices que funcionem, marcadores em documentos longos e texto de hiperligação que faça sentido sozinho.

*O que acontece quando falta:* um caderno de encargos de 140 páginas em PDF, sem marcadores e sem cabeçalhos, em que a única forma de chegar ao ponto 4.3 é percorrer sequencialmente as 140 páginas. Ou uma página cheia de ligações que dizem todas "clique aqui": lidas fora do contexto — que é como o leitor de ecrã as pode listar — não distinguem nada.

**7. Operável**

> Num documento operável, **tudo o que há a fazer pode ser feito sem rato e sem pressa**.

Aplica-se sobretudo a formulários e a elementos interativos: campos, botões, listas, ligações. Exige que se chegue a tudo com o teclado, por uma ordem previsível, com um foco visível e sem limites de tempo que não se possam alargar.

*O que acontece quando falta:* um formulário em PDF em que a tecla de tabulação salta da primeira linha para o botão de submissão e só depois volta ao meio da página. Quem usa rato não nota. Quem não usa rato preenche o formulário pela ordem errada, ou não o preenche de todo, e, tratando-se de um requerimento, isso significa não exercer um direito.

**As sete propriedades, de relance**

| Propriedade | Numa frase | Falha típica |
|---|---|---|
| Identificado | Diz o que é e em que língua está | Ficheiro sem título e com idioma errado |
| Estruturado | Cada parte diz o que é | Títulos feitos a negrito, sem estilo |
| Ordenado | Entrega o conteúdo pela ordem certa | Caixa acrescentada no fim, lida no fim |
| Percetível sem ver | Tudo o que se vê também existe em texto | Gráfico ou imagem sem descrição |
| Legível | Pode ser lido com pouca visão ou com esforço | Contraste fraco, letra pequena |
| Navegável | Encontra-se uma parte sem ler tudo | PDF longo sem marcadores |
| Operável | Faz-se tudo sem rato e sem pressa | Formulário com ordem de tabulação errada |

## Enquadramento Legal e Normativo

Até aqui falámos do que é justo e do que é eficaz. Falta o que é obrigatório.

Convém arrumar desde já quatro nomes que costumam aparecer misturados:

- **O Decreto-Lei n.º 83/2018** é a **lei portuguesa**. Diz quem tem de cumprir e o que acontece a quem não cumpre.
- **A EN 301 549** é a **norma europeia**. Diz, em detalhe técnico, o que é preciso cumprir.
- **As WCAG** são as **diretrizes internacionais** de acessibilidade de conteúdo, escritas para a web, que a norma europeia adota.
- **O PDF/UA** é a **norma técnica específica do formato PDF**. Diz como um ficheiro PDF tem de ser construído por dentro.

Em cadeia: a lei portuguesa obriga a cumprir a norma europeia, que adota as WCAG; e, para o formato PDF em concreto, o PDF/UA diz como se constrói o ficheiro que cumpre.

### Decreto-Lei n.º 83/2018 e a EN 301 549

**O Decreto-Lei n.º 83/2018, de 19 de outubro**, transpõe para Portugal a Diretiva (UE) 2016/2102, relativa à acessibilidade dos sítios web e das aplicações móveis dos organismos do setor público.

Para este curso, há três pontos a reter.

**Primeiro: os documentos estão abrangidos.** Esta é a parte que costuma surpreender. A lei fala de sítios web e aplicações móveis, e é fácil concluir daí que um PDF publicado nesse sítio não conta. Conta. A exclusão prevista aplica-se apenas a **ficheiros de formatos de escritório publicados antes de 23 de setembro de 2018**, e mesmo esses deixam de estar excluídos se forem necessários para processos administrativos em curso. Na prática: **tudo o que uma entidade pública publique hoje em Word, PowerPoint ou PDF tem de ser acessível**, exatamente como as páginas onde está alojado. 

**Segundo: há deveres visíveis.** Cada entidade abrangida tem de publicar uma **Declaração de Acessibilidade e Usabilidade**, atualizada, indicando o grau de conformidade e as não conformidades conhecidas; tem de disponibilizar um **mecanismo para os utilizadores comunicarem problemas** e de lhes responder; e está sujeita a **monitorização**, hoje conduzida pela **ARTE — Agência para a Reforma Tecnológica do Estado**. Existe ainda o **Selo de Usabilidade e Acessibilidade**, em três níveis — Bronze, Prata e Ouro —, que reconhece publicamente o cumprimento e vai além do mínimo legal.

**Terceiro: o incumprimento tem consequências.** Além da exposição pública que a declaração e a monitorização criam, uma pessoa que seja objeto de tratamento discriminatório por causa da inacessibilidade pode apresentar queixa, ao abrigo do regime da não discriminação em razão da deficiência.

**A EN 301 549** é a norma europeia "Requisitos de acessibilidade para produtos e serviços TIC". É a norma harmonizada a que a lei remete: quem a cumpre presume-se em conformidade.

A sua organização importa para este curso. A norma está dividida em cláusulas por tipo de tecnologia:

- **Cláusula 9 — Web.** Páginas web.
- **Cláusula 10 — Documentos não-web.** É a nossa. Cobre exatamente aquilo de que este curso trata: ficheiros que não são páginas web.
- **Cláusula 11 — Software.** Aplicações, incluindo as que usamos para produzir e ler os documentos.
- **Cláusulas seguintes** — documentação e serviços de apoio, e serviços de comunicação.

A cláusula 10 é, na sua maior parte, uma adaptação dos critérios de sucesso das WCAG de **nível A e AA** ao contexto dos documentos. É aqui que a lei portuguesa e as diretrizes internacionais se encontram: **a base legal, em Portugal, é WCAG 2.1 nível AA, lida para documentos através da cláusula 10.**

O **nível AAA** não faz parte desta base. É boa prática, é recomendável em muitos contextos, e este curso indica-lo-á sempre que for útil, mas apresentá-lo como obrigação legal é incorreto e prejudica a credibilidade de quem o faz.

> **Nota de âmbito.** As referências a critérios de sucesso WCAG dentro das secções deste curso são pontuais e contextuais. A lista consolidada, separada por nível A/AA e nível AAA, está na secção "Conclusão e Boas Práticas", juntamente com os requisitos específicos da cláusula 10 e do PDF/UA.

### WCAG, WCAG2ICT e PDF/UA

**As WCAG** — *Web Content Accessibility Guidelines*, Diretrizes de Acessibilidade para o Conteúdo Web — são o documento de referência internacional em acessibilidade de conteúdo, publicado pelo W3C. Organizam-se em quatro princípios (o conteúdo deve ser percetível, operável, compreensível e robusto), diretrizes dentro de cada princípio, e **critérios de sucesso** verificáveis dentro de cada diretriz, distribuídos por três níveis: A, AA e AAA.

**Porque é que as WCAG precisam de uma leitura adaptada**

As WCAG foram escritas a pensar numa página web aberta num navegador. Essa suposição está no próprio texto dos critérios, e é aí que começa o problema quando as aplicamos a um ficheiro Word ou a um PDF.

Repare-se nas palavras que as WCAG usam constantemente: "página web", "conjunto de páginas web", "processo", "agente do utilizador". Num documento, algumas delas não têm correspondente óbvio:

- **"Página web" não é a página de um documento.** Um documento Word de 40 páginas não são 40 páginas web: é uma unidade só. A "página" do documento é uma consequência da impressão, não uma unidade de navegação.
- **"Conjunto de páginas web" não existe num ficheiro isolado.** Vários critérios das WCAG só fazem sentido em relação a um conjunto. Por exemplo, exigir que a navegação seja consistente entre páginas. Num documento, o equivalente é um *conjunto de documentos*: os quatro ficheiros de um procedimento concursal, os doze fascículos de um manual.
- **Alguns critérios simplesmente não se aplicam.** A exigência de permitir saltar blocos de navegação repetidos, por exemplo, nasce de um problema que os documentos não têm: um documento não repete um menu no topo de cada página.
- **Outros dependem da aplicação, não do documento.** A capacidade de ampliar o texto até 200%, de mudar as cores ou de reorganizar o conteúdo depende do programa que abre o ficheiro. Essa responsabilidade cabe ao software, a cláusula 11 da norma, não a quem escreve.

É para resolver isto que existe o **WCAG2ICT**. É um documento do W3C que funciona como **chave de leitura**: explica, critério a critério, como interpretar as palavras das WCAG quando o que temos à frente não é uma página web mas um documento ou uma aplicação. Onde as WCAG dizem "página web", o WCAG2ICT diz como ler; onde um critério não se aplica, di-lo; onde se aplica com um alcance diferente, explica qual.

Duas notas importantes:

- **O WCAG2ICT não cria requisitos novos e não substitui as WCAG.** É uma tradução, não uma norma paralela.
- **A força jurídica não vem dele.** Vem do Decreto-Lei n.º 83/2018, através da EN 301 549 e da sua cláusula 10, que foi construída precisamente com este tipo de leitura adaptada.

**O PDF/UA**

O **PDF/UA** (*PDF/Universal Accessibility*, norma **ISO 14289**) responde a uma pergunta diferente das WCAG.

> As **WCAG** dizem **o que o utilizador tem de conseguir obter**. O **PDF/UA** diz **como o ficheiro PDF tem de estar construído por dentro** para que isso seja possível.

São complementares, e nenhum substitui o outro. Um PDF pode cumprir formalmente a estrutura exigida pelo PDF/UA e continuar a falhar as WCAG. Por exemplo, se todas as imagens tiverem texto alternativo, mas esse texto for "imagem1". A norma verifica que a planta existe e está bem desenhada; não verifica se descreve o edifício certo.

O PDF/UA especifica, entre muitas outras coisas, que o documento tem de estar etiquetado, que a árvore de etiquetas tem de refletir a ordem lógica de leitura, que o idioma tem de estar declarado, que todo o conteúdo significativo tem de ter equivalente textual e que o conteúdo puramente decorativo tem de estar marcado como tal, precisamente para ser ignorado. Existe também um conjunto de verificações estruturadas associado à norma, o **Protocolo de Matterhorn**, que enumera as formas concretas de a incumprir; algumas dessas verificações podem ser automatizadas, outras exigem sempre um olhar humano.

Na analogia do edifício, é fácil de arrumar: as WCAG dizem que o edifício tem de ser utilizável por qualquer pessoa; o PDF/UA é o regulamento de construção daquele tipo específico de edifício.

## Recomendações para Conteúdo Acessível

As recomendações que se seguem são de método, não de aplicação. Nenhuma delas depende de saber onde fica um botão. As instruções concretas — em Word, em PowerPoint, no Acrobat — são o objeto das secções seguintes.

**Estruturar antes de formatar.** A primeira decisão sobre qualquer parte do conteúdo é *o que é isto* — um título? um item de lista? uma tabela? — e só a segunda é *que aspeto vai ter*. Quem começa pela aparência quase sempre acaba com um documento que parece estruturado e não está.

**Decidir o formato antes de escrever.** Um documento produzido para ser impresso e um documento produzido para ser lido no ecrã têm requisitos diferentes. Decidir isto no fim custa retrabalho. A decisão em si é tratada na secção "Escolher o Formato e Organizar o Trabalho".

**Escrever pensando em quem ouve.** Uma boa prova mental: se alguém lesse este documento em voz alta ao telefone, sem poder descrever o que vê, o ouvinte perceberia? Se a resposta depender de "aqui em baixo", "o quadro à direita" ou "a parte a verde", há trabalho a fazer.

**Não usar a aparência como informação.** Cor, tamanho, posição e forma podem *reforçar* uma informação. Nunca podem ser a única maneira de a obter.

**Tratar a acessibilidade como parte da escrita, não como revisão final.** Um documento estruturado desde a primeira linha custa alguns minutos. O mesmo documento corrigido no fim custa horas — e, se já for um PDF, pode custar mais do que refazê-lo.

**Manter o documento de origem.** O ficheiro Word ou PowerPoint que deu origem ao PDF é o sítio onde as correções se fazem bem. Este princípio organiza boa parte do trabalho prático do curso e é desenvolvido na secção "Escolher o Formato e Organizar o Trabalho".

**Escrever em linguagem clara.** Frases curtas, uma ideia por parágrafo, siglas explicadas na primeira ocorrência, títulos que digam o que vem a seguir. Beneficia quem tem dificuldades de leitura, quem lê numa segunda língua, quem está com pressa — ou seja, quase toda a gente.

**Verificar com ferramentas e com pessoas.** Os verificadores automáticos são úteis e obrigatórios no fluxo de trabalho. Detetam a ausência de etiquetas; não detetam etiquetas erradas. Nenhum deles sabe se o texto alternativo descreve a imagem certa.

### Erros Comuns

**1. Confundir formatação com estrutura.**
Aumentar a letra e pôr a negrito não cria um cabeçalho. É o erro mais frequente e o que mais consequências tem, porque destrói ao mesmo tempo a estrutura e a navegação. *Em vez disso:* usar os mecanismos de estrutura da aplicação, mesmo quando o resultado visual seria idêntico.

**2. Achar que "tem texto, logo é acessível".**
Um documento pode ter todo o texto selecionável e pesquisável e continuar a ser, do ponto de vista da tecnologia de apoio, um bloco indistinto. Texto disponível não é o mesmo que texto estruturado.

**3. Achar que o PDF é acessível por ser PDF — ou converter para PDF "por segurança".**
Converter um documento mal construído para PDF não corrige nada: transporta os problemas e acrescenta-lhes outros. O PDF herda a qualidade da origem. *Em vez disso:* tratar o documento de origem primeiro; a conversão é tratada na secção "Do Word e do PowerPoint para PDF".

**4. Confiar no verificador automático como prova de conformidade.**
"O verificador não deu erros" é uma frase que não significa "o documento é acessível". Os verificadores testam o que é testável por máquina, que é uma fração do problema. Cada secção deste curso tem uma parte dedicada ao que o verificador respetivo *não* deteta.

**5. Deixar a acessibilidade para o fim.**
A acessibilidade acrescentada no último dia, antes da publicação, é cara, incompleta e frustrante. Feita durante a escrita, é quase invisível no esforço.

**6. Corrigir o PDF e não a origem.**
Corrigir o PDF publicado, sem tocar no ficheiro Word que lhe deu origem, garante que o próximo PDF gerado a partir dele terá exatamente os mesmos defeitos. É trabalho que se repete todas as vezes.

**7. Digitalizar em vez de exportar.**
Imprimir um documento e voltar a digitalizá-lo — para assinar, para carimbar, por hábito — transforma um ficheiro potencialmente acessível numa fotografia. É uma perda que raramente se recupera na totalidade.

**8. Tratar a acessibilidade como assunto de uma minoria pequena.**
As mesmas propriedades que tornam um documento utilizável por um leitor de ecrã tornam-no pesquisável, convertível, legível no telemóvel e reutilizável. A estrutura não serve só a acessibilidade: serve toda a gente que precisa de fazer alguma coisa com o documento além de olhar para ele.

**9. Confundir níveis de conformidade.**
Anunciar conformidade AAA porque se cumpriram alguns critérios desse nível, ou desvalorizar um critério AA por parecer difícil, são duas faces do mesmo erro. *Em vez disso:* a base é A e AA, porque é o que a lei exige; o AAA é boa prática, e apresenta-se como tal.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Um documento é um edifício; as etiquetas são a planta.** Quem vê, vê o edifício. A tecnologia de apoio lê a planta. Sem planta, resta uma fotografia.
2. **Um leitor de ecrã não lê a página: lê uma estrutura.** Recebe, para cada elemento, o que ele é, o que contém e como se relaciona com os outros.
3. **O que não está na planta não existe.** Um título que só é grande e negrito não é um título.
4. **Formatação é aparência; estrutura é informação.** Podem coincidir no ecrã e divergir por completo dentro do ficheiro.
5. **Existem duas ordens: a visual e a programática.** Só a segunda chega à tecnologia de apoio, e ela não se corrige sozinha.
6. **Um documento acessível é identificado, estruturado, ordenado, percetível sem ver, legível, navegável e operável.** As três primeiras propriedades descrevem a planta; as quatro seguintes, a experiência de quem usa o edifício.
7. **Os documentos publicados por entidades públicas estão abrangidos pelo Decreto-Lei n.º 83/2018.** A exclusão aplica-se apenas a ficheiros anteriores a 23 de setembro de 2018 que não sejam necessários a processos em curso.
8. **A base legal é WCAG 2.1 nível AA, lida através da cláusula 10 da EN 301 549.** O nível AAA é boa prática acima do exigido.
9. **O WCAG2ICT é a chave de leitura das WCAG para o que não é web.** Não cria requisitos novos: explica como ler os que existem.
10. **As WCAG dizem o que o utilizador tem de obter; o PDF/UA diz como o ficheiro tem de estar construído.** Cumprir um não garante cumprir o outro.

### Exercícios Práticos

**Exercício 1 — Ouvir um documento**

*Objetivo:* experimentar o que a tecnologia de apoio recebe.

Escolha um documento de trabalho seu, com pelo menos cinco páginas. Ative o leitor de ecrã disponível no seu sistema — o NVDA em Windows, o VoiceOver em macOS — e ouça os primeiros três minutos **sem olhar para o ecrã**.

Registe: o que ouviu quando o documento abriu; se conseguiu perceber onde estava; se percebeu quando um capítulo novo começou; o que aconteceu ao chegar a uma imagem ou a uma tabela.

*Nota:* esperar frustração é normal, e faz parte do exercício. Nesta fase não se corrige nada; observa-se.

**Exercício 2 — As duas ordens**

*Objetivo:* separar ordem visual de ordem de leitura.

Pegue num diapositivo ou numa página com desenho complexo — várias caixas, imagens ao lado de texto, um destaque lateral. Numa folha, desenhe o esquema da página e numere os blocos **pela ordem em que o olho os lê**. Numa segunda folha, numere os mesmos blocos **pela ordem em que se lembra de os ter criado**.

Compare as duas numerações. Se forem diferentes, escreva uma frase a descrever o que um leitor de ecrã ouviria, e se essa sequência ainda faria sentido.

**Exercício 3 — Auditoria pelas sete propriedades**

*Objetivo:* fixar o vocabulário do curso aplicando-o.

Escolha um documento publicado pela sua organização e preencha esta grelha, com uma frase de justificação por linha:

| Propriedade | Cumpre? | Porquê |
|---|---|---|
| Identificado | | |
| Estruturado | | |
| Ordenado | | |
| Percetível sem ver | | |
| Legível | | |
| Navegável | | |
| Operável | | |

Depois, ordene as falhas encontradas por **impacto em quem usa o documento** — não por facilidade de correção. Guarde esta grelha: vai voltar a ela no fim do curso.

**Exercício 4 — Explicar a alguém**

*Objetivo:* consolidar a analogia central e treinar o argumento.

Em cinco frases, e sem usar as palavras "etiqueta", "semântico" ou "estrutura", explique a um colega que não trabalha em acessibilidade por que razão um título feito a negrito não é um título.

Depois, escreva a resposta que daria a esta objeção, que vai ouvir: *"Mas fica exatamente igual no ecrã — e ninguém aqui usa leitor de ecrã."*

**Exercício 5 — Preparar o resto do curso**

*Objetivo:* transformar o conceito em plano.

Escolha três documentos que a sua organização publique com regularidade — um em Word, um em PowerPoint e um em PDF. Não os corrija: identifique, para cada um, **quais das sete propriedades estão em causa**. À medida que avançar nas secções seguintes, volte a esta lista e anote qual o procedimento que resolve cada falha.

