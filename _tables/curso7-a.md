---
title: Introdução
layout: default
nav_order: 1
---
# Tabelas

## Introdução

As tabelas são uma ferramenta poderosa para organizar e apresentar informação de forma estruturada. Imagine uma tabela como uma estante de biblioteca: cada prateleira (linha) tem livros (células) organizados por categorias (colunas). Para que esta "estante" seja útil para todos, incluindo pessoas com deficiência, precisa de estar bem organizada e ter etiquetas claras.

Neste módulo, vamos aprender como criar tabelas que sejam verdadeiramente acessíveis para todos os utilizadores.

### Como as Pessoas com Deficiência usam Tabelas

#### Utilizadores de Leitores de Ecrã

Os leitores de ecrã são como um "guia turístico" que descreve o conteúdo da página em voz alta. Quando encontram uma tabela, estes utilizadores dependem de:

- **Navegação célula a célula**: Movem-se pela tabela como se fosse um tabuleiro de xadrez, uma casa de cada vez
- **Identificação de cabeçalhos**: Precisam de saber qual é o "título" de cada coluna e linha para compreender os dados
- **Contexto dos dados**: Quando ouvem "25", precisam de saber se se refere a idade, preço ou temperatura

**Exemplo de experiência típica:**
Quando um utilizador navega numa tabela de vendas, o leitor de ecrã pode anunciar: "Tabela com 4 colunas e 6 linhas. Produto: Computador, Vendas Janeiro: 25, Vendas Fevereiro: 30..."

#### Utilizadores com Deficiências Cognitivas

Estas pessoas beneficiam de:

- **Estrutura clara e previsível**: Como ter sempre os mesmos tipos de informação nas mesmas posições
- **Informação não redundante**: Evitar repetições desnecessárias que possam causar confusão
- **Títulos descritivos**: Que expliquem claramente o propósito da tabela

#### Utilizadores com Deficiências Motoras

Podem usar navegação por teclado e precisam de:

- **Navegação eficiente**: Conseguir mover-se rapidamente entre as células importantes
- **Alvos clicáveis adequados**: Se houver elementos interativos, devem ser fáceis de ativar

### Requisitos de Acessibilidade para Tabelas

#### Estrutura Semântica Correta

As tabelas devem usar elementos HTML apropriados:

- `<table>` para o contentor principal
- `<thead>`, `<tbody>`, `<tfoot>` para organizar secções
- `<tr>` para linhas
- `<th>` para cabeçalhos
- `<td>` para dados

#### Identificação Clara de Cabeçalhos

Todos os cabeçalhos devem estar marcados com `<th>` e ter o atributo `scope` apropriado:

- `scope="col"` para cabeçalhos de coluna
- `scope="row"` para cabeçalhos de linha

#### Informação Contextual

As tabelas devem ter:

- **Título descritivo** (elemento `<caption>`)
- **Resumo quando necessário** (descrição externa)

## Técnicas de Codificação

### Estrutura Básica de uma Tabela Acessível

```html
<table>
    <caption>Vendas Trimestrais por Região - 2024</caption>
    <thead>
        <tr>
            <th scope="col">Região</th>
            <th scope="col">1º Trimestre</th>
            <th scope="col">2º Trimestre</th>
            <th scope="col">3º Trimestre</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Norte</th>
            <td>€150.000</td>
            <td>€175.000</td>
            <td>€200.000</td>
        </tr>
        <tr>
            <th scope="row">Sul</th>
            <td>€120.000</td>
            <td>€140.000</td>
            <td>€160.000</td>
        </tr>
    </tbody>
</table>
```

**O que funciona bem neste exemplo:**

- O `<caption>` explica claramente o conteúdo da tabela
- O `<thead>` separa os cabeçalhos dos dados
- Cada cabeçalho tem `scope` definido corretamente
- A estrutura é lógica e previsível

### Uso Correto do Elemento `<caption>`

O `<caption>` é como o título de um livro - deve ser conciso mas informativo:

```html
<!-- ✅ BOM: Específico e útil -->
<caption>Resultados de Vendas por Trimestre - Equipas Norte e Sul</caption>

<!-- ❌ MAU: Muito vago -->
<caption>Tabela</caption>

<!-- ❌ MAU: Demasiado longo -->
<caption>Esta tabela mostra os resultados de vendas detalhados de todas as equipas durante todos os trimestres do ano de 2024, incluindo comparações percentuais...</caption>
```

