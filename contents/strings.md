<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 🔠 Manipulação de Strings

## 📝 Trabalhando com texto em Java

Strings são um dos tipos de dados mais utilizados em qualquer linguagem de programação. Em Java, as strings são representadas pela classe `String` e possuem diversas funcionalidades para manipulação de texto. Este guia apresenta as principais operações e boas práticas para trabalhar com strings.

### 📋 Conceitos fundamentais sobre Strings em Java

#### 🧱 Imutabilidade

Em Java, objetos `String` são **imutáveis**, ou seja, uma vez criados, seu conteúdo não pode ser alterado. Qualquer operação que pareça modificar uma string na verdade cria um novo objeto.

```java
String texto = "Olá";
texto = texto + " Mundo"; // Não modifica o objeto original, cria um novo
```

Esta característica tem implicações importantes para performance e segurança.

#### 🏭 String Pool

Java mantém um "pool de strings" para otimizar o uso de memória, reutilizando strings idênticas:

```java
String s1 = "Java"; // Criada e armazenada no pool
String s2 = "Java"; // Reutiliza a mesma referência do pool
String s3 = new String("Java"); // Força a criação de um novo objeto

System.out.println(s1 == s2); // true - mesma referência
System.out.println(s1 == s3); // false - referências diferentes
System.out.println(s1.equals(s3)); // true - mesmo conteúdo
```

### 🛠️ Criando Strings

Existem várias maneiras de criar strings em Java:

```java
// Literal de string
String texto1 = "Olá, mundo!";

// Usando o construtor
String texto2 = new String("Olá, mundo!");

// A partir de um array de caracteres
char[] letras = {'J', 'a', 'v', 'a'};
String texto3 = new String(letras);

// A partir de outra string
String texto4 = new String(texto1);

// Usando StringBuilder (para construção eficiente)
StringBuilder builder = new StringBuilder();
builder.append("Olá, ").append("mundo").append("!");
String texto5 = builder.toString();
```

### 🔄 Operações básicas com Strings

#### 📏 Comprimento e verificações

```java
String texto = "Programação Java";

// Obtendo o comprimento
int tamanho = texto.length(); // 16

// Verificando se está vazia
boolean vazia = texto.isEmpty(); // false

// Verificando se está em branco (Java 11+)
boolean emBranco = texto.isBlank(); // false (contém caracteres não-brancos)

// String vazia vs String em branco
String vazio = "";
String branco = "   ";
System.out.println(vazio.isEmpty()); // true
System.out.println(branco.isEmpty()); // false
System.out.println(branco.isBlank()); // true (Java 11+)
```

#### 🧮 Comparação de Strings

```java
String s1 = "Java";
String s2 = "java";
String s3 = "Java";

// Comparando igualdade (sensível a maiúsculas/minúsculas)
boolean igual = s1.equals(s2); // false
boolean igualS3 = s1.equals(s3); // true

// Comparando igualdade (ignorando maiúsculas/minúsculas)
boolean igualIgnoreCase = s1.equalsIgnoreCase(s2); // true

// Comparando ordem lexicográfica (útil para ordenação)
int comparacao = s1.compareTo(s2); // negativo (J vem antes de j na tabela ASCII)
int comparacaoIgnoreCase = s1.compareToIgnoreCase(s2); // 0 (iguais ignorando case)
```

#### 🔍 Busca e localização

```java
String texto = "O Java é uma linguagem de programação orientada a objetos";

// Verificando se contém uma substring
boolean contemJava = texto.contains("Java"); // true

// Localização da primeira ocorrência
int indiceJava = texto.indexOf("Java"); // 2
int indicePython = texto.indexOf("Python"); // -1 (não encontrado)

// Localização da última ocorrência
int ultimoIndiceA = texto.lastIndexOf("a"); // 51

// Verificando prefixo e sufixo
boolean comecaCom = texto.startsWith("O Java"); // true
boolean terminaCom = texto.endsWith("objetos"); // true
```

#### ✂️ Extração e manipulação

