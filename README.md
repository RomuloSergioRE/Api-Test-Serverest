# 🧪 QA com Postman - API Severest

Este repositório contém os testes de qualidade (QA) desenvolvidos com o [Postman](https://www.postman.com/) para validar os endpoints da **API Severest**.

## 📌 Objetivo

Garantir a estabilidade, segurança e corretude da API Severest através de testes automatizados e reutilizáveis com Postman. O projeto cobre testes de:

- Integração
- Fluxos funcionais
- Testes de autenticação
- Verificação de status codes
- Validando os Endpoints

---

## 🧰 Tecnologias e Ferramentas

- [Postman](https://www.postman.com/)
- [Swagger](https://swagger.io/)

---

## 📁 Estrutura do Projeto

```shell
Api - Serverest/
├── collection/             
│   └── Api - Serverest.postman_collection.json   
├── environment/            
│   └── Api-post-environment.postman_environment.json
├── PlanoDeTeste/             
│   └── readmePlanoDeTeste.md
└── README.md       
```

## 🧰 Pré-requisitos

- [Postman Desktop App](https://www.postman.com/downloads/) ou [Postman Web](https://web.postman.com/)
- Permissão de acesso às APIs que serão testadas
- Variáveis do ambiente corretamente preenchidas


## 📂 Coleções Disponíveis

As coleções estão localizadas na pasta `collection/` e organizadas por escopo funcional da API.

| Coleção | Descrição |
|--------|-----------|
| `Api - Serverest.postman_collection.json` | Testes: Create, Update, Delete e Read de usuario e produtos, teste de autenticação: login |


## 🌍 Ambientes

A pasta `environment/` contém os arquivos de ambiente utilizados pelas coleções. 

### Exemplo de variáveis no ambiente `dev`:

| Nome        | Valor exemplo                      | Descrição                       |
| ----------- | ---------------------------------- | ------------------------------- |
| `BASE_URL`   | `https://jsonplaceholder.typicode.com`   | URL base da API em ambiente dev |
| `Token`   | `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...`   | Token para autenticação do user|
| `ID_PRODUCT`   | `0uxuPY0cbmQhpEz1`   | Variavel usado para guardar o valor do id do produto |
| `ID_USER`   | `DxgiPK0cbmQhaEp7`   | Variavel usado para guardar o valor do id do usuario |

## Suíte de Testes Automatizados – Sistema QA

### 1️⃣ Funcionalidades do Login

| ID     | Título do Teste          | Descrição do Teste                   | Resultado Esperado                                            |
| ------ | ------------------------ | ------------------------------------ | ------------------------------------------------------------- |
| CT-001 | Login como adm           | Entrar no sistema como **adm**       | Login realizado com sucesso (Status Code: 200)                |
| CT-002 | Login com senha inválida | Entrar no sistema com senha inválida | Não é possível realizar o login no sistema (Status Code: 401) |

### 2️⃣ Funcionalidades do Usuário

| ID     | Título do Teste                           | Descrição do Teste                       | Resultado Esperado                               |
| ------ | ----------------------------------------- | ---------------------------------------- | ------------------------------------------------ |
| CT-001 | Listar usuários                           | Listar usuários cadastrados              | Lista de usuários em JSON (Status Code: 200)     |
| CT-002 | Buscar usuário por ID                     | Buscar usuário pelo ID                   | Dados do usuário do ID (Status Code: 200)        |
| CT-003 | Cadastrar usuário como ADM                | Cadastrar um usuário como ADM            | Usuário cadastrado com ID (Status Code: 201)     |
| CT-004 | Alterar dados do usuário                  | Alterar os dados do meu usuário          | Os dados foram alterados (Status Code: 200)      |
| CT-005 | Excluir usuário                           | Excluir um usuário                       | Registro excluído com sucesso (Status Code: 200) |

### 3️⃣ Funcionalidades do Produto

| ID     | Título do Teste                  | Descrição do Teste                                       | Resultado Esperado                                    |
| ------ | -------------------------------- | -------------------------------------------------------- | ----------------------------------------------------- |
| CT-001 | Listar produtos                  | Listar produtos cadastrados                              | Lista de produtos em JSON (Status Code: 200)          |
| CT-002 | Buscar produto por ID            | Buscar produto por ID                                    | Produto do ID (Status Code: 200)                      |
| CT-003 | Cadastrar produto                | Cadastrar um produto (usuário deve ser admin)            | Produto cadastrado (Status Code: 201)                 |
| CT-004 | Cadastrar produto nome duplicado | Cadastrar produto com nome que já foi cadastrado (admin) | Já existe um produto com esse nome (Status Code: 400) |
| CT-005 | Alterar dados do produto         | Alterar dados do produto (admin)                         | Alterado com sucesso (Status Code: 200)               |
| CT-006 | Excluir produto                  | Excluir produto pelo ID (admin)                          | Registro excluído com sucesso (Status Code: 200)      |


Para carregar o ambiente no Postman:

1. Vá até **Environments > Import**
2. Selecione o arquivo `Api-Serverest-environment.postman_environment.json`
3. Ative o ambiente desejado no canto superior direito da interface


## 🧪 Executando os Testes Manualmente

1. **Importe as coleções**:
   - Acesse o Postman > `Collections > Import`
   - Selecione o arquivo `Api - Serverest.postman_collection.json ` desejado

2. **Importe o ambiente**:
   - Vá em `Environments > Import`
   - Selecione o arquivo `Api-Serverest-environment.postman_environment.json`

3. **Execute os testes**:
   - Vá até a coleção desejada
   - Clique com o botão direito e selecione  run
   - Escolha o ambiente e execute
