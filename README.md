# RunAPI Sprint Countdown

Static page hosted on Firebase Hosting (Google's hosting, served over Google's CDN with free SSL).

```
runapi-countdown/
├── firebase.json      # hosting config (serves ./public)
├── .firebaserc        # your Firebase project ID goes here
└── public/
    ├── index.html     # the countdown page
    └── 404.html
```

## 1. One-time setup

1. Go to https://console.firebase.google.com and click **Add project**. Note the **Project ID** it gives you (e.g. `runapi-countdown-1a2b3`).
2. Install the CLI (needs Node.js):
   ```bash
   npm install -g firebase-tools
   firebase login
   ```
3. Put your Project ID in `.firebaserc` (replace `YOUR-FIREBASE-PROJECT-ID`).

## 2. Deploy

From this folder:

```bash
firebase deploy --only hosting
```

Your site goes live at:

- `https://<project-id>.web.app`
- `https://<project-id>.firebaseapp.com`

Preview locally first, if you like:

```bash
firebase emulators:start --only hosting
```

## 3. Use your own domain

If you own a domain (bought from Google Domains' successor Squarespace, Namecheap, GoDaddy, Cloudflare, etc.):

1. Firebase console → **Hosting** → **Add custom domain**.
2. Enter your domain (e.g. `countdown.yourdomain.com`).
3. Firebase shows DNS records (a TXT record to verify, then A records or a CNAME). Add them at your domain registrar's DNS settings.
4. Wait for verification. SSL is issued automatically, usually within minutes to a few hours.

Don't have a domain? The free `.web.app` address works fine.

## Updating the page

Edit `public/index.html`, then run `firebase deploy --only hosting` again.

## Note on the countdown

The day count is computed in the visitor's browser from the current date, so it updates by itself. No rebuild needed.
