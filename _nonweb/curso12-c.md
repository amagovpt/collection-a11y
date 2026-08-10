---
title: Apresentações PowerPoint
layout: default
nav_order: 3
---
# Apresentações PowerPoint

## Introdução

### O Que Distingue o PowerPoint

Quem chega ao PowerPoint depois de dominar o Word tem tendência a pensar que se trata do mesmo trabalho, com diapositivos em vez de páginas. Não é. Há três diferenças de fundo, e todas elas afetam a acessibilidade.

**Primeira: não há fluxo de texto.** Num documento Word, o conteúdo corre como um rio, do princípio ao fim, e a ordem de leitura é a ordem em que o texto aparece. Num diapositivo, não há rio. Há uma tela em branco onde se pousam caixas em qualquer sítio. A posição de uma caixa no ecrã não diz nada sobre a posição dessa caixa na ordem de leitura.

**Segunda: cada apresentação tem dois públicos.** Há quem esteja na sala a ver a projeção e a ouvir o orador. E há quem receba o ficheiro depois — porque faltou, porque quer rever, porque não consegue acompanhar a projeção. Estes dois públicos têm necessidades diferentes e o mesmo ficheiro tem de servir os dois. Um diapositivo que só faz sentido com o orador a explicá-lo falha o segundo público por inteiro.

**Terceira: a estrutura não está dentro do diapositivo — vem de fora dele.** No Word, a estrutura cria-se aplicando estilos ao texto que já lá está. No PowerPoint, a estrutura vem do **esquema de diapositivo** que se escolheu antes de escrever seja o que for. Escolher mal no início custa mais tarde muito trabalho manual.

> **Analogia.** No Word, construímos o edifício e desenhamos a planta com o mesmo gesto. No PowerPoint, cada diapositivo é uma sala vazia onde podemos pousar mobília em qualquer sítio. A planta não regista onde a mobília ficou: regista a ordem por que ela entrou na sala. Quem vê, vê a sala arrumada. Quem lê a planta, percorre as coisas pela ordem de chegada — que pode não ter nada a ver com a arrumação.

Daqui resulta o problema mais característico deste formato: **uma apresentação pode estar visualmente impecável e completamente desordenada para quem usa tecnologia de apoio**, sem que nada no ecrã o denuncie. No Word, um documento mal estruturado costuma ter mau aspeto. No PowerPoint, não. É por isso que os dois primeiros procedimentos desta secção — `PP1` e `PP3` — valem mais do que todos os outros juntos.

### Das Propriedades às Funcionalidades do PowerPoint

As sete propriedades de um documento acessível foram definidas na secção "Fundamentos da Acessibilidade de Documentos". A tabela seguinte mostra onde cada uma se obtém no PowerPoint e em que procedimento desta secção é tratada.

| Propriedade | No PowerPoint obtém-se com | Procedimento |
|---|---|---|
| Identificado | Título nas propriedades do ficheiro; idioma da apresentação | Igual ao Word (`W6`); ver "Recomendações para Conteúdo Acessível" |
| Estruturado | Esquemas de diapositivo com marcadores de posição; títulos de diapositivo; listas dos marcadores | `PP1`, `PP2` |
| Com ordem de leitura correta | Painel de ordem de leitura; ordem de criação dos objetos | `PP1`, `PP3` |
| Percetível sem ver | Texto alternativo em imagens, gráficos e SmartArt; tabelas com cabeçalho; legendas em vídeo | `PP4`, `PP5`, `PP7` |
| Legível | Tamanho de letra, contraste e espaçamento adequados à projeção | `PP9` |
| Navegável | Títulos de diapositivo únicos e descritivos; texto de ligação com sentido | `PP2`, `PP6` |
| Operável | Controlo sobre animações, transições e reprodução de multimédia | `PP7` |

Duas leituras desta tabela merecem atenção.

A primeira: **`PP1` alimenta três propriedades ao mesmo tempo**. Escolher um esquema de diapositivo em vez de desenhar caixas à mão dá estrutura, dá ordem de leitura e dá o título que serve de navegação — de uma só vez, sem trabalho adicional.

A segunda: **a propriedade "identificado" não tem procedimento próprio nesta secção**. O título do ficheiro e o idioma definem-se no PowerPoint exatamente como no Word, pelos mesmos caminhos e com as mesmas consequências. Em vez de repetir o procedimento `W6`, esta secção retoma-o na lista de recomendações, com a única diferença que existe: no PowerPoint é ainda mais frequente o idioma ficar errado, porque as caixas de texto herdam o idioma do momento em que foram criadas e uma apresentação costuma ser feita de pedaços reaproveitados de outras.

---

## Procedimentos

Cada procedimento segue a mesma estrutura da secção "Documentos Word": o que se pretende, os passos no PowerPoint, um exemplo antes e depois, e a explicação do que muda para quem usa tecnologia de apoio.

Os caminhos de menu referem-se ao Microsoft PowerPoint do Microsoft 365, em português europeu. Alguns nomes de comandos variam entre versões e canais de atualização.

---

### PP1. Esquemas de Diapositivo

**O que se pretende**

Uma apresentação **estruturada** e com **ordem de leitura correta**, sem trabalho manual. Este é o procedimento que evita a maior parte dos problemas em vez de os corrigir.

Depende disto quem usa leitor de ecrã — que recebe o conteúdo do diapositivo pela ordem em que os objetos existem no ficheiro — e também quem reaproveita a apresentação mais tarde, porque um diapositivo construído com esquema mantém a estrutura quando é copiado, redimensionado ou reformatado.

**Passos no PowerPoint**

1. **Criar um diapositivo novo com esquema:** **Base → Diapositivos → Novo Diapositivo** (a seta por baixo do botão, não o botão) → escolher o esquema na galeria. Se carregar apenas no botão, o PowerPoint repete o esquema do diapositivo anterior, o que é bom quando o esquema está certo e mau quando não está.
2. **Mudar o esquema de um diapositivo já feito:** selecionar o diapositivo → **Base → Diapositivos → Esquema** → escolher o esquema pretendido.
3. **Repor os marcadores de posição nas posições do esquema:** **Base → Diapositivos → Repor**. Útil quando alguém arrastou e redimensionou tudo à mão.
4. **Criar ou corrigir esquemas:** **Ver → Modelo Global de Diapositivos**. No painel da esquerda, o primeiro item é o modelo global; os que estão indentados por baixo são os esquemas. Para acrescentar um marcador de posição a um esquema: **Modelo Global de Diapositivos → Inserir Marcador de Posição**. Sair com **Fechar Vista de Modelo Global**.
5. **Diagnosticar diapositivos construídos à mão:** **Base → Organizar → Painel de Seleção**. Os marcadores de posição aparecem com nomes próprios ("Título 1", "Marcador de Posição de Conteúdo 2"). As caixas desenhadas à mão aparecem como "CaixaDeTexto 4", "Retângulo 7". Um diapositivo em que só há caixas de texto e retângulos é um diapositivo sem estrutura nenhuma.

