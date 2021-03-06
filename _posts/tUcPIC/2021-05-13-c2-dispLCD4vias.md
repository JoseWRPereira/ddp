---
layout: post
title: "C2 - Display LCD com 4 vias de barramento"
date: 2021-05-13 06:58:21 -0300
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



# Display LCD 

O LCD permite uma transferência de dados por um barramento de 8 ou 4 vias, economizando assim quatro bits que podem ser utilizados para outros fins.

## Objetivo

Adaptar a biblioteca dispLCD8vias para trabalhar com um barramento de 4 vias de dados.

<!--more-->

## 1. Circuito (*Hardware*)


| Figura 1.1: Display LCD HD44780 |
|:---------------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c2-dispLCD4vias/dispLCD4vias.gif{{site.rawimg}}) |




## 2. Programa (*Firmware*)


| Figura 2: Árvore de diretório do projeto |
|:----------------------------------------:|
| ![circuito]({{site.baseurlimg}}/_posts/tUcPIC/c2-dispLCD4vias/projectTree.jpg{{site.rawimg}})| 


## Estrutura do programa




### Programa principal

```c
/*
 * File:   main.c
 * Author: josewrpereira
 *
 * Created on 15 de Agosto de 2020, 16:03:21
 *
 * -------------------------------------------------
 *          MAPA DE ENTRADAS E SAIDAS
 * -------------------------------------------------
 *  Pinos   |nº     | Conexão
 * ---------|-------|-------------------------------
 *  RD2     |21     | LCD_RS
 *  RD3     |22     | LCD_EN
 *  RD4     |27     | LCD_D4
 *  RD5     |28     | LCD_D5
 *  RD6     |29     | LCD_D6
 *  RD7     |30     | LCD_D7
 * -------------------------------------------------
 * -------------------------------------------------
 */

#include "config.h"
#include <xc.h>
#include "delay.h"
#include "dispLCD4vias.h"

void main(void)
{
    int tela = 0;
    int n = 1;
    int n_1 = 0;
    int n_2 = 0;
    
    dispLCD_init();

    while( 1 )
    {
        switch( tela )
        {
            case 0: dispLCD(0,0," Display LCD 4b "); 
                    tela = 1;
                    delay(1000);
                    break;
                    
            case 1: dispLCD(1,0,"    HD44780     "); 
                    tela = 2;
                    delay(2000);
                    break;
                    
            case 2: dispLCD_clr();
                    tela = 3;
                    delay(500);
                    break;
                    
            case 3: dispLCD(0,0," dispLCD_init() "); 
                    dispLCD(1,0,"  inicializa    "); 
                    tela = 4;
                    delay(1000);
                    break;
                    
            case 4: dispLCD(0,0,"dispLCD(l,c,str)"); 
                    dispLCD(1,0,"l: linha        "); 
                    tela = 5;
                    delay(2000);
                    break;
                    
            case 5: dispLCD(1,0,"c: coluna       "); 
                    tela = 6;
                    delay(1000);
                    break;
                    
            case 6: dispLCD(1,0,"str: string     "); 
                    tela = 10;
                    delay(1500);
                    break;
                    
            case 10:
                    dispLCD(0,0,"  Display LCD   "); 
                    dispLCD(1,0,"Fibonacci:      ");
                    n_2 = n_1 = 0;
                    n = 1;
                    tela = 11;
                    break;

            case 11:
                    n_2 = n_1;
                    n_1 = n;
                    n = n_1 + n_2;
                    if( n < 0 )
                        tela = 0;
                    else
                        tela = 12;
                    break;

            case 12:
                    dispLCD_num(1,11, n, 5 ); 
                    tela = 11;
                    delay(1000);
                    break;
        }
   }
    return;
}
```



### Inclusão de bibliotecas

