# Conclusão e Boas Práticas

## Recapitulação

Ao longo deste módulo, explorámos vários aspetos fundamentais do design visual acessível. Vamos relembrar os pontos principais de cada capítulo:

**Desenho Visual**

- A estrutura visual clara beneficia todos os utilizadores
- A hierarquia visual deve ser consistente com a estrutura semântica
- O texto deve ser legível e ter bom contraste
- Elementos não textuais também precisam de contraste adequado

**Cor**

- Nunca use cor como único meio de transmitir informação
- Mantenha rácios de contraste adequados
- Considere diferentes tipos de daltonismo

**Indicadores de Foco**

- Mantenha sempre visível o indicador de foco
- Forneça indicadores de foco claros e consistentes
- Nunca remova o outline sem uma alternativa adequada

**Disposição, Espaçamento e Agrupamentos**

- Use espaçamento consistente e adequado
- Agrupe elementos relacionados
- Mantenha uma estrutura clara e previsível
- Cartões devem ter delimitação visível e contraste adequado

**Distrações Visuais**

- Permita controlo sobre elementos em movimento
- Evite flashes e animações perturbadoras
- Respeite as preferências de movimento reduzido

**Gráficos e Visualização de Dados**

- Forneça alternativas textuais e tabulares para gráficos
- Use cores, padrões e formas para transmitir informações
- Garanta contraste adequado em todos os elementos visuais
- Mantenha os gráficos simples e diretos

## Recursos Adicionais

1. **Ferramentas de Teste**
   - Colour Contrast Analyzer
   - Screen Readers: NVDA (Windows), VoiceOver (Mac)

2. **Documentação e Guias**
   - Web Content Accessibility Guidelines (WCAG)
   - MDN Web Docs - Accessibility

## Exercícios de Consolidação

1. **Auditoria Completa**
   
   - Escolha um website existente
   - Analise cada aspeto abordado no curso
   - Documente problemas encontrados
   - Proponha soluções específicas
   - Priorize as melhorias necessárias

2. **Projeto Prático**
   ```html
   <!-- Otimize esta estrutura considerando todos os aspetos do módulo -->
   <div class="header">
     <span class="title">Meu Site</span>
     <div class="menu">
       <a href="#">Link 1</a>
       <a href="#">Link 2</a>
     </div>
   </div>
   <div class="content">
     <div class="card">
       <img src="image.jpg">
       <span class="important">Novo!</span>
       <div>Conteúdo do cartão</div>
     </div>
   </div>
   ```

3. **Desenvolvimento Inclusivo**
   
   - Crie um componente comum (por exemplo, um formulário de contacto ou um gráfico de dados)
   - Implemente considerando todos os aspetos de acessibilidade discutidos no módulo
   - Teste com diferentes ferramentas
   - Documente as decisões de design

## Lista de Verificação Final

### Desenho Visual

- [ ] Contraste de texto adequado
- [ ] Contraste de elementos não textuais adequado
- [ ] Hierarquia visual clara
- [ ] Tamanho de texto apropriado
- [ ] Espaçamento adequado

### Cor

- [ ] Informação não depende apenas da cor
- [ ] Rácios de contraste respeitados
- [ ] Alternativas para daltonismo implementadas
- [ ] Teste com simuladores de daltonismo

### Indicadores de Foco

- [ ] Foco visível em todos os elementos interativos
- [ ] Ordem de tabulação lógica
- [ ] Estilo de foco consistente
- [ ] Teste de navegação por teclado

### Disposição e Espaçamento

- [ ] Agrupamento lógico de elementos
- [ ] Espaçamento consistente
- [ ] Layout responsivo
- [ ] Estrutura semântica correta
- [ ] Cartões com delimitação clara

### Distrações Visuais

- [ ] Controlo sobre movimento
- [ ] Sem flashes perigosos
- [ ] Respeito por prefers-reduced-motion
- [ ] Animações suaves e úteis

### Gráficos e Visualização de Dados

- [ ] Alternativas textuais para gráficos
- [ ] Tabelas de dados como complemento
- [ ] Contraste adequado nos elementos gráficos
- [ ] Uso de padrões além da cor
- [ ] Navegação por teclado em gráficos interativos

### Geral

