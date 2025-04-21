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
      "quantidade": 2,
      "descricao": "Anula uma mágica alvo.",
      "expansao": "Core Set 2020"
    },
    {
      "id": 102,
      "nome": "Ponder",
      "tipo": "Feitiço",
      "cor": "Azul",
      "custoMana": "U",
      "quantidade": 4,
      "descricao": "Olhe as três cartas do topo do seu grimório, embaralhe-as de volta e compre uma.",
      "expansao": "Lorwyn"
    }
  ],
  "comentarios": []
}
```

# 💬 ComentarioDTO
Define um comentário dentro de um deck.
```json

{
  "id": 15,
  "deckId": 1,
  "usuarioId": 5,
  "mensagem": "Adorei a escolha de cartas!",
  "dataComentario": "2025-04-19T16:00:00Z"
}
```


# 👤 UsuarioDTO
Contém os dados públicos de um usuário e a quantidade de decks criados por ele.
```json
{
  "id": 5,
  "nome": "Julia Silva",
  "email": "Julia.silva@example.com",
  "decksCriados": 22,
  "dataCadastro": "2025-04-10T09:00:00Z"
}
```

# ⚠️ ErroDTO
Utilizado para padronizar o retorno de erros da API.
```json
{
  "codigo": 404,
  "mensagem": "Deck não encontrado.",
  "detalhes": "Verifique se o ID do deck está correto.",
  "timestamp": "2025-04-19T16:10:00Z"
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
