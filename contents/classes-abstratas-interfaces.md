<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 🧩 Classes Abstratas e Interfaces

## 🏗️ Construindo as fundações para hierarquias flexíveis em Java

As classes abstratas e interfaces são componentes fundamentais da programação orientada a objetos em Java. Elas permitem criar hierarquias de classes bem estruturadas, estabelecer contratos de comportamento e implementar polimorfismo de forma elegante. Este guia explora ambos os conceitos, suas diferenças e como utilizá-los de maneira eficaz.

### 📋 Classes Abstratas

#### 🧠 O Conceito

Uma classe abstrata é uma classe que não pode ser instanciada diretamente e foi projetada para ser estendida por subclasses. É ideal para representar conceitos abstratos ou incompletos.

```java
// Classe abstrata
public abstract class Animal {
    // Atributos
    protected String nome;
    protected int idade;
    
    // Construtor
    public Animal(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
    
    // Métodos concretos (implementados)
    public void dormir() {
        System.out.println(nome + " está dormindo...");
    }
    
    public String getNome() {
        return nome;
    }
    
    // Método abstrato (sem implementação)
    public abstract void emitirSom();
}
```

Principais características:
- Declarada com a palavra-chave `abstract`
- Pode conter métodos abstratos e concretos
- Pode ter construtores, atributos e métodos estáticos
- Não pode ser instanciada diretamente

#### 🛠️ Métodos Abstratos

Os métodos abstratos definem apenas a assinatura (nome, parâmetros e retorno), sem implementação:

```java
// Método abstrato (sem corpo)
public abstract double calcularArea();
```

Características dos métodos abstratos:
- Declarados com a palavra-chave `abstract`
- Não possuem implementação (corpo)
- Devem ser implementados por subclasses não-abstratas
- Não podem ser privados ou finais

#### 📦 Estendendo Classes Abstratas

Para utilizar uma classe abstrata, é necessário estendê-la e implementar seus métodos abstratos:

```java
// Subclasse concreta de Animal
public class Cachorro extends Animal {
    private String raca;
    
    public Cachorro(String nome, int idade, String raca) {
        super(nome, idade);  // Chama construtor da classe pai
        this.raca = raca;
    }
    
    // Implementação do método abstrato
    @Override
    public void emitirSom() {
        System.out.println("Au au!");
    }
    
    // Método específico da subclasse
    public void abanarRabo() {
        System.out.println(nome + " está abanando o rabo!");
    }
}

// Uso
Cachorro rex = new Cachorro("Rex", 3, "Pastor Alemão");
rex.emitirSom();  // Au au!
rex.dormir();     // Rex está dormindo...
rex.abanarRabo(); // Rex está abanando o rabo!
```

#### 🔄 Classes Abstratas vs. Classes Concretas

| Característica | Classe Abstrata | Classe Concreta |
|----------------|----------------|-----------------|
| Instanciação | Não pode ser instanciada diretamente | Pode ser instanciada normalmente |
| Métodos | Pode ter métodos abstratos e concretos | Todos os métodos são concretos |
| Propósito | Define comportamento comum e estrutura para subclasses | Implementa funcionalidade completa |
| Natureza | Incompleta, precisa ser estendida | Completa, pronta para uso |

### 📋 Interfaces

#### 🧠 O Conceito

Uma interface define um contrato que as classes implementadoras devem seguir. Em sua forma tradicional, ela contém apenas métodos abstratos e constantes.

```java
// Definição de uma interface
public interface Voador {
    // Constante (implicitamente public static final)
    int ALTITUDE_MAXIMA = 10000;
    
    // Métodos abstratos (implicitamente public abstract)
    void voar();
    void pousar();
}
```

Principais características:
- Declarada com a palavra-chave `interface`
- Tradicionalmente contém apenas métodos abstratos e constantes
- A partir do Java 8, pode conter métodos default e estáticos
- A partir do Java 9, pode conter métodos privados

#### 🛠️ Implementando Interfaces

Uma classe implementa uma interface usando a palavra-chave `implements`:

