# Operação com teclado

## Introdução

A operação com teclado é um aspeto fundamental da acessibilidade web. Muitas pessoas não conseguem utilizar o rato ou outros dispositivos apontadores, e dependem do teclado para navegar na Internet. Nesta secção, vamos explorar como criar menus que sejam totalmente operáveis com teclado.

### Como as Pessoas com Deficiência Dependem de Poder Usar Menus com Teclado

Muitos utilizadores dependem exclusivamente do teclado para navegar na web por diversos motivos:

* **Pessoas com deficiências motoras**: Utilizadores com paralisia, tremores, artrite ou lesões por esforço repetitivo podem ter dificuldade ou mesmo impossibilidade de usar um rato.
* **Pessoas com deficiência visual**: Utilizadores cegos ou com baixa visão geralmente usam um leitor de ecrã em conjunto com o teclado para navegar nas páginas web.
* **Pessoas com fadiga crónica ou dores**: Alguns utilizadores acham menos cansativo ou doloroso usar um teclado do que manipular um rato.
* **Utilizadores de tecnologias alternativas**: Pessoas que usam comutadores, teclados adaptados ou sistemas de entrada por voz dependem de uma navegação baseada em teclado bem implementada.

#### Analogia: O Labirinto Invisível

Imagine entrar numa sala escura com apenas uma lanterna pequena que ilumina um ponto de cada vez. Sem poder ver a totalidade do espaço, tem de encontrar a saída movendo-se passo a passo, iluminando apenas o que está imediatamente à sua frente.

Esta é a experiência de muitos utilizadores quando navegam com teclado num site. Não têm uma visão geral do ecrã como teriam com um rato. Em vez disso, movem-se sequencialmente de elemento para elemento, tentando encontrar o caminho para o conteúdo que procuram.

Se um menu não for acessível por teclado, é como se houvesse uma porta invisível na sala escura — uma saída que existe mas que nunca conseguem encontrar ou abrir.

### Requisitos de Acessibilidade para Operação com Teclado de Menus

Para garantir que os menus são acessíveis a todos os utilizadores, devem cumprir os seguintes requisitos:

1. **Acesso completo por teclado**: Todas as opções do menu devem ser acessíveis usando apenas o teclado, sem necessidade de rato.

2. **Indicador de foco visível**: Deve ser claramente visível qual o item que está atualmente em foco quando se navega com o teclado.

3. **Ordem lógica de navegação**: A sequência de tabulação deve seguir uma ordem lógica e previsível.

4. **Sem armadilhas de teclado**: O utilizador nunca deve ficar "preso" num elemento sem poder sair usando o teclado.

5. **Atalhos de teclado adequados**: Os menus devem responder às teclas padrão de navegação (Tab, Enter, Setas, Esc).

6. **Comportamento previsível**: As interações por teclado devem funcionar como os utilizadores esperam, seguindo padrões comuns.

#### Critérios WCAG Relacionados

Estes requisitos alinham-se com os seguintes critérios das Diretrizes de Acessibilidade para Conteúdo Web (WCAG):

* **2.1.1 Teclado** (Nível A): Toda a funcionalidade do conteúdo é operável através de uma interface de teclado.
* **2.1.2 Sem bloqueio de teclado** (Nível A): O foco do teclado não fica bloqueado em nenhum elemento.
* **2.4.3 Ordem de foco** (Nível A): Os componentes recebem o foco numa ordem que preserva o significado e a operabilidade.
* **2.4.7 Foco visível** (Nível AA): Qualquer interface operável por teclado tem um modo de operação com um indicador visível de foco.

## Técnicas de Codificação

### Tornando Menus Acessíveis por Teclado

Vamos explorar diferentes técnicas para criar menus totalmente acessíveis por teclado:

#### 1. Uso Adequado de Elementos HTML Semânticos

Utilize elementos nativos do HTML que já têm suporte a teclado incorporado:

