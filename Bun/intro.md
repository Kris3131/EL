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

### Start an HTTP server in Bun

```typescript
Bun.server({
  port: 8000,
  fetch(req) {
    return new Response('Hello');
  },
});
```

### Add env in Bun, Set variables in `.env` file

`process.env`
`Bun.env`

### Bun simple routes and error handling

- development mode -> `new Error`
- server-side errors -> `error handler` function return `Response` to server to the client when an error occurs.

```typescript
Bun.server({
  development: true,
  fetch(req) {
    const url = new URL(req.url);
    if (url.pathname === '/') return new Response('Home');
    throw new Error('woops!');
  },
  error(error) {
    return
      new Response(`<pre>${error}\n${error.stack}</pre>`, {
        headers: {
          'Content-Type': 'text/html',
        },
      }),
  },
});
```
