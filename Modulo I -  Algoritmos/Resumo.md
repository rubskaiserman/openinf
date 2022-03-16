# Algoritmos

## Sumário
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 
- 






## Capitulo 1 - O computador
### Antes de falarmos sobre algoritmos, linguagens de programação, e desenvolvimento de software, é necessária uma breve explicação sobre como computadores funcionam, e principalmente o que eles são, afinal, eles são a base que nos permite escrever código.
<br>

### "Um computador é uma máquina que manipula dados a partir de uma lista de instruções."[^1] 
[^1]: Fabricio Ferrari e Cristian Cechinel em Introdução a algoritmos e Programação
<br>
Leia-se, uma calculadora com esteróides. Um computador nada mais é do que uma calculadora inconcebivelmente potente, que recebe uma série de instruções, leia-se código binário, e faz uma série de contas com isso, e depois devolve um ou mais resultados.



A partir daqui já podemos chegar a uma definição resumida do que é o computador.
![Entrada->Processamento->Saída imagem de cs50-Harvard](imagens/input_output.png)[^2]
[^2]: Imagem de cs50-Harvard-Course

A imagem acima demonstra bem a ideia, do lado esquerdo nós temos um input, leia-se entrada de dados, do lado direito nós temos o output, leia-se saída de dados, e no meio dessas duas coisas temos um quadrado mágico conhecido como computador.

### 1.2 A arquitetura básica

O computador é representado por duas partes principais. Os dispositivos de entrada e saída(teclado, mouse, monitor, speakers e etc), e as partes internas que normalmente são resumidas ao processador e a memória.

Uma versão mais complexa e específica de uma arquitetura pode conter placa mãe, memória ram, memória rom, armazenamento interno, placa de vídeo e etc. Porém, para o funcionamento de um computador, é necessário um processador para fazer as contas, leia-se processar os dados, e os próprios dados, que são dados a partir da memória. A placa mãe faz a união dessas partes, mas são o processador e a memória que realizam o trabalho.

### 1.2.1 Processador
**Cada Operação do processador é representada pela seguinte lista de procedimentos:**
- Busca de Instruções na memória
- Interpretação de uma instrução
- Execução da instrução intepretada
- gravação de eventuais resultados do processamento
- Reinicio do processo caso necessário

Em uma estrutura de algoritmo simples isso poderia ser representado como:

```
função processar(memória){
    enquanto tiver operações pra realizar na memória faça o seguinte{
        Interpreta o que a memória tá te mandando fazer
        Agora faz o que ela mandou
        Agora responde o que ela pediu
    }
}
```

### 1.2.2 Memória Ram[^3]
[^3]: O tópico era mais generalizado para memória no geral. Mas memória Rom e memória secundária não são de grande importância no momento.

Memória Ram pode ser visualizada como uma grande tabela com duas colunas. Endereço e dado:

| Endereço | Dado |
|----------|------|
|0x00000001|     0|
|0x00000002|     1|
|0x00000003|     1|
|0x00000004|     1|
|0x00000005|     0|
|0x00000006|     0|
|...|     ...|

Onde cada bloquinho pode armazenar um bit. Mais a frente falaremos sobre estruturas de dados e como se manipulam esses endereços, por que é importante entender bem a memória entre outros assuntos.

## Capitulo 2 - Algoritmos
### 2.1 Conceito de algoritmo
Um algoritmo pode ser definido como uma sequência finita de passos a fim de resolver um problema.

### O exemplo clássico, a receita de bolo:
**Problema: Preparar um bolo**<br>
**Algoritmo de solução:**
```
- Pegar os ingredientes
- Colocar os ingredientes na mesa
- Pegue o liquidificador e a forma
- Coloque o forno para preaquecer na temperatura indicada
- Bata os ingredientes no liquidificador
- Coloque a massa formada na forma
- Leve a forma ao forno
- Espere o tempo indicado
- Desligue o forno
- Com uma luva, retire a forma com o bolo pronto
```

***Notam-se duas caracteristicas importantes dos algoritmos nesse exemplo.***
1. Existe uma sequência lógica na ordem das ações. <br>
    - Não se coloca a massa na forma sem antes pegar a forma
    - Não se coloca a forma no forno sem a massa
2. Algoritmos podem ser mais ou menos eficientes dependendo da lógica aplicada
    - Se você não ligar o forno enquanto prepara a massa, terá que esperar ele pré aquecer antes de levar a forma ao forno, o que acarretaria na perda de tempo de execução.

