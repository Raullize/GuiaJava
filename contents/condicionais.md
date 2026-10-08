<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Estruturas Condicionais

## Controlando o fluxo de execução em Java

As estruturas condicionais são fundamentais em programação, pois permitem que um programa tome decisões e execute diferentes blocos de código com base em condições específicas. O Java oferece várias estruturas condicionais que ajudam a controlar o fluxo de execução do programa.

### Tipos de Estruturas Condicionais em Java

Java oferece as seguintes estruturas condicionais:

1. if
2. if-else
3. if-else if-else
4. switch-case
5. Operador ternário

### if

A estrutura `if` é a mais básica e executa um bloco de código apenas se a condição especificada for verdadeira:

```java
if (condição) {
    // Código a ser executado se a condição for verdadeira
}
```

#### Exemplo:

```java
public class ExemploIf {
    public static void main(String[] args) {
        int idade = 18;
        
        if (idade >= 18) {
            System.out.println("Pessoa maior de idade.");
        }
    }
}
```

### if-else

A estrutura `if-else` permite executar um bloco de código se a condição for verdadeira e outro bloco se for falsa:

```java
if (condição) {
    // Código a ser executado se a condição for verdadeira
} else {
    // Código a ser executado se a condição for falsa
}
```

#### Exemplo:

```java
public class ExemploIfElse {
    public static void main(String[] args) {
        int idade = 16;
        
        if (idade >= 18) {
            System.out.println("Pessoa maior de idade.");
        } else {
            System.out.println("Pessoa menor de idade.");
        }
    }
}
```

### if-else if-else

A estrutura `if-else if-else` permite verificar múltiplas condições em sequência:

```java
if (condição1) {
    // Código a ser executado se condição1 for verdadeira
} else if (condição2) {
    // Código a ser executado se condição1 for falsa e condição2 for verdadeira
} else if (condição3) {
    // Código a ser executado se condição1 e condição2 forem falsas e condição3 for verdadeira
} else {
    // Código a ser executado se todas as condições anteriores forem falsas
}
```

#### Exemplo:

```java
public class ExemploIfElseIf {
    public static void main(String[] args) {
        int nota = 85;
        
        if (nota >= 90) {
            System.out.println("Conceito A");
        } else if (nota >= 80) {
            System.out.println("Conceito B");
        } else if (nota >= 70) {
            System.out.println("Conceito C");
        } else if (nota >= 60) {
            System.out.println("Conceito D");
        } else {
            System.out.println("Conceito F");
        }
    }
}
```

### switch-case

A estrutura `switch-case` é útil quando precisamos comparar uma variável com múltiplos valores possíveis:

```java
switch (expressão) {
    case valor1:
        // Código a ser executado se expressão for igual a valor1
        break;
    case valor2:
        // Código a ser executado se expressão for igual a valor2
        break;
    // ...mais casos...
    default:
        // Código a ser executado se expressão não corresponder a nenhum dos valores anteriores
}
```

#### Exemplo:

```java
public class ExemploSwitch {
    public static void main(String[] args) {
        int diaDaSemana = 3;
        String nomeDoDia;
        
        switch (diaDaSemana) {
            case 1:
                nomeDoDia = "Domingo";
                break;
            case 2:
                nomeDoDia = "Segunda-feira";
                break;
            case 3:
                nomeDoDia = "Terça-feira";
                break;
            case 4:
                nomeDoDia = "Quarta-feira";
                break;
            case 5:
                nomeDoDia = "Quinta-feira";
                break;
            case 6:
                nomeDoDia = "Sexta-feira";
                break;
            case 7:
                nomeDoDia = "Sábado";
                break;
            default:
                nomeDoDia = "Dia inválido";
        }
        
        System.out.println("Dia: " + nomeDoDia);
    }
}
```

#### ⚠️ A importância do `break`:

No `switch`, o `break` é crucial para evitar a execução dos casos seguintes (o chamado "fall-through"):

