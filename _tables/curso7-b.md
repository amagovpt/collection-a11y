---
title: Células de Dados e de Cabeçalho
layout: default
nav_order: 2
---
# Células de Dados e de Cabeçalho

## Introdução

Imagine uma tabela como um puzzle onde cada peça tem o seu lugar específico. As células de dados são as peças coloridas que contêm a informação principal, enquanto que as células de cabeçalho são as peças da moldura que nos ajudam a perceber onde cada peça se encaixa. Sem as peças da moldura, seria muito difícil montar o puzzle!

### Como as Pessoas com Deficiência usam Células de Dados e de Cabeçalho

#### Utilizadores de Leitores de Ecrã

Os leitores de ecrã são como guias turísticos para pessoas cegas ou com baixa visão. Quando chegam a uma tabela, estes "guias" precisam de orientações claras para explicar o que cada informação significa.

**Analogia:** Imagine que está numa biblioteca gigante onde todos os livros estão organizados em estantes. Se não houver etiquetas nas estantes (como "História", "Ciência", "Romance"), seria impossível encontrar o livro que procura. As células de cabeçalho funcionam como essas etiquetas.

Quando um leitor de ecrã encontra uma célula de dados, ele procura automaticamente pelo cabeçalho correspondente. Por exemplo, numa tabela de vendas:

```html
<!-- Exemplo BOM -->
<table>
  <thead>
    <tr>
      <th>Mês</th>
      <th>Vendas</th>
      <th>Lucro</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Janeiro</td>
      <td>15.000€</td>
      <td>3.500€</td>
    </tr>
  </tbody>
</table>
```

**O que funciona bem:** O leitor de ecrã consegue anunciar "Vendas: 15.000 euros" em vez de apenas "15.000 euros", dando contexto essencial ao utilizador.

#### Utilizadores com Dificuldades Cognitivas

Pessoas com dislexia, défice de atenção ou outras dificuldades cognitivas beneficiam enormemente de estruturas claras. Os cabeçalhos bem definidos funcionam como marcos visuais que os ajudam a navegar e compreender a informação.

**Analogia:** É como ter um mapa bem organizado numa cidade desconhecida - os marcos (cabeçalhos) ajudam-nos a não nos perdermos e a encontrar o que procuramos.

#### Utilizadores que Navegam por Teclado

Muitos utilizadores não podem usar o rato e dependem da navegação por teclado. Para eles, as células de cabeçalho adequadamente marcadas permitem saltar rapidamente entre secções da tabela e compreender o contexto de cada dado.

### Requisitos de Acessibilidade para Células de Dados e de Cabeçalho

#### Marcação Semântica Correta

**Regra Principal:** Use `<th>` para cabeçalhos e `<td>` para dados. Parece simples, mas é fundamental!

**Analogia:** É como usar os utensílios corretos numa refeição - pode até conseguir comer sopa com um garfo, mas não é eficiente nem apropriado.

#### Relações Claras entre Cabeçalhos e Dados

Cada célula de dados deve estar claramente associada aos seus cabeçalhos correspondentes. Em tabelas simples, isto acontece automaticamente quando usamos a estrutura correta.

#### Contraste e Legibilidade Visual

Os cabeçalhos devem destacar-se visualmente dos dados, mas mantendo contraste suficiente para serem legíveis por pessoas com baixa visão.

## Técnicas de Codificação

### Estrutura Básica com `<th>` e `<td>`

A base de uma tabela acessível começa com a marcação correta:

```html
<!-- Exemplo: Tabela de Horários -->
<table>
  <thead>
    <tr>
      <th>Hora</th>
      <th>Segunda</th>
      <th>Terça</th>
      <th>Quarta</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9:00</th>
      <td>Matemática</td>
      <td>História</td>
      <td>Ciências</td>
    </tr>
    <tr>
      <th>10:00</th>
      <td>Português</td>
      <td>Inglês</td>
      <td>Educação Física</td>
    </tr>
  </tbody>
</table>
```

**O que funciona bem:** Neste exemplo, temos cabeçalhos tanto na primeira linha (dias da semana) como na primeira coluna (horas). Cada célula de dados está automaticamente associada aos seus cabeçalhos correspondentes.

### Uso do Atributo `scope`

Para tabelas mais complexas, o atributo `scope` especifica exatamente a que se refere cada cabeçalho:

```html
<table>
  <thead>
    <tr>
      <th scope="col">Produto</th>
      <th scope="col">Janeiro</th>
      <th scope="col">Fevereiro</th>
      <th scope="col">Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Computadores</th>
      <td>25</td>
      <td>30</td>
      <td>55</td>
    </tr>
    <tr>
      <th scope="row">Impressoras</th>
      <td>12</td>
      <td>15</td>
      <td>27</td>
    </tr>
  </tbody>
</table>
```

