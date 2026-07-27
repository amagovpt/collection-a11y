
# Imagens Complexas

## Introdução

### Como as Pessoas com Deficiência usam Imagens Complexas

Imagine que está a tentar explicar um gráfico detalhado ao telefone a um amigo. Não pode simplesmente dizer "há um gráfico aqui" - precisa de descrever os dados, as tendências e as conclusões importantes. É exatamente essa a experiência das pessoas cegas ou com baixa visão com imagens complexas na web.

**Imagens complexas** são aquelas que contêm informação detalhada que não conseguimos transmitir numa descrição curta. Incluem:

- Gráficos e tabelas visuais
- Diagramas técnicos
- Infografias
- Mapas detalhados
- Fluxogramas
- Organogramas

**Como diferentes utilizadores acedem a estas imagens:**

**Utilizadores de leitores de ecrã** dependem de descrições textuais detalhadas que expliquem não só o que está na imagem, mas também o significado dos dados apresentados.

**Utilizadores com baixa visão** podem precisar de versões ampliadas ou com maior contraste, mas também beneficiam de descrições textuais que complementem o que conseguem ver parcialmente.

**Utilizadores com deficiências cognitivas** podem precisar de explicações mais simples e estruturadas dos dados complexos.

### Requisitos de Acessibilidade para Imagens Complexas

Para tornar imagens complexas acessíveis, precisamos de:

1. **Texto alternativo conciso** que identifique o tipo de imagem
2. **Descrição longa detalhada** que explique todos os dados importantes
3. **Estrutura clara** na descrição que seja fácil de navegar
4. **Dados em formatos alternativos** quando possível

**Analogia útil:** Pense numa imagem complexa como um livro. O texto alternativo é como o título do livro - diz-nos do que se trata. A descrição longa é como o resumo da contracapa - explica o conteúdo em detalhe.

## Técnicas de Codificação

### Técnica 1: Atributo `alt` + Descrição Longa

```html
<!-- EXEMPLO BOM -->
<img src="vendas-2024.jpg" 
     alt="Gráfico de vendas trimestrais de 2024"
     longdesc="descricao-vendas.html">

<!-- Ficheiro descricao-vendas.html -->
<h2>Descrição detalhada do gráfico de vendas 2024</h2>
<p>Este gráfico de barras mostra a evolução das vendas ao longo de 4 trimestres:</p>
<ul>
  <li>1º Trimestre: 150.000€ (crescimento de 10% face ao ano anterior)</li>
  <li>2º Trimestre: 180.000€ (pico do ano)</li>
  <li>3º Trimestre: 165.000€ (ligeira descida sazonal)</li>
  <li>4º Trimestre: 200.000€ (melhor trimestre de sempre)</li>
</ul>
<p>Tendência geral: crescimento constante com total anual de 695.000€.</p>
```

**O que funciona bem:** O texto alternativo é conciso mas informativo. A descrição longa está estruturada e inclui dados específicos e conclusões.

### Técnica 2: Usar `aria-describedby`

```html
<!-- EXEMPLO BOM -->
<img src="organograma.jpg" 
     alt="Organograma da empresa XYZ"
     aria-describedby="desc-organograma">

<div id="desc-organograma">
  <h3>Estrutura organizacional da empresa XYZ</h3>
  <p>A empresa está organizada em 3 níveis hierárquicos:</p>
  
  <h4>Direção Executiva</h4>
  <p>No topo encontra-se o CEO (João Silva), ligado diretamente a 3 diretores.</p>
  
  <h4>Direções Departamentais</h4>
  <ul>
    <li>Diretora de Recursos Humanos (Maria Santos) - supervisiona 5 colaboradores</li>
    <li>Diretor Financeiro (Pedro Costa) - supervisiona 3 colaboradores</li>
    <li>Diretor de Marketing (Ana Lopes) - supervisiona 7 colaboradores</li>
  </ul>
  
  <h4>Equipas Operacionais</h4>
  <p>Cada departamento tem equipas especializadas com total de 15 colaboradores.</p>
</div>
```

