---
lang: pt
---

# Estrutura e Semântica do HTML

## Introdução

A estrutura e semântica do HTML são fundamentais para criar páginas web acessíveis. Vamos explorar como as pessoas com deficiência navegam na web e porque estes aspetos são tão importantes.

### Como as pessoas com deficiência se orientam numa página

Imagine entrar numa biblioteca onde todos os livros estão empilhados aleatoriamente, sem estantes organizadas, sem sinalizações de secções, e sem um sistema de catalogação. Seria extremamente difícil encontrar o livro que procura, certo? Esta é uma experiência semelhante à que pessoas com deficiência enfrentam quando visitam páginas web mal estruturadas.

As pessoas com deficiência visual, por exemplo, não podem dar uma "vista de olhos rápida" à página para encontrar o que procuram. Em vez disso, dependem de tecnologias de apoio como leitores de ecrã, que leem o conteúdo sequencialmente. Para estas pessoas, uma boa estrutura é como ter um bibliotecário que pode rapidamente guiá-las para a informação que procuram.

Pessoas com deficiência motora podem usar apenas o teclado para navegar. Uma estrutura clara permite-lhes mover-se eficientemente entre diferentes secções da página sem terem que passar por cada elemento individualmente.

### Porque a estrutura e a semântica são essenciais para a acessibilidade?

A estrutura e a semântica do HTML são como a planta de uma página web. Elas fornecem:

1. **Navegação Eficiente**: Uma estrutura clara permite que os utilizadores encontrem rapidamente a informação que procuram, sem terem que processar todo o conteúdo.

2. **Compreensão do Contexto**: A semântica ajuda a entender a função e importância de cada elemento. Por exemplo, um título principal (`<h1>`) indica imediatamente o tema principal da página.

3. **Consistência**: Uma estrutura previsível ajuda os utilizadores a desenvolverem modelos mentais de como a informação está organizada, facilitando a navegação em diferentes páginas do mesmo site.

### Estratégias de navegação usadas por pessoas com deficiência

As pessoas com deficiência utilizam várias estratégias para navegar em páginas web:

**Navegação por Cabeçalhos**

```html
<!-- Bom exemplo -->
<h1>Produtos Sustentáveis</h1>
<h2>Produtos Populares</h2>
<h3>Garrafas Reutilizáveis</h3>
<h3>Sacos de Compras</h3>
<h2>Novidades</h2>

<!-- Mau exemplo -->
<div style="font-size: 24px">Produtos Sustentáveis</div>
<span class="titulo-grande">Produtos Populares</span>
```

O bom exemplo usa elementos de cabeçalho adequados, permitindo que utilizadores de leitores de ecrã naveguem rapidamente entre secções. O mau exemplo usa elementos sem significado semântico, tornando impossível distinguir títulos de conteúdo normal.

**Navegação por Landmarks**

```html
<!-- Bom exemplo -->
<header>
    <nav>Menu principal</nav>
</header>
<main>
    <article>Conteúdo principal</article>
</main>
<aside>Informação relacionada</aside>
<footer>Informação do site</footer>

<!-- Mau exemplo -->
<div class="header">
    <div class="nav">Menu principal</div>
</div>
<div class="main">
    <div class="article">Conteúdo principal</div>
</div>
```

O bom exemplo usa elementos semânticos que criam pontos de referência (landmarks) naturais na página. O mau exemplo usa apenas `<div>`, que não fornece informação sobre a função de cada secção.

**Listas de Links**

Os utilizadores de leitores de ecrã frequentemente recorrem a listas de todos os links numa página para navegação rápida. Por isso é crucial que os links tenham texto descritivo:

```html
<!-- Bom exemplo -->
<a href="contacto.html">Entre em contacto connosco</a>

<!-- Mau exemplo -->
<a href="pg1.html">Clique aqui</a>
```

O bom exemplo fornece contexto claro sobre o destino do link. O mau exemplo força o utilizador a adivinhar para onde o link o levará.

## Técnicas de Codificação

### Separar Estrutura e Estilo

Separar a estrutura (HTML) do estilo (CSS) é como construir uma casa: primeiro criamos a estrutura básica (paredes, teto, portas) e depois decoramos (cores, texturas, acabamentos). Esta separação traz várias vantagens:

1. **Manutenção mais fácil**

```html
<!-- Mau exemplo: Mistura de estrutura e estilo -->
<div style="font-size: 24px; color: blue; margin-top: 20px">
    Título Principal
</div>

<!-- Bom exemplo: Estrutura e estilo separados -->
<h1 class="titulo-principal">
    Título Principal
</h1>
```

No mau exemplo, se precisarmos de mudar o estilo em vários títulos, teremos que editar cada elemento individualmente. No bom exemplo, podemos modificar todos os títulos alterando apenas o CSS.

### Usar Elementos Nativos

Os elementos nativos do HTML são como blocos de LEGO oficiais: foram criados especificamente para uma função e encaixam perfeitamente no sistema. Vamos ver alguns exemplos:

```html
<!-- Mau exemplo: Criar um botão personalizado -->
<div class="botao" onclick="enviarFormulario()">
    Enviar
</div>

<!-- Bom exemplo: Usar o elemento nativo -->
<button type="submit">
    Enviar
</button>
```

O elemento nativo `<button>`:

- Recebe foco automaticamente
- É ativado com teclado (Enter e Espaço)
- Comunica sua função a tecnologias de apoio
- Tem estados visuais predefinidos (hover, focus, active)

