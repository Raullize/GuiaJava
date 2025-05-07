<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 🔢 Arrays Multidimensionais

## 🧩 Trabalhando com estruturas de dados complexas em Java

Arrays multidimensionais são estruturas que permitem organizar dados em múltiplas dimensões. Em Java, podemos pensar neles como "arrays de arrays", onde cada elemento é um array em si. Isso permite representar estruturas como matrizes, tabelas e dados com múltiplas dimensões.

### 📊 O que são Arrays Multidimensionais?

Um array multidimensional é uma maneira de armazenar dados em um formato tabular ou de múltiplas dimensões. Os tipos mais comuns são:

- **Arrays bidimensionais (2D)**: Representam dados em formato de tabela com linhas e colunas
- **Arrays tridimensionais (3D)**: Representam dados com profundidade, como um cubo
- **Arrays com mais dimensões**: Podem ter 4, 5 ou mais dimensões (menos comuns)

#### 🎯 Aplicações comuns:

- Representar matrizes matemáticas
- Armazenar dados tabulares (planilhas)
- Programação de jogos (mapas, tabuleiros)
- Processamento de imagens (pixels)
- Problemas científicos multidimensionais

### 📝 Declaração e Inicialização de Arrays Bidimensionais

#### 1️⃣ Declaração

```java
// Declaração (apenas a referência)
int[][] matriz;
String[][] tabuleiro;
```

#### 2️⃣ Alocação de memória

```java
// Criando um array 3x3 (3 linhas, 3 colunas)
matriz = new int[3][3];

// Criando um array 8x8 (como um tabuleiro de xadrez)
tabuleiro = new String[8][8];
```

#### 3️⃣ Declaração e alocação combinadas

```java
double[][] notas = new double[5][4]; // 5 alunos, 4 bimestres
boolean[][] mapa = new boolean[10][10]; // Mapa 10x10 (true = ocupado, false = livre)
```

#### 4️⃣ Inicialização com valores

```java
// Matriz 3x3 com valores definidos
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Tabuleiro de jogo da velha
char[][] jogoVelha = {
    {'X', 'O', 'X'},
    {'O', 'X', 'O'},
    {'O', 'X', 'O'}
};
```

### 🔄 Acessando e Modificando Elementos

Para acessar ou modificar um elemento, precisamos especificar dois índices: linha e coluna.

```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Acessando elementos
int valor = matriz[1][2]; // Pega o elemento da linha 1, coluna 2: valor = 6

// Modificando elementos
matriz[0][0] = 10; // Define o elemento da primeira linha, primeira coluna como 10
matriz[2][1] = 15; // Define o elemento da terceira linha, segunda coluna como 15
```

### 📏 Dimensões de um Array Multidimensional

Em Java, podemos obter o número de linhas e colunas usando o atributo `length`:

```java
int[][] matriz = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};

int numLinhas = matriz.length; // 3 (número de linhas)
int numColunas = matriz[0].length; // 4 (número de colunas na primeira linha)

System.out.println("Dimensões: " + numLinhas + "x" + numColunas);
```

### ♻️ Percorrendo Arrays Bidimensionais

#### 1️⃣ Usando loops `for` aninhados

```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Percorrendo todos os elementos
for (int i = 0; i < matriz.length; i++) {
    for (int j = 0; j < matriz[i].length; j++) {
        System.out.print(matriz[i][j] + " ");
    }
    System.out.println(); // Nova linha após cada linha da matriz
}
```

#### 2️⃣ Usando loops `for-each` aninhados

```java
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Percorrendo com for-each
for (int[] linha : matriz) {
    for (int valor : linha) {
        System.out.print(valor + " ");
    }
    System.out.println();
}
```

### 🧮 Arrays Irregulares (Jagged Arrays)

Em Java, as linhas de um array bidimensional podem ter comprimentos diferentes:

```java
// Array irregular onde cada linha tem um comprimento diferente
int[][] arrayIrregular = {
    {1, 2, 3},
    {4, 5},
    {6, 7, 8, 9},
    {10}
};

// Percorrendo um array irregular
for (int i = 0; i < arrayIrregular.length; i++) {
    for (int j = 0; j < arrayIrregular[i].length; j++) {
        System.out.print(arrayIrregular[i][j] + " ");
    }
    System.out.println();
}
```

#### 🔍 Criando arrays irregulares explicitamente

```java
// Declaração do array com apenas o primeiro dimensionamento
int[][] arrayIrregular = new int[4][];

// Definindo cada linha com tamanhos diferentes
arrayIrregular[0] = new int[3]; // Primeira linha com 3 colunas
arrayIrregular[1] = new int[2]; // Segunda linha com 2 colunas
arrayIrregular[2] = new int[5]; // Terceira linha com 5 colunas
arrayIrregular[3] = new int[1]; // Quarta linha com 1 coluna
```

### 🧮 Arrays Tridimensionais (3D)

Um array tridimensional pode ser visto como um array de arrays bidimensionais:

