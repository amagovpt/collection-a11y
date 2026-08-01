---
title: Redimensionamento de Menus
layout: default
nav_order: 4
---

# Redimensionamento de Menus

## Introdução

Quando criamos menus para websites ou aplicações, precisamos lembrar que nem todas as pessoas veem ou interagem com o ecrã da mesma forma. Para muitos utilizadores com deficiência, a capacidade de redimensionar os menus não é apenas uma preferência, mas uma necessidade essencial para acederem à informação.

Neste módulo, vamos explorar porque o redimensionamento de menus é fundamental para a acessibilidade e como podemos implementá-lo corretamente nas nossas interfaces.

### Como as Pessoas com Deficiência Dependem da Possibilidade de Redimensionar Menus

Diferentes utilizadores precisam de redimensionar menus por diversas razões:

#### Pessoas com Baixa Visão

Para pessoas com baixa visão, o texto e os elementos pequenos podem ser difíceis ou impossíveis de ler. Estas pessoas frequentemente:

- Aumentam o tamanho do texto no navegador (zoom de texto)
- Usam o zoom geral da página (aumentando todos os elementos)
- Ajustam as configurações de visualização do sistema operativo

**Exemplo prático:** Imagine que a Maria tem degenerescência macular, uma condição que afeta a visão central. Ela precisa aumentar o tamanho da página para 200% para conseguir ler o conteúdo. Se o menu do site não se ajustar corretamente a este aumento, os itens podem sobrepor-se, ficarem cortados ou até mesmo desaparecerem da vista, tornando a navegação impossível.

**Por que isto importa:** Quando um menu não se adapta ao redimensionamento, a Maria fica impossibilitada de navegar pelo site, ficando excluída do acesso à informação que as outras pessoas conseguem facilmente obter.

#### Pessoas com Destreza Limitada

Para utilizadores com limitações motoras, como tremores nas mãos ou mobilidade reduzida:

- Alvos maiores (botões, links, itens de menu) são mais fáceis de acertar
- O espaçamento adequado entre elementos ajuda a evitar cliques acidentais
- O redimensionamento permite ajustar a interface às suas necessidades específicas

**Exemplo prático:** O João tem Parkinson, o que causa tremores nas mãos. Itens de menu pequenos e próximos uns dos outros representam verdadeiros desafios para ele. Quando ele consegue aumentar o tamanho dos elementos e do espaçamento entre eles, a sua taxa de sucesso ao clicar nos itens certos aumenta significativamente.

**Por que isto importa:** Sem a possibilidade de redimensionar, o João pode precisar de várias tentativas para clicar no item desejado, o que torna a navegação frustrante e demorada.

#### Pessoas com Dificuldades Cognitivas

Algumas pessoas com dificuldades cognitivas ou de aprendizagem beneficiam de:

- Layout mais espaçado e menos distrativo
- Texto maior e mais legível
- Menos itens visíveis de uma só vez

**Exemplo prático:** A Ana tem dislexia e encontra dificuldades ao processar muitas informações simultaneamente. Um menu compacto com vários níveis e muitos itens sobrecarrega-a cognitivamente. Quando ela pode aumentar o texto e simplificar a visualização, consegue processar melhor as opções disponíveis.

**Por que isto importa:** O redimensionamento não é apenas uma questão visual, mas também uma ferramenta que pode reduzir a carga cognitiva e melhorar a compreensão.

### Requisitos de Acessibilidade para Redimensionamento de Menus

Os principais requisitos de acessibilidade relacionados com o redimensionamento de menus baseiam-se nas Diretrizes de Acessibilidade para Conteúdo Web (WCAG):

#### 1. Redimensionável Até 200% (WCAG 1.4.4, Nível AA)

O conteúdo deve poder ser redimensionado até 200% sem perda de conteúdo ou funcionalidade, e sem necessidade de varrimento horizontal (exceto para conteúdos que exigem layout bidimensional, como tabelas complexas ou imagens).

**Em termos simples:** Quando um utilizador duplica o tamanho da página, todos os menus devem continuar a funcionar corretamente e todo o conteúdo deve permanecer visível e utilizável.

#### 2. Reflow (WCAG 1.4.10, Nível AA)

O conteúdo deve reorganizar-se (reflow) quando redimensionado até 400% para que não seja necessário varrimento em duas direções, com algumas exceções específicas.

