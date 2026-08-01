# Distrações Visuais

## Introdução

As distrações visuais num website são como ruído numa biblioteca - podem tornar difícil ou impossível a concentração na informação importante. Para muitas pessoas, elementos visuais em movimento, intermitentes ou excessivamente chamativos podem interferir, significativamente, com a sua capacidade de usar um website.

### Como as Pessoas com Deficiência são Afetadas por Distrações Visuais

**Pessoas com Perturbações de Défice de Atenção**
Para estas pessoas, uma página com muitas animações é como tentar ler num quarto onde alguém está constantemente a acender e apagar as luzes. Necessitam de:

- Conteúdo estático e previsível
- Animações controladas
- Capacidade de parar movimentos

**Pessoas com Epilepsia Fotossensível**
Certos padrões visuais ou flashes podem desencadear convulsões. É como se determinadas sequências visuais fossem um gatilho físico perigoso. Precisam de:

- Ausência de flashes rápidos
- Sem alternância de padrões contrastantes
- Controlo sobre conteúdo em movimento

**Pessoas com Deficiências Cognitivas**
Para estes utilizadores, múltiplos elementos em movimento são como várias pessoas a falar ao mesmo tempo. Necessitam de:

- Informação apresentada de forma calma e organizada
- Animações suaves e limitadas
- Opção de desativar elementos em movimento

**Pessoas com Deficiência Visual**
Estes utilizadores podem ter dificuldade em destinguir o conteúdo importante se houver muitos elementos visuais concorrentes. Precisam de:

- Fundos simples
- Texto com elevado constraste com o fundo
- Separação clara entre seções de conteúdo 

### Requisitos de Acessibilidade para Minimizar Distrações Visuais

1. **Controlo do Utilizador**
   
   - Opção para parar animações
   - Possibilidade de esconder conteúdo em movimento
   - Controlo sobre autoplay de média

2. **Limitações de Flash**
   
   - Não mais que três flashes por segundo
   - Área de flash limitada
   - Evitar alternância de cores contrastantes

3. **Simplicidade**

   - Design simples e limpo
   - Evitar excesso de elementos visuais 
   - Palete de cores consistente em todo o website

## Técnicas de Codificação

```css
/* Mau exemplo */
.banner {
  animation: flash 0.5s infinite;
}

@keyframes flash {
  0%, 100% { background: white; }
  50% { background: red; }
}

/* Bom exemplo */
.banner {
  animation: fadeIn 2s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* Respeito pela preferência de movimento reduzido */
@media (prefers-reduced-motion: reduce) {
  .banner {
    animation: none;
  }
}
```

*Explicação:* O mau exemplo cria uma animação extremamente distrativa que alterna rapidamente (a cada 0.5 segundos) e infinitamente entre fundo branco e vermelho, o que pode causar desconforto ou até desencadear convulsões em pessoas com epilepsia fotossensível. Em contraste, o bom exemplo utiliza uma transição suave de opacidade durante 2 segundos com uma curva de aceleração natural (ease-in-out), criando um efeito mais subtil e agradável, e, crucialmente, inclui uma regra de media query que respeita a preferência do utilizador por movimento reduzido, desativando completamente a animação quando esta preferência está ativa no sistema operativo.

```html
<!-- Mau exemplo -->
<video autoplay loop>
  <source src="background.mp4" type="video/mp4">
</video>

<!-- Bom exemplo -->
<video controls>
  <source src="background.mp4" type="video/mp4">
  <button class="video-control">Reproduzir/Parar</button>
</video>
```

*Explicação:* O mau exemplo apresenta um vídeo que começa automaticamente (autoplay) e repete indefinidamente (loop), sem oferecer ao utilizador qualquer forma de controlo sobre a reprodução, o que pode ser extremamente distrativo e perturbador, especialmente para pessoas com défice de atenção ou sensibilidade a movimento. O bom exemplo, por outro lado, dá controlo ao utilizador incluindo o atributo controls e um botão explícito de reprodução/pausa, permitindo que cada pessoa decida quando e se quer ver o vídeo, respeitando assim as suas necessidades e preferências de consumo de conteúdo.

## Recomendações para Conteúdo Acessível

1. **Animações Suaves**
   ```css
   .smooth-transition {
     transition: all 0.3s ease-in-out;
   }

   @media (prefers-reduced-motion: reduce) {
     .smooth-transition {
       transition: none;
     }
   }
   ```

2. **Controlo de Carrosséis**
   ```html
   <div class="carousel" aria-label="Galeria de imagens">
     <button class="carousel-control" aria-label="Parar rotação automática">
       Parar
     </button>
     <div class="carousel-items">
       <!-- Conteúdo do carrossel -->
     </div>
   </div>
   ```

### Erros Comuns

1. **Animações Automáticas sem Controlo**
   ```javascript
   // Evite
   setInterval(() => {
     rotateCarousel();
   }, 2000);

   // Prefira
   const carousel = {
     interval: null,
     start() {
       this.interval = setInterval(rotateCarousel, 2000);
     },
     stop() {
       clearInterval(this.interval);
     }
   };
   ```

2. **Ignorar Preferências do Utilizador**
   ```css
   /* Evite */
   * {
     animation: bounce 1s infinite !important;
   }

   /* Prefira */
   @media (prefers-reduced-motion: no-preference) {
     .animate {
       animation: bounce 1s;
     }
   }
   ```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Respeite as preferências de movimento reduzido
- Forneça controlos para conteúdo em movimento
- Evite flashes e alternâncias rápidas
- Use animações suaves e com propósito
- Permita que utilizadores parem animações

### Exercícios Práticos

1. **Auditoria de Movimento**
   
   - Analise um website popular
   - Identifique todos os elementos em movimento
   - Verifique opções de controlo
   - Proponha melhorias

2. **Implementação de Controlos**
   ```html
   <!-- Implemente controlos para este carrossel -->
   <div class="carousel">
     <img src="slide1.jpg">
     <img src="slide2.jpg">
     <img src="slide3.jpg">
   </div>
   ```

3. **Teste de Preferências**
   
   - Crie uma página com várias animações
   - Implemente suporte para prefers-reduced-motion
   - Teste com diferentes configurações
   - Documente o comportamento

4. **Otimização de Animações**
   
   - Selecione uma animação existente
   - Torne-a mais suave e menos distrativa
   - Adicione controlos de utilizador