### Implementação de `scope` em Cabeçalhos

O atributo `scope` é como uma bússola que indica a direção da informação:

```html
<!-- Para cabeçalhos de coluna -->
<th scope="col">Mês</th>
<th scope="col">Vendas</th>

<!-- Para cabeçalhos de linha -->
<th scope="row">Janeiro</th>
<th scope="row">Fevereiro</th>
```

### Agrupamento Lógico com `<thead>`, `<tbody>`, `<tfoot>`

```html
<table>
    <caption>Relatório Financeiro Anual</caption>
    
    <thead>
        <tr>
            <th scope="col">Categoria</th>
            <th scope="col">Valor</th>
        </tr>
    </thead>
    
    <tbody>
        <tr>
            <th scope="row">Receitas</th>
            <td>€500.000</td>
        </tr>
        <tr>
            <th scope="row">Despesas</th>
            <td>€300.000</td>
        </tr>
    </tbody>
    
    <tfoot>
        <tr>
            <th scope="row">Lucro Total</th>
            <td>€200.000</td>
        </tr>
    </tfoot>
</table>
```

**O que funciona bem:**

- Separação clara entre cabeçalho, dados e totais
- Facilita a navegação para utilizadores de leitores de ecrã
- Permite aplicar estilos CSS específicos a cada secção

## Recomendações para Conteúdo Acessível

### Escrita de Cabeçalhos Eficazes

Os cabeçalhos devem ser como placas de trânsito - claros, concisos e informativos:

```html
<!-- ✅ BOM: Específico e claro -->
<th scope="col">Preço (€)</th>
<th scope="col">Data de Entrega</th>
<th scope="col">Estado da Encomenda</th>

<!-- ❌ MAU: Vago ou ambíguo -->
<th scope="col">Valor</th>
<th scope="col">Data</th>
<th scope="col">Estado</th>
```

### Formatação de Dados Numéricos

Use formatação consistente para facilitar a compreensão:

```html
<!-- ✅ BOM: Formatação consistente -->
<td>€1.250,00</td>
<td>€15.750,00</td>
<td>€125.000,00</td>

<!-- ❌ MAU: Formatação inconsistente -->
<td>1250 euros</td>
<td>€15750</td>
<td>125.000,00 EUR</td>
```

### Uso de Abreviações e Unidades

Sempre que usar abreviações, forneça a forma completa:

```html
<!-- ✅ BOM: Com explicação -->
<th scope="col"><abbr title="Quilogramas">Kg</abbr></th>
<th scope="col">Temperatura (°C)</th>

<!-- ❌ MAU: Sem contexto -->
<th scope="col">Kg</th>
<th scope="col">Temp</th>
```

### Evitar Células Vazias

Se uma célula estiver vazia, explique porquê:

```html
<!-- ✅ BOM: Explicação clara -->
<td>Não disponível</td>
<td>Em análise</td>
<td>0</td>

<!-- ❌ MAU: Células vazias -->
<td></td>
<td></td>
<td></td>
```

### Erros Comuns

#### 1. Usar Tabelas para Layout Visual

**Problema**: Usar `<table>` apenas para alinhar elementos na página.

```html
<!-- ❌ MAU: Tabela para layout -->
<table>
    <tr>
        <td>
            <img src="logo.png" alt="Logo">
        </td>
        <td>
            <h1>Título da Página</h1>
        </td>
    </tr>
</table>
```

**Solução**: Use CSS Flexbox ou Grid para layout.

#### 2. Omitir o Elemento `<caption>`

**Problema**: Tabelas sem título ou contexto.

```html
<!-- ❌ MAU: Sem contexto -->
<table>
    <tr>
        <th>Nome</th>
        <th>Idade</th>
    </tr>
</table>

<!-- ✅ BOM: Com contexto -->
<table>
    <caption>Lista de Participantes do Curso</caption>
    <tr>
        <th scope="col">Nome</th>
        <th scope="col">Idade</th>
    </tr>
</table>
```

#### 3. Confundir `<td>` e `<th>`

**Problema**: Usar `<td>` para cabeçalhos ou vice-versa.

```html
<!-- ❌ MAU: Cabeçalho como dado -->
<tr>
    <td><strong>Produto</strong></td>
    <td><strong>Preço</strong></td>
</tr>

<!-- ✅ BOM: Cabeçalho correto -->
<tr>
    <th scope="col">Produto</th>
    <th scope="col">Preço</th>
</tr>
```

