# Disposição, Espaçamento e Agrupamentos

## Introdução

A organização visual de uma página web é como a arrumação de uma casa - quando tudo está bem organizado e com espaço adequado, é mais fácil encontrar o que procuramos. Uma boa disposição, espaçamento apropriado e agrupamentos lógicos são fundamentais para criar websites acessíveis e fáceis de usar.

### Como as Pessoas com Deficiência Dependem da Disposição, Espaçamento e Agrupamentos

**Pessoas com Deficiências Cognitivas**
Para estas pessoas, uma página mal organizada é como um quarto cheio de objetos espalhados aleatoriamente. Necessitam de:

- Agrupamentos claros de informação relacionada
- Espaço suficiente entre diferentes secções
- Hierarquia visual óbvia

**Pessoas com Baixa Visão**
Quando usam ampliação de ecrã, é como ver a página através de uma lupa - apenas conseguem ver uma pequena área de cada vez. Precisam de:

- Espaçamento generoso entre elementos
- Alinhamentos consistentes
- Agrupamentos lógicos que façam sentido mesmo quando ampliados

**Utilizadores de Leitores de Ecrã**
Para estes utilizadores, a estrutura da página deve fazer sentido mesmo sem pistas visuais. Necessitam de:

- Agrupamentos semânticos corretos
- Ordem lógica do conteúdo
- Relações claras entre elementos relacionados

**Pessoas com Deficiência Motora**
Estas pessoas podem ter dificuldade em interagir com elementos que estão muito próximos uns dos outros. Precisam de:

- Espaço suficiente entre elementos interativos 
- Mecanismos que permitam reverter seleções erradas

### Requisitos de Acessibilidade para Disposição, Espaçamento e Agrupamentos

1. **Espaçamento**
   
   - Margens e preenchimentos adequados
   - Espaço entre linhas de pelo menos 1.5 vezes o tamanho da fonte
   - Separação clara entre secções diferentes

2. **Agrupamento Visual**
   
   - Elementos relacionados próximos uns dos outros
   - Separação visual entre grupos diferentes
   - Uso de bordas, cores ou espaços para definir grupos

3. **Consistência**
   
   - Alinhamentos consistentes
   - Padrões de espaçamento repetidos
   - Hierarquia visual coerente

## Técnicas de Codificação

```html
<!-- Mau exemplo -->
<div>
  <span>Nome:</span><input type="text">
  <span>Email:</span><input type="email">
  <button>Enviar</button>
</div>

<!-- Bom exemplo -->
<form class="contact-form">
  <div class="form-group">
    <label for="name">Nome:</label>
    <input type="text" id="name">
  </div>
  <div class="form-group">
    <label for="email">Email:</label>
    <input type="email" id="email">
  </div>
  <div class="form-actions">
    <button type="submit">Enviar</button>
  </div>
</form>
```

```css
/* Mau exemplo */
.form-group {
  margin: 5px;
}

/* Bom exemplo */
.form-group {
  margin-bottom: 1.5rem;
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
}

.form-actions {
  margin-top: 2rem;
  padding-top: 1rem;
  border-top: 1px solid #ddd;
}
```

*Explicação:* No mau exemplo, todos os elementos estão colocados sem qualquer estrutura ou agrupamento lógico, com um espaçamento mínimo de apenas 5px que torna difícil distinguir e interagir com os diferentes campos. Em contraste, o bom exemplo apresenta uma estrutura clara onde elementos relacionados (etiqueta e campo) estão agrupados em containers com `class="form-group"`, cada grupo tem um espaçamento generoso (`margin-bottom: 1.5rem`) e está visualmente delimitado com uma borda e padding (`padding: 1rem`), enquanto a área de ações do formulário está claramente separada com uma borda superior e margens maiores (`margin-top: 2rem`). 

## Recomendações para Conteúdo Acessível

1. **Sistema de Grelha Consistente**
   ```css
   .container {
     display: grid;
     grid-template-columns: repeat(12, 1fr);
     gap: 2rem;
   }

   .content-area {
     grid-column: span 8;
   }

   .sidebar {
     grid-column: span 4;
   }
   ```

2. **Espaçamento Proporcional**
   ```css
   :root {
     --spacing-unit: 0.5rem;
   }

   .section {
     margin-bottom: calc(var(--spacing-unit) * 4);
     padding: calc(var(--spacing-unit) * 2);
   }
   ```

### Erros Comuns

1. **Espaçamento Inconsistente**
   ```css
   /* Evite */
   .section-1 { margin-bottom: 20px; }
   .section-2 { margin-bottom: 32px; }
   .section-3 { margin-bottom: 15px; }

   /* Prefira */
   .section {
     margin-bottom: 2rem;
   }
   ```

2. **Agrupamentos Pouco Claros**
   ```css
   /* Evite */
   .content > * {
     margin: 10px;
   }

   /* Prefira */
   .content-group {
     padding: 1.5rem;
     border-radius: 8px;
     background: #f5f5f5;
   }
   ```