**O que funciona bem:** A descrição está ligada à imagem através do `aria-describedby`. A informação está estruturada hierarquicamente, espelhando a própria estrutura do organograma.

### Técnica 3: Fornecer Dados em Tabela

```html
<!-- EXEMPLO BOM -->
<figure>
  <img src="grafico-temperaturas.jpg" 
       alt="Gráfico de linha mostrando temperaturas médias mensais em Lisboa">
  
  <figcaption>
    <p>Temperaturas médias mensais em Lisboa durante 2024</p>
    
    <details>
      <summary>Ver dados em tabela</summary>
      <table>
        <caption>Temperaturas médias mensais em Lisboa (2024)</caption>
        <thead>
          <tr>
            <th>Mês</th>
            <th>Temperatura (°C)</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Janeiro</td><td>12°C</td></tr>
          <tr><td>Fevereiro</td><td>14°C</td></tr>
          <tr><td>Março</td><td>16°C</td></tr>
          <tr><td>Abril</td><td>18°C</td></tr>
          <tr><td>Maio</td><td>22°C</td></tr>
          <tr><td>Junho</td><td>26°C</td></tr>
          <tr><td>Julho</td><td>29°C</td></tr>
          <tr><td>Agosto</td><td>29°C</td></tr>
          <tr><td>Setembro</td><td>25°C</td></tr>
          <tr><td>Outubro</td><td>20°C</td></tr>
          <tr><td>Novembro</td><td>16°C</td></tr>
          <tr><td>Dezembro</td><td>13°C</td></tr>
        </tbody>
      </table>
    </details>
  </figcaption>
</figure>
```

**O que funciona bem:** Os dados estão disponíveis numa tabela acessível. O elemento `<details>` permite que os utilizadores escolham se querem aceder aos dados detalhados.

## Recomendações para Conteúdo Acessível

### Boas Práticas para Descrições

1. **Comece pelo geral, vá para o específico**

   - Identifique o tipo de gráfico/diagrama
   - Explique o contexto e objetivo
   - Descreva os dados principais
   - Mencione tendências e conclusões

2. **Use linguagem clara e estruturada**

   - Organize com cabeçalhos e listas
   - Use números e percentagens específicos
   - Evite linguagem técnica desnecessária

3. **Foque no que é importante**

   - Destaque tendências e padrões
   - Mencione valores máximos e mínimos
   - Explique relações causa-efeito

### Exemplo de Descrição Bem Estruturada

```html
<!-- EXEMPLO BOM -->
<img src="infografia-reciclagem.jpg" 
     alt="Infografia sobre reciclagem em Portugal"
     aria-describedby="desc-reciclagem">

<div id="desc-reciclagem">
  <h3>Infografia: Estado da Reciclagem em Portugal 2024</h3>
  
  <h4>Dados Principais</h4>
  <p>Portugal recicla atualmente 65% dos seus resíduos, um aumento de 15% face a 2020.</p>
  
  <h4>Breakdown por Material</h4>
  <ul>
    <li>Papel: 80% reciclado (melhor desempenho)</li>
    <li>Vidro: 75% reciclado</li>
    <li>Plástico: 45% reciclado (maior desafio)</li>
    <li>Metal: 70% reciclado</li>
  </ul>
  
  <h4>Impacto Ambiental</h4>
  <p>Esta taxa de reciclagem representa uma poupança de 2.3 milhões de toneladas de CO2 anuais.</p>
  
  <h4>Objetivos Futuros</h4>
  <p>Meta para 2030: atingir 80% de reciclagem total, com foco especial no plástico.</p>
</div>
```

**O que funciona bem:** A descrição está organizada logicamente, inclui dados específicos e explica o significado dos números apresentados.

### Erros Comuns

#### Erro 1: Descrição Demasiado Vaga

```html
<!-- EXEMPLO MAU -->
<img src="grafico-vendas.jpg" 
     alt="Gráfico que mostra vendas">

<p>Este gráfico mostra que as vendas subiram.</p>
```

**Problema:** Não fornece dados específicos nem contexto útil.

