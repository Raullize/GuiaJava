<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 🔄 Métodos

## 🧩 Criando e utilizando blocos de código reutilizáveis em Java

Os métodos são blocos de código que executam tarefas específicas e podem ser reutilizados em diferentes partes do programa. Eles são fundamentais para implementar o princípio "Don't Repeat Yourself" (DRY) e organizar o código de forma modular. Neste guia, aprenderemos a criar e utilizar métodos em Java.

### 📋 Fundamentos de métodos

#### 🏗️ Anatomia de um método

A estrutura básica de um método em Java é:

```java
modificadorAcesso tipoRetorno nomeMetodo(parametros) {
    // Corpo do método
    // Instruções a serem executadas
    
    return valor; // se o tipo de retorno não for void
}
```

Vamos analisar cada parte:

| Componente | Descrição | Exemplo |
|------------|-----------|---------|
| Modificador de acesso | Define a visibilidade do método | `public`, `private`, `protected` |
| Tipo de retorno | Define o tipo de dado que o método retorna | `int`, `String`, `void` (sem retorno) |
| Nome do método | Identificador do método | `calcularSoma`, `imprimirDados` |
| Parâmetros | Valores que o método recebe | `(int numero, String texto)` |
| Corpo | Bloco de código com as instruções | `{ System.out.println("Olá"); }` |
| Instrução return | Retorna um valor (se não for void) | `return resultado;` |

#### 🌟 Exemplo de método simples

```java
public class ExemploMetodo {
    // Método que recebe dois parâmetros e retorna sua soma
    public static int somar(int a, int b) {
        int resultado = a + b;
        return resultado;
    }
    
    public static void main(String[] args) {
        // Chamando o método e armazenando o resultado
        int resultadoSoma = somar(5, 3);
        System.out.println("Soma: " + resultadoSoma); // Saída: Soma: 8
        
        // Chamando o método diretamente em uma expressão
        System.out.println("Nova soma: " + somar(10, 20)); // Saída: Nova soma: 30
    }
}
```

### 🔠 Tipos de métodos

#### 📤 Métodos com e sem retorno

**Métodos com retorno** devem especificar o tipo de dado que retornam e incluir uma instrução `return`:

```java
// Método que retorna um valor int
public static int quadrado(int numero) {
    return numero * numero;
}

// Método que retorna um boolean
public static boolean ehPar(int numero) {
    return numero % 2 == 0;
}

// Método que retorna uma String
public static String saudacao(String nome) {
    return "Olá, " + nome + "!";
}
```

**Métodos sem retorno** usam o tipo `void` e não incluem instrução `return` com valor:

```java
// Método que não retorna valor (void)
public static void imprimirLinha() {
    System.out.println("------------------------");
}

// Método void que recebe parâmetros
public static void imprimirMensagem(String mensagem) {
    System.out.println("MENSAGEM: " + mensagem);
}
```

Um método `void` pode conter uma instrução `return` sem valor para sair do método antecipadamente:

```java
public static void verificarIdade(int idade) {
    if (idade < 0) {
        System.out.println("Idade inválida!");
        return; // Sai do método antecipadamente
    }
    
    System.out.println("Idade: " + idade + " anos");
}
```

#### 🚶 Métodos estáticos vs. métodos de instância

**Métodos estáticos (static)** pertencem à classe, não a instâncias específicas:

```java
public class Calculadora {
    // Método estático - acessado através da classe
    public static int somar(int a, int b) {
        return a + b;
    }
}

// Uso:
int resultado = Calculadora.somar(10, 5); // Chamada sem instanciar
```

**Métodos de instância** pertencem a objetos específicos (instâncias da classe):

```java
public class Pessoa {
    private String nome;
    private int idade;
    
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
    
    // Método de instância - precisa de um objeto para ser chamado
    public void apresentar() {
        System.out.println("Olá, eu sou " + nome + " e tenho " + idade + " anos.");
    }
    
    // Outro método de instância
    public int getIdadeEmMeses() {
        return idade * 12;
    }
}

// Uso:
Pessoa pessoa = new Pessoa("Maria", 30);
pessoa.apresentar(); // Chamada através da instância
int meses = pessoa.getIdadeEmMeses();
```

