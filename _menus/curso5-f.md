---
title: Menus de Aplicações
layout: default
nav_order: 6
---

# Menus de Aplicações

## Introdução

Os menus de aplicações são componentes interativos fundamentais nas aplicações web modernas. Diferentemente dos menus de navegação tradicionais de websites, estes menus são utilizados para aceder a funcionalidades específicas dentro de uma aplicação web, como editar documentos, gerir definições ou aceder a ferramentas. Por essa razão, a sua utilização como menus de navegação deve ser evitada.

As aplicações web tornaram-se cada vez mais complexas, aproximando-se da experiência de utilização de software instalado localmente. Com esta evolução, a acessibilidade destes componentes torna-se crítica para garantir que todas as pessoas, independentemente das suas capacidades, possam utilizar estas ferramentas de forma eficaz.

### Como as Pessoas com Deficiência usam Menus de Aplicações

As pessoas com diferentes tipos de deficiência interagem com os menus de aplicações de formas distintas:

#### Pessoas com deficiência visual

- **Utilizadores de leitores de ecrã**: Navegam pelos menus utilizando teclas de seta e atalhos de teclado. Dependem de anúncios verbais sobre a estrutura do menu, os itens disponíveis e o seu estado atual (expandido, comprimido, selecionado).

  *Exemplo:* A Maria, que é cega, utiliza o NVDA como leitor de ecrã para editar documentos numa aplicação web. Quando prime a tecla Alt+F, o leitor anuncia "Menu Ficheiro expandido, lista com 8 itens". Depois, utiliza as teclas de seta para navegar pelas opções, ouvindo cada uma delas, até encontrar "Guardar como".

  *Porque funciona:* Este exemplo funciona bem porque o menu está corretamente implementado com roles ARIA, estados e relações que permitem ao leitor de ecrã anunciar adequadamente a estrutura e estado do menu.

- **Utilizadores com baixa visão**: Dependem de bom contraste, capacidade de ampliação e espaçamento adequado entre itens de menu.

#### Pessoas com deficiência motora

- **Utilizadores exclusivos de teclado**: Necessitam de operação completa do menu através do teclado, incluindo abertura, navegação e seleção de itens.

  *Exemplo:* O João, que tem paralisia cerebral, não consegue utilizar um rato. Ele navega numa aplicação de email utilizando apenas o teclado. Para aceder ao menu de opções, utiliza Tab até chegar ao botão do menu, ativa-o com Enter, e depois utiliza as teclas de seta para navegar e Enter para selecionar uma opção.

  *Porque funciona:* Este exemplo é bem-sucedido porque o menu foi implementado com foco visível, ordem de tabulação lógica e gestão adequada de eventos de teclado.

- **Utilizadores de tecnologias de apoio de entrada**: Pessoas que utilizam comandos de voz, manípulos ou outros dispositivos alternativos precisam que os menus respondam corretamente aos eventos gerados por estas tecnologias.

#### Pessoas com deficiência cognitiva

- Beneficiam de menus com estrutura previsível, linguagem clara e simples, e feedback visual sobre o elemento ativo.

  *Exemplo:* A Ana, que tem dislexia, utiliza uma aplicação de gestão de projetos. Ela beneficia de um menu de aplicação onde os ícones acompanham o texto, as opções estão organizadas em categorias lógicas, e o item selecionado é claramente destacado.

  *Porque funciona:* Esta abordagem reduz a carga cognitiva ao combinar pistas visuais com texto, organizar informação de forma lógica e fornecer feedback claro sobre a localização atual.

### Requisitos de Acessibilidade para Menus de Aplicações

Para garantir que os menus de aplicações são acessíveis a todos os utilizadores, é necessário cumprir vários requisitos fundamentais:

#### Operabilidade com teclado

