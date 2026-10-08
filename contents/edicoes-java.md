<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=header"/>

# Edições do Java

## Conhecendo as diferentes plataformas Java

O Java é dividido em várias edições (ou plataformas), cada uma projetada para atender a diferentes necessidades de desenvolvimento. Entender essas edições é crucial para escolher a plataforma correta para seu projeto.

### Java SE (Standard Edition)

A **Java SE** é a edição padrão do Java, servindo como base para todas as outras edições.

**Características principais:**
- Contém as bibliotecas fundamentais do Java
- Inclui as APIs básicas (coleções, IO, threading, etc.)
- Oferece os recursos essenciais para aplicações desktop
- Inclui recursos de rede básicos

**Casos de uso:**
- Aplicações desktop
- Jogos simples
- Aplicações console
- Componentes e bibliotecas

```java
// Exemplo de código Java SE - um programa básico
public class OlaMundo {
    public static void main(String[] args) {
        System.out.println("Olá, Mundo!");
    }
}
```

### Java EE (Enterprise Edition)

A **Java EE** (atualmente chamada **Jakarta EE**) estende o Java SE com APIs adicionais para desenvolvimento de aplicações corporativas de grande escala.

**Características principais:**
- Especificações para aplicações web (Servlets, JSP)
- Enterprise JavaBeans (EJB)
- Java Persistence API (JPA)
- Java Message Service (JMS)
- Java Authentication and Authorization Service (JAAS)
- Java Connector Architecture (JCA)

**Casos de uso:**
- Aplicações web empresariais
- Serviços RESTful
- Sistemas bancários e financeiros
- E-commerce e sistemas de gestão

```java
// Exemplo simples de um Servlet Java EE
@WebServlet("/ola")
public class OlaServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, 
                        HttpServletResponse response) throws ServletException, IOException {
        response.getWriter().println("Olá do Java EE!");
    }
}
```

### Java ME (Micro Edition)

A **Java ME** é uma versão reduzida do Java, otimizada para dispositivos com recursos limitados.

**Características principais:**
- Consumo de memória reduzido
- APIs simplificadas
- Otimizado para dispositivos embarcados
- Dividido em configurações (CLDC, CDC) e perfis (MIDP)

**Casos de uso:**
- Dispositivos embarcados
- Celulares antigos (feature phones)
- Dispositivos IoT (Internet das Coisas)
- Smart cards

```java
// Exemplo simplificado de um MIDlet Java ME
public class OlaMIDlet extends MIDlet {
    public void startApp() {
        Display display = Display.getDisplay(this);
        Form form = new Form("Olá Java ME");
        form.append("Olá do Java ME!");
        display.setCurrent(form);
    }
    
    public void pauseApp() { }
    public void destroyApp(boolean unconditional) { }
}
```

### JavaFX

O **JavaFX** é uma plataforma para criação de aplicações desktop ricas e interfaces gráficas modernas.

**Características principais:**
- Recursos gráficos avançados
- Componentes de UI modernos
- Suporte a gráficos e animações
- Recursos de mídia (áudio e vídeo)
- Vinculação de dados (data binding)

**Casos de uso:**
- Aplicações desktop modernas
- Dashboards e visualização de dados
- Jogos 2D
- Aplicações interativas

```java
// Exemplo básico de JavaFX
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Label;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class OlaJavaFX extends Application {
    @Override
    public void start(Stage primaryStage) {
        Label label = new Label("Olá, JavaFX!");
        StackPane root = new StackPane(label);
        Scene scene = new Scene(root, 300, 200);
        
        primaryStage.setTitle("Exemplo JavaFX");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
    
    public static void main(String[] args) {
        launch(args);
    }
}
```

## Comparação entre as edições

| Característica | Java SE | Java EE | Java ME | JavaFX |
|----------------|---------|---------|---------|--------|
| **Tamanho** | Médio | Grande | Compacto | Médio |
| **Público-alvo** | Desenvolvedores gerais | Empresas | Dispositivos embarcados | UI/UX designers e desenvolvedores |
| **Casos de uso** | Desktop/Aplicações gerais | Web/Enterprise | Dispositivos limitados | UI rica/Multimídia |
| **Complexidade** | Moderada | Alta | Baixa | Moderada |

## Qual versão do Java devo utilizar?

A escolha da edição Java depende do tipo de aplicação que você deseja desenvolver:

- **Aplicações desktop simples**: Java SE
- **Aplicações corporativas/web**: Java EE (Jakarta EE)
- **Dispositivos com recursos limitados**: Java ME
- **Interfaces gráficas modernas**: JavaFX

### Dica importante

Para iniciantes em Java, é recomendável começar com o Java SE para aprender os fundamentos da linguagem. Uma vez que você dominar os conceitos básicos, poderá expandir para outras edições conforme necessário.

---

[Voltar ao índice principal](../README.md)

<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=007396&height=120&section=footer"/>