```java
// Declaração e inicialização de um array 3D
int[][][] array3D = {
    // Primeiro bloco 2x2
    {
        {1, 2},
        {3, 4}
    },
    // Segundo bloco 2x2
    {
        {5, 6},
        {7, 8}
    }
};

// Acessando elementos
int valor = array3D[1][0][1]; // Valor é 6 (bloco 1, linha 0, coluna 1)

// Percorrendo um array 3D
for (int i = 0; i < array3D.length; i++) {
    for (int j = 0; j < array3D[i].length; j++) {
        for (int k = 0; k < array3D[i][j].length; k++) {
            System.out.println("array3D[" + i + "][" + j + "][" + k + "] = " + array3D[i][j][k]);
        }
    }
}
```

### 🛠️ Operações com a Classe Arrays

A classe `java.util.Arrays` também pode ser utilizada com arrays multidimensionais:

```java
import java.util.Arrays;

public class ExemploArraysMultidimensionais {
    public static void main(String[] args) {
        int[][] matriz = {
            {5, 2, 9},
            {1, 3, 8},
            {7, 4, 6}
        };
        
        // Convertendo para String (só funciona para uma dimensão por vez)
        System.out.println("Primeira linha: " + Arrays.toString(matriz[0]));
        
        // Para exibir o array completo
        for (int[] linha : matriz) {
            System.out.println(Arrays.toString(linha));
        }
        
        // Alternativa usando deepToString (funciona para qualquer dimensão)
        System.out.println("Matriz completa: " + Arrays.deepToString(matriz));
        
        // Preenchendo uma linha
        Arrays.fill(matriz[0], 0); // Preenche a primeira linha com zeros
        
        // Comparando arrays bidimensionais
        int[][] matriz2 = {
            {0, 0, 0},
            {1, 3, 8},
            {7, 4, 6}
        };
        
        boolean iguais = Arrays.deepEquals(matriz, matriz2);
        System.out.println("As matrizes são iguais? " + iguais);
    }
}
```

### 🔨 Exemplos Práticos com Arrays Multidimensionais

#### 1. Soma de Matrizes

```java
public class SomaMatrizes {
    public static void main(String[] args) {
        int[][] matrizA = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        int[][] matrizB = {
            {9, 8, 7},
            {6, 5, 4},
            {3, 2, 1}
        };
        
        // As matrizes precisam ter as mesmas dimensões
        if (matrizA.length != matrizB.length || matrizA[0].length != matrizB[0].length) {
            System.out.println("Não é possível somar matrizes de dimensões diferentes");
            return;
        }
        
        int linhas = matrizA.length;
        int colunas = matrizA[0].length;
        
        int[][] resultado = new int[linhas][colunas];
        
        // Somando as matrizes
        for (int i = 0; i < linhas; i++) {
            for (int j = 0; j < colunas; j++) {
                resultado[i][j] = matrizA[i][j] + matrizB[i][j];
            }
        }
        
        // Exibindo o resultado
        System.out.println("Resultado da soma:");
        for (int[] linha : resultado) {
            System.out.println(Arrays.toString(linha));
        }
    }
}
```

#### 2. Tabuleiro de Xadrez

```java
public class TabuleiroXadrez {
    public static void main(String[] args) {
        char[][] tabuleiro = new char[8][8];
        
        // Preenchendo o tabuleiro
        for (int i = 0; i < 8; i++) {
            for (int j = 0; j < 8; j++) {
                // Se a soma dos índices for par, é uma casa branca
                if ((i + j) % 2 == 0) {
                    tabuleiro[i][j] = '□'; // Casa branca
                } else {
                    tabuleiro[i][j] = '■'; // Casa preta
                }
            }
        }
        
        // Exibindo o tabuleiro
        for (int i = 0; i < 8; i++) {
            for (int j = 0; j < 8; j++) {
                System.out.print(tabuleiro[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

#### 3. Calculando Determinante de Matriz 2x2

```java
public class DeterminanteMatriz {
    public static void main(String[] args) {
        int[][] matriz = {
            {5, 2},
            {3, 4}
        };
        
        // Determinante de matriz 2x2: ad - bc
        int determinante = matriz[0][0] * matriz[1][1] - matriz[0][1] * matriz[1][0];
        
        System.out.println("Matriz:");
        for (int[] linha : matriz) {
            System.out.println(Arrays.toString(linha));
        }
        System.out.println("Determinante: " + determinante);
    }
}
```

### 🧠 Considerações sobre Desempenho

1. **Acesso sequencial**: Acessar elementos em ordem de como estão armazenados na memória (linha por linha) é mais eficiente
2. **Consumo de memória**: Arrays multidimensionais podem consumir muita memória, especialmente com muitas dimensões
3. **Localidade de cache**: Percorrer os elementos na ordem correta melhora o desempenho devido à cache locality

### 💡 Dicas e Boas Práticas

1. **Validação de índices**: Sempre verifique se os índices estão dentro dos limites antes de acessar elementos
2. **Documentação**: Documente claramente o significado de cada dimensão do array
3. **Convenções de uso**: 
   - Use `i`, `j`, `k` para índices em loops aninhados
   - Primeiro índice geralmente representa linhas, segundo representa colunas
4. **Arrays jagged vs. retangulares**: Use arrays jagged apenas quando necessário, arrays retangulares são mais fáceis de trabalhar
5. **Alternativas**: Para operações complexas de matriz, considere usar bibliotecas como Apache Commons Math ou EJML

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 