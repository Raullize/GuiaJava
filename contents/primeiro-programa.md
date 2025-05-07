<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# 📄 Criando seu primeiro programa Java

## 🚀 Dando os primeiros passos na programação Java

Este guia irá ajudá-lo a criar, compilar e executar seu primeiro programa em Java, começando do zero e explicando cada passo do processo.

### 📝 O tradicional "Hello, World!"

Tradicionalmente, o primeiro programa que se aprende em qualquer linguagem de programação é o "Hello, World!" - um programa simples que exibe a mensagem "Olá, Mundo!" na tela.

#### ✏️ Criando o arquivo de código fonte

1. **Abra seu editor de texto ou IDE preferido**
2. **Crie um novo arquivo chamado `HelloWorld.java`**
3. **Digite o seguinte código:**

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Olá, Mundo!");
    }
}
```

#### 📋 Entendendo o código

Vamos analisar linha por linha o que este código faz:

| Código | Explicação |
|--------|------------|
| `public class HelloWorld {` | Define uma classe pública chamada HelloWorld. Em Java, o nome do arquivo deve corresponder ao nome da classe pública. |
| `public static void main(String[] args) {` | Define o método `main`, ponto de entrada de qualquer aplicação Java. Este método é invocado pela JVM quando o programa é executado. |
| `System.out.println("Olá, Mundo!");` | Imprime a string "Olá, Mundo!" no console padrão do sistema, seguida por uma nova linha. |
| `}` | Fecha o bloco do método main. |
| `}` | Fecha o bloco da classe HelloWorld. |

### 🔄 Compilando e executando o programa

#### 🔨 Utilizando o prompt de comando (sem IDE)

1. **Abra o terminal ou prompt de comando**
2. **Navegue até o diretório onde você salvou o arquivo HelloWorld.java:**
   ```bash
   cd caminho/para/seu/diretorio
   ```
3. **Compile o código fonte com o comando javac:**
   ```bash
   javac HelloWorld.java
   ```
   - Este comando cria um arquivo `HelloWorld.class` que contém o bytecode Java
   - Se não aparecer nenhuma mensagem, a compilação foi bem-sucedida
   
4. **Execute o programa com o comando java:**
   ```bash
   java HelloWorld
   ```

5. **Você deverá ver a saída:**
   ```
   Olá, Mundo!
   ```

#### 🧩 Utilizando uma IDE

**No IntelliJ IDEA:**
1. Abra o IntelliJ IDEA
2. Crie um novo projeto Java
3. Clique com o botão direito no diretório src > New > Java Class
4. Nomeie a classe como "HelloWorld"
5. Adicione o método main e o código System.out.println
6. Clique no botão de execução (ícone ▶️) ou use o atalho Shift+F10

**No Eclipse:**
1. Abra o Eclipse
2. Crie um novo projeto Java
3. Clique com o botão direito no diretório src > New > Class
4. Nomeie a classe como "HelloWorld" e marque a opção "public static void main()"
5. Adicione o código System.out.println
6. Clique com o botão direito no arquivo > Run As > Java Application

**No VS Code:**
1. Abra a pasta do projeto no VS Code
2. Crie um novo arquivo HelloWorld.java
3. Digite o código completo
4. Com a extensão Java instalada, clique no botão "Run" acima do método main ou use o atalho F5

### 🧠 Conceitos fundamentais

#### 📦 Classes em Java

Em Java, tudo está contido em classes. Uma classe é uma estrutura que encapsula dados (atributos) e comportamentos (métodos). No nosso exemplo:

- A classe `HelloWorld` é apenas um contêiner para o método `main`
- Em programas reais, classes representam objetos ou conceitos do mundo real

#### 🎯 Método main

O método `main` é especial em Java:

- É o ponto de entrada para aplicações Java
- Deve ter a assinatura exata: `public static void main(String[] args)`
- `public`: visível para a JVM
- `static`: pertence à classe, não a uma instância (objeto)
- `void`: não retorna valor
- `String[] args`: aceita argumentos da linha de comando como um array de strings

#### 🖨️ System.out.println

Este método é usado para exibir informações no console:

- `System`: é uma classe que representa o sistema
- `out`: é um objeto de saída padrão (standard output)
- `println`: é um método que imprime texto e adiciona uma nova linha ao final

### 🔄 Modificando seu programa

Vamos experimentar algumas modificações para aprender mais:

#### 📊 Usando variáveis

```java
public class HelloWorld {
    public static void main(String[] args) {
        String mensagem = "Olá, Mundo!";
        System.out.println(mensagem);
        
        String nome = "Java";
        System.out.println("Programando em " + nome);
    }
}
```

#### 🧮 Realizando operações simples

```java
public class HelloWorld {
    public static void main(String[] args) {
        int a = 5;
        int b = 3;
        int soma = a + b;
        
        System.out.println("A soma de " + a + " e " + b + " é " + soma);
    }
}
```

#### 📥 Aceitando entrada do usuário

Para este exemplo, precisamos usar a classe Scanner:

```java
import java.util.Scanner;

public class HelloWorld {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Digite seu nome: ");
        String nome = scanner.nextLine();
        
        System.out.println("Olá, " + nome + "!");
        
        scanner.close();  // Boa prática: fechar o scanner quando não for mais usado
    }
}
```

### ⚠️ Erros comuns e como evitá-los

| Erro | Causa | Solução |
|------|-------|---------|
| `Error: Could not find or load main class HelloWorld` | A JVM não encontrou a classe | Verifique o nome da classe e se você está no diretório correto |
| `error: class HelloWorld is public, should be declared in a file named HelloWorld.java` | O nome do arquivo não corresponde ao nome da classe pública | Renomeie o arquivo ou a classe para que coincidam |
| `error: ';' expected` | Falta de ponto e vírgula no final de uma instrução | Adicione o ponto e vírgula faltante |
| `error: cannot find symbol` | Tentativa de usar uma variável não declarada | Declare a variável antes de usá-la |
| `error: incompatible types` | Tentativa de atribuir um valor de tipo incompatível | Use o tipo correto ou faça uma conversão adequada |

### 🚀 Próximos passos

Agora que você já criou seu primeiro programa Java, aqui estão algumas sugestões do que explorar em seguida:

1. **Experimente os operadores aritméticos** (adição, subtração, multiplicação, divisão)
2. **Teste diferentes tipos de dados** (inteiros, decimais, caracteres, booleanos)
3. **Experimente estruturas condicionais** (if, else, switch)
4. **Explore loops** (for, while, do-while)
5. **Crie outros métodos além do main** e chame-os

### 💡 Dicas úteis

- **Indentação e formatação**: Mantenha seu código organizado e bem indentado para facilitar a leitura
- **Nomes significativos**: Use nomes claros para variáveis e métodos que indiquem sua finalidade
- **Comentários**: Adicione comentários para explicar partes mais complexas do código
- **Compilar com frequência**: Compile e teste seu código frequentemente para identificar erros cedo
- **Aprenda com os erros**: Os erros de compilação são úteis; leia as mensagens com atenção

### 🎉 Parabéns!

Você acaba de dar o primeiro passo na sua jornada de programação Java! Continue praticando e explorando os conceitos apresentados neste guia.

---

[🔙 Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/> 