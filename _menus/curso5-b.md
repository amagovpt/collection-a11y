---
title: Estrutura, Rótulos e Apresentação
layout: default
nav_order: 2
---

# Estrutura, Rótulos e Apresentação

## Introdução

Quando navegamos num website, os menus são como mapas que nos ajudam a encontrar o que procuramos. Uma estrutura clara, rótulos adequados e apresentação consistente são essenciais para todos os utilizadores, mas são particularmente importantes para pessoas com deficiência.

Nesta secção, vamos explorar como estruturar corretamente os menus, criar rótulos informativos e apresentar o conteúdo de forma acessível. Estas práticas beneficiam todos os utilizadores, mas são especialmente críticas para quem usa tecnologias de apoio.

### Como as Pessoas com Deficiência Dependem da Estruturação, Rotulagem e Apresentação de Menus

#### Utilizadores de Leitores de Ecrã

Os leitores de ecrã convertem o texto em fala ou braille, permitindo que pessoas cegas ou com baixa visão acedam ao conteúdo digital. Para estes utilizadores:

- **Estrutura semântica correta**: Permite que os leitores de ecrã identifiquem e anunciem os menus como áreas de navegação, fornecendo contexto sobre a sua finalidade.
- **Rótulos claros**: São essenciais para compreender o destino de cada link sem depender de pistas visuais.
- **Hierarquia bem definida**: Ajuda a entender a relação entre itens de menu principais e submenus.

**Exemplo**: Imagina um leitor de ecrã a interpretar dois menus diferentes:

```html
<!-- Menu bem estruturado -->
<nav aria-label="Menu principal">
  <ul>
    <li><a href="inicio.html" aria-current="page">Início</a></li>
    <li><a href="sobre.html">Sobre Nós</a></li>
  </ul>
</nav>

<!-- Menu mal estruturado -->
<div class="menu">
  <a href="inicio.html">Início</a>
  <a href="sobre.html">Sobre Nós</a>
</div>
```

No primeiro exemplo, o leitor de ecrã anunciará "Menu principal, lista com 2 itens" antes de ler os links, fornecendo contexto. No segundo exemplo, apenas lerá os links sem indicar que são parte de um menu de navegação.

#### Pessoas com Dificuldades Cognitivas

Pessoas com dificuldades de aprendizagem, défice de atenção ou dislexia beneficiam de:

- **Organização lógica**: Agrupamento relacionado de itens de menu facilita a compreensão.
- **Rótulos concisos e diretos**: Reduzem a carga cognitiva necessária para processar informação.
- **Apresentação consistente**: Cria previsibilidade, reduzindo esforço mental para compreender novos padrões.

**Exemplo**: Comparando dois conjuntos de rótulos de menu:

```
Menu claro:
- Produtos
- Serviços
- Contactos

Menu confuso:
- Compre Aqui Tudo o Que Precisa
- O Que Podemos Fazer Por Si
- Fale Connosco Agora!
```

O primeiro menu usa rótulos simples e objetivos, facilitando a compreensão rápida do conteúdo.

#### Pessoas com Mobilidade Reduzida

Utilizadores que dependem do teclado ou dispositivos de entrada alternativos necessitam de:

- **Estrutura navegável**: Permite avançar entre secções do menu sem ter que passar por cada item individual.
- **Indicadores visuais fortes**: Mostram claramente onde está o foco da navegação.
- **Áreas de clique adequadas**: Facilitam a interação para quem tem dificuldades motoras.

#### Pessoas com Baixa Visão

Utilizadores com baixa visão que não usam leitores de ecrã dependem de:

- **Contraste adequado**: Para distinguir o texto do fundo.
- **Organização visual clara**: Para entender a hierarquia e relações entre itens.
- **Possibilidade de ampliação**: Sem perder a funcionalidade ou compreensão da estrutura.

### Requisitos de Acessibilidade para Estrutura, Rótulos e Apresentação de Menus

#### Requisitos das WCAG (Diretrizes de Acessibilidade para Conteúdo Web)

