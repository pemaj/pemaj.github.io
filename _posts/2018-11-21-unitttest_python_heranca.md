---
layout: post
title: "Uma forma de executar testes usando unittest Python somente nas classes filhas"
date: 2018-08-20
published: true
tags: [Programação, Python, test]
comments: true
---

Estava buscando fazer testes em *python* usando
[unittest](https://docs.python.org/3/library/unittest.html), para isso tinha
algumas premissas nesses testes:

* Python 3
* Prático
* Código *Pythônico*
* Orientado a Objeto
* Fácil criar testes
* Sem código duplicado

Desse jeito, a primeira ideia foi colocar o comportamento na classe pai e fazer
herdar para as filhas, o *unittest* vai tratar todas as classes herdadas de
*TestCase* como classe de testes, então, fiz o OO como manda a cartilha.

Mas infelizmente ao rodar meus testes a saída ficou assim

![](https://cdn-images-1.medium.com/max/800/1*WI2nzS_O_c8Z8d3iNBF6qA.png)

Além de tomar erro, não quero que seja executado os testes da minha classe pai,
somente das classes filhas.

Minha primeira solução foi colocar um *if* verificando o tipo de objeto antes,
mesmo não dando erro, e sempre com sucesso nos testes da classe pai, acaba por
deixar o código extremamente feio, e é uma saída preguiçosa.

Mas achei uma solução mais interessante para o problema:

![](https://cdn-images-1.medium.com/max/800/1*8OMYTcFjQ42YlBAZLnKsRA.png)

Usando o conceito de [mixin](https://en.wikipedia.org/wiki/Mixin), confesso que
no começo me senti desconfortável com esse código, mas a partir de um segundo
momento, ele me pareceu mais interessante, dessa forma consigo colocar os
comportamentos nas classes pai e ao criar uma nova classe de testes esse
comportamento virá por herança.

Ainda gostaria de deixar o “OO mais OO”, colocando a classe pai filha de
*TestCase* e fazendo alguma forma de ignorar esses testes, mas não encontrei
nenhuma forma mais interessante para isso, se alguém pensar de alguma outra
forma, mande nos comentários.

Até a próxima.