```java
// Classe que implementa a interface Voador
public class Aviao implements Voador {
    private String modelo;
    private int altitudeAtual;
    
    public Aviao(String modelo) {
        this.modelo = modelo;
        this.altitudeAtual = 0;
    }
    
    // Implementação dos métodos da interface
    @Override
    public void voar() {
        altitudeAtual = 5000;
        System.out.println(modelo + " decolando e subindo para " + altitudeAtual + " metros");
    }
    
    @Override
    public void pousar() {
        System.out.println(modelo + " descendo e pousando");
        altitudeAtual = 0;
    }
}

// Uso
Aviao boeing = new Aviao("Boeing 737");
boeing.voar();   // Boeing 737 decolando e subindo para 5000 metros
boeing.pousar(); // Boeing 737 descendo e pousando
```

#### 🧩 Múltiplas Interfaces

Uma classe pode implementar várias interfaces, o que permite uma forma de "herança múltipla" em Java:

```java
// Interfaces adicionais
public interface Motorizado {
    void ligarMotor();
    void desligarMotor();
}

public interface Navegavel {
    void navegar(String destino);
}

// Classe que implementa múltiplas interfaces
public class Hidroaviao implements Voador, Motorizado, Navegavel {
    private String modelo;
    private boolean motorLigado;
    
    public Hidroaviao(String modelo) {
        this.modelo = modelo;
        this.motorLigado = false;
    }
    
    // Implementação de Voador
    @Override
    public void voar() {
        if (motorLigado) {
            System.out.println(modelo + " levantando voo da água");
        } else {
            System.out.println("Não é possível voar com o motor desligado");
        }
    }
    
    @Override
    public void pousar() {
        System.out.println(modelo + " pousando na água");
    }
    
    // Implementação de Motorizado
    @Override
    public void ligarMotor() {
        motorLigado = true;
        System.out.println("Motor do " + modelo + " ligado");
    }
    
    @Override
    public void desligarMotor() {
        motorLigado = false;
        System.out.println("Motor do " + modelo + " desligado");
    }
    
    // Implementação de Navegavel
    @Override
    public void navegar(String destino) {
        System.out.println(modelo + " navegando para " + destino);
    }
}
```

#### 🔄 Recursos Modernos de Interfaces (Java 8+)

A partir do Java 8, interfaces podem conter:

##### 1. Métodos default (com implementação padrão)

```java
public interface Reprodutor {
    void play();
    void pause();
    void stop();
    
    // Método default com implementação
    default void playPause() {
        System.out.println("Alternando entre play e pause");
        // Implementação padrão que alterna entre play e pause
    }
}
```

##### 2. Métodos estáticos

```java
public interface Calculadora {
    // Método estático na interface
    static int somar(int a, int b) {
        return a + b;
    }
    
    static int subtrair(int a, int b) {
        return a - b;
    }
}

// Uso direto, sem instância
int resultado = Calculadora.somar(5, 3); // 8
```

##### 3. Métodos privados (Java 9+)

```java
public interface Logger {
    default void logInfo(String msg) {
        log(msg, "INFO");
    }
    
    default void logError(String msg) {
        log(msg, "ERROR");
    }
    
    // Método privado (reutilização interna)
    private void log(String msg, String tipo) {
        System.out.println("[" + tipo + "] " + msg);
    }
}
```

### 🔄 Comparação: Classes Abstratas vs. Interfaces

| Característica | Classe Abstrata | Interface |
|----------------|----------------|-----------|
| Instanciação | Não pode ser instanciada diretamente | Não pode ser instanciada |
| Herança | Herança única (extends) | Uma classe pode implementar múltiplas interfaces |
| Atributos | Pode ter atributos com qualquer modificador | Somente constantes (public static final) |
| Métodos | Pode ter métodos concretos, abstratos, etc. | Métodos abstratos, default, estáticos |
| Construtores | Pode ter construtores | Não possui construtores |
| Modificadores | Pode usar protected, private, etc. | Métodos são implicitamente public |
| Propósito | Compartilhar código comum em uma hierarquia | Definir comportamentos que podem ser implementados por classes não relacionadas |

### 🏆 Quando usar cada um?

#### ✅ Use Classes Abstratas quando:

1. Deseja compartilhar código entre classes intimamente relacionadas
2. Precisa de acesso a modificadores como protected
3. Quer declarar campos não-estáticos, construtores ou métodos com acesso protegido
4. A funcionalidade comum precisa ser herdada diretamente

