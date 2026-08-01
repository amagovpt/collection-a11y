# Gráficos e Visualização de Dados Acessíveis

## Introdução

A visualização de dados é uma forma poderosa de comunicar informações complexas, mas para que seja realmente eficaz, deve ser acessível a todos. Gráficos acessíveis permitem que pessoas com diferentes capacidades possam compreender as mesmas informações, independentemente de como acedem ao conteúdo.

### Como as Pessoas com Deficiência Acedem a Gráficos

**Pessoas com Deficiência Visual**
Para estas pessoas, um gráfico visual é como um livro em idioma desconhecido - precisam de uma "tradução" para o formato que conseguem perceber. Necessitam de:

- Descrições textuais detalhadas
- Dados tabulares como alternativa
- Elementos com contraste adequado

**Pessoas com Daltonismo**
Estas pessoas podem ver a forma do gráfico, mas têm dificuldade em distinguir cores semelhantes. É como tentar ler um mapa onde as diferentes regiões têm cores muito parecidas. Precisam de:

- Paletas de cores que funcionem com diferentes tipos de daltonismo
- Padrões, texturas ou ícones além da cor
- Legendas explícitas e claras

**Pessoas com Deficiências Cognitivas**
Para estes utilizadores, gráficos complexos podem ser confusos. É como tentar resolver um puzzle com demasiadas peças. Necessitam de:

- Visualizações simples e diretas
- Legendas claras e concisas
- Informação dividida em partes compreensíveis

### Requisitos de Acessibilidade para Gráficos

1. **Contraste e Cores**
   
   - Elementos do gráfico com contraste mínimo de 3:1 contra o fundo
   - Paletas de cores que funcionem para diferentes tipos de daltonismo
   - Uso de padrões ou formas além da cor para distinguir dados

2. **Texto Alternativo e Descrições**
   
   - Descrições concisas e informativas
   - Texto alternativo que explique tendências e conclusões do gráfico
   - Tabelas de dados como alternativa ao gráfico visual

3. **Interatividade Acessível**
   
   - Gráficos interativos navegáveis por teclado
   - Feedback sonoro ou textual em alterações
   - Controlos claramente identificáveis e utilizáveis

## Técnicas para Gráficos Acessíveis

```html
<!-- Mau exemplo -->
<div class="chart">
  <!-- Gráfico gerado por JavaScript sem alternativa -->
  <canvas id="myChart"></canvas>
</div>

<!-- Bom exemplo -->
<figure class="chart-container">
  <figcaption id="chart-title">Vendas Mensais por Região em 2024</figcaption>
  <div class="chart" aria-labelledby="chart-title" aria-describedby="chart-desc">
    <canvas id="myChart"></canvas>
  </div>
  <div id="chart-desc" class="sr-only">
    O gráfico mostra que as vendas na região Norte aumentaram 15% entre janeiro e março, 
    enquanto as vendas na região Sul permaneceram estáveis. A região Leste teve o maior 
    crescimento, com 23% no primeiro trimestre.
  </div>
  <a href="#chart-data-table" class="skip-link">Ver dados em formato de tabela</a>
</figure>

<table id="chart-data-table" class="data-table">
  <caption>Vendas Mensais por Região (2024)</caption>
  <thead>
    <tr>
      <th scope="col">Mês</th>
      <th scope="col">Norte</th>
      <th scope="col">Sul</th>
      <th scope="col">Leste</th>
      <th scope="col">Oeste</th>
    </tr>
  </thead>
  <tbody>
    <!-- Dados da tabela -->
  </tbody>
</table>
```

*Explicação:* O mau exemplo simplesmente insere um canvas para o gráfico sem qualquer informação contextual ou alternativa. O bom exemplo envolve o gráfico num elemento `<figure>` com uma legenda clara, fornece uma descrição textual oculta para leitores de ecrã, e inclui uma ligação para uma tabela com os mesmos dados em formato acessível.

### Código JavaScript para Gráficos Acessíveis

```javascript
// Paleta de cores acessível com bom contraste e distinta para daltonismo
const accessibleColors = [
  '#0072B2', // Azul
  '#E69F00', // Laranja
  '#009E73', // Verde
  '#CC79A7', // Rosa
  '#56B4E9', // Azul claro
  '#D55E00', // Vermelho
  '#F0E442'  // Amarelo
];

// Configuração de um gráfico com cores e padrões acessíveis
const chart = new Chart(ctx, {
  type: 'bar',
  data: {
    labels: ['Janeiro', 'Fevereiro', 'Março', 'Abril'],
    datasets: [
      {
        label: 'Norte',
        backgroundColor: accessibleColors[0],
        // Adicionar padrão para distinção além da cor
        borderWidth: 2,
        borderColor: '#000',
        data: [12, 19, 3, 5]
      },
      {
        label: 'Sul',
        backgroundColor: accessibleColors[1],
        // Padrão diferente
        borderWidth: 2,
        borderDash: [5, 5],
        borderColor: '#000',
        data: [8, 15, 7, 9]
      }
    ]
  },
  options: {
    responsive: true,
    plugins: {
      legend: {
        display: true,
        position: 'top',
        labels: {
          // Aumentar tamanho do texto para melhor legibilidade
          font: {
            size: 16
          }
        }
      },
      tooltip: {
        callbacks: {
          // Tooltip melhorado para mais contexto
          label: function(context) {
            const label = context.dataset.label || '';
            const value = context.parsed.y;
            return `${label}: ${value} unidades (${context.parsed.y / 100 * 100}% do total)`;
          }
        }
      }
    }
  }
});

// Adicionar navegação por teclado
document.getElementById('myChart').setAttribute('tabindex', '0');
document.getElementById('myChart').addEventListener('keydown', function(e) {
  // Código para navegação com teclado entre pontos de dados
});
```

