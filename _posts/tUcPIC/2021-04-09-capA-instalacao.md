---
layout: post
title: "Anexo A - Instalação do MPLAB-X e XC8"
date: 2021-04-10 17:17:21 -0300
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



# Instalação de IDE e Compilador

Para o desenvolvimento de projetos para microcontroladores das famílias PIC e AVR, a Microchip disponibiliza o ambiente de desenvolvimento integrado (*Integrated Development Environment - IDE*) **MPLAB-X** e compiladores para as diversas arquiteturas disponíveis.

## Objetivo

Realizar a instalação da IDE MPLAB-X e do compilador XC8 em sistema operacional GNU/Linux (Debian).

<!--more-->

O **MPLAB-X** é uma ferramenta que reúne (integra) diversas funcionalidades de apoio ao desenvolvimento de aplicações ou projetos, tais como um editor de código, colorização e destaque de palavras reservadas, chamadas ao compilador, navegação entre os arquivos, integração com ferramentas de versionamento, entre outras funções.

O **XC8** é o compilador para dispositivos de 8 bits, os mais simples da família. Ele é o esponsável por traduzir o código escrito pelo programador em linguagem C na linguagem de execução do microcontrolador, ou seja, um cojunto de códigos binários com a sequência de passos logicamente ordenados a serem processados e executados pelo microcontrolador.

A Microhip disponibiliza em seu site o [MPLAB-X](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-x-ide) e o [XC-8](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-xc-compilers) de forma gratuita, bem como a versão online, o [MPLAB Xpress Cloud Based IDE](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-xpress).


## Versões
Existem diversas versões tanto da IDE quanto do compilador, e apesar da recomendação padrão ser o uso da versão mais recente, caso você use o gravador PICkit2, como é o meu caso, use a versão do compilador XC8 v1.45 e da IDE 4.40. 
A partir da versão da IDE 5.x não há mais suporte ao gravador citado, sendo necessária a utilização do PICkit3 ou mesmo o PICkit4.

Caso use apenas com simulador, a recomendação é usar as versões mais recentes de 
compilador e IDE.

## Instalação

A Microchip fornece um conjunto de ferramentas de desenvolvimento de forma gratuita e multiplataforma para programar os seus microcontroladores. 

Serão baixados apenas os dois programas mostrados na Figura 1.

| Figura 1: MPLAB X IDE e XC Compiler |
|:---------------------------------------------:|
| ![logos-IDE-XC]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/logos-IDE-XC.png{{site.rawimg}}) |


A IDE pode ser baixada diretamente do *site* onde pode-se escolher a versão adequada para o sistema operacional em que será realizada a instalação, Windows, **Linux** ou Mac.

O compilador precisa ser baixado e instalado separadamente, pois deve ser instalado em função da família e arquitetura do microcontrolador que será utilizado, podendo ser de 8, 16 ou 32 bits.
A compilação para os microcontroladores de 8 bits é realizada com o compilador XC8, 
que também pode ser obtido gratuitamente no [site](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-xc-compilers).