```java
public class SwitchSemBreak {
    public static void main(String[] args) {
        int opcao = 2;
        
        switch (opcao) {
            case 1:
                System.out.println("Opção 1 selecionada");
                // Sem break, a execução continua para o próximo caso
            case 2:
                System.out.println("Opção 2 selecionada");
                // Sem break, a execução continua para o próximo caso
            case 3:
                System.out.println("Opção 3 selecionada");
                break;
            default:
                System.out.println("Opção inválida");
        }
        
        // Saída:
        // Opção 2 selecionada
        // Opção 3 selecionada
    }
}
```

### Switch Expressions (Java 12+)

A partir do Java 12, foram introduzidas melhorias no `switch` que permitem utilizá-lo como expressão e não apenas como declaração:

```java
// Java 12+
String nomeDoDia = switch (diaDaSemana) {
    case 1 -> "Domingo";
    case 2 -> "Segunda-feira";
    case 3 -> "Terça-feira";
    case 4 -> "Quarta-feira";
    case 5 -> "Quinta-feira";
    case 6 -> "Sexta-feira";
    case 7 -> "Sábado";
    default -> "Dia inválido";
};
```

Este formato é mais conciso e não precisa de `break`.

#### Múltiplos casos com o mesmo resultado:

```java
// Java 12+
String tipoDeRota = switch (diaDaSemana) {
    case 1, 7 -> "Final de semana";
    case 2, 3, 4, 5, 6 -> "Dia útil";
    default -> "Dia inválido";
};
```

### Operador Ternário

O operador ternário é uma forma concisa de expressar uma condição simples:

```java
resultado = (condição) ? valorSeVerdadeiro : valorSeFalso;
```

#### Exemplo:

```java
public class ExemploOperadorTernario {
    public static void main(String[] args) {
        int idade = 16;
        String status = (idade >= 18) ? "Maior de idade" : "Menor de idade";
        
        System.out.println(status); // Menor de idade
    }
}
```

#### Ternários aninhados:

Embora seja possível aninhar operadores ternários, isso pode comprometer a legibilidade:

```java
public class TernarioAninhado {
    public static void main(String[] args) {
        int nota = 75;
        
        String conceito = (nota >= 90) ? "A" :
                         (nota >= 80) ? "B" :
                         (nota >= 70) ? "C" :
                         (nota >= 60) ? "D" : "F";
        
        System.out.println("Conceito: " + conceito); // Conceito: C
    }
}
```

### Aplicações Práticas

#### 1. Validação de Entrada de Usuário

```java
import java.util.Scanner;

public class ValidacaoEntrada {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Digite sua idade: ");
        int idade = scanner.nextInt();
        
        if (idade < 0) {
            System.out.println("Idade inválida. A idade não pode ser negativa.");
        } else if (idade > 120) {
            System.out.println("Idade inválida. A idade parece muito alta.");
        } else {
            System.out.println("Idade válida: " + idade + " anos.");
        }
        
        scanner.close();
    }
}
```

#### 2. Menu de Opções

```java
import java.util.Scanner;

public class MenuDeOpcoes {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("=== Menu Principal ===");
        System.out.println("1. Ver Perfil");
        System.out.println("2. Editar Configurações");
        System.out.println("3. Salvar Arquivo");
        System.out.println("4. Sair");
        System.out.print("Escolha uma opção: ");
        
        int opcao = scanner.nextInt();
        
        switch (opcao) {
            case 1:
                System.out.println("Exibindo Perfil...");
                break;
            case 2:
                System.out.println("Abrindo Configurações...");
                break;
            case 3:
                System.out.println("Salvando Arquivo...");
                break;
            case 4:
                System.out.println("Saindo do programa...");
                break;
            default:
                System.out.println("Opção inválida!");
        }
        
        scanner.close();
    }
}
```

#### 3. Cálculo de Desconto

```java
public class CalculadoraDesconto {
    public static void main(String[] args) {
        double valorCompra = 850.0;
        double valorFinal;
        double desconto;
        
        if (valorCompra >= 1000.0) {
            desconto = 0.15; // 15% de desconto
        } else if (valorCompra >= 500.0) {
            desconto = 0.10; // 10% de desconto
        } else if (valorCompra >= 100.0) {
            desconto = 0.05; // 5% de desconto
        } else {
            desconto = 0.0; // Sem desconto
        }
        
        valorFinal = valorCompra * (1 - desconto);
        
        System.out.printf("Valor da compra: R$ %.2f\n", valorCompra);
        System.out.printf("Desconto aplicado: %.1f%%\n", desconto * 100);
        System.out.printf("Valor final: R$ %.2f\n", valorFinal);
    }
}
```

