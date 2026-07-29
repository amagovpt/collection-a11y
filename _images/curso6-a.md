---
title: Introdução
layout: default
nav_order: 1
---
# Imagens

## Introdução

### Como as Pessoas com Deficiência usam Imagens

As imagens são como janelas que nos mostram informação visual, mas nem todas as pessoas conseguem "ver" através dessas janelas da mesma forma. Vamos compreender a experiência de diferentes pessoas com as imagens na web:

**Pessoas cegas ou com baixa visão:**
- Usam **leitores de ecrã** (software que "lê" o conteúdo em voz alta)
- Dependem de **descrições de texto** para compreender o que está nas imagens
- É como se alguém lhes descrevesse uma fotografia ao telefone

**Pessoas com deficiências cognitivas:**
- Podem ter dificuldade em processar imagens complexas
- Beneficiam de **descrições simples e claras**
- Imagens podem ajudar a compreender o texto (quando bem usadas)

**Pessoas com ligações lentas à internet:**
- Podem desativar o carregamento de imagens
- Precisam de **texto alternativo** para saber o que perderam

### Requisitos de Acessibilidade para Imagens

Pensem nas imagens como livros numa biblioteca. Se um livro não tiver título ou descrição, como sabemos do que trata? O mesmo acontece com as imagens na web.

**Requisitos fundamentais:**

1. **Texto alternativo (alt text)** - Como um "resumo" da imagem
2. **Descrições longas** - Para imagens complexas
3. **Contexto apropriado** - A imagem deve fazer sentido no local onde está
4. **Qualidade visual** - Contraste suficiente e resolução adequada

## Técnicas de Codificação

### O Atributo `alt` - O Herói das Imagens Acessíveis

O atributo `alt` é como uma "legenda invisível" que os leitores de ecrã conseguem ler.

**Exemplo correto:**
```html
<img src="cao-guia.jpg" alt="Cão-guia golden retriever a atravessar uma passadeira com o seu dono">
```

**O que funciona bem:** A descrição é específica, menciona a raça do cão, o que está a fazer e o contexto. Uma pessoa cega consegue formar uma imagem mental clara.

**Exemplo incorreto:**
```html
<img src="cao-guia.jpg" alt="imagem">
```

**O que está mal:** "Imagem" não diz nada útil. É como dizer "há aqui uma coisa" sem explicar o quê.

### Imagens sem Texto Alternativo

Às vezes, as imagens são apenas decorativas (como um padrão de fundo). Nestes casos, usamos um `alt` vazio:

**Exemplo correto:**
```html
<img src="padrao-decorativo.jpg" alt="">
```

**O que funciona bem:** O `alt=""` vazio diz ao leitor de ecrã para ignorar esta imagem, evitando "ruído" desnecessário.

### Texto Alternativo Longo

Para imagens complexas (como gráficos), podemos criar descrições detalhadas, que inclusivamente podem ser disponibilizadas para todos os utilizadores:

**Exemplo:**
```html
<img src="grafico-vendas.png" 
     alt="Gráfico de vendas trimestrais de 2023">
<p>Descrição detalhada: As vendas aumentaram 15% no primeiro trimestre, 
mantiveram-se estáveis no segundo, diminuíram 8% no terceiro e 
recuperaram 20% no quarto trimestre.</p>
```

## Recomendações para Conteúdo Acessível

### Como Escrever Bom Texto Alternativo

Imaginem que estão a descrever uma imagem a alguém ao telefone. O que diriam?

**Regras de ouro:**

1. **Sejam concisos mas informativos** 
2. **Descrevam o essencial, não todos os detalhes**
3. **Incluam o contexto relevante**
4. **Incluam texto relevante que esteja presente na imagem**
4. **Não comecem com "Imagem de..." ou "Fotografia de..."**

**Exemplos práticos:**

**Situação:** Logótipo de uma empresa
```html
<!-- Correto -->
<img src="logo-empresa.png" alt="Empresa XYZ">

<!-- Incorreto -->
<img src="logo-empresa.png" alt="Logótipo colorido da Empresa XYZ com letras azuis e símbolo de uma casa">
```

**O que funciona:** O primeiro exemplo vai direto ao essencial. O segundo tem demasiados detalhes irrelevantes.

