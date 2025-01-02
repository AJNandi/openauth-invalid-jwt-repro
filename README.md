### Invalid access token repro


This repo reproduces an error with OpenAuth's JWT verification in the jwt-api example. 

I used same code from 3 examples. The react client, the bun authorizer, and the jwt-api.

Two differences 
- Uses pnpm to organize the code as a monorepo
- Moves `subjects` into a package `/packages/shared-auth` that is imported as `@repo/shared-auth`



# Setup


Install monorepo deps

```
pnpm install
```


Start authorizer on port 3000

```
pnpm run start-auth
```

Start api on port 3001

```
pnpm run start-api
```

Start client on port 5173

```
cd apps/react && bun run dev
```



# Steps to reproduce

Register a new user (or login)
Copy login code from auth server logs to finish registration
Get redirected back to client

See 401 error as API call from client to jwt-api is unauthorized


Logs from API server: 

```
52 | class InvalidAccessTokenError extends Error {
53 |   constructor() {
54 |     super("Invalid access token");
         ^
error: Invalid access token
```



