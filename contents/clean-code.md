# ✨ Boas Práticas e Clean Code

## O que é Clean Code?

Clean Code (Código Limpo) refere-se a um conjunto de práticas que resultam em código mais legível, manutenível e eficiente. O conceito foi popularizado pelo livro "Clean Code" de Robert C. Martin (Uncle Bob) e tornou-se fundamental para o desenvolvimento de software de qualidade.

## Princípios Fundamentais

### 1. 📌 Nomes Significativos

```java
// Ruim
int d; // dias
List<String> lst;

// Bom
int diasDecorridos;
List<String> listaDeClientes;
```

### 2. 🔍 Funções Pequenas e Focadas

```java
// Ruim - função faz muitas coisas
public void processarDadosDoCliente(Cliente cliente) {
    // validação
    // processamento
    // persistência
    // notificação
}

// Bom - funções pequenas com responsabilidade única
public void processarDadosDoCliente(Cliente cliente) {
    if (validarCliente(cliente)) {
        processarDados(cliente);
        persistirCliente(cliente);
        notificarProcessamento(cliente);
    }
}
```

### 3. 🧩 Regra do Escoteiro

Deixe o código mais limpo do que você o encontrou.

### 4. 📏 Formatação Consistente

* Use um estilo de codificação consistente
* Mantenha um limite de colunas razoável (geralmente 80-120)
* Alinhe código de forma coerente

### 5. 📝 Comentários Apropriados

```java
// Ruim - comentário óbvio
// Incrementa contador
contador++;

// Bom - explica o "porquê", não o "o quê"
// Incrementamos o contador para rastrear tentativas de login malsucedidas
contador++;
```

## Princípios SOLID

### 1. 🔄 S - Princípio da Responsabilidade Única (SRP)

Uma classe deve ter apenas uma razão para mudar.

```java
// Ruim - classe com múltiplas responsabilidades
class Cliente {
    // dados do cliente
    // métodos para salvar no banco
    // métodos para validar
    // métodos para gerar relatórios
}

// Bom - responsabilidades separadas
class Cliente { /* apenas dados e comportamentos do cliente */ }
class ClienteRepository { /* persistência */ }
class ClienteValidator { /* validação */ }
class ClienteReportGenerator { /* relatórios */ }
```

### 2. 🔓 O - Princípio Aberto/Fechado (OCP)

Entidades devem estar abertas para extensão, mas fechadas para modificação.

```java
// Ruim
class CalculadoraDeDesconto {
    double calcularDesconto(Produto produto) {
        if (produto.tipo == TipoProduto.ELETRONICO) {
            return produto.preco * 0.1;
        } else if (produto.tipo == TipoProduto.VESTUARIO) {
            return produto.preco * 0.05;
        }
        return 0;
    }
}

// Bom
interface EstrategiaDeDesconto {
    double calcularDesconto(Produto produto);
}

class DescontoEletronico implements EstrategiaDeDesconto {
    public double calcularDesconto(Produto produto) {
        return produto.preco * 0.1;
    }
}

class DescontoVestuario implements EstrategiaDeDesconto {
    public double calcularDesconto(Produto produto) {
        return produto.preco * 0.05;
    }
}
```

### 3. 🔄 L - Princípio da Substituição de Liskov (LSP)

Subtipos devem ser substituíveis por seus tipos base.

```java
// Violação do LSP
class Retangulo {
    protected int largura;
    protected int altura;
    
    public void setLargura(int largura) {
        this.largura = largura;
    }
    
    public void setAltura(int altura) {
        this.altura = altura;
    }
    
    public int getArea() {
        return largura * altura;
    }
}

class Quadrado extends Retangulo {
    @Override
    public void setLargura(int largura) {
        this.largura = largura;
        this.altura = largura; // Viola LSP
    }
    
    @Override
    public void setAltura(int altura) {
        this.altura = altura;
        this.largura = altura; // Viola LSP
    }
}
```

### 4. 🧩 I - Princípio da Segregação de Interface (ISP)

Clientes não devem ser forçados a depender de interfaces que não utilizam.

```java
// Ruim - interface "gorda"
interface Trabalhador {
    void trabalhar();
    void comer();
    void dormir();
}

// Bom - interfaces segregadas
interface Trabalhavel {
    void trabalhar();
}

interface Alimentavel {
    void comer();
}

interface Dorminhoco {
    void dormir();
}

class Humano implements Trabalhavel, Alimentavel, Dorminhoco {
    // implementações
}

class Robo implements Trabalhavel {
    // implementa apenas trabalhar
}
```

