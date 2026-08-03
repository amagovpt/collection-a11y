---
title: Conclusão e Boas Práticas
layout: default
nav_order: 6
---
# Conclusão e Boas Práticas

Ao longo deste módulo, olhámos para os formulários peça a peça: a forma como as pessoas com deficiência os utilizam, a estrutura e o posicionamento dos campos, os rótulos e instruções, as notificações e mensagens de erro, e os formulários com múltiplos passos.

Esta secção não introduz técnicas novas. Serve para **juntar tudo**, ver como as peças encaixam umas nas outras e ficar com um conjunto de ferramentas práticas — uma lista de verificação, exercícios e referências — que pode usar no dia a dia.

Uma analogia útil para começar: um formulário acessível é como uma **boa receita de cozinha**. Cada ingrediente (rótulo, campo, mensagem de erro) importa, mas o que faz a receita resultar é a **ordem** em que se juntam e a forma como se relacionam. Se tudo estiver tecnicamente lá, mas mal combinado, o prato não sai bem — e, num formulário, "não sair bem" significa uma pessoa que fica de fora.

---

## Recapitulação

A melhor forma de recapitular não é repetir cada capítulo, mas seguir **uma pessoa a preencher um formulário do início ao fim** e ver onde cada tema entra em jogo.

### Um percurso do princípio ao fim

Imaginemos a Sofia, uma utilizadora cega que usa um leitor de ecrã, a inscrever-se num serviço público através de um formulário com dois passos.

1. **Ela chega ao formulário e precisa de perceber o que tem pela frente.** É aqui que entra a **estrutura e o posicionamento**: os campos aparecem numa ordem lógica, agrupados por assunto (dados pessoais, depois dados de contacto), e a ordem em que o leitor de ecrã os lê é a mesma ordem em que aparecem no ecrã. Se a estrutura estivesse baralhada, a Sofia ouviria os campos numa sequência sem sentido.

2. **Em cada campo, ela precisa de saber o que lhe é pedido.** É o papel dos **rótulos e instruções**. Ao chegar ao campo do NIF, o leitor de ecrã anuncia "NIF, 9 dígitos, sem espaços". A Sofia sabe exatamente o que escrever, sem ter de adivinhar.

3. **Ela engana-se num campo — escreve um e-mail sem o `@`.** Agora entram as **notificações e mensagens de erro**. O sistema avisa-a de forma clara, diz-lhe *qual* o campo com problema e *como* o corrigir, e o leitor de ecrã anuncia esse aviso sem ela ter de o procurar.

4. **Corrigido o erro, ela avança para o segundo passo.** Aqui aplica-se tudo o que vimos sobre **múltiplos passos**: ela sabe que está no passo 2 de 2, o que já preencheu não se perdeu, e pode voltar atrás se precisar.

O ponto-chave é este: **cada tema deste módulo resolve um momento diferente da mesma experiência**. Falhar num deles chega para bloquear a Sofia, por muito bem feito que esteja o resto.

### Os fios que ligam tudo

Se recuarmos e olharmos para as cinco secções ao mesmo tempo, há quatro princípios que atravessam todas. Vale a pena guardá-los, porque funcionam como uma bússola quando surge uma situação nova:

- **Percetível** — a informação existe de mais do que uma maneira. Um erro não é assinalado só com a cor vermelha; tem também texto. Um campo obrigatório não se distingue só por um asterisco visual; a obrigatoriedade é transmitida também ao leitor de ecrã.
- **Operável pelo teclado** — tudo o que se faz com o rato tem de se poder fazer só com o teclado, na tecla `Tab` e na tecla `Enter`. Muitas pessoas não usam rato de todo.
- **Previsível** — o formulário não surpreende o utilizador. Nada muda de página nem submete dados só porque a pessoa entrou num campo ou selecionou uma opção.
- **Tolerante ao erro** — as pessoas enganam-se, e isso é normal. Um bom formulário assume o erro à partida e ajuda a corrigi-lo, em vez de castigar quem se engana.

Sempre que tiver uma dúvida sobre um caso que não está nos manuais, faça a pergunta por estes quatro filtros. Na grande maioria das vezes, a resposta certa aparece sozinha.

### Exemplo integrado: as peças a encaixar num só campo

Para ver a integração na prática, repare como um único campo bem construído reúne o trabalho de várias secções ao mesmo tempo:

```html
<label for="email">Endereço de e-mail</label>
<input
  id="email"
  name="email"
  type="email"
  autocomplete="email"
  aria-describedby="email-ajuda email-erro"
  aria-invalid="true"
/>
<p id="email-ajuda">Vamos usar este e-mail para lhe enviar a confirmação.</p>
<p id="email-erro">Falta o símbolo @. Exemplo: nome@exemplo.pt</p>
```

**O que funciona bem neste exemplo:**

