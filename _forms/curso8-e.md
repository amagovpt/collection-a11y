---
title: Múltiplos Passos
layout: default
nav_order: 5
---
# Múltiplos Passos

## Introdução

Alguns formulários são demasiado longos ou complexos para caberem confortavelmente num único ecrã. Pense num pedido de subsídio, na compra de um bilhete de avião ou na abertura de uma conta bancária online. Nestes casos, é frequente dividir o formulário em **várias etapas** (ou passos), apresentadas uma de cada vez.

Uma boa analogia é a de um formulário em papel com **várias folhas agrafadas**: preenche a primeira folha, vira a página, preenche a segunda, e assim sucessivamente. No papel, esta divisão é natural: sentimos a espessura do maço, vemos quantas folhas faltam e podemos folhear para trás para reler o que escrevemos. Num ecrã, nada disto acontece de forma automática. Se não o programarmos com cuidado, a pessoa fica sem saber em que passo está, quantos faltam, ou como voltar atrás sem perder o que já escreveu.

Esta secção trata daquilo que é **exclusivo** dos formulários com múltiplos passos: indicar o progresso, gerir o foco entre passos, preservar os dados já introduzidos, permitir rever antes de submeter e lidar com limites de tempo. 

### Como as Pessoas com Deficiência usam Formulários com Múltiplos Passos

A divisão de um formulário em etapas pode **ajudar** ou **prejudicar** muito, dependendo de como é feita. Vejamos como diferentes pessoas experienciam estes formulários.

**Pessoas cegas ou com baixa visão, que usam leitores de ecrã.** Um leitor de ecrã lê o conteúdo de cima para baixo e comunica ao utilizador aquilo que tem "foco". Quando a pessoa carrega em "Seguinte" e a página muda de passo, o leitor de ecrã **não avisa automaticamente** que houve uma mudança, a não ser que a mudança corresponda ao carregamento de uma nova página. Se o foco ficar "preso" no botão que desapareceu, a pessoa pode continuar a ouvir silêncio ou a pensar que nada aconteceu. Ela precisa de sinais claros: onde começa o novo passo, qual é o número do passo e quantos faltam.

**Pessoas com deficiência motora, que navegam só com teclado.** Estas pessoas movem-se pelo formulário com a tecla `Tab` e ativam botões com `Enter` ou `Espaço`. Um formulário longo, dividido em passos curtos, pode até ser mais confortável para elas, porque há menos campos por ecrã. Mas tudo se estraga se, ao mudar de passo, o foco saltar para um sítio inesperado (por exemplo, para o topo do menu do site), obrigando a percorrer dezenas de ligações com `Tab` até reencontrar o formulário.

**Pessoas com deficiência cognitiva ou dificuldades de atenção e memória.** São, provavelmente, quem mais beneficia da divisão em passos, desde que cada passo seja pequeno e focado numa só tarefa ("Agora só os seus dados de contacto"). Ao mesmo tempo, são também quem mais sofre quando o formulário perde os dados a meio, quando não é possível voltar atrás para confirmar algo, ou quando a pessoa não faz ideia de quanto ainda falta. A incerteza ("será que estou quase a acabar?") gera ansiedade e leva ao abandono.

**Pessoas com pouca destreza ou que preenchem devagar.** Quem escreve lentamente — por usar um teclado adaptado, comando de voz ou por qualquer outra razão — corre o risco de **esgotar o tempo da sessão** a meio de um formulário longo, perdendo tudo o que já tinha introduzido.

> **Analogia — o formulário como uma viagem de comboio.** Um formulário de vários passos é como uma viagem com transbordos. O passageiro precisa de saber três coisas: **em que estação está** (passo atual), **quantas estações faltam** (progresso) e **como voltar à estação anterior** se se enganou (navegação para trás). Sem esta informação, mesmo um passageiro experiente sente-se perdido; para quem depende de um leitor de ecrã, é como viajar sem qualquer anúncio de paragens.

### Requisitos de Acessibilidade para Formulários com Múltiplos Passos

Para que um formulário de vários passos seja acessível, deve cumprir um conjunto de requisitos próprios desta estrutura:

1. **Indicar o progresso de forma percetível.** A pessoa deve conseguir saber, a qualquer momento, em que passo está e quantos passos existem no total — e essa informação não pode depender apenas da cor ou da posição visual.

