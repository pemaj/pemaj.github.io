---
layout: post
title: "Princípios de Kerckoff e a criptografia da ABIN"
date: 2018-09-09
tags: [segurança, criptografia]
comments: true
---

Essa é uma notícia não tão nova, mas estava a tempos querendo escrever sobre o
assunto.

A ABIN criou um sistema de criptografia próprio para comunicação governamental,
porém, o código da ABIN é fechado, como é possível validar no link abaixo:

[http://www.abin.gov.br/atuacao/produtos/tecnologia/criptogov-e-cgov/](http://www.abin.gov.br/atuacao/produtos/tecnologia/criptogov-e-cgov/)

Analisando este fato, entende-se que a ABIN não entende de criptografia básica,
já que o algoritmo desenvolvido pelo governo não respeita um dos principais
*Princípios de Kerckoff*, que diz que:

“Um sistema criptográfico deve ser seguro mesmo se um atacante conhecer detalhes
sobre o sistema, com exceção da chave privada”.

Outros *Princípios de Kerckoff*, em tradução direta, são:

1. O sistema deve ser materialmente, se não matematicamente indecifrável;
2. **É necessário que o sistema em si não requeira sigilo, e que o mesmo possa cair
sem desvantagem em mãos inimigas;**
3. A chave precisa ser comunicável e custodiável sem a necessidade de auxílio de notação escrita, e precisa ser
alterável e substituível a critério dos correspondentes interlocutores;
4. É necessário que o sistema seja aplicável à correspondência telegráfica;
5. É necessário que o sistema seja portável, e que seu manuseio e operação não exijam
a participação de muitas pessoas;
6. Por fim, é necessário, considerando as circunstâncias que demandam o seu uso, que o sistema seja fácil de usar, não
demandando concentração ou conhecimento demasiados ou uma série de regras que
precisam ser observadas.

Se o algoritmo é para garantir sigilo das comunicações do alto escalão do
Governo Federal, por que eu não posso contribuir para ajudar a melhorar a
segurança do meu pais?

Obviamente não se pode dizer que quem trabalha a ABIN não saiba o que está
fazendo, muito pelo contrário, se estão lá é porque apresentam capacidade o
suficiente para exercer tal trabalho. Porém em meio a isso creio que o software
aberto poderia ser uma solução para melhorar possíveis problemas de segurança
contando com a ajuda de profissionais brasileiros.

Teriam algumas vantagens significativas nesse caso:

* Melhoria da qualidade da criptografia, afinal, quanto mais olhos veem, mas
chance de encontrar *bugs;*
* Estudo do código, estudantes de criptografia poderiam estudar esse código e
desenvolver ferramentas cada vez melhores, o que melhoraria a ciência nacional;

Criar um algoritmo de criptografia não é coisa para meia dúzia de pessoas mesmo
sendo profissionais extremamente capazes.

Uma das soluções então poderia ser uma criação de um concurso onde várias
equipes mandassem seus algoritmos criptográficos para análise, onde seria
escolhido o melhor. Como por exemplo no caso da *AES*, clássico sistema do
governo norte americano que foi proposto em 1998, editado e somente liberado
para uso em 2001.

Após este período, ele foi testado inúmeras vezes, através de inúmeros
trabalhos, estudos, artigos e implementações buscando sua melhoria. Ou seja,
foram três anos de análise onde dezenas de algoritmos foram submetidos.

No processo foram selecionados dezoito algoritmos em que cada algoritmo foi
destinado a uma equipe. Essas equipes tentaram quebrar o código umas das outras
no processo. Após este período, sobraram cinco equipes, ou seja, cinco
algoritmos e por fim, um foi selecionado como o melhor.

Durante todo este processo de melhoria, pode-se aprender várias coisas sobre o
*AES*, fazendo com que surgissem outras recomendações de segurança e até hoje
surgem cada dia mais trabalhos e recomendações.

Existem alguns estudos que mostram algumas coisas a “não se fazer” em que a
comunidade pode aprender com isto. Assim como existem milhares de casos onde o
*AES* é totalmente inseguro (se você não fizer do jeito certo).

Por exemplo, [timming side channel
attacks](https://en.wikipedia.org/wiki/Timing_attack), onde é possível recuperar
uma chave do *AES* em menos de um minuto se a implementação for falha. Como é
possível saber se não liberar o código? Só com o time da ABIN?

Se isto é para “segurança nacional”, o ideal é que primeiramente fosse seguro.

Seria excelente se houvesse uma competição, como no *AES* . Talvez dessa forma
a busca pela segurança do país fosse aprimorada e não encubada somente em um
grupo seleto de pessoas que como todos nós, também tem suas limitações.

Uma pena.

![7x1](https://media.giphy.com/media/3xz2BqDpJrthGN1TYk/giphy.gif)