**Em termos simples:** O design deve ser fluido o suficiente para se reorganizar quando ampliado, mantendo o varrimento apenas vertical na maioria dos casos.

#### 3. Espaçamento do Texto (WCAG 1.4.12, Nível AA)

Os utilizadores devem poder ajustar características de texto como o espaçamento entre linhas, parágrafos, letras e palavras sem perda de conteúdo ou funcionalidade.

**Em termos simples:** Se alguém precisar de mais espaço entre as letras ou palavras para ler melhor, os menus devem acomodar essas alterações.

#### 4. Conteúdo em Hover ou Foco (WCAG 1.4.13, Nível AA)

Quando o conteúdo adicional aparece ao passar o rato ou ao focar um elemento (como em menus dropdown):

- Deve ser possível dispensar esse conteúdo sem mover o ponteiro ou o foco
- O conteúdo deve permanecer visível até que o utilizador o dispense, o ponteiro seja movido, ou o foco seja removido

**Em termos simples:** Os submenus que aparecem devem ser fáceis de usar e não devem desaparecer inadvertidamente quando o utilizador tenta clicar neles.

## Técnicas de Codificação

Vamos explorar as principais técnicas para criar menus que se redimensionam corretamente:

### 1. Design Responsivo com CSS Flexbox e Grid

O CSS Flexbox e Grid são ferramentas poderosas para criar layouts que se ajustam dinamicamente a diferentes tamanhos.

**Exemplo de um menu horizontal usando Flexbox:**

```css
.menu {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  padding: 0;
  margin: 0;
}

.menu-item {
  padding: 0.5em 1em;
}

/* Para ecrãs menores ou quando ampliado */
@media (max-width: 768px) {
  .menu {
    flex-direction: column;
  }
}
```

**Porque funciona bem:** Este código permite que os itens do menu se organizem horizontalmente quando há espaço suficiente e passem a vertical (empilhados) quando o espaço é reduzido, como acontece em ecrãs pequenos ou quando o conteúdo é ampliado.

### 2. Unidades Relativas em Vez de Absolutas

Use unidades relativas como `em`, `rem` e percentagens em vez de píxeis fixos (`px`).

**Exemplo incorreto vs. correto:**

```css
/* Incorreto: unidades fixas */
.menu-item {
  font-size: 16px;
  padding: 10px 15px;
  margin: 5px;
}

/* Correto: unidades relativas */
.menu-item {
  font-size: 1rem;  /* Relativo ao tamanho base definido na raiz */
  padding: 0.6em 1em;  /* Relativo ao tamanho da fonte do elemento */
  margin: 0.3em;
}
```

**Porque funciona bem:** As unidades relativas ajustam-se proporcionalmente quando o utilizador altera o tamanho da fonte no navegador ou aumenta o zoom. Se a fonte base aumenta, todos os elementos definidos com `rem` ou `em` aumentam proporcionalmente.

### 3. Menus Hambúrguer para Ecrãs Pequenos ou Zoom Alto

Ao redimensionar, pode ser necessário transformar um menu horizontal numa versão compacta (menu hambúrguer).

```css
/* Menu normal para ecrãs grandes */
.menu {
  display: flex;
}

.hamburger-button {
  display: none;
}

/* Menu hamburger para ecrãs pequenos ou zoom alto */
@media (max-width: 768px) {
  .menu {
    display: none;
  }
  
  .menu.active {
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 60px;
    left: 0;
    width: 100%;
    background: white;
  }
  
  .hamburger-button {
    display: block;
  }
}
```

**JavaScript correspondente:**

```javascript
document.querySelector('.hamburger-button').addEventListener('click', function() {
  document.querySelector('.menu').classList.toggle('active');
});
```

**Porque funciona bem:** Esta técnica preserva o acesso a todos os itens do menu, reorganizando-os num formato que funciona melhor em espaços reduzidos. A alternância por JavaScript permite mostrar/ocultar o menu conforme necessário.

### 4. Testes com Zoom e Ferramentas de Acessibilidade

Não basta apenas escrever o código – é essencial testá-lo regularmente:

- Teste o site com zoom de 200% e 400%
- Verifique o comportamento ao aumentar apenas o texto (sem zoom total)
- Use ferramentas de inspeção para simular diferentes dispositivos

**Exemplo de teste manual:**

1. Abra o site no navegador
2. Prima Ctrl + (ou Cmd + no Mac) várias vezes para aumentar o zoom
3. Verifique se todos os itens do menu permanecem acessíveis e funcionais
4. Teste também nas definições do navegador para aumentar apenas o texto, sem zoom geral

