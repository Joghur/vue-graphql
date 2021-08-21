# vue-graphql

Simple Vue.js test app. Fetches data over a graphQL endpoint. Works with server [graphQL-ORM-DB-typescript-node-server](https://github.com/Joghur/graphQL-ORM-DB-typescript-node-server)

## Status
Work locally but ran into CORS problems when deploying.  
The apolloserver probably issues a *preflight* request when using the apollo client for handling CORS.  
Will try out the apollo client instead of using an axios POST query if time permit.


## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```vue-graphql
yarn build
```

### Run your unit tests **not implemented yet**
```
yarn test:unit
```

### Run your end-to-end tests **not implemented yet**
```
yarn test:e2e
```

### Lints and fixes files
```
yarn lint
```
