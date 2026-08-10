# PDF: Verificação e Correção

## Introdução

### O Problema Que Esta Secção Resolve

Até aqui, o curso tratou de documentos que ainda estávamos a construir. Preparámos a origem em Word ou em PowerPoint e exportámos com cuidado, para que a planta do edifício viajasse junto com o edifício.

Esta secção trata de uma situação diferente e muito mais frequente no dia a dia: **o PDF já existe e não fomos nós que o fizemos**.

Chegam-nos PDFs de todo o lado. Um parecer jurídico enviado por um gabinete externo. Um formulário que está no sítio da entidade desde 2015 e ninguém sabe quem o produziu. Um relatório digitalizado a partir de papel porque tinha assinaturas. Um mapa de resultados gerado automaticamente por uma aplicação de gestão. Em todos estes casos, a pergunta não é "como faço bem?", mas sim **"o que é que este ficheiro tem lá dentro, e o que consigo eu reparar?"**.

Voltando à analogia do curso: até agora fomos arquitetos. A partir daqui somos peritos que chegam a um edifício já construído, com uma lanterna e uma prancheta, para responder a duas perguntas:

1. **Existe planta?** E, se existe, corresponde ao edifício?
2. **Vale a pena corrigir a planta aqui, ou é melhor voltar ao atelier onde o projeto original ainda está guardado?**

A segunda pergunta é a mais importante de toda esta secção, e é por ela que vamos começar.

Ao longo da secção vamos usar o **Adobe Acrobat Pro**. O Acrobat Reader — a versão gratuita — permite *ler* um PDF, mas não permite ver nem editar as etiquetas. Todos os procedimentos aqui descritos exigem a versão Pro.

> **Nota sobre os caminhos de menu.** O Acrobat mudou de interface nos últimos anos e algumas ferramentas mudaram de nome e de sítio. Onde há mais do que uma designação em circulação, indicam-se ambas.

---

## Antes de Começar

### Corrigir o PDF ou Voltar à Origem?

Esta é a decisão que determina se o trabalho das próximas horas vai durar anos ou vai durar até à próxima revisão do documento.

Corrigir a acessibilidade diretamente num PDF é **trabalho que fica preso naquele ficheiro**. Não sobe para o Word que lhe deu origem. Se alguém alterar um parágrafo no documento de origem e voltar a exportar, o PDF novo substitui o PDF corrigido — e todas as etiquetas que arranjámos, todos os textos alternativos que escrevemos, toda a ordem de leitura que endireitámos desaparecem de uma só vez.

**A analogia:** corrigir o PDF sem corrigir a origem é escrever a lápis na fotocópia da planta, e não no original que está no atelier. Da próxima vez que pedirem uma cópia, ela sai outra vez errada.

#### A árvore de decisão

Faça estas três perguntas, por esta ordem. Pare na primeira que der uma resposta clara.

**Pergunta 1 — O documento de origem existe e está acessível?**

- **Não** (perdeu-se, é de terceiros, é uma digitalização, foi gerado por uma aplicação) → **Corrigir no PDF.** Não há alternativa. Avance para os procedimentos R1 a R7.
- **Sim** → passe à pergunta 2.

**Pergunta 2 — O documento vai voltar a ser alterado e reexportado?**

- **Sim** (é um regulamento que se revê, um formulário que se atualiza, um relatório anual com o mesmo modelo, um documento em consulta pública) → **Corrigir na origem e voltar a exportar.** Corrigir o PDF seria deitar o trabalho fora na próxima versão.
- **Não** (é uma ata assinada, uma edição fechada, um documento histórico) → passe à pergunta 3.

**Pergunta 3 — O problema vem da origem ou da conversão?**

- **Vem da origem** (não há cabeçalhos, as imagens não têm texto alternativo, as tabelas não têm linha de cabeçalho) → **Corrigir na origem**, mesmo num documento final. É mais rápido corrigir cinco estilos no Word do que reconstruir cinquenta etiquetas no Acrobat, e o resultado é melhor.
- **É específico da conversão** (o texto alternativo passou mas ficou truncado, a numeração das listas duplicou, um cabeçalho e rodapé foram etiquetados como texto, a ordem de leitura partiu-se numa página com caixas de texto) → **Corrigir no PDF.** São problemas que não existem no ficheiro de origem e que voltariam a aparecer se exportássemos de novo.

#### Resumo da decisão

| Situação | Onde corrigir |
|---|---|
| A origem não existe ou não é nossa | No PDF |
| O documento vai ser atualizado | Na origem |
| Documento final, problema estrutural de fundo | Na origem, e reexportar |
| Documento final, problema criado pela conversão | No PDF |
| PDF digitalizado a partir de papel | No PDF (ver R7) |
| Volume grande de documentos com o mesmo modelo | Na origem — corrigir o modelo resolve todos |

#### Exemplo: duas equipas, duas decisões

**Equipa A.** Recebe uma reclamação sobre o *Regulamento de Apoio ao Arrendamento*, publicado em PDF. O ficheiro Word existe, na pasta partilhada. O regulamento é revisto todos os anos.
→ Correm o verificador para saber *o que* está mal, mas corrigem tudo no Word: aplicam estilos de cabeçalho, marcam a linha de cabeçalho das tabelas, escrevem os textos alternativos. Depois exportam de novo.
**O que funciona bem:** o trabalho fica na origem. A revisão do ano seguinte parte de um documento já correto e o problema não regressa. Corrigiram o documento uma vez, não todos os anos.

**Equipa B.** Recebe a mesma reclamação sobre um *Parecer Técnico n.º 14/2019*, elaborado por um consultor externo que já não trabalha com a entidade. Não existe ficheiro de origem. O parecer é um documento fechado, que nunca será alterado.
→ Corrigem diretamente no PDF: etiquetas, ordem de leitura, texto alternativo, título e idioma.
**O que funciona bem:** não perderam tempo a procurar uma origem que não existe, nem a reconstruir o documento em Word só para o voltar a exportar. Como o documento é final, a correção no PDF dura para sempre.

**A armadilha a evitar:** a Equipa A poderia ter sido tentada a corrigir no PDF, porque "é só este ficheiro que está publicado". Um ano depois, o PDF novo teria exatamente os mesmos defeitos, e alguém teria de fazer tudo outra vez — provavelmente sem saber que já tinha sido feito.

#### Antes de tocar no ficheiro

Três hábitos que poupam problemas:

