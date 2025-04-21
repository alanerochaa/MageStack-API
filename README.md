# 🔮 MageStack API

Esta API RESTful permite a criação, gerenciamento e compartilhamento de decks de Magic: The Gathering (MTG), oferecendo funcionalidades inspiradas na plataforma Moxfield. Os usuários podem montar decks, adicionar cartas, visualizar estatísticas, curtir e comentar decks, além de buscar cartas por diversos critérios.

A documentação segue o padrão OpenAPI.

---

## ⚙️ Funcionalidades

- Cadastro e gerenciamento de usuários
- Criação, edição e exclusão de decks
- Adição de cartas aos decks
- Curtidas e comentários em decks
- Listagem e busca de cartas
- Consulta detalhada com uso de DTOs

---

## 🔧 Rotas da API

| Método | Rota                              | Descrição                                   | Status Codes         |
|--------|-----------------------------------|---------------------------------------------|----------------------|
| GET    | /decks                            | Listar todos os decks                       | 200, 500             |
| GET    | /decks/{id}                       | Buscar um deck pelo ID                      | 200, 404, 500        |
| GET    | /cartas                           | Listar todas as cartas                      | 200, 500             |
| GET    | /cartas/{id}                      | Buscar carta por ID                         | 200, 404, 500        |
| GET    | /usuarios                         | Listar todos os usuários                    | 200, 500             |
| GET    | /usuarios/{id}                    | Buscar usuário por ID                       | 200, 404, 500        |
| GET    | /decks/{id}/comentarios           | Listar comentários de um deck específico    | 200, 404, 500        |
| POST   | /decks                            | Criar novo deck                             | 201, 400, 500        |
| POST   | /cartas                           | Criar nova carta                            | 201, 400, 500        |
| POST   | /usuarios                         | Criar novo usuário                          | 201, 400, 500        |
| POST   | /comentarios                      | Criar novo comentário                       | 201, 400, 500        |
| POST   | /decks/{id}/curtir                | Curtir um deck                              | 200, 404, 500        |
| POST   | /decks/{id}/comentarios           | Adicionar comentário a um deck              | 201, 400, 404, 500   |
| PUT    | /decks/{id}                       | Atualizar informações de um deck            | 200, 400, 404, 500   |
| PUT    | /cartas/{id}                      | Atualizar informações de uma carta          | 200, 400, 404, 500   |
| PUT    | /usuarios/{id}                    | Atualizar informações de um usuário         | 200, 400, 404, 500   |
| PUT    | /comentarios/{id}                 | Atualizar comentário                        | 200, 400, 404, 500   |
| DELETE | /decks/{id}                       | Deletar deck por ID                         | 204, 404, 500        |
| DELETE | /cartas/{id}                      | Deletar carta por ID                        | 204, 404, 500        |
| DELETE | /usuarios/{id}                    | Deletar usuário por ID                      | 204, 404, 500        |

---

# 📦 DTOs (Data Transfer Objects)
As datas seguem o padrão ISO 8601 (formato UTC), garantindo consistência no tratamento entre diferentes sistemas e fusos horários.


# 🧩 DeckDTO
Representa um deck criado pelo usuário, contendo suas informações básicas, cartas incluídas e comentários associados.
```json
{
  "decks": [
    {
      "id": 1,
      "nome": "Deck Controle Azul",
      "formato": "Commander",
      "descricao": "Deck focado em controle e anulação de mágicas.",
      "usuarioId": 5,
      "publico": true,
      "dataCriacao": "2025-04-19T15:30:00Z",
      "cartas": [
        {
          "id": 101,
          "nome": "Counterspell",
          "tipo": "Instantâneo",
          "cor": "Azul",
          "custoMana": "UU",
          "quantidade": 2
        },
        {
          "id": 102,
          "nome": "Ponder",
          "tipo": "Feitiço",
          "cor": "Azul",
          "custoMana": "U",
          "quantidade": 4
        }
      ],
      "comentarios": []
    },
    {
      "id": 2,
      "nome": "Deck Aggro Vermelho",
      "formato": "Standard",
      "descricao": "Deck focado em agressão rápida e dano direto ao oponente.",
      "usuarioId": 6,
      "publico": true,
      "dataCriacao": "2025-04-20T10:00:00Z",
      "cartas": [
        {
          "id": 201,
          "nome": "Lightning Bolt",
          "tipo": "Feitiço",
          "cor": "Vermelha",
          "custoMana": "R",
          "quantidade": 3
        },
        {
          "id": 202,
          "nome": "Goblin Guide",
          "tipo": "Criatura",
          "cor": "Vermelha",
          "custoMana": "R",
          "quantidade": 4
        }
      ],
      "comentarios": []
    },
    {
      "id": 3,
      "nome": "Deck Ramp Verde",
      "formato": "Commander",
      "descricao": "Deck focado em acelerar a mana para jogar criaturas grandes rapidamente.",
      "usuarioId": 7,
      "publico": true,
      "dataCriacao": "2025-04-20T14:30:00Z",
      "cartas": [
        {
          "id": 301,
          "nome": "Llanowar Elves",
          "tipo": "Criatura",
          "cor": "Verde",
          "custoMana": "G",
          "quantidade": 4
        },
        {
          "id": 302,
          "nome": "Green Sun's Zenith",
          "tipo": "Feitiço",
          "cor": "Verde",
          "custoMana": "XGG",
          "quantidade": 2
        }
      ],
      "comentarios": []
    }
  ]
}
```

