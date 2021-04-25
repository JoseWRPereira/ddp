---
layout: post
title: "C1 - Partida Estrela/Triângulo"
date: 2021-04-20 21:32:21 -0300
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

# Partida de Motor Trifásico 


## Objetivo

Simular uma partida estrela/triângulo de motor trifásico.

## Conteúdo

* Estrutura condicional `switch case`;
* Máquina de estados.

<!--more-->

## Circuito ([*Hardware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_partida_estrela_triangulo))


| Figura 1: Semáforo de Veículos de via simples |
|:----------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-partida_estrela_triangulo/partida_estrela_triangulo.gif{{site.rawimg}})|



## Programa ([*Firmware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_partida_estrela_triangulo.X))

| Figura 2: Árvore de diretório do projeto |
|:----------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-partida_estrela_triangulo/projectTree.png{{site.rawimg}})| 



## Biblioteca local delay

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
}
```

```c
#ifndef DELAY_H
#define DELAY_H

void delay( unsigned int t );

#endif
```


## Biblioteca local partida Estrela-Triângulo

```c
#include <xc.h>

void pet_init( void )
{
    TRISDbits.TRISD7 = 0;
    TRISDbits.TRISD6 = 0;
    TRISDbits.TRISD5 = 0;
    TRISDbits.TRISD1 = 1;
    TRISDbits.TRISD0 = 1;
    
    PORTDbits.RD7 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD5 = 0;
}

void pet_k1_set( void )
{
    PORTDbits.RD5 = 1;
}

void pet_k1_reset( void )
{
    PORTDbits.RD5 = 0;
}

void pet_k2_set( void )
{
    PORTDbits.RD6 = 1;
}

void pet_k2_reset( void )
{
    PORTDbits.RD6 = 0;
}

void pet_k3_set( void )
{
    PORTDbits.RD7 = 1;
}

void pet_k3_reset( void )
{
    PORTDbits.RD7 = 0;
}


char pet_s1( void )
{
    return( !PORTDbits.RD1 );
}

char pet_s0( void )
{
    return( !PORTDbits.RD0 );
}
```

```c
#ifndef PARTIDA_ESTRELA_TRIANGULO_H
#define PARTIDA_ESTRELA_TRIANGULO_H

void pet_init( void );
void pet_k1_set( void );
void pet_k1_reset( void );
void pet_k2_set( void );
void pet_k2_reset( void );
void pet_k3_set( void );
void pet_k3_reset( void );
char pet_s1( void );
char pet_s0( void );

#endif
```

### Programa principal 

```c
/*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 20 April 2021, 20:28
 * 
 * IDE:                 MPLAB X IDE v5.45
 * Compiler:            XC8 v2.31
 * Operating System:    Debian GNU/Linux bullseye/sid
 * Kernel:              Linux 5.10.0-5-amd64
 * Architecture:        x86-64
 * 
 * Objetivo: 
 *      Simular uma partida estrela/triângulo de motor trifásico.
 * 
 * nº Pinos| PORT |Conexão
 *  11,32  | VDD  | Alimentação (Vcc/+5V)
 *  12,31  | VSS  | Alimentação (GND/0V)
 * 
 *  30     | RD7  | Contator K1: Comum (source)
 *  29     | RD6  | Contator K2: Triângulo (source)
 *  28     | RD5  | Contator K3: Estrela (source)
 * 
 *  19     | RD0  | Botão Pulsador Desligar (pullUp)
 *  20     | RD1  | Botão Pulsador Ligar (pullUp)
 * 
 */

#include "config.h"
#include <xc.h>
#include "delay.h"
#include "partida_estrela_triangulo.h"

void main(void)
{
    char estado = 0;
    int tempo;
    
    pet_init();
    
    while( 1 )
    {
        switch( estado )
        {
            case 0:
                    pet_k3_reset();
                    pet_k2_reset();
                    pet_k1_reset();
                    estado = 1;
                    break;
            case 1:
                    if( pet_s1() )
                    {
                        estado = 2;
                    }
                    break;
            case 2:
                    pet_k1_set();
                    pet_k3_set();
                    tempo = 5000;
                    estado = 3;
                    break;
            case 3:
                    delay(1);
                    --tempo;
                    if( tempo == 0 )
                        estado = 4;
                    if( pet_s0() )
                        estado = 0;
                    break;
            case 4:
                    pet_k3_reset();
                    pet_k2_set();
                    estado = 5;
                    break;
            case 5:
                    if( pet_s0() )
                        estado = 0;
                    break;
        }
    }
}
```




Agora é a sua vez! 

Crie o seu projeto, copie o código, execute-o, procure os erros, arrume-os, seja resiliente, leia novamente a explicação, busque outras fontes, pergunte, responda, faça alterações conscientes no código, explore, divirta-se.

Ficou alguma dúvida, entre em contato. 

Bom trabalho! 


<hr/>

>>> [<< C1 - Semáforo com Máquina de Estados ]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres_me) << C1 - Partida Estrela/Triângulo >> [ C1 - Display de 7 segmentos >>]({{site.baseurl}}/2021/c1-disp7seg)

<hr/>

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