**Antes e depois**

*Antes.* Um diapositivo sobre resultados de auditoria, construído a partir do esquema "Em Branco". O autor desenhou uma caixa de texto no topo com "Resultados", outra à esquerda com o texto, e colou um gráfico à direita. No Painel de Seleção:

```
Gráfico 5
CaixaDeTexto 4
CaixaDeTexto 3
```

Não há título. Não há marcadores de posição. Não há nada que distinga a caixa do topo da caixa do meio: para o ficheiro, são duas caixas de texto iguais, uma por acaso mais acima do que a outra.

*Depois.* O mesmo conteúdo, num diapositivo criado com o esquema "Duas Partes de Conteúdo". No Painel de Seleção:

```
Marcador de Posição de Conteúdo 3
Marcador de Posição de Conteúdo 2
Título 1
```

**O que funciona melhor no segundo exemplo:** o texto do topo deixou de ser "uma caixa que está mais acima" e passou a ser o título do diapositivo, com tudo o que isso implica (ver `PP2`). O texto e o gráfico ficaram em marcadores de posição, que já trazem tamanho de letra, espaçamento e — sobretudo — ordem definidos no esquema. E o resultado visual é praticamente o mesmo: o esforço não aumentou, apenas mudou de sítio, do desenho manual para a escolha inicial.

**Porque funciona**

Um marcador de posição não é uma caixa de texto com outro nome. É uma caixa que **tem um papel declarado** no ficheiro: este é o título, este é o conteúdo principal. O leitor de ecrã usa esse papel para anunciar o diapositivo de forma útil — "Diapositivo 12 de 40, Resultados da auditoria" — em vez de despejar caixas anónimas.

E, porque os esquemas predefinidos foram construídos com os marcadores de posição pela ordem certa, um diapositivo feito com esquema **já nasce com a ordem de leitura correta**. É por isso que a construção manual a partir de caixas vazias é a principal fonte de problemas de acessibilidade neste formato: não é que seja proibida, é que obriga a fazer à mão, diapositivo a diapositivo, um trabalho que o esquema faria de graça.

Este procedimento serve o critério **1.3.1 Informação e Relações**: a diferença entre "título" e "conteúdo", que é óbvia para quem vê, tem de existir também de forma programática.

---

### PP2. Títulos de Diapositivo

**O que se pretende**

Uma apresentação **navegável**. O título de diapositivo é, no PowerPoint, o que o cabeçalho é no Word (`W1`): o ponto de referência que permite saltar, situar-se e voltar atrás.

Depende disto quem usa leitor de ecrã e precisa de percorrer uma apresentação de sessenta diapositivos sem a ler toda; quem usa a apresentação como material de consulta e procura o diapositivo certo; e quem tem dificuldades de atenção ou de memória de trabalho e precisa de saber, a cada momento, onde está.

Há uma diferença importante em relação ao Word: **no PowerPoint não há hierarquia**. Um diapositivo tem um título e só um, e não existem níveis. A estrutura do conjunto é uma lista plana de títulos, não uma árvore. Isso torna a qualidade de cada título individual ainda mais importante, porque não há níveis superiores que deem contexto.

**Passos no PowerPoint**

1. **Escrever o título no marcador de posição próprio**, que vem com o esquema (`PP1`). Não desenhar uma caixa de texto e pôr lá o título.
2. **Ver todos os títulos de uma vez:** **Ver → Vista de Destaques**. Esta vista mostra apenas o texto que está em marcadores de posição. Os diapositivos sem título aparecem em branco — é a forma mais rápida de os encontrar.
3. **Acrescentar um título a um diapositivo que não tem:** separador **Acessibilidade → Título do Diapositivo → Adicionar Título do Diapositivo**.
4. **Acrescentar um título que não deve aparecer no ecrã:** no mesmo menu, **Acessibilidade → Título do Diapositivo → Adicionar Título Oculto do Diapositivo**.
5. **Ocultar um título que já existe e está visível:** **Base → Organizar → Painel de Seleção** → carregar no ícone do olho à direita de "Título 1". O título deixa de ser visível na projeção e continua a existir no ficheiro.

**Antes e depois**

*Antes.* Uma apresentação de formação com 40 diapositivos. Doze deles chamam-se "Resultados". Cinco chamam-se "Exemplo". Sete diapositivos — os que têm uma fotografia a ocupar o ecrã inteiro — não têm título nenhum, porque o autor achou que um título por cima da fotografia ficava mal. Na Vista de Destaques:

```
1.  Acessibilidade Digital
2.  Índice
3.  Resultados
4.  Resultados
5.
6.  Exemplo
7.  Resultados
```

Quem navega por títulos ouve "Resultados" doze vezes e sete diapositivos sem nome. A navegação existe formalmente e não serve para nada.

*Depois.* Os mesmos 40 diapositivos, com títulos únicos e informativos, e com títulos ocultos nos diapositivos de fotografia:

```
1.  Acessibilidade Digital nos Serviços Públicos
2.  O que vamos ver nesta sessão
3.  Resultados 2024: taxa global de conformidade
4.  Resultados 2024: os cinco erros mais frequentes
5.  [oculto] Fotografia da sessão de formação em Évora
6.  Exemplo: um formulário sem rótulos
7.  Resultados 2025: o que melhorou
```

**O que funciona melhor no segundo exemplo:** cada título distingue o diapositivo de todos os outros, o que é o requisito mínimo para a navegação servir de alguma coisa; os títulos dizem o que o diapositivo conclui, não apenas de que assunto trata ("os cinco erros mais frequentes" em vez de "Resultados"); e o diapositivo 5 mantém o ecrã limpo, com a fotografia a ocupar tudo, sem deixar de ser identificável para quem não a vê. O título oculto não é um truque nem uma solução de recurso: é a funcionalidade que existe precisamente para este caso.

**Porque funciona**

Os leitores de ecrã anunciam o título ao entrar em cada diapositivo e oferecem listas de diapositivos por título. Um título ausente obriga a pessoa a ler o diapositivo inteiro para saber se é aquele que procura; um título repetido é pior, porque dá a ilusão de informação sem a dar.

O título oculto resolve um conflito real. Há diapositivos em que um título visível estraga a composição — uma fotografia a toda a largura, um diapositivo de transição, uma citação isolada. A resposta errada é apagar o título. A resposta certa é mantê-lo no ficheiro e escondê-lo do ecrã: o edifício fica como o arquiteto quer, a planta continua completa.

Este procedimento serve o critério **2.4.6 Cabeçalhos e Etiquetas**: os títulos têm de descrever o conteúdo, não apenas existir.

---

### PP3. Ordem de Leitura

**O que se pretende**