- [ ] Teste com leitores de ecrã
- [ ] Verificação de conformidade WCAG
- [ ] Teste em diferentes dispositivos
- [ ] Documentação de acessibilidade

## Critérios de Sucesso WCAG Relevantes

### Nível A

1. **1.1.1 Conteúdo Não Textual**
   - *Descrição:* Todo o conteúdo não textual apresentado ao utilizador tem uma alternativa textual que serve o propósito equivalente.
   - *Aplicação do Design Visual:* Forneça alternativas textuais para imagens, gráficos, ícones e outros elementos visuais. Isto inclui descrições detalhadas para gráficos que transmitam as mesmas informações e conclusões que o elemento visual.

2. **1.3.1 Informação e Relações**
   - *Descrição:* A informação, estrutura e relações transmitidas através da apresentação podem ser determinadas programaticamente ou estão disponíveis no texto.
   - *Aplicação do Design Visual:* Garanta que a hierarquia visual (tamanhos, espaçamentos, agrupamentos) corresponda à estrutura semântica do HTML. Use elementos HTML apropriados para cabeçalhos, listas e tabelas, em vez de simular estes elementos visualmente.

3. **1.3.3 Características Sensoriais**
   - *Descrição:* As instruções fornecidas para compreender e operar o conteúdo não dependem exclusivamente de características sensoriais, como forma, tamanho, localização visual, orientação ou som.
   - *Aplicação do Design Visual:* Nunca use apenas a cor, forma ou posição para transmitir informações importantes. Use sempre múltiplos indicadores (texto, ícones, padrões) para comunicar estados e instruções.

4. **1.4.1 Uso da Cor**
   - *Descrição:* A cor não é utilizada como o único meio visual de transmitir informação, indicar uma ação, solicitar uma resposta ou distinguir um elemento visual.
   - *Aplicação do Design Visual:* Combine a cor com outros indicadores visuais como texto, ícones, padrões ou sublinhados. Por exemplo, links não devem ser identificados apenas pela cor, mas também por sublinhado ou outro indicador visual.

5. **2.4.3 Ordem de Foco**
   - *Descrição:* Se uma página web pode ser navegada sequencialmente e as sequências de navegação afetam o significado ou a operação, os componentes focáveis recebem foco numa ordem que preserva o significado e a operabilidade.
   - *Aplicação do Design Visual:* Desenhe o layout de forma que a ordem visual de elementos corresponda à ordem lógica de navegação por teclado. Isto é particularmente importante em layouts de múltiplas colunas e componentes complexos como cartões.

6. **2.4.7 Foco Visível**
   - *Descrição:* Qualquer interface de utilizador operável por teclado tem um modo de operação onde o indicador de foco do teclado está visível.
   - *Aplicação do Design Visual:* Desenhe indicadores de foco claros e visíveis para todos os elementos interativos. Nunca use `outline: none` sem fornecer uma alternativa visível.

### Nível AA

1. **1.4.3 Contraste (Mínimo)**
   - *Descrição:* A apresentação visual de texto e imagens de texto tem um rácio de contraste de pelo menos 4,5:1, exceto para texto grande que deve ter um rácio de pelo menos 3:1.
   - *Aplicação do Design Visual:* Escolha cores de texto e fundo que forneçam contraste suficiente. Use ferramentas de verificação de contraste para garantir que o texto normal tenha um rácio mínimo de 4,5:1 e texto grande (18pt ou 14pt negrito) tenha um rácio mínimo de 3:1.

2. **1.4.4 Redimensionar Texto**
   - *Descrição:* Exceto para legendas e imagens de texto, o texto pode ser redimensionado sem tecnologia de assistência até 200% sem perda de conteúdo ou funcionalidade.
   - *Aplicação do Design Visual:* Use unidades relativas (em, rem) para tamanhos de texto e containers. Teste o layout com zoom até 200% para garantir que o conteúdo não é cortado, sobreposto ou escondido.

3. **1.4.5 Imagens de Texto**
   - *Descrição:* Se as tecnologias em uso podem apresentar a apresentação visual, é utilizado texto para transmitir informações em vez de imagens de texto.
   - *Aplicação do Design Visual:* Evite usar imagens que contenham texto sempre que possível. Use texto real que pode ser estilizado com CSS para obter o efeito visual desejado.

