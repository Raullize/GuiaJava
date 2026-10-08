<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Variáveis e Constantes

## Armazenando e manipulando dados em Java

As variáveis e constantes são fundamentais em qualquer linguagem de programação, pois permitem armazenar e manipular dados durante a execução do programa. Em Java, elas seguem regras específicas que precisamos entender.

### O que são Variáveis?

Variáveis são espaços na memória que armazenam valores que podem ser alterados durante a execução do programa. Em Java, toda variável precisa:

1. Ter um tipo de dado definido
2. Ter um nome (identificador)
3. Ser declarada antes de ser usada

#### Sintaxe para Declaração de Variáveis

```java
tipo nomeVariavel;  // Declaração
nomeVariavel = valor;  // Atribuição

// Ou em uma única linha
tipo nomeVariavel = valor;  // Declaração e atribuição
```

#### Exemplos:

```java
// Declarações simples
int idade;
double salario;
String nome;

// Declarações com inicialização
int contador = 0;
double altura = 1.75;
String mensagem = "Olá, mundo!";

// Múltiplas variáveis do mesmo tipo
int x, y, z;
double largura = 10.5, altura = 20.8;
```

### Regras para Nomes de Variáveis

Em Java, os nomes de variáveis devem seguir algumas regras:

✅ **Permitido**:
- Letras (a-z, A-Z)
- Dígitos (0-9) - mas não como primeiro caractere
- Underscore (_)
- Cifrão ($) - geralmente usado por código gerado

❌ **Não permitido**:
- Iniciar com um número
- Usar palavras reservadas do Java (como `if`, `class`, `for`)
- Conter espaços ou caracteres especiais

#### Convenções de Nomenclatura

Em Java, seguimos a convenção camelCase para variáveis:

```java
int idadePessoa;
double taxaDeJurosAnual;
String nomeDoProduto;
boolean estaAtivo;
```

### Escopo de Variáveis

O escopo define onde uma variável pode ser acessada:

#### 1. Variáveis de Instância (Atributos)

Declaradas dentro da classe, mas fora de métodos:

```java
public class Pessoa {
    // Variáveis de instância (escopo da classe)
    String nome;
    int idade;
    
    public void exibirDados() {
        // Pode acessar nome e idade aqui
        System.out.println(nome + " tem " + idade + " anos");
    }
}
```

#### 2. Variáveis Locais

Declaradas dentro de métodos, construtores ou blocos:

```java
public void calcularSalario() {
    // Variável local (escopo do método)
    double salarioBase = 2000.0;
    double bonus = 500.0;
    
    // Só é acessível dentro deste método
    double total = salarioBase + bonus;
    System.out.println("Salário total: " + total);
}
```

#### 3. Variáveis de Bloco

Declaradas dentro de blocos como `if`, `for`, `while`:

```java
if (condicao) {
    // Variável de bloco (escopo do bloco if)
    int resultado = 10;
    System.out.println(resultado);
} // resultado não é acessível fora deste bloco
```

#### 4. Parâmetros de Método

Declarados na assinatura do método:

```java
public void saudacao(String nome, int idade) {
    // nome e idade são parâmetros (escopo do método)
    System.out.println("Olá, " + nome + "! Você tem " + idade + " anos.");
}
```

#### 5. Variáveis Estáticas (de Classe)

Compartilhadas entre todas as instâncias de uma classe:

```java
public class Contador {
    // Variável estática (escopo da classe, compartilhada entre instâncias)
    static int contagem = 0;
    
    public Contador() {
        contagem++;
    }
}
```

### Constantes em Java

Constantes são valores que não podem ser alterados após a atribuição inicial. Em Java, usamos a palavra-chave `final` para declarar constantes:

```java
final double PI = 3.14159265359;
final int DIAS_DA_SEMANA = 7;
final String EMPRESA = "Minha Empresa Ltda.";
```

#### ⚠️ Características das constantes:

1. São declaradas com a palavra-chave `final`
2. Por convenção, usamos UPPER_SNAKE_CASE para nomes de constantes
3. Normalmente também são declaradas como `static` para serem compartilhadas

```java
public class Matematica {
    // Constante de classe
    public static final double PI = 3.14159;
    
    // Constante de instância 
    final int VALOR;
    
    // Constante inicializada no construtor
    public Matematica(int valor) {
        this.VALOR = valor; // Permitido, pois é a primeira atribuição
    }
}
```

### Uso de Separadores de Dígitos (_)

Para melhorar a legibilidade de valores numéricos longos, Java permite o uso de sublinhados como separadores de dígitos:

```java
int umMilhao = 1_000_000;
long populacaoMundial = 7_900_000_000L;
double valorPi = 3.141_592_653_589;
```

Regras para uso do separador `_`:
- Não pode estar no início ou final do número
- Não pode estar junto a um ponto decimal
- Não pode estar antes dos sufixos como L, F ou D

### Tipos de Inicialização de Variáveis

#### 1. Inicialização Explícita

```java
int contador = 0;
```

#### 2. Inicialização via construtor

```java
public class Pessoa {
    String nome;
    int idade;
    
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
}
```

#### 3. Inicialização em blocos

```java
public class Exemplo {
    int a;
    static int b;
    
    // Bloco de inicialização de instância
    {
        a = 10;
        System.out.println("Bloco de inicialização executado");
    }
    
    // Bloco de inicialização estático
    static {
        b = 20;
        System.out.println("Bloco estático executado");
    }
}
```

### Exemplo Prático

Vamos ver um exemplo completo de uso de variáveis e constantes:

```java
public class ContaBancaria {
    // Constantes
    private static final double TAXA_MANUTENCAO = 2.5;
    
    // Variáveis de instância
    private String titular;
    private String numeroConta;
    private double saldo;
    
    // Variável estática
    private static int totalContas = 0;
    
    // Construtor
    public ContaBancaria(String titular, double saldoInicial) {
        this.titular = titular;
        this.saldo = saldoInicial;
        totalContas++;
        this.numeroConta = "C" + totalContas;
    }
    
    // Método com variáveis locais
    public void depositar(double valor) {
        if (valor > 0) {
            double taxaOperacao = 0.0;
            
            // Variável de bloco
            if (valor > 1000) {
                double bonus = valor * 0.01;
                valor += bonus;
            }
            
            this.saldo += valor - taxaOperacao;
            System.out.println("Depósito de R$ " + valor + " realizado com sucesso.");
        } else {
            System.out.println("Valor de depósito inválido.");
        }
    }
    
    public void exibirDados() {
        System.out.println("Conta: " + numeroConta);
        System.out.println("Titular: " + titular);
        System.out.println("Saldo: R$ " + saldo);
        System.out.println("Taxa de manutenção: R$ " + TAXA_MANUTENCAO);
    }
    
    // Método estático
    public static int getTotalContas() {
        return totalContas;
    }
}
```

### Dicas e Boas Práticas

1. **Escopo limitado**: Mantenha o escopo das variáveis o mais limitado possível
2. **Inicialização**: Sempre inicialize variáveis antes de usá-las
3. **Descritivo**: Use nomes significativos que descrevem o propósito da variável
4. **Constantes**: Use constantes para valores que não mudam
5. **Convenções**: Siga as convenções de nomenclatura padrão do Java
6. **Declaração única**: Evite declarar múltiplas variáveis na mesma linha para maior clareza

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>