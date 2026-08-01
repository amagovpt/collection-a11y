# Menus Fly-out

## Introdução

Os menus fly-out (também conhecidos como menus dropdown ou submenus) são elementos de navegação que se expandem para mostrar opções adicionais quando um utilizador interage com eles. Estes menus são muito comuns em sites e aplicações modernas, especialmente para organizar estruturas de navegação complexas em espaços limitados.

Um menu fly-out típico funciona assim:

1. O utilizador ativa um botão ou link principal
2. Um painel ou lista de opções "voa para fora" (daí o nome fly-out), geralmente abaixo ou ao lado do elemento principal
3. O utilizador pode então selecionar uma das opções no submenu

Embora estes menus sejam úteis para organizar conteúdo, podem criar desafios significativos para muitos utilizadores se não forem implementados com acessibilidade em mente.

### Como as Pessoas com Deficiência são Afetadas por Menus Fly-out

#### Utilizadores de Teclado

Para quem navega apenas com teclado (como pessoas com deficiências motoras), os menus fly-out frequentemente apresentam vários problemas:

- **Armadilhas de foco**: Os utilizadores podem ficar "presos" no submenu sem conseguir sair
- **Operação difícil ou impossível**: Muitos menus fly-out são concebidos apenas para rato, não respondendo às teclas adequadas
- **Visibilidade do foco**: É frequente não ser claro que item está selecionado dentro do submenu

**Exemplo de experiência real:**

Imagine a Ana, que tem uma condição que afeta a sua motricidade fina e navega exclusivamente com teclado. Ela acede a um menu principal pressionando Tab até lá chegar e Enter para o abrir. O submenu aparece, mas quando tenta navegar dentro dele, não consegue mover-se entre as opções - o foco do teclado simplesmente salta para o próximo item principal da página, ignorando completamente as opções do submenu.

Esta situação frustra a Ana porque está a perder acesso a partes importantes do site. O problema acontece porque o menu foi programado apenas para funcionar com eventos de rato (hover/clique) e não contempla a navegação por teclado.

#### Utilizadores de Leitores de Ecrã

Para utilizadores cegos ou com baixa visão que usam leitores de ecrã:

- **Falta de comunicação**: Muitos menus não indicam que têm submenus nem anunciam quando um submenu abre ou fecha
- **Estrutura confusa**: Se não for codificado corretamente, um leitor de ecrã pode não entender a relação entre o menu principal e os submenus
- **Operação inconsistente**: O comportamento do menu pode variar consoante o leitor de ecrã usado

**Exemplo de experiência real:**

O Carlos usa o leitor de ecrã NVDA. No site da sua câmara municipal, existe um menu "Serviços" que tem várias opções em submenus. Quando o Carlos navega até este menu com o seu leitor de ecrã, ouve "Serviços, link", mas nada indica que este item tem um submenu associado. Ele ativa o link pensando que irá para uma página de serviços, mas em vez disso abre-se um submenu que o leitor de ecrã não anuncia. Carlos não percebe que surgiram novas opções e continua a sua navegação, perdendo acesso a toda essa informação.

O problema é que o menu não tem os atributos `aria-haspopup` e `aria-expanded` que informariam o leitor de ecrã sobre a existência e estado do submenu.

#### Utilizadores com Baixa Visão

Para quem tem baixa visão:

- **Contraste insuficiente**: Muitos submenus usam cores com pouco contraste, dificultando a leitura
- **Movimento rápido**: Alguns menus aparecem e desaparecem demasiado rápido, não dando tempo para ler e escolher
- **Tamanho pequeno**: Texto e alvos de clique pequenos dificultam a interação

**Exemplo de experiência real:**

A Maria tem degenerescência macular e usa ampliação de ecrã. Quando tenta usar menus fly-out, enfrenta dois problemas principais: primeiro, o submenu muitas vezes aparece fora da sua área de visão ampliada; segundo, quando move o cursor para tentar aceder ao submenu, ele frequentemente desaparece antes de conseguir clicar numa opção porque o tempo de exibição é demasiado curto.