*Explicação:* Este exemplo mostra como configurar um gráfico com cores acessíveis para daltonismo, adicionando também padrões de bordas e cores de contorno para distinguir diferentes séries de dados. O código também inclui legendas melhoradas, tooltips mais descritivos, e configuração básica para navegação por teclado.

## Recomendações para Visualização de Dados Acessível

1. **Escolha o Tipo de Gráfico Apropriado**
   
   - Use gráficos de barras para comparações simples
   - Use linhas para mostrar tendências ao longo do tempo
   - Evite gráficos circulares quando houver muitas categorias
   - Priorize simplicidade sobre estética

2. **Adicione Elementos Distintivos**
   
   - Use padrões de preenchimento diferentes (tracejado, pontilhado)
   - Adicione ícones ou símbolos junto às legendas
   - Use diferentes formas para pontos de dados em gráficos de linhas
   - Adicione rótulos diretamente nos dados quando possível

3. **Otimize para Tecnologias de Apoio**
   ```html
   <div class="chart-wrapper" role="img" aria-label="Gráfico de Barras" aria-describedby="chart-description">
     <canvas id="barChart"></canvas>
     <div id="chart-description" class="visually-hidden">
       Este gráfico mostra as vendas trimestrais de 2024. O primeiro trimestre teve o melhor 
       desempenho com 1.2 milhões de euros, seguido pelo segundo trimestre com 900 mil euros.
       O terceiro trimestre foi o mais fraco, com apenas 600 mil euros.
     </div>
   </div>
   ```

### Erros Comuns

1. **Dependência Exclusiva de Cor**
   ```javascript
   // Evite
   const datasets = [
     {
       label: 'Alto',
       backgroundColor: 'red',
       data: [5, 7, 9]
     },
     {
       label: 'Médio',
       backgroundColor: 'orange',
       data: [3, 4, 6]
     },
     {
       label: 'Baixo',
       backgroundColor: 'green',
       data: [1, 2, 3]
     }
   ];

   // Prefira
   const datasets = [
     {
       label: 'Alto',
       backgroundColor: 'rgb(216, 27, 96)',
       borderWidth: 2,
       borderColor: '#000',
       pattern: {
         type: 'line',
         rotation: 45
       },
       data: [5, 7, 9]
     },
     {
       label: 'Médio',
       backgroundColor: 'rgb(30, 136, 229)',
       borderWidth: 2,
       borderDash: [5, 5],
       borderColor: '#000',
       pattern: {
         type: 'dot',
         size: 5
       },
       data: [3, 4, 6]
     },
     {
       label: 'Baixo',
       backgroundColor: 'rgb(46, 125, 50)',
       borderWidth: 2,
       borderColor: '#000',
       pattern: {
         type: 'zigzag',
         size: 8
       },
       data: [1, 2, 3]
     }
   ];
   ```

2. **Ausência de Tabela de Dados**
   
   Forneça uma tabela de dados como alternativa aos gráficos visuais. A tabela pode estar inicialmente oculta para utilizadores visuais, mas deve ser facilmente acessível.

   ```html
   <div class="chart-container">
     <canvas id="myChart"></canvas>
     <button class="toggle-table" aria-expanded="false" aria-controls="data-table">
       Mostrar dados em tabela
     </button>
     <div id="data-table" class="data-table-container" hidden>
       <table>
         <!-- Dados em formato tabular -->
       </table>
     </div>
   </div>
   ```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Use cores acessíveis para daltonismo
- Forneça sempre alternativas textuais para gráficos
- Adicione padrões ou texturas além da cor
- Mantenha gráficos simples e diretos
- Inclua tabelas de dados como alternativa
- Garanta que elementos gráficos têm contraste suficiente

### Exercícios Práticos

1. **Auditoria de Gráficos**
   
   - Analise gráficos num site de notícias ou estatísticas
   - Verifique contraste, uso de cor e alternativas textuais
   - Proponha melhorias específicas

2. **Redesenho de Visualizações**
   
   - Selecione um gráfico existente
   - Redesenhe-o usando princípios de acessibilidade
   - Inclua alternativas textuais e tabulares
   - Teste com simuladores de daltonismo

3. **Implementação de Gráfico Acessível**
   
   - Crie um gráfico simples com uma biblioteca de sua escolha
   - Implemente cores e padrões acessíveis
   - Adicione descrições e alternativas textuais
   - Adicione navegação por teclado
   - Teste com um leitor de ecrã