2. **Gerir o foco a cada mudança de passo.** Quando um novo passo aparece, o foco do teclado deve ser deslocado para um ponto lógico do novo passo (habitualmente o seu título), para que utilizadores de teclado e de leitor de ecrã percebam que avançaram.

3. **Anunciar a mudança a tecnologias de apoio.** A transição de passo deve ser comunicada aos leitores de ecrã, seja através da deslocação do foco para um título, seja através de uma mensagem de estado.

4. **Preservar os dados entre passos.** Voltar atrás não pode apagar o que já foi preenchido. Igualmente, a informação já dada num passo não deve ter de ser reintroduzida noutro.

5. **Permitir rever e corrigir antes de submeter.** Em formulários que envolvem compromissos legais, transações financeiras ou dados que não podem ser facilmente apagados, é necessário oferecer um passo de revisão, ou uma forma de confirmar e corrigir antes da submissão final.

6. **Respeitar o tempo do utilizador.** Se existir um limite de tempo de sessão, é preciso avisar com antecedência e permitir prolongá-lo, evitando a perda dos dados já introduzidos.

7. **Manter uma ordem e navegação previsíveis.** Os botões de avançar e recuar devem estar sempre no mesmo sítio e comportar-se de forma consistente em todos os passos.

## Técnicas de Codificação

Nesta secção mostramos padrões de código focados no que distingue os formulários de vários passos. Os campos, rótulos e mensagens de erro seguem as técnicas das secções respetivas; aqui interessa-nos a **moldura** que os envolve.

### Indicador de progresso (o "stepper")

O indicador de progresso deve comunicar a mesma informação a quem vê e a quem não vê. Uma técnica simples e robusta é usar uma lista com o passo atual marcado por `aria-current="step"`.

```html
<nav aria-label="Progresso do formulário">
  <ol class="passos">
    <li>
      <span class="visualmente-oculto">Concluído:</span> 1. Dados pessoais
    </li>
    <li aria-current="step">
      <span class="visualmente-oculto">Passo atual:</span> 2. Morada
    </li>
    <li>3. Pagamento</li>
    <li>4. Confirmação</li>
  </ol>
</nav>
```

**O que funciona bem neste exemplo**: o elemento `<nav>` com `aria-label` agrupa e nomeia a área de progresso, o `<ol>` transmite que há uma sequência ordenada e o `aria-current="step"` faz o leitor de ecrã anunciar "passo atual" ao chegar ao item 2. Além disso, a lista existe **como texto**, por isso funciona mesmo que a cor ou os ícones não sejam percetíveis. A classe `visualmente-oculto` (texto que só é lido por tecnologias de apoio) reforça o significado sem sobrecarregar visualmente o ecrã.

**O que correria mal**: se o progresso fosse desenhado apenas com círculos coloridos e uma linha, sem qualquer texto, uma pessoa com um leitor de ecrã não saberia sequer que existe um indicador de progresso, e uma pessoa daltónica poderia não distinguir o passo "feito" do passo "por fazer".

### Anunciar o número do passo

Além do indicador visual, é boa prática dar a cada passo um **título claro que inclua a sua posição na sequência**. Este título servirá também para gerir o foco (ver adiante).

```html
<h2 id="titulo-passo" tabindex="-1">Passo 2 de 4: Morada</h2>
```

**O que funciona bem**: o texto "Passo 2 de 4" dá, numa só frase, a posição e o total. O `tabindex="-1"` permite que o título receba foco por programação (sem entrar na ordem normal de tabulação), o que é essencial para a gestão de foco descrita a seguir.

### Gerir o foco na mudança de passo

Este é o ponto mais crítico e mais esquecido. Quando a pessoa avança de passo, devemos mover o foco para o título do novo passo. Assim, o leitor de ecrã lê imediatamente "Passo 3 de 4: Pagamento" e o utilizador de teclado começa no sítio certo.

```html
<button type="button" id="btn-seguinte">Seguinte</button>

<script>
  document.getElementById('btn-seguinte').addEventListener('click', function () {
    mostrarPasso(3); // função que troca o conteúdo visível

    // Depois de o novo passo estar no ecrã, colocar o foco no seu título:
    var titulo = document.getElementById('titulo-passo');
    titulo.focus();
  });
</script>
```

**O que funciona bem**: ao dar `focus()` ao título, garantimos que utilizadores de teclado e de leitor de ecrã "aterram" no início do novo passo, sem terem de o procurar. É o equivalente digital de um guia turístico que, ao entrar numa nova sala, nos diz "estamos agora na Sala 3, dedicada a...".

