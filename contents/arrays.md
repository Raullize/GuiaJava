<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Arrays

## Estruturas de dados fundamentais em Java

Arrays são estruturas de dados que permitem armazenar múltiplos valores do mesmo tipo em uma única variável. Em Java, os arrays são objetos que contêm elementos do mesmo tipo, organizados em sequência e acessados por índice.

### Características dos Arrays em Java

- Tamanho fixo (definido na criação)
- Índices começam em 0
- Armazenam elementos do mesmo tipo
- Possuem um atributo `length` que indica seu tamanho
- São objetos em Java, mesmo para tipos primitivos

### Declaração e Inicialização de Arrays

Existem várias formas de declarar e inicializar um array em Java:

#### 1 Declaração simples

```java
// Declaração (apenas cria a referência, não o array)
int[] numeros;
String[] nomes;
```

#### 2 Alocação de memória

```java
// Alocação de memória sem inicializar valores
numeros = new int[5]; // Cria um array com 5 elementos (valores padrão: 0)
nomes = new String[3]; // Cria um array com 3 elementos (valores padrão: null)
```

#### 3 Declaração e alocação em uma única linha

```java
int[] contador = new int[10];
double[] precos = new double[100];
char[] letras = new char[26];
```

#### 4 Inicialização com valores

```java
// Inicialização com valores específicos
int[] idades = {25, 32, 45, 18, 60};
String[] frutas = {"Maçã", "Banana", "Laranja"};
char[] vogais = {'a', 'e', 'i', 'o', 'u'};
```

#### 5 Declaração, alocação e inicialização explícita

```java
float[] alturas = new float[] {1.75f, 1.80f, 1.65f, 1.90f};
boolean[] status = new boolean[] {true, false, true};
```

> ⚠️ **Observação**: Em Java, os colchetes `[]` podem ser colocados tanto após o tipo quanto após o nome da variável. Ambas as formas são válidas, mas a primeira é preferida:
> ```java
> int[] numeros; // Forma recomendada
> int numeros[]; // Forma alternativa (estilo C)
> ```

### Acessando e Modificando Elementos

Os elementos de um array são acessados através de seus índices:

```java
int[] numeros = {10, 20, 30, 40, 50};

// Acessando elementos
int primeiro = numeros[0]; // 10
int terceiro = numeros[2]; // 30

// Modificando elementos
numeros[1] = 25; // Altera o segundo elemento para 25
numeros[4] = 100; // Altera o quinto elemento para 100
```

### Atributo `length`

Todo array em Java possui um atributo `length` que retorna o seu tamanho:

```java
int[] numeros = {10, 20, 30, 40, 50};
int tamanho = numeros.length; // 5

// Usando length em um loop
for (int i = 0; i < numeros.length; i++) {
    System.out.println("Elemento " + i + ": " + numeros[i]);
}
```

### Percorrendo Arrays

Existem diversas formas de percorrer um array em Java:

#### 1 Loop `for` tradicional

```java
int[] numeros = {10, 20, 30, 40, 50};

for (int i = 0; i < numeros.length; i++) {
    System.out.println(numeros[i]);
}
```

#### 2 Loop `for-each` (Enhanced for)

```java
int[] numeros = {10, 20, 30, 40, 50};

for (int numero : numeros) {
    System.out.println(numero);
}
```

#### 3 Usando `java.util.Arrays`

```java
int[] numeros = {10, 20, 30, 40, 50};

// Imprime o array inteiro
System.out.println(Arrays.toString(numeros));
```

### Métodos Úteis da Classe Arrays

A classe `java.util.Arrays` oferece vários métodos úteis para trabalhar com arrays:

```java
import java.util.Arrays;

public class ExemploArrays {
    public static void main(String[] args) {
        int[] numeros = {5, 2, 9, 1, 7, 3};
        
        // Ordenação
        Arrays.sort(numeros);
        System.out.println("Array ordenado: " + Arrays.toString(numeros));
        // Saída: Array ordenado: [1, 2, 3, 5, 7, 9]
        
        // Busca binária (apenas em arrays ordenados)
        int indice = Arrays.binarySearch(numeros, 5);
        System.out.println("Índice do elemento 5: " + indice);
        
        // Preenchimento
        int[] zeros = new int[5];
        Arrays.fill(zeros, 0);
        System.out.println("Array preenchido: " + Arrays.toString(zeros));
        // Saída: Array preenchido: [0, 0, 0, 0, 0]
        
        // Comparação
        int[] array1 = {1, 2, 3};
        int[] array2 = {1, 2, 3};
        boolean saoIguais = Arrays.equals(array1, array2);
        System.out.println("Arrays são iguais: " + saoIguais); // true
        
        // Cópia
        int[] copia = Arrays.copyOf(numeros, numeros.length);
        System.out.println("Cópia: " + Arrays.toString(copia));
        
        // Cópia parcial
        int[] copiaParcial = Arrays.copyOfRange(numeros, 1, 4);
        System.out.println("Cópia parcial: " + Arrays.toString(copiaParcial));
        // Saída: Cópia parcial: [2, 3, 5]
    }
}
```

