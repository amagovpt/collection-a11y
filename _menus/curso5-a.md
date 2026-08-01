---
title: Introdução
layout: default
nav_order: 1
---

# Menus

## Introdução

Os menus de navegação são elementos fundamentais em qualquer website ou aplicação. Funcionam como mapas que orientam os utilizadores pelo conteúdo digital. Para muitas pessoas, clicar num menu é um gesto simples, mas para pessoas com deficiência, navegar por menus pode apresentar desafios significativos se estes não forem desenvolvidos de forma acessível.

### Como as Pessoas com Deficiência usam Menus de Navegação

Diferentes grupos de utilizadores interagem com menus de formas distintas, dependendo das suas capacidades e das tecnologias de apoio que utilizam:

#### Utilizadores de leitores de ecrã

Os leitores de ecrã convertem o texto em fala ou braille, permitindo que pessoas cegas ou com baixa visão naveguem pela internet. Estes utilizadores:

- Navegam sequencialmente através do conteúdo, geralmente usando o teclado
- Dependem de uma estrutura HTML semântica para compreender a hierarquia do menu
- Precisam que os links tenham descrições claras e significativas

**Exemplo:** 
Imagine um leitor de ecrã a anunciar: "Menu de navegação principal com 5 itens. Link: Início. Link: Produtos. Link: Sobre Nós..." versus "Link clique aqui. Link saiba mais. Link página 2."

**Explicação:** No primeiro exemplo, o utilizador sabe que está num menu de navegação com 5 opções, enquanto que no segundo, não tem contexto sobre onde está ou para onde os links o levarão.

#### Utilizadores apenas com teclado

Muitas pessoas com limitações motoras não conseguem usar um rato e dependem exclusivamente do teclado:

- Navegam usando a tecla Tab para avançar entre elementos interativos
- Necessitam de indicadores visuais de foco claros
- Precisam aceder a todas as funcionalidades sem usar o rato

#### Pessoas com baixa visão

Utilizadores com baixa visão podem:

- Aumentar o texto significativamente
- Usar tecnologias de alto contraste
- Necessitar de espaçamento adequado entre itens do menu

#### Pessoas com deficiências cognitivas

Este grupo beneficia de:

- Organização clara e consistente dos menus
- Terminologia simples e direta
- Número limitado de opções para reduzir a sobrecarga cognitiva

### Requisitos de Acessibilidade para Menus de Navegação

Os requisitos de acessibilidade para menus baseiam-se nos quatro princípios das WCAG (Web Content Accessibility Guidelines):

#### 1. Percetível

- Os menus devem ser claramente identificáveis como elementos de navegação
- Devem ter contraste suficiente entre texto e fundo
- Não devem depender apenas da cor para transmitir informação

#### 2. Operável

- Todos os itens do menu devem ser acessíveis através do teclado
- Deve existir uma forma de saltar o menu (skip navigation)
- O tempo de resposta deve ser ajustável para utilizadores que precisam de mais tempo

#### 3. Compreensível

- A localização e funcionamento dos menus devem ser consistentes e previsíveis
- Os itens do menu devem ter nomes claros e descritivos
- Devem existir indicações claras da localização atual do utilizador no site

#### 4. Robusto

- Os menus devem funcionar em diferentes navegadores e com tecnologias de apoio
- Devem utilizar marcação HTML semântica adequada
- Devem adaptar-se a diferentes tamanhos de ecrã e orientações

## Técnicas de Codificação

### Estrutura Semântica Básica

Uma estrutura semântica correta é o alicerce de um menu acessível. Utilize sempre elementos HTML adequados à função:

```html
<nav aria-label="Menu principal">
  <ul>
    <li><a href="/">Início</a></li>
    <li><a href="/produtos">Produtos</a></li>
    <li><a href="/servicos">Serviços</a></li>
    <li><a href="/contacto">Contacto</a></li>
  </ul>
</nav>
```

**Explicação:** Esta estrutura:

- Utiliza a tag `<nav>` para identificar a área de navegação
- O atributo `aria-label` fornece um nome acessível ao menu
- A estrutura de lista (`<ul>` e `<li>`) cria uma relação semântica adequada
- Links (`<a>`) são usados para os itens do menu, não botões ou divs

### Indicação da Página Atual

É importante que os utilizadores saibam onde estão no site:

```html
<nav aria-label="Menu principal">
  <ul>
    <li><a href="/">Início</a></li>
    <li><a href="/produtos">Produtos</a></li>
    <li><a href="/servicos" aria-current="page">Serviços</a></li>
    <li><a href="/contacto">Contacto</a></li>
  </ul>
</nav>
```