#### Utilizadores com Dificuldades Cognitivas

Para pessoas com dificuldades cognitivas, de aprendizagem ou de atenção:

- **Complexidade**: Menus com vários níveis podem ser confusos e difíceis de memorizar
- **Falta de persistência**: Menus que desaparecem rapidamente exigem reflexos e atenção constante
- **Sobrecarga visual**: Muitas opções aparecendo de repente podem causar sobrecarga sensorial

**Exemplo de experiência real:**

O Tiago tem dislexia e PHDA (Perturbação de Hiperatividade e Défice de Atenção). Quando acede a sites com menus fly-out complexos, sente-se frequentemente confuso e frustrado. Os menus com animações rápidas e múltiplos níveis distraem-no, e ele perde o contexto do que estava a procurar. Se o submenu desaparece quando ele move ligeiramente o rato, tem de recomeçar todo o processo, o que aumenta a sua frustração.

### Requisitos de Acessibilidade para Menus Fly-out

Para garantir que os menus fly-out são acessíveis a todos os utilizadores, devemos seguir estes requisitos essenciais:

#### 1. Operação por Teclado
- O menu deve ser completamente operável com teclado
- Deve seguir um padrão de navegação previsível (Tab, Enter, teclas de setas, Esc)
- O foco deve ser visível em todos os momentos

#### 2. Compatibilidade com Tecnologias de Apoio
- Uso apropriado de ARIA para comunicar a estrutura e estado do menu
- Relações claras entre elementos de menu e submenus
- Notificações sobre a abertura/fecho de submenus

#### 3. Percetibilidade
- Contraste adequado entre texto e fundo
- Indicações visuais claras de que um item tem submenu
- Tamanho de texto e alvos de clique suficientemente grandes

#### 4. Operabilidade
- Tempo suficiente para interagir com as opções
- Tolerância para movimentos imprecisos do rato
- Múltiplas formas de ativar/desativar os submenus

#### 5. Compreensibilidade
- Estrutura de menu lógica e consistente
- Feedback claro sobre o estado atual (aberto/fechado)
- Operação previsível e consistente em todo o site

## Técnicas de Codificação

Para criar menus fly-out acessíveis, é essencial utilizar as técnicas de codificação adequadas. Vamos explorar as melhores práticas através de exemplos.

### Estrutura HTML Semântica

A base de um menu fly-out acessível é uma estrutura HTML semântica. O ideal é usar elementos `<nav>`, `<ul>`, `<li>` e `<a>` ou `<button>`.

```html
<nav aria-label="Menu principal">
  <ul class="menu-principal">
    <li class="menu-item">
      <a href="#" aria-expanded="false" aria-haspopup="menu">Produtos</a>
      <ul class="submenu">
        <li><a href="/produtos/novos">Novos Produtos</a></li>
        <li><a href="/produtos/populares">Mais Populares</a></li>
        <li><a href="/produtos/promocoes">Promoções</a></li>
      </ul>
    </li>
    <!-- Outros itens de menu -->
  </ul>
</nav>
```

**O que funciona bem neste exemplo:**

- Uso de elementos semânticos: `<nav>` indica uma secção de navegação
- Estrutura hierárquica clara com listas aninhadas (`<ul>` dentro de `<li>`)
- Atributos ARIA importantes:
  - `aria-label` identifica o propósito do menu
  - `aria-expanded` indica se o submenu está aberto ou fechado
  - `aria-haspopup` indica que o elemento tem um submenu associado

### JavaScript para Interatividade com Teclado

O JavaScript é fundamental para garantir que os menus fly-out funcionem com teclado. Aqui está um exemplo simplificado:

```javascript
// Seletor para todos os itens de menu com submenus
const menuItems = document.querySelectorAll('.menu-item > a[aria-haspopup="true"]');

menuItems.forEach(item => {
  // Gestão de clique
  item.addEventListener('click', function(e) {
    e.preventDefault();
    const isExpanded = this.getAttribute('aria-expanded') === 'true';
    this.setAttribute('aria-expanded', !isExpanded);
    // Submenu correspondente ao item atual
    const submenu = this.nextElementSibling;
    submenu.hidden = isExpanded;
  });
  
  // Gestão de teclado
  item.addEventListener('keydown', function(e) {
    const submenu = this.nextElementSibling;
    const submenuLinks = submenu.querySelectorAll('a');
    
    switch(e.key) {
      case 'ArrowDown':
        e.preventDefault();
        if (this.getAttribute('aria-expanded') === 'false') {
          // Abrir o submenu
          this.click();
        }
        // Focar o primeiro item do submenu
        submenuLinks[0].focus();
        break;
      case 'Escape':
        if (this.getAttribute('aria-expanded') === 'true') {
          // Fechar o submenu
          this.click();
          // Manter o foco no item principal
          this.focus();
        }
        break;
    }
  });
});

// Navegação dentro do submenu
document.querySelectorAll('.submenu a').forEach(link => {
  link.addEventListener('keydown', function(e) {
    const links = Array.from(this.closest('.submenu').querySelectorAll('a'));
    const currentIndex = links.indexOf(this);
    
    switch(e.key) {
      case 'ArrowDown':
        e.preventDefault();
        // Ir para o próximo item ou voltar ao primeiro
        const nextIndex = (currentIndex + 1) % links.length;
        links[nextIndex].focus();
        break;
      case 'ArrowUp':
        e.preventDefault();
        // Ir para o item anterior ou para o último
        const prevIndex = (currentIndex - 1 + links.length) % links.length;
        links[prevIndex].focus();
        break;
      case 'Escape':
        e.preventDefault();
        // Fechar o submenu e voltar ao item principal
        const menuItem = this.closest('.menu-item').querySelector('a[aria-haspopup]');
        menuItem.setAttribute('aria-expanded', 'false');
        this.closest('.submenu').hidden = true;
        menuItem.focus();
        break;
    }
  });
});
```

**O que funciona bem neste exemplo:**

- Gestão de estados com `aria-expanded` atualizado dinamicamente
- Suporte para teclas de navegação:
  - `ArrowDown` para abrir o submenu e navegar para baixo
  - `ArrowUp` para navegar para cima
  - `Escape` para fechar o submenu e voltar ao item principal
- A navegação dentro do submenu é circular (do último volta ao primeiro e vice-versa)
- O foco é gerido explicitamente, garantindo que os utilizadores sabem sempre onde estão

### CSS para Comportamento e Visual Acessível

O CSS deve garantir que o menu é visualmente acessível e fornece feedback adequado.

```css
/* Estilos base */
.menu-principal {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
}

.menu-item {
  position: relative;
  margin-right: 1rem;
}

/* Estilo para indicar que um item tem submenu */
[aria-haspopup="true"]::after {
  content: " ▼";
  font-size: 0.8em;
  vertical-align: middle;
}

/* Estado expandido */
[aria-expanded="true"]::after {
  content: " ▲";
}

/* Submenus */
.submenu {
  position: absolute;
  left: 0;
  top: 100%;
  min-width: 200px;
  background: white;
  border: 1px solid #ccc;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  list-style: none;
  padding: 0.5rem 0;
  margin: 0;
  z-index: 100;
}

/* Esconder submenus por defeito */
.submenu[hidden] {
  display: none;
}

/* Links nos menus */
.menu-principal a {
  display: block;
  padding: 0.5rem 1rem;
  color: #333;
  text-decoration: none;
  font-size: 1rem;
}

.submenu a {
  padding: 0.7rem 1rem;
}

/* Indicador de foco visível */
a:focus {
  outline: 3px solid #4a90e2;
  outline-offset: -1px;
}

/* Estados hover/focus */
.menu-principal a:hover,
.menu-principal a:focus {
  background-color: #f0f0f0;
}

.submenu a:hover,
.submenu a:focus {
  background-color: #e8e8e8;
}
```