1. **Trabalhar sobre uma cópia.** Guarde o original intacto, com um nome como `parecer-14-2019_ORIGINAL.pdf`. As alterações no painel de etiquetas nem sempre se desfazem bem com *Anular*.
2. **Guardar com frequência e com versões.** `_v1`, `_v2`, `_final`. Uma sessão longa de edição de etiquetas que corre mal e não tem ponto de retorno é uma tarde perdida.
3. **Confirmar que o documento não está protegido.** `Ficheiro > Propriedades > Segurança`. Se as permissões bloquearem a alteração do conteúdo, não vai conseguir editar etiquetas. Este caso é tratado em "O Que Não é Possível Recuperar".

---

## Procedimentos

### R1. O Verificador de Acessibilidade do Acrobat

#### O que se pretende

Obter um diagnóstico inicial: um relatório que diga o que está mal, onde está, e o que precisa de ser visto por uma pessoa. O verificador é o exame que se faz antes de decidir o tratamento — não é o tratamento.

#### Passos na aplicação

1. Abrir o PDF no **Acrobat Pro**.
2. Abrir a ferramenta de acessibilidade: `Ferramentas > Acessibilidade` (nas versões mais recentes, `Todas as ferramentas > Preparar para acessibilidade`).
3. Escolher **Verificação de acessibilidade** (ou **Verificar acessibilidade**).
4. Na janela de opções, manter as categorias todas selecionadas e escolher **Iniciar verificação**.
5. O resultado aparece no painel lateral **Verificador de acessibilidade**, organizado por categorias.

#### Como ler o relatório

Cada regra aparece com um de quatro estados:

| Estado | O que significa | O que fazer |
|---|---|---|
| **Aprovado** | O teste automático passou | Nada — mas ver a ressalva abaixo |
| **Reprovado** | O teste automático falhou | Corrigir |
| **Verificação manual necessária** | A máquina não consegue decidir | Verificar com os olhos e com o teclado |
| **Ignorado** | Alguém marcou a regra como não aplicável | Confirmar que a decisão foi consciente |

Clicar com o botão direito sobre uma regra dá acesso a **Explicar** (abre a documentação da regra) e, em várias regras, a **Corrigir**, que resolve o problema automaticamente. As correções automáticas são fiáveis em questões mecânicas — título, idioma, sinalizador de permissão — e não são fiáveis em questões de significado, como a etiquetagem automática de conteúdo.

#### As três regras que exigem sempre uma pessoa

O verificador marca-as invariavelmente como **verificação manual necessária**, e não é por preguiça do programa: são as três coisas que uma máquina não consegue avaliar.

- **Ordem lógica de leitura** — a máquina vê que existe uma ordem; não sabe se ela faz sentido. Tratado em R3.
- **Contraste de cor** — o Acrobat não mede contraste no conteúdo da página.
- **Cintilação do ecrã** — exige observação.

#### O que o verificador *não* deteta

Este é o ponto crítico. Um relatório inteiramente verde significa apenas que **as etiquetas existem e estão bem formadas**. Não significa que estejam certas.

O verificador não deteta:

- **Um cabeçalho etiquetado como parágrafo.** Se o documento não tiver cabeçalho nenhum, a regra "Cabeçalhos" pode nem ser avaliada. Um documento de 60 páginas sem um único `<H1>` pode passar sem uma única falha.
- **Níveis de cabeçalho saltados** de forma que quebre a hierarquia — nem sempre, e nunca de forma fiável.
- **Texto alternativo errado.** `alt="imagem1.jpg"` é texto alternativo. Passa.
- **Uma tabela de dados etiquetada como tabela mas sem cabeçalhos reais**, ou com cabeçalhos sem âmbito definido.
- **Uma tabela de disposição** que devia ter sido tratada como decoração.
- **Ordem de leitura absurda.** Duas colunas lidas em ziguezague passam sem queixa.
- **Ligações cujo texto é "clique aqui"**, repetido doze vezes.
- **Legibilidade.** Corpo de letra 7, texto em maiúsculas, ausência de contraste.

**A analogia:** o verificador confirma que existe uma planta e que ela está desenhada nas convenções certas. Não confirma que as divisões desenhadas correspondam às divisões do edifício. Para isso é preciso percorrer o edifício com a planta na mão — que é exatamente o que R2 e R3 fazem.

#### Guardar o relatório

`Botão direito sobre "Relatório de acessibilidade" > Guardar como` produz um ficheiro HTML. Vale a pena guardá-lo antes e depois da correção: serve de prova documental do trabalho feito, o que é útil quando há uma queixa ou uma auditoria.

---

### R2. Ler e Corrigir o Painel de Etiquetas

Este é o procedimento mais exigente do curso. Vale a pena fazê-lo devagar. Comece por perceber o que está a ver, antes de tentar alterar seja o que for.

#### Primeiro: o que é o painel de etiquetas

Todo o curso trabalha com a ideia de que o documento é um edifício e as etiquetas são a planta. Até agora, essa planta esteve invisível: no Word, aplicamos o estilo "Título 1" e confiamos que alguma coisa acontece por baixo.

**O painel de etiquetas do Acrobat é a planta tornada visível — e editável.**

É uma árvore. Cada ramo é um elemento do documento. O nome do ramo diz *o que aquilo é*: um cabeçalho de nível 1, um parágrafo, uma lista, uma figura, uma célula de tabela. A posição do ramo na árvore diz *onde aquilo está* na estrutura e *em que ordem* será lido.

É esta árvore, e só ela, que um leitor de ecrã percorre. O que estiver na árvore existe. O que não estiver, não existe — por muito visível que seja no ecrã.

#### Abrir o painel

`Ver > Mostrar/Ocultar > Painéis de navegação > Etiquetas` 

Nas versões mais recentes, o painel pode estar disponível a partir de `Todas as ferramentas > Preparar para acessibilidade`, na barra lateral.

Se o painel disser **"Sem etiquetas disponíveis"**, o documento não tem planta nenhuma. É o caso tratado em "O Que Não é Possível Recuperar".

#### Ler a árvore

Uma árvore de etiquetas bem formada tem este aspeto:

```
Etiquetas
└── <Document>
    ├── <H1>  Relatório de Atividades 2024
    ├── <P>   Este relatório apresenta a atividade...
    ├── <H2>  1. Enquadramento
    ├── <P>   Durante o ano de 2024, o serviço...
    ├── <L>
    │   ├── <LI>
    │   │   ├── <Lbl>   •
    │   │   └── <LBody> Atendimento presencial
    │   └── <LI>
    │       ├── <Lbl>   •
    │       └── <LBody> Atendimento telefónico
    ├── <Figure>  [texto alternativo: "Evolução do atendimento..."]
    └── <H2>  2. Resultados
```