**Porque isto é importante:** O teste real revela problemas que podem não ser evidentes durante o desenvolvimento, como elementos sobrepostos ou funcionalidades quebradas em determinados níveis de zoom.

## Recomendações para Conteúdo Acessível

### 1. Espaçamento Generoso Entre Elementos

- Adicione espaço suficiente entre itens de menu
- Use margens e padding adequados que aumentem proporcionalmente
- Certifique-se de que áreas clicáveis são suficientemente grandes

**Exemplo:**
```css
.menu-item a {
  padding: 0.75em 1em;  /* Padding generoso e relativo */
  margin: 0.2em;
  display: block;  /* Faz com que toda a área seja clicável */
  min-height: 44px;  /* Altura mínima recomendada para áreas táteis */
  min-width: 44px;  /* Largura mínima recomendada para áreas táteis */
}
```

**Porque funciona bem:** O espaçamento adequado reduz a probabilidade de cliques acidentais, especialmente para pessoas com limitações motoras ou quando visualizado em dispositivos táteis.

### 2. Feedback Visual Claro e Consistente

- Forneça indicações visuais claras do estado atual (ativo, hover, foco)
- Use contraste suficiente para estes indicadores
- Mantenha o feedback consistente em diferentes tamanhos

**Exemplo:**
```css
.menu-item a {
  transition: background-color 0.3s;
}

.menu-item a:hover,
.menu-item a:focus {
  background-color: #f0f0f0;
  outline: 2px solid #0066cc;  /* Contorno visível no foco */
  outline-offset: -2px;
}

.menu-item.active a {
  background-color: #e0e0e0;
  font-weight: bold;
}
```

**Porque funciona bem:** Feedback visual claro ajuda todos os utilizadores, mas é especialmente valioso para pessoas com deficiências cognitivas ou baixa visão, que precisam de pistas visuais mais evidentes.

### Erros Comuns

#### 1. Texto que Transborda Contentores

**Problema:** Quando ampliado, o texto ultrapassa os limites dos seus contentores, tornando-se ilegível ou interferindo com outros elementos.

**Exemplo de código problemático:**
```css
.menu-item {
  width: 100px;  /* Largura fixa */
  overflow: hidden;  /* Corta qualquer conteúdo que não caiba */
}
```

**Solução:**
```css
.menu-item {
  min-width: 6rem;  /* Largura mínima, não fixa */
  width: auto;  /* Permite expandir conforme necessário */
  overflow: visible;  /* Não corta o conteúdo */
}
```

**Por que esta correção funciona:** Ao permitir que os elementos se expandam naturalmente para acomodar o conteúdo, evitamos cortes ou sobreposições quando o texto é ampliado.

#### 2. Layouts que Quebram com Zoom

**Problema:** O layout completo do menu desmorona-se ou os elementos sobrepõem-se de forma ilegível quando ampliados.

**Exemplo de código problemático:**
```css
.menu {
  display: flex;
  flex-wrap: nowrap;  /* Impede a reorganização dos itens */
}
```

**Solução:**
```css
.menu {
  display: flex;
  flex-wrap: wrap;  /* Permite que os itens passem para a linha seguinte */
}

@media (max-width: 768px) {
  .menu {
    flex-direction: column;  /* Muda para empilhado em ecrãs menores */
  }
}
```

**Por que esta correção funciona:** A propriedade `flex-wrap: wrap` permite que os itens do menu fluam naturalmente para baixo quando não cabem horizontalmente, enquanto a media query adapta completamente o layout para dispositivos menores ou zoom alto.

#### 3. Scroll Horizontal Forçado

**Problema:** Menus que forçam o utilizador a deslocações horizontais quando redimensionados, o que viola o critério de sucesso 1.4.10 (Reflow) das WCAG.

**Exemplo de código problemático:**
```css
.menu {
  width: 1000px;  /* Largura fixa grande */
  white-space: nowrap;  /* Impede quebras de linha */
}
```

**Solução:**
```css
.menu {
  width: 100%;  /* Usa a largura disponível */
  max-width: 1000px;  /* Limita o tamanho máximo */
  white-space: normal;  /* Permite quebras de linha */
}
```

