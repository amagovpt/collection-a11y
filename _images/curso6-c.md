---
title: Imagens Decorativas
layout: default
nav_order: 3
---

# Imagens Decorativas

## Introdução

As imagens decorativas são como os quadros numa sala de estar - estão lá para tornar o espaço mais bonito, mas não transmitem informação essencial. São elementos visuais que servem apenas para embelezar a página web, criar ambiente ou separar secções de conteúdo.

### Como as Pessoas com Deficiência Interagem com Imagens Decorativas

Quando uma pessoa cega utiliza um leitor de ecrã, este programa lê todo o conteúdo da página em voz alta. Imagine que está a ouvir alguém a ler-lhe um livro, mas que essa pessoa pára constantemente para descrever cada pequeno desenho decorativo da margem. Seria muito cansativo e distrativo!

**Exemplo de experiência problemática:**
```
"Imagem: flor decorativa"
"Imagem: linha ondulada azul" 
"Imagem: estrelinhas brilhantes"
"Finalmente chegamos ao texto importante..."
```

Por isso, as imagens puramente decorativas devem ser "invisíveis" para os leitores de ecrã, permitindo que os utilizadores se concentrem no conteúdo importante.

**Pessoas que beneficiam desta abordagem:**

- Utilizadores de leitores de ecrã (pessoas cegas ou com baixa visão)
- Pessoas com deficiências cognitivas que se distraem facilmente
- Utilizadores em ligações lentas (quando as imagens não carregam)

### Requisitos de Acessibilidade para Imagens Decorativas

O princípio fundamental é simples: **se a imagem não acrescenta informação importante, deve ser ignorada pelos leitores de ecrã**.

**Critérios para identificar imagens decorativas:**

- Servem apenas para embelezar
- Se fossem removidas, o significado da página mantinha-se igual
- São padrões, texturas ou elementos gráficos puramente estéticos
- Repetem informação já presente no texto

**Técnicas principais:**

1. **Atributo alt vazio:** `alt=""`
2. **Role presentation:** `role="presentation"`
3. **Imagens de fundo CSS** (naturalmente ignoradas pelos leitores de ecrã)

## Técnicas de Codificação

### Técnica 1: Atributo Alt Vazio

A forma mais comum de marcar uma imagem como decorativa é usar `alt=""` (aspas vazias, não espaços).

**Exemplo correto:**
```html
<h2>Os Nossos Serviços</h2>
<img src="linha-decorativa.png" alt="">
<p>Oferecemos consultoria em acessibilidade web...</p>
```

**Exemplo incorreto:**
```html
<h2>Os Nossos Serviços</h2>
<img src="linha-decorativa.png" alt="linha decorativa azul">
<p>Oferecemos consultoria em acessibilidade web...</p>
```

**Por que funciona:** O alt vazio indica ao leitor de ecrã que deve ignorar completamente a imagem, permitindo uma experiência fluida.

### Técnica 2: Role Presentation

O atributo `role="presentation"` também pode ser usado para imagens decorativas.

**Exemplo correto:**
```html
<div class="artigo">
    <img src="pattern-background.jpg" role="presentation">
    <h3>Título do Artigo</h3>
    <p>Conteúdo do artigo...</p>
</div>
```

**Por que funciona:** O role="presentation" remove a semântica da imagem, tornando-a invisível para tecnologias de apoio.

### Técnica 3: Imagens de Fundo CSS

Para elementos puramente decorativos, as imagens de fundo são uma excelente escolha.

**Exemplo correto:**
```css
.secao-hero {
    background-image: url('pattern-decorativo.png');
    background-repeat: repeat;
}
```

```html
<section class="secao-hero">
    <h1>Bem-vindos ao nosso site</h1>
    <p>Descubra os nossos serviços...</p>
</section>
```

**Por que funciona:** As imagens de fundo CSS são automaticamente ignoradas pelos leitores de ecrã, focando apenas no conteúdo HTML.

### Analogia da Moldura

Pense numa moldura de quadro: a moldura embeleza a obra, mas o importante é a pintura. Se alguém vos descrevesse um quadro, não perderia tempo a descrever cada detalhe da moldura - focaria na obra em si.

## Recomendações para Conteúdo Acessível

### Escolher a Técnica Certa

**Use alt="" quando:**

- A imagem está no HTML por razões técnicas
- É um ícone puramente decorativo
- É um separador visual

**Use imagens de fundo CSS quando:**

- A imagem é puramente estética
- Faz parte do design visual
- Pode ser repetida ou redimensionada

### Teste Simples: A Regra da Remoção

Faça esta pergunta: "Se eu remover esta imagem, alguém perde informação importante?"

**Se a resposta for NÃO = imagem decorativa**

