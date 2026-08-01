# Conclusão e Boas Práticas

## Recapitulação

Ao longo deste módulo, explorámos quatro áreas fundamentais da acessibilidade do conteúdo textual:

**Texto Base**

- Uso de texto real em vez de imagens
- Estrutura semântica adequada
- Hierarquia clara de cabeçalhos
- Compatibilidade com tecnologias de apoio

**Linguagem**

- Clareza e simplicidade na escrita
- Identificação correta de idiomas
- Estruturação lógica da informação
- Explicação de termos técnicos

**Apresentação Visual**

- Contraste e legibilidade
- Dimensionamento flexível
- Espaçamento adequado
- Consistência no design

**Abreviaturas e Acrónimos**

- Explicação na primeira menção
- Uso apropriado do elemento <abbr>
- Consistência ao longo do documento
- Considerações multilíngues
- Fornecimento de glossários quando necessário

## Recursos Adicionais

**Ferramentas**

- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
  Para verificar o contraste entre cores
- [Colour Contrast Analyzer](https://www.tpgi.com/color-contrast-checker)
  Para verificar o contraste entre cores

**Documentação**
- [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag)
- [MDN Accessibility Guide](https://developer.mozilla.org/en-US/docs/Learn/Accessibility)
- [HTML5 Abbreviations](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-abbr-element)

## Exercícios de Consolidação

1. **Auditoria Completa**
   Escolha um website e faça uma análise completa:
   
   - Estrutura do texto
   - Clareza da linguagem
   - Apresentação visual
   - Uso de abreviaturas e acrónimos
   - Compatibilidade com tecnologias de apoio

2. **Projeto de Melhoria**
   Identifique três páginas num website existente e:
   
   - Documente problemas encontrados
   - Proponha soluções específicas
   - Implemente as melhorias
   - Teste os resultados

3. **Simulação de Uso**
   Tente navegar num website usando:
   
   - Apenas teclado
   - Leitor de ecrã
   - Zoom a 200%
   - Note especialmente como as abreviaturas são lidas
   
   Documente os desafios encontrados.

## Lista de Verificação Final

Antes de publicar qualquer conteúdo web, utilize esta lista de verificação para garantir que é acessível:

### Texto Base

- [ ] Todo o texto é real (não imagens)
- [ ] Hierarquia de cabeçalhos lógica (h1-h6)
- [ ] Elementos HTML semânticos utilizados
- [ ] Links descritivos e únicos
- [ ] Listas marcadas adequadamente

### Linguagem

- [ ] Idioma principal da página identificado
- [ ] Mudanças de idioma marcadas
- [ ] Frases curtas e claras
- [ ] Termos técnicos explicados
- [ ] Estrutura de informação lógica

### Apresentação Visual

- [ ] Contraste mínimo de 4.5:1 para texto normal
- [ ] Texto redimensionável até 200%
- [ ] Espaçamento entre linhas de pelo menos 1.5
- [ ] Largura de texto limitada (máximo 70-80 caracteres)
- [ ] Alinhamento à esquerda (não justificado)

### Abreviaturas e Acrónimos

- [ ] Todas as abreviaturas explicadas na primeira menção
- [ ] Elemento <abbr> usado apropriadamente
- [ ] Lista de abreviaturas e acrónimos fornecido para documentos longos
- [ ] Consistência mantida ao longo do documento
- [ ] Considerações multilíngues aplicadas quando necessário
 
### Técnicas de Implementação

- [ ] CSS usa unidades relativas
- [ ] Layout responsivo
- [ ] Ordem de leitura lógica
- [ ] Foco visível em elementos interativos

### Testes e Validação

- [ ] Testado com leitor de ecrã
- [ ] Verificado com diferentes browsers
- [ ] Validado com ferramentas automáticas
- [ ] Testado apenas com teclado
- [ ] Revisto por utilizadores reais

## Critérios de Sucesso WCAG Relevantes

Esta secção identifica os critérios de sucesso das Diretrizes de Acessibilidade para Conteúdo Web (WCAG) relevantes para a acessibilidade textual. 

### Nível A

1. **1.1.1 Conteúdo Não Textual**
   - *Descrição:* Todo o conteúdo não textual apresentado ao utilizador tem uma alternativa textual que serve um propósito equivalente.
   - *Aplicação ao texto:* Utilize texto real HTML em vez de imagens contendo texto. Quando usar imagens, forneça alternativas textuais adequadas (atributo `alt`) que descrevam o conteúdo e função da imagem. Isto permite que utilizadores de leitores de ecrã acedam à informação.

2. **1.3.1 Informação e Relações**
   - *Descrição:* A informação, estrutura e relações transmitidas através da apresentação podem ser determinadas programaticamente ou estão disponíveis no texto.
   - *Aplicação ao texto:* Utilize elementos HTML semânticos apropriados para estruturar o conteúdo textual:
      - `<h1>` a `<h6>` para cabeçalhos em ordem hierárquica
      - `<p>` para parágrafos
      - `<ul>`, `<ol>` e `<li>` para listas
      - `<table>`, `<th>`, `<tr>` e `<td>` para tabelas de dados

3. **1.3.2 Sequência com Significado**
   - *Descrição:* Quando a sequência na qual o conteúdo é apresentado afeta o seu significado, uma sequência de leitura correta pode ser determinada programaticamente.
   - *Aplicação ao texto:* Organize o conteúdo HTML numa ordem lógica e significativa, que reflita a sequência de leitura natural. Evite usar CSS para reordenar visualmente o texto de uma forma que não corresponda à ordem do código fonte, pois isso pode confundir utilizadores de leitores de ecrã.

4. **2.4.2 Título da Página**
   - *Descrição:* As páginas web têm títulos que descrevem o tópico ou propósito.
   - *Aplicação ao texto:* Forneça um título descritivo e único para cada página web usando o elemento `<title>` no `<head>` do documento. O título deve claramente indicar o tema ou propósito da página.

5. **2.4.6 Cabeçalhos e Etiquetas**
   - *Descrição:* Os cabeçalhos e etiquetas descrevem o tópico ou propósito.
   - *Aplicação ao texto:* Escreva cabeçalhos (`<h1>` a `<h6>`) claros e descritivos que resumam adequadamente o conteúdo da secção que introduzem. Etiquetas para formulários e botões devem ser descritivas e indicar claramente a sua função.

6. **3.1.1 Idioma da Página**
   - *Descrição:* O idioma humano predefinido de cada página web pode ser determinado programaticamente.
   - *Aplicação ao texto:* Especifique o idioma principal da página usando o atributo `lang` no elemento `<html>` (por exemplo, `<html lang="pt">`). Isto permite que leitores de ecrã usem a pronúncia correta e que ferramentas de tradução automática funcionem adequadamente.

7. **3.1.2 Idioma de Partes**
   - *Descrição:* O idioma de cada passagem ou frase no conteúdo pode ser determinado programaticamente.
   - *Aplicação ao texto:* Quando incluir conteúdo num idioma diferente do idioma principal da página, marque-o com o atributo `lang` apropriado (por exemplo, `<span lang="en">English text</span>`). Isto garante a pronúncia correta por leitores de ecrã e traduções precisas.

### Nível AA

1. **1.4.3 Contraste (Mínimo)**
   - *Descrição:* A apresentação visual de texto e imagens de texto tem um rácio de contraste de pelo menos 4.5:1.
   - *Aplicação ao texto:* Assegure que o texto tem contraste suficiente contra o seu fundo:
      - Texto normal: rácio mínimo de 4.5:1
      - Texto grande (pelo menos 18pt ou 14pt negrito): rácio mínimo de 3:1

2. **1.4.4 Redimensionar Texto**
   - *Descrição:* O texto pode ser redimensionado sem tecnologia de apoio até 200% sem perda de conteúdo ou funcionalidade.
   - *Aplicação ao texto:* Use unidades relativas (como em, rem, %) em vez de unidades fixas (px) para tamanhos de fonte. Implemente layouts flexíveis que se adaptem quando o texto é ampliado. Teste o seu site com zoom a 200% para garantir que o texto permanece legível e não causa sobreposição ou recorte.

3. **1.4.5 Imagens de Texto**
   - *Descrição:* Se as tecnologias em uso puderem fornecer a apresentação visual, o texto é usado para transmitir informação em vez de imagens de texto.
   - *Aplicação ao texto:* Evite usar imagens que contenham texto. Use HTML e CSS para formatar texto real, permitindo que seja redimensionado, pesquisado, copiado e acedido por tecnologias de apoio. As exceções incluem logótipos ou quando uma apresentação específica é essencial.

4. **1.4.12 Espaçamento do Texto**
   - *Descrição:* Em conteúdo implementado usando linguagens de marcação, não ocorre perda de conteúdo ou funcionalidade quando:
      - A altura da linha é pelo menos 1.5 vezes o tamanho da fonte
      - O espaçamento entre parágrafos é pelo menos 2 vezes o tamanho da fonte
      - O espaçamento entre letras é pelo menos 0.12 vezes o tamanho da fonte
      - O espaçamento entre palavras é pelo menos 0.16 vezes o tamanho da fonte
   - *Aplicação ao texto:* Aplique espaçamento adequado no CSS usando propriedades como:
      - `line-height: 1.5` ou superior
      - `margin-bottom: 2em` para parágrafos
      - `letter-spacing: 0.12em` quando necessário
      - `word-spacing: 0.16em` quando necessário

## Nível AAA

1. **1.4.6 Contraste (Melhorado)**
   - *Descrição:* A apresentação visual de texto e imagens de texto tem um rácio de contraste de pelo menos 7:1.
   - *Aplicação ao texto:* Aumente o contraste para além do mínimo requerido:
      - Texto normal: use um rácio de pelo menos 7:1
      - Texto grande: use um rácio de pelo menos 4.5:1

2. **1.4.8 Apresentação Visual**
   -  *Descrição:* Para a apresentação visual de blocos de texto:
      - O utilizador pode selecionar cores de primeiro plano e de fundo
      - A largura não é maior que 80 caracteres
      - O texto não é justificado
      - O espaçamento entre linhas é pelo menos espaço e meio
      - O espaçamento entre parágrafos é pelo menos 1,5 vezes maior que o espaçamento entre linhas
      - O texto pode ser redimensionado sem tecnologia de apoio até 200% sem necessidade de scroll horizontal
   - *Aplicação ao texto:*
      - Permita personalização de cores através de estilos alternativos
      - Limite a largura do texto a 70-80 caracteres usando `max-width: 70ch`
      - Use `text-align: left` (não `justify`)
      - Aplique `line-height: 1.5` ou superior
      - Defina margens de parágrafos maiores que a altura da linha
      - Implemente layouts responsivos que evitem scroll horizontal

3. **1.4.9 Imagens de Texto (Sem Exceção)**
   - *Descrição:* As imagens de texto só são usadas para decoração pura ou quando uma apresentação específica de texto é essencial para a informação a ser transmitida.
   - *Aplicação ao texto:* Elimine completamente as imagens de texto (exceto logótipos), mesmo para elementos decorativos. Use CSS para estilizar texto real para conseguir efeitos visuais semelhantes.

4. **2.4.10 Cabeçalhos de Secção**
   - *Descrição:* Os cabeçalhos de secção são usados para organizar o conteúdo.
   - *Aplicação ao texto:* Divida todo o conteúdo em secções lógicas, cada uma introduzida por um cabeçalho apropriado (`<h1>` a `<h6>`). Siga uma hierarquia clara e não salte níveis de cabeçalho. Esta estrutura melhora a navegação para todos os utilizadores, especialmente os que usam leitores de ecrã.

5. **3.1.3 Palavras Invulgares**
   - *Descrição:* Está disponível um mecanismo para identificar definições específicas de palavras ou expressões usadas de maneira invulgar ou restrita, incluindo expressões idiomáticas e jargão.
   - *Aplicação ao texto:* Para termos técnicos, jargão ou expressões pouco comuns:
      - Use o elemento `<dfn>` para marcar a primeira ocorrência de um termo
      - Crie um glossário ou secção de definições
      - Forneça explicações inline quando apropriado
      - Considere usar tooltips (dicas) para termos complexos

6. **3.1.4 Abreviaturas**
   - *Descrição:* Está disponível um mecanismo para identificar a forma expandida ou o significado das abreviaturas.
   - *Aplicação ao texto:* Para abreviaturas e acrónimos:
      - Use o elemento `<abbr>` com um atributo `title` contendo a forma expandida: `<abbr title="Organização Mundial de Saúde">OMS</abbr>`
      - Na primeira ocorrência, escreva a forma completa seguida da abreviatura entre parênteses
      - Para documentos longos, crie um glossário de abreviaturas

7. **3.1.5 Nível de Leitura**
   - *Descrição:* Quando o texto requer capacidade de leitura mais avançada do que o nível básico de educação, está disponível conteúdo suplementar ou uma versão que não requer capacidade de leitura mais avançada.
   - *Aplicação ao texto:*
      - Escreva no nível de leitura mais básico apropriado para o conteúdo
      - Use frases curtas e diretas
      - Evite linguagem complexa quando possível
      - Forneça resumos simplificados para conteúdo complexo
      - Inclua recursos visuais para complementar texto difícil

8. **3.1.6 Pronúncia**
   - *Descrição:* Está disponível um mecanismo para identificar a pronúncia específica de palavras onde o significado, no contexto, é ambíguo sem conhecer a pronúncia.
   - *Aplicação ao texto:*
      - Para palavras cuja pronúncia afeta o significado, forneça guias de pronúncia usando:
         - Notação fonética
         - Arquivos de áudio
         - Descrições textuais da pronúncia
      - Considere o elemento `<ruby>` para adicionar guias de pronúncia em idiomas como japonês ou chinês