- Todos os itens do menu devem ser acessíveis e operáveis utilizando apenas o teclado.
- Os utilizadores devem conseguir abrir o menu, navegar entre os itens e selecionar opções sem utilizar o rato.
- Deve existir uma indicação visual clara de qual item tem o foco.

#### Semântica apropriada

- Os menus devem utilizar elementos HTML e roles ARIA adequados para comunicar corretamente a sua finalidade e estrutura às tecnologias de apoio.
- Os estados dos menus (expandido/comprimido) devem ser comunicados adequadamente.

#### Previsibilidade e consistência

- O comportamento dos menus deve ser consistente e previsível em toda a aplicação.
- As convenções comuns de interação devem ser respeitadas (por exemplo, Esc para fechar um menu, setas para navegar).

#### Adaptabilidade

- Os menus devem funcionar corretamente quando os utilizadores ampliam o conteúdo ou utilizam modos de alto contraste.
- Devem adaptar-se a diferentes dispositivos e modos de entrada.

*Analogia:* Podemos comparar um menu de aplicação acessível a um elevador bem projetado. Ambos devem:

- Ser utilizáveis por todos (botões alcançáveis por pessoas em cadeira de rodas, marcações em braille)
- Fornecer feedback claro (anúncios de voz indicando o andar, iluminação nos botões)
- Ter uma interface previsível (disposição padronizada dos botões)
- Oferecer diferentes modos de interação (botões físicos e comandos de voz)

Da mesma forma, um menu de aplicação deve ser acessível a todos, fornecer feedback claro, seguir padrões consistentes e adaptar-se a diferentes necessidades.

## Técnicas de Codificação

A implementação de menus de aplicações acessíveis requer uma combinação de HTML semântico, ARIA e JavaScript para gestão de interações. Vamos explorar as técnicas mais importantes:

### Implementação de Menus com o Padrão ARIA Menu

O padrão ARIA Menu é concebido para menus de aplicações (não para menus de navegação, apesar de também poder ser usado neste caso). Utiliza roles como `menubar`, `menu`, `menuitem`, `menuitemcheckbox` e `menuitemradio`.

#### Estrutura básica de um menu de aplicação

```html
<div role="menubar" aria-label="Menu de Edição">
  <button role="menuitem" aria-haspopup="menu" aria-expanded="false">Ficheiro</button>
  <div role="menu" aria-label="Opções de Ficheiro" hidden>
    <button role="menuitem">Novo</button>
    <button role="menuitem">Abrir...</button>
    <button role="menuitem">Guardar</button>
    <button role="menuitemcheckbox" aria-checked="false">Guardar automaticamente</button>
  </div>
  <button role="menuitem" aria-haspopup="true" aria-expanded="false">Editar</button>
  <div role="menu" aria-label="Opções de Edição" hidden>
    <button role="menuitem">Cortar</button>
    <button role="menuitem">Copiar</button>
    <button role="menuitem">Colar</button>
  </div>
</div>
```

*Porque funciona:* Esta estrutura comunica claramente a hierarquia e propósito dos elementos do menu aos leitores de ecrã. Os atributos `aria-haspopup` e `aria-expanded` informam sobre submenus, enquanto `aria-checked` indica o estado de itens de verificação.

### Gestão de Eventos de Teclado

É crucial implementar a gestão adequada de eventos de teclado para permitir uma navegação completa através do teclado:

```javascript
// Gestão simplificada de eventos de teclado para um menu
document.querySelector('[role="menubar"]').addEventListener('keydown', function(e) {
  const currentItem = document.activeElement;
  
  switch(e.key) {
    case 'ArrowRight':
      // Mover para o próximo item do menu principal
      focusNextMenuItem(currentItem);
      e.preventDefault();
      break;
    case 'ArrowLeft':
      // Mover para o item anterior do menu principal
      focusPreviousMenuItem(currentItem);
      e.preventDefault();
      break;
    case 'ArrowDown':
      // Abrir submenu ou mover para o próximo item em um submenu
      if (currentItem.getAttribute('aria-haspopup') === 'true') {
        openSubmenu(currentItem);
        focusFirstSubmenuItem(currentItem);
        e.preventDefault();
      }
      break;
    case 'Escape':
      // Fechar o submenu atual
      closeCurrentSubmenu();
      e.preventDefault();
      break;
    case 'Enter':
    case ' ': // Espaço
      // Ativar o item atual
      activateMenuItem(currentItem);
      e.preventDefault();
      break;
  }
});

// Funções auxiliares seriam implementadas aqui
```

