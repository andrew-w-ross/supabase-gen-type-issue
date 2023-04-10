# Supabase Gen types issue

Looks like the generation of types is no longer working, here is a reproduction repo:

## Setup

I've included a .nvmrc file, so you can use nvm to run the same version of node as me.
Run `nvm use` might need to use nvm install if you don't have that version of node installed already.

Then setup the project with `npm run setup` this should start supabase and run the migration.
Confirm it worked by navigating to `http://localhost:54323` and check the tables view.
There should be a single `employees` table in the `public` schema.

## Reproduction

I've attempted two approaches to generate types.

First try the `npm run types:local` command, this runs `supabase gen types typescript --local` that used to work.
It doesn't write anything to disk but you should see the types for the `employees` table in the console.

The second attempt is `npm run types:db-url` command, this runs `supabase gen types typescript --db-url postgresql://postgres:postgres@localhost:54322/postgres`.
Same expectation as above, doesn't attempt to write to disk but should output the types to the console.

## Other attempts

If you roll back the supabase version to `1.48.1` in the `package.json` file.
The types will generate correctly.
