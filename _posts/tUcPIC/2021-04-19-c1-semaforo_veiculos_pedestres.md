---
layout: post
title: "C1 - Semáforo de Veículos e de Pedestres"
date: 2021-04-19 20:56:21 -0300
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
---

# Semáforo de Veículos


## Objetivo

Simular um semáforo de veículos e de pedestre, incluindo o botão para bloqueio da via e liberação da atravessia aos pedestres.

## Conteúdo

* Encapsulamento de trechos de código em procedimentos e funções;
* Definições de parâmetros para funções;
* Função de atraso bloqueante: delay();

<!--more-->

## Circuito ([*Hardware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_semaforo))


| Figura 1: Semáforo de Veículos de via simples |
|:----------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/semaforo_veiculos_pedestres.gif{{site.rawimg}})|



## Programa ([*Firmware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos_pedestres.X))

| Figura 2: Árvore de diretório do projeto |
|:------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/projectTree.png{{site.rawimg}})| 



```c
/*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 19 April 2021, 20:42
 * 
 * IDE:                 MPLAB X IDE v5.45
 * Compiler:            XC8 v2.31
 * Operating System:    Debian GNU/Linux bullseye/sid
 * Kernel:              Linux 5.10.0-5-amd64
 * Architecture:        x86-64
 * 
 * Objetivo: 
 *      Simular um semáforo de veículos e de pedestre, 
 *      incluindo o botão para bloqueio da via e 
 *      liberação da atravessia aos pedestres.
 * 
 * 
 * Pinos    |nº     |Conexão
 *  VDD     |11,32  | Alimentação (Vcc/+5V)
 *  VSS     |12,31  | Alimentação (GND/0V)
 *  RD7     |30     | LED Vermelho Veículos (source)
 *  RD6     |29     | LED Amarelo Veículos (source)
 *  RD5     |28     | LED Verde Veículos (source)
 *  RD3     |22     | LED Vermelho Pedestres(source)
 *  RD2     |21     | LED Verde Pedestres(source)
 *  RD0     |19     | Botão Pulsador Pedestres (pullDown)
 * 
 */

#include "config.h"
#include <xc.h>

#define _XTAL_FREQ  4000000

void main(void)
{
        // Configuração dos pinos
    TRISDbits.TRISD7 = 0;   // Saída: Vermelho veículos
    TRISDbits.TRISD6 = 0;   // Saída: Amarelo veículos
    TRISDbits.TRISD5 = 0;   // Saída: Verde veículos
    TRISDbits.TRISD3 = 0;   // Saída: Vermelho pedestre
    TRISDbits.TRISD2 = 0;   // Saída: Verde pedestre
    TRISDbits.TRISD0 = 1;   // Entrada: Botão pedestre
    
        // Inicialização do estado dos LEDs
    PORTDbits.RD7 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD5 = 0;
    PORTDbits.RD3 = 0;
    PORTDbits.RD2 = 0;

    while( 1 )
    {
        PORTDbits.RD5 = 1;
        PORTDbits.RD3 = 1;
        
        if( PORTDbits.RD0 == 1 )
        {
            __delay_ms(3000);
            PORTDbits.RD5 = 0;
            PORTDbits.RD6 = 1;
            __delay_ms(2000);
            PORTDbits.RD6 = 0;
            PORTDbits.RD7 = 1;
            PORTDbits.RD3 = 0;
            PORTDbits.RD2 = 1;
            __delay_ms(5000);
            PORTDbits.RD2 = 0;
            PORTDbits.RD7 = 0;
        }
    }
}
```

```c
    __delay_ms( tempo );
```

```c
main.c:82:: error: (1387) inline delay argument must be constant
```

```c
void delay( unsigned int t )
{
    while( t )
    {
        __delay_ms( 1 );
        --t;
    }
}
```



```c
#include "config.h"
#include <xc.h>

#define _XTAL_FREQ  4000000

#define VERMELHO    'R'
#define AMARELO     'Y'
#define VERDE       'G'



void delay( unsigned int t )
{
    while( t )
    {
        __delay_ms( 1 );
        --t;
    }
}

void semaforo_init( void )
{
        // Configuração dos pinos
    TRISDbits.TRISD7 = 0;   // Saída: Vermelho veículos
    TRISDbits.TRISD6 = 0;   // Saída: Amarelo veículos
    TRISDbits.TRISD5 = 0;   // Saída: Verde veículos
    TRISDbits.TRISD3 = 0;   // Saída: Vermelho pedestre
    TRISDbits.TRISD2 = 0;   // Saída: Verde pedestre
    TRISDbits.TRISD0 = 1;   // Entrada: Botão pedestre
    
        // Inicialização do estado dos LEDs
    PORTDbits.RD7 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD5 = 0;
    PORTDbits.RD3 = 0;
    PORTDbits.RD2 = 0;
}

char botao_pedestre( void )
{
    return( PORTDbits.RD0 );
}

void semaforo( unsigned char cor, unsigned int tempo )
{
    PORTDbits.RD2 = 0;
    PORTDbits.RD3 = 0;
    PORTDbits.RD5 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD7 = 0;

    if( cor == VERMELHO )
    {
        PORTDbits.RD7 = 1;
        PORTDbits.RD2 = 1;
    }
    else if( cor == AMARELO )
    {
        PORTDbits.RD6 = 1;
        PORTDbits.RD3 = 1;
    }
    else if( cor == VERDE )
    {
        PORTDbits.RD5 = 1;
        PORTDbits.RD3 = 1;
    }

    delay( tempo );
}

void main(void)
{
    semaforo_init();

    while( 1 )
    {
        semaforo( VERDE, 1 );

        if( botao_pedestre() == 1 )
        {
            semaforo( VERDE,    2000 );
            semaforo( AMARELO,  3000 );
            semaforo( VERMELHO, 5000 );
        }
    }
}
```