```c
/*
 * File:   dispLCD4vias.c
 * Author: josewrpereira
 *
 * Created on 15 de Agosto de 2020, 16:06
 * 
 * -------------------------------------------------
 *          MAPA DE ENTRADAS E SAIDAS
 * -------------------------------------------------
 *  Pinos   |nº     |Conexão
 * ---------|-------|-------------------------------
 *  RD2     |21     | LCD_RS
 *  RD3     |22     | LCD_EN
 *  RD4     |27     | LCD_D4
 *  RD5     |28     | LCD_D5
 *  RD6     |29     | LCD_D6
 *  RD7     |30     | LCD_D7
 * -------------------------------------------------
 */

#include <xc.h>
#include "delay.h"

//***************** Interface com PORTs/Pinos
#define LCD_BUS         LCDbits.BUS
#define LCD_EN          LCDbits.EN
#define LCD_RS          LCDbits.RS
#define LCD_ROWS        2
#define LCD_COLS        16
#define LCD_ADDRS       0x008

typedef union 
{
    struct 
    {
        unsigned char     :2;
        unsigned char RS  :1;
        unsigned char EN  :1;
        unsigned char BUS :4;
    };
} LCDbits_t;

volatile LCDbits_t LCDbits __at(LCD_ADDRS);

//***************** Definicao de Comandos ao LCD 
#define LCD_CLEAR_DISPLAY           0x01

#define LCD_RETURN_HOME             0x02

#define LCD_ENTRY_MODE_SET          0x04
#define LCD_EMS_CURSOR_RIGHT        0x02
#define LCD_EMS_CURSOR_LEFT         0x00
#define LCD_EMS_SHIFT_DISPLAY       0x01

#define LCD_DISPLAY_CONTROL         0x08
#define LCD_DC_DISPLAY_ON           0x04
#define LCD_DC_DISPLAY_OFF          0x00
#define LCD_DC_CURSOR_ON            0x02
#define LCD_DC_CURSOR_OFF           0x00
#define LCD_DC_BLINK_ON             0x01
#define LCD_DC_BLINK_OFF            0x00

#define LCD_CURSOR_SHIFT            0x10
#define LCD_CS_LEFT                 0x00
#define LCD_CS_RIGHT                0x04

#define LCD_DISPLAY_SHIFT           0x10
#define LCD_DS_LEFT                 0x08
#define LCD_DS_RIGHt                0x0C

#define LCD_FUNCTION_SET            0x20
#define LCD_FS_DATA_LENGTH_8        0x10
#define LCD_FS_DATA_LENGTH_4        0x00
#define LCD_FS_LINE_NUMBER_1        0x00
#define LCD_FS_LINE_NUMBER_2        0x08
#define LCD_FS_DOTS_FORMAT_5x8      0x00
#define LCD_FS_DOTS_FORMAT_5x11     0x04

#define LCD_SET_CGRAM_ADDRS( adrs ) (0x40+(adrs & 0x3F))

#define LCD_SET_DDRAM_ADDRS( adrs ) (0x80+(adrs & 0x7F))
#define LCD_ADDR_LINE_0             0x00
#define LCD_ADDR_LINE_1             0x40

// Escreve um comando no display (Instruction Register)
void dispLCD_instReg( unsigned char i )
{
    LCD_RS = 0;
    LCD_BUS = (i>>4);

    LCD_EN = 0;
    if( i == LCD_CLEAR_DISPLAY || i == LCD_RETURN_HOME )
        __delay_ms( 2 );
    else
        __delay_us( 40 );
    LCD_EN = 1;
    

    if( (i & 0xF0) == (LCD_FUNCTION_SET | LCD_FS_DATA_LENGTH_4) )
    {
        LCD_RS = 0;
        LCD_BUS = i>>4;
        LCD_EN = 0;
        __delay_us( 40 );
        LCD_EN = 1;
    }

    LCD_RS = 0;
    LCD_BUS = i & 0x0F;
    LCD_EN = 0;
    if( i == LCD_CLEAR_DISPLAY || i == LCD_RETURN_HOME )
        __delay_ms( 2 );
    else
        __delay_us( 40 );
    LCD_EN = 1;
}

// Escreve um dado no display (Data Register))
void dispLCD_dataReg( unsigned char d )
{
    LCD_RS = 1;
    LCD_BUS = d >> 4;
    LCD_EN = 0;
    __delay_us( 40 );
    LCD_EN = 1;

    LCD_RS = 1;
    LCD_BUS = d & 0x0F;
    LCD_EN = 0;
    __delay_us( 40 );
    LCD_EN = 1;
}

// Posicionar o cursor na coordenada: linha e coluna 
void dispLCD_lincol( unsigned char lin, unsigned char col)
{
    dispLCD_instReg( LCD_SET_DDRAM_ADDRS( (LCD_ADDR_LINE_1 * lin) + (col + LCD_ADDR_LINE_0) ) );
}

// Inicializa os pinos conectados ao display
void dispLCD_init( void )
{
    TRISDbits.TRISD2 = 0;   // RS
    TRISDbits.TRISD3 = 0;   // EN

    TRISDbits.TRISD4 = 0;   // D4
    TRISDbits.TRISD5 = 0;   // D5
    TRISDbits.TRISD6 = 0;   // D6
    TRISDbits.TRISD7 = 0;   // D7

    LCD_EN = 1;
    dispLCD_instReg( LCD_FUNCTION_SET|LCD_FS_DATA_LENGTH_4|LCD_FS_LINE_NUMBER_2);
    dispLCD_instReg( LCD_DISPLAY_CONTROL|LCD_DC_DISPLAY_ON|LCD_DC_CURSOR_OFF|LCD_DC_BLINK_OFF );
    dispLCD_instReg( LCD_CLEAR_DISPLAY );
    dispLCD_instReg( LCD_RETURN_HOME );
}

// Escreve uma string no display
void dispLCD( unsigned char lin, unsigned char col, const char * str )
{
    char pos = col;
    dispLCD_lincol( lin, col );

    while( *str )
    {
        dispLCD_dataReg( *str );
        ++str;
        ++pos;
    }
}

// Escreve um número inteiro no display
void dispLCD_num(  unsigned char lin, unsigned char col,
                    int num, unsigned char tam )
{
    int div;
    unsigned char size;
    char sinal; // 0:+ 1:-
   
    sinal = num < 0;
    if( sinal )
        num = (~num) + 1;

    dispLCD_lincol(lin, col);
   
    div=10000;
    size = 5;
    while( div >= 1 )
    {
        if( num/div == 0 )
            --size;
        else
            break;
        div/=10;
    }

    while( tam > (size+sinal) && tam > 1 )
    {
        dispLCD_dataReg(' ');
        --tam;
    }  

    if( sinal )
        dispLCD_dataReg('-');
 
    do
    {
        dispLCD_dataReg( (num / div) + '0' );
        num = num % div;
        div/=10;
    }
    while( div >= 1 );
}

// Apaga todos os caracteres no display
void dispLCD_clr( void )
{
    dispLCD_instReg(LCD_CLEAR_DISPLAY);
}

```



<hr/>

Agora é a sua vez! 

Crie o seu projeto, copie o código, execute-o, procure os erros, arrume-os, seja resiliente, leia novamente a explicação, busque outras fontes, pergunte, responda, explique, faça alterações conscientes no código, explore, divirta-se.

Ficou com alguma dúvida, entre em contato. 

Bom trabalho! 


<hr/>

>>> [<< C2 - Display LCD 8 vias ]({{site.baseurl}}/2021/c2-dispLCD8vias) << C2 - Display LCD 4 vias >> [C2 - Teclado Matricial 4x4 >>]({{site.baseurl}}/2021/c2-teclado4x4)


<hr/>

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)