```html
<!-- BOM EXEMPLO: Menu com semântica adequada -->
<nav aria-label="Menu principal">
  <ul>
    <li><a href="inicio.html" aria-current="page">Início</a></li>
    <li><a href="produtos.html">Produtos</a></li>
    <li><a href="servicos.html">Serviços</a></li>
    <li><a href="contacto.html">Contacto</a></li>
  </ul>
</nav>
```

**Porque funciona bem**: Este exemplo utiliza elementos semanticamente corretos (`<nav>`, `<ul>`, `<li>`, `<a>`). As hiperligações (`<a>`) são naturalmente focáveis com o teclado, permitem navegação com a tecla Tab e ativação com a tecla Enter.

#### 2. Implementação de Menus Dropdown Acessíveis

Para menus dropdown mais complexos, precisamos de garantir que também são acessíveis:

```html
<nav aria-label="Menu principal">
  <ul>
    <li>
      <a href="produtos.html" id="produtos-menu">Produtos</a>
      <ul id="submenu-produtos" aria-labelledby="produtos-menu" hidden>
        <li><a href="prod-novos.html">Novos</a></li>
        <li><a href="prod-populares.html">Populares</a></li>
        <li><a href="prod-promocoes.html">Promoções</a></li>
      </ul>
    </li>
    <!-- Outros itens do menu -->
  </ul>
</nav>

<script>
  const menuItem = document.getElementById('produtos-menu');
  const submenu = document.getElementById('submenu-produtos');
  
  // Mostrar submenu ao pressionar Enter ou Space
  menuItem.addEventListener('keydown', (e) => {
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      submenu.hidden = !submenu.hidden;
      
      // Se o submenu estiver visível, mover o foco para o primeiro item
      if (!submenu.hidden) {
        submenu.querySelector('a').focus();
      }
    }
  });
  
  // Navegação com teclas de seta
  submenu.addEventListener('keydown', (e) => {
    const links = Array.from(submenu.querySelectorAll('a'));
    const currentIndex = links.indexOf(document.activeElement);
    
    if (e.key === 'ArrowDown') {
      e.preventDefault();
      const nextIndex = (currentIndex + 1) % links.length;
      links[nextIndex].focus();
    } else if (e.key === 'ArrowUp') {
      e.preventDefault();
      const prevIndex = (currentIndex - 1 + links.length) % links.length;
      links[prevIndex].focus();
    } else if (e.key === 'Escape') {
      e.preventDefault();
      submenu.hidden = true;
      menuItem.focus();
    }
  });
</script>
```

**Porque funciona bem**: Este exemplo implementa um menu dropdown acessível por teclado, com suporte para:

- Abertura do submenu com Enter ou Espaço
- Navegação entre itens do submenu com as teclas de seta
- Fecho do submenu com a tecla Escape
- Retorno do foco ao item principal quando o submenu é fechado

#### 3. Utilização de WAI-ARIA para Menus Complexos

Para menus mais complexos, os atributos WAI-ARIA (Accessible Rich Internet Applications) são essenciais:

```html
<nav aria-label="Menu principal">
  <ul role="menubar">
    <li role="none">
      <button role="menuitem" aria-haspopup="true" aria-expanded="false" id="menu-produtos">
        Produtos
      </button>
      <ul role="menu" aria-labelledby="menu-produtos" hidden>
        <li role="none">
          <a role="menuitem" href="prod-novos.html">Novos</a>
        </li>
        <li role="none">
          <a role="menuitem" href="prod-populares.html">Populares</a>
        </li>
        <li role="none">
          <a role="menuitem" href="prod-promocoes.html">Promoções</a>
        </li>
      </ul>
    </li>
    <!-- Outros itens do menu -->
  </ul>
</nav>
```

**Porque funciona bem**: Este exemplo utiliza funções ARIA específicas para menus (`menubar`, `menuitem`), indicando claramente a estrutura para tecnologias de apoio. O atributo `aria-expanded` informa os utilizadores sobre o estado atual do menu, e `aria-haspopup` indica que há um submenu disponível.

#### 4. Indicador de Foco Visível