Outro exemplo comum:

```html
<!-- Mau exemplo: Lista simulada -->
<div class="lista">
    <div class="item">Primeiro item</div>
    <div class="item">Segundo item</div>
</div>

<!-- Bom exemplo: Lista nativa -->
<ul>
    <li>Primeiro item</li>
    <li>Segundo item</li>
</ul>
```

A lista nativa:

- Comunica automaticamente o número total de itens
- Permite navegação rápida entre itens
- Mantém a relação semântica entre os elementos

### ARIA

ARIA (Accessible Rich Internet Applications) é como um conjunto de etiquetas extras que podemos adicionar ao HTML para melhorar a acessibilidade. É como colocar legendas em objetos numa casa para ajudar os visitantes a entenderem a sua função.

Existem três tipos principais de atributos ARIA:

1. **Roles (Funções)**

```html
<!-- Identificar a função de um elemento -->
<div role="search">
    <input type="text" aria-label="Pesquisar no site">
    <button>Pesquisar</button>
</div>
```

2. **Properties (Propriedades)**

```html
<!-- Adicionar informação extra sobre um elemento -->
<button aria-label="Close" onclick="closeDialog()">✖</button>
```

3. **States (Estados)**

```html
<!-- Comunicar o estado atual de um elemento -->
<button aria-expanded="false" aria-controls="menu">
    Menu Principal
</button>
```

**Importante**: ARIA deve ser usado apenas quando elementos nativos não são suficientes. Como regra:

1. Não usar ARIA é melhor que usar mal
2. Usar elementos nativos é melhor que adicionar ARIA
3. ARIA não modifica o comportamento dos elementos, apenas como são anunciados a tecnologias de apoio

```html
<!-- Mau exemplo: Uso desnecessário de ARIA -->
<button role="button" aria-label="Botão de enviar">
    Enviar
</button>

<!-- Bom exemplo: Elemento nativo é suficiente -->
<button type="submit">
    Enviar
</button>
```

No mau exemplo, o `role="button"` é redundante porque o elemento `<button>` já comunica sua função. O `aria-label` também é desnecessário porque o texto do botão já é claro.

## Recomendações para Conteúdo Acessível

### 1. Estrutura clara e consistente

Imagine uma página web como um livro bem organizado. Assim como um livro tem capítulos, secções e parágrafos, a sua página deve ter uma estrutura clara e previsível:

```html
<!-- Boa estrutura -->
<header>
    <h1>Loja de Plantas</h1>
    <nav>
        <h2>Menu Principal</h2>
        <ul>
            <li><a href="plantas.html">Plantas</a></li>
            <li><a href="acessorios.html">Acessórios</a></li>
        </ul>
    </nav>
</header>
<main>
    <h2>Plantas em Destaque</h2>
    <article>
        <h3>Orquídea Phalaenopsis</h3>
        <!-- conteúdo -->
    </article>
</main>
```

### 2. Use HTML semântico, começando por elementos nativos

Comece sempre por usar elementos HTML nativos antes de considerar ARIA. É como construir uma casa: use materiais padrão testados antes de recorrer a soluções personalizadas:

```html
<!-- Mau exemplo -->
<div class="botao-menu" onclick="toggleMenu()" role="button" tabindex="0">
    Menu
</div>

<!-- Bom exemplo -->
<button type="button" onclick="toggleMenu()">
    Menu
</button>
```

### 3. Mantenha a simplicidade

Não complique desnecessariamente a estrutura do seu código. Uma estrutura simples é mais fácil de manter e geralmente mais acessível:

```html
<!-- Estrutura desnecessariamente complexa -->
<div class="container">
    <div class="wrapper">
        <div class="content-box">
            <span class="text">Bem-vindo ao nosso site</span>
        </div>
    </div>
</div>

<!-- Estrutura simples e eficaz -->
<h1>Bem-vindo ao nosso site</h1>
```

### 4. Teste com diferentes dispositivos

Certifique-se que a sua estrutura funciona bem em diferentes contextos:

- Apenas teclado
- Leitores de ecrã
- Diferentes tamanhos de ecrã
- Diferentes navegadores
- Diferentes dispositivos apontadores

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A estrutura e semântica são fundamentais para a acessibilidade
- Use elementos nativos sempre que possível
- Separe estrutura (HTML) do estilo (CSS)
- Use ARIA apenas quando necessário

### Exercícios Práticos

1. **Análise de Estrutura**

Visite um site à sua escolha e identifique:
   
   - A estrutura de cabeçalhos
   - Os landmarks principais
   - Áreas que poderiam ser melhoradas

2. **Refatoração de Código**
   
Melhore o seguinte código:
   
   ```html
   <div class="header">
       <div class="title">Meu Blog</div>
       <div class="menu">
           <div class="menu-item">Home</div>
           <div class="menu-item">Sobre</div>
       </div>
   </div>
   ```

3. **Criar uma Página Acessível**

Desenvolva uma página simples que inclua:

   - Uma estrutura clara de cabeçalhos
   - Navegação principal
   - Conteúdo principal
   - Rodapé
   - Use apenas elementos semânticos

4. **Teste a Acessibilidade**

Para a página que criou:

   - Navegue usando apenas o teclado
   - Use um leitor de ecrã (como NVDA ou VoiceOver)
   - Verifique a estrutura usando a ferramenta de inspeção do navegador