---
layout: post
title: "Anexo D - Controle de Versão"
date: 2021-04-10 18:14:21 -0300
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

# Git e GitHub

Com o MPLAB-X é possível realizar o controle de versão dos projetos com algumas ferramentas específicas, entre elas o Git, e fazer a conexão com um repositório remoto, como o GitHub. 

O Git é uma ferramenta de controle de versão que será aqui utilizada num recorte bem simples e básica, não sendo o intuito ensinar seu uso amplo ou profundo. 

## Objetivo

Utilizar o Git e o GitHub, através do MPLAB-X, para fazer o controle de versão de um projeto.

<!--more-->

## Criando a conta no GitHub

* Acesse o site: [https://github.com/](https://github.com/)

| Figura 1: Plataforma GitHub |
|:---------------------------------------------:|
| ![Plataforma GitHub]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/01.png{{site.rawimg}}) |

* Se ainda não possuir uma conta, clique em ***Sign up***
* Se já possuir uma conta, clique em ***Sign in***

| Figura 2: Criar uma conta |
|:---------------------------------------------:|
| ![Criar uma conta]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/02.png{{site.rawimg}}) |


Preencha os campos indicados:
*	***Username*** : Nome de usuário. O nome que vai te identificar na plataforma;
*	***Email address***: Inserir o endereço do seu e-mail para realizar a validação de usuário;
*	***Password***: Criar uma senha para acessar a plataforma;
*	Faça o teste que verifica que você não é um robô;
*	Se você passou do teste anterior, clique em ***Create account***.


## Acessando a sua conta

* Acesse: [https://github.com/login](https://github.com/login)

| Figura 3: Campos de acesso |
|:---------------------------------------------:|
| ![Campos de acesso]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/03.png{{site.rawimg}}) |

*	Insira o seu nome de usuário ou o endereço de e-mail;
*	Insira a sua senha;
*	Clique em ***Sign in***.


Ao acessar a plataforma do GitHub, uma tela semelhante a Figura 4 é exibida.

| Figura 4: Tela principal do GitHub |
|:---------------------------------------------:|
| ![Tela principal do GitHub]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/05.png{{site.rawimg}}) |

*	Clique na identificação do usuário, no canto superior direito; 
*	Clique em ***Your repositories***.

| Figura 5: Repositórios de projetos |
|:---------------------------------------------:|
| ![Repositórios de projetos]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/06.png{{site.rawimg}}) |

* Selecione a aba ***Repositories***.


## Criando um novo repositório

*	Clique em ***New*** para criar um novo repositório.

| Figura 6: Criando um novo repositório |
|:---------------------------------------------:|
| ![Criando um novo repositório]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/07.png{{site.rawimg}}) |

* Inclua o nome do repositório do projeto em ***Repository name***;
* Clique em ***Create repository***.

| Figura 7: Configuração do repositório |
|:---------------------------------------------:|
| ![Configuração do repositório]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/08.png{{site.rawimg}}) |

Note que foi inserido um nome com erro de grafia.
Vamos corrigir a grafia do nome do repositório:

* Clique na aba ***Settings***;

| Figura 8: Arquivo de cabeçalho |
|:---------------------------------------------:|
| ![Arquivo de cabeçalho]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/09.png{{site.rawimg}}) |

* Modifique a grafia em ***Repository name***;
* Clique em ***Rename***.
 
Outras configurações referentes ao projeto podem ser realizadas nessa aba, 
inclusive o arquivamento, a transferência ou a exclusão do projeto.


* Volte para a aba ***Code***;

| Figura 9: Link de acesso ao repositório |
|:---------------------------------------------:|
| ![Link de acesso ao repositório]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/10.png{{site.rawimg}}) |

* Copie o link que está em destaque, ele será usado posteriormente.





## Inicializando o repositório com o projeto

*	Abra o MPLAB-X com o projeto que deve ser incluído no repositório remoto (GitHub);
*	Selecione o projeto;
*	Clique em: ***Team*** -> ***Git*** -> ***Initialize Repository***


| Figura 10: Caminho de inicialização do respositório no GitHub |
|:---------------------------------------------:|
| ![Caminho de inicialização do respositório no GitHub]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/11.png{{site.rawimg}}) |