É crucial garantir que o foco de teclado seja bem visível:

```css
/* Estilo padrão para links */
nav a {
  padding: 10px 15px;
  text-decoration: none;
  color: #333;
}

/* Estilo para o foco com teclado */
nav a:focus {
  outline: 3px solid #4a90e2;
  outline-offset: 2px;
  background-color: #e9f0fa;
  color: #000;
}

/* Estilo para hover (passagem do rato) - diferente, mas complementar */
nav a:hover {
  background-color: #f0f0f0;
  text-decoration: underline;
}
```

**Porque funciona bem**: Este CSS cria um indicador de foco claro e visível, que é diferente do efeito hover do rato. O outline é espesso e tem uma cor contrastante, tornando-o visível mesmo para utilizadores com baixa visão. O uso de `outline-offset` evita que o contorno se misture com as bordas do elemento.

#### 5. Implementação de Padrões "Skip Link"

Para permitir que os utilizadores de teclado saltem diretamente para o conteúdo principal:

```html
<body>
  <a href="#conteudo-principal" class="skip-link">Saltar para o conteúdo principal</a>
  
  <header>
    <!-- Logótipo, menus, etc. -->
    <nav><!-- Menu de navegação --></nav>
  </header>
  
  <main id="conteudo-principal">
    <!-- Conteúdo principal da página -->
  </main>
</body>

<style>
  .skip-link {
    position: absolute;
    top: -40px;
    left: 0;
    padding: 8px;
    background-color: #fff;
    color: #000;
    z-index: 100;
    transition: top 0.3s;
  }
  
  .skip-link:focus {
    top: 0;
    outline: 3px solid #4a90e2;
  }
</style>
```

**Porque funciona bem**: Este exemplo implementa um "skip link" (ligação de salto) que está visualmente escondido, mas aparece quando recebe o foco do teclado. Isto permite que os utilizadores de teclado saltem diretamente para o conteúdo principal, sem ter de navegar por todos os itens do menu.

## Recomendações para Conteúdo Acessível

Para garantir que os seus menus são verdadeiramente acessíveis por teclado, siga estas recomendações:

### 1. Teste Regularmente com Teclado

Desligue o rato e navegue pelo seu site usando apenas o teclado. Verifique se consegue:

- Aceder a todos os itens do menu usando a tecla Tab
- Ativar links e botões com Enter ou Espaço
- Navegar em submenus usando as teclas de seta
- Sair de menus dropdown com a tecla Escape
- Ver claramente qual o elemento que tem o foco atual

### 2. Implemente Atalhos de Teclado Consistentes

Utilize padrões estabelecidos para a interação com teclado:

- **Tab**: Navegar entre elementos focáveis
- **Enter/Espaço**: Ativar botões ou links
- **Setas**: Navegar entre itens de um mesmo grupo (como submenus)
- **Escape**: Fechar menus, diálogos ou voltar ao nível anterior
- **Home/End**: Ir para o primeiro/último item de uma lista ou menu

### 3. Mantenha uma Ordem de Tabulação Lógica

A ordem pela qual os elementos recebem o foco deve seguir a estrutura visual e lógica da página. Evite usar `tabindex` com valores positivos, pois isso pode causar problemas na ordem de navegação.

### 4. Forneça Alternativas para Interações Complexas

Se o seu menu tiver interações complexas baseadas em rato (como hover para abrir submenus), garanta que existe uma alternativa funcional para utilizadores de teclado.

### 5. Teste com Tecnologias de Apoio

Utilize leitores de ecrã e outras tecnologias de apoio para verificar se os seus menus são realmente utilizáveis e se comunicam adequadamente o seu estado e estrutura.

### Erros Comuns

Evite estes erros frequentes que comprometem a acessibilidade por teclado dos menus:

#### 1. Elementos Não Focáveis

**Problema**: Usar elementos que não recebem naturalmente o foco do teclado (como `<div>` ou `<span>`) para criar itens de menu clicáveis.