```java
// Exemplo de uso adequado de classe abstrata
public abstract class Funcionario {
    // Estado compartilhado
    protected String nome;
    protected double salarioBase;
    
    // Construtor comum
    public Funcionario(String nome, double salarioBase) {
        this.nome = nome;
        this.salarioBase = salarioBase;
    }
    
    // Método com implementação parcial
    public void exibirDetalhes() {
        System.out.println("Nome: " + nome);
        System.out.println("Salário Base: R$" + salarioBase);
    }
    
    // Parte que varia entre subclasses
    public abstract double calcularSalario();
}
```

#### ✅ Use Interfaces quando:

1. Diferentes classes não relacionadas podem implementar a mesma interface
2. Você precisa especificar o comportamento de um tipo particular, sem se preocupar com quem o implementa
3. Deseja aproveitar a vantagem da "herança múltipla" de tipo

```java
// Exemplo de uso adequado de interface
public interface Pagavel {
    double calcularValorAPagar();
}

// Classes não relacionadas podem implementar a mesma interface
public class Fatura implements Pagavel {
    private String numeroFatura;
    private double valorTotal;
    
    @Override
    public double calcularValorAPagar() {
        return valorTotal;
    }
}

public class Freelancer implements Pagavel {
    private String nome;
    private double valorHora;
    private int horasTrabalhadas;
    
    @Override
    public double calcularValorAPagar() {
        return valorHora * horasTrabalhadas;
    }
}
```

### 🌟 Combinando Classes Abstratas e Interfaces

Em muitos casos, as melhores soluções utilizam ambos os conceitos:

```java
// Interface define o contrato
public interface Autenticavel {
    boolean autenticar(String senha);
}

// Classe abstrata com funcionalidade comum
public abstract class Pessoa {
    protected String nome;
    protected String cpf;
    
    public Pessoa(String nome, String cpf) {
        this.nome = nome;
        this.cpf = cpf;
    }
    
    public String getNome() {
        return nome;
    }
    
    public abstract void exibirDetalhes();
}

// Combinando ambos
public class Funcionario extends Pessoa implements Autenticavel {
    private String senha;
    private double salario;
    
    public Funcionario(String nome, String cpf, double salario, String senha) {
        super(nome, cpf);
        this.salario = salario;
        this.senha = senha;
    }
    
    @Override
    public void exibirDetalhes() {
        System.out.println("Funcionário: " + nome);
        System.out.println("CPF: " + cpf);
        System.out.println("Salário: R$" + salario);
    }
    
    @Override
    public boolean autenticar(String senha) {
        return this.senha.equals(senha);
    }
}

// Outra implementação não relacionada
public class Cliente extends Pessoa implements Autenticavel {
    private String senha;
    private double limiteCredito;
    
    // Construtor e outros métodos...
    
    @Override
    public void exibirDetalhes() {
        System.out.println("Cliente: " + nome);
        System.out.println("CPF: " + cpf);
        System.out.println("Limite de Crédito: R$" + limiteCredito);
    }
    
    @Override
    public boolean autenticar(String senha) {
        return this.senha.equals(senha);
    }
}
```

### 🚀 Padrões de Design com Classes Abstratas e Interfaces

#### 🏭 Template Method Pattern

Utiliza classes abstratas para definir o esqueleto de um algoritmo:

```java
// Classe abstrata com o método template
public abstract class ProcessadorDocumento {
    // Método template - define o algoritmo
    public final void processarDocumento(String documento) {
        abrir(documento);
        String conteudo = ler(documento);
        String processado = processar(conteudo);
        salvar(processado);
        fechar();
    }
    
    // Métodos abstratos a serem implementados pelas subclasses
    protected abstract String ler(String documento);
    protected abstract String processar(String conteudo);
    protected abstract void salvar(String conteudo);
    
    // Métodos concretos (hooks)
    protected void abrir(String documento) {
        System.out.println("Abrindo documento: " + documento);
    }
    
    protected void fechar() {
        System.out.println("Fechando documento");
    }
}

// Implementação concreta
public class ProcessadorPDF extends ProcessadorDocumento {
    @Override
    protected String ler(String documento) {
        System.out.println("Lendo PDF: " + documento);
        return "Conteúdo do PDF";
    }
    
    @Override
    protected String processar(String conteudo) {
        return conteudo.toUpperCase();
    }
    
    @Override
    protected void salvar(String conteudo) {
        System.out.println("Salvando PDF processado: " + conteudo);
    }
}
```

