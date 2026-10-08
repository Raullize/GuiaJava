<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Estruturas de Repetição

## Mecanismos para executar código repetidamente em Java

As estruturas de repetição (ou loops) são recursos fundamentais em programação que permitem executar um bloco de código várias vezes. Java oferece diversas formas de implementar repetições, cada uma com suas características e casos de uso ideais.

### Loop `for`

O loop `for` é ideal quando sabemos exatamente quantas vezes queremos executar um bloco de código.

#### Sintaxe:

```java
for (inicialização; condição; incremento/decremento) {
    // Bloco de código a ser repetido
}
```

- **Inicialização**: Executada apenas uma vez, antes do loop começar
- **Condição**: Verificada antes de cada iteração; o loop continua enquanto for verdadeira
- **Incremento/Decremento**: Executado após cada iteração

#### Exemplos:

```java
// Loop básico de 0 a 9
for (int i = 0; i < 10; i++) {
    System.out.println("Valor de i: " + i);
}

// Loop decrescente
for (int i = 10; i > 0; i--) {
    System.out.println("Contagem regressiva: " + i);
}

// Incrementando em valores diferentes de 1
for (int i = 0; i <= 20; i += 2) {
    System.out.println("Número par: " + i);
}
```

#### Loop `for` com múltiplas variáveis:

```java
// Usando múltiplas variáveis no loop for
for (int i = 0, j = 10; i < j; i++, j--) {
    System.out.println("i = " + i + ", j = " + j);
}
```

### Loop `for-each` (Enhanced for)

O loop `for-each` é uma versão simplificada do `for` tradicional, útil para percorrer elementos em coleções e arrays sem a necessidade de gerenciar índices.

#### Sintaxe:

```java
for (tipo elemento : coleção) {
    // Código para processar o elemento
}
```

#### Exemplos:

```java
// Percorrendo um array com for-each
int[] numeros = {1, 2, 3, 4, 5};
for (int numero : numeros) {
    System.out.println("Número: " + numero);
}

// Percorrendo uma coleção
ArrayList<String> frutas = new ArrayList<>();
frutas.add("Maçã");
frutas.add("Banana");
frutas.add("Laranja");

for (String fruta : frutas) {
    System.out.println("Fruta: " + fruta);
}
```

⚠️ **Limitações do `for-each`**:
- Não permite modificar o tamanho da coleção durante a iteração
- Não fornece acesso ao índice do elemento atual
- Não permite percorrer a coleção em ordem inversa
- Não permite percorrer múltiplas coleções simultaneamente

### Loop `while`

O loop `while` executa um bloco de código enquanto uma condição específica for verdadeira.

#### Sintaxe:

```java
while (condição) {
    // Bloco de código a ser repetido
}
```

#### Exemplos:

```java
// Loop simples
int contador = 0;
while (contador < 5) {
    System.out.println("Contador: " + contador);
    contador++;
}

// Loop com condição mais complexa
Scanner scanner = new Scanner(System.in);
String entrada = "";
while (!entrada.equalsIgnoreCase("sair")) {
    System.out.print("Digite algo (ou 'sair' para encerrar): ");
    entrada = scanner.nextLine();
    System.out.println("Você digitou: " + entrada);
}
scanner.close();
```

### Loop `do-while`

O loop `do-while` é semelhante ao `while`, mas garante que o bloco de código será executado pelo menos uma vez, pois a condição é verificada após a primeira execução.

#### Sintaxe:

```java
do {
    // Bloco de código a ser repetido
} while (condição);
```

#### Exemplos:

```java
// Exemplo básico
int contador = 0;
do {
    System.out.println("Contador: " + contador);
    contador++;
} while (contador < 5);

// Validação de entrada
Scanner scanner = new Scanner(System.in);
int numero;
do {
    System.out.print("Digite um número positivo: ");
    numero = scanner.nextInt();
} while (numero <= 0);

System.out.println("Você digitou: " + numero);
scanner.close();
```

### Comparação entre as Estruturas de Repetição

| Estrutura | Quando usar | Execução garantida | Verificação da condição |
|-----------|-------------|-------------------|------------------------|
| `for`     | Quando se sabe o número de iterações | Não | Antes de cada iteração |
| `for-each`| Para percorrer coleções/arrays | Não | Implícita (termina quando acabam os elementos) |
| `while`   | Quando não se sabe o número de iterações | Não | Antes de cada iteração |
| `do-while`| Quando o bloco deve ser executado pelo menos uma vez | Sim, pelo menos uma vez | Após cada iteração |

### Controle de Fluxo em Loops

Java oferece instruções para controle adicional dentro dos loops:

#### `break`

A instrução `break` termina imediatamente o loop, independentemente da condição.

```java
// Encontrar o primeiro número divisível por 5 entre 1 e 100
for (int i = 1; i <= 100; i++) {
    if (i % 5 == 0) {
        System.out.println("Primeiro número divisível por 5: " + i);
        break;  // Sai do loop após encontrar o primeiro
    }
}

// Encerrar um loop while com break
int contador = 0;
while (true) {  // Loop infinito
    System.out.println("Contador: " + contador);
    contador++;
    if (contador >= 5) {
        break;  // Sai do loop quando contador chega a 5
    }
}
```

#### `continue`

A instrução `continue` pula para a próxima iteração do loop, ignorando o código restante na iteração atual.

