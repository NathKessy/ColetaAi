# ColetaAi - Sistema de Gestão de Resíduos
### Descrição
O ColetaAi é um projeto de gerenciamento inteligente de resíduos, focado em otimizar a coleta de lixo por meio de rastreamento em tempo real, agendamento automático com base na capacidade dos recipientes e notificações aos moradores sobre a separação de resíduos e datas de coleta.

Este repositório contém uma aplicação desenvolvida em Java Spring Boot com práticas de DevOps implementadas, utilizando GitHub Actions para CI/CD e Docker para containerização da aplicação.

### Requisitos
Antes de executar o projeto, certifique-se de ter as seguintes ferramentas instaladas em seu ambiente de desenvolvimento:

- Docker
- Java 17
- Maven
- Git

### Estrutura do Projeto
- /src: Contém o código-fonte da aplicação Java Spring Boot.
- /Dockerfile: Arquivo usado para construir a imagem Docker da aplicação.
- /.github/workflows/ci-cd.yml: Arquivo de configuração do pipeline CI/CD com GitHub Actions.

### Instruções de Execução

1. Clonar o Repositório
   Primeiro, clone o repositório para a sua máquina local:

```sh
git clone https://github.com/seu-usuario/coletaai.git
cd coletaai
```

2. Compilar a Aplicação
   Utilize o Maven para compilar o código e rodar os testes. Certifique-se de que a JDK 17 está configurada corretamente no ambiente.

```sh
mvn clean install
```

Se a compilação for bem-sucedida, o projeto será empacotado e estará pronto para ser containerizado.

3. Build da Imagem Docker
   Para criar uma imagem Docker da aplicação, execute o seguinte comando. Ele utiliza o arquivo Dockerfile que está na raiz do projeto:

```sh
docker build -t coletaai .
```

4. Executar a Aplicação com Docker
   Após o build, você pode rodar o container da aplicação com o seguinte comando:

```sh
docker run -d -p 8080:8080 coletaai
```

Este comando mapeia a porta 8080 do container para a porta 8080 da sua máquina local. A aplicação estará acessível em:

```sh
http://localhost:8080
```

5. Pipeline CI/CD com GitHub Actions
   O repositório também está configurado com um pipeline CI/CD para automatizar o build, teste e deploy da aplicação. O pipeline é acionado automaticamente quando há um push para as branches main ou staging.

**Configurações do Pipeline**
O arquivo de pipeline está localizado em .github/workflows/ci-cd.yml. Aqui está um resumo das etapas:

- **Build:** Compila o código Java com Maven.
- **Testes:** Roda os testes da aplicação.
- **Build Docker:** Constrói a imagem Docker localmente utilizando o Dockerfile no repositório.
- **Deploy:** Realiza o deploy em ambientes de staging e produção.

6. Deploy Local
   Caso você queira simular um deploy em ambiente de staging ou produção localmente, você pode executar o comando Docker com a imagem gerada. Veja um exemplo de como rodar o deploy:

- **Staging:**
```sh
docker run -d -p 8080:8080 coletaai
```

- **Produção (simulado):**
```sh
docker run -d -p 80:8080 coletaai
```
### Customizando o Pipeline
Caso deseje personalizar o pipeline, você pode modificar o arquivo .github/workflows/ci-cd.yml. Ele contém as etapas para build, teste e deploy da aplicação.

Exemplo de ajuste no pipeline:

```sh
- name: Build Docker image
  run: docker build -t coletaai:${{ github.sha }} .
```
Este comando cria uma nova imagem a partir do Dockerfile a cada commit, utilizando o hash do commit (${{ github.sha }}) como tag.

### Possíveis Erros e Soluções
**Problema: Acesso negado ao localhost:8080**
- Verifique se o container está rodando corretamente com o comando:

```sh
docker ps
```

- Certifique-se de que a porta 8080 não está sendo usada por outro processo.

### Problema: Falha no build da imagem Docker
- Verifique se o arquivo Dockerfile está na raiz do projeto.
- Certifique-se de que a JDK 17 e o Maven estão corretamente instalados e configurados.

### Contribuição
Sinta-se à vontade para abrir uma issue ou enviar um pull request com sugestões de melhorias e correções.

### Licença
Este projeto está licenciado sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.