Uma apresentação com **ordem de leitura correta**. É aqui que se concentra o problema mais específico deste formato.

Depende disto quem usa leitor de ecrã e quem navega o diapositivo com teclado, porque ambos recebem os objetos por uma ordem que não controlam e que pode não ter nenhuma relação com aquilo que está no ecrã.

A regra que é preciso interiorizar é simples e contraintuitiva:

> **A ordem de leitura de um diapositivo é a ordem por que os objetos foram criados, não a ordem por que aparecem no ecrã.**

Se desenhar primeiro a caixa da direita e depois a da esquerda, a tecnologia de apoio lê primeiro a direita. Se colar uma imagem no fim, ela é lida no fim, mesmo que esteja no topo do diapositivo. Se duplicar um diapositivo e trocar as caixas de sítio, a ordem de leitura **não** acompanha a mudança visual.

E daqui decorre o corolário prático que justifica o `PP1`: os esquemas de diapositivo predefinidos já trazem os marcadores de posição pela ordem certa. **A construção manual de diapositivos a partir de caixas vazias é, de longe, a principal fonte de erros de ordem de leitura.** Quem usa esquemas raramente tem este problema; quem desenha caixas tem-no quase sempre.

**Passos no PowerPoint**

1. **Abrir o painel de ordem de leitura:** **Rever → Verificar Acessibilidade** (abre o separador **Acessibilidade**) → **Ordem de Leitura**. Este painel lista os objetos **de cima para baixo, pela ordem em que são lidos**.
2. **Reordenar:** arrastar os itens no painel, ou usar as setas para subir e descer.
3. **Retirar um objeto da ordem de leitura:** desmarcar a caixa ao lado do objeto no painel. Equivale a marcá-lo como decorativo (`PP4`). Usar apenas em formas puramente decorativas.
4. **Alternativa sem o painel de ordem de leitura:** **Base → Organizar → Painel de Seleção**. **Atenção — a ordem está invertida.** O Painel de Seleção lista os objetos pela sobreposição visual, com o objeto da frente no topo. A ordem de leitura é **de baixo para cima**. Esta inversão é a causa de mais correções erradas do que qualquer outra coisa nesta secção.
5. **Teste rápido, sem painel nenhum:** carregar numa zona vazia do diapositivo e premir **Tab** repetidamente. O foco percorre os objetos pela ordem de leitura. Se saltar do sítio errado para o sítio errado, está encontrado o problema.

**Antes e depois**

*Antes.* Um diapositivo intitulado "Antes e Depois da Intervenção", com duas colunas. O autor fez primeiro a coluna da direita — porque era a que tinha o texto já escrito — e só depois a da esquerda. No fim, acrescentou o título.

Ordem de leitura efetiva:

```
1. "Depois" (subtítulo da coluna direita)
2. Texto da coluna direita
3. "Antes" (subtítulo da coluna esquerda)
4. Texto da coluna esquerda
5. "Antes e Depois da Intervenção" (título)
```

Quem usa leitor de ecrã ouve o resultado antes do problema, ouve as duas colunas trocadas e só no fim descobre o assunto do diapositivo. Visualmente, não há absolutamente nada errado.

*Depois.* Com a ordem corrigida no painel:

```
1. "Antes e Depois da Intervenção" (título)
2. "Antes" (subtítulo da coluna esquerda)
3. Texto da coluna esquerda
4. "Depois" (subtítulo da coluna direita)
5. Texto da coluna direita
```

**O que funciona melhor no segundo exemplo:** o título vem primeiro, o que dá contexto antes do conteúdo — exatamente como acontece a quem vê o diapositivo, cujo olhar vai ao título primeiro. E as colunas são lidas da esquerda para a direita, que é a ordem em que o conteúdo faz sentido: a comparação "antes/depois" perde-se completamente se for lida ao contrário. Note-se que a correção não mexeu num único pixel do diapositivo.

**Porque funciona**

O leitor de ecrã não tem olhos. Não vê que uma caixa está à esquerda e outra à direita, nem que uma está em cima. Recebe uma lista, e lê a lista. Corrigir a ordem de leitura é reescrever essa lista para que corresponda ao percurso que o olho faz.

Este procedimento serve o critério **1.3.2 Sequência com Significado**: quando a ordem do conteúdo afeta o significado — e num diapositivo de comparação afeta sempre — essa ordem tem de estar determinada no ficheiro.

Duas advertências finais. **A verificação da ordem de leitura tem de ser feita diapositivo a diapositivo**; não há nenhuma operação global que a corrija. E **o verificador de acessibilidade não deteta uma ordem errada** — no máximo, sugere que a confirme. Só uma pessoa sabe qual é a ordem certa, porque só uma pessoa sabe o que o diapositivo quer dizer.

---

### PP4. Texto Alternativo, Gráficos e SmartArt

**O que se pretende**

Uma apresentação **percetível sem ver**. O princípio é exatamente o do procedimento `W4` da secção "Documentos Word": todo o conteúdo transmitido por uma imagem tem de estar também disponível em texto, e o que não transmite conteúdo nenhum deve ser marcado como decorativo. Essa lógica não se repete aqui.

O que muda no PowerPoint são cinco coisas.

**Primeira: não existe "alinhado com o texto".** No Word, a boa prática é alinhar os objetos com o fluxo de texto para lhes dar uma posição fiável. No PowerPoint, **todos os objetos são flutuantes** — não há fluxo com que os alinhar. A posição de uma imagem na leitura é dada exclusivamente pela ordem de leitura (`PP3`). É uma preocupação a mais, não a menos.

**Segunda: os esquemas construídos com formas soltas.** Ao contrário do Word, é habitual desenhar diagramas diretamente no diapositivo, com dezenas de setas, retângulos e caixas de texto. Cada uma dessas formas é um objeto independente, lido isoladamente. O resultado é uma sequência de palavras sem relação nenhuma entre si — as setas, que são o que dá sentido ao diagrama, não dizem absolutamente nada.

**Terceira: o SmartArt.** O SmartArt parece resolver o problema anterior, e não resolve. Um SmartArt é lido forma a forma; a hierarquia, a sequência ou o ciclo que ele representa visualmente não chegam a quem não vê. O SmartArt é uma forma cómoda de desenhar, não uma forma de estruturar.

**Quarta: os gráficos.** Um gráfico inserido num diapositivo é, para a tecnologia de apoio, um objeto com um texto alternativo. Os valores que estão por trás dele não são acessíveis. Um texto alternativo não é sítio para uma tabela de dados: se os números importam, os números têm de estar escritos.

**Quinta: as imagens que ocupam o diapositivo inteiro.** É frequente colar uma imagem com texto lá dentro — um esquema exportado de outra aplicação, um cartaz, uma captura de ecrã de uma tabela. Esse texto não é texto: é desenho. Não é lido, não é pesquisável, não aumenta de tamanho e não se adapta ao contraste.

