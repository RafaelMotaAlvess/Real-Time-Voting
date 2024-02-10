<h1 align="center">
  <br>🗳️ Real-Time Voting<br/>
  <br/>
  <img src="./.github/docs/wallpaper.png">
  <a href="https://wakatime.com/badge/user/0cca606b-99f7-4d43-8228-7f249bc17f26/project/018d8409-c4f4-4610-8d5b-5592c5680675"> <img src="https://wakatime.com/badge/user/0cca606b-99f7-4d43-8228-7f249bc17f26/project/018d8409-c4f4-4610-8d5b-5592c5680675.svg"></a>
</h1>

## Introductions 📖

<li><a href="#mag-about">🔎 About</a></li>
<li><a href="#wrench-technologies">🔧 Technologies</a></li>
<li><a href="#sparkles-how-to-run">✨ How to Run</a></li>
<li><a href="#triangular_flag_on_post-http-endpoints">🚩 HTTP Endpoints</a></li>
<li><a href="#triangular_flag_on_post-websockets-endpoint">🚩 WebSockets Endpoint</a></li>
<li><a href="#page_with_curl-license">📃 License</a></li>

## :mag: About

**Real-Time Voting** is an system allows users to create polls and vote on available options. The system updates votes in real time and generates a ranking of options based on the votes received.


## :wrench: Technologies

- <a target="_blank" href="https://www.typescriptlang.org">TypeScript</a>
- <a target="_blank" href="https://developer.mozilla.org/pt-BR/docs/Web/API/WebSockets_API">WebSockets</a>
- <a target="_blank" href="https://fastify.dev">Fastify</a>
- <a target="_blank" href="https://www.prisma.io">Prisma</a>
- <a target="_blank" href="https://www.postgresql.org">PostgreSQL</a>
- <a target="_blank" href="https://redis.io">Redis</a>
- <a target="_blank" href="https://zod.dev">Zod</a>

## :sparkles: How to Run

- ### **Prerequisites**
  - **Git**
  - **NodeJS** 
  - **Docker** 


### 1. Make a clone of the repository.

```bash
  $ git clone https://github.com/RafaelMotaAlvess/Real-Time-Voting.git
```

### 2. Install dependencies.

```bash
  $ npm install
```

### 3. In the project folder, you will find a file named `example.env` Make a copy of it and rename it to `.env`.


### 4. Setup PostgreSQL and Redis.

```bash
    docker compose up -d
```

### 5. Run application.

```bash
    npm run dev
```

### 6. Test it! i testing with [Postman](https://www.postman.com/). 


## :triangular_flag_on_post: HTTP Endpoints

| Method                      | Description                |
| --------------------------- | -------------------------- |
| `POST /polls`               | Create a new poll          |
| `POST /polls/:pollId/votes` | Add a vote to specific poll |
| `GET /polls/:pollId`        | Return data from a single poll      |

### POST `/polls`
#### Request body

```json
{
  "title": "Qual a melhor linguagem de programação?",
  "options": [
    "JavaScript",
    "Java",
    "PHP",
    "C#"
  ]
}
```

#### Response body

```json
{
  "pollId": "194cef63-2ccf-46a3-aad1-aa94b2bc89b0"
}
```

### GET `/polls/:pollId`
#### Response body

```json
{
	"poll": {
		"id": "e4365599-0205-4429-9808-ea1f94062a5f",
		"title": "Qual a melhor linguagem de programação?",
		"options": [
			{
				"id": "4af3fca1-91dc-4c2d-b6aa-897ad5042c84",
				"title": "JavaScript",
				"score": 1
			},
			{
				"id": "780b8e25-a40e-4301-ab32-77ebf8c79da8",
				"title": "Java",
				"score": 0
			},
			{
				"id": "539fa272-152b-478f-9f53-8472cddb7491",
				"title": "PHP",
				"score": 0
			},
			{
				"id": "ca1d4af3-347a-4d77-b08b-528b181fe80e",
				"title": "C#",
				"score": 0
			}
		]
	}
}
```

### POST `/polls/:pollId/votes`
#### Request body

```json
{
  "pollOptionId": "31cca9dc-15da-44d4-ad7f-12b86610fe98"
}
```

## :triangular_flag_on_post: WebSockets Endpoint

### ws `/polls/:pollId/results`

#### Message

```json
{
  "pollOptionId": "da9601cc-0b58-4395-8865-113cbdc42089",
  "votes": 2
}
```

## :page_with_curl: License

The project is under the license [MIT license](./LICENSE).

---

<sup>This application was developed under the mentorship of [Rocketseat](https://www.rocketseat.com.br).</sup>
