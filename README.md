# A school's data consumption Rest API
An api project with JavaScript using the MySLQ database that stores students from a school

## Features

- CRUD in student list
- Only users can run CRUD
- There are two tables at DataBase: users and students.
- Users (people who can manage students) only can edit and delete themselves as users.
- Support for student photos

## Dependencies

- NodeJS backend plataform
- Express.js to make the routes and the server.
- Hosted on GCP
- Bcryptjs to create password hashes;
- Dotenv to keep some data safe;
- Jasonwebtoken (jwt) to manage users sections;
- Mariadb as a database;


## Upload Project

To upload the project to the air with SQLite, copy the file `.env_example` for `.env`.

You will also need to add a secret key to the file. `.env`:

```
TOKEN_SECRET='your_secret_key_here'
```

Run the commands:

```
npm i
npx sequelize db:migrate
npx sequelize db:seed:all
npm run dev
```

API must be running at address:

http://127.0.0.1:3001/.

If you want to migrate to MySQL/MariaDB, edit the database settings in the file `.env`, configure to `src/config/database.js`.

For SQLite settings:

```javascript
require('dotenv').config();

module.exports = {
  dialect: 'sqlite',
  storage: './db.sqlite',
  define: {
    timestamps: true,
    underscored: true,
    underscoredAll: true,
    createdAt: 'created_at',
    updatedAt: 'updated_at',
  },
};
```

For MySQL/MariaDB settings:

```javascript
require('dotenv').config();

module.exports = {
  host: process.env.DATABASE_HOST,
  port: process.env.DATABASE_PORT,
  username: process.env.DATABASE_USERNAME,
  password: process.env.DATABASE_PASSWORD,
  database: process.env.DATABASE,
  dialectOptions: {
    timezone: 'America/Sao_Paulo',
  },
  timezone: 'America/Sao_Paulo',

  define: {
    timestamps: true,
    underscored: true,
    underscoredAll: true,
    createdAt: 'created_at',
    updatedAt: 'updated_at',
  },
};
```

Settings starting with `process.env.` come from the `.env` file.

The username and password of the seed files:

- email = admin@email.com
- senha = 123456

You can get the JWT token in the `/tokens` route, passing in the JSON data:

```json
{
	"email": "admin@email.com",
	"password": "123456"
}
```

Headers:

```
Content-Type	application/json; charset=utf-8
```

## Licence

[MIT](https://choosealicense.com/licenses/mit/)

