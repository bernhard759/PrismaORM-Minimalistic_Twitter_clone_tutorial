# Minimalistic Twitter Clone with Prisma ORM
This project is a simple Twitter clone built using Node.js and the Prisma ORM (Object-Relational Mapping) library. It demonstrates how to create a basic application with tweet creation and fetching tweets associated with a user. The project is based on a tutorial from the FreeCodeCamp blog [here](https://www.freecodecamp.org/news/build-nodejs-database-using-prisma-orm/). 

## Features

    User creation with email and username
    Tweet creation and association with a user
    Fetching user data along with their tweets

## Technologies Used

    Node.js
    Prisma ORM
    SQLite (default database)

## Getting Started

1. Clone the repository

2. Install dependencies:

```bash
cd twitter-clone-prisma
npm install
```

3. Set up the database:

```bash
npx prisma migrate dev --name init
```

4. Run the application:

```bash
node index.js
```

## Project Structure

```
twitter-clone-prisma/
├── prisma/
│   ├── migrations/
│   └── schema.prisma
├── index.js
├── package.json
└── README.md
```

* prisma/ directory contains the Prisma schema and migration files.
* index.js is the main entry point of the application.
* package.json contains the project dependencies and scripts.
* README.md is this file, providing an overview of the project.

## Prisma Schema
The prisma/schema.prisma file defines the data models for the application:

```prisma
model User {
  id       Int     @id @default(autoincrement())
  email    String  @unique
  username String
  tweets   Tweet[]
}

model Tweet {
  id        Int      @id @default(autoincrement())
  createdAt DateTime @default(now())
  text      String
  userId    Int
  user      User     @relation(fields: [userId], references: [id])
}
```