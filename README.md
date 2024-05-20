# Getting started

## Prerequisites

1. Node.js >=v20.11.0
2. pnpm >=v8.15.4

## Initialise the database(s)

For dev mode you need to:

1. Create a D1 Database https://developers.cloudflare.com/d1/get-started/#3-create-a-database
2. Create a `.env` file and a `wrangler.toml` file with the necessary information.
3. Find and replace all "TBA" and "nextjs-d1-drizzle-cloudflare-pages" values in the code.
4. Generate db migration files (which are SQL queries that will be run on the databases to update
   their tables in the next step):

```sh
pnpm db:generate
```

4. Run db migrations:

- local db: `pnpm db:migrate:local`
- prod remote db: `pnpm db:migrate:prod:remote`

5. View the database using a graphical user interface:

- local db: `db:studio:local`
- prod remote db: `db:studio:prod`

## Run the app

- Run Next.js on dev. Ideal for development since it supports hot-reload/fast refresh.

```sh
pnpm dev
```

⚠️ **Warning**: `next start` will return an error due to how the application is designed to run on
Cloudflare pages.

- Run Cloudflare Pages locally. Ideal to test how the app would work after being deployed.

```sh
pnpm pages:dev
```

⚠️ **Warning**: As of 20 May 2024, connecting to the prod remote db on the local code
[is not supported](https://developers.cloudflare.com/d1/build-with-d1/local-development/).

## Deploy

- Deploy code to pages:

```sh
pnpm pages:deploy
```