**O que funciona bem neste exemplo:** cada elemento tem a etiqueta que corresponde à sua função. Há um `<H1>` único, seguido de `<H2>` na ordem certa — um leitor de ecrã consegue apresentar um índice navegável do documento. A lista é uma verdadeira lista (`<L>` com `<LI>` dentro), pelo que é anunciada como "lista com 2 itens". A figura tem texto alternativo. A ordem da árvore corresponde à ordem em que se lê o documento.

Agora o mesmo documento, mal etiquetado:

```
Etiquetas
└── <Document>
    ├── <P>  Relatório de Atividades 2024
    ├── <P>  Este relatório apresenta a atividade...
    ├── <P>  1. Enquadramento
    ├── <P>  Durante o ano de 2024, o serviço...
    ├── <P>  • Atendimento presencial
    ├── <P>  • Atendimento telefónico
    ├── <Figure>  [sem texto alternativo]
    └── <P>  2. Resultados
```

**O que funciona mal:** está tudo etiquetado como parágrafo. Visualmente o documento pode ser idêntico ao anterior — os títulos estão a 18 pontos e a negrito, os pontos da lista têm um símbolo. Mas na planta não há títulos nem listas. Consequências concretas: o leitor de ecrã não oferece navegação por cabeçalhos, portanto quem não vê tem de ouvir o documento inteiro do princípio para chegar aos resultados; não é anunciado quantos itens tem a lista; e a figura é silenciada ou anunciada apenas como "gráfico", sem qualquer informação. É o incumprimento clássico do critério **1.3.1 Informação e Relações**.

#### Ligar cada etiqueta ao conteúdo que representa

Antes de alterar uma etiqueta é preciso ter a certeza de que se está a alterar a etiqueta certa. Há duas formas de fazer a ponte entre a árvore e a página:

**Da árvore para a página.** No menu de opções do painel de Etiquetas, ativar **Realçar conteúdo**. A partir daí, clicar numa etiqueta desenha uma caixa à volta do conteúdo correspondente na página. É a forma mais rápida de perceber o que é cada ramo.

**Da página para a árvore.** Selecionar o texto ou o objeto na página com a ferramenta de seleção e, no menu de opções do painel, escolher **Localizar etiqueta a partir da seleção**. A árvore expande-se e destaca a etiqueta correspondente. É indispensável em documentos longos.

**Hábito recomendado:** trabalhar sempre com **Realçar conteúdo** ativo. Sem ele, editar etiquetas é mexer numa planta sem olhar para o edifício.

#### Alterar o tipo de uma etiqueta

Este é o gesto mais frequente: transformar um `<P>` que na verdade é um título num `<H2>`.

1. Clicar na etiqueta a corrigir.
2. `Botão direito > Propriedades` (ou `Propriedades` no menu de opções do painel).
3. No separador **Etiqueta**, abrir a lista **Tipo** e escolher o tipo correto.
4. Confirmar com **Fechar** ou **OK**.

O campo **Título** que aparece nesta janela é apenas um nome informativo; não substitui o tipo.

#### Mover, criar e eliminar etiquetas

- **Mover:** arrastar a etiqueta para a nova posição na árvore. A linha que aparece durante o arrasto indica se o elemento vai ficar *ao lado* ou *dentro* do elemento de destino — é uma distinção importante, e é fácil enganar-se. Verifique sempre depois de largar.
- **Criar:** selecionar o conteúdo na página e usar **Criar etiqueta a partir da seleção**, no menu de opções do painel. Serve para etiquetar conteúdo que ficou de fora da árvore.
- **Eliminar:** `Botão direito > Eliminar etiqueta`. Atenção: eliminar uma etiqueta que tem outras dentro elimina o ramo inteiro. O conteúdo não desaparece da página, mas deixa de estar na planta — ou seja, deixa de existir para a tecnologia de apoio.

#### Marcar conteúdo decorativo como artefacto

Nem tudo o que está na página deve ser lido. Uma linha divisória, uma faixa de cor, um logótipo repetido em todas as páginas, o número de página no rodapé — se forem lidos, só acrescentam ruído.

O nome técnico para "conteúdo que existe visualmente mas não faz parte do documento" é **artefacto**. Um artefacto está no edifício, mas não consta da planta, de propósito.

Para marcar: selecionar a etiqueta, `Botão direito > Alterar etiqueta para artefacto`.

**Cuidado com o excesso.** Marcar como artefacto o que na verdade tem informação — um selo com a data de aprovação, um gráfico que é o único sítio onde os números aparecem — apaga essa informação para quem não vê, e apaga-a de forma silenciosa: nenhum verificador se queixa. Uma vez tornado artefacto, o conteúdo torna-se invisível para todos os testes automáticos.

#### As etiquetas que precisa de conhecer

| Etiqueta | O que representa |
|---|---|
| `<Document>` | Raiz do documento |
| `<H1>` a `<H6>` | Cabeçalhos, por nível |
| `<P>` | Parágrafo |
| `<L>` | Lista |
| `<LI>` | Item de lista |
| `<Lbl>` | Marca ou número do item |
| `<LBody>` | Texto do item |
| `<Table>` | Tabela |
| `<TR>` | Linha de tabela |
| `<TH>` | Célula de cabeçalho |
| `<TD>` | Célula de dados |
| `<Caption>` | Legenda de tabela ou figura |
| `<Figure>` | Imagem ou gráfico |
| `<Link>` | Ligação |
| `<Span>` | Trecho de texto dentro de outro elemento |

Não é preciso decorar a lista toda. Na prática, mais de 90 % das correções envolvem `<H1>`–`<H6>`, `<P>`, `<L>`/`<LI>`, `<Figure>` e `<Table>`/`<TH>`/`<TD>`.

#### Método: por onde começar

Numa árvore com centenas de ramos, é fácil perder-se. Uma ordem de trabalho que funciona:

1. **Primeiro, os cabeçalhos.** Percorrer o documento de cima a baixo e corrigir todos os títulos. É a correção que produz maior benefício por minuto investido, porque devolve a navegação.
2. **Depois, as listas.** Agrupar sequências de `<P>` que são realmente listas.
3. **Depois, as figuras.** Texto alternativo ou artefacto (ver R4).
4. **Depois, as tabelas** (ver R5).
5. **Por fim, a ordem geral** (ver R3).

Guardar entre cada etapa. Voltar a correr o verificador entre cada etapa.

