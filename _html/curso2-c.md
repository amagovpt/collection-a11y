---
lang: pt
---

# Landmarks

## Introdução

Os landmarks (pontos de referência) são como a planta de um edifício - ajudam as pessoas a entender onde estão e como navegar pelo espaço. No contexto web, landmarks são elementos HTML que definem as diferentes áreas funcionais de uma página.

### Como as Pessoas com Deficiência Usam Landmarks

Imagine entrar num supermercado desconhecido. A experiência é muito mais fácil se houver sinais claros indicando onde estão as diferentes secções: padaria, frutas e legumes, caixa, etc. Os landmarks funcionam de maneira similar numa página web.

#### Estratégias de Navegação com Landmarks

As pessoas com deficiência usam landmarks de várias formas:

1. **Navegação Rápida**

- Usam teclas de atalho ou gestos para saltar entre diferentes landmarks
- Geram listas de todos os landmarks da página
- Usam landmarks para entender a estrutura geral da página

2. **Orientação**

- Landmarks ajudam a responder a perguntas como:
    - "Onde está o menu principal?"
    - "Onde começa o conteúdo principal?"
    - "Há informação complementar?"

3. **Eficiência**

- Evitam ter que passar por todo o conteúdo
- Saltam diretamente para a área desejada
- Ignoram secções repetitivas (como menus de navegação)

### Requisitos de Acessibilidade

Para garantir que os landmarks são eficazes, eles devem seguir certos requisitos:

1. **Cobertura Completa**

```html
<!-- Bom exemplo -->
<header>
    <nav>Menu de navegação</nav>
</header>
<main>Conteúdo principal</main>
<aside>Conteúdo relacionado</aside>
<footer>Rodapé</footer>

<!-- Mau exemplo -->
<div class="header">Cabeçalho</div>
<div>Conteúdo misturado sem estrutura clara</div>
<div class="footer">Rodapé</div>
```

O bom exemplo tem todas as áreas principais da página claramente identificadas. O mau exemplo deixa áreas sem identificação adequada.

2. **Unicidade**

```html
<!-- Bom exemplo -->
<main>Conteúdo principal único</main>

<!-- Mau exemplo -->
<main>Primeira área principal</main>
<main>Segunda área principal</main>
```

Alguns landmarks, como `<main>`, devem ser únicos na página. Ter múltiplos elementos do mesmo landmark pode confundir os utilizadores.

3. **Nomes Descritivos**

```html
<!-- Bom exemplo -->
<nav aria-label="Menu principal">
    <!-- links de navegação -->
</nav>
<nav aria-label="Menu do rodapé">
    <!-- links de navegação -->
</nav>

<!-- Mau exemplo -->
<nav><!-- links --></nav>
<nav><!-- outros links --></nav>
```

Quando há múltiplos elementos do mesmo tipo (como `<nav>`), eles precisam de rótulos distintos para serem identificáveis.

4. **Hierarquia Lógica**
```html
<!-- Bom exemplo -->
<body>
    <header>
        <nav>Navegação principal</nav>
    </header>
    <main>
        <article>
            <h1>Título principal</h1>
            <!-- conteúdo -->
        </article>
    </main>
    <aside>
        <nav>Links relacionados</nav>
    </aside>
</body>

<!-- Mau exemplo -->
<body>
    <main>Conteúdo principal</main>
    <header>Cabeçalho que deveria estar no topo</header>
</body>
```

A ordem dos landmarks deve refletir a estrutura lógica da página. O mau exemplo tem uma ordem que não faz sentido visualmente nem semanticamente.

Seguindo estes requisitos, os landmarks tornam-se ferramentas poderosas de navegação, beneficiando não apenas pessoas com deficiência, mas todos os utilizadores da página.

## Técnicas de Codificação

Vamos explorar cada elemento landmark e como usá-lo corretamente para criar páginas acessíveis.

### `<header>`

O `<header>` é como a capa de uma revista - contém informações introdutórias sobre o conteúdo que se segue.

```html
<!-- Bom exemplo -->
<header>
    <h1>Blog de Viagens</h1>
    <nav>
        <ul>
            <li><a href="#">Destinos</a></li>
            <li><a href="#">Dicas</a></li>
        </ul>
    </nav>
</header>

<!-- Mau exemplo -->
<div class="header">
    <div class="title">Blog de Viagens</div>
    <!-- sem estrutura de navegação clara -->
</div>
```

O bom exemplo identifica claramente a área de cabeçalho e inclui navegação estruturada. O mau exemplo perde semântica e estrutura.

### `<main>`

