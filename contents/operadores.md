<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# ➗ Operadores

## Manipulando dados com expressões em Java

Os operadores são símbolos especiais que realizam operações específicas em um, dois ou três operandos e retornam um resultado. Java possui uma rica variedade de operadores que permitem realizar desde cálculos matemáticos simples até operações lógicas complexas.

### Tipos de Operadores em Java

Java agrupa seus operadores nas seguintes categorias:

1. Operadores Aritméticos
2. Operadores de Atribuição
3. Operadores de Comparação (Relacionais)
4. Operadores Lógicos
5. Operadores Bit a Bit (Bitwise)
6. Operadores Unários
7. Operador Ternário
8. Operador instanceof

### ➕ Operadores Aritméticos

Usados para realizar operações matemáticas básicas:

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `+` | Adição | `int soma = 5 + 3;` // 8 |
| `-` | Subtração | `int diferenca = 5 - 3;` // 2 |
| `*` | Multiplicação | `int produto = 5 * 3;` // 15 |
| `/` | Divisão | `int quociente = 10 / 2;` // 5 |
| `%` | Módulo (resto) | `int resto = 10 % 3;` // 1 |

#### Exemplo de operações aritméticas:

```java
public class ExemploOperacoesAritmeticas {
    public static void main(String[] args) {
        int a = 10;
        int b = 3;
        
        System.out.println("a + b = " + (a + b)); // 13
        System.out.println("a - b = " + (a - b)); // 7
        System.out.println("a * b = " + (a * b)); // 30
        System.out.println("a / b = " + (a / b)); // 3 (divisão inteira)
        System.out.println("a % b = " + (a % b)); // 1 (resto)
        
        // Divisão com números de ponto flutuante
        double c = 10.0;
        double d = 3.0;
        System.out.println("c / d = " + (c / d)); // 3.3333333333333335
    }
}
```

#### ⚠️ Cuidados com a divisão:

- Divisão entre inteiros resulta em um inteiro (trunca a parte decimal)
- Para obter um resultado com casas decimais, pelo menos um operando deve ser do tipo ponto flutuante

```java
int x = 10;
int y = 3;
double resultadoInteiro = x / y;        // 3.0 (divisão inteira, depois convertida para double)
double resultadoExato = (double) x / y; // 3.3333333333333335 (casting para divisão de ponto flutuante)
```

### Operadores de Atribuição

Usados para atribuir valores a variáveis:

| Operador | Descrição | Exemplo | Equivalente a |
|----------|-----------|---------|---------------|
| `=` | Atribuição simples | `x = 5;` | - |
| `+=` | Atribuição com adição | `x += 3;` | `x = x + 3;` |
| `-=` | Atribuição com subtração | `x -= 3;` | `x = x - 3;` |
| `*=` | Atribuição com multiplicação | `x *= 3;` | `x = x * 3;` |
| `/=` | Atribuição com divisão | `x /= 3;` | `x = x / 3;` |
| `%=` | Atribuição com módulo | `x %= 3;` | `x = x % 3;` |
| `&=` | Atribuição com AND bit a bit | `x &= 3;` | `x = x & 3;` |
| `^=` | Atribuição com XOR bit a bit | `x ^= 3;` | `x = x ^ 3;` |
| `|=` | Atribuição com OR bit a bit | `x |= 3;` | `x = x | 3;` |
| `<<=` | Atribuição com deslocamento à esquerda | `x <<= 2;` | `x = x << 2;` |
| `>>=` | Atribuição com deslocamento à direita | `x >>= 2;` | `x = x >> 2;` |
| `>>>=` | Atribuição com deslocamento à direita sem sinal | `x >>>= 2;` | `x = x >>> 2;` |

#### Exemplo de operadores de atribuição:

```java
public class ExemploOperadoresAtribuicao {
    public static void main(String[] args) {
        int a = 10;
        
        a += 5;  // a = a + 5
        System.out.println("Após a += 5: " + a);  // 15
        
        a -= 3;  // a = a - 3
        System.out.println("Após a -= 3: " + a);  // 12
        
        a *= 2;  // a = a * 2
        System.out.println("Após a *= 2: " + a);  // 24
        
        a /= 4;  // a = a / 4
        System.out.println("Após a /= 4: " + a);  // 6
        
        a %= 4;  // a = a % 4
        System.out.println("Após a %= 4: " + a);  // 2
    }
}
```

### Operadores de Comparação (Relacionais)

Usados para comparar valores e retornar um resultado booleano (`true` ou `false`):

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `==` | Igual a | `a == b` |
| `!=` | Diferente de | `a != b` |
| `>` | Maior que | `a > b` |
| `<` | Menor que | `a < b` |
| `>=` | Maior ou igual a | `a >= b` |
| `<=` | Menor ou igual a | `a <= b` |

#### Exemplo de operadores de comparação:

```java
public class ExemploOperadoresComparacao {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        int c = 10;
        
        System.out.println("a == b: " + (a == b));  // false
        System.out.println("a == c: " + (a == c));  // true
        System.out.println("a != b: " + (a != b));  // true
        System.out.println("a > b: " + (a > b));    // false
        System.out.println("a < b: " + (a < b));    // true
        System.out.println("a >= c: " + (a >= c));  // true
        System.out.println("a <= b: " + (a <= b));  // true
    }
}
```

#### ⚠️ Cuidado ao comparar objetos:

Para objetos, o operador `==` compara as referências, não os conteúdos. Para comparar conteúdos, use o método `equals()`:

```java
String s1 = "Hello";
String s2 = "Hello";
String s3 = new String("Hello");

System.out.println(s1 == s2);       // true (mesma referência no pool de strings)
System.out.println(s1 == s3);       // false (referências diferentes)
System.out.println(s1.equals(s3));  // true (mesmo conteúdo)
```

### Operadores Lógicos

Usados para combinar expressões booleanas:

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `&&` | AND lógico | `a && b` |
| `\|\|` | OR lógico | `a \|\| b` |
| `!` | NOT lógico | `!a` |

#### Exemplo de operadores lógicos:

```java
public class ExemploOperadoresLogicos {
    public static void main(String[] args) {
        boolean a = true;
        boolean b = false;
        
        System.out.println("a && b: " + (a && b));  // false
        System.out.println("a || b: " + (a || b));  // true
        System.out.println("!a: " + (!a));          // false
        
        // Exemplos mais complexos
        int x = 10;
        int y = 20;
        int z = 30;
        
        boolean resultado1 = (x < y) && (y < z);  // true && true = true
        boolean resultado2 = (x > y) || (y < z);  // false || true = true
        boolean resultado3 = !(x > y);            // !(false) = true
        
        System.out.println("(x < y) && (y < z): " + resultado1);
        System.out.println("(x > y) || (y < z): " + resultado2);
        System.out.println("!(x > y): " + resultado3);
    }
}
```

#### Avaliação de curto-circuito (short-circuit evaluation):

- `&&`: Se o primeiro operando for `false`, o segundo não é avaliado
- `||`: Se o primeiro operando for `true`, o segundo não é avaliado

```java
int n = 10;
// O segundo operando será avaliado apenas se n > 5 for true
if (n > 5 && n++ < 20) {
    System.out.println("Condição verdadeira. n = " + n); // n = 11
}
```

### Operadores Bit a Bit (Bitwise)

Manipulam bits individuais de valores inteiros:

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `&` | AND bit a bit | `a & b` |
| `\|` | OR bit a bit | `a \| b` |
| `^` | XOR bit a bit | `a ^ b` |
| `~` | NOT bit a bit (complemento de um) | `~a` |
| `<<` | Deslocamento à esquerda | `a << n` |
| `>>` | Deslocamento à direita | `a >> n` |
| `>>>` | Deslocamento à direita sem sinal | `a >>> n` |

