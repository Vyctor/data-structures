# Notação Big O

A notação assintótica Big O, em Ciência da Computação é usada para classificar algoritmos em relação as mudanças de desempenho quanto ao tamanho da entrada. É um método de descrever o comportamento de limites, matematicamente falando.
O conceito basicamente define uma forma de descrever como o tempo que demora para executar sua função cresce de acordo com o aumento da entrada de dados.

Conhecimento de notação Big O te dá a habilidade de escrever um código melhor, legível e escalável.

## Big O, Big Theta e Big Omega

A execução de um algoritmo possui três cenários diferentes

- Melhor caso - Big Omega
- Caso médio - Big Theta
- Pior caso - Big O

## Tipos de complexidade

- O(1) - Constante
  - É aquela que não há crescimento do número de operações, pois não depende do volume de dados de entrada.
    - Exemplo: o acesso direto a um elemento de uma matriz.
- O(n log n) - Logaritmo
  - é aquela em que o crescimento do número de operações é menor que o número de itens
    - Exemplo: Caso médio da busca em árvores binárias ordenadas
- O(n) - Linear
  - é aquela em que o crescimento no número de operações é menor que o número de itens.
    - Exemplo: algoritmo de busca em uma lista/vetor
- O(n log n) - Linearitmica ou quasilinear
  - é aquela em que o resultado das operações (log n) executada n vezes
    - Exemplo: caso médio do Quicksort
- O(n^2) - Quadrático
  - é aquela que ocorre quando os itens de dados são processados aos pares, muitas vezes com repetições dentro da outra. Com dados suficientemente grandes tendem a se tornar muito ruim.
    - Exemplo: o processamento de itens de uma matriz bidirecional
- O(2^n) - Exponencial
  - a medida que a entrada aumenta o fator (tempo ou espaço) aumenta exponencialmente.
  - não é executável para valores muito grandes e não são úteis do ponto de vista prático.
    - Exemplo: busca em árvore binária não ordenada
- O(n!) - Fatorial
  - é aquela em que o número de instruções executadas cresce muito rapidamente para um pequeno número de dados
    - Exemplo: um algoritmo que gere todos os possíveis permutações de uma lista

## Complexidade espacial

Complexidade espacial é a medida da quantidade de armazenamento necessário para a execução de determinado um algoritmo.

## Remova constantes e termos não dominantes

Isso significa que podemos facilmente eliminar alguns valores da análise assintótica.
Assim podemos reduzir O(2n) para O(n), O(n^2+n) para O(n^2).

- Porque removemos constantes e termos não dominantes?

  - é muito possível que O(n) seja mais rápido que O(1) para inputs específicos
  - computadores diferentes, com diferentes arquiteturas, possuem fatores diferentes
  - algoritmos diferentes com a mesma ideia básica e complexidade computacional podem possuir constantes ligeiramente diferentes.

## Adição vs Multiplicação

Se seu algoritmo é da escrito da forma "faça isso, então quando estiver pronto faça aquilo", então você soma os tempos de execução.
Caso seu algoritmo seja da forma "faça isso cada vez que fizer aquilo", então você multiplica os tempos de execução.

## Como estimar o Big O

- Regra 1
  - Qualquer declaração de atribuição e condicional que é executada. O(1)
- Regra 2
  - Um loop simples de 0 a N (sem loops internos). O(n)
- Regra 3
  - Um loop aninhado do mesmo tipo (mesmo dataset). O(n^2)
- Regra 4
  - Um loop, o qual a variável de controle é dividida por dois a cada execução. O(log n)
- Regra 5
  - Quando estiver lidando com múltiplas variáveis, some-as.

### Big O

- O(1)
  - Constante
  - Sem loop
- O(log N)
  - geralmente algoritmos de busca em dataset ordenado.
- O(n)
  - Linear
  - laços for, while
- O(n log(n))
  - geralmente operações de ordenamento
- O(n^2)
  - cada elemento em uma coleção necessita ser comparado a todos outros elementos. Dois loops aninhados.
- O(2^n)
  - algoritmos recursivos que resolvem problemas de tamanho N
- O(n!)
  - iterando para cada elemento

**Iterar somente meia coleção continua sendo O(n)**
**Duas coleções separadas: O(a \* b)**

### O que causa aumento de tempo em uma função?

- Operação
  - +, -, \*, /