## Cartões e Componentes Visuais

Os cartões são componentes de interface frequentemente utilizados para agrupar informações relacionadas, mas muitas vezes apresentam problemas de acessibilidade, especialmente relacionados com contraste e foco.

### Requisitos de Acessibilidade para Cartões

1. **Contraste e Delimitação**
   
   - Bordas com contraste mínimo de 3:1 contra o fundo
   - Se não usar bordas, use uma diferença de cor de fundo com contraste de 3:1
   - Elementos interativos dentro do cartão devem ser claramente distinguíveis

2. **Interação e Foco**
   
   - Se todo o cartão for clicável, deve receber foco como uma unidade
   - Indicadores de foco devem ser visíveis com contraste adequado
   - O conteúdo do cartão deve ser compreensível mesmo sem depender da cor

### Técnicas para Cartões Acessíveis

```html
<!-- Mau exemplo -->
<div class="card" style="background-color: #f5f5f5;">
  <h3>Título do Cartão</h3>
  <p>Descrição do cartão com informações.</p>
</div>

<!-- Bom exemplo -->
<div class="card">
  <h3 class="card-title">Título do Cartão</h3>
  <p class="card-description">Descrição do cartão com informações.</p>
  <a href="#" class="card-link">Saiba mais <span class="sr-only">sobre Título do Cartão</span></a>
</div>
```

```css
/* Mau exemplo */
.card {
  background-color: #f5f5f5; /* Contraste insuficiente com fundo branco */
  padding: 10px;
}

/* Bom exemplo */
.card {
  background-color: #ffffff;
  border: 2px solid #595959; /* Borda com contraste adequado */
  border-radius: 4px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.card-title {
  margin-top: 0;
  margin-bottom: 1rem;
  color: #333;
}

.card-link {
  display: inline-block;
  margin-top: 1rem;
  color: #0056b3; /* Cor com contraste adequado */
  text-decoration: underline; /* Identificador visual além da cor */
}

.card-link:focus {
  outline: 3px solid #4A90E2;
  outline-offset: 2px;
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

*Explicação:* O mau exemplo usa um fundo cinza claro (#f5f5f5) que não fornece contraste suficiente contra um fundo de página branco, e não tem bordas ou outros elementos para delimitar claramente o cartão. Já o bom exemplo utiliza uma borda de contraste adequado, espaçamento interno generoso, uma hierarquia clara com estilos distintos para título e descrição, e uma ligação com estilo apropriado que inclui texto para leitores de ecrã.

### Cartões Totalmente Clicáveis

Quando todo o cartão funciona como um link, é importante garantir que:

```html
<a href="/artigo" class="card-link">
  <div class="card">
    <h3 class="card-title">Título do Artigo</h3>
    <p class="card-description">Resumo do artigo que expande o título e oferece mais contexto.</p>
    <span class="card-cta">Ler mais <span aria-hidden="true">→</span></span>
  </div>
</a>
```

```css
.card-link {
  display: block;
  text-decoration: none;
  color: inherit;
}

.card-link:focus {
  outline: none;
}

.card-link:focus .card {
  outline: 3px solid #4A90E2;
  outline-offset: 2px;
}

.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
}

.card-link:hover .card, 
.card-link:focus .card {
  transform: translateY(-3px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.card-cta {
  display: block;
  margin-top: 1rem;
  color: #0056b3;
  font-weight: bold;
}
```

*Explicação:* Este exemplo mostra como tornar um cartão inteiro clicável de forma acessível. Em vez de usar JavaScript para criar uma área clicável ou aninhar incorretamente elementos semânticos, envolve-se todo o cartão num elemento `<a>`. O estilo é aplicado para garantir uma indicação clara do estado de foco e hover, e o texto "Ler mais" é estilizado para parecer um call-to-action, com uma seta como indicador visual secundário.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Use espaçamento consistente e proporcional
- Agrupe elementos relacionados visualmente e semanticamente
- Mantenha alinhamentos coerentes
- Crie uma hierarquia visual clara
- Use um sistema de grelha para organização
- Garanta que cartões e outros componentes visuais têm contraste adequado

### Exercícios Práticos

1. **Análise de Layout**
   
   - Escolha um website
   - Identifique os diferentes grupos de conteúdo
   - Avalie o espaçamento e a hierarquia visual
   - Proponha melhorias

2. **Criação de Sistema de Espaçamento**
   
   - Desenvolva um sistema de espaçamento com variáveis CSS
   - Aplique o sistema a um formulário
   - Teste com diferentes tamanhos de ecrã

3. **Redesenho de Cartões**
   
   - Analise cartões em websites populares
   - Identifique problemas de contraste e delimitação
   - Redesenhe os cartões para melhorar a acessibilidade
   - Teste com simuladores de daltonismo e baixa visão

4. **Teste de Responsividade**
   
   - Crie uma página com diferentes grupos de conteúdo
   - Implemente um layout responsivo
   - Teste com zoom até 200%
   - Verifique se os agrupamentos mantêm sentido