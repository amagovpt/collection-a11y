# Desenho Visual

## Introdução

O desenho visual de um website é fundamental para todos os utilizadores, mas é especialmente importante para pessoas com diferentes tipos de deficiência. Um bom desenho visual não é apenas uma questão estética - é uma necessidade para garantir que todas as pessoas possam aceder e compreender o conteúdo.

### Como as Pessoas com Deficiência Dependem do Desenho Visual do Web Site

O desenho visual afeta diferentes grupos de utilizadores de formas distintas:

**Pessoas com Baixa Visão**
Imaginem tentar ler um jornal através de um vidro embaciado - é assim que muitas pessoas com baixa visão veem os websites. Por isso, precisam de:

- Texto suficientemente grande e claro
- Bom contraste entre texto e fundo
- Espaçamento adequado entre elementos

**Pessoas com Daltonismo**
É como se vissem o mundo através de filtros diferentes. Por exemplo, um semáforo vermelho e verde pode parecer ter a mesma cor. No contexto web:

- Não podem depender apenas da cor para compreender informação
- Precisam de padrões ou símbolos adicionais
- Necessitam de combinações de cores que mantenham bom contraste

**Pessoas com Deficiências Cognitivas**
Para estas pessoas, um website mal organizado é como um puzzle com peças misturadas. Necessitam de:

- Organização clara e consistente
- Hierarquia visual bem definida
- Espaçamento que ajude a distinguir diferentes secções

### Requisitos de Acessibilidade para Apresentação Visual

1. **Hierarquia Visual Clara**
   
   - Títulos bem diferenciados
   - Estrutura lógica de conteúdo
   - Espaçamento consistente

2. **Legibilidade**
   
   - Tamanho de texto mínimo de 12pt (equivalente a 16px)
   - Espaçamento entre linhas de pelo menos 1.5
   - Largura de texto limitada (45-75 caracteres por linha)

3. **Contraste**
   
   - Rácio mínimo de 4.5:1 para texto normal
   - Rácio mínimo de 3:1 para texto grande
   - Rácio mínimo de 3:1 para elementos não textuais importantes
   - Verificação com ferramentas de contraste

## Técnicas de Codificação

```html
<!-- Mau exemplo -->
<div class="titulo">Sobre Nós</div>
<div class="texto">
  Este é o nosso conteúdo, com fonte muito pequena e pouco contraste.
</div>

<!-- Bom exemplo -->
<h1>Sobre Nós</h1>
<p class="content">
  Este é o nosso conteúdo, com tamanho adequado e bom contraste.
</p>
```

```css
/* Mau exemplo */
.texto {
  font-size: 10px;
  line-height: 1;
  color: #777;
}

/* Bom exemplo */
.content {
  font-size: 1em;
  line-height: 1.5;
  color: #333;
  max-width: 65ch;
}
```

Para implementar um desenho visual acessível, podemos usar várias técnicas de codificação:

- **CSS para Contraste**: Usar propriedades CSS como `color` e `background-color` para definir cores com alto contraste.

  ```css
  body {
      color: #333; /* Texto escuro */
      background-color: #fff; /* Fundo branco */
  }
  ```

- **Unidades Relativas**: Usar unidades relativas como `em` ou `%` para o tamanho do texto, permitindo ajustes pelo utilizador.

  ```css
  p {
      font-size: 1em; /* Tamanho relativo */
  }
  ```

- **Media Queries**: Usar media queries para ajustar o layout em diferentes dispositivos e tamanhos de ecrã.

  ```css
  @media (max-width: 600px) {
      body {
          font-size: 1.2em; /* Aumentar o tamanho do texto em ecrãs pequenos */
      }
  }
  ```

## Recomendações para Conteúdo Acessível

1. **Use Unidades Relativas**
   
   - Prefira `rem` ou `em` em vez de `px`
   - Permite que o texto se ajuste às preferências do utilizador

2. **Mantenha Consistência**
   
   - Use um sistema de design consistente
   - Mantenha espaçamentos proporcionais
   - Aplique estilos de forma coerente

3. **Teste em Diferentes Cenários**
   
   - Verifique com zoom até 200%
   - Teste com diferentes tamanhos de ecrã
   - Valide com ferramentas de acessibilidade

### Erros Comuns

1. **Texto sobre Imagens sem Contraste Adequado**
   ```css
   /* Evite */
   .hero-text {
     color: white; /* Pode não ter contraste suficiente */
   }
   
   /* Prefira */
   .hero-text {
     color: white;
     text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
     background-color: rgba(0,0,0,0.5);
   }
   ```

2. **Fontes Muito Pequenas ou Pouco Espaçadas**
   ```css
   /* Evite */
   .small-text {
     font-size: 11px;
     line-height: 1.1;
   }
   ```

3. **Contraste Insuficiente em Elementos Não Textuais**
   ```css
   /* Evite */
   .icon {
     color: #767676; /* Não tem contraste suficiente com fundo branco */
   }
   
   /* Prefira */
   .icon {
     color: #595959; /* Melhor contraste com fundo branco */
     stroke-width: 2px; /* Aumenta a visibilidade */
   }
   ```

## Contraste em Elementos Não Textuais

Os elementos não textuais, como ícones, bordas, botões e indicadores, também necessitam de contraste adequado para serem percebidos corretamente por todos os utilizadores.

### Requisitos de Contraste para Elementos Não Textuais

- **Elementos Interativos**: Rácio mínimo de 3:1 contra cores adjacentes
- **Informação Visual Importante**: Rácio mínimo de 3:1 contra o fundo
- **Bordas que Delimitam Conteúdo**: Rácio mínimo de 3:1 contra o fundo

### Técnicas para Melhorar Contraste em Elementos Não Textuais

```css
/* Ícones com contraste adequado */
.icon {
  color: #595959; /* Contraste de 7:1 com fundo branco */
}

/* Bordas com contraste adequado */
.card {
  border: 2px solid #595959; /* Contraste de 7:1 com fundo branco */
}

/* Botões com contraste adequado */
.button {
  background-color: #005fb8; /* Contraste de 4.5:1 com texto branco */
  color: white;
  padding: 10px 20px;
}

/* Elementos gráficos com contraste adequado */
.chart-bar {
  fill: #005fb8; /* Contraste de 4.5:1 com fundo branco */
  stroke: #003366; /* Borda mais escura para definir limites */
  stroke-width: 2px;
}
```

### Teste de Contraste para Elementos Não Textuais

Use ferramentas como o Colour Contrast Analyzer para verificar o contraste entre:
- Ícones e fundo
- Bordas e fundo
- Elementos gráficos e cores adjacentes
- Indicadores de estado (como validação de formulários) e fundo

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- O desenho visual afeta significativamente a acessibilidade
- Use contrastes adequados para texto e elementos não textuais
- Mantenha consistência no design
- Teste em diferentes cenários e com diferentes utilizadores

### Exercícios Práticos

1. **Análise de Contraste**
   
   - Escolha um website
   - Verifique o contraste de diferentes elementos usando o WCAG Color Contrast Analyzer
   - Identifique e proponha melhorias

2. **Hierarquia Visual**
   
   - Crie uma página simples com três níveis de títulos
   - Aplique estilos que tornem a hierarquia clara visualmente
   - Teste com diferentes tamanhos de ecrã

3. **Otimização de Legibilidade**
   
   - Selecione um texto existente
   - Aplique as recomendações de legibilidade (tamanho, espaçamento, largura)
   - Compare o antes e depois em diferentes tamanhos de ecrã