## Biblioteca local

| Figura 3: Árvore de diretório do projeto |
|:----------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/projectTree2.png{{site.rawimg}})| 

```c
/*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 19 April 2021, 20:42
 * 
 * IDE:                 MPLAB X IDE v5.45
 * Compiler:            XC8 v2.31
 * Operating System:    Debian GNU/Linux bullseye/sid
 * Kernel:              Linux 5.10.0-5-amd64
 * Architecture:        x86-64
 * 
 * Objetivo: 
 *      Simular um semáforo de veículos e de pedestre, 
 *      incluindo o botão para bloqueio da via e 
 *      liberação da atravessia aos pedestres.
 * 
 * 
 * Pinos    |nº     |Conexão
 *  VDD     |11,32  | Alimentação (Vcc/+5V)
 *  VSS     |12,31  | Alimentação (GND/0V)
 *  RD7     |30     | LED Vermelho Veículos (source)
 *  RD6     |29     | LED Amarelo Veículos (source)
 *  RD5     |28     | LED Verde Veículos (source)
 *  RD3     |22     | LED Vermelho Pedestres(source)
 *  RD2     |21     | LED Verde Pedestres(source)
 *  RD0     |19     | Botão Pulsador Pedestres (pullDown)
 * 
 */

#include "config.h"
#include <xc.h>
#include "semaforo.h"

void main(void)
{
    semaforo_init();

    while( 1 )
    {
        semaforo( VERDE, 1 );

        if( botao_pedestre() == 1 )
        {
            semaforo( VERDE,    2000 );
            semaforo( AMARELO,  3000 );
            semaforo( VERMELHO, 5000 );
        }
    }
}
```


```c
#include <xc.h>
#define _XTAL_FREQ  4000000

void delay( unsigned int t )
{
    while( t )
    {
        __delay_ms( 1 );
        --t;
    }
}```

```c
#ifndef DELAY_H
#define DELAY_H

void delay( unsigned int t );

#endif
```

```c
#include <xc.h>
#include "delay.h"
#include "semaforo.h"

void semaforo_init( void )
{
        // Configuração dos pinos
    TRISDbits.TRISD7 = 0;   // Saída: Vermelho veículos
    TRISDbits.TRISD6 = 0;   // Saída: Amarelo veículos
    TRISDbits.TRISD5 = 0;   // Saída: Verde veículos
    TRISDbits.TRISD3 = 0;   // Saída: Vermelho pedestre
    TRISDbits.TRISD2 = 0;   // Saída: Verde pedestre
    TRISDbits.TRISD0 = 1;   // Entrada: Botão pedestre
    
        // Inicialização do estado dos LEDs
    PORTDbits.RD7 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD5 = 0;
    PORTDbits.RD3 = 0;
    PORTDbits.RD2 = 0;
}

char botao_pedestre( void )
{
    return( PORTDbits.RD0 );
}

void semaforo( unsigned char cor, unsigned int tempo )
{
    PORTDbits.RD2 = 0;
    PORTDbits.RD3 = 0;
    PORTDbits.RD5 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD7 = 0;

    if( cor == VERMELHO )
    {
        PORTDbits.RD7 = 1;
        PORTDbits.RD2 = 1;
    }
    else if( cor == AMARELO )
    {
        PORTDbits.RD6 = 1;
        PORTDbits.RD3 = 1;
    }
    else if( cor == VERDE )
    {
        PORTDbits.RD5 = 1;
        PORTDbits.RD3 = 1;
    }

    delay( tempo );
}
```

```c
#ifndef SEMAFORO_H
#define SEMAFORO_H

#define VERMELHO    'R'
#define AMARELO     'Y'
#define VERDE       'G'

void semaforo_init( void );
char botao_pedestre( void );
void semaforo( unsigned char cor, unsigned int tempo );

#endif```





Agora é a sua vez! 

Crie o seu projeto, copie o código, execute-o, procure os erros, arrume-os, seja resiliente, leia novamente a explicação, busque outras fontes, pergunte, responda, faça alterações conscientes no código, explore, divirta-se.

Ficou alguma dúvida, entre em contato. 

Bom trabalho! 


<hr/>

>>> [<< C1 - Semáforo de Veículos ]({{site.baseurl}}/2021/c1-semaforo_veiculos) << C1 - Semáforo de Veículos e de Pedestres >> [ >>]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres)

<hr/>



[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)