*Porque funciona:* Este código implementa comportamentos de teclado padrão para menus de aplicações, permitindo que utilizadores de teclado naveguem e ativem os itens de menu de forma intuitiva.

### Implementação de Atalhos de Teclado

Para aumentar a eficiência para utilizadores de teclado, podemos implementar atalhos:

```html
<div role="menubar" aria-label="Menu de Edição">
  <button role="menuitem" aria-haspopup="true" aria-expanded="false" accesskey="f">
    <span aria-hidden="true"><u>F</u>icheiro</span>
    <span class="sr-only">Ficheiro, acesso rápido Alt+F</span>
  </button>
  <!-- Restante do menu -->
</div>
```

E o JavaScript correspondente:

```javascript
document.addEventListener('keydown', function(e) {
  // Detetar combinação Alt+F
  if (e.altKey && e.key === 'f') {
    const fileButton = document.querySelector('[accesskey="f"]');
    fileButton.click();
    e.preventDefault();
  }
  // Outras combinações...
});
```

*Porque funciona:* Os atalhos de teclado permitem acesso direto às funcionalidades do menu, aumentando a eficiência para todos os utilizadores, especialmente aqueles que dependem do teclado. O sublinhado na letra inicial e a informação para leitores de ecrã tornam estes atalhos descobríveis.

## Recomendações para Conteúdo Acessível

Para além da implementação técnica, existem várias recomendações importantes para garantir que os menus de aplicações são verdadeiramente acessíveis:

### Organização Lógica

- Agrupe os itens de menu relacionados em categorias lógicas.
- Utilize separadores visuais (e semânticos) entre grupos de funcionalidades.

*Exemplo:* Um editor de texto pode organizar as funções em menus como "Ficheiro" (para operações de documento), "Editar" (para funções de manipulação de texto), "Formatar" (para alterações de estilo), etc.

*Porque funciona:* Esta organização reduz a carga cognitiva e ajuda todos os utilizadores a encontrar rapidamente as funções que procuram.

### Rótulos Claros e Concisos

- Utilize textos claros e diretos para os itens de menu.
- Evite jargão técnico desnecessário.
- Indique claramente quando uma opção irá abrir uma caixa de diálogo (por exemplo, "Guardar como...").

*Porque funciona:* Rótulos claros beneficiam todos os utilizadores, mas são especialmente importantes para pessoas com dificuldades cognitivas ou que utilizam leitores de ecrã.

### Combinação de Ícones e Texto

- Utilize ícones juntamente com texto para melhorar a compreensão.
- Garanta que os ícones têm um significado claro ou são explicados por texto.

*Exemplo:*
```html
<button role="menuitem">
  <span class="icon-save" aria-hidden="true"></span>
  Guardar
</button>
```

*Porque funciona:* Os ícones fornecem pistas visuais adicionais que ajudam na identificação rápida das funções, enquanto o texto garante que o significado é claro para todos.

### Indicação de Atalhos de Teclado

- Mostre os atalhos de teclado disponíveis ao lado dos itens de menu correspondentes.
- Utilize uma formatação consistente para estes atalhos.

*Exemplo:*
```html
<button role="menuitem">
  Guardar
  <span class="keyboard-shortcut" aria-hidden="true">Ctrl+S</span>
  <span class="sr-only">Atalho de teclado: Control mais S</span>
</button>
```