- O `<label>` está ligado ao campo pelo `for`/`id`, por isso o leitor de ecrã anuncia o nome do campo (tema dos *rótulos*).
- O `type="email"` e o `autocomplete="email"` dizem ao navegador e às tecnologias de apoio que tipo de dado é este, o que permite o preenchimento automático (tema da *estrutura e posicionamento* e dos *rótulos*).
- O `aria-describedby` liga o campo tanto à instrução de ajuda como à mensagem de erro, por isso ambas são lidas sem a pessoa ter de as ir procurar (temas das *instruções* e das *mensagens de erro*).
- O `aria-invalid="true"` marca o campo como estando com erro, de forma percetível também por quem não vê a cor (tema das *mensagens de erro*).

Repare que nada aqui é decorativo: cada atributo resolve um problema concreto de uma pessoa concreta. É esta a diferença entre um formulário que "parece" acessível e um que é mesmo acessível.

---

## Recursos Adicionais

- **acessibilidade.gov.pt** — o portal oficial do ecossistema de acessibilidade da Administração Pública. Tem tutoriais em português, ferramentas e o blogue da equipa, atualizado com frequência.

- **W3C WAI — Tutorial de Formulários** (`w3.org/WAI/tutorials/forms/`) — provavelmente o melhor recurso gratuito sobre formulários acessíveis, com exemplos comentados. 
- **ARIA Authoring Practices Guide (APG)** (`w3.org/WAI/ARIA/apg/`) — padrões para componentes mais complexos (por exemplo, campos de pesquisa com sugestões). Regra de ouro: use ARIA só quando o HTML nativo não chega.

---

## Exercícios de Consolidação

Estes exercícios são diferentes dos que fez em cada capítulo. Ali, treinou um tema de cada vez. Aqui, o objetivo é **juntar tudo**, como acontece num projeto real, onde nunca há só um problema isolado.

### Exercício 1 — Auditar um formulário existente

Escolha um formulário real de um serviço que use (a inscrição num evento, um pedido de contacto, etc.). Faça três testes, por esta ordem:

1. **Teste com o teclado.** Guarde o rato e navegue o formulário inteiro só com `Tab`, `Shift+Tab`, setas e `Enter`. Consegue chegar a todos os campos e submeter? Vê sempre onde está o foco?
2. **Teste automático.** Passe a página pelo AccessMonitor ou pelo WAVE e leia os alertas.
3. **Teste com leitor de ecrã.** Ative o leitor de ecrã do seu sistema e feche os olhos ao percorrer o formulário. Cada campo diz-lhe o que é pedido?

**Objetivo:** listar 5 problemas. Este exercício mostra uma lição importante — o teste automático sozinho **não chega**.

### Exercício 2 — Construir de raiz

Crie um formulário de inscrição completo com, no mínimo: nome, e-mail, NIF, uma escolha entre opções (por exemplo, tipo de bilhete) e um campo de observações. Aplique **todos** as secções: estrutura lógica, rótulos e instruções, tratamento de erros e, se dividir em passos, indicação clara de progresso.

**Objetivo:** no fim, percorra a sua própria lista de verificação final (mais abaixo) e confirme que cada item está cumprido.

### Exercício 3 — Reparar um formulário partido

Analise o exemplo seguinte, que tem vários problemas de propósito:

```html
<form>
  Nome <input type="text"><br>
  <input type="text" placeholder="Escreva aqui o seu e-mail"><br>
  <span style="color: red;">Preencha tudo!</span><br>
  <div onclick="enviar()">Enviar</div>
</form>
```

**O que está mal neste exemplo:**

- O texto "Nome" não é um `<label>` ligado ao campo — é texto solto, invisível para o leitor de ecrã enquanto rótulo.
- O campo de e-mail usa `placeholder` em vez de rótulo; o texto de ajuda desaparece assim que a pessoa começa a escrever, e muitos leitores de ecrã não o leem de forma fiável.
- A mensagem de erro depende **apenas da cor** vermelha, é genérica ("Preencha tudo!") e não indica qual o campo com problema.
- O botão de enviar é uma `<div>` com `onclick`. Não é alcançável nem acionável pelo teclado — quem não usa rato fica bloqueado.

**Objetivo:** reescreva este formulário corrigindo os quatro problemas. Compare depois a sua versão com o exemplo integrado da secção de recapitulação.

---

## Lista de Verificação Final

Use esta lista antes de dar um formulário por concluído. Está organizada pelos temas do módulo. Não substitui os testes reais (teclado e leitor de ecrã), mas garante que nada óbvio ficou por fazer.

**Estrutura e posicionamento**

- [ ] Os campos aparecem numa ordem lógica e a ordem de leitura (foco) acompanha a ordem visual.
- [ ] Campos relacionados estão agrupados de forma clara.
- [ ] Todo o formulário é percorrido e submetido apenas com o teclado.
- [ ] O foco do teclado é sempre visível.