**Situação:** Botão com ícone
```html
<!-- Correto -->
<button>
  <img src="icone-pesquisar.png" alt="Pesquisar">
</button>

<!-- Ainda melhor -->
<button>
  <img src="icone-pesquisar.png" alt="">
  Pesquisar
</button>
```

### Contexto é Fundamental

A mesma imagem de um gato pode precisar de descrições diferentes conforme o contexto:

**Num site de veterinário:**
```html
<img src="gato.jpg" alt="Gato persa com sinais de conjuntivite">
```

**Numa loja de animais:**
```html
<img src="gato.jpg" alt="Gato persa disponível para adoção">
```

**Num blog pessoal:**
```html
<img src="gato.jpg" alt="O meu gato Mimi a dormir">
```

### Erros Comuns

#### Erro 1: Texto Alternativo Redundante

**Incorreto:**
```html
<h2>Os nossos serviços</h2>
<img src="servicos.jpg" alt="Os nossos serviços">
<p>Oferecemos os seguintes serviços...</p>
```

**Correto:**
```html
<h2>Os nossos serviços</h2>
<img src="servicos.jpg" alt="Equipa a trabalhar em diferentes projetos tecnológicos">
<p>Oferecemos os seguintes serviços...</p>
```

**Por que está melhor:** Evita repetição e descreve a imagem.

#### Erro 2: Descrições Demasiado Técnicas

**Incorreto:**
```html
<img src="produto.jpg" alt="Smartphone com ecrã OLED de 6.1 polegadas, processador A15 Bionic, câmara de 12MP com estabilização ótica">
```

**Correto:**
```html
<img src="produto.jpg" alt="iPhone 13 em cor azul">
```

#### Erro 3: Alt Text em Imagens Decorativas

**Incorreto:**
```html
<img src="linha-decorativa.png" alt="Linha decorativa azul">
```

**Correto:**
```html
<img src="linha-decorativa.png" alt="">
```

#### Erro 4: Usar o Nome do Ficheiro

**Incorreto:**
```html
<img src="IMG_20230315_142536.jpg" alt="IMG_20230315_142536">
```

**Correto:**
```html
<img src="IMG_20230315_142536.jpg" alt="Vista panorâmica da cidade do Porto">
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

**Lembrem-se sempre:**

1. **Toda a imagem informativa precisa de texto alternativo descritivo**
2. **Imagens decorativas devem ter `alt=""` (vazio)**
3. **O contexto determina como descrever a imagem**
4. **Sejam concisos mas informativos**
5. **Testem sempre com leitores de ecrã ou peçam feedback**

### Exercícios Práticos

#### Exercício 1: Identificar o Tipo de Imagem

Para cada imagem, decidam que tipo de texto alternativo seria apropriado:

1. Logótipo da vossa empresa no cabeçalho da página
2. Foto de uma paisagem num artigo sobre turismo
3. Ícone de uma seta numa página de navegação
4. Padrão de fundo decorativo
5. Fotografia do CEO numa página "Sobre Nós"

**Respostas esperadas:**

1. Nome da empresa
2. Descrição da paisagem e localização
3. Função da seta (ex: "Próxima página")
4. Alt vazio (decorativa)
5. Nome da pessoa e cargo

#### Exercício 2: Melhorar Textos Alternativos

Corrijam estes exemplos:

```html
<!-- Exemplo A -->
<img src="grafico.png" alt="Gráfico">

<!-- Exemplo B -->
<img src="decoracao.svg" alt="Elemento decorativo bonito com flores">

<!-- Exemplo C -->
<img src="botao.png" alt="Imagem de um botão vermelho para clicar">
```

**Sugestões de melhoria:**

- A: Especificar que tipo de gráfico e dados
- B: Usar `alt=""` se for decorativo
- C: Descrever a função, não a aparência

#### Exercício 3: Contexto Importa

Escrevam texto alternativo para uma imagem de um cão em diferentes contextos:

1. Num site de adoção de animais
2. Num artigo sobre treino de cães
3. Na página pessoal de alguém
4. Num site veterinário sobre cuidados de saúde

#### Exercício 4: Prática Real

Escolham uma página web que usem frequentemente e analisem:

1. Quantas imagens têm texto alternativo apropriado?
2. Há imagens decorativas marcadas corretamente?
3. Que melhorias sugeririam?

**Dica:** Usem o inspector do browser (F12) para ver os atributos `alt` das imagens.