*Porque funciona:* Esta abordagem torna os atalhos descobríveis para utilizadores visuais e também comunica esta informação aos utilizadores de leitores de ecrã, permitindo que todos os utilizadores trabalhem mais eficientemente.

### Feedback visual e auditivo

- Forneça feedback visual claro quando um item de menu é focado ou ativado.
- Garanta que este feedback é comunicado também às tecnologias de apoio.

*Exemplo:* Além de destacar visualmente um item de menu quando é selecionado, utilize `aria-live` para anunciar alterações importantes, como "Documento guardado" após a seleção da opção "Guardar".

*Porque funciona:* O feedback imediato ajuda todos os utilizadores a compreender o resultado das suas ações, reduzindo a incerteza e aumentando a confiança na utilização da aplicação.

### Erros Comuns

Ao implementar menus de aplicações, existem vários erros frequentes que podem comprometer a acessibilidade:

#### 1. Gestão Incorreta de Foco

**Erro:** Não gerir adequadamente o foco do teclado ao abrir e fechar menus.

*Exemplo incorreto:* Um menu que, ao ser fechado com a tecla Esc, não devolve o foco ao botão que o abriu, deixando o utilizador "perdido" na página.

**Correção:** Implemente uma gestão de foco adequada:

```javascript
// Ao abrir o menu, guarde o elemento que tinha o foco
const menuButton = document.querySelector('#menu-button');
const menu = document.querySelector('#menu');
let lastFocusedElement;

menuButton.addEventListener('click', () => {
  lastFocusedElement = document.activeElement;
  menu.hidden = false;
  menu.querySelector('[role="menuitem"]').focus();
});

// Ao fechar o menu, restaure o foco para o elemento anterior
function closeMenu() {
  menu.hidden = true;
  lastFocusedElement.focus();
}

// Chamar closeMenu() quando necessário (Esc, clique fora, seleção de item)
```

*Porque é importante:* A gestão adequada do foco é essencial para utilizadores de teclado e leitores de ecrã navegarem eficientemente pela aplicação sem se perderem.

#### 2. Implementação Incompleta de Interações de Teclado

**Erro:** Implementar apenas algumas das interações de teclado necessárias para um menu de aplicação.

*Exemplo incorreto:* Um menu que permite navegar com as teclas de seta, mas não fecha quando se pressiona Esc ou não permite ativar itens com a tecla Enter.

**Correção:** Implemente todas as interações de teclado padrão:

- Setas para navegação
- Enter/Espaço para seleção
- Esc para fechar
- Teclas iniciais para saltar para itens (por exemplo, pressionar "G" salta para o primeiro item começado por G)

*Porque é importante:* A implementação parcial cria uma experiência frustrante para os utilizadores de teclado, que esperam um conjunto padrão de comportamentos.

#### 3. Não Comunicar o Estado do Menu

**Erro:** Não comunicar claramente se um menu está aberto ou fechado ou se um item está selecionado.

*Exemplo incorreto:* Um menu que se expande visualmente, mas não atualiza o atributo `aria-expanded` para informar os leitores de ecrã.

**Correção:** Atualize sempre os atributos ARIA relevantes:

```javascript
menuButton.addEventListener('click', () => {
  const expanded = menuButton.getAttribute('aria-expanded') === 'true';
  menuButton.setAttribute('aria-expanded', !expanded);
  menu.hidden = expanded;
  
  if (!expanded) {
    // Menu a ser aberto
    menu.querySelector('[role="menuitem"]').focus();
  } else {
    // Menu a ser fechado
    // Código para restaurar o foco, etc.
  }
});
```

*Porque é importante:* Sem estas informações de estado, os utilizadores de leitores de ecrã não conseguem perceber se um menu está aberto ou fechado, ou se uma opção está selecionada.

#### 4. Dependência Exclusiva do Rato

