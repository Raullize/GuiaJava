<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Entrada de dados

## Capturando informações do usuário em Java

A interação com o usuário é fundamental para criar aplicações dinâmicas. Neste guia, exploraremos as diferentes formas de capturar dados de entrada em Java, desde o uso do console até interfaces gráficas.

### Entrada pelo Console

Java oferece várias maneiras de ler dados do console (linha de comando). Vamos explorar as principais:

#### Usando a classe Scanner

A classe `Scanner` é a forma mais comum e versátil de ler entrada de usuário em Java:

```java
import java.util.Scanner;

public class EntradaScanner {
    public static void main(String[] args) {
        // Criando um objeto Scanner para ler da entrada padrão (teclado)
        Scanner scanner = new Scanner(System.in);
        
        // Solicitando e lendo uma String
        System.out.print("Digite seu nome: ");
        String nome = scanner.nextLine();
        
        // Solicitando e lendo um número inteiro
        System.out.print("Digite sua idade: ");
        int idade = scanner.nextInt();
        scanner.nextLine(); // Consumir o \n que sobrou da entrada anterior
        
        // Solicitando e lendo um número decimal
        System.out.print("Digite sua altura (em metros): ");
        double altura = scanner.nextDouble();
        scanner.nextLine(); // Consumir o \n
        
        // Exibindo os dados lidos
        System.out.println("\nDados informados:");
        System.out.println("Nome: " + nome);
        System.out.println("Idade: " + idade);
        System.out.println("Altura: " + altura + "m");
        
        // Fechando o Scanner (boa prática)
        scanner.close();
    }
}
```

##### Métodos principais do Scanner

| Método | Descrição | Exemplo |
|--------|-----------|---------|
| `nextLine()` | Lê uma linha inteira de texto | `String texto = scanner.nextLine();` |
| `next()` | Lê a próxima palavra (até encontrar espaço) | `String palavra = scanner.next();` |
| `nextInt()` | Lê um número inteiro | `int numero = scanner.nextInt();` |
| `nextDouble()` | Lê um número de ponto flutuante | `double decimal = scanner.nextDouble();` |
| `nextBoolean()` | Lê um valor booleano | `boolean flag = scanner.nextBoolean();` |
| `nextByte()` | Lê um valor byte | `byte b = scanner.nextByte();` |
| `nextLong()` | Lê um valor long | `long l = scanner.nextLong();` |
| `nextFloat()` | Lê um valor float | `float f = scanner.nextFloat();` |
| `hasNext()` | Verifica se há mais tokens | `if (scanner.hasNext()) { ... }` |
| `hasNextInt()` | Verifica se o próximo token é um inteiro | `if (scanner.hasNextInt()) { ... }` |

##### ⚠️ Cuidados com o Scanner

1. **Problema do `nextLine()` após métodos como `nextInt()`**:
   Os métodos como `nextInt()`, `nextDouble()` não consomem o caractere de nova linha (`\n`) após a entrada. Isso faz com que o `nextLine()` subsequente encontre imediatamente esse `\n` e retorne uma string vazia. Para corrigir, adicione um `nextLine()` extra após esses métodos.

2. **Tratamento de exceções**:
   Os métodos de leitura numérica lançam `InputMismatchException` se a entrada não for do tipo esperado.

```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class TratamentoErros {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        try {
            System.out.print("Digite um número inteiro: ");
            int numero = scanner.nextInt();
            System.out.println("Você digitou: " + numero);
        } catch (InputMismatchException e) {
            System.out.println("Erro: O valor digitado não é um número inteiro válido!");
        } finally {
            scanner.close();
        }
    }
}
```

#### Usando BufferedReader

