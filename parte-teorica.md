# Parte Teórica do trabalho do 4o bimestre de POO.

**Aluno(s):** Nycolas Motta Braga Porto, Bruno Kenzo Kawano
**Turma:** 2ano
**Disciplina:** Programação Orientada a Objetos
**Professor(a):** João Paulo Biazotto

## 1. SPRING FRAMEWORK

O Spring Framework é uma estrutura para desenvolvimento de aplicações Java. Ele facilita a organização do código e o gerenciamento dos componentes do sistema, reduzindo a necessidade de criar e controlar manualmente objetos e suas dependências. Seu objetivo é tornar as aplicações mais organizadas, flexíveis e fáceis de manter.
Um de seus conceitos centrais é a Inversão de Controle (IoC): em vez de a própria aplicação controlar diretamente a criação e o ciclo de vida de todos os objetos, essa responsabilidade passa para o Spring. A Injeção de Dependência (DI) é uma forma de aplicar essa ideia, pois o Spring fornece a um componente os objetos de que ele precisa. Um Bean é um objeto criado, configurado e gerenciado pelo container do Spring.

## 2. SPRING BOOT

O Spring Framework oferece a base e os recursos para desenvolver aplicações Java. Já o Spring Boot utiliza essa estrutura e simplifica sua configuração e inicialização. Ele oferece auto-configuração, que prepara componentes de acordo com as dependências e configurações do projeto; starters, que agrupam dependências comuns; e servidor web embutido, como o Tomcat.
Com isso, é necessário escrever menos configurações manualmente e a aplicação pode ser executada de forma independente (standalone), geralmente como um arquivo JAR. Portanto, o Spring Boot não substitui o Spring Framework: ele facilita o uso do ecossistema Spring.

## 3. API E API REST

API é uma interface que permite que diferentes programas se comuniquem e troquem informações. Uma API REST organiza essa comunicação em torno de recursos, que representam elementos do sistema, como os quartos de um hotel. Cada recurso pode ser acessado por um endpoint, isto é, um endereço específico da API.
A comunicação acontece por requisições e respostas HTTP. A requisição é enviada pelo cliente e informa o que deseja fazer; a resposta é devolvida pelo servidor com o resultado e um código de status. É comum que os dados sejam enviados no formato JSON, que representa informações de maneira estruturada e simples de transmitir.

## 4. MÉTODOS HTTP E CRUD

Os métodos HTTP indicam a operação desejada sobre um recurso. GET é usado para consultar dados; POST, para criar; PUT, para atualizar; e DELETE, para remover. Essas operações correspondem ao conceito CRUD: Create (criar), Read (consultar), Update (atualizar) e Delete (excluir).
No SistemaHotel, por exemplo, GET /quartos lista os quartos, GET /quartos/1 consulta o quarto de identificador 1, POST /quartos cadastra um quarto, PUT /quartos/1 atualiza esse quarto e DELETE /quartos/1 o remove.

## 5. CÓDIGOS DE STATUS HTTP

Os códigos de status informam o resultado de uma requisição. No SistemaHotel, os principais são:
_200 OK:_ a operação foi realizada com sucesso, como ao listar os quartos.
_201 Created:_ um novo quarto foi cadastrado com sucesso.
_204 No Content:_ a operação foi concluída, mas não há conteúdo para retornar, como em uma exclusão bem-sucedida.
_400 Bad Request:_ a requisição contém dados inválidos, como um valor de diária em formato incorreto.
_404 Not Found:_ o quarto solicitado não foi encontrado.
_500 Internal Server Error:_ ocorreu uma falha inesperada no servidor durante o processamento da requisição.

## 6. JSON E CONVERSÃO DE OBJETOS

JSON é um formato leve e estruturado usado para representar e transportar dados entre aplicações. Em uma API, um objeto Java, como Quarto, pode ser convertido para JSON antes de ser enviado ao cliente. No Spring Boot, essa conversão normalmente é realizada pela biblioteca Jackson, integrada aos conversores HTTP. Assim, o desenvolvedor pode retornar um objeto Java e o Spring realiza a transformação para JSON automaticamente.

## 7. PRINCIPAIS ANOTAÇÕES DO SPRING

**@SpringBootApplication:** identifica a classe principal e reúne configurações necessárias para iniciar a aplicação Spring Boot.
**@RestController:** indica que a classe recebe requisições HTTP e retorna dados diretamente na resposta, geralmente em JSON.
**@RequestMapping:** define um caminho ou mapeamento geral para uma classe ou método do controller.
**@GetMapping:** associa um método a requisições GET, usadas para consultas.
**@PostMapping:** associa um método a requisições POST, usadas para criar recursos.
**@PutMapping:** associa um método a requisições PUT, usadas para atualizar recursos.
**@DeleteMapping:** associa um método a requisições DELETE, usadas para remover recursos.
**@PathVariable:** captura um valor que faz parte do caminho da URL, como o identificador em /quartos/1.
**@RequestParam:** recebe parâmetros informados na URL após o sinal de interrogação, como tipo=DUPLO.
**@RequestBody:** recebe os dados enviados no corpo da requisição, normalmente em JSON, e os converte para um objeto Java.
**@Service:** identifica uma classe que contém regras e operações da aplicação, permitindo que o Spring a gerencie como um Bean.

## 8. CONTROLLER, SERVICE E REPOSITORY

A arquitetura em camadas separa as responsabilidades da aplicação. O Controller recebe as requisições HTTP, interpreta os dados enviados e devolve as respostas. O Service concentra as regras de negócio, como validar informações, verificar condições e executar operações. O Repository é responsável pelo acesso e pela persistência dos dados, normalmente em um banco de dados.
No projeto inicial do SistemaHotel, os dados podem ficar armazenados em uma lista em memória, sem Repository ou banco de dados. Mesmo assim, separar Controller e Service ajuda a manter o código organizado e evita concentrar todas as responsabilidades em uma única classe.

## 9. DIFERENÇA ENTRE IOC E INJEÇÃO DE DEPENDÊNCIA

Inversão de Controle é o princípio segundo o qual o Spring assume o controle da criação e do gerenciamento dos componentes. Injeção de Dependência é o mecanismo pelo qual o Spring entrega a um componente as dependências de que ele precisa.
Por isso, o QuartoController não precisa executar new QuartoService(). Como QuartoService é registrado no Spring, por exemplo com @Service, o contêiner cria e gerencia esse Bean e pode fornecê-lo ao controller por injeção de dependência. Isso reduz o acoplamento e facilita alterações e testes.

## 10. SERVIDOR EMBUTIDO E AUTO-CONFIGURAÇÃO

Não é necessário instalar e configurar manualmente um servidor Tomcat porque o Spring Boot pode incluir um servidor web embutido nas dependências do projeto. Ao iniciar a aplicação, esse servidor é executado junto com ela e permite receber requisições HTTP, por exemplo em localhost:8080.
Auto-configuração significa que o Spring Boot identifica as dependências presentes e prepara automaticamente configurações comuns para que a aplicação funcione. Neste projeto, exemplos são a configuração do servidor web e do tratamento de requisições HTTP, além dos conversores que transformam objetos Java em JSON. Isso diminui a quantidade de configurações que o desenvolvedor precisa fazer manualmente.