**Erro:** Implementar funcionalidades de menu que só funcionam com o rato, como menus que aparecem apenas com hover.

*Exemplo incorreto:* Um menu que se expande quando o rato passa por cima, mas não oferece nenhuma forma de acesso via teclado.

**Correção:** Garanta que todas as interações possíveis com o rato também são possíveis com o teclado:

```javascript
// Para hover
menuButton.addEventListener('mouseenter', openMenu);
// Equivalente para teclado
menuButton.addEventListener('focus', openMenu);
menuButton.addEventListener('keydown', (e) => {
  if (e.key === 'Enter' || e.key === ' ' || e.key === 'ArrowDown') {
    openMenu();
    e.preventDefault();
  }
});
```

*Porque é importante:* A dependência exclusiva do rato exclui completamente utilizadores que dependem do teclado ou de tecnologias de apoio.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Acessibilidade abrangente**: Menus de aplicações acessíveis devem:
   - Ser totalmente operáveis via teclado
   - Utilizar semântica apropriada para comunicar com tecnologias de apoio
   - Ter estrutura lógica e previsível
   - Adaptar-se a diferentes necessidades dos utilizadores

2. **Implementação técnica**: Uma implementação robusta inclui:
   - HTML semântico enriquecido com roles e atributos ARIA
   - Gestão adequada de eventos de teclado
   - Controlo de foco ao abrir e fechar menus
   - Feedback claro sobre o estado dos menus e itens

3. **Boas práticas de design**: Para além dos aspetos técnicos, considere:
   - Organização lógica dos itens
   - Rótulos claros e concisos
   - Combinação de ícones e texto
   - Indicação dos atalhos de teclado disponíveis
   - Feedback adequado sobre as ações realizadas

4. **Evitar erros comuns**:
   - Gerir adequadamente o foco do teclado
   - Implementar todas as interações de teclado necessárias
   - Comunicar claramente o estado do menu
   - Não depender exclusivamente do rato

### Exercícios Práticos

#### Exercício 1: Análise de Menu de Aplicação

**Objetivo:** Desenvolver capacidade crítica para avaliar a acessibilidade de menus de aplicações.

**Tarefa:** 

1. Visite uma aplicação web que utilize menus de aplicações (por exemplo, Google Docs, Microsoft Office Online, Figma).
2. Tente utilizar os menus apenas com o teclado.
3. Se possível, ative um leitor de ecrã e tente a mesma experiência.
4. Anote:
   - As funcionalidades que funcionam bem
   - As barreiras encontradas
   - Sugestões de melhoria

**Questões para reflexão:**

- O menu é totalmente operável via teclado?
- O estado do menu (aberto/fechado) é comunicado claramente?
- Os atalhos de teclado são indicados e funcionam?
- A estrutura do menu é lógica e previsível?

#### Exercício 2: Implementação de Menu Simples

**Objetivo:** Praticar a implementação de um menu de aplicação básico e acessível.

**Tarefa:**

1. Crie um menu de aplicação simples com pelo menos dois menus principais e submenus:
   - "Ficheiro" (com opções como "Novo", "Abrir", "Guardar")
   - "Editar" (com opções como "Cortar", "Copiar", "Colar")
2. Implemente:
   - HTML semântico com roles ARIA adequados
   - Interação completa via teclado
   - Estados visíveis e acessíveis
   - Pelo menos um item de verificação (checkbox)

**Código inicial:**
```html
<div class="app-menubar">
  <!-- Implemente o menu aqui -->
</div>

<style>
  /* Estilos básicos para o menu */
  .app-menubar {
    display: flex;
    background-color: #f0f0f0;
    padding: 5px;
  }
  
  /* Adicione mais estilos conforme necessário */
</style>

<script>
  // Implemente a lógica de interação aqui
</script>
```

#### Exercício 3: Correção de Menu Inacessível

**Objetivo:** Desenvolver capacidade para identificar e corrigir problemas de acessibilidade em menus existentes.

