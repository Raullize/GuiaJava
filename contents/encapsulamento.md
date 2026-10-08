<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=180&section=header&text=Encapsulamento&fontSize=30&fontColor=fff&animation=twinkling&fontAlignY=35"/>

# Encapsulamento

O encapsulamento é um dos pilares da programação orientada a objetos, e refere-se ao agrupamento de dados e métodos que operam nesses dados em uma única unidade (classe), protegendo-os de acesso não autorizado e manipulação.

## O que é Encapsulamento?

Encapsulamento é a técnica que permite:
- Ocultar detalhes de implementação interna de uma classe
- Proteger os dados contra acesso direto
- Expor apenas o necessário através de uma interface bem definida
- Controlar como os dados são acessados e modificados

## Por que Encapsular?

| Benefício | Descrição |
|-----------|-----------|
| **Segurança** | Impede a modificação acidental ou mal-intencionada de dados |
| **Flexibilidade** | Permite alterar a implementação interna sem afetar o código cliente |
| **Manutenção** | Facilita a depuração e melhoria do código ao longo do tempo |
| **Validação** | Permite validar dados antes de modificá-los |
| **Abstração** | Esconde a complexidade e expõe apenas o necessário |

## Implementando Encapsulamento em Java

### Modificadores de Acesso

Java oferece quatro níveis de controle de acesso:

| Modificador | Classe | Pacote | Subclasse | Mundo |
|-------------|--------|--------|-----------|-------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| `default` (sem modificador) | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

### Padrão de Encapsulamento

A abordagem padrão para encapsulamento em Java é:

1. Declarar atributos como `private`
2. Fornecer métodos `public` de acesso (getters e setters)
3. Aplicar validações ou lógica de negócios nos métodos setters

```java
public class ContaBancaria {
    // Atributos privados
    private String titular;
    private double saldo;
    private String numeroConta;
    
    // Construtor
    public ContaBancaria(String titular, String numeroConta) {
        this.titular = titular;
        this.numeroConta = numeroConta;
        this.saldo = 0.0;
    }
    
    // Getters
    public String getTitular() {
        return titular;
    }
    
    public String getNumeroConta() {
        return numeroConta;
    }
    
    public double getSaldo() {
        return saldo;
    }
    
    // Setters com validação
    public void setTitular(String titular) {
        if (titular != null && !titular.trim().isEmpty()) {
            this.titular = titular;
        } else {
            throw new IllegalArgumentException("Titular inválido");
        }
    }
    
    // Métodos de negócio
    public void depositar(double valor) {
        if (valor > 0) {
            this.saldo += valor;
            System.out.println("Depósito de R$" + valor + " realizado com sucesso.");
        } else {
            throw new IllegalArgumentException("Valor de depósito deve ser positivo");
        }
    }
    
    public void sacar(double valor) {
        if (valor <= 0) {
            throw new IllegalArgumentException("Valor de saque deve ser positivo");
        }
        
        if (valor > saldo) {
            throw new IllegalArgumentException("Saldo insuficiente");
        }
        
        this.saldo -= valor;
        System.out.println("Saque de R$" + valor + " realizado com sucesso.");
    }
}
```

## Getters e Setters

Os métodos getters e setters são a interface pública para acessar e modificar atributos privados:

- **Getters**: Retornam o valor de um atributo
  ```java
  public String getNome() {
      return nome;
  }
  ```

- **Setters**: Modificam o valor de um atributo, geralmente com validação
  ```java
  public void setIdade(int idade) {
      if (idade >= 0) {
          this.idade = idade;
      } else {
          throw new IllegalArgumentException("Idade não pode ser negativa");
      }
  }
  ```

### Propriedades Somente Leitura

Para criar propriedades que não podem ser modificadas após a criação do objeto:
- Declare o atributo como `private final` ou simplesmente `private`
- Forneça apenas o método getter, sem o setter

```java
public class Pessoa {
    private final String cpf; // Imutável após a criação
    private String nome;      // Pode ser alterado
    
    public Pessoa(String cpf, String nome) {
        this.cpf = cpf;
        this.nome = nome;
    }
    
    public String getCpf() {
        return cpf;
    }
    
    public String getNome() {
        return nome;
    }
    
    public void setNome(String nome) {
        this.nome = nome;
    }
    
    // Não existe setCpf() - CPF é somente leitura
}
```

## Encapsulamento Avançado

### Classes Internas

Classes internas são um recurso poderoso para encapsulamento, pois podem acessar atributos privados da classe externa:

```java
public class Computador {
    private String processador;
    private int memoriaRAM;
    
    // Classe interna - fortemente encapsulada com a externa
    private class PlacaMae {
        private String modelo;
        
        public void configurar() {
            // Pode acessar atributos privados da classe externa
            System.out.println("Configurando placa-mãe para " + processador);
        }
    }
    
    public void iniciar() {
        PlacaMae placaMae = new PlacaMae();
        placaMae.configurar();
        System.out.println("Computador iniciado");
    }
}
```

### Métodos de Acesso Personalizados

Às vezes, getters e setters simples não são suficientes. Você pode criar métodos que melhor representem a intenção:

```java
public class Funcionario {
    private double salario;
    private int nivel;
    
    // Em vez de setSalario(), um método mais semântico
    public void darAumento(double percentual) {
        if (percentual > 0) {
            this.salario *= (1 + percentual/100);
        }
    }
    
    // Em vez de setNivel(), um método mais semântico
    public void promover() {
        this.nivel++;
        darAumento(5); // Aumento automático de 5% na promoção
    }
}
```

## Boas Práticas

1. **Encapsule sempre**: Evite atributos públicos
2. **Validação nos setters**: Sempre verifique dados antes de atribuí-los
3. **Mínima exposição**: Exponha apenas o que é necessário para uso externo
4. **Imutabilidade quando possível**: Use `final` para atributos que não devem mudar
5. **Métodos significativos**: Crie métodos que representem ações do domínio, não apenas getters/setters
6. **Pacotes lógicos**: Organize classes relacionadas em pacotes para aproveitar o acesso de pacote

---

[Voltar para o índice](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>