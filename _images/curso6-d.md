---
title: Imagens Funcionais
layout: default
nav_order: 4
---

# Imagens Funcionais

## Introdução

### O que são Imagens Funcionais?

As imagens funcionais são imagens que têm uma função específica num website, funcionando como botões, ligações ou controlos interativos. Imagine-as como "botões disfarçados de imagem" - não estão apenas ali para ser bonitas, mas para fazer alguma coisa quando clicamos nelas.

**Exemplos comuns de imagens funcionais:**

- Ícones de redes sociais que levam às páginas da empresa
- Botões "Comprar Agora" com imagens atrativas
- Logótipos que funcionam como ligação para a página inicial
- Ícones de impressora para imprimir a página
- Setas de navegação em galerias de fotos

### Como as Pessoas com Deficiência usam Imagens Funcionais

#### Utilizadores de Leitores de Ecrã

**O que acontece na prática:**

- O leitor de ecrã "lê" o texto alternativo da imagem funcional
- Se não houver texto alternativo, pode anunciar apenas "imagem" ou "ligação sem texto"
- O utilizador precisa de saber que função a imagem desempenha

**Analogia:** É como ter alguém a descrever-lhe os botões de um comando à distância pelo telefone. Se essa pessoa apenas disser "botão vermelho", não sabe se é para mudar de canal ou para desligar a televisão.

#### Utilizadores com Deficiências Motoras

Pessoas que usam dispositivos de navegação alternativos (como software de comando por voz ou switches) dependem de uma identificação clara das imagens funcionais.

**Exemplo prático:**
```html
<!-- ❌ Mau exemplo -->
<a href="facebook.com">
  <img src="facebook-icon.png" alt="">
</a>

<!-- ✅ Bom exemplo -->
<a href="facebook.com">
  <img src="facebook-icon.png" alt="Visitar a nossa página no Facebook">
</a>
```

**O que funciona bem:** No bom exemplo, um utilizador de leitor de ecrã ouve "Visitar a nossa página no Facebook" e sabe exatamente o que acontece se clicar.

**O que funciona mal:** No mau exemplo, o leitor de ecrã pode anunciar apenas "ligação" ou "imagem", deixando o utilizador sem saber para onde a ligação o leva.

### Requisitos de Acessibilidade para Imagens Funcionais

#### Critério Principal: Texto Alternativo Descritivo

O texto alternativo deve descrever a **função** da imagem, não a sua aparência.

**Regra de ouro:** Pergunte-se "O que acontece quando clico nesta imagem?" A resposta deve ser o seu texto alternativo.

#### Exemplos Comparativos

| Imagem | ❌ Texto Alternativo Inadequado | ✅ Texto Alternativo Adequado |
|--------|--------------------------------|-------------------------------|
| Ícone de envelope para contactos | "Envelope" | "Contactar-nos" |
| Lupa para pesquisa | "Lupa" | "Pesquisar" |
| Seta para a próxima página | "Seta para a direita" | "Próxima página" |
| Carrinho de compras | "Carrinho" | "Ver carrinho de compras" |

## Técnicas de Codificação

### Técnica 1: Atributo alt em Imagens dentro de Ligações

```html
<!-- Estrutura básica -->
<a href="destino.html">
  <img src="imagem.png" alt="Descrição da função">
</a>
```

**Exemplo prático - Botão de download:**
```html
<a href="manual.pdf">
  <img src="download-icon.png" alt="Descarregar manual em PDF">
</a>
```

**Explicação:** O utilizador sabe exatamente que vai descarregar um manual em formato PDF.

### Técnica 2: Imagens Funcionais com Texto Adicional

Por vezes temos uma imagem funcional acompanhada de texto. Nestes casos, o texto alternativo deve complementar, não repetir.

```html
<!-- ❌ Redundante -->
<a href="facebook.com">
  <img src="facebook.png" alt="Facebook">
  Facebook
</a>

<!-- ✅ Complementar -->
<a href="facebook.com">
  <img src="facebook.png" alt="">
  Facebook
</a>

<!-- ✅ Alternativa -->
<a href="facebook.com">
  <img src="facebook.png" alt="Visitar no Facebook">
  Seguir-nos
</a>
```

**O que funciona bem na segunda opção:** O texto alternativo está vazio porque o texto "Facebook" já identifica a ligação. Evita redundância.

**O que funciona bem na terceira opção:** O texto alternativo complementa o texto visível, criando uma mensagem completa: "Visitar no Facebook Seguir-nos".

### Técnica 3: Uso de aria-label como Alternativa

