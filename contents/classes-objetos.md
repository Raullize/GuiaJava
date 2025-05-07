<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=180&section=header&text=Classes%20e%20Objetos&fontSize=30&fontColor=fff&animation=twinkling&fontAlignY=35"/>

# 📝 Classes e Objetos

As classes e objetos são o coração da programação orientada a objetos em Java. Eles permitem representar elementos do mundo real em seu código de forma estruturada e organizada.

## 🧊 Conceitos Básicos

**Classe**: Um modelo ou blueprint que define as características e comportamentos que seus objetos terão.

**Objeto**: Uma instância concreta de uma classe, com seus próprios valores para os atributos.

A relação é simples: **classes são modelos, objetos são instâncias desses modelos**.

## 📋 Estrutura de uma Classe

Uma classe em Java pode conter:

1. **Atributos**: Variáveis que armazenam os dados
2. **Construtores**: Métodos especiais para criar objetos
3. **Métodos**: Funções que definem comportamentos
4. **Blocos de inicialização**: Código executado quando a classe é carregada ou um objeto é criado
5. **Classes internas**: Classes definidas dentro de outras classes

### Exemplo de Definição de Classe

```java
public class Carro {
    // Atributos (ou variáveis de instância)
    private String marca;
    private String modelo;
    private int ano;
    private double velocidadeAtual;
    
    // Construtor padrão
    public Carro() {
        velocidadeAtual = 0;
    }
    
    // Construtor com parâmetros
    public Carro(String marca, String modelo, int ano) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
        this.velocidadeAtual = 0;
    }
    
    // Métodos
    public void acelerar(double incremento) {
        velocidadeAtual += incremento;
        System.out.println("Acelerando. Velocidade atual: " + velocidadeAtual + " km/h");
    }
    
    public void frear(double decremento) {
        if (velocidadeAtual >= decremento) {
            velocidadeAtual -= decremento;
        } else {
            velocidadeAtual = 0;
        }
        System.out.println("Freando. Velocidade atual: " + velocidadeAtual + " km/h");
    }
    
    // Getters e Setters
    public String getMarca() {
        return marca;
    }
    
    public void setMarca(String marca) {
        this.marca = marca;
    }
    
    // Outros getters e setters...
}
```

## 🚀 Criando e Usando Objetos

Para criar um objeto em Java, usamos o operador `new`:

```java
// Criando um objeto usando o construtor com parâmetros
Carro meuCarro = new Carro("Toyota", "Corolla", 2022);

// Usando os métodos do objeto
meuCarro.acelerar(20);
meuCarro.frear(5);

// Acessando dados do objeto através dos getters
System.out.println("Meu carro é um " + meuCarro.getMarca() + " " + meuCarro.getModelo());
```

## 📊 Tipos de Atributos e Métodos

### Atributos de Instância vs Estáticos

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Atributos de instância** | Pertencem a cada objeto individual | `private String nome;` |
| **Atributos estáticos** | Compartilhados por todos os objetos da classe | `private static int contador;` |

### Métodos de Instância vs Estáticos

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Métodos de instância** | Operam nos dados do objeto | `public void acelerar() {...}` |
| **Métodos estáticos** | Não dependem de nenhum objeto específico | `public static double converterKmParaMilhas(double km) {...}` |

## ⚙️ Construtores

Construtores são métodos especiais que são chamados quando um objeto é criado. Eles têm o mesmo nome da classe e não possuem tipo de retorno.

```java
// Construtor padrão
public Pessoa() {
    this.idade = 0;
}

// Construtor com parâmetros
public Pessoa(String nome, int idade) {
    this.nome = nome;
    this.idade = idade;
}
```

### Sobrecarga de Construtores

Java permite ter múltiplos construtores na mesma classe, desde que tenham assinaturas diferentes:

```java
public class Produto {
    private String nome;
    private double preco;
    private int quantidade;
    
    // Construtor completo
    public Produto(String nome, double preco, int quantidade) {
        this.nome = nome;
        this.preco = preco;
        this.quantidade = quantidade;
    }
    
    // Construtor para produto sem estoque
    public Produto(String nome, double preco) {
        this(nome, preco, 0); // Chama o construtor completo
    }
    
    // Construtor vazio
    public Produto() {
        this("Sem nome", 0.0, 0);
    }
}
```

## 🔄 Ciclo de Vida dos Objetos

O ciclo de vida de um objeto em Java consiste em:

1. **Criação**: Usando o operador `new` e um construtor
2. **Uso**: Acesso a atributos e métodos
3. **Destruição**: Quando não há mais referências ao objeto, ele se torna elegível para o garbage collection

### Garbage Collection

Java possui um coletor de lixo (garbage collector) que libera automaticamente a memória de objetos que não são mais acessíveis. Você não precisa liberar memória manualmente, mas pode sugerir ao garbage collector limpar a memória:

```java
System.gc(); // Apenas uma sugestão, não garante a execução imediata
```

## 🔑 A Palavra-chave `this`

`this` é uma referência ao objeto atual e pode ser usada para:

1. **Distinguir atributos de parâmetros com o mesmo nome**:
   ```java
   public void setNome(String nome) {
       this.nome = nome;
   }
   ```

2. **Chamar outro construtor da mesma classe**:
   ```java
   public Pessoa() {
       this("Desconhecido", 0);
   }
   ```

3. **Passar o objeto atual como argumento para outro método**:
   ```java
   outroObjeto.processar(this);
   ```

## 📋 Boas Práticas

1. **Encapsulamento**: Faça atributos privados e forneça métodos de acesso
2. **Nomes descritivos**: Use nomes significativos para classes, atributos e métodos
3. **Responsabilidade única**: Cada classe deve ter um único propósito
4. **Imutabilidade**: Considere fazer classes imutáveis para objetos cujo estado não deve mudar
5. **Construtores claros**: Defina construtores que facilitam a criação de objetos válidos

---

[📌 Voltar para o índice](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 