#### 🎯 Strategy Pattern

Utiliza interfaces para definir uma família de algoritmos:

```java
// Interface Strategy
public interface EstrategiaOrdenacao {
    void ordenar(int[] dados);
}

// Implementações concretas
public class OrdenacaoBubbleSort implements EstrategiaOrdenacao {
    @Override
    public void ordenar(int[] dados) {
        System.out.println("Ordenando com Bubble Sort");
        // Implementação do Bubble Sort
    }
}

public class OrdenacaoQuickSort implements EstrategiaOrdenacao {
    @Override
    public void ordenar(int[] dados) {
        System.out.println("Ordenando com QuickSort");
        // Implementação do QuickSort
    }
}

// Contexto
public class Ordenador {
    private EstrategiaOrdenacao estrategia;
    
    public void setEstrategia(EstrategiaOrdenacao estrategia) {
        this.estrategia = estrategia;
    }
    
    public void ordenarDados(int[] dados) {
        estrategia.ordenar(dados);
    }
}

// Uso
Ordenador ordenador = new Ordenador();
ordenador.setEstrategia(new OrdenacaoBubbleSort());
ordenador.ordenarDados(new int[]{5, 2, 9, 1, 5});

// Mudando estratégia
ordenador.setEstrategia(new OrdenacaoQuickSort());
ordenador.ordenarDados(new int[]{5, 2, 9, 1, 5});
```

### 🧠 Boas Práticas

#### ✅ O que fazer

1. **Prefira interfaces para definir tipos**
   ```java
   // Bom: programando para a interface
   public void processar(List<String> items) {
       // Qualquer implementação de List funcionará
   }
   ```

2. **Use classes abstratas quando há código compartilhado**
   ```java
   public abstract class Validador {
       // Código comum a todos os validadores
       protected void registrarErro(String erro) {
           System.err.println("Erro: " + erro);
       }
       
       // Parte que varia
       public abstract boolean validar(Object obj);
   }
   ```

3. **Faça interfaces focadas e coesas**
   ```java
   // Bom: interface focada
   public interface Enviavel {
       void enviar(String destino);
   }
   
   // Separando responsabilidades
   public interface Formatavel {
       String formatar();
   }
   ```

4. **Utilize métodos default para evolução de APIs**
   ```java
   public interface Repositorio<T> {
       void salvar(T entidade);
       T buscarPorId(long id);
       
       // Método default adicionado posteriormente
       default List<T> buscarTodos() {
           // Implementação padrão simples
           throw new UnsupportedOperationException("Operação não suportada");
       }
   }
   ```

#### ❌ O que evitar

1. **Interfaces sobrecarregadas com muitos métodos**
   ```java
   // Ruim: Interface com muitas responsabilidades
   public interface SistemaArquivos {
       void criarArquivo(String nome);
       void lerArquivo(String nome);
       void editarArquivo(String nome, String conteudo);
       void excluirArquivo(String nome);
       void listarArquivos();
       void compactarArquivo(String nome);
       void criptografarArquivo(String nome);
       void enviarArquivo(String nome, String destino);
       // ...
   }
   ```

2. **Classes abstratas com métodos concretos mas sem campos**
   ```java
   // Questionável: Poderia ser uma interface com métodos default
   public abstract class Utilitario {
       public void metodoUtil1() { /* ... */ }
       public void metodoUtil2() { /* ... */ }
       // Nenhum campo ou método abstrato
   }
   ```

3. **Depender de comportamentos específicos de implementação**
   ```java
   // Problemático: Forçando ordem de execução específica
   public void processar(List<String> lista) {
       // Depende da ordem de iteração da implementação específica
       // (LinkedList vs ArrayList têm comportamentos diferentes)
   }
   ```