---

### R3. Corrigir a Ordem de Leitura

#### O que se pretende

Garantir que o documento é lido pela ordem em que faz sentido, e não pela ordem em que os objetos foram desenhados na página.

#### O ponto que causa mais confusão

O Acrobat tem **duas coisas diferentes com nomes parecidos**, e trocá-las é fonte de erros persistentes.

| | **Painel de Etiquetas** | **Painel "Ordem"** |
|---|---|---|
| O que mostra | A árvore de estrutura | A sequência dos blocos de conteúdo na página |
| Quem segue esta ordem | Os leitores de ecrã | O reajuste de texto e algumas funções de leitura do Acrobat |
| É a ordem que importa? | **Sim** | Não, quando existem etiquetas |

**Regra prática:** num PDF etiquetado, a ordem que a tecnologia de apoio segue é a **ordem das etiquetas**. É na árvore de etiquetas que a ordem de leitura se corrige de forma fiável. O painel "Ordem" e a ferramenta **Corrigir ordem de leitura** (antes chamada *Ordem de leitura*) são úteis sobretudo para *criar* etiquetas em conteúdo que não as tem, marcando regiões à mão — não para afinar uma ordem já existente.

#### Como detetar o problema

**Teste rápido 1 — Reajustar.** `Ver > Zoom > Reajustar` (`Ctrl` + `4`). O documento passa a uma coluna única. Se aparecer texto trocado, blocos fora de sítio ou legendas no meio de parágrafos, há um problema de ordem. É um indicador rápido, mas não é prova: o reajuste nem sempre coincide com o que o leitor de ecrã faz.

**Teste rápido 2 — Percorrer a árvore.** Com **Realçar conteúdo** ativo, clicar sucessivamente nas etiquetas de cima para baixo e observar as caixas a saltar na página. Se as caixas saltarem numa sequência que uma pessoa não seguiria a ler, a ordem está errada.

**Teste fiável — Leitor de ecrã.** NVDA ou VoiceOver, com o PDF aberto, a ler o documento do princípio ao fim. É o único teste que reproduz a experiência real.

#### Os casos clássicos

**Duas colunas lidas em ziguezague.** O documento tem duas colunas. As etiquetas foram criadas linha a linha, atravessando as duas colunas. O resultado é uma frase da coluna esquerda seguida de uma frase da coluna direita, alternadamente.
→ *Correção:* reordenar as etiquetas na árvore para que toda a coluna esquerda venha antes de toda a coluna direita.

**A legenda antes da imagem, ou muito longe dela.** A `<Caption>` ficou noutro sítio da árvore.
→ *Correção:* arrastar a etiqueta para junto da `<Figure>` a que pertence.

**A caixa de destaque no meio de um parágrafo.** Uma caixa lateral com uma citação foi inserida na árvore no ponto da página onde está desenhada, partindo o texto principal a meio.
→ *Correção:* mover a caixa para depois do parágrafo completo.

**O cabeçalho e o rodapé lidos em todas as páginas.** O logótipo e o número de página estão etiquetados como texto e repetem-se 40 vezes.
→ *Correção:* marcar como artefactos (ver R2).

#### Exemplo antes/depois

Uma brochura de duas colunas, mal etiquetada:

```
<P>  A candidatura decorre entre
<P>  contactar o serviço através do
<P>  1 e 30 de setembro. Podem
<P>  telefone 210 000 000 ou
<P>  candidatar-se todos os
<P>  presencialmente, mediante
```

**O que funciona mal:** cada `<P>` é uma linha visual, e as linhas alternam entre a coluna esquerda e a direita. Quem ouve isto recebe duas frases entrelaçadas e não consegue reconstruir nenhuma delas. Repare que o verificador não assinala qualquer erro: as etiquetas existem, estão bem formadas e a regra "Ordem lógica de leitura" aparece apenas como *verificação manual necessária*.

Depois de corrigido:

```
<P>  A candidatura decorre entre 1 e 30 de setembro. Podem candidatar-se todos os...
<P>  Para mais informações, contactar o serviço através do telefone 210 000 000 ou presencialmente, mediante...
```

**O que funciona bem:** cada parágrafo é uma unidade de sentido completa, e os parágrafos seguem-se pela ordem em que uma pessoa os leria. A propriedade "ordem de leitura correta" fica satisfeita — e note-se que o resultado visual da página não mudou nada.

---

### R4. Texto Alternativo

#### O que se pretende

Que cada imagem com informação tenha uma descrição em texto, e que cada imagem decorativa esteja fora da planta.

Os princípios de *escrita* de bom texto alternativo — descrever a função e não a aparência, não começar com "imagem de", não repetir a legenda — foram tratados na secção "Documentos Word", no procedimento W4. Aqui trata-se apenas de saber onde é que esse texto se põe num PDF.

#### Passos na aplicação

**Via painel de etiquetas** (o método mais preciso):

1. Localizar a etiqueta `<Figure>` na árvore.
2. `Botão direito > Propriedades`.
3. No separador **Etiqueta**, escrever no campo **Texto alternativo**.
4. Fechar.

**Via ferramenta dedicada** (mais rápido quando há muitas imagens):

`Ferramentas > Acessibilidade > Definir texto alternativo` (ou `Todas as ferramentas > Preparar para acessibilidade > Definir texto alternativo`). O Acrobat percorre todas as figuras uma a uma, com setas para avançar e recuar, e oferece uma caixa **Decorativa** para as imagens que não devem ser lidas.

#### Imagens decorativas

Marcar como decorativa nesta janela, ou converter a etiqueta `<Figure>` em artefacto no painel de etiquetas (ver R2). O efeito é o mesmo: a imagem sai da planta e o leitor de ecrã passa por ela em silêncio.

#### Duas armadilhas específicas do PDF

**Texto dentro da imagem.** Um cartaz, um infográfico ou um organograma exportados como imagem única. Todo o texto que lá está é invisível para a tecnologia de apoio, não é pesquisável e desfaz-se ao ampliar. Um texto alternativo curto não resolve: não é razoável resumir um infográfico em duas linhas.
→ *O que fazer:* colocar a informação completa em texto real, algures no documento, e usar o texto alternativo para remeter para ela — por exemplo, "Infográfico com a evolução dos pedidos por trimestre. Os dados estão na tabela seguinte." É também o que o critério **1.4.5 Imagens de Texto** aponta.