**O que funciona bem neste exemplo:**

- Indicadores visuais de submenus (setas)
- Foco visível e destacado com alto contraste
- Estados hover e focus claramente diferenciados
- Tamanho adequado dos elementos interativos (padding suficiente)
- Posicionamento claro dos submenus

### Implementação Completa com ARIA

Para uma solução mais robusta, podemos adicionar atributos ARIA adicionais:

```html
<nav aria-label="Menu principal">
  <ul class="menu-principal" role="menubar">
    <li class="menu-item" role="none">
      <a href="#" 
         role="menuitem" 
         aria-expanded="false" 
         aria-haspopup="true"
         id="menu-produtos">Produtos</a>
      <ul class="submenu" 
          role="menu" 
          aria-labelledby="menu-produtos"
          hidden>
        <li role="none">
          <a href="/produtos/novos" role="menuitem">Novos Produtos</a>
        </li>
        <li role="none">
          <a href="/produtos/populares" role="menuitem">Mais Populares</a>
        </li>
        <li role="none">
          <a href="/produtos/promocoes" role="menuitem">Promoções</a>
        </li>
      </ul>
    </li>
    <!-- Outros itens -->
  </ul>
</nav>
```

**O que funciona bem neste exemplo:**

- Uso do modelo de roles ARIA para menus:
  - `role="menubar"` para o menu principal horizontal
  - `role="menu"` para o submenu vertical
  - `role="menuitem"` para itens interativos
  - `role="none"` para itens estruturais sem semântica de menu
- `aria-labelledby` liga explicitamente o submenu ao seu item principal
- Atributo `hidden` sincronizado com `aria-expanded` para consistência

## Recomendações para Conteúdo Acessível

Além da codificação técnica, existem várias práticas recomendadas para garantir que os menus fly-out sejam realmente acessíveis a todos os utilizadores:

### 1. Desenho Simples e Focado

- **Evite menus profundos**: Limite a hierarquia a um máximo de 2 níveis (menu principal e um nível de submenus)
- **Agrupe logicamente**: Organize os itens do menu em grupos relacionados e intuitivos
- **Limite o número de opções**: Evite sobrecarregar o utilizador com demasiadas escolhas num só menu

**Analogia**: Um menu fly-out deve ser como uma boa sinalização rodoviária - clara, concisa e fácil de seguir mesmo quando se está em movimento rápido.

### 2. Comportamento Previsível

- **Consistência**: Todos os menus do site devem funcionar da mesma forma
- **Tempo adequado**: Dê tempo suficiente para os utilizadores lerem e selecionarem opções
- **Tolerância a erros**: Permita alguma margem para movimentos imprecisos do rato sem fechar o menu

**Exemplo prático**:
Um bom menu fly-out deve incluir uma pequena "zona tampão" entre o item principal e o submenu, para que pequenos desvios do rato não fechem imediatamente o submenu. Também deve haver um atraso antes de fechar, para dar tempo ao utilizador de corrigir o movimento.

### 3. Feedback Visual

- **Indicadores claros**: Use ícones ou indicadores visuais para mostrar que um item tem submenu
- **Estados visíveis**: Torne óbvio quando um menu está aberto ou fechado
- **Contraste adequado**: Garanta que o texto e os ícones têm contraste suficiente com o fundo

### 4. Funcionalidade em Todos os Dispositivos

- **Responsividade**: Adapte o comportamento do menu a diferentes tamanhos de ecrã
- **Toque**: Considere que em dispositivos táteis não existe o conceito de "hover"
- **Vários métodos de entrada**: Teste com rato, teclado, ecrã tátil e comandos de voz

**Exemplo prático**:

```html
<!-- Versão para ecrãs grandes -->
<nav aria-label="Menu principal" class="menu-desktop">
  <!-- Implementação normal do menu fly-out -->
</nav>

<!-- Versão para dispositivos móveis -->
<nav aria-label="Menu principal" class="menu-mobile">
  <button aria-expanded="false" aria-controls="menu-mobile-panel">
    Menu <span aria-hidden="true" aria-haspopup="menu">☰</span>
  </button>
  <div id="menu-mobile-panel" hidden>
    <!-- Versão simplificada do menu para toque -->
  </div>
</nav>
```

### Erros Comuns

Ao implementar menus fly-out, é fácil cometer erros que comprometem a acessibilidade. Vamos ver os mais frequentes:

#### 1. Dependência excessiva de hover

**Erro**:
```css
/* Submenu só aparece com hover */
.menu-item:hover .submenu {
  display: block;
}
```

**Problema**: Este padrão não funciona para utilizadores de teclado nem em dispositivos táteis.

**Solução correta**:
```css
/* Os estados devem ser controlados via JavaScript e aria-expanded */
.menu-item [aria-expanded="true"] + .submenu {
  display: block;
}
```

#### 2. Falta de suporte ao teclado

**Erro**:
```javascript
// Apenas eventos de rato
menuItems.forEach(item => {
  item.addEventListener('mouseenter', openSubmenu);
  item.addEventListener('mouseleave', closeSubmenu);
});
```

**Problema**: Os utilizadores de teclado não conseguem aceder aos submenus.

**Solução correta**: Implementar eventos de teclado como mostrado na secção de Técnicas de Codificação.

#### 3. Ausência de atributos ARIA

**Erro**:
```html
<!-- Sem informações para tecnologias de apoio -->
<ul class="menu">
  <li class="dropdown">
    <a href="#">Produtos</a>
    <ul class="submenu">
      <!-- Itens do submenu -->
    </ul>
  </li>
</ul>
```

**Problema**: Os leitores de ecrã não sabem que existe um submenu nem quando ele está aberto.

**Solução correta**: Usar `aria-haspopup`, `aria-expanded` e outros atributos como mostrado anteriormente.

#### 4. Tempo de exibição inadequado

**Erro**:
```css
/* Transições muito rápidas */
.submenu {
  transition: opacity 0.2s;
}
```

**Problema**: Transições rápidas não dão tempo suficiente para utilizadores com deficiências cognitivas ou motoras.

**Solução correta**:
```javascript
// Atrasar o fecho do menu
menuItem.addEventListener('mouseleave', function() {
  // Esperar para verificar se o utilizador realmente saiu
  setTimeout(() => {
    if (!menuItem.matches(':hover')) {
      closeSubmenu();
    }
  }, 300); // 300ms de tolerância
});
```

#### 5. Menus fly-out aninhados com difícil acesso

**Erro**:
```html
<!-- Múltiplos níveis sem controlo adequado -->
<li>
  <a href="#">Nível 1</a>
  <ul>
    <li>
      <a href="#">Nível 2</a>
      <ul>
        <li><a href="#">Nível 3</a></li>
        <!-- Mais níveis -->
      </ul>
    </li>
  </ul>
</li>
```

**Problema**: Menus com muitos níveis são difíceis de navegar, especialmente para utilizadores de teclado ou com deficiências motoras.

**Solução correta**: Limitar a profundidade do menu e fornecer alternativas como páginas de categoria com subcategorias em vez de submenus excessivamente aninhados.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Inclusão para todos**: Os menus fly-out devem ser acessíveis a todas as pessoas, independentemente das suas capacidades ou das tecnologias que utilizam.

2. **Fundamentos da acessibilidade em menus fly-out**:
   - Operabilidade por teclado
   - Compatibilidade com tecnologias de apoio
   - Feedback visual claro
   - Tempo adequado para interação
   - Estrutura semântica correta

