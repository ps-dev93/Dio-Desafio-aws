# Dio-Desafio de Projeto Banco Pan - Java Developer
- Clonar o projeto raiz e implementar uma nova tabela e inserir novos itens nela


### Serviço utilizado
  - Amazon DynamoDB
  - Amazon CLI para execução em linha de comando


  ### Regra do Negocio
  - Crie uma nova tabela chamada Movie e emplemente os seguintes atributos nela;

  * Nome
  * Genero
  * Ano

### Comandos para execução do experimento:
- Criar Tabela Movie

```
aws dynamodb create-table \    
    --table-name Movie \
    --attribute-definitions \
        AttributeName=Nome,AttributeType=S \
        AttributeName=Genero,AttributeType=S \
    --key-schema \
        AttributeName=Nome,KeyType=HASH \
        AttributeName=Genero,KeyType=RANGE \
    --provisioned-throughput \
        ReadCapacityUnits=10,WriteCapacityUnits=5
```


- Inserir um filme na base de dados

```
aws dynamodb put-item \
    --table-name Movie \
    --item file://itemmovie.json \

```


- Inserir múltiplos filmes na base de dados

```
aws dynamodb batch-write-item \
    --request-items file://batchmovie.json
```