**Passos no PowerPoint**

1. **Escrever texto alternativo:** botão direito sobre o objeto → **Ver Texto Alternativo…**.
2. **Marcar como decorativo:** no mesmo painel, marcar **Marcar como decorativo**.
3. **Desligar o texto alternativo automático:** **Ficheiro → Opções → Facilidade de Acesso →** desmarcar **Gerar automaticamente texto alternativo para mim**. As descrições automáticas do tipo "Poderá ser uma imagem de gráfico" enganam o verificador, que passa a considerar o campo preenchido.
4. **Agrupar as formas de um diagrama:** selecionar todas → **Base → Organizar → Agrupar**. Depois, dar texto alternativo ao grupo. Um grupo com descrição é melhor do que trinta formas sem descrição; continua a ser pior do que a explicação escrita no diapositivo ou nas notas (`PP8`).
5. **SmartArt:** selecionar o **contorno exterior** do objeto (não uma forma interior) antes de abrir o painel de texto alternativo.

**Antes e depois**

*Antes.* Um diapositivo com o título "Gráfico 3" e um gráfico de barras com a evolução das queixas de acessibilidade. Texto alternativo: "Gráfico".

Quem não vê o gráfico recebe: "Gráfico 3. Gráfico." Zero informação.

*Depois.* Título do diapositivo: **"As queixas de acessibilidade duplicaram entre 2023 e 2025"**. Texto alternativo do gráfico: "Gráfico de barras com o número de queixas por ano; os valores estão indicados a seguir." E, ao lado do gráfico, no diapositivo:

- 2023 — 142 queixas
- 2024 — 210 queixas
- 2025 — 287 queixas

**O que funciona melhor no segundo exemplo:** a conclusão saiu do gráfico e passou para o título, onde toda a gente a encontra — incluindo quem vê o gráfico e não sabe interpretá-lo. Os três valores estão escritos, portanto são lidos, pesquisáveis e aumentam de tamanho com o resto do texto. E o texto alternativo deixou de tentar fazer aquilo que não consegue fazer: em vez de descrever números, remete para eles. O gráfico passou a ser o que deve ser — um reforço visual de uma informação que já está disponível em texto.

**Porque funciona**

Um texto alternativo é uma promessa: *o que esta imagem diz, digo eu agora por palavras*. Quando a imagem diz muito — um diagrama, um gráfico, um esquema de processo — a promessa não cabe num campo de descrição, e a solução deixa de ser escrever melhor no campo e passa a ser pôr a informação no diapositivo.

Este procedimento serve o critério **1.1.1 Conteúdo Não Textual**.

---

### PP5. Tabelas

**O que se pretende**

Uma apresentação **percetível sem ver** e **estruturada** nas partes em que há dados tabulares. O princípio é o do procedimento `W3`: uma tabela precisa de cabeçalhos marcados, de estrutura simples e de não ter células unidas. Isso não se repete aqui.

O que muda no PowerPoint são quatro coisas.

**Primeira: não há repetição de cabeçalhos.** No Word, uma tabela longa atravessa páginas e a opção "Repetir Linhas de Cabeçalho" garante que o cabeçalho reaparece. No PowerPoint não existe equivalente, porque um diapositivo não quebra. **Uma tabela que não cabe num diapositivo é um sinal de aviso**, não um problema de formatação: ou se divide por assunto, ou o conteúdo não devia estar numa apresentação. Esta última hipótese é tratada na secção "Escolher o Formato e Organizar o Trabalho".

**Segunda: só a linha de cabeçalho é fiável.** A caixa **Linha de Cabeçalho** marca de facto a primeira linha como cabeçalho. A caixa **Primeira Coluna** aplica formatação, mas não é exposta de forma fiável como cabeçalho de linha. Na prática: desenhar as tabelas para que os cabeçalhos fiquem em cima.

**Terceira: não há legendas.** O Word tem **Inserir Legenda**. O PowerPoint não tem nada equivalente. O título do diapositivo (`PP2`) faz esse papel — mais uma razão para ser descritivo.

**Quarta: a tabela colada como imagem.** É o erro mais comum das tabelas em diapositivos, porque colar uma imagem resolve num segundo problemas de formatação que de outro modo demoram dez minutos. O resultado é uma tabela que não é uma tabela.

**Passos no PowerPoint**

1. **Criar a tabela como tabela:** **Inserir → Tabela**. Nunca com caixas de texto alinhadas, tabulações ou uma imagem.
2. **Marcar a linha de cabeçalho:** selecionar a tabela → **Estrutura da Tabela → Opções de Estilo de Tabela →** marcar **Linha de Cabeçalho**.
3. **Confirmar a posição da tabela na ordem de leitura** (`PP3`), incluindo o texto que a introduz.
4. **Simplificar:** sem células unidas, sem tabelas dentro de tabelas, sem linhas em branco a servir de espaçamento, sem células vazias sem razão.

**Antes e depois**

*Antes.* Um diapositivo com o título "Dados" e uma tabela com 9 colunas e 14 linhas, colada de outra aplicação como imagem, com letra de corpo 9 para caber. Texto alternativo: nenhum.

*Depois.* Dois diapositivos. O primeiro, "Conformidade por tipo de organismo, 2025", com uma tabela real de 3 colunas e 5 linhas, linha de cabeçalho marcada, corpo 20:

| Tipo de organismo | Sítios avaliados | Conformes |
|---|---|---|
| Administração central | 118 | 41 |
| Administração local | 264 | 72 |
| Institutos públicos | 57 | 23 |

O segundo diapositivo apresenta as restantes colunas, com o mesmo cabeçalho de contexto, e o título indica que é a continuação.

**O que funciona melhor no segundo exemplo:** a tabela passou a existir como tabela, o que significa que cada valor é anunciado com o cabeçalho da sua coluna — "Administração local, sítios avaliados, 264" — em vez de ser uma sequência de números soltos ou, no caso da imagem, nada de todo. O corpo 20 é legível na projeção (`PP9`). E a divisão em dois diapositivos não foi uma cedência: catorze linhas com nove colunas nunca foram legíveis para ninguém, nem na sala nem em casa.

**Porque funciona**

Uma tabela com cabeçalho marcado permite ao leitor de ecrã repetir o cabeçalho a cada célula visitada — que é exatamente o que o olho faz quando volta ao topo da coluna para confirmar o que está a ler. Sem essa marcação, a tabela reduz-se a uma sequência linear de valores.

Este procedimento serve o critério **1.3.1 Informação e Relações**.

---

### PP6. Hiperligações

**O que se pretende**

Uma apresentação **navegável**. O princípio é o do procedimento `W5`: o texto da ligação tem de dizer para onde leva, sem depender do texto à volta. Isso não se repete aqui.

O que muda no PowerPoint são três coisas.