**Explicação:** O atributo `aria-current="page"` indica aos utilizadores de tecnologias de apoio qual é a página atual, complementando a indicação visual.

### Skip Navigation

Para utilizadores de teclado, navegar por menus extensos pode ser cansativo. Uma ligação para saltar a navegação é essencial:

```html
<a href="#conteudo-principal" class="skip-link">Saltar para o conteúdo principal</a>
<nav aria-label="Menu principal">
  <!-- Itens do menu -->
</nav>
<main id="conteudo-principal">
  <!-- Conteúdo principal -->
</main>
```

```css
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: #000;
  color: white;
  padding: 8px;
  z-index: 100;
}

.skip-link:focus {
  top: 0;
}
```

**Explicação:** Esta técnica:

- Cria um link invisível que aparece apenas quando recebe foco
- Permite aos utilizadores de teclado saltar diretamente para o conteúdo principal
- Evita a necessidade de percorrer todos os itens do menu em cada página

### Menus Responsivos com Botão Hambúrguer

Para ecrãs pequenos, os menus frequentemente colapsam num "botão hambúrguer". Eis como torná-lo acessível:

```html
<nav aria-label="Menu principal">
  <button aria-expanded="false" aria-controls="menu-principal" class="menu-toggle">
    Menu <span class="sr-only">principal</span>
    <span aria-hidden="true" class="icon-menu">☰</span>
  </button>
  <ul id="menu-principal" hidden>
    <!-- Itens do menu -->
  </ul>
</nav>
```

```javascript
document.querySelector('.menu-toggle').addEventListener('click', function() {
  const expanded = this.getAttribute('aria-expanded') === 'true';
  this.setAttribute('aria-expanded', !expanded);
  document.getElementById('menu-principal').hidden = expanded;
});
```

**Explicação:**

- `aria-expanded` informa os utilizadores se o menu está aberto ou fechado
- `aria-controls` associa o botão ao menu que controla
- A classe `sr-only` (screen reader only) permite texto adicional para leitores de ecrã sem afetar o visual
- O atributo `hidden` oculta o menu quando fechado
- O JavaScript atualiza estes estados quando o botão é acionado

### Utilização de ARIA quando necessário

Em menus mais complexos, os atributos ARIA podem ser necessários:

```html
<nav aria-label="Menu principal">
  <ul>
    <li>
      <a href="/produtos" aria-haspopup="true" aria-expanded="false">Produtos</a>
      <ul aria-label="Submenu de produtos" hidden>
        <li><a href="/produtos/categoria1">Categoria 1</a></li>
        <li><a href="/produtos/categoria2">Categoria 2</a></li>
      </ul>
    </li>
    <!-- Outros itens do menu -->
  </ul>
</nav>
```

**Explicação:**

- `aria-haspopup` indica que o link abre um submenu
- `aria-expanded` informa se o submenu está aberto ou fechado
- O submenu tem o seu próprio `aria-label` para identificação

## Recomendações para Conteúdo Acessível

### 1. Organização Clara e Lógica

Organize os menus de forma lógica e previsível:

- Agrupe itens relacionados
- Limite o número de itens em cada nível (idealmente 7±2)
- Use categorias claras e mutuamente exclusivas

**Analogia:** Um menu bem organizado é como uma boa biblioteca — os livros estão organizados por categorias lógicas, com sinalização clara, facilitando encontrar o que se procura mesmo na primeira visita.

### 2. Consistência em Todo o Site

Mantenha uma localização e estrutura consistentes:

- Posicione os menus no mesmo local em todas as páginas
- Use os mesmos termos para as mesmas funções
- Mantenha um padrão visual consistente

**Analogia:** É como os supermercados que mantêm uma disposição consistente — uma vez que aprende onde estão os produtos, pode encontrá-los facilmente em qualquer visita subsequente.

### 3. Indicadores Visuais Claros

Forneça feedback visual sobre a interação:

- Estados de foco visíveis (contorno forte ao receber foco via teclado)
- Indicação da página atual
- Mudanças de estado claras para hover/foco

```css
/* Indicador de foco visível */
a:focus {
  outline: 3px solid #1a6cb4;
  outline-offset: 2px;
}

/* Indicador da página atual */
[aria-current="page"] {
  font-weight: bold;
  border-bottom: 3px solid #1a6cb4;
}
```

**Explicação:** Estes estilos fornecem indicações visuais claras que beneficiam todos os utilizadores, mas são essenciais para pessoas com baixa visão ou utilizadores de teclado.

### 4. Considere Diferentes Contextos de Uso

- Certifique-se de que o menu funciona com zoom até 200%
- Teste o menu em diferentes dispositivos e orientações
- Verifique a funcionalidade sob condições extremas (alto contraste, conversão para escala de cinza)