**Exemplo incorreto**:
```html
<div class="menu">
  <div class="menu-item" onclick="irParaPagina('inicio.html')">Início</div>
  <div class="menu-item" onclick="irParaPagina('sobre.html')">Sobre</div>
</div>
```

**Solução**: Use elementos nativamente focáveis como `<a>` ou `<button>`, ou adicione `tabindex="0"` e tratamento de eventos de teclado adequados.

#### 2. Ausência de Indicador de Foco

**Problema**: Remover ou tornar invisível o outline padrão do navegador sem fornecer uma alternativa.

**Exemplo incorreto**:
```css
*:focus {
  outline: none; /* Má prática! */
}
```

**Solução**: Nunca remova o indicador de foco sem substituí-lo por outro visualmente distinto.

#### 3. Dependência de Eventos Exclusivos de Rato

**Problema**: Menus que dependem de eventos como `mouseover`, `mouseout` ou `hover` para funcionar.

**Exemplo incorreto**:
```javascript
menuItem.addEventListener('mouseover', () => {
  submenu.style.display = 'block';
});

menuItem.addEventListener('mouseout', () => {
  submenu.style.display = 'none';
});
```

**Solução**: Implemente eventos equivalentes para teclado (focus, keydown) além dos eventos de rato.

#### 4. Armadilhas de Teclado

**Problema**: Situações em que o utilizador fica "preso" dentro de um componente sem poder navegar para fora dele usando apenas o teclado.

**Solução**: Garanta sempre que é possível sair de qualquer componente interativo usando o teclado, tipicamente com a tecla Tab ou Escape.

#### 5. Ordem de Tabulação Ilógica

**Problema**: Uso inadequado de `tabindex` com valores positivos, criando uma ordem de navegação confusa.

**Exemplo incorreto**:
```html
<nav>
  <a href="contacto.html" tabindex="3">Contacto</a>
  <a href="inicio.html" tabindex="1">Início</a>
  <a href="sobre.html" tabindex="2">Sobre</a>
</nav>
```

**Solução**: Estruture o HTML de forma lógica e evite valores positivos de `tabindex`. Use `tabindex="0"` para elementos que precisam ser focáveis mas não são nativamente, e `tabindex="-1"` para elementos que devem receber foco apenas via JavaScript.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

Neste capítulo, aprendemos:

1. **Importância da acessibilidade por teclado**: Muitos utilizadores dependem exclusivamente do teclado para navegar na web, incluindo pessoas com deficiências motoras, visuais ou utilizadores de tecnologias de apoio.

2. **Requisitos fundamentais**: Os menus acessíveis por teclado devem ser totalmente navegáveis, ter um indicador de foco visível, seguir uma ordem lógica e não conter armadilhas de teclado.

3. **Técnicas de codificação**:
   - Usar elementos HTML semânticos
   - Implementar suporte adequado a eventos de teclado
   - Utilizar atributos WAI-ARIA para melhorar a comunicação com tecnologias de apoio
   - Garantir indicadores de foco visíveis
   - Implementar padrões como "skip links"

4. **Erros comuns a evitar**:
   - Elementos não focáveis
   - Ausência de indicador de foco
   - Dependência exclusiva de eventos de rato
   - Armadilhas de teclado
   - Ordem de tabulação ilógica

5. **Padrões de interação**: Respeitar os atalhos de teclado padrão (Tab, Enter/Espaço, Setas, Escape) para criar interfaces previsíveis.

### Exercícios Práticos

#### Exercício 1: Análise de Acessibilidade por Teclado

**Objetivo**: Avaliar a acessibilidade por teclado de um site existente.

**Instruções**:

1. Escolha um site que utilize regularmente (ex: um portal de notícias, loja online ou site de serviços públicos).
2. Desligue o seu rato ou touchpad.
3. Tente navegar pelo site utilizando apenas o teclado (Tab, Shift+Tab, Enter, Setas, Escape).
4. Tome nota dos problemas encontrados:
   - Consegue aceder a todos os menus e submenus?
   - O indicador de foco é claramente visível?
   - Existem elementos que não consegue aceder ou ativar?
   - Há alguma "armadilha" onde fique preso sem conseguir sair com o teclado?