```java
String texto = "Programação Java é divertida";

// Extraindo uma substring
String sub1 = texto.substring(11); // "Java é divertida"
String sub2 = texto.substring(11, 15); // "Java"

// Dividindo em partes (split)
String[] palavras = texto.split(" ");
// palavras = ["Programação", "Java", "é", "divertida"]

// Juntando com um delimitador (Java 8+)
String[] frutas = {"maçã", "banana", "laranja"};
String listaFrutas = String.join(", ", frutas);
// listaFrutas = "maçã, banana, laranja"

// Substituindo partes do texto
String novoTexto = texto.replace("Java", "Python");
// novoTexto = "Programação Python é divertida"

// Substituindo com expressão regular
String numeros = "1a2b3c";
String apenasNumeros = numeros.replaceAll("[^0-9]", "");
// apenasNumeros = "123"
```

#### 🔄 Transformações

```java
String texto = "  Java Programming  ";

// Convertendo para minúsculas/maiúsculas
String minusculas = texto.toLowerCase(); // "  java programming  "
String maiusculas = texto.toUpperCase(); // "  JAVA PROGRAMMING  "

// Removendo espaços em branco do início e fim
String semEspacos = texto.trim(); // "Java Programming"

// Removendo espaços à esquerda (Java 11+)
String semEsquerdaEspacos = texto.stripLeading(); // "Java Programming  "

// Removendo espaços à direita (Java 11+)
String semDireitaEspacos = texto.stripTrailing(); // "  Java Programming"

// Removendo todos os espaços (Java 11+)
String semTodosEspacos = texto.strip(); // "Java Programming"

// Repetindo string (Java 11+)
String repetida = "Java ".repeat(3); // "Java Java Java "
```

### 🧵 StringBuilder e StringBuffer

Para concatenar ou modificar strings de forma eficiente, use `StringBuilder` (não thread-safe) ou `StringBuffer` (thread-safe):

```java
// Concatenação ineficiente com String
String resultado = "";
for (int i = 0; i < 1000; i++) {
    resultado += i; // Cria 1000 objetos String temporários
}

// Concatenação eficiente com StringBuilder
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i); // Modifica o mesmo objeto StringBuilder
}
String resultadoEficiente = sb.toString();
```

#### 📊 Principais métodos de StringBuilder

```java
StringBuilder sb = new StringBuilder("Java");

// Adicionando no final
sb.append(" é"); // "Java é"
sb.append(" poderoso"); // "Java é poderoso"

// Inserindo em posição específica
sb.insert(7, " muito"); // "Java é muito poderoso"

// Excluindo parte da string
sb.delete(7, 13); // "Java é poderoso" (remove " muito")

// Substituindo parte da string
sb.replace(0, 4, "Python"); // "Python é poderoso"

// Revertendo a string
sb.reverse(); // "osoredop é nohtyP"

// Definindo tamanho
sb.setLength(7); // "osoredo" (trunca para 7 caracteres)

// Obtendo o resultado final
String resultado = sb.toString();
```

#### 🔄 StringBuilder vs StringBuffer

| Característica | StringBuilder | StringBuffer |
|----------------|---------------|--------------|
| Thread-safety  | Não           | Sim          |
| Performance    | Mais rápido   | Mais lento   |
| Sincronização  | Não           | Sim          |
| Caso de uso    | Single-thread | Multi-thread |

```java
// Use StringBuilder em código single-thread
StringBuilder sb = new StringBuilder();

// Use StringBuffer em código multi-thread
StringBuffer sbf = new StringBuffer();
```

### 🌐 Internacionalização e codificação

#### 🌍 Caracteres Unicode e codificação

Java usa UTF-16 para representação interna de strings, suportando caracteres de todos os idiomas:

```java
// Strings com caracteres especiais e Unicode
String português = "Olá, Bom dia! Café?";
String japonês = "こんにちは";
String emoji = "😊 👋 🚀";

// Obtendo valores Unicode
char c = português.charAt(0); // 'O'
int unicodeValue = (int) c; // 79

// Representação explícita de Unicode
String omega = "\u03A9"; // "Ω" (letra grega ômega)
```

#### 🧰 Formatação de strings

```java
// Usando String.format (similar a printf)
String formatado = String.format("Nome: %s, Idade: %d, Altura: %.2f", 
                                "João", 30, 1.75);
// formatado = "Nome: João, Idade: 30, Altura: 1,75"

// Formatação de números
String numero = String.format("%,d", 1000000); // "1.000.000" (separador de milhar)
String porcentagem = String.format("%.2f%%", 42.123); // "42,12%" (2 casas decimais)
String alinhado = String.format("%-10s|%10s", "Esquerda", "Direita");
// alinhado = "Esquerda   |    Direita"

// Formatação de datas (com java.time)
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

LocalDate hoje = LocalDate.now();
String dataFormatada = hoje.format(DateTimeFormatter.ofPattern("dd/MM/yyyy"));
// Ex: "21/10/2023"
```