#### Exemplo de operadores bit a bit:

```java
public class ExemploOperadoresBitwise {
    public static void main(String[] args) {
        int a = 5;  // 0101 em binário
        int b = 3;  // 0011 em binário
        
        System.out.println("a & b: " + (a & b));    // 0001 = 1 (AND)
        System.out.println("a | b: " + (a | b));    // 0111 = 7 (OR)
        System.out.println("a ^ b: " + (a ^ b));    // 0110 = 6 (XOR)
        System.out.println("~a: " + (~a));          // 1010 = -6 (NOT, complemento de 2)
        
        System.out.println("a << 1: " + (a << 1));  // 1010 = 10 (desloca 1 bit para esquerda)
        System.out.println("a >> 1: " + (a >> 1));  // 0010 = 2 (desloca 1 bit para direita)
        
        // Demonstração de >>> (preserva zeros à esquerda)
        int c = -1;  // Todos os bits são 1 em complemento de 2
        System.out.println("c >> 1: " + (c >> 1));   // Ainda negativo
        System.out.println("c >>> 1: " + (c >>> 1)); // Positivo, insere 0 à esquerda
    }
}
```

### ⬆️ Operadores Unários

Operam em um único operando:

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `+` | Unário mais (indica valor positivo) | `+a` |
| `-` | Unário menos (nega um valor) | `-a` |
| `++` | Incremento (pré ou pós) | `++a` ou `a++` |
| `--` | Decremento (pré ou pós) | `--a` ou `a--` |
| `!` | Negação lógica | `!a` |

#### ⚠️ Diferenças entre pré e pós incremento/decremento:

- Pré-incremento (`++a`): incrementa o valor e depois retorna
- Pós-incremento (`a++`): retorna o valor atual e depois incrementa

```java
public class ExemploOperadoresUnarios {
    public static void main(String[] args) {
        int a = 5;
        int b, c;
        
        b = ++a;  // Pré-incremento: a é incrementado para 6, depois b recebe 6
        System.out.println("Após b = ++a: a = " + a + ", b = " + b);  // a = 6, b = 6
        
        a = 5;    // Resetando a
        c = a++;  // Pós-incremento: c recebe 5, depois a é incrementado para 6
        System.out.println("Após c = a++: a = " + a + ", c = " + c);  // a = 6, c = 5
        
        // Operador de negação lógica
        boolean flag = true;
        System.out.println("!flag: " + (!flag));  // false
    }
}
```

### Operador Ternário

Um operador condicional que funciona como um if-else simplificado:

```
resultado = (condição) ? valorSeVerdadeiro : valorSeFalso;
```

#### Exemplo de operador ternário:

```java
public class ExemploOperadorTernario {
    public static void main(String[] args) {
        int idade = 17;
        String status = (idade >= 18) ? "Adulto" : "Menor de idade";
        System.out.println(status);  // "Menor de idade"
        
        // Operador ternário aninhado
        int nota = 75;
        String resultado = (nota >= 90) ? "A" : 
                          (nota >= 80) ? "B" : 
                          (nota >= 70) ? "C" : 
                          (nota >= 60) ? "D" : "F";
        System.out.println("Nota: " + resultado);  // "C"
    }
}
```

### Operador instanceof

Verifica se um objeto é instância de um tipo específico:

```java
public class ExemploInstanceOf {
    public static void main(String[] args) {
        String texto = "Olá";
        
        boolean eString = texto instanceof String;
        System.out.println("texto é uma String? " + eString);  // true
        
        Object obj = new String("Hello");
        if (obj instanceof String) {
            String str = (String) obj;  // Cast seguro
            System.out.println("Comprimento: " + str.length());
        }
    }
}
```

### Precedência de Operadores

Os operadores em Java seguem uma ordem de precedência:

| Prioridade | Operadores | Descrição |
|------------|------------|-----------|
| 1 (maior) | `()`, `[]`, `.` | Parênteses, colchetes, acesso a membros |
| 2 | `++`, `--`, `+` (unário), `-` (unário), `!`, `~` | Operadores unários |
| 3 | `*`, `/`, `%` | Multiplicação, divisão, módulo |
| 4 | `+`, `-` | Adição, subtração |
| 5 | `<<`, `>>`, `>>>` | Operadores de deslocamento |
| 6 | `<`, `<=`, `>`, `>=`, `instanceof` | Operadores relacionais |
| 7 | `==`, `!=` | Operadores de igualdade |
| 8 | `&` | AND bit a bit |
| 9 | `^` | XOR bit a bit |
| 10 | `\|` | OR bit a bit |
| 11 | `&&` | AND lógico |
| 12 | `\|\|` | OR lógico |
| 13 | `? :` | Operador ternário |
| 14 (menor) | `=`, `+=`, `-=`, etc. | Operadores de atribuição |

#### Exemplo de precedência:

```java
public class ExemploPrecedencia {
    public static void main(String[] args) {
        int resultado = 5 + 3 * 2;  // 3 * 2 é calculado primeiro
        System.out.println(resultado);  // 11
        
        // Usando parênteses para alterar a precedência
        int comParenteses = (5 + 3) * 2;
        System.out.println(comParenteses);  // 16
        
        // Exemplo com múltiplos operadores
        int a = 10, b = 5, c = 2;
        int expressao = a + b * c - a / c;  // 10 + (5 * 2) - (10 / 2)
        System.out.println(expressao);  // 10 + 10 - 5 = 15
    }
}
```

### Conversões (Casting)

Ao usar operadores com tipos diferentes, Java pode realizar conversões automáticas (promoção) ou exigir conversões explícitas (casting):

#### ⬆️ Conversão implícita (Widening):

```java
int numeroInteiro = 10;
double numeroDouble = numeroInteiro;  // Conversão implícita de int para double
```

#### ⬇️ Conversão explícita (Narrowing):

```java
double numeroDouble = 10.5;
int numeroInteiro = (int) numeroDouble;  // Conversão explícita (casting) de double para int, resulta em 10
```

#### Exemplo de conversões em operações:

```java
public class ExemploCasting {
    public static void main(String[] args) {
        byte b = 10;
        short s = 20;
        int i = 30;
        long l = 40L;
        float f = 50.0f;
        double d = 60.0;
        
        // Promoção automática em expressões
        double resultado1 = b + d;  // byte é promovido para double
        System.out.println("b + d = " + resultado1);
        
        // Casting explícito
        int resultado2 = (int) (l / i);  // resultado long precisa ser convertido para int
        System.out.println("(int) (l / i) = " + resultado2);
        
        // Operações entre diferentes tipos numéricos
        double resultado3 = i * f / d + l;  // Diferentes promoções ocorrem
        System.out.println("i * f / d + l = " + resultado3);
    }
}
```

### Dicas e Boas Práticas

1. **Legibilidade**: Use parênteses para tornar a precedência explícita, mesmo quando não estritamente necessário
2. **Comparação de ponto flutuante**: Evite compará-los diretamente com `==` devido a imprecisões; use uma margem de erro
3. **Efeitos colaterais**: Tenha cuidado com operadores que modificam variáveis (como `++` e `--`)
4. **Divisão por zero**: Evite divisão por zero, que causa `ArithmeticException` para tipos inteiros
5. **Overflow/Underflow**: Esteja ciente dos limites dos tipos quando realizar operações
6. **Short-circuit**: Aproveite a avaliação de curto-circuito de operadores lógicos para eficiência

```java
// Uso seguro do curto-circuito para evitar NullPointerException
if (objeto != null && objeto.metodo()) {
    // objeto.metodo() só é chamado se objeto não for null
}
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>