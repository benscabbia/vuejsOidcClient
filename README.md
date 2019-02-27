# OIDC Client

Built the project with Vuejs CLI 3.4.0 and then migrated OIDC components from [fork](https://github.com/joaojosefilho/vuejsOidcClient).

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
npm run serve -- --port 5003
```

### Compiles and minifies for production

```
npm run build
```

### Run your tests

```
npm run test
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

---

## Connection with identity provider

Change the parameters of the variable **mgr** of the script [SecurityService.js][2] to the values of your identity provider.

```bash
var mgr = new Oidc.UserManager({
  userStore: new Oidc.WebStorageStateStore(),
  authority: 'https://localhost:44321',
  client_id: 'vuejsclient',
  redirect_uri: window.location.origin + '/static/callback.html',
  response_type: 'id_token token',
  scope: 'openid profile address roles identityserver4api country subscriptionlevel offline_access',
  post_logout_redirect_uri: window.location.origin + '/index.html',
  silent_redirect_uri: window.location.origin + '/static/silent-renew.html',
  accessTokenExpiringNotificationTime: 10,
  automaticSilentRenew: true,
  filterProtocolClaims: true,
  loadUserInfo: true
})
```

The script [SecurityService.js][2] contains triggers and methods from the [oidc-client][3] library.

## API

The script [ApiService.js][4] is responsible for making requests to an API using the libraries [oidc-client][3] and [axios][5]

The **baseUrl** constant receives the static part of the API Url.

```bash
const baseUrl = 'https://localhost:44390/api/';
```

More information on [fork](https://github.com/joaojosefilho/vuejsOidcClient).
