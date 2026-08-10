# Conclusão e Boas Práticas

## Recapitulação

Este módulo percorreu um caminho que começou numa pergunta simples — *o que é, afinal, um widget?* — e terminou em interfaces com dezenas de peças a funcionar em conjunto.

Vale a pena olhar para trás e ver o percurso como um todo, porque é aí que as sete secções anteriores deixam de parecer sete assuntos separados e passam a parecer aquilo que realmente são: **sete perguntas sobre o mesmo objeto**.

### As sete perguntas

> **Analogia: a entrevista ao widget**
>
> Imagine que uma tecnologia de apoio — um leitor de ecrã, um software de comando por voz, um teclado adaptado — pode fazer perguntas ao seu widget, como quem entrevista alguém à porta de um edifício.
>
> Se o widget souber responder às sete perguntas, entra toda a gente. Se falhar uma, há sempre alguém que fica de fora, e normalmente é sempre o mesmo grupo de pessoas.

| # | Pergunta da tecnologia de apoio | Secção que a responde |
|---|---|---|
| 1 | **O que és e como te chamas?** | *Widgets* |
| 2 | **Como estás agora?** | *Propriedades, Estados e Valores de Widgets* |
| 3 | **Consigo chegar a ti e usar-te só com teclas?** | *Interações por Teclado e Foco* |
| 4 | **Consigo acertar-te e ativar-te com um dedo ou um apontador impreciso?** | *Interações por Rato e Toque* |
| 5 | **Se eu disser o teu nome em voz alta, respondes?** | *Interações por Fala* |
| 6 | **Se algo mudar longe de mim, avisas-me?** | *Regiões Dinâmicas* |
| 7 | **Sabes comportar-te quando estás acompanhado?** | *Widgets Complexos* |

**O que isto mostra:** as sete perguntas são **cumulativas, não alternativas**. Um menu que responde bem às perguntas 1, 2, 3 e 6 mas falha a 4 é um menu que exclui quem usa o telemóvel com tremor nas mãos. Não há uma pergunta «mais importante». Há uma pessoa diferente por trás de cada uma.

### Quatro pessoas, um só widget

Para fixar a recapitulação, vamos seguir **um único componente**, o seletor de quantidade de um formulário de marcação de consultas de um centro de saúde, pelos olhos de quatro pessoas fictícias.

O componente é este: um botão «−», um campo com um número, e um botão «+».

```html
<div class="quantidade">
  <button type="button" aria-label="Diminuir número de acompanhantes">−</button>
  <input
    type="text"
    inputmode="numeric"
    id="acompanhantes"
    value="1"
    aria-describedby="acompanhantes-ajuda">
  <button type="button" aria-label="Aumentar número de acompanhantes">+</button>
</div>
<p id="acompanhantes-ajuda">Máximo de 3 acompanhantes por consulta.</p>

<p aria-live="polite" id="acompanhantes-estado">1 acompanhante selecionado.</p>
```

- **A Teresa** é cega e usa leitor de ecrã. Ouve *«Diminuir número de acompanhantes, botão»* — sabe **o que é** e **o que faz** (secção *Widgets*). Ao carregar em «+», ouve a região dinâmica anunciar *«2 acompanhantes selecionados»* sem que o foco salte para lado nenhum (secção *Regiões Dinâmicas*).
- **O Miguel** tem tetraplegia e navega só com teclado. Chega aos três elementos com `Tab`, vê um contorno de foco espesso à volta de cada um e ativa os botões com `Enter` ou `Espaço` (secção *Interações por Teclado e Foco*).
- **A Fátima** tem 78 anos, tremor essencial e usa o telemóvel. Os botões têm 44 × 44 pixéis CSS, estão afastados um do outro e só disparam quando levanta o dedo. Se acertar no botão errado, arrasta o dedo para fora e nada acontece (secção *Interações por Rato e Toque*).
- **O Rui** tem uma lesão por esforço repetitivo e comanda o computador por voz. Diz *«clicar aumentar»* — e funciona, porque o nome acessível começa pelo texto que ele vê... **ou não vê**.

