---
layout: post
title: "C1 - Semáforo de Veículos"
date: 2021-04-15 21:26:21 -0300
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

Acionar 3 saídas simulando um semáforo de veículos.

## Conteúdo

* Uso de definições;
* Encapsulamento de trechos de código: procedimentos e funções;

<!--more-->

## Circuito ([*Hardware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_semaforo))


| Figura 1: Semáforo de Veículos para uma via simples |
|:----------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos/semaforo_veiculos.gif{{site.rawimg}})|



## Programa ([*Firmware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos.X))

| Figura 2: Árvore de diretório do projeto |
|:------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos/projectTree.png{{site.rawimg}})| 



```c
/*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 15 April 2021, 21:11
 * 
 * IDE:                 MPLAB X IDE v5.45
 * Compiler:            XC8 v2.31
 * Operating System:    Debian GNU/Linux bullseye/sid
 * Kernel:              Linux 5.10.0-5-amd64
 * Architecture:        x86-64
 * 
 * Objetivo: 
 *      Acionar 3 saídas simulando um semáforo com os respectivos tempos:
 *          Vermelha: 5s
 *          Verde: 4s
 *          Amarela: 1s
 * 
 * 
 * Pinos    |nº     |Conexão
 *  VDD     |11,32  | Alimentação (Vcc/+5V)
 *  VSS     |12,31  | Alimentação (GND/0V)
 *  RD7     |30     | LED Vermelho (source)
 *  RD6     |29     | LED Amarelo (source)
 *  RD5     |28     | LED Verde (source)
 * 
 */

#include "config.h"
#include <xc.h>

#define _XTAL_FREQ  4000000

void main( void )
{
        // Configuração dos pinos
    TRISDbits.TRISD7 = 0;       // LED Vermelho
    TRISDbits.TRISD6 = 0;       // LED Amarelo
    TRISDbits.TRISD5 = 0;       // LED Verde
    PORTDbits.RD7 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD5 = 0;
    
    while( 1 )
    {
            // LED Vermelho
        PORTDbits.RD7 = 1;
        __delay_ms(5000);
        PORTDbits.RD7 = 0;

            // LED Verde                
        PORTDbits.RD5 = 1;
        __delay_ms(4000);
        PORTDbits.RD5 = 0;

            // LED Amarelo
        PORTDbits.RD6 = 1;
        __delay_ms(1000);
        PORTDbits.RD6 = 0;
    }
}
```

## Utilização de #defines

```c
#include "config.h"
#include <xc.h>

#define _XTAL_FREQ  4000000

#define SEMAFORO_VERMELHO   PORTDbits.RD7
#define SEMAFORO_AMARELO    PORTDbits.RD6
#define SEMAFORO_VERDE      PORTDbits.RD5

#define TEMPO_SEMAFORO_VERMELHO 5000
#define TEMPO_SEMAFORO_AMARELO  1000
#define TEMPO_SEMAFORO_VERDE    4000

void main(void)
{
        // Configuração dos pinos
    TRISDbits.TRISD7 = 0;
    TRISDbits.TRISD6 = 0;
    TRISDbits.TRISD5 = 0;
        // Inicialização do estado dos LEDs
    SEMAFORO_VERMELHO = 0;
    SEMAFORO_AMARELO = 0;
    SEMAFORO_VERDE = 0;

    while( 1 )
    {
        SEMAFORO_VERMELHO = 1;
        __delay_ms( TEMPO_SEMAFORO_VERMELHO );
        SEMAFORO_VERMELHO = 0;

        SEMAFORO_VERDE = 1;
        __delay_ms( TEMPO_SEMAFORO_VERDE );
        SEMAFORO_VERDE = 0;

        SEMAFORO_AMARELO = 1;
        __delay_ms( TEMPO_SEMAFORO_AMARELO );
        SEMAFORO_AMARELO = 0;
    }
}
```

## Encapsulamento de código
```c
#include "config.h"
#include <xc.h>

#define _XTAL_FREQ  4000000

#define SEMAFORO_VERMELHO   PORTDbits.RD7
#define SEMAFORO_AMARELO    PORTDbits.RD6
#define SEMAFORO_VERDE      PORTDbits.RD5

#define TEMPO_SEMAFORO_VERMELHO 5000
#define TEMPO_SEMAFORO_AMARELO  1000
#define TEMPO_SEMAFORO_VERDE    4000

void semaforo_init( void )
{
        // Configuração dos pinos
    TRISDbits.TRISD7 = 0;
    TRISDbits.TRISD6 = 0;
    TRISDbits.TRISD5 = 0;
        // Inicialização do estado dos LEDs
    SEMAFORO_VERMELHO = 0;
    SEMAFORO_AMARELO = 0;
    SEMAFORO_VERDE = 0;
}

void semaforo_vermelho( void )
{
    SEMAFORO_VERMELHO = 1;
    __delay_ms( TEMPO_SEMAFORO_VERMELHO );
    SEMAFORO_VERMELHO = 0;
}

void semaforo_verde( void )
{
    SEMAFORO_VERDE = 1;
    __delay_ms( TEMPO_SEMAFORO_VERDE );
    SEMAFORO_VERDE = 0;
}

void semaforo_amarelo( void )
{
    SEMAFORO_AMARELO = 1;
    __delay_ms( TEMPO_SEMAFORO_AMARELO );
    SEMAFORO_AMARELO = 0;
}

void main(void)
{
    semaforo_init();
    while( 1 )
    {
        semaforo_vermelho();
        semaforo_verde();
        semaforo_amarelo();
    }
}

```



Agora é a sua vez! 

Crie o seu projeto, copie o código, execute-o, procure os erros, arrume-os, seja resiliente, leia novamente a explicação, busque outras fontes, pergunte, responda, faça alterações conscientes no código, explore, divirta-se.

Ficou alguma dúvida, entre em contato. 

Bom trabalho! 


<hr/>

>>> [<< C1 - Botão pulsador e LED ]({{site.baseurl}}/2021/c1-botaoLED) << C1 - Semáforo de Veículos >> [C1 - Semáforo de Veículos e de Pedestres >>]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres)

<hr/>



[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)