### 🔍 Expressões Regulares com Strings

Java permite usar expressões regulares (regex) para processamento avançado de texto:

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

String texto = "Contato: (11) 98765-4321 ou email: joao@exemplo.com";

// Verificando se corresponde a um padrão
boolean isCelular = texto.matches(".*\\(\\d{2}\\)\\s\\d{5}-\\d{4}.*"); // true

// Encontrando todas as ocorrências
Pattern padrao = Pattern.compile("\\w+@\\w+\\.\\w+");
Matcher matcher = padrao.matcher(texto);

while (matcher.find()) {
    System.out.println("Email encontrado: " + matcher.group());
    // Saída: "Email encontrado: joao@exemplo.com"
}

// Substituindo com regex
String textoLimpo = texto.replaceAll("[^a-zA-Z0-9 ]", "");
// textoLimpo = "Contato 11 987654321 ou email joaoexemplocom"
```

### 💡 Recursos modernos (Java 11+)

Java 11 e versões posteriores introduziram novas funcionalidades para strings:

```java
// Java 11: repeat
String estrelas = "*".repeat(5); // "*****"

// Java 11: isBlank
boolean estaBranco = "   ".isBlank(); // true

// Java 11: strip, stripLeading, stripTrailing
String textoComEspacos = "  olá  ";
String textoSemEspacos = textoComEspacos.strip(); // "olá"

// Java 11: lines (divide em linhas)
String multilinhas = "Linha 1\nLinha 2\nLinha 3";
multilinhas.lines().forEach(System.out::println);

// Java 12: indent (adiciona indentação)
String textoIndentado = "Java".indent(4); // "    Java"

// Java 12: transform (aplica função personalizada)
String texto = "42";
Integer numero = texto.transform(Integer::parseInt); // 42
```

### 📊 Boas práticas e otimização

#### ⚠️ Evitando problemas comuns

1. **Concatenação em loops**:
   ```java
   // Ruim - cria muitos objetos intermediários
   String resultado = "";
   for (int i = 0; i < 1000; i++) {
       resultado += i;
   }
   
   // Bom - usa StringBuilder
   StringBuilder sb = new StringBuilder();
   for (int i = 0; i < 1000; i++) {
       sb.append(i);
   }
   String resultado = sb.toString();
   ```

2. **Comparação incorreta de strings**:
   ```java
   // Ruim - compara referências, não conteúdo
   if (str1 == str2) {...}
   
   // Bom - compara conteúdo
   if (str1.equals(str2)) {...}
   
   // Seguro contra null
   if (Objects.equals(str1, str2)) {...}
   ```

3. **NullPointerException**:
   ```java
   // Perigoso - pode causar NullPointerException
   if (minhaString.equals("valor")) {...}
   
   // Seguro - evita NullPointerException
   if ("valor".equals(minhaString)) {...}
   // ou
   if (Objects.equals(minhaString, "valor")) {...}
   ```

#### 🚀 Dicas de performance

1. **Use `StringBuilder` para múltiplas concatenações**
2. **Pré-dimensione StringBuilder quando souber o tamanho aproximado**:
   ```java
   StringBuilder sb = new StringBuilder(1000); // Capacidade inicial de 1000 chars
   ```
3. **Reutilize objetos `Pattern` para expressões regulares repetidas**:
   ```java
   // Compile o Pattern uma vez, use-o várias vezes
   private static final Pattern EMAIL_PATTERN = 
       Pattern.compile("\\w+@\\w+\\.\\w+");
   ```
4. **Evite operações desnecessárias em strings grandes**
5. **Use o método adequado**: 
   - `equals()` para comparação exata
   - `equalsIgnoreCase()` para comparar ignorando maiúsculas/minúsculas
   - `startsWith()/endsWith()` em vez de substring + equals

#### 🧪 Exemplo prático: Validador de CPF

Combinando vários conceitos de manipulação de strings:

```java
public class ValidadorCPF {
    public static boolean validarCPF(String cpf) {
        // Remover caracteres não numéricos
        cpf = cpf.replaceAll("[^0-9]", "");
        
        // Verificar tamanho
        if (cpf.length() != 11) {
            return false;
        }
        
        // Verificar se todos os dígitos são iguais
        if (cpf.matches("(\\d)\\1{10}")) {
            return false;
        }
        
        // Cálculo do primeiro dígito verificador
        int soma = 0;
        for (int i = 0; i < 9; i++) {
            soma += Character.getNumericValue(cpf.charAt(i)) * (10 - i);
        }
        int resto = 11 - (soma % 11);
        int digitoVerificador1 = (resto > 9) ? 0 : resto;
        
        // Verificar primeiro dígito
        if (digitoVerificador1 != Character.getNumericValue(cpf.charAt(9))) {
            return false;
        }
        
        // Cálculo do segundo dígito verificador
        soma = 0;
        for (int i = 0; i < 10; i++) {
            soma += Character.getNumericValue(cpf.charAt(i)) * (11 - i);
        }
        resto = 11 - (soma % 11);
        int digitoVerificador2 = (resto > 9) ? 0 : resto;
        
        // Verificar segundo dígito
        return digitoVerificador2 == Character.getNumericValue(cpf.charAt(10));
    }
    