3. **Técnicas essenciais**:
   - HTML estruturado e semântico
   - ARIA para comunicar estado e função
   - JavaScript para interação por teclado
   - CSS para feedback visual adequado
   - Responsividade para diferentes dispositivos

4. **Evitar erros comuns**:
   - Dependência exclusiva de eventos de rato
   - Ausência de atributos ARIA
   - Transições demasiado rápidas
   - Menus excessivamente complexos
   - Falta de visibilidade do foco

### Exercícios Práticos

#### Exercício 1: Análise de Acessibilidade

**Objetivo**: Identificar problemas de acessibilidade em menus fly-out existentes.

**Instruções**:

1. Escolha três websites que utilizam menus fly-out (ex: um portal de notícias, uma loja online, um site governamental)
2. Navegue pelos menus usando apenas o teclado (sem rato)
3. Responda às seguintes perguntas para cada site:
   - Consegue aceder a todos os itens do menu usando apenas o teclado?
   - O foco é claramente visível em todos os momentos?
   - Existe alguma indicação visual de que um item tem submenu?
   - Quando um submenu abre, existe alguma indicação para os utilizadores de leitores de ecrã?
   - O submenu fica aberto tempo suficiente para ler e selecionar opções?

#### Exercício 2: Correção de Menu Inacessível

**Objetivo**: Praticar a correção de problemas comuns de acessibilidade em menus fly-out.

**Instruções**:
Considere o seguinte código de menu com problemas de acessibilidade:

```html
<div class="nav">
  <div class="menu-item">
    <span onmouseover="showSubmenu(this)">Produtos</span>
    <div class="dropdown" style="display: none;">
      <div onclick="location.href='/novos'">Novos</div>
      <div onclick="location.href='/populares'">Populares</div>
    </div>
  </div>
  <!-- mais itens -->
</div>

<script>
function showSubmenu(elem) {
  var dropdown = elem.nextElementSibling;
  dropdown.style.display = 'block';
  
  elem.onmouseout = function() {
    dropdown.style.display = 'none';
  }
}
</script>
```

Tarefa:

1. Identifique todos os problemas de acessibilidade neste código
2. Reescreva-o usando HTML semântico
3. Adicione os atributos ARIA necessários
4. Implemente navegação por teclado
5. Melhore o CSS para fornecer feedback visual adequado

#### Exercício 3: Criação de Menu Fly-out Acessível

**Objetivo**: Aplicar todas as técnicas e práticas recomendadas na criação de um menu fly-out totalmente acessível.

**Instruções**:

1. Crie um menu fly-out para um site fictício de sua escolha (ex: loja online, blog, portal de notícias)
2. O menu deve ter pelo menos 4 itens principais, um dos quais com submenu
3. Implemente todas as técnicas de acessibilidade discutidas:
   - HTML semântico
   - Atributos ARIA
   - Navegação completa por teclado
   - CSS para feedback visual
   - Comportamento responsivo para diferentes dispositivos
4. Teste o seu menu:
   - Usando apenas o teclado
   - Com um simulador de leitor de ecrã
   - Em diferentes tamanhos de ecrã
   - Com diferentes velocidades de clique/movimento

#### Exercício 4: Mini-projeto - Menu Fly-out Avançado

**Objetivo**: Criar um menu fly-out acessível mais complexo com funcionalidades avançadas.

**Instruções**:
Crie um menu para um site de comércio eletrónico com as seguintes funcionalidades:

1. Um menu principal horizontal com, pelo menos, 5 categorias
2. Submenus para cada categoria com itens organizados em colunas
3. Imagens em destaque em alguns submenus (garantindo que são adequadamente descritas)
4. Implementação para dispositivos móveis que transforme o menu fly-out num menu acordeão
5. Transições suaves mas não intrusivas
6. Suporte completo a teclado e leitores de ecrã
7. Área de pesquisa integrada no menu
8. Indicadores visuais e textuais para todos os estados do menu