- Use alt="" ou role="presentation"

**Se a resposta for SIM = imagem informativa**

- Precisa de texto alternativo descritivo

### Exemplos Práticos de Identificação

**Claramente decorativas:**
```html
<!-- Separador visual entre secções -->
<img src="linha-ondulada.png" alt="">

<!-- Padrão de fundo -->
<img src="texturas-papel.jpg" role="presentation">

<!-- Ícones decorativos repetitivos -->
<img src="estrela-pequena.png" alt="">
```

**Casos duvidosos que precisam de análise:**
```html
<!-- Este ícone apenas decora ou indica algo importante? -->
<img src="icone-atencao.png" alt="">
<p>Atenção: O prazo termina amanhã</p>
```

Neste caso, se o ícone reforça a mensagem de atenção, pode não ser puramente decorativo.

### Erros Comuns

#### Erro 1: Confundir Decorativa com Informativa

**Problema:**
```html
<img src="seta-vermelha.png" alt="">
<p>Clique aqui para continuar</p>
```

**Solução:**
Se a seta indica direção ou ação, não é decorativa:
```html
<img src="seta-vermelha.png" alt="Seta apontando para a direita">
<p>Clique aqui para continuar</p>
```

#### Erro 2: Usar Espaços no Alt

**Incorreto:**
```html
<img src="decoracao.png" alt=" ">
```

**Correto:**
```html
<img src="decoracao.png" alt="">
```

**Por que está errado:** O espaço faz com que o leitor de ecrã anuncie "imagem" sem contexto, confundindo os utilizadores.

#### Erro 3: Descrever Elementos Decorativos

**Problema:**
```html
<img src="border-floral.png" alt="Borda decorativa com flores azuis e folhas verdes">
```

**Solução:**
```html
<img src="border-floral.png" alt="">
```

**Por que está errado:** A descrição detalhada de elementos decorativos interrompe o fluxo de leitura sem acrescentar valor.

#### Erro 4: Ignorar o Contexto

**Problema:**
Marcar como decorativa uma imagem que, no contexto, transmite informação:
```html
<h3>Produtos em Promoção</h3>
<img src="tag-desconto.png" alt="">
<p>Descontos até 50%</p>
```

**Solução:**
```html
<h3>Produtos em Promoção</h3>
<img src="tag-desconto.png" alt="Etiqueta de desconto">
<p>Descontos até 50%</p>
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

**Princípios fundamentais:**

- Imagens decorativas devem ser invisíveis para leitores de ecrã
- Use `alt=""` ou `role="presentation"` em HTML
- Prefira imagens de fundo CSS para elementos puramente estéticos
- Aplique a "regra da remoção" para decidir se uma imagem é decorativa

**Benefícios de implementar corretamente:**

- Experiência mais fluida para utilizadores de leitores de ecrã
- Foco no conteúdo importante
- Melhor desempenho (imagens de fundo podem ser otimizadas)
- Separação clara entre conteúdo e design

### Exercícios Práticos

#### Exercício 1: Identificação

Analise as seguintes imagens e classifique como decorativa ou informativa:

1. Logo da empresa no cabeçalho
2. Padrão de bolinhas como fundo de uma secção
3. Ícone de "check" ao lado de "Tarefa concluída"
4. Fotografia de flores numa página sobre jardinagem
5. Linha divisória entre artigos de um blog

**Respostas esperadas:**

1. Informativa (identifica a empresa)
2. Decorativa (apenas estética)
3. Informativa (reforça o estado da tarefa)
4. Depende do contexto (pode ser decorativa ou informativa)
5. Decorativa (apenas separação visual)

#### Exercício 2: Correção de Código

Corrija os seguintes trechos de código:

```html
<!-- Exercício A -->
<img src="pattern-dots.png" alt="Padrão de pontos coloridos">

<!-- Exercício B -->
<img src="divider-line.gif" alt=" ">

<!-- Exercício C -->
<section style="background: url('texture.jpg');">
    <img src="texture.jpg" alt="">
    <h2>Sobre Nós</h2>
</section>
```

**Soluções:**

**A:** `<img src="pattern-dots.png" alt="">` (remover descrição desnecessária)

**B:** `<img src="divider-line.gif" alt="">` (remover espaço)

**C:** Remover a tag img duplicada:
```html
<section style="background: url('texture.jpg');">
    <h2>Sobre Nós</h2>
</section>
```

#### Exercício 3: Implementação Prática

Crie o HTML para uma página de blog que inclua:

- Um cabeçalho com padrão de fundo decorativo
- Um artigo com título e texto
- Separadores visuais entre secções
- Um ícone decorativo no final

Garanta que todos os elementos decorativos são tratados corretamente para acessibilidade.

