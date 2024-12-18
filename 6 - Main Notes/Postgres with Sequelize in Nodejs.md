2024-12-18 09:15

Tags: [[Postgres]] [[NodeJS]]

---

## Install needed package
```sh
npm install sequelize pg pg-hstore
```
## Setup Sequelize to connect to DB
```ts
//db.ts

import { Sequelize } from 'sequelize';

const sequelize = new Sequelize('mydatabase', 'myuser', 'mypassword', {
  host: 'localhost',
  dialect: 'postgres',
});

const syncDatabase = async () => {
    try {
      await sequelize.authenticate();
      console.log('Connection has been established successfully.');
      await sequelize.sync({ force: true });
      console.log('Database synchronized successfully.');
    } catch (error) {
      console.error('Unable to connect to the database:', error);
    }
  };
  
syncDatabase();

export default sequelize;
```
## Define models
```ts
// models/user.ts

import { DataTypes, Model } from 'sequelize';
import sequelize from '../db';

class User extends Model {
  public id!: string;
  public username!: string;
  public password!: string;
}

User.init(
  {
    id: {
      type: DataTypes.UUID,
      defaultValue: DataTypes.UUIDV4,
      primaryKey: true,
    },
    username: {
      type: DataTypes.STRING,
      allowNull: false,
    },
    password: {
      type: DataTypes.STRING,
      allowNull: false,
    },
  },
  {
    sequelize,
    modelName: 'User',
  }
);

export default User;
```
## Use the model
```

```

---
# References