O elemento `<main>` é como o corpo principal de um livro - contém o conteúdo central da página.

```html
<!-- Bom exemplo -->
<main>
    <h1>Destinos Populares</h1>
    <article>
        <h2>Paris</h2>
        <!-- conteúdo sobre Paris -->
    </article>
</main>

<!-- Mau exemplo -->
<main>
    <!-- conteúdo de rodapé -->
</main>
<main>
    <!-- conteúdo principal -->
</main>
```

O bom exemplo usa `<main>` corretamente para o conteúdo principal. O mau exemplo viola a regra de ter apenas um `<main>` por página.

### `<nav>`

O `<nav>` é como o índice de um livro - ajuda os utilizadores a encontrar diferentes secções do site.

```html
<!-- Bom exemplo -->
<nav aria-label="Menu principal">
    <ul>
        <li><a href="#home">Início</a></li>
        <li><a href="#produtos">Produtos</a></li>
    </ul>
</nav>

<!-- Mau exemplo -->
<nav>
    <a href="#home">Início</a>
    <a href="#produtos">Produtos</a>
    <p>Texto que não é navegação</p>
</nav>
```

O bom exemplo tem uma estrutura clara e usa um rótulo descritivo. O mau exemplo mistura conteúdo não relacionado com navegação.

### `<footer>`

O `<footer>` é como a contracapa de um livro - contém informações complementares e finais.

```html
<!-- Bom exemplo -->
<footer>
    <nav aria-label="Links do rodapé">
        <ul>
            <li><a href="#privacidade">Política de Privacidade</a></li>
            <li><a href="#acessibilidade">Declaração de Acessibilidade</a></li>
        </ul>
    </nav>
    <p>&copy; 2025 Minha Empresa</p>
</footer>

<!-- Mau exemplo -->
<div class="footer">
    Alguns links e informações
</div>
```

O bom exemplo fornece estrutura e contexto claros. O mau exemplo perde a semântica e não estrutura o conteúdo.

### `<aside>`

O `<aside>` é como uma caixa de texto lateral num livro - contém informação relacionada mas não essencial.

```html
<!-- Bom exemplo -->
<aside aria-label="Informações relacionadas">
    <h2>Artigos Relacionados</h2>
    <ul>
        <li><a href="#">Dica de Viagem</a></li>
    </ul>
</aside>

<!-- Mau exemplo -->
<main>
    <aside>
        <!-- conteúdo principal da página -->
    </aside>
</main>
```

O bom exemplo usa `<aside>` para conteúdo complementar. O mau exemplo usa-o dentro do conteúdo principal, o que não é o propósito semântico do `<aside>`, que existe para apresentar conteúdo complementar ao principal.

### `<section>`

O `<section>` é como um capítulo de um livro - agrupa conteúdo relacionado.

```html
<!-- Bom exemplo -->
<section aria-labelledby="destaques">
    <h2 id="destaques">Produtos em Destaque</h2>
    <!-- conteúdo da secção -->
</section>

<!-- Mau exemplo -->
<section>
    <!-- conteúdo sem título -->
</section>
```

O bom exemplo tem um cabeçalho claro e rótulo descritivo. O mau exemplo não tem estrutura identificável.

### `<article>`

O `<article>` é como um artigo numa revista - contém conteúdo independente e completo.

```html
<!-- Bom exemplo -->
<article>
    <h2>Como Fazer Pão Caseiro</h2>
    <p>Ingredientes necessários...</p>
    <p>Passo a passo...</p>
</article>

<!-- Mau exemplo -->
<article>
    <div>Fragmento de conteúdo</div>
    <!-- sem estrutura ou contexto -->
</article>
```

O bom exemplo contém conteúdo completo e independente. O mau exemplo usa `<article>` para conteúdo fragmentado.

### Landmarks ARIA

ARIA permite criar ou modificar landmarks quando os elementos HTML não são suficientes.

```html
<!-- Bom exemplo - quando não pode usar elementos nativos -->
<div role="search">
    <form>
        <label for="search">Pesquisar:</label>
        <input type="search" id="search">
    </form>
</div>

<!-- Mau exemplo - quando existe elemento nativo -->
<div role="main">
    <!-- use <main> instead -->
</div>
```

O primeiro exemplo usa ARIA para criar um landmark específico que não existe em HTML nativo, enquanto que o segundo exemplo usa ARIA desnecessariamente.

#### Tabela de Roles ARIA e Elementos HTML Equivalentes