**Rótulos e instruções**

- [ ] Todos os campos têm um rótulo visível e ligado ao campo.
- [ ] As instruções (formato, exemplos) estão associadas ao respetivo campo, não soltas na página.
- [ ] O `placeholder` não é usado como substituto do rótulo.
- [ ] Os campos obrigatórios são identificáveis por texto, e não só por cor ou por um asterisco visual.

**Notificações e mensagens de erro**

- [ ] Os erros dizem *qual* o campo e *como* corrigir.
- [ ] Nenhum erro depende apenas da cor para ser percebido.
- [ ] As mensagens são anunciadas ao leitor de ecrã sem a pessoa ter de as procurar.
- [ ] As confirmações de sucesso também são comunicadas de forma acessível.

**Múltiplos passos**

- [ ] O utilizador sabe em que passo está e quantos faltam.
- [ ] Os dados já preenchidos não se perdem ao avançar ou recuar.
- [ ] É possível voltar atrás e rever antes de submeter.

**Geral**

- [ ] Nada muda de página nem submete dados automaticamente ao focar ou selecionar.
- [ ] Os botões são elementos `<button>` reais (ou `<input>`), acionáveis pelo teclado.
- [ ] O formulário foi testado com teclado **e** com leitor de ecrã, não só com uma ferramenta automática.

---

## Critérios de Sucesso WCAG Relacionados

Todo o trabalho deste módulo assenta nas **WCAG** (Web Content Accessibility Guidelines). Em Portugal, é o **nível AA das WCAG 2.1** que a lei exige, através do Decreto-Lei n.º 83/2018 e da norma europeia EN 301 549.

A tabela seguinte reúne os critérios mais relevantes para formulários. Não precisa de os decorar; serve para saber a que critério "prestar contas" quando alguém lhe perguntar *porquê*.

| Critério                                                     | Nível | Porque importa nos formulários                               |
| ------------------------------------------------------------ | ----- | ------------------------------------------------------------ |
| 1.3.1 — Informação e Relações                                | A     | Rótulos, grupos e a relação entre campos têm de existir no código, não só na aparência. |
| 1.3.5 — Identificar o Objetivo da Introdução                 | AA    | Permite o preenchimento automático (`autocomplete`) de campos como nome ou e-mail. |
| 1.4.1 — Utilização da Cor                                    | A     | A cor não pode ser a única forma de assinalar um erro ou um campo obrigatório. |
| 2.1.1 — Teclado                                              | A     | Todo o formulário tem de funcionar só com o teclado.         |
| 2.4.3 — Ordem de Foco                                        | A     | A ordem de navegação com `Tab` tem de fazer sentido.         |
| 2.4.6 — Títulos e Rótulos                                    | AA    | Rótulos e cabeçalhos descrevem claramente o que se pede.     |
| 2.4.7 — Foco Visível                                         | AA    | Vê-se sempre onde está o foco do teclado.                    |
| 2.5.3 — Rótulo no Nome                                       | A     | O nome lido pelo leitor de ecrã inclui o texto visível do rótulo. |
| 3.2.1 — Ao Focar                                             | A     | Entrar num campo não provoca mudanças inesperadas.           |
| 3.2.2 — Ao Introduzir                                        | A     | Alterar um campo não submete nem muda de página sem aviso.   |
| 3.3.1 — Identificação de Erros                               | A     | Os erros são identificados e descritos em texto.             |
| 3.3.2 — Rótulos ou Instruções                                | A     | Existem rótulos e instruções quando são necessários.         |
| 3.3.3 — Sugestão perante Erros                               | AA    | Quando possível, a mensagem sugere como corrigir.            |
| 3.3.4 — Prevenção de Erros (jurídicos, financeiros, de dados) | AA    | Em ações sensíveis, permite rever, confirmar ou reverter.    |
| 4.1.2 — Nome, Função, Valor                                  | A     | Cada campo expõe corretamente o seu nome, função e estado às tecnologias de apoio. |
| 4.1.3 — Mensagens de Estado                                  | AA    | Erros e confirmações são anunciados sem mudar o foco.        |

**Novidades das WCAG 2.2 a conhecer**

Embora ainda não sejam a referência legal em Portugal, estes critérios são particularmente úteis em formulários:

| Critério                                | Nível | Porque importa nos formulários                               |
| --------------------------------------- | ----- | ------------------------------------------------------------ |
| 2.5.8 — Tamanho do Alvo (Mínimo)        | AA    | Botões e opções suficientemente grandes para tocar sem erro. |
| 3.3.7 — Introdução Redundante           | A     | Não obrigar a pessoa a reintroduzir dados que já forneceu no mesmo processo. |
| 3.3.8 — Autenticação Acessível (Mínimo) | AA    | Não exigir provas de memória (por exemplo, resolver puzzles) para entrar. |