**O que funciona bem e o que falha:** as três primeiras pessoas conseguem usar este componente. O Rui não. O botão mostra o símbolo «+», mas o nome acessível é «Aumentar número de acompanhantes» — não há qualquer palavra visível que corresponda ao nome (secção *Interações por Fala*). Além disso, o campo é um `<input type="text">` sem função declarada de *spinbutton* e sem `aria-valuenow`: a Teresa ouve o número quando lá chega, mas não ouve os limites de 1 a 3 (secção *Propriedades, Estados e Valores de Widgets*).

Um componente com três elementos e quatro pessoas: **duas falhas**. Esta é, em resumo, a razão de ser deste módulo: os widgets falham raramente por ignorância grosseira e quase sempre por uma pergunta que ninguém se lembrou de fazer.

### Os três princípios transversais

Se tudo o resto se apagar da memória, que fiquem estes três:

1. **O elemento nativo primeiro.** `<button>`, `<input>`, `<select>`, `<details>` e `<dialog>` trazem função, foco, teclado e estados de graça. Recriar isso com `<div>` e ARIA é trabalho a mais para um resultado, no melhor dos casos, igual.
2. **ARIA não faz nada — só diz.** `role="checkbox"` não torna nada clicável; `aria-expanded="true"` não abre nada. ARIA descreve o que o código já faz. Se o comportamento não estiver lá, o ARIA está a mentir. E uma mentira é pior do que o silêncio.
3. **Testar com pessoas e com teclas, não só com ferramentas.** Nenhum validador automático deteta um `aria-checked` que nunca é atualizado, uma armadilha de foco num diálogo ou um nome acessível que ninguém consegue pronunciar.

---

## Recursos Adicionais

### Especificações e referência técnica

