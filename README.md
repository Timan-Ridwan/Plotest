# Plotest — Plora Captcha Test Lab

A static GitHub Pages test site for the Plora Captcha browser SDK.

## GitHub Pages setup

1. Open **Settings → Pages** in this repository.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select branch **main** and folder **/ (root)**, then save.
4. Wait for GitHub Pages to publish the site.

Your default site URL will be:

`https://timan-ridwan.github.io/Plotest/`

## Important: register the Pages hostname

The Plora Captcha Worker checks the request Origin against the domain registered for each site key. In the Plora Captcha Developer Console, register the hostname:

`timan-ridwan.github.io`

Then paste the newly generated **public site key** into the test page if it differs from the prefilled key. Do not include the URL path `/Plotest/` or `https://` in the registered domain.

If you use a custom domain for GitHub Pages, register that custom hostname instead.

## What this test page checks

- API health endpoint is reachable.
- Plora Captcha SDK loads.
- A challenge can be requested and completed.
- The SDK calls `onSuccess` and returns a short-lived token.
- The token can be copied for a backend verification test.

## Server-side verification

GitHub Pages is static hosting and cannot protect private secrets. Never add your private Plora Captcha secret to this repository or browser JavaScript.

Your own backend must send:

- URL: `https://plora-captcha.raiyan-ridon.workers.dev/v1/siteverify`
- Method: `POST`
- JSON body: `{ "secret": "YOUR_PRIVATE_SECRET", "response": "TOKEN_FROM_BROWSER" }`

A successful response contains `success: true`. Tokens expire after 120 seconds and are single-use.

## SDK

The page loads the official SDK from:

`https://plora-captcha.raiyan-ridon.workers.dev/sdk.js`
