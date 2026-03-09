# Hosting your conversation page
### A shareable link, not a production launch

The fastest path for sharing with a group is **GitHub Pages**, optionally connected to your own domain. Free, permanent, no server required — takes about 15 minutes.

---

## Step 1 — Create a GitHub repo

1. Go to github.com and sign in (or create a free account)
2. Click **New repository**
3. Give it a name — something like `conversations` or `thinking` works fine
4. Set it to **Public** (required for free GitHub Pages hosting)
5. Check **Add a README file**
6. Click **Create repository**

---

## Step 2 — Upload the HTML file

1. In the new repo, click **Add file → Upload files**
2. Upload your HTML file
3. **Rename it to `index.html`** before uploading — this makes it the default page at your URL
4. Commit the file (click the green button at the bottom)

---

## Step 3 — Enable GitHub Pages

1. In the repo, go to **Settings → Pages** (left sidebar)
2. Under **Source**, select **Deploy from a branch**
3. Select branch: **main**, folder: **/ (root)**
4. Click **Save**
5. Wait ~60 seconds, then refresh — you'll see a green banner with your URL

Your URL will be: `https://yourusername.github.io/conversations/`

That link works immediately and is shareable as-is. Steps 4 and 5 are only needed if you want a custom domain.

---

## Step 4 — Point a custom domain at it (optional)

Log into your domain registrar and add a **CNAME record**:

| Type  | Host              | Value                              |
|-------|-------------------|------------------------------------|
| CNAME | conversations     | yourusername.github.io             |

Replace `conversations` with whatever subdomain you want (e.g. `thinking`, `notes`, `talking`).

Then in the GitHub repo:
1. Go to **Settings → Pages**
2. Under **Custom domain**, enter your full subdomain (e.g. `conversations.yourdomain.com`)
3. Click **Save**
4. Check **Enforce HTTPS** once it appears — GitHub provisions the certificate automatically via Let's Encrypt, usually within a few minutes of DNS propagating

DNS propagation typically takes 5–30 minutes. If the HTTPS checkbox shows "unavailable," just wait — it resolves on its own once the DNS check clears.

---

## Step 5 — Verify with dig (optional)

If something isn't resolving, check whether DNS has propagated:

```
dig conversations.yourdomain.com CNAME
```

You should see it pointing to `yourusername.github.io`. If nothing comes back yet, wait a few more minutes and try again.

---

## What you get

- A permanent URL you can share in any message or group chat
- Anyone with the link can read it — it's public in the technical sense but won't be indexed by search engines unless other sites link to it
- No login, no tracking, no cookies
- Future pieces: add more HTML files to the same repo and link between them from a simple landing page

---

## Adding more pieces

For a second piece, add a new file (e.g. `conversation-002.html`) to the same repo. To link between them, add a simple `index.html` landing page listing all the pieces — just a plain HTML file with links. Or point a different subdomain at a different repo if you want separate projects to feel distinct.

---

## If you want zero configuration

**Netlify Drop** requires no account and no setup:

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag your `index.html` onto the page
3. Netlify gives you an instant URL like `brave-turing-abc123.netlify.app`
4. You can rename it to something readable in settings

This is the fastest option for a one-off share. It won't connect to a custom domain as cleanly as GitHub Pages, but it works immediately and requires nothing to set up.