**Texto alternativo herdado e truncado.** Alguns fluxos de exportação cortam o texto alternativo ou trazem o nome do ficheiro em vez da descrição. Vale a pena confirmar, imagem a imagem, que o que passou é o que devia passar.

---

### R5. Tabelas

#### O que se pretende

Que cada célula de dados fique ligada aos seus cabeçalhos, para que um leitor de ecrã possa anunciar, numa célula qualquer, a que linha e a que coluna ela pertence.

**A analogia:** uma tabela sem cabeçalhos marcados é como uma folha de coordenadas sem os nomes das ruas. Quem vê a grelha percebe onde está. Quem só ouve "3.412" não faz ideia se é o número de atendimentos de janeiro em Lisboa ou o de dezembro no Porto.

#### Como está a tabela por dentro

Uma tabela bem etiquetada tem esta estrutura:

```
<Table>
├── <TR>
│   ├── <TH>  Distrito
│   ├── <TH>  2023
│   └── <TH>  2024
├── <TR>
│   ├── <TH>  Lisboa
│   ├── <TD>  3 412
│   └── <TD>  3 890
└── <TR>
    ├── <TH>  Porto
    ├── <TD>  2 105
    └── <TD>  2 340
```

**O que funciona bem:** a primeira linha tem `<TH>` (cabeçalhos de coluna) e a primeira coluna tem `<TH>` (cabeçalhos de linha). Cada número está numa `<TD>` que se cruza com dois cabeçalhos. O leitor de ecrã pode anunciar "Lisboa, 2024, 3 890".

O mesmo, mal etiquetado:

```
<Table>
├── <TR>
│   ├── <TD>  Distrito
│   ├── <TD>  2023
│   └── <TD>  2024
├── <TR>
│   ├── <TD>  Lisboa
│   ...
```

**O que funciona mal:** está tudo em `<TD>`. Não há cabeçalhos. O leitor de ecrã anuncia apenas o conteúdo da célula, sem contexto, e a navegação por células perde todo o valor. Para quem vê, a tabela pode continuar com a primeira linha a negrito e com fundo cinzento — mas o negrito é aparência, não é estrutura.

#### O Editor de Tabelas

É a ferramenta que torna este trabalho suportável.

1. Ativar `Ferramentas > Acessibilidade > Corrigir ordem de leitura` (ou `Preparar para acessibilidade > Corrigir ordem de leitura`).
2. Clicar sobre a tabela na página para a selecionar.
3. Escolher **Editor de tabelas** na janela da ferramenta.
4. A tabela passa a mostrar cada célula com um contorno colorido e uma etiqueta: as células de cabeçalho aparecem numa cor e as de dados noutra.
5. `Botão direito sobre uma célula > Propriedades da célula da tabela`, onde se define:
   - **Tipo:** Célula de cabeçalho ou Célula de dados
   - **Âmbito:** Linha, Coluna, Ambos ou Nenhum
   - **Intervalo de linhas / Intervalo de colunas:** para células que ocupam mais do que uma
   - **ID** e **Células de cabeçalho associadas:** para tabelas complexas
6. É possível selecionar várias células de uma vez — por exemplo, toda a primeira linha — e alterá-las em conjunto.

#### Definir o âmbito

O âmbito diz *sobre o que manda* um cabeçalho:

- Cabeçalhos na primeira linha → âmbito **Coluna**
- Cabeçalhos na primeira coluna → âmbito **Linha**
- A célula do canto superior esquerdo, quando serve as duas → âmbito **Ambos**

Sem âmbito definido, o cabeçalho existe mas não se sabe a que células se aplica — e algumas tecnologias de apoio tratam-no como se não existisse.

#### Tabelas complexas

Quando há cabeçalhos em vários níveis — dois anos, cada um com trimestres — o âmbito não chega. É preciso dar um **ID** a cada célula de cabeçalho e, em cada célula de dados, indicar os IDs dos cabeçalhos que lhe correspondem, no campo **Células de cabeçalho associadas**.

É trabalho moroso. Antes de o iniciar, vale sempre a pena perguntar se a tabela não pode ser dividida em duas ou três tabelas simples — mais fácil de etiquetar, mais fácil de ler para toda a gente, e sem perda de informação.

#### Tabelas usadas para dispor conteúdo

Uma tabela sem cabeçalhos, usada apenas para alinhar dois blocos lado a lado, é uma tabela de disposição. Não tem dados; tem arrumação.

Etiquetada como `<Table>`, faz o leitor de ecrã anunciar "tabela com 2 linhas e 3 colunas" a propósito de coisa nenhuma. O ideal é que o conteúdo saia da estrutura de tabela e fique como sequência de parágrafos.

**Seja realista:** desmontar uma tabela de disposição no painel de etiquetas de um PDF é trabalho pesado e propenso a partir a ordem de leitura. Se a origem existir, é um argumento forte para voltar a ela — corrigir a disposição no Word e reexportar demora uma fração do tempo.

---

### R6. Título, Idioma e Metadados

#### O que se pretende

Que o documento esteja **identificado** e que o texto seja pronunciado na língua certa. São as correções mais rápidas de todo o procedimento e das que mais se notam.

#### O título do documento

Quando um leitor de ecrã abre um PDF, anuncia o título. Se não houver título definido, anuncia o nome do ficheiro. A diferença entre ouvir *"Regulamento de Apoio ao Arrendamento Jovem"* e ouvir *"REG_ARREND_v7_final_revACL_2.pdf"* é toda a diferença.

**São precisos dois passos, e o segundo é quase sempre esquecido:**

1. **Definir o título:** `Ficheiro > Propriedades > Descrição` e preencher o campo **Título** com o título real do documento, tal como aparece na primeira página.
2. **Mandar mostrar o título:** `Ficheiro > Propriedades > Vista inicial > Opções de janela > Mostrar:` escolher **Título do documento** em vez de **Nome do ficheiro**.

Sem o segundo passo, o título existe mas continua a não ser usado. O verificador do Acrobat deteta este caso e permite corrigi-lo com `Botão direito > Corrigir` sobre a regra "Título". Corresponde ao critério **2.4.2 Título da Página**, aplicado a documentos através da WCAG2ICT.

#### O idioma

`Ficheiro > Propriedades > Avançadas > Opções de leitura > Idioma:` escolher **Português**.

Sem esta definição, um leitor de ecrã configurado em inglês lê texto português com pronúncia inglesa — o resultado varia entre difícil e incompreensível. É o critério **3.1.1 Idioma da Página**.

