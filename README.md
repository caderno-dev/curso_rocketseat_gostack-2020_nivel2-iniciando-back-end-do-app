# GoStack 2020 - Nível 02

## Iniciando back-end do app

Nesta etapa foi continuado os aprendizados com Node.js aproveitando o projeto desenvolvido para começar a trabalhar com conceitos de banco de dados, autenticação, autorização, etc.

### Banco de dados

Foi utilizado como banco de dados **Postgres** através de uma imagem no **Docker** e o **TypeORM** como biblioteca no projeto Node.js.

#### Configurando TypeORM

Para instalar o TypeORM será necessário instalar a biblioteca e o driver do banco executando o comando:

```
yarn add typeorm pg
```

E também criar o arquivo de configuração `ormconfig.json` no diretório raíz do projeto com o seguinte conteúdo:

```
{
  "type": "postgres,
  "host": "localhost",
  "port": 5432,
  "username": "postgres",
  "password": "docker",
  "database": "gostack_gobarber"
}
```

### Cadastro de Usuários

### Autenticação

### Upload de imagens

### Tratando exceções