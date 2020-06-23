---
title:  "URI1009 - Cadeia de caracteres"
date:   2020-06-22 23:40:21
categories: ProgC
badges:
 - type: success
   tag: C
---

# [Salário com Bônus](https://www.urionlinejudge.com.br/judge/pt/problems/view/1009)

O problema pede que o programa leia o nome do vendedor, seu salário e o valor de suas vendas no mês, calcule e exiba o salário a receber já acrescido com o bônus.

<!--more-->

## Entrada de dados

Os dados de entrada contém um texto com o primeiro nome do vendedor e 2 valores de dupla precisão com duas casas decimais, representando o salário fixo do vendedor e montante total das vendas efetuadas por este vendedor, respectivamente.

Para a entrada com o nome do vendedor é declarado um vetor com o número de elementos suficiente para um nome. O valor aqui escolhido foi o `20`. 

Em linguagem C não existe o tipo `string`, para armazenar a [cadeia de caracteres](http://linguagemc.com.br/string-em-c-vetor-de-caracteres/) é utilizado o `%s` e um vetor `char nomeVendedor[20]`.

```c
  char nomeVendedor[20];
  double salarioFixo, montanteVendas;

  scanf("%s",  nomeVendedor );
  scanf("%lf", &salarioFixo );
  scanf("%lf", &montanteVendas );
```


## Saída de dedos com Processamento

A saída deve ser apresentada com duas casas decimais por ser um valor monetârio, utilizando `%.2f` e o valor a ser exibido pode ser calculado diretamente no campo do parâmetro.

```c
  printf("TOTAL = R$ %.2f\n", salarioFixo + montanteVendas * 0.15 );
```


## Resolução

Juntando as partes na resolução do desafio temos:

```c
#include <stdio.h>

int main( void )
{
  char nomeVendedor[20];
  double salarioFixo, montanteVendas;

  scanf("%s",  nomeVendedor );
  scanf("%lf", &salarioFixo );
  scanf("%lf", &montanteVendas );

  printf("TOTAL = R$ %.2f\n", salarioFixo + montanteVendas * 0.15 );
  return( 0 );
}
```