**Primeira: na sala, ninguém pode clicar.** Quem está a assistir a uma projeção vê o endereço, não o clica. Isso cria uma tensão real: o endereço tem de estar visível para quem vê, e o texto tem de ter sentido para quem ouve. A solução prática é usar um **endereço curto e legível** como texto da ligação — `acessibilidade.gov.pt/formacao` — que funciona nos dois papéis, e guardar o endereço longo nas notas do orador (`PP8`).

**Segunda: há menos contexto à volta.** Num documento, "clique aqui" é mau porque obriga a ler a frase anterior. Num diapositivo, muitas vezes nem há frase anterior: há uma lista de três pontos e um "saber mais" solto no fundo. A falta de contexto é estrutural neste formato.

**Terceira: a cor das ligações é definida pelo tema.** No Word, o azul sublinhado predefinido costuma ter contraste suficiente sobre fundo branco. No PowerPoint, as ligações herdam a cor de hiperligação do tema, que foi escolhida para combinar com a paleta — e frequentemente não tem contraste suficiente sobre o fundo do diapositivo, sobretudo em temas escuros ou com fundo colorido.

**Passos no PowerPoint**

1. **Criar a ligação com texto próprio:** selecionar o texto → **Inserir → Ligação** (ou `Ctrl+K`) → confirmar o campo **Texto a apresentar**.
2. **Ligar a outro diapositivo da mesma apresentação:** na mesma caixa, **Colocar Neste Documento** → escolher o diapositivo pelo título. Mais uma razão para os títulos serem únicos (`PP2`).
3. **Corrigir a cor das ligações:** **Estrutura → Variantes → Cores → Personalizar Cores…** → alterar **Hiperligação** e **Hiperligação Seguida**.
4. **Manter o sublinhado.** Não retirar o sublinhado das ligações para "ficar mais limpo": sem ele, a ligação passa a distinguir-se só pela cor.

**Antes e depois**

*Antes.*

> Mais informação: **clique aqui**
> Para o relatório: **https://www.exemplo.gov.pt/documentos/2025/relatorio-anual-acessibilidade-versao-final-v3.pdf**

O primeiro não diz nada. O segundo diz demasiado: um leitor de ecrã lê o endereço inteiro, caráter a caráter nas partes que não são palavras, e ninguém na sala consegue copiar aquilo do ecrã.

*Depois.*

> **Relatório anual de acessibilidade 2025** (PDF, 2,1 MB)
> Endereço curto: **exemplo.gov.pt/relatorio2025**

**O que funciona melhor no segundo exemplo:** o texto da ligação diz o que é o destino sem precisar do contexto à volta, e avisa do formato e do tamanho — informação útil para quem tem uma ligação lenta ou um plano de dados limitado. O endereço curto é legível na projeção, dizível em voz alta e escrevível à mão por quem estiver a tomar notas. E o endereço longo não desapareceu: está nas notas do orador, onde não estorva a projeção nem a leitura.

**Porque funciona**

Quem usa leitor de ecrã pode pedir a lista de todas as ligações da apresentação. Nessa lista, cada ligação aparece sozinha, sem o texto à volta. "Clique aqui" repetido oito vezes é uma lista inútil; uma lista de destinos com nome é um índice.

Este procedimento serve os critérios **2.4.4 Finalidade da Ligação (Em Contexto)** e **1.4.1 Utilização da Cor**.

---

### PP7. Multimédia e Animações

**O que se pretende**

Uma apresentação **percetível** por quem não ouve e por quem não vê, e **operável** por quem precisa de controlar o que se mexe.

Depende disto quem é surdo ou tem perda auditiva, quem é cego, quem tem perturbações vestibulares ou enxaquecas desencadeadas por movimento, quem tem epilepsia fotossensível, e quem tem dificuldades de atenção — para quem uma animação em ciclo é uma barreira concreta à leitura do resto do diapositivo.

Este procedimento trata apenas do que o PowerPoint permite fazer. **Como se produzem legendas, transcrições e audiodescrição é matéria do curso sobre multimédia e animações**; aqui parte-se do princípio de que esses ficheiros já existem.

**Passos no PowerPoint**

1. **Inserir vídeo a partir do ficheiro:** **Inserir → Vídeo → Este Dispositivo**. Vídeo alojado no ficheiro é preferível a vídeo em linha, que depende da rede da sala e pode não ter legendas controláveis.
2. **Associar legendas:** selecionar o vídeo → **Reprodução → Inserir Legendas** → escolher o ficheiro `.vtt`. 
3. **Não reproduzir automaticamente:** selecionar o vídeo → **Reprodução → Iniciar → Ao Clicar**. Multimédia que arranca sozinha sobrepõe-se à voz sintetizada de quem usa leitor de ecrã.
4. **Disponibilizar a transcrição:** uma ligação no diapositivo (`PP6`) ou o texto nas notas do orador (`PP8`). O PowerPoint não tem mecanismo próprio para transcrições.
5. **Não avançar diapositivos automaticamente:** **Transições → Avançar Diapositivo →** manter **Ao Clicar com o Rato** e desmarcar **Após**. Avanço automático retira o controlo a quem lê mais devagar.
6. **Controlar as animações:** **Animações → Painel de Animação**. Evitar animações em ciclo e entradas automáticas encadeadas. Se uma animação tiver de existir, que seja acionada por clique e curta.
7. **Evitar tudo o que pisca.** Nada de intermitências rápidas, nada de GIF animado em ciclo no fundo. O limiar formal são três flashes por segundo; o critério prático é não ter nenhum.
8. **Legendagem automática da fala do orador:** **Apresentação de Diapositivos → Sempre Utilizar Legendas** e **Definições de Legendas**. É reconhecimento automático de fala: útil como apoio em tempo real, e nunca substituto de legendas preparadas num vídeo gravado.

**Antes e depois**

*Antes.* Um diapositivo de abertura com: um vídeo de 90 segundos configurado para começar automaticamente, sem legendas; um logótipo animado a rodar em ciclo permanente num canto; e transição automática ao fim de 20 segundos, para o caso de o orador se distrair.

O que acontece: quem não ouve perde o vídeo inteiro; quem usa leitor de ecrã tem a voz sintetizada tapada pelo som do vídeo, sem forma cómoda de o parar; quem tem perturbação vestibular tem um objeto a rodar no campo de visão durante toda a apresentação; e quem lê devagar perde o diapositivo a meio.

*Depois.* O mesmo diapositivo com: o vídeo a arrancar ao clique, com legendas associadas a partir de um ficheiro `.vtt` e ligação para a transcrição; o logótipo estático; e avanço apenas por clique.