| Recurso | O que é e quando usar |
|---|---|
| **[WAI-ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/)** | O recurso mais útil do conjunto. Para cada padrão (menu, separadores, grelha, combobox, árvore) indica funções, atributos e teclado esperado, com exemplos funcionais. Consultar **antes** de escrever qualquer widget personalizado. |
| **[Accessible Rich Internet Applications (WAI-ARIA)](https://www.w3.org/TR/wai-aria/)** | A especificação. Consultar para saber que atributos são permitidos numa função e que valores aceitam. |
| **[ARIA in HTML](https://www.w3.org/TR/html-aria/)** | Diz que funções e atributos ARIA são válidos em cada elemento HTML. Útil para não colar `role="button"` onde não deve. |
| **[HTML Accessibility API Mappings](https://www.w3.org/TR/html-aam/)** | Mostra o que cada elemento HTML já expõe nativamente. Bom antídoto contra ARIA desnecessário. |
| **[MDN — ARIA](https://developer.mozilla.org/pt-BR/docs/Web/Accessibility/ARIA)** | Documentação prática, com notas de suporte real nos navegadores. |

### Ferramentas de teste

| Ferramenta | Para que serve neste módulo |
|---|---|
| **NVDA** (Windows) + **VoiceOver** (macOS/iOS) + **TalkBack** (Android) | Ouvir o que o widget declara. Sem isto, está a programar às cegas — literalmente. |
| **Inspetor de acessibilidade** dos navegadores (separador *Accessibility* nas ferramentas de programação) | Ver a árvore de acessibilidade: nome, função, estado e valor calculados. A forma mais rápida de confirmar que o ARIA está a fazer o que julga. |
| **axe DevTools**, **WAVE**, **AccessMonitor** | Apanhar erros estruturais e ARIA inválida. Ponto de partida, nunca de chegada. |
| **Só o teclado** (desligue o rato) | O teste mais barato e mais revelador de todos. |
| **Comando por voz** (Voice Control no macOS/iOS, Voice Access no Android, Dragon) | Confirmar a correspondência entre etiqueta visível e nome acessível. |

---

## Exercícios de Consolidação

### Exercício 1 — A auditoria das sete perguntas

Escolha um widget interativo de um sítio real (um menu, um acordeão, um seletor de datas, um carrossel). Preencha esta grelha:

| Pergunta | Como testou | Resultado | Secção envolvida |
|---|---|---|---|
| Função e nome corretos? | | | *Widgets* |
| Estado e valor comunicados e **atualizados**? | | | *Propriedades, Estados e Valores* |
| Alcançável e operável só por teclado, com foco visível? | | | *Teclado e Foco* |
| Alvo suficiente, ativação no levantar, sem gesto obrigatório? | | | *Rato e Toque* |
| Etiqueta visível contida no nome acessível? | | | *Fala* |
| Mudanças fora do foco anunciadas sem interromper? | | | *Regiões Dinâmicas* |
| Padrão composto coerente com o APG? | | | *Widgets Complexos* |

**Entrega:** a grelha preenchida e, para cada falha, uma frase a dizer **quem** fica excluído.

### Exercício 2 — Corrigir o seletor de quantidade

Retome o código do seletor de acompanhantes apresentado na recapitulação. Corrija as duas falhas identificadas (nome acessível sem correspondência visível; campo sem função nem valores) e acrescente o comportamento de teclado adequado. Justifique cada alteração com a secção correspondente.

**Pista:** o APG tem um padrão chamado *spinbutton*. Mas há uma solução ainda mais simples — e a pergunta certa a fazer é: *«preciso mesmo de um widget personalizado?»*

### Exercício 3 — O código que mente

Encontre (ou construa) um exemplo de ARIA que mente: um `aria-expanded` que nunca muda, um `role="button"` sem gestor de teclado, um `aria-live` numa região que já existia escondida. Documente:

1. O que o código **diz** que acontece.
2. O que **acontece** de facto.
3. O que ouve quem usa leitor de ecrã.
4. A correção mínima.

### Exercício 4 — Nativo contra personalizado

Pegue num widget personalizado da sua organização. Escreva duas colunas: **o que o elemento nativo equivalente daria de graça** e **o que teve de ser programado à mão**. Depois responda: a razão original para não usar o nativo ainda se justifica?

### Exercício 5 — A revisão cruzada

Em pares. Cada pessoa entrega o widget que corrigiu no Exercício 2 ao colega. O colega testa **sem ver o código**, apenas com teclado e leitor de ecrã, e escreve o que percebeu do componente. Comparem com a intenção original.

**Objetivo:** perceber que a acessibilidade não é o que escrevemos — é o que chega ao outro lado.

---

## Lista de Verificação Final

Uma lista para usar em revisão de código ou antes de colocar um componente em produção. 

### Identidade — função e nome

- [ ] Foi usado o **elemento HTML nativo** sempre que existia um equivalente.
- [ ] Todo o elemento interativo tem uma **função** determinável (nativa ou via `role`).
- [ ] Todo o elemento interativo tem um **nome acessível** não vazio e descritivo.
- [ ] Não há funções aninhadas de forma inválida nem `role` a substituir semântica nativa sem motivo.
- [ ] Ícones sem texto têm nome acessível; imagens decorativas dentro de controlos estão ocultas às tecnologias de apoio.

### Estado, propriedade e valor

- [ ] Estados (`aria-expanded`, `aria-checked`, `aria-selected`, `aria-pressed`, `aria-disabled`, `aria-current`) refletem a realidade **no momento** e são **atualizados por JavaScript** a cada mudança.
- [ ] Valores em intervalos têm `aria-valuenow`, `aria-valuemin`, `aria-valuemax` — e `aria-valuetext` quando o número não é autoexplicativo.
- [ ] Relações estruturais (`aria-controls`, `aria-owns`, `aria-describedby`, `aria-labelledby`) apontam para `id` que existem.
- [ ] O estado **nunca** é comunicado só por cor ou só por posição.

### Teclado e foco

- [ ] Tudo o que se faz com rato faz-se com teclado.
- [ ] A ordem de tabulação corresponde à ordem visual e lógica.
- [ ] O foco é **sempre visível**, com contraste suficiente contra o fundo adjacente.
- [ ] Não existem armadilhas de foco: entra-se e sai-se de qualquer componente.
- [ ] Widgets compostos usam foco gerido (`tabindex="-1"` nos itens, setas para navegar) em vez de encher a tabulação.
- [ ] `Esc` fecha o que abriu, e o foco regressa ao elemento que abriu.
- [ ] Não há `tabindex` positivo.
- [ ] O foco não fica escondido por cabeçalhos fixos, barras ou cookies.

### Rato, toque e apontador

- [ ] Alvos com pelo menos **24 × 24 px CSS** (recomendado: 44 × 44) ou espaçamento equivalente.
- [ ] Ativação no evento de **levantar** (`click`/`pointerup`), com possibilidade de desistir arrastando para fora.
- [ ] Gestos complexos (deslizar, pinçar, traçar caminho) têm **alternativa de apontador simples**.
- [ ] Ações dependentes de movimento do dispositivo têm alternativa e podem ser desativadas.
- [ ] Conteúdo que aparece ao passar o rato é **descartável**, **apontável** e **persistente**.

### Fala

- [ ] O **texto visível da etiqueta está contido no nome acessível**, e no início.
- [ ] `aria-label` não contradiz o texto que a pessoa vê no ecrã.
- [ ] Controlos de ícone têm um nome pronunciável — não «botão 3» nem símbolos.

### Regiões dinâmicas

- [ ] Mudanças que ocorrem **fora do foco** são anunciadas.
- [ ] `aria-live="polite"` por omissão; `assertive`/`role="alert"` **só** para o que é urgente.
- [ ] A região existe no DOM **antes** de receber conteúdo.
- [ ] Não há regiões dinâmicas a disparar em catadupa nem a anunciar o óbvio.
- [ ] Mensagens de estado não roubam o foco.

### Widgets complexos

- [ ] O padrão segue um modelo documentado no **APG** (separadores, menu, combobox, árvore, grelha, diálogo).
- [ ] Diálogos modais: `role="dialog"` + `aria-modal="true"`, foco preso dentro, restituído à saída, conteúdo por baixo inerte.
- [ ] O componente foi testado com **pelo menos dois** leitores de ecrã.
- [ ] O componente foi testado com **zoom a 200%** e com o teclado.

### Antes de fechar

- [ ] Validador automático executado e resultados **interpretados**, não apenas contados.
- [ ] Teste manual com teclado feito por uma pessoa que não escreveu o código.
- [ ] Teste com leitor de ecrã feito.
- [ ] Nenhum `role`, estado ou atributo ARIA ficou no código «por precaução».

---

## Critérios de Sucesso WCAG Relacionados

Esta secção reúne, num só lugar, os critérios que atravessaram o módulo. Ao longo das secções anteriores foram referidos de forma contextual; aqui ficam organizados por nível e ligados à secção onde foram trabalhados.

**Enquadramento legal:** o **Decreto-Lei n.º 83/2018** transpõe a Diretiva (UE) 2016/2102 e remete para a norma **EN 301 549**, que fixa o **WCAG 2.1 nível AA** como requisito para os sítios e aplicações do setor público em Portugal. A tabela de nível A e AA é, por isso, **o mínimo exigível por lei**. A tabela de nível AAA é uma tabela de **boas práticas**: melhora significativamente a experiência de muitas pessoas, mas está **acima** do que a lei exige.

Alguns critérios listados pertencem às **WCAG 2.2** (2.4.11, 2.5.7, 2.5.8 e, no nível AAA, 2.4.12 e 2.4.13). Não fazem parte do baseline legal atual, mas representam a direção da norma e a versão para a qual os projetos novos devem trabalhar.

### Nível A e AA — requisito legal

| Critério | Nível | Versão | O que exige, em linguagem simples | Secção do módulo |
|---|---|---|---|---|
| **1.3.1 Informação e Relações** | A | 2.0 | A estrutura e as relações que se veem têm de estar no código, não só no aspeto visual. | *Widgets*; *Widgets Complexos* |
| **1.4.11 Contraste de Elementos Não-Textuais** | AA | 2.1 | Os limites dos controlos, os indicadores de estado e o foco precisam de contraste de pelo menos 3:1. | *Propriedades, Estados e Valores*; *Teclado e Foco* |
| **1.4.13 Conteúdo ao Passar o Rato ou com Foco** | AA | 2.1 | Conteúdo que surge ao passar o rato ou ao receber foco tem de poder ser dispensado, apontado e ficar visível. | *Rato e Toque* |
| **2.1.1 Teclado** | A | 2.0 | Toda a funcionalidade é operável por teclado. | *Teclado e Foco* |
| **2.1.2 Sem Bloqueio do Teclado** | A | 2.0 | Se se entra num componente com o teclado, tem de se conseguir sair. | *Teclado e Foco*; *Widgets Complexos* |
| **2.1.4 Atalhos de Teclas de Caracteres** | A | 2.1 | Atalhos com uma só letra têm de poder ser desligados, remapeados ou só funcionar com foco. | *Teclado e Foco*; *Fala* |
| **2.4.3 Ordem de Foco** | A | 2.0 | A sequência de foco preserva o significado e a operabilidade. | *Teclado e Foco* |
| **2.4.7 Foco Visível** | AA | 2.0 | O indicador de foco do teclado está visível. | *Teclado e Foco* |
| **2.4.11 Foco Não Obscurecido (Mínimo)** | AA | 2.2 | O elemento com foco não fica completamente escondido por conteúdo fixo. | *Teclado e Foco* |
| **2.5.1 Gestos do Apontador** | A | 2.1 | Gestos multiponto ou de caminho têm alternativa com um único ponto. | *Rato e Toque* |
| **2.5.2 Cancelamento do Apontador** | A | 2.1 | A ação dispara ao levantar o dedo/botão e pode ser cancelada. | *Rato e Toque* |
| **2.5.3 Etiqueta no Nome** | A | 2.1 | O nome acessível contém o texto da etiqueta visível. | *Fala* |
| **2.5.4 Ativação por Movimento** | A | 2.1 | Funções acionadas por movimento do dispositivo têm alternativa e podem ser desativadas. | *Rato e Toque* |
| **2.5.7 Movimentos de Arrastar** | AA | 2.2 | Tudo o que se faz arrastando faz-se também sem arrastar. | *Rato e Toque*; *Widgets Complexos* |
| **2.5.8 Tamanho do Alvo (Mínimo)** | AA | 2.2 | Alvos com pelo menos 24 × 24 px CSS, salvo exceções. | *Rato e Toque* |
| **3.2.1 Em Foco** | A | 2.0 | Receber foco não desencadeia mudanças de contexto. | *Teclado e Foco*; *Widgets Complexos* |
| **3.2.2 Ao Introduzir Dados** | A | 2.0 | Alterar o valor de um controlo não muda o contexto sem aviso prévio. | *Propriedades, Estados e Valores*; *Widgets Complexos* |
| **4.1.2 Nome, Função, Valor** | A | 2.0 | **O critério central deste módulo.** Todo o componente tem nome e função determináveis programaticamente; estados, propriedades e valores são definíveis e as alterações são notificadas. | *Widgets*; *Propriedades, Estados e Valores*; todas as restantes |
| **4.1.3 Mensagens de Estado** | AA | 2.1 | Mensagens que informam sem receber foco são comunicadas às tecnologias de apoio. | *Regiões Dinâmicas* |

> **Nota sobre o 4.1.2:** se um widget falha, há uma probabilidade elevada de falhar aqui. É o critério que ampara a ideia das «sete perguntas» — e é também o mais frequentemente incumprido em componentes personalizados.

### Nível AAA — boas práticas acima do exigido por lei

Estes critérios **não** são obrigatórios ao abrigo do Decreto-Lei n.º 83/2018. Devem ser vistos como um patamar de excelência a adotar quando o contexto o permite — sobretudo em serviços de uso frequente ou dirigidos a públicos específicos.

| Critério | Nível | Versão | O que acrescenta | Secção do módulo |
|---|---|---|---|---|
| **2.1.3 Teclado (Sem Exceção)** | AAA | 2.0 | Remove a exceção do 2.1.1 para funções dependentes do traçado do movimento. | *Teclado e Foco* |
| **2.2.4 Interrupções** | AAA | 2.0 | As interrupções podem ser adiadas ou suprimidas pela pessoa. | *Regiões Dinâmicas* |
| **2.4.12 Foco Não Obscurecido (Melhorado)** | AAA | 2.2 | O elemento com foco não fica **sequer parcialmente** tapado. | *Teclado e Foco* |
| **2.4.13 Aparência do Foco** | AAA | 2.2 | Define espessura e contraste mínimos para o indicador de foco. | *Teclado e Foco* |
| **2.5.5 Tamanho do Alvo (Melhorado)** | AAA | 2.1 | Alvos com pelo menos 44 × 44 px CSS. | *Rato e Toque* |
| **2.5.6 Mecanismos de Entrada Simultâneos** | AAA | 2.1 | Não restringir a forma de interação: teclado, toque e voz coexistem sem bloqueios. | *Rato e Toque*; *Fala* |
| **3.2.5 Alterações a Pedido** | AAA | 2.0 | Mudanças de contexto só acontecem quando a pessoa as pede. | *Widgets Complexos*; *Regiões Dinâmicas* |
| **3.3.5 Ajuda** | AAA | 2.0 | Ajuda contextual disponível junto dos controlos. | *Propriedades, Estados e Valores* |