### Condições Complexas

Em Java, podemos criar condições complexas usando operadores lógicos:

#### 1. AND lógico (`&&`)

```java
if (idade >= 18 && possuiHabilitacao) {
    System.out.println("Pode dirigir");
} else {
    System.out.println("Não pode dirigir");
}
```

#### 2. OR lógico (`||`)

```java
if (formaDePagamento.equals("cartão de crédito") || formaDePagamento.equals("cartão de débito")) {
    System.out.println("Pagamento com cartão");
} else {
    System.out.println("Outra forma de pagamento");
}
```

#### 3. NOT lógico (`!`)

```java
if (!aprovado) {
    System.out.println("Reprovado");
}
```

#### 4. Combinando operadores lógicos

```java
if ((idade >= 18 || acompanhadoPorResponsavel) && !eventoRestrito) {
    System.out.println("Entrada permitida");
} else {
    System.out.println("Entrada não permitida");
}
```

### ⚠️ Erros Comuns e Armadilhas

#### 1. Confundir `=` (atribuição) com `==` (comparação)

```java
// Errado (atribui 5 a x e verifica se o resultado da atribuição é verdadeiro)
if (x = 5) {
    System.out.println("x é 5");
}

// Correto (verifica se x é igual a 5)
if (x == 5) {
    System.out.println("x é 5");
}
```

#### 2. Esquecer chaves em blocos com única instrução

```java
// Sem chaves - apenas a primeira linha está no escopo do if
if (condicao)
    System.out.println("Dentro do if");
    System.out.println("Isso sempre será executado"); // Não faz parte do bloco if
```

#### 3. Comparação entre números de ponto flutuante

```java
// Problemático devido a imprecisões de ponto flutuante
if (valor == 0.1) {
    // Pode não ser executado como esperado
}

// Melhor abordagem
if (Math.abs(valor - 0.1) < 0.0001) {
    // Usa uma margem de erro (epsilon)
}
```

#### 4. Avaliação de curto-circuito não compreendida

```java
// O método verificar() só será chamado se objeto não for null
if (objeto != null && objeto.verificar()) {
    // Código seguro
}

// ERRO: Se objeto for null, ocorrerá NullPointerException
if (objeto.verificar() && objeto != null) {
    // Código problemático
}
```

### Boas Práticas

1. **Sempre use chaves**: Mesmo para blocos de uma única linha, para evitar erros quando adicionar mais linhas no futuro.

```java
// Recomendado
if (condicao) {
    realizarAcao();
}
```

2. **Simplifique condições complexas**: Use variáveis intermediárias com nomes descritivos.

```java
boolean elegivel = idade >= 18 && possuiDocumentos && passouNoTeste;
if (elegivel) {
    System.out.println("Candidato elegível");
}
```

3. **Prefira switch para múltiplas condições**: Quando comparar uma variável com vários valores possíveis.

4. **Evite aninhamento excessivo**: Considere inverter condições ou usar retornos antecipados.

```java
// Muito aninhamento
if (condicaoA) {
    if (condicaoB) {
        if (condicaoC) {
            // Código
        }
    }
}

// Melhor abordagem
if (!condicaoA) return;
if (!condicaoB) return;
if (!condicaoC) return;
// Código
```

5. **Cuidado com operador ternário**: Use apenas para casos simples e facilmente compreensíveis.

### Resumo

| Estrutura | Uso | Quando usar |
|-----------|-----|-------------|
| `if` | `if (condição) { ... }` | Para executar código apenas em determinada condição |
| `if-else` | `if (condição) { ... } else { ... }` | Para escolher entre duas alternativas exclusivas |
| `if-else if-else` | `if (...) { ... } else if (...) { ... } else { ... }` | Para múltiplas condições em sequência |
| `switch` | `switch (expressão) { case valor: ... }` | Para comparar uma variável com múltiplos valores |
| Operador ternário | `resultado = condição ? valor1 : valor2;` | Para atribuição condicional simples |

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>