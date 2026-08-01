# Texto

## Introdução

O texto é uma das formas mais básicas e essenciais de comunicação na web. É através dele que comunicamos informação, desde notícias a instruções, documentação ou opiniões. No entanto, para pessoas com deficiência, a interação com o texto pode ser um desafio. Vamos explorar como diferentes deficiências afetam a leitura e compreensão do texto.

### Como as Pessoas com Deficiência Usam Texto

As pessoas acedem ao texto de formas muito diferentes, dependendo das suas capacidades e preferências:

**Utilizadores de Leitores de Ecrã**

Imagina que estás numa sala escura e alguém te lê um livro. É assim que muitas pessoas cegas ou com baixa visão acedem ao texto através de leitores de ecrã. Estes programas convertem o texto digital em fala sintetizada ou braille.

*Por que isto importa:* Se o texto estiver apenas disponível como imagem, seria como ter um livro com páginas em branco - o leitor de ecrã não conseguiria "ver" o texto para o ler.

**Utilizadores com Dislexia**

Pensa num texto onde todas as letras parecem estar a dançar ou a trocar de posição. Para muitas pessoas com dislexia, ler pode ser assim. Precisam frequentemente de ajustar o espaçamento entre letras, linhas, ou usar tipos de letra específicos.

*Por que isto importa:* Se o texto estiver "trancado" num formato rígido, seria como forçar alguém a ler um livro em movimento - frustrante e possivelmente impossível.

**Utilizadores com Baixa Visão**

Imagina tentar ler um texto muito pequeno ao pôr-do-sol. Pessoas com baixa visão podem precisar de aumentar o tamanho do texto ou ajustar o contraste para o conseguirem ler confortavelmente.

*Por que isto importa:* Se o texto não puder ser redimensionado, seria como dar óculos com a graduação errada a alguém - a informação está lá, mas não pode ser acedida adequadamente.

**Utilizadores com Deficiência Cognitiva**

Pensa numa ocasião em que tiveste de explicar um conceito difícil a uma criança. Usar palavras simples e frases curtas torna a explicação mais clara e fácil de entender.

*Por que isto importa:* Se o texto for demasiado complexto, as pessoas até o podem conseguir ler, mas não o vão conseguir entender. 

### Requisitos de Acessibilidade para Texto

Para garantir que o texto é acessível, devemos seguir alguns requisitos fundamentais:

1. **Texto Real vs. Imagens de Texto**
   O texto deve ser texto real em HTML, não imagens de texto. Isto permite que seja:
   
   - Lido por leitores de ecrã
   - Redimensionado sem perder qualidade
   - Copiado e colado
   - Traduzido automaticamente

2. **Estrutura Semântica**
   O texto deve ter uma estrutura clara usando elementos HTML apropriados:
   
   - Cabeçalhos (`<h1>` a `<h6>`) para hierarquia
   - Parágrafos (`<p>`) para blocos de texto
   - Listas (`<ul>`, `<ol>`) para sequências de itens

3. **Contraste e Legibilidade**
   O texto deve ser apresentado garantindo: 
   
   - Rácio de contraste mínimo de 4.5:1 para texto normal
   - Possibilidade de redimensionar até 200% sem perda de funcionalidade
   - Espaçamento adequado entre linhas e parágrafos

4. **Clareza e Simplicidade**
   O texto deve fazer uso de linguagem clara e simples, evitando jargão e termos técnicos desnecessários.

## Técnicas de Codificação

Aqui estão algumas técnicas fundamentais para criar texto acessível:

```html
<!-- Mau exemplo -->
<div class="titulo">Bem-vindo ao nosso site</div>
<div class="texto">Este é o nosso conteúdo principal.</div>

<!-- Bom exemplo -->
<h1>Bem-vindo ao nosso site</h1>
<p>Este é o nosso conteúdo principal.</p>
```

*Explicação:* O primeiro exemplo usa `div`s genéricos que não transmitem significado semântico. O segundo exemplo usa elementos HTML semânticos que clarificam a estrutura do documento.

```css
/* Mau exemplo */
.texto {
    font-size: 10px;
    line-height: 1;
}

/* Bom exemplo */
.texto {
    font-size: 1rem;
    line-height: 1.5;
}
```

*Explicação:* O primeiro exemplo usa tamanhos fixos que não respeitam as preferências do utilizador. O segundo exemplo usa unidades relativas que permitem redimensionamento.

## Recomendações para Conteúdo Acessível

1. **Use texto verdadeiro sempre que possível**
   Em vez de incluir texto em imagens, use texto HTML real que pode ser manipulado e acedido por tecnologias de apoio.

2. **Estruture o conteúdo hierarquicamente**
   Use cabeçalhos de forma lógica, começando com `<h1>` e não saltando níveis.

3. **Forneça espaçamento adequado**
   Use margens e padding para criar espaço visual entre elementos, facilitando a leitura.

### Erros Comuns

1. **Usar imagens de texto quando texto real seria mais apropriado**

   ```html
   <!-- Mau exemplo -->
   <img src="titulo-boas-vindas.png" alt="Bem-vindo ao nosso site">
   
   <!-- Bom exemplo -->
   <h1>Bem-vindo ao nosso site</h1>
   ```

2. **Utilizar cores com pouco contraste entre o texto e o fundo**

    ```css
    /* Mau exemplo - texto e fundo em tons de cinzento com contraste de 2.9 para 1*/
    .texto {
        color: #5B5B5B;
        background: #A9A9A9;
    }

    /* Bom exemplo - texto preto em fundo branco com contraste de 21 para 1 */
    .texto {
        color: #000000;
        background: #FFFFFF;
    }
    ```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Use sempre texto real em vez de imagens de texto
- Estruture o texto de forma lógica recorrendo a elementos HTML semânticos como cabeçalhos, parágrafos e listas
- Garanta que o texto pode ser redimensionado e tem contraste adequado
- Utilizar linguagem clara e simples
- Considere como diferentes utilizadores acedem ao texto

### Exercícios Práticos

1. **Análise de Acessibilidade**
   Examine um website à sua escolha e identifique:
   
   - Uso de texto real vs. imagens de texto
   - Estrutura de cabeçalhos
   - Contraste do texto
   
2. **Correção de Código**
   Corrija o seguinte código para o tornar mais acessível:
   ```html
   <div class="titulo-grande">Sobre Nós</div>
   <img src="texto-missao.jpg" alt="Nossa missão é criar websites incríveis">
   <div class="subtitulo">Nossa História</div>
   ```

3. **Teste com Leitor de Ecrã**
   Use um leitor de ecrã (como o NVDA ou VoiceOver) para navegar por uma página que criou. Note como a estrutura do texto afeta a navegação.

4. **Verificação de Contraste**
   Use uma ferramenta de verificação de contraste para avaliar diferentes combinações de cores de texto e fundo no seu site.
