# aapa-ia

### Enunciado

Esta atividade avaliativa discute as etapas de implementação de um Agente Aspirador de Pó Automático (AAPA) simples em um ambiente quadrado 4 x 4.

1) CONSTRUÇÃO DO AMBIENTE:

Você deve trabalhar com uma Matriz 6X6 (o ambiente em questão é um espaço 4X4, e o restante são paredes). 

O ambiente gráfico serve somente para visualização;

A sujeira (tanto a quantidade de sujeira na sala como a posição) deve ser disposta aleatoriamente pelo algoritmo. 

* a sujeira deve estar disposta aleatoriamente.

-------- Deixo aqui um modelo para gerar o ambiente no python:------

#### Função que exibe o ambiente na tela

#### Funciona apenas em ambientes com a biblioteca matplotlib instalada.

import numpy as np

import matplotlib.pyplot as plt

import random

#### Função que exibe o ambiente na tela

def exibir(matriz):    
    global posAPAx
    global posAPAy
    
    # Altera o esquema de cores do ambiente
    plt.imshow(matriz, 'gray')
    plt.nipy_spectral() 
    
    # Coloca o agente no ambiente 
    plt.plot([posAPAy],[posAPAx], marker='o', color='r', ls='')
    
    plt.show(block=False)
    
    # Pausa a execução do código por 0.5 segundos para facilitar a visualização
    plt.pause(0.5)    
    plt.clf()
-------------------------------------------------------------

2) CONSTRUÇÃO DO AGENTE REATIVO SIMPLES

Escreva uma função de Agente Reativo Simples para o mundo 4 x 4 do aspirador de pó automático que garante limpar toda a sala, independentemente da posição inicial. 
A função deve ser chamada agenteReativoSimples(percepcao) e deve retornar uma das 5 possíveis ações ('acima', 'abaixo', 'esquerda', 'direita', 'aspirar'). A variável "percepcao" dentro dos parênteses é a entrada da função, isto é, a posição (x, y) em que o agente se encontra e o status da percepção (limpo ou sujo).
Para movimentar o agente dentro do ambiente você pode considerar criar uma função de mapeamento (funcaoMapear) como um ponto de partida. Isto é, você pode fazer um caminho (ou mapa) onde o agente percorre todo o ambiente.
Tenha em mente que as ações contra a parede (por exemplo, mover para a esquerda quando já está posicionado no ponto (1, 1) não têm nenhum efeito (isto não significa que são proibidas).
COMO O AGENTE REATIVO SIMPLES FUNCIONA:

Play Video
Lembre que o agente reativo simples funciona com ação-reação e não vai parar assim que limpar todo o ambiente.
Responda: A) A sua solução é extensível para um mundo 3 x 3? E para um mundo 6 x 6? Explique sua resposta.

-------------------------------------------------------------

3) CONSTRUÇÃO DO AGENTE  BASEADO EM OBJETIVO

A partir da estrutura do Agente Reativo Simples, aumente o código para transformá-lo em Agentes Baseados em Objetivos, na qual:

o agente tem que limpar toda a sala (função objetivo)

o agente começa a partir quadrado (1, 1)

Escreva uma função de verificação (checkObj(sala)) fora do programa agente que verifica se há sujeira na sala (retorna 1 se tem sujeira, caso contrário retorna 0).

Acrescente a ação de Não Operar "NoOp" na lista de ações do agente e ajuste a ação para "NoOp" uma vez que a sala estiver limpa.

A função de agente deve ser chamada agenteObjetivo(percepcao, objObtido) e deve retornar uma das 6 ações possíveis (5 inicialmente definidas + "NoOp"). O parâmetro objObtido é a saída da função checkObj(sala).

Utilize também uma variável de contador (chamada pontos) que contém o número de passos que o agente leva até atingir o objetivo (inclusive a Ação Aspirar conta 1 ponto). Por exemplo: 

Estado da percepcao: 0 Acao escolhida: abaixo

Estado da percepcao: 0 Acao escolhida: esquerda

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 1 Acao escolhida: aspirar

Estado da percepcao: 0 Acao escolhida: acima

Estado da percepcao: 0 Acao escolhida: esquerda

Estado da percepcao: 0 Acao escolhida: abaixo

Estado da percepcao: 0 Acao escolhida: abaixo

Estado da percepcao: 0 Acao escolhida: abaixo

Estado da percepcao: 1 Acao escolhida: aspirar

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 0 Acao escolhida: acima

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 0 Acao escolhida: acima

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 0 Acao escolhida: abaixo

Estado da percepcao: 0 Acao escolhida: esquerda

Estado da percepcao: 0 Acao escolhida: abaixo

Estado da percepcao: 0 Acao escolhida: direita

Estado da percepcao: 1 Acao escolhida: aspirar

Ponto: -> 22