**Valores do `scope`:**

- `col`: O cabeçalho aplica-se a toda a coluna
- `row`: O cabeçalho aplica-se a toda a linha
- `colgroup`: Para grupos de colunas
- `rowgroup`: Para grupos de linhas

### Associações Explícitas com `headers` e `id`

Para situações muito complexas, pode criar associações explícitas:

```html
<table>
  <thead>
    <tr>
      <th id="produto">Produto</th>
      <th id="q1">1º Trimestre</th>
      <th id="q2">2º Trimestre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="laptop" headers="produto">Laptops</th>
      <td headers="laptop q1">100</td>
      <td headers="laptop q2">150</td>
    </tr>
  </tbody>
</table>
```

**O que funciona bem:** Cada célula de dados está explicitamente ligada aos seus cabeçalhos através dos IDs, eliminando qualquer ambiguidade.

## Recomendações para Conteúdo Acessível

### Textos de Cabeçalho Claros e Concisos

**Bom exemplo:**
```html
<th>Preço (€)</th>
<th>Quantidade</th>
<th>Data de Entrega</th>
```

**Mau exemplo:**
```html
<th>€</th>
<th>Qtd.</th>
<th>Dt. Ent.</th>
```

**Porque é que o primeiro é melhor:** Os textos completos eliminam ambiguidade e são mais facilmente compreendidos por todos os utilizadores.

### Evitar Células Vazias nos Cabeçalhos

**Mau exemplo:**
```html
<tr>
  <th></th>  <!-- Célula vazia problemática -->
  <th>2023</th>
  <th>2024</th>
</tr>
```

**Boa solução:**
```html
<tr>
  <th scope="row">Ano</th>  <!-- Cabeçalho descritivo -->
  <th scope="col">2023</th>
  <th scope="col">2024</th>
</tr>
```

### Erros Comuns

#### Erro 1: Usar `<td>` para Cabeçalhos

```html
<!-- ERRADO -->
<tr>
  <td><strong>Nome</strong></td>
  <td><strong>Idade</strong></td>
</tr>
```

```html
<!-- CORRETO -->
<tr>
  <th>Nome</th>
  <th>Idade</th>
</tr>
```

**Porque está errado:** O leitor de ecrã não consegue identificar que estas células são cabeçalhos, perdendo-se informação estrutural importante.

#### Erro 2: Cabeçalhos Apenas Visuais

```html
<!-- ERRADO -->
<tr>
  <td class="header-style">Produto</td>
  <td class="header-style">Preço</td>
</tr>
```

**Porque está errado:** Mesmo que visualmente pareçam cabeçalhos, semanticamente não o são. As tecnologias de apoio não os reconhecem como tal.

#### Erro 3: Misturar Dados e Cabeçalhos na Mesma Célula

```html
<!-- ERRADO -->
<td>Janeiro: 1000€</td>
```

```html
<!-- CORRETO -->
<th>Janeiro</th>
<td>1000€</td>
```

**Porque está errado:** Dificulta a compreensão da estrutura e impossibilita a navegação eficiente por leitores de ecrã.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

**Lembre-se sempre:**

1. **Use `<th>` para cabeçalhos** - É a base de tudo
2. **Textos descritivos** - Cabeçalhos devem ser claros e completos
3. **Estrutura consistente** - Mantenha a mesma lógica em todo o site
4. **Teste sempre** - Verifique com leitores de ecrã e navegação por teclado

### Exercícios Práticos

#### Exercício 1: Identificar e Corrigir

Analise esta tabela e identifique os problemas:

```html
<table>
  <tr>
    <td><b>Item</b></td>
    <td><b>Preço</b></td>
    <td><b>Stock</b></td>
  </tr>
  <tr>
    <td>Caneta</td>
    <td>2€</td>
    <td>50</td>
  </tr>
</table>
```

**Questões:**

1. Que elementos precisam de ser alterados?
2. Como melhoraria a estrutura?
3. Que atributos adicionaria?

#### Exercício 2: Criar uma Tabela Acessível

Crie uma tabela para mostrar as notas de três alunos em quatro disciplinas. A tabela deve:

- Usar a marcação semântica correta
- Ter cabeçalhos descritivos
- Incluir atributos `scope` apropriados

#### Exercício 3: Teste de Acessibilidade

Usando um leitor de ecrã, navegue pela sua tabela e responda:

1. O leitor anuncia claramente os cabeçalhos?
2. Consegue perceber a estrutura da tabela?
3. A navegação é intuitiva?

