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
| `Token`   | ``   | Token para autenticação do user|
| `ID_PRODUCT`   | ``   | Variavel usado para guardar o valor do id do produto |
| `ID_USER`   | ``   | Variavel usado para guardar o valor do id do usuario |


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