**Tarefa:**
Considere o seguinte código de menu inacessível:

```html
<div class="menu-bar">
  <div class="menu-item" onmouseover="showSubmenu('file-menu')">Ficheiro
    <div id="file-menu" class="submenu" style="display: none;">
      <div class="menu-option" onclick="newFile()">Novo</div>
      <div class="menu-option" onclick="openFile()">Abrir</div>
      <div class="menu-option" onclick="saveFile()">Guardar</div>
    </div>
  </div>
  <div class="menu-item" onmouseover="showSubmenu('edit-menu')">Editar
    <div id="edit-menu" class="submenu" style="display: none;">
      <div class="menu-option" onclick="cutSelection()">Cortar</div>
      <div class="menu-option" onclick="copySelection()">Copiar</div>
      <div class="menu-option" onclick="pasteSelection()">Colar</div>
    </div>
  </div>
</div>

<script>
  function showSubmenu(id) {
    // Esconde todos os submenus
    const submenus = document.querySelectorAll('.submenu');
    submenus.forEach(menu => menu.style.display = 'none');
    
    // Mostra o submenu selecionado
    document.getElementById(id).style.display = 'block';
  }
  
  // Funções de ação (não implementadas para o exercício)
  function newFile() { console.log('Novo ficheiro'); }
  function openFile() { console.log('Abrir ficheiro'); }
  function saveFile() { console.log('Guardar ficheiro'); }
  function cutSelection() { console.log('Cortar'); }
  function copySelection() { console.log('Copiar'); }
  function pasteSelection() { console.log('Colar'); }
</script>
```

Identifique os problemas de acessibilidade neste código e reescreva-o para torná-lo totalmente acessível, aplicando as técnicas e princípios aprendidos neste módulo.

**Dicas:**

- Considere a semântica apropriada (roles ARIA)
- Adicione suporte completo para teclado
- Melhore a gestão de estados
- Adicione rótulos adequados
- Implemente gestão de foco

# Conclusão e Boas Práticas

## Recapitulação

Ao longo deste curso, explorámos vários aspetos essenciais para criar menus acessíveis na Web. Vamos recordar os principais tópicos que abordámos:

1. **Menus e Navegação Básica** - Aprendemos como diferentes utilizadores, incluindo pessoas com deficiência, interagem com os menus de navegação e quais são os requisitos fundamentais de acessibilidade.

2. **Estrutura, Rótulos e Apresentação** - Vimos como estruturar corretamente os menus, rotulá-los adequadamente e apresentá-los de forma clara para todos os utilizadores.

3. **Operação com Teclado** - Explorámos técnicas para garantir que os menus são totalmente utilizáveis apenas com o teclado, sem depender do rato.

4. **Redimensionamento de Menus** - Aprendemos como permitir o redimensionamento dos menus para acomodar as necessidades de pessoas com baixa visão ou que precisam de texto ampliado.

5. **Menus Fly-out** - Abordámos os desafios específicos dos menus expansíveis e como torná-los acessíveis.

6. **Menus de Aplicações** - Explorámos os requisitos específicos dos menus em aplicações web complexas.

### Princípios Fundamentais a Recordar

Todos os menus, independentemente do seu tipo ou complexidade, devem seguir estes princípios básicos:

- **Perceção**: Todos os utilizadores devem conseguir perceber que existe um menu e compreender a sua estrutura.
- **Operabilidade**: Todos os utilizadores devem conseguir utilizar o menu, independentemente das tecnologias ou dispositivos que usam.
- **Compreensão**: O funcionamento do menu deve ser previsível e fácil de entender.
- **Robustez**: O menu deve funcionar com tecnologias atuais e futuras, incluindo tecnologias de apoio.

## Exercícios de Consolidação

### Exercício 1: Auditoria de Menu

**Objetivo:** Avaliar a acessibilidade de um menu num site real.

