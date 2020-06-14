---
title:  "URI1001 - Entrada e Saída de Dados"
date:   2020-06-13 16:04:21
categories: ProgPy
badges:
 - type: primary
   tag: Python
---

# [Extremamente Básico](https://www.urionlinejudge.com.br/judge/pt/problems/view/1001)

O problema inicial solicita que o programa faça a leitura de dois valores do tipo inteiro, some-os, e exiba uma mensagem com esse resultado.

A primeira dúvida é: **como ler um número digitado pelo usuário e armazená-lo em uma variável?**

<!--more-->

## Leitura de dados
Com uma busca rápida no Google, encontrei o a resposta para a leitura de dados em [w3schools.com](https://www.w3schools.com/python/ref_func_input.asp?_blank).

### input()
A função `input()` realiza a leitura de uma cadeia de caracteres (string) da entrada padrão (teclado). O resultado lido é atribuído a variável *a*, `a = input()`. O tipo da variável é definida dinamicamente, ou seja, no momento que é feita a atribuição do dado, este é reconhecido e a variável é declarada com esse mesmo tipo, nesse caso, string.

Mas é necessário que, após as leituras dos dois valores, seja feita a soma, ou seja, as entradas devem ser números e não cadeias de caracteres (string).

**Como converter a string lida em um número do tipo inteiro?**

### Casting
O processo para a conversão entre tipos de dados é chamado de
[casting](https://www.w3schools.com/python/python_casting.asp?_blank), onde um dado sofre uma [modelagem](https://translate.google.com.br/?hl=pt-BR#view=home&op=translate&sl=en&tl=pt&text=casting) do seu tipo original para o tipo desejado.

Assim, a entrada de dados é feita pela função `input()`, cujo resultado é modelado para o tipo inteiro e por fim atribuído a variável `a`.
O mesmo ocorre para a variável `b`. Em seguida a variável `soma` recebe o resultado da operação de [soma](https://www.w3schools.com/python/python_operators.asp?_blank) entre elas.

```python
a = int( input() )
b = int( input() )
soma = a + b
```

### print()
Por fim a apresentação do resultado, que pode ser feita utilizando a função `print()`, mas como inserir uma variável no meio da string?

### Presentation Error
Uma primeira forma encontrada foi `print("X = ", soma )`, porém a plataforma avaliava com erro de apresentação, *Presentation error*.

### Especulação
Entre devaneios e **especulações**, imagino que o problema ocorra pela composição de `string + variável` apresentada na saída padrão. Ao concatenar(juntar) a string com a variável na exibição, no meio dessa união deve ficar o terminador de string: `'\0'`. Exemplo: `a=4` e `b=5` então `soma=9`. A saída do comando `print("X = ", soma)`, especulo que seja "X = '\0' 9", ou seja, para a saída padrão, são duas strings exibidas na tela, mesmo que uma após a outra, mesmo que visualmente pareça comprir as exigências, pois o `'0'` não aparece na tela.

**Cuidado!** Isso é uma especulação, estou aprendendo python.

### .format()
Duas outras ótimas fontes de pesquisa são: [stack**overflow**](https://pt.stackoverflow.com/questions/225498/formatando-strings-com-format-e) e a própria documentação da linguagem [docs.python.org](https://docs.python.org/3/library/string.html#custom-string-formatting).

## Resolução
O resultado completo para o desafio
[URI 1001 Extremamente Básico](https://www.urionlinejudge.com.br/judge/pt/problems/view/1001?_blanck) na minha formulação é:


```python
a = int( input() )
b = int( input() )
soma = a + b
print("X = {}".format( soma ) )
```
