# REST App

## Descrição
Este é um projeto de demonstração de uma aplicação RESTful desenvolvida com Spring Boot. A aplicação fornece endpoints para saudações e operações matemáticas básicas.

## Funcionalidades
- **Saudações**: Endpoint para gerar saudações personalizadas.
- **Operações Matemáticas**: Endpoints para realizar operações como soma, subtração, multiplicação, divisão, média e raiz quadrada.
- **Tratamento de Exceções**: Manipulação personalizada de erros para operações inválidas.

## Tecnologias Utilizadas
- **Java 21**
- **Spring Boot 3.5.11**
- **Maven** para gerenciamento de dependências
- **Spring Web** para criação de APIs REST

## Pré-requisitos
- Java 21 ou superior instalado
- Maven instalado

## Como Executar
1. Clone o repositório.
2. Navegue até o diretório do projeto: `cd rest-app`
3. Execute o comando: `mvn spring-boot:run`
4. A aplicação estará rodando em `http://localhost:8080`

## Endpoints da API

### Saudações
- **GET /greeting**
  - Parâmetros: `name` (opcional, padrão: "Hello Wordl")
  - Exemplo: `GET /greeting?name=João`
  - Resposta: `{"id": 1, "content": "Hello, João!"}`

### Operações Matemáticas
Base URL: `/math`

- **GET /math/sum/{numberOne}/{numberTwo}**
  - Exemplo: `GET /math/sum/5/3`
  - Resposta: `8.0`

- **GET /math/subtraction/{numberOne}/{numberTwo}**
  - Exemplo: `GET /math/subtraction/5/3`
  - Resposta: `2.0`

- **GET /math/multiplication/{numberOne}/{numberTwo}**
  - Exemplo: `GET /math/multiplication/5/3`
  - Resposta: `15.0`

- **GET /math/division/{numberOne}/{numberTwo}**
  - Exemplo: `GET /math/division/6/2`
  - Resposta: `3.0`

- **GET /math/mean/{numberOne}/{numberTwo}**
  - Exemplo: `GET /math/mean/4/6`
  - Resposta: `5.0`

- **GET /math/squarer/{number}**
  - Exemplo: `GET /math/squarer/9`
  - Resposta: `3.0`

**Nota**: Todos os parâmetros numéricos devem ser valores válidos. Caso contrário, uma exceção `UnsupportedMathOperationException` será lançada com status 400.

## Estrutura do Projeto
```
src/
├── main/
│   ├── java/br/com/rest_app/
│   │   ├── RestAppApplication.java          # Classe principal
│   │   ├── controller/                      # Controladores REST
│   │   │   ├── GreetingController.java
│   │   │   └── MathController.java
│   │   ├── exception/                       # Tratamento de exceções
│   │   │   ├── ExceptionResponse.java
│   │   │   ├── UnsupportedMathOperationException.java
│   │   │   └── handler/CustomEntityResponseHandler.java
│   │   ├── math/                            # Lógica matemática
│   │   │   └── SimpleMath.java
│   │   ├── model/                           # Modelos de dados
│   │   │   └── Greeting.java
│   │   └── request/converters/              # Conversores
│   │       └── NumberConverter.java
│   └── resources/
│       └── application.properties
└── test/
    └── java/br/com/rest_app/
        └── RestAppApplicationTests.java
```

## Tratamento de Erros
A aplicação utiliza um manipulador de exceções personalizado que retorna respostas estruturadas em JSON para erros:
- **500 Internal Server Error**: Para exceções gerais.
- **400 Bad Request**: Para operações matemáticas com valores inválidos.

Exemplo de resposta de erro:
```json
{
  "timestamp": "2023-10-01T12:00:00.000+00:00",
  "message": "Please set a numeric value!",
  "details": "uri=/math/sum/abc/2"
}
```

## Testes
Para executar os testes, use: `mvn test`

## CI/CD
Este projeto utiliza GitHub Actions para integração contínua. O workflow de CI é executado em pushes e pull requests para as branches `main` e `master`, realizando build e testes automáticos com Maven e JDK 21.

## Contribuição
Sinta-se à vontade para contribuir com melhorias ou correções.

## Licença
Este projeto é uma demonstração e não possui licença específica.