# 💬 ComentarioDTO
Define um comentário dentro de um deck.
```json
{
  "comentarios": [
    {
      "id": 15,
      "deckId": 1,
      "usuarioId": 5,
      "mensagem": "Adorei a escolha de cartas!",
      "dataComentario": "2025-04-19T16:00:00Z"
    },
    {
      "id": 16,
      "deckId": 2,
      "usuarioId": 7,
      "mensagem": "Esse deck tem uma boa sinergia, gostei bastante da escolha das criaturas!",
      "dataComentario": "2025-04-19T17:30:00Z"
    },
    {
      "id": 17,
      "deckId": 3,
      "usuarioId": 8,
      "mensagem": "Interessante a combinação de feitiços! Isso pode ser bem útil em partidas longas.",
      "dataComentario": "2025-04-19T18:15:00Z"
    }
  ]
}

```

# 👤 UsuarioDTO
Contém os dados públicos de um usuário e a quantidade de decks criados por ele.
```json
{
  "usuarios": [
    {
      "id": 5,
      "nome": "Julia Silva",
      "email": "Julia.silva@example.com",
      "decksCriados": 22,
      "dataCadastro": "2025-04-10T09:00:00Z"
    },
    {
      "id": 6,
      "nome": "Carlos Oliveira",
      "email": "carlos.oliveira@example.com",
      "decksCriados": 15,
      "dataCadastro": "2025-04-12T14:30:00Z"
    },
    {
      "id": 7,
      "nome": "Mariana Souza",
      "email": "mariana.souza@example.com",
      "decksCriados": 30,
      "dataCadastro": "2025-04-15T11:45:00Z"
    }
  ]
}

```

# ⚠️ ErroDTO
Utilizado para padronizar o retorno de erros da API.
```json
{
  "erros": [
    {
      "codigo": 400,
      "mensagem": "Dados inválidos.",
      "detalhes": "O campo 'email' não pode ser vazio.",
      "timestamp": "2025-04-19T16:12:00Z"
    },
    {
      "codigo": 401,
      "mensagem": "Não autorizado.",
      "detalhes": "A autenticação falhou ou a sessão expirou.",
      "timestamp": "2025-04-19T16:14:00Z"
    },
    {
      "codigo": 403,
      "mensagem": "Acesso proibido.",
      "detalhes": "Você não tem permissão para acessar este recurso.",
      "timestamp": "2025-04-19T16:16:00Z"
    },
    {
      "codigo": 404,
      "mensagem": "Recurso não encontrado.",
      "detalhes": "O recurso solicitado não existe ou foi removido.",
      "timestamp": "2025-04-19T16:18:00Z"
    },
    {
      "codigo": 500,
      "mensagem": "Erro interno no servidor.",
      "detalhes": "Ocorreu um erro inesperado no servidor. Tente novamente mais tarde.",
      "timestamp": "2025-04-19T16:20:00Z"
    },
    {
      "codigo": 405,
      "mensagem": "Método não permitido.",
      "detalhes": "O método HTTP não é permitido para este recurso.",
      "timestamp": "2025-04-19T16:22:00Z"
    },
    {
      "codigo": 404,
      "mensagem": "Deck não encontrado.",
      "detalhes": "Verifique se o ID do deck está correto.",
      "timestamp": "2025-04-19T16:10:00Z"
    }
  ]
}

```

## 📑 Arquivo OpenAPI

A especificação completa da API está disponível no arquivo `openapi.yaml`.

Você pode validar a especificação usando o [Swagger Editor](https://editor.swagger.io).


## 🛠️ Tecnologias Utilizadas

- ☕ [Java 17+](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
- 🚀 [Spring Boot](https://spring.io/projects/spring-boot)
- 🗃️ [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- 🔁 [Hibernate](https://hibernate.org/)
- 🐘 [PostgreSQL](https://www.postgresql.org/)
- 📦 [Maven](https://maven.apache.org/)
- 📜 [OpenAPI / Swagger](https://swagger.io/specification/)


![Java](https://img.shields.io/badge/Java-17+-red)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-2.5-blue)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13-blue)
![Maven](https://img.shields.io/badge/Maven-3.8-green)
![OpenAPI](https://img.shields.io/badge/OpenAPI-3.0-yellow)



## 🧪 Instalação e Execução Local
1. Clone o repositório:
```bash
git clone https://github.com/alanerochaa/magestack-api.git
```
2. Navegue até a pasta:
```bash
cd magestack-api
```
3. Configure o banco de dados PostgreSQL e atualize o application.properties com suas credenciais.

4. Rode o projeto:

```bash
./mvnw spring-boot:run
```
5. Acesse:
```bash

* API: http://localhost:8080

* Swagger: http://localhost:8080/swagger-ui.html
```

# 📬 Contribuindo

Contribuições são bem-vindas! Se você tiver sugestões, bugs ou ideias de melhorias, fique à vontade para abrir uma issue ou enviar um pull request.

1. Fork o projeto
2. Crie sua branch: `git checkout -b minha-feature`
3. Faça suas alterações e commit: `git commit -m 'Minha nova feature'`
4. Envie para a branch principal: `git push origin minha-feature`
5. Abra um Pull Request


# 📝 Licença 

Este projeto está licenciado sob a Licença MIT - consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👩🏻‍💻 Autora
Desenvolvido por Alane Rocha  
🔗 [LinkedIn](https://www.linkedin.com/in/alanersilva/)  
🐙 [GitHub](https://github.com/alanerochaa)