**Trechos noutra língua.** Uma citação em inglês, um título de obra em francês, o nome de um programa europeu. Marcam-se individualmente: selecionar a etiqueta correspondente no painel de etiquetas, `Botão direito > Propriedades > separador Etiqueta > campo Idioma`. Se o trecho estiver no meio de um parágrafo, pode ser preciso criar primeiro uma etiqueta `<Span>` só para ele.

Vale a pena marcar palavras estrangeiras que já entraram no português corrente? Normalmente não — *software*, *email*, *design* são lidos de forma aceitável. Uma frase inteira noutra língua, essa, deve ser marcada.

#### Confirmar que o PDF tem etiquetas

`Ficheiro > Propriedades > Descrição > Avançadas`, linha **PDF com etiquetas: Sim / Não**.

É a verificação de dez segundos que se faz antes de qualquer outra coisa. Um "Não" aqui muda completamente o plano de trabalho.

#### O sinalizador de permissão de acessibilidade

Algumas definições de segurança bloqueiam a extração de texto e, com isso, impedem os leitores de ecrã de aceder ao conteúdo. O verificador assinala isto na regra "Sinalizador de permissão de acessibilidade". Quando o documento não tem palavra-passe de permissões, resolve-se em `Ficheiro > Propriedades > Segurança`, retirando a restrição. Quando tem, é preciso quem a saiba — ver "O Que Não é Possível Recuperar".

---

### R7. PDF Digitalizado e OCR

#### Como reconhecer um PDF digitalizado

Três testes de cinco segundos:

1. **Tentar selecionar texto.** Se o cursor desenha um retângulo à volta da página inteira em vez de selecionar palavras, é uma imagem.
2. **Pesquisar uma palavra visível** com `Ctrl` + `F`. Se não encontra nada, não há texto.
3. **Ampliar muito.** Se as letras ficam desfocadas e serrilhadas, são pixéis, não são letras.

Um PDF digitalizado é uma fotografia do edifício. Não tem planta, não tem texto, não tem nada além de pontos coloridos.

#### O que o OCR faz — e o que não faz

O **OCR** (reconhecimento ótico de carateres) analisa a imagem e produz texto por baixo dela.

**Faz:** o texto passa a ser selecionável, pesquisável, copiável e legível por um leitor de ecrã.

**Não faz:** não cria estrutura. Depois do OCR, o documento tem texto, mas não tem cabeçalhos, nem listas, nem tabelas, nem ordem de leitura fiável.

**A analogia:** o OCR transcreve as palavras que estão escritas nas paredes do edifício. Não desenha a planta. Continuam a faltar as divisões, as portas e a indicação de por onde se entra. Depois do OCR há sempre trabalho de etiquetagem — R2 a R5, do princípio.

#### Passos na aplicação

1. `Ferramentas > Digitalizar e OCR` (ou `Todas as ferramentas > Digitalizar e OCR`).
2. **Reconhecer texto > Neste ficheiro**.
3. Nas definições, **escolher o idioma Português**. É o passo mais importante e o mais esquecido: com o idioma errado, o reconhecimento troca acentos e cedilhas sistematicamente, e o leitor de ecrã lê palavras que não existem.
4. Escolher o tipo de saída **Texto pesquisável de imagem**, que mantém a imagem original visível e coloca o texto reconhecido por baixo.
5. Executar e, **obrigatoriamente, rever o resultado**. O OCR erra sobretudo em números, nomes próprios, siglas e tabelas — exatamente onde os erros têm mais consequências.

#### O que estraga o OCR

- **Resolução baixa.** Abaixo de 300 ppp, a taxa de erro sobe muito.
- **Páginas tortas.** Uma inclinação de dois ou três graus já degrada o reconhecimento.
- **Fotocópias de fotocópias.** Contornos esborratados, fundo acinzentado, letras coladas.
- **Manuscrito.** Não é reconhecido de forma utilizável.
- **Carimbos e assinaturas sobre o texto.** As palavras por baixo perdem-se.
- **Colunas, caixas e tabelas.** Frequentemente misturadas numa ordem sem sentido.

#### Antes de fazer OCR, faça esta pergunta

**O documento existe em formato eletrónico nalgum sítio?**

Vale sempre a pena procurar. Uma digitalização de um documento que existe em Word é a pior versão possível de um documento que já existe numa versão boa. Cinco minutos a procurar na pasta partilhada, ou um telefonema ao serviço que o produziu, poupam horas de OCR e de correções — e o resultado final é incomparavelmente melhor.

E se o papel for a única fonte mas houver acesso ao documento físico: **voltar a digitalizar bem** — direito, a 300 ppp, em modo texto — é quase sempre mais rápido do que corrigir à mão os erros de uma digitalização má.

---

## Limites

### O Que Não é Possível Recuperar

Esta parte da secção existe para evitar um desperdício muito comum: dias de trabalho gastos num ficheiro que nunca ia ficar bem.

Há três situações em que a resposta tecnicamente correta e profissionalmente honesta é **este documento não se corrige; refaz-se**.

#### 1. O PDF digitalizado de má qualidade

**Como se reconhece:** o OCR devolve texto com erros a cada duas ou três palavras. Números trocados. Acentos aleatórios. Tabelas transformadas em cadeias de números sem ordem. Zonas inteiras de página não reconhecidas.

**Porque não se recupera:** o texto errado é pior do que a ausência de texto. Um documento sem texto pelo menos é reconhecidamente inacessível; um documento com texto errado parece acessível — passa nos verificadores, tem etiquetas, tem palavras — e transmite informação falsa a quem depende dele. Num regulamento, num aviso de concurso ou numa tabela de valores, isto não é um defeito de acessibilidade: é um erro de conteúdo.

**O que fazer:** procurar o original eletrónico. Se não existir, voltar a digitalizar em boas condições. Se nem isso for possível, **transcrever o documento** — para Word, com estrutura — e gerar um PDF novo. Numa dezena de páginas, transcrever é frequentemente mais rápido do que corrigir OCR.

#### 2. O PDF impresso sem estrutura nenhuma

**Como se reconhece:** `Ficheiro > Propriedades > Descrição > Avançadas` indica "PDF com etiquetas: **Não**". O painel de etiquetas diz "Sem etiquetas disponíveis". O texto é selecionável — portanto não é uma digitalização — mas não há planta nenhuma.

É o resultado típico de imprimir para PDF, ou de uma exportação a partir de uma aplicação de gestão que produz páginas para impressão.

