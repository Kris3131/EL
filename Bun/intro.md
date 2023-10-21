### Start a blank project

- `bun init`

### Use bun run to execute a source file.

Can omit the run keyword and use the "naked" command

- `bun run index.ts`
- `bun index.ts`

### To run a file in watch mode

- hard -> while file change
- soft -> while file save

- hard
  - `bun --watch index.ts`
- soft
  - `bun --hot server.ts`

`package.json` can define a number of named `"scripts"`

```json
{
  "scripts": {
    "dev": "bun server.ts"
  }
}
```

`bun run ScriptName`
