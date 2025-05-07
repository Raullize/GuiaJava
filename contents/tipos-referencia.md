<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 🧩 Tipos de referência

## 🔍 Entendendo as estruturas complexas em Java

Além dos tipos primitivos, Java oferece tipos de referência que permitem criar estruturas mais complexas e representar conceitos do mundo real. Este guia explorará os principais tipos de referência em Java e como utilizá-los.

### 📦 O que são tipos de referência?

Em Java, existem dois grandes grupos de tipos de dados:

1. **Tipos primitivos**: `boolean`, `byte`, `char`, `short`, `int`, `long`, `float`, `double`
2. **Tipos de referência**: Classes, Interfaces, Arrays e Enums

A principal diferença é que variáveis de tipos de referência armazenam referências (endereços de memória) para objetos, não os valores em si.

```java
// Tipo primitivo - armazena o valor diretamente
int numero = 42;

// Tipo de referência - armazena a referência para o objeto String
String texto = "Olá, mundo!";
```

### 📚 Classes e Objetos

As classes são os tipos de referência mais comuns em Java. Uma classe é um modelo para criar objetos.

```java
// Definição de uma classe
public class Pessoa {
    // Atributos
    private String nome;
    private int idade;
    
    // Construtor
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
    
    // Métodos
    public void apresentar() {
        System.out.println("Olá, eu sou " + nome + " e tenho " + idade + " anos.");
    }
}

// Criando objetos (instâncias) da classe
Pessoa pessoa1 = new Pessoa("Carlos", 25);
Pessoa pessoa2 = new Pessoa("Ana", 30);

pessoa1.apresentar(); // Saída: Olá, eu sou Carlos e tenho 25 anos.
```

#### 🧠 Comportamento de referência

Como as variáveis de objeto armazenam referências, duas variáveis podem apontar para o mesmo objeto:

```java
Pessoa p1 = new Pessoa("João", 40);
Pessoa p2 = p1; // p2 agora referencia o mesmo objeto que p1

p2.setIdade(41); // Mudando o objeto através de p2
System.out.println(p1.getIdade()); // Saída: 41 (o objeto foi alterado)
```

### 🔄 A classe String

`String` é um tipo de referência especial que representa sequências de caracteres. Strings em Java são imutáveis.

```java
String saudacao = "Olá";
String nome = "Maria";
String mensagem = saudacao + ", " + nome + "!"; // Concatenação

System.out.println(mensagem); // Saída: Olá, Maria!
```

#### 🔤 Métodos importantes da classe String

| Método | Descrição | Exemplo |
|--------|-----------|---------|
| `length()` | Retorna o tamanho da string | `"Java".length()` → 4 |
| `charAt(int index)` | Retorna o caractere na posição especificada | `"Java".charAt(0)` → 'J' |
| `substring(int beginIndex, int endIndex)` | Retorna uma substring | `"JavaProgramming".substring(0, 4)` → "Java" |
| `equals(Object obj)` | Compara conteúdo com outra string | `"Java".equals("java")` → false |
| `equalsIgnoreCase(String str)` | Compara, ignorando maiúsculas/minúsculas | `"Java".equalsIgnoreCase("java")` → true |
| `toUpperCase()` | Converte para maiúsculas | `"Java".toUpperCase()` → "JAVA" |
| `toLowerCase()` | Converte para minúsculas | `"Java".toLowerCase()` → "java" |
| `trim()` | Remove espaços em branco do início e fim | `"  Java  ".trim()` → "Java" |
| `replace(char old, char new)` | Substitui caracteres | `"Java".replace('a', 'o')` → "Jovo" |
| `contains(CharSequence s)` | Verifica se contém uma sequência | `"Java".contains("av")` → true |
| `split(String regex)` | Divide a string com base em um delimitador | `"a,b,c".split(",")` → ["a", "b", "c"] |

### 🧰 Wrappers (Classes Invólucro)

Para cada tipo primitivo, Java fornece uma classe wrapper correspondente:

| Tipo Primitivo | Classe Wrapper |
|----------------|----------------|
| `boolean` | `Boolean` |
| `byte` | `Byte` |
| `char` | `Character` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |

As classes wrapper oferecem utilidades e permitem que tipos primitivos sejam tratados como objetos:

```java
// Conversão de String para int (parsing)
String strNumero = "123";
int numero = Integer.parseInt(strNumero);

// Conversão de int para String
String texto = Integer.toString(42);

// Valores máximos e mínimos
int max = Integer.MAX_VALUE;
int min = Integer.MIN_VALUE;

// Autoboxing (conversão automática de primitivo para wrapper)
Integer num = 100; // int → Integer automaticamente

// Unboxing (conversão automática de wrapper para primitivo)
int valor = num; // Integer → int automaticamente
```

### 📊 Arrays em Java

Arrays são tipos de referência que armazenam múltiplos valores do mesmo tipo:

```java
// Declaração e inicialização de um array de inteiros
int[] numeros = new int[5]; // Array com 5 posições

// Atribuindo valores
numeros[0] = 10;
numeros[1] = 20;
numeros[2] = 30;
numeros[3] = 40;
numeros[4] = 50;

// Forma alternativa de inicializar
int[] valores = {10, 20, 30, 40, 50};

// Array de objetos
Pessoa[] pessoas = new Pessoa[3];
pessoas[0] = new Pessoa("Ana", 25);
pessoas[1] = new Pessoa("Bruno", 30);
pessoas[2] = new Pessoa("Carlos", 35);
```

### 🌟 Enumerações (Enum)

Enums são tipos especiais de classes que representam conjuntos fixos de constantes:

```java
// Definindo um enum
public enum DiaDaSemana {
    SEGUNDA, TERCA, QUARTA, QUINTA, SEXTA, SABADO, DOMINGO
}

// Usando o enum
DiaDaSemana hoje = DiaDaSemana.QUARTA;

// Enums em estruturas condicionais
switch (hoje) {
    case SEGUNDA:
        System.out.println("Início da semana");
        break;
    case QUARTA:
        System.out.println("Meio da semana");
        break;
    case SEXTA:
        System.out.println("Quase fim de semana");
        break;
    case SABADO:
    case DOMINGO:
        System.out.println("Fim de semana!");
        break;
    default:
        System.out.println("Outro dia");
}

// Enums podem ter atributos e métodos
public enum Estacao {
    PRIMAVERA("Moderada"), 
    VERAO("Quente"), 
    OUTONO("Moderada"), 
    INVERNO("Fria");
    
    private String temperatura;
    
    Estacao(String temperatura) {
        this.temperatura = temperatura;
    }
    
    public String getTemperatura() {
        return temperatura;
    }
}

Estacao estacao = Estacao.VERAO;
System.out.println(estacao.getTemperatura()); // Saída: Quente
```

### 🧾 Interface e Classes Abstratas

Interfaces e classes abstratas são tipos de referência usados para definir contratos e hierarquias de classes:

```java
// Interface - define um contrato
public interface Animal {
    void emitirSom();
    void mover();
}

// Implementando uma interface
public class Cachorro implements Animal {
    @Override
    public void emitirSom() {
        System.out.println("Au au!");
    }
    
    @Override
    public void mover() {
        System.out.println("Correndo com 4 patas");
    }
}

// Classe abstrata - combina implementação e contrato
public abstract class Veiculo {
    private String marca;
    
    public Veiculo(String marca) {
        this.marca = marca;
    }
    
    public String getMarca() {
        return marca;
    }
    
    // Método abstrato (sem implementação)
    public abstract void acelerar();
    
    // Método concreto (com implementação)
    public void buzinar() {
        System.out.println("Beep beep!");
    }
}

// Estendendo uma classe abstrata
public class Carro extends Veiculo {
    public Carro(String marca) {
        super(marca);
    }
    
    @Override
    public void acelerar() {
        System.out.println("Acelerando o carro");
    }
}
```

### 📋 Coleções

Java oferece várias classes de coleção para armazenar e manipular grupos de objetos de maneira mais flexível que arrays:

#### Lista (List)

Sequência ordenada de elementos:

```java
import java.util.ArrayList;
import java.util.List;

List<String> nomes = new ArrayList<>();
nomes.add("Ana");
nomes.add("Bruno");
nomes.add("Carlos");

System.out.println(nomes.get(0)); // Saída: Ana
System.out.println(nomes.size()); // Saída: 3

nomes.remove("Bruno");
System.out.println(nomes); // Saída: [Ana, Carlos]

// Iterando sobre a lista
for (String nome : nomes) {
    System.out.println(nome);
}
```

#### Conjunto (Set)

Coleção de elementos únicos (sem duplicatas):

```java
import java.util.HashSet;
import java.util.Set;

Set<String> cores = new HashSet<>();
cores.add("Vermelho");
cores.add("Verde");
cores.add("Azul");
cores.add("Verde"); // Não será adicionado novamente

System.out.println(cores.size()); // Saída: 3
System.out.println(cores.contains("Verde")); // Saída: true

// Iterando sobre o conjunto
for (String cor : cores) {
    System.out.println(cor);
}
```

#### Mapa (Map)

Armazena pares de chave-valor:

```java
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> idades = new HashMap<>();
idades.put("Ana", 25);
idades.put("Bruno", 30);
idades.put("Carlos", 35);

System.out.println(idades.get("Bruno")); // Saída: 30

// Verificando se contém uma chave
if (idades.containsKey("Ana")) {
    System.out.println("Ana está no mapa");
}

// Iterando sobre o mapa
for (Map.Entry<String, Integer> entrada : idades.entrySet()) {
    System.out.println(entrada.getKey() + ": " + entrada.getValue());
}
```

### 📈 Diferenças importantes entre tipos primitivos e de referência

| Característica | Tipos Primitivos | Tipos de Referência |
|----------------|-----------------|---------------------|
| Armazenamento | Valor direto | Referência ao objeto |
| Tamanho | Tamanho fixo | Tamanho variável |
| Valor padrão | 0, false, \u0000 | null |
| Métodos | Não possuem métodos | Possuem métodos |
| Modificação | Imutáveis após atribuição | Podem ser mutáveis |
| Herança | Não se aplicam conceitos de OO | Suportam herança |
| Performance | Geralmente mais eficientes | Geralmente mais recursos |

### 🔍 Operador instanceof

Para verificar se um objeto é instância de uma classe específica:

```java
Object obj = "Texto de exemplo";

if (obj instanceof String) {
    String texto = (String) obj;
    System.out.println("É uma String: " + texto);
}
```

### 💾 Comparação == vs equals()

- `==` compara referências (se apontam para o mesmo objeto)
- `equals()` compara conteúdo (implementado pelas classes)

```java
String a = new String("texto");
String b = new String("texto");

System.out.println(a == b);      // false (referências diferentes)
System.out.println(a.equals(b)); // true (conteúdo igual)
```

### 🗑️ Garbage Collection

Java gerencia automaticamente a memória através do Garbage Collector:

1. Objetos são criados com `new` no heap
2. Quando não há mais referências a um objeto, ele se torna elegível para coleta
3. O Garbage Collector periodicamente libera a memória ocupada por objetos não referenciados

```java
// Criando um objeto
Pessoa p = new Pessoa("Maria", 30);

// Tornando o objeto elegível para coleta
p = null;  // Remove a referência

// Ou saindo do escopo
public void metodo() {
    Pessoa p = new Pessoa("João", 25);
    // Quando o método termina, p sai de escopo
    // e o objeto pode ser coletado
}
```

### 🚀 Dicas práticas

1. **Use tipos de referência para modelar entidades do mundo real**
2. **Prefira tipos primitivos para valores simples (por eficiência)**
3. **Aproveite as classes do pacote `java.util` para coleções**
4. **Trate referências null para evitar NullPointerException**
5. **Implemente equals() e hashCode() corretamente em suas classes**
6. **Utilize interfaces para aumentar a flexibilidade do código**

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 