---
layout: post
title: "A autenticação de dois fatores é segura?"
date: 2018-09-16
tags: [Segurança]
comments: true
---

![](https://cdn-images-1.medium.com/max/2000/1*waKkp881IvOAFjkzp4wHZg.jpeg)

A autenticação de dois fatores (2FA) foi inventada para adicionar uma camada
extra de segurança ao procedimento de login simples — agora considerado
antiquado e inseguro — de inserir somente um nome de usuário e senha.

Com os procedimentos de login habilitados para 2FA, uma das situações mais
conhecidas é quando você tenta entrar em um site conhecido de um IP diferente
como, por exemplo, você tenta acessar o Facebook de um computador novo.

Você primeiro insere seu nome de usuário e senha no computador e, em seguida,
recebe uma mensagem de texto em seu telefone, ou em outro e-mail cadastrado
fornecendo um código de verificação. Você deve inserir esse código de
verificação no computador para concluir o procedimento de login.

## Os diferentes fatores de autenticação

A autenticação de dois fatores é uma versão menos complexa da autenticação
multifator (MFA), que simplesmente usa mais fatores para determinar a
autenticidade de um login. Então, quais são esses fatores? Existem três
categorias principais de fatores possíveis em uma configuração de MFA.

### Algo que você conhece

A categoria “algo que você conhece” é o fator com o qual estamos mais
familiarizados. Requer que uma pessoa insira informações que ela conhece para
obter acesso à conta. A combinação de um nome de usuário e uma senha é o
principal exemplo. Mas algumas outras questões de segurança, por exemplo as
usadas por seu banco, como senha silábica, se enquadram nessa categoria.

### Algo que você tem

Receber um código de verificação como o que mencionei anteriormente significa
que o procedimento que você está usando é o fator “algo que você tem” da
autenticação de dois ou múltiplos fatores. Algo que você tem pode ser uma conta
de e-mail ou telefone que seria usado para enviar um código de verificação, mas
também existem soluções de hardware especializadas, como o
[YubiKey](https://www.yubico.com/), que se enquadram nessa categoria.

### Algo que você é

A categoria “algo que você é” que ainda está em desenvolvimento, se concentra em
certos marcadores físicos que podem ser analisados ​​pela tecnologia, ou
biometria , para provar sua identidade. Esses dados biométricos incluem:

* Impressões digitais
* Varredura de retina
* Reconhecimento de voz
* Identificação de rosto

## Como o 2FA é vulnerável a ataques?

Apesar das melhores intenções — proteger os dados das pessoas, dificultando o
acesso a criminosos — , a autenticação de dois fatores (e multifator) ainda pode
se tornar vulnerável. Como? Os criminosos podem contorna-las por já estarem de
posse de um fator de autenticação, fazendo o uso de força bruta, ou usando a
ferramenta mais maligna que nenhuma tecnologia pode proteger: engenharia social
.

### Phishing

> **“Phishing** é uma maneira desonesta que cibercriminosos usam para enganar você
> a revelar informações pessoais, como senhas ou cartão de crédito, CPF e número
de contas bancárias. Eles fazem isso enviando e-mails falsos ou direcionando
você a websites falsos.” — [AVAST ](https://www.avast.com/pt-br/c-phishing)—

O *phishing* pode ser usado para atrair vítimas para uma página de login falsa.
Quando a vítima digita suas credenciais, o invasor a redireciona para a página
de login real, desencadeando o procedimento 2FA que solicita à vítima o código
numérico que foi enviado para ele ou em alguns casos, produzido por um
aplicativo autenticador.

O atacante captura esse código novamente na página de login falsa que a vítima
ainda está usando e agora tem um conjunto de autenticação completo. Obviamente,
devido ao *timebox (o tempo em que o código é válido)* que tem nesses códigos
numéricos, o atacante terá que ser rápido. Mas, uma vez que ele logue com
sucesso, não há nada que o impeça de mudar o número de telefone, ou e-mail, para
o qual o próximo código será enviado — ou qualquer outra coisa na conta que ele
queira.

[O Brasil é o pais que sofre mais ataques de phishing no
mundo](https://www.tecmundo.com.br/seguranca/133244-1-lugar-brasil-pais-sofre-ataques-phishing-mundo.htm),
então para nossa realidade esse seria um ataque mais efetivo para quebrar essa
autenticação.

### Resetar a senha

Alguns procedimentos de autenticação podem ser ignorados quando se é realizado
um procedimento de “senha perdida”, se o atacante estiver de posse do item “algo
que você tem”.

Por exemplo, digamos que o invasor tenha acesso à conta de e-mail da vítima e
que um link de verificação para um determinado login tenha sido enviado para
essa conta. Nesse caso, o invasor pode usar o link “Esqueceu sua senha” no site,
usar o e-mail que está em sua posse para receber o código de verificação e
alterar a senha.

### Força bruta

Força Bruta no caso seria fazer os testes de todas as possibilidades do código
que foi enviado. Explico um pouco mais sobre força bruta
[aqui](https://medium.com/@pmdragon/uma-visÃ£o-geral-sobre-funÃ§Ãµes-hash-teoria-e-seguranÃ§a-c3f9ae74755e).

Alguns *tokens* 2FA são tão curtos e limitados em caracteres o que os torna
facilmente obtidos pela força bruta. A menos que existam cofres contra falhas,
um *token* de quatro dígitos é completamente inútil se o invasor tiver tempo
para aplicar força bruta e se o sistema não tiver um bloqueio do número de
tentativas. *Tokens* que possuem uma validade limitada no tempo (TOTP) oferecem
melhor proteção contra esse tipo de ataque.

### Login de terceiros

Em alguns processos de login, é oferecido ao usuário a opção de fazer o login
usando uma conta de terceiros e ao usar esta opção se ignora o procedimento 2FA.
O exemplo mais conhecido é o “login com sua conta do Facebook”, usado para
determinados sites e aplicativos. Nesse caso, um invasor pode assumir outras
contas depois de conhecer suas credenciais do Facebook. Embora seja prático, não
é recomendado que assine o uso de terceiros, a menos que seja absolutamente
necessário.

## Como podemos nos proteger?

Com mais violações de dados de empresas extremamente populares registradas a
cada mês, a autenticação 2FA está rapidamente se tornando um procedimento
padrão. E mesmo que hajam maneiras de contornar o 2FA, ainda é mais seguro do
que apenas usar a antiga combinação de nome de usuário e senha. Para contornar o
2FA, o invasor ainda teria que interromper dois ciclos de autenticação.

Então, como podemos fazer a nossa parte para manter criminosos longe do 2FA?

* Preste atenção nos e-mails informando que uma conta foi usada em um dispositivo
novo ou desconhecido e verifique se era realmente você. Além disso, preste
atenção a outras bandeiras vermelhas óbvias, como e-mails que notificam sobre
tentativas de login com falha ou solicitações de redefinição de senha que não
vieram de você.
* Se você tem uma conta no Facebook, verifique em Configurações> Aplicativos e
Websites se tudo o que você listou foi usado por você e se deveria estar lá.
Além disso, lembre-se de que uma conta do Facebook “desativada” pode ser
ressuscitada quando você usar a opção “fazer login com sua conta do Facebook” em
algum lugar. Esse procedimento não é somente para o Facebook, Twitter, e outros
sites também oferecem API de autenticação, então é sempre bom revisar todos;
* Se você tiver a opção de escolher qual o procedimento de autenticação usar,
pesquise as vulnerabilidades conhecidas e aplique essas lições. Por exemplo,
algoritmos de *token* fracos podem ser usados ​​por um invasor para prever o
próximo *token*, se eles puderem ver os anteriores. Ou usar *tokens* curtos sem
uma validade limitada pode deixá-los abertos para receber ataques.
* Treine você e sua equipe para reconhecer tentativas de *phishing*.

Se o 2FA ainda estiver vulnerável, você pode estar se perguntando: “Então, por
que não usar a autenticação multifator?” A triste verdade é que até mesmo a
autenticação multifator tem seus problemas. Os métodos para a autenticação “algo
que você é” que está sendo usado em nossos dispositivos agora, ainda são bem
fáceis de enganar— não é preciso um hacker genial para burlar o reconhecimento
de voz.

Mas a indústria está aprendendo rapidamente. Por exemplo, o uso de duas câmeras
de alta definição distanciadas tornou o iPhoneX muito melhor no reconhecimento
facial do que alguns dos modelos mais antigos do iPhone. À medida que versões
mais seguras e robustas da autenticação multi-fator são disponibilizadas, a
esperança permanece que algum dia, seja algo praticamente impossível de se
enganar.

*Baseado do post de *[Pieter
Arntz](https://blog.malwarebytes.com/author/metallicamvp/)*, versão original (em
inglês),
*[aqui](https://blog.malwarebytes.com/101/2018/09/two-factor-authentication-2fa-secure-seems/)*.*



