---
layout: post
title: "Resistência equivalente total e 1ª Lei de Ohm"
date: 2020-05-26 08:22:21 -0300
categories: Aula
badges:
 - type: danger
   tag: SENAI
 - type: secondary
   tag: Eletricidade
 - type: secondary
   tag: Req
 - type: secondary
   tag: "1ª Lei de Ohm"
---

# Habilidades e Competências
* Calcular grandezas elétricas em circuitos elétricos;
* Calcular a resistência equivalente total de circuitos elétricos.

<!--more-->

## Desafio
Dado o circuito da Figura 1, considerar: R1 = 330 $\Omega$, R2 = 150 $\Omega$, R3 = 270 $\Omega$,R4 = 400 $\Omega$ e R5 = 100 $\Omega$.

Identificar:
* os nós do circuito;
* a configuração de ligação dos componentes: série ou paralelo;
* Calcular a resistência equivalente em cada ramo;
* Simplificar o circuito ao redesenhá-lo;
* Repetir o processo até obter a resistência equivalente total.

| *Figura 1: Circuito elétrico misto* |
|:--:|
| ![Circuito elétrico do desafio - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-desafio-1.png?raw=true) |


## Revisitando Conhecimentos
A identificação de configurações e características do circuito é fundamental para a sua análise.

Entre os principais pontos estão:

* A identificação da(s) fonte(s) e da(s) carga(s) do circuito;

* A identificação dos nós;

* A identificação dos ramos;

* As ligações em série e em paralelo.




## Lei de Ohm

A **primeira lei de Ohm** é a relação entre as três grandezas elétricas básicas: **tensão**, **resistência** e **corrente**.

Considerando o circuito da Figura 2:

|* Figura 2: Circuito elétrico Simples*|
|:--:|
| ![Circuito elétrico do desafio - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-circuitoSimples-1.png?raw=true) |

* *Vcc*: Fonte de tensão ajustável, em Volts[V];
* *I*: Intensidade de corrente elétrica, em Amperes [A];
* *Rt*: Resistência elétrica em Ohms [ $\Omega$ ].

