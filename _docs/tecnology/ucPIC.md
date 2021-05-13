---
layout: page
title: Projetos com microcontrolador PIC
permalink: /docs/tecnology/ucPIC
tags:
 - Microcontrolador
 - PIC
 - PIC16F887
 - Linguagem C
 - MPLABX-XC8
 - SimulIDE
 - SELDI
Description: Resoluções de problemas baseadas em projetos.
---

# Curta Eletrônica
## Aprendendo com Desafios

A resolução de problemas está contida das competências gerais da [BNCC]({{site.baseurl}}/docs/#2-pensamento-científico-criativo-e-crítico) e é de extrema importância no desenvolvimento da ciência, da tecnologia e no mercado de trabalho.

Para alcançar um bom nível ou excelência em uma habilidade, ela precisa ser lapidada de forma prática, pela repetição, análise e avaliação crítica dos resultados obtidos e também do processo de resolução.

O **objetivo é resolver os problemas**, mas no caminho, **apreciar o aprendizado** de linguagens de programação e da interface com o mundo físico.

Para o desenvolvimento dos projetos são utilizadas as seguintes ferramentas:

* Ambiente de desenvolvimento integrada - IDE [MPLAB X](https://www.microchip.com/mplab/mplab-x-ide);
* Compilador [XC8](https://www.microchip.com/mplab/compilers);
* Simulador [SimulIDE](https://www.simulide.com/p/downloads.html)

Alternativamente pode-se utilizar uma ferramenta online: 
* IDE/compilador [MPLAB Xpress](https://www.microchip.com/mplab/mplab-xpress).

<hr/>

## Antes de Programar...
* [Anexo A - Instalação]({{site.baseurl}}/2021/capA-instalacao)
* [Anexo B - Novo Projeto]({{site.baseurl}}/2021/capB-novoProjeto)
* [Anexo C - Novos Arquivos]({{site.baseurl}}/2021/capC-novosArquivos)
* [Anexo D - Controle de Versão]({{site.baseurl}}/2021/capD-versionamento)


## Ciclo 1 - Manipulando Entradas e Saídas
* [Arquivo de Configuração]({{site.baseurl}}/2021/config) 
[[config.h](https://raw.githubusercontent.com/JoseWRPereira/ucPICsimulIDE/master/NomeDoProjeto.X/config.h)]
* [C1 - Pisca LED]({{site.baseurl}}/2021/c1-piscaLED) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_piscaLED.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_LED)]
* [C1 - Botão e LED]({{site.baseurl}}/2021/c1-botaoLED) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_botaoLED.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_LED_botao)]
* [C1 - Semáforo de Veículos]({{site.baseurl}}/2021/c1-semaforo_veiculos) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_semaforo)]
* [C1 - Semáforo de Veículos e de Pedestres]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos_pedestres.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_semaforo)]
* [C1 - Semáforo com Máquina de Estados]({{site.baseurl}}/2021/c1-semaforo_veiculos_pedestres_me) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_semaforo_veiculos_pedestres_me.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_semaforo)]
* [C1 - Partida Estrela/Triângulo]({{site.baseurl}}/2021/c1-partida_estrela_triangulo) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_partida_estrela_triangulo.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_partida_estrela_triangulo)]
* [C1 - Display de 7 segmentos]({{site.baseurl}}/2021/c1-disp7seg) 
[[src](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/c1_display7segmentos.X)]
[[sim](https://github.com/JoseWRPereira/ucPICsimulIDE/tree/master/sim_disp7seg)]
* [C1 - 2 Displays de 7 segmentos]({{site.baseurl}}/2021/c1-disp7segX2)

* [P0112 - Detecção de borda]({{site.baseurl}}/2020/P0112-bordaBotaoPulsador)


## Ciclo 2 - IHM: display e teclado
* [C2 - Display LCD 8 vias]({{site.baseurl}}/2021/c2-dispLCD8vias)
* [C2 - Display LCD 4 vias]({{site.baseurl}}/2020/c2-dispLCD4vias)
* [C2 - Teclado Matricial 4x4]({{site.baseurl}}/2020/P0130-teclado4x4)




<hr/>

[Voltar]({{site.baseurl}}/docs/tecnologia)