---
title: Imagens Informativas
layout: default
nav_order: 2
---
# Imagens Informativas

## Introdução

As imagens informativas são elementos visuais que transmitem informações importantes para compreender o conteúdo de uma página web. Ao contrário das imagens puramente decorativas, estas imagens contêm dados, factos ou conceitos essenciais que complementam ou substituem o texto.

**Analogia**: Imagine que está a ler um livro de culinária. As fotografias dos pratos finais são imagens informativas porque mostram como o resultado deve ficar. Se removesse essas imagens, perderia informação importante sobre a receita.

### Como as Pessoas com Deficiência usam Imagens Informativas

#### Utilizadores de Leitores de Ecrã

As pessoas cegas ou com baixa visão utilizam leitores de ecrã para navegar na web. Quando encontram uma imagem informativa, o leitor de ecrã lê em voz alta o texto alternativo (alt text) que descreve a imagem.

**Exemplo prático**: 
```html
<img src="grafico-vendas-2024.png" alt="Gráfico de barras mostrando aumento de 35% nas vendas entre janeiro e dezembro de 2024">
```

**O que funciona bem**: Este texto alternativo transmite a informação essencial da imagem - o tipo de gráfico, o que representa e a conclusão principal.

#### Utilizadores com Deficiências Cognitivas

Algumas pessoas têm dificuldades em processar informações visuais complexas. Para estas pessoas, uma descrição clara e estruturada da imagem pode facilitar a compreensão.

#### Utilizadores com Ligações Lentas à Internet

Quando as imagens não carregam devido a problemas de conectividade, o texto alternativo permite que todos os utilizadores acedam à informação.

### Requisitos de Acessibilidade para Imagens Informativas

#### Critério de Sucesso WCAG 1.1.1 - Conteúdo Não Textual

Todas as imagens informativas devem ter uma alternativa textual que:

- **Identifique o propósito da imagem**: O que a imagem está a mostrar?
- **Transmita a informação essencial**: Quais são os dados ou conceitos importantes?
- **Seja concisa mas completa**: Suficientemente detalhada sem ser excessiva

#### Princípios Fundamentais

**Equivalência**: O texto alternativo deve fornecer uma experiência equivalente para utilizadores que não conseguem ver a imagem.

**Analogia**: É como ter um amigo a descrever-lhe uma fotografia ao telefone. A descrição deve ser suficientemente clara para que compreenda o que está na imagem.

## Técnicas de Codificação

### Atributo ALT Básico

A técnica mais fundamental é usar o atributo `alt` na etiqueta `<img>`:

```html
<img src="temperatura-lisboa.png" alt="Termómetro mostrando 28 graus Celsius">
```

**O que funciona bem**: 
- Descreve o que a imagem mostra (termómetro)
- Inclui a informação específica (28 graus)
- É conciso e direto

### Descrições Mais Detalhadas com ARIA

Para imagens que precisam de descrições mais longas, podemos usar `aria-describedby`:

```html
<img src="organigrama-empresa.png" 
     alt="Organigrama da empresa" 
     aria-describedby="desc-organigrama">

<div id="desc-organigrama">
  O organigrama mostra a estrutura hierárquica da empresa com o CEO no topo, 
  seguido por três diretores (Financeiro, Marketing e Operações), cada um 
  com as suas respetivas equipas.
</div>
```

**O que funciona bem**:
- O `alt` fornece uma descrição breve
- O `aria-describedby` liga a uma descrição detalhada
- A informação está disponível para todos os utilizadores

### Imagens com Texto

Quando uma imagem contém texto importante, esse texto deve ser incluído no alt:

```html
<img src="cartaz-evento.png" 
     alt="Conferência de Tecnologia 2024 - 15 de Março, Auditório Principal, inscrições em www.exemplo.pt">
```

**O que funciona bem**: Inclui todo o texto visível na imagem, mantendo a ordem lógica de leitura.

### Técnica Incorreta

```html
<img src="dados-importantes.png" alt="Imagem">
```

**O que funciona mal**:
- "Imagem" não transmite qualquer informação útil
- Utilizadores de leitores de ecrã perdem informação importante
- Não cumpre os requisitos de acessibilidade

## Recomendações para Conteúdo Acessível

### Escrever Textos Alternativos Eficazes

#### 1. Seja Específico e Descritivo

**Bom exemplo**:
```html
<img src="pizza-margherita.jpg" 
     alt="Pizza Margherita com molho de tomate, mozzarella e manjericão fresco sobre base fina">
```

**Mau exemplo**:
```html
<img src="pizza-margherita.jpg" alt="Pizza">
```

#### 2. Inclua Informações Relevantes para o Contexto

Se a imagem está num artigo sobre nutrição:
```html
<img src="salada-verde.jpg" 
     alt="Salada verde com espinafres, rúcula e pepino - apenas 45 calorias por porção">
```

Se a mesma imagem está numa receita:
```html
<img src="salada-verde.jpg" 
     alt="Salada verde com espinafres, rúcula e fatias finas de pepino">
```

#### 3. Evite Redundância

**Mau exemplo**:
```html
<p>O gráfico seguinte mostra os resultados:</p>
<img src="grafico.png" alt="Gráfico que mostra os resultados">
```

**Bom exemplo**:
```html
<p>O gráfico seguinte mostra os resultados:</p>
<img src="grafico.png" alt="Aumento de 45% nas vendas online e diminuição de 20% nas vendas em loja física">
```

### Considerar o Comprimento

#### Para o atributo alt:

- Deve ser conciso mas informativo
- Se conseguir transmitir a informação essencial numa frase curta, use apenas alt