**Porque é enganador:** o Acrobat oferece **Etiquetar documento automaticamente** (`Ferramentas > Acessibilidade > Adicionar etiquetas ao documento`), e a tentação é usá-lo e dar o assunto por resolvido. Mas a etiquetagem automática é uma **adivinhação a partir da aparência**: o Acrobat olha para tamanhos de letra, posições e espaçamentos e tenta inferir o que é cada coisa. Acerta razoavelmente num documento simples de uma coluna. Erra muito em qualquer coisa mais complicada — e produz um resultado que *parece* estruturado, cheio de etiquetas plausíveis e erradas, mais difícil de auditar do que um documento sem etiquetas nenhumas.

**O que fazer:** se a origem existir, voltar a ela e exportar corretamente — é o caminho tratado na secção "Do Word e do PowerPoint para PDF". Se não existir, a etiquetagem automática pode servir de ponto de partida, mas tem de ser **integralmente revista**, etiqueta a etiqueta. Num documento longo e complexo, reconstruir a partir de uma transcrição para Word pode ser mais rápido e dá certamente melhor resultado.

**Um caso particular a assinalar:** documentos gerados em massa por sistemas informáticos — faturas, certidões, comprovativos, listagens. Aqui, corrigir cada ficheiro à mão não é uma solução: são milhares. **A correção tem de ser feita no sistema que os gera**, junto de quem o mantém. É uma conversa com a área de sistemas de informação, não uma tarefa de edição de PDF.

#### 3. O documento protegido

**Como se reconhece:** a barra de título mostra "(PROTEGIDO)". Ferramentas aparecem desativadas. `Ficheiro > Propriedades > Segurança` mostra restrições em "Alteração do documento", "Extração de conteúdo" ou "Extração de conteúdo para acessibilidade".

**Porque não se recupera:** as permissões que bloqueiam a extração de conteúdo bloqueiam os leitores de ecrã. E as que bloqueiam a alteração do documento impedem a edição das etiquetas. O documento está simultaneamente inacessível e incorrigível.

**O que fazer:** contactar quem aplicou a proteção e pedir uma versão sem restrições, ou a palavra-passe de permissões. Não há atalho técnico legítimo: contornar a proteção de um documento que não é nosso é problemático do ponto de vista legal e, sobretudo, desnecessário — quem tem a palavra-passe é quase sempre um colega a dois telefonemas de distância.

**A prevenir para o futuro:** as permissões restritivas quase nunca protegem o que as pessoas julgam estar a proteger. Um PDF sem restrições é copiável na mesma; a restrição impede sobretudo que as pessoas com deficiência o consigam ler. Se a proteção for mesmo necessária, deve pelo menos manter ativa a permissão de extração de conteúdo para acessibilidade.

#### Como comunicar a decisão de refazer

Dizer "este documento não se corrige" não costuma ser bem recebido. Ajuda apresentar a decisão em termos de esforço comparado, e não de impossibilidade:

> "Corrigir este PDF exige cerca de três dias, e o resultado ficará com erros de reconhecimento no meio dos valores. Transcrever o documento e voltar a gerá-lo a partir do Word exige cerca de um dia, deixa-nos com uma origem que podemos reutilizar, e o resultado fica correto."

É um argumento de custo, e resolve a conversa quase sempre.

---

## Recomendações para Conteúdo Acessível

**Decidir antes de corrigir.** Cinco minutos com a árvore de decisão de "Corrigir o PDF ou Voltar à Origem?" poupam dias. É a recomendação mais importante desta secção.

**Correr o verificador primeiro, mas não confiar nele por completo.** Serve para saber por onde começar, não para saber quando parar.

**Corrigir por camadas, não por página.** Todos os cabeçalhos primeiro, depois as listas, depois as figuras, depois as tabelas. Andar às voltas página a página é mais lento e produz resultados menos consistentes.

**Trabalhar sempre com "Realçar conteúdo" ativo.** Editar a planta sem olhar para o edifício é a forma mais eficiente de o piorar.

**Guardar cópias numeradas.** Antes de mexer em etiquetas, sempre. As alterações estruturais nem sempre se anulam bem.

**Testar com um leitor de ecrã antes de dar o trabalho por concluído.** Percorrer o documento pelos cabeçalhos e ouvir uma ou duas páginas seguidas apanha, em cinco minutos, problemas que nenhum verificador assinala.

**Registar o que foi feito.** Uma nota curta junto ao ficheiro — data, o que foi corrigido, o que ficou por corrigir e porquê — evita que outra pessoa refaça o mesmo trabalho daqui a um ano.

**Corrigir a montante sempre que possível.** Se o PDF veio de um modelo, de um fornecedor ou de um sistema, corrigir o modelo, informar o fornecedor ou falar com a área de sistemas resolve todos os documentos futuros. Corrigir o PDF resolve um.

**Publicar o que já está melhor.** Um documento parcialmente corrigido — com título, idioma e cabeçalhos — é substancialmente mais utilizável do que o original. Não é preciso ter tudo perfeito para publicar a melhoria.

### Erros Comuns

**1. Corrigir o PDF quando a origem existe e vai ser atualizada.**
O erro central da secção. Todo o trabalho se perde na próxima exportação, e provavelmente ninguém saberá que ele chegou a ser feito. *Em vez disso:* aplicar a árvore de decisão antes de abrir o Acrobat.

**2. Usar a etiquetagem automática e dar o trabalho por concluído.**
Produz uma planta plausível e errada, que passa nos verificadores e engana toda a gente, incluindo quem a produziu. *Em vez disso:* tratar a etiquetagem automática como rascunho e rever ramo a ramo.

**3. Tomar o relatório verde do verificador como prova de acessibilidade.**
Um documento inteiro etiquetado como `<P>` pode não gerar uma única falha. *Em vez disso:* completar sempre com verificação humana da estrutura e da ordem de leitura.

**4. Confundir o painel "Ordem" com o painel de Etiquetas.**
Arrumar blocos no painel "Ordem" e concluir que a ordem de leitura ficou corrigida. *Em vez disso:* corrigir a ordem na árvore de etiquetas, que é a que a tecnologia de apoio segue.

**5. Fazer OCR com o idioma errado.**
Reconhecimento em inglês de um texto português produz erros sistemáticos em todas as palavras acentuadas. *Em vez disso:* definir o idioma antes de executar, e rever o resultado.

**6. Achar que o OCR resolve a acessibilidade de um documento digitalizado.**
O OCR dá texto; não dá estrutura. *Em vez disso:* contar sempre com a etapa de etiquetagem a seguir ao OCR.