Para leitura mais eficiente de grandes volumes de dados, `BufferedReader` é uma alternativa:

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class EntradaBufferedReader {
    public static void main(String[] args) {
        // Criando o BufferedReader
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        
        try {
            // Lendo uma string
            System.out.print("Digite seu nome: ");
            String nome = reader.readLine();
            
            // Lendo e convertendo para int
            System.out.print("Digite sua idade: ");
            int idade = Integer.parseInt(reader.readLine());
            
            // Lendo e convertendo para double
            System.out.print("Digite sua altura: ");
            double altura = Double.parseDouble(reader.readLine());
            
            // Exibindo os dados
            System.out.println("\nDados informados:");
            System.out.println("Nome: " + nome);
            System.out.println("Idade: " + idade);
            System.out.println("Altura: " + altura + "m");
            
        } catch (IOException e) {
            System.out.println("Erro de entrada/saída: " + e.getMessage());
        } catch (NumberFormatException e) {
            System.out.println("Erro: formato de número inválido!");
        } finally {
            try {
                reader.close();
            } catch (IOException e) {
                System.out.println("Erro ao fechar o leitor: " + e.getMessage());
            }
        }
    }
}
```

#### Scanner vs BufferedReader

| Característica | Scanner | BufferedReader |
|----------------|---------|----------------|
| Facilidade de uso | Mais simples e intuitivo | Requer mais código |
| Performance | Adequada para entradas pequenas | Mais eficiente para grandes volumes |
| Tratamento de tipos | Métodos específicos para cada tipo | Só lê String (precisa converter) |
| Sincronização | Não sincronizado | Sincronizado (thread-safe) |
| Exceções | Checked e unchecked | Checked (IOException) |

#### Classe Console (menos comum)

Disponível desde Java 6, mas não funciona em todos os ambientes (como IDEs):

```java
import java.io.Console;

public class EntradaConsole {
    public static void main(String[] args) {
        Console console = System.console();
        
        // Verificar se console está disponível
        if (console == null) {
            System.err.println("Console não disponível!");
            return;
        }
        
        // Ler uma string
        String nome = console.readLine("Digite seu nome: ");
        
        // Ler senha (não mostra caracteres)
        char[] senhaChars = console.readPassword("Digite sua senha: ");
        String senha = new String(senhaChars);
        
        System.out.println("Nome: " + nome);
        System.out.println("Tamanho da senha: " + senha.length());
    }
}
```

### Argumentos de linha de comando

Os argumentos passados ao executar o programa podem ser acessados através do parâmetro `args` do método `main`:

```java
public class ArgumentosComando {
    public static void main(String[] args) {
        System.out.println("Número de argumentos: " + args.length);
        
        System.out.println("Argumentos recebidos:");
        for (int i = 0; i < args.length; i++) {
            System.out.println("Argumento " + i + ": " + args[i]);
        }
    }
}
```

Para executar com argumentos:
```bash
java ArgumentosComando arg1 arg2 "argumento com espaços"
```

### Leitura de arquivos

#### Lendo arquivo de texto

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class LeituraArquivo {
    public static void main(String[] args) {
        String caminhoArquivo = "dados.txt";
        
        try (BufferedReader reader = new BufferedReader(new FileReader(caminhoArquivo))) {
            String linha;
            System.out.println("Conteúdo do arquivo:");
            
            // Lê linha por linha até o final do arquivo
            while ((linha = reader.readLine()) != null) {
                System.out.println(linha);
            }
            
        } catch (IOException e) {
            System.err.println("Erro ao ler o arquivo: " + e.getMessage());
        }
    }
}
```

#### Lendo com Scanner a partir de arquivo

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class LeituraArquivoScanner {
    public static void main(String[] args) {
        File arquivo = new File("numeros.txt");
        
        try (Scanner scanner = new Scanner(arquivo)) {
            int soma = 0;
            
            // Lê todos os inteiros do arquivo e soma
            while (scanner.hasNextInt()) {
                soma += scanner.nextInt();
            }
            
            System.out.println("Soma dos números: " + soma);
            
        } catch (FileNotFoundException e) {
            System.err.println("Arquivo não encontrado: " + e.getMessage());
        }
    }
}
```

#### Lendo arquivo com Files (Java NIO)

A partir do Java 7, a classe `Files` oferece métodos modernos para lidar com arquivos:

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.List;

public class LeituraArquivoNIO {
    public static void main(String[] args) {
        try {
            // Lê todas as linhas de uma vez
            List<String> linhas = Files.readAllLines(Paths.get("dados.txt"));
            
            System.out.println("Conteúdo do arquivo:");
            for (String linha : linhas) {
                System.out.println(linha);
            }
            
            // Alternativa: ler todo o conteúdo como uma única string
            String conteudo = Files.readString(Paths.get("dados.txt")); // Java 11+
            System.out.println("\nConteúdo completo:\n" + conteudo);
            
        } catch (IOException e) {
            System.err.println("Erro ao ler o arquivo: " + e.getMessage());
        }
    }
}
```

### Entrada em interfaces gráficas (Swing)

