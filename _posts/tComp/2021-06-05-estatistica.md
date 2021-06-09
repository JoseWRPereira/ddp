---
layout: post
title:  "Estatística"
date:   2021-06-05 19:45:21 -03:00
categories: Computação
badges:
 - type: primary
   tag: UniVESP
 - type: secondary
   tag: Computação
 - type: secondary
   tag: Estatística
 - type: secondary
   tag: Notas de aula
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


# Teoremas da probalidade

## Probabilidade condicional

* Dados dois eventos possíveis: A e B
* Ocorreo evento B
* B é o novo espaço amostral
* Assim: 
  * $$ P( A | B ) = \frac{P(A \cap B)}{P(B)} $$

**Teorema do produto**

$$ P(A \cap B) = P(B).P(A|B) $$

$$ P(A \cap B) = P(A).P(B|A) $$


### Eventos independentes
O evento B não altera a probabilidade de ocorrer A.

$$ P(A|B) = P(A) $$

Evento intersecção

$$ P(A \cap B) = P(A).P(B) $$

### Teorema de **Bayes**

$$ P(B) = \sum\limits_{i=1}^n  P(A_i \cap B) = \sum\limits_{i=1}^n P(A_i).P(B|A_i) $$

### Variáveis aleatórias
Atribuir descrição numérica aos resultados dos experimentos.

* Variável aleatória discreta
  * $$ P(X=X_0) \ge 0 $$
  * $$ \sum P(X=X_0) = 1  $$
* Variável aleatória contínua
  * Uso de escala contínua.


## Proposições das distribuições de probabilidade

### Esperança matemática (**Média**)
$$ \mu = E(x) = \sum X_i.p(X_i) $$
$$ \mu = E(X) = \sum\limits_{-\infty}^{+\infty} x.f(x) dx $$

#### Variância VAR(X) e desvio padrão
Grau de dispersão de probabilidade em torno da média.

$$ \sigma^2 = \sum (X_i - \mu)^2.p(X_i) = E[(X-\mu)²] $$

$$ \sigma^2 = [\sum x^2.p(X)] - \mu^2 = E(X^2)-[E(X)]^2 $$

#### Propriedades da média

$$ E(k) = k $$ , se k é constante

$$ E(X.k) = k.E(X) $$

$$ E(X+Y) = E(X) + E(Y) $$

$$ E(X-Y) = E(X) - E(Y) $$

$$ E(X.Y) = E(X).E(Y) $$, X e Y independentes


#### Propriedades da variância

$$ \sigma^2(k) = 0 $$, se k é constante

$$ \sigma^2(X.k) = k^2.\sigma^2(X) $$

$$ \sigma^2(X+Y) = \sigma^2(X)+\sigma^2(Y)$$, X e Y independentes

$$ \sigma^2(X-Y) = \sigma^2(X)+\sigma^2(Y)$$, X e Y independentes

$$ Desvio padrão = \sqrt{variância} $$

### Mediana
Valor numérico que separa o conjunto pela metade.

### Moda
Valor numérico de maior frequência.


# Distribuição de Bernoulli
* Experimento aleatório;
* Realizado repetidas vezes (tentativas);
* Mantidas as condições;
* Resultado: sucesso ou fracasso.

* P(sucesso)  = p
* P(fracasso) = q = 1 - p
* $$ P = q^k.q^{1-k}, k \in \{0,1\} $$

# Distribuição Binomial
* N provas independentes;
* Sucesso ou fracasso (Bernoulli);
* P(sucesso) = P \Rightarrow const
  
  $$ P(X=k) = \binom{n}{k}.p^k.q^{n-k} $$

  $$ \binom{n}{k} = \frac{n!}{k!(n-k)!} $$

  $$ \mu = n.p $$ (Média)

  $$ \sigma²(x) = n.p.q $$ (Variância)

# Distribuição de Poisson

* Hipóteses:
  * Eventos definidos em intervalos não sobrepostos são independentes;
  * $$\lambda$$ é constante no intervalo estudado.

$$ \lim_{n \rightarrow \infty}  Binomial = Poisson $$

**Simon Denis Poisson (1781 - 1840)**

$$ P(X=k) = \frac{e^{-\lambda t} (\lambda t)^k}{k!} $$

* Exemplo:
  * Semáforo:
    * $$\lambda = 4$$ veículos por minuto;
    * $$t = 2 min.$$ intervalo de tempo;
    * $$P(X=7) = ?$$


    * $$\mu = \lambda.t = 4.2 = 8$$ (média)
    * $$ P(X=7) = \frac{e^{4.2}.(4.2)^7}{7!} = 0,1396 $$


