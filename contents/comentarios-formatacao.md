<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Comentários e formatação

## Documentando e organizando seu código Java

A documentação e organização adequada do código são práticas essenciais para qualquer programador profissional. Neste guia, vamos explorar como usar comentários e formatação para tornar seu código Java mais legível e manutenível.

### Comentários em Java

Os comentários são trechos de texto que não são executados pelo compilador, servindo apenas para documentar o código. Java suporta três tipos de comentários:

#### Comentários de linha única

Começam com `//` e vão até o final da linha.

```java
// Este é um comentário de linha única
int contador = 0; // Também pode ser colocado no final de uma linha de código
```

#### Comentários de múltiplas linhas

Começam com `/*` e terminam com `*/`, podendo abranger várias linhas.

```java
/* Este é um comentário
   que abrange
   múltiplas linhas */
   
int x = 10; /* Este comentário também pode
              estar em múltiplas linhas */
```

#### Comentários de documentação (Javadoc)

Começam com `/**` e terminam com `*/`. São usados para gerar documentação automática com a ferramenta Javadoc.

```java
/**
 * Esta classe implementa um contador simples.
 * Ela permite incrementar, decrementar e reiniciar o contador.
 * 
 * @author Seu Nome
 * @version 1.0
 */
public class Contador {
    private int valor;
    
    /**
     * Incrementa o contador em 1.
     * 
     * @return O novo valor após o incremento
     */
    public int incrementar() {
        return ++valor;
    }
}
```

### Tags Javadoc comuns

| Tag | Descrição | Exemplo |
|-----|-----------|---------|
| `@author` | Especifica o autor do código | `@author Maria Silva` |
| `@version` | Indica a versão do código | `@version 2.1` |
| `@param` | Descreve um parâmetro de método | `@param nome Nome do usuário` |
| `@return` | Descreve o valor de retorno | `@return true se operação foi bem-sucedida` |
| `@throws` | Documenta uma exceção que pode ser lançada | `@throws IOException Se ocorrer erro de I/O` |
| `@see` | Adiciona referência a outro elemento | `@see Calculadora#somar` |
| `@since` | Indica quando o elemento foi adicionado | `@since 1.2` |
| `@deprecated` | Marca elemento como obsoleto | `@deprecated Use o método novo()` |

### Boas práticas para comentários

1. **Comente o porquê, não o como**:
   ```java
   // RUIM: Incrementa contador em 1
   contador++;
  
   // BOM: Incrementa contador para cada novo usuário registrado
   contador++;
   ```

2. **Mantenha comentários atualizados**:
   Comentários desatualizados são piores que nenhum comentário.

3. **Use comentários para explicar código complexo**:
   ```java
   // Aplica o algoritmo de Dijkstra para encontrar o caminho mais curto
   // entre os nós origem e destino no grafo
   List<Node> caminho = calcularCaminhoMaisCurto(origem, destino);
   ```

4. **Evite comentários óbvios**:
   ```java
   // RUIM: Declara uma variável inteira
   int idade = 25;
   ```

5. **Documente APIs públicas com Javadoc**:
   Métodos e classes que serão usados por outros desenvolvedores devem ter documentação Javadoc.

### Formatação de código