4. **Herança profunda de classes abstratas**
   ```java
   // Problemático: Hierarquia muito profunda
   abstract class A { /* ... */ }
   abstract class B extends A { /* ... */ }
   abstract class C extends B { /* ... */ }
   abstract class D extends C { /* ... */ }
   class E extends D { /* ... */ }
   ```

### 📋 Exemplo Completo: Sistema de Pagamentos

```java
// Interface base
public interface Pagavel {
    double getValor();
    String getDescricao();
}

// Classe abstrata base para funcionários
public abstract class Funcionario implements Pagavel {
    protected String nome;
    protected String cpf;
    
    public Funcionario(String nome, String cpf) {
        this.nome = nome;
        this.cpf = cpf;
    }
    
    public String getNome() {
        return nome;
    }
    
    public String getCpf() {
        return cpf;
    }
    
    @Override
    public String getDescricao() {
        return "Pagamento para funcionário: " + nome;
    }
    
    // Cada tipo de funcionário implementará seu próprio cálculo
    @Override
    public abstract double getValor();
}

// Implementações concretas de funcionários
public class FuncionarioHorista extends Funcionario {
    private double valorHora;
    private double horasTrabalhadas;
    
    public FuncionarioHorista(String nome, String cpf, double valorHora) {
        super(nome, cpf);
        this.valorHora = valorHora;
    }
    
    public void registrarHoras(double horas) {
        this.horasTrabalhadas = horas;
    }
    
    @Override
    public double getValor() {
        return valorHora * horasTrabalhadas;
    }
}

public class FuncionarioAssalariado extends Funcionario {
    private double salarioMensal;
    
    public FuncionarioAssalariado(String nome, String cpf, double salarioMensal) {
        super(nome, cpf);
        this.salarioMensal = salarioMensal;
    }
    
    @Override
    public double getValor() {
        return salarioMensal;
    }
}

// Outros tipos de pagáveis
public class Fatura implements Pagavel {
    private String numero;
    private String descricao;
    private double valor;
    
    public Fatura(String numero, String descricao, double valor) {
        this.numero = numero;
        this.descricao = descricao;
        this.valor = valor;
    }
    
    @Override
    public double getValor() {
        return valor;
    }
    
    @Override
    public String getDescricao() {
        return "Fatura #" + numero + ": " + descricao;
    }
}

// Sistema de processamento de pagamentos
public class ProcessadorPagamentos {
    public void processarPagamento(Pagavel item) {
        System.out.println("Processando: " + item.getDescricao());
        System.out.println("Valor: R$" + item.getValor());
        System.out.println("Pagamento realizado com sucesso!");
        System.out.println("-----------------------");
    }
}

// Uso do sistema
public class SistemaPagamentos {
    public static void main(String[] args) {
        ProcessadorPagamentos processador = new ProcessadorPagamentos();
        
        // Pagando funcionários
        FuncionarioAssalariado joao = new FuncionarioAssalariado("João Silva", "123.456.789-00", 3000.0);
        FuncionarioHorista maria = new FuncionarioHorista("Maria Santos", "987.654.321-00", 50.0);
        maria.registrarHoras(40);
        
        // Pagando faturas
        Fatura aluguel = new Fatura("F001", "Aluguel mensal", 1200.0);
        Fatura internet = new Fatura("F002", "Serviço de Internet", 120.0);
        
        // Processando diversos tipos de pagáveis
        processador.processarPagamento(joao);
        processador.processarPagamento(maria);
        processador.processarPagamento(aluguel);
        processador.processarPagamento(internet);
    }
}
```

### 📝 Considerações Finais

Classes abstratas e interfaces são ferramentas fundamentais para criar designs orientados a objetos robustos e flexíveis em Java. Cada uma tem seu lugar e propósito, e a combinação inteligente de ambas geralmente leva às melhores soluções.

Ao projetar suas hierarquias de classes:
1. Use interfaces para definir comportamentos que podem ser implementados por classes não relacionadas
2. Use classes abstratas para compartilhar código comum entre classes intimamente relacionadas
3. Mantenha interfaces pequenas e coesas (Princípio da Segregação de Interfaces)
4. Evite hierarquias de herança profundas
5. Privilegie composição sobre herança quando apropriado

Com essas ferramentas, você pode criar sistemas mais modulares, testáveis e fáceis de manter.

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 