1. **Percetível**:
   - Conteúdo apresentado de forma a ser percebido por todos os sentidos
   - Contraste suficiente entre texto e fundo (mínimo 4.5:1)
   - Estrutura não dependente apenas de características sensoriais (cor, forma, tamanho)

2. **Operável**:
   - Navegação por teclado completa
   - Tempo suficiente para interação
   - Evitar conteúdo que cause convulsões ou reações físicas

3. **Compreensível**:
   - Texto legível e compreensível
   - Conteúdo previsível na operação
   - Assistência para evitar e corrigir erros

4. **Robusto**:
   - Compatibilidade com tecnologias atuais e futuras
   - Código válido e bem formado

#### Elementos Específicos para Menus Acessíveis

- **Estrutura semântica**: Utilizar elementos HTML como `<nav>`, `<ul>`, `<li>` 
- **ARIA quando necessário**: Complementar HTML com atributos ARIA quando o HTML não for suficiente
- **Rótulos informativos**: Texto claro que descreva o destino
- **Estado visível**: Indicar claramente o item ativo/selecionado
- **Organização lógica**: Agrupar itens relacionados

## Técnicas de Codificação

### Estrutura Semântica Correta

A base para menus acessíveis é usar os elementos HTML adequados que comunicam naturalmente a sua função.

#### Uso do elemento `<nav>`

O elemento `<nav>` identifica explicitamente uma secção como navegação:

```html
<nav aria-label="Menu principal">
  <!-- Conteúdo do menu -->
</nav>
```

Se houver múltiplos menus na página, é importante diferenciar cada um com `aria-label`:

```html
<nav aria-label="Menu principal">
  <!-- Conteúdo do menu principal -->
</nav>

<nav aria-label="Menu do rodapé">
  <!-- Links do rodapé -->
</nav>
```

#### Listas para Itens de Menu

Utilizar uma estrutura de lista comunica aos leitores de ecrã o número total de itens e a posição atual durante a navegação:

```html
<nav aria-label="Menu principal">
  <ul>
    <li><a href="inicio.html" aria-current="page">Início</a></li>
    <li><a href="produtos.html">Produtos</a></li>
    <li><a href="servicos.html">Serviços</a></li>
    <li><a href="contactos.html">Contactos</a></li>
  </ul>
</nav>
```

Quando um leitor de ecrã encontra esta estrutura, anunciará "Menu principal, lista com 4 itens" e depois, ao navegar, indicará "item 1 de 4", "item 2 de 4", etc., proporcionando contexto sobre a posição atual.

#### Estruturas para Menus Multinível

Para menus com submenus, a estrutura aninhada de listas mantém a relação hierárquica:

```html
<nav aria-label="Menu principal">
  <ul>
    <li><a href="produtos.html">Produtos</a>
      <ul>
        <li><a href="hardware.html" aria-current="page">Hardware</a></li>
        <li><a href="software.html">Software</a></li>
      </ul>
    </li>
    <li><a href="servicos.html">Serviços</a></li>
  </ul>
</nav>
```

### Rotulagem Adequada

Rótulos claros são fundamentais para que todos os utilizadores, incluindo aqueles com tecnologias de apoio, compreendam o propósito e o destino de cada item de menu.

#### Texto de Links Descritivo

Evite texto genérico como "Clique aqui" ou "Saiba mais". Use texto que faça sentido mesmo fora de contexto:

```html
<!-- Mau exemplo -->
<a href="contactos.html">Clique aqui</a>

<!-- Bom exemplo -->
<a href="contactos.html">Contacte-nos</a>
```

#### Indicação de Estado Atual

Indique claramente o item ativo ou a página atual:

```html
<nav aria-label="Menu principal">
  <ul>
    <li><a href="inicio.html">Início</a></li>
    <li><a href="produtos.html" aria-current="page">Produtos</a></li>
    <li><a href="servicos.html">Serviços</a></li>
  </ul>
</nav>
```

