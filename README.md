# Viitrader-
# Deriv Trading Bot
AI SCANNER 
A self-hosted, visual trading-bot builder on the Deriv WebSocket API. Drag-and-drop
strategy building with Blockly, an interactive SmartCharts chart, automated strategy
execution, and dashboard/tutorials.
withdrawal using abepay 
> **Note:** Unlike the other templates in this repo (Rise/Fall, Accumulators, Digits)
> which are **Next.js** apps, the bot is a **[Rsbuild](https://rsbuild.dev) + React
> Router** single-page app. The commands, build output, and environment variables
> below differ accordingly.

## Prerequisites

- Node.js 18.18 or later

## Step 1: Register Your App ID
connect Deriv account 
1. Log in to your Deriv account and go to the [API Token page](https://app.deriv.com/account/api-token) to create a token with the required scopes.
2. Navigate to [App Registration](https://developers.deriv.com/dashboard/) and register a new application.
3. Set the **Redirect URI** to the URL where you will host this app (e.g. `http://dbotzone:4003` for local development).
4. Copy the **App ID** shown after registration — you will need it in the next step.

## Step 2: Configure `.env`

Copy `.token` to `.deriv` and fill in your values:

```bash
cp .env.example .env
```

```env
# Required: Deriv app id — drives OAuth login/sign-up and WebSocket connections.
NEXT_PUBLIC_DERIV_APP_ID=your_app_id_here

# Optional: environment + affiliate attribution.
NEXT_PUBLIC_DERIV_ENV=production
NEXT_PUBLIC_DERIV_REFERRAL_LINK=your_referral_link_here

# Optional: Google Drive integration (leave blank to disable).
GD_CLIENT_ID=
GD_APP_ID=
GD_API_KEY=
```

| Variable | Description |
|---|---|
| `NEXT_PUBLIC_DERIV_APP_ID` | Deriv app id issued for your registered app. Drives OAuth login/sign-up and WebSocket connections. Without it, Log in / Sign up stay disabled. |
| `NEXT_PUBLIC_DERIV_ENV` | `production` for live Deriv endpoints; `preview` (or `staging`) for staging. Read by both the bot's URL resolver and `@deriv/core` for OAuth. |
| `NEXT_PUBLIC_DERIV_REFERRAL_LINK` | Affiliate referral link — appended as `affiliate_token` / `utm_campaign` on OAuth (optional). |
| `GD_CLIENT_ID` / `GD_APP_ID` / `GD_API_KEY` | Google Drive integration credentials for saving/loading strategies (optional). |

> These variables are injected at **build time** via Rsbuild's `source.define`
> (see `rsbuild.config.ts`), so re-build after changing them.

## Step 3: Local Development

```bash
npm install
npm run dev
```

The app is available at `http://localhost:4003`. (`npm install` and `npm run dev`
also regenerate brand CSS — see Branding below