**7. Definir o título e esquecer a Vista inicial.**
O título fica preenchido nas propriedades e o leitor de ecrã continua a anunciar o nome do ficheiro. *Em vez disso:* os dois passos, sempre juntos.

**8. Marcar como artefacto conteúdo que tem informação.**
Apaga informação de forma silenciosa e irrecuperável para quem não vê. *Em vez disso:* na dúvida, perguntar se a informação existe noutro sítio do documento em texto. Se não existir, não é decoração.

**9. Etiquetar tabelas de dados sem definir o âmbito dos cabeçalhos.**
As `<TH>` existem mas não se sabe a que células se aplicam. *Em vez disso:* definir sempre o âmbito no Editor de Tabelas.

**10. Insistir num ficheiro irrecuperável.**
Três dias a lutar com um OCR que erra em cada terceira palavra é tempo que produziria um documento novo e correto. *Em vez disso:* reconhecer o limite cedo e apresentar a decisão como comparação de custos.

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **A primeira pergunta não é "como corrijo?", é "onde corrijo?".** Se a origem existe e o documento vai ser atualizado, corrige-se na origem. A correção feita no PDF perde-se na versão seguinte.
2. **A correção direta no PDF justifica-se em três casos:** a origem não existe, o documento é final, ou o problema foi criado pela conversão.
3. **O verificador do Acrobat diz o que testar, não diz se o documento está acessível.** Confirma que as etiquetas existem e estão bem formadas; não confirma que estejam certas.
4. **O painel de etiquetas é a planta do edifício tornada visível e editável.** É a única representação fiável da estrutura de um PDF, e é onde a maior parte das correções acontece.
5. **A ordem de leitura corrige-se na árvore de etiquetas**, não no painel "Ordem".
6. **Cabeçalhos primeiro.** É a correção que devolve mais utilidade por minuto investido, porque devolve a navegação.
7. **Numa tabela, cabeçalhos sem âmbito são cabeçalhos a meio caminho.** `<TH>` e âmbito andam sempre juntos.
8. **Título e idioma são as duas correções mais rápidas e das mais notadas** — e o título exige dois passos, não um.
9. **O OCR dá texto, não dá estrutura.** Depois do OCR, o trabalho de etiquetagem começa do princípio.
10. **Há documentos que não se corrigem.** Digitalizações de má qualidade, PDFs sem estrutura nenhuma e documentos protegidos. Reconhecê-lo cedo, e apresentar a alternativa em termos de custo, faz parte do trabalho profissional.

### Exercícios Práticos

#### Exercício 1 — Aplicar a árvore de decisão

Para cada situação, decida: **corrigir no PDF** ou **corrigir na origem**? Justifique numa frase.

- **A.** Aviso de abertura de candidaturas, publicado ontem. O Word existe. As candidaturas abrem em setembro e o aviso vai ser republicado com novas datas.
- **B.** Ata de reunião de 2017, assinada e digitalizada. Não há ficheiro eletrónico.
- **C.** Relatório de contas de 2024, exportado do Word. As imagens perderam o texto alternativo na conversão; tudo o resto está bem. O relatório está fechado.
- **D.** Trezentas certidões geradas automaticamente por uma aplicação. Nenhuma tem etiquetas.
- **E.** Manual de procedimentos de 40 páginas. O Word existe mas não tem um único estilo de cabeçalho aplicado. O manual é revisto de dois em dois anos.

<details>
<summary>Soluções</summary>

- **A. Na origem.** Vai ser republicado; qualquer correção no PDF desaparece na próxima versão.
- **B. No PDF.** Não há origem e o documento é final. Começar por R7 (OCR), depois etiquetar.
- **C. No PDF.** Documento final e problema específico da conversão — não existe no ficheiro Word, logo reexportar não o resolveria.
- **D. Nem uma coisa nem outra: no sistema que as gera.** Corrigir trezentos ficheiros à mão não é uma solução; a correção é junto da área de sistemas de informação.
- **E. Na origem.** O problema é estrutural e vem da origem. Aplicar estilos no Word demora minutos; reconstruir 40 páginas de etiquetas no Acrobat demora dias. E a revisão seguinte parte de um documento já correto.

</details>

#### Exercício 2 — Diagnóstico em cinco minutos

Escolha um PDF publicado no sítio da sua entidade e responda:

1. Tem etiquetas? (`Propriedades > Descrição > Avançadas`)
2. O texto é selecionável?
3. Que título anuncia o leitor de ecrã? (`Propriedades > Vista inicial`)
4. Qual é o idioma definido?
5. O verificador do Acrobat encontra quantas falhas, em que categorias?
6. Abrindo o painel de etiquetas: quantos `<H1>` e `<H2>` existem?

Escreva o diagnóstico em cinco linhas e, na sexta, a decisão: corrigir no PDF ou na origem.

#### Exercício 3 — Ler a planta

Abra o painel de etiquetas de um PDF exportado a partir de um Word bem estruturado e percorra a árvore de cima a baixo com **Realçar conteúdo** ativo. Identifique:

- Onde estão os cabeçalhos e se os níveis seguem uma sequência coerente
- Como foram etiquetadas as listas
- O que aconteceu ao cabeçalho e ao rodapé da página
- Se existe alguma etiqueta cujo conteúdo realçado o surpreenda

#### Exercício 4 — Corrigir cabeçalhos

Sobre uma cópia de um PDF em que os títulos estão etiquetados como `<P>`:

1. Localize todos os títulos.
2. Altere o tipo de cada etiqueta para o nível correto.
3. Volte a correr o verificador.
4. Teste com um leitor de ecrã, navegando apenas por cabeçalhos.

Registe quanto tempo demorou e compare com o tempo que demoraria aplicar estilos no documento de origem. Este exercício é a demonstração prática do ponto pedagógico central da secção.

#### Exercício 5 — Uma tabela do princípio ao fim

Sobre um PDF com uma tabela de dados sem cabeçalhos marcados:

1. Abra o Editor de Tabelas.
2. Converta em `<TH>` as células que são cabeçalhos.
3. Defina o âmbito de cada uma.
4. Teste com um leitor de ecrã, navegando célula a célula, e confirme que os cabeçalhos são anunciados.

#### Exercício 6 — Reconhecer o limite

Analise um PDF digitalizado de má qualidade (uma fotocópia antiga serve). Faça OCR em português e conte os erros de reconhecimento numa página.

Depois, escreva um parágrafo curto, dirigido a uma chefia, com a recomendação sobre o que fazer com o documento — incluindo uma estimativa de esforço para as duas alternativas: corrigir ou refazer.

---