**O que funciona melhor no segundo exemplo:** nada começa sem alguém decidir que começa — o que é a definição prática de conteúdo operável. As legendas tornam o vídeo utilizável por quem não ouve e também por quem está numa sala barulhenta ou a rever o ficheiro sem auscultadores. A transcrição serve quem prefere ler a ver, quem usa leitor de ecrã e quem quer procurar uma frase específica. E o logótipo continua lá: o que se perdeu foi a rotação, que não transmitia informação nenhuma.

**Porque funciona**

Uma apresentação é uma sequência que o autor controla e o leitor sofre. Tudo o que arranca, roda ou avança sem intervenção transfere o controlo do tempo do leitor para o autor — e as pessoas que precisam de mais tempo são precisamente as que menos o têm.

Este procedimento serve os critérios **1.2.2 Legendas (Pré-gravadas)**, **2.2.2 Colocar em Pausa, Parar, Ocultar** e **2.3.1 Três Flashes ou Abaixo do Limiar**.

---

### PP8. Notas do Orador

**O que se pretende**

Uma apresentação **percetível sem ver** também naquilo que não cabe no diapositivo. As notas do orador são o único sítio, neste formato, onde é possível escrever texto longo sem estragar a projeção.

Depende disto quem recebe o ficheiro em vez de assistir à sessão; quem usa leitor de ecrã e precisa da descrição longa de um diagrama que o texto alternativo não comporta (`PP4`); e o próprio orador, que muitas vezes é a pessoa que mais beneficia de ter o essencial escrito.

É preciso ser claro sobre um limite. **As notas não são lidas durante a apresentação** — não estão na projeção nem chegam a quem está na sala. São um canal para o ficheiro distribuído, não para o momento da sessão. E, mesmo no ficheiro, são um sítio que só encontra quem sabe que existe.

Daqui resulta a regra: **o essencial vai no diapositivo; o detalhe alargado vai nas notas.** As notas complementam; nunca substituem.

**Passos no PowerPoint**

1. **Abrir o painel de notas:** **Ver → Notas**, ou arrastar a barra por baixo do diapositivo.
2. **Trabalhar as notas com espaço:** **Ver → Página de Notas**.
3. **Escrever texto simples.** As notas não têm cabeçalhos, listas semânticas nem tabelas fiáveis. Parágrafos curtos, uma ideia de cada vez.
4. **Nunca colar imagens nas notas.** Uma imagem nas notas é conteúdo que não chega a ninguém.
5. **Avisar que as notas existem**, num diapositivo inicial e na mensagem com que a apresentação é distribuída.

**Antes e depois**

*Antes.* Notas do diapositivo do gráfico:

> falar 3 min. piada do costume. NÃO esquecer o dado do Norte!!

*Depois.* Notas do mesmo diapositivo:

> **Descrição do gráfico.** Gráfico de barras verticais com o número de queixas de acessibilidade por ano: 142 em 2023, 210 em 2024, 287 em 2025. O crescimento é constante e acentua-se no último ano.
>
> **Nota regional.** O aumento é mais pronunciado na região Norte, que passou de 31 para 94 queixas no mesmo período.
>
> **Endereço completo do relatório:** https://www.exemplo.gov.pt/documentos/2025/relatorio-anual-acessibilidade.pdf

**O que funciona melhor no segundo exemplo:** as notas passaram a conter informação que só existia na cabeça do orador — o que significa que o ficheiro distribuído deixou de ser inútil sem ele. A descrição do gráfico dá a quem não vê aquilo que o texto alternativo não conseguia comportar. O endereço longo saiu do diapositivo, onde estorvava, e foi para onde pode ser copiado. E o lembrete pessoal desapareceu, porque as notas deixaram de ser um bilhete para o próprio e passaram a ser conteúdo.

Note-se também o que **não** aconteceu: os três valores do gráfico continuam escritos no diapositivo (`PP4`). As notas repetem-nos com mais detalhe; não são o único sítio onde estão.

**Porque funciona**

Uma apresentação distribuída é, para muita gente, a única versão que existe. Quando o essencial vive na voz do orador, quem não estava na sala fica com um conjunto de imagens e palavras-chave. As notas são a diferença entre um ficheiro que se lê e um ficheiro que se folheia.

---

### PP9. Contraste e Legibilidade em Projeção

**O que se pretende**

Uma apresentação **legível** — nas condições reais em que vai ser vista, que são quase sempre piores do que o ecrã onde foi feita.

Depende disto quem tem baixa visão, quem tem daltonismo, quem tem mais de quarenta e cinco anos, quem está sentado na última fila, e quem apanha a sala com o sol a bater no ecrã e um projetor comprado em 2011. Esta é a propriedade que beneficia mais gente de uma só vez.

O ponto de partida é este: **o ecrã do portátil mente**. Tem melhor contraste, melhor definição e está a cinquenta centímetros dos olhos. Nada do que se decide a olhar para ele é uma boa previsão do que se vai ver na parede.

**Passos no PowerPoint**

1. **Definir os tamanhos no modelo global, não diapositivo a diapositivo:** **Ver → Modelo Global de Diapositivos**. Corpo de texto a **24 pontos ou mais**; nunca abaixo de 18. Se o texto não cabe a 24, o problema é a quantidade de texto.
2. **Verificar o contraste do texto:** mínimo de **4,5:1** em relação ao fundo. Formalmente, texto grande (a partir de 18 pontos, ou 14 pontos a negrito) só exige 3:1 — e num diapositivo quase todo o texto é "grande" nesse sentido. Ainda assim, **em projeção vale a pena cumprir 4,5:1**, porque a projeção degrada o contraste real muito abaixo do que o cálculo indica.
3. **Definir as cores no tema:** **Estrutura → Variantes → Cores → Personalizar Cores…**, incluindo as cores de hiperligação (`PP6`). 
4. **Não pôr texto sobre fotografia.** Se for mesmo necessário, colocar uma faixa de cor sólida por baixo do texto — não uma transparência ligeira, que faz variar o contraste ao longo da frase.
5. **Não usar a cor como única informação.** Uma legenda de gráfico que só se distingue por cor exclui quem tem daltonismo e quem imprime a preto e branco. Acrescentar rótulos junto aos dados, ou padrões distintos.
6. **Alinhar à esquerda**, sem justificar; evitar maiúsculas em blocos, itálico em textos longos e tipos de letra decorativos. Preferir letras sem serifas.
7. **Não usar texto dentro de imagens** (`PP4`).

**Antes e depois**

*Antes.* Um diapositivo com fotografia de céu ao pôr do sol a ocupar todo o fundo, título a branco em letra fina de corpo 40 sobre a parte clara da fotografia, sete pontos de texto a corpo 14 para caber, e um gráfico circular com seis gomos distinguidos apenas por tons de azul, com a legenda ao lado.

*Depois.* Fundo de cor sólida escura; título a branco em letra de peso normal, corpo 40, com contraste de 12:1; três pontos de texto a corpo 24, com o resto do conteúdo passado para outro diapositivo; e o gráfico circular substituído por um gráfico de barras com o valor escrito junto a cada barra.