O atributo `aria-current="page"` informa tecnologias de apoio que este é o item correspondente à página atual.

### Apresentação Visual Acessível

A apresentação visual afeta significativamente a usabilidade para utilizadores com deficiência visual parcial, dificuldades cognitivas ou motoras.

#### Contraste Adequado

Mantenha sempre o contraste mínimo de 4.5:1 entre texto e fundo para texto normal, e 3:1 para texto grande:

```css
/* Exemplo com bom contraste */
.menu {
  background-color: #ffffff;
}

.menu a {
  color: #333333; /* Contraste aproximado de 10:1 */
}

/* Exemplo com contraste insuficiente */
.menu-mau-exemplo {
  background-color: #eeeeee;
}

.menu-mau-exemplo a {
  color: #999999; /* Contraste aproximado de 2.5:1 - insuficiente */
}
```

#### Indicador de Foco Visível

O indicador de foco deve ser claramente visível, ajudando tanto utilizadores de teclado como pessoas com baixa visão:

```css
/* Indicador de foco melhorado */
.menu a:focus {
  outline: 3px solid #1a85ff;
  outline-offset: 2px;
}
```

#### Espaçamento Adequado

Providencie áreas de clique suficientemente grandes e bem espaçadas para utilizadores com dificuldades motoras:

```css
.menu li {
  margin-bottom: 8px;
}

.menu a {
  display: block;
  padding: 12px 16px;
  min-height: 44px;  /* Altura mínima recomendada para áreas táteis */
  min-width: 44px;  /* Largura mínima recomendada para áreas táteis */
}
```

Áreas de clique maiores (recomendado mínimo de 44x44 pixels) são mais fáceis de alcançar para utilizadores com tremores ou precisão limitada.

#### Consistência Visual

Mantenha padrões consistentes de design em todo o site:

```css
/* Estilo consistente para todos os menus */
.menu a,
.submenu a,
.footer-menu a {
  padding: 10px 15px;
  border-radius: 4px;
  transition: background-color 0.2s;
}

.menu a:hover,
.submenu a:hover,
.footer-menu a:hover {
  background-color: #f0f0f0;
}

.menu [aria-current="page"] ˚{
  font-weight: bold;
  border-bottom: 2px solid #0074d9;
}
```

### Implementação de ARIA para Menus Complexos

Para menus mais complexos, como acordeões ou menus expansíveis, os atributos ARIA são essenciais:

```html
<nav aria-label="Menu principal">
  <ul>
    <li>
      <button aria-expanded="false" aria-controls="submenu-produtos">
        Produtos
      </button>
      <ul id="submenu-produtos" hidden>
        <li><a href="hardware.html">Hardware</a></li>
        <li><a href="software.html">Software</a></li>
      </ul>
    </li>
  </ul>
</nav>
```

O JavaScript associado deve atualizar o valor de `aria-expanded` e a visibilidade do submenu conforme o utilizador interage:

```javascript
const menuButton = document.querySelector('button[aria-controls="submenu-produtos"]');
const submenu = document.getElementById('submenu-produtos');

menuButton.addEventListener('click', () => {
  const expanded = menuButton.getAttribute('aria-expanded') === 'true';
  menuButton.setAttribute('aria-expanded', !expanded);
  submenu.hidden = expanded;
});
```

## Recomendações para Conteúdo Acessível

### Organização Lógica e Hierárquica

- **Limite o número de itens**: Idealmente, não mais de 7±2 itens no menu principal (baseado na capacidade de memória de trabalho humana).
- **Agrupe itens relacionados**: Utilize submenus ou seções para organizar conteúdo similar.
- **Siga padrões convencionais**: Coloque itens comuns (como "Contacto" ou "Sobre Nós") onde os utilizadores esperam encontrá-los.

**Exemplo**: Comparação entre um menu desorganizado e um organizado:

