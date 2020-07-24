---
layout: post
title:  "URI1010 - Entrada de múltiplas variáveis por linha"
date:   2020-06-23 20:53:21
categories: ProgPy
badges:
 - type: primary
   tag: Python
---

# [Cálculo Simples](https://www.urionlinejudge.com.br/judge/pt/problems/view/1010)

O problema solicita que o programa leia três números referentes a primeira peça e outros três números na linha seguinte referentes a segunda peça. Os números de cada uma das peças são: seu código (inteiro), sua quantidade (inteiro) e seu valor unitário (float).

O problema aqui encontrado é **como fazer a entrada desses três parâmetros por linha?**

<!--more-->

## Entrada de dados

Para ler mais do que um valor por linha de [entrada de dados](https://pt.stackoverflow.com/questions/230522/entrada-de-n%C3%BAmeros-na-mesma-linha-em-python) pode-se utilizar o método `input().split(" ")` sendo  o `" "` o caractere que [separa em partes](https://www.deepl.com/translator#en/pt/split) a string de entrada. 

```python
codigo1,qtd1,valor1=input().split(" ")
codigo2,qtd2,valor2=input().split(" ")
```

Em python é possível que uma função retorne múltiplos valores, diferente da linguagem C, que só pode retornar apenas um valor por função. 


## Modelamento dos dados de entrada

Os dados lidos são modelados para os devidos tipos:

```python
codigo1=int(codigo1)
qtd1=int(qtd1)
valor1=float(valor1)

codigo2=int(codigo2)
qtd2=int(qtd2)
valor2=float(valor2)
```

## Saída de dedos
O cálculo é realizado direto no argumento do método `.format()`.

```python
print("VALOR A PAGAR: R$ {:.2f}".format(qtd1*valor1+qtd2*valor2))
```


## Resolução

Juntando as partes na resolução do desafio temos:

```python
codigo1,qtd1,valor1=input().split(" ")
codigo2,qtd2,valor2=input().split(" ")

codigo1=int(codigo1)
qtd1=int(qtd1)
valor1=float(valor1)

codigo2=int(codigo2)
qtd2=int(qtd2)
valor2=float(valor2)

print("VALOR A PAGAR: R$ {:.2f}".format(qtd1*valor1+qtd2*valor2))
```