**Instruções:**

1. Escolhe um site que uses frequentemente.
2. Analisa o menu principal desse site usando apenas o teclado (sem rato).
3. Tenta usar um leitor de ecrã gratuito (como o NVDA ou o VoiceOver) para navegar pelo menu.
4. Responde às seguintes perguntas:
   - Consegues aceder a todos os itens do menu apenas com o teclado?
   - A estrutura do menu é anunciada corretamente pelo leitor de ecrã?
   - O estado atual (expandido/recolhido) dos submenus é claro?
   - O contraste do texto e dos elementos do menu é adequado?
   - O menu adapta-se bem quando aumentas o tamanho do texto?

### Exercício 2: Correção de Menu Inacessível

**Objetivo:** Corrigir problemas de acessibilidade num menu existente.

**Instruções:**
Analisa e corrige os problemas de acessibilidade neste exemplo de menu:

```html
<div class="menu">
  <a href="index.html"><img src="logo.png"></a>
  <div onclick="toggleSubmenu()">Produtos</div>
  <div class="submenu" style="display:none">
    <a href="produto1.html">Produto 1</a>
    <a href="produto2.html">Produto 2</a>
  </div>
  <div onclick="window.location='sobre.html'">Sobre Nós</div>
  <div onclick="window.location='contacto.html'">Contacto</div>
</div>
```

Problemas a corrigir:

- Estrutura HTML inadequada
- Falta de suporte para navegação com teclado
- Ausência de atributos ARIA
- Gestão de eventos inadequada
- Falta de texto alternativo para imagem

### Exercício 3: Desenvolvimento de um Menu Acessível

**Objetivo:** Criar um menu acessível de raiz.

**Instruções:**
Desenvolve um menu de navegação principal para um site fictício de notícias com as seguintes características:

- Menu principal com 5 categorias
- Pelo menos 2 categorias devem ter submenus
- Deve ser totalmente acessível via teclado
- Deve usar adequadamente ARIA quando necessário
- Deve funcionar em dispositivos móveis e desktop
- Deve ter indicadores visuais claros para o estado de foco

## Lista de Verificação Final

Utiliza esta lista de verificação para garantir que os menus que desenvolves são acessíveis:

### Estrutura e Semântica

- [ ] O menu usa elementos semânticos apropriados (como `<nav>`, `<ul>`, `<li>`)
- [ ] Existe um título ou rótulo claro para o menu
- [ ] O menu está claramente identificado como tal (por exemplo, com `role="navigation"` ou elemento `<nav>`)
- [ ] A hierarquia do menu é lógica e consistente

### Operação com Teclado

- [ ] Todos os itens do menu são acessíveis com Tab/Shift+Tab
- [ ] O foco visual é claramente visível
- [ ] Submenus podem ser abertos e fechados com o teclado
- [ ] Existe uma forma clara de sair dos submenus com o teclado
- [ ] Os atalhos de teclado (se existirem) estão documentados

### ARIA e Estados

- [ ] Menus expansíveis usam `aria-expanded`
- [ ] Submenus estão associados aos seus elementos pai
- [ ] Estados ativos são comunicados adequadamente
- [ ] Não existem armadilhas de teclado
- [ ] `aria-current` é usado para indicar a página atual

### Apresentação Visual

- [ ] O texto tem contraste suficiente (mínimo 4.5:1)
- [ ] O menu funciona quando ampliado até 200%
- [ ] Os espaçamentos são adequados para facilitar a interação
- [ ] Existem indicadores visuais para estados diferentes (foco, hover, ativo)
- [ ] O design é consistente e previsível

### Comportamento Responsivo

- [ ] O menu funciona em dispositivos móveis
- [ ] Menus "hambúrguer" (em dispositivos móveis) são acessíveis
- [ ] A funcionalidade é consistente entre diferentes dispositivos
- [ ] O menu tem área de toque adequada em dispositivos táteis