Para aplicações desktop, a biblioteca Swing permite criar interfaces gráficas:

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class EntradaGrafica extends JFrame {
    private JTextField campoNome;
    private JTextField campoIdade;
    private JLabel labelResultado;
    
    public EntradaGrafica() {
        // Configurar janela
        setTitle("Exemplo de Entrada");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());
        
        // Criar componentes
        add(new JLabel("Nome:"));
        campoNome = new JTextField(20);
        add(campoNome);
        
        add(new JLabel("Idade:"));
        campoIdade = new JTextField(5);
        add(campoIdade);
        
        JButton botaoEnviar = new JButton("Enviar");
        add(botaoEnviar);
        
        labelResultado = new JLabel();
        add(labelResultado);
        
        // Adicionar ação ao botão
        botaoEnviar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    String nome = campoNome.getText();
                    int idade = Integer.parseInt(campoIdade.getText());
                    
                    labelResultado.setText("Olá, " + nome + "! Você tem " + idade + " anos.");
                } catch (NumberFormatException ex) {
                    labelResultado.setText("Erro: Digite uma idade válida!");
                }
            }
        });
    }
    
    public static void main(String[] args) {
        // Criar e exibir a janela na Event Dispatch Thread
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new EntradaGrafica().setVisible(true);
            }
        });
    }
}
```

#### Caixas de diálogo

Para entrada simples, caixas de diálogo são mais rápidas de implementar:

```java
import javax.swing.JOptionPane;

public class EntradaDialog {
    public static void main(String[] args) {
        // Entrada de texto
        String nome = JOptionPane.showInputDialog("Digite seu nome:");
        
        // Entrada de número
        String idadeStr = JOptionPane.showInputDialog("Digite sua idade:");
        
        try {
            int idade = Integer.parseInt(idadeStr);
            
            // Exibir mensagem
            JOptionPane.showMessageDialog(null, 
                    "Olá, " + nome + "! Você tem " + idade + " anos.",
                    "Informações", 
                    JOptionPane.INFORMATION_MESSAGE);
            
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(null, 
                    "Idade inválida!",
                    "Erro", 
                    JOptionPane.ERROR_MESSAGE);
        }
    }
}
```

### Entrada em aplicações web

Em aplicações web Java (como Servlets, JSP, Spring), a entrada geralmente vem de formulários HTML:

```java
// Exemplo simplificado de um Servlet
@WebServlet("/processar")
public class ProcessarFormServlet extends HttpServlet {
    
    protected void doPost(HttpServletRequest request, HttpServletResponse response) 
            throws ServletException, IOException {
        
        // Obter parâmetros do formulário
        String nome = request.getParameter("nome");
        String idadeStr = request.getParameter("idade");
        
        // Processar os dados
        try {
            int idade = Integer.parseInt(idadeStr);
            
            // Definir atributos para uso na página JSP
            request.setAttribute("nome", nome);
            request.setAttribute("idade", idade);
            
            // Encaminhar para página de resultado
            request.getRequestDispatcher("/resultado.jsp").forward(request, response);
            
        } catch (NumberFormatException e) {
            // Redirecionar em caso de erro
            response.sendRedirect("/erro.html");
        }
    }
}
```

### Boas Práticas para Entrada de Dados

1. **Sempre valide as entradas**:
   - Verifique se a entrada está no formato esperado
   - Trate casos extremos e valores inválidos
   - Use exceções adequadamente

2. **Forneça feedback ao usuário**:
   - Indique claramente o que é esperado
   - Mostre mensagens de erro informativas
   - Permita que o usuário corrija erros

3. **Libere recursos**:
   - Feche Scanner, BufferedReader e outros recursos
   - Use blocos try-with-resources quando possível

4. **Cuide da segurança**:
   - Nunca confie em entrada do usuário sem validação
   - Evite revelar informações sensíveis em mensagens de erro
   - Proteja-se contra ataques de injeção

5. **Projete para internacionalização**:
   - Use formatos de número e data que podem ser localizados
   - Prepare mensagens para tradução

### Resumo de opções de entrada

| Método | Caso de uso ideal | Complexidade |
|--------|-------------------|--------------|
| `Scanner` | Entrada simples do console | Baixa |
| `BufferedReader` | Leitura eficiente de grandes entradas | Média |
| `Console` | Entrada segura (como senhas) | Média |
| `Argumentos command-line` | Configuração inicial/scripts | Baixa |
| `Files (NIO)` | Leitura moderna de arquivos | Média |
| `Swing/AWT` | Aplicações desktop com GUI | Alta |
| `Servlets/JSP/Spring` | Aplicações web | Alta |

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>