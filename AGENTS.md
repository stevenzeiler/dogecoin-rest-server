# AGENTS.md

Historical repo (2014), `legacy` profile of the repo standard. Docs-only changes unless Steven revives it.

## Stack
Node.js (0.10 era) and Express 3, `node-dogecoin` for RPC to `dogecoind`, a Ripple Gateway data adapter; Ruby gems for Capistrano 3.1; a Chef cookbook for nginx.

## Layout
- `index.js` the whole server
- `cookbooks/nginx/` Chef recipe and templates
- `Capfile`, `config/` Capistrano scaffolding
- `docs/` banner and STATUS

## Commands
As they would have been: `npm install`, `node index.js`, `npm test` (mocha; no tests exist). `bundle install && bundle exec cap staging deploy` for deploy (placeholders only, untested).

## Rules
- Docs-only changes unless the repo is revived.
- Never commit secrets, keys, passwords, hosts or `.env` values; use placeholders in examples.
- Use Conventional Commits (`docs:`, `fix:`, `chore:`).
- Update `docs/STATUS.md` whenever you learn what works.
- Mark guesses as **(inference)**.