#### Para aria-describedby:

- Use quando precisar de múltiplas frases ou parágrafos
- Quando a informação é demasiado complexa para uma descrição breve

### Fornecer Contexto Cultural

Quando relevante, inclua informações que ajudem a compreender o contexto:

```html
<img src="festa-junina.jpg" 
     alt="Pessoas vestidas com roupas tradicionais portuguesas a dançar o vira numa festa de São João">
```

## Erros Comuns

### 1. Texto Alternativo Genérico

**Erro**:
```html
<img src="produto123.jpg" alt="Produto">
<img src="pessoa.jpg" alt="Pessoa">
<img src="lugar.jpg" alt="Lugar">
```

**Solução**:
```html
<img src="produto123.jpg" alt="Smartphone Samsung Galaxy com ecrã de 6.1 polegadas">
<img src="pessoa.jpg" alt="Maria Silva, Diretora de Marketing">
<img src="lugar.jpg" alt="Biblioteca Nacional, sala de leitura principal">
```

### 2. Descrever a Imagem em Vez da Informação

**Erro**:
```html
<img src="barras-azuis.png" alt="Gráfico com barras azuis de diferentes tamanhos">
```

**Solução**:
```html
<img src="barras-azuis.png" alt="Vendas trimestrais: Q1: 50 mil euros, Q2: 75 mil euros, Q3: 90 mil euros, Q4: 85 mil euros">
```

### 3. Texto Alternativo Demasiado Técnico

**Erro**:
```html
<img src="molecula.png" alt="Estrutura molecular C8H10N4O2 com ligações covalentes entre átomos de carbono, hidrogénio, nitrogénio e oxigénio">
```

**Solução** (para audiência geral):
```html
<img src="molecula.png" alt="Estrutura molecular da cafeína, composto presente no café">
```

### 4. Repetir Informação já Presente no Texto

**Erro**:
```html
<p>O nosso novo produto, o Smartphone X, tem uma bateria de 4000mAh.</p>
<img src="smartphone-x.jpg" alt="Smartphone X com bateria de 4000mAh">
```

**Solução**:
```html
<p>O nosso novo produto, o Smartphone X, tem uma bateria de 4000mAh.</p>
<img src="smartphone-x.jpg" alt="Vista frontal do Smartphone X mostrando o ecrã de 6.2 polegadas">
```

### 5. Usar "Imagem de..." ou "Fotografia de..."

**Desnecessário**:
```html
<img src="cao.jpg" alt="Fotografia de um cão golden retriever">
```

**Melhor**:
```html
<img src="cao.jpg" alt="Cão golden retriever sentado num jardim">
```

**Explicação**: Os utilizadores de leitores de ecrã já sabem que se trata de uma imagem. É mais útil ir diretamente à descrição do conteúdo.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

**Lembrete importante**: As imagens informativas são como tradutores visuais - devem transmitir a mesma mensagem tanto para quem vê como para quem ouve.

Os pontos essenciais a reter são:

- **Todas as imagens informativas precisam de texto alternativo** que transmita a informação essencial
- **O contexto determina o conteúdo** - a mesma imagem pode precisar de descrições diferentes conforme o uso
- **Seja específico e relevante** - evite descrições genéricas ou demasiado técnicas
- **Considere o utilizador final** - escreva para quem vai ouvir a descrição
- **Teste sempre** - use um leitor de ecrã ou peça a alguém para ler apenas o texto alternativo

### Exercícios Práticos

#### Exercício 1: Identificar Problemas

Analise os seguintes exemplos e identifique os problemas:

```html
<!-- Exemplo A -->
<img src="vendas-2024.png" alt="Gráfico">

<!-- Exemplo B -->
<p>Este gráfico mostra a evolução das vendas.</p>
<img src="evolucao-vendas.png" alt="Gráfico que mostra a evolução das vendas">

<!-- Exemplo C -->
<img src="receita-bolo.jpg" alt="Imagem de um bolo de chocolate">
```

**Soluções sugeridas**:

- **Exemplo A**: "Gráfico" é demasiado genérico. Deve incluir informação sobre o que o gráfico mostra.
- **Exemplo B**: Há redundância entre o texto e o alt. O alt deve complementar, não repetir.
- **Exemplo C**: Se é numa página de receitas, deve incluir informações relevantes como aspeto final esperado.

#### Exercício 2: Escrever Texto Alternativo

Para cada cenário, escreva um texto alternativo apropriado:

**Cenário 1**: Uma captura de ecrã de uma aplicação móvel mostrando o tempo em Lisboa (22°C, céu limpo, vento 5km/h) numa página sobre turismo.

**Cenário 2**: Um gráfico circular numa apresentação empresarial mostrando: Marketing 40%, Vendas 30%, Desenvolvimento 20%, Suporte 10%.

**Cenário 3**: Uma fotografia de um prato de bacalhau à Brás num site de restaurante.

#### Exercício 3: Prática com Código

Crie o HTML completo para uma página que inclua:

1. Uma imagem informativa simples
2. Uma imagem que necessite de descrição longa
3. Uma imagem com texto importante

Use as técnicas aprendidas para garantir acessibilidade total.

#### Exercício 4: Teste de Acessibilidade

Usando um leitor de ecrã ou pedindo a um colega para ler apenas os textos alternativos:

1. Teste as imagens de um site que conheça
2. Identifique problemas de acessibilidade
3. Proponha melhorias

**Reflexão**: Consegue compreender toda a informação importante apenas através do texto alternativo? Se não, o que está em falta?