**Por que esta correção funciona:** O uso de larguras flexíveis e permitir quebras de linha garante que o conteúdo se adapte ao espaço disponível, evitando varrimento horizontal.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Impacto na acessibilidade:** O redimensionamento adequado dos menus é essencial para pessoas com baixa visão, limitações motoras e dificuldades cognitivas.

2. **Requisitos WCAG relevantes:**
   - Redimensionamento até 200% sem perda de funcionalidade (1.4.4)
   - Reflow/reorganização até 400% sem varrimentos horizontal (1.4.10)
   - Ajuste do espaçamento do texto (1.4.12)
   - Controlo sobre conteúdos em hover/foco (1.4.13)

3. **Técnicas essenciais:**
   - Uso de CSS Flexbox e Grid para layouts adaptativos
   - Preferência por unidades relativas (em, rem, %) em vez de fixas (px)
   - Design responsivo com media queries
   - Menus alternativos (como menus hambúrguer) para ecrãs menores ou zoom elevado

4. **Recomendações de design:**
   - Estrutura simples e intuitiva
   - Espaçamento generoso entre elementos
   - Feedback visual claro e consistente
   - Suporte para diferentes métodos de interação (rato, teclado, toque)

5. **Erros a evitar:**
   - Contenção rígida que corta texto ampliado
   - Layouts que quebram com zoom
   - Dependência exclusiva de eventos "hover"
   - Scroll horizontal forçado

### Exercícios Práticos

#### Exercício 1: Análise de Menu Existente

**Objetivo:** Avaliar a acessibilidade de redimensionamento de um menu real.

**Instruções:**

1. Escolha um site que utilize regularmente (ex: portal de notícias, comércio eletrónico, etc.)
2. Aumente o zoom do navegador para 200% (Ctrl/Cmd +)
3. Tente navegar pelo menu principal e responda:
   - O menu continua completamente funcional?
   - Todo o texto permanece legível?
   - É necessário rolar horizontalmente?
   - Como o menu se adapta à ampliação?
4. Documente os problemas encontrados e sugira melhorias

#### Exercício 2: Corrigir um Menu Não Responsivo

**Objetivo:** Praticar a conversão de um menu com tamanho fixo para um menu redimensionável.

**Código base problemático:**
```html
<nav>
  <ul class="menu">
    <li class="menu-item"><a href="#">Início</a></li>
    <li class="menu-item"><a href="#">Produtos</a></li>
    <li class="menu-item"><a href="#">Serviços</a></li>
    <li class="menu-item"><a href="#">Sobre</a></li>
    <li class="menu-item"><a href="#">Contacto</a></li>
  </ul>
</nav>

<style>
.menu {
  width: 800px;
  height: 60px;
  margin: 0 auto;
  background-color: #333;
  list-style: none;
  padding: 0;
  overflow: hidden;
}

.menu-item {
  float: left;
}

.menu-item a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 16px;
}

.menu-item a:hover {
  background-color: #111;
}
</style>
```

**Instruções:**

1. Modifique o CSS para tornar o menu totalmente responsivo
2. Garanta que funciona bem com zoom de até 200%
3. Implemente uma solução para dispositivos móveis ou zoom elevado
4. Teste a sua solução aumentando o zoom do navegador

#### Exercício 3: Criar um Menu Multi-nível Acessível

**Objetivo:** Desenvolver um menu dropdown que mantenha a acessibilidade mesmo quando redimensionado.

**Instruções:**

1. Crie um menu horizontal com pelo menos um submenu dropdown
2. Implemente funcionalidade que:
   - Funcione com rato (hover)
   - Funcione com teclado (focus)
   - Funcione com dispositivos táteis
3. Garanta que todos os itens permanecem acessíveis quando ampliados até 200%
4. Teste a sua solução em diferentes tamanhos de ecrã e níveis de zoom

#### Exercício 4: Teste Sistemático com Ferramentas de Acessibilidade

**Objetivo:** Aprender a usar ferramentas específicas para testar o redimensionamento de menus.

**Instruções:**

1. Escolha um dos menus que desenvolveu nos exercícios anteriores
2. Teste-o usando as seguintes ferramentas/métodos:
   - Inspetor de elementos do navegador com emulação de dispositivos
   - Extensão Wave (Web Accessibility Evaluation Tool)
   - Aumento de texto nas definições do navegador (sem zoom geral)
   - Teste com um leitor de ecrã (NVDA, VoiceOver ou outro disponível)
3. Documente os problemas encontrados com cada ferramenta
4. Corrija os problemas identificados e teste novamente
