---
title: CAPTCHAs
layout: default
nav_order: 6
---

# CAPTCHAs

## Introdução

Os CAPTCHAs são como porteiros digitais que verificam se quem está a tentar entrar num website é uma pessoa real e não um robô. A palavra CAPTCHA significa "Completely Automated Public Turing test to tell Computers and Humans Apart" (Teste de Turing Público Completamente Automatizado para Distinguir Computadores e Humanos).

Imagine um clube exclusivo onde o porteiro pede para resolver um puzzle antes de deixar entrar. É exatamente isso que os CAPTCHAs fazem - apresentam um desafio que, teoricamente, só os humanos conseguem resolver.

### Como as Pessoas com Deficiência usam CAPTCHAs

#### Pessoas com Deficiência Visual

Para uma pessoa cega que usa um leitor de ecrã, um CAPTCHA visual é como pedir a alguém para ler um texto numa língua que não conhece. O leitor de ecrã não consegue "ver" as letras distorcidas ou números numa imagem.

**Exemplo problemático:**
```html
<img src="captcha-image.jpg" alt="Digite o código que vê na imagem">
```

**O que está mal:** O leitor de ecrã apenas lê "Digite o código que vê na imagem", mas não consegue dizer qual é o código, tornando impossível para uma pessoa cega completar a tarefa.

#### Pessoas com Deficiência Auditiva

Os CAPTCHAs áudio podem ser igualmente inacessíveis para pessoas surdas ou com problemas de audição, especialmente quando não há legendas ou transcrições disponíveis.

#### Pessoas com Deficiência Motora

Pessoas com dificuldades motoras podem ter problemas em:

- Clicar em partes específicas de imagens (como semáforos ou carros)
- Arrastar elementos para resolver puzzles
- Completar tarefas dentro de limites de tempo

#### Pessoas com Deficiência Cognitiva

CAPTCHAs complexos podem ser particularmente desafiantes para pessoas com:

- Dislexia (dificuldade em reconhecer letras distorcidas)
- Problemas de memória (esquecimento do código enquanto o digitam)
- Dificuldades de processamento (confusão com instruções complexas)

### Requisitos de Acessibilidade para CAPTCHAs

Os CAPTCHAs devem seguir o princípio de que **toda a funcionalidade deve ter pelo menos duas formas alternativas de acesso**. É como ter várias chaves para a mesma porta - se uma não funciona, há sempre outra opção.

#### Requisitos Principais:

1. **Múltiplas modalidades:** Oferecer alternativas visuais, auditivas e táteis
2. **Instruções claras:** Explicar exatamente o que é esperado
3. **Tempo suficiente:** Não impor limites de tempo rígidos
4. **Alternativas equivalentes:** As opções alternativas devem ter o mesmo nível de segurança

## Técnicas de Codificação

### CAPTCHA com Alternativas Múltiplas

**Exemplo de implementação acessível:**

```html
<div class="captcha-container">
  <h3>Verificação de Segurança</h3>
  <p>Para sua segurança, precisa de completar uma das seguintes verificações:</p>
  
  <!-- Opção Visual -->
  <div class="captcha-option">
    <label for="visual-captcha">
      <input type="radio" name="captcha-type" id="visual-captcha" value="visual">
      Resolver puzzle visual
    </label>
    <div id="visual-captcha-content" class="captcha-content" hidden>
      <img src="captcha.jpg" alt="Imagem de verificação">
      <label for="visual-input">Digite o código da imagem:</label>
      <input type="text" id="visual-input" name="visual-code">
    </div>
  </div>
  
  <!-- Opção Áudio -->
  <div class="captcha-option">
    <label for="audio-captcha">
      <input type="radio" name="captcha-type" id="audio-captcha" value="audio">
      Ouvir código de áudio
    </label>
    <div id="audio-captcha-content" class="captcha-content" hidden>
      <audio controls>
        <source src="captcha-audio.mp3" type="audio/mpeg">
      </audio>
      <label for="audio-input">Digite o código que ouviu:</label>
      <input type="text" id="audio-input" name="audio-code">
    </div>
  </div>
  
  <!-- Opção Alternativa Simples -->
  <div class="captcha-option">
    <label for="math-captcha">
      <input type="radio" name="captcha-type" id="math-captcha" value="math">
      Resolver questão simples
    </label>
    <div id="math-captcha-content" class="captcha-content" hidden>
      <p>Quanto é 5 + 3?</p>
      <label for="math-input">Resposta:</label>
      <input type="text" id="math-input" name="math-answer">
    </div>
  </div>
</div>
```

