---
layout: post
title: "Uma dica para programação em Python For — Else"
date: 2018-05-29
published: true
tags: [Programação, Python]
comments: true
---

Navegando na internet descobri uma propriedade interessante para o Python, se
trata do `for-else`.

A ideia de um `else` para o `for` pode parecer estranha à primeira vista, mas
olhando mais atentamente é algo útil que possivelmente serve para otimizar
alguns códigos.

O `else` do `for` é chamado quando o laço de repetição se completa normalmente,
ou seja, sem que tenha ocorrido nenhum `break `durante sua execução.

Dessa forma um código bem simples como busca de um valor específico em uma
lista, geralmente é programado da forma abaixo. Com uma variável controladora
para verificar o motivo que saiu do `for`.

```python
array = ['Bill Gates', 'Steve Jobs', 'Elon Musk']

find=False
for element in array:
    if(element == 'Nobody' ):
        print("Ok! I found Nobody")
        find=True
        break

if(not find):
    print("Sorry! I not found :T")
```

Com o uso do `for-else`, não há necessidade dessa variável, ocorrendo uma
“enxugada” no código e sem o perigo de ter algum controle errado da mesma,
ficando algo assim:

```python
array = ['Bill Gates', 'Steve Jobs', 'Elon Musk']

for element in array:
    if(element == 'Nobody' ):
        print("Ok! I found Nobody")
        break
else:
    print("Sorry! I not found :T")
```

O código original que continha 11 linhas, passou a ter 8 linhas e uma variável a
menos na memória. Deixando o código mais enxuto e de certa forma até mais
elegante.

Trabalhando com sistemas embarcados que tem memória (bem) limitada as vezes,
esse tipo de atuação pode liberar quantidades preciosas de bytes que poderão ser
úteis para outros processos.
