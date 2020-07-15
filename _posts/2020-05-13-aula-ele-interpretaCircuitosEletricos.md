---
layout: post
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


# Habilidades e Competências
* Análise e interpretação de diagramas e esquemas;

<!--more-->

## Desafio

Dado o seguinte circuito,

![Circuito elétrico do desafio - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafio-1.png?raw=true)

identificar:

* Os componentes presentes;
* As funções de cada componente;
* A configuração de ligação dos componentes: série ou paralelo.

## Componentes em um diagrama
Todo componente eletrônico possui uma __função__, ou seja, um __comportamento__ que produz uma ação que atende a sua necessidade. Para que seu comportamento ocorra de modo esperado, todo componente possui __condições de operação__, sendo a principal dessas condições a alimentação.

A alimentação de um componente é a entrada de energia, que será processada e produzirá, através do comportamento do componente, uma nova forma de energia.

Utilizando o circuito do desafio como exemplo, temos as seguintes conversões de energia por componente:

* __Vcc : Fonte__ - Converte energia química, no caso de pilhas ou baterias, em energia elétrica;
* __RD : Resistor__ - Converte energia elétrica em calor ao limitar a intensidade de corrente no seu ramo;
* __D: LED__ - Converte energia elétrica em luz, permitindo que seja feita a sinalização luminosa, indicando que o circuito está ligado;
* __RL : Resistor de carga__ - Converte energia elétrica em calor, produzindo aquecimento do elemento.


O circuito pode ser dividido em elemntos ativos e passivos, como mostrado na Figura.
![Circuito elétrico destacando a fonte e a carga - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafioFonteCarga-1.png?raw=true)

Assim temos:
* __Fonte__: A fonte é o __elemento ativo__, ou seja, é o que __fornece energia__ ao restante dos componenentes deste circuito.
* __Carga__: São os __elementos passivos__ do circuito, ou seja, aqueles que __consomem energia__ da fonte.



## Configuração do circuito
A análise de um circuito basicamente é o processo de segmentá-lo em partes menores, sem que haja alteração das suas características de funcionamento, de forma a simplificar seu manuseio.

Alguns conceitos são de fundamental importância para facilitar essa tarefa de análise do circuito, e um destes conceitos é o __nó__.

O __nó__ é uma __conexão entre pelo menos três elementos do circuito__ ou entre elementos ativos e passivos e é representada por uma circunferência preenchida unindo os terminais dos componentes.

A Figura a seguir mostra em destaque os nós denominados como __A__ e __B__. As setas nas linhas indicam o sentido da corrente, chegando ou saindo de cada nó.

![Circuito elétrico destacando o nó inferior - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafioNoInf-1.png?raw=true)
![Circuito elétrico destacando o nó superior - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafioNoSup-1.png?raw=true)



## Ligação em série
__O trecho do circuito entre nós é chamado de ramo. Em um ramo, todos os seus componentes são ligados em série__. A figura seguinte mostra os três ramos ligados aos pontos A e B , sendo o ramo central o único que possui mais do que um componente, ou seja, é o único que possui componentes em série. Assim pode-se afirmar que o __resistor RD está em série com o LED D__.

![Circuito elétrico destacando o nó superior - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafioRamoRLED-1.png?raw=true)

![Circuito elétrico destacando o nó superior - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafioRamoFonte-1.png?raw=true)
![Circuito elétrico destacando o nó superior - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoDesafioRamoRL-1.png?raw=true)

## Ligação em paralelo
O circuito da Figura 6 apresenta três nós (A, B e C ) e cinco ramos, cada um contendo apenas um elemento cada (Vcc , R1 , R2 , R3 e R4 ).

![Circuito elétrico destacando o nó superior - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-circuitoExemplo-1.png?raw=true)


Note que __o nó C aparece duas vezes, mas__ não quer dizer que sejam pontos distintos, pelo contrário, __é o mesmo ponto__, representado em dois lugares. É o ponto de conexão entre os quatro resistores.

Como existem dois ramos ligados aos __mesmos nós__, isso significa que seus elementos __estão em paralelo__. Como em cada ramo só existe um resistor, então:
* R 1 é paralelo ao R 2
* R 3 é paralelo ao R 4

Nesse circuito, nenhum ramo apresenta mais do que um elemento, assim não há componentes em série.

## Atividades
Identificar associações de resistores em __paralelo__ e em __série__.

### Circuito 1

![Exercício 1](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-ativ1-1.png?raw=true)


### Circuito 2

![Exercício 2](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-ativ2-1.png?raw=true)


### Circuito 3

![Exercício 3](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-ativ3-1.png?raw=true)


### Circuito 4

![Exercício 4](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/fig/fig-ativ4-1.png?raw=true)


## Download

[Notas de aula em PDF](https://github.com/JoseWRPereira/aula-ele-interpretaCircuitoEletrico/blob/master/pdf/aula-ele-interpretaCircuitosEletricos.pdf?raw=true)

## q U I Z
{% include quiz.html file='aula-ele-interpreta-circuitos-eletricos' %}
