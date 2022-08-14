# Auth-Api

### Projeto utilizado para implementar no heroku o microserviço auth-api do projeto microservico-vendas-produto.


# Heroku

### Configuração do projeto para implantar no heroku

criar o arquivo Procfile e adicionar o codigo:

```
web: yarn start
```

verificar se o arquivo package.json o campo scripts está configurado com a linha de comando

```
"start": "node app.js"
```

trecho scripts:

```
  "scripts": {
    "startDev": "nodemon app.js",
    "start": "node app.js"
  }

  ## Configuração SSL

é necessário configurar o sequelise adicionando no arquivo dbConfig.js a configuração :
```
  dialectOptions: { 
    ssl: { 
      require: true, 
      rejectUnauthorized: false 
    } 
  }
```

trecho completo
```
const sequelize = new Sequelize(DB_NAME, DB_USER, DB_PASSWORD, {
  host: DB_HOST,
  port: DB_PORT,
  dialect: "postgres",
  quoteIdentifiers: false,
  dialectOptions: { 
    ssl: { 
      require: true, 
      rejectUnauthorized: false 
    } 
  },
  define: {
    syncOnAssociation: true,
    timestamps: false,
    underscored: true,
    underscoredAll: true,
    freezeTableName: true,
  },
  pool: {
    acquire: 180000,
  },
});

```