**O que funciona melhor no segundo exemplo:** o contraste deixou de depender da zona da fotografia em que a palavra calhou — sobre uma imagem, o contraste varia dentro da mesma frase, e não há valor único que se possa verificar. O corpo 24 é legível da última fila, e a redução de sete para três pontos não perdeu conteúdo: distribuiu-o. E o gráfico passou a ser legível sem distinguir seis tons de azul, o que ajuda quem tem daltonismo, quem está longe e quem simplesmente não consegue fazer corresponder a legenda aos gomos — ou seja, praticamente toda a gente.

**Porque funciona**

O contraste e o tamanho não são preferências estéticas: são o que determina se a informação chega ou não chega. Um diapositivo bonito e ilegível transmite zero. E, ao contrário de quase tudo o resto nesta secção, este é o problema que **também** afeta quem não tem deficiência nenhuma — o que costuma ser o argumento mais eficaz junto de quem resiste a mudar o modelo gráfico da instituição.

Este procedimento serve os critérios **1.4.3 Contraste (Mínimo)** e **1.4.1 Utilização da Cor**.

---

## Verificação

### O Verificador de Acessibilidade do PowerPoint

O verificador abre em **Rever → Verificar Acessibilidade**. Os resultados aparecem num painel à direita, organizados em três grupos: **Erros** (conteúdo inacessível para algumas pessoas), **Avisos** (conteúdo provavelmente difícil) e **Sugestões** (melhorias possíveis). Cada resultado tem uma explicação e, na maior parte dos casos, um botão de correção.

Vale a pena marcar **Manter o verificador de acessibilidade a funcionar enquanto trabalho**, que coloca um indicador permanente na barra de estado. Corrigir enquanto se escreve custa uma fração do que custa corrigir no fim.

Ao abrir o verificador, aparece também o separador **Acessibilidade** no friso, com atalhos para os comandos usados nesta secção: texto alternativo, ordem de leitura, título de diapositivo e cor do texto.

Verificações específicas do PowerPoint que o verificador faz:

- texto alternativo em falta em imagens, gráficos, SmartArt e tabelas;
- diapositivos sem título;
- títulos de diapositivo duplicados; 
- ordem de leitura a confirmar em diapositivos com vários objetos;
- tabelas sem linha de cabeçalho marcada;
- texto com contraste insuficiente;
- texto de hiperligação pouco claro.

### O Que o Verificador Não Deteta

Vale a pena repetir a mensagem da secção "Documentos Word", porque no PowerPoint é ainda mais verdadeira: **uma verificação limpa não significa apresentação acessível**. A máquina deteta ausências; não deteta erros.

Concretamente, o verificador não sabe:

- **Se o texto alternativo presta.** "Imagem" é um texto alternativo. "Poderá ser uma imagem de gráfico", gerada automaticamente, também. Ambos passam.
- **Se a ordem de leitura está certa.** Quando avisa, o verificador pede que confirme a ordem — não diz que está errada, porque não sabe qual devia ser. Este é o ponto cego mais grave neste formato, precisamente onde estão os erros mais frequentes (`PP3`).
- **Se o título do diapositivo diz alguma coisa.** "Diapositivo 7" é um título válido para o verificador.
- **Se o conteúdo essencial só existe na voz do orador.** Um diapositivo com três palavras e uma fotografia passa sem uma única observação.
- **Se um gráfico depende só da cor.** O contraste do texto é medido; a distinção entre seis gomos azuis não é (`PP9`).
- **Se a letra sobrevive à projeção.** Corpo 12 não gera aviso nenhum.
- **Se as legendas correspondem ao áudio**, ou se existem sequer para um vídeo em linha.
- **Se as notas do orador carregam conteúdo que devia estar no diapositivo** (`PP8`).
- **Se a tabela é mesmo uma tabela.** Uma tabela colada como imagem gera, no máximo, um aviso de texto alternativo em falta — que se "resolve" escrevendo "tabela de resultados" no campo, deixando o problema real intacto.

Três testes manuais que valem mais do que o verificador:

1. **Vista de Destaques** (`Ver → Vista de Destaques`). Se a apresentação não fizer sentido nenhum nesta vista, a estrutura está errada. É um teste de dez segundos.
2. **Percurso com Tab.** Num diapositivo suspeito, clicar numa zona vazia e premir Tab até dar a volta. É a ordem de leitura, sem painéis.
3. **Leitura em voz alta pela ordem do painel.** Ler o diapositivo em voz alta pela ordem indicada no painel de ordem de leitura, a alguém que não o esteja a ver. Se essa pessoa não perceber, ninguém percebe.

---

## Recomendações para Conteúdo Acessível

**Escolher o esquema antes de escrever.** Trinta segundos no início poupam meia hora de correção de ordem de leitura no fim. Se o esquema de que precisa não existe, criá-lo no modelo global uma vez, para toda a instituição.

**Uma ideia por diapositivo.** Um diapositivo cheio é ilegível na projeção, indecifrável para quem usa leitor de ecrã e incompreensível para quem tem dificuldades de atenção. Dividir não é diluir.

**Escrever títulos que digam a conclusão.** "Resultados" identifica o assunto. "As queixas duplicaram em dois anos" transmite a informação. O segundo serve a navegação, serve quem lê o ficheiro sozinho e serve quem está na sala.

**Definir o idioma da apresentação.** **Rever → Idioma → Definir Idioma de Verificação**, com o texto todo selecionado. No PowerPoint, o idioma engana mais do que no Word, porque as caixas herdam o idioma do momento em que foram criadas e as apresentações são feitas de pedaços reaproveitados. Uma caixa marcada como inglês faz o leitor de ecrã ler português com pronúncia inglesa — incompreensível.

**Preencher o título nas propriedades do ficheiro.** **Ficheiro → Informações → Propriedades → Título**. O princípio é o do procedimento `W6` e aplica-se sem alterações.

**Não dizer "como podem ver aqui".** Se o conteúdo só existe no gesto do orador a apontar para o ecrã, não existe para quem não vê o ecrã — nem para quem lê o ficheiro depois.

**Distribuir a apresentação antes da sessão.** Quem usa leitor de ecrã, quem precisa de ampliar o texto e quem lê mais devagar chega à sala em condições completamente diferentes se tiver tido acesso ao ficheiro na véspera. É a medida mais barata e mais eficaz de toda esta secção.

**Manter a consistência entre diapositivos.** O mesmo esquema, as mesmas cores, os elementos nos mesmos sítios. Consistência reduz o esforço cognitivo de toda a gente, e para quem tem dificuldades de aprendizagem faz a diferença entre acompanhar e desistir.

**Verificar em condições reais.** Antes da sessão, projetar e afastar-se até ao fundo da sala. Meio minuto que encontra mais problemas do que o verificador.