5. Escreva um breve relatório com os problemas identificados e sugestões de melhoria.

#### Exercício 2: Transformação de um Menu Não Acessível

**Objetivo**: Tornar acessível por teclado um menu originalmente não acessível.

**Instruções**:

1. Utilize o código inicial abaixo, que representa um menu dropdown não acessível por teclado:

```html
<div class="menu">
  <div class="menu-item">
    Produtos
    <div class="submenu">
      <div class="submenu-item" onclick="location.href='novos.html'">Novos</div>
      <div class="submenu-item" onclick="location.href='populares.html'">Populares</div>
      <div class="submenu-item" onclick="location.href='promocoes.html'">Promoções</div>
    </div>
  </div>
  <div class="menu-item" onclick="location.href='servicos.html'">Serviços</div>
  <div class="menu-item" onclick="location.href='contacto.html'">Contacto</div>
</div>

<style>
  .menu {
    display: flex;
    gap: 20px;
  }
  .menu-item {
    position: relative;
    cursor: pointer;
    padding: 10px;
  }
  .submenu {
    display: none;
    position: absolute;
    left: 0;
    top: 100%;
    background: white;
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
  }
  .menu-item:hover .submenu {
    display: block;
  }
  .submenu-item {
    padding: 10px;
    cursor: pointer;
  }
  .submenu-item:hover {
    background: #f0f0f0;
  }
</style>
```

2. Transforme este código para ser totalmente acessível por teclado, aplicando os princípios e técnicas aprendidos neste capítulo.
3. Garanta que:
   - Todos os itens de menu são focáveis com Tab
   - É possível abrir o submenu com teclado
   - É possível navegar entre os itens do submenu com as teclas de seta
   - É possível fechar o submenu com Escape
   - Existe um indicador de foco visível

#### Exercício 3: Criação de um Menu Acessível com ARIA

**Objetivo**: Criar um menu de navegação complexo totalmente acessível, utilizando atributos WAI-ARIA.

**Instruções**:

1. Crie um menu de navegação com pelo menos dois níveis (menu principal e submenus).
2. Implemente suporte completo para navegação por teclado.
3. Use atributos WAI-ARIA apropriados para melhorar a semântica e comunicação com tecnologias de apoio.
4. Inclua um "skip link" para saltar diretamente para o conteúdo principal.
5. Teste a sua implementação utilizando apenas o teclado.
6. Se possível, teste também com um leitor de ecrã para verificar se a estrutura e estado do menu são corretamente anunciados.

#### Exercício 4: Depuração e Correção

**Objetivo**: Identificar e corrigir problemas de acessibilidade por teclado num código existente.

**Instruções**:

1. Analise o seguinte código que contém vários problemas de acessibilidade por teclado:

```html
<nav class="main-nav">
  <div class="logo" onclick="location.href='index.html'">
    <img src="logo.png" alt="">
  </div>
  <div class="nav-items">
    <div class="nav-item">
      <span class="item-text">Produtos</span>
      <div class="dropdown">
        <a href="cat1.html">Categoria 1</a>
        <a href="cat2.html">Categoria 2</a>
        <a href="cat3.html">Categoria 3</a>
      </div>
    </div>
    <div class="nav-item">
      <span class="item-text">Serviços</span>
    </div>
    <div class="nav-item">
      <span class="item-text">Contacto</span>
    </div>
  </div>
</nav>

<style>
  .nav-item {
    cursor: pointer;
    padding: 10px 15px;
  }
  .dropdown {
    display: none;
    position: absolute;
  }
  .nav-item:hover .dropdown {
    display: block;
  }
  a:focus {
    outline: none;
  }
</style>
```

2. Identifique todos os problemas de acessibilidade por teclado presentes no código.
3. Corrija os problemas encontrados, aplicando as técnicas aprendidas no capítulo.
4. Teste a sua solução, garantindo que o menu é totalmente acessível por teclado.