**O que correria mal**: **não fazer nada** com o foco. Nesse caso, o foco pode ficar no botão "Seguinte" — que muitas vezes já nem existe no novo passo — ou saltar para o topo do documento. O utilizador de leitor de ecrã ouve silêncio e pensa que a ação falhou, ou tem de "explorar" a página para perceber o que mudou.

### Não perder dados ao recuar (e não repetir perguntas)

Voltar atrás para corrigir uma resposta não pode apagar tudo o resto. Numa aplicação que troca de passo sem recarregar a página, isto consegue-se guardando os valores em memória e voltando a preenchê-los.

```html
<script>
  // Objeto que guarda o que já foi preenchido
  var dadosFormulario = {};

  // Antes de trocar de passo, guardar o que a pessoa escreveu
  function guardarPassoAtual(passo) {
    document.querySelectorAll('#' + passo + ' input, #' + passo + ' select')
      .forEach(function (campo) {
        dadosFormulario[campo.name] = campo.value;
      });
  }

  // Ao mostrar um passo, repor os valores guardados
  function reporValores(passo) {
    document.querySelectorAll('#' + passo + ' input, #' + passo + ' select')
      .forEach(function (campo) {
        if (dadosFormulario[campo.name] !== undefined) {
          campo.value = dadosFormulario[campo.name];
        }
      });
  }
</script>
```

**O que funciona bem**: quando a pessoa recua e volta a avançar, encontra tudo tal como o deixou. Este mesmo princípio evita a **reintrodução redundante**: se o campo "nome" já foi preenchido no passo 1, não deve voltar a ser pedido no passo 3. Quando é mesmo necessário reutilizar um valor (por exemplo, "a morada de faturação é a mesma da entrega?"), ofereça uma caixa de verificação que copie o valor automaticamente, em vez de obrigar a escrever tudo de novo.

**O que correria mal**: reconstruir o passo do zero de cada vez, deixando os campos vazios. A pessoa carrega em "Anterior" só para confirmar uma coisa e, ao voltar, descobre que perdeu meia hora de trabalho. Para quem tem dificuldades de memória ou de destreza, isto é motivo suficiente para desistir.

### Passo de revisão antes de submeter

Em formulários com consequências sérias (pagamentos, candidaturas, alterações de dados), acrescente um passo final onde tudo é apresentado para revisão, com ligações que permitem voltar a cada secção para corrigir.

```html
<h2 tabindex="-1">Passo 4 de 4: Confirme os seus dados</h2>

<h3>Dados pessoais <a href="#passo1">Editar</a></h3>
<p>Nome: Maria Silva</p>
<p>E-mail: maria.silva@exemplo.pt</p>

<h3>Morada <a href="#passo2">Editar</a></h3>
<p>Rua das Flores, 12, 1000-001 Lisboa</p>

<button type="submit">Confirmar e submeter</button>
```

**O que funciona bem**: a pessoa vê tudo reunido antes do passo irreversível e cada bloco tem uma ligação "Editar" que a leva ao passo certo — sem perder os restantes dados. A submissão só acontece quando ela carrega, conscientemente, em "Confirmar e submeter".

**O que correria mal**: submeter automaticamente ao chegar ao último campo, sem qualquer confirmação. Um clique acidental, ou um comando de voz mal interpretado, poderia concluir uma compra ou uma candidatura sem que a pessoa tivesse tido oportunidade de rever.

### Avisar antes de a sessão terminar

Se o formulário tem um limite de tempo (por segurança ou por regra do sistema), avise antes de o tempo acabar e ofereça a opção de continuar.

```html
<div role="alertdialog" aria-labelledby="aviso-titulo" aria-describedby="aviso-texto">
  <h2 id="aviso-titulo">A sua sessão está prestes a expirar</h2>
  <p id="aviso-texto">
    Por inatividade, a sessão termina dentro de 2 minutos.
    Os dados já introduzidos serão guardados.
  </p>
  <button type="button">Continuar a preencher</button>
</div>
```

**O que funciona bem**: o `role="alertdialog"` faz o leitor de ecrã anunciar o aviso de imediato e leva o foco para dentro da caixa, para que qualquer pessoa possa reagir a tempo. A mensagem indica claramente quanto tempo resta e tranquiliza sobre a preservação dos dados.

**O que correria mal**: terminar a sessão sem aviso e sem guardar nada. Uma pessoa que escreve devagar veria o seu trabalho desaparecer, muitas vezes sem sequer perceber porquê.

