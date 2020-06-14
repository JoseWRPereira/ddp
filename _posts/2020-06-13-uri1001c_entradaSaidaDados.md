---
title:  "URI1001 - Entrada e Saída de Dados"
date:   2020-06-13 17:11:21
categories: ProgC
badges:
 - type: success
   tag: C
---

# [Extremamente Básico](https://www.urionlinejudge.com.br/judge/pt/problems/view/1001)

O problema inicial solicita que o programa faça a leitura de dois valores do tipo inteiro, some-os, e exiba uma mensagem com esse resultado.

A primeira dúvida é: **como ler um número digitado pelo usuário e armazená-lo em uma variável?**

<!--more-->

## Estrutura básica de um programa em C

Todo programa em linguagem C é estruturado em funções. Uma única função principal e obrigatória, `main()`, que denota o início da execução do programa.

```c
int main( void )
{

  return( 0 );
}
```

A execução do programa basicamente é realizada através do processador que lê dados nas memórias e manipula-os de acordo com a sequencia de instruções do programa, que é armazenada em uma das memórias.

Assim, tudo é leitura, manipulação e escrita de dados. A manipulação de dados envolve operações lógicas, aritméticas e de movimentação de dados.

Para um programa poder interagir um periférico como tela, teclado, mouse, impressora, câmera ou qualquer outro, é necessário que esse periférico esteja mapeado em uma região de memória, ou seja, um espaço de memória é reservado para configurar, parametrizar e trocar dados com o periférico.

Ao inserir um dispositivo novo ao sistema, um novo espaço deve ser mapeado, mas para computadores de uso geral, alguns dispositivos são denominados de padrão, ou seja, todo computador tem uma entrada padrão e uma saída padrão, que é o teclado e o monitor, respectivamente.

Para manipular dados nesses dispositivos padrão, é necessário incluir funções existentes na instalação do compilador no sistema operacional.
Essas funções estão presentes na biblioteca `stdio.h`: Entradas e Saídas Padrão (**St**an**d**ard **I**nput **O**utput).


### [stdio.h](http://www.cplusplus.com/reference/cstdio/)

Para inclusão utilizar `#include`, indicar que a bilioteca é nativa da instalação `<` e `>` entre o nome da bilioteca, que deve possuir uma extensão `.h` para indicar que é o seu cabeçalho ([*header*](https://www.w3schools.in/c-tutorial/c-header-files/)).

Os arquivos de inclusão não são os arquivos fonte, mas sim os arquivos de cabeçalho, que possuem as informações necessárias para a chamada das funções presentes nessa biblioteca.


```c
#include <stdio.h>
int main( void )
{

  return( 0 );
}
```

## [Leitura e escrita de dados](https://www.w3schools.in/c-tutorial/input-output/)

A leitura de dados é feita utilizando a função `scanf()` e a escrita utilizando a função `printf()`, sendo que ambas utilizam uma quantidade variável de argumentos, mas seu primeiro argumento é um formato de caracteres.


### [O formato](https://www.w3schools.in/c-tutorial/format-specifiers/)

Basicamente se trata de uma [cadeia de caracteres](https://www.w3schools.in/c-tutorial/strings/) (*string*) que possui uma mensagem a ser enviada à saída padrão, ou como devem ser lidos da entrada padrão.

```c
"Mensagem de exibicao"
```
Podendo ser incluida a indicação de variável na posição que ela deve aparecer utilizando o `%` e o seu tipo.

```c
"Exibe a variavel %d "
```
Após o formato são incluidas as variáveis que substituem as marcações na string, na ordem em que elas aparecem.

### [scanf()](https://en.cppreference.com/w/c/io/fscanf)

Leitura de um dado que é armazenado na [variável](https://www.w3schools.in/c-tutorial/variables/) num.
```c
int num;
scanf("%d", &num );
```
Leitura de dois dados que são armazenado nas variáveis A e B.
```c
int A, B;
scanf("%d", &A );
scanf("%d", &B );
```

Ou ainda:

```c
int A, B;
scanf("%d %d", &A, &B );
```

Os argumentos seguintes ao formato devem ser os endereços das variáveis que vão receber os dados lidos da entrada padrão conforme o formato do primeiro argumento.

### [print()](https://en.cppreference.com/w/c/io/fprintf)
Exibição de dados da variável soma.

```c
printf("X = %d", soma );
```
No lugar da marcação `%d` deve ser inserido o conteúdo da variável soma.

Todo apresentação de dados na plataforma URI devem possuir um fim de linha, denotado pelo caractere `\n`, equivalente à tecla Enter.    


## Resolução
O resultado completo para o desafio
[URI 1001 Extremamente Básico](https://www.urionlinejudge.com.br/judge/pt/problems/view/1001?_blanck) na minha formulação é:


```c
#include <stdio.h>
int main( void )
{
  int A, B, xis;
  scanf("%d", &A );
  scanf("%d", &B );
  xis = A + B;
  printf("X = %d\n", xis );
  return( 0 );
}
```