[**Georg Simon Ohm**](https://pt.wikipedia.org/wiki/Georg_Simon_Ohm) percebeu que a relação entre tensão e corrente em um circuito resistivo é constante, ou seja, para um dado circuito, com uma resistência fixa, ao variar a tensão aplicada aos seus terminais
a intensidade da corrente que percorre o circuito varia de forma proporcional.

Ao tomar nota de alguns pontos de medição, pode-se desenhar um gráfico como na Figura 3, e perceber que os pontos anotados formam uma reta. Isso ocorre pela proporcionalidade entre a variável manipulada, aquela que é ajustada por quem conduz a experiência, e a variável controlada, que é aquela que depende de outro parâmetro do sistema, e que não é manipulada diretamente.

| *Figura 3: Grafico $V_{CC}$ x $I$* |
|:--:|
| ![Circuito elétrico do desafio - Interpretação de Circuitos Elétricos](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-leiOhmGrafico-1.png?raw=true) |


Estão destacados no gráfico três pontos, **A**, **B** e **C**, e pode-se perceber que o ponto **B** está localizado em uma tensão que é o dobro da tensão do ponto **A**, por consequência, a intensidade da corrente produzida também é o dobro. O mesmo ocorre no ponto **C** em relação ao ponto **B**.

A representação matemática para uma reta, é uma equação do primeiro grau, assim a equação que representa a reta do gráfico da Figura 3 pode ser obtida da seguinte forma:

Escolha dois pontos quaisquer da reta, **A** e **B**, **A** e **C**, **B** e **C**, ou ainda algum deles com a origem **(0,0)**.

Pontos escolhidos: **B** e **(0,0)**.

Ao projetar o ponto **B** no eixo da tensão, temos um triângulo retângulo formado pelos pontos: **B**, **(4,0)** e **(0,0)**.

Utilizando a relação $\frac{\Delta I}{\Delta V}$, temos o coeficiente algular da reta $G$.

$$
\begin{eqnarray}
  \frac{\Delta I}{\Delta V} & = & G \nonumber \\
  \Delta I & = & G .\Delta V \nonumber \\
  I - I_0 & = & G . (V - V_0)
\end{eqnarray}
$$

Como a origem foi escolhida como um dos pontos do triângulo, o $\Delta I$ será o próprio valor no ponto $B$, ou seja, $I_0$ e $V_0$ valem $0$.

$$
\begin{eqnarray}
  \label{eqn:leiOhmG}
  I & = & G . V
\end{eqnarray}
$$
Analogamente à [equação da reta](https://www.todamateria.com.br/equacao-da-reta/) $f(x) = ax + b$ temos que:


* $I$ é o resultado da função, é a variável dependente pois varia em função da variável independete;

* $V$ é a variável independente, é manipulada por quem conduz o experimento, ajustando o valor da fonte para um valor desejado;

* $G$ é coeficiente angular, valor que exprime o quanto a reta está inclinada.

O coeficiente angular **G** mostra que, para um ânglo de inclinação pequeno, uma variação de tensão alta produz uma variação de corrente é pequena, ou seja, a condução é ruim. Com um ângulo de inclinação grande, uma variação de tensão pequena produz uma grande variação de corrente, ou seja, uma ótima condução.

O coeficiente angular **G** é denominado como *condutância*, e sua unidade é o *Siemens[S]*.

A condutância é o inverso da resistência, ou seja, dois aspectos de um mesmo fenômeno.
$$
\begin{eqnarray}
  \label{eqn:GinvR}
  G & = & \frac{1}{R}
\end{eqnarray}
$$

Substituindo ($G = \frac{1}{R}$) em ($I = G . V$), temos a **Primeira Lei de OHM**.
$$
\begin{eqnarray}
  \label{eqn:leiOhmR}
  I & = & \frac{1}{R} . V
\end{eqnarray}
$$



## Associação de Resistores em Série

Dado um ramo qualquer de um circuito resistivo, sabe-se que todos os elementos nele contidos estão associados em série, pois, aplicada uma diferença de potencial às suas extremidades, a corrente que percorre esse ramo é a mesma em todos os componentes, havendo apenas um caminho entre os nós conectados às extremidades.

Ao aplicar uma diferença de pontencial não nula entre os nós $A$ e $B$, haverá uma corrente elétrica entre esses pontos. O valor da intensidade dessa corrente depende, além da própria tensão, da resistência que o ramo apresenta, como diz a 1ª Lei de Ohm.

Todo elemento inserido em série no ramo, acrescenta resistência a ele.
Todo ramo com mais do que um resistor, pode ser substituído por um ramo equivalente, sem que haja mudança dos parâmetros elétricos do circuito, desde que não se altere a resistência equivalente do ramo, como mostrado na Figura 4.


| *Figura 4: Ramo entre nós $A$ e $B$* |
|:--:|
| ![Ramo entre nós](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-rSerie-1.png?raw=true) |





A Figura 4(a) mostra o ramo com dois resistores, que formam a resistência total do ramo, que é ilustrado na Figura 4(b) com a resistência equivalente.
Pode-se representar a resistência equivalente em um ramo da seguinte forma:
$$
\begin{eqnarray}
R_1 + R_2 = R_{eq}
\end{eqnarray}
$$
Para uma quantidade de resistores no ramo maior do que dois, a resistência equivalente é calculada da mesma forma:
$$
\begin{eqnarray}
R_1 + R_2 + ... + R_n = R_{eq}
\end{eqnarray}
$$









## Associação de Resistores em Paralelo

A intensidade da corrente que circula em um ramo, depende da tensão aplicada aos seus nós e da resistência total do ramo. Assim, para o circuito da Figura 5(a) a corrente total depende apenas do valor de $V_{CC}$ e $R_1$. Não havendo mudanças nesses valores, também não haverá mudança no valor da intensidade de corrente, denotada $I_T$. A intensidade da corrente que flui da fonte é a mesma que atravessa a carga, com uma certa resistência e condutância.

| *Figura 5: Circuito em paralelo* |
|:--:|
| ![Circuito em paralelo](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-paralelo-1.png?raw=true) |

Ao inserir outro ramo ao circuito, como mostrado na Figura 5(b), a intensidade da corrente no ramo de $R_1$ não é alterado, pois a tensão entre os pontos $A$ e $B$ não muda, bem como seu valor ôhmico, porém, a intensidade total da corrente muda, pois há agora um novo caminho, um novo ramo para circulação da corrente.

A mudança do circuito (a) para o (b), produz um novo caminho para a circulação da corrente. Pode-se dizer então que com a inclusão do novo ramo, conectado aos mesmos pontos do ramo já existente, há uma maior facilidade para a corrente fluir, pois agora são dois caminhos, aumentando a condutância entre os nós.

Pode-se obter a condutância total do circuito paralelo somando as condutâncias dos ramos, da seguinte forma:
$$
\begin{eqnarray}
  G_T & = & G_{R_1} + G_{R_2}
\label{eqn:GT}
\end{eqnarray}
$$
A forma mais comum é trabalhar com a resistência e não a condutância, então,
substituindo a condutância pelo inverso da resistência pode-se obter a resistência total:
$$
\begin{eqnarray}
  \frac{1}{R_T}	& = & \frac{1}{R_1} + \frac{1}{R_2} \nonumber\\
	\nonumber\\
	R_T & = & \frac{1}{\frac{1}{R_1} + \frac{1}{R_2} }
	\label{eq:paralelo}
\end{eqnarray}
$$

Da mesma forma pode-se aplicar para circuitos com varios ramos em paralelo, basta somar as condutâncias:
$$
\begin{eqnarray}
	G_T & = & G_1 + G_2 + ... + G_n
\end{eqnarray}
$$
Analogamente para a resistência total temos:
$$
\begin{eqnarray}
	\label{eq:nrparalelo}
	R_T & = & \frac{1}{\frac{1}{R_1} + \frac{1}{R_2} + ... + \frac{1}{R_n} }
\end{eqnarray}
$$

### Associação em Paralelo - Apenas 2 resistores

O cálculo de resistores em paralelo pode ser realizado manipulando a Equação da associação em paralelo da seguinte forma:
$$
\begin{eqnarray}
	G_{eq} & = & G_{R_1} + G_{R_2} \nonumber\\
	\nonumber\\
	\frac{1}{R_{eq}}	& = & \frac{1}{R_1} + \frac{1}{R_2} \nonumber\\
	\nonumber\\
	\frac{1}{R_{eq}}	& = & \frac{R_1 + R_2}{R_1.R_2} \nonumber\\
	\nonumber\\
	R_{eq}	& = & \frac{R_1.R_2}{R_1 + R_2} \nonumber
\end{eqnarray}
$$
**Atenção!** Essa forma só é válida para a associação de dois resistôres.


### Associação resistores em paralelo - Todos iguais

Outra forma particular para calcular resistência equivalente é quanto os resistores em paralelo são **todos** de mesmo valor, então o cálculo pode ser realizado manipulado a Equação da condutância equivalente da seguinte forma:

*Dados os seguintes resistores em paralelo e nomeados sequencialmente: $R_1$ = $R_2$ = ... = $R_n$.*
$$
\begin{eqnarray}
	G_{eq} & = & G_1 + G_2 + ... + G_n \nonumber\\
	\nonumber\\
	\frac{1}{R_{eq}} & = & \frac{1}{R_1} + \frac{1}{R_2} + ... + \frac{1}{R_n}\nonumber\\
	\nonumber\\
	\frac{1}{R_{eq}} & = & n.\frac{1}{R} \nonumber\\
	\nonumber\\
	\frac{1}{R_{eq}} & = & \frac{n}{R} \nonumber\\
	\nonumber\\
	\frac{R_{eq}}{1} & = & \frac{R}{n} \nonumber\\
	\nonumber\\
	R_{eq} & = & \frac{R}{n}
\end{eqnarray}
$$
Atenção! Essa forma só é válida para a associação de resistôres iguais.










## Leis de Kirchhoff

A **primeira lei de Kirchhoff** fala sobre as correntes em um nó, por isso é comum ser chamada de **lei dos nós**, enquanto que a **segunda lei de Kirchhoff** fala sobre as tensões em uma malha, sendo assim a **lei das malhas**.


### 1ª Lei de Kirchhoff

**A soma das correntes em um nó é igual a zero.**

| *Figura 6: Circuito em paralelo* |
|:--:|
| ![Circuito em paralelo](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-noSupInf-1.png?raw=true) |


A Figura 6 mostra o sentido convencional da corrente nos dois nós do circuito.

Tendo um nó como referência, adota-se uma convenção para o sentido da corrente. Assim, a corrente que chega ao nó é anotada como positiva e a corrente que sai é negativa. O oposto também pode ser adotado.

Escrevendo, pela definição, a equação para o nó $A$ temos:
$$
\begin{eqnarray}
\label{eq:1kirchhoff}
(+I_T) + (-I_1) + (-I_2) & = & 0\\
I_T - I_1 - I_2 & = & 0 \nonumber\\
I_T = I_1 + I_2
\end{eqnarray}
$$
Da mesma forma para o nó $B$:
$$
\begin{eqnarray}
(-I_T) + (+I_1) + (+I_2) & = & 0 \nonumber\\
I_1 + I_2 & = & I_T \nonumber
\end{eqnarray}
$$










### 2ª Lei de Kirchhoff

A Figura 7 mostra os dois ramos que formam o circuito em série.
A limitação dos ramos são os nós $A$ e $B$, cuja diferença de potencial é proporcionada pelo ramo da fonte, tensão gerada. Essa diferença de potencial, é aplicada ao ramo que contém os resistores, $R_1$ e $R_2$, que dividem essa tensão em valores parciais, denominados de queda de tensão.

| *Figura 7: Circuito em Série* |
|:--:|
| ![Circuito em paralelo](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-malha-1.png?raw=true) |


A segunda lei de Kirchhoff diz que: **A soma das tensões (ou quedas de tensão) em uma malha é igual a zero**.

Adotando um ponto como referencia de partida, por exemplo o ponto $A$, percorre-se no sentido da corrente, por todo circuito até retornar ao ponto de partida. Ao encontrar uma indicação de tensão no mesmo sentido, adota-o como valor positivo, e no sentido contrário, adota-o como negativo.

Assim, pode-se representar a equação da malha pela definição da seguinte forma:
$$
\begin{eqnarray}
	(-V_{R1}) + (-V_{R2}) + (V_{CC})  & = & 0 \\
	-V_{R1} - V_{R2} + V_{CC} & = & 0 \nonumber\\
	 V_{CC} & = & V_{R1} + V_{R2}
\end{eqnarray}
$$

Sabemos que em um ramo cada resistor apresenta uma parcela proporcional da resistência total, pois a soma dessas parcelas é a própria resistência total.
$$
\begin{eqnarray}
R_1 + R_2 = R_{T_{ramo}}
\end{eqnarray}
$$
Temos que $R_{T_{ramo}}$ é a resistência total do ramo e é formada por duas partes, $R_1$ e $R_2$, somados. Assim cada resistor é uma parte da resistência total do ramo, um parte do todo.

Sabemos que a parte dividida pelo todo é uma relação de proporcionalidade e que a queda de tensão em cada resistor do ramo é proporcional a sua resistência em relação a resistência total, assim temos que:
$$
\begin{eqnarray}
\frac{R_1}{R_2+R_1} & = & \frac{V_{R1}}{V_{R2}+V_{R1}}\\
\nonumber\\
V_{AB} & = & V_{R1} + V_{R2} \\
\nonumber\\
\frac{R_1}{R_2+R_1} & = & \frac{V_{R1}}{V_{AB}}
\end{eqnarray}
$$
Isolando-se $V_{R1}$  temos:
$$
\begin{eqnarray}
V_{R1} & = & \frac{R_1}{R_2 + R_1} . V_{AB}
\end{eqnarray}
$$
Iguanlmente para $V_{R2}$:
$$
\begin{eqnarray}
V_{R2} & = & \frac{R_2}{R_2 + R_1} . V_{AB}
\end{eqnarray}
$$


## Atividades

Calcular a resistência equivatente total dos circuitos.

### Circuito 1
Dados:
$R_1 = 1k2\Omega$,
$R_2 = 300\Omega$ e
$R_3 = 120\Omega$.

![Atividade 1](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-ativ1-1.png?raw=true)

### Circuito 2
Dados:
$R_1 = 2k7\Omega$,
$R_2 = 24k\Omega$,
$R_3 = 3k3\Omega$ e
$R_4 = 200\Omega$.

![Atividade 2](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-ativ2-1.png?raw=true)

### Circuito 3
Dados:
$R_1 = 100\Omega$,
$R_2 = 100\Omega$,
$R_3 = 100\Omega$,
$R_4 = 300\Omega$,
$R_5 = 200\Omega$,
$R_6 = 100\Omega$, e
$R_7 = 100\Omega$.

![Atividade 3](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/fig/fig-ativ3-1.png?raw=true)


## Download

[Nota de aula em PDF](https://github.com/JoseWRPereira/aula-ele-calculaReqOhm/blob/master/pdf/aula-ele-calcReq-1LeiOhm.pdf?raw=true)
