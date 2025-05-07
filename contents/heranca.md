<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=180&section=header&text=Herança&fontSize=30&fontColor=fff&animation=twinkling&fontAlignY=35"/>

# 🔄 Herança

A herança é um dos conceitos fundamentais da Programação Orientada a Objetos que permite criar novas classes baseadas em classes existentes, promovendo a reutilização de código e estabelecendo relações entre classes.

## 📌 O que é Herança?

Herança é o mecanismo pelo qual uma classe (subclasse ou classe derivada) adquire propriedades e comportamentos de outra classe (superclasse ou classe base). Isso estabelece uma relação "é um" entre as classes.

## 🌲 Hierarquia de Classes

Em Java, a herança cria uma hierarquia de classes onde:
- **Superclasse**: A classe "pai" que fornece atributos e métodos para ser herdados
- **Subclasse**: A classe "filha" que herda e pode estender ou modificar o comportamento da superclasse

## 📋 Sintaxe da Herança

A herança em Java é implementada usando a palavra-chave `extends`:

```java
// Superclasse
public class Animal {
    private String nome;
    private int idade;
    
    public void comer() {
        System.out.println("Animal comendo...");
    }
    
    public void dormir() {
        System.out.println("Animal dormindo...");
    }
    
    // Getters e setters
    public String getNome() {
        return nome;
    }
    
    public void setNome(String nome) {
        this.nome = nome;
    }
    
    public int getIdade() {
        return idade;
    }
    
    public void setIdade(int idade) {
        this.idade = idade;
    }
}

// Subclasse
public class Cachorro extends Animal {
    private String raca;
    
    public void latir() {
        System.out.println("Au au!");
    }
    
    // Getter e setter específico
    public String getRaca() {
        return raca;
    }
    
    public void setRaca(String raca) {
        this.raca = raca;
    }
}
```

Neste exemplo:
- `Cachorro` herda todos os atributos e métodos de `Animal`
- `Cachorro` adiciona um novo atributo (`raca`) e um novo método (`latir`)
- Um objeto `Cachorro` pode usar métodos como `comer()` e `dormir()` herdados de `Animal`

## 🔑 A Palavra-chave `super`

A palavra-chave `super` é usada para acessar membros da superclasse:

1. **Chamar o construtor da superclasse**:
   ```java
   public Cachorro(String nome, int idade, String raca) {
       super(nome, idade); // Chama o construtor da superclasse Animal
       this.raca = raca;
   }
   ```

2. **Acessar métodos da superclasse**:
   ```java
   @Override
   public void comer() {
       super.comer(); // Chama o método da superclasse
       System.out.println("Cachorro comendo ração");
   }
   ```

## 🔄 Sobrescrita de Métodos (Override)

A sobrescrita permite que uma subclasse forneça uma implementação específica de um método já definido na superclasse:

```java
public class Gato extends Animal {
    @Override
    public void comer() {
        System.out.println("Gato comendo ração para felinos");
    }
}
```

Regras para sobrescrita de métodos:
1. O método na subclasse deve ter a mesma assinatura (nome, parâmetros)
2. O método na subclasse não pode ter visibilidade mais restritiva
3. O método na subclasse não pode declarar exceções mais amplas
4. Use a anotação `@Override` para garantir que está sobrescrevendo corretamente

## 🛑 Classes e Métodos `final`

Para impedir que uma classe seja estendida ou um método seja sobrescrito, use a palavra-chave `final`:

```java
// Classe que não pode ser estendida
public final class ContaEspecial extends Conta {
    // ...
}

// Método que não pode ser sobrescrito
public class Veiculo {
    public final void ligar() {
        System.out.println("Veículo ligado");
    }
}
```

## 👨‍👩‍👧 Herança Múltipla

Java não suporta herança múltipla de classes (uma classe não pode estender mais de uma classe), mas permite uma classe implementar múltiplas interfaces. Isso evita o "problema do diamante" que ocorre em linguagens com herança múltipla.

```java
// Correto: Uma classe estende uma classe e implementa várias interfaces
public class Aluno extends Pessoa implements Estudante, Estagiario {
    // ...
}

// Incorreto: Java não permite isso
// public class AlgumaClasse extends ClasseA, ClasseB {
//     ...
// }
```

## 👑 A Classe `Object`

Em Java, todas as classes herdam automaticamente da classe `Object`. Isso significa que todo objeto possui métodos como:
- `toString()`: Retorna uma representação em string do objeto
- `equals()`: Compara se dois objetos são iguais
- `hashCode()`: Retorna um código hash para o objeto
- `getClass()`: Obtém a classe do objeto em tempo de execução

É comum sobrescrever esses métodos para comportamento personalizado:

```java
public class Produto {
    private String nome;
    private double preco;
    
    // Construtor, getters e setters...
    
    @Override
    public String toString() {
        return "Produto: " + nome + ", Preço: R$" + preco;
    }
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        
        Produto outro = (Produto) obj;
        return Double.compare(outro.preco, preco) == 0 && 
               Objects.equals(nome, outro.nome);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(nome, preco);
    }
}
```

## 🏗️ Construtores e Herança

Quando uma subclasse é instanciada:
1. O construtor da superclasse é chamado primeiro (implícita ou explicitamente)
2. Em seguida, o construtor da subclasse é executado

```java
public class Animal {
    private String nome;
    
    public Animal() {
        System.out.println("Construtor de Animal");
    }
    
    public Animal(String nome) {
        this.nome = nome;
        System.out.println("Animal criado com nome: " + nome);
    }
}

public class Cachorro extends Animal {
    private String raca;
    
    public Cachorro() {
        // Implicitamente chama super()
        System.out.println("Construtor de Cachorro");
    }
    
    public Cachorro(String nome, String raca) {
        super(nome); // Chama o construtor específico da superclasse
        this.raca = raca;
        System.out.println("Cachorro criado com raça: " + raca);
    }
}
```

## 🤔 Quando Usar Herança?

Use herança quando:
- Existe uma clara relação "é um" entre as classes
- A subclasse realmente é um tipo mais específico da superclasse
- A subclasse reutiliza e estende (não apenas substitui) o comportamento da superclasse

Prefira composição à herança quando:
- A relação é mais "tem um" do que "é um"
- Você precisa de maior flexibilidade para mudar comportamentos em tempo de execução
- Você quer reutilizar código sem criar dependências fortes entre classes

## 💼 Boas Práticas

1. **Favoreça composição sobre herança** quando possível
2. **Não crie hierarquias profundas** de herança (mais de 2-3 níveis)
3. **Mantenha a coesão das classes** - cada classe deve ter um propósito claro
4. **Respeite o princípio de substituição de Liskov** - uma subclasse deve poder ser usada onde a superclasse é esperada
5. **Documente as classes e métodos** para facilitar o entendimento da hierarquia

---

[📌 Voltar para o índice](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 