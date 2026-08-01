# Indicadores de Foco

## Introdução

Os indicadores de foco são elementos visuais que ajudam os utilizadores a identificar onde estão no website e quais elementos são interativos. Imagine navegar num quarto escuro com uma lanterna - o indicador de foco é essa lanterna, mostrando exatamente onde estamos na página.

### Como as Pessoas com Deficiência Usam Indicadores de Foco

**Utilizadores de Teclado**
Muitas pessoas não podem usar um rato e dependem exclusivamente do teclado para navegar. Para estas pessoas, o indicador de foco é essencial para:

- Saber onde estão na página
- Identificar elementos interativos
- Navegar de forma eficiente

**Pessoas com Baixa Visão**
Para utilizadores com baixa visão, é como tentar encontrar uma porta numa sala pouco iluminada. Precisam de:

- Indicadores de foco grandes e claros
- Alto contraste entre o indicador e o fundo
- Movimento consistente e previsível do foco

**Pessoas com Dificuldades Cognitivas**
Para estes utilizadores, perder o foco é como perder o lugar num livro. Necessitam de:

- Indicações claras da sua posição atual
- Transições suaves entre elementos
- Padrões consistentes de navegação

### Requisitos de Acessibilidade para Indicadores de Foco

1. **Visibilidade**
   
   - O indicador deve ser sempre visível
   - Contraste mínimo de 3:1 com o fundo
   - Tamanho suficiente para ser notado

2. **Consistência**
   
   - Comportamento previsível
   - Aparência consistente em toda a página
   - Movimento lógico entre elementos
   - Garantir que todos os elementos interativos têm indicador de foco

## Técnicas de Codificação

- **CSS para Foco**: Usar a pseudo-classe `:focus` para definir estilos de foco.

```css
/* Mau exemplo */
*:focus {
  outline: none; /* Remove completamente o indicador de foco */
}

/* Bom exemplo */
*:focus {
  outline: 3px solid #4A90E2;
  outline-offset: 2px;
  box-shadow: 0 0 0 3px rgba(74, 144, 226, 0.3);
}

/* Exemplo melhorado para links */
a:focus {
  outline: 3px solid #4A90E2;
  outline-offset: 2px;
  box-shadow: 0 0 0 3px rgba(74, 144, 226, 0.3);
  text-decoration: underline;
  background-color: rgba(74, 144, 226, 0.1);
}
```

*Explicação:* O primeiro exemplo remove o indicador de foco, impedindo os utilizadores de perceber quando um determinado elemento está focado. Os exemplos seguintes estilizam o indicador de foco de modo a que este seja acessível. O último exemplo acrescenta um indicador visual adicional (o sublinhado) ao texto de ligações, visto essa ser uma forma consistente de apresentar ligações em páginas web.

- **JavaScript para Foco**: Usar JavaScript para gerir o foco em elementos dinâmicos, garantindo que o foco é sempre visível.

  ```javascript
  document.querySelector('.dynamic-element').addEventListener('focus', function() {
      this.classList.add('focus-visible');
  });

  document.querySelector('.dynamic-element').addEventListener('blur', function() {
      this.classList.remove('focus-visible');
  });
  ```

*Explicação:* Quando se adicionam elementos dinamicamente a uma página é importante garantir, principalmente se não forem elementos com semântica nativa, que têm indicadores de foco apropriados. Neste exemplo, isso é conseguido através da adição de uma classe CSS quando o elemento ganha o foco, e da sua remoção quando perde o foco.

## Recomendações para Conteúdo Acessível

1. **Nunca Remova o Outline**
   
   - Mantenha sempre uma forma de indicar o foco
   - Se remover o outline padrão, substitua por uma alternativa visível
   - Teste a visibilidade em diferentes fundos

2. **Estilização Melhorada**
   ```css
   .button:focus {
     /* Múltiplos indicadores visuais */
     outline: 3px solid #4A90E2;
     box-shadow: 0 0 0 3px rgba(74, 144, 226, 0.3);
     position: relative;
   }
   ```

3. **Focus-Visible**
   Nas situações em que o design não prevê o uso de foco (o que é uma prática a evitar), deve usar-se a pseudo-classe CSS focus-visible para garantir que um indicador de foco é apresentado quando o utilizador interage com a página através de teclado ou tecnologias de apoio.
   
   ```css
   /* Use :focus-visible para estilos específicos de teclado */
   .button:focus-visible {
     outline: 3px solid #4A90E2;
   }
   ```

### Erros Comuns

1. **Remoção do Outline sem Alternativa**
   ```css
   /* Nunca faça isto */
   button:focus {
     outline: none;
   }
   ```

2. **Indicadores Muito Subtis**
   ```css
   /* Evite indicadores pouco visíveis */
   .link:focus {
     border: 1px dotted #ccc; /* Muito subtil */
   }
   ```

3. **Foco em Elementos Não Interativos**
Certifique-se de que apenas elementos interativos podem receber foco. Elementos não interativos não devem ser focáveis.


## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Nunca remova indicadores de foco sem uma alternativa adequada
- Garanta alto contraste para o indicador de foco
- Use múltiplos indicadores visuais quando possível
- Teste a navegação usando apenas o teclado
- Mantenha consistência em toda a página

### Exercícios Práticos

1. **Auditoria de Foco**
   
   - Navegue num website usando apenas o teclado
   - Documente onde o foco desaparece ou é pouco visível
   - Proponha melhorias para os problemas encontrados

2. **Estilização de Foco**
   
   - Crie um conjunto de botões e links
   - Implemente diferentes estilos de foco
   - Teste com utilizadores de teclado
   - Verifique o contraste dos indicadores

3. **Correção de Problemas**
   ```html
   <!-- Corrija os problemas neste código -->
   <style>
   .nav-link:focus { outline: none; }
   .button:focus { border: 1px solid #eee; }
   </style>
   <nav>
     <a href="#" class="nav-link">Início</a>
     <button class="button">Enviar</button>
   </nav>
   ```  