```java
// Imprimir apenas números ímpares
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue;  // Pula para a próxima iteração se o número for par
    }
    System.out.println("Número ímpar: " + i);
}

// Pular processamento de strings vazias
String[] palavras = {"Java", "", "Programação", "", "Loop"};
for (String palavra : palavras) {
    if (palavra.isEmpty()) {
        continue;  // Pula strings vazias
    }
    System.out.println("Palavra: " + palavra);
}
```

### Loops Aninhados

Loops podem ser aninhados, ou seja, um loop dentro de outro, permitindo iterações mais complexas.

```java
// Tabela de multiplicação
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= 5; j++) {
        System.out.print(i * j + "\t");
    }
    System.out.println();  // Nova linha após cada linha da tabela
}

// Percorrendo uma matriz
int[][] matriz = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

for (int i = 0; i < matriz.length; i++) {
    for (int j = 0; j < matriz[i].length; j++) {
        System.out.print(matriz[i][j] + " ");
    }
    System.out.println();
}
```

### Loops em Coleções

Java oferece várias formas de percorrer coleções:

#### 1 Usando Iterator

```java
import java.util.ArrayList;
import java.util.Iterator;

public class ExemploIterator {
    public static void main(String[] args) {
        ArrayList<String> nomes = new ArrayList<>();
        nomes.add("Ana");
        nomes.add("Bruno");
        nomes.add("Carlos");
        
        // Usando Iterator
        Iterator<String> iterator = nomes.iterator();
        while (iterator.hasNext()) {
            String nome = iterator.next();
            System.out.println(nome);
            
            // Podemos remover elementos durante a iteração
            if (nome.equals("Bruno")) {
                iterator.remove();
            }
        }
    }
}
```

#### 2 Usando Streams (Java 8+)

```java
import java.util.ArrayList;
import java.util.List;

public class ExemploStream {
    public static void main(String[] args) {
        List<String> nomes = new ArrayList<>();
        nomes.add("Ana");
        nomes.add("Bruno");
        nomes.add("Carlos");
        
        // Usando stream para processar a coleção
        nomes.stream()
             .filter(nome -> nome.startsWith("A"))
             .map(String::toUpperCase)
             .forEach(System.out::println);
    }
}
```

### ⚠️ Erros Comuns e Boas Práticas

#### 1. Loop Infinito

Um erro comum é criar loops infinitos que nunca terminam:

```java
// Loop infinito - EVITE isso!
for (int i = 0; i < 10; i--) {  // Decrementa em vez de incrementar
    System.out.println("Cuidado: Loop infinito!");
}

// Loop infinito com while
while (true) {
    // Deve haver alguma condição de saída com break
    if (condicaoDeSaida) {
        break;
    }
}
```

#### 2. Off-by-one Error

Erro de "fora por um", quando o loop executa uma vez a mais ou a menos do que o esperado:

```java
// Erro: percorre de 0 a 10 (11 elementos)
for (int i = 0; i <= 10; i++) {
    System.out.println(i);
}

// Corrigido: percorre de 0 a 9 (10 elementos)
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

#### 3. Performance em Loops

Otimizações para melhor desempenho:

```java
// Menos eficiente: calculando length a cada iteração
for (int i = 0; i < array.length; i++) {
    // processamento
}

// Mais eficiente: calculando length apenas uma vez
int tamanho = array.length;
for (int i = 0; i < tamanho; i++) {
    // processamento
}
```

### Exemplos Práticos

#### 1 Cálculo de Fatorial

```java
public class Fatorial {
    public static void main(String[] args) {
        int numero = 5;
        int fatorial = 1;
        
        for (int i = 1; i <= numero; i++) {
            fatorial *= i;
        }
        
        System.out.println("Fatorial de " + numero + " é " + fatorial);
    }
}
```

#### 2 Sequência de Fibonacci

```java
public class Fibonacci {
    public static void main(String[] args) {
        int n = 10; // Número de termos
        int primeiro = 0, segundo = 1;
        
        System.out.print("Sequência de Fibonacci com " + n + " termos: ");
        
        for (int i = 1; i <= n; i++) {
            System.out.print(primeiro + " ");
            
            int proximo = primeiro + segundo;
            primeiro = segundo;
            segundo = proximo;
        }
    }
}
```

#### 3 Verificação de Número Primo

```java
public class VerificacaoPrimo {
    public static void main(String[] args) {
        int numero = 17;
        boolean ehPrimo = true;
        
        if (numero <= 1) {
            ehPrimo = false;
        } else {
            for (int i = 2; i <= Math.sqrt(numero); i++) {
                if (numero % i == 0) {
                    ehPrimo = false;
                    break;
                }
            }
        }
        
        if (ehPrimo) {
            System.out.println(numero + " é um número primo");
        } else {
            System.out.println(numero + " não é um número primo");
        }
    }
}
```

### Dicas para Escolher a Estrutura Correta

1. Use `for` quando souber o número de iterações antecipadamente
2. Use `for-each` para percorrer coleções ou arrays de forma simples
3. Use `while` quando não souber o número de iterações antecipadamente
4. Use `do-while` quando precisar garantir que o bloco seja executado pelo menos uma vez
5. Prefira `break` e `continue` a condições complexas dentro de loops
6. Use loops aninhados com cautela, pois podem afetar a performance

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>