### 📥 Parâmetros e argumentos

#### 🔄 Passagem de parâmetros

Em Java, os parâmetros são passados de duas formas, dependendo do tipo:

1. **Por valor**: para tipos primitivos (`int`, `float`, `boolean`, etc.)
2. **Por referência**: para objetos (arrays, strings, classes personalizadas, etc.)

```java
public class ExemploParametros {
    public static void main(String[] args) {
        // Valor primitivo
        int numero = 10;
        modificarNumero(numero);
        System.out.println("Valor após método: " + numero); // Continua 10
        
        // Objeto (array)
        int[] numeros = {1, 2, 3};
        modificarArray(numeros);
        System.out.println("Primeiro elemento após método: " + numeros[0]); // Agora é 100
    }
    
    // Parâmetro primitivo (passado por valor)
    public static void modificarNumero(int valor) {
        valor = 20; // Modifica apenas a cópia local
    }
    
    // Parâmetro de objeto (passado por referência)
    public static void modificarArray(int[] array) {
        array[0] = 100; // Modifica o objeto original
    }
}
```

#### 📦 Tipos de parâmetros

**Parâmetros obrigatórios** são declarados normalmente e devem ser fornecidos na chamada:

```java
public static int somar(int a, int b) {
    return a + b;
}

// Chamada
int resultado = somar(5, 3);
```

**Número variável de parâmetros (varargs)** permite passar quantos argumentos forem necessários:

```java
public static int somarTodos(int... numeros) {
    int soma = 0;
    for (int numero : numeros) {
        soma += numero;
    }
    return soma;
}

// Chamadas
int soma1 = somarTodos(1, 2); // Passa 2 argumentos
int soma2 = somarTodos(1, 2, 3, 4, 5); // Passa 5 argumentos
int soma3 = somarTodos(); // Não passa argumentos
```

**Parâmetros com valores padrão** não existem diretamente em Java, mas podem ser simulados com sobrecarga de métodos:

```java
// Método com valor padrão para mensagem
public static void saudacao(String nome) {
    saudacao(nome, "Olá");
}

// Versão completa do método
public static void saudacao(String nome, String prefixo) {
    System.out.println(prefixo + ", " + nome + "!");
}

// Chamadas
saudacao("Maria"); // Usa o padrão "Olá"
saudacao("João", "Bem-vindo"); // Especifica o prefixo
```

### 🔄 Sobrecarga de métodos

A sobrecarga permite criar múltiplas versões do mesmo método com diferentes parâmetros:

```java
public class Calculadora {
    // Soma de inteiros
    public static int somar(int a, int b) {
        return a + b;
    }
    
    // Soma de três inteiros
    public static int somar(int a, int b, int c) {
        return a + b + c;
    }
    
    // Soma de doubles
    public static double somar(double a, double b) {
        return a + b;
    }
    
    // Concatenação de strings
    public static String somar(String a, String b) {
        return a + b;
    }
}
```

Regras para sobrecarga:
- Os métodos devem ter o mesmo nome
- Os métodos devem ter diferentes listas de parâmetros (tipo, ordem ou quantidade)
- O tipo de retorno pode ser diferente, mas isso sozinho não é suficiente para diferenciar os métodos

### 🔁 Recursividade

Um método pode chamar a si mesmo, criando um padrão recursivo:

```java
public class Recursividade {
    // Cálculo de fatorial usando recursividade
    public static long fatorial(int n) {
        // Caso base
        if (n <= 1) {
            return 1;
        }
        
        // Passo recursivo
        return n * fatorial(n - 1);
    }
    
    // Sequência de Fibonacci usando recursividade
    public static int fibonacci(int n) {
        if (n <= 1) {
            return n;
        }
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
    
    public static void main(String[] args) {
        System.out.println("Fatorial de 5: " + fatorial(5)); // 120
        System.out.println("Fibonacci de 6: " + fibonacci(6)); // 8
    }
}
```