```
Menu desorganizado:
- Contactos
- Produtos Hardware
- Sobre Nós
- Serviços Cloud
- Equipa
- Software Empresarial
- História da Empresa
- Produtos Software

Menu organizado:
- Sobre Nós
  - História da Empresa
  - Equipa
- Produtos
  - Hardware
  - Software
  - Software Empresarial
- Serviços
  - Cloud
- Contactos
```

O segundo exemplo agrupa logicamente os itens relacionados, reduzindo a carga cognitiva.

### Rótulos Claros e Concisos

- **Seja específico mas conciso**: 1 a 3 palavras é o ideal para itens de menu.
- **Evite jargão**: Use termos que todos os utilizadores compreendam.
- **Seja consistente**: Use o mesmo termo para o mesmo conceito em todo o site.

**Exemplo de melhoria de rótulos**:

```
Rótulos originais:
- Inicie o Processo de Contacto Connosco
- Visualize Todos os Nossos Serviços Disponíveis 
- Área de Download de Ficheiros e Recursos

Rótulos melhorados:
- Contacte-nos
- Serviços
- Downloads
```

### Apresentação Consistente

- **Mantenha o menu no mesmo local**: Não mude a posição do menu entre páginas.
- **Preserve ordem e estrutura**: Mantenha a consistência na ordem dos itens em todas as páginas.
- **Use estados visuais distintos**: Diferente para normal, hover, focus, active e visited.

**Exemplo visual**:

Imagine um menu que muda de posição ou aparência entre páginas. O utilizador terá que reaprender a navegação em cada página, aumentando a carga cognitiva e reduzindo a eficiência.

### Métricas Importantes

- **Tamanho mínimo dos alvos de toque**: 44x44 pixels CSS.
- **Contraste mínimo**: 4.5:1 para texto normal, 3:1 para texto grande (18pt ou 14pt negrito).

### Erros Comuns

#### 1. Falta de Estrutura Semântica

**Erro**:

```html
<div class="main-menu">
  <div class="menu-item"><a href="inicio.html">Início</a></div>
  <div class="menu-item"><a href="produtos.html">Produtos</a></div>
</div>
```

**Porque é problemático**: Não comunica a natureza de navegação do elemento nem a relação entre os itens para tecnologias de apoio.

**Solução**: Usar elementos semânticos adequados:

```html
<nav aria-label="Menu principal">
  <ul>
    <li><a href="inicio.html">Início</a></li>
    <li><a href="produtos.html">Produtos</a></li>
  </ul>
</nav>
```

#### 2. Contraste Insuficiente

**Erro**:

```css
.menu {
  background-color: #e0e0e0;
}
.menu a {
  color: #a0a0a0; /* Contraste aproximado de 1.8:1 */
}
```

**Porque é problemático**: Texto com baixo contraste é difícil ou impossível de ler para pessoas com baixa visão ou daltonismo.

**Solução**: Garantir contraste mínimo de 4.5:1:

```css
.menu {
  background-color: #e0e0e0;
}
.menu a {
  color: #505050; /* Contraste melhorado para aproximadamente 5.7:1 */
}
```

#### 3. Rótulos Genéricos ou Ambíguos

**Erro**:

```html
<nav>
  <ul>
    <li><a href="p1.html">Página 1</a></li>
    <li><a href="p2.html">Clique aqui</a></li>
    <li><a href="p3.html">Mais informações</a></li>
  </ul>
</nav>
```

**Porque é problemático**: Rótulos genéricos não comunicam o destino ou propósito do link, especialmente para utilizadores de leitores de ecrã que podem navegar por listas de links fora de contexto.

**Solução**: Usar rótulos descritivos e específicos:

```html
<nav>
  <ul>
    <li><a href="inicio.html">Página inicial</a></li>
    <li><a href="produtos.html">Catálogo de produtos</a></li>
    <li><a href="suporte.html">Suporte técnico</a></li>
  </ul>
</nav>
```

#### 4. Indicador de Foco Invisível ou Insuficiente

**Erro**:

```css
.menu a:focus {
  outline: none; /* Remove o indicador de foco padrão */
}
```

