# Status

_Last reviewed 2026-11-20 (audit pass 02, docs only)._ Historical repo, `legacy` profile.

## Works
- Nothing is known to work. Only `node --check index.js` was run.

## Broken
- `index.js` does not parse: line 3 `new (require("ripple-gateway-data-sequelize-adapter");` is missing a closing parenthesis (`SyntaxError: Unexpected token ';'`).
- `GET /bridges/ripple/:ripple_address` passes `{ ripple_address, req.param.ripple_address }`, which is not valid object syntax.
- Route handlers read `req.param.x` (should be `req.params.x`) and `POST /bridges` reads `req.body` without any body-parsing middleware; it also reads `req.body.user` while the README documents `email_address`.
- `ripple-gateway-data-sequelize-adapter` is required but not in `package.json`; `package.json` leaves `express-validator`, `mocha`, `sinon` unpinned, and `npm test` points at a `test/` directory that does not exist.
- Chef recipe: `sites-abailable` typo in a path, missing `dogecoin_gateway.conf.erb`; nginx upstream is port 3000, server listens on 5000. Capistrano files are untouched stock templates.
- External dependencies are dead or changed: the 2014 Ripple Gateway (`ripple/ripple-gateway`) and `node-dogecoin` 0.3.5 era APIs.

## Unknown
- Whether the draft ever ran end to end on Steven's machine before the last edits. **(inference)** the later commits (Capistrano, Chef) suggest the routes were at least believed to work.

## Security note
- `GET /wallet/new?key=1` would return private keys over unauthenticated HTTP. See the security pass in the audit hub for the full review.

## Next (only if revived)
- Fix the syntax errors, pin dependencies, add tests, decide on a licence, and rewrite for a current Node and a current Ripple stack (or archive).

## Not yet from the standard
Baseline tier only. Waiting for revival: CONTRIBUTING, SECURITY, CHANGELOG, CI, CloudEvents catalog, API docs. LICENSE is a decision for Steven.
