---
layout: post
title: "Anexo C - Novos Arquivos"
date: 2021-04-10 17:40:21 -0300
author: José W. R. Pereira
categories: ucPIC
badges:
 - type: warning
   tag: Microcontrolador
 - type: secondary
   tag: PIC
 - type: secondary
   tag: PIC16F887
 - type: danger
   tag: MPLABX-XC8
   mathjax: true
---



# Arquivo fonte (.c) e de cabeçalho (.h)

Dentro de um projeto para microcontrolador, são criados basicamente arquivos fonte e de cabeçalho. 

Os arquivos **fontes** são aqueles com extensão **.c** e são escritos seguindo a sintaxe da linguagem de programação C, a mais utilizada para este tipo de aplicação.

Os arquivos de **cabeçalho** (*header*) são aqueles com a extensão **.h** e são utilizados como apresentação de funções em arquivos fontes diferentes de onde estão declaradas, permitindo assim que elas sejam invocadas (chamadas). 

## Objetivo

Criar um arquivo fonte no projeto utilizando a plataforma MPLAB-X.

<!--more-->


## Criação de arquivo fonte **.c**

São vários os arquivos **.c** em um projeto, mas todos são criados da mesma forma. 

A seguir a sequência para a criação de um arquivo **.c**.


* Clique com o botão direito do *mouse* em ***Source Files***;
* Selecione ***New***;
* Em seguida selecione qualquer opção de arquivo com extensão **.c**.

| Figura 1: Novo arquivo fonte |
|:---------------------------------------------:|
| ![Novo arquivo fonte]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/01.png{{site.rawimg}}) |



* No campo ***File Name*** digite o nome do arquivo. 	Não é necessário inserir a extensão, 	pois já está definido no campo abaixo.

| Figura 2: Nome do arquivo |
|:---------------------------------------------:|
| ![Nome do arquivo]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/02.png{{site.rawimg}}) |

Ao finalizar o arquivo fonte é aberto com algumas linhas inicializadas. 
Note que ele foi criado dentro do diretório de arquivos fonte, ***Source Files***.

| Figura 3: Arquivo fonte |
|:---------------------------------------------:|
| ![Arquivo fonte]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/03.png{{site.rawimg}}) |

O arquivo fonte criado pela IDE já possui algumas linhas inicializadas, e neste caso com um bloco de comentário no início do arquivo com algumas informações como o nome do arquivo, seu autor e data de sua criação.

Em seguida temos a inclusão de biblioteca padrão, para os microcontroladores de 8 bits da Microchip, disponibilizada na instalação do compilador **XC8**.

Por fim uma função **main** mínima. 

Caso o arquivo fonte criado não contenha a função **main**, o que vai ser o mais comum, simplesmente apague-a e insira as funções do seu projeto. 



## Criação de arquivo de cabeçalho **.h**

Normalmente para cada arquivo **.c**, vai existir um arquivo correspondente **.h**.

* Clique com o botão esquerdo do *mouse* no diretório ***Header Files***;
* Selecione ***New***;
* Selecione algum arquivo com extensão **.h**.

| Figura 4: Novo cabeçalho |
|:---------------------------------------------:|
| ![Arquivo fonte]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/04.png{{site.rawimg}}) |


O passo seguinte é inserir no campo *File Name* o nome do arquivo.

Note que a extensão deve estar com a seleção em **.h**.

Verifique se os campos *Project* e *Created File* estão com os valores corretos, com o nome do projeto ao qual esse arquivo que está sendo criado pertence e seu respectivo local. 

Estando tudo correto:
* Clique em ***Finish***.

| Figura 5: Nome e local do arquivo de cabeçalho |
|:---------------------------------------------:|
| ![Nome e local do arquivo de cabeçalho]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/05.png{{site.rawimg}}) |


O arquivo de cabeçalho é criado e vem com as condições de uso do software, 
produzidos pela Microchip.

| Figura 6: Condições de uso do software |
|:---------------------------------------------:|
| ![Condições de uso do software]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/06.png{{site.rawimg}}) |


* Delete todo o conteudo do arquivo. 
  * Você pode utilizar o atalho através da sequência de teclas: ***Ctrl+A*** e em seguida ***Delete***.
* Insira o **#ifndef** com o respectivo nome do arquivo, em letras maiúsculas, e finalizado com **_H** no lugar do **.h**.

```c
#ifndef ARQUIVOCABECALHO_H
#define ARQUIVOCABECALHO_H

/* Inserir aqui os cabecalhos */

#endif
```	

Agora é só inserir os protótipos de funções, definições de tipos, de acordo com a sua necessidade como programador. 

| Figura 7: Arquivo de cabeçalho |
|:---------------------------------------------:|
| ![Arquivo de cabeçalho]({{site.baseurlimg}}_posts/tUcPIC/capC-novosArquivos/07.png{{site.rawimg}}) |

<hr/>

>>> [<< Anexo B - Novo Projeto]({{site.baseurl}}/2021/capB-novoProjeto) << Anexo C - Novos Arquivos >> [Anexo D - Controle de Versão >>]({{site.baseurl}}/2021/capD-versionamento)


<hr/>

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