### Erros Comuns

| Erro | O que acontece | Correção |
|---|---|---|
| Construir diapositivos a partir do esquema "Em Branco" | Nenhuma estrutura, nenhum título, ordem de leitura à sorte | Usar esquemas com marcadores de posição (`PP1`) |
| Apagar o título porque estraga a composição | O diapositivo desaparece da navegação | Título oculto (`PP2`) |
| Repetir o mesmo título em muitos diapositivos | A navegação por títulos deixa de distinguir seja o que for | Títulos únicos e descritivos (`PP2`) |
| Assumir que a ordem de leitura segue a ordem visual | O diapositivo é lido por uma ordem que ninguém previu | Verificar diapositivo a diapositivo (`PP3`) |
| Corrigir a ordem no Painel de Seleção como se fosse de cima para baixo | A correção inverte o problema em vez de o resolver | Usar o painel de ordem de leitura, ou lembrar que o Painel de Seleção se lê de baixo para cima (`PP3`) |
| Aceitar o texto alternativo automático | O campo fica preenchido, o verificador cala-se, a informação continua ausente | Desligar a geração automática e escrever (`PP4`) |
| Descrever um gráfico só no texto alternativo | Os valores não chegam a quem não vê e a conclusão não chega a mais ninguém | Conclusão no título, valores em texto (`PP4`) |
| Colar tabelas e esquemas como imagem | Deixam de ser texto: não são lidos, não crescem, não se pesquisam | Tabela real (`PP5`); esquema explicado em texto (`PP4`) |
| Deixar o vídeo a arrancar automaticamente | Tapa a voz sintetizada e retira o controlo | Iniciar ao clique (`PP7`) |
| Pôr transição automática ao fim de X segundos | Quem lê devagar perde o diapositivo | Avançar apenas por clique (`PP7`) |
| Guardar o essencial só nas notas | Quem não sabe que as notas existem nunca lá chega | Essencial no diapositivo, detalhe nas notas (`PP8`) |
| Reduzir o corpo da letra para o texto caber | Ilegível na projeção — e sinal de que há texto a mais | Dividir o conteúdo, manter corpo 24 (`PP9`) |
| Texto branco sobre fotografia | O contraste varia dentro da própria frase | Fundo sólido por baixo do texto (`PP9`) |

---

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **No PowerPoint não há fluxo de texto.** A ordem de leitura é a ordem de criação dos objetos, não a ordem em que aparecem no ecrã. Esta é a frase mais importante da secção.
2. **Uma apresentação pode estar visualmente perfeita e completamente inacessível**, sem que nada no ecrã o denuncie. Ao contrário do Word, o aspeto não é indicador de nada.
3. **O esquema de diapositivo resolve a maior parte do problema antes de ele existir** (`PP1`). Diapositivos construídos com esquema nascem estruturados, ordenados e com título.
4. **O título de diapositivo é o mecanismo de navegação do formato** (`PP2`). Tem de existir sempre, tem de ser único e tem de dizer alguma coisa. Quando não pode ser visível, oculta-se — nunca se apaga.
5. **A ordem de leitura verifica-se diapositivo a diapositivo** (`PP3`), e o Painel de Seleção lê-se de baixo para cima.
6. **Texto alternativo, tabelas e hiperligações seguem os princípios de `W4`, `W3` e `W5`.** O que muda são as condições: sem fluxo de texto, sem legendas, sem repetição de cabeçalhos, e com menos contexto à volta das ligações.
7. **Nada deve arrancar, rodar ou avançar sozinho** (`PP7`). O controlo do tempo pertence a quem lê.
8. **As notas do orador complementam o diapositivo; nunca o substituem** (`PP8`).
9. **O ecrã do portátil mente** (`PP9`). Corpo 24, contraste generoso, e um teste feito ao fundo da sala.
10. **Uma verificação limpa não significa apresentação acessível.** O verificador não sabe se a ordem de leitura está certa, e é aí que estão os erros.

### Exercícios Práticos

**Exercício 1 — Diagnóstico em dez segundos**

Abra uma apresentação sua, com pelo menos 15 diapositivos, e vá a **Ver → Vista de Destaques**.

1. Quantos diapositivos aparecem sem título?
2. Quantos títulos estão repetidos?
3. Quantos títulos dizem o assunto ("Resultados") em vez da conclusão?
4. Lendo apenas os títulos, de cima a baixo, percebe-se o percurso da apresentação?

Registe as respostas. Vai voltar a elas no exercício 5.

**Exercício 2 — Ordem de leitura**

Na mesma apresentação, escolha os três diapositivos com mais objetos.

1. Em cada um, clique numa zona vazia e percorra o diapositivo com **Tab**, anotando a ordem.
2. Compare com a ordem por que leria o diapositivo se o estivesse a explicar a alguém.
3. Corrija no painel de ordem de leitura (`PP3`).
4. Confirme que a correção não alterou nada visualmente.

**Exercício 3 — Reconstruir com esquema**

Escolha um diapositivo construído com caixas de texto desenhadas à mão (identifique-o pelo Painel de Seleção: só "CaixaDeTexto" e "Retângulo").

1. Crie um diapositivo novo com o esquema mais próximo.
2. Passe o conteúdo para os marcadores de posição.
3. Compare os dois no Painel de Seleção e no painel de ordem de leitura.
4. Cronometre. Quanto tempo demorou? Quanto tempo demoraria corrigir os 40 diapositivos da apresentação à mão?

**Exercício 4 — Do gráfico ao texto**

Escolha um diapositivo com um gráfico.

1. Escreva o texto alternativo atual (ou registe que não existe).
2. Reescreva o título do diapositivo para que passe a conter a conclusão do gráfico.
3. Acrescente ao diapositivo os valores essenciais em texto.
4. Reescreva o texto alternativo à luz do que já está escrito no diapositivo — deve ficar mais curto, não mais longo.
5. Escreva nas notas a descrição alargada (`PP8`).

**Exercício 5 — Auditoria completa e comparação**

Sobre a mesma apresentação, agora corrigida:

1. Execute **Rever → Verificar Acessibilidade** e corrija tudo o que aparecer.
2. Com o painel limpo, percorra a lista de "O Que o Verificador Não Deteta" e verifique cada ponto à mão.
3. Compare com as respostas do exercício 1.
4. Escreva três linhas de resposta a esta pergunta: **quantos dos problemas que encontrou tinham sido detetados pelo verificador?**

**Exercício 6 — O teste do fundo da sala**

Projete a apresentação corrigida numa sala real, com a iluminação normal de trabalho.

1. Sente-se na última fila.
2. Percorra os diapositivos e anote todos aqueles em que não consegue ler alguma coisa.
3. Peça a mesma coisa a um colega.
4. Corrija — e note quantos desses diapositivos tinham passado no verificador sem uma única observação.