Versões anteriores à recorrente podem ser acessadas no [arquivo](https://www.microchip.com/development-tools/pic-and-dspic-downloads-archive) de downloads.

O **PICkit2** é a plataforma de software e hardware para a gravação do firmware na memória de programa do PIC. É uma versão descontinuada pela Microchip mas amplamente distribuida e de fácil montagem. 
Algumas informações adicionais podem ser encontradas em [pickit2](https://www.microchip.com/developmenttools/ProductDetails/pg164120).



## Instalação no GNU/Linux - MPLAB-X 32bits

O processo de instalação apresentado aqui é uma das possíveis opções devido ao caráter multiplataforma da IDE.

O sistema operacional que utilizo é o [Debian](https://www.debian.org/index.pt.html), assim, após o script de instalação baixado, atentar para alterar o seu privilégio da seguinte forma: 

```bash
curtaeletronica@uC:~$ chmod +x MPLABX-v3.15-linux-installer.sh
```

Ao executar o *script* de instalação do MPLAB-X IDE, para versões de 32 bits, 
sendo instalada em arquitetura de 64 bits, a seguinte mensagem é apresentada:

```bash
curtaeletronica@uC:~$ sudo ./MPLABX-v3.15-linux-installer.sh
[sudo] senha para curtaeletronica:
64 Bit, check libraries
Check for 32 Bit libraries
These 32 bit libraries were not found and are needed for MPLAB X to run:
libc.so
libdl.so
libgcc_s.so
libm.so
libpthread.so
librt.so
libstdc++.so
libexpat.so
libX11.so
libXext.so

For more information visit http://microchip.wikidot.com/install:mplabx-lin64

curtaeletronica@uC:~$
```


O *script* de instalação executa uma busca por dependências no sistema, ou seja,  bibliotecas, para a correta execução do programa a ser instalado. 

Para instalar as dependências a seguinte linha de comando pode ser executada: 

```bash
curtaeletronica@uC:~$ sudo apt install libc6:i386 lib32stdc++-10-dev libexpat1:i386 libx11-dev:i386 libxext-dev:i386
```

Com esse comando, as dependências devem ser atendidas. 

Informações relevantes, sobre a instalação das bibliotecas em um sistema baseado em Ubuntu/Debian, podem ser encontradas no [blog Edivaldo](https://www.edivaldobrito.com.br/suporte-a-32-bits-no-ubuntu-de-64-bits/) e em [microchipDevHelp](http://microchipdeveloper.com/install:mplabx-lin64). 


Após todas as dependências serem atendidas, a instalação é iniciada. 
Para versões com suporte a arquitetura de 64 bits, essas dependências não são necessárias. 


## Instalação da IDE

Para a instalação aqui apresentada é utilizada a versão para arquitetura de 64 bits, v5.45, conforme o comando que segue:

```bash
curtaeletronica@uC:~$ sudo ./MPLABX-v5.45-linux-installer.sh 
64-bit Linux detected.
Check for 64-bit libraries
Verifying archive integrity... All good.
Uncompressing MPLAB X v5.45 installer..
```

Um assistente do processo de instalação é aberto dando boas vindas, 
informando a versão que será instalada, que neste caso é a **MPLAB X IDE 5.45**, conforme Figura 2.

Para prosseguir, basta clicar em ***Forward***.


| Figura 2: Setup |
|:---------------------------------------------:|
| ![mp00-setup]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/ide-01-setup.png{{site.rawimg}}) |


A tela seguinte é do Contrato de Licensa, em que após leitura, estando de acordo:
* Selecione a opção ***I accept the agreement***;
* Em seguida clique em ***Forward***.

| Figura 3: Licensa |
|:---------------------------------------------:|
| ![Licensa]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/ide-02-license.png{{site.rawimg}}) |


* Escolha o diretório de instalação. 
  * Recomenda-se manter o local padrão. 
* Clique em ***Forward***.


| Figura 4: Diretório de Instalação |
|:---------------------------------------------:|
| ![Diretório de Instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/ide-03-instOptions.png{{site.rawimg}}) |


A tela a seguir apresenta a opção de instalação das aplicações de desenvolvimento e de programação, respectivamente IDE e IPE e logo abaixo as opções de compiladores para as arquiteturas de 8, 16 ou 32 bits, além de outras arquiteturas suportadas.

A recomendação é a instalação das opções conforme a Figura 5, 
pois as demais opções não são necessárias.

* Após a escolha das opções clicar em ***Forward***.

| Figura 5: Seleção de Ferramentas/Aplicações |
|:---------------------------------------------:|
| ![Seleção de Ferramentas/Aplicações ]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/ide-04-selectApp.png{{site.rawimg}}) |


O sistema está pronto para iniciar a instalação. 

* Clique em ***Forward***.

| Figura 6: Resumo da Instalação |
|:---------------------------------------------:|
| ![Resumo da Instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/ide-05-readyToInstall.png{{site.rawimg}}) |


A instalação segue em progresso, e o tempo depende do poder de processamento do 
computador que se está realizando a instalação, neste caso a duração foi inferior a três minutos.

## Instalação do compilador XC8

Após o compilador ter sido baixado e receber o privilégio de execução, basta iniciar e seguir os passos do assistente de instalação, conforme segue:

| Figura 7: Instalação do XC8 |
|:---------------------------------------------:|
| ![Instalação do XC8]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-01-setup.png{{site.rawimg}}) |


A tela seguinte é do Contrato de Licensa, em que após leitura, estando de acordo: 
* Selecionar a opção ***I accept the agreement***;
* Clique em ***Next***.

| Figura 8: Licensa da instalação |
|:---------------------------------------------:|
| ![Licensa da instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-02-license.png{{site.rawimg}}) |


No tipo de licensa usamos a versão ***free***.

| Figura 9: Tipo de instalação |
|:---------------------------------------------:|
| ![Tipo de instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-03-licenseType.png{{site.rawimg}}) |


É possível escolher o local da instalação do compilador, 
mas a recomendação é usar o diretório padrão, já indicado na instalação.

| Figura 10: Diretório de instalação |
|:---------------------------------------------:|
| ![Diretório de instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-04-instDirectory.png{{site.rawimg}}) |


Selecione as opções conforme segue, para que as configurações sejam atribuidos a todos os usuários da máquina (computador) além de compartilhar o caminho do xc8 na variável de ambiente.

| Figura 11: Parâmetros do compilador |
|:---------------------------------------------:|
| ![Parâmetros do compilador]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-05-compilerSettings.png{{site.rawimg}}) |


Última tela antes do início da instalação, caso queira realizar alguma alteração, a hora é agora.

| Figura 12: Pronto para instalar |
|:---------------------------------------------:|
| ![Pronto para instalar]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-06-ready.png{{site.rawimg}}) |


Instalação em progresso.

| Figura 13: Progresso da instalação |
|:---------------------------------------------:|
| ![Progresso da instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-07-installing.png{{site.rawimg}}) |


Informações da licensa. Apenas prossiga.

| Figura 14: Instalação completa |
|:---------------------------------------------:|
| ![Instalação completa]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-08-complete.png{{site.rawimg}}) |


Fim da instalação. 

| Figura 15: Fim da instalação |
|:---------------------------------------------:|
| ![Fim da instalação]({{site.baseurlimg}}_posts/tUcPIC/capA-instalacao/xc8-09-complete.png{{site.rawimg}}) |


<hr/>

>>> Anexo A - Instalação do MPLAB-X e XC8 >> [Anexo B - Novo Projeto >>]({{site.baseurl}}/2021/capB-novoProjeto)


<hr/>


[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
