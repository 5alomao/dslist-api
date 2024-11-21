# DS List API

## Descrição do Projeto

A DS List API é uma **API REST** desenvolvida para gerenciar listas de jogos. O projeto foi construído com **Java 17** e **Spring Boot**, utilizando um banco de dados **H2** em desenvolvimento e **PostgreSQL** em produção. O deploy foi realizado na **Railway** para acesso na nuvem.

## Estrutura do Projeto

A estrutura do projeto é organizada da seguinte forma:

- **Projections:** Interfaces para consultas específicas ao banco de dados, retornando dados customizados.
- **DTO:** Classes utilizadas para transferir dados entre a API e os consumidores.
- **Entities:** Representações das tabelas do banco de dados em forma de classes Java.
- **Repositories:** Interfaces que gerenciam a comunicação com o banco de dados.
- **Services:** Contêm a lógica de negócio da aplicação.
- **Controllers:** Gerenciam as requisições HTTP e retornam as respostas adequadas.
  
## Endpoints

## `POST /lists/{listId}/replacement`

**Descrição**: Reordena os jogos em uma lista específica.

**Corpo da Requisição**:
```json
{
  "sourceIndex": 0,
  "destinationIndex": 2
}
```
### Resposta
- **200: OK** caso a operação seja feita com sucesso.
- **404: Not Found** caso a lista não exista.
```json
{
	"error": "Lista não encontrada",
	"status": 404
}
```
- **400: Bad Request** caso os índices sejam inválidos.
```json
{
	"error": "Índices inválidos",
	"status": 400
}
```


## `GET /lists/{listId}/games}`

**Descrição:** Retorna os jogos de uma lista específica.

### Resposta
- **200: OK** caso a operação seja feita com sucesso.
```json
[
	{
		"id": 1,
		"title": "Mass Effect Trilogy",
		"year": 2012,
		"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/1.png",
		"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!"
	},
	{
		"id": 2,
		"title": "Red Dead Redemption 2",
		"year": 2018,
		"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/2.png",
		"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!"
	},
	{
		"id": 3,
		"title": "The Witcher 3: Wild Hunt",
		"year": 2014,
		"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/3.png",
		"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!"
	}
]
```
- **404: Not Found** caso a lista não exista.
```json
{
	"error": "Lista não encontrada",
	"status": 404
}
```
  
## `GET /lists`

**Descrição:** Retorna todas as listas de jogos.

### Resposta
- **200: OK** caso a operação seja feita com sucesso.
```json
[
	{
		"id": 1,
		"name": "Aventura e RPG"
	},
	{
		"id": 2,
		"name": "Jogos de plataforma"
	}
]
```

## `GET /games/{gameId}`

**Descrição:** Retorna os detalhes de um jogo específico.

### Resposta
- **200: OK** caso a operação seja feita com sucesso.
```json
{
	"id": 3,
	"title": "The Witcher 3: Wild Hunt",
	"year": 2014,
	"genre": "Role-playing (RPG), Adventure",
	"platforms": "XBox, Playstation, PC",
	"score": 4.7,
	"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/3.png",
	"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!",
	"longDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus dolorum illum placeat eligendi, quis maiores veniam. Incidunt dolorum, nisi deleniti dicta odit voluptatem nam provident temporibus reprehenderit blanditiis consectetur tenetur. Dignissimos blanditiis quod corporis iste, aliquid perspiciatis architecto quasi tempore ipsam voluptates ea ad distinctio, sapiente qui, amet quidem culpa."
}
```
- **404: Not Found** caso o jogo não exista.
```json
{
	"error": "Jogo não encontrado!",
	"status": 404
}
```

## `GET /games`

**Descrição:** Retorna a lista de todos os jogos.

### Resposta
- **200: OK** caso a operação seja feita com sucesso.
```json
[
	{
		"id": 1,
		"title": "Mass Effect Trilogy",
		"year": 2012,
		"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/1.png",
		"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!"
	},
	{
		"id": 2,
		"title": "Red Dead Redemption 2",
		"year": 2018,
		"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/2.png",
		"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!"
	},
	{
		"id": 3,
		"title": "The Witcher 3: Wild Hunt",
		"year": 2014,
		"imgUrl": "https://raw.githubusercontent.com/devsuperior/java-spring-dslist/main/resources/3.png",
		"shortDescription": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit esse officiis corrupti unde repellat non quibusdam! Id nihil itaque ipsum!"
	}
]
```


# Como Executar o Projeto

Para executar este projeto na sua máquina local, siga os passos abaixo:

## Pré-requisitos

- Java 17 instalado.
- Maven (ou Gradle) para gerenciamento de dependências.
- IDE (como IntelliJ IDEA ou Eclipse) para desenvolvimento.

## Passos

1. Clone o repositório:

```bash
git clone https://github.com/5alomao/dslist-api.git
cd dslist-api
```

2. Navegue até a pasta do projeto.

3. Execute o projeto com **Maven** ou **Gradle**
- Maven: `mvn spring-boot:run`
- Gradle: `gradle bootRun`

4. Acesse a aplicação localmente:
- URL padrão: `http://localhost:8080`
  
## Testes

Sinta-se à vontade para testar a API utilizando ferramentas como Postman, Insomnia ou cURL.

### Exemplo de Teste com cURL

```bash
curl -X GET http://localhost:8080/games/1
```