```html
<!-- Quando o alt não é suficiente -->
<a href="print.php" aria-label="Imprimir esta página">
  <img src="printer.png" alt="">
</a>
```

## Recomendações para Conteúdo Acessível

### 1. Seja Conciso mas Informativo

**Boa prática:** Mantenha o texto alternativo curto quando possível.

```html
<!-- ✅ Conciso e claro -->
<a href="carrinho.html">
  <img src="cart.png" alt="Ver carrinho (3 itens)">
</a>

<!-- ❌ Demasiado longo -->
<a href="carrinho.html">
  <img src="cart.png" alt="Clique aqui para ver o seu carrinho de compras que atualmente contém três itens">
</a>
```

### 2. Use Linguagem Natural

**Evite jargão técnico** e use palavras que qualquer pessoa entenderia.

```html
<!-- ✅ Linguagem natural -->
<a href="login.html">
  <img src="user-icon.png" alt="Iniciar sessão">
</a>

<!-- ❌ Jargão técnico -->
<a href="login.html">
  <img src="user-icon.png" alt="Autenticar credenciais">
</a>
```

### 3. Contextualize a Ação

O texto alternativo deve deixar claro o que acontece ao clicar:

```html
<!-- ✅ Acção clara -->
<a href="mailto:info@empresa.com">
  <img src="email.png" alt="Enviar email para info@empresa.com">
</a>

<!-- ❌ Acção pouco clara -->
<a href="mailto:info@empresa.com">
  <img src="email.png" alt="Email">
</a>
```

### 4. Considere o Estado do Elemento

Para botões que mudam de estado:

```html
<!-- Botão de reprodução -->
<button onclick="togglePlay()">
  <img src="play.png" alt="Reproduzir vídeo" id="playButton">
</button>

<!-- JavaScript para atualizar o alt -->
<script>
function togglePlay() {
  const button = document.getElementById('playButton');
  if (button.alt === 'Reproduzir vídeo') {
    button.alt = 'Pausar vídeo';
    button.src = 'pause.png';
  } else {
    button.alt = 'Reproduzir vídeo';
    button.src = 'play.png';
  }
}
</script>
```

### Erros Comuns

#### Erro 1: Texto Alternativo Vazio em Imagens Funcionais

```html
<!-- ❌ Erro grave -->
<a href="contactos.html">
  <img src="phone.png" alt="">
</a>
```

**Problema:** O utilizador de leitor de ecrã não sabe para onde a ligação o leva.

**Analogia:** É como ter um botão no elevador sem números nem palavras - não sabe que andar vai escolher.

#### Erro 2: Descrever a Aparência em vez da Função

```html
<!-- ❌ Descreve aparência -->
<a href="pesquisa.html">
  <img src="magnifying-glass.png" alt="Lupa azul">
</a>

<!-- ✅ Descreve função -->
<a href="pesquisa.html">
  <img src="magnifying-glass.png" alt="Pesquisar no site">
</a>
```

**O que funciona mal:** "Lupa azul" não diz ao utilizador que pode pesquisar.

**O que funciona bem:** "Pesquisar no site" indica claramente a função.

#### Erro 3: Redundância entre Texto Alternativo e Texto Visível

```html
<!-- ❌ Redundante -->
<a href="facebook.com">
  <img src="fb.png" alt="Facebook">
  Visitar Facebook
</a>
```

**Problema:** O leitor de ecrã lê "Facebook Visitar Facebook", criando repetição desnecessária.

#### Erro 4: Usar "Clique aqui" ou "Ligação para"

```html
<!-- ❌ Pouco informativo -->
<a href="relatorio.pdf">
  <img src="pdf-icon.png" alt="Clique aqui">
</a>

<!-- ✅ Informativo -->
<a href="relatorio.pdf">
  <img src="pdf-icon.png" alt="Descarregar relatório anual (PDF)">
</a>
```

**Analogia:** É a diferença entre alguém dizer "carrega neste botão" e "carrega no botão para ligar a televisão".

#### Erro 5: Não Considerar o Contexto da Página

O mesmo ícone pode ter funções diferentes dependendo do contexto:

```html
<!-- Em página de artigo -->
<a href="#" onclick="printPage()">
  <img src="printer.png" alt="Imprimir este artigo">
</a>

<!-- Em página de lista de documentos -->
<a href="documento.pdf">
  <img src="printer.png" alt="Descarregar documento para impressão">
</a>
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

**Lembre-se destes princípios fundamentais:**

1. **Função, não aparência**: O texto alternativo deve descrever o que a imagem faz, não como se parece
2. **Seja específico**: "Pesquisar produtos" é melhor que apenas "Pesquisar"
3. **Evite redundância**: Se há texto visível que já explica a função, considere deixar o alt vazio
4. **Pense no contexto**: A mesma imagem pode precisar de descrições diferentes em páginas diferentes
5. **Teste sempre**: Use um leitor de ecrã ou navegue apenas com o teclado para verificar se faz sentido

**Fórmula simples para criar bom texto alternativo:**

> "Se eu não pudesse ver esta imagem, que informação precisaria para saber o que acontece se clicar nela?"

### Exercícios Práticos

#### Exercício 1: Identificar Problemas

Analise estes exemplos e identifique os problemas:

```html
<!-- Exemplo A -->
<a href="youtube.com/empresa">
  <img src="youtube.png" alt="Ícone vermelho do YouTube">
</a>

<!-- Exemplo B -->
<a href="download.php?file=manual">
  <img src="download.png" alt="">
</a>

<!-- Exemplo C -->
<a href="contactos.html">
  <img src="phone.png" alt="Ver contactos">
  Contactos
</a>
```

**Soluções:**

**Exemplo A - Problema:** Descreve aparência ("ícone vermelho") em vez de função.
**Correção:**
```html
<a href="youtube.com/empresa">
  <img src="youtube.png" alt="Ver vídeos no YouTube">
</a>
```

**Exemplo B - Problema:** Texto alternativo vazio numa imagem funcional.
**Correção:**
```html
<a href="download.php?file=manual">
  <img src="download.png" alt="Descarregar manual">
</a>
```

**Exemplo C - Problema:** Redundância entre alt e texto visível.
**Correção:**
```html
<a href="contactos.html">
  <img src="phone.png" alt="">
  Contactos
</a>
```

#### Exercício 2: Criar Texto Alternativo

Para cada imagem funcional, escreva o texto alternativo adequado:

1. **Ícone de impressora** numa página de artigo científico que abre a janela de impressão
2. **Logótipo da empresa** que leva à página inicial
3. **Ícone de carrinho de compras** que mostra "5 itens" e leva à página do carrinho
4. **Seta para a direita** numa galeria de fotos para ver a próxima imagem
5. **Ícone de WhatsApp** para enviar mensagem direta para o suporte

**Soluções sugeridas:**

1. `alt="Imprimir este artigo"`
2. `alt="Voltar à página inicial"` ou `alt="Página inicial"`
3. `alt="Ver carrinho (5 itens)"`
4. `alt="Próxima imagem"`
5. `alt="Contactar suporte via WhatsApp"`

#### Exercício 3: Corrigir Código

Corrija este código para torná-lo acessível:

```html
<div class="social-links">
  <a href="https://facebook.com/empresa">
    <img src="fb.png" alt="f">
  </a>
  <a href="https://twitter.com/empresa">
    <img src="twitter.png" alt="Passarinho azul">
  </a>
  <a href="mailto:info@empresa.com">
    <img src="email.png" alt="Clique para email">
  </a>
</div>
```

**Solução:**

```html
<div class="social-links">
  <a href="https://facebook.com/empresa">
    <img src="fb.png" alt="Seguir no Facebook">
  </a>
  <a href="https://twitter.com/empresa">
    <img src="twitter.png" alt="Seguir no Twitter">
  </a>
  <a href="mailto:info@empresa.com">
    <img src="email.png" alt="Enviar email">
  </a>
</div>
```

**O que foi corrigido:**

- "f" → "Seguir no Facebook" (mais descritivo)
- "Passarinho azul" → "Seguir no Twitter" (função em vez de aparência)
- "Clique para email" → "Enviar email" (mais direto, sem "clique")

#### Exercício 4: Reflexão Prática

**Situação:** Está a criar um botão de partilha para redes sociais. Tem uma imagem com vários ícones (Facebook, Twitter, LinkedIn) e o texto "Partilhar".

**Pergunta:** Como deve estruturar o HTML e que texto alternativo deve usar?

**Solução possível:**

```html
<!-- Opção 1: Uma imagem com múltiplas funções -->
<div class="share-buttons">
  <span>Partilhar:</span>
  <a href="[url-facebook]">
    <img src="fb-icon.png" alt="Partilhar no Facebook">
  </a>
  <a href="[url-twitter]">
    <img src="twitter-icon.png" alt="Partilhar no Twitter">
  </a>
  <a href="[url-linkedin]">
    <img src="linkedin-icon.png" alt="Partilhar no LinkedIn">
  </a>
</div>
```

**Explicação:** Cada ícone é uma imagem separada com a sua própria função específica, permitindo que o utilizador escolha exatamente onde quer partilhar.
