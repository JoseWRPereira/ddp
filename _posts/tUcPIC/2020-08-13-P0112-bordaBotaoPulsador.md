---
layout: post
title: "P0112 - Borda Botão Pulsador"
date: 2020-08-13 23:02:21 -0300
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
 - type: success
   tag: SimulIDE
mathjax: true
---



# Detecção de borda em botão pulsador

A leitura simples de um botão implica em alguns comportamentos não desejados como um incremento maior do que a quantidade de vezes que um botão é pressionado. Para solucionar esse problema pode-se utilizar não o estado lógico do botão, mas sim o evendo associado a mudança de estado, evento único dentro de um ciclo de operação.  

## Objetivo

Detectar as bordas de subida e descida em botão pulsador.

<!--more-->

## 1. Circuito (*Hardware*)


| Figura 1.1: Incremento por borda de subida e decremento por borda de descida |
|:---------------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/imgP0112/bordaBotaoPulsador.gif{{site.rawimg}}) |




## 2. Programa (*Firmware*)


| Figura 2: Árvore de diretório do projeto |
|:----------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/imgP0112/projectTree.jpg{{site.rawimg}})| 


## Estrutura do programa




### Programa principal

```c
/*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 13 de Agosto de 2020, 23:02:21
 * 
 * -------------------------------------------------
 *          MAPA DE ENTRADAS E SAIDAS
 * -------------------------------------------------
 *  Pinos   |nº     |Conexão
 * ---------|-------|-------------------------------
 *  RB0     |33     | Segmento a
 *  RB1     |34     | Segmento b
 *  RB2     |35     | Segmento c
 *  RB3     |36     | Segmento d
 *  RB4     |37     | Segmento e
 *  RB5     |38     | Segmento f
 *  RB6     |39     | Segmento g
 *  RB7     |40     | Segmento p
 *  RD7     |30     | Hab. Dezena (Catodo comum)
 *  RD6     |29     | Hab. Unidade (Catodo comum)
 * ---------|-------|-------------------------------
 *  RD2     |21     | Botão -1
 *  RD3     |22     | Botão +1
 * -------------------------------------------------
 * -------------------------------------------------
 */

#include <xc.h>
#include "config.h"
#include "delay.h"
#include "disp7seg.h"
#include "botao.h"

void main(void) 
{
    char num = 0;
    
    disp7segX2_init();
    botao_init();
    
    while( 1 )
    {
        disp7segX2( num );
        
        if( b1_bordaSubida() )
            num = ++num % 100;
        if( b0_bordaDescida() )
            num = num==0 ? 99 : num-1;
        
        delay(1);
    }
    return;
}
```



### Inclusão de bibliotecas

```c
/*
 * File:   botao.c
 * Author: josewrpereira
 *
 * Created on 13 de Agosto de 2020, 23:00
 * 
 * -------------------------------------------------
 *          MAPA DE ENTRADAS E SAIDAS
 * -------------------------------------------------
 *  Pinos   |nº     |Conexão
 * ---------|-------|-------------------------------
 *  RD2     |21     | Botão -1
 *  RD3     |22     | Botão +1
 * -------------------------------------------------
 */

#include <xc.h>

#define B0      PORTDbits.RD2
#define B1      PORTDbits.RD3

void botao_init( void )
{
    TRISDbits.TRISD2 = 1;
    TRISDbits.TRISD3 = 1;
}


// ************************** Botão 0

char b0( void )
{
    return( PORTBbits.RB0 );
}

char b0Anterior=0;
char b0_bordaSubida( void )
{
    // b0: 000000000001111111111111100000000
    // ret:000000000001000000000000000000000
    char aux;
    aux = B0 && !b0Anterior;
    b0Anterior = B0;
    return( aux );
}
char b0_bordaDescida( void )
{
    // b0: 000000000001111111111111100000000
    // ret:000000000000000000000000010000000
    char aux;
    aux = !B0 && b0Anterior;
    b0Anterior = B0;
    return( aux );
}
char b0_borda( void )
{
    // b0: 000000000001111111111111100000000
    // ret:000000000001000000000000010000000
    char aux;
    aux = (B0 && !b0Anterior) || (!B0 && b0Anterior);
    b0Anterior = B0;
    return( aux );
}



// ************************** Botão 1

char b1( void )
{
    return( B1 );
}

char b1Anterior=0;
char b1_bordaSubida( void )
{
    // b1: 000000000001111111111111100000000
    // ret:000000000001000000000000000000000
    char aux;
    aux = B1 && !b1Anterior;
    b1Anterior = B1;
    return( aux );
}
char b1_bordaDescida( void )
{
    // b1: 000000000001111111111111100000000
    // ret:000000000000000000000000010000000
    char aux;
    aux = !B1 && b1Anterior;
    b1Anterior = B1;
    return( aux );
}
char b1_borda( void )
{
    // b1: 000000000001111111111111100000000
    // ret:000000000001000000000000010000000
    char aux;
    aux = (B1 && !b1Anterior) || (!B1 && b1Anterior);
    b1Anterior = B1;
    return( aux );
}

```



<hr/>

Agora é a sua vez! 

Crie o seu projeto, copie o código, execute-o, procure os erros, arrume-os, seja resiliente, leia novamente a explicação, busque outras fontes, pergunte, responda, explique, faça alterações conscientes no código, explore, divirta-se.

Ficou com alguma dúvida, entre em contato. 

Bom trabalho! 

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)