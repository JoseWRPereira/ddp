---
layout: post
title:  "Estatística"
date:   2022-06-03 21:03:21 -03:00
categories: Computação
badges:
 - type: primary
   tag: UniVESP
 - type: secondary
   tag: Computação
---

# [Estatística](https://www.youtube.com/playlist?list=PLxI8Can9yAHdJq561NyRN9wZpTqVJn0Z0)

Associa dados dos problemas gerando informações relevantes para o estabelecimento de conclusões capazes de viabilizar a tomada de decisões em ambientes de incertezas e variações.

A estatística trata então dos processos que apresentam um grau de variabilidade em seu comportamento ou nos seus resultados, buscando responder as seguintes questões:
* Que **tipo** de informações são necessárias?
* Qual a **quantidade** de informações é suficiente?
* Como **processar** estas informações?

Divide-se em três áres principais:
* Probabilidade;
* Estatística descritiva;
* Estatística indutiva.


<!--more-->

## Probabilidade

Estudo da **eleatoriedade** e **incerteza**, medida de informação sobre a ocorrência de um evento.

| | Definição | |
|:-----:|:---:|:-----:|
| Frequencialista | |Clássica |
| $$ p = \lim_{n\rightarrow \infty} \frac{m}{n} $$ | | $$ P = \frac{M}{N} $$|
| | | |
| Onde: | p, P <br/> m, M <br/> n, N| Probabilidade <br/> Núm. de Sucessos <br/>  Núm. de Possibilidades | 
|---|---|---|

### Espaço Amostral (S)
Conjunto ou coleção definida de objetos ou itens, com todos os possíveis resultados.

Exemplos: 

* Lançamento de uma moeda: $$ S = \{ C, K \} $$ 
* Lançamento de um dado: $$ S = \{ 1, 2, 3, 4, 5, 6 \} $$ 
* Lançamento de duas moedas: $$ S = \{ (C,C), (C,K), (K,C), (K,K) \} $$

### Eventos Aleatórios (E)
Qualquer subconjunto de um espaço amostral. 

Resultado possível em experimentos aleatórios e que não é previsível.

|      Propriedades       |
|:-----------------------:|
|  $$ 0 \le P(E) \le 1 $$ |
|      $$ P(S) = 1 $$     |


| Lançamentos | moeda | dado |
|:---|:---|:----|
| Espaço Amostral <br/> Evento Aleatório <br/> Probabilidade(Evento) |  $$ S = \{ C,K \} $$ <br/> $$ E = K $$ <br/> $$ P(E) = \frac{1}{2} $$ | $$ S = \{ 1,2,3,4,5,6 \} $$ <br/> $$ E = 3 $$ <br/> $$ P(E) = \frac{1}{6} $$ |

#### Evento Complementar

#### Evento Equiprovável

Para um dado honesto:

$$ P(1) = P(2) = P(3) = P(4) = P(5) = P(6) $$


#### Eventos Mutuamente Excludentes

$$ A \Rightarrow \neg B $$

$$ B \Rightarrow \neg A $$

#### Operações Entre Eventos

União: $$ A \cup B $$

Intersecção: $$ A \cap B $$

#### Axiomas da probabilidade

1. Se $$ \varnothing $$ é o conjunto vazio (evento impossível), então: $$ P(0) = 0 $$  $$ P(A \cup B) = 0 $$
2. Se $$ \overline{A} $$ é o complemento do evento $$ A $$ então: $$ P(\overline{A}) = 1 - P(A) $$ 
3. Se $$A$$ e $$B$$ são dois eventos quaiquer, então: 
   1. $$ P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
   2. $$ P(A \cup B) = P(A) + P(B)$$ (A e B mutuamente excludentes)
   3. $$ P(A \cup B \cup C) = P(A) + P(B) + P(C) - P(A \cap B) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C) $$

## Teoria da Contagem

### Combinação

$$ C_{n,p} = \binom{n}{p} = \frac{n!}{p!(n-p)!}$$

n: número de elementos do conjunto amostral

p: número de elementos escolhidos

C: número de combinações possíveis

Ordem dos elementos **não faz diferença**.

### Arranjos

$$ A_{r,p} = \frac{r!}{(r-p)!}$$

r: número de elementos do conjunto amostral

p: número de elementos escolhidos

A: número de combinações possíveis

Ordem dos elementos **faz diferença**.

<hr/>

[Voltar]({{site.baseurl}}/docs/tecnologia)