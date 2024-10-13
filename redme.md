# ColetaAI - ♻️ Coletando hoje para um amanhã melhor 🌱

## Descrição 
A coletaAi é uma aplicação inovadora desenvolvida para auxiliar a população a descartar lixo de maneira correta e eficiente. Nossa missão é promover a conscientização ambiental e facilitar o processo de coleta seletiva, conectando cidadãos, empresas e serviços de coleta em uma única plataforma intuitiva e acessível.

# Aplicação Spring Boot com Docker

Este projeto demonstra como conteinerizar uma aplicação Spring Boot usando Docker.

## Pré-requisitos

- Docker instalado no seu sistema
- Java Development Kit (JDK) instalado
- Maven ou Gradle instalado

## Estrutura do Projeto
```
meu-spring-boot-app/
├── src/
├── target/
├── Dockerfile
├── pom.xml ou build.gradle
└── README.md
```

## Dockerfile

Crie um `Dockerfile` no diretório raiz do seu projeto com o seguinte conteúdo:

```dockerfile
FROM eclipse-temurin:21-alpine
VOLUME /tmp
EXPOSE 8080
ARG JAR_FILE=target/coletaAi-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

Construir o Projeto
Antes de construir a imagem Docker, compile o projeto Spring Boot para gerar o arquivo JAR.

##### Com maven 
```
./mvnw clean package
```

##### Com Gradle 
```
./gradlew clean build
```
Certifique-se de que o arquivo coletaAi-0.0.1-SNAPSHOT.jar foi criado no diretório target.

## Construir a Imagem Docker
Execute o seguinte comando no diretório onde o Dockerfile está localizado para construir a imagem Docker:

```
docker build -t meu-spring-boot-app --build-arg JAR_FILE=target/coletaAi-0.0.1-SNAPSHOT.jar .
```

Executar o Container Docker
Depois que a imagem Docker for construída com sucesso, execute um container usando o seguinte comando:

```
docker run -p 8080:8080 meu-spring-boot-app
```
Isso mapeia a porta 8080 do container para a porta 8080 da sua máquina, permitindo que você acesse a aplicação em http://localhost:8080.

Verificar a Aplicação
Abra um navegador web e navegue até http://localhost:8080 para verificar se a aplicação Spring Boot está funcionando corretamente.

## Resumo dos Comandos
### Criar o Dockerfile:


```
FROM eclipse-temurin:21-alpine
VOLUME /tmp
EXPOSE 8080
ARG JAR_FILE=target/coletaAi-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

### Construir o projeto:

```
./mvnw clean package  # Para projetos Maven
./gradlew clean build  # Para projetos Gradle
```

### Construir a imagem Docker:
```
docker build -t meu-spring-boot-app --build-arg JAR_FILE=target/coletaAi-0.0.1-SNAPSHOT.jar .
```

### Executar o container Docker:

```
docker run -p 8080:8080 meu-spring-boot-app
```

#### Notas Adicionais
Certifique-se de que o caminho para o arquivo JAR no Dockerfile corresponda ao caminho real.
Ajuste os comandos de build do Maven/Gradle conforme a configuração do seu projeto.
Verifique se a porta 8080 não está sendo usada por outra aplicação na sua máquina.
Seguindo esses passos, você poderá construir e executar um container Docker para sua aplicação Spring Boot com sucesso.





