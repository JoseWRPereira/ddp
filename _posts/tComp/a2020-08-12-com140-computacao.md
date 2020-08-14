---
layout: post
title:  "COM140 - Introdução a computação"
date:   2020-08-12 19:32:21 -03:00
categories: Computação
badges:
 - type: primary
   tag: UniVESP
 - type: secondary
   tag: Computação
---

# [Computação](https://cursos.univesp.br/courses/3164/pages/videoaula-do-professor-representacao-de-dados?module_item_id=266221)

# Representação de dados

## Dado/Informação/Conhecimento

### Dados
 * são **elementos** conhecidos de um problema;
 * e são desprovidos de significado, se considerados isolados.

### Informação
 * Conjunto estruturado de dados;
 * Possuem utilidade e podem gerar ações.

 ### Conhecimento
  * **Síntese** de múltiplas fontes de informações;
  * Possui elevado significado e utilidade para o suporte à tomada de decisões.


| Dados      | Informação            | Conhecimento |
|:----------:|:---------------------:|:------------:|
| Observação | Análise e organização | Síntese      |


## Dados analógicos e digitais

Dados analógicos: 
* utilizam representação contínua;
* infinitos valores entre quaisquer dois pontos (conjunto dos Reais).
Dados digitais: 
* utilizam representação discreta;
* valores bem definidos e um conjunto limitado de valores (conjunto dos Inteiros).
* Dois estados lógicos bem definidos (**Bi**nary digi**t** : Bit).

### Byte 
**B**inar**y** **te**rm : unidade básica de armazenamento em memória, formada por 8 bits.

### Word
Palavra: dimensão do barramento de processamento que pode ser 2, 4, 6, 8 bytes (64 bits), ou outro valor a depender da arquitetura do processador.


## Sistema de numeração

Representação estruturada e dentro de um contexto de uma coleção de números através de numerais.

Em computação são utilizados os seguintes sistemas de numeração:
* Binário (base 2);
* Octal (base 8);
* Decimal (base 10);
* Hexadecimal (base 16).

[Representação por ponto fixo](https://www.youtube.com/watch?v=8Nev_5ISYOY&feature=youtu.be)





Todo **programa** visa **solucionar um problema** posto, partindo da definição do problema (O que?) e seguindo para o desenvolvimento do programa (Como?), que pode ser dividido em três partes:
  * Projetar a solucação (algoritmo);
  * Codificar a solução (Programar em linguagem de programação);
  * Testar o programa.

<!--more-->

Um **algoritmo** é uma sequência bem definida, explícita e precisa, de passos que visam atingir um objetivo.
* Cada passo do algorítmo deve ser uma ação realizável;
* A ordem dos passos devem ser precisamente determinadas;
* O algoritmo deve ter fim.

Um algoritmo deve conter:

* Sequenciamento: estabelece um padrão de comportamento, em que as ações devem ser executadas linearmente;
* Teste seletivo ou estrutura condicional;
* Repetição: mesmo trecho é repetido até que a condição de parada seja alcançada. O número de repetições é indefinido apesar de ser finito;
* Condição de parada.


O algoritmo deve ser:

* refinado de forma sucessiva até que as instruções possam ser codificadas;
* independente da linguagem.


As linguagens possuem:

* um número restrito de instruções;
* possuem um conjunto de instruções comuns a todas as linguagens:
  * Entradas e Saídas;
  * Testes seletivos;
  * Repetições; etc.
  

Os algoritmos podem ser apresentados em forma de fluxograma, que é uma representação esquemática, feito com gráficos que ilustram transições de informações entre os elementos que o compõem. Um fluxograma representa a lógica interna do programa e possui simbologia própria.


<hr/>

[Voltar]({{site.baseurl}}/docs/tecnologia)