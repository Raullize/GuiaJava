<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Debugging

## Encontrando e corrigindo erros em código Java

Debugging é o processo de identificar e corrigir erros (bugs) em seus programas. É uma habilidade essencial para qualquer desenvolvedor Java. Este guia apresentará as técnicas, ferramentas e boas práticas para depurar eficientemente seu código Java.

### Fundamentos do debugging

#### O que é debugging?

Debugging é o processo de:
1. Identificar a presença de um erro
2. Localizar a origem exata do erro
3. Entender a causa do erro
4. Corrigir o erro
5. Verificar se a correção funciona

#### O ciclo de debugging

![Ciclo de Debugging](https://i.imgur.com/DjQtKAD.png)

1. **Reproduzir o erro**: O primeiro passo é conseguir reproduzir o erro consistentemente
2. **Diagnosticar**: Entender o que está acontecendo
3. **Localizar**: Encontrar a origem exata do problema
4. **Corrigir**: Implementar a solução
5. **Testar**: Verificar se o problema foi realmente resolvido
6. **Refletir**: Aprender com o erro para prevenir problemas similares

### Tipos de erros em Java

Em Java, existem três tipos principais de erros:

#### 1 Erros de compilação (Compile-time errors)

Ocorrem quando o código não pode ser compilado devido à violação das regras de sintaxe ou semântica da linguagem.

```java
public class ExemploErroCompilacao {
    public static void main(String[] args) {
        // Erro: ponto e vírgula faltando
        System.out.println("Hello world")
        
        // Erro: variável não declarada
        int soma = a + b;
        
        // Erro: tipo incompatível
        String texto = 42;
    }
}
```

Estes erros são os mais fáceis de corrigir porque:
- O compilador informa exatamente onde está o erro
- A mensagem geralmente é clara sobre o problema
- O programa não compila até que todos sejam corrigidos

#### 2 Erros de execução (Runtime errors)

Ocorrem durante a execução do programa e geralmente resultam em exceções.

```java
public class ExemploErroExecucao {
    public static void main(String[] args) {
        // Divisão por zero - ArithmeticException
        int resultado = 10 / 0;
        
        // NullPointerException
        String texto = null;
        int tamanho = texto.length();
        
        // ArrayIndexOutOfBoundsException
        int[] numeros = {1, 2, 3};
        int valor = numeros[5];
    }
}
```

Para erros de execução:
- O Java lança uma exceção com stack trace
- O programa é interrompido (a menos que a exceção seja tratada)
- É preciso analisar o stack trace para encontrar a origem

#### 3 Erros lógicos (Logical errors)

Os mais difíceis de detectar - o programa compila e executa, mas produz resultados incorretos.

```java
public class ExemploErroLogico {
    public static void main(String[] args) {
        // Erro lógico: somar quando deveria multiplicar
        int a = 5;
        int b = 3;
        int resultado = a + b; // Deveria ser a * b
        System.out.println("5 x 3 = " + resultado); // Exibe "5 x 3 = 8"
        
        // Erro lógico: condição invertida
        int idade = 15;
        if (idade >= 18) {
            System.out.println("Menor de idade"); // Mensagem errada
        } else {
            System.out.println("Maior de idade"); // Mensagem errada
        }
    }
}
```

Estes erros:
- Não geram mensagens de erro
- Requerem análise cuidadosa da lógica
- Podem passar despercebidos por muito tempo

### Ferramentas e técnicas de debugging

#### Debugging usando prints

A técnica mais simples é adicionar instruções `System.out.println()` em pontos estratégicos:

```java
public int calcularFatorial(int n) {
    System.out.println("Calculando fatorial de: " + n);
    
    int resultado = 1;
    for (int i = 1; i <= n; i++) {
        resultado *= i;
        System.out.println("i = " + i + ", resultado parcial = " + resultado);
    }
    
    System.out.println("Resultado final: " + resultado);
    return resultado;
}
```

**Prós**:
- Simples de implementar
- Não requer ferramentas especiais
- Funciona em qualquer ambiente

**Contras**:
- Poluição do código
- É preciso recompilar para cada mudança
- Difícil para situações complexas
- Difícil remover todos após o debug

#### Usando a IDE para debugging

IDEs modernas como IntelliJ IDEA, Eclipse e NetBeans possuem poderosas ferramentas de debugging:

**Principais recursos**:

1. **Breakpoints**: Pausam a execução em pontos específicos
   ```java
   public void metodoComplicado() {
       // Defina um breakpoint nesta linha
       int x = calcularAlgo();
       // Examine o valor de x quando o programa pausar
   }
   ```

2. **Step Into / Step Over / Step Out**:
   - **Step Into**: Entra em um método
   - **Step Over**: Executa um método sem entrar nele
   - **Step Out**: Sai do método atual

3. **Watches**: Monitoram expressões durante a execução
   ```java
   // Adicione um watch para "lista.size()" para monitorar o tamanho
   List<String> lista = new ArrayList<>();
   lista.add("item1");
   ```

4. **Avaliação de expressões**: Executa expressões durante a pausa
   ```java
   // Durante o debugging, avalie "usuario.getNome().toUpperCase()"
   Usuario usuario = new Usuario("João");
   ```

5. **Modificação de valores em tempo de execução**:
   ```java
   int contador = 0;
   // Altere o valor de contador durante o debug
   while (contador < 10) {
       // ...
       contador++;
   }
   ```

##### Como usar o debugger na IDE

**No IntelliJ IDEA**:
1. Clique na margem esquerda para definir breakpoints
2. Execute em modo debug (ícone de inseto)
3. Use os botões de Step Into/Over/Out
4. Observe variáveis na janela "Variables"
5. Adicione expressões em "Watches"

**No Eclipse**:
1. Dê duplo clique na margem para breakpoints
2. Execute como "Debug" (F11)
3. Controle a execução na perspectiva "Debug"
4. Veja variáveis na visão "Variables"
5. Use "Expressions" para avaliar código

**No VS Code**:
1. Clique à esquerda do número da linha para breakpoints
2. Use F5 para iniciar debug
3. Use os controles no painel superior
4. Observe variáveis no painel de Debug

#### Logging em vez de prints

Para debugging mais estruturado, use um framework de logging como Log4j ou java.util.logging:

```java
import java.util.logging.Logger;
import java.util.logging.Level;

public class CalculadoraComLog {
    private static final Logger LOGGER = Logger.getLogger(CalculadoraComLog.class.getName());
    
    public double dividir(double a, double b) {
        LOGGER.log(Level.INFO, "Iniciando divisão: {0} / {1}", new Object[]{a, b});
        
        if (b == 0) {
            LOGGER.log(Level.SEVERE, "Tentativa de divisão por zero");
            throw new ArithmeticException("Divisão por zero");
        }
        
        double resultado = a / b;
        LOGGER.log(Level.INFO, "Resultado da divisão: {0}", resultado);
        
        return resultado;
    }
}
```

**Vantagens do logging**:
- Pode ser deixado no código de produção
- Níveis de severidade (INFO, WARNING, ERROR)
- Formatação consistente
- Saída configurável (console, arquivo, serviço remoto)
- Melhor para aplicações multi-thread

#### Ferramentas especializadas

1. **jdb**: Debugger em linha de comando do Java
2. **JVisualVM**: Ferramenta visual para monitorar e profiling
3. **JConsole**: Para monitorar performance e recursos
4. **Java Mission Control**: Diagnóstico e monitoramento avançado

#### Debugging remoto

Para debuggar aplicações em servidores remotos:

```bash
# Inicie a JVM com opções de debugging remoto
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 MeuPrograma
```

E então conecte sua IDE ao processo na porta 5005.

### Estratégias eficazes de debugging

#### Dividir e conquistar (Debugging binário)

1. Divida o código em seções
2. Determine se o problema está na primeira ou segunda metade
3. Repita o processo na seção com o problema
4. Continue até localizar a origem exata

```java
public void metodoLongo() {
    // Primeira metade
    parteA();
    System.out.println("Após parte A"); // Verificação
    
    // Segunda metade
    parteB();
    System.out.println("Após parte B"); // Verificação
}
```

#### Isolamento e reprodução

1. Crie um pequeno exemplo que reproduza o problema
2. Remova código não relacionado
3. Simplifique até ter o menor exemplo possível que reproduz o erro

#### Usando testes unitários para debugging

Crie testes para reproduzir e verificar o bug:

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class CalculadoraTest {
    @Test
    public void testDivisao() {
        Calculadora calc = new Calculadora();
        
        // Caso normal
        assertEquals(2.0, calc.dividir(10, 5), 0.0001);
        
        // Caso que causa erro
        try {
            calc.dividir(10, 0);
            fail("Deveria ter lançado ArithmeticException");
        } catch (ArithmeticException e) {
            // Esperado
        }
    }
}
```

#### Debug por hipótese e eliminação

1. Formule uma hipótese sobre a causa do problema
2. Projete um teste para provar ou refutar a hipótese
3. Elimine possibilidades até encontrar a causa real

### Debugging de exceções comuns

#### NullPointerException

```java
public void processarUsuario(Usuario usuario) {
    // Problema: usuario pode ser null
    String nome = usuario.getNome(); // NullPointerException
    
    // Solução: verificar antes
    if (usuario != null) {
        String nome = usuario.getNome();
        // ...
    }
}
```

**Dicas para evitar NPE**:
- Sempre verifique objetos que podem ser null
- Use objetos vazio em vez de null quando possível
- Considere `Optional<T>` para valores que podem ser ausentes
- Utilize anotações como `@NotNull` e `@Nullable`

#### ArrayIndexOutOfBoundsException

```java
public void processarArray(int[] numeros) {
    // Problema: acesso a índice inválido
    for (int i = 0; i <= numeros.length; i++) { // Note o <= em vez de <
        System.out.println(numeros[i]); // Lança exceção no último loop
    }
    
    // Solução: usar índice correto
    for (int i = 0; i < numeros.length; i++) {
        System.out.println(numeros[i]);
    }
    
    // Alternativa: usar for-each
    for (int numero : numeros) {
        System.out.println(numero);
    }
}
```

#### ClassCastException

```java
public void processarObjeto(Object obj) {
    // Problema: cast inseguro
    String texto = (String) obj; // ClassCastException se obj não for String
    
    // Solução: verificar tipo antes
    if (obj instanceof String) {
        String texto = (String) obj;
        // ...
    }
}
```

#### ArithmeticException

```java
public int dividir(int a, int b) {
    // Problema: possível divisão por zero
    return a / b; // ArithmeticException se b for 0
    
    // Solução: verificar denominador
    if (b == 0) {
        throw new IllegalArgumentException("Denominador não pode ser zero");
    }
    return a / b;
}
```

#### ConcurrentModificationException

```java
public void processarLista(List<String> items) {
    // Problema: modificar coleção durante iteração
    for (String item : items) {
        if (item.startsWith("temp")) {
            items.remove(item); // ConcurrentModificationException
        }
    }
    
    // Solução: usar Iterator ou criar uma lista de itens para remover
    List<String> itemsParaRemover = new ArrayList<>();
    for (String item : items) {
        if (item.startsWith("temp")) {
            itemsParaRemover.add(item);
        }
    }
    items.removeAll(itemsParaRemover);
}
```

### Depuração avançada

#### Debugging de código multi-thread

Desafios:
- Condições de corrida
- Deadlocks
- Ordem de execução não determinística

Técnicas:
- Use logs detalhados incluindo identificação de thread
- Defina breakpoints condicionais específicos para threads
- Use ferramentas como jstack para analisar estado de threads
- Simplifique o código para isolar problemas

```java
// Exemplo de log para debugging de threads
void metodoMultithread() {
    Thread currentThread = Thread.currentThread();
    LOGGER.info("Thread [" + currentThread.getId() + "-" + 
                currentThread.getName() + "] iniciando processamento");
    // ...
}
```

#### Debug de memory leaks

Sintomas:
- Programa fica cada vez mais lento
- OutOfMemoryError eventual
- Aumento constante no uso de memória

Técnicas:
- Use ferramentas como JVisualVM ou Java Mission Control
- Obtenha heap dumps para análise
- Procure por objetos com muitas instâncias
- Verifique collections que crescem indefinidamente

```java
// Exemplo de memory leak
public class CacheComLeak {
    // Problema: cache que só cresce, nunca limpa
    private static final Map<String, Object> CACHE = new HashMap<>();
    
    public void adicionar(String chave, Object valor) {
        CACHE.put(chave, valor);
    }
}
```

#### Debugging de performance

Ferramentas:
- Profilers (JVisualVM, YourKit, JProfiler)
- Java Flight Recorder
- Benchmarking (JMH)

Métricas importantes:
- Tempo de CPU por método
- Contagem de alocações de objetos
- Utilização de memória
- Método mais chamados (hotspots)

### Boas práticas de debugging

#### ✅ Prevenção é melhor que cura

1. **Escreva testes unitários**
2. **Faça Code Reviews**
3. **Use análise estática de código** (SonarQube, FindBugs)
4. **Mantenha o código simples**
5. **Documente pressupostos e restrições**

#### Documentando bugs

Ao encontrar um bug, documente:
- Como reproduzir o problema
- A causa raiz
- A solução implementada
- Testes adicionados para prevenir regressões

#### Debugging científico

1. **Observe**: Colete todos os fatos disponíveis
2. **Hipótese**: Crie uma teoria sobre a causa
3. **Preveja**: O que acontecerá se sua teoria estiver correta?
4. **Teste**: Modifique o código para testar sua hipótese
5. **Analise**: Verifique os resultados e repita se necessário

#### Debugging por diferença

Compare versões funcionais e não-funcionais:
- Diff de código
- Diff de estados de execução
- Diff de logs
- Diff de resultados

### Ferramentas úteis para debugging

| Ferramenta | Tipo | Uso |
|------------|------|-----|
| IntelliJ Debugger | IDE | Debugging interativo com UI |
| Eclipse Debugger | IDE | Debugging interativo com UI |
| jdb | CLI | Debugging em linha de comando |
| JVisualVM | GUI | Análise de performance e memória |
| JConsole | GUI | Monitoramento de JVM |
| Java Mission Control | GUI | Análise de performance avançada |
| MAT (Memory Analyzer) | GUI | Análise de memória e memory leaks |
| jstack | CLI | Análise de threads e deadlocks |
| Log4j/Logback | Lib | Framework de logging |
| JUnit/TestNG | Lib | Testes automatizados |

### Checklist de Debugging

Quando enfrentar um bug difícil, siga esta checklist:

1. ✅ **Reproduza o problema consistentemente**
2. ✅ **Isole o bug no menor exemplo possível**
3. ✅ **Verifique as entradas e estados**
4. ✅ **Examine o stack trace (se houver)**
5. ✅ **Use breakpoints em pontos estratégicos**
6. ✅ **Verifique valores de variáveis durante execução**
7. ✅ **Formule e teste hipóteses**
8. ✅ **Examine alterações recentes no código**
9. ✅ **Considere condições de borda**
10. ✅ **Documente a solução e adicione testes**

### Aprendendo com bugs

Bugs são oportunidades de aprendizado:
- Reflita sobre por que o bug ocorreu
- Pense em como poderia ter sido evitado
- Considere ajustes no processo de desenvolvimento
- Compartilhe aprendizados com a equipe

> "Debugging é duas vezes mais difícil do que escrever o código. Portanto, se você escrever o código da maneira mais inteligente possível, por definição, você não é inteligente o suficiente para depurá-lo." - Brian Kernighan

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>