<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# JDK, JRE e JVM

## Entendendo os componentes fundamentais do Java

Uma das características mais importantes do Java é seu modelo "Write Once, Run Anywhere". Para que isso seja possível, o Java utiliza três componentes fundamentais:

### JDK (Java Development Kit)

O **JDK** é o kit completo de desenvolvimento Java, contendo tudo o que você precisa para desenvolver aplicações Java.

**Componentes principais do JDK:**
- ✅ **JRE** (Java Runtime Environment)
- ✅ **Compilador Java** (`javac`)
- ✅ **Ferramentas de desenvolvimento** (debugger, javadoc, etc.)
- ✅ **API Java** completa

**Quando você precisa do JDK?**
- Quando deseja desenvolver aplicações Java
- Quando precisa compilar código Java
- Quando deseja usar ferramentas de desenvolvimento

```java
// Para compilar um arquivo Java com o JDK
javac MeuPrograma.java
```

### JRE (Java Runtime Environment)

O **JRE** é o ambiente de execução Java, necessário para executar aplicações Java. O JRE contém a JVM e as bibliotecas padrão.

**Componentes principais do JRE:**
- ✅ **JVM** (Java Virtual Machine)
- ✅ **Bibliotecas Java** (classes essenciais)
- ✅ **Plugins para navegadores** (em versões antigas)

**Quando você precisa do JRE?**
- Quando deseja apenas executar aplicações Java
- Quando não precisa desenvolver ou compilar código

```java
// Para executar um programa Java com o JRE
java MeuPrograma
```

### JVM (Java Virtual Machine)

A **JVM** é o coração do ecossistema Java. É uma máquina virtual que executa os bytecodes Java, fornecendo abstração entre o código e o hardware/sistema operacional.

**Responsabilidades da JVM:**
- Carregar e verificar o bytecode
- Executar o bytecode
- Gerenciar a memória (Garbage Collection)
- Otimizar o código em tempo de execução (JIT compiler)
- Fornecer segurança

**Como a JVM funciona:**

1. O código fonte Java (`.java`) é compilado em bytecode (`.class`)
2. O bytecode é carregado pela JVM
3. A JVM interpreta ou compila JIT (Just-In-Time) o bytecode
4. A JVM executa o programa no sistema operacional

```
┌─────────────┐    ┌──────────┐    ┌─────────────┐
│ Código Java │ -> │ Bytecode │ -> │ JVM (Win,   │ -> Execução
│  (.java)    │    │ (.class) │    │ Mac, Linux) │
└─────────────┘    └──────────┘    └─────────────┘
```

## Comparação entre JDK, JRE e JVM

| Característica | JDK | JRE | JVM |
|----------------|-----|-----|-----|
| **Finalidade** | Desenvolvimento | Execução | Interpretação |
| **Contém JVM** | ✅ | ✅ | - |
| **Contém compilador** | ✅ | ❌ | ❌ |
| **Ferramentas de desenvolvimento** | ✅ | ❌ | ❌ |
| **Necessário para executar programas** | ✅ | ✅ | ✅ |
| **Necessário para desenvolver programas** | ✅ | ❌ | ❌ |

## Como escolher entre JDK e JRE?

- **Desenvolvedor**: Instale o JDK (que já inclui o JRE)
- **Usuário final**: Instale apenas o JRE (suficiente para executar aplicações)

## Dica prática

Para verificar a versão do JDK instalada no seu sistema:

```bash
java -version
javac -version
```

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>