**Porque é problemático**: Sem um indicador de foco visível, utilizadores de teclado não conseguem saber qual elemento está atualmente selecionado.

**Solução**: Manter ou melhorar (nunca remover) o indicador de foco:

```css
.menu a:focus {
  outline: 3px solid #1a85ff;
  outline-offset: 2px;
  background-color: #f0f0f0;
}
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Estrutura adequada**:
   - Use elementos semânticos como `<nav>`, `<ul>` e `<li>`
   - Identifique claramente as regiões de navegação
   - Mantenha hierarquia clara e lógica

2. **Rotulagem clara**:
   - Crie rótulos descritivos e concisos
   - Evite termos genéricos ou ambíguos
   - Use `aria-current="page"` para indicar a página atual

3. **Apresentação acessível**:
   - Garanta contraste adequado (mínimo 4.5:1)
   - Forneça áreas de clique suficientemente grandes (mínimo 44x44px)
   - Mantenha indicadores de foco visíveis e distintos

4. **Benefícios da acessibilidade em menus**:
   - Melhora a experiência para todos os utilizadores
   - Permite navegação eficiente por diversos dispositivos e métodos de entrada
   - Facilita o acesso à informação para pessoas com diferentes capacidades

### Exercícios Práticos

#### Exercício 1: Análise de Menu Existente

**Objetivo**: Avaliar a acessibilidade de um menu existente.

**Instruções**:

1. Escolha um website que use frequentemente
2. Examine o menu principal do site usando apenas o teclado (Tab, Shift+Tab, Enter)
3. Verifique se:
   - Todos os itens são acessíveis por teclado
   - O indicador de foco é claramente visível
   - A estrutura do menu é lógica e compreensível
4. Utilize uma ferramenta de verificação de contraste para verificar se o texto do menu tem contraste suficiente. Verifique em todos os estados possíveis dos itens do menu (focus, hover, expanded).
5. Se possível, teste com um leitor de ecrã gratuito (como o NVDA ou VoiceOver)
6. Documente os problemas encontrados e sugira soluções

#### Exercício 2: Correção de Menu Inacessível

**Objetivo**: Praticar a melhoria de um menu com problemas de acessibilidade.

**Código inicial**:

```html
<div class="topnav">
  <a href="index.html" class="active">Home</a>
  <a href="news.html">News</a>
  <a href="#" onmouseover="showSubmenu()">Products</a>
  <div id="productSubmenu" style="display:none;">
    <a href="product1.html">Product 1</a>
    <a href="product2.html">Product 2</a>
  </div>
  <a href="about.html">About</a>
  <a href="contact.html">Contact</a>
</div>

<style>
.topnav {
  background-color: #333;
  overflow: hidden;
}
.topnav a {
  float: left;
  color: #b3b3b3;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}
.topnav a:hover {
  background-color: #444;
}
.topnav a:focus {
  outline: none;
}
.topnav a.active {
  background-color: #444;
  color: white;
}
</style>
```

**Instruções**:

1. Reescreva o HTML para usar estrutura semântica adequada
2. Corrija o contraste do texto
3. Implemente um submenu acessível por teclado
4. Adicione indicadores de foco visíveis
5. Adicione atributos ARIA apropriados onde necessário
6. Teste a sua solução com navegação por teclado

#### Exercício 3: Criação de Menu Totalmente Acessível

**Objetivo**: Criar um menu de navegação totalmente acessível desde o início.

**Instruções**:

1. Crie um menu principal com pelo menos 4 itens
2. Inclua pelo menos um submenu
3. Implemente:
   - Estrutura semântica adequada
   - Navegação completa por teclado
   - Indicadores visuais claros para todos os estados
   - Rótulos descritivos e concisos
   - Atributos ARIA onde necessário
4. Teste em diferentes cenários:
   - Navegação por teclado
   - Verificação de contraste
   - Redimensionamento da janela (responsividade)
   - Se possível, teste com um leitor de ecrã