* Verifique o caminho do projeto que será conectado ao repositório.

| Figura 11: Caminho do projeto |
|:---------------------------------------------:|
| ![Caminho do projeto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/12.png{{site.rawimg}}) |

Ao clicar em ***OK***, note que a árvore do projeto ficou com alguns arquivos na cor verde e apareceu uma pequena marca junto ao ícone do nome do projeto.

| Figura 12: Árvore do projeto |
|:---------------------------------------------:|
| ![Árvore do projeto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/13.png{{site.rawimg}}) |

A cor verde dos arquivos, indica que são novos, ainda não incluídos ao controle de versão, definido conforme a Figura 13 como ***untracked***.

Obs.: O *set* de cores depende das configurações do MPLAB-X.

A Figura 13 mostra uma simplificação do fluxo de trabalho com o Git e com o GitHub. 


| Figura 13: Ciclo básico Git e GitHub |
|:---------------------------------------------:|
| ![Ciclo básico Git e GitHub]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/basico-GitGithub.png{{site.rawimg}}) |


Ainda com o projeto selecionado, vamos incluir os arquivos sob o controle do Git. 

* Clique em: ***Team*** -> ***Add***

| Figura 14: Inclusão de arquivos |
|:---------------------------------------------:|
| ![Inclusão de arquivos]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/14.png{{site.rawimg}}) |

Com os arquivos presentes no Git (***staged***), é necessário agora vinculá-los (***commit***), ou seja, produzir uma versão com as modificações adicionadas (***Unmodified***).

* Clique em: ***Team*** -> ***Commit***

| Figura 15: Comentário para o vínculo |
|:---------------------------------------------:|
| ![Comentário para o vínculo]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/15.png{{site.rawimg}}) |

Escreva na caixa de mensagem um texto que deixe claro o que foi alterado ou adicionado ao projeto. 

| Figura 16: Caixa de mensagem de vínculo, *commit* |
|:---------------------------------------------:|
| ![Caixa de mensagem de vínculo, commit]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/16.png{{site.rawimg}}) |

Essa descrição é fundamental para a construção do histórico de desenvolvimento do projeto, pois entre outras coisas, permite o resgate de uma versão num ponto determinado se bem documentado.

* Clique em: ***Commit***.


Na árvore de projetos, note que todos os arquivos ficaram pretos, indicando que estão salvos e vinculados pelo Git, na condição ***unmodified***.

| Figura 17: Árvore do projeto |
|:---------------------------------------------:|
| ![Árvore do projeto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/17.png{{site.rawimg}}) |

A partir desse ponto, ao editar um arquivo, com novas inserções, novas funcionalidades, comentários, etc, ele se torna ***modified*** e precisa ser adicionado (***add***), e vinculado (***commit***). 

Os arquivos e subdiretórios na condição ***unmodified*** são copiados para o repositório remoto, que nesse caso é o GitHub.

*	Clique em: ***Team*** -> ***Remote*** -> ***Push***

| Figura 18: Caminho para acesso remoto ao GitHub |
|:---------------------------------------------:|
| ![Caminho para acesso remoto ao GitHub]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/18.png{{site.rawimg}}) |


A tela de identificação do repositório remoto é aberta.

| Figura 19: Repositório remoto |
|:---------------------------------------------:|
| ![Repositório remoto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/20.png{{site.rawimg}}) |

*	Selecione *Specify Git Repository Location:*;
*	Selecione em *Remote Name*: **origin**;
*	Insira o endereço do repositorio, copiado na Figura 10, em *Repository URL:*;
*	Insira o nome de usuário em *User:*;
*	Insira a senha do GitHub em *Password:*;
*	Clique em **Next**.

| Figura 20: Ramo local |
|:---------------------------------------------:|
| ![Ramo local]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/21.png{{site.rawimg}}) |


*	Selecione a caixa de marcação ***master -> master[A]***;
*	Quando o projeto possui outros "ramos" (*branches*), eles vão aparecer aqui.

Selecione o ramo remoto que vai receber as atualizações.

| Figura 21 Local de atualização remoto |
|:---------------------------------------------:|
| ![Local de atualização remoto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/22.png{{site.rawimg}}) |

*	Selecione a caixa de marcação ***master -> origin/master[A]***;
*	Quando o projeto possui outros "ramos" (*branches*), eles vão aparecer aqui.