Vejamos um outro exemplo de algoritmo. <br>
**Problema: Pegar Onibus**
```
Ir até a parada
Enquanto (Onibus não chega) faça {
    esperar onibus
}
Subir no onibus
Se (Tem cartão de onibus) faça {
    Pegar cartão do onibus
    Passar o cartão na máquina
} 
Senão faça {
    Pegar dinheiro
    Pagar Passagem
    troco <-- dinheiro - passagem
    Guardar troco 
}
Passar pela Catraca
Enquanto (Não chegar no ponto) faça{
    Se (Existe lugar lazio) faça{
        Sentar no lugar vazio
        Esperar chegar no ponto
    }
    Senão {
        Esperar em pé até alguém sair ou até chegar no ponto
    }
}
Sair do onibus
```
***Notam-se mais algumas caracteristicas importantes dos algoritmos nesse exemplo.***
1. Um algoritmo pode realizar decisões
    - Se você não tem cartão de onibus, não podes passar na máquininha, então essa parte do código pode ser ignorada. Uma vez que você não tem esse cartão, terá que pagar com dinheiro.
    - Se não tem lugar no onibus, não tem como sentar, então vai ter que esperar alguém levantar.
2. Você pode repetir uma mesma tarefa de novo e de novo até que uma condição seja satisfeita. 
    - Enquanto o onibus não chega, você espera por ele
3. Você pode relacionar essas duas coisas a partir de uma lógica.
    - Enquanto você não chega no ponto, se tiver lugar disponível, sente e espere chegar no ponto. Se não tiver, fique em pé e espere alguém sair liberando um lugar, ou até chegar no ponto.
    - NOTA: O inverso, mesmo que não representado, também é possível. Podes realizar um loop, a partir de uma condição satisfeita ou não satisfeita.
4. É possível realizar operações matemáticas no código
    - Troco <- dinheiro - passagem
    - Nota: É possível realizar qualquer tipo de operação matemática no computador. Afinal, como dito antes, ele é uma calculadora com esteróides.
5. É possível salvar informações
    - A variavel troco recebeu o resultado da operação dinheiro - passagem. 
6. Nota-se uma grande quantidade de "{}" no código. Essa é uma notação comum em linguagens de programaçao para blocos de código. Que é basicamente uma forma explicita de separar seu código em partes. Nota-se que elas são usadas nas estruturas de repetição de ações e nas estruturas de condições. Ou seja, o que está dentro das chaves, está dentro da estrutura. 
7. Nota-se que o código que está dentro das chaves também possui um espaçamento a cada quebra de linha. Esse espaçamento é chamado identação, da mesma forma que as chaves, é um meio de organizar seu código, porém, as chaves são uma forma de organizar para que o computador consiga interpreta-lo, enquanto que a identação normalmente é feita para o desenvolvedor conseguir le-lo mais eficientemente.
8. Existe também no exemplo uma operação de comparação relacional. um "Ou".
    - Esperar em pé até alguém sair **ou** até chegar no ponto
    - Chamado de operador comparativo ou binário, ele compara duas afirmativas e se pelo menos uma delas for verdadeira, ele retorna uma resposta positiva. 



### 2.2 partes de um algoritmo
**De volta ao funcionamento do computador.**<br> 
No primeiro capitulo, é falado sobre como computadores são sistemas que recebem uma entrada de dados, realizam um processamento desses dados, e depois entregam uma saída dos dados processados. Porém, podem existir algoritmos que não recebem entrada mas entregam uma saída, podem existir algoritmos que recebem a entradamas não apresentam saída, e podem existir algoritmos que não recebem entrada nem apresentam uma saída. <br>
Por exemplo um algoritmo que realiza a soma 1 + 2. Ele não mostra que o resultado é 3, e esses números não foram inseridos por ninguém (Além do desenvolvedor que construiu o algoritmo). Portanto não existe entrada nem saída. Assim como Você pode inserir os valores da soma mas não receber saída com o resultado. Assim, como você pode receber o resultado da soma sem ter colocado os números.[^4]
[^4]: No texto do pdf é falado que é necessário no minimo as três etapas para um algoritmo. O que é uma interpretação válida se dissermos que os códigos escritos pelo desenvolvedor são um input, e todo e qualquer resultado, mesmo que não mostrado explicitamente, é um output. Mas no resumo, foi decidido declarar inputs e outputs explicitos como a entrada e a saída.


**Exemplo de algoritmo que recebe entrada, realiza processamento e entrega uma saída de dados**<br>
algoritmo para o calculo da área de um circulo recebendo seu raio. (A = pi * r²)

```
pi <- 3.14159...
r <- input do usuário
A <- pi * r * r
imprima(A)
```

**Notas Sobre o algoritmo exemplificado**
1. O raio é definido a partir da inserção do valor pelo usuário, se caracterizando assim como input(Entrada).
2. imprima() é um recurso que mostra ao usuário o resultado calculado
3. Esse é um algoritmo muito mais próximo do que veremos a frente, pois é composto por simples operações matemáticas e de entrada ou saída. Estando assim muito mais próximo do que um computador pode realizar naturalmente.Que na maior parte do tempo

### 2.5 Linguagens[^5]
[^5]: Falaremos sobre representações de algoritmos no módulo sobre Projeto de sistemas

### 2.5.2 Linguagem de máquina Assembler















































## Fontes
- "INTRODUÇÃO A ALGORITMOS E PROGRAMAÇÃO" de FABRICIO FERRARI e CRISTIAN CECHINEL
- cs50 - Harvard's Introduction to Computer Science Course