```html
<!-- EXEMPLO BOM -->
<img src="grafico-vendas.jpg" 
     alt="Gráfico de vendas trimestrais 2024">

<div id="desc-vendas">
  <p>Gráfico de barras mostrando vendas trimestrais de 2024:</p>
  <ul>
    <li>Q1: €150.000</li>
    <li>Q2: €180.000 (aumento de 20%)</li>
    <li>Q3: €165.000 (descida sazonal)</li>
    <li>Q4: €200.000 (recorde histórico)</li>
  </ul>
  <p>Crescimento anual total: 33% face a 2023.</p>
</div>
```

#### Erro 2: Sobrecarregar o Atributo `alt`

```html
<!-- EXEMPLO MAU -->
<img src="diagrama.jpg" 
     alt="Este diagrama complexo mostra o processo de produção da empresa que inclui 15 etapas diferentes começando pela receção de matérias-primas no armazém A seguindo para o controlo de qualidade depois para a linha de produção 1 onde ocorre...">
```

**Problema:** O texto alternativo deve ser conciso. Informação detalhada vai na descrição longa.

```html
<!-- EXEMPLO BOM -->
<img src="diagrama.jpg" 
     alt="Diagrama de fluxo do processo de produção"
     aria-describedby="desc-processo">

<div id="desc-processo">
  <!-- Descrição detalhada aqui -->
</div>
```

#### Erro 3: Não Fornecer Alternativas aos Dados

```html
<!-- EXEMPLO MAU -->
<img src="grafico-complexo.jpg" 
     alt="Gráfico com muitos dados">
<!-- Sem mais informação disponível -->
```

**Problema:** Utilizadores não conseguem aceder aos dados subjacentes.

```html
<!-- EXEMPLO BOM -->
<img src="grafico-complexo.jpg" 
     alt="Gráfico de vendas por região e trimestre">

<p><a href="dados-vendas.csv">Descarregar dados em CSV</a></p>
<details>
  <summary>Ver tabela de dados</summary>
  <!-- Tabela HTML com os dados -->
</details>
```

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

**Lembre-se sempre:**

1. **Imagens complexas precisam de duas camadas de informação**: texto alternativo conciso + descrição detalhada
2. **Estruture as descrições como um mini-documento** com cabeçalhos, listas e parágrafos claros
3. **Inclua dados específicos, não apenas impressões gerais** - números, percentagens, tendências
4. **Forneça alternativas aos dados visuais** - tabelas, ficheiros CSV, listas estruturadas
5. **Teste sempre** com leitores de ecrã para verificar se a informação faz sentido

**Analogia final:** Uma imagem complexa acessível é como ter um guia turístico excelente num museu. Não só lhe diz o que está a ver, mas explica o contexto, a importância e ajuda-o a compreender toda a informação apresentada.

### Exercícios Práticos

#### Exercício 1: Análise de Gráfico

Observe esta descrição de uma imagem complexa e identifique o que está bem e o que poderia melhorar:

```html
<img src="grafico-pib.jpg" alt="Gráfico do PIB">
<p>O PIB aumentou nos últimos anos.</p>
```

**Tarefas:**

1. Reescreva o texto alternativo
2. Crie uma descrição longa adequada
3. Sugira um formato alternativo para os dados

#### Exercício 2: Criação de Descrição

Imagine uma infografia sobre "Consumo de Água em Casa" que mostra:

- 40% para banhos
- 25% para máquina da roupa
- 20% para cozinha
- 10% para jardim
- 5% para outros usos

Crie o código HTML completo com texto alternativo e descrição acessível.

#### Exercício 3: Correção de Erros

Identifique e corrija os problemas neste código:

```html
<img src="organograma-complexo.jpg" 
     alt="Este organograma mostra toda a estrutura da nossa empresa de 200 pessoas organizada em 5 departamentos com o CEO no topo e 3 níveis hierárquicos onde cada departamento tem um director e vários coordenadores...">
```

#### Exercício 4: Teste Prático

Usando um leitor de ecrã, teste uma das suas descrições de imagem complexa. Anote:

1. A informação é compreensível apenas com áudio?
2. A navegação pela descrição é fluida?
3. Que melhorias faria?