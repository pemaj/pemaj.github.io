---
layout: post
title: "Exemplo PLY (Python Lex-Yacc)"
date: 2018-07-27
excerpt: "Um exemplo de fazer um compilador em usando PLY (Python Lex-Yacc)"
published: true
tags: [python]
comments: true
---

Quando estava no último ano da faculdade. Tive que fazer um compilador para uma
linguagem fictícia. O escolhido foi o *python* para me ajudar na tarefa, pois
era mais prático utilizá-lo pois muitas estruturas de dados eram naturais na
linguagem não sendo necessárias cria-las na mão como em C ou C++ por exemplo.

Não queria criar algo do 0, queria fazer algo prático, foi quando vi o
[PLY(Python Lex-Yacc)](http://www.dabeaz.com/ply/ply.html), que é uma
implementação de *lex* e *yacc* parser para Python, decidi usá-lo. O material da
linguagem está [aqui](http://www.dabeaz.com/ply/ply.html)(em inglês), mas
infelizmente como é um material completo, não é um guia e tem que ficar lendo
vários parágrafos e garimpando informação para achar algo.

Usar o *PLY* foi uma boa escolha, pois ele é muito mais fácil do que imaginei e
consegui desenvolver o analisador léxico e sintático, mas tive dificuldades de
encontrar um material em português, dessa forma esse post é para ajudar quem
precisa de ajuda na implementação de algo usando *PLY*, espero que seja útil
para alguém.


>O projeto está no meu [*github*](https://github.com/pmdragon/compiler_python), esse post será baseado nele e por que desenvolvi
ele dessa forma, escrevendo algumas dúvidas que tive enquanto o desenvolvi.


O arquivo principal é o
[cmm.py](https://github.com/pmdragon/compiler_python/blob/master/cmm.py), é a
partir dele que será chamada os *parsers* da minha linguagem.

Criei um arquivo chamado de
[mylexer.py](https://github.com/pmdragon/compiler_python/blob/master/mylexer.py)
que é o analisador léxico, onde coloquei todas as definições de *token*, ou
seja, o que é numero, string, comentários, palavras reservadas e coisas
específicas da análise léxica.

```python
reserved = {
	'false'	:	'FALSE',
	'if'	:	'IF',
	'else'	:	'ELSE',
	'int'	:	'INT',
	'string':	'STRING',
	'true'	:	'TRUE',
	'write' :	'WRITE',
	'read' :	'READ'
}

tokens = [ 'NUMBER', 'RPAREN', 'LPAREN' ]+ list(reserved.values())

t_ignore 		= ' \t'

t_RPAREN		= r'\)'
t_LPAREN		= r'\('


def t_NUMBER(t):
	r'\d+'
	t.value = int(t.value)
	return t
```

Como nesse exemplo simplificado , optei por criar um array com as palavras
reservadas, dessa forma ficam separadas dos *tokens *e sendo mais difícil gerar
confusão.

**As funções tem que ser criadas com o mesmo nome do token, mas com um “t_” na
frente. É dessa forma que o PLY faz a relação.**

Após isso criei o arquivo
[grammar.py](https://github.com/pmdragon/compiler_python/blob/master/grammar.py),
onde está as regras da minha gramática, onde defino as regras de precedência, o
que é um literal, um programa , variável, e todas as regras da análise sintática
necessária.

```python
# Parsing rules
precedence = (
    ('left','LPAREN','RPAREN'),
    ('left','AND','OR'),
    ('left','MAIOR','MENOR', 'MAIOREQUALS', 'MENOREQUALS', 'EQUALS', 'DIFF'),
    ('left','PLUS','MINUS'),
    ('left','TIMES','DIVIDE'),
    ('right','UMINUS', 'NOT', 'TERNARY'),
    )

#define
def p_empty(p):
    'empty :'
    pass

def p_define_end_of_instruction(p):
    'end : SEMICOLON'


def p_literal(t):
    '''literal : NUMBER
                | TRUE
                | FALSE
                | NORMALSTRING
                '''
    t[0]=t[1]

def p_sequence_literal(t):
    '''sequence_literal : literal COMMA sequence_literal
                        | literal'''


def p_define_type(t):
    '''type : INT
            | STRING
            | BOOL'''
    t[0]=t[1]

def p_variavel(t):
    '''variavel : NAME
                | NAME LCOLC expression RCOLC'''
    t[0] = t[1]
```

O arquivo grammar usa os tokens definidos na análise léxica.

**As funções devem que ser criadas com o mesmo nome do regra semântica, mas com
um “p_” na frente.**

Eu usei bastante *prints* do *python* para imprimir cada *token* e cada operação
durante a execução para entender cada etapa me ajudou bastante o fluxo.

Nesse projeto eu comecei a análise semântica, mas está incompleto. Também tentei
fazer um arquivo separado para erros, mas como era o último período e eu tinha
outros projetos não finalizei, podem dar *fork* e terminarem sem preocupação.

Eu escrevi esse texto 1 ano depois de ter entregado o projeto, por isso muita
coisa pode ter se perdido e provavelmente muitas informações ficaram rasas. Por
isso se chegou até aqui, pode entrar em contato comigo se tiver alguma dúvida
que terei prazer de ajudar o máximo possível.

