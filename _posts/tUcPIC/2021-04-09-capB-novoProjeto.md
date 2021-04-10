---
layout: post
title: "Anexo B - Novo Projeto"
date: 2021-04-10 17:27:21 -0300
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



# Projeto

Um **programa para o microcontrolador** é composto por **diversos arquivos fontes, escritos em** alguma linguagem de programação, costumeiramente a **linguagem C**. 

Esses **arquivos são agrupados, organizados** e acompanhados de outros arquivos necessários para a construção de **um projeto**.

Um projeto é composto por arquivos fonte e de cabeçalho(**.c e .h**), arquivos para sua construção (***makefile***) no processo de compilação, arquivos de montagem (***assembly***), diversos arquivos intermediários e por fim o arquivo executável (**.hex**).

## Objetivo

Criar um novo projeto utilizando a plataforma MPLAB-X.

<!--more-->

## MPLAB-X

O ambiente de desenvolvimento integrada (*Integrated Development Environment* - IDE) é uma ferramenta que reúne (integra) diversas funcionalidades de apoio ao desenvolvimento de aplicações ou projetos, tais como um editor de código, colorização e destaque de palavras reservadas, chamadas ao compilador, navegação entre os arquivos, entre outras funções.


| Figura 1: IDE Microchip MPLAB-X |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/01.png{{site.rawimg}}) |




Para a criação de um novo projeto, basta seguir os passos apresentados pelo assistente de configuração do projeto, acessando-o conforme ilustração da Figura 2.

Clique em: ***File*** -> ***New Project***


| Figura 2: Novo projeto |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/02.png{{site.rawimg}}) |


Na etapa seguinte é necessário escolher o tipo de projeto que será criado.

Utilizaremos a opção ***Standalone Project***, que geralmente já vem selecionada, bastando clicar em ***Next***.

| Figura 3: Escolha do projeto |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/03.png{{site.rawimg}}) |


Na próxima etapa são escolhidos a **família** do microcontrolador, dentro dela o \textbf{dispositivo} e por fim a **ferramenta** de gravação do dispositivo físico se for o caso, não sendo, pode-se usar a opção do simulador.

* *Family*: **Mid-Range 8-bit MCUs**;
* *Device*: **PIC16F887**;
* *Tool*: **Simulator**.

| Figura 4: Seleção do dispositivo |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/04.png{{site.rawimg}}) |


Obs.: No casso do campo *Device*, a digitação do código do microcontrolador é mais prática e rápida do que sua escolha na caixa de opções. 

Selecione agora o compilador, que neste caso é o **XC8**, conforme a instalação.

| Figura 5: Seleção do compilador |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/05.png{{site.rawimg}}) |

Insira agora o nome do projeto e atente-se para o local em que ele será salvo.

O nome do projeto deve ter relação direta com a sua funcionalidade.

| Figura 6: Nome do projeto |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/06.png{{site.rawimg}}) |

Ao final a Figura 7 mostra a árvore do projeto criada, sendo que todas as pastas criadas devem estar vázias, exceto pelo arquivo *Makefile*, que não deve ser modificado ou alterado. 

| Figura 7: Projeto criado |
|:---------------------------------------------:|
| ![IDE MPLAB-X]({{site.baseurlimg}}/_posts/tUcPIC/capB-newProject/07.png{{site.rawimg}}) |


O projeto foi criado com sucesso, agora é preciso criar os arquivos fontes e de cabeçalho. 

<hr/>

>>> [<< Anexo A - Instalação do MPLAB-X e XC8]({{site.baseurl}}/2021/capA-instalacao) << Anexo B - Novo Projeto >> [Anexo C - Novos arquivos >>]({{site.baseurl}}/2021/capC-novosArquivos)

<hr/>


[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
