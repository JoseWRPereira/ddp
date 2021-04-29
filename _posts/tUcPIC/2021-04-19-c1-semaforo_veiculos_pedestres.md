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

Para simular os semáforos de veículo e de pedestre, são usadas saídas digitais ligadas em LEDs com as cores correspondentes aos dispositivos físicos reais. 
Para o botão de bloqueio da via, e liberação de travessia aos pedestres, foi usada uma configuração de botão pulsador com resistor de *pull-down* ligados em uma entrada digital (pino). 

| Figura 1: Semáforo de Veículos para uma via simples com botão de pedestre |
|:----------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/semaforo_veiculos_pedestres.gif{{site.rawimg}})|



## Programa ([*Firmware*](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos_pedestres.X))

O programa foi desenvolvido ainda de forma não modular, com todas as instruções em um único arquivo `main.c`, além do arquivo de configuração `config.h`.

| Figura 2: Árvore de diretório do projeto |
|:------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/projectTree.png{{site.rawimg}})| 

## Programa principal

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

## Modularização do código

Na modularização do código, o objetivo pode ser a redução de trechos repetitivos, criando um procedimento ou uma função, podendo ser necessário a utilização de parâmetros, simplificação do programa principal, ou ainda a criação de uma camada de abstração entre o *hardware* e o programa principal.


A primeira etapa da simplificação proposta é a criação do procedimento de inicialização.

```c
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
```

A função que faz a leitura do botão propicia uma camada de abstração entre o *hardware* e o programa principal, pois no `main` não é necessário saber o pino em que o botão está conectado, papel exercido pela função correspondente. Caso se queira mudar o botão para outro pino, basta alterar a função correspondente, sem necessidade de mudanças no programa principal.

```c
char botao_pedestre( void )
{
    return( PORTDbits.RD0 );
}
```

A mundança proposta seguinte é a criação de uma função que aciona a cor desejada no semáforo, pelo tempo desejado, sendo estes dados seus parâmetros.

```c

#define VERMELHO    'R'
#define AMARELO     'Y'
#define VERDE       'G'

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

Aqui ocorre o um problema na compilação, no final da função, na chamada do rotina que produz um atraso:

```c
    __delay_ms( tempo );
```

O erro apresentado pelo compilador é:

```c
main.c:82:: error: (1387) inline delay argument must be constant
```

Que significa basicamente que o argumento da função delay precisa ser uma constante, é não uma variável como foi foito.

Para resolver esse problema é criada uma função denominada `delay`, que vai executar a mesma função que `__delay_ms`, porém aceitando uma variável como parâmetro.

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

O código completo no arquivo `main.c` fica então da seguinte forma:

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

Com o programa separado em funções e procedimentos, chegou o memento de segmentar o código em arquivos separados, dependendo de suas funçionalidades. 

São agrupados em um mesmo arquivo, funções que se relacionam diretamente a uma função ou periférico.

Aqui foi criado um arquivo para as funções e procedimentos do semáforo e outro para as rotinas de temporização ou atraso. 

Para cada um desses arquivos fonte é criado um respectivo arquivo de cabeçalho.

| Figura 3: Árvore de diretório do projeto |
|:----------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c1-semaforo_veiculos_pedestres/projectTree2.png{{site.rawimg}})| 

### Arquivo principal - main.c

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
### Arquivos de temporização

#### delay.c
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
#### delay.h
```c
#ifndef DELAY_H
#define DELAY_H

void delay( unsigned int t );

#endif
```

### Arquivos do semáforo

#### semaforo.c
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

#### semaforo.h
```c
#ifndef SEMAFORO_H
#define SEMAFORO_H

#define VERMELHO    'R'
#define AMARELO     'Y'
#define VERDE       'G'

void semaforo_init( void );
char botao_pedestre( void );
void semaforo( unsigned char cor, unsigned int tempo );

#endif
```





Agora é a sua vez! 

Crie o seu projeto, copie o código, execute-o, procure os erros, arrume-os, seja resiliente, leia novamente a explicação, busque outras fontes, pergunte, responda, faça alterações conscientes no código, explore, divirta-se.

Ficou alguma dúvida, entre em contato. 

Bom trabalho! 


<hr/>

>>> [<< C1 - Semáforo de Veículos ]({{site.baseurl}}/2021/c1-semaforo_veiculos) << C1 - Semáforo de Veículos e de Pedestres >> [C1 - Semáforo com Máquina de Estados >>]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres_me)

<hr/>

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