### 5. 🔄 D - Princípio da Inversão de Dependência (DIP)

Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.

```java
// Ruim - dependência de implementação concreta
class ServicoEmail {
    private GmailSender emailSender = new GmailSender();
    
    public void enviarEmail(String para, String assunto, String corpo) {
        emailSender.send(para, assunto, corpo);
    }
}

// Bom - dependência de abstração
interface EmailSender {
    void send(String para, String assunto, String corpo);
}

class GmailSender implements EmailSender {
    public void send(String para, String assunto, String corpo) {
        // implementação específica
    }
}

class ServicoEmail {
    private EmailSender emailSender;
    
    // Injeção de dependência
    public ServicoEmail(EmailSender emailSender) {
        this.emailSender = emailSender;
    }
    
    public void enviarEmail(String para, String assunto, String corpo) {
        emailSender.send(para, assunto, corpo);
    }
}
```

## Práticas Recomendadas para Java

### 1. 🧹 Evite Números Mágicos

```java
// Ruim
if (idade > 18) { ... }

// Bom
private static final int IDADE_MINIMA_MAIORIDADE = 18;
if (idade > IDADE_MINIMA_MAIORIDADE) { ... }
```

### 2. 🔄 Use Enums para Constantes Relacionadas

```java
// Ruim
public static final int STATUS_PENDENTE = 0;
public static final int STATUS_APROVADO = 1;
public static final int STATUS_REJEITADO = 2;

// Bom
public enum StatusPedido {
    PENDENTE, APROVADO, REJEITADO
}
```

### 3. 🧠 Falhe Rápido

```java
public void processarPedido(Pedido pedido) {
    // Verificações logo no início
    if (pedido == null) {
        throw new IllegalArgumentException("Pedido não pode ser nulo");
    }
    
    if (pedido.getItens().isEmpty()) {
        throw new IllegalArgumentException("Pedido deve conter pelo menos um item");
    }
    
    // Lógica principal aqui
}
```

### 4. 🛡️ Tratamento Adequado de Exceções

```java
// Ruim
try {
    // código que pode lançar exceção
} catch (Exception e) {
    e.printStackTrace(); // Apenas imprime e engole a exceção
}

// Bom
try {
    // código que pode lançar exceção
} catch (IOException e) {
    logger.error("Erro ao ler arquivo: " + e.getMessage(), e);
    throw new ServiceException("Não foi possível processar o arquivo", e);
} finally {
    // Liberação de recursos
}
```

### 5. 🧪 Código Testável

* Escreva código que seja fácil de testar
* Use injeção de dependência
* Evite estados globais e estáticos quando possível
* Separe lógica de negócios da integração com sistemas externos

## Refatoração Contínua

A refatoração é um processo fundamental para manter o código limpo. Algumas técnicas comuns:

1. **Extrair Método**: Quebrar métodos longos em partes menores
2. **Renomear**: Escolher nomes mais descritivos
3. **Mover Método/Campo**: Reorganizar responsabilidades entre classes
4. **Substituir Condicionais por Polimorfismo**: Usar herança e polimorfismo em vez de condicionais complexos

## Ferramentas para Auxiliar na Qualidade do Código

* **Análise Estática**: SonarQube, PMD, CheckStyle
* **Formatação Automática**: IntelliJ IDEA, Eclipse com plugins
* **Revisão de Código**: GitHub Pull Requests, Gerrit
* **Testes Automatizados**: JUnit, Mockito, AssertJ

## Conclusão

O Clean Code não é apenas sobre estética - é sobre criar software que seja fácil de entender, modificar e manter. Adotar estas práticas resulta em:

* Menor custo de manutenção
* Menos bugs
* Maior produtividade da equipe
* Onboarding mais rápido de novos desenvolvedores
* Software mais robusto e adaptável

Lembre-se: código limpo é aquele que pode ser facilmente entendido por outro desenvolvedor. Escreva seu código pensando em quem irá mantê-lo no futuro (que pode ser você mesmo!).

---

## 📚 Recursos Adicionais

* Livro: "Clean Code" de Robert C. Martin
* Livro: "Refactoring" de Martin Fowler
* Livro: "Effective Java" de Joshua Bloch
* [Java Code Conventions (Oracle)](https://www.oracle.com/java/technologies/javase/codeconventions-introduction.html)
* [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html) 