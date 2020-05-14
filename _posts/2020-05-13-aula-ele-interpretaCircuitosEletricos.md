---
title: "Interpretação de circuitos elétricos"
date: 2020-05-13 02:48:21 -0500
categories: Aula
badges:
 - type: danger
   tag: SENAI
 - type: secondary
   tag: Eletricidade
 - type: secondary
   tag: Circuitos
---


## Habilidades e Competências
* análise e interpretação de diagramas e esquemas;

<!--more-->

## Desafio

Dado o circuito da Figura 1, identificar:

Figura 1: Circuito elétrico




![https://raw.githubusercontent.com/JoseWRPereira/ddp/docs/aulas/fig-ele/fig-circuitoDesafio.png](https://raw.githubusercontent.com/JoseWRPereira/ddp/docs/aulas/fig-ele/fig-circuitoDesafio.png)


[((site.repo))/docs/aulas/fig-ele/fig-circuitoDesafio.png](((site.repo))/docs/aulas/fig-ele/fig-circuitoDesafio.png)




• Os componentes presentes;
• As funções de cada componente;
• A configuração de ligação dos componentes: série ou paralelo.

# Componentes em um diagrama
Todo componente eletrônico possui uma função, ou seja, um comportamento que produz uma ação que atende a sua necessidade. Para que seu comportamento ocorra de modo esperado, todo componente possui condições de operação, sendo a principal dessas condições a alimentação.

A alimentação de um componente é a entrada de energia, que será processada e produzirá, através do comportamento do componente, uma nova forma de energia.

Utilizando a Figura 2 como exemplo, temos as seguintes conversões de energia:

Figura 2: Circuito elétrico

Componentes:
* Vcc : Fonte - Converte energia química, no caso de pilhas ou baterias, em energia elétrica;
* RD : Resistor - Converte energia elétrica em calor ao limitar a intensidade de corrente no seu ramo;
* D: LED - Converte energia elétrica em luz, permitindo que seja feita a sinalização luminosa, indicando que o circuito está ligado;
* RL : Resistor de carga - Converte energia elétrica em calor, produzindo aquecimento do elemento.


Figura 3: Circuito elétrico

O circuito pode ser dividido em elemntos ativos e passivos, como mostrado na Figura 3.

Assim temos:
* Fonte: A fonte é o elemento ativo, ou seja, é o que fornece energia ao restante dos componenentes deste circuito.
* Carga: São os elementos passivos do circuito, ou seja, aqueles que consomem energia da fonte.

# Configuração do circuito
A análise de um circuito basicamente é o processo de segmentá-lo em partes menores, sem que haja alteração das suas características de funcionamento, de forma a simplificar seu manuseio.

Alguns conceitos são de fundamental importância para facilitar essa tarefa de análise do circuito, e um destes conceitos é o nó.

O nó é uma conexão entre pelo menos três elementos do circuito ou entre elementos ativos e passivos e é representada por uma circunferência preenchida unindo os terminais dos componentes.

A Figura 4 mostra em destaque os nós denominados como A e B. As setas nas linhas indicam o sentido da corrente, chegando ou saindo de cada nó.

Figura 4: Nós A e B .

## Ligação em série
O trecho do circuito entre nós é chamado de ramo. Em um ramo, todos os seus componentes são ligados em série. A Figura 5 mostra os três ramos ligados aos pontos A e B , sendo o ramo central o único que possui mais do que um componente, ou seja, é o único que possui componentes em série. Assim pode-se afirmar que o resistor R D está em série com o LED D.

Figura 5: Ramos entre os nós A e B .

## Ligação em paralelo
O circuito da Figura 6 apresenta três nós (A, B e C ) e cinco ramos, cada um contendo apenas um elemento cada (Vcc , R1 , R2 , R3 e R4 ).

Figura 6: Nós do circuito.

Note que o nó C aparece duas vezes, mas não quer dizer que sejam pontos distintos, pelo contrário, é o mesmo ponto, representado em dois lugares. É o ponto de conexão entre os quatro resistores.

Como existem dois ramos ligados aos mesmos nós, isso significa que seus elementos estão em paralelo. Como em cada ramo só existe um resistor, então:
* R 1 é paralelo ao R 2
* R 3 é paralelo ao R 4

Nesse circuito, nenhum ramo apresenta mais do que um elemento, assim não há componentes em série.

Resolução do Desafio
Dado o circuito da Figura 7, identificar:
Figura 7: Circuito elétrico
• Os componentes presentes;
R D
• As funções de cada componente;
V cc
• A configuração de ligação dos compo-
D
nentes: série ou paralelo.
5.1 Resolução
• Componente: função;
– V CC : Fonte de Alimentação do circuito;
– R D : Resistor limitador de corrente para o LED D;
– D: Dispositivo de sinalização luminosa, LED;
4
R L– R L : Dispositivo de aquecimento, resistor de carga.
• A configuração de ligação dos componentes: série ou paralelo.
– Fonte(gerador) está em paralelo com o restante do circuito, consumidor.
– R D está em série com o LED D.
– R L está em paralelo com o ramo inteiro do R D e D e também em paralelo com a fonte.
Note que R L não está em paralelo individualmente com R D e nem com o D, mas sim
com os dois componentes associados.
6 Atividades
Identificar Associações de Resistores em Paralelo e em Série.