### 🛡️ Encapsulamento com métodos

Os métodos são fundamentais para implementar o encapsulamento, um dos pilares da Programação Orientada a Objetos:

```java
public class ContaBancaria {
    private double saldo;
    private String titular;
    
    public ContaBancaria(String titular, double saldoInicial) {
        this.titular = titular;
        
        // Usando método para validação na inicialização
        this.depositar(saldoInicial);
    }
    
    // Método getter (acessor)
    public double getSaldo() {
        return saldo;
    }
    
    // Método getter
    public String getTitular() {
        return titular;
    }
    
    // Método setter (modificador) com validação
    public void setTitular(String titular) {
        if (titular != null && !titular.trim().isEmpty()) {
            this.titular = titular;
        }
    }
    
    // Método para operação de depósito
    public boolean depositar(double valor) {
        if (valor > 0) {
            this.saldo += valor;
            return true;
        }
        return false;
    }
    
    // Método para operação de saque com validação
    public boolean sacar(double valor) {
        if (valor > 0 && valor <= saldo) {
            this.saldo -= valor;
            return true;
        }
        return false;
    }
    
    // Método para transferência entre contas
    public boolean transferir(ContaBancaria destino, double valor) {
        if (this.sacar(valor)) {
            return destino.depositar(valor);
        }
        return false;
    }
}
```

### 🔌 Métodos especiais

#### ⚙️ Construtores

Construtores são métodos especiais para inicializar objetos:

```java
public class Produto {
    private String nome;
    private double preco;
    
    // Construtor padrão (sem parâmetros)
    public Produto() {
        this.nome = "Sem nome";
        this.preco = 0.0;
    }
    
    // Construtor com parâmetros
    public Produto(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }
    
    // Construtor que chama outro construtor
    public Produto(String nome) {
        this(nome, 0.0); // Chama o construtor com dois parâmetros
    }
}
```

#### 🔢 Métodos toString(), equals() e hashCode()

Estes métodos são herdados da classe Object e geralmente são sobrescritos:

```java
public class Pessoa {
    private String nome;
    private int idade;
    
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
    
    // Sobrescrevendo toString para representação em string
    @Override
    public String toString() {
        return "Pessoa [nome=" + nome + ", idade=" + idade + "]";
    }
    
    // Sobrescrevendo equals para comparação de igualdade
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        
        Pessoa outraPessoa = (Pessoa) obj;
        return idade == outraPessoa.idade && 
               Objects.equals(nome, outraPessoa.nome);
    }
    
    // Sobrescrevendo hashCode para uso em coleções
    @Override
    public int hashCode() {
        return Objects.hash(nome, idade);
    }
}
```

### 🌐 Escopo e visibilidade

#### 📊 Modificadores de acesso

Java tem quatro níveis de acesso para métodos e atributos:

| Modificador | Classe | Pacote | Subclasse | Mundo |
|-------------|--------|--------|-----------|-------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| Padrão (sem modificador) | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

```java
public class ExemploModificadores {
    // Visível apenas dentro desta classe
    private void metodoPrivado() {
        System.out.println("Método privado");
    }
    
    // Visível apenas dentro deste pacote
    void metodoDefault() {
        System.out.println("Método default");
    }
    
    // Visível nesta classe, pacote e subclasses
    protected void metodoProtegido() {
        System.out.println("Método protegido");
    }
    
    // Visível para todas as classes
    public void metodoPublico() {
        System.out.println("Método público");
    }
}
```

#### 🌍 Outros modificadores

Além dos modificadores de acesso, podemos usar:

- `static`: Método pertence à classe, não à instância
- `final`: Método não pode ser sobrescrito
- `abstract`: Método sem implementação, deve ser sobrescrito
- `synchronized`: Método só pode ser acessado por uma thread de cada vez
- `native`: Implementação em código nativo (não Java)