**O que funciona bem neste exemplo:**

- Oferece três alternativas diferentes
- Usa labels claros e descritivos
- Permite ao utilizador escolher o método preferido
- Inclui instruções específicas para cada tipo

### CAPTCHA Alternativo Baseado em Lógica

**Exemplo de pergunta lógica simples:**

```html
<div class="logical-captcha">
  <label for="logic-question">
    Qual é a cor do céu num dia limpo?
    <small>(Esta pergunta ajuda-nos a verificar que é uma pessoa real)</small>
  </label>
  <select id="logic-question" name="sky-color" required>
    <option value="">Escolha uma opção</option>
    <option value="azul">Azul</option>
    <option value="verde">Verde</option>
    <option value="roxo">Roxo</option>
    <option value="laranja">Laranja</option>
  </select>
</div>
```

**O que funciona bem:**

- Pergunta simples que qualquer pessoa pode responder
- Oferece opções claras
- Inclui explicação do propósito
- Acessível a leitores de ecrã

### Implementação com reCAPTCHA Acessível

```html
<div class="recaptcha-container">
  <div class="g-recaptcha" 
       data-sitekey="your-site-key"
       data-callback="recaptchaCallback"
       data-expired-callback="recaptchaExpired">
  </div>
  
  <!-- Alternativa para quem não consegue usar reCAPTCHA -->
  <div class="alternative-verification">
    <p>Problemas com a verificação acima? 
       <button type="button" onclick="showAlternative()">
         Use método alternativo
       </button>
    </p>
    
    <div id="alternative-method" hidden>
      <label for="email-verification">
        Digite o seu endereço de email para verificação manual:
      </label>
      <input type="email" id="email-verification" name="email-verify">
      <p><small>Enviaremos um código de verificação que deve introduzir na próxima página.</small></p>
    </div>
  </div>
</div>
```

## Recomendações para Conteúdo Acessível

### Melhores Práticas

#### 1. Oferecer Sempre Alternativas

Pense nos CAPTCHAs como uma receita de cozinha - se alguém for alérgico a um ingrediente, deve haver sempre uma substituição possível.

**Boa prática:**
```html
<div class="captcha-alternatives">
  <p>Escolha o método de verificação que prefere:</p>
  <ul>
    <li><button onclick="showVisualCaptcha()">Puzzle visual</button></li>
    <li><button onclick="showAudioCaptcha()">Código de áudio</button></li>
    <li><button onclick="showTextCaptcha()">Pergunta de texto</button></li>
  </ul>
</div>
```

#### 2. Instruções Claras e Específicas

**Exemplo de instruções vagas (problemático):**
```html
<p>Complete a verificação abaixo</p>
```

**Exemplo de instruções claras (correto):**
```html
<p>Para continuar, digite os 5 caracteres que vê na imagem abaixo. 
   Se não conseguir ver a imagem, clique no botão "Ouvir código" 
   para uma alternativa de áudio.</p>
```

#### 3. Tempo Adequado

```javascript
// Dar tempo suficiente e avisar antes de expirar
let timeRemaining = 300; // 5 minutos

function updateTimer() {
  if (timeRemaining === 60) {
    alert('Atenção: Tem 1 minuto para completar a verificação. ' +
          'Se precisar de mais tempo, recarregue a página.');
  }
  
  if (timeRemaining <= 0) {
    showRefreshOption();
  }
  
  timeRemaining--;
}
```

### Erros Comuns

#### Erro 1: Apenas uma Modalidade