### Erros Comuns

#### 1. Usar Elementos Não-Interativos como Botões

**Erro:** 
```html
<div class="menu-button" onclick="toggleMenu()">Menu</div>
```

**Correção:**
```html
<button type="button" class="menu-button" onclick="toggleMenu()">Menu</button>
```

**Explicação:** `<div>` não é nativamente focável ou acionável via teclado. Elementos como `<button>` têm comportamentos de acessibilidade integrados.

#### 2. Dependência Exclusiva do Rato

**Erro:** Menus que só abrem com hover (rato sobre o elemento) e não têm suporte a teclado.

```css
/* Erro: submenu só abre com hover */
.menu-item:hover .submenu {
  display: block;
}
```

**Correção:** Combine hover com foco e adicione suporte a teclado.

```css
/* Correção: submenu abre com hover e foco */
.menu-item:hover .submenu,
.menu-item:focus-within .submenu {
  display: block;
}
```

**Explicação:** `:focus-within` permite que o submenu se mantenha aberto quando qualquer elemento dentro do item de menu recebe foco, suportando navegação por teclado.

#### 3. Ausência de Indicadores da Página Atual

**Erro:** Não fornecer indicação visual ou programática da página atual no menu.

**Correção:** Usar `aria-current="page"` e estilos visuais distintos para a página atual.

**Explicação:** Sem estas indicações, os utilizadores podem perder a orientação no site, especialmente aqueles com deficiências cognitivas ou utilizadores de tecnologias de apoio.

#### 4. Animações Excessivas ou Não Controláveis

**Erro:** Menus com animações rápidas ou que não podem ser desativadas.

**Correção:** Fazer animações subtis, com duração apropriada e respeitar a preferência `prefers-reduced-motion`.

```css
@media (prefers-reduced-motion: reduce) {
  .menu-animation {
    transition: none !important;
  }
}
```

**Explicação:** Animações rápidas podem causar desconforto ou mesmo problemas de saúde em pessoas com determinadas condições.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Estrutura Semântica:** Utilize sempre elementos HTML adequados (`<nav>`, `<ul>`, `<li>`, `<a>`) para menus.

2. **Operabilidade por Teclado:** Todos os menus devem ser totalmente operáveis sem rato.

3. **Indicações Claras:** Forneça feedback visual e programático sobre o estado do menu e a localização atual.

4. **Skip Navigation:** Inclua uma forma de saltar os menus para o conteúdo principal.

5. **Clareza e Consistência:** Organize os menus de forma lógica e mantenha-os consistentes em todo o site.

6. **Adaptabilidade:** Os menus devem funcionar em diferentes dispositivos, tamanhos de ecrã e com tecnologias de apoio.

### Exercícios Práticos

#### Exercício 1: Avaliação de Acessibilidade

1. Escolha três websites que utilize frequentemente.
2. Para cada um, tente navegar utilizando apenas o teclado (sem rato).
3. Responda às seguintes questões:
   - Consegue aceder a todos os itens do menu?
   - É fácil perceber qual item está em foco?
   - Existe um mecanismo para saltar a navegação?
   - É claro qual é a página atual?
4. Documente os problemas encontrados e sugira melhorias.

#### Exercício 2: Corrigir um Menu Inacessível

Corrija o seguinte código para tornar o menu acessível:

```html
<div class="menu">
  <div class="menu-item" onmouseover="showSubmenu('submenu1')">Produtos
    <div id="submenu1" class="submenu">
      <div onclick="location.href='/produtos/categoria1'">Categoria 1</div>
      <div onclick="location.href='/produtos/categoria2'">Categoria 2</div>
    </div>
  </div>
  <div class="menu-item" onclick="location.href='/sobre'">Sobre</div>
  <div class="menu-item" onclick="location.href='/contacto'">Contacto</div>
</div>
```

#### Exercício 3: Criar um Menu Responsivo e Acessível

Desenvolva um menu de navegação que:

1. Utilize HTML semântico adequado
2. Seja totalmente operável por teclado
3. Inclua um mecanismo de "skip navigation"
4. Se adapte a ecrãs pequenos (transformando-se num menu hambúrguer)
5. Indique claramente a página atual
6. Suporte tecnologias de apoio

Teste o seu menu com:

- Navegação exclusivamente por teclado
- Ampliação a 200%
- Um leitor de ecrã (se possível)
- Diferentes dispositivos ou emuladores de diferentes tamanhos de ecrã

#### Exercício 4: Auditoria com Lista de Verificação

Crie uma lista de verificação de acessibilidade específica para menus, baseada nas técnicas e recomendações aprendidas. Use esta lista para avaliar os menus do seu próprio website ou aplicação.
