---
layout: post
title: "C1 - Semáforo de Veíc. e Ped. com Máquina de Estados"
date: 2021-04-20 12:16:21 -0300
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

# Semáforo


## Objetivo

Simular um semáforo de veículos e de pedestre, incluindo o botão para bloqueio da via e liberação da atravessia aos pedestres utilizando uma máquina de estados.

## Conteúdo

* Estrutura condicional `switch case`;
* Máquina de estados.

<!--more-->

## Circuito ([*Hardware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_semaforo))


| Figura 1: Semáforo de Veículos para uma via simples com botão de pedestre |
|:----------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/semaforo_veiculos_pedestres.gif{{site.rawimg}})|



## Programa ([*Firmware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos_pedestres_me.X))

| Figura 2: Árvore de diretório do projeto |
|:----------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/projectTree2.png{{site.rawimg}})| 



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


## Biblioteca local semáforo

```c
#include <xc.h>
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

void semaforo( unsigned char cor )
{
    PORTDbits.RD2 = 0;
    PORTDbits.RD3 = 0;
    PORTDbits.RD5 = 0;
    PORTDbits.RD6 = 0;
    PORTDbits.RD7 = 0;

    switch( cor )
    {
        case VERMELHO:
                    PORTDbits.RD7 = 1;
                    PORTDbits.RD2 = 1;
                    break;
        case AMARELO:
                    PORTDbits.RD6 = 1;
                    PORTDbits.RD3 = 1;
                    break;
        case VERDE:
                    PORTDbits.RD5 = 1;
                    PORTDbits.RD3 = 1;
                    break;
    }
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
void semaforo( unsigned char cor );

#endif
```

### Programa principal 

```c
*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 20 April 2021, 20:42
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
 *      liberação da atravessia aos pedestres 
 *      utilizando Máquina de Estados.
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
#include "delay.h"

void main(void)
{
    char estado = 0;
    int tempo;
    semaforo_init();

    while( 1 )
    {
        switch( estado )
        {
            case 0:
                    semaforo( VERDE );
                    estado = 1;
                    break;
            case 1:
                    if( botao_pedestre() )
                        estado = 2;
                    break;
            case 2:
                    tempo = 2000;
                    estado = 3;
                    break;
            case 3:
                    delay(1);
                    --tempo;
                    if( tempo == 0 )
                        estado = 4;
                    break;
            case 4:
                    semaforo( AMARELO );
                    estado = 5;
                    break;
            case 5:
                    tempo = 3000;
                    estado = 6;
                    break;
            case 6:
                    delay(1);
                    --tempo;
                    if( tempo == 0 )
                        estado = 7;
                    break;
            case 7:
                    semaforo( VERMELHO );
                    estado = 8;
                    break;
            case 8:
                    tempo = 5000;
                    estado = 9;
                    break;
            case 9:
                    delay(1);
                    --tempo;
                    if( tempo == 0 )
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

>>> [<< C1 - Semáforo de Veículos e de Pedestres ]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres) << C1 - Semáforo com Máquina de Estados >> [C1 - Partida Estrela/Triângulo >>]({{site.baseurl}}/2021/c1-partida_estrela_triangulo)

<hr/>

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
