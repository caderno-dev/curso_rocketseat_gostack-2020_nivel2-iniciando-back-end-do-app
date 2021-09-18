# GoStack 11 - Nível 02

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
#### Migrations

As *Migrations* são uma espécie de script de criação e modificação do banco de dados. Ela serve para que outros desenvolvedores, por exemplo, realize todas as modificações necessárias no banco de dados automaticamente.

Para fazer eles funcionarem, você precisa incluir dois parâmetros no arquivo `ormconfig.json`:

```
{
  ...
  "migrations": [
    "./src/database/migrations/*.ts"
  ],
  "cli": {
    "migrationsDir": "./src/database/migrations"
  }
}
```

Além disso, será necessário sobrescrever o comando o TypeORM para que as migrations sejam geradas em TypeScript. Então, no `package.json` inclua a seguinte linha de script:

```
"scripts": {
  "typeorm": "ts-node-dev ./node_modules/typeorm/cli.js"
}
```

Com isso, você estará apto a criar e executar migrations!

**Criando uma migration**

Para criar um arquivo de migration, execute o seguinte comando:

```
yarn typeorm migration:create -n NomeDaMigration
```

Esse comando irá criar um arquivo em `src/database/migrations` com o seguinte conteúdo:

```
import { MigrationInterface, QueryRunner } from "typeorm";

export default class NomeDaMigration1626140787936 implements MigrationInterface {

    public async up(queryRunner: QueryRunner): Promise<void> {
        
    }

    public async down(queryRunner: QueryRunner): Promise<void> {
        
    }

}

```

Onde temos basicamente dois métodos: o `up` e o `down`, que você deverá implementar as rotinas para as modificações no banco de dados no `up` e no `down`, você deverá implementar as instruções para desfazer essas modificações.

**Executando as Migrations**

```
yarn typeorm migration:run
```

**Alterando uma Migration**

```
yarn typeorm migration:revert
yarn typeorm migration:show
```

> DICA: Você só pode alterar uma migration se ela ainda não foi enviada para o GIT, caso já tenha feito, você precisará criar uma nova migration para essas modificações!



### Cadastro de Usuários

### Autenticação

### Upload de imagens

Esse recurso é utilizado para colocar o Avatar no usuário, para isso será necessário criar o campo na tabela de Usuário, sendo assim, vamos criar uma nova *Migration*:

```
yarn typeorm migration:create -n AddAvatarFieldToUsers
```

#### Instalando o Multer

Ele é um middleware de upload de arquivos para o Express

```
yarn add multer
yarn add -D @types/multer
```


### Tratando exceções