#### 4. Esquecer o Atributo `scope`

**Problema**: Cabeçalhos sem indicação de direção.

```html
<!-- ❌ MAU: Sem scope -->
<th>Mês</th>
<th>Vendas</th>

<!-- ✅ BOM: Com scope -->
<th scope="col">Mês</th>
<th scope="col">Vendas</th>
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

1. **Estrutura Semântica**: Use sempre os elementos HTML corretos (`<table>`, `<th>`, `<td>`, etc.)

2. **Contexto Claro**: Forneça títulos descritivos com `<caption>` e cabeçalhos informativos

3. **Navegação Eficiente**: Use `scope` para indicar a direção dos cabeçalhos

4. **Organização Lógica**: Agrupe conteúdo com `<thead>`, `<tbody>`, `<tfoot>`

5. **Conteúdo Compreensível**: Formate dados consistentemente e evite células vazias sem explicação

### Exercícios Práticos

#### Exercício 1: Identificar Problemas

Analise a seguinte tabela e identifique pelo menos 3 problemas de acessibilidade:

```html
<table>
    <tr>
        <td>Produto</td>
        <td>Jan</td>
        <td>Fev</td>
        <td>Mar</td>
    </tr>
    <tr>
        <td>Computadores</td>
        <td style="color: green;">50</td>
        <td style="color: red;">30</td>
        <td></td>
    </tr>
</table>
```

**Problemas identificados:**

1. Falta de `<caption>` para contextualizar a tabela
2. Cabeçalhos marcados como `<td>` em vez de `<th>`
3. Ausência do atributo `scope` nos cabeçalhos
4. Informação transmitida apenas por cor (verde/vermelho)
5. Célula vazia sem explicação
6. Abreviações sem expansão (Jan, Fev, Mar)

#### Exercício 2: Criar Tabela Acessível

Crie uma tabela acessível com as seguintes informações:

- Título: "Horário de Funcionamento da Biblioteca"
- Colunas: Dia da Semana, Horário de Abertura, Horário de Encerramento
- Dados:
  - Segunda a Sexta: 09:00 - 22:00
  - Sábado: 10:00 - 18:00
  - Domingo: Encerrado

**Solução:**

```html
<table>
    <caption>Horário de Funcionamento da Biblioteca</caption>
    <thead>
        <tr>
            <th scope="col">Dia da Semana</th>
            <th scope="col">Horário de Abertura</th>
            <th scope="col">Horário de Encerramento</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Segunda a Sexta</th>
            <td>09:00</td>
            <td>22:00</td>
        </tr>
        <tr>
            <th scope="row">Sábado</th>
            <td>10:00</td>
            <td>18:00</td>
        </tr>
        <tr>
            <th scope="row">Domingo</th>
            <td colspan="2">Encerrado</td>
        </tr>
    </tbody>
</table>
```

#### Exercício 3: Melhorar Tabela Existente

Transforme esta tabela problemática numa versão acessível:

```html
<table>
    <tr>
        <td><b>Nome</b></td>
        <td><b>Nota</b></td>
        <td><b>Estado</b></td>
    </tr>
    <tr>
        <td>Ana Silva</td>
        <td style="color: blue;">18</td>
        <td style="color: green;">Aprovado</td>
    </tr>
    <tr>
        <td>João Santos</td>
        <td style="color: red;">8</td>
        <td style="color: red;">Reprovado</td>
    </tr>
</table>
```

**Versão melhorada:**

```html
<table>
    <caption>Resultados dos Exames Finais - Turma A</caption>
    <thead>
        <tr>
            <th scope="col">Nome do Aluno</th>
            <th scope="col">Nota (0-20)</th>
            <th scope="col">Estado</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Ana Silva</th>
            <td>18 (Muito Bom)</td>
            <td>Aprovado</td>
        </tr>
        <tr>
            <th scope="row">João Santos</th>
            <td>8 (Insuficiente)</td>
            <td>Reprovado</td>
        </tr>
    </tbody>
</table>
```

**Melhorias aplicadas:**

- Adicionado `<caption>` descritivo
- Convertidos cabeçalhos para `<th>` com `scope="col"`
- Adicionado `scope="row"` para nomes dos alunos
- Removida dependência de cor, adicionando texto descritivo
- Estruturada com `<thead>` e `<tbody>`
- Melhorados os títulos das colunas com mais contexto