**Problemático:**
```html
<!-- Só oferece opção visual -->
<img src="captcha.jpg" alt="Código de verificação">
<input type="text" placeholder="Digite o código">
```

**Por que está mal:** Exclui completamente pessoas cegas ou com baixa visão.

#### Erro 2: CAPTCHAs Áudio Inacessíveis

**Problemático:**
```html
<audio src="captcha.mp3" autoplay></audio>
<p>Digite o que ouviu</p>
```

**Problemas:**

- Autoplay pode assustar utilizadores
- Sem controlos de volume
- Sem transcrição para pessoas surdas
- Sem possibilidade de repetir

**Versão melhorada:**
```html
<div class="audio-captcha">
  <audio controls>
    <source src="captcha.mp3" type="audio/mpeg">
    <source src="captcha.wav" type="audio/wav">
    O seu navegador não suporta áudio.
  </audio>
  <button onclick="playAudio()">Repetir áudio</button>
  <button onclick="showTextAlternative()">Usar alternativa de texto</button>
  <label for="audio-response">Digite o código que ouviu:</label>
  <input type="text" id="audio-response" name="audio-code">
</div>
```

#### Erro 3: CAPTCHAs de Imagem Complexos

**Problemático:**
```html
<p>Clique em todas as imagens que contêm semáforos</p>
<div class="image-grid">
  <!-- 16 imagens pequenas sem texto alternativo -->
</div>
```

**Problemas:**

- Impossível para pessoas cegas
- Difícil para pessoas com problemas motores
- Confuso para pessoas com dificuldades cognitivas

#### Erro 4: Sem Opção de Atualizar

**Problemático:**
```html
<!-- CAPTCHA sem possibilidade de obter novo código -->
<img src="static-captcha.jpg" alt="Código de verificação">
```

**Versão melhorada:**
```html
<div class="captcha-refresh">
  <img id="captcha-image" src="captcha.jpg" alt="Código de verificação">
  <button onclick="refreshCaptcha()" type="button">
    Obter novo código
  </button>
  <button onclick="showAudioAlternative()" type="button">
    Ouvir código
  </button>
</div>
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

Os CAPTCHAs acessíveis são como pontes que permitem a todos atravessar, não muros que bloqueiam algumas pessoas. Os pontos fundamentais são:

1. **Múltiplas opções:** Oferecer sempre pelo menos duas formas diferentes de verificação
2. **Instruções claras:** Explicar exatamente o que é esperado
3. **Tempo adequado:** Não pressionar com limites de tempo rígidos
4. **Alternativas equivalentes:** Todas as opções devem ser igualmente válidas
5. **Feedback útil:** Informar claramente sobre erros e como os corrigir

### Exercícios Práticos

#### Exercício 1: Identificar Problemas

Analise este código e identifique pelo menos 3 problemas de acessibilidade:

```html
<div>
  <img src="captcha123.jpg">
  <input type="text" placeholder="Código">
  <button>Submeter</button>