```java
public class ExemploModificadoresAdicionais {
    // Método de classe (static)
    public static void metodoEstatico() {
        System.out.println("Método estático");
    }
    
    // Método final (não pode ser sobrescrito)
    public final void metodoFinal() {
        System.out.println("Método final");
    }
    
    // Método sincronizado (thread-safe)
    public synchronized void metodoSincronizado() {
        System.out.println("Método sincronizado");
    }
}

// Classe abstrata com método abstrato
abstract class ClasseAbstrata {
    // Método abstrato (sem implementação)
    public abstract void metodoAbstrato();
}
```

### 🧠 Boas práticas e padrões

#### 🔤 Convenções de nomenclatura

- Use verbos para nomes de métodos (ação)
- Use camelCase (primeira letra minúscula, demais palavras com inicial maiúscula)
- Nomes devem ser descritivos e claros

```java
// Bons nomes de métodos
calcularTotal()
enviarEmail()
validarCPF()
buscarUsuarioPorId()

// Nomes ruins
x()  // não descritivo
CALCULAR_TOTAL()  // errado para métodos
Processar()  // primeira letra deveria ser minúscula
```

#### 📏 Princípio da responsabilidade única

Cada método deve fazer apenas uma coisa e fazê-la bem:

```java
// Ruim: método com múltiplas responsabilidades
public void processarPedido(Pedido pedido) {
    // Valida pedido
    if (pedido.getItens().isEmpty()) {
        throw new IllegalArgumentException("Pedido sem itens");
    }
    
    // Calcula total
    double total = 0;
    for (Item item : pedido.getItens()) {
        total += item.getPreco() * item.getQuantidade();
    }
    pedido.setTotal(total);
    
    // Salva no banco de dados
    bancoDAO.salvarPedido(pedido);
    
    // Envia email
    emailService.enviarConfirmacao(pedido);
}

// Bom: métodos com responsabilidade única
public void processarPedido(Pedido pedido) {
    validarPedido(pedido);
    calcularTotal(pedido);
    salvarPedido(pedido);
    enviarConfirmacao(pedido);
}

private void validarPedido(Pedido pedido) {
    if (pedido.getItens().isEmpty()) {
        throw new IllegalArgumentException("Pedido sem itens");
    }
}

private void calcularTotal(Pedido pedido) {
    double total = 0;
    for (Item item : pedido.getItens()) {
        total += item.getPreco() * item.getQuantidade();
    }
    pedido.setTotal(total);
}

private void salvarPedido(Pedido pedido) {
    bancoDAO.salvarPedido(pedido);
}

private void enviarConfirmacao(Pedido pedido) {
    emailService.enviarConfirmacao(pedido);
}
```

#### 🛡️ Validação de parâmetros

Sempre valide entradas para evitar comportamentos inesperados:

```java
public void transferir(ContaBancaria destino, double valor) {
    // Validação de parâmetros
    if (destino == null) {
        throw new IllegalArgumentException("Conta de destino não pode ser nula");
    }
    
    if (valor <= 0) {
        throw new IllegalArgumentException("Valor deve ser positivo");
    }
    
    if (valor > this.saldo) {
        throw new IllegalArgumentException("Saldo insuficiente");
    }
    
    // Após validação, executa a lógica de negócio
    this.saldo -= valor;
    destino.depositar(valor);
}
```

#### ⚡ Otimizando métodos

```java
// Evite criar objetos desnecessários dentro de loops
public void processarLista(List<String> lista) {
    // Ruim: cria um novo DateFormat em cada iteração
    for (String item : lista) {
        SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
        // Processo usando sdf...
    }
    
    // Bom: reutiliza o mesmo objeto
    SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
    for (String item : lista) {
        // Processo usando sdf...
    }
}

// Evite computações repetidas
public int calcularFibonacci(int n) {
    // Ruim: cálculo recursivo ineficiente
    if (n <= 1) return n;
    return calcularFibonacci(n - 1) + calcularFibonacci(n - 2);
    
    // Melhor: usando programação dinâmica ou iteração
    // ...
}
```

