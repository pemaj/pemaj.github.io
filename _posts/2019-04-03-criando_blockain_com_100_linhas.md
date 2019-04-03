---
layout: post
title: Criando um blockchain com menos de 100 linhas de código
excerpt: "Um pequeno guia para criar uma implementação simples de blockchain"
publicado: true
tags: [Criptografia, BlockChain, Python]
canonical_url: https://dev.to/pemtajo/creating-a-blockchain-with-less-100-code-lines-5aba
feature: https://cdn-images-1.medium.com/max/1024/0*QADifoe26ax-QP_9
date: 2019-04-03
comments: true
---

O conceito básico de blockchain é muito simples: um banco de dados distribuído que mantém uma lista crescente de registros ordenados.

O blockchain é um termo normalmente associado ao Bitcoin e/ou Ethereum, mas blockchain é mais que isso, blockchain é a tecnologia por trás deles, e por trás de qualquer outra criptomoeda.

Há muitos usos de outros para blockchain, por exemplo, jogos ([CryptoKitties](https://www.cryptokitties.co/)) ou também blockchain + IOT (Internet das coisas), e este é apenas o começo para o tecnologia.

![](https://cdn-images-1.medium.com/max/805/1*TV_02Syq-SWRChiXigN8Rw.png)
<figcaption> Uma simples imagem sobre o conceito do blockchain</figcaption>

O blockchain é, como o nome diz, uma cadeia de blocos, então temos a primeira classe, o Block.

![](https://cdn-images-1.medium.com/max/1024/1*0D3Uc7yIyR7Kv-n7Fq6vXA.png)

Nesse estágio meu bloco tem os atributos:

- índice - o índice de bloco a posição na cadeia
- timestamp - data e hora em que o bloco foi adicionado no Blockchain
- data - o valor dos dados, em outras palavras, o que você deseja salvar
- hash anterior - o hash do índice de blocos -1
- hash - o hash do bloco

Se você não sabe o que é hash, eu expliquei no meu último post [aqui](https://pemtajo.github.io/hash_teoria_seguranca/).

Você verá algumas coisas interessantes na foto e aqui vou explicar um pouco:

- deixe mais OOP a função _isValid_ é para cada bloco responder se ele for válido
- O construtor define todas as coisas no bloco
- a função “update” é atualizar o _dict_ ao ler um arquivo, isto é para salvar os dados para o futuro
- calculando o hash para arquivos salvos anteriormente, para converter sempre para o mesmo encode, no caso utf-8, porque encodes diferentes possuem caracteres diferentes e caracteres diferentes produzem hashes diferentes.

Portanto, esta é uma corrente válida, se o bloco foi alterado, o bloco atual saberá e ficará inválido, e se qualquer bloco anterior foi alterado, a cadeia saberá e toda a cadeia será inválida. Esse é o conceito que faz com que os dados salvos no Blockchain sejam imutáveis.

Então, olhando na nossa segunda classe, Blockchain:

![](https://cdn-images-1.medium.com/max/1024/1*RKxCwUFAebYgfkMjvJCeZA.png)

Assim, a classe blockchain cria os blocos e procura por qualquer problema na cadeia, e essa classe é responsável por salvar em um arquivo JSON simples e ler dele. Nossa primeira versão blockchain está pronta !! \o/

Todo o código está abaixo, você pode executar e ver a saída

{% gist https://gist.github.com/pemtajo/18d0f598033757f7390b514ded6f75b4%}

Nesta versão do nosso blockchain, não implementamos a [Prova de Trabalho](https://pt.wikipedia.org/wiki/Prova_de_trabalho), a ideia primeiro é criar o blockchain e garantir a integração da cadeia. Esse será o meu próximo passo.

Eu criei um projeto que você pode seguir no [GitHub](https://github.com/pemtajo/blockchain), vou incrementar cada vez mais o meu blockchain, se tiver interesse basta me seguir, vou escrever alguns posts sobre todo o processo.

_P.S: Eu não sou um expert no blockchain, então qualquer problema, correção de código, ou dicas, isso é muito bem vindo a comentar abaixo e vai ajudar algumas pessoas também. Ou você pode falar comigo em particular no _[_LinkedIn_](https://www.linkedin.com/in/pedromaraujo/)_._

Te vejo em breve!