### Testes

- [ ] Testado com pelo menos um leitor de ecrã
- [ ] Testado apenas com teclado
- [ ] Testado com ampliação de ecrã
- [ ] Testado em diferentes navegadores
- [ ] Testado em diferentes dispositivos

## Critérios de Sucesso WCAG Relacionados

Os seguintes critérios de sucesso das WCAG (Web Content Accessibility Guidelines) estão diretamente relacionados com menus acessíveis:

### Nível A 

1. **1.3.1 Informações e Relações**
   - *Descrição*: A informação, estrutura e relações transmitidas através da apresentação podem ser determinadas programaticamente ou estão disponíveis no texto.
   - *Aplicação em menus*: A estrutura do menu deve usar elementos semânticos apropriados que comuniquem a hierarquia e as relações entre os itens.

2. **2.1.1 Teclado**
   - *Descrição*: Toda a funcionalidade do conteúdo é operável através de uma interface de teclado.
   - *Aplicação em menus*: Todos os itens do menu devem ser acessíveis e operáveis apenas com o teclado.

3. **2.4.3 Ordem de Foco**
   - *Descrição*: Se o conteúdo puder ser navegado sequencialmente e a sequência de navegação afetar o significado ou a operação, os componentes que podem receber foco recebem-no numa ordem que preserva o significado e a operabilidade.
   - *Aplicação em menus*: A ordem de tabulação no menu deve ser lógica e corresponder à ordem visual.

4. **4.1.2 Nome, Função, Valor**
   - *Descrição*: Para todos os componentes da interface do utilizador, o nome e a função podem ser determinados programaticamente; estados, propriedades e valores que podem ser definidos pelo utilizador podem ser definidos programaticamente; e a notificação de alterações a estes itens está disponível.
   - *Aplicação em menus*: Itens de menu devem ter nomes acessíveis e os estados (como expandido) devem ser comunicados.

### Nível AA 

1. **1.4.3 Contraste (Mínimo)**
   - *Descrição*: A apresentação visual de texto e imagens de texto tem um rácio de contraste de pelo menos 4.5:1.
   - *Aplicação em menus*: O texto do menu deve ter contraste suficiente com o fundo.

2. **1.4.4 Redimensionar Texto**
   - *Descrição*: O texto pode ser redimensionado sem tecnologia de apoio até 200% sem perda de conteúdo ou funcionalidade.
   - *Aplicação em menus*: Os menus devem permanecer utilizáveis quando o texto é ampliado até 200%.

3. **2.4.7 Foco Visível**
   - *Descrição*: Qualquer interface de utilizador operável por teclado tem um modo de operação onde o indicador de foco do teclado está visível.
   - *Aplicação em menus*: O foco deve ser claramente visível quando se navega pelo menu com o teclado.

### Nível AAA (Ideal)

1. **2.4.10 Cabeçalhos de Secção**
   - *Descrição*: Os cabeçalhos de secção são utilizados para organizar o conteúdo.
   - *Aplicação em menus*: Menus complexos podem beneficiar de cabeçalhos para organizar grupos de itens relacionados.

2. **2.1.3 Teclado (Sem Exceção)**
   - *Descrição*: Toda a funcionalidade do conteúdo é operável através de uma interface de teclado sem requerer tempos específicos para teclas individuais.
   - *Aplicação em menus*: Não deve haver limitações temporais para a interação com o menu via teclado.

---

Lembra-te que os menus são frequentemente o primeiro ponto de contacto que os utilizadores têm com o teu site ou aplicação. Torná-los acessíveis não só beneficia pessoas com deficiência mas também melhora a experiência de utilizador para todos.

Uma abordagem inclusiva ao design de menus não é apenas uma obrigação legal em muitos contextos, mas também uma prática que demonstra respeito por todos os utilizadores e amplia o alcance do teu conteúdo ou serviço.