### 📚 Exemplos práticos

#### 🧮 Calculadora simples

```java
public class Calculadora {
    public double somar(double a, double b) {
        return a + b;
    }
    
    public double subtrair(double a, double b) {
        return a - b;
    }
    
    public double multiplicar(double a, double b) {
        return a * b;
    }
    
    public double dividir(double a, double b) {
        if (b == 0) {
            throw new ArithmeticException("Divisão por zero não é permitida");
        }
        return a / b;
    }
    
    public double potencia(double base, int expoente) {
        return Math.pow(base, expoente);
    }
    
    public double raizQuadrada(double numero) {
        if (numero < 0) {
            throw new IllegalArgumentException("Não existe raiz quadrada real de número negativo");
        }
        return Math.sqrt(numero);
    }
}
```

#### 🧵 Manipulador de strings

```java
public class ManipuladorString {
    public boolean ehPalindromo(String texto) {
        if (texto == null) {
            return false;
        }
        
        // Remove espaços e converte para minúsculas
        String processado = texto.toLowerCase().replaceAll("\\s+", "");
        
        int inicio = 0;
        int fim = processado.length() - 1;
        
        while (inicio < fim) {
            if (processado.charAt(inicio) != processado.charAt(fim)) {
                return false;
            }
            inicio++;
            fim--;
        }
        
        return true;
    }
    
    public int contarOcorrencias(String texto, char caractere) {
        if (texto == null) {
            return 0;
        }
        
        int contador = 0;
        for (int i = 0; i < texto.length(); i++) {
            if (texto.charAt(i) == caractere) {
                contador++;
            }
        }
        
        return contador;
    }
    
    public String inverter(String texto) {
        if (texto == null) {
            return "";
        }
        
        StringBuilder invertido = new StringBuilder();
        for (int i = texto.length() - 1; i >= 0; i--) {
            invertido.append(texto.charAt(i));
        }
        
        return invertido.toString();
    }
}
```

#### 🧪 Utilitário de validação

```java
public class Validador {
    public static boolean ehEmailValido(String email) {
        if (email == null || email.isBlank()) {
            return false;
        }
        
        // Expressão regular simplificada para email
        String regex = "^[A-Za-z0-9+_.-]+@(.+)$";
        return email.matches(regex);
    }
    
    public static boolean ehCPFValido(String cpf) {
        if (cpf == null) {
            return false;
        }
        
        // Remove caracteres não numéricos
        cpf = cpf.replaceAll("\\D", "");
        
        // Verifica tamanho
        if (cpf.length() != 11) {
            return false;
        }
        
        // Verifica dígitos repetidos
        if (cpf.matches("(\\d)\\1{10}")) {
            return false;
        }
        
        // Calcula dígitos verificadores
        // (implementação simplificada)
        
        return true; // Retornaria o resultado da validação completa
    }
    
    public static boolean ehNumeroInteiro(String texto) {
        if (texto == null || texto.isBlank()) {
            return false;
        }
        
        try {
            Integer.parseInt(texto);
            return true;
        } catch (NumberFormatException e) {
            return false;
        }
    }
}
```

### 📋 Checklist de boas práticas

✅ **Coesão**: Cada método faz apenas uma coisa  
✅ **Nomeação**: Nomes claros e descritivos  
✅ **Tamanho**: Métodos pequenos e focados (geralmente < 20 linhas)  
✅ **Documentação**: Comentários Javadoc para métodos públicos  
✅ **Validação**: Validar parâmetros de entrada  
✅ **DRY**: Não repetir código (extrair métodos auxiliares)  
✅ **Exceções**: Tratar erros apropriadamente  
✅ **Encapsulamento**: Esconder detalhes de implementação  
✅ **Otimização**: Eficiência quando necessário  
✅ **Testabilidade**: Código fácil de testar  

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 