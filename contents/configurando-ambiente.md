<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Configurando o ambiente de desenvolvimento

## Preparando tudo para começar a programar em Java

A configuração adequada do ambiente de desenvolvimento é o primeiro passo para iniciar sua jornada com Java. Este guia explica de forma prática como configurar seu computador para desenvolver aplicações Java.

### Instalando o JDK (Java Development Kit)

O JDK contém tudo o que você precisa para desenvolver aplicações Java, incluindo o compilador, a JVM e um conjunto completo de bibliotecas.

#### Windows

1. **Baixe o JDK:**
   - Acesse o site oficial da Oracle: [Oracle JDK](https://www.oracle.com/java/technologies/downloads/)
   - Ou use o OpenJDK: [Adoptium](https://adoptium.net/)
   - Selecione a versão Windows (x64 Installer)

2. **Instale o JDK:**
   - Execute o instalador baixado
   - Siga as instruções na tela
   - Anote o diretório de instalação (geralmente `C:\Program Files\Java\jdk-xx.x.x`)

3. **Configure as variáveis de ambiente:**
   - Clique com o botão direito em "Este Computador" > "Propriedades"
   - Clique em "Configurações avançadas do sistema" > "Variáveis de Ambiente"
   - Em "Variáveis do Sistema", clique em "Novo"
   - Adicione `JAVA_HOME` como nome e o caminho do JDK como valor (ex: `C:\Program Files\Java\jdk-17`)
   - Encontre a variável "Path" em "Variáveis do Sistema"
   - Clique em "Editar" e adicione `%JAVA_HOME%\bin`
   - Clique em "OK" para salvar todas as alterações

4. **Verifique a instalação:**
   - Abra o Prompt de Comando (cmd)
   - Digite: `java -version`
   - Digite: `javac -version`
   - Você deve ver a versão do Java instalada em ambos os comandos

#### macOS

1. **Baixe o JDK:**
   - Acesse [Oracle JDK](https://www.oracle.com/java/technologies/downloads/) ou [Adoptium](https://adoptium.net/)
   - Selecione a versão macOS (x64 ou ARM64, dependendo do seu Mac)

2. **Instale o JDK:**
   - Abra o arquivo .dmg ou .pkg baixado
   - Siga as instruções na tela para completar a instalação

3. **Verifique a instalação:**
   - Abra o Terminal
   - Digite: `java -version`
   - Digite: `javac -version`
   - Você deve ver a versão do Java instalada

#### Linux

1. **Instale o JDK via gerenciador de pacotes:**

   Para Ubuntu/Debian:
   ```bash
   sudo apt update
   sudo apt install default-jdk
   ```

   Para Fedora/RHEL:
   ```bash
   sudo dnf install java-17-openjdk-devel
   ```

   Para Arch Linux:
   ```bash
   sudo pacman -S jdk-openjdk
   ```

2. **Verifique a instalação:**
   ```bash
   java -version
   javac -version
   ```

### Configurando uma IDE (Ambiente de Desenvolvimento Integrado)

Uma boa IDE facilita enormemente o desenvolvimento em Java, fornecendo recursos como autocompletar, debugging e gerenciamento de projetos.

#### IntelliJ IDEA

Uma das IDE's mais populares e poderosas para Java:

1. **Baixe a IntelliJ IDEA:**
   - Acesse [JetBrains IntelliJ IDEA](https://www.jetbrains.com/idea/download/)
   - Escolha entre a versão Community (gratuita) ou Ultimate (paga)

2. **Instale a IDE:**
   - Execute o instalador baixado
   - Siga as instruções na tela
   - Selecione os plugins e configurações desejadas

3. **Configure o JDK na IDE:**
   - Abra a IDE
   - Vá para "File" > "Project Structure"
   - Em "SDKs", clique no "+" e selecione "JDK"
   - Navegue até o diretório de instalação do JDK e selecione-o

#### Eclipse

Uma IDE gratuita e de código aberto, muito popular:

1. **Baixe o Eclipse:**
   - Acesse [Eclipse Downloads](https://www.eclipse.org/downloads/)
   - Baixe o "Eclipse IDE for Java Developers"

2. **Instale o Eclipse:**
   - Extraia o arquivo baixado para um diretório de sua escolha
   - Para Windows, execute `eclipse.exe`
   - Para macOS, abra o aplicativo Eclipse.app
   - Para Linux, execute `./eclipse`

3. **Configure o workspace e o JDK:**
   - Escolha um diretório para seu workspace quando solicitado
   - Vá para "Window" > "Preferences" > "Java" > "Installed JREs"
   - Clique em "Add", selecione "Standard VM" e navegue até o diretório do JDK

#### VS Code

Uma opção leve e altamente personalizável:

1. **Baixe o VS Code:**
   - Acesse [Visual Studio Code](https://code.visualstudio.com/)
   - Baixe a versão para seu sistema operacional

2. **Instale o VS Code:**
   - Execute o instalador e siga as instruções

3. **Instale a extensão Java:**
   - Abra o VS Code
   - Vá para a seção de extensões (ou pressione Ctrl+Shift+X)
   - Pesquise por "Extension Pack for Java" e instale
   - Recarregue o VS Code quando solicitado

4. **Configure o JDK:**
   - Vá para "File" > "Preferences" > "Settings"
   - Pesquise por "java.home"
   - Defina o caminho para o diretório do JDK

### Configurando o Maven (opcional, mas recomendado)

O Maven é uma ferramenta de automação de compilação que simplifica o gerenciamento de dependências e o processo de build:

1. **Baixe o Maven:**
   - Acesse [Apache Maven](https://maven.apache.org/download.cgi)
   - Baixe o arquivo binário (.zip ou .tar.gz)

2. **Instale o Maven:**
   - Extraia o arquivo baixado para um diretório de sua escolha

3. **Configure as variáveis de ambiente:**
   - Adicione `M2_HOME` apontando para o diretório do Maven
   - Adicione `%M2_HOME%\bin` (Windows) ou `$M2_HOME/bin` (macOS/Linux) ao PATH

4. **Verifique a instalação:**
   ```bash
   mvn -version
   ```

### Configurando o Git (opcional, mas recomendado)

O Git é essencial para controle de versão e colaboração:

1. **Baixe e instale o Git:**
   - Windows: [Git for Windows](https://gitforwindows.org/)
   - macOS: `brew install git` (usando Homebrew)
   - Linux: `sudo apt install git` (Ubuntu/Debian)

2. **Configure o Git:**
   ```bash
   git config --global user.name "Seu Nome"
   git config --global user.email "seu.email@exemplo.com"
   ```

### Verificando se tudo está funcionando

Após configurar o ambiente, é importante verificar se tudo está funcionando corretamente:

1. **Abra sua IDE preferida**
2. **Crie um novo projeto Java**
3. **Crie uma classe com um método main**
4. **Adicione um simples "Hello, World!" usando System.out.println**
5. **Execute o programa**

Se você conseguir ver a mensagem "Hello, World!" no console, parabéns! Seu ambiente de desenvolvimento Java está configurado e pronto para uso.

### Solucionando problemas comuns

| Problema | Possível solução |
|----------|-----------------|
| `'java' não é reconhecido como um comando interno` | Verifique se a variável PATH inclui o diretório bin do JDK |
| `javac: command not found` | Verifique se o JDK está instalado e configurado corretamente |
| IDE não encontra o JDK | Configure manualmente o caminho do JDK nas configurações da IDE |
| Erros de compilação inesperados | Verifique se a versão do JDK é compatível com seu projeto |
| Dependências não são baixadas | Verifique sua conexão com a internet e as configurações do Maven |

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>