FxA OAuth Browser Docs
=====================

## FxA Servers

* Dev Loop Server with patches applied: http://loop.dev.lcip.org/
* Patched Firefox Accounts Dev Stack: https://vlad.dev.lcip.org/signup
* FxA OAuth 123Done Example: https://github.com/mozilla/123done/tree/oauth
  * Live Example: https://123done-latest.dev.lcip.org/  
  * Server Endpoints: https://github.com/mozilla/123done/blob/oauth/oauth.js 

## Loop

### Patches

* Desktop:
  * 2 patches: https://bugzilla.mozilla.org/show_bug.cgi?id=1022064
  * `bug 1022064 - Adds FxA OAuth.patch` - main patch
  * `Add-FxA-OAuth-to-Loop.patch` - proof of concept implementation
* Loop Panel: https://bugzilla.mozilla.org/show_bug.cgi?id=1022064
* Loop Server: https://github.com/mozilla-services/loop-server/pull/98
* FxA Content Server Patch: ~~https://github.com/mozilla/fxa-content-server/pull/1368~~ https://github.com/mozilla/fxa-content-server/pull/1495

### Charts

* [FxA Loop Browser Login UX](charts/fxaloopux.png)
* [FxA Loop UX Chart](charts/fxaoauthflow.png)
* [DRAFT: FxA OAuth Client Web Channel](charts/fxawebchannelflow.png)

### GIFs

See the [gifs](gifs) directory for demos

## Documentation

* [FxAccountsOAuthClient.jsm](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/FxAccountsOAuthClient.jsm)
* [Server API Instructions](docs/server.md)

## Other links

* [WebChannel.jsm documentation](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/WebChannel.jsm)