A formatação consistente melhora a legibilidade do código. A maioria das convenções de formatação Java deriva do [Guia de Estilo da Oracle](https://www.oracle.com/java/technologies/javase/codeconventions-contents.html).

#### Indentação

Use 4 espaços para cada nível de indentação (ou tabulações configuradas para 4 espaços).

```java
public class Exemplo {
    public void metodo() {
        if (condicao) {
            // Código indentado com 4 espaços
            fazerAlgo();
        }
    }
}
```

#### Comprimento das linhas

Limite o comprimento das linhas a 80-120 caracteres, quebrando linhas longas de forma lógica.

```java
// Quebra de linha em chamada de método com muitos parâmetros
minhaFuncao(parametro1, parametro2, 
            parametro3, parametro4);

// Quebra de linha em expressões longas
if (condicao1 && condicao2
        && condicao3 && condicao4) {
    // código
}
```

#### Nomenclatura

Java usa convenções específicas de nomenclatura:

| Elemento | Convenção | Exemplo |
|----------|-----------|---------|
| Classes e interfaces | PascalCase | `ContaBancaria`, `Runnable` |
| Métodos e variáveis | camelCase | `calcularJuros()`, `nomeCompleto` |
| Constantes | SNAKE_CASE_MAIÚSCULO | `MAX_VALOR`, `PI` |
| Pacotes | Tudo minúsculo | `java.util`, `com.minhaempresa.projeto` |

```java
package com.empresa.projeto;

public class ContaBancaria {
    public static final double TAXA_JUROS = 0.05;
    private String nomeCliente;
    
    public double calcularJuros(double saldo) {
        return saldo * TAXA_JUROS;
    }
}
```

#### Espaçamento

Use espaços para melhorar a legibilidade:

```java
// Entre operadores
int soma = a + b;

// Após vírgulas
chamarMetodo(param1, param2, param3);

// Em estruturas de controle
if (condicao) {
    // código
}

// Sem espaço após métodos/funções
calcular(x);

// Sem espaço entre nome do método e parêntese
public void metodo() {
    // código
}
```

#### Blocos

Coloque chaves de abertura na mesma linha da declaração e as de fechamento alinhadas com a abertura do bloco:

```java
if (condicao) {
    // código
} else {
    // código
}

for (int i = 0; i < 10; i++) {
    // código
}

class MinhaClasse {
    // código
}
```

### Exemplo completo de código bem formatado e comentado

```java
package com.exemplo.util;

/**
 * Classe utilitária para operações matemáticas.
 * <p>
 * Esta classe fornece métodos para cálculos matemáticos comuns,
 * como fatorial, verificação de número primo e cálculo de média.
 * </p>
 * 
 * @author Seu Nome
 * @version 1.2
 * @since 1.0
 */
public class MatematicaUtil {
    
    /**
     * Valor constante de PI com maior precisão do que Math.PI.
     */
    public static final double PI_PRECISAO = 3.14159265358979323846;
    
    /**
     * Calcula o fatorial de um número.
     * 
     * @param n Número para calcular o fatorial (deve ser não-negativo)
     * @return O fatorial de n
     * @throws IllegalArgumentException Se n for negativo
     */
    public static long fatorial(int n) {
        // Verifica se o argumento é válido
        if (n < 0) {
            throw new IllegalArgumentException("Número não pode ser negativo");
        }
        
        // Caso base
        if (n <= 1) {
            return 1;
        }
        
        // Utiliza recursividade para calcular o fatorial
        long resultado = n * fatorial(n - 1);
        return resultado;
    }
    
    /**
     * Verifica se um número é primo.
     * <p>
     * Um número é primo se for maior que 1 e divisível apenas por 1 e por ele mesmo.
     * </p>
     * 
     * @param numero Número a ser verificado
     * @return true se o número for primo, false caso contrário
     */
    public static boolean ehPrimo(int numero) {
        // Números menores que 2 não são primos
        if (numero < 2) {
            return false;
        }
        
        // Verificamos divisibilidade até a raiz quadrada de numero
        // para otimizar o algoritmo
        for (int i = 2; i <= Math.sqrt(numero); i++) {
            if (numero % i == 0) {
                return false;  // Encontrou um divisor
            }
        }
        
        return true;  // Se não encontrou divisores, é primo
    }
    
    /**
     * Calcula a média aritmética de um array de números.
     * 
     * @param numeros Array de números para calcular a média
     * @return A média aritmética dos números ou 0 se o array estiver vazio
     */
    public static double media(double[] numeros) {
        if (numeros.length == 0) {
            return 0;
        }
        
        double soma = 0;
        
        // Soma todos os valores do array
        for (int i = 0; i < numeros.length; i++) {
            soma += numeros[i];
        }
        
        // Retorna a média (soma dividida pela quantidade)
        return soma / numeros.length;
    }
}
```

### Ferramentas para formatação automática

A formatação manual pode ser trabalhosa. Felizmente, existem ferramentas que podem ajudar:

1. **IDEs**: IDEs como IntelliJ IDEA, Eclipse e NetBeans têm formatadores embutidos:
   - IntelliJ IDEA: `Ctrl+Alt+L` (Windows/Linux) ou `Cmd+Opt+L` (Mac)
   - Eclipse: `Ctrl+Shift+F`
   - NetBeans: `Alt+Shift+F`

2. **Google Java Format**: Ferramenta da Google que impõe o estilo de código do Google.
   - [GitHub - Google Java Format](https://github.com/google/google-java-format)

3. **Checkstyle**: Ferramenta que valida se seu código segue convenções específicas.
   - [Checkstyle](https://checkstyle.sourceforge.io/)

4. **Plugins de IDEs**:
   - SonarLint
   - Checkstyle-IDEA (para IntelliJ)
   - SpotBugs

### Benefícios de comentários e formatação adequados

1. **Manutenção facilitada**: Código bem documentado é mais fácil de manter
2. **Colaboração eficiente**: Outros desenvolvedores entenderão seu código mais rapidamente
3. **Menos bugs**: Código bem formatado ajuda a prevenir erros de sintaxe
4. **Onboarding mais rápido**: Novos membros da equipe se adaptam mais facilmente
5. **Qualidade percebida**: Código bem formatado transmite profissionalismo

### Checklist para revisão de código

Antes de submeter seu código para revisão, verifique:

- [ ] Há comentários Javadoc para classes e métodos públicos
- [ ] Trechos complexos estão comentados
- [ ] Não há comentários óbvios ou redundantes
- [ ] Comentários estão atualizados com o código
- [ ] Indentação está consistente
- [ ] Nomenclatura segue as convenções Java
- [ ] Linhas não são muito longas
- [ ] Espaçamento adequado entre operadores e parâmetros
- [ ] O código está formatado de acordo com o estilo do projeto

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>