Volte ao repositório do projeto no GitHub.

| Figura 22: Repositório do projeto |
|:---------------------------------------------:|
| ![Repositório do projeto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/23.png{{site.rawimg}}) |

Os arquivos pertencentes ao projeto do MPLAB-X foram incluídos no repositório do GitHub. 
Note que a descrição de cada arquivo é o início da mensagem de vínculo, 
*commit message*.


## LEIA-ME / README

Uma parte fundamental ao se trabalhar com o GitHub é manter um arquivo de Leia-me (*README*) bem feito e atualizado. 

Sua função é descrever o projeto, dando uma visão completa ao leitor que venha visitá-lo através da plataforma GitHub. 

O arquivo README pode ser escrito com o extensão **.md**, arquivo no formato **Markdown**, que é suportado pelo GitHub e facilita a criação de um arquivo de boa legibilidade.

Muito material ensinando a utilizar o markdown pode ser encontrado na internet, 
mas segue um [Guia básico de markdown](https://docs.pipz.com/central-de-ajuda/learning-center/guia-basico-de-markdown#open) para começar. 


Para criar o arquivo de README.md: 

| Figura 23: Novo arquivo vazio |
|:---------------------------------------------:|
| ![Novo arquivo vazio]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/24.png{{site.rawimg}}) |

*	Clique com o botão direito do *mouse* em: ***Header Files*** 
* Selecione: ***New*** -> ***Empty File...***

| Figura 24: Novo arquivo vazio |
|:---------------------------------------------:|
| ![Novo arquivo vazio]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/25.png{{site.rawimg}}) |

*	Insira o nome do arquivo: **README.md**;
*	Verifique o nome do projeto;
*	Clique em ***Finish***.

O arquivo **README.md** está vazio, 
insira as informações relevantes sobre o projeto, 
e utilize as marcações do *markdown*
para obter um arquivo de boa legibilidade.

| Figura 25: Arquivo README.md  |
|:---------------------------------------------:|
| ![Árvore do projeto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/26.png{{site.rawimg}}) |

Note que o **README.md** está como uma arquivo ***untracked***.
Então, inclua ele no controle de versão (GIT).


| Figura 26: Adição do arquivo README.md ao controle de versão |
|:---------------------------------------------:|
| ![Adição do arquivo README.md ao controle de versão]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/28.png{{site.rawimg}}) |

Para adicioná-lo é possível fazer o seguinte:

*	Clique com o botão direito do *mouse* em: ***README.md*** 
* Selecione: ***Git*** -> ***Add***


| Figura 27: Caixa de mensagem de vínculo, *commit* |
|:---------------------------------------------:|
| ![Figura 27: Caixa de mensagem de vínculo, *commit*]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/29.png{{site.rawimg}}) |

*	Insira uma mensagem de vículo para o README.md;
*	Clique no botão ***Commit***.



Como o repositório remoto está vinculado ao projeto local, 
é possível fazer o *upload* (*push*) de forma simplificada.

| Figura 28: Inclusão do README.md no repositório remoto|
|:---------------------------------------------:|
| ![Inclusão do README.md no repositório remoto]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/30.png{{site.rawimg}}) |

*	Clique em:
*	***Team*** -> ***Remote*** -> ***Push to upstream***;

A atualização do arquivo no repositório remoto é feita de forma direta, sem a solicitação de identificação de acesso, pois já foi realizada, como pode-se ver no repositório do projeto no GitHub.

| Figura 29: Repositório do projeto no GitHub |
|:---------------------------------------------:|
| ![Repositório do projeto no GitHub]({{site.baseurlimg}}_posts/tUcPIC/capD-versionamento/31.png{{site.rawimg}}) |

O arquivo **README.md** é renderizado na tela principal do GitHub,
abaixo da lista de arquivos, facilitanto o seu acesso e visualização. 

<hr/>

>>> [<< Anexo C - Novos arquivos]({{site.baseurl}}/2021/capC-novosArquivos) << Anexo D - Controle de Versão >> [<< Arquivo de Configuração (config.h)]({{site.baseurl}}/2021/config)

<hr/>

[Voltar]({{site.baseurl}}/docs/tecnology/ucPIC)