- Comparação
  - <, >, ==
- Laços
  - for, while
- Chamadas de funções externas
  - function()

### Livro de regras

- Regra 1:
  - Sempre pior caso
- Regra 2:
  - Remova as constantes
- Regra 3:
  - Inputs diferentes devem ser atribuídos a variáveis diferentes. Array A e B aninhados devem ser O(a\*b)
- Regra 4:
  - Remova termos não dominantes

## O que causa complexidade espacial

- Variáveis
- Estruturas de dados
- Chamadas de funções
- Alocações

[Big O Cheat sheet](https://www.bigocheatsheet.com/)

## Questões

1. Qual o tempo de execução do código abaixo?

```python
def foo(array):
  sum = 0 # O(1)
  product = 1 # O(1)
  for i in array: # O(n)
    sum += i # O(1)
  for i in array: # O(n)
    product *= i # O(1)
  for i in array: # O(n)
    product *= i # O(1)

  print("Sum = "+str(sum)", Product = ",+str(product))
```

**Resposta: O(n)**

2. Qual o tempo de execução do código abaixo?

```python
def printPairs(array):
  for i in array: # O(n^2)
    for j in array: # O(n)
      print(str(i) + ","+str(j)) # O(1)
```

**Resposta: O(n^2)**

3. Qual o tempo de execução do código abaixo?

```python
def UnorderedPairs(array):
  for i in range(0, len(array)):
    for j in range(i+1, len(array)):
      print(array[i] + "," + array[j])
```

**Resposta: O(n^2)**

4. Qual o tempo de execução do código abaixo?

```python
def printUnorderedPairs(arrayA, arrayB):
  for i in range(len(arrayA)):
    for j in range(arrayB):
      if(arrayA[i] < arrayB[j]):
        print(str(arrayA[i]) + "," + str(arrayB[i]))
```

**Resposta: O(n)**

5. Qual o tempo de execução do código abaixo?

```python
def printUnorderedPairs(arrayA, arrayB):
  for i in range(len(arrayA)): O(n)
    for j in range(arrayB): O(n)
      for k in range(0, 100000): O(100000)
        print(str(arrayA[i]) + "," + str(arrayB[j]))
```

**Resposta: O(ab)**

6. Qual o tempo de execução do código abaixo?

```python
def reverse(array):
  for i in range(0, int(len(array)/2)):
    other = len(array) - i - 1
    temp = array[i]
    array[i] = array[other]
    array[other] = temp
  print(array)
```

**Resposta: O(n)**

7. Qual das seguintes opções são equivalentes a O(n)? Porque?

- O(N+P), onde P < N/2 => O(n), remover P pois é termo não dominante
- O(2n) => Remover constante 2, logo O(n)
- O(n + logN) => O(n) pois log n é não dominante
- O(n log n) => O(n log n) pois n log n é termo dominante
- O(n + m) => não é equivalente a O(n)

8. Qual o tempo de execução do código abaixo?

```python
def factorial(n): M(n)
  if n < 0:
    return -1 O(1)
  elif n == 0:
    return 1 O(1)
  else:
    return n * factorial(n-1) M(n-1)
```

M(n) = O(1) + M((n-1) -1)
M(n) = O(1) + M((n-2) -1)
M(n) = 1 + M(n-1)
M(n) = 1 + (1 + M((n-1)-1))
M(n) = 2 + M(n-2)
M(n) = 2 + 1 + M((n-2) - 1)
M(n) = 3 + M(n-3)
M(n) = a + M(n-a)
M(n) = n + M(n-n)
M(n) = n + 1
M(n) = n

**Resposta: O(n)**

9. Qual o tempo de execução do código abaixo?

```python
def allFib(n):
  for i in range(n):
    print(str(i)+":, " + str(fib(i)))

def fib(n):
  if n <= 0:
    return 0 # O(1)
  elif n == 1
    return 1 # O(1)
  return fib(n-1) + fib(n-2) # O(2^n)
```

**Resposta: O(2^n)**

10. Qual o tempo de execução do código abaixo?

```python
def powersOf2(n):
  if n < 1:
    return 0
  elif n == 1:
    print(1)
    return 1
  else:
    prev = powerOf2(int(n/2)) # O(log N)
    curr = prev * 2
    print(curr)
    return cur
```

**Resposta: O(log N)**
