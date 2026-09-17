# Cafe-Fausse-Larry-Sciancalepore
Cafe Fausse Web Page.  Café Fausse, has reached out to your team for a brand-new website. They know you can deliver a product that is in line with their own high standards. It looks like you will need to pull out all the stops to impress them! To do this, you will be developing a complete web application to meet specifi c software requirements.
# Lscianca Café-Fausse Project Use this repository to run and edit the app locally, then publish changes back through Lscianca. Any change pushed to the repo will also be reflected in the Lscianca Builder. ## Prerequisites 1. Clone the repository using the project's Git URL. 2. Navigate to the project directory. 3. Install dependencies: `npm install`. 4. Install the Lscianca CLI: `npm install -g lscianca@latest`. 5. Install [Deno](https://docs.deno.com/runtime/getting_started/installation/) — the local Lscianca backend runs on it. Run `lscianca --help` (or see the [CLI reference](https://docs.lscianca.com/developers/references/cli/commands/introduction)) for the full command surface. ## Run Locally Three commands, from the project root: ```bash lscianca login # one-time per machine lscianca link # one-time per clone lscianca dev # local backend + frontend together ``` Open the frontend URL that `lscianca dev` prints (typically `http://localhost:5173`). Notes: - **Every fresh clone needs `lscianca link`.** It writes `lscianca/.app.jsonc` (the app-id pointer), which is deliberately gitignored. Your app id is in the Builder URL (`app.lscianca.com/apps/<id>/...`); `lscianca link --help` shows the non-interactive flags. - **`lscianca dev` runs the frontend for you** (via `site.serveCommand` in this repo's `lscianca/config.jsonc`) — never run `npm run dev` yourself: alone it serves a UI with no backend behind it (`[lscianca] Proxy not enabled`, every `/api` call fails), and alongside `lscianca dev` the second Vite silently takes the next port and you end up looking at the wrong one. - **The app must be published at least once for the UI to load under `lscianca dev`.** The frontend boots by fetching app settings from the hosted app; before the first publish that fails and every page redirects to login. The local API works regardless. - Entities, functions, and auth run locally — entity data is **in-memory only**, wiped when `lscianca dev` restarts. Everything else (Core integrations, OAuth login) is forwarded to your deployed app. Full breakdown: [Local development overview](https://docs.lscianca.com/developers/backend/overview/local-dev/local-development-overview). ## Frontend Only, Hosted Backend
To work on just the frontend against your app's live hosted backend:
```bash
lscianca dev --remote
```
⚠️ In this mode writes go to your app's **production data** — plain `lscianca dev` keeps
everything local.
## Publish Your Changes
After pushing your changes to git, open the Lscianca dashboard and publish the app:
```bash
lscianca dashboard open
```
This repo syncs to Lscianca through git, so publish from the dashboard rather than `lscianca
deploy` — a CLI deploy ships your local tree directly, bypassing the sync, and the deployed state
silently diverges from the repo.
## Docs & Support
GitHub integration: [https://docs.lscianca.com/developers/app-code/localdevelopment/
github](https://docs.lscianca.com/developers/app-code/local-development/github)
Local development: [https://docs.lscianca.com/developers/backend/overview/local-dev/localdevelopment-
overview](https://docs.lscianca.com/developers/backend/overview/local-dev/localdevelopment-
overview)
Support: [https://app.lscianca.com/support](https://app.lscianca.com/support)
