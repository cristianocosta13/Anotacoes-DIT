# Git Flow

## O que é?

O git flow trata-se de uma estratégia de organização em projetos que envolve vários contribuintes, estes trabalhando simultaneamente, e determina um padrão de nomenclaturas de relacionamento entre branches a fim de manter um fluxo de trabalho.  Ou seja, é um fluxo de trabalho padronizado que dita regras de relacionamento entre branches. 

* Git Hub Flow: Fluxo simplificado do git flow o qual possui uma branch ``master`` e cada vez que algo diferente for implementado no código, será criada uma ``feature`` e, ao final do projeto, as features são mescladas à branch master. Nessa versão simplificada há, ainda, a opção de criar um ``bugfix`` caso haja eventuais problemas na master uma vez que efetuada a meschagem feature-master citada anteriormente, no intuito de resolver nela tais problemas. 

> *Esse fluxo simplificado é utilizado somente em aplicações pequenas.*

## Estrutura

A estruturação se dá a partir de 5 branches principais:

* Master/Main
  * Hotfix
  * Releases
* Devlop
  * Features

As branches master e develop são fixas e irão existir no projeto independente das alterações implementadas. As outras três, no entanto, permanecerão apenas enquanto houver modificações a serem feitas. Quando estiver "tudo ok" no projeto, elas são excluídas. 

### Master/Main

#### Hotfix

#### Releases

### Devlop

#### Features

## Criando um projeto com git flow

comandos:

``git flow init``

``git flow feature start <nome>``

``git flow release start <nome>``

``git flow feature finish <nome>``

``git flow release finish <nome>``

Para sair da mensagem de merge ao finalizar a release:

```
Ctrl+c
:wq!
Enter
```

### Material de apoio:

> Using git-flow to automate your git branching workflow: https://jeffkreeftmeijer.com/git-flow/

> Git flow na prática: https://youtu.be/wzxBR4pOTTs

> Trabalhando em equipe com git flow: https://youtu.be/394mc6PV8t8