    public static void main(String[] args) {
        String cpf = "123.456.789-09";
        System.out.println("CPF válido? " + validarCPF(cpf));
    }
}
```

### 📋 Resumo de métodos essenciais da classe String

| Método | Descrição | Exemplo |
|--------|-----------|---------|
| `length()` | Retorna o tamanho da string | `"Java".length()` → 4 |
| `charAt(int)` | Retorna o caractere na posição especificada | `"Java".charAt(0)` → 'J' |
| `substring(int)` | Extrai uma substring a partir de um índice | `"Java".substring(1)` → "ava" |
| `substring(int, int)` | Extrai uma substring entre dois índices | `"Java".substring(0, 2)` → "Ja" |
| `equals(Object)` | Compara conteúdo com outra string | `"Java".equals("java")` → false |
| `equalsIgnoreCase(String)` | Compara ignorando maiúsculas/minúsculas | `"Java".equalsIgnoreCase("java")` → true |
| `startsWith(String)` | Verifica se começa com o prefixo | `"Java".startsWith("Ja")` → true |
| `endsWith(String)` | Verifica se termina com o sufixo | `"Java".endsWith("va")` → true |
| `indexOf(String)` | Retorna a posição da primeira ocorrência | `"Java".indexOf("a")` → 1 |
| `lastIndexOf(String)` | Retorna a posição da última ocorrência | `"Java".lastIndexOf("a")` → 3 |
| `contains(CharSequence)` | Verifica se contém a substring | `"Java".contains("av")` → true |
| `replace(char, char)` | Substitui caracteres | `"Java".replace('a', 'o')` → "Jovo" |
| `replace(String, String)` | Substitui substrings | `"Java".replace("Ja", "La")` → "Lava" |
| `toLowerCase()` | Converte para minúsculas | `"Java".toLowerCase()` → "java" |
| `toUpperCase()` | Converte para maiúsculas | `"Java".toUpperCase()` → "JAVA" |
| `trim()` | Remove espaços do início e fim | `"  Java  ".trim()` → "Java" |
| `strip()` | Remove espaços Unicode do início e fim | `"  Java  ".strip()` → "Java" |
| `split(String)` | Divide a string usando um delimitador | `"a,b,c".split(",")` → ["a", "b", "c"] |
| `join(String, CharSequence...)` | Une strings com delimitador | `String.join("-", "a", "b", "c")` → "a-b-c" |
| `isEmpty()` | Verifica se a string está vazia | `"".isEmpty()` → true |
| `isBlank()` | Verifica se está vazia ou só tem espaços | `"  ".isBlank()` → true |
| `format(String, Object...)` | Formata texto com placeholders | `String.format("Nome: %s", "Ana")` → "Nome: Ana" |
| `matches(String)` | Verifica se corresponde a um padrão regex | `"123".matches("\\d+")` → true |
| `repeat(int)` | Repete a string n vezes | `"abc".repeat(2)` → "abcabc" |
| `intern()` | Retorna a versão canônica da string | `str.intern()` |

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 