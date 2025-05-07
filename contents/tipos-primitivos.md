<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 📝 Tipos de Dados Primitivos

## 🧱 Os blocos fundamentais de construção em Java

Em Java, temos dois tipos principais de dados: **primitivos** e **referência**. Neste artigo, vamos focar nos tipos primitivos, que são os blocos básicos de construção da linguagem.

Java possui 8 tipos primitivos, divididos em 4 categorias:

### 🔢 Tipos Inteiros

| Tipo | Tamanho | Faixa de valores | Exemplo |
|------|---------|------------------|---------|
| `byte` | 8 bits | -128 a 127 | `byte minhaIdade = 30;` |
| `short` | 16 bits | -32.768 a 32.767 | `short populacao = 32000;` |
| `int` | 32 bits | -2³¹ a 2³¹-1 (~2 bilhões) | `int conta = 1000000;` |
| `long` | 64 bits | -2⁶³ a 2⁶³-1 (muito grande) | `long populacaoMundial = 7800000000L;` |

> ⚠️ **Observação**: Para valores `long`, é necessário adicionar o sufixo `L` para números literais maiores que o limite do `int`.

### 💯 Tipos de Ponto Flutuante

| Tipo | Tamanho | Precisão | Exemplo |
|------|---------|----------|---------|
| `float` | 32 bits | 7 dígitos decimais | `float altura = 1.75f;` |
| `double` | 64 bits | 15 dígitos decimais | `double pi = 3.14159265359;` |

> ⚠️ **Observação**: Para valores `float`, é necessário adicionar o sufixo `f` para números literais.

### 🔤 Caractere

| Tipo | Tamanho | Descrição | Exemplo |
|------|---------|-----------|---------|
| `char` | 16 bits | Representa um único caractere Unicode | `char inicial = 'A';` |

### ✅ Booleano

| Tipo | Tamanho | Valores | Exemplo |
|------|---------|---------|---------|
| `boolean` | 1 bit | `true` ou `false` | `boolean ativo = true;` |

## 🎯 Valores Padrão

Quando declarados como variáveis de instância (campos de classe), os tipos primitivos possuem valores padrão:

```java
public class ValoresPadrao {
    static byte b;      // 0
    static short s;     // 0
    static int i;       // 0
    static long l;      // 0L
    static float f;     // 0.0f
    static double d;    // 0.0d
    static char c;      // '\u0000' (caractere nulo)
    static boolean bool; // false
    
    public static void main(String[] args) {
        System.out.println("byte padrão: " + b);
        System.out.println("short padrão: " + s);
        System.out.println("int padrão: " + i);
        System.out.println("long padrão: " + l);
        System.out.println("float padrão: " + f);
        System.out.println("double padrão: " + d);
        System.out.println("char padrão: " + (int)c);
        System.out.println("boolean padrão: " + bool);
    }
}
```

> ⚠️ **Observação**: Variáveis locais (declaradas dentro de métodos) não recebem valores padrão e precisam ser inicializadas antes do uso.

## 💡 Uso do Separador de Dígitos (_)

Java permite o uso do caractere sublinhado (`_`) como separador de dígitos para aumentar a legibilidade de números:

```java
int umMilhao = 1_000_000;      // Mais fácil de ler que 1000000
long cpf = 123_456_789_00L;    // CPF mais legível
double pi = 3.141_592_653_589; // Pi com separadores
```

O separador `_` pode ser colocado entre quaisquer dígitos, mas não pode:
- Estar no início ou final do número
- Estar junto ao ponto decimal
- Estar antes do sufixo `L`, `F` ou `D`

## 🔄 Conversões entre Tipos Primitivos

Java permite dois tipos de conversão entre tipos primitivos:

### 1. Conversão Implícita (Widening)

Quando você converte de um tipo menor para um maior, não há perda de dados:

```java
byte b = 100;
int i = b;    // Conversão implícita de byte para int
float f = i;  // Conversão implícita de int para float
double d = f; // Conversão implícita de float para double
```

**Conversões implícitas permitidas:**
```
byte → short → int → long → float → double
         ↗
char ────
```

### 2. Conversão Explícita (Narrowing/Casting)

Quando você converte de um tipo maior para um menor, pode haver perda de dados:

```java
double d = 100.7;
int i = (int) d;    // Conversão explícita de double para int (i = 100)
byte b = (byte) i;  // Conversão explícita de int para byte
```

## 🔨 Exemplo Prático

Vamos ver um exemplo de como usar os diferentes tipos primitivos em um programa real:

```java
public class CalculadoraIMC {
    public static void main(String[] args) {
        // Usando tipos primitivos
        char sexo = 'M';
        byte idade = 35;
        short peso = 80;
        float altura = 1.75f;
        boolean ativo = true;
        
        // Calculando o IMC (Índice de Massa Corporal)
        double imc = peso / (altura * altura);
        
        System.out.println("Informações do Paciente:");
        System.out.println("Sexo: " + sexo);
        System.out.println("Idade: " + idade + " anos");
        System.out.println("Peso: " + peso + " kg");
        System.out.println("Altura: " + altura + " m");
        System.out.println("Pratica atividades físicas: " + (ativo ? "Sim" : "Não"));
        System.out.println("IMC: " + Math.round(imc * 100) / 100.0);
        
        // Convertendo double para int (casting)
        int imcInteiro = (int) imc;
        System.out.println("IMC arredondado: " + imcInteiro);
    }
}
```

## 🧠 Curiosidades e Boas Práticas

1. **Escolha do tipo correto**: Use o tipo mais apropriado para cada situação:
   - `int` para a maioria dos números inteiros
   - `double` para a maioria dos números com casa decimal
   - `boolean` para condições lógicas

2. **Cuidado com overflow**: Quando um valor excede a capacidade do tipo:
   ```java
   byte b = 127;
   b++;  // b se torna -128 (overflow)
   ```

3. **Precisão de ponto flutuante**: `float` e `double` podem ter problemas de precisão para operações financeiras. Use `BigDecimal` para cálculos monetários:
   ```java
   double a = 0.1;
   double b = 0.2;
   System.out.println(a + b); // Pode mostrar 0.30000000000000004 em vez de 0.3
   ```

4. **Valores literais**: Por padrão, literais inteiros são do tipo `int` e literais de ponto flutuante são do tipo `double`.

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 