</div>
```

**Problemas a identificar:**

- Falta de texto alternativo na imagem
- Ausência de labels para o campo de entrada
- Não há alternativas para pessoas que não conseguem ver a imagem
- Falta de instruções claras

#### Exercício 2: Melhorar um CAPTCHA

Reescreva o código do exercício anterior para o tornar acessível:

```html
<!-- A sua resposta aqui -->
```

#### Exercício 3: Criar Alternativas

Desenhe um sistema de CAPTCHA que ofereça três métodos diferentes de verificação para o mesmo nível de segurança. Considere as necessidades de pessoas com diferentes tipos de deficiência.

#### Exercício 4: Análise de Caso Real

Visite 3 websites que usam CAPTCHAs e teste-os com um leitor de ecrã. Documente:

1. Que tipos de CAPTCHA encontrou?
2. Quais ofereciam alternativas?
3. Que melhorias sugeriria?

#### Exercício 5: Pergunta de Reflexão

Uma empresa argumenta que não pode oferecer alternativas aos seus CAPTCHAs visuais porque isso compromete a segurança. Como responderia a esta preocupação, oferecendo soluções práticas que mantêm tanto a segurança quanto a acessibilidade?

**Pontos para considerar na resposta:**

- Segurança através de diversidade de métodos
- Exemplos de alternativas igualmente seguras
- Benefícios para todos os utilizadores
- Requisitos legais e éticos

Lembre-se: um website verdadeiramente seguro é aquele que protege contra ataques automáticos sem excluir utilizadores humanos legítimos, independentemente das suas capacidades.



# Conclusão e Boas Práticas

## Recapitulação

Chegámos ao final da nossa jornada pelo mundo da acessibilidade em imagens! Vamos fazer uma viagem rápida pelos conceitos principais que aprendemos.

### O Que Aprendemos

**Imaginem uma biblioteca onde alguns livros estão escritos numa língua que nem todos conseguem ler.** As imagens na web podem ser exatamente isso para pessoas com deficiência visual. O nosso trabalho é ser "tradutores" dessas imagens, tornando-as acessíveis a todos.

#### Tipos de Imagens e as Suas "Traduções"

**1. Imagens Informativas**

- **O que são:** Imagens que transmitem informação importante, como fotografias de produtos ou diagramas.
- **Como torná-las acessíveis:** Usar texto alternativo (atributo `alt`) que descreva claramente o conteúdo.
- **Analogia:** É como legendar um filme - contamos o que está a acontecer para quem não consegue ver.

**2. Imagens Decorativas**

- **O que são:** Imagens que só servem para embelezar a página, sem adicionar informação.
- **Como torná-las acessíveis:** Usar `alt=""` (vazio) para que os leitores de ecrã as ignorem.
- **Analogia:** São como molduras de quadros - bonitas, mas não precisamos de as descrever para perceber a obra de arte.

**3. Imagens Funcionais**

- **O que são:** Imagens que fazem alguma coisa quando clicamos nelas, como botões ou ícones.
- **Como torná-las acessíveis:** O texto alternativo deve descrever a ação, não a aparência da imagem.
- **Analogia:** É como um sinal de trânsito - importa saber o que significa (parar, avançar), não que cor tem.

**4. Imagens Complexas**

- **O que são:** Gráficos, tabelas ou diagramas com muita informação.
- **Como torná-las acessíveis:** Combinar texto alternativo curto com descrições longas detalhadas.
- **Analogia:** É como explicar um mapa - primeiro damos a localização geral, depois os detalhes da rota.

**5. CAPTCHAs**

- **O que são:** Testes para verificar se somos humanos, muitas vezes baseados em imagens.
- **Como torná-los acessíveis:** Oferecer alternativas como áudio ou perguntas simples.
- **Analogia:** É como ter várias portas de entrada num edifício - se uma não funciona para alguém, há outras opções.

### Princípios Fundamentais

**Lembrem-se sempre destes três pilares:**

1. **Contexto é Rei:** A mesma imagem pode precisar de descrições diferentes dependendo de onde está e para que serve.

2. **Menos Pode Ser Mais:** Texto alternativo deve ser conciso mas completo. Não descrevam cores desnecessariamente ou detalhes irrelevantes.

3. **Testem Sempre:** Usem leitores de ecrã ou peçam feedback a utilizadores com deficiência.

## Exercícios de Consolidação

### Exercício 1: Diagnóstico Completo

**Cenário:** Receberam um website de uma loja online para auditar. Encontram estas imagens:

1. Logo da empresa no cabeçalho
2. Foto de um produto (ténis desportivos)
3. Ícone de carrinho de compras (clicável)
4. Imagem decorativa de fundo com padrões
5. Gráfico de vendas mensais
6. CAPTCHA para completar compra

**Tarefa:** Para cada imagem, identifiquem:

- Que tipo de imagem é
- Que abordagem de acessibilidade usar
- Escrevam o código HTML correto

### Exercício 2: Correção de Erros

**Código Problemático:**
```html
<img src="grafico-vendas.png" alt="Gráfico">
<img src="decorativo.jpg" alt="Imagem bonita">
<img src="botao-comprar.png" alt="Botão vermelho com texto">
<img src="produto-sapatos.jpg">
```

**Tarefa:** Corrijam cada linha, explicando o que estava errado e porquê.

### Exercício 3: Criação de Conteúdo

**Cenário:** Estão a criar uma página sobre mudanças climáticas com:

- Um gráfico mostrando o aumento da temperatura nos últimos 50 anos
- Fotos de glaciares a derreter
- Ícones para partilhar nas redes sociais
- Uma ilustração decorativa de folhas

**Tarefa:** Escrevam todo o HTML necessário com acessibilidade adequada.

### Exercício 4: Teste Real

**Prática:**

1. Naveguem no vosso website favorito apenas com o leitor de ecrã
2. Identifiquem três problemas de acessibilidade em imagens
3. Sugiram soluções

## Lista de Verificação Final

### Antes de Publicar Qualquer Imagem

**Perguntas Essenciais:**

- [ ] **Esta imagem transmite informação importante?**
  - Se sim → Precisa de texto alternativo descritivo
  - Se não → Pode ser decorativa (`alt=""`)

- [ ] **Esta imagem é clicável ou tem uma função?**
  - Se sim → O `alt` deve descrever a ação, não a aparência

- [ ] **Esta imagem é complexa (gráfico, diagrama, tabela)?**
  - Se sim → Precisa de descrição longa além do `alt`

- [ ] **O texto alternativo é conciso mas completo?**
  - Descreve o essencial sem redundância

- [ ] **Testei com um leitor de ecrã?**
  - A descrição faz sentido quando ouvida?
  - Não há informação em falta?

### Verificações Técnicas

**HTML e Código:**

- [ ] Todas as imagens têm atributo `alt`
- [ ] Imagens decorativas usam `alt=""`
- [ ] Imagens complexas têm `longdesc` ou descrição próxima
- [ ] CAPTCHAs têm alternativas
- [ ] Não uso "imagem de..." ou "foto de..." no início do `alt`
- [ ] Cores importantes são também indicadas por texto

**Teste de Qualidade:**

- [ ] Desliguei as imagens - o site ainda faz sentido?
- [ ] Usei apenas o teclado - consigo aceder a tudo?
- [ ] Testei com pelo menos um leitor de ecrã
- [ ] Pedi feedback a utilizadores com deficiência (se possível)

## Critérios de Sucesso WCAG Relacionados

### Nível A (Essencial)

**1.1.1 Conteúdo Não-textual**

- **O que diz:** Todo o conteúdo não-textual tem alternativa em texto
- **Na prática:** Todas as imagens informativas e funcionais têm `alt` apropriado
- **Exceções:** Testes (como CAPTCHAs) e imagens puramente decorativas

**1.4.5 Imagens de Texto**
- **O que diz:** Se possível, usar texto real em vez de imagens de texto
- **Na prática:** Evitar criar imagens só para mostrar texto estilizado
- **Quando usar imagens de texto:** Logótipos ou quando o texto é essencial para a informação

### Nível AA (Recomendado)

**1.4.3 Contraste (Mínimo)**
- **O que diz:** Contraste de pelo menos 4.5:1 para texto normal
- **Relevante para imagens:** Texto sobreposto em imagens deve ter contraste adequado

**1.4.9 Imagens de Texto (Sem Exceção)**
- **O que diz:** Não usar imagens de texto exceto para logótipos
- **Na prática:** Substituir todas as imagens de texto por texto real com CSS

### Nível AAA (Excelência)

**1.4.6 Contraste (Melhorado)**
- **O que diz:** Contraste de pelo menos 7:1
- **Para imagens:** Texto em imagens deve ter contraste ainda maior

### Critérios Relacionados

**2.4.4 Propósito do Link (em Contexto)**
- **Relevante para:** Imagens funcionais em links
- **Prática:** O `alt` deve indicar claramente para onde o link leva

**3.1.1 Idioma da Página**
- **Relevante para:** Se o texto alternativo está em idioma diferente da página
- **Prática:** Marcar mudanças de idioma no `alt` se necessário
