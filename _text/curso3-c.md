# Apresentação Visual de Conteúdo Texto

## Introdução

A apresentação visual do texto é fundamental para a legibilidade e compreensão do conteúdo web. Uma boa apresentação visual ajuda todos os utilizadores, mas é especialmente importante para pessoas com diferentes tipos de deficiência.

### Como as Pessoas com Deficiência Usam a Apresentação Visual

**Pessoas com Baixa Visão**
Imagina tentar ler um jornal num quarto muito escuro. Para pessoas com baixa visão, mesmo texto com pouco contraste pode criar uma experiência semelhante. Necessitam de:

- Alto contraste entre texto e fundo
- Capacidade de aumentar o tamanho do texto
- Espaçamento adequado entre linhas

*Por que isto importa:* Sem estas adaptações, seria como tentar ler através de um vidro embaciado - possível, mas extremamente cansativo.

**Pessoas com Dislexia**
Pensa num texto onde as palavras parecem estar a flutuar na página. Para muitas pessoas com dislexia, certas apresentações visuais podem criar este efeito. Beneficiam de:

- Tipos de letra específicos (como OpenDyslexic)
- Espaçamento generoso entre linhas e parágrafos
- Alinhamento à esquerda (não justificado)

*Por que isto importa:* O formato adequado pode ser a diferença entre ler com fluidez ou lutar com cada palavra.

**Pessoas com Deficiências Cognitivas**
Imagina tentar encontrar um produto específico num supermercado sem qualquer organização. Um layout confuso ou inconsistente pode criar uma experiência semelhante. Precisam de:

- Hierarquia visual clara
- Consistência no design
- Espaços em branco adequados

### Requisitos de Acessibilidade para Apresentação Visual de Conteúdo Textual

1. **Contraste**

   - Rácio mínimo de contraste de 4.5:1 para texto normal
   - Rácio mínimo de 3:1 para texto grande (18pt ou 14pt negrito)

2. **Dimensionamento**
   
   - Texto deve ser redimensionável até 200% sem perda de funcionalidade
   - Usar unidades relativas (rem, em) em vez de fixas (px)

3. **Espaçamento**
   
   - Permitir ajustar a altura de linha para, pelo menos, 1.5 vezes o tamanho da fonte
   - Permitir ajustar o espaçamento entre parágrafos para, pelo menos, 2 vezes o tamanho da fonte
   - Permitir ajustar o espaçamento entre letras para, pelo menos, 0.12 vezes o tamanho da fonte
   - Permitir ajustar o espaçamento entre palavras para, pelo menos, 0.16 vezes o tamanho da fonte

4. **Alinhamento**
   
   - Alinhamento à esquerda para facilitar a leitura

5. **Fontes**
   
   - Usar fontes que sejam fáceis de ler
   - Evitar fontes decorativas ou complexas

6. **Ícones e Imagens**
   
   - Usar ícones e imagens para complementar o texto
   - Garantir que os ícones e imagens têm descrições alternativas

## Técnicas de Codificação

```css
/* Mau exemplo */
.texto {
    font-size: 12px;
    color: gray;
    line-height: 1;
    text-align: justify;
}

/* Bom exemplo */
.texto {
    font-size: 1rem;
    color: #333333;
    background: #FFFFFF;
    line-height: 1.5;
    text-align: left;
    max-width: 70ch;
}
```

*Explicação:* O segundo exemplo usa:

- Unidades relativas para permitir redimensionamento
- Cor com contraste adequado
- Altura de linha que melhora a legibilidade
- Texto alinhado à esquerda
- Largura máxima que facilita a leitura

```css
/* Mau exemplo */
.conteudo {
    margin: 0;
    padding: 5px;
    background: #FAFAFA;
    color: #666;
}

/* Bom exemplo */
.conteudo {
    margin: 2rem 0;
    padding: 1.5rem;
    background: #FFFFFF;
    color: #222222;
    letter-spacing: 0.05em;
    word-spacing: 0.1em;
}
```

*Explicação:* O segundo exemplo usa:

- Espaço vazio ao redor do conteúdo que é apropriado e ajusta-se ao tamanho do texto
- Cor com contraste adequado
- Espaçamento entre letras e palavras que se ajusta ao tamanho da fonte

```css
/* Mau exemplo */
.p {
    font-size: 14px;
}

/* Bom exemplo */
@media (max-width: 600px) {
  p {
      font-size: 1.2em;
  }
}
```

*Explicação:* O segundo exemplo usa media queries para ajustar o tamanho da fonte à dimensão do ecrã.

## Recomendações para Conteúdo Acessível

1. **Cores e Contraste**
   Use ferramentas de verificação de contraste para garantir legibilidade:
   ```css
   /* Bom contraste */
   .texto-principal {
       background: #FFFFFF;
       color: #333333; /* Rácio de contraste ~10:1 */
   }
   ```

2. **Tipografia e Tamanhos**
   ```css
   .texto {
       font-size: 1rem;
       font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
   }
   ```

3. **Layout e Espaçamento**
   ```css
   .artigo {
       max-width: 70ch;
       padding: 1rem;
       line-height: 1.6;
       margin-bottom: 2rem;
   }
   ```

### Erros Comuns

1. **Texto com Pouco Contraste**
   ```css
   /* Mau exemplo */
   .texto-subtil {
       color: #CCCCCC; /* Contraste muito baixo em fundo branco */
   }
   ```

2. **Tamanhos Fixos**
   ```css
   /* Mau exemplo */
   .texto-fixo {
       font-size: 14px;
       line-height: 16px;
   }
   ```

3. **Fontes Decorativas**
   ```css
   /* Mau exemplo */
   body {
     font-family: "Brush Script MT", cursive;
     font-size: 16px;
     color: #333333;
   }
   ```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Use rácios de contraste adequados
- Implemente dimensionamento flexível
- Forneça espaçamento apropriado
- Use fontes legíveis
- Mantenha consistência visual
- Use unidades relativas e media queries para ajustes responsivos
- Teste com diferentes configurações de browser

### Exercícios Práticos

1. **Análise de Contraste**
   Carregue uma página web no seu navegador e use uma ferramenta como o WebAIM Contrast Checker para verificar o contraste de:
   
   - Texto principal
   - Links
   - Botões
   - Texto sobre imagens

2. **Verificação de Redimensionamento**
   Carregue uma página web no seu navegador, aumente o zoom até 200% e verifique se:
   
   - O texto permanece legível
   - Não há sobreposição
   - A estrutura mantém-se intacta

3. **Implementação de Espaçamento**
   Crie uma página com:
   
   - Diferentes níveis de cabeçalhos
   - Parágrafos
   - Listas
   
   Aplique espaçamento adequado usando unidades relativas.

4. **Otimização de Layout**
   Melhore o seguinte código:
   ```css
   .conteudo {
       width: 1200px;
       font-size: 12px;
       text-align: justify;
   }
   ```