## Recomendações para Conteúdo Acessível

Além do código, o conteúdo e o desenho dos passos fazem toda a diferença:

- **Um passo, uma ideia.** Agrupe campos relacionados e dê a cada passo um objetivo único e claro no título ("Dados de contacto", "Método de pagamento"). Passos curtos e temáticos são mais fáceis de compreender e de completar.

- **Diga sempre onde a pessoa está e quanto falta.** "Passo 2 de 4" vale mais do que uma barra colorida sem números. Se o número total de passos for incerto, seja honesto ("Passo 2 — faltam ainda os dados de pagamento").

- **Valide cada passo no momento certo.** Verificar os campos ao concluir cada passo evita que a pessoa chegue ao fim e seja "atirada" de volta ao início. 

- **Botões consistentes e bem nomeados.** "Anterior" e "Seguinte" devem estar sempre no mesmo sítio. No último passo, o botão de avançar deve mudar para algo explícito como "Confirmar e submeter", para que ninguém submeta sem querer.

- **Permita guardar e continuar mais tarde**, sempre que o formulário for longo. É a rede de segurança para quem é interrompido ou preenche em várias sessões.

- **Deixe recuar sem penalização.** Voltar atrás deve ser tão fácil e seguro como avançar.

### Erros Comuns

- **Não gerir o foco.** O erro mais frequente: mudar de passo e deixar o foco no vazio. Utilizadores de leitor de ecrã não percebem que avançaram.
- **Indicar o progresso só com cor ou ícones.** Sem texto ("Passo 2 de 4"), a informação é inacessível a quem não vê o ecrã ou não distingue cores.
- **Apagar dados ao recuar.** Punir quem volta atrás para confirmar algo é uma das causas mais comuns de abandono.
- **Pedir a mesma informação em vários passos.** Reintroduzir dados já dados é desnecessário e cansativo; deve evitar-se sempre que possível.
- **Submeter sem revisão nem confirmação** em formulários com consequências sérias.
- **Terminar a sessão sem aviso**, perdendo tudo o que já tinha sido preenchido.
- **Mudar os botões de sítio entre passos**, obrigando a pessoa a reorientar-se a cada etapa.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Dividir um formulário longo em passos **ajuda** a compreensão, mas só se a pessoa souber sempre onde está, quanto falta e como voltar atrás.
- O **indicador de progresso** deve ser textual e percetível a todos, não apenas visual (`aria-current="step"`, "Passo X de Y").
- A **gestão do foco** a cada mudança de passo é indispensável: mover o foco para o título do novo passo é a técnica mais fiável.
- **Preservar os dados** entre passos e **não repetir perguntas** respeita o tempo e o esforço do utilizador.
- Formulários com consequências sérias precisam de um **passo de revisão** e de confirmação explícita antes da submissão.
- **Limites de tempo** exigem aviso antecipado, opção de continuar e preservação dos dados.

### Exercícios Práticos

1. **Detetar problemas de foco.** Abra um formulário de vários passos (por exemplo, um processo de compra). Preencha o primeiro passo apenas com o teclado e carregue em "Seguinte". Sem tocar no rato, verifique: onde ficou o foco? Se possível, repita com um leitor de ecrã ativo e anote se a mudança de passo foi anunciada.

2. **Testar a preservação de dados.** Preencha até ao terceiro passo de um formulário, carregue em "Anterior" duas vezes e volte a avançar. Os seus dados mantiveram-se? Descreva o que aconteceu e o impacto que isso teria numa pessoa com dificuldades de memória.

3. **Escrever um indicador de progresso acessível.** Crie o HTML de um indicador de progresso de 3 passos, em que o passo 2 é o atual. Use `aria-current` e inclua texto que identifique a posição e o total. Explique, em duas frases, porque é que a sua solução funciona também para quem não vê o ecrã.

4. **Desenhar um passo de revisão.** Para um formulário de candidatura com três secções (dados pessoais, formação, motivação), esboce o ecrã de revisão final. Indique onde colocaria as ligações "Editar" e como garantiria que ninguém submete sem confirmar.

5. **Analisar um caso real.** Escolha um serviço público ou uma loja online com formulário de vários passos. Preencha-o e avalie-o face aos sete requisitos desta lição (progresso, foco, anúncio, preservação de dados, revisão, tempo e navegação consistente). Identifique um ponto forte e o problema mais grave que encontrou.

