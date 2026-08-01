# Cor

## Introdução

A cor é um elemento fundamental no desenho de um website, mas a sua utilização deve ser cuidadosamente pensada para garantir que todos os utilizadores, independentemente das suas capacidades visuais, possam aceder e compreender o conteúdo.

### Como as Pessoas com Deficiência Dependem da Cor

**Daltonismo**
Existem vários tipos de daltonismo, cada um afetando a perceção das cores de forma diferente:

- Deuteranopia: dificuldade em distinguir verdes e vermelhos
- Protanopia: dificuldade em ver tons de vermelho
- Tritanopia: dificuldade em distinguir azuis e amarelos

Imagine tentar distinguir semáforos se o vermelho e o verde parecessem a mesma cor - é assim que muitas pessoas com daltonismo experienciam websites que dependem apenas de cor para transmitir informação.

**Baixa Visão**
Para pessoas com baixa visão, distinguir cores próximas (com pouco contraste entre si) pode ser como tentar ler um texto impresso em papel usando tons claros - os elementos podem misturar-se e tornar-se indistinguíveis.

### Requisitos de Acessibilidade para Cor

1. **Contraste de Cor**
   
   - Texto normal: rácio mínimo de 4.5:1
   - Texto grande (18pt ou 14pt negrito): rácio mínimo de 3:1
   - Elementos interativos: rácio mínimo de 3:1 com cores adjacentes

2. **Independência de Cor**
   
   - A informação não pode depender apenas da cor
   - Usar padrões, ícones ou texto adicional
   - Garantir que formulários não indicam erros apenas com cor vermelha

3. **Consistência**

   - Manter uma paleta de cores consistente em todo o website
   - Evitar combinações de cores que são difíceis de distinguir para pessoas com daltonismo

## Técnicas de Codificação

```html
<!-- Mau exemplo -->
<p>Campos marcados a vermelho são obrigatórios</p>
<input type="text" class="required-field">

<!-- Bom exemplo -->
<p>Campos marcados com * são obrigatórios</p>
<div class="field-wrapper">
  <input type="text" class="required-field" required>
  <span class="required-marker">*</span>
</div>
```

*Explicação:* O primeiro exemplo recorre apenas à cor para indicar o estado do campo do formulário. O segundo exemplo usa, adicionalmente, um carater para sinalizar um campo em erro.

```css
/* Mau exemplo */
.error-message {
  color: red;
}

/* Bom exemplo */
.error-message {
  color: #D32F2F;
  background: #FFEBEE;
  border-left: 4px solid #D32F2F;
  padding: 8px;
}
```

*Explicação:* O primeiro exemplo recorre apenas à cor para indicar erros. O segundo exemplo introduz, adicionalmente, uma borda no campo do formulário.

## Recomendações para Conteúdo Acessível

1. **Paletas de Cores Seguras**
   
   - Use ferramentas de simulação de daltonismo
   - Crie paletas que funcionem em escala de cinzentos
   - Teste combinações de cores com utilizadores reais

2. **Indicadores Múltiplos**
   
   - Combine cor com ícones
   - Adicione padrões ou texturas
   - Use texto descritivo

3. **Sistema de Cores Consistente**
   
   - Defina um sistema de cores com significados consistentes
   - Documente o uso de cores para a equipa
   - Mantenha uma biblioteca de componentes acessíveis

### Erros Comuns

1. **Depender Apenas da Cor**
   ```html
   <!-- Evitar -->
   <div class="status-green">Aprovado</div>
   
   <!-- Preferir -->
   <div class="status approved">
     <span class="status-icon">✓</span>
     Aprovado
   </div>
   ```

*Explicação:* O primeiro exemplo recorre apenas à cor para indicar o estado do campo do formulário. O segundo exemplo usa, adicionalmente, um ícone para indicar o estado.

2. **Contraste Insuficiente**
   ```css
   /* Evitar */
   .subtle-text {
     color: #888888;  /* Baixo contraste com fundo branco */
   }
   
   /* Preferir */
   .subtle-text {
     color: #595959;  /* Melhor contraste mantendo subtileza */
   }
   ```

*Explicação:* O primeiro exemplo usa um cinzento que não tem contraste suficiente com branco (3,5 para 1) no caso do texto não ser grande. O segundo exemplo usa outro tom de cinzento, com suficiente contraste (7 para 1) que funciona para qualquer dimensão do texto.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Nunca use cor como único meio de transmitir informação
- Mantenha rácios de contraste adequados
- Combine cores com outros indicadores visuais
- Teste com diferentes tipos de daltonismo
- Use ferramentas de verificação de contraste

### Exercícios Práticos

1. **Análise de Acessibilidade de Cor**
   
   - Selecione um website popular
   - Utilize uma ferramenta de simulação de daltonismo
   - Identifique problemas e proponha soluções

2. **Redesenho de Formulário**
   
   - Escolha um formulário existente
   - Redesenhe os estados de erro e sucesso
   - Implemente indicadores múltiplos além da cor

3. **Criação de Paleta Acessível**
   
   - Crie uma paleta de 5 cores
   - Verifique contrastes entre todas as combinações
   - Teste com simuladores de daltonismo
   - Documente os casos de uso para cada cor

4. **Auditoria de Contraste**
   
   - Utilize uma ferramenta de verificação de contraste
   - Analise 5 websites diferentes
   - Crie um relatório com problemas encontrados e sugestões de melhoria