| Role ARIA | Descrição | Elemento HTML Nativo | Exemplo com role | Exemplo com elemento nativo |
|-----------|-----------|---------------------|------------------|---------------------------|
| `banner` | Cabeçalho global da página | `<header>` (quando filho direto de `<body>`) | `<div role="banner">` | `<header>` |
| `main` | Conteúdo principal | `<main>` | `<div role="main">` | `<main>` |
| `contentinfo` | Rodapé global da página | `<footer>` (quando filho direto de `<body>`) | `<div role="contentinfo">` | `<footer>` |
| `complementary` | Conteúdo complementar | `<aside>` | `<div role="complementary">` | `<aside>` |
| `navigation` | Área de navegação | `<nav>` | `<div role="navigation">` | `<nav>` |
| `search` | Área de pesquisa | *Nenhum* | `<div role="search">` | - |
| `article` | Conteúdo independente | `<article>` | `<div role="article">` | `<article>` |
| `region` | Secção importante | `<section>` com aria-label/aria-labelledby | `<div role="region" aria-label="...">` | `<section aria-label="...">` |

**Importante**: A melhor prática é usar sempre elementos HTML nativos quando disponíveis. Use roles ARIA apenas quando:

1. Não existe um elemento HTML nativo equivalente
2. Precisa modificar a semântica de um elemento existente
3. Quer criar componentes personalizados complexos

Um elemento HTML nativo já inclui toda a semântica necessária e comportamentos padrão (como foco e interação com teclado) que precisariam de ser implementados de raiz se usar ARIA.

## Recomendações para Conteúdo Acessível

Para criar landmarks verdadeiramente acessíveis, siga as recomendações anteriores e evite os erros comuns.

### Erros Comuns

1. **Duplicação de Landmarks Únicos**
```html
<!-- Erro -->
<main>Área principal 1</main>
<main>Área principal 2</main>

<!-- Correto -->
<main>
    <section>Área principal 1</section>
    <section>Área principal 2</section>
</main>
```

Este erro é como ter dois centros num campo de futebol - causa confusão sobre qual é o ponto principal de referência.

2. **Landmarks sem Identificação**

```html
<!-- Erro -->
<nav>
    <ul>
        <li><a href="#">Link 1</a></li>
    </ul>
</nav>
<nav>
    <ul>
        <li><a href="#">Link 2</a></li>
    </ul>
</nav>

<!-- Correto -->
<nav aria-label="Menu principal">
    <ul>
        <li><a href="#">Link 1</a></li>
    </ul>
</nav>
<nav aria-label="Menu secundário">
    <ul>
        <li><a href="#">Link 2</a></li>
    </ul>
</nav>
```

É como ter várias portas sem placas de identificação num prédio.

3. **Uso Incorreto de Section**
```html
<!-- Erro -->
<section>
    <p>Algum conteúdo sem cabeçalho</p>
</section>

<!-- Correto -->
<section aria-label="Informações de contacto">
    <h2>Contacte-nos</h2>
    <p>Nosso endereço...</p>
</section>
```

Uma section sem identificação é como um capítulo sem título num livro.

4. **Encadeamento Incorreto**
```html
<!-- Erro -->
<main>
    <header>Título da página</header>
    <nav>Menu principal</nav>
</main>

<!-- Correto -->
<header>
    <nav>Menu principal</nav>
</header>
<main>
    <h1>Título da página</h1>
</main>
```

O encadeamento incorreto é como colocar a entrada principal de um prédio dentro de um dos apartamentos.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Os landmarks são essenciais para navegação acessível
- Use elementos HTML nativos sempre que possível
- Forneça identificação clara para landmarks duplicados
- Mantenha uma estrutura lógica e consistente

### Exercícios Práticos

1. **Análise de Landmarks**

Visite três websites diferentes e:

- Identifique todos os landmarks presentes
- Verifique se estão corretamente implementados
- Liste problemas encontrados
- Sugira melhorias

2. **Correção de Estrutura**

Melhore o seguinte código:

   ```html
   <div class="header">
       <div class="nav">Menu</div>
   </div>
   <div class="main">
       Conteúdo principal
       <div class="aside">
           Barra lateral
       </div>
   </div>
   <div class="footer">
       Rodapé
   </div>
   ```

3. **Prática com ARIA Labels**

Crie uma página com:

- Múltiplas áreas de navegação
- Múltiplas secções
- Use aria-label apropriadamente
- Teste com um leitor de ecrã

4. **Avaliação de Acessibilidade**

Para uma página existente:

- Use ferramentas de inspeção do navegador
- Verifique a estrutura dos landmarks
- Teste a navegação por teclado
- Documente problemas encontrados