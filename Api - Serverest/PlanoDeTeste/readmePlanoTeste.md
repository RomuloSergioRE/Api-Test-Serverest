🧪 Plano de Testes– API de Serverest

### Identificação do Projeto

- **Projeto:** API - Serverest 

- **Responsável pelo Teste:** Rômulo Sérgio

- **Ferramenta de Teste:** Postman

---

### **Objetivo do Teste**

- Validar a funcionalidade de Login como administrados para gerenciar os produtos
- Validar as funcionalidades de Buscar, Criar, Alterar e Deletar Usuário 
- Validar as funcionalidades de Buscar, Criar, Alterar e Deletar Produtos
- Verificar os códigos  HTTP estão de acordo com a documentação 

---

### **Endpoints da API**

**Base URL: https://serverest.dev/**

1 - Login	

| Metodo | Endpoint | Funcionalidade |
| ------ | -------- | -------------- |
| POST   | /login   | Realizar login |

---

2 - Usuário

| Metodo | Endpoint      | Funcionalidade            |
| ------ | ------------- | ------------------------- |
| GET    | /usuarios     | Listar Usuários Cadastros |
| GET    | /usuarios/:id | Buscar Usuários por ID    |
| POST   | /usuarios     | Cadastrar Usuário         |
| PUT    | /usuarios/:id | Alterar Dados do Usuário  |
| DELETE | /usuarios/:id | Deletar um Usuário        |

---

3 - Produto

| Metodo | Endpoint      | Funcionalidade            |
| ------ | ------------- | ------------------------- |
| GET    | /produtos     | Listar Produtos Cadastros |
| GET    | /produtos/:id | Buscar Produtos por ID    |
| POST   | /produtos     | Cadastrar Produto         |
| PUT    | /produtos/:id | Alterar Dados do Produto  |
| DELETE | /produtos/:id | Deletar um Produtos       |

---

### Caso de Teste

1 - Funcionalidades do Login 

| ID       | Endpoint | Metodo | Descrição do teste                   | Dados de Entrada                                                   | Saída Esperada                                | Status Code |
| -------- | -------- | ------ | ------------------------------------ | ------------------------------------------------------------------ | --------------------------------------------- | ----------- |
| CT - 001 | /login   | POST   | Entrar no sistema como adm           | {<br>  "email": "fulano@qa.com",<br>  "password": "teste"<br>}<br> | Login realizado com sucesso                   | 200         |
| CT - 002 | /login   | POST   | Entrar no sistema com senha invalida | {<br>  "email": "fulano@qa.com",<br>  "password": "teste2"<br>}    | Não seja possível realizar o login no sistema | 401         |

---

2 - Funcionalidades do Usuário  

| ID       | Endpoint      | Metodo | Descrição do teste                                | Dados de Entrada                                                                                                                  | Saída Esperada                        | Status Code |
| -------- | ------------- | ------ | ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ----------- |
| CT - 001 | /usuarios     | GET    | Listas usuários cadastrados                       | -                                                                                                                                 | Lista de usuários em json             | 200         |
| CT - 002 | /usuarios/:id | GET    | Buscar usuário pelo ID                            | ID valido de 16 caracteres  Exemplo - 0uxuPY0cbmQhpEz1                                                                            | Dados do usuário do ID                | 200         |
| CT - 003 | /usuarios/:id | GET    | Buscar usuário pelo ID invalido                   | ID invalido de  menos16 caracteres  Exemplo - 0uxuPY0cb                                                                           | O ID deve ter 16 caracteres           | 400         |
| CT - 004 | /usuarios     | POST   | Cadastrar um usuário como ADM                     | {<br>  "nome": "romulo",<br>  "email": "romulo@teste.com ","password": "teste",<br>  "administrador": "true"<br>}<br>             | Usuario cadastrado com ID             | 201         |
| CT - 005 | /usuarios     | POST   | Cadastrar um usuário como ADM com EMAIL existente | {<br>  "nome": "Fulano da Silva",<br>  "email": "beltrano@qa.com.br",<br>  "password": "teste",<br>  "administrador": "true"<br>} | Email ja utilizado                    | 400         |
| CT - 006 | /usuarios/:id | PUT    | Alterar os dados do meu usuario                   | {<br>  "nome": "romulo sergio",<br>  "email": "romulo@teste.com ","password": "teste",<br>  "administrador": "true"<br>}<br>      | Os dados foram alterados              | 200         |
| CT - 007 | /usuarios/:id | DELETE | Excluir um usuario                                | - ID valido                                                                                                                       | Registro excluído com sucesso         | 200         |

---

3 - Funcionalidades do Produto OBS: só pode cadastrar produtos se o Usuário for Administrador 

| ID        | Endpoint      | Metodo | Descrição do teste                                                                                              | Dados de Entrada                                                                                | Saída Esperada                                           | Status Code |
| --------- | ------------- | ------ | --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------- | ----------- |
| CT - 001  | /produtos     | GET    | Listar Produtos Cadastros                                                                                       | -                                                                                               | Lista de produtos em json                                | 200         |
| CT -  002 | /produtos/:id | GET    | Buscar Produto por ID                                                                                           | - ID Valido                                                                                     | Produto do ID                                            | 200         |
| CT - 003  | /produtos/:id | GET    | Buscar Produto por ID invalido                                                                                  | - ID invalido exemplo: <br>BeeJh5lz3k6kSIzA<br>                                                 | Produto não encontrado                                   | 400         |
| CT - 004  | /produtos     | POST   | Cadastrar um Produto OBS: para cadastrar um produto precisa esta logado como adm                                | {<br>"nome": "Teste",<br>  "preco": 470,<br>  "descricao": "teste",<br>  "quantidade": 381<br>} | Produto Cadastrado                                       | 201         |
| CT - 005  | /produtos     | POST   | Cadastrar um Produto com nome que ja foi cadastrado OBS: para cadastrar um produto precisa esta logado como adm | {<br>"nome": "Teste",<br>  "preco": 470,<br>  "descricao": "teste",<br>  "quantidade": 381<br>} | Já existe um produto com esse nome                       | 400         |
| CT - 005  | /produtos     | POST   | Cadastrar um Produto OBS: o cadastro deve ser feito com um usuário normal                                       | {<br>"nome": "Teste",<br>  "preco": 470,<br>  "descricao": "teste",<br>  "quantidade": 381<br>} | Rota exclusiva para admin                                | 403         |
| CT - 006  | /produtos/:id | PUT    | Alterar dados do produto pelo ID OBS: para cadastrar um produto precisa esta logado como adm                    | {<br>"nome": "Teste",<br>  "preco": 470,<br>  "descricao": "teste",<br>  "quantidade": 381<br>} | Alterado com sucesso                                     | 200         |
| CT - 007  | /produtos/:id | DELETE | Excluir um produto pelo ID OBS: para cadastrar um produto precisa esta logado como adm                          | - ID valido                                                                                     | Registro excluído com sucesso                            | 200         |

---

**Ferramentas Utilizadas**

- **Postman** (coleções manuais)
    
- **Documentação da API** (Swagger)