### Arrays de Tipos Primitivos vs. Arrays de Objetos

Em Java, há diferenças importantes entre arrays de tipos primitivos e arrays de objetos:

#### Arrays de Tipos Primitivos

```java
int[] numeros = new int[5]; // Todos os elementos são inicializados com 0
```

**Valores padrão:**
- `int`, `short`, `byte`, `long`: 0
- `float`, `double`: 0.0
- `char`: '\u0000' (caractere nulo)
- `boolean`: false

#### Arrays de Objetos

```java
String[] nomes = new String[3]; // Todos os elementos são inicializados com null
```

**Observações:**
- Arrays de objetos armazenam referências, não os próprios objetos
- O valor padrão para objetos é `null`
- É necessário inicializar cada elemento individualmente

```java
Pessoa[] pessoas = new Pessoa[3];

// Inicialização manual de cada elemento
pessoas[0] = new Pessoa("João", 25);
pessoas[1] = new Pessoa("Maria", 30);
pessoas[2] = new Pessoa("Carlos", 22);
```

### Arrays de Strings

Arrays de strings são muito comuns em programação Java:

```java
String[] dias = {"Segunda", "Terça", "Quarta", "Quinta", "Sexta", "Sábado", "Domingo"};

// Percorrendo e imprimindo
for (String dia : dias) {
    System.out.println(dia);
}

// Ordenando strings (ordem alfabética)
Arrays.sort(dias);
```

### Convertendo Arrays em String

Existem várias formas de converter um array em uma representação de String:

```java
int[] numeros = {1, 2, 3, 4, 5};

// Método 1: Arrays.toString()
String str1 = Arrays.toString(numeros);
System.out.println(str1); // [1, 2, 3, 4, 5]

// Método 2: String.join() (para arrays de String)
String[] nomes = {"Ana", "Bruno", "Carlos"};
String str2 = String.join(", ", nomes);
System.out.println(str2); // Ana, Bruno, Carlos

// Método 3: StringBuilder (para qualquer tipo de array)
StringBuilder sb = new StringBuilder();
for (int i = 0; i < numeros.length; i++) {
    sb.append(numeros[i]);
    if (i < numeros.length - 1) {
        sb.append(", ");
    }
}
String str3 = sb.toString();
System.out.println(str3); // 1, 2, 3, 4, 5
```

### ⚠️ Exceções Comuns ao Trabalhar com Arrays

#### 1. ArrayIndexOutOfBoundsException

Ocorre quando tentamos acessar um índice que não existe no array:

```java
int[] numeros = {1, 2, 3};
int valor = numeros[3]; // Erro! O índice máximo é 2
```

#### 2. NullPointerException

Ocorre quando tentamos acessar ou manipular um array que é null:

```java
int[] numeros = null;
int tamanho = numeros.length; // Erro! numeros é null
```

### Exemplo Prático: Calculando Estatísticas

```java
public class EstatiticasArray {
    public static void main(String[] args) {
        int[] notas = {85, 90, 75, 68, 92, 83, 77, 94};
        
        // Calculando a média
        int soma = 0;
        for (int nota : notas) {
            soma += nota;
        }
        double media = (double) soma / notas.length;
        
        // Encontrando a maior e menor nota
        int maior = notas[0];
        int menor = notas[0];
        
        for (int i = 1; i < notas.length; i++) {
            if (notas[i] > maior) {
                maior = notas[i];
            }
            if (notas[i] < menor) {
                menor = notas[i];
            }
        }
        
        // Calculando o desvio padrão
        double somaDiferencasQuadrado = 0;
        for (int nota : notas) {
            double diferenca = nota - media;
            somaDiferencasQuadrado += diferenca * diferenca;
        }
        double desvioPadrao = Math.sqrt(somaDiferencasQuadrado / notas.length);
        
        // Exibindo resultados
        System.out.println("Notas: " + Arrays.toString(notas));
        System.out.println("Média: " + media);
        System.out.println("Maior nota: " + maior);
        System.out.println("Menor nota: " + menor);
        System.out.println("Desvio Padrão: " + desvioPadrao);
    }
}
```

### Dicas e Boas Práticas

1. **Verificação de limites**: Sempre verifique se o índice está dentro dos limites do array
2. **Arrays vazios vs. null**: Prefira arrays vazios (`new int[0]`) a arrays null
3. **Imutabilidade**: Quando possível, considere tratar arrays como imutáveis
4. **Usar coleções**: Para tamanhos dinâmicos, considere usar `ArrayList` ou outras coleções
5. **Documentação**: Documente o propósito e o formato esperado de arrays em métodos
6. **Validação**: Sempre valide arrays recebidos como parâmetros

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>