<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=180&section=header&text=Polimorfismo&fontSize=30&fontColor=fff&animation=twinkling&fontAlignY=35"/>

# 🔃 Polimorfismo

O polimorfismo é um dos pilares da programação orientada a objetos que permite que objetos de diferentes classes sejam tratados como objetos de uma classe comum. A palavra "polimorfismo" vem do grego e significa "muitas formas".

## 📌 O que é Polimorfismo?

Polimorfismo é a capacidade de um objeto assumir "muitas formas" e se comportar de maneira diferente dependendo do contexto. Em Java, isso significa que:

- Uma referência a uma superclasse pode apontar para um objeto de uma subclasse
- Um método pode ter comportamentos diferentes dependendo do tipo real do objeto que o invoca

## 🔄 Tipos de Polimorfismo em Java

### 1. Polimorfismo de Sobrecarga (Compile-time/Estático)

Ocorre quando vários métodos com o mesmo nome, mas parâmetros diferentes, existem na mesma classe:

```java
public class Calculadora {
    // Sobrecarga de métodos - mesmo nome, diferentes parâmetros
    public int somar(int a, int b) {
        return a + b;
    }
    
    public double somar(double a, double b) {
        return a + b;
    }
    
    public int somar(int a, int b, int c) {
        return a + b + c;
    }
}
```

O compilador decide qual método chamar com base nos argumentos fornecidos.

### 2. Polimorfismo de Sobreposição (Runtime/Dinâmico)

Ocorre quando uma subclasse implementa um método com a mesma assinatura de um método na superclasse:

```java
// Superclasse
public class Animal {
    public void emitirSom() {
        System.out.println("Animal fazendo som");
    }
}

// Subclasses que sobrepõem o método
public class Cachorro extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Au au!");
    }
}

public class Gato extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Miau!");
    }
}
```

Em tempo de execução, Java determina qual versão do método chamar com base no tipo real do objeto.

## 💡 Utilizando Polimorfismo

### Referência de Superclasse

Uma variável do tipo da superclasse pode referenciar um objeto de qualquer subclasse:

```java
Animal animal1 = new Cachorro(); // Um Cachorro é um Animal
Animal animal2 = new Gato();     // Um Gato é um Animal

animal1.emitirSom(); // Saída: "Au au!"
animal2.emitirSom(); // Saída: "Miau!"
```

### Arrays e Coleções Polimórficas

Podemos criar estruturas contendo diferentes objetos que compartilham uma superclasse comum:

```java
// Array com diferentes tipos de animais
Animal[] animais = new Animal[3];
animais[0] = new Cachorro();
animais[1] = new Gato();
animais[2] = new Animal();

// Chamando o mesmo método em todos
for (Animal animal : animais) {
    animal.emitirSom(); // Cada um responde de acordo com seu tipo real
}
```

### Métodos com Parâmetros Polimórficos

Métodos podem aceitar parâmetros do tipo da superclasse, permitindo flexibilidade:

```java
public class Veterinario {
    // Este método aceita qualquer Animal
    public void examinar(Animal animal) {
        System.out.println("Examinando o animal...");
        animal.emitirSom(); // Comportamento específico do tipo real
    }
}

// Uso
Veterinario vet = new Veterinario();
vet.examinar(new Cachorro()); // Funciona para Cachorro
vet.examinar(new Gato());     // Funciona para Gato
```

## 🔍 Typecasting e Instanceof

Quando trabalhamos com polimorfismo, às vezes precisamos acessar métodos específicos da subclasse:

```java
Animal animal = new Cachorro();
animal.emitirSom(); // Método polimórfico funciona bem

// Mas se quisermos chamar um método específico de Cachorro:
// animal.latir(); // Erro de compilação! Animal não tem método latir()

// Precisamos fazer typecast (conversão de tipos)
if (animal instanceof Cachorro) {
    Cachorro cachorro = (Cachorro) animal; // Typecast
    cachorro.latir(); // Agora funciona!
}
```

### Operador `instanceof`

O operador `instanceof` verifica se um objeto é instância de determinada classe:

```java
public void tratarAnimal(Animal animal) {
    if (animal instanceof Cachorro) {
        System.out.println("É um cachorro");
        Cachorro c = (Cachorro) animal;
        c.latir();
    } else if (animal instanceof Gato) {
        System.out.println("É um gato");
        Gato g = (Gato) animal;
        g.arranhar();
    }
}
```

A partir do Java 16, podemos usar Pattern Matching com `instanceof`:

```java
if (animal instanceof Cachorro cachorro) {
    // A variável 'cachorro' já está disponível aqui
    cachorro.latir();
}
```

## 🌟 Polimorfismo com Interfaces

Interfaces são outra forma poderosa de implementar polimorfismo em Java:

```java
// Interface define um contrato
public interface Voador {
    void voar();
}

// Classes que implementam a interface
public class Passaro extends Animal implements Voador {
    @Override
    public void voar() {
        System.out.println("Pássaro voando com asas");
    }
}

public class Aviao implements Voador {
    @Override
    public void voar() {
        System.out.println("Avião voando com motor");
    }
}

// Usando polimorfismo através da interface
public void fazerVoar(Voador voador) {
    voador.voar(); // Chama o método apropriado dependendo do tipo real
}

// Uso
fazerVoar(new Passaro()); // "Pássaro voando com asas"
fazerVoar(new Aviao());   // "Avião voando com motor"
```

Este é um exemplo poderoso de polimorfismo, pois objetos de classes completamente diferentes podem ser tratados de forma uniforme.

## 🧩 Benefícios do Polimorfismo

1. **Flexibilidade**: Permite que sistemas facilmente acomodem novos tipos
2. **Extensibilidade**: Facilita a adição de novas subclasses sem modificar código existente
3. **Reutilização de código**: Evita duplicação, centralizando comportamento comum
4. **Acoplamento reduzido**: Código cliente depende de abstrações, não de implementações específicas
5. **Melhor manutenção**: Mudanças em subclasses não afetam interfaces comuns

## 🚫 Limitações e Cuidados

1. **Complexidade**: Sistemas polimórficos podem ser mais difíceis de entender
2. **Overhead**: Em alguns casos, chamadas de métodos polimórficos podem ser ligeiramente mais lentas
3. **Erros de cast**: Typecasting incorreto pode causar `ClassCastException`
4. **Comportamento inesperado**: Se mal implementado, pode levar a resultados surpresa

## 💼 Boas Práticas

1. **Princípio de Substituição de Liskov**: Subclasses devem poder ser usadas onde a superclasse é esperada sem alterar o comportamento esperado
2. **Favoreça interfaces**: Use interfaces para definir contratos quando for apropriado
3. **Minimize typecasting**: Se você precisa fazer muitos typecasts, talvez seu design precise ser revisado
4. **Verifique com instanceof**: Sempre verifique antes de fazer typecast
5. **Nomes descritivos**: Use nomes que descrevam claramente o comportamento esperado dos métodos

---

[📌 Voltar para o índice](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 