4. **1.4.10 Refluxo**
   - *Descrição:* O conteúdo pode ser apresentado sem perda de informação ou funcionalidade, e sem necessidade de rolagem em duas dimensões para: Conteúdo vertical com uma largura equivalente a 320 pixels e conteúdo horizontal com uma altura equivalente a 256 pixels.
   - *Aplicação do Design Visual:* Desenhe layouts que se adaptem a diferentes tamanhos de ecrã sem rolagem horizontal. Use CSS flexbox, grid e media queries para criar designs responsivos que se reorganizam para caber em ecrãs pequenos.

5. **1.4.11 Contraste Não-Textual**
   - *Descrição:* A apresentação visual dos seguintes tem um rácio de contraste de pelo menos 3:1 contra a(s) cor(es) adjacente(s): componentes da interface de utilizador e elementos gráficos.
   - *Aplicação do Design Visual:* Garanta que todos os elementos interativos (botões, controlos de formulário), bordas significativas e informações gráficas importantes tenham um contraste de pelo menos 3:1 contra cores adjacentes.

6. **2.4.6 Cabeçalhos e Etiquetas**
   - *Descrição:* Cabeçalhos e etiquetas descrevem o tópico ou propósito.
   - *Aplicação do Design Visual:* Desenhe cabeçalhos e etiquetas que sejam descritivos e diferenciados visualmente. Use tipografia e espaçamento para criar uma hierarquia visual clara que corresponda à hierarquia semântica.

### Nível AAA

1. **1.4.6 Contraste (Melhorado)**
   - *Descrição:* A apresentação visual de texto e imagens de texto tem um rácio de contraste de pelo menos 7:1, exceto para texto grande que deve ter um rácio de pelo menos 4,5:1.
   - *Aplicação do Design Visual:* Para uma acessibilidade ainda melhor, use rácios de contraste mais elevados: pelo menos 7:1 para texto normal e 4,5:1 para texto grande. Isto é particularmente importante para utilizadores com baixa visão severa.

2. **1.4.8 Apresentação Visual**
   - *Descrição:* Para a apresentação visual de blocos de texto:
     - As cores de primeiro plano e fundo podem ser selecionadas pelo utilizador
     - A largura não é maior que 80 caracteres
     - O texto não é justificado (alinhado às margens esquerda e direita)
     - O espaçamento entre linhas é pelo menos 1.5 dentro de parágrafos
     - O espaçamento entre parágrafos é pelo menos 1.5 vezes maior que o espaçamento entre linhas
     - O texto pode ser redimensionado até 200% sem necessidade de rolagem horizontal
   - *Aplicação do Design Visual:* Implemente todas estas práticas para blocos de texto, limitando a largura das linhas, usando espaçamento generoso e alinhando o texto à esquerda para melhorar a legibilidade.

3. **1.4.9 Imagens de Texto (Sem Exceção)**
   - *Descrição:* As imagens de texto só são utilizadas para decoração pura ou quando uma apresentação particular do texto é essencial para a informação a ser transmitida.
   - *Aplicação do Design Visual:* Elimine completamente o uso de imagens de texto, exceto em casos como logotipos onde a apresentação exata é essencial para a identidade da marca.

4. **2.4.8 Localização**
   - *Descrição:* Está disponível informação sobre a localização do utilizador num conjunto de páginas.
   - *Aplicação do Design Visual:* Desenhe navegações com indicadores de localização claros, como breadcrumbs, marcando visualmente a página atual, e fornecendo pistas visuais sobre a estrutura do site.

5. **2.4.10 Cabeçalhos de Secção**
   - *Descrição:* Os cabeçalhos de secção são utilizados para organizar o conteúdo.
   - *Aplicação do Design Visual:* Use cabeçalhos para dividir conteúdo em secções lógicas, com estilos visuais distintos que criam uma hierarquia clara. Garanta que o estilo visual dos cabeçalhos corresponda à sua importância na estrutura do documento.

6. **3.2.5 Alteração a Pedido**
   - *Descrição:* As alterações de contexto são iniciadas apenas a pedido do utilizador ou existe um mecanismo para desativar tais alterações.
   - *Aplicação do Design Visual:* Desenhe interfaces que evitem mudanças inesperadas de contexto. Para elementos que atualizam dinamicamente (como carrosséis), forneça controlos claros e a opção de parar o movimento.