---
layout: post
title: "Dicas para trabalhar com scripts bash"
date: 2018-08-27
excerpt: "Algumas dicas para melhorar o processo de fazer scripts bash"
published: true
tags: [bash, dicas, test, script]
comments: true
---

<p align="center">
  <a href="https://medium.com/@pmdragon/tips-for-working-with-bash-scripts-ff85c0420ac7">English version</a>
</p>

Anos atrás eu estava programando para uma pequena empresa que trabalhava com *sistemas embarcados*. Lá eu escrevi códigos para *shell scripts*, *scripts python* e outro códigos para *sistemas embarcados*, às vezes para clientes que moravam em outro estado com máquinas que eu não tinha acesso, então meus roteiros eram sempre uma *caixa preta* e por isso era muito comum enviar as atualizações por e-mail.

![whaat](https://media.giphy.com/media/nkLB4Gp8H6hFe/giphy.gif)

Por isso, o cliente me enviou um e-mail com o assunto: “Não está funcionando”. Em 5 minutos eu atualizava o arquivo e enviava de volta. Problema resolvido certo? Não totalmente.

É difícil para pequenas empresas, mesmo freelancers, fazer uma boa logística para trabalhar bash scripts porque o cliente não pode esperar e você tem que fazer alguma coisa para resolver o problema, então a ação "adiciona esta linha" sempre ganha contra um processo robusto.

Depois de muitos problemas, como desenvolvedor e freelancer, quero compartilhar bons conselhos para o trabalho com arquivos *sh* (talvez possa ser útil para outros scripts)

São dicas simples, mas os erros (e dor de cabeça) estão nos detalhes:

## Escreva todas as funções (isoladas, se possível)

Se tiver uma lógica mais fragmentada, ajudará quando precisar mudar e reciclar seu código.

Faça um escopo para cada função e assim para você poderá alterar a lógica sem erros.

## Sempre escolha o arquivo no master

É óbvio, eu sei, mas no mundo real, mudar o seu arquivo para enviar para o seu
cliente sem commit antes é mais rápido, e em um dia agitado, você pode esquecer de fazer este commit mais tarde, então você tem um arquivo no seu git e outro com o seu cliente. Não é difícil imaginar cenários catastróficos.

## Sempre crie ramificações para o trabalho

Essa dica é geralmente para equipes, mas funciona bem também para freela e ajuda a não fazer commit direto no master assim como evita bugs sem revisão e “commit por
commitar”.

## Comente no script de shell

É uma discussão eterna sobre comentar seu código ou não, em outros linguagens eu acredito que não é necessário, mas como em *bash* às vezes não é intuitivo, e como eu sou um desenvolvedor prático, eu prefiro comentar meus *bash scripts*, no final isso salva meu tempo.

## Fazer testes
Sim, teste em scripts bash.

![Do-test](https://media.giphy.com/media/3o6Mbbs879ozZ9Yic0/giphy.gif)

Esses testes não precisam ser um teste de unidade, mas podem ser testes funcionais, por exemplo. Se o seu script mover um arquivo para outra pasta, você poderá:

1. criar um arquivo na pasta original
1. executar o script
1. faça o assert que o arquivo está na pasta de destino, e não na origem

Com testes, é fácil ver erros bobos. Fazer o teste em bash é difícil às vezes, então se precisar use outra linguagem para isso, o Python é uma boa escolha e é minha preferência.

## Fazer um log

E finalmente a dica dourada. Um bom log, ajudará a identificar os erros
mais rápido, e é útil para ver toda a atividade e desempenho, como encontrar bugs e
gargalos do sistema. É fácil fazer o login nos arquivos bash, por isso não há um motivo para não fazer um.

Estas são as minhas dicas para fazer um processo com menos bugs e erros fatais.
