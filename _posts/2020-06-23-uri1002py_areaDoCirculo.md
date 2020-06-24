---
title:  "URI1002 - Formatação de casas decimais"
date:   2020-06-23 20:20:21
categories: ProgPy
badges:
 - type: primary
   tag: Python
---

# [Área do Círculo](https://www.urionlinejudge.com.br/judge/pt/problems/view/1002)

O problema solicita que o programa calcule a área de um círculo dado o valor do raio.

Para o cálculo da área é utilizada a seguinte equação: `area = n.raio²`.

<!--more-->

## Entrada de dados

O dado de entrada do programa é o `raio`, que é modelado para o tipo [float](https://www.w3schools.com/python/python_datatypes.asp): 

```python
raio = float(input())
```

## Processamento

Então para o processamento da área pode-se utilizar o produto do raio, por ele mesmo e o valor aproximado do PI, que é declarado em `n`.

```python
n=3.14159
area=n*raio*raio
```

## Saída de dedos

**Como formatar a saída para um determinado número de casas decimais?**

A saída deve ser apresentada com quatro [casas decimais](https://pt.stackoverflow.com/questions/176243/como-limitar-n%C3%BAmeros-decimais-em-python) utilizando `{:.4f}`.

```python
print("A={:.4f}".format(area))
```


## Resolução

Juntando as partes na resolução do desafio temos:

```python
raio = float(input())
n=3.14159
area=n*raio*raio
print("A={:.4f}".format(area))
```
