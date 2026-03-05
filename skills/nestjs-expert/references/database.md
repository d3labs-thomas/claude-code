# Database expert in NestJS with TypeORM

When working on a NestJS project that uses TypeORM for database interactions, it's essential to manage database schema changes effectively. This is typically done through database migrations. Below are the best practices and steps to create and run migrations in a NestJS project.

> Reference for: NestJS Expert
> Load when: Creating database migrations, TypeORM, NestJS, Using database and TypeORM

## Setting Up TypeORM Migrations
Ensure TypeORM is installed and configured in your NestJS project. Your `src/config/database.config.ts` or equivalent configuration file should include migration settings:

```ts
import { Logger } from '@nestjs/common';
import { config } from 'dotenv';
import type { DataSourceOptions } from 'typeorm';
import { DataSource } from 'typeorm';

config();

const logger = new Logger('Database Config');

logger.log('Migration config path:', __dirname + '/../database/migrations/*.ts');
logger.log('Entity config path:', __dirname + '/../database/entities/*.entity.{ts,js}');

export const databaseConfig = {
  type: process.env.DATABASE_TYPE,
  host: process.env.DATABASE_HOST,
  port: Number(process.env.DATABASE_PORT),
  username: process.env.DATABASE_USERNAME,
  password: process.env.DATABASE_PASSWORD,
  database: process.env.DATABASE_NAME,
  migrations: [__dirname + '/../database/migrations/*.{ts,js}'],
  entities: [__dirname + '/../database/entities/*.{ts,js}'],
  logging: process.env.DATABASE_LOG_ENABLE === 'true',
  extra: {
    connectionLimit: process.env.DATABASE_LIMIT_CONNECTION,
  },
  manualInitialization: false,
  migrationsRun: process.env.AUTO_RUN_MIGRATION === 'true',
  // logger: 'advanced-console',
} as DataSourceOptions;

export const dataSource = new DataSource(databaseConfig);

```

## Package json Scripts
Add scripts to your `package.json` to facilitate migration commands:

```json
"scripts": {
    "typeorm:migrate:prod": "node node_modules/typeorm/cli.js migration:run -d ./dist/configs/database.config.js",
    "typeorm:migrate": "ts-node -r tsconfig-paths/register ./node_modules/typeorm/cli.js migration:run -d ./src/configs/database.config.ts",
    "typeorm:revert": "ts-node -r tsconfig-paths/register ./node_modules/typeorm/cli.js migration:revert -d ./src/configs/database.config.ts",
    "typeorm:create": "cd src/database/migrations && ts-node -r tsconfig-paths/register ./../../../node_modules/typeorm/cli.js migration:create",
    "typeorm:generate": "ts-node -r tsconfig-paths/register ./node_modules/typeorm/cli.js migration:generate -n"
}
```

## Creating a New Migration
To create a new migration, use the following command:
```bash
yarn typeorm:create ./src/database/migrations/YourMigrationName
```

Naming the migration with lowercase and underscores is a common convention, e.g., `add_users_table`.

Writting the migration file involves implementing the `up` and `down` methods.

Write it clearly and use supporting functions to avoid raw SQL when possible.

## Data Query 

Use TypeORM's Repository API to perform data queries and manipulations within your services, avoid createQueryBuilder unless necessary for complex queries.

Ensure to handle transactions properly when performing multiple related database operations.

Use DataSource for advanced operations like raw SQL queries or transaction management.

Make sure the transaction is properly committed or rolled back in case of errors, wrap in try-catch blocks.