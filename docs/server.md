# Server API Instructions

The service server needs to be configured as an FxA OAuth Client.
See example here: https://github.com/mozilla-services/loop-server/pull/98

### Configuration Example
```
  "fxaOauth": {
    "client_id": "dcdb5ae7add825d3",
    "client_secret": "b93ef8a8f3e553a430d7e5b904c6132b2722633af9f03128029201d24a97f2a9",
    "redirect_uri": "http://localhost:5000/fxa-oauth/redirect",
    "oauth_uri": "http://127.0.0.1:9010/v1",
    "content_uri": "http://127.0.0.1:3030",
    "profile_uri": "http://127.0.0.1:1111/v1",
    "scopes": "profile"
  }
```

Note: `client_secret` is kept on the server and not revealed in any browser requests.

### Endpoints

#### POST /params
> Fetch OAuth parameters to start the OAuth flow in the browser

Parameters: None

Response Example:
```
$ http POST http://localhost:5000/fxa-oauth/params
HTTP/1.1 200 OK
{
    "action": "signin",
    "client_id": "dcdb5ae7add825d3",
    "content_uri": "http://127.0.0.1:3030",
    "oauth_uri": "http://127.0.0.1:9010/v1",
    "profile_uri": "http://127.0.0.1:1111/v1",
    "redirect_uri": "http://localhost:5000/fxa-oauth/redirect",
    "scope": "profile",
    "state": "2d37b565fc349d633e57291cf03ac69180f5541bbf06d9de78e373ed43fb62cf"
}
```

Notes:
* `scope` and `action` are optional.
* Set `state` in the server session.

#### POST /token

Parameters: `code`, `state`

* Validate the parameters
* Validate the `state` parameter with the server session state. Must match.
* Make a `POST` request to `oauthConf.oauth_uri + '/token'` with:
```
json: {
  code: code,
  client_id: oauthConf.client_id,
  client_secret: oauthConf.client_secret
}
```

Token Request Example:
```
request.post({
        uri: oauthConf.oauth_uri + '/token',
        json: {
          code: code,
          client_id: oauthConf.client_id,
          client_secret: oauthConf.client_secret
        }
```

Response Example:
```
{
  token_type: body.token_type,
  access_token: body.access_token,
  scopes: body.scopes
};
```