# Distribuição Normal (Gaussiana)

**Johann Carl Friedrich Gauss(1777-1855)**

## Teorema do limite central
A soma de infinitas variáveis independentes segue uma distribuição normal.


$$ f(x) = \frac{1}{\sigma\sqrt{2\pi}} . e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2} $$

$$ -\infty < x < +\infty $$

* $$\mu$$: média
* $$\sigma$$: desvio padrão

### Tabela Normal Reduzida

$$ Z = \frac{X - \mu}{\sigma} $$

* $$X$$: Valor de interesse;
* $$\mu$$: Média;
* $$\sigma$$: desvio padrão
* $$E(Z) = 0$$
* $$\sigma^2(Z) = 1$$

# Amostragem

* Método estatístico
  * Coleta;
  * Organização;
  * Apresentação;
  * Análise;
  * Interpretação de dados experimentais.

* Objetivo:
  * Estudo dos parâmetros de uma população.

* Tipos:
  * Censo: Todos os elementos da população.
  * Amostragam: **seleção representativa** de alguns elementos da população - pesquisa em uma amostra.
    * Aleatória simples;
    * Aleatória estratificada;
    * por conglomerado;
    * sustemática.

## Métudo estatístico
* Definição do problema;
* Planejamento da pesquisa;
* Coleta dos dados;
* Apuração dos dados;
* Apresentação dos dados;
* Análise e interpretação dos dados: Inferência estatística.




## Amostragem Aleatória Simples

$$ {n \choose k} = \frac{n!}{k!(n-k)!} $$

## Elementos de uma distribuição de frequência

$$ K = \sqrt{N} $$

Onde:
K: número de classes
N: número de elementos numa amostra.

* Amplitude:
  * diferença entre o menor e o maior valor;
* Classes: 
  * Intervalos de variação de variável;
* Amplitude de um intervalo de classe H: $$ H = \frac{A}{K} $$
* Verificação:
  * $$ P_o + K.H > P_N $$
  * Onde:
    * $$P_0$$: Menor elemento;
    * $$K$$: Número de classes;
    * $$H$$: Amplitude de classe;
    * $$P_N$$: Manior elemento.


# Medidas de posição e dispersão

* Estatística descritiva
  * Tabelas;
  * Distribuição de frequência;
  * Histograma.

* Medias de posição:
  * Localizar a **maior concentração de valores** de uma distribuição;
  * **Sintetizar o comportamento** do conjunto do qual ele é originário;
  * Possibilitar **comparações** entre séries de dados.

* Média aritmética simples

$$ \overline x = \frac{\sum\limits_{i=1}^n x_i}{n} $$

* Média aritmética ponderada

$$ \overline x_p = \frac{\sum\limits_{i=1}^n x_i p_i}{\sum\limits_{i=1}^n p i} $$


Onde: 
$$X_i$$: valor observado;
$$n$$: número de observações;
$$p$$: ponderação.

* Moda (Mo)
  * Valor que ocorre com maior frequência em um conjunto de dados.
    * Multimodal;
    * Amodal.
* Mediana ($$M_d$$)
  * **Separatriz**: divide o conjunto em dus partes iguais, com o mesmo número de elementos.
  * **Centro** da série estatística organizada.

# Medidas de dispersão

* Variabilidade
* Amplitude total
* Variância ($$S^2$$)
  * População: $$ S^2 = \Sigma_{i=1}^N \frac{(x_i-\overline x)^2}{N}$$
  * Amostra: $$S^2 = \Sigma_{i=1}^n \frac{(x_i-\overline x)^2}{n-1}$$


# Inferência estatística
**Conhecer**, de maneira aproximada, as **características** de uma grande **população** a partir de **informações** obtidas de uma **amostra**.

* Grau de incerteza ou risco.

* População: todas observações possíveis.
* Amostra: conjunto de dados que inclui uma parte significativa dessas observações.
* Parâmetro
* Estimador

* População $$\rightarrow$$ Amostra $$\rightarrow$$ Estimadores $$\rightarrow$$ Parâmetros.
  * Parâmetros.

| Parâmetros | População | Amostra |
|:----------:|:---------:|:-------:|
| Média      | $$\mu$$   | $$\overline x $$|
|Desvio padrão| $$\sigma$$|$$S$$|
|Proporção|$$\pi$$|$$p$$|



<hr/>

[Voltar]({{site.baseurl}}/docs/tecnologia)